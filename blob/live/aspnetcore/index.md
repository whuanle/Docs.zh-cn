---
title: "ASP.NET Core 简介"
author: rick-anderson
description: "提供 ASP.NET Core 简介。"
keywords: ASP.NET Core
ms.author: riande
manager: wpickett
ms.date: 12/12/2017
ms.topic: article
ms.technology: aspnet
ms.prod: asp.net-core
uid: index
ms.openlocfilehash: 5d8e9a72a3b69866f5a4f725076e44575d20d64f
ms.sourcegitcommit: 12e5194936b7e820efc5505a2d5d4f84e88eb5ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="introduction-to-aspnet-core"></a><span data-ttu-id="9814e-104">ASP.NET Core 简介</span><span class="sxs-lookup"><span data-stu-id="9814e-104">Introduction to ASP.NET Core</span></span>

<span data-ttu-id="9814e-105">作者：[Daniel Roth](https://github.com/danroth27)[Rick Anderson](https://twitter.com/RickAndMSFT) 和 [Shaun Luttin](https://twitter.com/dicshaunary)</span><span class="sxs-lookup"><span data-stu-id="9814e-105">By [Daniel Roth](https://github.com/danroth27), [Rick Anderson](https://twitter.com/RickAndMSFT), and [Shaun Luttin](https://twitter.com/dicshaunary)</span></span>

<span data-ttu-id="9814e-106">ASP.NET Core 是一个跨平台的高性能[开源](https://github.com/aspnet/home)框架，用于生成基于云且连接 Internet 的新式应用程序。</span><span class="sxs-lookup"><span data-stu-id="9814e-106">ASP.NET Core is a cross-platform, high-performance, [open-source](https://github.com/aspnet/home) framework for building modern, cloud-based, Internet-connected applications.</span></span> <span data-ttu-id="9814e-107">使用 ASP.NET Core，可以：</span><span class="sxs-lookup"><span data-stu-id="9814e-107">With ASP.NET Core, you can:</span></span>

* <span data-ttu-id="9814e-108">生成 Web 应用和服务、[IoT](https://www.microsoft.com/internet-of-things/) 应用和移动后端。</span><span class="sxs-lookup"><span data-stu-id="9814e-108">Build web apps and services, [IoT](https://www.microsoft.com/internet-of-things/) apps, and mobile backends.</span></span>
* <span data-ttu-id="9814e-109">在 Windows、macOS 和 Linux 上使用喜爱的开发工具。</span><span class="sxs-lookup"><span data-stu-id="9814e-109">Use your favorite development tools on Windows, macOS, and Linux.</span></span>
* <span data-ttu-id="9814e-110">部署到云或本地。</span><span class="sxs-lookup"><span data-stu-id="9814e-110">Deploy to the cloud or on-premises.</span></span>
* <span data-ttu-id="9814e-111">在 [.NET Core 或 .NET Framework](https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server) 上运行。</span><span class="sxs-lookup"><span data-stu-id="9814e-111">Run on [.NET Core or .NET Framework](https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server).</span></span>

## <a name="why-use-aspnet-core"></a><span data-ttu-id="9814e-112">为何使用 ASP.NET Core？</span><span class="sxs-lookup"><span data-stu-id="9814e-112">Why use ASP.NET Core?</span></span>

<span data-ttu-id="9814e-113">数百万开发人员使用过（并将继续使用）[ASP.NET 4.x](https://docs.microsoft.com/en-us/aspnet/overview) 创建 Web 应用。</span><span class="sxs-lookup"><span data-stu-id="9814e-113">Millions of developers have used (and continue to use) [ASP.NET 4.x](https://docs.microsoft.com/en-us/aspnet/overview) to create web apps.</span></span> <span data-ttu-id="9814e-114">ASP.NET Core 是重新设计的 ASP.NET 4.x，更改了体系结构，形成了更精简的模块化框架。</span><span class="sxs-lookup"><span data-stu-id="9814e-114">ASP.NET Core is a redesign of ASP.NET 4.x, with architectural changes that result in a leaner, more modular framework.</span></span>

<span data-ttu-id="9814e-115">ASP.NET Core 具有如下优点：</span><span class="sxs-lookup"><span data-stu-id="9814e-115">ASP.NET Core provides the following benefits:</span></span>

* <span data-ttu-id="9814e-116">生成 Web UI 和 Web API 的统一场景。</span><span class="sxs-lookup"><span data-stu-id="9814e-116">A unified story for building web UI and web APIs.</span></span>
* <span data-ttu-id="9814e-117">集成[新式客户端框架](xref:client-side/index)和开发工作流。</span><span class="sxs-lookup"><span data-stu-id="9814e-117">Integration of [modern, client-side frameworks](xref:client-side/index) and development workflows.</span></span>
* <span data-ttu-id="9814e-118">基于环境的云就绪[配置系统](xref:fundamentals/configuration/index)。</span><span class="sxs-lookup"><span data-stu-id="9814e-118">A cloud-ready, environment-based [configuration system](xref:fundamentals/configuration/index).</span></span>
* <span data-ttu-id="9814e-119">内置[依赖项注入](xref:fundamentals/dependency-injection)。</span><span class="sxs-lookup"><span data-stu-id="9814e-119">Built-in [dependency injection](xref:fundamentals/dependency-injection).</span></span>
* <span data-ttu-id="9814e-120">轻型的[高性能](https://github.com/aspnet/benchmarks)模块化 HTTP 请求管道。</span><span class="sxs-lookup"><span data-stu-id="9814e-120">A lightweight, [high-performance](https://github.com/aspnet/benchmarks), and modular HTTP request pipeline.</span></span>
* <span data-ttu-id="9814e-121">能够在 [IIS](xref:host-and-deploy/iis/index)、[Nginx](xref:host-and-deploy/linux-nginx)、[Apache](xref:host-and-deploy/linux-apache)、[Docker](xref:host-and-deploy/docker/index) 上进行托管或在自己的进程中进行自托管。</span><span class="sxs-lookup"><span data-stu-id="9814e-121">Ability to host on [IIS](xref:host-and-deploy/iis/index), [Nginx](xref:host-and-deploy/linux-nginx), [Apache](xref:host-and-deploy/linux-apache), [Docker](xref:host-and-deploy/docker/index), or self-host in your own process.</span></span>
* <span data-ttu-id="9814e-122">定目标到 [.NET Core](https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server) 时，可以使用并行应用版本控制。</span><span class="sxs-lookup"><span data-stu-id="9814e-122">Side-by-side app versioning when targeting [.NET Core](https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server).</span></span>
* <span data-ttu-id="9814e-123">简化新式 Web 开发的工具。</span><span class="sxs-lookup"><span data-stu-id="9814e-123">Tooling that simplifies modern web development.</span></span>
* <span data-ttu-id="9814e-124">能够在 Windows、macOS 和 Linux 进行生成和运行。</span><span class="sxs-lookup"><span data-stu-id="9814e-124">Ability to build and run on Windows, macOS, and Linux.</span></span>
* <span data-ttu-id="9814e-125">开放源代码和[以社区为中心](https://live.asp.net/)。</span><span class="sxs-lookup"><span data-stu-id="9814e-125">Open-source and [community-focused](https://live.asp.net/).</span></span>

<span data-ttu-id="9814e-126">ASP.NET Core 完全作为 [NuGet](https://www.nuget.org/) 包的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="9814e-126">ASP.NET Core ships entirely as [NuGet](https://www.nuget.org/) packages.</span></span> <span data-ttu-id="9814e-127">这样一来，可以将应用优化为只包含必需 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="9814e-127">This allows you to optimize your app to include only the necessary NuGet packages.</span></span> <span data-ttu-id="9814e-128">实际上，定目标到 .NET Core 的 ASP.NET Core 2.x 应用只需要使用[一个 NuGet 包](xref:fundamentals/metapackage)。</span><span class="sxs-lookup"><span data-stu-id="9814e-128">In fact, ASP.NET Core 2.x apps targeting .NET Core only require a [single NuGet package](xref:fundamentals/metapackage).</span></span> <span data-ttu-id="9814e-129">较小的应用图面区域的优势包括：提升安全性、减少维护和提高性能。</span><span class="sxs-lookup"><span data-stu-id="9814e-129">The benefits of a smaller app surface area include tighter security, reduced servicing, and improved performance.</span></span>

## <a name="build-web-apis-and-web-ui-using-aspnet-core-mvc"></a><span data-ttu-id="9814e-130">使用 ASP.NET Core MVC 生成 Web API 和 Web UI</span><span class="sxs-lookup"><span data-stu-id="9814e-130">Build web APIs and web UI using ASP.NET Core MVC</span></span>

<span data-ttu-id="9814e-131">ASP.NET Core MVC 提供生成 [Web API](xref:tutorials/index#build-web-apis) 和 [Web 应用](xref:tutorials/index#build-web-apps)所需的功能：</span><span class="sxs-lookup"><span data-stu-id="9814e-131">ASP.NET Core MVC provides features to build [web APIs](xref:tutorials/index#build-web-apis) and [web apps](xref:tutorials/index#build-web-apps):</span></span>

* <span data-ttu-id="9814e-132">[Model-View-Controller (MVC) 模式](xref:mvc/overview) 使 Web API 和 Web 应用[可测试](testing/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9814e-132">The [Model-View-Controller (MVC) pattern](xref:mvc/overview) helps make your web APIs and web apps [testable](testing/index.md).</span></span>
* <span data-ttu-id="9814e-133">ASP.NET Core 2.0 中新增的 [Razor 页面](xref:mvc/razor-pages/index)是基于页面的编程模型，可简化 Web UI 生成并提高工作效率。</span><span class="sxs-lookup"><span data-stu-id="9814e-133">[Razor Pages](xref:mvc/razor-pages/index) (new in ASP.NET Core 2.0) is a page-based programming model that makes building web UI easier and more productive.</span></span>
* <span data-ttu-id="9814e-134">[Razor 标记](xref:mvc/views/razor)提供了适用于 [Razor 页面](xref:mvc/razor-pages/index)和 [MVC 视图](xref:mvc/views/overview)的高效语法。</span><span class="sxs-lookup"><span data-stu-id="9814e-134">[Razor markup](xref:mvc/views/razor) provides a productive syntax for [Razor Pages](xref:mvc/razor-pages/index) and [MVC views](xref:mvc/views/overview).</span></span>
* <span data-ttu-id="9814e-135">[标记帮助程序](xref:mvc/views/tag-helpers/intro)使服务器端代码可以在 Razor 文件中参与创建和呈现 HTML 元素。</span><span class="sxs-lookup"><span data-stu-id="9814e-135">[Tag Helpers](xref:mvc/views/tag-helpers/intro) enable server-side code to participate in creating and rendering HTML elements in Razor files.</span></span>
* <span data-ttu-id="9814e-136">内置的[多数据格式和内容协商](mvc/models/formatting.md)支持使 Web API 可访问多种客户端，包括浏览器和移动设备。</span><span class="sxs-lookup"><span data-stu-id="9814e-136">Built-in support for [multiple data formats and content negotiation](mvc/models/formatting.md) lets your web APIs reach a broad range of clients, including browsers and mobile devices.</span></span>
* <span data-ttu-id="9814e-137">[模型绑定](xref:mvc/models/model-binding)自动将 HTTP 请求中的数据映射到操作方法参数。</span><span class="sxs-lookup"><span data-stu-id="9814e-137">[Model binding](xref:mvc/models/model-binding) automatically maps data from HTTP requests to action method parameters.</span></span>
* <span data-ttu-id="9814e-138">[模型验证](xref:mvc/models/validation)自动执行客户端和服务器端验证。</span><span class="sxs-lookup"><span data-stu-id="9814e-138">[Model validation](xref:mvc/models/validation) automatically performs client- and server-side validation.</span></span>

## <a name="client-side-development"></a><span data-ttu-id="9814e-139">客户端开发</span><span class="sxs-lookup"><span data-stu-id="9814e-139">Client-side development</span></span>

<span data-ttu-id="9814e-140">ASP.NET Core 与常用客户端框架和库（包括 [Angular](xref:spa/angular)、[React](xref:spa/react) 和 [Bootstrap](xref:client-side/bootstrap)）无缝集成。</span><span class="sxs-lookup"><span data-stu-id="9814e-140">ASP.NET Core integrates seamlessly with popular client-side frameworks and libraries, including [Angular](xref:spa/angular), [React](xref:spa/react), and [Bootstrap](xref:client-side/bootstrap).</span></span> <span data-ttu-id="9814e-141">有关详细信息，请参阅[客户端开发](xref:client-side/index)。</span><span class="sxs-lookup"><span data-stu-id="9814e-141">See [Client-side development](xref:client-side/index) for more details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9814e-142">后续步骤</span><span class="sxs-lookup"><span data-stu-id="9814e-142">Next steps</span></span>

<span data-ttu-id="9814e-143">有关更多信息，请参见以下资源：</span><span class="sxs-lookup"><span data-stu-id="9814e-143">For more information, see the following resources:</span></span>

* [<span data-ttu-id="9814e-144">ASP.NET Core 教程</span><span class="sxs-lookup"><span data-stu-id="9814e-144">ASP.NET Core tutorials</span></span>](xref:tutorials/index)
* [<span data-ttu-id="9814e-145">ASP.NET Core 基础知识</span><span class="sxs-lookup"><span data-stu-id="9814e-145">ASP.NET Core fundamentals</span></span>](xref:fundamentals/index)
* <span data-ttu-id="9814e-146">[每周 ASP.NET Community Standup](https://live.asp.net/) 介绍了团队的工作进度和计划。</span><span class="sxs-lookup"><span data-stu-id="9814e-146">[The weekly ASP.NET community standup](https://live.asp.net/) covers the team's progress and plans.</span></span> <span data-ttu-id="9814e-147">它以新博客和第三方软件为重点。</span><span class="sxs-lookup"><span data-stu-id="9814e-147">It features new blogs and third-party software.</span></span>