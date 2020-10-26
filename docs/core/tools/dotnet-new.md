---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
no-loc:
- Blazor
- WebAssembly
ms.date: 09/01/2020
ms.openlocfilehash: 4a4c8e2806fee663b5f6aa255a6f24250a072a85
ms.sourcegitcommit: 532b03d5bbab764d63356193b04cd2281bc01239
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2020
ms.locfileid: "92526616"
---
# <a name="dotnet-new"></a><span data-ttu-id="c9bfb-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c9bfb-103">dotnet new</span></span>

<span data-ttu-id="c9bfb-104">本文**適用于：** ✔️ .net CORE 2.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c9bfb-105">名稱</span><span class="sxs-lookup"><span data-stu-id="c9bfb-105">Name</span></span>

<span data-ttu-id="c9bfb-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c9bfb-107">概要</span><span class="sxs-lookup"><span data-stu-id="c9bfb-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="c9bfb-108">描述</span><span class="sxs-lookup"><span data-stu-id="c9bfb-108">Description</span></span>

<span data-ttu-id="c9bfb-109">此 `dotnet new` 命令會建立 .Net Core 專案或以範本為基礎的其他成品。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="c9bfb-110">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="c9bfb-111">隱含還原</span><span class="sxs-lookup"><span data-stu-id="c9bfb-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="c9bfb-112">引數</span><span class="sxs-lookup"><span data-stu-id="c9bfb-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="c9bfb-113">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="c9bfb-114">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="c9bfb-115">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="c9bfb-116">您可以執行 `dotnet new --list` 或 `dotnet new -l` 查看所有已安裝範本的清單。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="c9bfb-117">如果 `TEMPLATE` 值與所傳回資料表 **的樣板** 或 **簡短名稱** 資料行中的文字完全相符，則會在這兩個數據行上執行子字串比對。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="c9bfb-118">從 .NET Core 3.0 SDK 開始，當您 `dotnet new` 在下列情況下叫用命令時，CLI 會在 NuGet.org 中搜尋範本：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="c9bfb-119">如果 CLI 在叫用時找不到範本比對 `dotnet new` ，甚至不是部分。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="c9bfb-120">如果有較新版本的範本可供使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="c9bfb-121">在此情況下，會建立專案或成品，但 CLI 會警告您有關範本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="c9bfb-122">下表說明隨 .NET Core SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="c9bfb-123">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="c9bfb-124">按一下 [簡短名稱] 連結，以查看特定的範本選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="c9bfb-125">範本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-125">Templates</span></span>                                    | <span data-ttu-id="c9bfb-126">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="c9bfb-126">Short name</span></span>                      | <span data-ttu-id="c9bfb-127">語言</span><span class="sxs-lookup"><span data-stu-id="c9bfb-127">Language</span></span>     | <span data-ttu-id="c9bfb-128">標籤</span><span class="sxs-lookup"><span data-stu-id="c9bfb-128">Tags</span></span>                                  | <span data-ttu-id="c9bfb-129">推出的版本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="c9bfb-130">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c9bfb-130">Console Application</span></span>                          | [<span data-ttu-id="c9bfb-131">安慰</span><span class="sxs-lookup"><span data-stu-id="c9bfb-131">console</span></span>](#console)             | <span data-ttu-id="c9bfb-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-132">[C#], F#, VB</span></span> | <span data-ttu-id="c9bfb-133">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="c9bfb-133">Common/Console</span></span>                        | <span data-ttu-id="c9bfb-134">1.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-134">1.0</span></span>        |
| <span data-ttu-id="c9bfb-135">類別庫</span><span class="sxs-lookup"><span data-stu-id="c9bfb-135">Class library</span></span>                                | [<span data-ttu-id="c9bfb-136">classlib</span><span class="sxs-lookup"><span data-stu-id="c9bfb-136">classlib</span></span>](#classlib)           | <span data-ttu-id="c9bfb-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-137">[C#], F#, VB</span></span> | <span data-ttu-id="c9bfb-138">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="c9bfb-138">Common/Library</span></span>                        | <span data-ttu-id="c9bfb-139">1.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-139">1.0</span></span>        |
| <span data-ttu-id="c9bfb-140">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="c9bfb-140">WPF Application</span></span>                              | [<span data-ttu-id="c9bfb-141">Wpf</span><span class="sxs-lookup"><span data-stu-id="c9bfb-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="c9bfb-142">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-142">[C#], VB</span></span>     | <span data-ttu-id="c9bfb-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="c9bfb-143">Common/WPF</span></span>                            | <span data-ttu-id="c9bfb-144">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="c9bfb-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="c9bfb-145">WPF 類別庫</span><span class="sxs-lookup"><span data-stu-id="c9bfb-145">WPF Class library</span></span>                            | [<span data-ttu-id="c9bfb-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="c9bfb-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="c9bfb-147">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-147">[C#], VB</span></span>     | <span data-ttu-id="c9bfb-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="c9bfb-148">Common/WPF</span></span>                            | <span data-ttu-id="c9bfb-149">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="c9bfb-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="c9bfb-150">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="c9bfb-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="c9bfb-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="c9bfb-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="c9bfb-152">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-152">[C#], VB</span></span>     | <span data-ttu-id="c9bfb-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="c9bfb-153">Common/WPF</span></span>                            | <span data-ttu-id="c9bfb-154">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="c9bfb-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="c9bfb-155">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="c9bfb-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="c9bfb-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="c9bfb-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="c9bfb-157">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-157">[C#], VB</span></span>     | <span data-ttu-id="c9bfb-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="c9bfb-158">Common/WPF</span></span>                            | <span data-ttu-id="c9bfb-159">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="c9bfb-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="c9bfb-160">Windows Forms (WinForms) 應用程式</span><span class="sxs-lookup"><span data-stu-id="c9bfb-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="c9bfb-161">winforms</span><span class="sxs-lookup"><span data-stu-id="c9bfb-161">winforms</span></span>](#winforms)           | <span data-ttu-id="c9bfb-162">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-162">[C#], VB</span></span>     | <span data-ttu-id="c9bfb-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="c9bfb-163">Common/WinForms</span></span>                       | <span data-ttu-id="c9bfb-164">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="c9bfb-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="c9bfb-165">Windows Forms (WinForms) 類別庫</span><span class="sxs-lookup"><span data-stu-id="c9bfb-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="c9bfb-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="c9bfb-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="c9bfb-167">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-167">[C#], VB</span></span>     | <span data-ttu-id="c9bfb-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="c9bfb-168">Common/WinForms</span></span>                       | <span data-ttu-id="c9bfb-169">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="c9bfb-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="c9bfb-170">背景工作服務</span><span class="sxs-lookup"><span data-stu-id="c9bfb-170">Worker Service</span></span>                               | [<span data-ttu-id="c9bfb-171">工人</span><span class="sxs-lookup"><span data-stu-id="c9bfb-171">worker</span></span>](#web-others)           | <span data-ttu-id="c9bfb-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-172">[C#]</span></span>         | <span data-ttu-id="c9bfb-173">Common/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="c9bfb-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="c9bfb-174">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-174">3.0</span></span>        |
| <span data-ttu-id="c9bfb-175">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="c9bfb-175">Unit Test Project</span></span>                            | [<span data-ttu-id="c9bfb-176">mstest</span><span class="sxs-lookup"><span data-stu-id="c9bfb-176">mstest</span></span>](#test)                 | <span data-ttu-id="c9bfb-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-177">[C#], F#, VB</span></span> | <span data-ttu-id="c9bfb-178">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="c9bfb-178">Test/MSTest</span></span>                           | <span data-ttu-id="c9bfb-179">1.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-179">1.0</span></span>        |
| <span data-ttu-id="c9bfb-180">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="c9bfb-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="c9bfb-181">Nunit</span><span class="sxs-lookup"><span data-stu-id="c9bfb-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="c9bfb-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-182">[C#], F#, VB</span></span> | <span data-ttu-id="c9bfb-183">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="c9bfb-183">Test/NUnit</span></span>                            | <span data-ttu-id="c9bfb-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="c9bfb-184">2.1.400</span></span>    |
| <span data-ttu-id="c9bfb-185">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="c9bfb-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="c9bfb-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-186">[C#], F#, VB</span></span> | <span data-ttu-id="c9bfb-187">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="c9bfb-187">Test/NUnit</span></span>                            | <span data-ttu-id="c9bfb-188">2.2</span><span class="sxs-lookup"><span data-stu-id="c9bfb-188">2.2</span></span>        |
| <span data-ttu-id="c9bfb-189">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="c9bfb-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="c9bfb-190">xunit</span><span class="sxs-lookup"><span data-stu-id="c9bfb-190">xunit</span></span>](#test)                  | <span data-ttu-id="c9bfb-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c9bfb-191">[C#], F#, VB</span></span> | <span data-ttu-id="c9bfb-192">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="c9bfb-192">Test/xUnit</span></span>                            | <span data-ttu-id="c9bfb-193">1.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-193">1.0</span></span>        |
| <span data-ttu-id="c9bfb-194">Razor 元件</span><span class="sxs-lookup"><span data-stu-id="c9bfb-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="c9bfb-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-195">[C#]</span></span>         | <span data-ttu-id="c9bfb-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c9bfb-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="c9bfb-197">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-197">3.0</span></span>        |
| <span data-ttu-id="c9bfb-198">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="c9bfb-198">Razor Page</span></span>                                   | [<span data-ttu-id="c9bfb-199">page</span><span class="sxs-lookup"><span data-stu-id="c9bfb-199">page</span></span>](#page)                   | <span data-ttu-id="c9bfb-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-200">[C#]</span></span>         | <span data-ttu-id="c9bfb-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c9bfb-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="c9bfb-202">2.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-202">2.0</span></span>        |
| <span data-ttu-id="c9bfb-203">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="c9bfb-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="c9bfb-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="c9bfb-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="c9bfb-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-205">[C#]</span></span>         | <span data-ttu-id="c9bfb-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c9bfb-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="c9bfb-207">2.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-207">2.0</span></span>        |
| <span data-ttu-id="c9bfb-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c9bfb-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="c9bfb-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-209">[C#]</span></span>         | <span data-ttu-id="c9bfb-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c9bfb-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="c9bfb-211">2.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-211">2.0</span></span>        |
| <span data-ttu-id="c9bfb-212">Blazor 伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="c9bfb-212">Blazor Server App</span></span>                            | [<span data-ttu-id="c9bfb-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="c9bfb-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="c9bfb-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-214">[C#]</span></span>         | <span data-ttu-id="c9bfb-215">WebBlazor</span><span class="sxs-lookup"><span data-stu-id="c9bfb-215">Web/Blazor</span></span>                            | <span data-ttu-id="c9bfb-216">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-216">3.0</span></span>        |
| <span data-ttu-id="c9bfb-217">BlazorWebAssembly應用程式</span><span class="sxs-lookup"><span data-stu-id="c9bfb-217">Blazor WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="c9bfb-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-218">[C#]</span></span>         | <span data-ttu-id="c9bfb-219">WebBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="c9bfb-219">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="c9bfb-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="c9bfb-220">3.1.300</span></span>    |
| <span data-ttu-id="c9bfb-221">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c9bfb-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="c9bfb-222">Web</span><span class="sxs-lookup"><span data-stu-id="c9bfb-222">web</span></span>](#web)                     | <span data-ttu-id="c9bfb-223">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c9bfb-223">[C#], F#</span></span>     | <span data-ttu-id="c9bfb-224">Web/空白</span><span class="sxs-lookup"><span data-stu-id="c9bfb-224">Web/Empty</span></span>                             | <span data-ttu-id="c9bfb-225">1.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-225">1.0</span></span>        |
| <span data-ttu-id="c9bfb-226">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="c9bfb-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="c9bfb-227">Mvc</span><span class="sxs-lookup"><span data-stu-id="c9bfb-227">mvc</span></span>](#web-options)             | <span data-ttu-id="c9bfb-228">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c9bfb-228">[C#], F#</span></span>     | <span data-ttu-id="c9bfb-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c9bfb-229">Web/MVC</span></span>                               | <span data-ttu-id="c9bfb-230">1.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-230">1.0</span></span>        |
| <span data-ttu-id="c9bfb-231">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="c9bfb-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="c9bfb-232">webapp，razor</span><span class="sxs-lookup"><span data-stu-id="c9bfb-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="c9bfb-233">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-233">[C#]</span></span>         | <span data-ttu-id="c9bfb-234">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="c9bfb-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="c9bfb-235">2.2、2。0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="c9bfb-236">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="c9bfb-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="c9bfb-237">角</span><span class="sxs-lookup"><span data-stu-id="c9bfb-237">angular</span></span>](#spa)                 | <span data-ttu-id="c9bfb-238">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-238">[C#]</span></span>         | <span data-ttu-id="c9bfb-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c9bfb-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c9bfb-240">2.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-240">2.0</span></span>        |
| <span data-ttu-id="c9bfb-241">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="c9bfb-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="c9bfb-242">反應</span><span class="sxs-lookup"><span data-stu-id="c9bfb-242">react</span></span>](#spa)                   | <span data-ttu-id="c9bfb-243">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-243">[C#]</span></span>         | <span data-ttu-id="c9bfb-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c9bfb-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c9bfb-245">2.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-245">2.0</span></span>        |
| <span data-ttu-id="c9bfb-246">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="c9bfb-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="c9bfb-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="c9bfb-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="c9bfb-248">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-248">[C#]</span></span>         | <span data-ttu-id="c9bfb-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c9bfb-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c9bfb-250">2.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-250">2.0</span></span>        |
| <span data-ttu-id="c9bfb-251">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="c9bfb-251">Razor Class Library</span></span>                          | [<span data-ttu-id="c9bfb-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="c9bfb-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="c9bfb-253">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-253">[C#]</span></span>         | <span data-ttu-id="c9bfb-254">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="c9bfb-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="c9bfb-255">2.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-255">2.1</span></span>        |
| <span data-ttu-id="c9bfb-256">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="c9bfb-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="c9bfb-257">webapi</span><span class="sxs-lookup"><span data-stu-id="c9bfb-257">webapi</span></span>](#webapi)               | <span data-ttu-id="c9bfb-258">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="c9bfb-258">[C#], F#</span></span>     | <span data-ttu-id="c9bfb-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c9bfb-259">Web/WebAPI</span></span>                            | <span data-ttu-id="c9bfb-260">1.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-260">1.0</span></span>        |
| <span data-ttu-id="c9bfb-261">ASP.NET Core gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="c9bfb-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="c9bfb-262">grpc</span><span class="sxs-lookup"><span data-stu-id="c9bfb-262">grpc</span></span>](#web-others)             | <span data-ttu-id="c9bfb-263">[C#]</span><span class="sxs-lookup"><span data-stu-id="c9bfb-263">[C#]</span></span>         | <span data-ttu-id="c9bfb-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="c9bfb-264">Web/gRPC</span></span>                              | <span data-ttu-id="c9bfb-265">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-265">3.0</span></span>        |
| <span data-ttu-id="c9bfb-266">dotnet .gitignore 檔</span><span class="sxs-lookup"><span data-stu-id="c9bfb-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="c9bfb-267">Config</span><span class="sxs-lookup"><span data-stu-id="c9bfb-267">Config</span></span>                                | <span data-ttu-id="c9bfb-268">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-268">3.0</span></span>        |
| <span data-ttu-id="c9bfb-269">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="c9bfb-269">global.json file</span></span>                             | [<span data-ttu-id="c9bfb-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="c9bfb-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="c9bfb-271">Config</span><span class="sxs-lookup"><span data-stu-id="c9bfb-271">Config</span></span>                                | <span data-ttu-id="c9bfb-272">2.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-272">2.0</span></span>        |
| <span data-ttu-id="c9bfb-273">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="c9bfb-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="c9bfb-274">Config</span><span class="sxs-lookup"><span data-stu-id="c9bfb-274">Config</span></span>                                | <span data-ttu-id="c9bfb-275">1.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-275">1.0</span></span>        |
| <span data-ttu-id="c9bfb-276">Dotnet 本機工具資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="c9bfb-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="c9bfb-277">Config</span><span class="sxs-lookup"><span data-stu-id="c9bfb-277">Config</span></span>                                | <span data-ttu-id="c9bfb-278">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-278">3.0</span></span>        |
| <span data-ttu-id="c9bfb-279">Web 組態</span><span class="sxs-lookup"><span data-stu-id="c9bfb-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="c9bfb-280">Config</span><span class="sxs-lookup"><span data-stu-id="c9bfb-280">Config</span></span>                                | <span data-ttu-id="c9bfb-281">1.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-281">1.0</span></span>        |
| <span data-ttu-id="c9bfb-282">方案檔</span><span class="sxs-lookup"><span data-stu-id="c9bfb-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="c9bfb-283">解決方案</span><span class="sxs-lookup"><span data-stu-id="c9bfb-283">Solution</span></span>                              | <span data-ttu-id="c9bfb-284">1.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-284">1.0</span></span>        |
| <span data-ttu-id="c9bfb-285">通訊協定緩衝區檔案</span><span class="sxs-lookup"><span data-stu-id="c9bfb-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="c9bfb-286">原</span><span class="sxs-lookup"><span data-stu-id="c9bfb-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="c9bfb-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="c9bfb-287">Web/gRPC</span></span>                              | <span data-ttu-id="c9bfb-288">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="c9bfb-289">選項</span><span class="sxs-lookup"><span data-stu-id="c9bfb-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="c9bfb-290">若指定的命令會導致建立範本，則顯示執行時會發生的情況摘要。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="c9bfb-291">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="c9bfb-292">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c9bfb-293">當所選範本將覆寫輸出目錄中的現有檔案時，這是必要的。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c9bfb-294">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-294">Prints out help for the command.</span></span> <span data-ttu-id="c9bfb-295">您可以針對 `dotnet new` 命令本身或任何範本來叫用它。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="c9bfb-296">例如 `dotnet new mvc --help`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="c9bfb-297">從或提供的安裝範本 `PATH` 套件 `NUGET_ID` 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c9bfb-298">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c9bfb-299">依預設，會 `dotnet new` 傳遞 \* 版本，代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="c9bfb-300">請參閱 [範例](#examples) 一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="c9bfb-301">當您執行此命令時，如果已安裝某個版本的範本，則範本將會更新為指定的版本，或更新為最新的穩定版本（如果未指定任何版本的話）。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="c9bfb-302">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="c9bfb-303">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="c9bfb-304">如果未指定名稱，則會列出所有範本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="c9bfb-305">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-305">The language of the template to create.</span></span> <span data-ttu-id="c9bfb-306">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c9bfb-307">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c9bfb-308">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c9bfb-309">在這些情況下，請將語言參數值括在引號中。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="c9bfb-310">例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="c9bfb-311">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-311">The name for the created output.</span></span> <span data-ttu-id="c9bfb-312">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="c9bfb-313">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="c9bfb-314">自 .NET Core 2.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c9bfb-315">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-315">Location to place the generated output.</span></span> <span data-ttu-id="c9bfb-316">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="c9bfb-317">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-317">Filters templates based on available types.</span></span> <span data-ttu-id="c9bfb-318">預先定義的值為 `project` 和 `item` 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-318">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="c9bfb-319">在或提供的上卸載範本套件 `PATH` `NUGET_ID` 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c9bfb-320">如果 `<PATH|NUGET_ID>` 未指定此值，則會顯示所有目前已安裝的範本套件及其相關聯的範本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="c9bfb-321">指定時 `NUGET_ID` ，請勿包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="c9bfb-322">如果您未指定此選項的參數，此命令會列出已安裝的範本以及這些範本的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c9bfb-323">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c9bfb-324">例如， *C：/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 可正常運作，但從包含的資料夾 */GarciaSoftware.ConsoleTemplate.CSharp* 則否。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="c9bfb-325">請勿在您的範本路徑上包含最終終止的目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="c9bfb-326">檢查目前已安裝的範本套件是否有可用的更新，並加以安裝。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="c9bfb-327">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="c9bfb-328">檢查目前已安裝的範本套件是否有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="c9bfb-329">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="c9bfb-330">範本選項</span><span class="sxs-lookup"><span data-stu-id="c9bfb-330">Template options</span></span>

<span data-ttu-id="c9bfb-331">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-331">Each project template may have additional options available.</span></span> <span data-ttu-id="c9bfb-332">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="c9bfb-333">console</span><span class="sxs-lookup"><span data-stu-id="c9bfb-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c9bfb-334">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c9bfb-335">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c9bfb-336">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c9bfb-337">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-337">SDK version</span></span> | <span data-ttu-id="c9bfb-338">預設值</span><span class="sxs-lookup"><span data-stu-id="c9bfb-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c9bfb-339">3.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c9bfb-340">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c9bfb-341">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c9bfb-342">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c9bfb-343">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-343">Not supported for F#.</span></span> <span data-ttu-id="c9bfb-344">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c9bfb-345">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c9bfb-346">如果有指定，就不會在專案建立期間執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="c9bfb-347">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-347">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="c9bfb-348">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-348">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="c9bfb-349">classlib</span><span class="sxs-lookup"><span data-stu-id="c9bfb-349">classlib</span></span>

- <span data-ttu-id="c9bfb-350">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-350">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="c9bfb-351">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-351">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c9bfb-352">值：`netcoreapp<version>` 建立 .NET Core 類別庫或 `netstandard<version>` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-352">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c9bfb-353">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-353">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c9bfb-354">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-354">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c9bfb-355">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-355">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c9bfb-356">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-356">Not supported for F#.</span></span> <span data-ttu-id="c9bfb-357">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-357">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c9bfb-358">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-358">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c9bfb-359">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-359">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c9bfb-360">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-360">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="c9bfb-361">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="c9bfb-361">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="c9bfb-362">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-362">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="c9bfb-363">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-363">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c9bfb-364">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-364">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="c9bfb-365">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-365">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c9bfb-366">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-366">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c9bfb-367">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-367">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="c9bfb-368">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-368">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c9bfb-369">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-369">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c9bfb-370">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-370">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="c9bfb-371">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="c9bfb-371">winforms, winformslib</span></span>

- <span data-ttu-id="c9bfb-372">_*`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-372">_*`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="c9bfb-373">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-373">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c9bfb-374">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-374">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="c9bfb-375">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-375">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c9bfb-376">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-376">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c9bfb-377">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-377">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="c9bfb-378">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="c9bfb-378">worker, grpc</span></span>

- <span data-ttu-id="c9bfb-379">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-379">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="c9bfb-380">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-380">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c9bfb-381">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-381">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="c9bfb-382">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-382">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c9bfb-383">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-383">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c9bfb-384">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-384">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c9bfb-385">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-385">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="c9bfb-386">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="c9bfb-386">mstest, xunit</span></span>

- <span data-ttu-id="c9bfb-387">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-387">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="c9bfb-388">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c9bfb-389">自 .NET Core 3.0 SDK 起提供的選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-389">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c9bfb-390">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-390">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c9bfb-391">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-391">SDK version</span></span> | <span data-ttu-id="c9bfb-392">預設值</span><span class="sxs-lookup"><span data-stu-id="c9bfb-392">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c9bfb-393">3.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-393">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c9bfb-394">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-394">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="c9bfb-395">使用 [dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-395">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c9bfb-396">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-396">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c9bfb-397">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-397">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="c9bfb-398">Nunit</span><span class="sxs-lookup"><span data-stu-id="c9bfb-398">nunit</span></span>

- <span data-ttu-id="c9bfb-399">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-399">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="c9bfb-400">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-400">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="c9bfb-401">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-401">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c9bfb-402">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-402">SDK version</span></span> | <span data-ttu-id="c9bfb-403">預設值</span><span class="sxs-lookup"><span data-stu-id="c9bfb-403">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c9bfb-404">3.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-404">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c9bfb-405">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-405">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c9bfb-406">2.2</span><span class="sxs-lookup"><span data-stu-id="c9bfb-406">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="c9bfb-407">2.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-407">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="c9bfb-408">使用 [dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-408">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c9bfb-409">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-409">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c9bfb-410">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-410">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="c9bfb-411">頁面</span><span class="sxs-lookup"><span data-stu-id="c9bfb-411">page</span></span>

- <span data-ttu-id="c9bfb-412">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-412">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="c9bfb-413">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-413">Namespace for the generated code.</span></span> <span data-ttu-id="c9bfb-414">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-414">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="c9bfb-415">建立不含 PageModel 的頁面。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-415">Creates the page without a PageModel.</span></span>

<span data-ttu-id="c9bfb-416">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-416">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="c9bfb-417">>viewimports.cshtml，proto</span><span class="sxs-lookup"><span data-stu-id="c9bfb-417">viewimports, proto</span></span>

- <span data-ttu-id="c9bfb-418">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-418">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="c9bfb-419">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-419">Namespace for the generated code.</span></span> <span data-ttu-id="c9bfb-420">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-420">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c9bfb-421">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-421">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="c9bfb-422">blazorserver</span><span class="sxs-lookup"><span data-stu-id="c9bfb-422">blazorserver</span></span>

- <span data-ttu-id="c9bfb-423">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-423">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="c9bfb-424">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-424">The type of authentication to use.</span></span> <span data-ttu-id="c9bfb-425">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-425">The possible values are:</span></span>

  - <span data-ttu-id="c9bfb-426">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-426">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c9bfb-427">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-427">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="c9bfb-428">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-428">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c9bfb-429">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-429">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c9bfb-430">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-430">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="c9bfb-431">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-431">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c9bfb-432">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-432">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c9bfb-433">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-433">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c9bfb-434">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-434">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c9bfb-435">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-435">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c9bfb-436">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-436">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="c9bfb-437">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-437">The reset password policy ID for this project.</span></span> <span data-ttu-id="c9bfb-438">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-438">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="c9bfb-439">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-439">The edit profile policy ID for this project.</span></span> <span data-ttu-id="c9bfb-440">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-440">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c9bfb-441">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-441">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c9bfb-442">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-442">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c9bfb-443">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-443">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c9bfb-444">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-444">The Client ID for this project.</span></span> <span data-ttu-id="c9bfb-445">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-445">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c9bfb-446">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-446">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c9bfb-447">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-447">The domain for the directory tenant.</span></span> <span data-ttu-id="c9bfb-448">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-448">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c9bfb-449">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-449">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c9bfb-450">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-450">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c9bfb-451">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-451">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c9bfb-452">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-452">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="c9bfb-453">應用程式的重新導向 URI 基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-453">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c9bfb-454">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-454">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c9bfb-455">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-455">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c9bfb-456">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-456">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c9bfb-457">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-457">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c9bfb-458">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-458">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c9bfb-459">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-459">Turns off HTTPS.</span></span> <span data-ttu-id="c9bfb-460">此選項只適用于 `Individual` 、 `IndividualB2C` 、 `SingleOrg` 或 `MultiOrg` 不用於的 `--auth` 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-460">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c9bfb-461">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-461">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c9bfb-462">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-462">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c9bfb-463">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-463">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c9bfb-464">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-464">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="c9bfb-465">Web</span><span class="sxs-lookup"><span data-stu-id="c9bfb-465">web</span></span>

- <span data-ttu-id="c9bfb-466">_*`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-466">_*`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="c9bfb-467">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-467">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c9bfb-468">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-468">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c9bfb-469">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-469">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c9bfb-470">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-470">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c9bfb-471">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-471">SDK version</span></span> | <span data-ttu-id="c9bfb-472">預設值</span><span class="sxs-lookup"><span data-stu-id="c9bfb-472">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c9bfb-473">3.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-473">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c9bfb-474">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-474">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c9bfb-475">2.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-475">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="c9bfb-476">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-476">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c9bfb-477">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-477">Turns off HTTPS.</span></span>

<span data-ttu-id="c9bfb-478">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-478">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="c9bfb-479">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="c9bfb-479">mvc, webapp</span></span>

- <span data-ttu-id="c9bfb-480">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-480">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="c9bfb-481">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-481">The type of authentication to use.</span></span> <span data-ttu-id="c9bfb-482">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-482">The possible values are:</span></span>

  - <span data-ttu-id="c9bfb-483">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-483">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c9bfb-484">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-484">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="c9bfb-485">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-485">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c9bfb-486">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-486">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c9bfb-487">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-487">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="c9bfb-488">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-488">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c9bfb-489">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-489">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c9bfb-490">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-490">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c9bfb-491">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-491">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c9bfb-492">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-492">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c9bfb-493">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-493">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="c9bfb-494">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-494">The reset password policy ID for this project.</span></span> <span data-ttu-id="c9bfb-495">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-495">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="c9bfb-496">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-496">The edit profile policy ID for this project.</span></span> <span data-ttu-id="c9bfb-497">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-497">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c9bfb-498">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-498">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c9bfb-499">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-499">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c9bfb-500">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-500">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c9bfb-501">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-501">The Client ID for this project.</span></span> <span data-ttu-id="c9bfb-502">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-502">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c9bfb-503">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-503">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c9bfb-504">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-504">The domain for the directory tenant.</span></span> <span data-ttu-id="c9bfb-505">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-505">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c9bfb-506">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-506">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c9bfb-507">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-507">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c9bfb-508">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-508">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c9bfb-509">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-509">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="c9bfb-510">應用程式的重新導向 URI 基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-510">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c9bfb-511">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-511">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c9bfb-512">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-512">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c9bfb-513">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-513">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c9bfb-514">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-514">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c9bfb-515">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-515">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c9bfb-516">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-516">Turns off HTTPS.</span></span> <span data-ttu-id="c9bfb-517">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-517">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c9bfb-518">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c9bfb-519">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c9bfb-520">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c9bfb-521">自 .NET Core 3.0 SDK 起提供的選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-521">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c9bfb-522">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c9bfb-523">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-523">SDK version</span></span> | <span data-ttu-id="c9bfb-524">預設值</span><span class="sxs-lookup"><span data-stu-id="c9bfb-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c9bfb-525">3.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c9bfb-526">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-526">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="c9bfb-527">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-527">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="c9bfb-528">在專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-528">Includes BrowserLink in the project.</span></span> <span data-ttu-id="c9bfb-529">無法在 .NET Core 2.2 和 3.1 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-529">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="c9bfb-530">判斷專案是否設定為在 Debug 組建中使用 [Razor 執行時間編譯](/aspnet/core/mvc/views/view-compilation#runtime-compilation) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-530">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="c9bfb-531">自 .NET Core 3.1.201 SDK 起提供的選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-531">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="c9bfb-532">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-532">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="c9bfb-533">角度、反應</span><span class="sxs-lookup"><span data-stu-id="c9bfb-533">angular, react</span></span>

- <span data-ttu-id="c9bfb-534">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-534">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="c9bfb-535">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-535">The type of authentication to use.</span></span> <span data-ttu-id="c9bfb-536">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-536">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="c9bfb-537">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-537">The possible values are:</span></span>

  - <span data-ttu-id="c9bfb-538">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-538">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c9bfb-539">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-539">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c9bfb-540">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-540">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c9bfb-541">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c9bfb-542">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-542">Turns off HTTPS.</span></span> <span data-ttu-id="c9bfb-543">只有在驗證為時，此選項才適用 `None` 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-543">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c9bfb-544">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-544">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c9bfb-545">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-545">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c9bfb-546">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-546">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c9bfb-547">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-547">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c9bfb-548">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-548">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c9bfb-549">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-549">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c9bfb-550">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-550">SDK version</span></span> | <span data-ttu-id="c9bfb-551">預設值</span><span class="sxs-lookup"><span data-stu-id="c9bfb-551">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c9bfb-552">3.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-552">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c9bfb-553">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-553">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c9bfb-554">2.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-554">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="c9bfb-555">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-555">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="c9bfb-556">reactredux</span><span class="sxs-lookup"><span data-stu-id="c9bfb-556">reactredux</span></span>

- <span data-ttu-id="c9bfb-557">_*`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-557">_*`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="c9bfb-558">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-558">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c9bfb-559">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-559">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c9bfb-560">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-560">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c9bfb-561">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-561">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c9bfb-562">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-562">SDK version</span></span> | <span data-ttu-id="c9bfb-563">預設值</span><span class="sxs-lookup"><span data-stu-id="c9bfb-563">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c9bfb-564">3.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-564">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c9bfb-565">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-565">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c9bfb-566">2.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-566">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="c9bfb-567">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-567">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c9bfb-568">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-568">Turns off HTTPS.</span></span>

<span data-ttu-id="c9bfb-569">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-569">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="c9bfb-570">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="c9bfb-570">razorclasslib</span></span>

- <span data-ttu-id="c9bfb-571">_*`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-571">_*`--no-restore`*\*</span></span>

  <span data-ttu-id="c9bfb-572">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-572">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="c9bfb-573">除了對此程式庫的元件之外，還支援新增傳統的 Razor 頁面和 Views。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-573">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="c9bfb-574">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-574">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="c9bfb-575">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-575">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="c9bfb-576">webapi</span><span class="sxs-lookup"><span data-stu-id="c9bfb-576">webapi</span></span>

- <span data-ttu-id="c9bfb-577">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-577">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="c9bfb-578">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-578">The type of authentication to use.</span></span> <span data-ttu-id="c9bfb-579">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-579">The possible values are:</span></span>

  - <span data-ttu-id="c9bfb-580">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-580">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c9bfb-581">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-581">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c9bfb-582">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-582">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c9bfb-583">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-583">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c9bfb-584">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-584">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c9bfb-585">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-585">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c9bfb-586">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-586">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c9bfb-587">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-587">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c9bfb-588">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-588">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c9bfb-589">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-589">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c9bfb-590">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-590">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c9bfb-591">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-591">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c9bfb-592">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-592">The Client ID for this project.</span></span> <span data-ttu-id="c9bfb-593">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-593">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c9bfb-594">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-594">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c9bfb-595">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-595">The domain for the directory tenant.</span></span> <span data-ttu-id="c9bfb-596">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-596">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c9bfb-597">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-597">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c9bfb-598">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-598">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c9bfb-599">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-599">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c9bfb-600">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-600">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c9bfb-601">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-601">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c9bfb-602">只適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-602">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c9bfb-603">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c9bfb-604">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-604">Turns off HTTPS.</span></span> <span data-ttu-id="c9bfb-605">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-605">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c9bfb-606">此選項僅適用于 `IndividualB2C` 或 `SingleOrg` 未用於驗證時。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-606">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c9bfb-607">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c9bfb-608">只適用于 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-608">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c9bfb-609">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-609">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c9bfb-610">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-610">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c9bfb-611">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-611">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c9bfb-612">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-612">SDK version</span></span> | <span data-ttu-id="c9bfb-613">預設值</span><span class="sxs-lookup"><span data-stu-id="c9bfb-613">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c9bfb-614">3.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-614">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c9bfb-615">3.0</span><span class="sxs-lookup"><span data-stu-id="c9bfb-615">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c9bfb-616">2.1</span><span class="sxs-lookup"><span data-stu-id="c9bfb-616">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="c9bfb-617">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-617">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c9bfb-618">\*\*_</span><span class="sxs-lookup"><span data-stu-id="c9bfb-618">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="c9bfb-619">globaljson</span><span class="sxs-lookup"><span data-stu-id="c9bfb-619">globaljson</span></span>

- <span data-ttu-id="c9bfb-620">_*`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="c9bfb-620">_*`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="c9bfb-621">指定要在檔案 *global.js* 中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-621">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="c9bfb-622">範例</span><span class="sxs-lookup"><span data-stu-id="c9bfb-622">Examples</span></span>

- <span data-ttu-id="c9bfb-623">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-623">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="c9bfb-624">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-624">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="c9bfb-625">在指定的目錄中建立 .NET Standard 類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-625">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="c9bfb-626">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-626">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="c9bfb-627">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-627">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="c9bfb-628">列出可用於單一頁面應用程式 (SPA) 範本的所有範本：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-628">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="c9bfb-629">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-629">List all templates matching the *we* substring.</span></span> <span data-ttu-id="c9bfb-630">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-630">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="c9bfb-631">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-631">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="c9bfb-632">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="c9bfb-632">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="c9bfb-633">安裝 ASP.NET Core 的 SPA 範本2.0 版：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-633">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="c9bfb-634">列出已安裝的範本以及這些範本的詳細資料，包括如何將它們卸載：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-634">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="c9bfb-635">在目前目錄中建立 *global.js* ，將 SDK 版本設定為3.1.101：</span><span class="sxs-lookup"><span data-stu-id="c9bfb-635">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="c9bfb-636">請參閱</span><span class="sxs-lookup"><span data-stu-id="c9bfb-636">See also</span></span>

- [<span data-ttu-id="c9bfb-637">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-637">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="c9bfb-638">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-638">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- <span data-ttu-id="c9bfb-639">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="c9bfb-639">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="c9bfb-640">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="c9bfb-640">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
