---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
ms.date: 02/13/2020
ms.openlocfilehash: f11512acf5a1fdc4bde49b3d1212ccf6335dff8b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451326"
---
# <a name="dotnet-new"></a><span data-ttu-id="ddf5a-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ddf5a-103">dotnet new</span></span>

<span data-ttu-id="ddf5a-104">**本文適用于：** ✔️ .net CORE 2.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ddf5a-105">名稱</span><span class="sxs-lookup"><span data-stu-id="ddf5a-105">Name</span></span>

<span data-ttu-id="ddf5a-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ddf5a-107">概要</span><span class="sxs-lookup"><span data-stu-id="ddf5a-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] 
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="ddf5a-108">描述</span><span class="sxs-lookup"><span data-stu-id="ddf5a-108">Description</span></span>

<span data-ttu-id="ddf5a-109">`dotnet new` 命令會根據範本建立 .NET Core 專案或其他成品。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="ddf5a-110">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="ddf5a-111">引數</span><span class="sxs-lookup"><span data-stu-id="ddf5a-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="ddf5a-112">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ddf5a-113">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ddf5a-114">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="ddf5a-115">您可以執行 `dotnet new --list`，以查看所有已安裝的範本清單。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="ddf5a-116">如果 `TEMPLATE` 值**與所傳回**資料表的 [樣板] 或 [**簡短名稱**] 資料行中的文字完全相符，則會在這兩個數據行上執行子字串相符。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="ddf5a-117">從 .NET Core 3.0 SDK 開始，當您在下列情況下叫用 `dotnet new` 命令時，CLI 會在 NuGet.org 中搜尋範本：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="ddf5a-118">如果 CLI 在叫用 `dotnet new`時找不到相符的範本，甚至不是部分。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="ddf5a-119">如果有較新版本的範本可用，則為。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="ddf5a-120">在此情況下，會建立專案或成品，但 CLI 會警告您有關範本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="ddf5a-121">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-121">The command contains a default list of templates.</span></span> <span data-ttu-id="ddf5a-122">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ddf5a-123">下表顯示隨 .NET Core SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="ddf5a-124">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="ddf5a-125">按一下 [簡短名稱] 連結，以查看特定的範本選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="ddf5a-126">範本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-126">Templates</span></span>                                    | <span data-ttu-id="ddf5a-127">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="ddf5a-127">Short name</span></span>                      | <span data-ttu-id="ddf5a-128">Language</span><span class="sxs-lookup"><span data-stu-id="ddf5a-128">Language</span></span>     | <span data-ttu-id="ddf5a-129">Tags</span><span class="sxs-lookup"><span data-stu-id="ddf5a-129">Tags</span></span>                                  | <span data-ttu-id="ddf5a-130">引導</span><span class="sxs-lookup"><span data-stu-id="ddf5a-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="ddf5a-131">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ddf5a-131">Console Application</span></span>                          | [<span data-ttu-id="ddf5a-132">console</span><span class="sxs-lookup"><span data-stu-id="ddf5a-132">console</span></span>](#console)             | <span data-ttu-id="ddf5a-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ddf5a-133">[C#], F#, VB</span></span> | <span data-ttu-id="ddf5a-134">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="ddf5a-134">Common/Console</span></span>                        | <span data-ttu-id="ddf5a-135">1.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-135">1.0</span></span>        |
| <span data-ttu-id="ddf5a-136">類別庫</span><span class="sxs-lookup"><span data-stu-id="ddf5a-136">Class library</span></span>                                | [<span data-ttu-id="ddf5a-137">classlib</span><span class="sxs-lookup"><span data-stu-id="ddf5a-137">classlib</span></span>](#classlib)           | <span data-ttu-id="ddf5a-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ddf5a-138">[C#], F#, VB</span></span> | <span data-ttu-id="ddf5a-139">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="ddf5a-139">Common/Library</span></span>                        | <span data-ttu-id="ddf5a-140">1.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-140">1.0</span></span>        |
| <span data-ttu-id="ddf5a-141">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="ddf5a-141">WPF Application</span></span>                              | [<span data-ttu-id="ddf5a-142">wpf</span><span class="sxs-lookup"><span data-stu-id="ddf5a-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="ddf5a-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-143">[C#]</span></span>         | <span data-ttu-id="ddf5a-144">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ddf5a-144">Common/WPF</span></span>                            | <span data-ttu-id="ddf5a-145">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-145">3.0</span></span>        |
| <span data-ttu-id="ddf5a-146">WPF 類別庫</span><span class="sxs-lookup"><span data-stu-id="ddf5a-146">WPF Class library</span></span>                            | [<span data-ttu-id="ddf5a-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="ddf5a-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="ddf5a-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-148">[C#]</span></span>         | <span data-ttu-id="ddf5a-149">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ddf5a-149">Common/WPF</span></span>                            | <span data-ttu-id="ddf5a-150">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-150">3.0</span></span>        |
| <span data-ttu-id="ddf5a-151">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="ddf5a-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="ddf5a-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="ddf5a-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="ddf5a-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-153">[C#]</span></span>         | <span data-ttu-id="ddf5a-154">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ddf5a-154">Common/WPF</span></span>                            | <span data-ttu-id="ddf5a-155">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-155">3.0</span></span>        |
| <span data-ttu-id="ddf5a-156">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="ddf5a-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="ddf5a-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ddf5a-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="ddf5a-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-158">[C#]</span></span>         | <span data-ttu-id="ddf5a-159">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ddf5a-159">Common/WPF</span></span>                            | <span data-ttu-id="ddf5a-160">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-160">3.0</span></span>        |
| <span data-ttu-id="ddf5a-161">Windows Forms （WinForms）應用程式</span><span class="sxs-lookup"><span data-stu-id="ddf5a-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="ddf5a-162">winforms</span><span class="sxs-lookup"><span data-stu-id="ddf5a-162">winforms</span></span>](#winforms)           | <span data-ttu-id="ddf5a-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-163">[C#]</span></span>         | <span data-ttu-id="ddf5a-164">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="ddf5a-164">Common/WinForms</span></span>                       | <span data-ttu-id="ddf5a-165">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-165">3.0</span></span>        |
| <span data-ttu-id="ddf5a-166">Windows Forms （WinForms）類別庫</span><span class="sxs-lookup"><span data-stu-id="ddf5a-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="ddf5a-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="ddf5a-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="ddf5a-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-168">[C#]</span></span>         | <span data-ttu-id="ddf5a-169">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="ddf5a-169">Common/WinForms</span></span>                       | <span data-ttu-id="ddf5a-170">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-170">3.0</span></span>        |
| <span data-ttu-id="ddf5a-171">背景工作服務</span><span class="sxs-lookup"><span data-stu-id="ddf5a-171">Worker Service</span></span>                               | [<span data-ttu-id="ddf5a-172">工作</span><span class="sxs-lookup"><span data-stu-id="ddf5a-172">worker</span></span>](#web-others)           | <span data-ttu-id="ddf5a-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-173">[C#]</span></span>         | <span data-ttu-id="ddf5a-174">一般/背景工作/Web</span><span class="sxs-lookup"><span data-stu-id="ddf5a-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="ddf5a-175">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-175">3.0</span></span>        |
| <span data-ttu-id="ddf5a-176">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="ddf5a-176">Unit Test Project</span></span>                            | [<span data-ttu-id="ddf5a-177">mstest.exe</span><span class="sxs-lookup"><span data-stu-id="ddf5a-177">mstest</span></span>](#test)                 | <span data-ttu-id="ddf5a-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ddf5a-178">[C#], F#, VB</span></span> | <span data-ttu-id="ddf5a-179">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="ddf5a-179">Test/MSTest</span></span>                           | <span data-ttu-id="ddf5a-180">1.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-180">1.0</span></span>        |
| <span data-ttu-id="ddf5a-181">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="ddf5a-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="ddf5a-182">nunit</span><span class="sxs-lookup"><span data-stu-id="ddf5a-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="ddf5a-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ddf5a-183">[C#], F#, VB</span></span> | <span data-ttu-id="ddf5a-184">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="ddf5a-184">Test/NUnit</span></span>                            | <span data-ttu-id="ddf5a-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="ddf5a-185">2.1.400</span></span>    |
| <span data-ttu-id="ddf5a-186">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="ddf5a-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="ddf5a-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ddf5a-187">[C#], F#, VB</span></span> | <span data-ttu-id="ddf5a-188">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="ddf5a-188">Test/NUnit</span></span>                            | <span data-ttu-id="ddf5a-189">2.2</span><span class="sxs-lookup"><span data-stu-id="ddf5a-189">2.2</span></span>        |
| <span data-ttu-id="ddf5a-190">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="ddf5a-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="ddf5a-191">xunit</span><span class="sxs-lookup"><span data-stu-id="ddf5a-191">xunit</span></span>](#test)                  | <span data-ttu-id="ddf5a-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ddf5a-192">[C#], F#, VB</span></span> | <span data-ttu-id="ddf5a-193">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="ddf5a-193">Test/xUnit</span></span>                            | <span data-ttu-id="ddf5a-194">1.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-194">1.0</span></span>        |
| <span data-ttu-id="ddf5a-195">Razor 元件</span><span class="sxs-lookup"><span data-stu-id="ddf5a-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="ddf5a-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-196">[C#]</span></span>         | <span data-ttu-id="ddf5a-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ddf5a-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="ddf5a-198">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-198">3.0</span></span>        |
| <span data-ttu-id="ddf5a-199">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="ddf5a-199">Razor Page</span></span>                                   | [<span data-ttu-id="ddf5a-200">page</span><span class="sxs-lookup"><span data-stu-id="ddf5a-200">page</span></span>](#page)                   | <span data-ttu-id="ddf5a-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-201">[C#]</span></span>         | <span data-ttu-id="ddf5a-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ddf5a-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="ddf5a-203">2.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-203">2.0</span></span>        |
| <span data-ttu-id="ddf5a-204">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="ddf5a-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="ddf5a-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="ddf5a-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="ddf5a-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-206">[C#]</span></span>         | <span data-ttu-id="ddf5a-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ddf5a-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="ddf5a-208">2.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-208">2.0</span></span>        |
| <span data-ttu-id="ddf5a-209">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ddf5a-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="ddf5a-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-210">[C#]</span></span>         | <span data-ttu-id="ddf5a-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ddf5a-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="ddf5a-212">2.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-212">2.0</span></span>        |
| <span data-ttu-id="ddf5a-213">Blazor 伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="ddf5a-213">Blazor Server App</span></span>                            | [<span data-ttu-id="ddf5a-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="ddf5a-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="ddf5a-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-215">[C#]</span></span>         | <span data-ttu-id="ddf5a-216">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="ddf5a-216">Web/Blazor</span></span>                            | <span data-ttu-id="ddf5a-217">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-217">3.0</span></span>        |
| <span data-ttu-id="ddf5a-218">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ddf5a-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="ddf5a-219">web</span><span class="sxs-lookup"><span data-stu-id="ddf5a-219">web</span></span>](#web)                     | <span data-ttu-id="ddf5a-220">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ddf5a-220">[C#], F#</span></span>     | <span data-ttu-id="ddf5a-221">Web/空白</span><span class="sxs-lookup"><span data-stu-id="ddf5a-221">Web/Empty</span></span>                             | <span data-ttu-id="ddf5a-222">1.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-222">1.0</span></span>        |
| <span data-ttu-id="ddf5a-223">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="ddf5a-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="ddf5a-224">mvc</span><span class="sxs-lookup"><span data-stu-id="ddf5a-224">mvc</span></span>](#web-options)             | <span data-ttu-id="ddf5a-225">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ddf5a-225">[C#], F#</span></span>     | <span data-ttu-id="ddf5a-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ddf5a-226">Web/MVC</span></span>                               | <span data-ttu-id="ddf5a-227">1.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-227">1.0</span></span>        |
| <span data-ttu-id="ddf5a-228">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="ddf5a-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="ddf5a-229">webapp，razor</span><span class="sxs-lookup"><span data-stu-id="ddf5a-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="ddf5a-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-230">[C#]</span></span>         | <span data-ttu-id="ddf5a-231">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="ddf5a-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="ddf5a-232">2.2、2。0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="ddf5a-233">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="ddf5a-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="ddf5a-234">angular</span><span class="sxs-lookup"><span data-stu-id="ddf5a-234">angular</span></span>](#spa)                 | <span data-ttu-id="ddf5a-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-235">[C#]</span></span>         | <span data-ttu-id="ddf5a-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ddf5a-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ddf5a-237">2.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-237">2.0</span></span>        |
| <span data-ttu-id="ddf5a-238">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="ddf5a-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="ddf5a-239">反應</span><span class="sxs-lookup"><span data-stu-id="ddf5a-239">react</span></span>](#spa)                   | <span data-ttu-id="ddf5a-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-240">[C#]</span></span>         | <span data-ttu-id="ddf5a-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ddf5a-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ddf5a-242">2.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-242">2.0</span></span>        |
| <span data-ttu-id="ddf5a-243">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="ddf5a-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="ddf5a-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="ddf5a-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="ddf5a-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-245">[C#]</span></span>         | <span data-ttu-id="ddf5a-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ddf5a-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ddf5a-247">2.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-247">2.0</span></span>        |
| <span data-ttu-id="ddf5a-248">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="ddf5a-248">Razor Class Library</span></span>                          | [<span data-ttu-id="ddf5a-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="ddf5a-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="ddf5a-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-250">[C#]</span></span>         | <span data-ttu-id="ddf5a-251">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="ddf5a-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="ddf5a-252">2.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-252">2.1</span></span>        |
| <span data-ttu-id="ddf5a-253">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="ddf5a-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="ddf5a-254">webapi</span><span class="sxs-lookup"><span data-stu-id="ddf5a-254">webapi</span></span>](#webapi)               | <span data-ttu-id="ddf5a-255">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="ddf5a-255">[C#], F#</span></span>     | <span data-ttu-id="ddf5a-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ddf5a-256">Web/WebAPI</span></span>                            | <span data-ttu-id="ddf5a-257">1.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-257">1.0</span></span>        |
| <span data-ttu-id="ddf5a-258">ASP.NET Core gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="ddf5a-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="ddf5a-259">grpc</span><span class="sxs-lookup"><span data-stu-id="ddf5a-259">grpc</span></span>](#web-others)             | <span data-ttu-id="ddf5a-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="ddf5a-260">[C#]</span></span>         | <span data-ttu-id="ddf5a-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ddf5a-261">Web/gRPC</span></span>                              | <span data-ttu-id="ddf5a-262">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-262">3.0</span></span>        |
| <span data-ttu-id="ddf5a-263">通訊協定緩衝區檔案</span><span class="sxs-lookup"><span data-stu-id="ddf5a-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="ddf5a-264">proto</span><span class="sxs-lookup"><span data-stu-id="ddf5a-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="ddf5a-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ddf5a-265">Web/gRPC</span></span>                              | <span data-ttu-id="ddf5a-266">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-266">3.0</span></span>        |
| <span data-ttu-id="ddf5a-267">dotnet .gitignore 檔</span><span class="sxs-lookup"><span data-stu-id="ddf5a-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="ddf5a-268">Config</span><span class="sxs-lookup"><span data-stu-id="ddf5a-268">Config</span></span>                                | <span data-ttu-id="ddf5a-269">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-269">3.0</span></span>        |
| <span data-ttu-id="ddf5a-270">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="ddf5a-270">global.json file</span></span>                             | [<span data-ttu-id="ddf5a-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="ddf5a-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="ddf5a-272">Config</span><span class="sxs-lookup"><span data-stu-id="ddf5a-272">Config</span></span>                                | <span data-ttu-id="ddf5a-273">2.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-273">2.0</span></span>        |
| <span data-ttu-id="ddf5a-274">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="ddf5a-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="ddf5a-275">Config</span><span class="sxs-lookup"><span data-stu-id="ddf5a-275">Config</span></span>                                | <span data-ttu-id="ddf5a-276">1.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-276">1.0</span></span>        |
| <span data-ttu-id="ddf5a-277">dotnet 本機工具資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="ddf5a-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="ddf5a-278">Config</span><span class="sxs-lookup"><span data-stu-id="ddf5a-278">Config</span></span>                                | <span data-ttu-id="ddf5a-279">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-279">3.0</span></span>        |
| <span data-ttu-id="ddf5a-280">Web 組態</span><span class="sxs-lookup"><span data-stu-id="ddf5a-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="ddf5a-281">Config</span><span class="sxs-lookup"><span data-stu-id="ddf5a-281">Config</span></span>                                | <span data-ttu-id="ddf5a-282">1.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-282">1.0</span></span>        |
| <span data-ttu-id="ddf5a-283">方案檔</span><span class="sxs-lookup"><span data-stu-id="ddf5a-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="ddf5a-284">解決方法</span><span class="sxs-lookup"><span data-stu-id="ddf5a-284">Solution</span></span>                              | <span data-ttu-id="ddf5a-285">1.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="ddf5a-286">選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="ddf5a-287">顯示執行指定的命令時，會發生什麼情況的摘要。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="ddf5a-288">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="ddf5a-289">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ddf5a-290">當選擇的範本會覆寫輸出目錄中的現有檔案時，這是必要的。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ddf5a-291">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-291">Prints out help for the command.</span></span> <span data-ttu-id="ddf5a-292">可以針對 `dotnet new` 命令本身或任何範本加以叫用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="ddf5a-293">例如： `dotnet new mvc --help` 。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="ddf5a-294">從提供的 `PATH` 或 `NUGET_ID` 安裝範本套件。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ddf5a-295">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ddf5a-296">根據預設，`dotnet new` 會傳遞版本的 \*，這代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="ddf5a-297">請參閱[範例](#examples)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="ddf5a-298">當您執行此命令時，如果已安裝某個版本的範本，此範本將會更新為指定的版本，或如果未指定任何版本，則為最新的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="ddf5a-299">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="ddf5a-300">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="ddf5a-301">如果未指定名稱，則會列出所有範本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="ddf5a-302">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-302">The language of the template to create.</span></span> <span data-ttu-id="ddf5a-303">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ddf5a-304">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ddf5a-305">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ddf5a-306">在這些情況下，請以引號括住語言參數值。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="ddf5a-307">例如： `dotnet new console -lang "F#"` 。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="ddf5a-308">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-308">The name for the created output.</span></span> <span data-ttu-id="ddf5a-309">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="ddf5a-310">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="ddf5a-311">自 .NET Core 2.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ddf5a-312">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-312">Location to place the generated output.</span></span> <span data-ttu-id="ddf5a-313">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="ddf5a-314">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-314">Filters templates based on available types.</span></span> <span data-ttu-id="ddf5a-315">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="ddf5a-316">在 `PATH` 或 `NUGET_ID` 提供的上卸載範本套件。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ddf5a-317">若未指定 `<PATH|NUGET_ID>` 值，則會顯示所有目前已安裝的範本套件及其相關聯的範本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="ddf5a-318">指定 `NUGET_ID`時，請勿包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="ddf5a-319">如果您未指定此選項的參數，此命令會列出已安裝的範本和其相關詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ddf5a-320">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ddf5a-321">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="ddf5a-322">請勿在您的範本路徑上包含最後終止的目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="ddf5a-323">檢查目前已安裝的範本套件是否有可用的更新，並加以安裝。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="ddf5a-324">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="ddf5a-325">檢查目前是否已安裝的範本套件是否有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="ddf5a-326">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="ddf5a-327">範本選項</span><span class="sxs-lookup"><span data-stu-id="ddf5a-327">Template options</span></span>

<span data-ttu-id="ddf5a-328">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-328">Each project template may have additional options available.</span></span> <span data-ttu-id="ddf5a-329">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="ddf5a-330">console</span><span class="sxs-lookup"><span data-stu-id="ddf5a-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-331">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ddf5a-332">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ddf5a-333">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ddf5a-334">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-334">SDK version</span></span> | <span data-ttu-id="ddf5a-335">預設值</span><span class="sxs-lookup"><span data-stu-id="ddf5a-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ddf5a-336">3.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ddf5a-337">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ddf5a-338">設定所建立之專案檔中的 `LangVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ddf5a-339">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ddf5a-340">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-340">Not supported for F#.</span></span> <span data-ttu-id="ddf5a-341">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ddf5a-342">如需預設C#版本清單，請參閱預設[值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`** 

  <span data-ttu-id="ddf5a-343">若已指定，則不會在專案建立期間執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="ddf5a-344">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="ddf5a-345">classlib</span><span class="sxs-lookup"><span data-stu-id="ddf5a-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-346">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ddf5a-347">值：`netcoreapp<version>` 建立 .NET Core 類別庫或 `netstandard<version>` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ddf5a-348">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ddf5a-349">設定所建立之專案檔中的 `LangVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ddf5a-350">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ddf5a-351">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-351">Not supported for F#.</span></span> <span data-ttu-id="ddf5a-352">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ddf5a-353">如需預設C#版本清單，請參閱預設[值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ddf5a-354">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="ddf5a-355">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ddf5a-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-356">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ddf5a-357">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ddf5a-358">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-358">Available since .NET Core 3.1 SDK.</span></span> 

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ddf5a-359">設定所建立之專案檔中的 `LangVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ddf5a-360">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ddf5a-361">如需預設C#版本清單，請參閱預設[值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ddf5a-362">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="ddf5a-363">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="ddf5a-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ddf5a-364">設定所建立之專案檔中的 `LangVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ddf5a-365">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ddf5a-366">如需預設C#版本清單，請參閱預設[值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ddf5a-367">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="ddf5a-368">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="ddf5a-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-369">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ddf5a-370">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ddf5a-371">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-371">Available since .NET Core 3.1 SDK.</span></span> 

- **`--exclude-launch-settings`**

  <span data-ttu-id="ddf5a-372">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="ddf5a-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ddf5a-373">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="ddf5a-374">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="ddf5a-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-375">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ddf5a-376">自 .NET Core 3.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ddf5a-377">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ddf5a-378">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-378">SDK version</span></span> | <span data-ttu-id="ddf5a-379">預設值</span><span class="sxs-lookup"><span data-stu-id="ddf5a-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ddf5a-380">3.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ddf5a-381">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ddf5a-382">使用[dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ddf5a-383">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="ddf5a-384">nunit</span><span class="sxs-lookup"><span data-stu-id="ddf5a-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-385">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="ddf5a-386">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ddf5a-387">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-387">SDK version</span></span> | <span data-ttu-id="ddf5a-388">預設值</span><span class="sxs-lookup"><span data-stu-id="ddf5a-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ddf5a-389">3.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ddf5a-390">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ddf5a-391">2.2</span><span class="sxs-lookup"><span data-stu-id="ddf5a-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="ddf5a-392">2.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ddf5a-393">使用[dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ddf5a-394">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="ddf5a-395">頁面</span><span class="sxs-lookup"><span data-stu-id="ddf5a-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ddf5a-396">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-396">Namespace for the generated code.</span></span> <span data-ttu-id="ddf5a-397">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="ddf5a-398">建立不含 PageModel 的頁面。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="ddf5a-399">viewimports.cshtml，proto</span><span class="sxs-lookup"><span data-stu-id="ddf5a-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ddf5a-400">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-400">Namespace for the generated code.</span></span> <span data-ttu-id="ddf5a-401">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="ddf5a-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="ddf5a-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ddf5a-403">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-403">The type of authentication to use.</span></span> <span data-ttu-id="ddf5a-404">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-404">The possible values are:</span></span>

  - <span data-ttu-id="ddf5a-405">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ddf5a-406">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ddf5a-407">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ddf5a-408">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ddf5a-409">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ddf5a-410">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ddf5a-411">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ddf5a-412">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ddf5a-413">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ddf5a-414">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ddf5a-415">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ddf5a-416">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="ddf5a-417">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ddf5a-418">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ddf5a-419">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ddf5a-420">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ddf5a-421">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ddf5a-422">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ddf5a-423">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-423">The Client ID for this project.</span></span> <span data-ttu-id="ddf5a-424">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ddf5a-425">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ddf5a-426">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-426">The domain for the directory tenant.</span></span> <span data-ttu-id="ddf5a-427">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ddf5a-428">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ddf5a-429">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ddf5a-430">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ddf5a-431">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ddf5a-432">應用程式的重新導向 URI 基底路徑中的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ddf5a-433">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ddf5a-434">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ddf5a-435">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ddf5a-436">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ddf5a-437">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="ddf5a-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ddf5a-438">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-438">Turns off HTTPS.</span></span> <span data-ttu-id="ddf5a-439">只有在 `Individual`、`IndividualB2C`、`SingleOrg`或 `MultiOrg` 不是用於 `--auth`時，才適用此選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ddf5a-440">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ddf5a-441">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ddf5a-442">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="ddf5a-443">Web</span><span class="sxs-lookup"><span data-stu-id="ddf5a-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ddf5a-444">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="ddf5a-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-445">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ddf5a-446">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ddf5a-447">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ddf5a-448">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-448">SDK version</span></span> | <span data-ttu-id="ddf5a-449">預設值</span><span class="sxs-lookup"><span data-stu-id="ddf5a-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ddf5a-450">3.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ddf5a-451">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ddf5a-452">2.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ddf5a-453">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ddf5a-454">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="ddf5a-455">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="ddf5a-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ddf5a-456">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-456">The type of authentication to use.</span></span> <span data-ttu-id="ddf5a-457">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-457">The possible values are:</span></span>

  - <span data-ttu-id="ddf5a-458">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ddf5a-459">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ddf5a-460">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ddf5a-461">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ddf5a-462">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ddf5a-463">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ddf5a-464">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ddf5a-465">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ddf5a-466">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ddf5a-467">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ddf5a-468">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ddf5a-469">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="ddf5a-470">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ddf5a-471">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ddf5a-472">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ddf5a-473">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ddf5a-474">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ddf5a-475">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ddf5a-476">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-476">The Client ID for this project.</span></span> <span data-ttu-id="ddf5a-477">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ddf5a-478">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ddf5a-479">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-479">The domain for the directory tenant.</span></span> <span data-ttu-id="ddf5a-480">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ddf5a-481">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ddf5a-482">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ddf5a-483">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ddf5a-484">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ddf5a-485">應用程式的重新導向 URI 基底路徑中的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ddf5a-486">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ddf5a-487">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ddf5a-488">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ddf5a-489">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ddf5a-490">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="ddf5a-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ddf5a-491">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-491">Turns off HTTPS.</span></span> <span data-ttu-id="ddf5a-492">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ddf5a-493">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ddf5a-494">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-495">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ddf5a-496">自 .NET Core 3.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ddf5a-497">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ddf5a-498">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-498">SDK version</span></span> | <span data-ttu-id="ddf5a-499">預設值</span><span class="sxs-lookup"><span data-stu-id="ddf5a-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ddf5a-500">3.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ddf5a-501">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="ddf5a-502">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="ddf5a-503">在專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="ddf5a-504">無法在 .NET Core 2.2 和 3.1 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="ddf5a-505">角度、反應</span><span class="sxs-lookup"><span data-stu-id="ddf5a-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ddf5a-506">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-506">The type of authentication to use.</span></span> <span data-ttu-id="ddf5a-507">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-507">Available since .NET Core 3.0 SDK.</span></span> 
  
  <span data-ttu-id="ddf5a-508">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-508">The possible values are:</span></span>

  - <span data-ttu-id="ddf5a-509">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ddf5a-510">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ddf5a-511">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="ddf5a-511">Excludes *launchSettings.json* from the generated template.</span></span> 

- **`--no-restore`**

  <span data-ttu-id="ddf5a-512">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ddf5a-513">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-513">Turns off HTTPS.</span></span> <span data-ttu-id="ddf5a-514">只有在 `None`驗證時，才適用此選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ddf5a-515">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ddf5a-516">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ddf5a-517">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-518">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ddf5a-519">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ddf5a-520">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ddf5a-521">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-521">SDK version</span></span> | <span data-ttu-id="ddf5a-522">預設值</span><span class="sxs-lookup"><span data-stu-id="ddf5a-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ddf5a-523">3.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ddf5a-524">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ddf5a-525">2.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="ddf5a-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="ddf5a-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ddf5a-527">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="ddf5a-527">Excludes *launchSettings.json* from the generated template.</span></span> 

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-528">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ddf5a-529">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ddf5a-530">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ddf5a-531">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-531">SDK version</span></span> | <span data-ttu-id="ddf5a-532">預設值</span><span class="sxs-lookup"><span data-stu-id="ddf5a-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ddf5a-533">3.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ddf5a-534">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ddf5a-535">2.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="ddf5a-536">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ddf5a-537">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="ddf5a-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="ddf5a-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="ddf5a-539">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="ddf5a-540">支援將傳統的 Razor 頁面和 Views 新增至此程式庫的元件。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="ddf5a-541">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="ddf5a-542">webapi</span><span class="sxs-lookup"><span data-stu-id="ddf5a-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ddf5a-543">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-543">The type of authentication to use.</span></span> <span data-ttu-id="ddf5a-544">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-544">The possible values are:</span></span>

  - <span data-ttu-id="ddf5a-545">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ddf5a-546">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ddf5a-547">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ddf5a-548">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ddf5a-549">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ddf5a-550">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ddf5a-551">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ddf5a-552">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ddf5a-553">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ddf5a-554">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ddf5a-555">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ddf5a-556">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ddf5a-557">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-557">The Client ID for this project.</span></span> <span data-ttu-id="ddf5a-558">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ddf5a-559">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ddf5a-560">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-560">The domain for the directory tenant.</span></span> <span data-ttu-id="ddf5a-561">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ddf5a-562">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ddf5a-563">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ddf5a-564">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ddf5a-565">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ddf5a-566">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ddf5a-567">僅適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ddf5a-568">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="ddf5a-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ddf5a-569">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-569">Turns off HTTPS.</span></span> <span data-ttu-id="ddf5a-570">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ddf5a-571">此選項僅適用于未使用 `IndividualB2C` 或 `SingleOrg` 進行驗證的情況。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ddf5a-572">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ddf5a-573">僅適用于 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddf5a-574">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ddf5a-575">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ddf5a-576">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ddf5a-577">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-577">SDK version</span></span> | <span data-ttu-id="ddf5a-578">預設值</span><span class="sxs-lookup"><span data-stu-id="ddf5a-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ddf5a-579">3.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ddf5a-580">3.0</span><span class="sxs-lookup"><span data-stu-id="ddf5a-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ddf5a-581">2.1</span><span class="sxs-lookup"><span data-stu-id="ddf5a-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ddf5a-582">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="ddf5a-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="ddf5a-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="ddf5a-584">指定要在*global json*檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="ddf5a-585">範例</span><span class="sxs-lookup"><span data-stu-id="ddf5a-585">Examples</span></span>

- <span data-ttu-id="ddf5a-586">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="ddf5a-587">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="ddf5a-588">在指定的目錄中建立 .NET Standard 類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="ddf5a-589">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="ddf5a-590">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="ddf5a-591">列出適用于單一頁面應用程式（SPA）範本的所有範本：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="ddf5a-592">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="ddf5a-593">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="ddf5a-594">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="ddf5a-595">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="ddf5a-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="ddf5a-596">安裝適用于 ASP.NET Core 的 SPA 範本2.0 版：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="ddf5a-597">列出已安裝的範本和其詳細資料，包括如何將它們卸載：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="ddf5a-598">在目前目錄中建立*json* ，將 SDK 版本設定為3.1.101：</span><span class="sxs-lookup"><span data-stu-id="ddf5a-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="ddf5a-599">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddf5a-599">See also</span></span>

- [<span data-ttu-id="ddf5a-600">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="ddf5a-601">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-601">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- <span data-ttu-id="ddf5a-602">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="ddf5a-602">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="ddf5a-603">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="ddf5a-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
