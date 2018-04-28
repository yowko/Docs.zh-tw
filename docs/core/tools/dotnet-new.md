---
title: dotnet new 命令 - .NET Core CLI
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
author: mairaw
ms.author: mairaw
ms.date: 03/26/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: ab8d6f779a428aab7bd2739105dcf08b51d14ab9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="4d525-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="4d525-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4d525-104">名稱</span><span class="sxs-lookup"><span data-stu-id="4d525-104">Name</span></span>

<span data-ttu-id="4d525-105">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="4d525-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4d525-106">概要</span><span class="sxs-lookup"><span data-stu-id="4d525-106">Synopsis</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="4d525-107">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4d525-107">.NET Core 2.0</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4d525-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4d525-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="4d525-109">描述</span><span class="sxs-lookup"><span data-stu-id="4d525-109">Description</span></span>

<span data-ttu-id="4d525-110">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="4d525-110">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="4d525-111">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="4d525-111">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="4d525-112">引數</span><span class="sxs-lookup"><span data-stu-id="4d525-112">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="4d525-113">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="4d525-114">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="4d525-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="4d525-115">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="4d525-115">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="4d525-116">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4d525-116">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="4d525-117">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="4d525-117">The command contains a default list of templates.</span></span> <span data-ttu-id="4d525-118">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="4d525-118">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="4d525-119">下表顯示隨 .NET Core 2.0 SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-119">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="4d525-120">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="4d525-120">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="4d525-121">範本描述</span><span class="sxs-lookup"><span data-stu-id="4d525-121">Template description</span></span>                          | <span data-ttu-id="4d525-122">範本名稱</span><span class="sxs-lookup"><span data-stu-id="4d525-122">Template name</span></span> | <span data-ttu-id="4d525-123">語言</span><span class="sxs-lookup"><span data-stu-id="4d525-123">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="4d525-124">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="4d525-124">Console application</span></span>                          | `console`     | <span data-ttu-id="4d525-125">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4d525-125">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4d525-126">類別庫</span><span class="sxs-lookup"><span data-stu-id="4d525-126">Class library</span></span>                                | `classlib`    | <span data-ttu-id="4d525-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4d525-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4d525-128">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="4d525-128">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="4d525-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4d525-129">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4d525-130">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="4d525-130">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="4d525-131">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4d525-131">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4d525-132">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4d525-132">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="4d525-133">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="4d525-133">[C#], F#</span></span>      |
| <span data-ttu-id="4d525-134">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="4d525-134">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="4d525-135">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="4d525-135">[C#], F#</span></span>      |
| <span data-ttu-id="4d525-136">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="4d525-136">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="4d525-137">[C#]</span><span class="sxs-lookup"><span data-stu-id="4d525-137">[C#]</span></span>          |
| <span data-ttu-id="4d525-138">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="4d525-138">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="4d525-139">[C#]</span><span class="sxs-lookup"><span data-stu-id="4d525-139">[C#]</span></span>          |
| <span data-ttu-id="4d525-140">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="4d525-140">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="4d525-141">[C#]</span><span class="sxs-lookup"><span data-stu-id="4d525-141">[C#]</span></span>          |
| <span data-ttu-id="4d525-142">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="4d525-142">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="4d525-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="4d525-143">[C#]</span></span>          |
| <span data-ttu-id="4d525-144">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="4d525-144">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="4d525-145">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="4d525-145">[C#], F#</span></span>      |
| <span data-ttu-id="4d525-146">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="4d525-146">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="4d525-147">Nuget 組態</span><span class="sxs-lookup"><span data-stu-id="4d525-147">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="4d525-148">Web 組態</span><span class="sxs-lookup"><span data-stu-id="4d525-148">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="4d525-149">方案檔</span><span class="sxs-lookup"><span data-stu-id="4d525-149">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="4d525-150">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="4d525-150">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="4d525-151">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="4d525-151">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="4d525-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="4d525-152">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4d525-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4d525-153">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="4d525-154">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="4d525-154">The command contains a default list of templates.</span></span> <span data-ttu-id="4d525-155">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="4d525-155">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="4d525-156">下表顯示隨 .NET Core 1.x SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-156">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="4d525-157">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="4d525-157">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="4d525-158">範本描述</span><span class="sxs-lookup"><span data-stu-id="4d525-158">Template description</span></span>  | <span data-ttu-id="4d525-159">範本名稱</span><span class="sxs-lookup"><span data-stu-id="4d525-159">Template name</span></span> | <span data-ttu-id="4d525-160">語言</span><span class="sxs-lookup"><span data-stu-id="4d525-160">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="4d525-161">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="4d525-161">Console application</span></span>  | `console`     | <span data-ttu-id="4d525-162">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="4d525-162">[C#], F#</span></span>  |
| <span data-ttu-id="4d525-163">類別庫</span><span class="sxs-lookup"><span data-stu-id="4d525-163">Class library</span></span>        | `classlib`    | <span data-ttu-id="4d525-164">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="4d525-164">[C#], F#</span></span>  |
| <span data-ttu-id="4d525-165">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="4d525-165">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="4d525-166">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="4d525-166">[C#], F#</span></span>  |
| <span data-ttu-id="4d525-167">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="4d525-167">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="4d525-168">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="4d525-168">[C#], F#</span></span>  |
| <span data-ttu-id="4d525-169">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4d525-169">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="4d525-170">[C#]</span><span class="sxs-lookup"><span data-stu-id="4d525-170">[C#]</span></span>      |
| <span data-ttu-id="4d525-171">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="4d525-171">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="4d525-172">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="4d525-172">[C#], F#</span></span>  |
| <span data-ttu-id="4d525-173">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="4d525-173">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="4d525-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="4d525-174">[C#]</span></span>      |
| <span data-ttu-id="4d525-175">Nuget 組態</span><span class="sxs-lookup"><span data-stu-id="4d525-175">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="4d525-176">Web 組態</span><span class="sxs-lookup"><span data-stu-id="4d525-176">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="4d525-177">方案檔</span><span class="sxs-lookup"><span data-stu-id="4d525-177">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="4d525-178">選項</span><span class="sxs-lookup"><span data-stu-id="4d525-178">Options</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="4d525-179">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4d525-179">.NET Core 2.0</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="4d525-180">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="4d525-180">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="4d525-181">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="4d525-181">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4d525-182">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="4d525-182">Prints out help for the command.</span></span> <span data-ttu-id="4d525-183">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="4d525-183">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="4d525-184">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="4d525-184">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4d525-185">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="4d525-185">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="4d525-186">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="4d525-186">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="4d525-187">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="4d525-187">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="4d525-188">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="4d525-188">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="4d525-189">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-189">Lists templates containing the specified name.</span></span> <span data-ttu-id="4d525-190">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-190">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4d525-191">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-191">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="4d525-192">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="4d525-192">The language of the template to create.</span></span> <span data-ttu-id="4d525-193">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="4d525-193">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4d525-194">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="4d525-194">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4d525-195">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d525-195">The name for the created output.</span></span> <span data-ttu-id="4d525-196">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d525-196">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4d525-197">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="4d525-197">Location to place the generated output.</span></span> <span data-ttu-id="4d525-198">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="4d525-198">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="4d525-199">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-199">Filters templates based on available types.</span></span> <span data-ttu-id="4d525-200">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="4d525-200">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="4d525-201">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="4d525-201">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="4d525-202">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="4d525-202">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="4d525-203">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="4d525-203">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="4d525-204">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="4d525-204">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4d525-205">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4d525-205">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="4d525-206">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-206">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="4d525-207">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="4d525-207">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="4d525-208">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="4d525-208">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4d525-209">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="4d525-209">Prints out help for the command.</span></span> <span data-ttu-id="4d525-210">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="4d525-210">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="4d525-211">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-211">Lists templates containing the specified name.</span></span> <span data-ttu-id="4d525-212">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-212">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4d525-213">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="4d525-213">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="4d525-214">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="4d525-214">The language of the template to create.</span></span> <span data-ttu-id="4d525-215">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="4d525-215">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4d525-216">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="4d525-216">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4d525-217">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d525-217">The name for the created output.</span></span> <span data-ttu-id="4d525-218">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d525-218">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4d525-219">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="4d525-219">Location to place the generated output.</span></span> <span data-ttu-id="4d525-220">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="4d525-220">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="4d525-221">範本選項</span><span class="sxs-lookup"><span data-stu-id="4d525-221">Template options</span></span>

<span data-ttu-id="4d525-222">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="4d525-222">Each project template may have additional options available.</span></span> <span data-ttu-id="4d525-223">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="4d525-223">The core templates have the following additional options:</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="4d525-224">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4d525-224">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="4d525-225">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="4d525-225">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="4d525-226">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="4d525-226">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="4d525-227">**classlib**</span><span class="sxs-lookup"><span data-stu-id="4d525-227">**classlib**</span></span>

<span data-ttu-id="4d525-228">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="4d525-228">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4d525-229">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="4d525-229">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="4d525-230">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="4d525-230">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="4d525-231">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="4d525-231">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="4d525-232">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="4d525-232">**mstest, xunit**</span></span>

<span data-ttu-id="4d525-233">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="4d525-233">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4d525-234">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="4d525-234">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="4d525-235">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="4d525-235">**globaljson**</span></span>

<span data-ttu-id="4d525-236">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="4d525-236">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="4d525-237">**web**</span><span class="sxs-lookup"><span data-stu-id="4d525-237">**web**</span></span>

<span data-ttu-id="4d525-238">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="4d525-238">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4d525-239">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="4d525-239">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="4d525-240">**webapi**</span><span class="sxs-lookup"><span data-stu-id="4d525-240">**webapi**</span></span>

<span data-ttu-id="4d525-241">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="4d525-241">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4d525-242">可能值為：</span><span class="sxs-lookup"><span data-stu-id="4d525-242">The possible values are:</span></span>

- <span data-ttu-id="4d525-243">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="4d525-243">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4d525-244">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-244">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4d525-245">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-245">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4d525-246">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-246">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4d525-247">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d525-247">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4d525-248">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-248">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4d525-249">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="4d525-249">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4d525-250">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d525-250">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4d525-251">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-251">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4d525-252">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d525-252">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4d525-253">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-253">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4d525-254">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="4d525-254">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4d525-255">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d525-255">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4d525-256">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-256">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4d525-257">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="4d525-257">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4d525-258">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="4d525-258">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4d525-259">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-259">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4d525-260">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="4d525-260">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4d525-261">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d525-261">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4d525-262">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-262">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4d525-263">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="4d525-263">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4d525-264">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="4d525-264">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4d525-265">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-265">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4d525-266">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="4d525-266">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4d525-267">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="4d525-267">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4d525-268">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-268">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4d525-269">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="4d525-269">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="4d525-270">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="4d525-270">**mvc, razor**</span></span>

<span data-ttu-id="4d525-271">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="4d525-271">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4d525-272">可能值為：</span><span class="sxs-lookup"><span data-stu-id="4d525-272">The possible values are:</span></span>

- <span data-ttu-id="4d525-273">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="4d525-273">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4d525-274">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-274">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="4d525-275">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-275">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4d525-276">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-276">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4d525-277">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-277">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="4d525-278">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-278">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4d525-279">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d525-279">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4d525-280">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-280">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4d525-281">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="4d525-281">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="4d525-282">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d525-282">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4d525-283">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4d525-284">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d525-284">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="4d525-285">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4d525-286">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d525-286">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="4d525-287">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-287">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4d525-288">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d525-288">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4d525-289">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-289">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4d525-290">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="4d525-290">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4d525-291">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d525-291">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4d525-292">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-292">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4d525-293">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="4d525-293">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4d525-294">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="4d525-294">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4d525-295">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-295">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="4d525-296">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="4d525-296">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4d525-297">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d525-297">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4d525-298">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-298">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="4d525-299">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="4d525-299">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4d525-300">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="4d525-300">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4d525-301">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="4d525-301">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="4d525-302">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="4d525-302">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="4d525-303">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="4d525-303">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4d525-304">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-304">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4d525-305">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="4d525-305">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4d525-306">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="4d525-306">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="4d525-307">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="4d525-307">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4d525-308">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="4d525-308">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4d525-309">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="4d525-309">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="4d525-310">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="4d525-310">**page**</span></span>

<span data-ttu-id="4d525-311">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4d525-311">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="4d525-312">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="4d525-312">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4d525-313">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="4d525-313">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="4d525-314">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="4d525-314">**viewimports**</span></span>

<span data-ttu-id="4d525-315">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4d525-315">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="4d525-316">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="4d525-316">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4d525-317">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4d525-317">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="4d525-318">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="4d525-318">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="4d525-319">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="4d525-319">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4d525-320">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="4d525-320">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="4d525-321">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="4d525-321">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="4d525-322">**classlib**</span><span class="sxs-lookup"><span data-stu-id="4d525-322">**classlib**</span></span>

<span data-ttu-id="4d525-323">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="4d525-323">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4d525-324">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="4d525-324">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="4d525-325">預設值是 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="4d525-325">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="4d525-326">**mvc**</span><span class="sxs-lookup"><span data-stu-id="4d525-326">**mvc**</span></span>

<span data-ttu-id="4d525-327">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="4d525-327">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4d525-328">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="4d525-328">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="4d525-329">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="4d525-329">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="4d525-330">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="4d525-330">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="4d525-331">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="4d525-331">Values: `None` or `Individual`.</span></span> <span data-ttu-id="4d525-332">預設值是 `None`。</span><span class="sxs-lookup"><span data-stu-id="4d525-332">The default value is `None`.</span></span>

<span data-ttu-id="4d525-333">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="4d525-333">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="4d525-334">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="4d525-334">Values: `true` or `false`.</span></span> <span data-ttu-id="4d525-335">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="4d525-335">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="4d525-336">範例</span><span class="sxs-lookup"><span data-stu-id="4d525-336">Examples</span></span>

<span data-ttu-id="4d525-337">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="4d525-337">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="4d525-338">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core 2.0 SDK 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="4d525-338">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="4d525-339">未經驗證即在目前的目錄中，建立以 .NET Core 2.0 為目標的新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="4d525-339">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="4d525-340">建立以 .NET Core 2.0 為目標的新 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="4d525-340">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="4d525-341">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="4d525-341">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="4d525-342">安裝適用於 ASP.NET Core 的單頁應用程式範本 2.0 版 (僅適用於 .NET Core SDK 1.1 及更新版本的命令選項)：</span><span class="sxs-lookup"><span data-stu-id="4d525-342">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

## <a name="see-also"></a><span data-ttu-id="4d525-343">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d525-343">See also</span></span>

[<span data-ttu-id="4d525-344">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="4d525-344">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="4d525-345">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="4d525-345">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
<span data-ttu-id="4d525-346">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="4d525-346">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
[<span data-ttu-id="4d525-347">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="4d525-347">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
