---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399123"
---
# <a name="dotnet-new"></a><span data-ttu-id="f1ebe-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f1ebe-103">dotnet new</span></span>

<span data-ttu-id="f1ebe-104">**本文適用于：✔️** .NET Core 2.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f1ebe-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f1ebe-105">Name</span></span>

<span data-ttu-id="f1ebe-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f1ebe-107">概要</span><span class="sxs-lookup"><span data-stu-id="f1ebe-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f1ebe-108">描述</span><span class="sxs-lookup"><span data-stu-id="f1ebe-108">Description</span></span>

<span data-ttu-id="f1ebe-109">該`dotnet new`命令基於範本創建 .NET Core 專案或其他專案。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="f1ebe-110">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="f1ebe-111">引數</span><span class="sxs-lookup"><span data-stu-id="f1ebe-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="f1ebe-112">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="f1ebe-113">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="f1ebe-114">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="f1ebe-115">您可以運行`dotnet new --list`以查看所有已安裝範本的清單。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="f1ebe-116">如果`TEMPLATE`該值與返回表中的 **"範本**"或 **"短名稱"** 列中的文本不匹配，則對這兩列執行子字串匹配。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="f1ebe-117">從 .NET Core 3.0 SDK 開始，當您在以下條件下調用`dotnet new`命令時，CLI 會搜索NuGet.org中的範本：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="f1ebe-118">如果 CLI 在調用`dotnet new`時找不到範本匹配，甚至不是部分範本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="f1ebe-119">如果有較新版本的範本可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="f1ebe-120">在這種情況下，將創建專案或專案，但 CLI 會警告您有關範本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="f1ebe-121">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-121">The command contains a default list of templates.</span></span> <span data-ttu-id="f1ebe-122">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="f1ebe-123">下表顯示了預先安裝的 .NET Core SDK 的範本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="f1ebe-124">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="f1ebe-125">按一下短名稱連結以查看特定的範本選項。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="f1ebe-126">範本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-126">Templates</span></span>                                    | <span data-ttu-id="f1ebe-127">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="f1ebe-127">Short name</span></span>                      | <span data-ttu-id="f1ebe-128">Language</span><span class="sxs-lookup"><span data-stu-id="f1ebe-128">Language</span></span>     | <span data-ttu-id="f1ebe-129">Tags</span><span class="sxs-lookup"><span data-stu-id="f1ebe-129">Tags</span></span>                                  | <span data-ttu-id="f1ebe-130">介紹</span><span class="sxs-lookup"><span data-stu-id="f1ebe-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="f1ebe-131">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="f1ebe-131">Console Application</span></span>                          | [<span data-ttu-id="f1ebe-132">console</span><span class="sxs-lookup"><span data-stu-id="f1ebe-132">console</span></span>](#console)             | <span data-ttu-id="f1ebe-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f1ebe-133">[C#], F#, VB</span></span> | <span data-ttu-id="f1ebe-134">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="f1ebe-134">Common/Console</span></span>                        | <span data-ttu-id="f1ebe-135">1.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-135">1.0</span></span>        |
| <span data-ttu-id="f1ebe-136">類別庫</span><span class="sxs-lookup"><span data-stu-id="f1ebe-136">Class library</span></span>                                | [<span data-ttu-id="f1ebe-137">classlib</span><span class="sxs-lookup"><span data-stu-id="f1ebe-137">classlib</span></span>](#classlib)           | <span data-ttu-id="f1ebe-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f1ebe-138">[C#], F#, VB</span></span> | <span data-ttu-id="f1ebe-139">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="f1ebe-139">Common/Library</span></span>                        | <span data-ttu-id="f1ebe-140">1.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-140">1.0</span></span>        |
| <span data-ttu-id="f1ebe-141">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="f1ebe-141">WPF Application</span></span>                              | [<span data-ttu-id="f1ebe-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="f1ebe-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="f1ebe-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-143">[C#]</span></span>         | <span data-ttu-id="f1ebe-144">公共/WPF</span><span class="sxs-lookup"><span data-stu-id="f1ebe-144">Common/WPF</span></span>                            | <span data-ttu-id="f1ebe-145">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-145">3.0</span></span>        |
| <span data-ttu-id="f1ebe-146">WPF 類庫</span><span class="sxs-lookup"><span data-stu-id="f1ebe-146">WPF Class library</span></span>                            | [<span data-ttu-id="f1ebe-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="f1ebe-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="f1ebe-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-148">[C#]</span></span>         | <span data-ttu-id="f1ebe-149">公共/WPF</span><span class="sxs-lookup"><span data-stu-id="f1ebe-149">Common/WPF</span></span>                            | <span data-ttu-id="f1ebe-150">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-150">3.0</span></span>        |
| <span data-ttu-id="f1ebe-151">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="f1ebe-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="f1ebe-152">wpf自訂控制lib</span><span class="sxs-lookup"><span data-stu-id="f1ebe-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="f1ebe-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-153">[C#]</span></span>         | <span data-ttu-id="f1ebe-154">公共/WPF</span><span class="sxs-lookup"><span data-stu-id="f1ebe-154">Common/WPF</span></span>                            | <span data-ttu-id="f1ebe-155">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-155">3.0</span></span>        |
| <span data-ttu-id="f1ebe-156">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="f1ebe-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="f1ebe-157">wpfuser控制lib</span><span class="sxs-lookup"><span data-stu-id="f1ebe-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="f1ebe-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-158">[C#]</span></span>         | <span data-ttu-id="f1ebe-159">公共/WPF</span><span class="sxs-lookup"><span data-stu-id="f1ebe-159">Common/WPF</span></span>                            | <span data-ttu-id="f1ebe-160">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-160">3.0</span></span>        |
| <span data-ttu-id="f1ebe-161">視窗表單（贏表單）應用程式</span><span class="sxs-lookup"><span data-stu-id="f1ebe-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="f1ebe-162">溫表單</span><span class="sxs-lookup"><span data-stu-id="f1ebe-162">winforms</span></span>](#winforms)           | <span data-ttu-id="f1ebe-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-163">[C#]</span></span>         | <span data-ttu-id="f1ebe-164">通用/雙贏</span><span class="sxs-lookup"><span data-stu-id="f1ebe-164">Common/WinForms</span></span>                       | <span data-ttu-id="f1ebe-165">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-165">3.0</span></span>        |
| <span data-ttu-id="f1ebe-166">視窗表單（獲勝表單）類庫</span><span class="sxs-lookup"><span data-stu-id="f1ebe-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="f1ebe-167">溫多利布</span><span class="sxs-lookup"><span data-stu-id="f1ebe-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="f1ebe-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-168">[C#]</span></span>         | <span data-ttu-id="f1ebe-169">通用/雙贏</span><span class="sxs-lookup"><span data-stu-id="f1ebe-169">Common/WinForms</span></span>                       | <span data-ttu-id="f1ebe-170">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-170">3.0</span></span>        |
| <span data-ttu-id="f1ebe-171">工人服務</span><span class="sxs-lookup"><span data-stu-id="f1ebe-171">Worker Service</span></span>                               | [<span data-ttu-id="f1ebe-172">工人</span><span class="sxs-lookup"><span data-stu-id="f1ebe-172">worker</span></span>](#web-others)           | <span data-ttu-id="f1ebe-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-173">[C#]</span></span>         | <span data-ttu-id="f1ebe-174">公用/工人/網路</span><span class="sxs-lookup"><span data-stu-id="f1ebe-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="f1ebe-175">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-175">3.0</span></span>        |
| <span data-ttu-id="f1ebe-176">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="f1ebe-176">Unit Test Project</span></span>                            | [<span data-ttu-id="f1ebe-177">mstest</span><span class="sxs-lookup"><span data-stu-id="f1ebe-177">mstest</span></span>](#test)                 | <span data-ttu-id="f1ebe-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f1ebe-178">[C#], F#, VB</span></span> | <span data-ttu-id="f1ebe-179">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="f1ebe-179">Test/MSTest</span></span>                           | <span data-ttu-id="f1ebe-180">1.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-180">1.0</span></span>        |
| <span data-ttu-id="f1ebe-181">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="f1ebe-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="f1ebe-182">Nunit</span><span class="sxs-lookup"><span data-stu-id="f1ebe-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="f1ebe-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f1ebe-183">[C#], F#, VB</span></span> | <span data-ttu-id="f1ebe-184">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="f1ebe-184">Test/NUnit</span></span>                            | <span data-ttu-id="f1ebe-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="f1ebe-185">2.1.400</span></span>    |
| <span data-ttu-id="f1ebe-186">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="f1ebe-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="f1ebe-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f1ebe-187">[C#], F#, VB</span></span> | <span data-ttu-id="f1ebe-188">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="f1ebe-188">Test/NUnit</span></span>                            | <span data-ttu-id="f1ebe-189">2.2</span><span class="sxs-lookup"><span data-stu-id="f1ebe-189">2.2</span></span>        |
| <span data-ttu-id="f1ebe-190">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="f1ebe-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="f1ebe-191">森特</span><span class="sxs-lookup"><span data-stu-id="f1ebe-191">xunit</span></span>](#test)                  | <span data-ttu-id="f1ebe-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f1ebe-192">[C#], F#, VB</span></span> | <span data-ttu-id="f1ebe-193">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="f1ebe-193">Test/xUnit</span></span>                            | <span data-ttu-id="f1ebe-194">1.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-194">1.0</span></span>        |
| <span data-ttu-id="f1ebe-195">剃刀元件</span><span class="sxs-lookup"><span data-stu-id="f1ebe-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="f1ebe-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-196">[C#]</span></span>         | <span data-ttu-id="f1ebe-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f1ebe-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="f1ebe-198">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-198">3.0</span></span>        |
| <span data-ttu-id="f1ebe-199">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="f1ebe-199">Razor Page</span></span>                                   | [<span data-ttu-id="f1ebe-200">網頁</span><span class="sxs-lookup"><span data-stu-id="f1ebe-200">page</span></span>](#page)                   | <span data-ttu-id="f1ebe-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-201">[C#]</span></span>         | <span data-ttu-id="f1ebe-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f1ebe-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="f1ebe-203">2.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-203">2.0</span></span>        |
| <span data-ttu-id="f1ebe-204">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="f1ebe-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="f1ebe-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="f1ebe-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="f1ebe-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-206">[C#]</span></span>         | <span data-ttu-id="f1ebe-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f1ebe-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="f1ebe-208">2.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-208">2.0</span></span>        |
| <span data-ttu-id="f1ebe-209">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="f1ebe-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="f1ebe-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-210">[C#]</span></span>         | <span data-ttu-id="f1ebe-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f1ebe-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="f1ebe-212">2.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-212">2.0</span></span>        |
| <span data-ttu-id="f1ebe-213">布拉佐伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="f1ebe-213">Blazor Server App</span></span>                            | [<span data-ttu-id="f1ebe-214">布拉佐伺服器</span><span class="sxs-lookup"><span data-stu-id="f1ebe-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="f1ebe-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-215">[C#]</span></span>         | <span data-ttu-id="f1ebe-216">網路/布拉佐爾</span><span class="sxs-lookup"><span data-stu-id="f1ebe-216">Web/Blazor</span></span>                            | <span data-ttu-id="f1ebe-217">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-217">3.0</span></span>        |
| <span data-ttu-id="f1ebe-218">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f1ebe-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="f1ebe-219">Web</span><span class="sxs-lookup"><span data-stu-id="f1ebe-219">web</span></span>](#web)                     | <span data-ttu-id="f1ebe-220">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="f1ebe-220">[C#], F#</span></span>     | <span data-ttu-id="f1ebe-221">Web/空白</span><span class="sxs-lookup"><span data-stu-id="f1ebe-221">Web/Empty</span></span>                             | <span data-ttu-id="f1ebe-222">1.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-222">1.0</span></span>        |
| <span data-ttu-id="f1ebe-223">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="f1ebe-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="f1ebe-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="f1ebe-224">mvc</span></span>](#web-options)             | <span data-ttu-id="f1ebe-225">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="f1ebe-225">[C#], F#</span></span>     | <span data-ttu-id="f1ebe-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="f1ebe-226">Web/MVC</span></span>                               | <span data-ttu-id="f1ebe-227">1.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-227">1.0</span></span>        |
| <span data-ttu-id="f1ebe-228">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="f1ebe-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="f1ebe-229">網路應用程式， 剃鬚刀</span><span class="sxs-lookup"><span data-stu-id="f1ebe-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="f1ebe-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-230">[C#]</span></span>         | <span data-ttu-id="f1ebe-231">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="f1ebe-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="f1ebe-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="f1ebe-233">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="f1ebe-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="f1ebe-234">角</span><span class="sxs-lookup"><span data-stu-id="f1ebe-234">angular</span></span>](#spa)                 | <span data-ttu-id="f1ebe-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-235">[C#]</span></span>         | <span data-ttu-id="f1ebe-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f1ebe-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f1ebe-237">2.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-237">2.0</span></span>        |
| <span data-ttu-id="f1ebe-238">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="f1ebe-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="f1ebe-239">反應</span><span class="sxs-lookup"><span data-stu-id="f1ebe-239">react</span></span>](#spa)                   | <span data-ttu-id="f1ebe-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-240">[C#]</span></span>         | <span data-ttu-id="f1ebe-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f1ebe-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f1ebe-242">2.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-242">2.0</span></span>        |
| <span data-ttu-id="f1ebe-243">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="f1ebe-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="f1ebe-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="f1ebe-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="f1ebe-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-245">[C#]</span></span>         | <span data-ttu-id="f1ebe-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f1ebe-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f1ebe-247">2.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-247">2.0</span></span>        |
| <span data-ttu-id="f1ebe-248">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="f1ebe-248">Razor Class Library</span></span>                          | [<span data-ttu-id="f1ebe-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="f1ebe-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="f1ebe-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-250">[C#]</span></span>         | <span data-ttu-id="f1ebe-251">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="f1ebe-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="f1ebe-252">2.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-252">2.1</span></span>        |
| <span data-ttu-id="f1ebe-253">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="f1ebe-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="f1ebe-254">韋薩皮</span><span class="sxs-lookup"><span data-stu-id="f1ebe-254">webapi</span></span>](#webapi)               | <span data-ttu-id="f1ebe-255">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="f1ebe-255">[C#], F#</span></span>     | <span data-ttu-id="f1ebe-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="f1ebe-256">Web/WebAPI</span></span>                            | <span data-ttu-id="f1ebe-257">1.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-257">1.0</span></span>        |
| <span data-ttu-id="f1ebe-258">ASP.NET核心 gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="f1ebe-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="f1ebe-259">grpc</span><span class="sxs-lookup"><span data-stu-id="f1ebe-259">grpc</span></span>](#web-others)             | <span data-ttu-id="f1ebe-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="f1ebe-260">[C#]</span></span>         | <span data-ttu-id="f1ebe-261">網路/gRPC</span><span class="sxs-lookup"><span data-stu-id="f1ebe-261">Web/gRPC</span></span>                              | <span data-ttu-id="f1ebe-262">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-262">3.0</span></span>        |
| <span data-ttu-id="f1ebe-263">協定緩衝區檔</span><span class="sxs-lookup"><span data-stu-id="f1ebe-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="f1ebe-264">原</span><span class="sxs-lookup"><span data-stu-id="f1ebe-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="f1ebe-265">網路/gRPC</span><span class="sxs-lookup"><span data-stu-id="f1ebe-265">Web/gRPC</span></span>                              | <span data-ttu-id="f1ebe-266">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-266">3.0</span></span>        |
| <span data-ttu-id="f1ebe-267">點網 gitignore 檔</span><span class="sxs-lookup"><span data-stu-id="f1ebe-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="f1ebe-268">Config</span><span class="sxs-lookup"><span data-stu-id="f1ebe-268">Config</span></span>                                | <span data-ttu-id="f1ebe-269">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-269">3.0</span></span>        |
| <span data-ttu-id="f1ebe-270">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="f1ebe-270">global.json file</span></span>                             | [<span data-ttu-id="f1ebe-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="f1ebe-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="f1ebe-272">Config</span><span class="sxs-lookup"><span data-stu-id="f1ebe-272">Config</span></span>                                | <span data-ttu-id="f1ebe-273">2.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-273">2.0</span></span>        |
| <span data-ttu-id="f1ebe-274">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="f1ebe-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="f1ebe-275">Config</span><span class="sxs-lookup"><span data-stu-id="f1ebe-275">Config</span></span>                                | <span data-ttu-id="f1ebe-276">1.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-276">1.0</span></span>        |
| <span data-ttu-id="f1ebe-277">點網本地工具清單檔</span><span class="sxs-lookup"><span data-stu-id="f1ebe-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="f1ebe-278">Config</span><span class="sxs-lookup"><span data-stu-id="f1ebe-278">Config</span></span>                                | <span data-ttu-id="f1ebe-279">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-279">3.0</span></span>        |
| <span data-ttu-id="f1ebe-280">Web 組態</span><span class="sxs-lookup"><span data-stu-id="f1ebe-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="f1ebe-281">Config</span><span class="sxs-lookup"><span data-stu-id="f1ebe-281">Config</span></span>                                | <span data-ttu-id="f1ebe-282">1.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-282">1.0</span></span>        |
| <span data-ttu-id="f1ebe-283">方案檔</span><span class="sxs-lookup"><span data-stu-id="f1ebe-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="f1ebe-284">解決方法</span><span class="sxs-lookup"><span data-stu-id="f1ebe-284">Solution</span></span>                              | <span data-ttu-id="f1ebe-285">1.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="f1ebe-286">選項。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="f1ebe-287">顯示運行給定命令時將會發生什麼情況的摘要。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="f1ebe-288">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="f1ebe-289">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="f1ebe-290">當選擇的範本將覆蓋輸出目錄中的現有檔時，這是必需的。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f1ebe-291">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-291">Prints out help for the command.</span></span> <span data-ttu-id="f1ebe-292">可以為`dotnet new`命令本身或任何範本調用它。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="f1ebe-293">例如： `dotnet new mvc --help` 。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="f1ebe-294">從`PATH`或`NUGET_ID`安裝 提供的範本包。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f1ebe-295">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="f1ebe-296">預設情況下，`dotnet new`將傳遞\*版本，該版本表示最新的穩定包版本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="f1ebe-297">請參閱["示例](#examples)"部分中的示例。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="f1ebe-298">如果在運行此命令時已安裝範本的版本，則範本將更新為指定版本，如果沒有指定版本，則該範本將更新到最新的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="f1ebe-299">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="f1ebe-300">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="f1ebe-301">如果未指定名稱，則列出所有範本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="f1ebe-302">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-302">The language of the template to create.</span></span> <span data-ttu-id="f1ebe-303">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f1ebe-304">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f1ebe-305">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="f1ebe-306">在這些情況下，將語言參數值括在引號中。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="f1ebe-307">例如： `dotnet new console -lang "F#"` 。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="f1ebe-308">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-308">The name for the created output.</span></span> <span data-ttu-id="f1ebe-309">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="f1ebe-310">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="f1ebe-311">自 .NET 核心 2.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f1ebe-312">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-312">Location to place the generated output.</span></span> <span data-ttu-id="f1ebe-313">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="f1ebe-314">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-314">Filters templates based on available types.</span></span> <span data-ttu-id="f1ebe-315">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="f1ebe-316">在`PATH`或`NUGET_ID`上卸載範本包。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f1ebe-317">未指定`<PATH|NUGET_ID>`該值時，將顯示所有當前安裝的範本包及其關聯的範本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="f1ebe-318">指定`NUGET_ID`時，不包括版本號。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="f1ebe-319">如果不為此選項指定參數，該命令將列出已安裝的範本及其詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f1ebe-320">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="f1ebe-321">例如 *，C：/使用者/\<使用者>/文檔/範本/加西亞軟體.ConsoleTemplate.CSharp*將工作，但 *./GarciaSoftware.ConsoleTemplate.CSharp*從包含的資料夾中不會。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="f1ebe-322">不要在範本路徑上包含最終終止目錄斜杠。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="f1ebe-323">檢查當前安裝的範本包是否有可用的更新並安裝它們。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="f1ebe-324">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="f1ebe-325">檢查當前安裝的範本包是否有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="f1ebe-326">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="f1ebe-327">範本選項</span><span class="sxs-lookup"><span data-stu-id="f1ebe-327">Template options</span></span>

<span data-ttu-id="f1ebe-328">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-328">Each project template may have additional options available.</span></span> <span data-ttu-id="f1ebe-329">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="f1ebe-330">console</span><span class="sxs-lookup"><span data-stu-id="f1ebe-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-331">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f1ebe-332">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f1ebe-333">下表根據您使用的 SDK 版本號列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f1ebe-334">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-334">SDK version</span></span> | <span data-ttu-id="f1ebe-335">預設值</span><span class="sxs-lookup"><span data-stu-id="f1ebe-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f1ebe-336">3.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f1ebe-337">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f1ebe-338">在`LangVersion`創建的專案檔案中設置屬性。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f1ebe-339">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="f1ebe-340">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-340">Not supported for F#.</span></span> <span data-ttu-id="f1ebe-341">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f1ebe-342">有關預設 C# 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ebe-343">如果指定，則不會在專案創建期間執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="f1ebe-344">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="f1ebe-345">classlib</span><span class="sxs-lookup"><span data-stu-id="f1ebe-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-346">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f1ebe-347">值：`netcoreapp<version>` 建立 .NET Core 類別庫或 `netstandard<version>` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="f1ebe-348">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f1ebe-349">在`LangVersion`創建的專案檔案中設置屬性。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f1ebe-350">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="f1ebe-351">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-351">Not supported for F#.</span></span> <span data-ttu-id="f1ebe-352">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f1ebe-353">有關預設 C# 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ebe-354">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="f1ebe-355">wpf， wpflib， wpf自訂控制lib， wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="f1ebe-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-356">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f1ebe-357">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="f1ebe-358">自 .NET 核心 3.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f1ebe-359">在`LangVersion`創建的專案檔案中設置屬性。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f1ebe-360">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="f1ebe-361">有關預設 C# 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ebe-362">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="f1ebe-363">勝利，溫多利布</span><span class="sxs-lookup"><span data-stu-id="f1ebe-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f1ebe-364">在`LangVersion`創建的專案檔案中設置屬性。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f1ebe-365">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="f1ebe-366">有關預設 C# 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ebe-367">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="f1ebe-368">工人， grpc</span><span class="sxs-lookup"><span data-stu-id="f1ebe-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-369">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f1ebe-370">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="f1ebe-371">自 .NET 核心 3.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f1ebe-372">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="f1ebe-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ebe-373">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="f1ebe-374">斯泰斯特， 迅達</span><span class="sxs-lookup"><span data-stu-id="f1ebe-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-375">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f1ebe-376">選項可用，因為 .NET 核心 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f1ebe-377">下表根據您使用的 SDK 版本號列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f1ebe-378">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-378">SDK version</span></span> | <span data-ttu-id="f1ebe-379">預設值</span><span class="sxs-lookup"><span data-stu-id="f1ebe-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f1ebe-380">3.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f1ebe-381">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="f1ebe-382">使用[dotnet 包](dotnet-pack.md)為專案啟用打包。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ebe-383">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="f1ebe-384">Nunit</span><span class="sxs-lookup"><span data-stu-id="f1ebe-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-385">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="f1ebe-386">下表根據您使用的 SDK 版本號列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f1ebe-387">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-387">SDK version</span></span> | <span data-ttu-id="f1ebe-388">預設值</span><span class="sxs-lookup"><span data-stu-id="f1ebe-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f1ebe-389">3.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f1ebe-390">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f1ebe-391">2.2</span><span class="sxs-lookup"><span data-stu-id="f1ebe-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="f1ebe-392">2.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="f1ebe-393">使用[dotnet 包](dotnet-pack.md)為專案啟用打包。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ebe-394">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="f1ebe-395">頁面</span><span class="sxs-lookup"><span data-stu-id="f1ebe-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="f1ebe-396">生成的代碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-396">Namespace for the generated code.</span></span> <span data-ttu-id="f1ebe-397">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="f1ebe-398">創建沒有頁面模型的頁面。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="f1ebe-399">視圖導入， 原型</span><span class="sxs-lookup"><span data-stu-id="f1ebe-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="f1ebe-400">生成的代碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-400">Namespace for the generated code.</span></span> <span data-ttu-id="f1ebe-401">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="f1ebe-402">布拉佐伺服器</span><span class="sxs-lookup"><span data-stu-id="f1ebe-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f1ebe-403">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-403">The type of authentication to use.</span></span> <span data-ttu-id="f1ebe-404">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-404">The possible values are:</span></span>

  - <span data-ttu-id="f1ebe-405">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f1ebe-406">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="f1ebe-407">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f1ebe-408">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f1ebe-409">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="f1ebe-410">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f1ebe-411">要連接到的 Azure 活動目錄 B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f1ebe-412">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f1ebe-413">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f1ebe-414">此專案的登錄和註冊策略 ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f1ebe-415">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="f1ebe-416">此專案的重置密碼原則 ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="f1ebe-417">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="f1ebe-418">此專案的編輯設定檔策略 ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="f1ebe-419">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f1ebe-420">要連接到的 Azure 活動目錄實例。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f1ebe-421">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f1ebe-422">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f1ebe-423">此專案的用戶端 ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-423">The Client ID for this project.</span></span> <span data-ttu-id="f1ebe-424">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f1ebe-425">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f1ebe-426">目錄租戶的域。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-426">The domain for the directory tenant.</span></span> <span data-ttu-id="f1ebe-427">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f1ebe-428">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f1ebe-429">要連接到的目錄的租戶 ID ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f1ebe-430">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f1ebe-431">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="f1ebe-432">重定向 URI 的應用程式基本路徑中的請求路徑。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f1ebe-433">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f1ebe-434">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f1ebe-435">允許此應用程式讀取存取目錄。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f1ebe-436">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f1ebe-437">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="f1ebe-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f1ebe-438">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-438">Turns off HTTPS.</span></span> <span data-ttu-id="f1ebe-439">僅當 、或`Individual`未`IndividualB2C`用於`SingleOrg``--auth`時`MultiOrg`，此選項才適用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f1ebe-440">指定本機資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f1ebe-441">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ebe-442">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="f1ebe-443">Web</span><span class="sxs-lookup"><span data-stu-id="f1ebe-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f1ebe-444">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="f1ebe-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-445">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f1ebe-446">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f1ebe-447">下表根據您使用的 SDK 版本號列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f1ebe-448">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-448">SDK version</span></span> | <span data-ttu-id="f1ebe-449">預設值</span><span class="sxs-lookup"><span data-stu-id="f1ebe-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f1ebe-450">3.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f1ebe-451">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f1ebe-452">2.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="f1ebe-453">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f1ebe-454">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="f1ebe-455">mvc， 網路應用</span><span class="sxs-lookup"><span data-stu-id="f1ebe-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f1ebe-456">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-456">The type of authentication to use.</span></span> <span data-ttu-id="f1ebe-457">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-457">The possible values are:</span></span>

  - <span data-ttu-id="f1ebe-458">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f1ebe-459">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="f1ebe-460">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f1ebe-461">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f1ebe-462">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="f1ebe-463">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f1ebe-464">要連接到的 Azure 活動目錄 B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f1ebe-465">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f1ebe-466">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f1ebe-467">此專案的登錄和註冊策略 ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f1ebe-468">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="f1ebe-469">此專案的重置密碼原則 ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="f1ebe-470">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="f1ebe-471">此專案的編輯設定檔策略 ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="f1ebe-472">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f1ebe-473">要連接到的 Azure 活動目錄實例。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f1ebe-474">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f1ebe-475">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f1ebe-476">此專案的用戶端 ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-476">The Client ID for this project.</span></span> <span data-ttu-id="f1ebe-477">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f1ebe-478">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f1ebe-479">目錄租戶的域。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-479">The domain for the directory tenant.</span></span> <span data-ttu-id="f1ebe-480">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f1ebe-481">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f1ebe-482">要連接到的目錄的租戶 ID ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f1ebe-483">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f1ebe-484">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="f1ebe-485">重定向 URI 的應用程式基本路徑中的請求路徑。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f1ebe-486">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f1ebe-487">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f1ebe-488">允許此應用程式讀取存取目錄。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f1ebe-489">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f1ebe-490">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="f1ebe-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f1ebe-491">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-491">Turns off HTTPS.</span></span> <span data-ttu-id="f1ebe-492">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f1ebe-493">指定本機資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f1ebe-494">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-495">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f1ebe-496">選項可用，因為 .NET 核心 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f1ebe-497">下表根據您使用的 SDK 版本號列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f1ebe-498">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-498">SDK version</span></span> | <span data-ttu-id="f1ebe-499">預設值</span><span class="sxs-lookup"><span data-stu-id="f1ebe-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f1ebe-500">3.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f1ebe-501">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="f1ebe-502">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="f1ebe-503">在專案中包括瀏覽器連結。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="f1ebe-504">選項在 .NET Core 2.2 和 3.1 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="f1ebe-505">角，反應</span><span class="sxs-lookup"><span data-stu-id="f1ebe-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f1ebe-506">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-506">The type of authentication to use.</span></span> <span data-ttu-id="f1ebe-507">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-507">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="f1ebe-508">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-508">The possible values are:</span></span>

  - <span data-ttu-id="f1ebe-509">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f1ebe-510">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f1ebe-511">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="f1ebe-511">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ebe-512">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f1ebe-513">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-513">Turns off HTTPS.</span></span> <span data-ttu-id="f1ebe-514">僅當身份驗證為`None`時，此選項才適用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f1ebe-515">指定本機資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f1ebe-516">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f1ebe-517">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-518">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f1ebe-519">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f1ebe-520">下表根據您使用的 SDK 版本號列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f1ebe-521">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-521">SDK version</span></span> | <span data-ttu-id="f1ebe-522">預設值</span><span class="sxs-lookup"><span data-stu-id="f1ebe-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f1ebe-523">3.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f1ebe-524">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f1ebe-525">2.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="f1ebe-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="f1ebe-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f1ebe-527">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="f1ebe-527">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-528">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f1ebe-529">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f1ebe-530">下表根據您使用的 SDK 版本號列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f1ebe-531">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-531">SDK version</span></span> | <span data-ttu-id="f1ebe-532">預設值</span><span class="sxs-lookup"><span data-stu-id="f1ebe-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f1ebe-533">3.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f1ebe-534">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f1ebe-535">2.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="f1ebe-536">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f1ebe-537">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="f1ebe-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="f1ebe-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ebe-539">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="f1ebe-540">除了元件添加到此庫之外，還支援添加傳統的 Razor 頁面和視圖。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="f1ebe-541">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="f1ebe-542">webapi</span><span class="sxs-lookup"><span data-stu-id="f1ebe-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f1ebe-543">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-543">The type of authentication to use.</span></span> <span data-ttu-id="f1ebe-544">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-544">The possible values are:</span></span>

  - <span data-ttu-id="f1ebe-545">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f1ebe-546">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f1ebe-547">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f1ebe-548">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f1ebe-549">要連接到的 Azure 活動目錄 B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f1ebe-550">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f1ebe-551">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f1ebe-552">此專案的登錄和註冊策略 ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f1ebe-553">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f1ebe-554">要連接到的 Azure 活動目錄實例。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f1ebe-555">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f1ebe-556">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f1ebe-557">此專案的用戶端 ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-557">The Client ID for this project.</span></span> <span data-ttu-id="f1ebe-558">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f1ebe-559">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f1ebe-560">目錄租戶的域。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-560">The domain for the directory tenant.</span></span> <span data-ttu-id="f1ebe-561">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f1ebe-562">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f1ebe-563">要連接到的目錄的租戶 ID ID。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f1ebe-564">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f1ebe-565">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f1ebe-566">允許此應用程式讀取存取目錄。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f1ebe-567">僅適用于`SingleOrg`身份驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f1ebe-568">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="f1ebe-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f1ebe-569">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-569">Turns off HTTPS.</span></span> <span data-ttu-id="f1ebe-570">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="f1ebe-571">此選項僅適用于或不`SingleOrg`用於身份驗證`IndividualB2C`時。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f1ebe-572">指定本機資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f1ebe-573">僅適用于`IndividualB2C`身份驗證。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ebe-574">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f1ebe-575">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f1ebe-576">下表根據您使用的 SDK 版本號列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f1ebe-577">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-577">SDK version</span></span> | <span data-ttu-id="f1ebe-578">預設值</span><span class="sxs-lookup"><span data-stu-id="f1ebe-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f1ebe-579">3.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f1ebe-580">3.0</span><span class="sxs-lookup"><span data-stu-id="f1ebe-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f1ebe-581">2.1</span><span class="sxs-lookup"><span data-stu-id="f1ebe-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="f1ebe-582">在專案創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="f1ebe-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="f1ebe-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="f1ebe-584">指定要在*global.json*檔中使用的 .NET Core SDK 的版本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="f1ebe-585">範例</span><span class="sxs-lookup"><span data-stu-id="f1ebe-585">Examples</span></span>

- <span data-ttu-id="f1ebe-586">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="f1ebe-587">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="f1ebe-588">在指定的目錄中創建 .NET 標準類庫專案：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="f1ebe-589">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="f1ebe-590">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="f1ebe-591">列出可用於單頁應用程式 （SPA） 範本的所有範本：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="f1ebe-592">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="f1ebe-593">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="f1ebe-594">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="f1ebe-595">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="f1ebe-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="f1ebe-596">安裝 ASP.NET 核心的 SPA 範本版本 2.0：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="f1ebe-597">列出已安裝的範本及其詳細資訊，包括如何卸載它們：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="f1ebe-598">在目前的目錄中創建*一個全域.json*將 SDK 版本設置為 3.1.101：</span><span class="sxs-lookup"><span data-stu-id="f1ebe-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="f1ebe-599">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1ebe-599">See also</span></span>

- [<span data-ttu-id="f1ebe-600">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="f1ebe-601">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-601">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- <span data-ttu-id="f1ebe-602">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="f1ebe-602">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="f1ebe-603">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="f1ebe-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
