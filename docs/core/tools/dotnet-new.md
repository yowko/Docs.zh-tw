---
title: dotnet new 命令 - .NET Core CLI
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
author: mairaw
ms.author: mairaw
ms.date: 06/12/2018
ms.openlocfilehash: f0ef91361dfbc2c2ba5532fbd607786289e98c69
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207765"
---
# <a name="dotnet-new"></a><span data-ttu-id="9cefc-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="9cefc-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9cefc-104">名稱</span><span class="sxs-lookup"><span data-stu-id="9cefc-104">Name</span></span>

<span data-ttu-id="9cefc-105">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="9cefc-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9cefc-106">概要</span><span class="sxs-lookup"><span data-stu-id="9cefc-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9cefc-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9cefc-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9cefc-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9cefc-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9cefc-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9cefc-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="9cefc-110">描述</span><span class="sxs-lookup"><span data-stu-id="9cefc-110">Description</span></span>

<span data-ttu-id="9cefc-111">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="9cefc-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="9cefc-112">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="9cefc-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="9cefc-113">引數</span><span class="sxs-lookup"><span data-stu-id="9cefc-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="9cefc-114">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="9cefc-115">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="9cefc-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="9cefc-116">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9cefc-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9cefc-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="9cefc-118">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="9cefc-118">The command contains a default list of templates.</span></span> <span data-ttu-id="9cefc-119">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="9cefc-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="9cefc-120">下表顯示隨 .NET Core SDK 2.1.300 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="9cefc-121">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="9cefc-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="9cefc-122">範本描述</span><span class="sxs-lookup"><span data-stu-id="9cefc-122">Template description</span></span>                          | <span data-ttu-id="9cefc-123">範本名稱</span><span class="sxs-lookup"><span data-stu-id="9cefc-123">Template name</span></span>   | <span data-ttu-id="9cefc-124">語言</span><span class="sxs-lookup"><span data-stu-id="9cefc-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="9cefc-125">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="9cefc-125">Console application</span></span>                          | `console`       | <span data-ttu-id="9cefc-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9cefc-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="9cefc-127">類別庫</span><span class="sxs-lookup"><span data-stu-id="9cefc-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="9cefc-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9cefc-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="9cefc-129">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="9cefc-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="9cefc-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9cefc-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="9cefc-131">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="9cefc-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="9cefc-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9cefc-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="9cefc-133">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="9cefc-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="9cefc-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-134">[C#]</span></span>          |
| <span data-ttu-id="9cefc-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="9cefc-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="9cefc-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-136">[C#]</span></span>          |
| <span data-ttu-id="9cefc-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="9cefc-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="9cefc-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-138">[C#]</span></span>          |
| <span data-ttu-id="9cefc-139">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9cefc-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="9cefc-140">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-140">[C#], F#</span></span>      |
| <span data-ttu-id="9cefc-141">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="9cefc-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="9cefc-142">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-142">[C#], F#</span></span>      |
| <span data-ttu-id="9cefc-143">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="9cefc-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="9cefc-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-144">[C#]</span></span>          |
| <span data-ttu-id="9cefc-145">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="9cefc-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="9cefc-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-146">[C#]</span></span>          |
| <span data-ttu-id="9cefc-147">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="9cefc-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="9cefc-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-148">[C#]</span></span>          |
| <span data-ttu-id="9cefc-149">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="9cefc-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="9cefc-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-150">[C#]</span></span>          |
| <span data-ttu-id="9cefc-151">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="9cefc-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="9cefc-152">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-152">[C#], F#</span></span>      |
| <span data-ttu-id="9cefc-153">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="9cefc-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="9cefc-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-154">[C#]</span></span>          |
| <span data-ttu-id="9cefc-155">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="9cefc-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="9cefc-156">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="9cefc-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="9cefc-157">Web 組態</span><span class="sxs-lookup"><span data-stu-id="9cefc-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="9cefc-158">方案檔</span><span class="sxs-lookup"><span data-stu-id="9cefc-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9cefc-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9cefc-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="9cefc-160">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="9cefc-160">The command contains a default list of templates.</span></span> <span data-ttu-id="9cefc-161">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="9cefc-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="9cefc-162">下表顯示隨 .NET Core SDK 2.0 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="9cefc-163">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="9cefc-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="9cefc-164">範本描述</span><span class="sxs-lookup"><span data-stu-id="9cefc-164">Template description</span></span>                          | <span data-ttu-id="9cefc-165">範本名稱</span><span class="sxs-lookup"><span data-stu-id="9cefc-165">Template name</span></span> | <span data-ttu-id="9cefc-166">語言</span><span class="sxs-lookup"><span data-stu-id="9cefc-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="9cefc-167">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="9cefc-167">Console application</span></span>                          | `console`     | <span data-ttu-id="9cefc-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9cefc-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="9cefc-169">類別庫</span><span class="sxs-lookup"><span data-stu-id="9cefc-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="9cefc-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9cefc-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="9cefc-171">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="9cefc-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="9cefc-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9cefc-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="9cefc-173">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="9cefc-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="9cefc-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9cefc-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="9cefc-175">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9cefc-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="9cefc-176">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-176">[C#], F#</span></span>      |
| <span data-ttu-id="9cefc-177">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="9cefc-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="9cefc-178">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-178">[C#], F#</span></span>      |
| <span data-ttu-id="9cefc-179">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="9cefc-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="9cefc-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-180">[C#]</span></span>          |
| <span data-ttu-id="9cefc-181">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="9cefc-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="9cefc-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-182">[C#]</span></span>          |
| <span data-ttu-id="9cefc-183">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="9cefc-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="9cefc-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-184">[C#]</span></span>          |
| <span data-ttu-id="9cefc-185">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="9cefc-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="9cefc-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-186">[C#]</span></span>          |
| <span data-ttu-id="9cefc-187">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="9cefc-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="9cefc-188">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-188">[C#], F#</span></span>      |
| <span data-ttu-id="9cefc-189">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="9cefc-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="9cefc-190">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="9cefc-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="9cefc-191">Web 組態</span><span class="sxs-lookup"><span data-stu-id="9cefc-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="9cefc-192">方案檔</span><span class="sxs-lookup"><span data-stu-id="9cefc-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="9cefc-193">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="9cefc-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="9cefc-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="9cefc-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="9cefc-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="9cefc-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9cefc-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9cefc-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="9cefc-197">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="9cefc-197">The command contains a default list of templates.</span></span> <span data-ttu-id="9cefc-198">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="9cefc-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="9cefc-199">下表顯示隨 .NET Core SDK 1.x 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="9cefc-200">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="9cefc-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="9cefc-201">範本描述</span><span class="sxs-lookup"><span data-stu-id="9cefc-201">Template description</span></span>  | <span data-ttu-id="9cefc-202">範本名稱</span><span class="sxs-lookup"><span data-stu-id="9cefc-202">Template name</span></span> | <span data-ttu-id="9cefc-203">語言</span><span class="sxs-lookup"><span data-stu-id="9cefc-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="9cefc-204">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="9cefc-204">Console application</span></span>  | `console`     | <span data-ttu-id="9cefc-205">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-205">[C#], F#</span></span>  |
| <span data-ttu-id="9cefc-206">類別庫</span><span class="sxs-lookup"><span data-stu-id="9cefc-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="9cefc-207">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-207">[C#], F#</span></span>  |
| <span data-ttu-id="9cefc-208">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="9cefc-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="9cefc-209">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-209">[C#], F#</span></span>  |
| <span data-ttu-id="9cefc-210">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="9cefc-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="9cefc-211">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-211">[C#], F#</span></span>  |
| <span data-ttu-id="9cefc-212">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9cefc-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="9cefc-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-213">[C#]</span></span>      |
| <span data-ttu-id="9cefc-214">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="9cefc-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="9cefc-215">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9cefc-215">[C#], F#</span></span>  |
| <span data-ttu-id="9cefc-216">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="9cefc-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="9cefc-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="9cefc-217">[C#]</span></span>      |
| <span data-ttu-id="9cefc-218">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="9cefc-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="9cefc-219">Web 組態</span><span class="sxs-lookup"><span data-stu-id="9cefc-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="9cefc-220">方案檔</span><span class="sxs-lookup"><span data-stu-id="9cefc-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="9cefc-221">選項</span><span class="sxs-lookup"><span data-stu-id="9cefc-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9cefc-222">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9cefc-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="9cefc-223">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="9cefc-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="9cefc-224">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="9cefc-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="9cefc-225">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="9cefc-225">Prints out help for the command.</span></span> <span data-ttu-id="9cefc-226">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="9cefc-227">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="9cefc-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="9cefc-228">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="9cefc-229">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="9cefc-230">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="9cefc-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="9cefc-231">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="9cefc-232">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="9cefc-233">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="9cefc-234">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="9cefc-235">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="9cefc-235">The language of the template to create.</span></span> <span data-ttu-id="9cefc-236">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="9cefc-237">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="9cefc-238">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="9cefc-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="9cefc-239">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="9cefc-240">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cefc-240">The name for the created output.</span></span> <span data-ttu-id="9cefc-241">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cefc-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="9cefc-242">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="9cefc-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9cefc-243">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="9cefc-243">Location to place the generated output.</span></span> <span data-ttu-id="9cefc-244">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="9cefc-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="9cefc-245">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-245">Filters templates based on available types.</span></span> <span data-ttu-id="9cefc-246">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="9cefc-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="9cefc-247">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="9cefc-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="9cefc-248">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="9cefc-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="9cefc-249">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="9cefc-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="9cefc-250">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="9cefc-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9cefc-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9cefc-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="9cefc-252">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="9cefc-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="9cefc-253">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="9cefc-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="9cefc-254">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="9cefc-254">Prints out help for the command.</span></span> <span data-ttu-id="9cefc-255">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="9cefc-256">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="9cefc-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="9cefc-257">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="9cefc-258">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="9cefc-259">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="9cefc-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="9cefc-260">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="9cefc-261">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="9cefc-262">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="9cefc-263">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="9cefc-264">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="9cefc-264">The language of the template to create.</span></span> <span data-ttu-id="9cefc-265">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="9cefc-266">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="9cefc-267">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="9cefc-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="9cefc-268">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="9cefc-269">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cefc-269">The name for the created output.</span></span> <span data-ttu-id="9cefc-270">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cefc-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9cefc-271">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="9cefc-271">Location to place the generated output.</span></span> <span data-ttu-id="9cefc-272">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="9cefc-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="9cefc-273">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-273">Filters templates based on available types.</span></span> <span data-ttu-id="9cefc-274">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="9cefc-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="9cefc-275">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="9cefc-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="9cefc-276">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="9cefc-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="9cefc-277">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="9cefc-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="9cefc-278">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="9cefc-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9cefc-279">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9cefc-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="9cefc-280">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="9cefc-281">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="9cefc-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="9cefc-282">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="9cefc-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="9cefc-283">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="9cefc-283">Prints out help for the command.</span></span> <span data-ttu-id="9cefc-284">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="9cefc-285">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="9cefc-286">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="9cefc-287">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="9cefc-288">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="9cefc-288">The language of the template to create.</span></span> <span data-ttu-id="9cefc-289">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="9cefc-290">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="9cefc-291">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="9cefc-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="9cefc-292">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="9cefc-293">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cefc-293">The name for the created output.</span></span> <span data-ttu-id="9cefc-294">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cefc-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9cefc-295">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="9cefc-295">Location to place the generated output.</span></span> <span data-ttu-id="9cefc-296">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="9cefc-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="9cefc-297">範本選項</span><span class="sxs-lookup"><span data-stu-id="9cefc-297">Template options</span></span>

<span data-ttu-id="9cefc-298">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="9cefc-298">Each project template may have additional options available.</span></span> <span data-ttu-id="9cefc-299">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="9cefc-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9cefc-300">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9cefc-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="9cefc-301">**主控台, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="9cefc-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="9cefc-302">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-303">**classlib**</span><span class="sxs-lookup"><span data-stu-id="9cefc-303">**classlib**</span></span>

<span data-ttu-id="9cefc-304">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9cefc-305">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="9cefc-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="9cefc-306">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="9cefc-307">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-308">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="9cefc-308">**mstest, xunit**</span></span>

<span data-ttu-id="9cefc-309">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="9cefc-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="9cefc-310">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="9cefc-311">**globaljson**</span></span>

<span data-ttu-id="9cefc-312">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="9cefc-313">**web**</span><span class="sxs-lookup"><span data-stu-id="9cefc-313">**web**</span></span>

<span data-ttu-id="9cefc-314">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="9cefc-314">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="9cefc-315">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-316">**webapi**</span><span class="sxs-lookup"><span data-stu-id="9cefc-316">**webapi**</span></span>

<span data-ttu-id="9cefc-317">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9cefc-317">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9cefc-318">可能值為：</span><span class="sxs-lookup"><span data-stu-id="9cefc-318">The possible values are:</span></span>

- <span data-ttu-id="9cefc-319">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-319">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="9cefc-320">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-320">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="9cefc-321">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-321">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="9cefc-322">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-322">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="9cefc-323">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9cefc-323">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9cefc-324">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-324">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9cefc-325">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-325">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="9cefc-326">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-326">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9cefc-327">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-327">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-328">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9cefc-328">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9cefc-329">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-329">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9cefc-330">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-330">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="9cefc-331">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-331">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="9cefc-332">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-332">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="9cefc-333">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-333">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="9cefc-334">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="9cefc-334">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="9cefc-335">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-335">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9cefc-336">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-336">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="9cefc-337">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-337">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9cefc-338">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-338">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9cefc-339">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-339">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="9cefc-340">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="9cefc-340">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="9cefc-341">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-341">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="9cefc-342">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="9cefc-342">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="9cefc-343">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9cefc-343">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9cefc-344">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-344">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-345">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-345">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-346">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="9cefc-346">**mvc, razor**</span></span>

<span data-ttu-id="9cefc-347">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9cefc-347">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9cefc-348">可能值為：</span><span class="sxs-lookup"><span data-stu-id="9cefc-348">The possible values are:</span></span>

- <span data-ttu-id="9cefc-349">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-349">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="9cefc-350">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-350">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="9cefc-351">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-351">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="9cefc-352">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-352">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="9cefc-353">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-353">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="9cefc-354">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-354">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="9cefc-355">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9cefc-355">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9cefc-356">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-356">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9cefc-357">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-357">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="9cefc-358">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-358">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9cefc-359">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-359">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-360">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-360">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="9cefc-361">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-361">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-362">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-362">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="9cefc-363">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-363">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-364">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9cefc-364">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9cefc-365">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-365">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="9cefc-366">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-366">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="9cefc-367">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-367">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="9cefc-368">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-368">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="9cefc-369">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-369">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="9cefc-370">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="9cefc-370">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="9cefc-371">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9cefc-372">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-372">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="9cefc-373">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-373">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9cefc-374">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-374">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9cefc-375">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-375">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="9cefc-376">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="9cefc-376">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="9cefc-377">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9cefc-378">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-378">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="9cefc-379">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="9cefc-379">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="9cefc-380">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-380">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="9cefc-381">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="9cefc-381">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="9cefc-382">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="9cefc-382">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="9cefc-383">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9cefc-383">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9cefc-384">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-384">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-385">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-385">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-386">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="9cefc-386">**page**</span></span>

<span data-ttu-id="9cefc-387">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9cefc-387">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="9cefc-388">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-388">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="9cefc-389">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="9cefc-389">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="9cefc-390">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="9cefc-390">**viewimports**</span></span>

<span data-ttu-id="9cefc-391">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9cefc-391">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="9cefc-392">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-392">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9cefc-393">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9cefc-393">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="9cefc-394">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="9cefc-394">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="9cefc-395">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-395">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-396">**classlib**</span><span class="sxs-lookup"><span data-stu-id="9cefc-396">**classlib**</span></span>

<span data-ttu-id="9cefc-397">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-397">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9cefc-398">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="9cefc-398">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="9cefc-399">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-399">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="9cefc-400">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-400">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-401">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="9cefc-401">**mstest, xunit**</span></span>

<span data-ttu-id="9cefc-402">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="9cefc-402">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="9cefc-403">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-404">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="9cefc-404">**globaljson**</span></span>

<span data-ttu-id="9cefc-405">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="9cefc-405">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="9cefc-406">**web**</span><span class="sxs-lookup"><span data-stu-id="9cefc-406">**web**</span></span>

<span data-ttu-id="9cefc-407">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="9cefc-407">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="9cefc-408">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-409">**webapi**</span><span class="sxs-lookup"><span data-stu-id="9cefc-409">**webapi**</span></span>

<span data-ttu-id="9cefc-410">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9cefc-410">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9cefc-411">可能值為：</span><span class="sxs-lookup"><span data-stu-id="9cefc-411">The possible values are:</span></span>

- <span data-ttu-id="9cefc-412">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-412">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="9cefc-413">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-413">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="9cefc-414">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-414">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="9cefc-415">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-415">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="9cefc-416">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9cefc-416">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9cefc-417">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-417">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9cefc-418">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-418">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="9cefc-419">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-419">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9cefc-420">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-420">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-421">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9cefc-421">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9cefc-422">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-422">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9cefc-423">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-423">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="9cefc-424">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-424">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="9cefc-425">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-425">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="9cefc-426">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="9cefc-427">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="9cefc-427">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="9cefc-428">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9cefc-429">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-429">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="9cefc-430">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-430">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9cefc-431">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9cefc-432">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="9cefc-433">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="9cefc-433">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="9cefc-434">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-434">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="9cefc-435">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="9cefc-435">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="9cefc-436">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9cefc-436">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9cefc-437">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-437">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-438">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-438">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-439">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="9cefc-439">**mvc, razor**</span></span>

<span data-ttu-id="9cefc-440">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9cefc-440">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9cefc-441">可能值為：</span><span class="sxs-lookup"><span data-stu-id="9cefc-441">The possible values are:</span></span>

- <span data-ttu-id="9cefc-442">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-442">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="9cefc-443">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-443">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="9cefc-444">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-444">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="9cefc-445">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-445">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="9cefc-446">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-446">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="9cefc-447">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-447">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="9cefc-448">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9cefc-448">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9cefc-449">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-449">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9cefc-450">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-450">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="9cefc-451">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-451">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9cefc-452">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-452">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-453">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-453">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="9cefc-454">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-454">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-455">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-455">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="9cefc-456">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-456">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-457">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9cefc-457">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9cefc-458">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-458">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="9cefc-459">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-459">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="9cefc-460">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-460">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="9cefc-461">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-461">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="9cefc-462">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-462">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="9cefc-463">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="9cefc-463">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="9cefc-464">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9cefc-465">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-465">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="9cefc-466">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cefc-466">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9cefc-467">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-467">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9cefc-468">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-468">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="9cefc-469">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="9cefc-469">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="9cefc-470">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9cefc-470">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9cefc-471">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-471">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="9cefc-472">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="9cefc-472">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="9cefc-473">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-473">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="9cefc-474">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="9cefc-474">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="9cefc-475">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="9cefc-475">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="9cefc-476">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9cefc-476">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9cefc-477">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9cefc-477">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9cefc-478">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9cefc-478">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9cefc-479">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="9cefc-479">**page**</span></span>

<span data-ttu-id="9cefc-480">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9cefc-480">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="9cefc-481">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-481">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="9cefc-482">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="9cefc-482">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="9cefc-483">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="9cefc-483">**viewimports**</span></span>

<span data-ttu-id="9cefc-484">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9cefc-484">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="9cefc-485">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-485">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9cefc-486">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9cefc-486">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="9cefc-487">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="9cefc-487">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="9cefc-488">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-488">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9cefc-489">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-489">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="9cefc-490">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-490">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="9cefc-491">**classlib**</span><span class="sxs-lookup"><span data-stu-id="9cefc-491">**classlib**</span></span>

<span data-ttu-id="9cefc-492">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-492">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9cefc-493">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-493">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="9cefc-494">預設值是 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-494">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="9cefc-495">**mvc**</span><span class="sxs-lookup"><span data-stu-id="9cefc-495">**mvc**</span></span>

<span data-ttu-id="9cefc-496">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9cefc-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9cefc-497">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="9cefc-498">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="9cefc-499">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9cefc-499">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="9cefc-500">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-500">Values: `None` or `Individual`.</span></span> <span data-ttu-id="9cefc-501">預設值是 `None`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-501">The default value is `None`.</span></span>

<span data-ttu-id="9cefc-502">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9cefc-502">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="9cefc-503">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-503">Values: `true` or `false`.</span></span> <span data-ttu-id="9cefc-504">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="9cefc-504">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="9cefc-505">範例</span><span class="sxs-lookup"><span data-stu-id="9cefc-505">Examples</span></span>

<span data-ttu-id="9cefc-506">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="9cefc-506">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="9cefc-507">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core SDK 2.0 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="9cefc-507">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="9cefc-508">未經驗證即在目前的目錄中建立新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="9cefc-508">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="9cefc-509">建立新的 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="9cefc-509">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="9cefc-510">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="9cefc-510">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="9cefc-511">安裝適用於 ASP.NET Core 的單頁應用程式範本 2.0 版 (僅適用於 .NET Core SDK 1.1 及更新版本的命令選項)：</span><span class="sxs-lookup"><span data-stu-id="9cefc-511">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="9cefc-512">在目前目錄中建立 *global.json*，並將 SDK 版本設為 2.0.0 (只能用於.NET Core SDK 2.0 或更新版本)：</span><span class="sxs-lookup"><span data-stu-id="9cefc-512">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="9cefc-513">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cefc-513">See also</span></span>

[<span data-ttu-id="9cefc-514">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="9cefc-514">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="9cefc-515">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="9cefc-515">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
<span data-ttu-id="9cefc-516">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="9cefc-516">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
[<span data-ttu-id="9cefc-517">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="9cefc-517">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
