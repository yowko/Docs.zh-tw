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
ms.openlocfilehash: cf65dc80f135badcb1580726a12a9ae9d94ae3d7
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="ce27d-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ce27d-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ce27d-105">名稱</span><span class="sxs-lookup"><span data-stu-id="ce27d-105">Name</span></span>

<span data-ttu-id="ce27d-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="ce27d-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ce27d-107">概要</span><span class="sxs-lookup"><span data-stu-id="ce27d-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ce27d-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ce27d-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ce27d-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ce27d-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="ce27d-110">描述</span><span class="sxs-lookup"><span data-stu-id="ce27d-110">Description</span></span>

<span data-ttu-id="ce27d-111">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="ce27d-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="ce27d-112">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="ce27d-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="ce27d-113">引數</span><span class="sxs-lookup"><span data-stu-id="ce27d-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="ce27d-114">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ce27d-115">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="ce27d-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ce27d-116">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="ce27d-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ce27d-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ce27d-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ce27d-118">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="ce27d-118">The command contains a default list of templates.</span></span> <span data-ttu-id="ce27d-119">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="ce27d-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ce27d-120">下表顯示隨 .NET Core 2.0 SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="ce27d-121">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="ce27d-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="ce27d-122">範本描述</span><span class="sxs-lookup"><span data-stu-id="ce27d-122">Template description</span></span>                          | <span data-ttu-id="ce27d-123">範本名稱</span><span class="sxs-lookup"><span data-stu-id="ce27d-123">Template name</span></span> | <span data-ttu-id="ce27d-124">語言</span><span class="sxs-lookup"><span data-stu-id="ce27d-124">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="ce27d-125">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ce27d-125">Console application</span></span>                          | `console`     | <span data-ttu-id="ce27d-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ce27d-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ce27d-127">類別庫</span><span class="sxs-lookup"><span data-stu-id="ce27d-127">Class library</span></span>                                | `classlib`    | <span data-ttu-id="ce27d-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ce27d-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ce27d-129">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="ce27d-129">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="ce27d-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ce27d-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ce27d-131">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="ce27d-131">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="ce27d-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ce27d-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ce27d-133">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce27d-133">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="ce27d-134">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ce27d-134">[C#], F#</span></span>      |
| <span data-ttu-id="ce27d-135">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="ce27d-135">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="ce27d-136">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ce27d-136">[C#], F#</span></span>      |
| <span data-ttu-id="ce27d-137">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="ce27d-137">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="ce27d-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce27d-138">[C#]</span></span>          |
| <span data-ttu-id="ce27d-139">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="ce27d-139">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="ce27d-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce27d-140">[C#]</span></span>          |
| <span data-ttu-id="ce27d-141">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="ce27d-141">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="ce27d-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce27d-142">[C#]</span></span>          |
| <span data-ttu-id="ce27d-143">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="ce27d-143">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="ce27d-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce27d-144">[C#]</span></span>          |
| <span data-ttu-id="ce27d-145">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="ce27d-145">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="ce27d-146">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ce27d-146">[C#], F#</span></span>      |
| <span data-ttu-id="ce27d-147">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="ce27d-147">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="ce27d-148">Nuget 組態</span><span class="sxs-lookup"><span data-stu-id="ce27d-148">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="ce27d-149">Web 組態</span><span class="sxs-lookup"><span data-stu-id="ce27d-149">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="ce27d-150">方案檔</span><span class="sxs-lookup"><span data-stu-id="ce27d-150">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="ce27d-151">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="ce27d-151">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="ce27d-152">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="ce27d-152">MVC/ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="ce27d-153">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ce27d-153">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ce27d-154">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ce27d-154">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ce27d-155">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="ce27d-155">The command contains a default list of templates.</span></span> <span data-ttu-id="ce27d-156">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="ce27d-156">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="ce27d-157">下表顯示隨 .NET Core 1.x SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-157">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="ce27d-158">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="ce27d-158">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="ce27d-159">範本描述</span><span class="sxs-lookup"><span data-stu-id="ce27d-159">Template description</span></span>  | <span data-ttu-id="ce27d-160">範本名稱</span><span class="sxs-lookup"><span data-stu-id="ce27d-160">Template name</span></span> | <span data-ttu-id="ce27d-161">語言</span><span class="sxs-lookup"><span data-stu-id="ce27d-161">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="ce27d-162">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ce27d-162">Console application</span></span>  | `console`     | <span data-ttu-id="ce27d-163">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ce27d-163">[C#], F#</span></span>  |
| <span data-ttu-id="ce27d-164">類別庫</span><span class="sxs-lookup"><span data-stu-id="ce27d-164">Class library</span></span>        | `classlib`    | <span data-ttu-id="ce27d-165">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ce27d-165">[C#], F#</span></span>  |
| <span data-ttu-id="ce27d-166">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="ce27d-166">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="ce27d-167">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ce27d-167">[C#], F#</span></span>  |
| <span data-ttu-id="ce27d-168">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="ce27d-168">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="ce27d-169">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ce27d-169">[C#], F#</span></span>  |
| <span data-ttu-id="ce27d-170">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce27d-170">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="ce27d-171">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce27d-171">[C#]</span></span>      |
| <span data-ttu-id="ce27d-172">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="ce27d-172">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="ce27d-173">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ce27d-173">[C#], F#</span></span>  |
| <span data-ttu-id="ce27d-174">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="ce27d-174">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="ce27d-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce27d-175">[C#]</span></span>      |
| <span data-ttu-id="ce27d-176">Nuget 組態</span><span class="sxs-lookup"><span data-stu-id="ce27d-176">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="ce27d-177">Web 組態</span><span class="sxs-lookup"><span data-stu-id="ce27d-177">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="ce27d-178">方案檔</span><span class="sxs-lookup"><span data-stu-id="ce27d-178">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="ce27d-179">選項</span><span class="sxs-lookup"><span data-stu-id="ce27d-179">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ce27d-180">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ce27d-180">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="ce27d-181">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="ce27d-181">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ce27d-182">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="ce27d-182">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ce27d-183">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="ce27d-183">Prints out help for the command.</span></span> <span data-ttu-id="ce27d-184">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-184">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ce27d-185">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="ce27d-185">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ce27d-186">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="ce27d-186">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ce27d-187">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-187">Lists templates containing the specified name.</span></span> <span data-ttu-id="ce27d-188">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-188">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ce27d-189">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-189">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ce27d-190">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="ce27d-190">The language of the template to create.</span></span> <span data-ttu-id="ce27d-191">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="ce27d-191">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ce27d-192">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-192">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ce27d-193">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce27d-193">The name for the created output.</span></span> <span data-ttu-id="ce27d-194">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce27d-194">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ce27d-195">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="ce27d-195">Location to place the generated output.</span></span> <span data-ttu-id="ce27d-196">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="ce27d-196">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ce27d-197">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-197">Filters templates based on available types.</span></span> <span data-ttu-id="ce27d-198">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="ce27d-198">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ce27d-199">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="ce27d-199">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="ce27d-200">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ce27d-200">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ce27d-201">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="ce27d-201">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="ce27d-202">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="ce27d-202">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ce27d-203">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ce27d-203">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="ce27d-204">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-204">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="ce27d-205">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="ce27d-205">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="ce27d-206">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="ce27d-206">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ce27d-207">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="ce27d-207">Prints out help for the command.</span></span> <span data-ttu-id="ce27d-208">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-208">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="ce27d-209">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-209">Lists templates containing the specified name.</span></span> <span data-ttu-id="ce27d-210">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-210">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ce27d-211">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-211">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="ce27d-212">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="ce27d-212">The language of the template to create.</span></span> <span data-ttu-id="ce27d-213">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="ce27d-213">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ce27d-214">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-214">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ce27d-215">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce27d-215">The name for the created output.</span></span> <span data-ttu-id="ce27d-216">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce27d-216">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ce27d-217">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="ce27d-217">Location to place the generated output.</span></span> <span data-ttu-id="ce27d-218">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="ce27d-218">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="ce27d-219">範本選項</span><span class="sxs-lookup"><span data-stu-id="ce27d-219">Template options</span></span>

<span data-ttu-id="ce27d-220">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="ce27d-220">Each project template may have additional options available.</span></span> <span data-ttu-id="ce27d-221">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="ce27d-221">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ce27d-222">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ce27d-222">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ce27d-223">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="ce27d-223">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="ce27d-224">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ce27d-224">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ce27d-225">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ce27d-225">**classlib**</span></span>

<span data-ttu-id="ce27d-226">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ce27d-226">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce27d-227">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="ce27d-227">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ce27d-228">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-228">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ce27d-229">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ce27d-229">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ce27d-230">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ce27d-230">**mstest, xunit**</span></span>

<span data-ttu-id="ce27d-231">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="ce27d-231">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ce27d-232">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ce27d-232">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ce27d-233">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ce27d-233">**globaljson**</span></span>

<span data-ttu-id="ce27d-234">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="ce27d-234">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="ce27d-235">**web**</span><span class="sxs-lookup"><span data-stu-id="ce27d-235">**web**</span></span>

<span data-ttu-id="ce27d-236">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="ce27d-236">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ce27d-237">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ce27d-237">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ce27d-238">**webapi**</span><span class="sxs-lookup"><span data-stu-id="ce27d-238">**webapi**</span></span>

<span data-ttu-id="ce27d-239">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="ce27d-239">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ce27d-240">可能值為：</span><span class="sxs-lookup"><span data-stu-id="ce27d-240">The possible values are:</span></span>

- <span data-ttu-id="ce27d-241">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="ce27d-241">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ce27d-242">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-242">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ce27d-243">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-243">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ce27d-244">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-244">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ce27d-245">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ce27d-245">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ce27d-246">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-246">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce27d-247">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-247">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ce27d-248">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce27d-248">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ce27d-249">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-249">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ce27d-250">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ce27d-250">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ce27d-251">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-251">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ce27d-252">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-252">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ce27d-253">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce27d-253">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ce27d-254">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-254">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ce27d-255">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-255">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ce27d-256">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="ce27d-256">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ce27d-257">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-257">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce27d-258">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-258">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ce27d-259">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce27d-259">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ce27d-260">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-260">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ce27d-261">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-261">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ce27d-262">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="ce27d-262">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ce27d-263">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-263">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ce27d-264">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="ce27d-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ce27d-265">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="ce27d-265">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ce27d-266">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-266">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ce27d-267">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ce27d-267">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ce27d-268">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="ce27d-268">**mvc, razor**</span></span>

<span data-ttu-id="ce27d-269">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="ce27d-269">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ce27d-270">可能值為：</span><span class="sxs-lookup"><span data-stu-id="ce27d-270">The possible values are:</span></span>

- <span data-ttu-id="ce27d-271">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="ce27d-271">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ce27d-272">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-272">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ce27d-273">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-273">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ce27d-274">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-274">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ce27d-275">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-275">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ce27d-276">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-276">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ce27d-277">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ce27d-277">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ce27d-278">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-278">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce27d-279">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-279">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="ce27d-280">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce27d-280">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ce27d-281">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-281">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ce27d-282">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce27d-282">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ce27d-283">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ce27d-284">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce27d-284">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ce27d-285">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ce27d-286">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ce27d-286">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ce27d-287">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-287">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ce27d-288">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-288">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ce27d-289">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce27d-289">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ce27d-290">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-290">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ce27d-291">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-291">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ce27d-292">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="ce27d-292">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ce27d-293">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-293">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="ce27d-294">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-294">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ce27d-295">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce27d-295">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ce27d-296">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-296">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="ce27d-297">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-297">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ce27d-298">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="ce27d-298">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ce27d-299">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ce27d-299">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="ce27d-300">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-300">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ce27d-301">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="ce27d-301">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ce27d-302">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-302">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ce27d-303">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="ce27d-303">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ce27d-304">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="ce27d-304">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="ce27d-305">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="ce27d-305">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ce27d-306">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ce27d-306">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ce27d-307">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ce27d-307">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ce27d-308">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="ce27d-308">**page**</span></span>

<span data-ttu-id="ce27d-309">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ce27d-309">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ce27d-310">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-310">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ce27d-311">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="ce27d-311">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ce27d-312">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ce27d-312">**viewimports**</span></span>

<span data-ttu-id="ce27d-313">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ce27d-313">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ce27d-314">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-314">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ce27d-315">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ce27d-315">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ce27d-316">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="ce27d-316">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="ce27d-317">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ce27d-317">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce27d-318">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-318">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ce27d-319">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-319">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ce27d-320">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ce27d-320">**classlib**</span></span>

<span data-ttu-id="ce27d-321">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ce27d-321">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce27d-322">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-322">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="ce27d-323">預設值是 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-323">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="ce27d-324">**mvc**</span><span class="sxs-lookup"><span data-stu-id="ce27d-324">**mvc**</span></span>

<span data-ttu-id="ce27d-325">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ce27d-325">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce27d-326">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-326">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ce27d-327">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-327">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ce27d-328">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="ce27d-328">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="ce27d-329">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-329">Values: `None` or `Individual`.</span></span> <span data-ttu-id="ce27d-330">預設值是 `None`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-330">The default value is `None`.</span></span>

<span data-ttu-id="ce27d-331">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="ce27d-331">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="ce27d-332">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-332">Values: `true` or `false`.</span></span> <span data-ttu-id="ce27d-333">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="ce27d-333">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ce27d-334">範例</span><span class="sxs-lookup"><span data-stu-id="ce27d-334">Examples</span></span>

<span data-ttu-id="ce27d-335">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="ce27d-335">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="ce27d-336">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core 2.0 SDK 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="ce27d-336">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="ce27d-337">未經驗證即在目前的目錄中，建立以 .NET Core 2.0 為目標的新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="ce27d-337">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="ce27d-338">建立以 .NET Core 2.0 為目標的新 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="ce27d-338">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="ce27d-339">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="ce27d-339">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="ce27d-340">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce27d-340">See also</span></span>

[<span data-ttu-id="ce27d-341">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="ce27d-341">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="ce27d-342">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="ce27d-342">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
<span data-ttu-id="ce27d-343">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="ce27d-343">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
[<span data-ttu-id="ce27d-344">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="ce27d-344">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
