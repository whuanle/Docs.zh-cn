---
title: 身份验证和授权在 ASP.NET Core SignalR
author: tdykstra
description: 了解如何在 ASP.NET Core SignalR 中使用身份验证和授权。
monikerRange: '>= aspnetcore-2.1'
ms.author: anurse
ms.custom: mvc
ms.date: 06/29/2018
uid: signalr/authn-and-authz
ms.openlocfilehash: fa5e8d4aea6100c54fd8b98411ef877d1dd8621c
ms.sourcegitcommit: 4d5f8680d68b39c411b46c73f7014f8aa0f12026
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028200"
---
# <a name="authentication-and-authorization-in-aspnet-core-signalr"></a>身份验证和授权在 ASP.NET Core SignalR

通过[Andrew Stanton-nurse](https://twitter.com/anurse)

[查看或下载示例代码](https://github.com/aspnet/Docs/tree/master/aspnetcore/signalr/authn-and-authz/sample/) [（如何下载）](xref:tutorials/index#how-to-download-a-sample)

## <a name="authenticate-users-connecting-to-a-signalr-hub"></a>连接到的 SignalR hub 的用户进行身份验证

可与 SignalR [ASP.NET Core 身份验证](xref:security/authentication/index)若要将用户与每个连接相关联。 在中心，可以从访问身份验证数据[ `HubConnectionContext.User` ](/dotnet/api/microsoft.aspnetcore.signalr.hubconnectioncontext.user)属性。 身份验证允许中心与用户关联的所有连接上调用方法 (请参阅[SignalR 中管理用户和组](xref:signalr/groups)有关详细信息)。 多个连接可能包含单个用户相关联。

### <a name="cookie-authentication"></a>Cookie 身份验证

在基于浏览器的应用中，cookie 身份验证允许你现有的用户凭据以自动传递到 SignalR 连接。 如果使用浏览器客户端，则需要无额外配置。 如果用户登录到你的应用，SignalR 连接会自动继承此身份验证。

Cookie 身份验证不被建议，除非应用只需要从浏览器客户端的用户进行身份验证。 使用时[.NET 客户端](xref:signalr/dotnet-client)，则`Cookies`属性可以配置在`.WithUrl`调用，以提供一个 cookie。 但是，使用 cookie 身份验证从.NET 客户端要求提供要交换的 cookie 身份验证数据的 API 应用。

### <a name="bearer-token-authentication"></a>持有者令牌身份验证

使用非浏览器客户端的客户端时，持有者令牌身份验证是建议的方法。 在这种方法，客户端提供访问令牌，用于服务器验证，并用于标识用户。 持有者令牌身份验证的详细信息已超出本文的讨论范围。 在服务器上，使用配置持有者令牌身份验证[JWT 持有者中间件](/dotnet/api/microsoft.extensions.dependencyinjection.jwtbearerextensions.addjwtbearer)。

在 JavaScript 客户端，该令牌可以使用提供[accessTokenFactory](xref:signalr/configuration#configure-bearer-authentication)选项。

[!code-typescript[Configure Access Token](authn-and-authz/sample/wwwroot/js/chat.ts?range=63-65)]

在.NET 客户端，没有类似[AccessTokenProvider](xref:signalr/configuration#configure-bearer-authentication)属性，可用于配置的令牌：

```csharp
var connection = new HubConnectionBuilder()
    .WithUrl("https://example.com/myhub", options =>
    { 
        options.AccessTokenProvider = () => Task.FromResult(_myAccessToken);
    })
    .Build();
```

> [!NOTE]
> 你提供的访问令牌函数之前调用**每个**所做的 SignalR 的 HTTP 请求。 如果需要续订令牌才能保持连接处于活动状态 （因为它在连接期间可能会过期），此函数中执行此操作从并返回更新的令牌。

在标准 web Api，持有者令牌将发送 HTTP 标头中。 但是，SignalR 是无法使用某些传输通道时在浏览器中设置这些标头。 使用 Websocket 和服务器发送事件时，会将令牌传输作为查询字符串参数。 若要在服务器上支持此功能，则需要其他配置：

[!code-csharp[Configure Server to accept access token from Query String](authn-and-authz/sample/Startup.cs?name=snippet)]

### <a name="windows-authentication"></a>Windows 身份验证

如果[Windows 身份验证](xref:security/authentication/windowsauth)配置为在应用中，SignalR 可以使用该标识安全中心。 但是，若要将消息发送给单个用户，您需要添加自定义的用户 ID 提供程序。 这是因为 Windows 身份验证系统不提供 SignalR 使用来确定用户名称的"名称标识符"声明。

添加新的类实现`IUserIdProvider`和检索的声明之一中要用作标识符的用户。 例如，若要使用"Name"声明 (即窗体中的 Windows 用户名`[Domain]\[Username]`)，创建以下类：

```csharp
public class NameUserIdProvider : IUserIdProvider
{
    public string GetUserId(HubConnectionContext connection)
    {
        return connection.User?.FindFirst(ClaimTypes.Name)?.Value;
    }
}
```

而非`ClaimTypes.Name`，可以使用的任何值`User`（例如 Windows SID 标识符等）。

> [!NOTE]
> 您选择的值必须是在系统中所有用户之间唯一的。 否则，适用于一个用户的消息可能最终转到不同的用户。

注册此组件中的您`Startup.ConfigureServices`方法**后**对的调用 `.AddSignalR`

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ... other services ...

    services.AddSignalR();
    services.AddSingleton<IUserIdProvider, NameUserIdProvider>();
}
```

在.NET 客户端，必须通过设置启用 Windows 身份验证[UseDefaultCredentials](/dotnet/api/microsoft.aspnetcore.http.connections.client.httpconnectionoptions.usedefaultcredentials)属性：

```csharp
var connection = new HubConnectionBuilder()
    .WithUrl("https://example.com/myhub", options =>
    {
        options.UseDefaultCredentials = true;
    })
    .Build();
```

使用 Microsoft Internet Explorer 或 Microsoft Edge 时，浏览器客户端仅支持 Windows 身份验证。

## <a name="authorize-users-to-access-hubs-and-hub-methods"></a>授权用户访问集线器和集线器方法

默认情况下，可以通过未经身份验证的用户调用一个中心中的所有方法。 为了要求身份验证，应用[Authorize](/dotnet/api/microsoft.aspnetcore.authorization.authorizeattribute)属性为中心：

[!code-csharp[Restrict a hub to only authorized users](authn-and-authz/sample/Hubs/ChatHub.cs?range=8-10,32)]

可以使用的构造函数参数和属性`[Authorize]`属性以限制只有匹配特定的用户访问[授权策略](xref:security/authorization/policies)。 例如，如果具有名为的自定义授权策略`MyAuthorizationPolicy`可以确保只有匹配该策略的用户可以访问的中心使用以下代码：

```csharp
[Authorize("MyAuthorizationPolicy")]
public class ChatHub: Hub
{
}
```

单个集线器方法可以具有`[Authorize]`也应用属性。 如果当前用户不匹配的策略应用于方法，是向调用方返回错误：

```csharp
[Authorize]
public class ChatHub: Hub
{
    public async Task Send(string message)
    {
        // ... send a message to all users ...
    }

    [Authorize("Administrators")]
    public void BanUser(string userName)
    {
        // ... ban a user from the chat room (something only Administrators can do) ...
    }
}
```
