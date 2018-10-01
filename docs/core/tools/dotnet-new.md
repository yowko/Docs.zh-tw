---
title: dotnet new 命令 - .NET Core CLI
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 2c82dda2d93225edb360316637e22964135cd5e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512551"
---
# <a name="dotnet-new"></a><span data-ttu-id="c72e2-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c72e2-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c72e2-104">名稱</span><span class="sxs-lookup"><span data-stu-id="c72e2-104">Name</span></span>

<span data-ttu-id="c72e2-105">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="c72e2-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c72e2-106">概要</span><span class="sxs-lookup"><span data-stu-id="c72e2-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c72e2-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c72e2-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c72e2-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c72e2-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c72e2-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c72e2-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="c72e2-110">描述</span><span class="sxs-lookup"><span data-stu-id="c72e2-110">Description</span></span>

<span data-ttu-id="c72e2-111">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="c72e2-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="c72e2-112">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="c72e2-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="c72e2-113">引數</span><span class="sxs-lookup"><span data-stu-id="c72e2-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="c72e2-114">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="c72e2-115">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="c72e2-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="c72e2-116">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c72e2-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c72e2-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="c72e2-118">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="c72e2-118">The command contains a default list of templates.</span></span> <span data-ttu-id="c72e2-119">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="c72e2-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c72e2-120">下表顯示隨 .NET Core SDK 2.1.300 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="c72e2-121">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="c72e2-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="c72e2-122">範本描述</span><span class="sxs-lookup"><span data-stu-id="c72e2-122">Template description</span></span>                          | <span data-ttu-id="c72e2-123">範本名稱</span><span class="sxs-lookup"><span data-stu-id="c72e2-123">Template name</span></span>   | <span data-ttu-id="c72e2-124">語言</span><span class="sxs-lookup"><span data-stu-id="c72e2-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="c72e2-125">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c72e2-125">Console application</span></span>                          | `console`       | <span data-ttu-id="c72e2-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c72e2-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c72e2-127">類別庫</span><span class="sxs-lookup"><span data-stu-id="c72e2-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="c72e2-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c72e2-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c72e2-129">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="c72e2-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="c72e2-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c72e2-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c72e2-131">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="c72e2-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="c72e2-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c72e2-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c72e2-133">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="c72e2-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="c72e2-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-134">[C#]</span></span>          |
| <span data-ttu-id="c72e2-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="c72e2-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="c72e2-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-136">[C#]</span></span>          |
| <span data-ttu-id="c72e2-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c72e2-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="c72e2-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-138">[C#]</span></span>          |
| <span data-ttu-id="c72e2-139">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c72e2-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="c72e2-140">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-140">[C#], F#</span></span>      |
| <span data-ttu-id="c72e2-141">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="c72e2-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="c72e2-142">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-142">[C#], F#</span></span>      |
| <span data-ttu-id="c72e2-143">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="c72e2-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="c72e2-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-144">[C#]</span></span>          |
| <span data-ttu-id="c72e2-145">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="c72e2-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="c72e2-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-146">[C#]</span></span>          |
| <span data-ttu-id="c72e2-147">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="c72e2-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="c72e2-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-148">[C#]</span></span>          |
| <span data-ttu-id="c72e2-149">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="c72e2-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="c72e2-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-150">[C#]</span></span>          |
| <span data-ttu-id="c72e2-151">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="c72e2-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="c72e2-152">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-152">[C#], F#</span></span>      |
| <span data-ttu-id="c72e2-153">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="c72e2-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="c72e2-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-154">[C#]</span></span>          |
| <span data-ttu-id="c72e2-155">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="c72e2-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="c72e2-156">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="c72e2-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="c72e2-157">Web 組態</span><span class="sxs-lookup"><span data-stu-id="c72e2-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="c72e2-158">方案檔</span><span class="sxs-lookup"><span data-stu-id="c72e2-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c72e2-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c72e2-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="c72e2-160">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="c72e2-160">The command contains a default list of templates.</span></span> <span data-ttu-id="c72e2-161">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="c72e2-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c72e2-162">下表顯示隨 .NET Core SDK 2.0 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="c72e2-163">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="c72e2-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="c72e2-164">範本描述</span><span class="sxs-lookup"><span data-stu-id="c72e2-164">Template description</span></span>                          | <span data-ttu-id="c72e2-165">範本名稱</span><span class="sxs-lookup"><span data-stu-id="c72e2-165">Template name</span></span> | <span data-ttu-id="c72e2-166">語言</span><span class="sxs-lookup"><span data-stu-id="c72e2-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="c72e2-167">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c72e2-167">Console application</span></span>                          | `console`     | <span data-ttu-id="c72e2-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c72e2-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c72e2-169">類別庫</span><span class="sxs-lookup"><span data-stu-id="c72e2-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="c72e2-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c72e2-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c72e2-171">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="c72e2-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="c72e2-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c72e2-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c72e2-173">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="c72e2-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="c72e2-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c72e2-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c72e2-175">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c72e2-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="c72e2-176">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-176">[C#], F#</span></span>      |
| <span data-ttu-id="c72e2-177">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="c72e2-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="c72e2-178">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-178">[C#], F#</span></span>      |
| <span data-ttu-id="c72e2-179">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="c72e2-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="c72e2-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-180">[C#]</span></span>          |
| <span data-ttu-id="c72e2-181">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="c72e2-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="c72e2-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-182">[C#]</span></span>          |
| <span data-ttu-id="c72e2-183">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="c72e2-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="c72e2-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-184">[C#]</span></span>          |
| <span data-ttu-id="c72e2-185">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="c72e2-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="c72e2-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-186">[C#]</span></span>          |
| <span data-ttu-id="c72e2-187">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="c72e2-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="c72e2-188">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-188">[C#], F#</span></span>      |
| <span data-ttu-id="c72e2-189">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="c72e2-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="c72e2-190">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="c72e2-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="c72e2-191">Web 組態</span><span class="sxs-lookup"><span data-stu-id="c72e2-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="c72e2-192">方案檔</span><span class="sxs-lookup"><span data-stu-id="c72e2-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="c72e2-193">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="c72e2-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="c72e2-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="c72e2-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="c72e2-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c72e2-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c72e2-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c72e2-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c72e2-197">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="c72e2-197">The command contains a default list of templates.</span></span> <span data-ttu-id="c72e2-198">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="c72e2-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="c72e2-199">下表顯示隨 .NET Core SDK 1.x 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="c72e2-200">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="c72e2-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="c72e2-201">範本描述</span><span class="sxs-lookup"><span data-stu-id="c72e2-201">Template description</span></span>  | <span data-ttu-id="c72e2-202">範本名稱</span><span class="sxs-lookup"><span data-stu-id="c72e2-202">Template name</span></span> | <span data-ttu-id="c72e2-203">語言</span><span class="sxs-lookup"><span data-stu-id="c72e2-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="c72e2-204">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c72e2-204">Console application</span></span>  | `console`     | <span data-ttu-id="c72e2-205">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-205">[C#], F#</span></span>  |
| <span data-ttu-id="c72e2-206">類別庫</span><span class="sxs-lookup"><span data-stu-id="c72e2-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="c72e2-207">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-207">[C#], F#</span></span>  |
| <span data-ttu-id="c72e2-208">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="c72e2-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="c72e2-209">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-209">[C#], F#</span></span>  |
| <span data-ttu-id="c72e2-210">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="c72e2-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="c72e2-211">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-211">[C#], F#</span></span>  |
| <span data-ttu-id="c72e2-212">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c72e2-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="c72e2-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-213">[C#]</span></span>      |
| <span data-ttu-id="c72e2-214">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="c72e2-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="c72e2-215">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c72e2-215">[C#], F#</span></span>  |
| <span data-ttu-id="c72e2-216">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="c72e2-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="c72e2-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="c72e2-217">[C#]</span></span>      |
| <span data-ttu-id="c72e2-218">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="c72e2-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="c72e2-219">Web 組態</span><span class="sxs-lookup"><span data-stu-id="c72e2-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="c72e2-220">方案檔</span><span class="sxs-lookup"><span data-stu-id="c72e2-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="c72e2-221">選項</span><span class="sxs-lookup"><span data-stu-id="c72e2-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c72e2-222">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c72e2-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="c72e2-223">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="c72e2-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c72e2-224">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="c72e2-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c72e2-225">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="c72e2-225">Prints out help for the command.</span></span> <span data-ttu-id="c72e2-226">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c72e2-227">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="c72e2-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c72e2-228">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c72e2-229">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="c72e2-230">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="c72e2-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="c72e2-231">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c72e2-232">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="c72e2-233">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c72e2-234">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c72e2-235">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="c72e2-235">The language of the template to create.</span></span> <span data-ttu-id="c72e2-236">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c72e2-237">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c72e2-238">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="c72e2-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c72e2-239">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c72e2-240">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="c72e2-240">The name for the created output.</span></span> <span data-ttu-id="c72e2-241">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="c72e2-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="c72e2-242">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="c72e2-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c72e2-243">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="c72e2-243">Location to place the generated output.</span></span> <span data-ttu-id="c72e2-244">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="c72e2-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c72e2-245">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-245">Filters templates based on available types.</span></span> <span data-ttu-id="c72e2-246">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="c72e2-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c72e2-247">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="c72e2-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="c72e2-248">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c72e2-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c72e2-249">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="c72e2-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="c72e2-250">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="c72e2-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c72e2-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c72e2-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="c72e2-252">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="c72e2-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c72e2-253">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="c72e2-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c72e2-254">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="c72e2-254">Prints out help for the command.</span></span> <span data-ttu-id="c72e2-255">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c72e2-256">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="c72e2-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c72e2-257">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c72e2-258">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="c72e2-259">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="c72e2-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="c72e2-260">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c72e2-261">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="c72e2-262">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c72e2-263">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c72e2-264">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="c72e2-264">The language of the template to create.</span></span> <span data-ttu-id="c72e2-265">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c72e2-266">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c72e2-267">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="c72e2-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c72e2-268">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c72e2-269">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="c72e2-269">The name for the created output.</span></span> <span data-ttu-id="c72e2-270">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="c72e2-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c72e2-271">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="c72e2-271">Location to place the generated output.</span></span> <span data-ttu-id="c72e2-272">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="c72e2-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c72e2-273">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-273">Filters templates based on available types.</span></span> <span data-ttu-id="c72e2-274">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="c72e2-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c72e2-275">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="c72e2-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="c72e2-276">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c72e2-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c72e2-277">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="c72e2-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="c72e2-278">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="c72e2-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c72e2-279">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c72e2-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="c72e2-280">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="c72e2-281">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="c72e2-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="c72e2-282">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="c72e2-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c72e2-283">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="c72e2-283">Prints out help for the command.</span></span> <span data-ttu-id="c72e2-284">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="c72e2-285">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="c72e2-286">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c72e2-287">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="c72e2-288">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="c72e2-288">The language of the template to create.</span></span> <span data-ttu-id="c72e2-289">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c72e2-290">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c72e2-291">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="c72e2-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c72e2-292">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c72e2-293">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="c72e2-293">The name for the created output.</span></span> <span data-ttu-id="c72e2-294">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="c72e2-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c72e2-295">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="c72e2-295">Location to place the generated output.</span></span> <span data-ttu-id="c72e2-296">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="c72e2-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="c72e2-297">範本選項</span><span class="sxs-lookup"><span data-stu-id="c72e2-297">Template options</span></span>

<span data-ttu-id="c72e2-298">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="c72e2-298">Each project template may have additional options available.</span></span> <span data-ttu-id="c72e2-299">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="c72e2-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c72e2-300">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c72e2-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="c72e2-301">**主控台, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="c72e2-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="c72e2-302">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-303">**classlib**</span><span class="sxs-lookup"><span data-stu-id="c72e2-303">**classlib**</span></span>

<span data-ttu-id="c72e2-304">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c72e2-305">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="c72e2-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c72e2-306">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c72e2-307">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-308">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="c72e2-308">**mstest, xunit**</span></span>

<span data-ttu-id="c72e2-309">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="c72e2-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c72e2-310">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c72e2-311">**globaljson**</span></span>

<span data-ttu-id="c72e2-312">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="c72e2-313">**web**</span><span class="sxs-lookup"><span data-stu-id="c72e2-313">**web**</span></span>

<span data-ttu-id="c72e2-314">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="c72e2-314">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c72e2-315">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-316">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="c72e2-316">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c72e2-317">此選項僅適用於未使用 `IndividualAuth` 或 `OrganizationalAuth` 時。</span><span class="sxs-lookup"><span data-stu-id="c72e2-317">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="c72e2-318">**webapi**</span><span class="sxs-lookup"><span data-stu-id="c72e2-318">**webapi**</span></span>

<span data-ttu-id="c72e2-319">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c72e2-319">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c72e2-320">可能值為：</span><span class="sxs-lookup"><span data-stu-id="c72e2-320">The possible values are:</span></span>

- <span data-ttu-id="c72e2-321">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-321">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c72e2-322">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-322">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c72e2-323">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-323">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c72e2-324">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-324">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c72e2-325">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c72e2-325">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c72e2-326">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-326">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c72e2-327">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-327">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c72e2-328">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-328">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c72e2-329">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-329">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-330">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c72e2-330">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c72e2-331">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-331">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c72e2-332">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-332">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c72e2-333">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-333">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c72e2-334">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-334">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c72e2-335">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-335">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c72e2-336">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="c72e2-336">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c72e2-337">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-337">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c72e2-338">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-338">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c72e2-339">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-339">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c72e2-340">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-340">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c72e2-341">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-341">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c72e2-342">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="c72e2-342">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c72e2-343">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-343">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c72e2-344">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="c72e2-344">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c72e2-345">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="c72e2-345">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c72e2-346">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-346">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-347">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-347">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-348">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="c72e2-348">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c72e2-349">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-349">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c72e2-350">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="c72e2-350">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c72e2-351">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="c72e2-351">**mvc, razor**</span></span>

<span data-ttu-id="c72e2-352">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c72e2-352">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c72e2-353">可能值為：</span><span class="sxs-lookup"><span data-stu-id="c72e2-353">The possible values are:</span></span>

- <span data-ttu-id="c72e2-354">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-354">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c72e2-355">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-355">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c72e2-356">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-356">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c72e2-357">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-357">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c72e2-358">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-358">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c72e2-359">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-359">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c72e2-360">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c72e2-360">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c72e2-361">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-361">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c72e2-362">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-362">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c72e2-363">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-363">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c72e2-364">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-364">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-365">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-365">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c72e2-366">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-366">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-367">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-367">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c72e2-368">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-369">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c72e2-369">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c72e2-370">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-370">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c72e2-371">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-371">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c72e2-372">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-372">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c72e2-373">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-373">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c72e2-374">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-374">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c72e2-375">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="c72e2-375">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c72e2-376">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-376">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c72e2-377">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-377">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c72e2-378">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-378">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c72e2-379">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-379">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c72e2-380">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-380">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c72e2-381">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="c72e2-381">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c72e2-382">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-382">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c72e2-383">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-383">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c72e2-384">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="c72e2-384">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c72e2-385">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-385">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c72e2-386">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="c72e2-386">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c72e2-387">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="c72e2-387">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="c72e2-388">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="c72e2-388">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c72e2-389">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-389">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-390">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-390">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-391">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="c72e2-391">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c72e2-392">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-392">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c72e2-393">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="c72e2-393">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c72e2-394">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="c72e2-394">**page**</span></span>

<span data-ttu-id="c72e2-395">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c72e2-395">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c72e2-396">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-396">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c72e2-397">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="c72e2-397">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c72e2-398">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c72e2-398">**viewimports**</span></span>

<span data-ttu-id="c72e2-399">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c72e2-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c72e2-400">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-400">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c72e2-401">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c72e2-401">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="c72e2-402">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="c72e2-402">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="c72e2-403">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-404">**classlib**</span><span class="sxs-lookup"><span data-stu-id="c72e2-404">**classlib**</span></span>

<span data-ttu-id="c72e2-405">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-405">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c72e2-406">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="c72e2-406">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c72e2-407">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-407">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c72e2-408">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-409">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="c72e2-409">**mstest, xunit**</span></span>

<span data-ttu-id="c72e2-410">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="c72e2-410">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c72e2-411">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-411">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-412">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c72e2-412">**globaljson**</span></span>

<span data-ttu-id="c72e2-413">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="c72e2-413">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="c72e2-414">**web**</span><span class="sxs-lookup"><span data-stu-id="c72e2-414">**web**</span></span>

<span data-ttu-id="c72e2-415">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="c72e2-415">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c72e2-416">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-416">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-417">**webapi**</span><span class="sxs-lookup"><span data-stu-id="c72e2-417">**webapi**</span></span>

<span data-ttu-id="c72e2-418">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c72e2-418">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c72e2-419">可能值為：</span><span class="sxs-lookup"><span data-stu-id="c72e2-419">The possible values are:</span></span>

- <span data-ttu-id="c72e2-420">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-420">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c72e2-421">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-421">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c72e2-422">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-422">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c72e2-423">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-423">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c72e2-424">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c72e2-424">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c72e2-425">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-425">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c72e2-426">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-426">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c72e2-427">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-427">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c72e2-428">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-428">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-429">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c72e2-429">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c72e2-430">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c72e2-431">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-431">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c72e2-432">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-432">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c72e2-433">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-433">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c72e2-434">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-434">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c72e2-435">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="c72e2-435">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c72e2-436">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c72e2-437">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-437">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c72e2-438">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-438">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c72e2-439">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-439">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c72e2-440">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-440">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c72e2-441">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="c72e2-441">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c72e2-442">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-442">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c72e2-443">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="c72e2-443">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c72e2-444">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="c72e2-444">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c72e2-445">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-445">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-446">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-446">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-447">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="c72e2-447">**mvc, razor**</span></span>

<span data-ttu-id="c72e2-448">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c72e2-448">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c72e2-449">可能值為：</span><span class="sxs-lookup"><span data-stu-id="c72e2-449">The possible values are:</span></span>

- <span data-ttu-id="c72e2-450">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-450">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c72e2-451">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-451">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c72e2-452">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-452">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c72e2-453">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-453">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c72e2-454">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-454">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c72e2-455">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-455">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c72e2-456">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c72e2-456">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c72e2-457">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-457">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c72e2-458">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-458">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c72e2-459">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-459">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c72e2-460">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-460">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-461">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-461">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c72e2-462">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-462">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-463">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-463">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c72e2-464">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-465">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c72e2-465">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c72e2-466">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-466">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c72e2-467">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-467">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c72e2-468">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-468">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c72e2-469">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-469">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c72e2-470">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-470">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c72e2-471">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="c72e2-471">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c72e2-472">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-472">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c72e2-473">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-473">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c72e2-474">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72e2-474">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c72e2-475">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-475">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c72e2-476">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-476">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c72e2-477">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="c72e2-477">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c72e2-478">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c72e2-478">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c72e2-479">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-479">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c72e2-480">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="c72e2-480">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c72e2-481">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-481">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c72e2-482">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="c72e2-482">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c72e2-483">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="c72e2-483">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="c72e2-484">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="c72e2-484">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c72e2-485">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c72e2-485">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c72e2-486">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c72e2-486">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c72e2-487">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="c72e2-487">**page**</span></span>

<span data-ttu-id="c72e2-488">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c72e2-488">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c72e2-489">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-489">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c72e2-490">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="c72e2-490">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c72e2-491">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c72e2-491">**viewimports**</span></span>

<span data-ttu-id="c72e2-492">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c72e2-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c72e2-493">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-493">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c72e2-494">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c72e2-494">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c72e2-495">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="c72e2-495">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="c72e2-496">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c72e2-497">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="c72e2-498">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="c72e2-499">**classlib**</span><span class="sxs-lookup"><span data-stu-id="c72e2-499">**classlib**</span></span>

<span data-ttu-id="c72e2-500">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c72e2-501">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-501">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="c72e2-502">預設值是 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-502">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="c72e2-503">**mvc**</span><span class="sxs-lookup"><span data-stu-id="c72e2-503">**mvc**</span></span>

<span data-ttu-id="c72e2-504">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="c72e2-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c72e2-505">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-505">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="c72e2-506">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-506">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="c72e2-507">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c72e2-507">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="c72e2-508">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-508">Values: `None` or `Individual`.</span></span> <span data-ttu-id="c72e2-509">預設值是 `None`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-509">The default value is `None`.</span></span>

<span data-ttu-id="c72e2-510">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="c72e2-510">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="c72e2-511">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-511">Values: `true` or `false`.</span></span> <span data-ttu-id="c72e2-512">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="c72e2-512">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c72e2-513">範例</span><span class="sxs-lookup"><span data-stu-id="c72e2-513">Examples</span></span>

<span data-ttu-id="c72e2-514">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="c72e2-514">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="c72e2-515">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core SDK 2.0 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="c72e2-515">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="c72e2-516">未經驗證即在目前的目錄中建立新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="c72e2-516">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="c72e2-517">建立新的 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="c72e2-517">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="c72e2-518">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="c72e2-518">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="c72e2-519">安裝適用於 ASP.NET Core 的單頁應用程式範本 2.0 版 (僅適用於 .NET Core SDK 1.1 及更新版本的命令選項)：</span><span class="sxs-lookup"><span data-stu-id="c72e2-519">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="c72e2-520">在目前目錄中建立 *global.json*，並將 SDK 版本設為 2.0.0 (只能用於.NET Core SDK 2.0 或更新版本)：</span><span class="sxs-lookup"><span data-stu-id="c72e2-520">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="c72e2-521">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c72e2-521">See also</span></span>

* [<span data-ttu-id="c72e2-522">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="c72e2-522">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="c72e2-523">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="c72e2-523">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* <span data-ttu-id="c72e2-524">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="c72e2-524">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
* [<span data-ttu-id="c72e2-525">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="c72e2-525">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
