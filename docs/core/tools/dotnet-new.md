---
title: dotnet new 命令 - .NET Core CLI
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
author: mairaw
ms.author: mairaw
ms.date: 10/24/2018
ms.openlocfilehash: a8d486f569f31d68d5659ac6a80d615474ef2506
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131478"
---
# <a name="dotnet-new"></a><span data-ttu-id="1b41e-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="1b41e-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1b41e-104">名稱</span><span class="sxs-lookup"><span data-stu-id="1b41e-104">Name</span></span>

<span data-ttu-id="1b41e-105">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="1b41e-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1b41e-106">概要</span><span class="sxs-lookup"><span data-stu-id="1b41e-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1b41e-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1b41e-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1b41e-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1b41e-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1b41e-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1b41e-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="1b41e-110">說明</span><span class="sxs-lookup"><span data-stu-id="1b41e-110">Description</span></span>

<span data-ttu-id="1b41e-111">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="1b41e-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="1b41e-112">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="1b41e-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="1b41e-113">引數</span><span class="sxs-lookup"><span data-stu-id="1b41e-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="1b41e-114">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="1b41e-115">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="1b41e-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="1b41e-116">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1b41e-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1b41e-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="1b41e-118">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="1b41e-118">The command contains a default list of templates.</span></span> <span data-ttu-id="1b41e-119">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="1b41e-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="1b41e-120">下表顯示隨 .NET Core SDK 2.1.300 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="1b41e-121">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="1b41e-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="1b41e-122">範本描述</span><span class="sxs-lookup"><span data-stu-id="1b41e-122">Template description</span></span>                          | <span data-ttu-id="1b41e-123">範本名稱</span><span class="sxs-lookup"><span data-stu-id="1b41e-123">Template name</span></span>    | <span data-ttu-id="1b41e-124">語言</span><span class="sxs-lookup"><span data-stu-id="1b41e-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="1b41e-125">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="1b41e-125">Console application</span></span>                          | `console`        | <span data-ttu-id="1b41e-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1b41e-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1b41e-127">類別庫</span><span class="sxs-lookup"><span data-stu-id="1b41e-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="1b41e-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1b41e-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1b41e-129">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="1b41e-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="1b41e-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1b41e-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1b41e-131">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="1b41e-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="1b41e-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1b41e-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1b41e-133">NUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="1b41e-133">NUnit test project</span></span>                           | `nunit`          | <span data-ttu-id="1b41e-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1b41e-134">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1b41e-135">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="1b41e-135">Razor page</span></span>                                   | `page`           | <span data-ttu-id="1b41e-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-136">[C#]</span></span>          |
| <span data-ttu-id="1b41e-137">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="1b41e-137">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="1b41e-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-138">[C#]</span></span>          |
| <span data-ttu-id="1b41e-139">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="1b41e-139">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="1b41e-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-140">[C#]</span></span>          |
| <span data-ttu-id="1b41e-141">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1b41e-141">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="1b41e-142">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-142">[C#], F#</span></span>      |
| <span data-ttu-id="1b41e-143">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="1b41e-143">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="1b41e-144">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-144">[C#], F#</span></span>      |
| <span data-ttu-id="1b41e-145">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="1b41e-145">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="1b41e-146">`razor`、 `webapp`</span><span class="sxs-lookup"><span data-stu-id="1b41e-146">`razor`, `webapp`</span></span>| <span data-ttu-id="1b41e-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-147">[C#]</span></span>          |
| <span data-ttu-id="1b41e-148">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="1b41e-148">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="1b41e-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-149">[C#]</span></span>          |
| <span data-ttu-id="1b41e-150">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="1b41e-150">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="1b41e-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-151">[C#]</span></span>          |
| <span data-ttu-id="1b41e-152">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="1b41e-152">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="1b41e-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-153">[C#]</span></span>          |
| <span data-ttu-id="1b41e-154">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="1b41e-154">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="1b41e-155">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-155">[C#], F#</span></span>      |
| <span data-ttu-id="1b41e-156">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="1b41e-156">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="1b41e-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-157">[C#]</span></span>          |
| <span data-ttu-id="1b41e-158">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="1b41e-158">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="1b41e-159">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="1b41e-159">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="1b41e-160">Web 組態</span><span class="sxs-lookup"><span data-stu-id="1b41e-160">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="1b41e-161">方案檔</span><span class="sxs-lookup"><span data-stu-id="1b41e-161">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1b41e-162">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1b41e-162">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="1b41e-163">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="1b41e-163">The command contains a default list of templates.</span></span> <span data-ttu-id="1b41e-164">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="1b41e-164">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="1b41e-165">下表顯示隨 .NET Core SDK 2.0 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-165">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="1b41e-166">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="1b41e-166">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="1b41e-167">範本描述</span><span class="sxs-lookup"><span data-stu-id="1b41e-167">Template description</span></span>                          | <span data-ttu-id="1b41e-168">範本名稱</span><span class="sxs-lookup"><span data-stu-id="1b41e-168">Template name</span></span> | <span data-ttu-id="1b41e-169">語言</span><span class="sxs-lookup"><span data-stu-id="1b41e-169">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="1b41e-170">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="1b41e-170">Console application</span></span>                          | `console`     | <span data-ttu-id="1b41e-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1b41e-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1b41e-172">類別庫</span><span class="sxs-lookup"><span data-stu-id="1b41e-172">Class library</span></span>                                | `classlib`    | <span data-ttu-id="1b41e-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1b41e-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1b41e-174">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="1b41e-174">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="1b41e-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1b41e-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1b41e-176">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="1b41e-176">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="1b41e-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="1b41e-177">[C#], F#, VB</span></span>  |
| <span data-ttu-id="1b41e-178">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1b41e-178">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="1b41e-179">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-179">[C#], F#</span></span>      |
| <span data-ttu-id="1b41e-180">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="1b41e-180">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="1b41e-181">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-181">[C#], F#</span></span>      |
| <span data-ttu-id="1b41e-182">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="1b41e-182">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="1b41e-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-183">[C#]</span></span>          |
| <span data-ttu-id="1b41e-184">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="1b41e-184">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="1b41e-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-185">[C#]</span></span>          |
| <span data-ttu-id="1b41e-186">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="1b41e-186">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="1b41e-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-187">[C#]</span></span>          |
| <span data-ttu-id="1b41e-188">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="1b41e-188">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="1b41e-189">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-189">[C#]</span></span>          |
| <span data-ttu-id="1b41e-190">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="1b41e-190">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="1b41e-191">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-191">[C#], F#</span></span>      |
| <span data-ttu-id="1b41e-192">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="1b41e-192">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="1b41e-193">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="1b41e-193">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="1b41e-194">Web 組態</span><span class="sxs-lookup"><span data-stu-id="1b41e-194">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="1b41e-195">方案檔</span><span class="sxs-lookup"><span data-stu-id="1b41e-195">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="1b41e-196">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="1b41e-196">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="1b41e-197">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="1b41e-197">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="1b41e-198">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="1b41e-198">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1b41e-199">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1b41e-199">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="1b41e-200">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="1b41e-200">The command contains a default list of templates.</span></span> <span data-ttu-id="1b41e-201">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="1b41e-201">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="1b41e-202">下表顯示隨 .NET Core SDK 1.x 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-202">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="1b41e-203">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="1b41e-203">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="1b41e-204">範本描述</span><span class="sxs-lookup"><span data-stu-id="1b41e-204">Template description</span></span>  | <span data-ttu-id="1b41e-205">範本名稱</span><span class="sxs-lookup"><span data-stu-id="1b41e-205">Template name</span></span> | <span data-ttu-id="1b41e-206">語言</span><span class="sxs-lookup"><span data-stu-id="1b41e-206">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="1b41e-207">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="1b41e-207">Console application</span></span>  | `console`     | <span data-ttu-id="1b41e-208">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-208">[C#], F#</span></span>  |
| <span data-ttu-id="1b41e-209">類別庫</span><span class="sxs-lookup"><span data-stu-id="1b41e-209">Class library</span></span>        | `classlib`    | <span data-ttu-id="1b41e-210">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-210">[C#], F#</span></span>  |
| <span data-ttu-id="1b41e-211">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="1b41e-211">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="1b41e-212">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-212">[C#], F#</span></span>  |
| <span data-ttu-id="1b41e-213">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="1b41e-213">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="1b41e-214">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-214">[C#], F#</span></span>  |
| <span data-ttu-id="1b41e-215">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1b41e-215">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="1b41e-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-216">[C#]</span></span>      |
| <span data-ttu-id="1b41e-217">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="1b41e-217">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="1b41e-218">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="1b41e-218">[C#], F#</span></span>  |
| <span data-ttu-id="1b41e-219">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="1b41e-219">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="1b41e-220">[C#]</span><span class="sxs-lookup"><span data-stu-id="1b41e-220">[C#]</span></span>      |
| <span data-ttu-id="1b41e-221">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="1b41e-221">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="1b41e-222">Web 組態</span><span class="sxs-lookup"><span data-stu-id="1b41e-222">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="1b41e-223">方案檔</span><span class="sxs-lookup"><span data-stu-id="1b41e-223">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="1b41e-224">選項</span><span class="sxs-lookup"><span data-stu-id="1b41e-224">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1b41e-225">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1b41e-225">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="1b41e-226">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="1b41e-226">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="1b41e-227">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="1b41e-227">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="1b41e-228">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="1b41e-228">Prints out help for the command.</span></span> <span data-ttu-id="1b41e-229">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-229">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="1b41e-230">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="1b41e-230">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="1b41e-231">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-231">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="1b41e-232">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-232">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="1b41e-233">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="1b41e-233">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="1b41e-234">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-234">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="1b41e-235">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-235">Lists templates containing the specified name.</span></span> <span data-ttu-id="1b41e-236">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-236">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="1b41e-237">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-237">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="1b41e-238">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="1b41e-238">The language of the template to create.</span></span> <span data-ttu-id="1b41e-239">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-239">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="1b41e-240">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-240">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="1b41e-241">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="1b41e-241">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="1b41e-242">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-242">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="1b41e-243">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b41e-243">The name for the created output.</span></span> <span data-ttu-id="1b41e-244">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b41e-244">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="1b41e-245">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="1b41e-245">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1b41e-246">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="1b41e-246">Location to place the generated output.</span></span> <span data-ttu-id="1b41e-247">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="1b41e-247">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="1b41e-248">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-248">Filters templates based on available types.</span></span> <span data-ttu-id="1b41e-249">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="1b41e-249">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="1b41e-250">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="1b41e-250">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="1b41e-251">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="1b41e-251">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="1b41e-252">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="1b41e-252">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="1b41e-253">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="1b41e-253">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1b41e-254">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1b41e-254">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="1b41e-255">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="1b41e-255">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="1b41e-256">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="1b41e-256">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="1b41e-257">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="1b41e-257">Prints out help for the command.</span></span> <span data-ttu-id="1b41e-258">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-258">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="1b41e-259">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="1b41e-259">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="1b41e-260">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-260">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="1b41e-261">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-261">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="1b41e-262">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="1b41e-262">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="1b41e-263">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-263">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="1b41e-264">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-264">Lists templates containing the specified name.</span></span> <span data-ttu-id="1b41e-265">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-265">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="1b41e-266">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-266">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="1b41e-267">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="1b41e-267">The language of the template to create.</span></span> <span data-ttu-id="1b41e-268">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-268">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="1b41e-269">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-269">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="1b41e-270">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="1b41e-270">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="1b41e-271">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-271">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="1b41e-272">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b41e-272">The name for the created output.</span></span> <span data-ttu-id="1b41e-273">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b41e-273">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1b41e-274">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="1b41e-274">Location to place the generated output.</span></span> <span data-ttu-id="1b41e-275">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="1b41e-275">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="1b41e-276">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-276">Filters templates based on available types.</span></span> <span data-ttu-id="1b41e-277">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="1b41e-277">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="1b41e-278">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="1b41e-278">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="1b41e-279">若要使用來源 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="1b41e-279">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="1b41e-280">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="1b41e-280">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="1b41e-281">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="1b41e-281">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="1b41e-282">如果您無法判斷將範本解除安裝需要 `PATH` 或是 `NUGET_ID` 引數，在沒有引數的情況下執行 `dotnet new --uninstall` 會列出所有已安裝的範本，以及將它們解除安裝所需的引數。</span><span class="sxs-lookup"><span data-stu-id="1b41e-282">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1b41e-283">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1b41e-283">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="1b41e-284">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-284">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="1b41e-285">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="1b41e-285">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="1b41e-286">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="1b41e-286">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="1b41e-287">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="1b41e-287">Prints out help for the command.</span></span> <span data-ttu-id="1b41e-288">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-288">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="1b41e-289">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-289">Lists templates containing the specified name.</span></span> <span data-ttu-id="1b41e-290">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-290">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="1b41e-291">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-291">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="1b41e-292">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="1b41e-292">The language of the template to create.</span></span> <span data-ttu-id="1b41e-293">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-293">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="1b41e-294">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-294">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="1b41e-295">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="1b41e-295">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="1b41e-296">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-296">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="1b41e-297">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b41e-297">The name for the created output.</span></span> <span data-ttu-id="1b41e-298">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b41e-298">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1b41e-299">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="1b41e-299">Location to place the generated output.</span></span> <span data-ttu-id="1b41e-300">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="1b41e-300">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="1b41e-301">範本選項</span><span class="sxs-lookup"><span data-stu-id="1b41e-301">Template options</span></span>

<span data-ttu-id="1b41e-302">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="1b41e-302">Each project template may have additional options available.</span></span> <span data-ttu-id="1b41e-303">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="1b41e-303">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1b41e-304">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1b41e-304">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="1b41e-305">**主控台, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="1b41e-305">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="1b41e-306">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-306">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-307">**classlib**</span><span class="sxs-lookup"><span data-stu-id="1b41e-307">**classlib**</span></span>

<span data-ttu-id="1b41e-308">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-308">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="1b41e-309">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="1b41e-309">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="1b41e-310">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-310">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="1b41e-311">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-312">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="1b41e-312">**mstest, xunit**</span></span>

<span data-ttu-id="1b41e-313">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="1b41e-313">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="1b41e-314">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-314">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-315">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="1b41e-315">**globaljson**</span></span>

<span data-ttu-id="1b41e-316">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-316">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="1b41e-317">**web**</span><span class="sxs-lookup"><span data-stu-id="1b41e-317">**web**</span></span>

<span data-ttu-id="1b41e-318">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1b41e-318">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="1b41e-319">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-319">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-320">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="1b41e-320">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="1b41e-321">此選項僅適用於未使用 `IndividualAuth` 或 `OrganizationalAuth` 時。</span><span class="sxs-lookup"><span data-stu-id="1b41e-321">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="1b41e-322">**webapi**</span><span class="sxs-lookup"><span data-stu-id="1b41e-322">**webapi**</span></span>

<span data-ttu-id="1b41e-323">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1b41e-323">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="1b41e-324">可能值為：</span><span class="sxs-lookup"><span data-stu-id="1b41e-324">The possible values are:</span></span>

- <span data-ttu-id="1b41e-325">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-325">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="1b41e-326">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-326">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="1b41e-327">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-327">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="1b41e-328">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-328">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="1b41e-329">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b41e-329">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="1b41e-330">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-330">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="1b41e-331">預設值為 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-331">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="1b41e-332">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-332">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="1b41e-333">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-333">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-334">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b41e-334">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="1b41e-335">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-335">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1b41e-336">預設值為 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-336">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="1b41e-337">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-337">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="1b41e-338">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-338">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="1b41e-339">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-339">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="1b41e-340">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="1b41e-340">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="1b41e-341">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-341">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1b41e-342">預設值為 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-342">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="1b41e-343">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-343">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="1b41e-344">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-344">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1b41e-345">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-345">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="1b41e-346">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="1b41e-346">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="1b41e-347">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-347">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="1b41e-348">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1b41e-348">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="1b41e-349">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="1b41e-349">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="1b41e-350">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-350">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-351">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-351">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-352">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="1b41e-352">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="1b41e-353">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-353">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="1b41e-354">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="1b41e-354">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="1b41e-355">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="1b41e-355">**mvc, razor**</span></span>

<span data-ttu-id="1b41e-356">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1b41e-356">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="1b41e-357">可能值為：</span><span class="sxs-lookup"><span data-stu-id="1b41e-357">The possible values are:</span></span>

- <span data-ttu-id="1b41e-358">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-358">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="1b41e-359">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-359">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="1b41e-360">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-360">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="1b41e-361">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-361">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="1b41e-362">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-362">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="1b41e-363">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-363">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="1b41e-364">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b41e-364">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="1b41e-365">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-365">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="1b41e-366">預設值為 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-366">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="1b41e-367">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-367">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="1b41e-368">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-369">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-369">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="1b41e-370">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-371">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-371">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="1b41e-372">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-372">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-373">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b41e-373">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="1b41e-374">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-374">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="1b41e-375">預設值為 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-375">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="1b41e-376">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-376">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="1b41e-377">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-377">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="1b41e-378">預設值為 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-378">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="1b41e-379">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="1b41e-379">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="1b41e-380">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-380">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1b41e-381">預設值為 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-381">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="1b41e-382">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-382">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="1b41e-383">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-383">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1b41e-384">預設值為 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-384">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="1b41e-385">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="1b41e-385">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="1b41e-386">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-386">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1b41e-387">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-387">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="1b41e-388">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="1b41e-388">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="1b41e-389">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-389">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="1b41e-390">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1b41e-390">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="1b41e-391">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="1b41e-391">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="1b41e-392">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="1b41e-392">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="1b41e-393">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-393">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-394">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-395">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="1b41e-395">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="1b41e-396">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-396">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="1b41e-397">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="1b41e-397">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="1b41e-398">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="1b41e-398">**page**</span></span>

<span data-ttu-id="1b41e-399">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1b41e-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="1b41e-400">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-400">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="1b41e-401">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="1b41e-401">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="1b41e-402">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="1b41e-402">**viewimports**</span></span>

<span data-ttu-id="1b41e-403">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1b41e-403">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="1b41e-404">預設值為 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-404">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1b41e-405">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1b41e-405">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="1b41e-406">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="1b41e-406">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="1b41e-407">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-407">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-408">**classlib**</span><span class="sxs-lookup"><span data-stu-id="1b41e-408">**classlib**</span></span>

<span data-ttu-id="1b41e-409">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-409">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="1b41e-410">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="1b41e-410">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="1b41e-411">預設值為 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-411">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="1b41e-412">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-413">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="1b41e-413">**mstest, xunit**</span></span>

<span data-ttu-id="1b41e-414">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="1b41e-414">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="1b41e-415">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-415">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-416">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="1b41e-416">**globaljson**</span></span>

<span data-ttu-id="1b41e-417">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="1b41e-417">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="1b41e-418">**web**</span><span class="sxs-lookup"><span data-stu-id="1b41e-418">**web**</span></span>

<span data-ttu-id="1b41e-419">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1b41e-419">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="1b41e-420">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-420">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-421">**webapi**</span><span class="sxs-lookup"><span data-stu-id="1b41e-421">**webapi**</span></span>

<span data-ttu-id="1b41e-422">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1b41e-422">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="1b41e-423">可能值為：</span><span class="sxs-lookup"><span data-stu-id="1b41e-423">The possible values are:</span></span>

- <span data-ttu-id="1b41e-424">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-424">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="1b41e-425">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-425">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="1b41e-426">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-426">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="1b41e-427">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-427">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="1b41e-428">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b41e-428">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="1b41e-429">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-429">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="1b41e-430">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-430">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="1b41e-431">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-431">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="1b41e-432">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-432">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-433">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b41e-433">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="1b41e-434">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-434">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1b41e-435">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-435">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="1b41e-436">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-436">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="1b41e-437">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-437">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="1b41e-438">預設值為 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-438">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="1b41e-439">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="1b41e-439">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="1b41e-440">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-440">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1b41e-441">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-441">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="1b41e-442">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-442">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="1b41e-443">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-443">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1b41e-444">預設值為 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-444">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="1b41e-445">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="1b41e-445">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="1b41e-446">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-446">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="1b41e-447">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1b41e-447">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="1b41e-448">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="1b41e-448">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="1b41e-449">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-449">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-450">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-450">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-451">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="1b41e-451">**mvc, razor**</span></span>

<span data-ttu-id="1b41e-452">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1b41e-452">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="1b41e-453">可能值為：</span><span class="sxs-lookup"><span data-stu-id="1b41e-453">The possible values are:</span></span>

- <span data-ttu-id="1b41e-454">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-454">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="1b41e-455">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-455">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="1b41e-456">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-456">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="1b41e-457">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-457">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="1b41e-458">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-458">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="1b41e-459">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-459">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="1b41e-460">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b41e-460">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="1b41e-461">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-461">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="1b41e-462">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-462">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="1b41e-463">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-463">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="1b41e-464">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-465">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-465">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="1b41e-466">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-467">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-467">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="1b41e-468">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-468">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-469">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b41e-469">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="1b41e-470">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-470">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="1b41e-471">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-471">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="1b41e-472">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-472">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="1b41e-473">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-473">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="1b41e-474">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-474">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="1b41e-475">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="1b41e-475">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="1b41e-476">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-476">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1b41e-477">預設值為 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-477">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="1b41e-478">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b41e-478">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="1b41e-479">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-479">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="1b41e-480">預設值為 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-480">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="1b41e-481">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="1b41e-481">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="1b41e-482">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="1b41e-482">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="1b41e-483">預設值為 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-483">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="1b41e-484">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="1b41e-484">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="1b41e-485">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-485">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="1b41e-486">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="1b41e-486">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="1b41e-487">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="1b41e-487">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="1b41e-488">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="1b41e-488">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="1b41e-489">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b41e-489">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="1b41e-490">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="1b41e-490">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="1b41e-491">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="1b41e-491">**page**</span></span>

<span data-ttu-id="1b41e-492">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1b41e-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="1b41e-493">預設值為 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-493">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="1b41e-494">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="1b41e-494">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="1b41e-495">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="1b41e-495">**viewimports**</span></span>

<span data-ttu-id="1b41e-496">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1b41e-496">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="1b41e-497">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-497">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1b41e-498">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1b41e-498">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="1b41e-499">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="1b41e-499">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="1b41e-500">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="1b41e-501">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-501">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="1b41e-502">預設值為 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-502">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="1b41e-503">**classlib**</span><span class="sxs-lookup"><span data-stu-id="1b41e-503">**classlib**</span></span>

<span data-ttu-id="1b41e-504">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="1b41e-505">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-505">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="1b41e-506">預設值為 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-506">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="1b41e-507">**mvc**</span><span class="sxs-lookup"><span data-stu-id="1b41e-507">**mvc**</span></span>

<span data-ttu-id="1b41e-508">`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1b41e-508">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="1b41e-509">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-509">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="1b41e-510">預設值為 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-510">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="1b41e-511">`-au|--auth` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1b41e-511">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="1b41e-512">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-512">Values: `None` or `Individual`.</span></span> <span data-ttu-id="1b41e-513">預設值為 `None`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-513">The default value is `None`.</span></span>

<span data-ttu-id="1b41e-514">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="1b41e-514">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="1b41e-515">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-515">Values: `true` or `false`.</span></span> <span data-ttu-id="1b41e-516">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="1b41e-516">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="1b41e-517">範例</span><span class="sxs-lookup"><span data-stu-id="1b41e-517">Examples</span></span>

<span data-ttu-id="1b41e-518">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="1b41e-518">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="1b41e-519">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core SDK 2.0 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="1b41e-519">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="1b41e-520">未經驗證即在目前的目錄中建立新 ASP.NET Core C# MVC 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="1b41e-520">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="1b41e-521">建立新的 xUnit 應用程式：</span><span class="sxs-lookup"><span data-stu-id="1b41e-521">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="1b41e-522">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="1b41e-522">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="1b41e-523">安裝適用於 ASP.NET Core 的單頁應用程式範本 2.0 版 (僅適用於 .NET Core SDK 1.1 及更新版本的命令選項)：</span><span class="sxs-lookup"><span data-stu-id="1b41e-523">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="1b41e-524">在目前目錄中建立 *global.json*，並將 SDK 版本設為 2.0.0 (只能用於.NET Core SDK 2.0 或更新版本)：</span><span class="sxs-lookup"><span data-stu-id="1b41e-524">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="1b41e-525">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b41e-525">See also</span></span>

* [<span data-ttu-id="1b41e-526">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="1b41e-526">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="1b41e-527">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="1b41e-527">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* <span data-ttu-id="1b41e-528">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="1b41e-528">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
* [<span data-ttu-id="1b41e-529">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="1b41e-529">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
