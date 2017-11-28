---
title: "dotnet new 命令 - .NET Core CLI"
description: "dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。"
keywords: "dotnet-new, CLI, CLI 命令, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.openlocfilehash: d64881380febee08414f57a36ed92079e8d69ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="66d83-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="66d83-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="66d83-105">name</span><span class="sxs-lookup"><span data-stu-id="66d83-105">Name</span></span>

<span data-ttu-id="66d83-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="66d83-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="66d83-107">概要</span><span class="sxs-lookup"><span data-stu-id="66d83-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="66d83-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="66d83-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="66d83-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="66d83-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="66d83-110">說明</span><span class="sxs-lookup"><span data-stu-id="66d83-110">Description</span></span>

<span data-ttu-id="66d83-111">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="66d83-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="66d83-112">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="66d83-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="66d83-113">引數</span><span class="sxs-lookup"><span data-stu-id="66d83-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="66d83-114">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="66d83-115">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="66d83-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="66d83-116">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="66d83-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="66d83-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="66d83-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="66d83-118">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="66d83-118">The command contains a default list of templates.</span></span> <span data-ttu-id="66d83-119">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="66d83-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="66d83-120">下表顯示隨 .NET Core 2.0 SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="66d83-121">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="66d83-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="66d83-122">範本描述</span><span class="sxs-lookup"><span data-stu-id="66d83-122">Template description</span></span>                          | <span data-ttu-id="66d83-123">範本名稱</span><span class="sxs-lookup"><span data-stu-id="66d83-123">Template name</span></span>  | <span data-ttu-id="66d83-124">語言</span><span class="sxs-lookup"><span data-stu-id="66d83-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="66d83-125">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="66d83-125">Console application</span></span>                          | <span data-ttu-id="66d83-126">主控台</span><span class="sxs-lookup"><span data-stu-id="66d83-126">console</span></span>        | <span data-ttu-id="66d83-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="66d83-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="66d83-128">類別庫</span><span class="sxs-lookup"><span data-stu-id="66d83-128">Class library</span></span>                                | <span data-ttu-id="66d83-129">classlib</span><span class="sxs-lookup"><span data-stu-id="66d83-129">classlib</span></span>       | <span data-ttu-id="66d83-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="66d83-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="66d83-131">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="66d83-131">Unit test project</span></span>                            | <span data-ttu-id="66d83-132">mstest</span><span class="sxs-lookup"><span data-stu-id="66d83-132">mstest</span></span>         | <span data-ttu-id="66d83-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="66d83-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="66d83-134">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="66d83-134">xUnit test project</span></span>                           | <span data-ttu-id="66d83-135">xunit</span><span class="sxs-lookup"><span data-stu-id="66d83-135">xunit</span></span>          | <span data-ttu-id="66d83-136">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="66d83-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="66d83-137">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="66d83-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="66d83-138">web</span><span class="sxs-lookup"><span data-stu-id="66d83-138">web</span></span>            | <span data-ttu-id="66d83-139">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="66d83-139">[C#], F#</span></span>      |
| <span data-ttu-id="66d83-140">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="66d83-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="66d83-141">mvc</span><span class="sxs-lookup"><span data-stu-id="66d83-141">mvc</span></span>            | <span data-ttu-id="66d83-142">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="66d83-142">[C#], F#</span></span>      |
| <span data-ttu-id="66d83-143">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="66d83-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="66d83-144">razor</span><span class="sxs-lookup"><span data-stu-id="66d83-144">razor</span></span>          | <span data-ttu-id="66d83-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="66d83-145">[C#]</span></span>          |
| <span data-ttu-id="66d83-146">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="66d83-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="66d83-147">angular</span><span class="sxs-lookup"><span data-stu-id="66d83-147">angular</span></span>        | <span data-ttu-id="66d83-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="66d83-148">[C#]</span></span>          |
| <span data-ttu-id="66d83-149">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="66d83-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="66d83-150">react</span><span class="sxs-lookup"><span data-stu-id="66d83-150">react</span></span>          | <span data-ttu-id="66d83-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="66d83-151">[C#]</span></span>          |
| <span data-ttu-id="66d83-152">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="66d83-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="66d83-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="66d83-153">reactredux</span></span>     | <span data-ttu-id="66d83-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="66d83-154">[C#]</span></span>          |
| <span data-ttu-id="66d83-155">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="66d83-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="66d83-156">webapi</span><span class="sxs-lookup"><span data-stu-id="66d83-156">webapi</span></span>         | <span data-ttu-id="66d83-157">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="66d83-157">[C#], F#</span></span>      |
| <span data-ttu-id="66d83-158">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="66d83-158">global.json file</span></span>                             | <span data-ttu-id="66d83-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="66d83-159">globaljson</span></span>     |               |
| <span data-ttu-id="66d83-160">Nuget 組態</span><span class="sxs-lookup"><span data-stu-id="66d83-160">Nuget config</span></span>                                 | <span data-ttu-id="66d83-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="66d83-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="66d83-162">Web 組態</span><span class="sxs-lookup"><span data-stu-id="66d83-162">Web config</span></span>                                   | <span data-ttu-id="66d83-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="66d83-163">webconfig</span></span>      |               |
| <span data-ttu-id="66d83-164">方案檔</span><span class="sxs-lookup"><span data-stu-id="66d83-164">Solution file</span></span>                                | <span data-ttu-id="66d83-165">sln</span><span class="sxs-lookup"><span data-stu-id="66d83-165">sln</span></span>            |               |
| <span data-ttu-id="66d83-166">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="66d83-166">Razor page</span></span>                                   | <span data-ttu-id="66d83-167">頁面</span><span class="sxs-lookup"><span data-stu-id="66d83-167">page</span></span>           |               |
| <span data-ttu-id="66d83-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="66d83-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="66d83-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="66d83-169">viewimports</span></span>    |               |
| <span data-ttu-id="66d83-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="66d83-170">MVC ViewStart</span></span>                                | <span data-ttu-id="66d83-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="66d83-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="66d83-172">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="66d83-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="66d83-173">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="66d83-173">The command contains a default list of templates.</span></span> <span data-ttu-id="66d83-174">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="66d83-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="66d83-175">下表顯示隨 .NET Core 1.x SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="66d83-176">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="66d83-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="66d83-177">範本描述</span><span class="sxs-lookup"><span data-stu-id="66d83-177">Template description</span></span>  | <span data-ttu-id="66d83-178">範本名稱</span><span class="sxs-lookup"><span data-stu-id="66d83-178">Template name</span></span>  | <span data-ttu-id="66d83-179">語言</span><span class="sxs-lookup"><span data-stu-id="66d83-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="66d83-180">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="66d83-180">Console application</span></span>  | <span data-ttu-id="66d83-181">主控台</span><span class="sxs-lookup"><span data-stu-id="66d83-181">console</span></span>        | <span data-ttu-id="66d83-182">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="66d83-182">[C#], F#</span></span>  |
| <span data-ttu-id="66d83-183">類別庫</span><span class="sxs-lookup"><span data-stu-id="66d83-183">Class library</span></span>        | <span data-ttu-id="66d83-184">classlib</span><span class="sxs-lookup"><span data-stu-id="66d83-184">classlib</span></span>       | <span data-ttu-id="66d83-185">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="66d83-185">[C#], F#</span></span>  |
| <span data-ttu-id="66d83-186">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="66d83-186">Unit test project</span></span>    | <span data-ttu-id="66d83-187">mstest</span><span class="sxs-lookup"><span data-stu-id="66d83-187">mstest</span></span>         | <span data-ttu-id="66d83-188">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="66d83-188">[C#], F#</span></span>  |
| <span data-ttu-id="66d83-189">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="66d83-189">xUnit test project</span></span>   | <span data-ttu-id="66d83-190">xunit</span><span class="sxs-lookup"><span data-stu-id="66d83-190">xunit</span></span>          | <span data-ttu-id="66d83-191">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="66d83-191">[C#], F#</span></span>  |
| <span data-ttu-id="66d83-192">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="66d83-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="66d83-193">web</span><span class="sxs-lookup"><span data-stu-id="66d83-193">web</span></span>            | <span data-ttu-id="66d83-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="66d83-194">[C#]</span></span>      |
| <span data-ttu-id="66d83-195">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="66d83-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="66d83-196">mvc</span><span class="sxs-lookup"><span data-stu-id="66d83-196">mvc</span></span>            | <span data-ttu-id="66d83-197">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="66d83-197">[C#], F#</span></span>  |
| <span data-ttu-id="66d83-198">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="66d83-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="66d83-199">webapi</span><span class="sxs-lookup"><span data-stu-id="66d83-199">webapi</span></span>         | <span data-ttu-id="66d83-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="66d83-200">[C#]</span></span>      |
| <span data-ttu-id="66d83-201">Nuget 組態</span><span class="sxs-lookup"><span data-stu-id="66d83-201">Nuget config</span></span>         | <span data-ttu-id="66d83-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="66d83-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="66d83-203">Web 組態</span><span class="sxs-lookup"><span data-stu-id="66d83-203">Web config</span></span>           | <span data-ttu-id="66d83-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="66d83-204">webconfig</span></span>      |           |
| <span data-ttu-id="66d83-205">方案檔</span><span class="sxs-lookup"><span data-stu-id="66d83-205">Solution file</span></span>        | <span data-ttu-id="66d83-206">sln</span><span class="sxs-lookup"><span data-stu-id="66d83-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="66d83-207">選項</span><span class="sxs-lookup"><span data-stu-id="66d83-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="66d83-208">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="66d83-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="66d83-209">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="66d83-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="66d83-210">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="66d83-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="66d83-211">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="66d83-211">Prints out help for the command.</span></span> <span data-ttu-id="66d83-212">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="66d83-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="66d83-213">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="66d83-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="66d83-214">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="66d83-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="66d83-215">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="66d83-216">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="66d83-217">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="66d83-218">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="66d83-218">The language of the template to create.</span></span> <span data-ttu-id="66d83-219">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="66d83-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="66d83-220">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="66d83-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="66d83-221">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="66d83-221">The name for the created output.</span></span> <span data-ttu-id="66d83-222">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="66d83-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="66d83-223">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="66d83-223">Location to place the generated output.</span></span> <span data-ttu-id="66d83-224">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="66d83-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="66d83-225">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-225">Filters templates based on available types.</span></span> <span data-ttu-id="66d83-226">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="66d83-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="66d83-227">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="66d83-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="66d83-228">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="66d83-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="66d83-229">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="66d83-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="66d83-230">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="66d83-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="66d83-231">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="66d83-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="66d83-232">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="66d83-233">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="66d83-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="66d83-234">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="66d83-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="66d83-235">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="66d83-235">Prints out help for the command.</span></span> <span data-ttu-id="66d83-236">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="66d83-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="66d83-237">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="66d83-238">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="66d83-239">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="66d83-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="66d83-240">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="66d83-240">The language of the template to create.</span></span> <span data-ttu-id="66d83-241">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="66d83-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="66d83-242">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="66d83-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="66d83-243">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="66d83-243">The name for the created output.</span></span> <span data-ttu-id="66d83-244">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="66d83-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="66d83-245">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="66d83-245">Location to place the generated output.</span></span> <span data-ttu-id="66d83-246">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="66d83-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="66d83-247">範本選項</span><span class="sxs-lookup"><span data-stu-id="66d83-247">Template options</span></span>

<span data-ttu-id="66d83-248">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="66d83-248">Each project template may have additional options available.</span></span> <span data-ttu-id="66d83-249">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="66d83-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="66d83-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="66d83-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="66d83-251">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="66d83-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="66d83-252">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="66d83-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="66d83-253">**classlib**</span><span class="sxs-lookup"><span data-stu-id="66d83-253">**classlib**</span></span>

<span data-ttu-id="66d83-254">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="66d83-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="66d83-255">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="66d83-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="66d83-256">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="66d83-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="66d83-257">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="66d83-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="66d83-258">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="66d83-258">**mstest, xunit**</span></span>

<span data-ttu-id="66d83-259">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="66d83-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="66d83-260">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="66d83-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="66d83-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="66d83-261">**globaljson**</span></span>

<span data-ttu-id="66d83-262">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="66d83-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="66d83-263">**web**</span><span class="sxs-lookup"><span data-stu-id="66d83-263">**web**</span></span>

<span data-ttu-id="66d83-264">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="66d83-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="66d83-265">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="66d83-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="66d83-266">**webapi**</span><span class="sxs-lookup"><span data-stu-id="66d83-266">**webapi**</span></span>

<span data-ttu-id="66d83-267">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="66d83-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="66d83-268">可能值為：</span><span class="sxs-lookup"><span data-stu-id="66d83-268">The possible values are:</span></span>

- <span data-ttu-id="66d83-269">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="66d83-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="66d83-270">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="66d83-271">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="66d83-272">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="66d83-273">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="66d83-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="66d83-274">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="66d83-275">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="66d83-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="66d83-276">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="66d83-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="66d83-277">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="66d83-278">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="66d83-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="66d83-279">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="66d83-280">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="66d83-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="66d83-281">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="66d83-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="66d83-282">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="66d83-283">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="66d83-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="66d83-284">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="66d83-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="66d83-285">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="66d83-286">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="66d83-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="66d83-287">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="66d83-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="66d83-288">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="66d83-289">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="66d83-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="66d83-290">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="66d83-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="66d83-291">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="66d83-292">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="66d83-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="66d83-293">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="66d83-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="66d83-294">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="66d83-295">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="66d83-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="66d83-296">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="66d83-296">**mvc, razor**</span></span>

<span data-ttu-id="66d83-297">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="66d83-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="66d83-298">可能值為：</span><span class="sxs-lookup"><span data-stu-id="66d83-298">The possible values are:</span></span>

- <span data-ttu-id="66d83-299">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="66d83-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="66d83-300">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="66d83-301">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="66d83-302">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="66d83-303">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="66d83-304">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="66d83-305">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="66d83-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="66d83-306">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="66d83-307">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="66d83-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="66d83-308">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="66d83-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="66d83-309">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="66d83-310">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="66d83-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="66d83-311">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="66d83-312">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="66d83-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="66d83-313">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="66d83-314">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="66d83-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="66d83-315">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="66d83-316">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="66d83-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="66d83-317">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="66d83-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="66d83-318">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="66d83-319">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="66d83-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="66d83-320">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="66d83-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="66d83-321">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="66d83-322">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="66d83-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="66d83-323">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="66d83-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="66d83-324">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="66d83-325">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="66d83-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="66d83-326">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="66d83-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="66d83-327">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="66d83-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="66d83-328">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="66d83-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="66d83-329">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="66d83-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="66d83-330">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="66d83-331">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="66d83-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="66d83-332">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="66d83-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="66d83-333">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="66d83-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="66d83-334">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="66d83-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="66d83-335">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="66d83-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="66d83-336">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="66d83-336">**page**</span></span>

<span data-ttu-id="66d83-337">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="66d83-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="66d83-338">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="66d83-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="66d83-339">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="66d83-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="66d83-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="66d83-340">**viewimports**</span></span>

<span data-ttu-id="66d83-341">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="66d83-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="66d83-342">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="66d83-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="66d83-343">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="66d83-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="66d83-344">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="66d83-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="66d83-345">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="66d83-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="66d83-346">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="66d83-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="66d83-347">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="66d83-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="66d83-348">**classlib**</span><span class="sxs-lookup"><span data-stu-id="66d83-348">**classlib**</span></span>

<span data-ttu-id="66d83-349">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="66d83-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="66d83-350">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="66d83-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="66d83-351">預設值是 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="66d83-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="66d83-352">**mvc**</span><span class="sxs-lookup"><span data-stu-id="66d83-352">**mvc**</span></span>

<span data-ttu-id="66d83-353">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="66d83-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="66d83-354">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="66d83-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="66d83-355">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="66d83-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="66d83-356">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="66d83-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="66d83-357">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="66d83-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="66d83-358">預設值是 `None`。</span><span class="sxs-lookup"><span data-stu-id="66d83-358">The default value is `None`.</span></span>

<span data-ttu-id="66d83-359">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="66d83-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="66d83-360">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="66d83-360">Values: `true` or `false`.</span></span> <span data-ttu-id="66d83-361">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="66d83-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="66d83-362">範例</span><span class="sxs-lookup"><span data-stu-id="66d83-362">Examples</span></span>

<span data-ttu-id="66d83-363">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="66d83-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="66d83-364">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core 2.0 SDK 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="66d83-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="66d83-365">未經驗證即在目前的目錄中，建立以 .NET Core 2.0 為目標的新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="66d83-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="66d83-366">建立以 .NET Core 2.0 為目標的新 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="66d83-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="66d83-367">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="66d83-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="66d83-368">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66d83-368">See also</span></span>

[<span data-ttu-id="66d83-369">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="66d83-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="66d83-370">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="66d83-370">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
<span data-ttu-id="66d83-371">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="66d83-371">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
[<span data-ttu-id="66d83-372">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="66d83-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
