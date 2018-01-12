---
title: "在 ASP.NET Core MVC 视图"
author: ardalis
description: "了解视图如何处理应用程序的数据表示和 ASP.NET 核心 MVC 中的用户交互。"
keywords: "ASP.NET 核心查看，MVC、 razor、 视图模型、 viewdata、 viewbag"
ms.author: riande
manager: wpickett
ms.date: 12/12/2017
ms.topic: article
ms.technology: aspnet
ms.prod: asp.net-core
uid: mvc/views/overview
ms.openlocfilehash: 2562d4e5fb85159e6ccb47990f54448ddc188077
ms.sourcegitcommit: 198fb0488e961048bfa376cf58cb853ef1d1cb91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2017
---
# <a name="views-in-aspnet-core-mvc"></a><span data-ttu-id="3ebfd-104">在 ASP.NET Core MVC 视图</span><span class="sxs-lookup"><span data-stu-id="3ebfd-104">Views in ASP.NET Core MVC</span></span>

<span data-ttu-id="3ebfd-105">通过[Steve Smith](https://ardalis.com/)和[Luke Latham](https://github.com/guardrex)</span><span class="sxs-lookup"><span data-stu-id="3ebfd-105">By [Steve Smith](https://ardalis.com/) and [Luke Latham](https://github.com/guardrex)</span></span>

<span data-ttu-id="3ebfd-106">本文档说明 ASP.NET 核心 MVC 应用程序中使用的视图。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-106">This document explains views used in ASP.NET Core MVC applications.</span></span> <span data-ttu-id="3ebfd-107">在 Razor 页上的信息，请参阅[简介 Razor 页](xref:mvc/razor-pages/index)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-107">For information on Razor Pages, see [Introduction to Razor Pages](xref:mvc/razor-pages/index).</span></span>

<span data-ttu-id="3ebfd-108">在**M**odel-**V**查看-**C**ontroller (MVC) 模式，*视图*处理应用程序的数据的演示文稿和用户交互。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-108">In the **M**odel-**V**iew-**C**ontroller (MVC) pattern, the *view* handles the app's data presentation and user interaction.</span></span> <span data-ttu-id="3ebfd-109">视图是 HTML 模板与嵌入[Razor 标记](xref:mvc/views/razor)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-109">A view is an HTML template with embedded [Razor markup](xref:mvc/views/razor).</span></span> <span data-ttu-id="3ebfd-110">Razor 标记是代码与 HTML 标记来生成一个发送到客户端的网页交互。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-110">Razor markup is code that interacts with HTML markup to produce a webpage that's sent to the client.</span></span>

<span data-ttu-id="3ebfd-111">ASP.NET 核心 mvc 视图是*.cshtml*文件使用[C# 编程语言](/dotnet/csharp/)Razor 标记中。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-111">In ASP.NET Core MVC, views are *.cshtml* files that use the [C# programming language](/dotnet/csharp/) in Razor markup.</span></span> <span data-ttu-id="3ebfd-112">通常情况下，查看文件会被分成文件夹为每个应用程序的名为[控制器](xref:mvc/controllers/actions)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-112">Usually, view files are grouped into folders named for each of the app's [controllers](xref:mvc/controllers/actions).</span></span> <span data-ttu-id="3ebfd-113">文件夹存储在*视图*根目录下的应用程序的文件夹：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-113">The folders are stored in a *Views* folder at the root of the app:</span></span>

![Visual Studio 解决方案资源管理器中的视图文件夹是使用主文件夹打开状态以显示 About.cshtml、 Contact.cshtml 和 Index.cshtml 文件打开](overview/_static/views_solution_explorer.png)

<span data-ttu-id="3ebfd-115">*主页*控制器由*主页*内的文件夹*视图*文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-115">The *Home* controller is represented by a *Home* folder inside the *Views* folder.</span></span> <span data-ttu-id="3ebfd-116">*主页*文件夹包含的视图*有关*，*联系人*，和*索引*（主页） 网页。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-116">The *Home* folder contains the views for the *About*, *Contact*, and *Index* (homepage) webpages.</span></span> <span data-ttu-id="3ebfd-117">当用户请求这些三个网页中的控制器操作之一*主页*控制器确定的三个视图用于生成并返回给用户的网页。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-117">When a user requests one of these three webpages, controller actions in the *Home* controller determine which of the three views is used to build and return a webpage to the user.</span></span>

<span data-ttu-id="3ebfd-118">使用[布局](xref:mvc/views/layout)提供一致的网页部分和减少代码重复。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-118">Use [layouts](xref:mvc/views/layout) to provide consistent webpage sections and reduce code repetition.</span></span> <span data-ttu-id="3ebfd-119">布局通常包含标头、 导航和菜单元素和页脚。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-119">Layouts often contain the header, navigation and menu elements, and the footer.</span></span> <span data-ttu-id="3ebfd-120">页眉和页脚通常包含多个元数据元素和链接到脚本和样式资产的样本标记。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-120">The header and footer usually contain boilerplate markup for many metadata elements and links to script and style assets.</span></span> <span data-ttu-id="3ebfd-121">布局帮助你避免在你的视图中此样本标记。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-121">Layouts help you avoid this boilerplate markup in your views.</span></span>

<span data-ttu-id="3ebfd-122">[分部视图](xref:mvc/views/partial)减少由管理视图的可重用部件的代码的重复。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-122">[Partial views](xref:mvc/views/partial) reduce code duplication by managing reusable parts of views.</span></span> <span data-ttu-id="3ebfd-123">例如，分部视图可用于在多个视图将显示博客网站上作者个人简介。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-123">For example, a partial view is useful for an author biography on a blog website that appears in several views.</span></span> <span data-ttu-id="3ebfd-124">作者个人简介是普通视图内容，不要求代码以执行以便生成的网页内容。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-124">An author biography is ordinary view content and doesn't require code to execute in order to produce the content for the webpage.</span></span> <span data-ttu-id="3ebfd-125">作者个人简介内容是内容的可用于按模型绑定单独出现时，查看，因此使用了分部视图适用于此类型是内容的理想之选。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-125">Author biography content is available to the view by model binding alone, so using a partial view for this type of content is ideal.</span></span>

<span data-ttu-id="3ebfd-126">[查看组件](xref:mvc/views/view-components)是类似于分部视图，因为它们允许您以减少重复代码，但它们适用于需要的代码来呈现网页以便在服务器上运行的视图内容。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-126">[View components](xref:mvc/views/view-components) are similar to partial views in that they allow you to reduce repetitive code, but they're appropriate for view content that requires code to run on the server in order to render the webpage.</span></span> <span data-ttu-id="3ebfd-127">在所呈现的内容需要数据库交互，如购物车网站时，视图组件是有用的。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-127">View components are useful when the rendered content requires database interaction, such as for a website shopping cart.</span></span> <span data-ttu-id="3ebfd-128">查看组件不限制为模型绑定，以便生成网页输出。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-128">View components aren't limited to model binding in order to produce webpage output.</span></span>

## <a name="benefits-of-using-views"></a><span data-ttu-id="3ebfd-129">使用视图的好处</span><span class="sxs-lookup"><span data-stu-id="3ebfd-129">Benefits of using views</span></span>

<span data-ttu-id="3ebfd-130">视图可帮助建立[ **S**eparation **o**f **C**oncerns (SoC) 设计](http://deviq.com/separation-of-concerns/)隔开的用户界面标记的 MVC 应用程序中应用程序的其他部分。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-130">Views help to establish a [**S**eparation **o**f **C**oncerns (SoC) design](http://deviq.com/separation-of-concerns/) within an MVC app by separating the user interface markup from other parts of the app.</span></span> <span data-ttu-id="3ebfd-131">以下 SoC 设计可让你的应用程序模块化，提供以下几个好处：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-131">Following SoC design makes your app modular, which provides several benefits:</span></span>

* <span data-ttu-id="3ebfd-132">应用程序更容易维护，因为它被更好地组织。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-132">The app is easier to maintain because it's better organized.</span></span> <span data-ttu-id="3ebfd-133">视图通常由应用程序功能分组。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-133">Views are generally grouped by app feature.</span></span> <span data-ttu-id="3ebfd-134">这使得更轻松地找到相关的视图，在功能上工作时。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-134">This makes it easier to find related views when working on a feature.</span></span>
* <span data-ttu-id="3ebfd-135">松散耦合的应用程序的部分。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-135">The parts of the app are loosely coupled.</span></span> <span data-ttu-id="3ebfd-136">你可以生成和更新单独从业务逻辑和数据访问组件的应用程序的视图。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-136">You can build and update the app's views separately from the business logic and data access components.</span></span> <span data-ttu-id="3ebfd-137">无需具有更新的应用程序其他部分，你可以修改应用程序的视图。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-137">You can modify the views of the app without necessarily having to update other parts of the app.</span></span>
* <span data-ttu-id="3ebfd-138">很容易地测试应用程序的用户界面部分，因为视图的单独单位。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-138">It's easier to test the user interface parts of the app because the views are separate units.</span></span>
* <span data-ttu-id="3ebfd-139">由于更好地组织，它是不太可能将用户界面的意外重复部分。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-139">Due to better organization, it's less likely that you'll accidently repeat sections of the user interface.</span></span>

## <a name="creating-a-view"></a><span data-ttu-id="3ebfd-140">创建视图</span><span class="sxs-lookup"><span data-stu-id="3ebfd-140">Creating a view</span></span>

<span data-ttu-id="3ebfd-141">特定于控制器的视图中创建*视图 / [ControllerName]*文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-141">Views that are specific to a controller are created in the *Views/[ControllerName]* folder.</span></span> <span data-ttu-id="3ebfd-142">控制器之间共享的视图都将置于*视图/共享*文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-142">Views that are shared among controllers are placed in the *Views/Shared* folder.</span></span> <span data-ttu-id="3ebfd-143">若要创建一个视图，添加新文件，并为其提供其关联的控制器操作具有相同的名称*.cshtml*文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-143">To create a view, add a new file and give it the same name as its associated controller action with the *.cshtml* file extension.</span></span> <span data-ttu-id="3ebfd-144">若要创建与对应的视图*有关*中的操作*主页*控制器，创建*About.cshtml*文件中*视图/主页*文件夹：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-144">To create a view that corresponds with the *About* action in the *Home* controller, create an *About.cshtml* file in the *Views/Home* folder:</span></span>

[!code-cshtml[Main](../../common/samples/WebApplication1/Views/Home/About.cshtml)]

<span data-ttu-id="3ebfd-145">*Razor*标记开头`@`符号。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-145">*Razor* markup starts with the `@` symbol.</span></span> <span data-ttu-id="3ebfd-146">运行的 C# 语句通过将 C# 中的代码[Razor 代码块](xref:mvc/views/razor#razor-code-blocks)设置 off，大括号内 (`{ ... }`)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-146">Run C# statements by placing C# code within [Razor code blocks](xref:mvc/views/razor#razor-code-blocks) set off by curly braces (`{ ... }`).</span></span> <span data-ttu-id="3ebfd-147">有关示例，请参阅"关于"分配到`ViewData["Title"]`上面所示。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-147">For example, see the assignment of "About" to `ViewData["Title"]` shown above.</span></span> <span data-ttu-id="3ebfd-148">您可以通过只需使用引用值显示在 HTML 内的值`@`符号。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-148">You can display values within HTML by simply referencing the value with the `@` symbol.</span></span> <span data-ttu-id="3ebfd-149">看到的内容`<h2>`和`<h3>`上面的元素。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-149">See the contents of the `<h2>` and `<h3>` elements above.</span></span>

<span data-ttu-id="3ebfd-150">上面所示视图内容是仅向用户呈现的整个网页的一部分。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-150">The view content shown above is only part of the entire webpage that's rendered to the user.</span></span> <span data-ttu-id="3ebfd-151">其他视图文件中指定的页面的布局的其余部分和视图的其他常见方面。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-151">The rest of the page's layout and other common aspects of the view are specified in other view files.</span></span> <span data-ttu-id="3ebfd-152">若要了解详细信息，请参阅[布局主题](xref:mvc/views/layout)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-152">To learn more, see the [Layout topic](xref:mvc/views/layout).</span></span>

## <a name="how-controllers-specify-views"></a><span data-ttu-id="3ebfd-153">控制器如何指定视图</span><span class="sxs-lookup"><span data-stu-id="3ebfd-153">How controllers specify views</span></span>

<span data-ttu-id="3ebfd-154">视图通常从之类的操作返回[ViewResult](/aspnet/core/api/microsoft.aspnetcore.mvc.viewresult)，这是一种[ActionResult](/aspnet/core/api/microsoft.aspnetcore.mvc.actionresult)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-154">Views are typically returned from actions as a [ViewResult](/aspnet/core/api/microsoft.aspnetcore.mvc.viewresult), which is a type of [ActionResult](/aspnet/core/api/microsoft.aspnetcore.mvc.actionresult).</span></span> <span data-ttu-id="3ebfd-155">操作方法可以创建并返回`ViewResult`直接，但此通常未完成。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-155">Your action method can create and return a `ViewResult` directly, but that isn't commonly done.</span></span> <span data-ttu-id="3ebfd-156">由于大多数控制器继承[控制器](/aspnet/core/api/microsoft.aspnetcore.mvc.controller)，只需使用`View`helper 方法，以返回`ViewResult`:</span><span class="sxs-lookup"><span data-stu-id="3ebfd-156">Since most controllers inherit from [Controller](/aspnet/core/api/microsoft.aspnetcore.mvc.controller), you simply use the `View` helper method to return the `ViewResult`:</span></span>

<span data-ttu-id="3ebfd-157">*HomeController.cs*</span><span class="sxs-lookup"><span data-stu-id="3ebfd-157">*HomeController.cs*</span></span>

[!code-csharp[Main](../../common/samples/WebApplication1/Controllers/HomeController.cs?highlight=5&range=16-21)]

<span data-ttu-id="3ebfd-158">在此操作返回时， *About.cshtml*视图中的最后一节所示呈现为以下网页：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-158">When this action returns, the *About.cshtml* view shown in the last section is rendered as the following webpage:</span></span>

![有关在 Edge 浏览器中呈现的页面](overview/_static/about-page.png)

<span data-ttu-id="3ebfd-160">`View`帮助器方法具有好几个重载。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-160">The `View` helper method has several overloads.</span></span> <span data-ttu-id="3ebfd-161">你可以选择指定：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-161">You can optionally specify:</span></span>

* <span data-ttu-id="3ebfd-162">返回一个显式视图：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-162">An explicit view to return:</span></span>

  ```csharp
  return View("Orders");
  ```
* <span data-ttu-id="3ebfd-163">A[模型](xref:mvc/models/model-binding)要传递给视图：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-163">A [model](xref:mvc/models/model-binding) to pass to the the view:</span></span>

  ```csharp
  return View(Orders);
  ```
* <span data-ttu-id="3ebfd-164">视图和模型：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-164">Both a view and a model:</span></span>

  ```csharp
  return View("Orders", Orders);
  ```

### <a name="view-discovery"></a><span data-ttu-id="3ebfd-165">视图发现</span><span class="sxs-lookup"><span data-stu-id="3ebfd-165">View discovery</span></span>

<span data-ttu-id="3ebfd-166">当操作返回的视图时，捗个称*视图发现*发生。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-166">When an action returns a view, a process called *view discovery* takes place.</span></span> <span data-ttu-id="3ebfd-167">此过程确定哪些视图文件使用基于视图名称。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-167">This process determines which view file is used based on the view name.</span></span> 

<span data-ttu-id="3ebfd-168">默认行为`View`方法 (`return View();`) 是返回具有与从中调用它的操作方法相同的名称的视图。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-168">The default behavior of the `View` method (`return View();`) is to return a view with the same name as the action method from which it's called.</span></span> <span data-ttu-id="3ebfd-169">例如，*有关*`ActionResult`控制器的方法名称用于搜索名为的视图文件*About.cshtml*。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-169">For example, the *About* `ActionResult` method name of the controller is used to search for a view file named *About.cshtml*.</span></span> <span data-ttu-id="3ebfd-170">首先，运行时查看*视图 / [ControllerName]*视图的文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-170">First, the runtime looks in the *Views/[ControllerName]* folder for the view.</span></span> <span data-ttu-id="3ebfd-171">如果找不到匹配的视图存在，它将搜索*共享*视图的文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-171">If it doesn't find a matching view there, it searches the *Shared* folder for the view.</span></span>

<span data-ttu-id="3ebfd-172">它并不重要如果隐式返回`ViewResult`与`return View();`或显式传递到的视图名称`View`方法替换`return View("<ViewName>");`。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-172">It doesn't matter if you implicitly return the `ViewResult` with `return View();` or explicitly pass the view name to the `View` method with `return View("<ViewName>");`.</span></span> <span data-ttu-id="3ebfd-173">在这两种情况下，查看发现搜索匹配的视图文件顺序如下：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-173">In both cases, view discovery searches for a matching view file in this order:</span></span>

   1. <span data-ttu-id="3ebfd-174">*视图 /\[ControllerName]\[ViewName].cshtml*</span><span class="sxs-lookup"><span data-stu-id="3ebfd-174">*Views/\[ControllerName]\[ViewName].cshtml*</span></span>
   1. <span data-ttu-id="3ebfd-175">*视图/共享/\[ViewName].cshtml*</span><span class="sxs-lookup"><span data-stu-id="3ebfd-175">*Views/Shared/\[ViewName].cshtml*</span></span>

<span data-ttu-id="3ebfd-176">视图文件路径可以提供而不是视图名称。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-176">A view file path can be provided instead of a view name.</span></span> <span data-ttu-id="3ebfd-177">如果使用从应用程序根目录开始的绝对路径 (根据需要第一页为"/"或"~ /")，则*.cshtml*必须指定扩展：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-177">If using an absolute path starting at the app root (optionally starting with "/" or "~/"), the *.cshtml* extension must be specified:</span></span>

```csharp
return View("Views/Home/About.cshtml");
```

<span data-ttu-id="3ebfd-178">你可以使用相对路径以在不同的目录，而无需指定视图*.cshtml*扩展。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-178">You can also use a relative path to specify views in different directories without the *.cshtml* extension.</span></span> <span data-ttu-id="3ebfd-179">内部`HomeController`，你可以返回*索引*视图你*管理*具有相对路径的视图：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-179">Inside the `HomeController`, you can return the *Index* view of your *Manage* views with a relative path:</span></span>

```csharp
return View("../Manage/Index");
```

<span data-ttu-id="3ebfd-180">同样，你可以指示与当前的特定于控制器的目录"。 /"前缀：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-180">Similarly, you can indicate the current controller-specific directory with the "./" prefix:</span></span>

```csharp
return View("./About");
```

<span data-ttu-id="3ebfd-181">[分部视图](xref:mvc/views/partial)和[查看组件](xref:mvc/views/view-components)使用类似的 （但不是完全相同的） 发现机制。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-181">[Partial views](xref:mvc/views/partial) and [view components](xref:mvc/views/view-components) use similar (but not identical) discovery mechanisms.</span></span>

<span data-ttu-id="3ebfd-182">你可以自定义视图如何使用自定义是位于应用程序的默认约定[IViewLocationExpander](/aspnet/core/api/microsoft.aspnetcore.mvc.razor.iviewlocationexpander)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-182">You can customize the default convention for how views are located within the app by using a custom [IViewLocationExpander](/aspnet/core/api/microsoft.aspnetcore.mvc.razor.iviewlocationexpander).</span></span>

<span data-ttu-id="3ebfd-183">视图发现依赖于按文件名称查找查看文件。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-183">View discovery relies on finding view files by file name.</span></span> <span data-ttu-id="3ebfd-184">如果基础的文件系统是区分大小写，视图名称是可能区分大小写。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-184">If the underlying file system is case sensitive, view names are probably case sensitive.</span></span> <span data-ttu-id="3ebfd-185">对于跨操作系统的兼容性，与匹配用例之间控制器和操作名称和关联的视图文件夹和文件名称。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-185">For compatibility across operating systems, match case between controller and action names and associated view folders and file names.</span></span> <span data-ttu-id="3ebfd-186">如果你遇到的错误，在使用区分大小写的文件系统时找不到视图文件，确认所请求的视图文件和实际视图文件名称之间与匹配大小写。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-186">If you encounter an error that a view file can't be found while working with a case-sensitive file system, confirm that the casing matches between the requested view file and the actual view file name.</span></span>

<span data-ttu-id="3ebfd-187">遵循组织您的视图以反映控制器、 操作和可维护性和清晰性的视图之间的关系的文件结构的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-187">Follow the best practice of organizing the file structure for your views to reflect the relationships among controllers, actions, and views for maintainability and clarity.</span></span>

## <a name="passing-data-to-views"></a><span data-ttu-id="3ebfd-188">将数据传递到视图</span><span class="sxs-lookup"><span data-stu-id="3ebfd-188">Passing data to views</span></span>

<span data-ttu-id="3ebfd-189">可以将数据传递给使用几种方法的视图。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-189">You can pass data to views using several approaches.</span></span> <span data-ttu-id="3ebfd-190">最可靠方法是指定[模型](xref:mvc/models/model-binding)视图中的类型。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-190">The most robust approach is to specify a [model](xref:mvc/models/model-binding) type in the view.</span></span> <span data-ttu-id="3ebfd-191">此模型通常称为*viewmodel*。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-191">This model is commonly referred to as a *viewmodel*.</span></span> <span data-ttu-id="3ebfd-192">从操作可将视图模型类型的实例传递到视图中。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-192">You pass an instance of the viewmodel type to the view from the action.</span></span>

<span data-ttu-id="3ebfd-193">视图模型用于将数据传递给视图允许视图以充分利用*强*类型检查。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-193">Using a viewmodel to pass data to a view allows the view to take advantage of *strong* type checking.</span></span> <span data-ttu-id="3ebfd-194">*强类型化*(或*强类型*) 意味着每个变量和常量具有显式定义的类型 (例如， `string`， `int`，或`DateTime`)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-194">*Strong typing* (or *strongly-typed*) means that every variable and constant has an explicitly defined type (for example, `string`, `int`, or `DateTime`).</span></span> <span data-ttu-id="3ebfd-195">在编译时被检查的类型视图中使用的有效性。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-195">The validity of types used in a view is checked at compile time.</span></span>

<span data-ttu-id="3ebfd-196">[Visual Studio](https://www.visualstudio.com/vs/)和[Visual Studio Code](https://code.visualstudio.com/)列表使用一种称为功能的强类型类成员[IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-196">[Visual Studio](https://www.visualstudio.com/vs/) and [Visual Studio Code](https://code.visualstudio.com/) list strongly-typed class members using a feature called [IntelliSense](/visualstudio/ide/using-intellisense).</span></span> <span data-ttu-id="3ebfd-197">当你想要查看的视图模型属性时，键入后跟句号 viewmodel 的变量名称 (`.`)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-197">When you want to see the properties of a viewmodel, type the variable name for the viewmodel followed by a period (`.`).</span></span> <span data-ttu-id="3ebfd-198">这有助于更快地编写代码错误较少。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-198">This helps you write code faster with fewer errors.</span></span>

<span data-ttu-id="3ebfd-199">指定模型使用`@model`指令。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-199">Specify a model using the `@model` directive.</span></span> <span data-ttu-id="3ebfd-200">使用与模型`@Model`:</span><span class="sxs-lookup"><span data-stu-id="3ebfd-200">Use the model with `@Model`:</span></span>

```cshtml
@model WebApplication1.ViewModels.Address

<h2>Contact</h2>
<address>
    @Model.Street<br>
    @Model.City, @Model.State @Model.PostalCode<br>
    <abbr title="Phone">P:</abbr> 425.555.0100
</address>
```

<span data-ttu-id="3ebfd-201">若要提供到视图模型，控制器将其传递作为参数：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-201">To provide the model to the view, the controller passes it as a parameter:</span></span>

```csharp
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";

    var viewModel = new Address()
    {
        Name = "Microsoft",
        Street = "One Microsoft Way",
        City = "Redmond",
        State = "WA",
        PostalCode = "98052-6399"
    };

    return View(viewModel);
}
```

<span data-ttu-id="3ebfd-202">可以提供到视图的模型类型没有限制。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-202">There are no restrictions on the model types that you can provide to a view.</span></span> <span data-ttu-id="3ebfd-203">我们建议使用**P**词条**O**ld **C**LR **O**对象 (POCO) viewmodel 与很少或没有定义的行为 （方法）。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-203">We recommend using **P**lain **O**ld **C**LR **O**bject (POCO) viewmodels with little or no behavior (methods) defined.</span></span> <span data-ttu-id="3ebfd-204">通常，viewmodel 类既存储在*模型*文件夹或单独*Viewmodel*根目录下的应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-204">Usually, viewmodel classes are either stored in the *Models* folder or a separate *ViewModels* folder at the root of the app.</span></span> <span data-ttu-id="3ebfd-205">*地址*viewmodel 使用在上面的示例是存储在名为的文件 POCO viewmodel *Address.cs*:</span><span class="sxs-lookup"><span data-stu-id="3ebfd-205">The *Address* viewmodel used in the example above is a POCO viewmodel stored in a file named *Address.cs*:</span></span>

```csharp
namespace WebApplication1.ViewModels
{
    public class Address
    {
        public string Name { get; set; }
        public string Street { get; set; }
        public string City { get; set; }
        public string State { get; set; }
        public string PostalCode { get; set; }
    }
}
```

> [!NOTE]
> <span data-ttu-id="3ebfd-206">你可以随意使用相同的类进行 viewmodel 类型和你的业务模型类型。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-206">Nothing prevents you from using the same classes for both your viewmodel types and your business model types.</span></span> <span data-ttu-id="3ebfd-207">但是，使用单独的模型允许您的视图以独立变化的业务逻辑和数据从应用的访问部分。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-207">However, using separate models allows your views to vary independently from the business logic and data access parts of your app.</span></span> <span data-ttu-id="3ebfd-208">分隔的模型和 viewmodel 还提供了安全好处时模型使用[模型绑定](xref:mvc/models/model-binding)和[验证](xref:mvc/models/validation)用户发送到应用的数据。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-208">Separation of models and viewmodels also offers security benefits when models use [model binding](xref:mvc/models/model-binding) and [validation](xref:mvc/models/validation) for data sent to the app by the user.</span></span>


<a name="VD_VB"></a>

### <a name="weakly-typed-data-viewdata-and-viewbag"></a><span data-ttu-id="3ebfd-209">弱类型化数据 （ViewData 和 ViewBag）</span><span class="sxs-lookup"><span data-stu-id="3ebfd-209">Weakly-typed data (ViewData and ViewBag)</span></span>

<span data-ttu-id="3ebfd-210">注意：`ViewBag`在 Razor 页中不可用。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-210">Note: `ViewBag` is not available in the Razor Pages.</span></span>

<span data-ttu-id="3ebfd-211">除了强类型化的视图，视图还可以访问*弱类型*(也称为*松散类型化*) 的数据集合。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-211">In addition to strongly-typed views, views have access to a *weakly-typed* (also called *loosely-typed*) collection of data.</span></span> <span data-ttu-id="3ebfd-212">与强类型不同*弱类型*(或*松散类型*) 意味着你不显式声明要使用的数据类型。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-212">Unlike strong types, *weak types* (or *loose types*) means that you don't explicitly declare the type of data you're using.</span></span> <span data-ttu-id="3ebfd-213">用于传递少量入和移出控制器和视图的数据，可以使用弱类型化数据的集合。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-213">You can use the collection of weakly-typed data for passing small amounts of data in and out of controllers and views.</span></span>

| <span data-ttu-id="3ebfd-214">将之间的数据传递...</span><span class="sxs-lookup"><span data-stu-id="3ebfd-214">Passing data between a ...</span></span>                        | <span data-ttu-id="3ebfd-215">示例</span><span class="sxs-lookup"><span data-stu-id="3ebfd-215">Example</span></span>                                                                        |
| ------------------------------------------------- | ------------------------------------------------------------------------------ |
| <span data-ttu-id="3ebfd-216">控制器和视图</span><span class="sxs-lookup"><span data-stu-id="3ebfd-216">Controller and a view</span></span>                             | <span data-ttu-id="3ebfd-217">填充数据的下拉列表。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-217">Populating a dropdown list with data.</span></span>                                          |
| <span data-ttu-id="3ebfd-218">视图和[布局视图](xref:mvc/views/layout)</span><span class="sxs-lookup"><span data-stu-id="3ebfd-218">View and a [layout view](xref:mvc/views/layout)</span></span>   | <span data-ttu-id="3ebfd-219">设置**\<标题 >**视图文件中的布局视图中的元素内容。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-219">Setting the **\<title>** element content in the layout view from a view file.</span></span>  |
| <span data-ttu-id="3ebfd-220">[分部视图](xref:mvc/views/partial)和视图</span><span class="sxs-lookup"><span data-stu-id="3ebfd-220">[Partial view](xref:mvc/views/partial) and a view</span></span> | <span data-ttu-id="3ebfd-221">会根据用户请求的网页显示数据的小组件。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-221">A widget that displays data based on the webpage that the user requested.</span></span>      |

<span data-ttu-id="3ebfd-222">此集合可以通过引用`ViewData`或`ViewBag`控制器和视图上的属性。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-222">This collection can be referenced through either the `ViewData` or `ViewBag` properties on controllers and views.</span></span> <span data-ttu-id="3ebfd-223">`ViewData`属性是弱类型化对象的字典。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-223">The `ViewData` property is a dictionary of weakly-typed objects.</span></span> <span data-ttu-id="3ebfd-224">`ViewBag`属性是周围的包装器`ViewData`为基础提供动态属性`ViewData`集合。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-224">The `ViewBag` property is a wrapper around `ViewData` that provides dynamic properties for the underlying `ViewData` collection.</span></span>

<span data-ttu-id="3ebfd-225">`ViewData`和`ViewBag`动态解析在运行时。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-225">`ViewData` and `ViewBag` are dynamically resolved at runtime.</span></span> <span data-ttu-id="3ebfd-226">因为它们未提供编译时类型检查，两者都通常更容易出错比使用视图模型。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-226">Since they don't offer compile-time type checking, both are generally more error-prone than using a viewmodel.</span></span> <span data-ttu-id="3ebfd-227">出于上述原因，一些开发人员更愿意按最小方式或从不使用`ViewData`和`ViewBag`。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-227">For that reason, some developers prefer to minimally or never use `ViewData` and `ViewBag`.</span></span>


<a name="VD"></a>

<span data-ttu-id="3ebfd-228">**ViewData**</span><span class="sxs-lookup"><span data-stu-id="3ebfd-228">**ViewData**</span></span>

<span data-ttu-id="3ebfd-229">`ViewData`是[ViewDataDictionary](/aspnet/core/api/microsoft.aspnetcore.mvc.viewfeatures.viewdatadictionary)通过访问的对象`string`密钥。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-229">`ViewData` is a [ViewDataDictionary](/aspnet/core/api/microsoft.aspnetcore.mvc.viewfeatures.viewdatadictionary) object accessed through `string` keys.</span></span> <span data-ttu-id="3ebfd-230">字符串数据可以存储和使用直接而无需强制转换，但您必须将其他转换`ViewData`对象时将其提取到特定类型的值。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-230">String data can be stored and used directly without the need for a cast, but you must cast other `ViewData` object values to specific types when you extract them.</span></span> <span data-ttu-id="3ebfd-231">你可以使用`ViewData`若要将数据从控制器传递到视图并在视图内，包括[分部视图](xref:mvc/views/partial)和[布局](xref:mvc/views/layout)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-231">You can use `ViewData` to pass data from controllers to views and within views, including [partial views](xref:mvc/views/partial) and [layouts](xref:mvc/views/layout).</span></span>

<span data-ttu-id="3ebfd-232">以下是设置问候语和地址使用的值的示例`ViewData`中某项操作：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-232">The following is an example that sets values for a greeting and an address using `ViewData` in an action:</span></span>

```csharp
public IActionResult SomeAction()
{
    ViewData["Greeting"] = "Hello";
    ViewData["Address"]  = new Address()
    {
        Name = "Steve",
        Street = "123 Main St",
        City = "Hudson",
        State = "OH",
        PostalCode = "44236"
    };

    return View();
}
```

<span data-ttu-id="3ebfd-233">处理在视图中的数据：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-233">Work with the data in a view:</span></span>

```cshtml
@{
    // Since Address isn't a string, it requires a cast.
    var address = ViewData["Address"] as Address;
}

@ViewData["Greeting"] World!

<address>
    @address.Name<br>
    @address.Street<br>
    @address.City, @address.State @address.PostalCode
</address>
```

<span data-ttu-id="3ebfd-234">**ViewBag**</span><span class="sxs-lookup"><span data-stu-id="3ebfd-234">**ViewBag**</span></span>

<span data-ttu-id="3ebfd-235">注意：`ViewBag`在 Razor 页中不可用。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-235">Note: `ViewBag` is not available in the Razor Pages.</span></span>

<span data-ttu-id="3ebfd-236">`ViewBag`是[DynamicViewData](/aspnet/core/api/microsoft.aspnetcore.mvc.viewfeatures.internal.dynamicviewdata)对象，它提供对存储在对象的动态访问`ViewData`。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-236">`ViewBag` is a [DynamicViewData](/aspnet/core/api/microsoft.aspnetcore.mvc.viewfeatures.internal.dynamicviewdata) object that provides dynamic access to the objects stored in `ViewData`.</span></span> <span data-ttu-id="3ebfd-237">`ViewBag`可以更便捷地使用，因为它不需要强制转换。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-237">`ViewBag` can be more convenient to work with, since it doesn't require casting.</span></span> <span data-ttu-id="3ebfd-238">下面的示例演示如何使用`ViewBag`与使用相同的结果与`ViewData`上面：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-238">The following example shows how to use `ViewBag` with the same result as using `ViewData` above:</span></span>

```csharp
public IActionResult SomeAction()
{
    ViewBag.Greeting = "Hello";
    ViewBag.Address  = new Address()
    {
        Name = "Steve",
        Street = "123 Main St",
        City = "Hudson",
        State = "OH",
        PostalCode = "44236"
    };

    return View();
}
```

```cshtml
@ViewBag.Greeting World!

<address>
    @ViewBag.Address.Name<br>
    @ViewBag.Address.Street<br>
    @ViewBag.Address.City, @ViewBag.Address.State @ViewBag.Address.PostalCode
</address>
```

<span data-ttu-id="3ebfd-239">**同时使用 ViewData 和 ViewBag**</span><span class="sxs-lookup"><span data-stu-id="3ebfd-239">**Using ViewData and ViewBag simultaneously**</span></span>

<span data-ttu-id="3ebfd-240">注意：`ViewBag`在 Razor 页中不可用。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-240">Note: `ViewBag` is not available in the Razor Pages.</span></span>

<span data-ttu-id="3ebfd-241">由于`ViewData`和`ViewBag`引用相同的基础`ViewData`集合，你可以同时使用`ViewData`和`ViewBag`和混合和匹配它们时读取和写入值之间。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-241">Since `ViewData` and `ViewBag` refer to the same underlying `ViewData` collection, you can use both `ViewData` and `ViewBag` and mix and match between them when reading and writing values.</span></span>

<span data-ttu-id="3ebfd-242">设置标题使用`ViewBag`和说明使用`ViewData`顶部*About.cshtml*视图：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-242">Set the title using `ViewBag` and the description using `ViewData` at the top of an *About.cshtml* view:</span></span>

```cshtml
@{
    Layout = "/Views/Shared/_Layout.cshtml";
    ViewBag.Title = "About Contoso";
    ViewData["Description"] = "Let us tell you about Contoso's philosophy and mission.";
}
```

<span data-ttu-id="3ebfd-243">读取的属性，但反向使用`ViewData`和`ViewBag`。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-243">Read the properties but reverse the use of `ViewData` and `ViewBag`.</span></span> <span data-ttu-id="3ebfd-244">在*_Layout.cshtml*文件中，获取标题使用`ViewData`并获取说明使用`ViewBag`:</span><span class="sxs-lookup"><span data-stu-id="3ebfd-244">In the *_Layout.cshtml* file, obtain the title using `ViewData` and obtain the description using `ViewBag`:</span></span>

```cshtml
<!DOCTYPE html>
<html lang="en">
<head>
    <title>@ViewData["Title"]</title>
    <meta name="description" content="@ViewBag.Description">
    ...
```

<span data-ttu-id="3ebfd-245">请记住字符串不需要强制转换为`ViewData`。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-245">Remember that strings don't require a cast for `ViewData`.</span></span> <span data-ttu-id="3ebfd-246">你可以使用`@ViewData["Title"]`而不需要转换。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-246">You can use `@ViewData["Title"]` without casting.</span></span>

<span data-ttu-id="3ebfd-247">同时使用`ViewData`和`ViewBag`在同一时间工作原理，作为执行混合和匹配读取和写入属性。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-247">Using both `ViewData` and `ViewBag` at the same time works, as does mixing and matching reading and writing the properties.</span></span> <span data-ttu-id="3ebfd-248">在呈现的以下标记：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-248">The following markup is rendered:</span></span>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>About Contoso</title>
    <meta name="description" content="Let us tell you about Contoso's philosophy and mission.">
    ...
```

<span data-ttu-id="3ebfd-249">**ViewData 和 ViewBag 之间的差异的摘要**</span><span class="sxs-lookup"><span data-stu-id="3ebfd-249">**Summary of the differences between ViewData and ViewBag**</span></span>

 <span data-ttu-id="3ebfd-250">`ViewBag`不是 Razor 页中可用的。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-250">`ViewBag` is not available in the Razor Pages.</span></span>

* `ViewData`
  * <span data-ttu-id="3ebfd-251">派生自[ViewDataDictionary](/aspnet/core/api/microsoft.aspnetcore.mvc.viewfeatures.viewdatadictionary)，因此它有可能有用，如字典属性`ContainsKey`， `Add`， `Remove`，和`Clear`。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-251">Derives from [ViewDataDictionary](/aspnet/core/api/microsoft.aspnetcore.mvc.viewfeatures.viewdatadictionary), so it has dictionary properties that can be useful, such as `ContainsKey`, `Add`, `Remove`, and `Clear`.</span></span>
  * <span data-ttu-id="3ebfd-252">字典中的键是字符串，因此允许有空白。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-252">Keys in the dictionary are strings, so whitespace is allowed.</span></span> <span data-ttu-id="3ebfd-253">示例：`ViewData["Some Key With Whitespace"]`</span><span class="sxs-lookup"><span data-stu-id="3ebfd-253">Example: `ViewData["Some Key With Whitespace"]`</span></span>
  * <span data-ttu-id="3ebfd-254">以外的任何类型`string`必须强制转换在要使用的视图`ViewData`。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-254">Any type other than a `string` must be cast in the view to use `ViewData`.</span></span>
* `ViewBag`
  * <span data-ttu-id="3ebfd-255">派生自[DynamicViewData](/aspnet/core/api/microsoft.aspnetcore.mvc.viewfeatures.internal.dynamicviewdata)，因此它允许使用点表示法的动态属性创建 (`@ViewBag.SomeKey = <value or object>`)，并没有强制转换是必需的。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-255">Derives from [DynamicViewData](/aspnet/core/api/microsoft.aspnetcore.mvc.viewfeatures.internal.dynamicviewdata), so it allows the creation of dynamic properties using dot notation (`@ViewBag.SomeKey = <value or object>`), and no casting is required.</span></span> <span data-ttu-id="3ebfd-256">语法`ViewBag`得更加快速地将添加到控制器和视图。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-256">The syntax of `ViewBag` makes it quicker to add to controllers and views.</span></span>
  * <span data-ttu-id="3ebfd-257">易于检查 null 值。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-257">Simpler to check for null values.</span></span> <span data-ttu-id="3ebfd-258">示例：`@ViewBag.Person?.Name`</span><span class="sxs-lookup"><span data-stu-id="3ebfd-258">Example: `@ViewBag.Person?.Name`</span></span>

<span data-ttu-id="3ebfd-259">**何时使用 ViewData 或 ViewBag**</span><span class="sxs-lookup"><span data-stu-id="3ebfd-259">**When to use ViewData or ViewBag**</span></span>

<span data-ttu-id="3ebfd-260">同时`ViewData`和`ViewBag`有同样传递数据在控制器和视图间的信息量很小的有效方法。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-260">Both `ViewData` and `ViewBag` are equally valid approaches for passing small amounts of data among controllers and views.</span></span> <span data-ttu-id="3ebfd-261">要使用哪一种根据首选项。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-261">The choice of which one to use is based on preference.</span></span> <span data-ttu-id="3ebfd-262">可以混合和匹配`ViewData`和`ViewBag`对象，然而，该代码是以易于读取和使用一致的一种方法的情况下维护。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-262">You can mix and match `ViewData` and `ViewBag` objects, however, the code is easier to read and maintain with one approach used consistently.</span></span> <span data-ttu-id="3ebfd-263">这两种方法是在运行时动态解析和因此容易导致运行时错误。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-263">Both approaches are dynamically resolved at runtime and thus prone to causing runtime errors.</span></span> <span data-ttu-id="3ebfd-264">一些开发团队避免它们。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-264">Some development teams avoid them.</span></span>

### <a name="dynamic-views"></a><span data-ttu-id="3ebfd-265">动态视图</span><span class="sxs-lookup"><span data-stu-id="3ebfd-265">Dynamic views</span></span>

<span data-ttu-id="3ebfd-266">不要声明模型的视图类型使用`@model`但具有传递给它们的模型实例 (例如， `return View(Address);`) 可以动态引用实例的属性：</span><span class="sxs-lookup"><span data-stu-id="3ebfd-266">Views that don't declare a model type using `@model` but that have a model instance passed to them (for example, `return View(Address);`) can reference the instance's properties dynamically:</span></span>

```cshtml
<address>
    @Model.Street<br>
    @Model.City, @Model.State @Model.PostalCode<br>
    <abbr title="Phone">P:</abbr> 425.555.0100
</address>
```

<span data-ttu-id="3ebfd-267">此功能提供的灵活性，但不提供编译保护或智能感知。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-267">This feature offers flexibility but doesn't offer compilation protection or IntelliSense.</span></span> <span data-ttu-id="3ebfd-268">如果属性不存在，网页生成失败，则在运行时。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-268">If the property doesn't exist, webpage generation fails at runtime.</span></span>

## <a name="more-view-features"></a><span data-ttu-id="3ebfd-269">详细视图功能</span><span class="sxs-lookup"><span data-stu-id="3ebfd-269">More view features</span></span>

<span data-ttu-id="3ebfd-270">[标记帮助程序](xref:mvc/views/tag-helpers/intro)方便地将服务器端行为添加到现有的 HTML 标记。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-270">[Tag Helpers](xref:mvc/views/tag-helpers/intro) make it easy to add server-side behavior to existing HTML tags.</span></span> <span data-ttu-id="3ebfd-271">使用标记帮助程序可避免编写自定义代码或在你的视图内的帮助器的需求。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-271">Using Tag Helpers avoids the need to write custom code or helpers within your views.</span></span> <span data-ttu-id="3ebfd-272">标记帮助程序作为属性应用于 HTML 元素，并将忽略通过无法处理它们的编辑器。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-272">Tag helpers are applied as attributes to HTML elements and are ignored by editors that can't process them.</span></span> <span data-ttu-id="3ebfd-273">这样可编辑，呈现在各种工具中的查看标记。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-273">This allows you to edit and render view markup in a variety of tools.</span></span>

<span data-ttu-id="3ebfd-274">生成自定义的 HTML 标记可以通过许多内置的 HTML 帮助器。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-274">Generating custom HTML markup can be achieved with many built-in HTML Helpers.</span></span> <span data-ttu-id="3ebfd-275">可以由更复杂的用户界面逻辑[视图组件](xref:mvc/views/view-components)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-275">More complex user interface logic can be handled by [View Components](xref:mvc/views/view-components).</span></span> <span data-ttu-id="3ebfd-276">查看组件提供相同 SoC 该控制器和视图提供。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-276">View components provide the same SoC that controllers and views offer.</span></span> <span data-ttu-id="3ebfd-277">它们可以消除对操作和处理使用常见用户界面元素的数据的视图的需要。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-277">They can eliminate the need for actions and views that deal with data used by common user interface elements.</span></span>

<span data-ttu-id="3ebfd-278">ASP.NET 核心的很多其他方面，如视图支持[依赖关系注入](xref:fundamentals/dependency-injection)，允许服务[注入到视图](xref:mvc/views/dependency-injection)。</span><span class="sxs-lookup"><span data-stu-id="3ebfd-278">Like many other aspects of ASP.NET Core, views support [dependency injection](xref:fundamentals/dependency-injection), allowing services to be [injected into views](xref:mvc/views/dependency-injection).</span></span>