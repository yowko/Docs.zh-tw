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
ms.workload: dotnetcore
ms.openlocfilehash: f5815e1ad2a36a8ef3279f6ff83465dba9ec5d50
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="07024-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="07024-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="07024-105">名稱</span><span class="sxs-lookup"><span data-stu-id="07024-105">Name</span></span>

<span data-ttu-id="07024-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="07024-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="07024-107">概要</span><span class="sxs-lookup"><span data-stu-id="07024-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="07024-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="07024-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="07024-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="07024-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="07024-110">描述</span><span class="sxs-lookup"><span data-stu-id="07024-110">Description</span></span>

<span data-ttu-id="07024-111">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="07024-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="07024-112">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="07024-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="07024-113">引數</span><span class="sxs-lookup"><span data-stu-id="07024-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="07024-114">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="07024-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="07024-115">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="07024-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="07024-116">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="07024-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="07024-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="07024-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="07024-118">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="07024-118">The command contains a default list of templates.</span></span> <span data-ttu-id="07024-119">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="07024-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="07024-120">下表顯示隨 .NET Core 2.0 SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="07024-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="07024-121">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="07024-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="07024-122">範本描述</span><span class="sxs-lookup"><span data-stu-id="07024-122">Template description</span></span>                          | <span data-ttu-id="07024-123">範本名稱</span><span class="sxs-lookup"><span data-stu-id="07024-123">Template name</span></span>  | <span data-ttu-id="07024-124">語言</span><span class="sxs-lookup"><span data-stu-id="07024-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="07024-125">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="07024-125">Console application</span></span>                          | <span data-ttu-id="07024-126">主控台</span><span class="sxs-lookup"><span data-stu-id="07024-126">console</span></span>        | <span data-ttu-id="07024-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="07024-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="07024-128">類別庫</span><span class="sxs-lookup"><span data-stu-id="07024-128">Class library</span></span>                                | <span data-ttu-id="07024-129">classlib</span><span class="sxs-lookup"><span data-stu-id="07024-129">classlib</span></span>       | <span data-ttu-id="07024-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="07024-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="07024-131">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="07024-131">Unit test project</span></span>                            | <span data-ttu-id="07024-132">mstest</span><span class="sxs-lookup"><span data-stu-id="07024-132">mstest</span></span>         | <span data-ttu-id="07024-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="07024-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="07024-134">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="07024-134">xUnit test project</span></span>                           | <span data-ttu-id="07024-135">xunit</span><span class="sxs-lookup"><span data-stu-id="07024-135">xunit</span></span>          | <span data-ttu-id="07024-136">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="07024-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="07024-137">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="07024-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="07024-138">web</span><span class="sxs-lookup"><span data-stu-id="07024-138">web</span></span>            | <span data-ttu-id="07024-139">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="07024-139">[C#], F#</span></span>      |
| <span data-ttu-id="07024-140">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="07024-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="07024-141">mvc</span><span class="sxs-lookup"><span data-stu-id="07024-141">mvc</span></span>            | <span data-ttu-id="07024-142">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="07024-142">[C#], F#</span></span>      |
| <span data-ttu-id="07024-143">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="07024-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="07024-144">razor</span><span class="sxs-lookup"><span data-stu-id="07024-144">razor</span></span>          | <span data-ttu-id="07024-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="07024-145">[C#]</span></span>          |
| <span data-ttu-id="07024-146">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="07024-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="07024-147">angular</span><span class="sxs-lookup"><span data-stu-id="07024-147">angular</span></span>        | <span data-ttu-id="07024-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="07024-148">[C#]</span></span>          |
| <span data-ttu-id="07024-149">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="07024-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="07024-150">react</span><span class="sxs-lookup"><span data-stu-id="07024-150">react</span></span>          | <span data-ttu-id="07024-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="07024-151">[C#]</span></span>          |
| <span data-ttu-id="07024-152">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="07024-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="07024-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="07024-153">reactredux</span></span>     | <span data-ttu-id="07024-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="07024-154">[C#]</span></span>          |
| <span data-ttu-id="07024-155">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="07024-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="07024-156">webapi</span><span class="sxs-lookup"><span data-stu-id="07024-156">webapi</span></span>         | <span data-ttu-id="07024-157">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="07024-157">[C#], F#</span></span>      |
| <span data-ttu-id="07024-158">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="07024-158">global.json file</span></span>                             | <span data-ttu-id="07024-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="07024-159">globaljson</span></span>     |               |
| <span data-ttu-id="07024-160">Nuget 組態</span><span class="sxs-lookup"><span data-stu-id="07024-160">Nuget config</span></span>                                 | <span data-ttu-id="07024-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="07024-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="07024-162">Web 組態</span><span class="sxs-lookup"><span data-stu-id="07024-162">Web config</span></span>                                   | <span data-ttu-id="07024-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="07024-163">webconfig</span></span>      |               |
| <span data-ttu-id="07024-164">方案檔</span><span class="sxs-lookup"><span data-stu-id="07024-164">Solution file</span></span>                                | <span data-ttu-id="07024-165">sln</span><span class="sxs-lookup"><span data-stu-id="07024-165">sln</span></span>            |               |
| <span data-ttu-id="07024-166">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="07024-166">Razor page</span></span>                                   | <span data-ttu-id="07024-167">頁面</span><span class="sxs-lookup"><span data-stu-id="07024-167">page</span></span>           |               |
| <span data-ttu-id="07024-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="07024-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="07024-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="07024-169">viewimports</span></span>    |               |
| <span data-ttu-id="07024-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="07024-170">MVC ViewStart</span></span>                                | <span data-ttu-id="07024-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="07024-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="07024-172">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="07024-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="07024-173">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="07024-173">The command contains a default list of templates.</span></span> <span data-ttu-id="07024-174">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="07024-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="07024-175">下表顯示隨 .NET Core 1.x SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="07024-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="07024-176">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="07024-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="07024-177">範本描述</span><span class="sxs-lookup"><span data-stu-id="07024-177">Template description</span></span>  | <span data-ttu-id="07024-178">範本名稱</span><span class="sxs-lookup"><span data-stu-id="07024-178">Template name</span></span>  | <span data-ttu-id="07024-179">語言</span><span class="sxs-lookup"><span data-stu-id="07024-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="07024-180">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="07024-180">Console application</span></span>  | <span data-ttu-id="07024-181">主控台</span><span class="sxs-lookup"><span data-stu-id="07024-181">console</span></span>        | <span data-ttu-id="07024-182">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="07024-182">[C#], F#</span></span>  |
| <span data-ttu-id="07024-183">類別庫</span><span class="sxs-lookup"><span data-stu-id="07024-183">Class library</span></span>        | <span data-ttu-id="07024-184">classlib</span><span class="sxs-lookup"><span data-stu-id="07024-184">classlib</span></span>       | <span data-ttu-id="07024-185">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="07024-185">[C#], F#</span></span>  |
| <span data-ttu-id="07024-186">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="07024-186">Unit test project</span></span>    | <span data-ttu-id="07024-187">mstest</span><span class="sxs-lookup"><span data-stu-id="07024-187">mstest</span></span>         | <span data-ttu-id="07024-188">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="07024-188">[C#], F#</span></span>  |
| <span data-ttu-id="07024-189">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="07024-189">xUnit test project</span></span>   | <span data-ttu-id="07024-190">xunit</span><span class="sxs-lookup"><span data-stu-id="07024-190">xunit</span></span>          | <span data-ttu-id="07024-191">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="07024-191">[C#], F#</span></span>  |
| <span data-ttu-id="07024-192">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="07024-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="07024-193">web</span><span class="sxs-lookup"><span data-stu-id="07024-193">web</span></span>            | <span data-ttu-id="07024-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="07024-194">[C#]</span></span>      |
| <span data-ttu-id="07024-195">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="07024-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="07024-196">mvc</span><span class="sxs-lookup"><span data-stu-id="07024-196">mvc</span></span>            | <span data-ttu-id="07024-197">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="07024-197">[C#], F#</span></span>  |
| <span data-ttu-id="07024-198">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="07024-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="07024-199">webapi</span><span class="sxs-lookup"><span data-stu-id="07024-199">webapi</span></span>         | <span data-ttu-id="07024-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="07024-200">[C#]</span></span>      |
| <span data-ttu-id="07024-201">Nuget 組態</span><span class="sxs-lookup"><span data-stu-id="07024-201">Nuget config</span></span>         | <span data-ttu-id="07024-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="07024-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="07024-203">Web 組態</span><span class="sxs-lookup"><span data-stu-id="07024-203">Web config</span></span>           | <span data-ttu-id="07024-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="07024-204">webconfig</span></span>      |           |
| <span data-ttu-id="07024-205">方案檔</span><span class="sxs-lookup"><span data-stu-id="07024-205">Solution file</span></span>        | <span data-ttu-id="07024-206">sln</span><span class="sxs-lookup"><span data-stu-id="07024-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="07024-207">選項</span><span class="sxs-lookup"><span data-stu-id="07024-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="07024-208">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="07024-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="07024-209">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="07024-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="07024-210">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="07024-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="07024-211">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="07024-211">Prints out help for the command.</span></span> <span data-ttu-id="07024-212">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="07024-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="07024-213">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="07024-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="07024-214">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="07024-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="07024-215">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="07024-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="07024-216">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="07024-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="07024-217">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="07024-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="07024-218">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="07024-218">The language of the template to create.</span></span> <span data-ttu-id="07024-219">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="07024-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="07024-220">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="07024-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="07024-221">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="07024-221">The name for the created output.</span></span> <span data-ttu-id="07024-222">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="07024-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="07024-223">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="07024-223">Location to place the generated output.</span></span> <span data-ttu-id="07024-224">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="07024-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="07024-225">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="07024-225">Filters templates based on available types.</span></span> <span data-ttu-id="07024-226">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="07024-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="07024-227">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="07024-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="07024-228">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="07024-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="07024-229">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="07024-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="07024-230">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="07024-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="07024-231">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="07024-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="07024-232">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="07024-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="07024-233">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="07024-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="07024-234">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="07024-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="07024-235">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="07024-235">Prints out help for the command.</span></span> <span data-ttu-id="07024-236">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="07024-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="07024-237">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="07024-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="07024-238">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="07024-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="07024-239">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="07024-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="07024-240">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="07024-240">The language of the template to create.</span></span> <span data-ttu-id="07024-241">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="07024-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="07024-242">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="07024-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="07024-243">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="07024-243">The name for the created output.</span></span> <span data-ttu-id="07024-244">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="07024-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="07024-245">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="07024-245">Location to place the generated output.</span></span> <span data-ttu-id="07024-246">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="07024-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="07024-247">範本選項</span><span class="sxs-lookup"><span data-stu-id="07024-247">Template options</span></span>

<span data-ttu-id="07024-248">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="07024-248">Each project template may have additional options available.</span></span> <span data-ttu-id="07024-249">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="07024-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="07024-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="07024-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="07024-251">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="07024-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="07024-252">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="07024-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="07024-253">**classlib**</span><span class="sxs-lookup"><span data-stu-id="07024-253">**classlib**</span></span>

<span data-ttu-id="07024-254">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="07024-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07024-255">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="07024-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="07024-256">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="07024-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="07024-257">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="07024-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="07024-258">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="07024-258">**mstest, xunit**</span></span>

<span data-ttu-id="07024-259">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="07024-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="07024-260">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="07024-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="07024-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="07024-261">**globaljson**</span></span>

<span data-ttu-id="07024-262">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="07024-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="07024-263">**web**</span><span class="sxs-lookup"><span data-stu-id="07024-263">**web**</span></span>

<span data-ttu-id="07024-264">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="07024-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="07024-265">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="07024-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="07024-266">**webapi**</span><span class="sxs-lookup"><span data-stu-id="07024-266">**webapi**</span></span>

<span data-ttu-id="07024-267">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="07024-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="07024-268">可能值為：</span><span class="sxs-lookup"><span data-stu-id="07024-268">The possible values are:</span></span>

- <span data-ttu-id="07024-269">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="07024-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="07024-270">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="07024-271">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="07024-272">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="07024-273">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="07024-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="07024-274">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="07024-275">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="07024-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="07024-276">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="07024-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="07024-277">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="07024-278">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="07024-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="07024-279">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="07024-280">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="07024-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="07024-281">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="07024-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="07024-282">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="07024-283">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="07024-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="07024-284">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="07024-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="07024-285">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="07024-286">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="07024-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="07024-287">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="07024-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="07024-288">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="07024-289">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="07024-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="07024-290">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="07024-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="07024-291">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="07024-292">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="07024-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="07024-293">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="07024-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="07024-294">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="07024-295">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="07024-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="07024-296">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="07024-296">**mvc, razor**</span></span>

<span data-ttu-id="07024-297">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="07024-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="07024-298">可能值為：</span><span class="sxs-lookup"><span data-stu-id="07024-298">The possible values are:</span></span>

- <span data-ttu-id="07024-299">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="07024-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="07024-300">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="07024-301">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="07024-302">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="07024-303">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="07024-304">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="07024-305">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="07024-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="07024-306">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="07024-307">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="07024-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="07024-308">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="07024-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="07024-309">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="07024-310">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="07024-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="07024-311">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="07024-312">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="07024-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="07024-313">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="07024-314">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="07024-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="07024-315">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="07024-316">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="07024-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="07024-317">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="07024-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="07024-318">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="07024-319">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="07024-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="07024-320">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="07024-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="07024-321">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="07024-322">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="07024-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="07024-323">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="07024-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="07024-324">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="07024-325">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="07024-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="07024-326">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="07024-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="07024-327">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="07024-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="07024-328">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="07024-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="07024-329">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="07024-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="07024-330">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="07024-331">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="07024-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="07024-332">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="07024-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="07024-333">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="07024-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="07024-334">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="07024-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="07024-335">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="07024-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="07024-336">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="07024-336">**page**</span></span>

<span data-ttu-id="07024-337">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="07024-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="07024-338">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="07024-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="07024-339">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="07024-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="07024-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="07024-340">**viewimports**</span></span>

<span data-ttu-id="07024-341">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="07024-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="07024-342">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="07024-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="07024-343">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="07024-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="07024-344">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="07024-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="07024-345">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="07024-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07024-346">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="07024-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="07024-347">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="07024-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="07024-348">**classlib**</span><span class="sxs-lookup"><span data-stu-id="07024-348">**classlib**</span></span>

<span data-ttu-id="07024-349">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="07024-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07024-350">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="07024-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="07024-351">預設值是 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="07024-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="07024-352">**mvc**</span><span class="sxs-lookup"><span data-stu-id="07024-352">**mvc**</span></span>

<span data-ttu-id="07024-353">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="07024-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07024-354">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="07024-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="07024-355">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="07024-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="07024-356">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="07024-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="07024-357">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="07024-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="07024-358">預設值是 `None`。</span><span class="sxs-lookup"><span data-stu-id="07024-358">The default value is `None`.</span></span>

<span data-ttu-id="07024-359">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="07024-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="07024-360">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="07024-360">Values: `true` or `false`.</span></span> <span data-ttu-id="07024-361">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="07024-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="07024-362">範例</span><span class="sxs-lookup"><span data-stu-id="07024-362">Examples</span></span>

<span data-ttu-id="07024-363">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="07024-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="07024-364">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core 2.0 SDK 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="07024-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="07024-365">未經驗證即在目前的目錄中，建立以 .NET Core 2.0 為目標的新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="07024-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="07024-366">建立以 .NET Core 2.0 為目標的新 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="07024-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="07024-367">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="07024-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="07024-368">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07024-368">See also</span></span>

[<span data-ttu-id="07024-369">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="07024-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="07024-370">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="07024-370">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
<span data-ttu-id="07024-371">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="07024-371">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
[<span data-ttu-id="07024-372">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="07024-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
