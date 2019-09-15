---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
ms.date: 05/06/2019
ms.openlocfilehash: 57b198d13984fb4585e1df6303afe481e7e0552d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969742"
---
# <a name="dotnet-new"></a><span data-ttu-id="b32be-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b32be-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b32be-104">名稱</span><span class="sxs-lookup"><span data-stu-id="b32be-104">Name</span></span>

<span data-ttu-id="b32be-105">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="b32be-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b32be-106">概要</span><span class="sxs-lookup"><span data-stu-id="b32be-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b32be-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b32be-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b32be-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b32be-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b32be-109">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b32be-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b32be-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b32be-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="b32be-111">描述</span><span class="sxs-lookup"><span data-stu-id="b32be-111">Description</span></span>

<span data-ttu-id="b32be-112">`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="b32be-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="b32be-113">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="b32be-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="b32be-114">引數</span><span class="sxs-lookup"><span data-stu-id="b32be-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="b32be-115">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="b32be-116">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="b32be-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="b32be-117">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="b32be-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="b32be-118">如果 `TEMPLATE` 值與 [範本] 或 [簡短名稱] 欄中的文字不完全相符，則會對這兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="b32be-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b32be-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b32be-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="b32be-120">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="b32be-120">The command contains a default list of templates.</span></span> <span data-ttu-id="b32be-121">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="b32be-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b32be-122">下表顯示隨 .NET Core SDK 2.2.100 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="b32be-123">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="b32be-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b32be-124">範本</span><span class="sxs-lookup"><span data-stu-id="b32be-124">Templates</span></span>                                    | <span data-ttu-id="b32be-125">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="b32be-125">Short Name</span></span>        | <span data-ttu-id="b32be-126">語言</span><span class="sxs-lookup"><span data-stu-id="b32be-126">Language</span></span>     | <span data-ttu-id="b32be-127">Tags</span><span class="sxs-lookup"><span data-stu-id="b32be-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="b32be-128">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="b32be-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="b32be-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-129">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-130">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="b32be-130">Common/Console</span></span>                        |
| <span data-ttu-id="b32be-131">類別庫</span><span class="sxs-lookup"><span data-stu-id="b32be-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="b32be-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-132">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-133">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="b32be-133">Common/Library</span></span>                        |
| <span data-ttu-id="b32be-134">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="b32be-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="b32be-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-135">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-136">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="b32be-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="b32be-137">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="b32be-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="b32be-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-138">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-139">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="b32be-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="b32be-140">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="b32be-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="b32be-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-141">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-142">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="b32be-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="b32be-143">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="b32be-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="b32be-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-144">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-145">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="b32be-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="b32be-146">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="b32be-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="b32be-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-147">[C#]</span></span>         | <span data-ttu-id="b32be-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b32be-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b32be-149">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="b32be-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="b32be-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-150">[C#]</span></span>         | <span data-ttu-id="b32be-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b32be-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b32be-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b32be-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="b32be-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-153">[C#]</span></span>         | <span data-ttu-id="b32be-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b32be-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b32be-155">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b32be-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="b32be-156">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-156">[C#], F#</span></span>     | <span data-ttu-id="b32be-157">Web/空白</span><span class="sxs-lookup"><span data-stu-id="b32be-157">Web/Empty</span></span>                             |
| <span data-ttu-id="b32be-158">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="b32be-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="b32be-159">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-159">[C#], F#</span></span>     | <span data-ttu-id="b32be-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b32be-160">Web/MVC</span></span>                               |
| <span data-ttu-id="b32be-161">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="b32be-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="b32be-162">`webapp`、 `razor`</span><span class="sxs-lookup"><span data-stu-id="b32be-162">`webapp`, `razor`</span></span> | <span data-ttu-id="b32be-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-163">[C#]</span></span>         | <span data-ttu-id="b32be-164">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="b32be-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="b32be-165">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="b32be-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="b32be-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-166">[C#]</span></span>         | <span data-ttu-id="b32be-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b32be-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b32be-168">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="b32be-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="b32be-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-169">[C#]</span></span>         | <span data-ttu-id="b32be-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b32be-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b32be-171">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="b32be-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="b32be-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-172">[C#]</span></span>         | <span data-ttu-id="b32be-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b32be-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b32be-174">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="b32be-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="b32be-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-175">[C#]</span></span>         | <span data-ttu-id="b32be-176">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="b32be-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="b32be-177">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="b32be-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="b32be-178">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-178">[C#], F#</span></span>     | <span data-ttu-id="b32be-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b32be-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="b32be-180">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="b32be-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="b32be-181">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-181">Config</span></span>                                |
| <span data-ttu-id="b32be-182">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="b32be-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="b32be-183">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-183">Config</span></span>                                |
| <span data-ttu-id="b32be-184">Web 組態</span><span class="sxs-lookup"><span data-stu-id="b32be-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="b32be-185">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-185">Config</span></span>                                |
| <span data-ttu-id="b32be-186">方案檔</span><span class="sxs-lookup"><span data-stu-id="b32be-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="b32be-187">方案</span><span class="sxs-lookup"><span data-stu-id="b32be-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b32be-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b32be-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="b32be-189">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="b32be-189">The command contains a default list of templates.</span></span> <span data-ttu-id="b32be-190">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="b32be-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b32be-191">下表顯示隨 .NET Core SDK 2.1.300 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="b32be-192">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="b32be-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b32be-193">範本</span><span class="sxs-lookup"><span data-stu-id="b32be-193">Templates</span></span>                                    | <span data-ttu-id="b32be-194">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="b32be-194">Short Name</span></span>      | <span data-ttu-id="b32be-195">語言</span><span class="sxs-lookup"><span data-stu-id="b32be-195">Language</span></span>     | <span data-ttu-id="b32be-196">Tags</span><span class="sxs-lookup"><span data-stu-id="b32be-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="b32be-197">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="b32be-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="b32be-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-198">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-199">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="b32be-199">Common/Console</span></span>                        |
| <span data-ttu-id="b32be-200">類別庫</span><span class="sxs-lookup"><span data-stu-id="b32be-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="b32be-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-201">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-202">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="b32be-202">Common/Library</span></span>                        |
| <span data-ttu-id="b32be-203">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="b32be-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="b32be-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-204">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-205">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="b32be-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="b32be-206">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="b32be-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="b32be-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-207">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-208">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="b32be-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="b32be-209">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="b32be-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="b32be-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-210">[C#]</span></span>         | <span data-ttu-id="b32be-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b32be-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b32be-212">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="b32be-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="b32be-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-213">[C#]</span></span>         | <span data-ttu-id="b32be-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b32be-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b32be-215">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b32be-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="b32be-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-216">[C#]</span></span>         | <span data-ttu-id="b32be-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b32be-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b32be-218">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b32be-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="b32be-219">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-219">[C#], F#</span></span>     | <span data-ttu-id="b32be-220">Web/空白</span><span class="sxs-lookup"><span data-stu-id="b32be-220">Web/Empty</span></span>                             |
| <span data-ttu-id="b32be-221">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="b32be-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="b32be-222">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-222">[C#], F#</span></span>     | <span data-ttu-id="b32be-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b32be-223">Web/MVC</span></span>                               |
| <span data-ttu-id="b32be-224">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="b32be-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="b32be-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-225">[C#]</span></span>         | <span data-ttu-id="b32be-226">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="b32be-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="b32be-227">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="b32be-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="b32be-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-228">[C#]</span></span>         | <span data-ttu-id="b32be-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b32be-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b32be-230">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="b32be-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="b32be-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-231">[C#]</span></span>         | <span data-ttu-id="b32be-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b32be-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b32be-233">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="b32be-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="b32be-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-234">[C#]</span></span>         | <span data-ttu-id="b32be-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b32be-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="b32be-236">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="b32be-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="b32be-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-237">[C#]</span></span>         | <span data-ttu-id="b32be-238">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="b32be-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="b32be-239">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="b32be-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="b32be-240">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-240">[C#], F#</span></span>     | <span data-ttu-id="b32be-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b32be-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="b32be-242">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="b32be-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="b32be-243">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-243">Config</span></span>                                |
| <span data-ttu-id="b32be-244">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="b32be-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="b32be-245">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-245">Config</span></span>                                |
| <span data-ttu-id="b32be-246">Web 組態</span><span class="sxs-lookup"><span data-stu-id="b32be-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="b32be-247">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-247">Config</span></span>                                |
| <span data-ttu-id="b32be-248">方案檔</span><span class="sxs-lookup"><span data-stu-id="b32be-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="b32be-249">方案</span><span class="sxs-lookup"><span data-stu-id="b32be-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b32be-250">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b32be-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="b32be-251">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="b32be-251">The command contains a default list of templates.</span></span> <span data-ttu-id="b32be-252">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="b32be-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b32be-253">下表顯示隨 .NET Core SDK 2.0.0 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="b32be-254">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="b32be-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b32be-255">範本</span><span class="sxs-lookup"><span data-stu-id="b32be-255">Templates</span></span>                                    | <span data-ttu-id="b32be-256">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="b32be-256">Short Name</span></span>    | <span data-ttu-id="b32be-257">語言</span><span class="sxs-lookup"><span data-stu-id="b32be-257">Language</span></span>     | <span data-ttu-id="b32be-258">Tags</span><span class="sxs-lookup"><span data-stu-id="b32be-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="b32be-259">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="b32be-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="b32be-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-260">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-261">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="b32be-261">Common/Console</span></span>      |
| <span data-ttu-id="b32be-262">類別庫</span><span class="sxs-lookup"><span data-stu-id="b32be-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="b32be-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-263">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-264">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="b32be-264">Common/Library</span></span>      |
| <span data-ttu-id="b32be-265">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="b32be-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="b32be-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-266">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-267">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="b32be-267">Test/MSTest</span></span>         |
| <span data-ttu-id="b32be-268">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="b32be-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="b32be-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b32be-269">[C#], F#, VB</span></span> | <span data-ttu-id="b32be-270">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="b32be-270">Test/xUnit</span></span>          |
| <span data-ttu-id="b32be-271">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b32be-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="b32be-272">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-272">[C#], F#</span></span>     | <span data-ttu-id="b32be-273">Web/空白</span><span class="sxs-lookup"><span data-stu-id="b32be-273">Web/Empty</span></span>           |
| <span data-ttu-id="b32be-274">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="b32be-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="b32be-275">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-275">[C#], F#</span></span>     | <span data-ttu-id="b32be-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b32be-276">Web/MVC</span></span>             |
| <span data-ttu-id="b32be-277">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="b32be-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="b32be-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-278">[C#]</span></span>         | <span data-ttu-id="b32be-279">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="b32be-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="b32be-280">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="b32be-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="b32be-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-281">[C#]</span></span>         | <span data-ttu-id="b32be-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b32be-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="b32be-283">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="b32be-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="b32be-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-284">[C#]</span></span>         | <span data-ttu-id="b32be-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b32be-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="b32be-286">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="b32be-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="b32be-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-287">[C#]</span></span>         | <span data-ttu-id="b32be-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b32be-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="b32be-289">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="b32be-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="b32be-290">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-290">[C#], F#</span></span>     | <span data-ttu-id="b32be-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b32be-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="b32be-292">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="b32be-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="b32be-293">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-293">Config</span></span>              |
| <span data-ttu-id="b32be-294">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="b32be-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="b32be-295">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-295">Config</span></span>              |
| <span data-ttu-id="b32be-296">Web 組態</span><span class="sxs-lookup"><span data-stu-id="b32be-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="b32be-297">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-297">Config</span></span>              |
| <span data-ttu-id="b32be-298">方案檔</span><span class="sxs-lookup"><span data-stu-id="b32be-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="b32be-299">方案</span><span class="sxs-lookup"><span data-stu-id="b32be-299">Solution</span></span>            |
| <span data-ttu-id="b32be-300">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="b32be-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="b32be-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b32be-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="b32be-302">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="b32be-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="b32be-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b32be-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="b32be-304">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b32be-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="b32be-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b32be-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b32be-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b32be-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b32be-307">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="b32be-307">The command contains a default list of templates.</span></span> <span data-ttu-id="b32be-308">使用 `dotnet new -all` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="b32be-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="b32be-309">下表顯示隨 .NET Core SDK 1.0.1 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="b32be-310">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="b32be-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b32be-311">範本</span><span class="sxs-lookup"><span data-stu-id="b32be-311">Templates</span></span>            | <span data-ttu-id="b32be-312">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="b32be-312">Short Name</span></span>    | <span data-ttu-id="b32be-313">語言</span><span class="sxs-lookup"><span data-stu-id="b32be-313">Language</span></span> | <span data-ttu-id="b32be-314">Tags</span><span class="sxs-lookup"><span data-stu-id="b32be-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="b32be-315">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="b32be-315">Console Application</span></span>  | `console`     | <span data-ttu-id="b32be-316">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-316">[C#], F#</span></span> | <span data-ttu-id="b32be-317">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="b32be-317">Common/Console</span></span> |
| <span data-ttu-id="b32be-318">類別庫</span><span class="sxs-lookup"><span data-stu-id="b32be-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="b32be-319">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-319">[C#], F#</span></span> | <span data-ttu-id="b32be-320">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="b32be-320">Common/Library</span></span> |
| <span data-ttu-id="b32be-321">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="b32be-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="b32be-322">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-322">[C#], F#</span></span> | <span data-ttu-id="b32be-323">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="b32be-323">Test/MSTest</span></span>    |
| <span data-ttu-id="b32be-324">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="b32be-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="b32be-325">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-325">[C#], F#</span></span> | <span data-ttu-id="b32be-326">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="b32be-326">Test/xUnit</span></span>     |
| <span data-ttu-id="b32be-327">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b32be-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="b32be-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-328">[C#]</span></span>     | <span data-ttu-id="b32be-329">Web/空白</span><span class="sxs-lookup"><span data-stu-id="b32be-329">Web/Empty</span></span>      |
| <span data-ttu-id="b32be-330">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="b32be-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="b32be-331">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b32be-331">[C#], F#</span></span> | <span data-ttu-id="b32be-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b32be-332">Web/MVC</span></span>        |
| <span data-ttu-id="b32be-333">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="b32be-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="b32be-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="b32be-334">[C#]</span></span>     | <span data-ttu-id="b32be-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b32be-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="b32be-336">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="b32be-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="b32be-337">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-337">Config</span></span>         |
| <span data-ttu-id="b32be-338">Web 組態</span><span class="sxs-lookup"><span data-stu-id="b32be-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="b32be-339">組態</span><span class="sxs-lookup"><span data-stu-id="b32be-339">Config</span></span>         |
| <span data-ttu-id="b32be-340">方案檔</span><span class="sxs-lookup"><span data-stu-id="b32be-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="b32be-341">方案</span><span class="sxs-lookup"><span data-stu-id="b32be-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="b32be-342">選項</span><span class="sxs-lookup"><span data-stu-id="b32be-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b32be-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b32be-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="b32be-344">若指定的命令會導致建立範本，則顯示執行時會發生的情況摘要。</span><span class="sxs-lookup"><span data-stu-id="b32be-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="b32be-345">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="b32be-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b32be-346">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="b32be-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b32be-347">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="b32be-347">Prints out help for the command.</span></span> <span data-ttu-id="b32be-348">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="b32be-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="b32be-349">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="b32be-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b32be-350">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="b32be-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="b32be-351">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="b32be-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="b32be-352">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="b32be-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="b32be-353">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="b32be-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="b32be-354">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="b32be-355">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b32be-356">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="b32be-357">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="b32be-357">The language of the template to create.</span></span> <span data-ttu-id="b32be-358">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="b32be-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b32be-359">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="b32be-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b32be-360">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="b32be-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b32be-361">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="b32be-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b32be-362">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="b32be-362">The name for the created output.</span></span> <span data-ttu-id="b32be-363">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="b32be-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="b32be-364">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="b32be-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b32be-365">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="b32be-365">Location to place the generated output.</span></span> <span data-ttu-id="b32be-366">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="b32be-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="b32be-367">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-367">Filters templates based on available types.</span></span> <span data-ttu-id="b32be-368">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="b32be-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="b32be-369">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="b32be-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b32be-370">當您排除 `<PATH|NUGET_ID>` 值時，會顯示目前已安裝的所有範本組件及其相關聯範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="b32be-371">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b32be-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b32be-372">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="b32be-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="b32be-373">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="b32be-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b32be-374">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b32be-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="b32be-375">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="b32be-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b32be-376">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="b32be-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b32be-377">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="b32be-377">Prints out help for the command.</span></span> <span data-ttu-id="b32be-378">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="b32be-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="b32be-379">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="b32be-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b32be-380">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="b32be-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="b32be-381">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="b32be-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="b32be-382">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="b32be-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="b32be-383">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="b32be-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="b32be-384">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="b32be-385">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b32be-386">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="b32be-387">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="b32be-387">The language of the template to create.</span></span> <span data-ttu-id="b32be-388">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="b32be-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b32be-389">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="b32be-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b32be-390">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="b32be-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b32be-391">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="b32be-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b32be-392">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="b32be-392">The name for the created output.</span></span> <span data-ttu-id="b32be-393">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="b32be-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="b32be-394">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="b32be-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b32be-395">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="b32be-395">Location to place the generated output.</span></span> <span data-ttu-id="b32be-396">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="b32be-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="b32be-397">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-397">Filters templates based on available types.</span></span> <span data-ttu-id="b32be-398">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="b32be-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="b32be-399">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="b32be-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="b32be-400">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b32be-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b32be-401">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="b32be-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="b32be-402">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="b32be-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b32be-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b32be-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="b32be-404">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="b32be-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b32be-405">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="b32be-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b32be-406">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="b32be-406">Prints out help for the command.</span></span> <span data-ttu-id="b32be-407">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="b32be-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="b32be-408">安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="b32be-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b32be-409">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="b32be-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="b32be-410">根據預設，`dotnet new` 會傳遞版本的 \*，其代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="b32be-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="b32be-411">您可於[範例](#examples)一節查看範例。</span><span class="sxs-lookup"><span data-stu-id="b32be-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="b32be-412">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="b32be-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="b32be-413">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="b32be-414">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b32be-415">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="b32be-416">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="b32be-416">The language of the template to create.</span></span> <span data-ttu-id="b32be-417">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="b32be-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b32be-418">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="b32be-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b32be-419">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="b32be-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b32be-420">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="b32be-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b32be-421">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="b32be-421">The name for the created output.</span></span> <span data-ttu-id="b32be-422">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="b32be-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b32be-423">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="b32be-423">Location to place the generated output.</span></span> <span data-ttu-id="b32be-424">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="b32be-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="b32be-425">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-425">Filters templates based on available types.</span></span> <span data-ttu-id="b32be-426">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="b32be-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="b32be-427">解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。</span><span class="sxs-lookup"><span data-stu-id="b32be-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="b32be-428">若要使用來源 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b32be-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b32be-429">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="b32be-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="b32be-430">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="b32be-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="b32be-431">如果您無法判斷將範本解除安裝需要 `PATH` 或是 `NUGET_ID` 引數，在沒有引數的情況下執行 `dotnet new --uninstall` 會列出所有已安裝的範本，以及將它們解除安裝所需的引數。</span><span class="sxs-lookup"><span data-stu-id="b32be-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b32be-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b32be-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="b32be-433">單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="b32be-434">在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。</span><span class="sxs-lookup"><span data-stu-id="b32be-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="b32be-435">當輸出目錄中已包含專案時，這是必要選項。</span><span class="sxs-lookup"><span data-stu-id="b32be-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b32be-436">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="b32be-436">Prints out help for the command.</span></span> <span data-ttu-id="b32be-437">可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。</span><span class="sxs-lookup"><span data-stu-id="b32be-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="b32be-438">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="b32be-439">如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b32be-440">例如，如果目錄中已包含專案，則不會列出所有專案範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="b32be-441">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="b32be-441">The language of the template to create.</span></span> <span data-ttu-id="b32be-442">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="b32be-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b32be-443">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="b32be-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b32be-444">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="b32be-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b32be-445">在這些情況下，您需要括住語言參數值，例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="b32be-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b32be-446">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="b32be-446">The name for the created output.</span></span> <span data-ttu-id="b32be-447">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="b32be-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b32be-448">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="b32be-448">Location to place the generated output.</span></span> <span data-ttu-id="b32be-449">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="b32be-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="b32be-450">範本選項</span><span class="sxs-lookup"><span data-stu-id="b32be-450">Template options</span></span>

<span data-ttu-id="b32be-451">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="b32be-451">Each project template may have additional options available.</span></span> <span data-ttu-id="b32be-452">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="b32be-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b32be-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b32be-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="b32be-454">**主控台**</span><span class="sxs-lookup"><span data-stu-id="b32be-454">**console**</span></span>

<span data-ttu-id="b32be-455">`--langVersion <VERSION_NUMBER>` - 在建立的專案檔中設定 `LangVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b32be-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="b32be-456">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="b32be-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="b32be-457">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="b32be-457">Not supported for F#.</span></span>

<span data-ttu-id="b32be-458">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-459">**angular、react、reactredux**</span><span class="sxs-lookup"><span data-stu-id="b32be-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="b32be-460">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="b32be-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b32be-461">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-462">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b32be-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b32be-463">此選項僅適用於未使用 `IndividualAuth` 或 `OrganizationalAuth` 時。</span><span class="sxs-lookup"><span data-stu-id="b32be-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="b32be-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="b32be-464">**razorclasslib**</span></span>

<span data-ttu-id="b32be-465">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="b32be-466">**classlib**</span></span>

<span data-ttu-id="b32be-467">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b32be-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b32be-468">值：`netcoreapp2.2` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="b32be-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b32be-469">預設值為 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="b32be-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="b32be-470">`--langVersion <VERSION_NUMBER>` - 在建立的專案檔中設定 `LangVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b32be-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="b32be-471">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="b32be-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="b32be-472">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="b32be-472">Not supported for F#.</span></span>

<span data-ttu-id="b32be-473">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-474">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="b32be-474">**mstest, xunit**</span></span>

<span data-ttu-id="b32be-475">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="b32be-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b32be-476">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="b32be-477">**nunit**</span></span>

<span data-ttu-id="b32be-478">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b32be-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b32be-479">預設值為 `netcoreapp2.1`。</span><span class="sxs-lookup"><span data-stu-id="b32be-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="b32be-480">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="b32be-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b32be-481">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-482">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="b32be-482">**page**</span></span>

<span data-ttu-id="b32be-483">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b32be-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b32be-484">預設值為 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="b32be-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b32be-485">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="b32be-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="b32be-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="b32be-486">**viewimports**</span></span>

<span data-ttu-id="b32be-487">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b32be-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b32be-488">預設值為 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="b32be-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b32be-489">**web**</span><span class="sxs-lookup"><span data-stu-id="b32be-489">**web**</span></span>

<span data-ttu-id="b32be-490">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="b32be-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b32be-491">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-492">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b32be-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b32be-493">此選項僅適用於未使用 `IndividualAuth` 或 `OrganizationalAuth` 時。</span><span class="sxs-lookup"><span data-stu-id="b32be-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="b32be-494">**mvc、webapp**</span><span class="sxs-lookup"><span data-stu-id="b32be-494">**mvc, webapp**</span></span>

<span data-ttu-id="b32be-495">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b32be-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b32be-496">可能值為：</span><span class="sxs-lookup"><span data-stu-id="b32be-496">The possible values are:</span></span>

- <span data-ttu-id="b32be-497">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="b32be-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b32be-498">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="b32be-499">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b32be-500">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b32be-501">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="b32be-502">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b32be-503">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b32be-504">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-505">預設值為 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b32be-506">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b32be-507">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-508">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="b32be-509">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-510">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="b32be-511">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-512">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b32be-513">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b32be-514">預設值為 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b32be-515">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b32be-516">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b32be-517">預設值為 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="b32be-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b32be-518">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="b32be-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b32be-519">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-520">預設值為 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="b32be-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b32be-521">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b32be-522">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-523">預設值為 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="b32be-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b32be-524">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="b32be-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b32be-525">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-526">預設值為 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="b32be-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="b32be-527">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="b32be-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b32be-528">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b32be-529">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="b32be-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b32be-530">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b32be-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b32be-531">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="b32be-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b32be-532">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="b32be-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b32be-533">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b32be-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b32be-534">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-535">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="b32be-536">**webapi**</span></span>

<span data-ttu-id="b32be-537">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b32be-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b32be-538">可能值為：</span><span class="sxs-lookup"><span data-stu-id="b32be-538">The possible values are:</span></span>

- <span data-ttu-id="b32be-539">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="b32be-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b32be-540">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b32be-541">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b32be-542">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b32be-543">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b32be-544">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-545">預設值為 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b32be-546">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b32be-547">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-548">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b32be-549">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-550">預設值為 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b32be-551">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b32be-552">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-553">預設值為 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="b32be-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b32be-554">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="b32be-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b32be-555">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-556">預設值為 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="b32be-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b32be-557">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b32be-558">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-559">預設值為 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="b32be-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b32be-560">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="b32be-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b32be-561">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b32be-562">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="b32be-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b32be-563">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b32be-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b32be-564">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="b32be-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b32be-565">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="b32be-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b32be-566">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b32be-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b32be-567">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-568">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="b32be-569">**globaljson**</span></span>

<span data-ttu-id="b32be-570">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="b32be-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b32be-571">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b32be-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="b32be-572">**主控台, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="b32be-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="b32be-573">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="b32be-574">**classlib**</span></span>

<span data-ttu-id="b32be-575">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b32be-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b32be-576">值：`netcoreapp2.1` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="b32be-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b32be-577">預設值為 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="b32be-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="b32be-578">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-579">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="b32be-579">**mstest, xunit**</span></span>

<span data-ttu-id="b32be-580">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="b32be-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b32be-581">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="b32be-582">**globaljson**</span></span>

<span data-ttu-id="b32be-583">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="b32be-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="b32be-584">**web**</span><span class="sxs-lookup"><span data-stu-id="b32be-584">**web**</span></span>

<span data-ttu-id="b32be-585">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="b32be-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b32be-586">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-587">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b32be-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b32be-588">此選項僅適用於未使用 `IndividualAuth` 或 `OrganizationalAuth` 時。</span><span class="sxs-lookup"><span data-stu-id="b32be-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="b32be-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="b32be-589">**webapi**</span></span>

<span data-ttu-id="b32be-590">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b32be-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b32be-591">可能值為：</span><span class="sxs-lookup"><span data-stu-id="b32be-591">The possible values are:</span></span>

- <span data-ttu-id="b32be-592">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="b32be-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b32be-593">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b32be-594">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b32be-595">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b32be-596">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b32be-597">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-598">預設值為 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b32be-599">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b32be-600">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-601">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b32be-602">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-603">預設值為 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b32be-604">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b32be-605">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-606">預設值為 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="b32be-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b32be-607">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="b32be-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b32be-608">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-609">預設值為 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="b32be-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b32be-610">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b32be-611">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-612">預設值為 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="b32be-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b32be-613">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="b32be-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b32be-614">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b32be-615">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="b32be-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b32be-616">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b32be-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b32be-617">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-618">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-619">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b32be-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b32be-620">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="b32be-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b32be-621">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="b32be-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b32be-622">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="b32be-622">**mvc, razor**</span></span>

<span data-ttu-id="b32be-623">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b32be-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b32be-624">可能值為：</span><span class="sxs-lookup"><span data-stu-id="b32be-624">The possible values are:</span></span>

- <span data-ttu-id="b32be-625">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="b32be-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b32be-626">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="b32be-627">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b32be-628">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b32be-629">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="b32be-630">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b32be-631">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b32be-632">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-633">預設值為 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b32be-634">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b32be-635">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-636">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="b32be-637">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-638">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="b32be-639">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-640">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b32be-641">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b32be-642">預設值為 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b32be-643">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b32be-644">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b32be-645">預設值為 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="b32be-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b32be-646">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="b32be-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b32be-647">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-648">預設值為 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="b32be-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b32be-649">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b32be-650">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-651">預設值為 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="b32be-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b32be-652">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="b32be-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b32be-653">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-654">預設值為 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="b32be-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="b32be-655">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="b32be-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b32be-656">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b32be-657">`--exclude-launch-settings` - 從產生的範本中排除 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="b32be-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b32be-658">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="b32be-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="b32be-659">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b32be-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b32be-660">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-661">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-662">`--no-https` - 專案不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b32be-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b32be-663">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="b32be-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b32be-664">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="b32be-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b32be-665">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="b32be-665">**page**</span></span>

<span data-ttu-id="b32be-666">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b32be-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b32be-667">預設值為 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="b32be-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b32be-668">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="b32be-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="b32be-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="b32be-669">**viewimports**</span></span>

<span data-ttu-id="b32be-670">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b32be-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b32be-671">預設值為 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="b32be-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b32be-672">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b32be-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="b32be-673">**主控台, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="b32be-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="b32be-674">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="b32be-675">**classlib**</span></span>

<span data-ttu-id="b32be-676">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b32be-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b32be-677">值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="b32be-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b32be-678">預設值為 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="b32be-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="b32be-679">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-680">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="b32be-680">**mstest, xunit**</span></span>

<span data-ttu-id="b32be-681">`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。</span><span class="sxs-lookup"><span data-stu-id="b32be-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b32be-682">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="b32be-683">**globaljson**</span></span>

<span data-ttu-id="b32be-684">`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="b32be-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="b32be-685">**web**</span><span class="sxs-lookup"><span data-stu-id="b32be-685">**web**</span></span>

<span data-ttu-id="b32be-686">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="b32be-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b32be-687">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="b32be-688">**webapi**</span></span>

<span data-ttu-id="b32be-689">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b32be-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b32be-690">可能值為：</span><span class="sxs-lookup"><span data-stu-id="b32be-690">The possible values are:</span></span>

- <span data-ttu-id="b32be-691">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="b32be-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b32be-692">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b32be-693">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b32be-694">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b32be-695">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b32be-696">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-697">預設值為 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b32be-698">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b32be-699">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-700">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b32be-701">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-702">預設值為 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b32be-703">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b32be-704">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-705">預設值為 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="b32be-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b32be-706">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="b32be-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b32be-707">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-708">預設值為 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="b32be-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b32be-709">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b32be-710">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-711">預設值為 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="b32be-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b32be-712">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="b32be-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b32be-713">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b32be-714">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="b32be-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b32be-715">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b32be-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b32be-716">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-717">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-718">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="b32be-718">**mvc, razor**</span></span>

<span data-ttu-id="b32be-719">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b32be-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b32be-720">可能值為：</span><span class="sxs-lookup"><span data-stu-id="b32be-720">The possible values are:</span></span>

- <span data-ttu-id="b32be-721">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="b32be-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b32be-722">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="b32be-723">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b32be-724">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b32be-725">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="b32be-726">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b32be-727">`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b32be-728">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-729">預設值為 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b32be-730">`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b32be-731">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-732">`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="b32be-733">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-734">`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="b32be-735">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-736">`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b32be-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b32be-737">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b32be-738">預設值為 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="b32be-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b32be-739">`--client-id <ID>` - 此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b32be-740">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b32be-741">預設值為 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="b32be-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b32be-742">`--domain <DOMAIN>` - 目錄租用戶的網域。</span><span class="sxs-lookup"><span data-stu-id="b32be-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b32be-743">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-744">預設值為 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="b32be-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b32be-745">`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="b32be-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b32be-746">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b32be-747">預設值為 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="b32be-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b32be-748">`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="b32be-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b32be-749">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b32be-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b32be-750">預設值為 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="b32be-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="b32be-751">`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="b32be-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b32be-752">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b32be-753">`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。</span><span class="sxs-lookup"><span data-stu-id="b32be-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b32be-754">`--use-browserlink` - 專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="b32be-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="b32be-755">`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b32be-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b32be-756">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b32be-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b32be-757">`--no-restore` - 專案建立期間不執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b32be-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b32be-758">**PAGE**</span><span class="sxs-lookup"><span data-stu-id="b32be-758">**page**</span></span>

<span data-ttu-id="b32be-759">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b32be-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="b32be-760">預設值為 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="b32be-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b32be-761">`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。</span><span class="sxs-lookup"><span data-stu-id="b32be-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="b32be-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="b32be-762">**viewimports**</span></span>

<span data-ttu-id="b32be-763">`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b32be-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="b32be-764">預設值為 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="b32be-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b32be-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b32be-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b32be-766">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="b32be-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="b32be-767">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b32be-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b32be-768">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="b32be-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="b32be-769">預設值為 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="b32be-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="b32be-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="b32be-770">**classlib**</span></span>

<span data-ttu-id="b32be-771">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b32be-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b32be-772">值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。</span><span class="sxs-lookup"><span data-stu-id="b32be-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="b32be-773">預設值為 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="b32be-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="b32be-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="b32be-774">**mvc**</span></span>

<span data-ttu-id="b32be-775">`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b32be-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b32be-776">值：`netcoreapp1.0` 或 `netcoreapp1.1`。</span><span class="sxs-lookup"><span data-stu-id="b32be-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="b32be-777">預設值為 `netcoreapp1.0`。</span><span class="sxs-lookup"><span data-stu-id="b32be-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="b32be-778">`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b32be-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b32be-779">值：`None` 或 `Individual`。</span><span class="sxs-lookup"><span data-stu-id="b32be-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="b32be-780">預設值為 `None`。</span><span class="sxs-lookup"><span data-stu-id="b32be-780">The default value is `None`.</span></span>

<span data-ttu-id="b32be-781">`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b32be-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="b32be-782">值：`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="b32be-782">Values: `true` or `false`.</span></span> <span data-ttu-id="b32be-783">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b32be-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="b32be-784">範例</span><span class="sxs-lookup"><span data-stu-id="b32be-784">Examples</span></span>

<span data-ttu-id="b32be-785">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="b32be-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="b32be-786">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="b32be-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="b32be-787">在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core SDK 2.0 或更新版本提供)：</span><span class="sxs-lookup"><span data-stu-id="b32be-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="b32be-788">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="b32be-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="b32be-789">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="b32be-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="b32be-790">列出 MVC 可用的所有範本：</span><span class="sxs-lookup"><span data-stu-id="b32be-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="b32be-791">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="b32be-792">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="b32be-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="b32be-793">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="b32be-794">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="b32be-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="b32be-795">安裝適用於 ASP.NET Core 的單頁應用程式範本 2.0 版 (僅適用於 .NET Core SDK 1.1 及更新版本的命令選項)：</span><span class="sxs-lookup"><span data-stu-id="b32be-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="b32be-796">在目前目錄中建立 *global.json*，並將 SDK 版本設為 2.0.0 (只能用於.NET Core SDK 2.0 或更新版本)：</span><span class="sxs-lookup"><span data-stu-id="b32be-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="b32be-797">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b32be-797">See also</span></span>

- [<span data-ttu-id="b32be-798">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="b32be-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="b32be-799">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="b32be-799">Create a custom template for dotnet new</span></span>](../tutorials/create-custom-template.md)
- <span data-ttu-id="b32be-800">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="b32be-800">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="b32be-801">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="b32be-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
