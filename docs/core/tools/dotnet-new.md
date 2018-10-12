---
title: dotnet new 命令 - .NET Core CLI
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 396c4ddf09854fa4582226bdb1422f8c929e459b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47208629"
---
# <a name="dotnet-new"></a><span data-ttu-id="3ba43-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="3ba43-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3ba43-104">名稱</span><span class="sxs-lookup"><span data-stu-id="3ba43-104">Name</span></span>

<span data-ttu-id="3ba43-105">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="3ba43-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3ba43-106">概要</span><span class="sxs-lookup"><span data-stu-id="3ba43-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3ba43-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3ba43-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3ba43-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3ba43-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3ba43-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3ba43-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="3ba43-110">描述</span><span class="sxs-lookup"><span data-stu-id="3ba43-110">Description</span></span>

<span data-ttu-id="3ba43-111">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="3ba43-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="3ba43-112">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="3ba43-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="3ba43-113">引數</span><span class="sxs-lookup"><span data-stu-id="3ba43-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="3ba43-114">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="3ba43-115">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="3ba43-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="3ba43-116">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3ba43-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3ba43-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="3ba43-118">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="3ba43-118">The command contains a default list of templates.</span></span> <span data-ttu-id="3ba43-119">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="3ba43-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="3ba43-120">下表顯示隨 .NET Core SDK 2.1.300 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="3ba43-121">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="3ba43-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="3ba43-122">範本描述</span><span class="sxs-lookup"><span data-stu-id="3ba43-122">Template description</span></span>                          | <span data-ttu-id="3ba43-123">範本名稱</span><span class="sxs-lookup"><span data-stu-id="3ba43-123">Template name</span></span>   | <span data-ttu-id="3ba43-124">語言</span><span class="sxs-lookup"><span data-stu-id="3ba43-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="3ba43-125">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="3ba43-125">Console application</span></span>                          | `console`       | <span data-ttu-id="3ba43-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3ba43-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3ba43-127">類別庫</span><span class="sxs-lookup"><span data-stu-id="3ba43-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="3ba43-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3ba43-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3ba43-129">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="3ba43-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="3ba43-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3ba43-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3ba43-131">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="3ba43-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="3ba43-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3ba43-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3ba43-133">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="3ba43-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="3ba43-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-134">[C#]</span></span>          |
| <span data-ttu-id="3ba43-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="3ba43-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="3ba43-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-136">[C#]</span></span>          |
| <span data-ttu-id="3ba43-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="3ba43-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="3ba43-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-138">[C#]</span></span>          |
| <span data-ttu-id="3ba43-139">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3ba43-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="3ba43-140">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-140">[C#], F#</span></span>      |
| <span data-ttu-id="3ba43-141">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="3ba43-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="3ba43-142">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-142">[C#], F#</span></span>      |
| <span data-ttu-id="3ba43-143">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="3ba43-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="3ba43-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-144">[C#]</span></span>          |
| <span data-ttu-id="3ba43-145">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="3ba43-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="3ba43-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-146">[C#]</span></span>          |
| <span data-ttu-id="3ba43-147">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="3ba43-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="3ba43-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-148">[C#]</span></span>          |
| <span data-ttu-id="3ba43-149">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="3ba43-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="3ba43-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-150">[C#]</span></span>          |
| <span data-ttu-id="3ba43-151">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="3ba43-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="3ba43-152">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-152">[C#], F#</span></span>      |
| <span data-ttu-id="3ba43-153">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="3ba43-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="3ba43-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-154">[C#]</span></span>          |
| <span data-ttu-id="3ba43-155">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="3ba43-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="3ba43-156">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="3ba43-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="3ba43-157">Web 組態</span><span class="sxs-lookup"><span data-stu-id="3ba43-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="3ba43-158">方案檔</span><span class="sxs-lookup"><span data-stu-id="3ba43-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3ba43-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3ba43-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="3ba43-160">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="3ba43-160">The command contains a default list of templates.</span></span> <span data-ttu-id="3ba43-161">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="3ba43-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="3ba43-162">下表顯示隨 .NET Core SDK 2.0 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="3ba43-163">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="3ba43-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="3ba43-164">範本描述</span><span class="sxs-lookup"><span data-stu-id="3ba43-164">Template description</span></span>                          | <span data-ttu-id="3ba43-165">範本名稱</span><span class="sxs-lookup"><span data-stu-id="3ba43-165">Template name</span></span> | <span data-ttu-id="3ba43-166">語言</span><span class="sxs-lookup"><span data-stu-id="3ba43-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="3ba43-167">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="3ba43-167">Console application</span></span>                          | `console`     | <span data-ttu-id="3ba43-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3ba43-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3ba43-169">類別庫</span><span class="sxs-lookup"><span data-stu-id="3ba43-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="3ba43-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3ba43-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3ba43-171">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="3ba43-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="3ba43-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3ba43-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3ba43-173">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="3ba43-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="3ba43-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3ba43-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3ba43-175">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3ba43-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="3ba43-176">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-176">[C#], F#</span></span>      |
| <span data-ttu-id="3ba43-177">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="3ba43-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="3ba43-178">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-178">[C#], F#</span></span>      |
| <span data-ttu-id="3ba43-179">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="3ba43-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="3ba43-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-180">[C#]</span></span>          |
| <span data-ttu-id="3ba43-181">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="3ba43-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="3ba43-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-182">[C#]</span></span>          |
| <span data-ttu-id="3ba43-183">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="3ba43-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="3ba43-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-184">[C#]</span></span>          |
| <span data-ttu-id="3ba43-185">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="3ba43-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="3ba43-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-186">[C#]</span></span>          |
| <span data-ttu-id="3ba43-187">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="3ba43-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="3ba43-188">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-188">[C#], F#</span></span>      |
| <span data-ttu-id="3ba43-189">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="3ba43-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="3ba43-190">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="3ba43-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="3ba43-191">Web 組態</span><span class="sxs-lookup"><span data-stu-id="3ba43-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="3ba43-192">方案檔</span><span class="sxs-lookup"><span data-stu-id="3ba43-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="3ba43-193">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="3ba43-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="3ba43-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="3ba43-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="3ba43-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="3ba43-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3ba43-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3ba43-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="3ba43-197">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="3ba43-197">The command contains a default list of templates.</span></span> <span data-ttu-id="3ba43-198">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="3ba43-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="3ba43-199">下表顯示隨 .NET Core SDK 1.x 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="3ba43-200">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="3ba43-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="3ba43-201">範本描述</span><span class="sxs-lookup"><span data-stu-id="3ba43-201">Template description</span></span>  | <span data-ttu-id="3ba43-202">範本名稱</span><span class="sxs-lookup"><span data-stu-id="3ba43-202">Template name</span></span> | <span data-ttu-id="3ba43-203">語言</span><span class="sxs-lookup"><span data-stu-id="3ba43-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="3ba43-204">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="3ba43-204">Console application</span></span>  | `console`     | <span data-ttu-id="3ba43-205">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-205">[C#], F#</span></span>  |
| <span data-ttu-id="3ba43-206">類別庫</span><span class="sxs-lookup"><span data-stu-id="3ba43-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="3ba43-207">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-207">[C#], F#</span></span>  |
| <span data-ttu-id="3ba43-208">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="3ba43-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="3ba43-209">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-209">[C#], F#</span></span>  |
| <span data-ttu-id="3ba43-210">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="3ba43-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="3ba43-211">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-211">[C#], F#</span></span>  |
| <span data-ttu-id="3ba43-212">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3ba43-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="3ba43-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-213">[C#]</span></span>      |
| <span data-ttu-id="3ba43-214">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="3ba43-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="3ba43-215">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="3ba43-215">[C#], F#</span></span>  |
| <span data-ttu-id="3ba43-216">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="3ba43-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="3ba43-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="3ba43-217">[C#]</span></span>      |
| <span data-ttu-id="3ba43-218">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="3ba43-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="3ba43-219">Web 組態</span><span class="sxs-lookup"><span data-stu-id="3ba43-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="3ba43-220">方案檔</span><span class="sxs-lookup"><span data-stu-id="3ba43-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="3ba43-221">選項</span><span class="sxs-lookup"><span data-stu-id="3ba43-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3ba43-222">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3ba43-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="3ba43-223">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="3ba43-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="3ba43-224">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="3ba43-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="3ba43-225">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="3ba43-225">Prints out help for the command.</span></span> <span data-ttu-id="3ba43-226">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="3ba43-227">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="3ba43-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="3ba43-228">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="3ba43-229">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="3ba43-230">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="3ba43-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="3ba43-231">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="3ba43-232">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="3ba43-233">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="3ba43-234">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="3ba43-235">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="3ba43-235">The language of the template to create.</span></span> <span data-ttu-id="3ba43-236">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="3ba43-237">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="3ba43-238">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="3ba43-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="3ba43-239">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="3ba43-240">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ba43-240">The name for the created output.</span></span> <span data-ttu-id="3ba43-241">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ba43-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="3ba43-242">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="3ba43-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3ba43-243">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="3ba43-243">Location to place the generated output.</span></span> <span data-ttu-id="3ba43-244">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="3ba43-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="3ba43-245">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-245">Filters templates based on available types.</span></span> <span data-ttu-id="3ba43-246">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="3ba43-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="3ba43-247">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="3ba43-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="3ba43-248">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="3ba43-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="3ba43-249">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="3ba43-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="3ba43-250">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="3ba43-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3ba43-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3ba43-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="3ba43-252">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="3ba43-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="3ba43-253">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="3ba43-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="3ba43-254">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="3ba43-254">Prints out help for the command.</span></span> <span data-ttu-id="3ba43-255">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="3ba43-256">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="3ba43-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="3ba43-257">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="3ba43-258">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="3ba43-259">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="3ba43-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="3ba43-260">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="3ba43-261">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="3ba43-262">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="3ba43-263">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="3ba43-264">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="3ba43-264">The language of the template to create.</span></span> <span data-ttu-id="3ba43-265">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="3ba43-266">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="3ba43-267">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="3ba43-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="3ba43-268">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="3ba43-269">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ba43-269">The name for the created output.</span></span> <span data-ttu-id="3ba43-270">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ba43-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3ba43-271">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="3ba43-271">Location to place the generated output.</span></span> <span data-ttu-id="3ba43-272">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="3ba43-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="3ba43-273">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-273">Filters templates based on available types.</span></span> <span data-ttu-id="3ba43-274">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="3ba43-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="3ba43-275">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="3ba43-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="3ba43-276">若要使用來源 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="3ba43-276">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="3ba43-277">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="3ba43-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="3ba43-278">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="3ba43-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="3ba43-279">如果您無法判斷將範本解除安裝需要 `PATH` 或是 `NUGET_ID` 引數，在沒有引數的情況下執行 `dotnet new --uninstall` 會列出所有已安裝的範本，以及將它們解除安裝所需的引數。</span><span class="sxs-lookup"><span data-stu-id="3ba43-279">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3ba43-280">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3ba43-280">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="3ba43-281">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-281">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="3ba43-282">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="3ba43-282">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="3ba43-283">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="3ba43-283">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="3ba43-284">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="3ba43-284">Prints out help for the command.</span></span> <span data-ttu-id="3ba43-285">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-285">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="3ba43-286">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-286">Lists templates containing the specified name.</span></span> <span data-ttu-id="3ba43-287">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-287">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="3ba43-288">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-288">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="3ba43-289">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="3ba43-289">The language of the template to create.</span></span> <span data-ttu-id="3ba43-290">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-290">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="3ba43-291">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-291">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="3ba43-292">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="3ba43-292">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="3ba43-293">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-293">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="3ba43-294">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ba43-294">The name for the created output.</span></span> <span data-ttu-id="3ba43-295">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ba43-295">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3ba43-296">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="3ba43-296">Location to place the generated output.</span></span> <span data-ttu-id="3ba43-297">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="3ba43-297">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="3ba43-298">範本選項</span><span class="sxs-lookup"><span data-stu-id="3ba43-298">Template options</span></span>

<span data-ttu-id="3ba43-299">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="3ba43-299">Each project template may have additional options available.</span></span> <span data-ttu-id="3ba43-300">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="3ba43-300">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3ba43-301">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3ba43-301">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="3ba43-302">**主控台, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="3ba43-302">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="3ba43-303">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-303">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-304">**classlib**</span><span class="sxs-lookup"><span data-stu-id="3ba43-304">**classlib**</span></span>

<span data-ttu-id="3ba43-305">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-305">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3ba43-306">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="3ba43-306">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="3ba43-307">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-307">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="3ba43-308">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-308">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-309">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="3ba43-309">**mstest, xunit**</span></span>

<span data-ttu-id="3ba43-310">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="3ba43-310">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="3ba43-311">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-312">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="3ba43-312">**globaljson**</span></span>

<span data-ttu-id="3ba43-313">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-313">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="3ba43-314">**web**</span><span class="sxs-lookup"><span data-stu-id="3ba43-314">**web**</span></span>

<span data-ttu-id="3ba43-315">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="3ba43-315">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="3ba43-316">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-316">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-317">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="3ba43-317">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="3ba43-318">此選項僅適用於未使用 `IndividualAuth` 或 `OrganizationalAuth` 時。</span><span class="sxs-lookup"><span data-stu-id="3ba43-318">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="3ba43-319">**webapi**</span><span class="sxs-lookup"><span data-stu-id="3ba43-319">**webapi**</span></span>

<span data-ttu-id="3ba43-320">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="3ba43-320">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="3ba43-321">可能值為：</span><span class="sxs-lookup"><span data-stu-id="3ba43-321">The possible values are:</span></span>

- <span data-ttu-id="3ba43-322">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-322">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="3ba43-323">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-323">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="3ba43-324">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-324">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="3ba43-325">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-325">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="3ba43-326">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ba43-326">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="3ba43-327">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-327">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="3ba43-328">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-328">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="3ba43-329">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-329">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="3ba43-330">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-330">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-331">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ba43-331">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="3ba43-332">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3ba43-333">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-333">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="3ba43-334">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-334">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="3ba43-335">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-335">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="3ba43-336">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-336">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="3ba43-337">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="3ba43-337">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="3ba43-338">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-338">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3ba43-339">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-339">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="3ba43-340">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-340">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="3ba43-341">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-341">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3ba43-342">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-342">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="3ba43-343">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="3ba43-343">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="3ba43-344">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-344">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="3ba43-345">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="3ba43-345">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="3ba43-346">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="3ba43-346">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="3ba43-347">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-347">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-348">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-348">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-349">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="3ba43-349">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="3ba43-350">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-350">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="3ba43-351">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="3ba43-351">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="3ba43-352">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="3ba43-352">**mvc, razor**</span></span>

<span data-ttu-id="3ba43-353">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="3ba43-353">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="3ba43-354">可能值為：</span><span class="sxs-lookup"><span data-stu-id="3ba43-354">The possible values are:</span></span>

- <span data-ttu-id="3ba43-355">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-355">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="3ba43-356">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-356">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="3ba43-357">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-357">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="3ba43-358">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-358">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="3ba43-359">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-359">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="3ba43-360">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-360">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="3ba43-361">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ba43-361">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="3ba43-362">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-362">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="3ba43-363">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-363">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="3ba43-364">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-364">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="3ba43-365">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-365">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-366">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-366">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="3ba43-367">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-367">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-368">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-368">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="3ba43-369">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-369">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-370">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ba43-370">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="3ba43-371">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-371">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="3ba43-372">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-372">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="3ba43-373">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-373">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="3ba43-374">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-374">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="3ba43-375">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-375">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="3ba43-376">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="3ba43-376">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="3ba43-377">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3ba43-378">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-378">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="3ba43-379">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-379">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="3ba43-380">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-380">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3ba43-381">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-381">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="3ba43-382">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="3ba43-382">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="3ba43-383">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-383">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3ba43-384">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-384">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="3ba43-385">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="3ba43-385">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="3ba43-386">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-386">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="3ba43-387">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="3ba43-387">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="3ba43-388">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="3ba43-388">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="3ba43-389">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="3ba43-389">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="3ba43-390">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-390">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-391">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-391">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-392">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="3ba43-392">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="3ba43-393">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-393">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="3ba43-394">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="3ba43-394">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="3ba43-395">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="3ba43-395">**page**</span></span>

<span data-ttu-id="3ba43-396">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3ba43-396">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="3ba43-397">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-397">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="3ba43-398">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="3ba43-398">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="3ba43-399">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="3ba43-399">**viewimports**</span></span>

<span data-ttu-id="3ba43-400">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3ba43-400">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="3ba43-401">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-401">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3ba43-402">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3ba43-402">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="3ba43-403">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="3ba43-403">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="3ba43-404">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-404">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-405">**classlib**</span><span class="sxs-lookup"><span data-stu-id="3ba43-405">**classlib**</span></span>

<span data-ttu-id="3ba43-406">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-406">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3ba43-407">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="3ba43-407">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="3ba43-408">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-408">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="3ba43-409">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-409">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-410">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="3ba43-410">**mstest, xunit**</span></span>

<span data-ttu-id="3ba43-411">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="3ba43-411">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="3ba43-412">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-413">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="3ba43-413">**globaljson**</span></span>

<span data-ttu-id="3ba43-414">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="3ba43-414">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="3ba43-415">**web**</span><span class="sxs-lookup"><span data-stu-id="3ba43-415">**web**</span></span>

<span data-ttu-id="3ba43-416">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="3ba43-416">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="3ba43-417">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-417">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-418">**webapi**</span><span class="sxs-lookup"><span data-stu-id="3ba43-418">**webapi**</span></span>

<span data-ttu-id="3ba43-419">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="3ba43-419">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="3ba43-420">可能值為：</span><span class="sxs-lookup"><span data-stu-id="3ba43-420">The possible values are:</span></span>

- <span data-ttu-id="3ba43-421">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-421">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="3ba43-422">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-422">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="3ba43-423">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-423">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="3ba43-424">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-424">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="3ba43-425">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ba43-425">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="3ba43-426">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-426">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="3ba43-427">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-427">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="3ba43-428">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-428">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="3ba43-429">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-429">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-430">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ba43-430">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="3ba43-431">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3ba43-432">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-432">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="3ba43-433">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-433">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="3ba43-434">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-434">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="3ba43-435">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-435">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="3ba43-436">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="3ba43-436">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="3ba43-437">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-437">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3ba43-438">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-438">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="3ba43-439">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-439">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="3ba43-440">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-440">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3ba43-441">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-441">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="3ba43-442">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="3ba43-442">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="3ba43-443">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-443">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="3ba43-444">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="3ba43-444">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="3ba43-445">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="3ba43-445">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="3ba43-446">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-446">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-447">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-447">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-448">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="3ba43-448">**mvc, razor**</span></span>

<span data-ttu-id="3ba43-449">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="3ba43-449">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="3ba43-450">可能值為：</span><span class="sxs-lookup"><span data-stu-id="3ba43-450">The possible values are:</span></span>

- <span data-ttu-id="3ba43-451">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-451">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="3ba43-452">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-452">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="3ba43-453">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-453">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="3ba43-454">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-454">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="3ba43-455">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-455">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="3ba43-456">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-456">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="3ba43-457">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ba43-457">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="3ba43-458">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-458">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="3ba43-459">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-459">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="3ba43-460">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-460">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="3ba43-461">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-461">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-462">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-462">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="3ba43-463">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-463">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-464">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-464">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="3ba43-465">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-465">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-466">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ba43-466">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="3ba43-467">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-467">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="3ba43-468">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-468">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="3ba43-469">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-469">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="3ba43-470">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-470">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="3ba43-471">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-471">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="3ba43-472">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="3ba43-472">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="3ba43-473">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-473">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3ba43-474">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-474">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="3ba43-475">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ba43-475">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="3ba43-476">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-476">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3ba43-477">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-477">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="3ba43-478">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="3ba43-478">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="3ba43-479">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="3ba43-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3ba43-480">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-480">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="3ba43-481">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="3ba43-481">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="3ba43-482">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-482">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="3ba43-483">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="3ba43-483">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="3ba43-484">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="3ba43-484">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="3ba43-485">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="3ba43-485">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="3ba43-486">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="3ba43-486">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3ba43-487">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="3ba43-487">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3ba43-488">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="3ba43-488">**page**</span></span>

<span data-ttu-id="3ba43-489">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3ba43-489">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="3ba43-490">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-490">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="3ba43-491">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="3ba43-491">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="3ba43-492">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="3ba43-492">**viewimports**</span></span>

<span data-ttu-id="3ba43-493">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3ba43-493">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="3ba43-494">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-494">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3ba43-495">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3ba43-495">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="3ba43-496">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="3ba43-496">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="3ba43-497">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-497">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3ba43-498">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-498">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="3ba43-499">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-499">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="3ba43-500">**classlib**</span><span class="sxs-lookup"><span data-stu-id="3ba43-500">**classlib**</span></span>

<span data-ttu-id="3ba43-501">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-501">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3ba43-502">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-502">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="3ba43-503">預設值是 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-503">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="3ba43-504">**mvc**</span><span class="sxs-lookup"><span data-stu-id="3ba43-504">**mvc**</span></span>

<span data-ttu-id="3ba43-505">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba43-505">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3ba43-506">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-506">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="3ba43-507">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-507">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="3ba43-508">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="3ba43-508">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="3ba43-509">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-509">Values: `None` or `Individual`.</span></span> <span data-ttu-id="3ba43-510">預設值是 `None`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-510">The default value is `None`.</span></span>

<span data-ttu-id="3ba43-511">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="3ba43-511">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="3ba43-512">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-512">Values: `true` or `false`.</span></span> <span data-ttu-id="3ba43-513">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="3ba43-513">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="3ba43-514">範例</span><span class="sxs-lookup"><span data-stu-id="3ba43-514">Examples</span></span>

<span data-ttu-id="3ba43-515">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="3ba43-515">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="3ba43-516">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core SDK 2.0 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="3ba43-516">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="3ba43-517">未經驗證即在目前的目錄中建立新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="3ba43-517">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="3ba43-518">建立新的 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="3ba43-518">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="3ba43-519">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="3ba43-519">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="3ba43-520">安裝適用於 ASP.NET Core 的單頁應用程式範本 2.0 版 (僅適用於 .NET Core SDK 1.1 及更新版本的命令選項)：</span><span class="sxs-lookup"><span data-stu-id="3ba43-520">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="3ba43-521">在目前目錄中建立 *global.json*，並將 SDK 版本設為 2.0.0 (只能用於.NET Core SDK 2.0 或更新版本)：</span><span class="sxs-lookup"><span data-stu-id="3ba43-521">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="3ba43-522">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ba43-522">See also</span></span>

* [<span data-ttu-id="3ba43-523">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="3ba43-523">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="3ba43-524">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="3ba43-524">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* <span data-ttu-id="3ba43-525">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="3ba43-525">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
* [<span data-ttu-id="3ba43-526">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="3ba43-526">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
