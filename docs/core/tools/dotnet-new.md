---
title: dotnet new 命令 - .NET Core CLI
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: ae24c4145cc67ca863c07e4d22af8a1c2c2dd732
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570459"
---
# <a name="dotnet-new"></a><span data-ttu-id="8d0eb-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8d0eb-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8d0eb-104">名稱</span><span class="sxs-lookup"><span data-stu-id="8d0eb-104">Name</span></span>

<span data-ttu-id="8d0eb-105">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8d0eb-106">概要</span><span class="sxs-lookup"><span data-stu-id="8d0eb-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8d0eb-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8d0eb-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8d0eb-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8d0eb-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8d0eb-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8d0eb-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="8d0eb-110">描述</span><span class="sxs-lookup"><span data-stu-id="8d0eb-110">Description</span></span>

<span data-ttu-id="8d0eb-111">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="8d0eb-112">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="8d0eb-113">引數</span><span class="sxs-lookup"><span data-stu-id="8d0eb-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="8d0eb-114">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="8d0eb-115">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="8d0eb-116">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8d0eb-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8d0eb-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="8d0eb-118">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-118">The command contains a default list of templates.</span></span> <span data-ttu-id="8d0eb-119">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="8d0eb-120">下表顯示隨 .NET Core SDK 2.1.300 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="8d0eb-121">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8d0eb-122">範本描述</span><span class="sxs-lookup"><span data-stu-id="8d0eb-122">Template description</span></span>                          | <span data-ttu-id="8d0eb-123">範本名稱</span><span class="sxs-lookup"><span data-stu-id="8d0eb-123">Template name</span></span>   | <span data-ttu-id="8d0eb-124">語言</span><span class="sxs-lookup"><span data-stu-id="8d0eb-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="8d0eb-125">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="8d0eb-125">Console application</span></span>                          | `console`       | <span data-ttu-id="8d0eb-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d0eb-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8d0eb-127">類別庫</span><span class="sxs-lookup"><span data-stu-id="8d0eb-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="8d0eb-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d0eb-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8d0eb-129">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="8d0eb-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="8d0eb-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d0eb-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8d0eb-131">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="8d0eb-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="8d0eb-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d0eb-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8d0eb-133">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="8d0eb-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="8d0eb-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-134">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="8d0eb-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="8d0eb-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-136">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="8d0eb-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="8d0eb-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-138">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-139">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d0eb-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="8d0eb-140">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-140">[C#], F#</span></span>      |
| <span data-ttu-id="8d0eb-141">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="8d0eb-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="8d0eb-142">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-142">[C#], F#</span></span>      |
| <span data-ttu-id="8d0eb-143">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="8d0eb-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="8d0eb-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-144">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-145">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="8d0eb-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="8d0eb-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-146">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-147">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="8d0eb-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="8d0eb-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-148">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-149">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="8d0eb-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="8d0eb-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-150">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-151">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="8d0eb-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="8d0eb-152">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-152">[C#], F#</span></span>      |
| <span data-ttu-id="8d0eb-153">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="8d0eb-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="8d0eb-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-154">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-155">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="8d0eb-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="8d0eb-156">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="8d0eb-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="8d0eb-157">Web 組態</span><span class="sxs-lookup"><span data-stu-id="8d0eb-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="8d0eb-158">方案檔</span><span class="sxs-lookup"><span data-stu-id="8d0eb-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8d0eb-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8d0eb-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="8d0eb-160">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-160">The command contains a default list of templates.</span></span> <span data-ttu-id="8d0eb-161">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="8d0eb-162">下表顯示隨 .NET Core SDK 2.0 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="8d0eb-163">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8d0eb-164">範本描述</span><span class="sxs-lookup"><span data-stu-id="8d0eb-164">Template description</span></span>                          | <span data-ttu-id="8d0eb-165">範本名稱</span><span class="sxs-lookup"><span data-stu-id="8d0eb-165">Template name</span></span> | <span data-ttu-id="8d0eb-166">語言</span><span class="sxs-lookup"><span data-stu-id="8d0eb-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="8d0eb-167">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="8d0eb-167">Console application</span></span>                          | `console`     | <span data-ttu-id="8d0eb-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d0eb-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8d0eb-169">類別庫</span><span class="sxs-lookup"><span data-stu-id="8d0eb-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="8d0eb-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d0eb-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8d0eb-171">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="8d0eb-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="8d0eb-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d0eb-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8d0eb-173">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="8d0eb-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="8d0eb-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d0eb-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8d0eb-175">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d0eb-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="8d0eb-176">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-176">[C#], F#</span></span>      |
| <span data-ttu-id="8d0eb-177">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="8d0eb-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="8d0eb-178">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-178">[C#], F#</span></span>      |
| <span data-ttu-id="8d0eb-179">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="8d0eb-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="8d0eb-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-180">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-181">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="8d0eb-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="8d0eb-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-182">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-183">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="8d0eb-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="8d0eb-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-184">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-185">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="8d0eb-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="8d0eb-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-186">[C#]</span></span>          |
| <span data-ttu-id="8d0eb-187">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="8d0eb-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="8d0eb-188">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-188">[C#], F#</span></span>      |
| <span data-ttu-id="8d0eb-189">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="8d0eb-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="8d0eb-190">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="8d0eb-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="8d0eb-191">Web 組態</span><span class="sxs-lookup"><span data-stu-id="8d0eb-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="8d0eb-192">方案檔</span><span class="sxs-lookup"><span data-stu-id="8d0eb-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="8d0eb-193">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="8d0eb-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="8d0eb-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="8d0eb-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="8d0eb-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="8d0eb-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8d0eb-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8d0eb-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8d0eb-197">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-197">The command contains a default list of templates.</span></span> <span data-ttu-id="8d0eb-198">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="8d0eb-199">下表顯示隨 .NET Core SDK 1.x 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="8d0eb-200">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8d0eb-201">範本描述</span><span class="sxs-lookup"><span data-stu-id="8d0eb-201">Template description</span></span>  | <span data-ttu-id="8d0eb-202">範本名稱</span><span class="sxs-lookup"><span data-stu-id="8d0eb-202">Template name</span></span> | <span data-ttu-id="8d0eb-203">語言</span><span class="sxs-lookup"><span data-stu-id="8d0eb-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="8d0eb-204">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="8d0eb-204">Console application</span></span>  | `console`     | <span data-ttu-id="8d0eb-205">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-205">[C#], F#</span></span>  |
| <span data-ttu-id="8d0eb-206">類別庫</span><span class="sxs-lookup"><span data-stu-id="8d0eb-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="8d0eb-207">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-207">[C#], F#</span></span>  |
| <span data-ttu-id="8d0eb-208">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="8d0eb-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="8d0eb-209">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-209">[C#], F#</span></span>  |
| <span data-ttu-id="8d0eb-210">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="8d0eb-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="8d0eb-211">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-211">[C#], F#</span></span>  |
| <span data-ttu-id="8d0eb-212">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d0eb-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="8d0eb-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-213">[C#]</span></span>      |
| <span data-ttu-id="8d0eb-214">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="8d0eb-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="8d0eb-215">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="8d0eb-215">[C#], F#</span></span>  |
| <span data-ttu-id="8d0eb-216">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="8d0eb-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="8d0eb-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d0eb-217">[C#]</span></span>      |
| <span data-ttu-id="8d0eb-218">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="8d0eb-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="8d0eb-219">Web 組態</span><span class="sxs-lookup"><span data-stu-id="8d0eb-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="8d0eb-220">方案檔</span><span class="sxs-lookup"><span data-stu-id="8d0eb-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="8d0eb-221">選項</span><span class="sxs-lookup"><span data-stu-id="8d0eb-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8d0eb-222">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8d0eb-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="8d0eb-223">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="8d0eb-224">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8d0eb-225">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-225">Prints out help for the command.</span></span> <span data-ttu-id="8d0eb-226">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="8d0eb-227">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8d0eb-228">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="8d0eb-229">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="8d0eb-230">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="8d0eb-231">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="8d0eb-232">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="8d0eb-233">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8d0eb-234">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="8d0eb-235">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-235">The language of the template to create.</span></span> <span data-ttu-id="8d0eb-236">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8d0eb-237">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-237">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8d0eb-238">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-238">The name for the created output.</span></span> <span data-ttu-id="8d0eb-239">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-239">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="8d0eb-240">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-240">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8d0eb-241">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-241">Location to place the generated output.</span></span> <span data-ttu-id="8d0eb-242">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-242">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="8d0eb-243">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-243">Filters templates based on available types.</span></span> <span data-ttu-id="8d0eb-244">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-244">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="8d0eb-245">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-245">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="8d0eb-246">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-246">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="8d0eb-247">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-247">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="8d0eb-248">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-248">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8d0eb-249">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8d0eb-249">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="8d0eb-250">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-250">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="8d0eb-251">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-251">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8d0eb-252">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-252">Prints out help for the command.</span></span> <span data-ttu-id="8d0eb-253">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-253">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="8d0eb-254">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-254">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8d0eb-255">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-255">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="8d0eb-256">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-256">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="8d0eb-257">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-257">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="8d0eb-258">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-258">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="8d0eb-259">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-259">Lists templates containing the specified name.</span></span> <span data-ttu-id="8d0eb-260">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-260">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8d0eb-261">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-261">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="8d0eb-262">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-262">The language of the template to create.</span></span> <span data-ttu-id="8d0eb-263">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-263">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8d0eb-264">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-264">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8d0eb-265">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-265">The name for the created output.</span></span> <span data-ttu-id="8d0eb-266">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-266">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8d0eb-267">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-267">Location to place the generated output.</span></span> <span data-ttu-id="8d0eb-268">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-268">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="8d0eb-269">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-269">Filters templates based on available types.</span></span> <span data-ttu-id="8d0eb-270">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-270">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="8d0eb-271">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-271">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="8d0eb-272">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-272">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="8d0eb-273">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-273">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="8d0eb-274">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-274">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8d0eb-275">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8d0eb-275">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="8d0eb-276">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-276">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="8d0eb-277">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-277">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="8d0eb-278">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-278">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8d0eb-279">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-279">Prints out help for the command.</span></span> <span data-ttu-id="8d0eb-280">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-280">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="8d0eb-281">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-281">Lists templates containing the specified name.</span></span> <span data-ttu-id="8d0eb-282">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-282">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8d0eb-283">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-283">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="8d0eb-284">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-284">The language of the template to create.</span></span> <span data-ttu-id="8d0eb-285">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-285">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8d0eb-286">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-286">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8d0eb-287">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-287">The name for the created output.</span></span> <span data-ttu-id="8d0eb-288">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-288">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8d0eb-289">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-289">Location to place the generated output.</span></span> <span data-ttu-id="8d0eb-290">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-290">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="8d0eb-291">範本選項</span><span class="sxs-lookup"><span data-stu-id="8d0eb-291">Template options</span></span>

<span data-ttu-id="8d0eb-292">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-292">Each project template may have additional options available.</span></span> <span data-ttu-id="8d0eb-293">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-293">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8d0eb-294">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8d0eb-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="8d0eb-295">**主控台, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-295">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="8d0eb-296">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-296">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-297">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-297">**classlib**</span></span>

<span data-ttu-id="8d0eb-298">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-298">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d0eb-299">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-299">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="8d0eb-300">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-300">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="8d0eb-301">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-301">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-302">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-302">**mstest, xunit**</span></span>

<span data-ttu-id="8d0eb-303">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-303">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="8d0eb-304">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-305">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-305">**globaljson**</span></span>

<span data-ttu-id="8d0eb-306">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-306">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="8d0eb-307">**web**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-307">**web**</span></span>

<span data-ttu-id="8d0eb-308">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-308">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8d0eb-309">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-310">**webapi**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-310">**webapi**</span></span>

<span data-ttu-id="8d0eb-311">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-311">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8d0eb-312">可能值為：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-312">The possible values are:</span></span>

- <span data-ttu-id="8d0eb-313">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-313">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8d0eb-314">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-314">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8d0eb-315">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-315">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8d0eb-316">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-316">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8d0eb-317">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-317">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8d0eb-318">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-318">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d0eb-319">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-319">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8d0eb-320">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-320">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8d0eb-321">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-321">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-322">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-322">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8d0eb-323">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-323">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d0eb-324">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-324">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8d0eb-325">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-325">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8d0eb-326">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-326">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8d0eb-327">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-327">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8d0eb-328">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-328">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8d0eb-329">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-329">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d0eb-330">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-330">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8d0eb-331">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-331">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8d0eb-332">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d0eb-333">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-333">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8d0eb-334">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-334">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8d0eb-335">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-335">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8d0eb-336">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-336">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8d0eb-337">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-337">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8d0eb-338">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-338">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-339">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-339">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-340">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-340">**mvc, razor**</span></span>

<span data-ttu-id="8d0eb-341">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-341">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8d0eb-342">可能值為：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-342">The possible values are:</span></span>

- <span data-ttu-id="8d0eb-343">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-343">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8d0eb-344">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-344">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="8d0eb-345">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-345">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8d0eb-346">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-346">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8d0eb-347">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-347">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="8d0eb-348">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-348">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8d0eb-349">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-349">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8d0eb-350">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-350">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d0eb-351">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-351">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8d0eb-352">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-352">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8d0eb-353">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-353">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-354">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-354">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="8d0eb-355">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-355">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-356">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-356">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="8d0eb-357">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-357">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-358">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-358">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8d0eb-359">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-359">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8d0eb-360">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-360">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8d0eb-361">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-361">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8d0eb-362">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-362">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8d0eb-363">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-363">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8d0eb-364">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-364">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8d0eb-365">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-365">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d0eb-366">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-366">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8d0eb-367">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-367">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8d0eb-368">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-368">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d0eb-369">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-369">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8d0eb-370">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-370">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8d0eb-371">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d0eb-372">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-372">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="8d0eb-373">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-373">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8d0eb-374">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-374">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8d0eb-375">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-375">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8d0eb-376">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-376">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="8d0eb-377">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-377">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8d0eb-378">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-378">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-379">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-379">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-380">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-380">**page**</span></span>

<span data-ttu-id="8d0eb-381">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-381">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8d0eb-382">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-382">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="8d0eb-383">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-383">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="8d0eb-384">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-384">**viewimports**</span></span>

<span data-ttu-id="8d0eb-385">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-385">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8d0eb-386">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-386">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8d0eb-387">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8d0eb-387">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="8d0eb-388">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-388">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="8d0eb-389">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-389">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-390">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-390">**classlib**</span></span>

<span data-ttu-id="8d0eb-391">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-391">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d0eb-392">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-392">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="8d0eb-393">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-393">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="8d0eb-394">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-395">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-395">**mstest, xunit**</span></span>

<span data-ttu-id="8d0eb-396">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-396">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="8d0eb-397">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-397">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-398">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-398">**globaljson**</span></span>

<span data-ttu-id="8d0eb-399">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-399">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="8d0eb-400">**web**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-400">**web**</span></span>

<span data-ttu-id="8d0eb-401">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-401">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8d0eb-402">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-402">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-403">**webapi**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-403">**webapi**</span></span>

<span data-ttu-id="8d0eb-404">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-404">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8d0eb-405">可能值為：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-405">The possible values are:</span></span>

- <span data-ttu-id="8d0eb-406">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-406">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8d0eb-407">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8d0eb-408">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8d0eb-409">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-409">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8d0eb-410">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-410">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8d0eb-411">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d0eb-412">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8d0eb-413">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-413">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8d0eb-414">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-414">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-415">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-415">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8d0eb-416">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-416">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d0eb-417">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-417">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8d0eb-418">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-418">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8d0eb-419">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-419">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8d0eb-420">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-420">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8d0eb-421">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-421">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8d0eb-422">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-422">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d0eb-423">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-423">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8d0eb-424">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-424">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8d0eb-425">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-425">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d0eb-426">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-426">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8d0eb-427">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-427">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8d0eb-428">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-428">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8d0eb-429">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-429">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8d0eb-430">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-430">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8d0eb-431">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-431">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-432">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-432">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-433">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-433">**mvc, razor**</span></span>

<span data-ttu-id="8d0eb-434">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-434">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8d0eb-435">可能值為：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-435">The possible values are:</span></span>

- <span data-ttu-id="8d0eb-436">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-436">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8d0eb-437">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-437">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="8d0eb-438">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-438">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8d0eb-439">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-439">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8d0eb-440">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-440">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="8d0eb-441">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-441">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8d0eb-442">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-442">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8d0eb-443">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-443">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d0eb-444">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-444">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8d0eb-445">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-445">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8d0eb-446">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-446">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-447">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-447">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="8d0eb-448">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-448">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-449">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-449">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="8d0eb-450">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-450">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-451">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-451">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8d0eb-452">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-452">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8d0eb-453">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-453">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8d0eb-454">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-454">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8d0eb-455">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-455">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8d0eb-456">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-456">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8d0eb-457">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-457">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8d0eb-458">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-458">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d0eb-459">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-459">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8d0eb-460">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-460">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8d0eb-461">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-461">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d0eb-462">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-462">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8d0eb-463">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-463">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8d0eb-464">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d0eb-465">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-465">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="8d0eb-466">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-466">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8d0eb-467">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-467">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8d0eb-468">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-468">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8d0eb-469">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-469">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="8d0eb-470">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-470">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8d0eb-471">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-471">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8d0eb-472">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-472">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8d0eb-473">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-473">**page**</span></span>

<span data-ttu-id="8d0eb-474">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-474">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8d0eb-475">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-475">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="8d0eb-476">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-476">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="8d0eb-477">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-477">**viewimports**</span></span>

<span data-ttu-id="8d0eb-478">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-478">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8d0eb-479">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-479">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8d0eb-480">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8d0eb-480">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8d0eb-481">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-481">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="8d0eb-482">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-482">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d0eb-483">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-483">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="8d0eb-484">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-484">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="8d0eb-485">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-485">**classlib**</span></span>

<span data-ttu-id="8d0eb-486">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-486">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d0eb-487">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-487">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="8d0eb-488">預設值是 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-488">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="8d0eb-489">**mvc**</span><span class="sxs-lookup"><span data-stu-id="8d0eb-489">**mvc**</span></span>

<span data-ttu-id="8d0eb-490">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-490">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d0eb-491">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-491">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="8d0eb-492">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-492">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="8d0eb-493">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-493">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="8d0eb-494">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-494">Values: `None` or `Individual`.</span></span> <span data-ttu-id="8d0eb-495">預設值是 `None`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-495">The default value is `None`.</span></span>

<span data-ttu-id="8d0eb-496">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-496">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="8d0eb-497">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-497">Values: `true` or `false`.</span></span> <span data-ttu-id="8d0eb-498">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="8d0eb-498">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="8d0eb-499">範例</span><span class="sxs-lookup"><span data-stu-id="8d0eb-499">Examples</span></span>

<span data-ttu-id="8d0eb-500">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-500">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="8d0eb-501">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core SDK 2.0 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-501">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="8d0eb-502">未經驗證即在目前的目錄中，建立以 .NET Core 2.0 為目標的新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-502">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="8d0eb-503">建立以 .NET Core 2.0 為目標的新 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-503">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="8d0eb-504">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-504">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="8d0eb-505">安裝適用於 ASP.NET Core 的單頁應用程式範本 2.0 版 (僅適用於 .NET Core SDK 1.1 及更新版本的命令選項)：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-505">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="8d0eb-506">在目前目錄中建立 *global.json*，並將 SDK 版本設為 2.0.0 (只能用於.NET Core SDK 2.0 或更新版本)：</span><span class="sxs-lookup"><span data-stu-id="8d0eb-506">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="8d0eb-507">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d0eb-507">See also</span></span>

[<span data-ttu-id="8d0eb-508">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="8d0eb-508">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="8d0eb-509">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="8d0eb-509">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
<span data-ttu-id="8d0eb-510">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="8d0eb-510">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
[<span data-ttu-id="8d0eb-511">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="8d0eb-511">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)