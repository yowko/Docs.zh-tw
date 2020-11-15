---
title: dotnet new 命令
description: Dotnet new 命令會根據指定的範本建立新的 .NET 專案。
no-loc:
- ':::no-loc(Blazor):::'
- ':::no-loc(WebAssembly):::'
ms.date: 09/04/2020
ms.openlocfilehash: 3ee644f05ea5929ffc7b11054ef1d974b811f418
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634451"
---
# <a name="dotnet-new"></a><span data-ttu-id="9ae63-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="9ae63-103">dotnet new</span></span>

<span data-ttu-id="9ae63-104">本文 **適用于：** ✔️ .net CORE 2.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9ae63-105">名稱</span><span class="sxs-lookup"><span data-stu-id="9ae63-105">Name</span></span>

<span data-ttu-id="9ae63-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="9ae63-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9ae63-107">概要</span><span class="sxs-lookup"><span data-stu-id="9ae63-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="9ae63-108">描述</span><span class="sxs-lookup"><span data-stu-id="9ae63-108">Description</span></span>

<span data-ttu-id="9ae63-109">此 `dotnet new` 命令會建立以範本為基礎的 .net 專案或其他成品。</span><span class="sxs-lookup"><span data-stu-id="9ae63-109">The `dotnet new` command creates a .NET project or other artifacts based on a template.</span></span>

<span data-ttu-id="9ae63-110">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="9ae63-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="9ae63-111">隱含還原</span><span class="sxs-lookup"><span data-stu-id="9ae63-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="9ae63-112">引數</span><span class="sxs-lookup"><span data-stu-id="9ae63-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="9ae63-113">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="9ae63-114">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="9ae63-115">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="9ae63-116">您可以執行 `dotnet new --list` 或 `dotnet new -l` 查看所有已安裝範本的清單。</span><span class="sxs-lookup"><span data-stu-id="9ae63-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="9ae63-117">如果 `TEMPLATE` 值與所傳回資料表 **的樣板** 或 **簡短名稱** 資料行中的文字完全相符，則會在這兩個數據行上執行子字串比對。</span><span class="sxs-lookup"><span data-stu-id="9ae63-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="9ae63-118">從 .NET Core 3.0 SDK 開始，當您 `dotnet new` 在下列情況下叫用命令時，CLI 會在 NuGet.org 中搜尋範本：</span><span class="sxs-lookup"><span data-stu-id="9ae63-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="9ae63-119">如果 CLI 在叫用時找不到範本比對 `dotnet new` ，甚至不是部分。</span><span class="sxs-lookup"><span data-stu-id="9ae63-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="9ae63-120">如果有較新版本的範本可供使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="9ae63-121">在此情況下，會建立專案或成品，但 CLI 會警告您有關範本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="9ae63-122">下表顯示隨 .NET SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-122">The following table shows the templates that come pre-installed with the .NET SDK.</span></span> <span data-ttu-id="9ae63-123">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="9ae63-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="9ae63-124">按一下 [簡短名稱] 連結，以查看特定的範本選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="9ae63-125">範本</span><span class="sxs-lookup"><span data-stu-id="9ae63-125">Templates</span></span>                                    | <span data-ttu-id="9ae63-126">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="9ae63-126">Short name</span></span>                      | <span data-ttu-id="9ae63-127">Language</span><span class="sxs-lookup"><span data-stu-id="9ae63-127">Language</span></span>     | <span data-ttu-id="9ae63-128">Tags</span><span class="sxs-lookup"><span data-stu-id="9ae63-128">Tags</span></span>                                  | <span data-ttu-id="9ae63-129">推出的版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="9ae63-130">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="9ae63-130">Console Application</span></span>                          | [<span data-ttu-id="9ae63-131">安慰</span><span class="sxs-lookup"><span data-stu-id="9ae63-131">console</span></span>](#console)             | <span data-ttu-id="9ae63-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-132">[C#], F#, VB</span></span> | <span data-ttu-id="9ae63-133">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="9ae63-133">Common/Console</span></span>                        | <span data-ttu-id="9ae63-134">1.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-134">1.0</span></span>        |
| <span data-ttu-id="9ae63-135">類別庫</span><span class="sxs-lookup"><span data-stu-id="9ae63-135">Class library</span></span>                                | [<span data-ttu-id="9ae63-136">classlib</span><span class="sxs-lookup"><span data-stu-id="9ae63-136">classlib</span></span>](#classlib)           | <span data-ttu-id="9ae63-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-137">[C#], F#, VB</span></span> | <span data-ttu-id="9ae63-138">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="9ae63-138">Common/Library</span></span>                        | <span data-ttu-id="9ae63-139">1.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-139">1.0</span></span>        |
| <span data-ttu-id="9ae63-140">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="9ae63-140">WPF Application</span></span>                              | [<span data-ttu-id="9ae63-141">Wpf</span><span class="sxs-lookup"><span data-stu-id="9ae63-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="9ae63-142">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-142">[C#], VB</span></span>     | <span data-ttu-id="9ae63-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="9ae63-143">Common/WPF</span></span>                            | <span data-ttu-id="9ae63-144">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="9ae63-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="9ae63-145">WPF 類別庫</span><span class="sxs-lookup"><span data-stu-id="9ae63-145">WPF Class library</span></span>                            | [<span data-ttu-id="9ae63-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="9ae63-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="9ae63-147">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-147">[C#], VB</span></span>     | <span data-ttu-id="9ae63-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="9ae63-148">Common/WPF</span></span>                            | <span data-ttu-id="9ae63-149">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="9ae63-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="9ae63-150">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="9ae63-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="9ae63-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="9ae63-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="9ae63-152">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-152">[C#], VB</span></span>     | <span data-ttu-id="9ae63-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="9ae63-153">Common/WPF</span></span>                            | <span data-ttu-id="9ae63-154">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="9ae63-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="9ae63-155">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="9ae63-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="9ae63-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="9ae63-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="9ae63-157">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-157">[C#], VB</span></span>     | <span data-ttu-id="9ae63-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="9ae63-158">Common/WPF</span></span>                            | <span data-ttu-id="9ae63-159">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="9ae63-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="9ae63-160">Windows Forms (WinForms) 應用程式</span><span class="sxs-lookup"><span data-stu-id="9ae63-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="9ae63-161">winforms</span><span class="sxs-lookup"><span data-stu-id="9ae63-161">winforms</span></span>](#winforms)           | <span data-ttu-id="9ae63-162">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-162">[C#], VB</span></span>     | <span data-ttu-id="9ae63-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="9ae63-163">Common/WinForms</span></span>                       | <span data-ttu-id="9ae63-164">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="9ae63-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="9ae63-165">Windows Forms (WinForms) 類別庫</span><span class="sxs-lookup"><span data-stu-id="9ae63-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="9ae63-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="9ae63-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="9ae63-167">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-167">[C#], VB</span></span>     | <span data-ttu-id="9ae63-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="9ae63-168">Common/WinForms</span></span>                       | <span data-ttu-id="9ae63-169">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="9ae63-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="9ae63-170">背景工作服務</span><span class="sxs-lookup"><span data-stu-id="9ae63-170">Worker Service</span></span>                               | [<span data-ttu-id="9ae63-171">工人</span><span class="sxs-lookup"><span data-stu-id="9ae63-171">worker</span></span>](#web-others)           | <span data-ttu-id="9ae63-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-172">[C#]</span></span>         | <span data-ttu-id="9ae63-173">Common/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="9ae63-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="9ae63-174">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-174">3.0</span></span>        |
| <span data-ttu-id="9ae63-175">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="9ae63-175">Unit Test Project</span></span>                            | [<span data-ttu-id="9ae63-176">mstest</span><span class="sxs-lookup"><span data-stu-id="9ae63-176">mstest</span></span>](#test)                 | <span data-ttu-id="9ae63-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-177">[C#], F#, VB</span></span> | <span data-ttu-id="9ae63-178">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="9ae63-178">Test/MSTest</span></span>                           | <span data-ttu-id="9ae63-179">1.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-179">1.0</span></span>        |
| <span data-ttu-id="9ae63-180">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="9ae63-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="9ae63-181">Nunit</span><span class="sxs-lookup"><span data-stu-id="9ae63-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="9ae63-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-182">[C#], F#, VB</span></span> | <span data-ttu-id="9ae63-183">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="9ae63-183">Test/NUnit</span></span>                            | <span data-ttu-id="9ae63-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="9ae63-184">2.1.400</span></span>    |
| <span data-ttu-id="9ae63-185">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="9ae63-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="9ae63-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-186">[C#], F#, VB</span></span> | <span data-ttu-id="9ae63-187">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="9ae63-187">Test/NUnit</span></span>                            | <span data-ttu-id="9ae63-188">2.2</span><span class="sxs-lookup"><span data-stu-id="9ae63-188">2.2</span></span>        |
| <span data-ttu-id="9ae63-189">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="9ae63-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="9ae63-190">xunit</span><span class="sxs-lookup"><span data-stu-id="9ae63-190">xunit</span></span>](#test)                  | <span data-ttu-id="9ae63-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9ae63-191">[C#], F#, VB</span></span> | <span data-ttu-id="9ae63-192">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="9ae63-192">Test/xUnit</span></span>                            | <span data-ttu-id="9ae63-193">1.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-193">1.0</span></span>        |
| <span data-ttu-id="9ae63-194">Razor 元件</span><span class="sxs-lookup"><span data-stu-id="9ae63-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="9ae63-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-195">[C#]</span></span>         | <span data-ttu-id="9ae63-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9ae63-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="9ae63-197">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-197">3.0</span></span>        |
| <span data-ttu-id="9ae63-198">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="9ae63-198">Razor Page</span></span>                                   | [<span data-ttu-id="9ae63-199">page</span><span class="sxs-lookup"><span data-stu-id="9ae63-199">page</span></span>](#page)                   | <span data-ttu-id="9ae63-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-200">[C#]</span></span>         | <span data-ttu-id="9ae63-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9ae63-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="9ae63-202">2.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-202">2.0</span></span>        |
| <span data-ttu-id="9ae63-203">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="9ae63-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="9ae63-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="9ae63-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="9ae63-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-205">[C#]</span></span>         | <span data-ttu-id="9ae63-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9ae63-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="9ae63-207">2.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-207">2.0</span></span>        |
| <span data-ttu-id="9ae63-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="9ae63-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="9ae63-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-209">[C#]</span></span>         | <span data-ttu-id="9ae63-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9ae63-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="9ae63-211">2.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-211">2.0</span></span>        |
| <span data-ttu-id="9ae63-212">:::no-loc(Blazor)::: 伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="9ae63-212">:::no-loc(Blazor)::: Server App</span></span>                            | [<span data-ttu-id="9ae63-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="9ae63-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="9ae63-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-214">[C#]</span></span>         | <span data-ttu-id="9ae63-215">Web:::no-loc(Blazor):::</span><span class="sxs-lookup"><span data-stu-id="9ae63-215">Web/:::no-loc(Blazor):::</span></span>                            | <span data-ttu-id="9ae63-216">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-216">3.0</span></span>        |
| <span data-ttu-id="9ae63-217">:::no-loc(Blazor)::::::no-loc(WebAssembly):::應用程式</span><span class="sxs-lookup"><span data-stu-id="9ae63-217">:::no-loc(Blazor)::: :::no-loc(WebAssembly)::: App</span></span>                       | [<span data-ttu-id="9ae63-218">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="9ae63-218">blazorwasm</span></span>](#blazorwasm)       | <span data-ttu-id="9ae63-219">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-219">[C#]</span></span>         | <span data-ttu-id="9ae63-220">Web:::no-loc(Blazor):::/:::no-loc(WebAssembly):::</span><span class="sxs-lookup"><span data-stu-id="9ae63-220">Web/:::no-loc(Blazor):::/:::no-loc(WebAssembly):::</span></span>                | <span data-ttu-id="9ae63-221">3.1.300</span><span class="sxs-lookup"><span data-stu-id="9ae63-221">3.1.300</span></span>    |
| <span data-ttu-id="9ae63-222">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9ae63-222">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="9ae63-223">Web</span><span class="sxs-lookup"><span data-stu-id="9ae63-223">web</span></span>](#web)                     | <span data-ttu-id="9ae63-224">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9ae63-224">[C#], F#</span></span>     | <span data-ttu-id="9ae63-225">Web/空白</span><span class="sxs-lookup"><span data-stu-id="9ae63-225">Web/Empty</span></span>                             | <span data-ttu-id="9ae63-226">1.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-226">1.0</span></span>        |
| <span data-ttu-id="9ae63-227">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="9ae63-227">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="9ae63-228">Mvc</span><span class="sxs-lookup"><span data-stu-id="9ae63-228">mvc</span></span>](#web-options)             | <span data-ttu-id="9ae63-229">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9ae63-229">[C#], F#</span></span>     | <span data-ttu-id="9ae63-230">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="9ae63-230">Web/MVC</span></span>                               | <span data-ttu-id="9ae63-231">1.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-231">1.0</span></span>        |
| <span data-ttu-id="9ae63-232">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="9ae63-232">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="9ae63-233">webapp，razor</span><span class="sxs-lookup"><span data-stu-id="9ae63-233">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="9ae63-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-234">[C#]</span></span>         | <span data-ttu-id="9ae63-235">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="9ae63-235">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="9ae63-236">2.2、2。0</span><span class="sxs-lookup"><span data-stu-id="9ae63-236">2.2, 2.0</span></span>   |
| <span data-ttu-id="9ae63-237">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="9ae63-237">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="9ae63-238">角</span><span class="sxs-lookup"><span data-stu-id="9ae63-238">angular</span></span>](#spa)                 | <span data-ttu-id="9ae63-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-239">[C#]</span></span>         | <span data-ttu-id="9ae63-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9ae63-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="9ae63-241">2.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-241">2.0</span></span>        |
| <span data-ttu-id="9ae63-242">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="9ae63-242">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="9ae63-243">反應</span><span class="sxs-lookup"><span data-stu-id="9ae63-243">react</span></span>](#spa)                   | <span data-ttu-id="9ae63-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-244">[C#]</span></span>         | <span data-ttu-id="9ae63-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9ae63-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="9ae63-246">2.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-246">2.0</span></span>        |
| <span data-ttu-id="9ae63-247">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="9ae63-247">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="9ae63-248">reactredux</span><span class="sxs-lookup"><span data-stu-id="9ae63-248">reactredux</span></span>](#reactredux)       | <span data-ttu-id="9ae63-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-249">[C#]</span></span>         | <span data-ttu-id="9ae63-250">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9ae63-250">Web/MVC/SPA</span></span>                           | <span data-ttu-id="9ae63-251">2.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-251">2.0</span></span>        |
| <span data-ttu-id="9ae63-252">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="9ae63-252">Razor Class Library</span></span>                          | [<span data-ttu-id="9ae63-253">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="9ae63-253">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="9ae63-254">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-254">[C#]</span></span>         | <span data-ttu-id="9ae63-255">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="9ae63-255">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="9ae63-256">2.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-256">2.1</span></span>        |
| <span data-ttu-id="9ae63-257">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="9ae63-257">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="9ae63-258">webapi</span><span class="sxs-lookup"><span data-stu-id="9ae63-258">webapi</span></span>](#webapi)               | <span data-ttu-id="9ae63-259">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="9ae63-259">[C#], F#</span></span>     | <span data-ttu-id="9ae63-260">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="9ae63-260">Web/WebAPI</span></span>                            | <span data-ttu-id="9ae63-261">1.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-261">1.0</span></span>        |
| <span data-ttu-id="9ae63-262">ASP.NET Core gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="9ae63-262">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="9ae63-263">grpc</span><span class="sxs-lookup"><span data-stu-id="9ae63-263">grpc</span></span>](#web-others)             | <span data-ttu-id="9ae63-264">[C#]</span><span class="sxs-lookup"><span data-stu-id="9ae63-264">[C#]</span></span>         | <span data-ttu-id="9ae63-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="9ae63-265">Web/gRPC</span></span>                              | <span data-ttu-id="9ae63-266">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-266">3.0</span></span>        |
| <span data-ttu-id="9ae63-267">dotnet .gitignore 檔</span><span class="sxs-lookup"><span data-stu-id="9ae63-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="9ae63-268">Config</span><span class="sxs-lookup"><span data-stu-id="9ae63-268">Config</span></span>                                | <span data-ttu-id="9ae63-269">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-269">3.0</span></span>        |
| <span data-ttu-id="9ae63-270">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="9ae63-270">global.json file</span></span>                             | [<span data-ttu-id="9ae63-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="9ae63-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="9ae63-272">Config</span><span class="sxs-lookup"><span data-stu-id="9ae63-272">Config</span></span>                                | <span data-ttu-id="9ae63-273">2.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-273">2.0</span></span>        |
| <span data-ttu-id="9ae63-274">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="9ae63-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="9ae63-275">Config</span><span class="sxs-lookup"><span data-stu-id="9ae63-275">Config</span></span>                                | <span data-ttu-id="9ae63-276">1.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-276">1.0</span></span>        |
| <span data-ttu-id="9ae63-277">Dotnet 本機工具資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="9ae63-277">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="9ae63-278">Config</span><span class="sxs-lookup"><span data-stu-id="9ae63-278">Config</span></span>                                | <span data-ttu-id="9ae63-279">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-279">3.0</span></span>        |
| <span data-ttu-id="9ae63-280">Web 組態</span><span class="sxs-lookup"><span data-stu-id="9ae63-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="9ae63-281">Config</span><span class="sxs-lookup"><span data-stu-id="9ae63-281">Config</span></span>                                | <span data-ttu-id="9ae63-282">1.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-282">1.0</span></span>        |
| <span data-ttu-id="9ae63-283">方案檔</span><span class="sxs-lookup"><span data-stu-id="9ae63-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="9ae63-284">解決方案</span><span class="sxs-lookup"><span data-stu-id="9ae63-284">Solution</span></span>                              | <span data-ttu-id="9ae63-285">1.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-285">1.0</span></span>        |
| <span data-ttu-id="9ae63-286">通訊協定緩衝區檔案</span><span class="sxs-lookup"><span data-stu-id="9ae63-286">Protocol Buffer File</span></span>                         | [<span data-ttu-id="9ae63-287">原</span><span class="sxs-lookup"><span data-stu-id="9ae63-287">proto</span></span>](#namespace)             |              | <span data-ttu-id="9ae63-288">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="9ae63-288">Web/gRPC</span></span>                              | <span data-ttu-id="9ae63-289">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-289">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="9ae63-290">選項</span><span class="sxs-lookup"><span data-stu-id="9ae63-290">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="9ae63-291">若指定的命令會導致建立範本，則顯示執行時會發生的情況摘要。</span><span class="sxs-lookup"><span data-stu-id="9ae63-291">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="9ae63-292">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-292">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="9ae63-293">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="9ae63-293">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="9ae63-294">當所選範本將覆寫輸出目錄中的現有檔案時，這是必要的。</span><span class="sxs-lookup"><span data-stu-id="9ae63-294">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9ae63-295">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="9ae63-295">Prints out help for the command.</span></span> <span data-ttu-id="9ae63-296">您可以針對 `dotnet new` 命令本身或任何範本來叫用它。</span><span class="sxs-lookup"><span data-stu-id="9ae63-296">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="9ae63-297">例如，`dotnet new mvc --help`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-297">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="9ae63-298">從或提供的安裝範本 `PATH` 套件 `NUGET_ID` 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-298">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="9ae63-299">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-299">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="9ae63-300">依預設，會 `dotnet new` 傳遞 \* 版本，代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-300">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="9ae63-301">請參閱 [範例](#examples) 一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="9ae63-301">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="9ae63-302">當您執行此命令時，如果已安裝某個版本的範本，則範本將會更新為指定的版本，或更新為最新的穩定版本（如果未指定任何版本的話）。</span><span class="sxs-lookup"><span data-stu-id="9ae63-302">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="9ae63-303">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-303">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="9ae63-304">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-304">Lists templates containing the specified name.</span></span> <span data-ttu-id="9ae63-305">如果未指定名稱，則會列出所有範本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-305">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="9ae63-306">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="9ae63-306">The language of the template to create.</span></span> <span data-ttu-id="9ae63-307">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-307">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="9ae63-308">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-308">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9ae63-309">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="9ae63-309">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="9ae63-310">在這些情況下，請將語言參數值括在引號中。</span><span class="sxs-lookup"><span data-stu-id="9ae63-310">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="9ae63-311">例如，`dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-311">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="9ae63-312">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ae63-312">The name for the created output.</span></span> <span data-ttu-id="9ae63-313">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ae63-313">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="9ae63-314">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="9ae63-314">Specifies a NuGet source to use during install.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="9ae63-315">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="9ae63-315">Location to place the generated output.</span></span> <span data-ttu-id="9ae63-316">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="9ae63-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="9ae63-317">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-317">Filters templates based on available types.</span></span> <span data-ttu-id="9ae63-318">預先定義的值為 `project` 和 `item` 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-318">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="9ae63-319">在或提供的上卸載範本套件 `PATH` `NUGET_ID` 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="9ae63-320">如果 `<PATH|NUGET_ID>` 未指定此值，則會顯示所有目前已安裝的範本套件及其相關聯的範本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="9ae63-321">指定時 `NUGET_ID` ，請勿包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="9ae63-322">如果您未指定此選項的參數，此命令會列出已安裝的範本以及這些範本的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9ae63-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9ae63-323">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="9ae63-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="9ae63-324">例如， *C：/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 可正常運作，但從包含的資料夾 */GarciaSoftware.ConsoleTemplate.CSharp* 則否。</span><span class="sxs-lookup"><span data-stu-id="9ae63-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="9ae63-325">請勿在您的範本路徑上包含最終終止的目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="9ae63-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="9ae63-326">檢查目前已安裝的範本套件是否有可用的更新，並加以安裝。</span><span class="sxs-lookup"><span data-stu-id="9ae63-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="9ae63-327">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="9ae63-328">檢查目前已安裝的範本套件是否有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="9ae63-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="9ae63-329">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="9ae63-330">範本選項</span><span class="sxs-lookup"><span data-stu-id="9ae63-330">Template options</span></span>

<span data-ttu-id="9ae63-331">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-331">Each project template may have additional options available.</span></span> <span data-ttu-id="9ae63-332">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="9ae63-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="9ae63-333">console</span><span class="sxs-lookup"><span data-stu-id="9ae63-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9ae63-334">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9ae63-335">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="9ae63-336">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="9ae63-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9ae63-337">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-337">SDK version</span></span> | <span data-ttu-id="9ae63-338">預設值</span><span class="sxs-lookup"><span data-stu-id="9ae63-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9ae63-339">5.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-339">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="9ae63-340">3.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-340">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9ae63-341">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-341">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="9ae63-342">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae63-342">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="9ae63-343">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="9ae63-343">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="9ae63-344">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="9ae63-344">Not supported for F#.</span></span> <span data-ttu-id="9ae63-345">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-345">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9ae63-346">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-346">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9ae63-347">如果有指定，就不會在專案建立期間執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-347">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="9ae63-348">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-348">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="9ae63-349">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-349">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="9ae63-350">classlib</span><span class="sxs-lookup"><span data-stu-id="9ae63-350">classlib</span></span>

- <span data-ttu-id="9ae63-351">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-351">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="9ae63-352">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-352">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9ae63-353">值： `net5.0` 或 `netcoreapp<version>` 建立 .Net 類別庫，或 `netstandard<version>` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="9ae63-353">Values: `net5.0` or `netcoreapp<version>` to create a .NET Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="9ae63-354">.NET 5.0 SDK 的預設值為 `net5.0` 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-354">The default value for .NET 5.0 SDK is `net5.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="9ae63-355">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae63-355">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="9ae63-356">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="9ae63-356">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="9ae63-357">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="9ae63-357">Not supported for F#.</span></span> <span data-ttu-id="9ae63-358">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-358">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9ae63-359">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-359">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9ae63-360">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-360">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9ae63-361">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-361">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="9ae63-362">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="9ae63-362">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="9ae63-363">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-363">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="9ae63-364">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-364">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9ae63-365">預設值是 `net5.0`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-365">The default value is `net5.0`.</span></span> <span data-ttu-id="9ae63-366">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-366">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="9ae63-367">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae63-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="9ae63-368">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="9ae63-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="9ae63-369">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9ae63-370">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-370">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9ae63-371">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-371">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="9ae63-372">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="9ae63-372">winforms, winformslib</span></span>

- <span data-ttu-id="9ae63-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="9ae63-374">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae63-374">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="9ae63-375">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="9ae63-375">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="9ae63-376">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-376">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9ae63-377">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-377">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9ae63-378">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-378">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="9ae63-379">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="9ae63-379">worker, grpc</span></span>

- <span data-ttu-id="9ae63-380">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-380">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="9ae63-381">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-381">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9ae63-382">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-382">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="9ae63-383">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-383">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9ae63-384">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-384">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9ae63-385">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-385">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9ae63-386">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-386">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="9ae63-387">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="9ae63-387">mstest, xunit</span></span>

- <span data-ttu-id="9ae63-388">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-388">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="9ae63-389">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-389">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9ae63-390">自 .NET Core 3.0 SDK 起提供的選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-390">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="9ae63-391">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="9ae63-391">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9ae63-392">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-392">SDK version</span></span> | <span data-ttu-id="9ae63-393">預設值</span><span class="sxs-lookup"><span data-stu-id="9ae63-393">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9ae63-394">5.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-394">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="9ae63-395">3.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-395">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9ae63-396">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-396">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="9ae63-397">使用 [dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="9ae63-397">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9ae63-398">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-398">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9ae63-399">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-399">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="9ae63-400">Nunit</span><span class="sxs-lookup"><span data-stu-id="9ae63-400">nunit</span></span>

- <span data-ttu-id="9ae63-401">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-401">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="9ae63-402">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-402">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="9ae63-403">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="9ae63-403">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9ae63-404">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-404">SDK version</span></span> | <span data-ttu-id="9ae63-405">預設值</span><span class="sxs-lookup"><span data-stu-id="9ae63-405">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9ae63-406">5.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-406">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="9ae63-407">3.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-407">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9ae63-408">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-408">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="9ae63-409">2.2</span><span class="sxs-lookup"><span data-stu-id="9ae63-409">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="9ae63-410">2.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-410">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="9ae63-411">使用 [dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="9ae63-411">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9ae63-412">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-412">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9ae63-413">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-413">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="9ae63-414">頁面</span><span class="sxs-lookup"><span data-stu-id="9ae63-414">page</span></span>

- <span data-ttu-id="9ae63-415">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-415">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="9ae63-416">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9ae63-416">Namespace for the generated code.</span></span> <span data-ttu-id="9ae63-417">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-417">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="9ae63-418">建立不含 PageModel 的頁面。</span><span class="sxs-lookup"><span data-stu-id="9ae63-418">Creates the page without a PageModel.</span></span>

<span data-ttu-id="9ae63-419">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-419">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="9ae63-420">>viewimports.cshtml，proto</span><span class="sxs-lookup"><span data-stu-id="9ae63-420">viewimports, proto</span></span>

- <span data-ttu-id="9ae63-421">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-421">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="9ae63-422">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9ae63-422">Namespace for the generated code.</span></span> <span data-ttu-id="9ae63-423">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-423">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="9ae63-424">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-424">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="9ae63-425">blazorserver</span><span class="sxs-lookup"><span data-stu-id="9ae63-425">blazorserver</span></span>

- <span data-ttu-id="9ae63-426">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-426">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="9ae63-427">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9ae63-427">The type of authentication to use.</span></span> <span data-ttu-id="9ae63-428">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="9ae63-428">The possible values are:</span></span>

  - <span data-ttu-id="9ae63-429">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-429">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="9ae63-430">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-430">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="9ae63-431">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-431">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="9ae63-432">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-432">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="9ae63-433">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-433">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="9ae63-434">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-434">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="9ae63-435">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="9ae63-435">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9ae63-436">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-436">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-437">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-437">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="9ae63-438">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-438">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9ae63-439">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-439">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="9ae63-440">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-440">The reset password policy ID for this project.</span></span> <span data-ttu-id="9ae63-441">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-441">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="9ae63-442">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-442">The edit profile policy ID for this project.</span></span> <span data-ttu-id="9ae63-443">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-443">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="9ae63-444">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="9ae63-444">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9ae63-445">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-445">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="9ae63-446">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-446">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="9ae63-447">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-447">The Client ID for this project.</span></span> <span data-ttu-id="9ae63-448">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-448">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="9ae63-449">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-449">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="9ae63-450">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="9ae63-450">The domain for the directory tenant.</span></span> <span data-ttu-id="9ae63-451">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-451">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-452">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-452">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="9ae63-453">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-453">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9ae63-454">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-454">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9ae63-455">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-455">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="9ae63-456">應用程式的重新導向 URI 基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="9ae63-456">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="9ae63-457">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-457">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-458">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-458">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="9ae63-459">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="9ae63-459">Allows this application read-access to the directory.</span></span> <span data-ttu-id="9ae63-460">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-460">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9ae63-461">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-461">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="9ae63-462">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9ae63-462">Turns off HTTPS.</span></span> <span data-ttu-id="9ae63-463">此選項只適用于 `Individual` 、 `IndividualB2C` 、 `SingleOrg` 或 `MultiOrg` 不用於的 `--auth` 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-463">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="9ae63-464">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9ae63-464">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9ae63-465">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-465">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9ae63-466">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-466">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9ae63-467">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-467">\*\*_</span></span>

### <a name="blazorwasm"></a><span data-ttu-id="9ae63-468">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="9ae63-468">blazorwasm</span></span>

- <span data-ttu-id="9ae63-469">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-469">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="9ae63-470">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-470">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="9ae63-471">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="9ae63-471">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9ae63-472">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-472">SDK version</span></span> | <span data-ttu-id="9ae63-473">預設值</span><span class="sxs-lookup"><span data-stu-id="9ae63-473">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9ae63-474">5.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-474">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="9ae63-475">3.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-475">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="9ae63-476">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-476">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="9ae63-477">包含應用程式的 ASP.NET Core 主機 :::no-loc(Blazor)::: :::no-loc(WebAssembly)::: 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-477">Includes an ASP.NET Core host for the :::no-loc(Blazor)::: :::no-loc(WebAssembly)::: app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="9ae63-478">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9ae63-478">The type of authentication to use.</span></span> <span data-ttu-id="9ae63-479">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="9ae63-479">The possible values are:</span></span>

  - <span data-ttu-id="9ae63-480">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-480">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="9ae63-481">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-481">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="9ae63-482">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-482">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="9ae63-483">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-483">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="9ae63-484">OIDC 提供者的授權單位。</span><span class="sxs-lookup"><span data-stu-id="9ae63-484">The authority of the OIDC provider.</span></span> <span data-ttu-id="9ae63-485">搭配 `Individual` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-485">Use with `Individual` authentication.</span></span> <span data-ttu-id="9ae63-486">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-486">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="9ae63-487">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="9ae63-487">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9ae63-488">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-488">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-489">預設值是 `https://aadB2CInstance.b2clogin.com/`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-489">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="9ae63-490">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-490">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9ae63-491">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-491">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="9ae63-492">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="9ae63-492">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9ae63-493">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-493">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9ae63-494">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-494">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="9ae63-495">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-495">The Client ID for this project.</span></span> <span data-ttu-id="9ae63-496">`IndividualB2C` `SingleOrg` `Individual` 在獨立案例中搭配、或驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-496">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="9ae63-497">預設值是 `33333333-3333-3333-33333333333333333`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-497">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="9ae63-498">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="9ae63-498">The domain for the directory tenant.</span></span> <span data-ttu-id="9ae63-499">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-499">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-500">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-500">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="9ae63-501">您想要呼叫之伺服器 API 的應用程式識別碼 Uri。</span><span class="sxs-lookup"><span data-stu-id="9ae63-501">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="9ae63-502">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-502">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-503">預設值是 `api.id.uri`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-503">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="9ae63-504">伺服器所裝載之 API 的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-504">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="9ae63-505">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-505">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-506">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-506">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="9ae63-507">用戶端要求布建存取權杖所需的 API 範圍。</span><span class="sxs-lookup"><span data-stu-id="9ae63-507">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="9ae63-508">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-508">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-509">預設值是 `user_impersonation`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-509">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="9ae63-510">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-510">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9ae63-511">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-511">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9ae63-512">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-512">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="9ae63-513">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="9ae63-513">Allows this application read-access to the directory.</span></span> <span data-ttu-id="9ae63-514">只適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-514">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9ae63-515">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-515">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="9ae63-516">產生漸進式 Web 應用程式 (PWA) 支援安裝和離線使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-516">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="9ae63-517">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9ae63-517">Turns off HTTPS.</span></span> <span data-ttu-id="9ae63-518">只有在 `Individual` 、或不是用於時，此選項才適用 `IndividualB2C` `SingleOrg` `--auth` 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-518">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="9ae63-519">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9ae63-519">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9ae63-520">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-520">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="9ae63-521">要從 web 應用程式呼叫的 API URL。</span><span class="sxs-lookup"><span data-stu-id="9ae63-521">URL of the API to call from the web app.</span></span> <span data-ttu-id="9ae63-522">只有在 `SingleOrg` `IndividualB2C` 未指定 ASP.NET Core 主機的情況下，才適用或驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-522">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="9ae63-523">預設值是 `https://graph.microsoft.com/v1.0/me`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-523">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="9ae63-524">指定 web 應用程式是否呼叫 Microsoft Graph。</span><span class="sxs-lookup"><span data-stu-id="9ae63-524">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="9ae63-525">只適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-525">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="9ae63-526">要求從 web 應用程式呼叫 API 的範圍。</span><span class="sxs-lookup"><span data-stu-id="9ae63-526">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="9ae63-527">只有在 `SingleOrg` `IndividualB2C` 未指定 ASP.NET Core 主機的情況下，才適用或驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-527">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="9ae63-528">預設為 `user.read`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-528">The default is `user.read`.</span></span>

<span data-ttu-id="9ae63-529">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-529">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="9ae63-530">Web</span><span class="sxs-lookup"><span data-stu-id="9ae63-530">web</span></span>

- <span data-ttu-id="9ae63-531">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-531">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="9ae63-532">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9ae63-533">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9ae63-534">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9ae63-535">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="9ae63-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9ae63-536">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-536">SDK version</span></span> | <span data-ttu-id="9ae63-537">預設值</span><span class="sxs-lookup"><span data-stu-id="9ae63-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9ae63-538">5.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-538">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="9ae63-539">3.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-539">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9ae63-540">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-540">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="9ae63-541">2.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-541">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="9ae63-542">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-542">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="9ae63-543">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9ae63-543">Turns off HTTPS.</span></span>

<span data-ttu-id="9ae63-544">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-544">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="9ae63-545">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="9ae63-545">mvc, webapp</span></span>

- <span data-ttu-id="9ae63-546">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-546">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="9ae63-547">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9ae63-547">The type of authentication to use.</span></span> <span data-ttu-id="9ae63-548">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="9ae63-548">The possible values are:</span></span>

  - <span data-ttu-id="9ae63-549">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-549">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="9ae63-550">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-550">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="9ae63-551">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="9ae63-552">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="9ae63-553">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-553">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="9ae63-554">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-554">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="9ae63-555">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="9ae63-555">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9ae63-556">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-556">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-557">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-557">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="9ae63-558">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-558">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9ae63-559">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-559">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="9ae63-560">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-560">The reset password policy ID for this project.</span></span> <span data-ttu-id="9ae63-561">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-561">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="9ae63-562">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-562">The edit profile policy ID for this project.</span></span> <span data-ttu-id="9ae63-563">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-563">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="9ae63-564">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="9ae63-564">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9ae63-565">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-565">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="9ae63-566">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-566">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="9ae63-567">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-567">The Client ID for this project.</span></span> <span data-ttu-id="9ae63-568">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-568">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="9ae63-569">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-569">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="9ae63-570">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="9ae63-570">The domain for the directory tenant.</span></span> <span data-ttu-id="9ae63-571">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-571">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-572">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-572">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="9ae63-573">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-573">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9ae63-574">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-574">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9ae63-575">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-575">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="9ae63-576">應用程式的重新導向 URI 基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="9ae63-576">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="9ae63-577">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-577">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-578">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-578">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="9ae63-579">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="9ae63-579">Allows this application read-access to the directory.</span></span> <span data-ttu-id="9ae63-580">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-580">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9ae63-581">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-581">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="9ae63-582">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9ae63-582">Turns off HTTPS.</span></span> <span data-ttu-id="9ae63-583">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="9ae63-583">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="9ae63-584">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9ae63-584">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9ae63-585">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-585">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9ae63-586">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-586">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9ae63-587">自 .NET Core 3.0 SDK 起提供的選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-587">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="9ae63-588">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="9ae63-588">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9ae63-589">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-589">SDK version</span></span> | <span data-ttu-id="9ae63-590">預設值</span><span class="sxs-lookup"><span data-stu-id="9ae63-590">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9ae63-591">5.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-591">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="9ae63-592">3.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-592">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9ae63-593">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-593">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="9ae63-594">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-594">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="9ae63-595">在專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="9ae63-595">Includes BrowserLink in the project.</span></span> <span data-ttu-id="9ae63-596">無法在 .NET Core 2.2 和 3.1 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-596">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="9ae63-597">判斷專案是否設定為在 Debug 組建中使用 [Razor 執行時間編譯](/aspnet/core/mvc/views/view-compilation#runtime-compilation) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-597">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="9ae63-598">自 .NET Core 3.1.201 SDK 起提供的選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-598">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="9ae63-599">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-599">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="9ae63-600">角度、反應</span><span class="sxs-lookup"><span data-stu-id="9ae63-600">angular, react</span></span>

- <span data-ttu-id="9ae63-601">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-601">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="9ae63-602">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9ae63-602">The type of authentication to use.</span></span> <span data-ttu-id="9ae63-603">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-603">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="9ae63-604">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="9ae63-604">The possible values are:</span></span>

  - <span data-ttu-id="9ae63-605">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-605">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="9ae63-606">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-606">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9ae63-607">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-607">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9ae63-608">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-608">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="9ae63-609">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9ae63-609">Turns off HTTPS.</span></span> <span data-ttu-id="9ae63-610">只有在驗證為時，此選項才適用 `None` 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-610">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="9ae63-611">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9ae63-611">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9ae63-612">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-612">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-613">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-613">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9ae63-614">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-614">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9ae63-615">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-615">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9ae63-616">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="9ae63-616">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9ae63-617">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-617">SDK version</span></span> | <span data-ttu-id="9ae63-618">預設值</span><span class="sxs-lookup"><span data-stu-id="9ae63-618">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9ae63-619">5.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-619">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="9ae63-620">3.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-620">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9ae63-621">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-621">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="9ae63-622">2.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-622">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="9ae63-623">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-623">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="9ae63-624">reactredux</span><span class="sxs-lookup"><span data-stu-id="9ae63-624">reactredux</span></span>

- <span data-ttu-id="9ae63-625">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-625">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="9ae63-626">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-626">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9ae63-627">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-627">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9ae63-628">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-628">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9ae63-629">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="9ae63-629">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9ae63-630">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-630">SDK version</span></span> | <span data-ttu-id="9ae63-631">預設值</span><span class="sxs-lookup"><span data-stu-id="9ae63-631">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9ae63-632">5.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-632">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="9ae63-633">3.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-633">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9ae63-634">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-634">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="9ae63-635">2.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-635">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="9ae63-636">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-636">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="9ae63-637">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9ae63-637">Turns off HTTPS.</span></span>

<span data-ttu-id="9ae63-638">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-638">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="9ae63-639">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="9ae63-639">razorclasslib</span></span>

- <span data-ttu-id="9ae63-640">_ *`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-640">_ *`--no-restore`*\*</span></span>

  <span data-ttu-id="9ae63-641">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-641">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="9ae63-642">除了對此程式庫的元件之外，還支援新增傳統的 Razor 頁面和 Views。</span><span class="sxs-lookup"><span data-stu-id="9ae63-642">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="9ae63-643">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ae63-643">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="9ae63-644">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-644">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="9ae63-645">webapi</span><span class="sxs-lookup"><span data-stu-id="9ae63-645">webapi</span></span>

- <span data-ttu-id="9ae63-646">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-646">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="9ae63-647">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9ae63-647">The type of authentication to use.</span></span> <span data-ttu-id="9ae63-648">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="9ae63-648">The possible values are:</span></span>

  - <span data-ttu-id="9ae63-649">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="9ae63-649">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="9ae63-650">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-650">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="9ae63-651">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-651">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="9ae63-652">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-652">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="9ae63-653">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="9ae63-653">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9ae63-654">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-654">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9ae63-655">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-655">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="9ae63-656">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-656">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9ae63-657">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-657">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="9ae63-658">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="9ae63-658">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9ae63-659">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-659">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9ae63-660">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-660">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="9ae63-661">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-661">The Client ID for this project.</span></span> <span data-ttu-id="9ae63-662">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-662">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="9ae63-663">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-663">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="9ae63-664">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="9ae63-664">The domain for the directory tenant.</span></span> <span data-ttu-id="9ae63-665">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-665">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="9ae63-666">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-666">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="9ae63-667">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ae63-667">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9ae63-668">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="9ae63-668">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9ae63-669">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-669">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="9ae63-670">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="9ae63-670">Allows this application read-access to the directory.</span></span> <span data-ttu-id="9ae63-671">只適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-671">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9ae63-672">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-672">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="9ae63-673">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9ae63-673">Turns off HTTPS.</span></span> <span data-ttu-id="9ae63-674">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="9ae63-674">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="9ae63-675">此選項僅適用于 `IndividualB2C` 或 `SingleOrg` 未用於驗證時。</span><span class="sxs-lookup"><span data-stu-id="9ae63-675">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="9ae63-676">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9ae63-676">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9ae63-677">只適用于 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="9ae63-677">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9ae63-678">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ae63-678">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9ae63-679">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="9ae63-679">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9ae63-680">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="9ae63-680">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9ae63-681">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9ae63-681">SDK version</span></span> | <span data-ttu-id="9ae63-682">預設值</span><span class="sxs-lookup"><span data-stu-id="9ae63-682">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9ae63-683">5.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-683">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="9ae63-684">3.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-684">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9ae63-685">3.0</span><span class="sxs-lookup"><span data-stu-id="9ae63-685">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="9ae63-686">2.1</span><span class="sxs-lookup"><span data-stu-id="9ae63-686">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="9ae63-687">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="9ae63-687">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9ae63-688">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ae63-688">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="9ae63-689">globaljson</span><span class="sxs-lookup"><span data-stu-id="9ae63-689">globaljson</span></span>

- <span data-ttu-id="9ae63-690">_ *`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="9ae63-690">_ *`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="9ae63-691">指定要在 *global.js* 檔案中使用的 .net SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-691">Specifies the version of the .NET SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="9ae63-692">範例</span><span class="sxs-lookup"><span data-stu-id="9ae63-692">Examples</span></span>

- <span data-ttu-id="9ae63-693">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="9ae63-693">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="9ae63-694">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="9ae63-694">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="9ae63-695">在指定的目錄中建立 .NET Standard 類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="9ae63-695">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="9ae63-696">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="9ae63-696">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="9ae63-697">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="9ae63-697">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="9ae63-698">列出可用於單一頁面應用程式 (SPA) 範本的所有範本：</span><span class="sxs-lookup"><span data-stu-id="9ae63-698">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="9ae63-699">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-699">List all templates matching the *we* substring.</span></span> <span data-ttu-id="9ae63-700">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="9ae63-700">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="9ae63-701">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-701">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="9ae63-702">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="9ae63-702">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="9ae63-703">安裝 ASP.NET Core 的 SPA 範本2.0 版：</span><span class="sxs-lookup"><span data-stu-id="9ae63-703">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="9ae63-704">列出已安裝的範本以及這些範本的詳細資料，包括如何將它們卸載：</span><span class="sxs-lookup"><span data-stu-id="9ae63-704">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="9ae63-705">在目前目錄中建立 *global.js* ，將 SDK 版本設定為3.1.101：</span><span class="sxs-lookup"><span data-stu-id="9ae63-705">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="9ae63-706">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ae63-706">See also</span></span>

- [<span data-ttu-id="9ae63-707">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="9ae63-707">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="9ae63-708">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="9ae63-708">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- <span data-ttu-id="9ae63-709">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="9ae63-709">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="9ae63-710">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="9ae63-710">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
