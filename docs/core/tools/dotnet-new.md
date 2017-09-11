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
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 335902f26148d8201b7311b57370fd37280c68dd
ms.contentlocale: zh-tw
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-new"></a><span data-ttu-id="62dd6-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="62dd6-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="62dd6-105">name</span><span class="sxs-lookup"><span data-stu-id="62dd6-105">Name</span></span>

<span data-ttu-id="62dd6-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="62dd6-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="62dd6-107">概要</span><span class="sxs-lookup"><span data-stu-id="62dd6-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="62dd6-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="62dd6-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="62dd6-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="62dd6-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="62dd6-110">說明</span><span class="sxs-lookup"><span data-stu-id="62dd6-110">Description</span></span>

<span data-ttu-id="62dd6-111">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="62dd6-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="62dd6-112">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="62dd6-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="62dd6-113">引數</span><span class="sxs-lookup"><span data-stu-id="62dd6-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="62dd6-114">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="62dd6-115">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="62dd6-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="62dd6-116">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="62dd6-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="62dd6-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="62dd6-118">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="62dd6-118">The command contains a default list of templates.</span></span> <span data-ttu-id="62dd6-119">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="62dd6-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="62dd6-120">下表顯示隨 .NET Core 2.0 SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="62dd6-121">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="62dd6-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="62dd6-122">範本描述</span><span class="sxs-lookup"><span data-stu-id="62dd6-122">Template description</span></span>                          | <span data-ttu-id="62dd6-123">範本名稱</span><span class="sxs-lookup"><span data-stu-id="62dd6-123">Template name</span></span>  | <span data-ttu-id="62dd6-124">語言</span><span class="sxs-lookup"><span data-stu-id="62dd6-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="62dd6-125">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="62dd6-125">Console application</span></span>                          | <span data-ttu-id="62dd6-126">主控台</span><span class="sxs-lookup"><span data-stu-id="62dd6-126">console</span></span>        | <span data-ttu-id="62dd6-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="62dd6-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="62dd6-128">類別庫</span><span class="sxs-lookup"><span data-stu-id="62dd6-128">Class library</span></span>                                | <span data-ttu-id="62dd6-129">classlib</span><span class="sxs-lookup"><span data-stu-id="62dd6-129">classlib</span></span>       | <span data-ttu-id="62dd6-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="62dd6-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="62dd6-131">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="62dd6-131">Unit test project</span></span>                            | <span data-ttu-id="62dd6-132">mstest</span><span class="sxs-lookup"><span data-stu-id="62dd6-132">mstest</span></span>         | <span data-ttu-id="62dd6-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="62dd6-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="62dd6-134">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="62dd6-134">xUnit test project</span></span>                           | <span data-ttu-id="62dd6-135">xunit</span><span class="sxs-lookup"><span data-stu-id="62dd6-135">xunit</span></span>          | <span data-ttu-id="62dd6-136">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="62dd6-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="62dd6-137">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="62dd6-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="62dd6-138">web</span><span class="sxs-lookup"><span data-stu-id="62dd6-138">web</span></span>            | <span data-ttu-id="62dd6-139">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="62dd6-139">[C#], F#</span></span>      |
| <span data-ttu-id="62dd6-140">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="62dd6-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="62dd6-141">mvc</span><span class="sxs-lookup"><span data-stu-id="62dd6-141">mvc</span></span>            | <span data-ttu-id="62dd6-142">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="62dd6-142">[C#], F#</span></span>      |
| <span data-ttu-id="62dd6-143">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="62dd6-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="62dd6-144">razor</span><span class="sxs-lookup"><span data-stu-id="62dd6-144">razor</span></span>          | <span data-ttu-id="62dd6-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="62dd6-145">[C#]</span></span>          |
| <span data-ttu-id="62dd6-146">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="62dd6-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="62dd6-147">angular</span><span class="sxs-lookup"><span data-stu-id="62dd6-147">angular</span></span>        | <span data-ttu-id="62dd6-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="62dd6-148">[C#]</span></span>          |
| <span data-ttu-id="62dd6-149">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="62dd6-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="62dd6-150">react</span><span class="sxs-lookup"><span data-stu-id="62dd6-150">react</span></span>          | <span data-ttu-id="62dd6-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="62dd6-151">[C#]</span></span>          |
| <span data-ttu-id="62dd6-152">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="62dd6-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="62dd6-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="62dd6-153">reactredux</span></span>     | <span data-ttu-id="62dd6-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="62dd6-154">[C#]</span></span>          |
| <span data-ttu-id="62dd6-155">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="62dd6-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="62dd6-156">webapi</span><span class="sxs-lookup"><span data-stu-id="62dd6-156">webapi</span></span>         | <span data-ttu-id="62dd6-157">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="62dd6-157">[C#], F#</span></span>      |
| <span data-ttu-id="62dd6-158">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="62dd6-158">global.json file</span></span>                             | <span data-ttu-id="62dd6-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="62dd6-159">globaljson</span></span>     |               |
| <span data-ttu-id="62dd6-160">Nuget 組態</span><span class="sxs-lookup"><span data-stu-id="62dd6-160">Nuget config</span></span>                                 | <span data-ttu-id="62dd6-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="62dd6-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="62dd6-162">Web 組態</span><span class="sxs-lookup"><span data-stu-id="62dd6-162">Web config</span></span>                                   | <span data-ttu-id="62dd6-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="62dd6-163">webconfig</span></span>      |               |
| <span data-ttu-id="62dd6-164">方案檔</span><span class="sxs-lookup"><span data-stu-id="62dd6-164">Solution file</span></span>                                | <span data-ttu-id="62dd6-165">sln</span><span class="sxs-lookup"><span data-stu-id="62dd6-165">sln</span></span>            |               |
| <span data-ttu-id="62dd6-166">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="62dd6-166">Razor page</span></span>                                   | <span data-ttu-id="62dd6-167">頁面</span><span class="sxs-lookup"><span data-stu-id="62dd6-167">page</span></span>           |               |
| <span data-ttu-id="62dd6-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="62dd6-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="62dd6-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="62dd6-169">viewimports</span></span>    |               |
| <span data-ttu-id="62dd6-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="62dd6-170">MVC ViewStart</span></span>                                | <span data-ttu-id="62dd6-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="62dd6-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="62dd6-172">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="62dd6-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="62dd6-173">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="62dd6-173">The command contains a default list of templates.</span></span> <span data-ttu-id="62dd6-174">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="62dd6-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="62dd6-175">下表顯示隨 .NET Core 1.x SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="62dd6-176">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="62dd6-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="62dd6-177">範本描述</span><span class="sxs-lookup"><span data-stu-id="62dd6-177">Template description</span></span>  | <span data-ttu-id="62dd6-178">範本名稱</span><span class="sxs-lookup"><span data-stu-id="62dd6-178">Template name</span></span>  | <span data-ttu-id="62dd6-179">語言</span><span class="sxs-lookup"><span data-stu-id="62dd6-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="62dd6-180">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="62dd6-180">Console application</span></span>  | <span data-ttu-id="62dd6-181">主控台</span><span class="sxs-lookup"><span data-stu-id="62dd6-181">console</span></span>        | <span data-ttu-id="62dd6-182">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="62dd6-182">[C#], F#</span></span>  |
| <span data-ttu-id="62dd6-183">類別庫</span><span class="sxs-lookup"><span data-stu-id="62dd6-183">Class library</span></span>        | <span data-ttu-id="62dd6-184">classlib</span><span class="sxs-lookup"><span data-stu-id="62dd6-184">classlib</span></span>       | <span data-ttu-id="62dd6-185">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="62dd6-185">[C#], F#</span></span>  |
| <span data-ttu-id="62dd6-186">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="62dd6-186">Unit test project</span></span>    | <span data-ttu-id="62dd6-187">mstest</span><span class="sxs-lookup"><span data-stu-id="62dd6-187">mstest</span></span>         | <span data-ttu-id="62dd6-188">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="62dd6-188">[C#], F#</span></span>  |
| <span data-ttu-id="62dd6-189">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="62dd6-189">xUnit test project</span></span>   | <span data-ttu-id="62dd6-190">xunit</span><span class="sxs-lookup"><span data-stu-id="62dd6-190">xunit</span></span>          | <span data-ttu-id="62dd6-191">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="62dd6-191">[C#], F#</span></span>  |
| <span data-ttu-id="62dd6-192">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="62dd6-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="62dd6-193">web</span><span class="sxs-lookup"><span data-stu-id="62dd6-193">web</span></span>            | <span data-ttu-id="62dd6-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="62dd6-194">[C#]</span></span>      |
| <span data-ttu-id="62dd6-195">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="62dd6-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="62dd6-196">mvc</span><span class="sxs-lookup"><span data-stu-id="62dd6-196">mvc</span></span>            | <span data-ttu-id="62dd6-197">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="62dd6-197">[C#], F#</span></span>  |
| <span data-ttu-id="62dd6-198">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="62dd6-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="62dd6-199">webapi</span><span class="sxs-lookup"><span data-stu-id="62dd6-199">webapi</span></span>         | <span data-ttu-id="62dd6-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="62dd6-200">[C#]</span></span>      |
| <span data-ttu-id="62dd6-201">Nuget 組態</span><span class="sxs-lookup"><span data-stu-id="62dd6-201">Nuget config</span></span>         | <span data-ttu-id="62dd6-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="62dd6-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="62dd6-203">Web 組態</span><span class="sxs-lookup"><span data-stu-id="62dd6-203">Web config</span></span>           | <span data-ttu-id="62dd6-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="62dd6-204">webconfig</span></span>      |           |
| <span data-ttu-id="62dd6-205">方案檔</span><span class="sxs-lookup"><span data-stu-id="62dd6-205">Solution file</span></span>        | <span data-ttu-id="62dd6-206">sln</span><span class="sxs-lookup"><span data-stu-id="62dd6-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="62dd6-207">選項</span><span class="sxs-lookup"><span data-stu-id="62dd6-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="62dd6-208">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="62dd6-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="62dd6-209">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="62dd6-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="62dd6-210">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="62dd6-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="62dd6-211">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="62dd6-211">Prints out help for the command.</span></span> <span data-ttu-id="62dd6-212">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="62dd6-213">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="62dd6-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="62dd6-214">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="62dd6-215">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="62dd6-216">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="62dd6-217">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="62dd6-218">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="62dd6-218">The language of the template to create.</span></span> <span data-ttu-id="62dd6-219">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="62dd6-220">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="62dd6-221">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="62dd6-221">The name for the created output.</span></span> <span data-ttu-id="62dd6-222">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="62dd6-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="62dd6-223">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="62dd6-223">Location to place the generated output.</span></span> <span data-ttu-id="62dd6-224">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="62dd6-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="62dd6-225">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-225">Filters templates based on available types.</span></span> <span data-ttu-id="62dd6-226">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="62dd6-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="62dd6-227">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="62dd6-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="62dd6-228">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="62dd6-228">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="62dd6-229">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-229">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="62dd6-230">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="62dd6-230">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="62dd6-231">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="62dd6-231">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="62dd6-232">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="62dd6-232">Prints out help for the command.</span></span> <span data-ttu-id="62dd6-233">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-233">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="62dd6-234">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-234">Lists templates containing the specified name.</span></span> <span data-ttu-id="62dd6-235">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-235">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="62dd6-236">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-236">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="62dd6-237">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="62dd6-237">The language of the template to create.</span></span> <span data-ttu-id="62dd6-238">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-238">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="62dd6-239">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-239">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="62dd6-240">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="62dd6-240">The name for the created output.</span></span> <span data-ttu-id="62dd6-241">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="62dd6-241">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="62dd6-242">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="62dd6-242">Location to place the generated output.</span></span> <span data-ttu-id="62dd6-243">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="62dd6-243">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="62dd6-244">範本選項</span><span class="sxs-lookup"><span data-stu-id="62dd6-244">Template options</span></span>

<span data-ttu-id="62dd6-245">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="62dd6-245">Each project template may have additional options available.</span></span> <span data-ttu-id="62dd6-246">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="62dd6-246">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="62dd6-247">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="62dd6-247">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="62dd6-248">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="62dd6-248">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="62dd6-249">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="62dd6-249">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="62dd6-250">**classlib**</span><span class="sxs-lookup"><span data-stu-id="62dd6-250">**classlib**</span></span>

<span data-ttu-id="62dd6-251">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-251">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="62dd6-252">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="62dd6-252">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="62dd6-253">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-253">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="62dd6-254">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="62dd6-254">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="62dd6-255">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="62dd6-255">**mstest, xunit**</span></span>

<span data-ttu-id="62dd6-256">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="62dd6-256">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="62dd6-257">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="62dd6-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="62dd6-258">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="62dd6-258">**globaljson**</span></span>

<span data-ttu-id="62dd6-259">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="62dd6-259">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="62dd6-260">**web**</span><span class="sxs-lookup"><span data-stu-id="62dd6-260">**web**</span></span>

<span data-ttu-id="62dd6-261">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="62dd6-261">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="62dd6-262">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="62dd6-262">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="62dd6-263">**webapi**</span><span class="sxs-lookup"><span data-stu-id="62dd6-263">**webapi**</span></span>

<span data-ttu-id="62dd6-264">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="62dd6-264">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="62dd6-265">可能值為：</span><span class="sxs-lookup"><span data-stu-id="62dd6-265">The possible values are:</span></span>

- <span data-ttu-id="62dd6-266">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-266">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="62dd6-267">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-267">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="62dd6-268">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-268">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="62dd6-269">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-269">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="62dd6-270">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="62dd6-270">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="62dd6-271">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-271">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="62dd6-272">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-272">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="62dd6-273">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="62dd6-273">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="62dd6-274">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-274">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="62dd6-275">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="62dd6-275">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="62dd6-276">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-276">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="62dd6-277">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-277">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="62dd6-278">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="62dd6-278">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="62dd6-279">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-279">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="62dd6-280">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-280">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="62dd6-281">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="62dd6-281">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="62dd6-282">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-282">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="62dd6-283">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-283">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="62dd6-284">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="62dd6-284">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="62dd6-285">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-285">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="62dd6-286">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-286">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="62dd6-287">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="62dd6-287">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="62dd6-288">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-288">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="62dd6-289">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="62dd6-289">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="62dd6-290">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="62dd6-290">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="62dd6-291">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-291">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="62dd6-292">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="62dd6-292">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="62dd6-293">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="62dd6-293">**mvc, razor**</span></span>

<span data-ttu-id="62dd6-294">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="62dd6-294">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="62dd6-295">可能值為：</span><span class="sxs-lookup"><span data-stu-id="62dd6-295">The possible values are:</span></span>

- <span data-ttu-id="62dd6-296">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-296">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="62dd6-297">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-297">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="62dd6-298">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-298">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="62dd6-299">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-299">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="62dd6-300">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-300">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="62dd6-301">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-301">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="62dd6-302">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="62dd6-302">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="62dd6-303">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-303">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="62dd6-304">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-304">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="62dd6-305">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="62dd6-305">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="62dd6-306">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-306">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="62dd6-307">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="62dd6-307">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="62dd6-308">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-308">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="62dd6-309">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="62dd6-309">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="62dd6-310">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-310">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="62dd6-311">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="62dd6-311">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="62dd6-312">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-312">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="62dd6-313">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-313">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="62dd6-314">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="62dd6-314">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="62dd6-315">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-315">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="62dd6-316">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-316">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="62dd6-317">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="62dd6-317">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="62dd6-318">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-318">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="62dd6-319">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-319">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="62dd6-320">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="62dd6-320">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="62dd6-321">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-321">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="62dd6-322">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-322">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="62dd6-323">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="62dd6-323">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="62dd6-324">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="62dd6-324">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="62dd6-325">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-325">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="62dd6-326">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="62dd6-326">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="62dd6-327">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-327">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="62dd6-328">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="62dd6-328">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="62dd6-329">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="62dd6-329">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="62dd6-330">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="62dd6-330">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="62dd6-331">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="62dd6-331">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="62dd6-332">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="62dd6-332">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="62dd6-333">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="62dd6-333">**page**</span></span>

<span data-ttu-id="62dd6-334">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="62dd6-334">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="62dd6-335">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-335">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="62dd6-336">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="62dd6-336">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="62dd6-337">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="62dd6-337">**viewimports**</span></span>

<span data-ttu-id="62dd6-338">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="62dd6-338">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="62dd6-339">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-339">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="62dd6-340">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="62dd6-340">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="62dd6-341">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="62dd6-341">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="62dd6-342">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-342">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="62dd6-343">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-343">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="62dd6-344">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-344">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="62dd6-345">**classlib**</span><span class="sxs-lookup"><span data-stu-id="62dd6-345">**classlib**</span></span>

<span data-ttu-id="62dd6-346">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-346">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="62dd6-347">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-347">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="62dd6-348">預設值是 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-348">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="62dd6-349">**mvc**</span><span class="sxs-lookup"><span data-stu-id="62dd6-349">**mvc**</span></span>

<span data-ttu-id="62dd6-350">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-350">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="62dd6-351">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-351">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="62dd6-352">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-352">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="62dd6-353">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="62dd6-353">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="62dd6-354">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-354">Values: `None` or `Individual`.</span></span> <span data-ttu-id="62dd6-355">預設值是 `None`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-355">The default value is `None`.</span></span>

<span data-ttu-id="62dd6-356">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="62dd6-356">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="62dd6-357">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-357">Values: `true` or `false`.</span></span> <span data-ttu-id="62dd6-358">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="62dd6-358">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="62dd6-359">範例</span><span class="sxs-lookup"><span data-stu-id="62dd6-359">Examples</span></span>

<span data-ttu-id="62dd6-360">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="62dd6-360">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="62dd6-361">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core 2.0 SDK 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="62dd6-361">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="62dd6-362">未經驗證即在目前的目錄中，建立以 .NET Core 2.0 為目標的新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="62dd6-362">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="62dd6-363">建立以 .NET Core 2.0 為目標的新 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="62dd6-363">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="62dd6-364">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="62dd6-364">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="62dd6-365">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62dd6-365">See also</span></span>

[<span data-ttu-id="62dd6-366">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="62dd6-366">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="62dd6-367">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="62dd6-367">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
<span data-ttu-id="62dd6-368">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="62dd6-368">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
[<span data-ttu-id="62dd6-369">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="62dd6-369">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)

