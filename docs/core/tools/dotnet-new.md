---
title: dotnet new 命令 - .NET Core CLI
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
author: mairaw
ms.author: mairaw
ms.date: 10/24/2018
ms.openlocfilehash: 56d76f1dd54097f9cf20129d74057235290c273c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188194"
---
# <a name="dotnet-new"></a><span data-ttu-id="1d61c-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="1d61c-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1d61c-104">名稱</span><span class="sxs-lookup"><span data-stu-id="1d61c-104">Name</span></span>

<span data-ttu-id="1d61c-105">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="1d61c-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1d61c-106">概要</span><span class="sxs-lookup"><span data-stu-id="1d61c-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1d61c-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1d61c-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1d61c-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1d61c-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1d61c-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1d61c-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="1d61c-110">描述</span><span class="sxs-lookup"><span data-stu-id="1d61c-110">Description</span></span>

<span data-ttu-id="1d61c-111">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="1d61c-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="1d61c-112">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="1d61c-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="1d61c-113">引數</span><span class="sxs-lookup"><span data-stu-id="1d61c-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="1d61c-114">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="1d61c-115">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="1d61c-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="1d61c-116">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1d61c-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1d61c-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="1d61c-118">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="1d61c-118">The command contains a default list of templates.</span></span> <span data-ttu-id="1d61c-119">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="1d61c-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="1d61c-120">下表顯示隨 .NET Core SDK 2.1.300 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="1d61c-121">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="1d61c-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="1d61c-122">範本描述</span><span class="sxs-lookup"><span data-stu-id="1d61c-122">Template description</span></span>                          | <span data-ttu-id="1d61c-123">範本名稱</span><span class="sxs-lookup"><span data-stu-id="1d61c-123">Template name</span></span>    | <span data-ttu-id="1d61c-124">語言</span><span class="sxs-lookup"><span data-stu-id="1d61c-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="1d61c-125">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="1d61c-125">Console application</span></span>                          | `console`        | <span data-ttu-id="1d61c-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1d61c-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1d61c-127">類別庫</span><span class="sxs-lookup"><span data-stu-id="1d61c-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="1d61c-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1d61c-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1d61c-129">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="1d61c-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="1d61c-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1d61c-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1d61c-131">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="1d61c-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="1d61c-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1d61c-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1d61c-133">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="1d61c-133">Razor page</span></span>                                   | `page`           | <span data-ttu-id="1d61c-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-134">[C#]</span></span>          |
| <span data-ttu-id="1d61c-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="1d61c-135">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="1d61c-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-136">[C#]</span></span>          |
| <span data-ttu-id="1d61c-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="1d61c-137">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="1d61c-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-138">[C#]</span></span>          |
| <span data-ttu-id="1d61c-139">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d61c-139">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="1d61c-140">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-140">[C#], F#</span></span>      |
| <span data-ttu-id="1d61c-141">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="1d61c-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="1d61c-142">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-142">[C#], F#</span></span>      |
| <span data-ttu-id="1d61c-143">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="1d61c-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="1d61c-144">`razor`、 `webapp`</span><span class="sxs-lookup"><span data-stu-id="1d61c-144">`razor`, `webapp`</span></span>| <span data-ttu-id="1d61c-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-145">[C#]</span></span>          |
| <span data-ttu-id="1d61c-146">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="1d61c-146">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="1d61c-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-147">[C#]</span></span>          |
| <span data-ttu-id="1d61c-148">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="1d61c-148">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="1d61c-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-149">[C#]</span></span>          |
| <span data-ttu-id="1d61c-150">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="1d61c-150">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="1d61c-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-151">[C#]</span></span>          |
| <span data-ttu-id="1d61c-152">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="1d61c-152">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="1d61c-153">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-153">[C#], F#</span></span>      |
| <span data-ttu-id="1d61c-154">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="1d61c-154">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="1d61c-155">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-155">[C#]</span></span>          |
| <span data-ttu-id="1d61c-156">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="1d61c-156">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="1d61c-157">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="1d61c-157">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="1d61c-158">Web 組態</span><span class="sxs-lookup"><span data-stu-id="1d61c-158">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="1d61c-159">方案檔</span><span class="sxs-lookup"><span data-stu-id="1d61c-159">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1d61c-160">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1d61c-160">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="1d61c-161">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="1d61c-161">The command contains a default list of templates.</span></span> <span data-ttu-id="1d61c-162">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="1d61c-162">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="1d61c-163">下表顯示隨 .NET Core SDK 2.0 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-163">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="1d61c-164">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="1d61c-164">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="1d61c-165">範本描述</span><span class="sxs-lookup"><span data-stu-id="1d61c-165">Template description</span></span>                          | <span data-ttu-id="1d61c-166">範本名稱</span><span class="sxs-lookup"><span data-stu-id="1d61c-166">Template name</span></span> | <span data-ttu-id="1d61c-167">語言</span><span class="sxs-lookup"><span data-stu-id="1d61c-167">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="1d61c-168">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="1d61c-168">Console application</span></span>                          | `console`     | <span data-ttu-id="1d61c-169">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1d61c-169">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1d61c-170">類別庫</span><span class="sxs-lookup"><span data-stu-id="1d61c-170">Class library</span></span>                                | `classlib`    | <span data-ttu-id="1d61c-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1d61c-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1d61c-172">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="1d61c-172">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="1d61c-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1d61c-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1d61c-174">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="1d61c-174">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="1d61c-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1d61c-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1d61c-176">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d61c-176">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="1d61c-177">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-177">[C#], F#</span></span>      |
| <span data-ttu-id="1d61c-178">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="1d61c-178">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="1d61c-179">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-179">[C#], F#</span></span>      |
| <span data-ttu-id="1d61c-180">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="1d61c-180">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="1d61c-181">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-181">[C#]</span></span>          |
| <span data-ttu-id="1d61c-182">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="1d61c-182">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="1d61c-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-183">[C#]</span></span>          |
| <span data-ttu-id="1d61c-184">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="1d61c-184">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="1d61c-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-185">[C#]</span></span>          |
| <span data-ttu-id="1d61c-186">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="1d61c-186">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="1d61c-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-187">[C#]</span></span>          |
| <span data-ttu-id="1d61c-188">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="1d61c-188">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="1d61c-189">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-189">[C#], F#</span></span>      |
| <span data-ttu-id="1d61c-190">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="1d61c-190">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="1d61c-191">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="1d61c-191">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="1d61c-192">Web 組態</span><span class="sxs-lookup"><span data-stu-id="1d61c-192">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="1d61c-193">方案檔</span><span class="sxs-lookup"><span data-stu-id="1d61c-193">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="1d61c-194">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="1d61c-194">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="1d61c-195">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="1d61c-195">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="1d61c-196">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="1d61c-196">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1d61c-197">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1d61c-197">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="1d61c-198">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="1d61c-198">The command contains a default list of templates.</span></span> <span data-ttu-id="1d61c-199">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="1d61c-199">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="1d61c-200">下表顯示隨 .NET Core SDK 1.x 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-200">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="1d61c-201">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="1d61c-201">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="1d61c-202">範本描述</span><span class="sxs-lookup"><span data-stu-id="1d61c-202">Template description</span></span>  | <span data-ttu-id="1d61c-203">範本名稱</span><span class="sxs-lookup"><span data-stu-id="1d61c-203">Template name</span></span> | <span data-ttu-id="1d61c-204">語言</span><span class="sxs-lookup"><span data-stu-id="1d61c-204">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="1d61c-205">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="1d61c-205">Console application</span></span>  | `console`     | <span data-ttu-id="1d61c-206">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-206">[C#], F#</span></span>  |
| <span data-ttu-id="1d61c-207">類別庫</span><span class="sxs-lookup"><span data-stu-id="1d61c-207">Class library</span></span>        | `classlib`    | <span data-ttu-id="1d61c-208">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-208">[C#], F#</span></span>  |
| <span data-ttu-id="1d61c-209">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="1d61c-209">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="1d61c-210">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-210">[C#], F#</span></span>  |
| <span data-ttu-id="1d61c-211">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="1d61c-211">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="1d61c-212">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-212">[C#], F#</span></span>  |
| <span data-ttu-id="1d61c-213">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d61c-213">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="1d61c-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-214">[C#]</span></span>      |
| <span data-ttu-id="1d61c-215">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="1d61c-215">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="1d61c-216">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1d61c-216">[C#], F#</span></span>  |
| <span data-ttu-id="1d61c-217">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="1d61c-217">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="1d61c-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="1d61c-218">[C#]</span></span>      |
| <span data-ttu-id="1d61c-219">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="1d61c-219">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="1d61c-220">Web 組態</span><span class="sxs-lookup"><span data-stu-id="1d61c-220">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="1d61c-221">方案檔</span><span class="sxs-lookup"><span data-stu-id="1d61c-221">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="1d61c-222">選項</span><span class="sxs-lookup"><span data-stu-id="1d61c-222">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1d61c-223">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1d61c-223">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="1d61c-224">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="1d61c-224">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="1d61c-225">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="1d61c-225">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="1d61c-226">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="1d61c-226">Prints out help for the command.</span></span> <span data-ttu-id="1d61c-227">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-227">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="1d61c-228">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="1d61c-228">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="1d61c-229">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-229">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="1d61c-230">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-230">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="1d61c-231">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="1d61c-231">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="1d61c-232">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-232">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="1d61c-233">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-233">Lists templates containing the specified name.</span></span> <span data-ttu-id="1d61c-234">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-234">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="1d61c-235">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-235">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="1d61c-236">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="1d61c-236">The language of the template to create.</span></span> <span data-ttu-id="1d61c-237">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-237">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="1d61c-238">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-238">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="1d61c-239">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="1d61c-239">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="1d61c-240">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-240">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="1d61c-241">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d61c-241">The name for the created output.</span></span> <span data-ttu-id="1d61c-242">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d61c-242">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="1d61c-243">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="1d61c-243">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1d61c-244">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="1d61c-244">Location to place the generated output.</span></span> <span data-ttu-id="1d61c-245">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="1d61c-245">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="1d61c-246">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-246">Filters templates based on available types.</span></span> <span data-ttu-id="1d61c-247">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="1d61c-247">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="1d61c-248">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="1d61c-248">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="1d61c-249">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="1d61c-249">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="1d61c-250">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="1d61c-250">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="1d61c-251">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="1d61c-251">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1d61c-252">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1d61c-252">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="1d61c-253">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="1d61c-253">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="1d61c-254">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="1d61c-254">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="1d61c-255">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="1d61c-255">Prints out help for the command.</span></span> <span data-ttu-id="1d61c-256">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-256">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="1d61c-257">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="1d61c-257">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="1d61c-258">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-258">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="1d61c-259">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-259">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="1d61c-260">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="1d61c-260">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="1d61c-261">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-261">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="1d61c-262">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-262">Lists templates containing the specified name.</span></span> <span data-ttu-id="1d61c-263">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-263">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="1d61c-264">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-264">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="1d61c-265">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="1d61c-265">The language of the template to create.</span></span> <span data-ttu-id="1d61c-266">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-266">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="1d61c-267">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-267">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="1d61c-268">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="1d61c-268">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="1d61c-269">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-269">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="1d61c-270">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d61c-270">The name for the created output.</span></span> <span data-ttu-id="1d61c-271">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d61c-271">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1d61c-272">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="1d61c-272">Location to place the generated output.</span></span> <span data-ttu-id="1d61c-273">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="1d61c-273">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="1d61c-274">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-274">Filters templates based on available types.</span></span> <span data-ttu-id="1d61c-275">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="1d61c-275">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="1d61c-276">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="1d61c-276">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="1d61c-277">若要使用來源 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="1d61c-277">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="1d61c-278">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="1d61c-278">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="1d61c-279">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="1d61c-279">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="1d61c-280">如果您無法判斷將範本解除安裝需要 `PATH` 或是 `NUGET_ID` 引數，在沒有引數的情況下執行 `dotnet new --uninstall` 會列出所有已安裝的範本，以及將它們解除安裝所需的引數。</span><span class="sxs-lookup"><span data-stu-id="1d61c-280">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1d61c-281">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1d61c-281">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="1d61c-282">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-282">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="1d61c-283">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="1d61c-283">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="1d61c-284">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="1d61c-284">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="1d61c-285">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="1d61c-285">Prints out help for the command.</span></span> <span data-ttu-id="1d61c-286">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-286">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="1d61c-287">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-287">Lists templates containing the specified name.</span></span> <span data-ttu-id="1d61c-288">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-288">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="1d61c-289">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-289">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="1d61c-290">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="1d61c-290">The language of the template to create.</span></span> <span data-ttu-id="1d61c-291">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-291">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="1d61c-292">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-292">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="1d61c-293">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="1d61c-293">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="1d61c-294">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-294">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="1d61c-295">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d61c-295">The name for the created output.</span></span> <span data-ttu-id="1d61c-296">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d61c-296">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1d61c-297">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="1d61c-297">Location to place the generated output.</span></span> <span data-ttu-id="1d61c-298">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="1d61c-298">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="1d61c-299">範本選項</span><span class="sxs-lookup"><span data-stu-id="1d61c-299">Template options</span></span>

<span data-ttu-id="1d61c-300">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="1d61c-300">Each project template may have additional options available.</span></span> <span data-ttu-id="1d61c-301">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="1d61c-301">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1d61c-302">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1d61c-302">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="1d61c-303">**主控台, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="1d61c-303">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="1d61c-304">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-305">**classlib**</span><span class="sxs-lookup"><span data-stu-id="1d61c-305">**classlib**</span></span>

<span data-ttu-id="1d61c-306">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-306">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="1d61c-307">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="1d61c-307">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="1d61c-308">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-308">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="1d61c-309">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-310">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="1d61c-310">**mstest, xunit**</span></span>

<span data-ttu-id="1d61c-311">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="1d61c-311">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="1d61c-312">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-312">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-313">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="1d61c-313">**globaljson**</span></span>

<span data-ttu-id="1d61c-314">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-314">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="1d61c-315">**web**</span><span class="sxs-lookup"><span data-stu-id="1d61c-315">**web**</span></span>

<span data-ttu-id="1d61c-316">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1d61c-316">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="1d61c-317">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-317">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-318">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="1d61c-318">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="1d61c-319">此選項僅適用於未使用 `IndividualAuth` 或 `OrganizationalAuth` 時。</span><span class="sxs-lookup"><span data-stu-id="1d61c-319">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="1d61c-320">**webapi**</span><span class="sxs-lookup"><span data-stu-id="1d61c-320">**webapi**</span></span>

<span data-ttu-id="1d61c-321">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1d61c-321">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="1d61c-322">可能值為：</span><span class="sxs-lookup"><span data-stu-id="1d61c-322">The possible values are:</span></span>

- <span data-ttu-id="1d61c-323">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-323">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="1d61c-324">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-324">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="1d61c-325">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-325">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="1d61c-326">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-326">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="1d61c-327">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d61c-327">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="1d61c-328">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-328">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="1d61c-329">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-329">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="1d61c-330">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-330">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="1d61c-331">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-331">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-332">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d61c-332">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="1d61c-333">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-333">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1d61c-334">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-334">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="1d61c-335">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-335">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="1d61c-336">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-336">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="1d61c-337">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-337">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="1d61c-338">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="1d61c-338">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="1d61c-339">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-339">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1d61c-340">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-340">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="1d61c-341">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-341">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="1d61c-342">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-342">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1d61c-343">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-343">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="1d61c-344">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="1d61c-344">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="1d61c-345">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-345">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="1d61c-346">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1d61c-346">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="1d61c-347">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="1d61c-347">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="1d61c-348">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-348">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-349">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-349">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-350">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="1d61c-350">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="1d61c-351">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-351">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="1d61c-352">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="1d61c-352">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="1d61c-353">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="1d61c-353">**mvc, razor**</span></span>

<span data-ttu-id="1d61c-354">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1d61c-354">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="1d61c-355">可能值為：</span><span class="sxs-lookup"><span data-stu-id="1d61c-355">The possible values are:</span></span>

- <span data-ttu-id="1d61c-356">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-356">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="1d61c-357">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-357">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="1d61c-358">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-358">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="1d61c-359">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-359">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="1d61c-360">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-360">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="1d61c-361">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-361">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="1d61c-362">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d61c-362">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="1d61c-363">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-363">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="1d61c-364">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-364">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="1d61c-365">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-365">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="1d61c-366">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-366">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-367">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-367">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="1d61c-368">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-369">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-369">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="1d61c-370">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-371">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d61c-371">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="1d61c-372">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-372">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="1d61c-373">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-373">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="1d61c-374">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-374">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="1d61c-375">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-375">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="1d61c-376">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-376">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="1d61c-377">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="1d61c-377">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="1d61c-378">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-378">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1d61c-379">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-379">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="1d61c-380">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-380">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="1d61c-381">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-381">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1d61c-382">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-382">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="1d61c-383">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="1d61c-383">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="1d61c-384">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-384">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1d61c-385">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-385">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="1d61c-386">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="1d61c-386">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="1d61c-387">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-387">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="1d61c-388">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1d61c-388">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="1d61c-389">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="1d61c-389">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="1d61c-390">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="1d61c-390">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="1d61c-391">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-391">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-392">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-392">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-393">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="1d61c-393">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="1d61c-394">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-394">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="1d61c-395">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="1d61c-395">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="1d61c-396">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="1d61c-396">**page**</span></span>

<span data-ttu-id="1d61c-397">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1d61c-397">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="1d61c-398">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-398">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="1d61c-399">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="1d61c-399">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="1d61c-400">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="1d61c-400">**viewimports**</span></span>

<span data-ttu-id="1d61c-401">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1d61c-401">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="1d61c-402">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-402">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1d61c-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1d61c-403">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="1d61c-404">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="1d61c-404">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="1d61c-405">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-405">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-406">**classlib**</span><span class="sxs-lookup"><span data-stu-id="1d61c-406">**classlib**</span></span>

<span data-ttu-id="1d61c-407">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-407">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="1d61c-408">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="1d61c-408">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="1d61c-409">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-409">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="1d61c-410">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-410">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-411">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="1d61c-411">**mstest, xunit**</span></span>

<span data-ttu-id="1d61c-412">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="1d61c-412">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="1d61c-413">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-413">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-414">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="1d61c-414">**globaljson**</span></span>

<span data-ttu-id="1d61c-415">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="1d61c-415">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="1d61c-416">**web**</span><span class="sxs-lookup"><span data-stu-id="1d61c-416">**web**</span></span>

<span data-ttu-id="1d61c-417">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1d61c-417">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="1d61c-418">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-418">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-419">**webapi**</span><span class="sxs-lookup"><span data-stu-id="1d61c-419">**webapi**</span></span>

<span data-ttu-id="1d61c-420">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1d61c-420">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="1d61c-421">可能值為：</span><span class="sxs-lookup"><span data-stu-id="1d61c-421">The possible values are:</span></span>

- <span data-ttu-id="1d61c-422">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-422">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="1d61c-423">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-423">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="1d61c-424">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-424">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="1d61c-425">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-425">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="1d61c-426">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d61c-426">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="1d61c-427">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-427">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="1d61c-428">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-428">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="1d61c-429">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-429">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="1d61c-430">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-430">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-431">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d61c-431">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="1d61c-432">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-432">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1d61c-433">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-433">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="1d61c-434">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-434">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="1d61c-435">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-435">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="1d61c-436">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-436">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="1d61c-437">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="1d61c-437">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="1d61c-438">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-438">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1d61c-439">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-439">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="1d61c-440">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-440">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="1d61c-441">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-441">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1d61c-442">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-442">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="1d61c-443">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="1d61c-443">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="1d61c-444">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-444">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="1d61c-445">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1d61c-445">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="1d61c-446">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="1d61c-446">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="1d61c-447">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-447">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-448">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-448">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-449">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="1d61c-449">**mvc, razor**</span></span>

<span data-ttu-id="1d61c-450">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1d61c-450">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="1d61c-451">可能值為：</span><span class="sxs-lookup"><span data-stu-id="1d61c-451">The possible values are:</span></span>

- <span data-ttu-id="1d61c-452">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-452">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="1d61c-453">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-453">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="1d61c-454">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-454">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="1d61c-455">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-455">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="1d61c-456">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-456">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="1d61c-457">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-457">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="1d61c-458">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d61c-458">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="1d61c-459">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-459">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="1d61c-460">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-460">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="1d61c-461">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-461">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="1d61c-462">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-462">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-463">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-463">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="1d61c-464">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-465">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-465">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="1d61c-466">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-467">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d61c-467">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="1d61c-468">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-468">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="1d61c-469">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-469">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="1d61c-470">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-470">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="1d61c-471">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-471">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="1d61c-472">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-472">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="1d61c-473">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="1d61c-473">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="1d61c-474">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-474">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1d61c-475">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-475">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="1d61c-476">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d61c-476">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="1d61c-477">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-477">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1d61c-478">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-478">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="1d61c-479">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="1d61c-479">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="1d61c-480">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1d61c-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1d61c-481">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-481">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="1d61c-482">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="1d61c-482">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="1d61c-483">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-483">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="1d61c-484">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1d61c-484">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="1d61c-485">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="1d61c-485">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="1d61c-486">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="1d61c-486">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="1d61c-487">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1d61c-487">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1d61c-488">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1d61c-488">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1d61c-489">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="1d61c-489">**page**</span></span>

<span data-ttu-id="1d61c-490">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1d61c-490">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="1d61c-491">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-491">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="1d61c-492">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="1d61c-492">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="1d61c-493">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="1d61c-493">**viewimports**</span></span>

<span data-ttu-id="1d61c-494">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1d61c-494">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="1d61c-495">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-495">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1d61c-496">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1d61c-496">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="1d61c-497">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="1d61c-497">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="1d61c-498">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-498">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="1d61c-499">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-499">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="1d61c-500">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-500">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="1d61c-501">**classlib**</span><span class="sxs-lookup"><span data-stu-id="1d61c-501">**classlib**</span></span>

<span data-ttu-id="1d61c-502">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-502">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="1d61c-503">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-503">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="1d61c-504">預設值是 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-504">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="1d61c-505">**mvc**</span><span class="sxs-lookup"><span data-stu-id="1d61c-505">**mvc**</span></span>

<span data-ttu-id="1d61c-506">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1d61c-506">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="1d61c-507">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-507">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="1d61c-508">預設值是 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-508">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="1d61c-509">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1d61c-509">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="1d61c-510">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-510">Values: `None` or `Individual`.</span></span> <span data-ttu-id="1d61c-511">預設值是 `None`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-511">The default value is `None`.</span></span>

<span data-ttu-id="1d61c-512">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="1d61c-512">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="1d61c-513">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-513">Values: `true` or `false`.</span></span> <span data-ttu-id="1d61c-514">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="1d61c-514">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="1d61c-515">範例</span><span class="sxs-lookup"><span data-stu-id="1d61c-515">Examples</span></span>

<span data-ttu-id="1d61c-516">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="1d61c-516">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="1d61c-517">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core SDK 2.0 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="1d61c-517">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="1d61c-518">未經驗證即在目前的目錄中建立新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="1d61c-518">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="1d61c-519">建立新的 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="1d61c-519">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="1d61c-520">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="1d61c-520">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="1d61c-521">安裝適用於 ASP.NET Core 的單頁應用程式範本 2.0 版 (僅適用於 .NET Core SDK 1.1 及更新版本的命令選項)：</span><span class="sxs-lookup"><span data-stu-id="1d61c-521">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="1d61c-522">在目前目錄中建立 *global.json*，並將 SDK 版本設為 2.0.0 (只能用於.NET Core SDK 2.0 或更新版本)：</span><span class="sxs-lookup"><span data-stu-id="1d61c-522">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="1d61c-523">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d61c-523">See also</span></span>

* [<span data-ttu-id="1d61c-524">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="1d61c-524">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="1d61c-525">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="1d61c-525">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* <span data-ttu-id="1d61c-526">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="1d61c-526">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
* [<span data-ttu-id="1d61c-527">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="1d61c-527">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
