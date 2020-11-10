---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
no-loc:
- 'Blazor'
- 'WebAssembly'
ms.date: 09/04/2020
ms.openlocfilehash: 2ee06c37cd950f3b9771db2f30fe353435641d67
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400587"
---
# <a name="dotnet-new"></a><span data-ttu-id="a29cd-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a29cd-103">dotnet new</span></span>

<span data-ttu-id="a29cd-104">本文 **適用于：** ✔️ .net CORE 2.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a29cd-105">名稱</span><span class="sxs-lookup"><span data-stu-id="a29cd-105">Name</span></span>

<span data-ttu-id="a29cd-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="a29cd-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a29cd-107">概要</span><span class="sxs-lookup"><span data-stu-id="a29cd-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="a29cd-108">描述</span><span class="sxs-lookup"><span data-stu-id="a29cd-108">Description</span></span>

<span data-ttu-id="a29cd-109">此 `dotnet new` 命令會建立 .Net Core 專案或以範本為基礎的其他成品。</span><span class="sxs-lookup"><span data-stu-id="a29cd-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="a29cd-110">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="a29cd-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="a29cd-111">隱含還原</span><span class="sxs-lookup"><span data-stu-id="a29cd-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="a29cd-112">引數</span><span class="sxs-lookup"><span data-stu-id="a29cd-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="a29cd-113">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="a29cd-114">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="a29cd-115">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="a29cd-116">您可以執行 `dotnet new --list` 或 `dotnet new -l` 查看所有已安裝範本的清單。</span><span class="sxs-lookup"><span data-stu-id="a29cd-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="a29cd-117">如果 `TEMPLATE` 值與所傳回資料表 **的樣板** 或 **簡短名稱** 資料行中的文字完全相符，則會在這兩個數據行上執行子字串比對。</span><span class="sxs-lookup"><span data-stu-id="a29cd-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="a29cd-118">從 .NET Core 3.0 SDK 開始，當您 `dotnet new` 在下列情況下叫用命令時，CLI 會在 NuGet.org 中搜尋範本：</span><span class="sxs-lookup"><span data-stu-id="a29cd-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="a29cd-119">如果 CLI 在叫用時找不到範本比對 `dotnet new` ，甚至不是部分。</span><span class="sxs-lookup"><span data-stu-id="a29cd-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="a29cd-120">如果有較新版本的範本可供使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="a29cd-121">在此情況下，會建立專案或成品，但 CLI 會警告您有關範本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="a29cd-122">下表說明隨 .NET Core SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="a29cd-123">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="a29cd-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="a29cd-124">按一下 [簡短名稱] 連結，以查看特定的範本選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="a29cd-125">範本</span><span class="sxs-lookup"><span data-stu-id="a29cd-125">Templates</span></span>                                    | <span data-ttu-id="a29cd-126">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="a29cd-126">Short name</span></span>                      | <span data-ttu-id="a29cd-127">語言</span><span class="sxs-lookup"><span data-stu-id="a29cd-127">Language</span></span>     | <span data-ttu-id="a29cd-128">Tags</span><span class="sxs-lookup"><span data-stu-id="a29cd-128">Tags</span></span>                                  | <span data-ttu-id="a29cd-129">推出的版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="a29cd-130">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="a29cd-130">Console Application</span></span>                          | [<span data-ttu-id="a29cd-131">安慰</span><span class="sxs-lookup"><span data-stu-id="a29cd-131">console</span></span>](#console)             | <span data-ttu-id="a29cd-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-132">[C#], F#, VB</span></span> | <span data-ttu-id="a29cd-133">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="a29cd-133">Common/Console</span></span>                        | <span data-ttu-id="a29cd-134">1.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-134">1.0</span></span>        |
| <span data-ttu-id="a29cd-135">類別庫</span><span class="sxs-lookup"><span data-stu-id="a29cd-135">Class library</span></span>                                | [<span data-ttu-id="a29cd-136">classlib</span><span class="sxs-lookup"><span data-stu-id="a29cd-136">classlib</span></span>](#classlib)           | <span data-ttu-id="a29cd-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-137">[C#], F#, VB</span></span> | <span data-ttu-id="a29cd-138">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="a29cd-138">Common/Library</span></span>                        | <span data-ttu-id="a29cd-139">1.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-139">1.0</span></span>        |
| <span data-ttu-id="a29cd-140">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="a29cd-140">WPF Application</span></span>                              | [<span data-ttu-id="a29cd-141">Wpf</span><span class="sxs-lookup"><span data-stu-id="a29cd-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="a29cd-142">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-142">[C#], VB</span></span>     | <span data-ttu-id="a29cd-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="a29cd-143">Common/WPF</span></span>                            | <span data-ttu-id="a29cd-144">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="a29cd-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="a29cd-145">WPF 類別庫</span><span class="sxs-lookup"><span data-stu-id="a29cd-145">WPF Class library</span></span>                            | [<span data-ttu-id="a29cd-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="a29cd-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="a29cd-147">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-147">[C#], VB</span></span>     | <span data-ttu-id="a29cd-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="a29cd-148">Common/WPF</span></span>                            | <span data-ttu-id="a29cd-149">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="a29cd-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="a29cd-150">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="a29cd-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="a29cd-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="a29cd-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="a29cd-152">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-152">[C#], VB</span></span>     | <span data-ttu-id="a29cd-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="a29cd-153">Common/WPF</span></span>                            | <span data-ttu-id="a29cd-154">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="a29cd-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="a29cd-155">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="a29cd-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="a29cd-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="a29cd-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="a29cd-157">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-157">[C#], VB</span></span>     | <span data-ttu-id="a29cd-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="a29cd-158">Common/WPF</span></span>                            | <span data-ttu-id="a29cd-159">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="a29cd-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="a29cd-160">Windows Forms (WinForms) 應用程式</span><span class="sxs-lookup"><span data-stu-id="a29cd-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="a29cd-161">winforms</span><span class="sxs-lookup"><span data-stu-id="a29cd-161">winforms</span></span>](#winforms)           | <span data-ttu-id="a29cd-162">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-162">[C#], VB</span></span>     | <span data-ttu-id="a29cd-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="a29cd-163">Common/WinForms</span></span>                       | <span data-ttu-id="a29cd-164">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="a29cd-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="a29cd-165">Windows Forms (WinForms) 類別庫</span><span class="sxs-lookup"><span data-stu-id="a29cd-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="a29cd-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="a29cd-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="a29cd-167">[C #]，VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-167">[C#], VB</span></span>     | <span data-ttu-id="a29cd-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="a29cd-168">Common/WinForms</span></span>                       | <span data-ttu-id="a29cd-169">適用于 VB 的 3.0 (5.0) </span><span class="sxs-lookup"><span data-stu-id="a29cd-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="a29cd-170">背景工作服務</span><span class="sxs-lookup"><span data-stu-id="a29cd-170">Worker Service</span></span>                               | [<span data-ttu-id="a29cd-171">工人</span><span class="sxs-lookup"><span data-stu-id="a29cd-171">worker</span></span>](#web-others)           | <span data-ttu-id="a29cd-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-172">[C#]</span></span>         | <span data-ttu-id="a29cd-173">Common/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="a29cd-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="a29cd-174">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-174">3.0</span></span>        |
| <span data-ttu-id="a29cd-175">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="a29cd-175">Unit Test Project</span></span>                            | [<span data-ttu-id="a29cd-176">mstest</span><span class="sxs-lookup"><span data-stu-id="a29cd-176">mstest</span></span>](#test)                 | <span data-ttu-id="a29cd-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-177">[C#], F#, VB</span></span> | <span data-ttu-id="a29cd-178">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="a29cd-178">Test/MSTest</span></span>                           | <span data-ttu-id="a29cd-179">1.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-179">1.0</span></span>        |
| <span data-ttu-id="a29cd-180">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="a29cd-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="a29cd-181">Nunit</span><span class="sxs-lookup"><span data-stu-id="a29cd-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="a29cd-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-182">[C#], F#, VB</span></span> | <span data-ttu-id="a29cd-183">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="a29cd-183">Test/NUnit</span></span>                            | <span data-ttu-id="a29cd-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="a29cd-184">2.1.400</span></span>    |
| <span data-ttu-id="a29cd-185">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="a29cd-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="a29cd-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-186">[C#], F#, VB</span></span> | <span data-ttu-id="a29cd-187">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="a29cd-187">Test/NUnit</span></span>                            | <span data-ttu-id="a29cd-188">2.2</span><span class="sxs-lookup"><span data-stu-id="a29cd-188">2.2</span></span>        |
| <span data-ttu-id="a29cd-189">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="a29cd-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="a29cd-190">xunit</span><span class="sxs-lookup"><span data-stu-id="a29cd-190">xunit</span></span>](#test)                  | <span data-ttu-id="a29cd-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a29cd-191">[C#], F#, VB</span></span> | <span data-ttu-id="a29cd-192">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="a29cd-192">Test/xUnit</span></span>                            | <span data-ttu-id="a29cd-193">1.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-193">1.0</span></span>        |
| <span data-ttu-id="a29cd-194">Razor 元件</span><span class="sxs-lookup"><span data-stu-id="a29cd-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="a29cd-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-195">[C#]</span></span>         | <span data-ttu-id="a29cd-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a29cd-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="a29cd-197">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-197">3.0</span></span>        |
| <span data-ttu-id="a29cd-198">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="a29cd-198">Razor Page</span></span>                                   | [<span data-ttu-id="a29cd-199">page</span><span class="sxs-lookup"><span data-stu-id="a29cd-199">page</span></span>](#page)                   | <span data-ttu-id="a29cd-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-200">[C#]</span></span>         | <span data-ttu-id="a29cd-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a29cd-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="a29cd-202">2.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-202">2.0</span></span>        |
| <span data-ttu-id="a29cd-203">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="a29cd-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="a29cd-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="a29cd-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="a29cd-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-205">[C#]</span></span>         | <span data-ttu-id="a29cd-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a29cd-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="a29cd-207">2.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-207">2.0</span></span>        |
| <span data-ttu-id="a29cd-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="a29cd-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="a29cd-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-209">[C#]</span></span>         | <span data-ttu-id="a29cd-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a29cd-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="a29cd-211">2.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-211">2.0</span></span>        |
| <span data-ttu-id="a29cd-212">Blazor 伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="a29cd-212">Blazor Server App</span></span>                            | [<span data-ttu-id="a29cd-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="a29cd-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="a29cd-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-214">[C#]</span></span>         | <span data-ttu-id="a29cd-215">WebBlazor</span><span class="sxs-lookup"><span data-stu-id="a29cd-215">Web/Blazor</span></span>                            | <span data-ttu-id="a29cd-216">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-216">3.0</span></span>        |
| <span data-ttu-id="a29cd-217">BlazorWebAssembly應用程式</span><span class="sxs-lookup"><span data-stu-id="a29cd-217">Blazor WebAssembly App</span></span>                       | [<span data-ttu-id="a29cd-218">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="a29cd-218">blazorwasm</span></span>](#blazorwasm)       | <span data-ttu-id="a29cd-219">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-219">[C#]</span></span>         | <span data-ttu-id="a29cd-220">WebBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="a29cd-220">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="a29cd-221">3.1.300</span><span class="sxs-lookup"><span data-stu-id="a29cd-221">3.1.300</span></span>    |
| <span data-ttu-id="a29cd-222">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a29cd-222">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="a29cd-223">Web</span><span class="sxs-lookup"><span data-stu-id="a29cd-223">web</span></span>](#web)                     | <span data-ttu-id="a29cd-224">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="a29cd-224">[C#], F#</span></span>     | <span data-ttu-id="a29cd-225">Web/空白</span><span class="sxs-lookup"><span data-stu-id="a29cd-225">Web/Empty</span></span>                             | <span data-ttu-id="a29cd-226">1.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-226">1.0</span></span>        |
| <span data-ttu-id="a29cd-227">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="a29cd-227">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="a29cd-228">Mvc</span><span class="sxs-lookup"><span data-stu-id="a29cd-228">mvc</span></span>](#web-options)             | <span data-ttu-id="a29cd-229">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="a29cd-229">[C#], F#</span></span>     | <span data-ttu-id="a29cd-230">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="a29cd-230">Web/MVC</span></span>                               | <span data-ttu-id="a29cd-231">1.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-231">1.0</span></span>        |
| <span data-ttu-id="a29cd-232">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="a29cd-232">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="a29cd-233">webapp，razor</span><span class="sxs-lookup"><span data-stu-id="a29cd-233">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="a29cd-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-234">[C#]</span></span>         | <span data-ttu-id="a29cd-235">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="a29cd-235">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="a29cd-236">2.2、2。0</span><span class="sxs-lookup"><span data-stu-id="a29cd-236">2.2, 2.0</span></span>   |
| <span data-ttu-id="a29cd-237">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="a29cd-237">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="a29cd-238">角</span><span class="sxs-lookup"><span data-stu-id="a29cd-238">angular</span></span>](#spa)                 | <span data-ttu-id="a29cd-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-239">[C#]</span></span>         | <span data-ttu-id="a29cd-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="a29cd-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="a29cd-241">2.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-241">2.0</span></span>        |
| <span data-ttu-id="a29cd-242">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="a29cd-242">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="a29cd-243">反應</span><span class="sxs-lookup"><span data-stu-id="a29cd-243">react</span></span>](#spa)                   | <span data-ttu-id="a29cd-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-244">[C#]</span></span>         | <span data-ttu-id="a29cd-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="a29cd-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="a29cd-246">2.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-246">2.0</span></span>        |
| <span data-ttu-id="a29cd-247">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="a29cd-247">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="a29cd-248">reactredux</span><span class="sxs-lookup"><span data-stu-id="a29cd-248">reactredux</span></span>](#reactredux)       | <span data-ttu-id="a29cd-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-249">[C#]</span></span>         | <span data-ttu-id="a29cd-250">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="a29cd-250">Web/MVC/SPA</span></span>                           | <span data-ttu-id="a29cd-251">2.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-251">2.0</span></span>        |
| <span data-ttu-id="a29cd-252">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="a29cd-252">Razor Class Library</span></span>                          | [<span data-ttu-id="a29cd-253">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="a29cd-253">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="a29cd-254">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-254">[C#]</span></span>         | <span data-ttu-id="a29cd-255">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="a29cd-255">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="a29cd-256">2.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-256">2.1</span></span>        |
| <span data-ttu-id="a29cd-257">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="a29cd-257">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="a29cd-258">webapi</span><span class="sxs-lookup"><span data-stu-id="a29cd-258">webapi</span></span>](#webapi)               | <span data-ttu-id="a29cd-259">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="a29cd-259">[C#], F#</span></span>     | <span data-ttu-id="a29cd-260">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="a29cd-260">Web/WebAPI</span></span>                            | <span data-ttu-id="a29cd-261">1.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-261">1.0</span></span>        |
| <span data-ttu-id="a29cd-262">ASP.NET Core gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="a29cd-262">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="a29cd-263">grpc</span><span class="sxs-lookup"><span data-stu-id="a29cd-263">grpc</span></span>](#web-others)             | <span data-ttu-id="a29cd-264">[C#]</span><span class="sxs-lookup"><span data-stu-id="a29cd-264">[C#]</span></span>         | <span data-ttu-id="a29cd-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="a29cd-265">Web/gRPC</span></span>                              | <span data-ttu-id="a29cd-266">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-266">3.0</span></span>        |
| <span data-ttu-id="a29cd-267">dotnet .gitignore 檔</span><span class="sxs-lookup"><span data-stu-id="a29cd-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="a29cd-268">Config</span><span class="sxs-lookup"><span data-stu-id="a29cd-268">Config</span></span>                                | <span data-ttu-id="a29cd-269">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-269">3.0</span></span>        |
| <span data-ttu-id="a29cd-270">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="a29cd-270">global.json file</span></span>                             | [<span data-ttu-id="a29cd-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="a29cd-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="a29cd-272">Config</span><span class="sxs-lookup"><span data-stu-id="a29cd-272">Config</span></span>                                | <span data-ttu-id="a29cd-273">2.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-273">2.0</span></span>        |
| <span data-ttu-id="a29cd-274">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="a29cd-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="a29cd-275">Config</span><span class="sxs-lookup"><span data-stu-id="a29cd-275">Config</span></span>                                | <span data-ttu-id="a29cd-276">1.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-276">1.0</span></span>        |
| <span data-ttu-id="a29cd-277">Dotnet 本機工具資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="a29cd-277">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="a29cd-278">Config</span><span class="sxs-lookup"><span data-stu-id="a29cd-278">Config</span></span>                                | <span data-ttu-id="a29cd-279">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-279">3.0</span></span>        |
| <span data-ttu-id="a29cd-280">Web 組態</span><span class="sxs-lookup"><span data-stu-id="a29cd-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="a29cd-281">Config</span><span class="sxs-lookup"><span data-stu-id="a29cd-281">Config</span></span>                                | <span data-ttu-id="a29cd-282">1.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-282">1.0</span></span>        |
| <span data-ttu-id="a29cd-283">方案檔</span><span class="sxs-lookup"><span data-stu-id="a29cd-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="a29cd-284">解決方案</span><span class="sxs-lookup"><span data-stu-id="a29cd-284">Solution</span></span>                              | <span data-ttu-id="a29cd-285">1.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-285">1.0</span></span>        |
| <span data-ttu-id="a29cd-286">通訊協定緩衝區檔案</span><span class="sxs-lookup"><span data-stu-id="a29cd-286">Protocol Buffer File</span></span>                         | [<span data-ttu-id="a29cd-287">原</span><span class="sxs-lookup"><span data-stu-id="a29cd-287">proto</span></span>](#namespace)             |              | <span data-ttu-id="a29cd-288">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="a29cd-288">Web/gRPC</span></span>                              | <span data-ttu-id="a29cd-289">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-289">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="a29cd-290">選項</span><span class="sxs-lookup"><span data-stu-id="a29cd-290">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="a29cd-291">若指定的命令會導致建立範本，則顯示執行時會發生的情況摘要。</span><span class="sxs-lookup"><span data-stu-id="a29cd-291">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="a29cd-292">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-292">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="a29cd-293">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="a29cd-293">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="a29cd-294">當所選範本將覆寫輸出目錄中的現有檔案時，這是必要的。</span><span class="sxs-lookup"><span data-stu-id="a29cd-294">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a29cd-295">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="a29cd-295">Prints out help for the command.</span></span> <span data-ttu-id="a29cd-296">您可以針對 `dotnet new` 命令本身或任何範本來叫用它。</span><span class="sxs-lookup"><span data-stu-id="a29cd-296">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="a29cd-297">例如 `dotnet new mvc --help`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-297">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="a29cd-298">從或提供的安裝範本 `PATH` 套件 `NUGET_ID` 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-298">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="a29cd-299">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-299">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="a29cd-300">依預設，會 `dotnet new` 傳遞 \* 版本，代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-300">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="a29cd-301">請參閱 [範例](#examples) 一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="a29cd-301">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="a29cd-302">當您執行此命令時，如果已安裝某個版本的範本，則範本將會更新為指定的版本，或更新為最新的穩定版本（如果未指定任何版本的話）。</span><span class="sxs-lookup"><span data-stu-id="a29cd-302">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="a29cd-303">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-303">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="a29cd-304">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-304">Lists templates containing the specified name.</span></span> <span data-ttu-id="a29cd-305">如果未指定名稱，則會列出所有範本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-305">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="a29cd-306">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="a29cd-306">The language of the template to create.</span></span> <span data-ttu-id="a29cd-307">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-307">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="a29cd-308">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-308">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="a29cd-309">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="a29cd-309">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="a29cd-310">在這些情況下，請將語言參數值括在引號中。</span><span class="sxs-lookup"><span data-stu-id="a29cd-310">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="a29cd-311">例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-311">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="a29cd-312">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="a29cd-312">The name for the created output.</span></span> <span data-ttu-id="a29cd-313">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="a29cd-313">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="a29cd-314">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="a29cd-314">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="a29cd-315">自 .NET Core 2.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-315">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="a29cd-316">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="a29cd-316">Location to place the generated output.</span></span> <span data-ttu-id="a29cd-317">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="a29cd-317">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="a29cd-318">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-318">Filters templates based on available types.</span></span> <span data-ttu-id="a29cd-319">預先定義的值為 `project` 和 `item` 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-319">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="a29cd-320">在或提供的上卸載範本套件 `PATH` `NUGET_ID` 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-320">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="a29cd-321">如果 `<PATH|NUGET_ID>` 未指定此值，則會顯示所有目前已安裝的範本套件及其相關聯的範本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-321">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="a29cd-322">指定時 `NUGET_ID` ，請勿包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-322">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="a29cd-323">如果您未指定此選項的參數，此命令會列出已安裝的範本以及這些範本的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a29cd-323">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="a29cd-324">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="a29cd-324">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="a29cd-325">例如， *C：/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 可正常運作，但從包含的資料夾 */GarciaSoftware.ConsoleTemplate.CSharp* 則否。</span><span class="sxs-lookup"><span data-stu-id="a29cd-325">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="a29cd-326">請勿在您的範本路徑上包含最終終止的目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="a29cd-326">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="a29cd-327">檢查目前已安裝的範本套件是否有可用的更新，並加以安裝。</span><span class="sxs-lookup"><span data-stu-id="a29cd-327">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="a29cd-328">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-328">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="a29cd-329">檢查目前已安裝的範本套件是否有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="a29cd-329">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="a29cd-330">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-330">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="a29cd-331">範本選項</span><span class="sxs-lookup"><span data-stu-id="a29cd-331">Template options</span></span>

<span data-ttu-id="a29cd-332">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-332">Each project template may have additional options available.</span></span> <span data-ttu-id="a29cd-333">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="a29cd-333">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="a29cd-334">console</span><span class="sxs-lookup"><span data-stu-id="a29cd-334">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a29cd-335">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-335">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a29cd-336">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-336">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="a29cd-337">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="a29cd-337">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a29cd-338">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-338">SDK version</span></span> | <span data-ttu-id="a29cd-339">預設值</span><span class="sxs-lookup"><span data-stu-id="a29cd-339">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a29cd-340">3.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-340">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a29cd-341">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-341">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="a29cd-342">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a29cd-342">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="a29cd-343">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="a29cd-343">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="a29cd-344">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="a29cd-344">Not supported for F#.</span></span> <span data-ttu-id="a29cd-345">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-345">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a29cd-346">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-346">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a29cd-347">如果有指定，就不會在專案建立期間執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-347">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="a29cd-348">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-348">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="a29cd-349">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-349">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="a29cd-350">classlib</span><span class="sxs-lookup"><span data-stu-id="a29cd-350">classlib</span></span>

- <span data-ttu-id="a29cd-351">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-351">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="a29cd-352">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-352">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a29cd-353">值：`netcoreapp<version>` 建立 .NET Core 類別庫或 `netstandard<version>` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="a29cd-353">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="a29cd-354">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-354">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="a29cd-355">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a29cd-355">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="a29cd-356">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="a29cd-356">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="a29cd-357">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="a29cd-357">Not supported for F#.</span></span> <span data-ttu-id="a29cd-358">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-358">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a29cd-359">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-359">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a29cd-360">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-360">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a29cd-361">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-361">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="a29cd-362">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="a29cd-362">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="a29cd-363">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-363">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="a29cd-364">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-364">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a29cd-365">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-365">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="a29cd-366">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-366">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="a29cd-367">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a29cd-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="a29cd-368">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="a29cd-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="a29cd-369">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a29cd-370">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-370">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a29cd-371">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-371">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="a29cd-372">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="a29cd-372">winforms, winformslib</span></span>

- <span data-ttu-id="a29cd-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="a29cd-374">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a29cd-374">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="a29cd-375">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="a29cd-375">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="a29cd-376">如需預設 c # 版本的清單，請參閱 [預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-376">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a29cd-377">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-377">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a29cd-378">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-378">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="a29cd-379">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="a29cd-379">worker, grpc</span></span>

- <span data-ttu-id="a29cd-380">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-380">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="a29cd-381">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-381">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a29cd-382">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-382">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="a29cd-383">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-383">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a29cd-384">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-384">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="a29cd-385">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-385">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a29cd-386">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-386">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="a29cd-387">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="a29cd-387">mstest, xunit</span></span>

- <span data-ttu-id="a29cd-388">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-388">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="a29cd-389">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-389">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a29cd-390">自 .NET Core 3.0 SDK 起提供的選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-390">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="a29cd-391">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="a29cd-391">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a29cd-392">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-392">SDK version</span></span> | <span data-ttu-id="a29cd-393">預設值</span><span class="sxs-lookup"><span data-stu-id="a29cd-393">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a29cd-394">3.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-394">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a29cd-395">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-395">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="a29cd-396">使用 [dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="a29cd-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a29cd-397">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-397">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a29cd-398">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-398">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="a29cd-399">Nunit</span><span class="sxs-lookup"><span data-stu-id="a29cd-399">nunit</span></span>

- <span data-ttu-id="a29cd-400">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-400">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="a29cd-401">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-401">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="a29cd-402">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="a29cd-402">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a29cd-403">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-403">SDK version</span></span> | <span data-ttu-id="a29cd-404">預設值</span><span class="sxs-lookup"><span data-stu-id="a29cd-404">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a29cd-405">3.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-405">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a29cd-406">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-406">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="a29cd-407">2.2</span><span class="sxs-lookup"><span data-stu-id="a29cd-407">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="a29cd-408">2.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-408">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="a29cd-409">使用 [dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="a29cd-409">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a29cd-410">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-410">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a29cd-411">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-411">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="a29cd-412">頁面</span><span class="sxs-lookup"><span data-stu-id="a29cd-412">page</span></span>

- <span data-ttu-id="a29cd-413">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-413">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="a29cd-414">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a29cd-414">Namespace for the generated code.</span></span> <span data-ttu-id="a29cd-415">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-415">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="a29cd-416">建立不含 PageModel 的頁面。</span><span class="sxs-lookup"><span data-stu-id="a29cd-416">Creates the page without a PageModel.</span></span>

<span data-ttu-id="a29cd-417">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-417">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="a29cd-418">>viewimports.cshtml，proto</span><span class="sxs-lookup"><span data-stu-id="a29cd-418">viewimports, proto</span></span>

- <span data-ttu-id="a29cd-419">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-419">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="a29cd-420">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a29cd-420">Namespace for the generated code.</span></span> <span data-ttu-id="a29cd-421">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-421">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="a29cd-422">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-422">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="a29cd-423">blazorserver</span><span class="sxs-lookup"><span data-stu-id="a29cd-423">blazorserver</span></span>

- <span data-ttu-id="a29cd-424">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-424">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="a29cd-425">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="a29cd-425">The type of authentication to use.</span></span> <span data-ttu-id="a29cd-426">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="a29cd-426">The possible values are:</span></span>

  - <span data-ttu-id="a29cd-427">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-427">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="a29cd-428">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-428">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="a29cd-429">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-429">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="a29cd-430">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-430">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="a29cd-431">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-431">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="a29cd-432">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-432">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="a29cd-433">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="a29cd-433">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a29cd-434">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-434">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-435">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-435">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="a29cd-436">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-436">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a29cd-437">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-437">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="a29cd-438">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-438">The reset password policy ID for this project.</span></span> <span data-ttu-id="a29cd-439">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-439">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="a29cd-440">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-440">The edit profile policy ID for this project.</span></span> <span data-ttu-id="a29cd-441">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-441">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="a29cd-442">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="a29cd-442">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a29cd-443">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-443">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="a29cd-444">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-444">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="a29cd-445">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-445">The Client ID for this project.</span></span> <span data-ttu-id="a29cd-446">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-446">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="a29cd-447">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-447">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="a29cd-448">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="a29cd-448">The domain for the directory tenant.</span></span> <span data-ttu-id="a29cd-449">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-449">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-450">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-450">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="a29cd-451">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-451">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a29cd-452">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-452">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a29cd-453">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-453">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="a29cd-454">應用程式的重新導向 URI 基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="a29cd-454">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="a29cd-455">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-455">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-456">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-456">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="a29cd-457">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="a29cd-457">Allows this application read-access to the directory.</span></span> <span data-ttu-id="a29cd-458">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-458">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a29cd-459">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-459">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="a29cd-460">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="a29cd-460">Turns off HTTPS.</span></span> <span data-ttu-id="a29cd-461">此選項只適用于 `Individual` 、 `IndividualB2C` 、 `SingleOrg` 或 `MultiOrg` 不用於的 `--auth` 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-461">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="a29cd-462">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="a29cd-462">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a29cd-463">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-463">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="a29cd-464">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-464">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a29cd-465">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-465">\*\*_</span></span>

### <a name="blazorwasm"></a><span data-ttu-id="a29cd-466">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="a29cd-466">blazorwasm</span></span>

- <span data-ttu-id="a29cd-467">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-467">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="a29cd-468">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-468">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="a29cd-469">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="a29cd-469">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a29cd-470">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-470">SDK version</span></span> | <span data-ttu-id="a29cd-471">預設值</span><span class="sxs-lookup"><span data-stu-id="a29cd-471">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a29cd-472">5.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-472">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="a29cd-473">3.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-473">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="a29cd-474">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-474">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="a29cd-475">包含應用程式的 ASP.NET Core 主機 Blazor WebAssembly 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-475">Includes an ASP.NET Core host for the Blazor WebAssembly app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="a29cd-476">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="a29cd-476">The type of authentication to use.</span></span> <span data-ttu-id="a29cd-477">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="a29cd-477">The possible values are:</span></span>

  - <span data-ttu-id="a29cd-478">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-478">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="a29cd-479">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-479">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="a29cd-480">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-480">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="a29cd-481">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-481">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="a29cd-482">OIDC 提供者的授權單位。</span><span class="sxs-lookup"><span data-stu-id="a29cd-482">The authority of the OIDC provider.</span></span> <span data-ttu-id="a29cd-483">搭配 `Individual` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-483">Use with `Individual` authentication.</span></span> <span data-ttu-id="a29cd-484">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-484">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="a29cd-485">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="a29cd-485">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a29cd-486">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-486">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-487">預設值是 `https://aadB2CInstance.b2clogin.com/`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-487">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="a29cd-488">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-488">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a29cd-489">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-489">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="a29cd-490">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="a29cd-490">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a29cd-491">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-491">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a29cd-492">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-492">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="a29cd-493">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-493">The Client ID for this project.</span></span> <span data-ttu-id="a29cd-494">`IndividualB2C` `SingleOrg` `Individual` 在獨立案例中搭配、或驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-494">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="a29cd-495">預設值是 `33333333-3333-3333-33333333333333333`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-495">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="a29cd-496">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="a29cd-496">The domain for the directory tenant.</span></span> <span data-ttu-id="a29cd-497">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-497">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-498">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-498">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="a29cd-499">您想要呼叫之伺服器 API 的應用程式識別碼 Uri。</span><span class="sxs-lookup"><span data-stu-id="a29cd-499">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="a29cd-500">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-500">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-501">預設值是 `api.id.uri`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-501">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="a29cd-502">伺服器所裝載之 API 的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-502">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="a29cd-503">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-503">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-504">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-504">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="a29cd-505">用戶端要求布建存取權杖所需的 API 範圍。</span><span class="sxs-lookup"><span data-stu-id="a29cd-505">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="a29cd-506">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-506">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-507">預設值是 `user_impersonation`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-507">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="a29cd-508">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-508">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a29cd-509">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-509">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a29cd-510">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-510">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="a29cd-511">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="a29cd-511">Allows this application read-access to the directory.</span></span> <span data-ttu-id="a29cd-512">只適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-512">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a29cd-513">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="a29cd-514">產生漸進式 Web 應用程式 (PWA) 支援安裝和離線使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-514">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="a29cd-515">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="a29cd-515">Turns off HTTPS.</span></span> <span data-ttu-id="a29cd-516">只有在 `Individual` 、或不是用於時，此選項才適用 `IndividualB2C` `SingleOrg` `--auth` 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-516">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="a29cd-517">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="a29cd-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a29cd-518">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="a29cd-519">要從 web 應用程式呼叫的 API URL。</span><span class="sxs-lookup"><span data-stu-id="a29cd-519">URL of the API to call from the web app.</span></span> <span data-ttu-id="a29cd-520">只有在 `SingleOrg` `IndividualB2C` 未指定 ASP.NET Core 主機的情況下，才適用或驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-520">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="a29cd-521">預設值是 `https://graph.microsoft.com/v1.0/me`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-521">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="a29cd-522">指定 web 應用程式是否呼叫 Microsoft Graph。</span><span class="sxs-lookup"><span data-stu-id="a29cd-522">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="a29cd-523">只適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-523">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="a29cd-524">要求從 web 應用程式呼叫 API 的範圍。</span><span class="sxs-lookup"><span data-stu-id="a29cd-524">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="a29cd-525">只有在 `SingleOrg` `IndividualB2C` 未指定 ASP.NET Core 主機的情況下，才適用或驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-525">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="a29cd-526">預設為 `user.read`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-526">The default is `user.read`.</span></span>

<span data-ttu-id="a29cd-527">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-527">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="a29cd-528">Web</span><span class="sxs-lookup"><span data-stu-id="a29cd-528">web</span></span>

- <span data-ttu-id="a29cd-529">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-529">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="a29cd-530">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a29cd-531">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a29cd-532">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a29cd-533">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="a29cd-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a29cd-534">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-534">SDK version</span></span> | <span data-ttu-id="a29cd-535">預設值</span><span class="sxs-lookup"><span data-stu-id="a29cd-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a29cd-536">3.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a29cd-537">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="a29cd-538">2.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-538">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="a29cd-539">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="a29cd-540">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="a29cd-540">Turns off HTTPS.</span></span>

<span data-ttu-id="a29cd-541">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-541">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="a29cd-542">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="a29cd-542">mvc, webapp</span></span>

- <span data-ttu-id="a29cd-543">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-543">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="a29cd-544">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="a29cd-544">The type of authentication to use.</span></span> <span data-ttu-id="a29cd-545">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="a29cd-545">The possible values are:</span></span>

  - <span data-ttu-id="a29cd-546">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="a29cd-547">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-547">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="a29cd-548">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="a29cd-549">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="a29cd-550">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-550">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="a29cd-551">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="a29cd-552">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="a29cd-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a29cd-553">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-554">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="a29cd-555">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a29cd-556">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-556">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="a29cd-557">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-557">The reset password policy ID for this project.</span></span> <span data-ttu-id="a29cd-558">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-558">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="a29cd-559">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-559">The edit profile policy ID for this project.</span></span> <span data-ttu-id="a29cd-560">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-560">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="a29cd-561">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="a29cd-561">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a29cd-562">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-562">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="a29cd-563">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-563">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="a29cd-564">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-564">The Client ID for this project.</span></span> <span data-ttu-id="a29cd-565">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-565">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="a29cd-566">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-566">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="a29cd-567">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="a29cd-567">The domain for the directory tenant.</span></span> <span data-ttu-id="a29cd-568">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-568">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-569">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-569">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="a29cd-570">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-570">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a29cd-571">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-571">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a29cd-572">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-572">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="a29cd-573">應用程式的重新導向 URI 基底路徑內的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="a29cd-573">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="a29cd-574">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-574">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-575">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-575">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="a29cd-576">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="a29cd-576">Allows this application read-access to the directory.</span></span> <span data-ttu-id="a29cd-577">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-577">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a29cd-578">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-578">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="a29cd-579">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="a29cd-579">Turns off HTTPS.</span></span> <span data-ttu-id="a29cd-580">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="a29cd-580">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="a29cd-581">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="a29cd-581">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a29cd-582">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-582">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a29cd-583">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-583">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a29cd-584">自 .NET Core 3.0 SDK 起提供的選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-584">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="a29cd-585">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="a29cd-585">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a29cd-586">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-586">SDK version</span></span> | <span data-ttu-id="a29cd-587">預設值</span><span class="sxs-lookup"><span data-stu-id="a29cd-587">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a29cd-588">3.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-588">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a29cd-589">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-589">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="a29cd-590">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-590">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="a29cd-591">在專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="a29cd-591">Includes BrowserLink in the project.</span></span> <span data-ttu-id="a29cd-592">無法在 .NET Core 2.2 和 3.1 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-592">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="a29cd-593">判斷專案是否設定為在 Debug 組建中使用 [Razor 執行時間編譯](/aspnet/core/mvc/views/view-compilation#runtime-compilation) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-593">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="a29cd-594">自 .NET Core 3.1.201 SDK 起提供的選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-594">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="a29cd-595">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-595">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="a29cd-596">角度、反應</span><span class="sxs-lookup"><span data-stu-id="a29cd-596">angular, react</span></span>

- <span data-ttu-id="a29cd-597">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-597">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="a29cd-598">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="a29cd-598">The type of authentication to use.</span></span> <span data-ttu-id="a29cd-599">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-599">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="a29cd-600">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="a29cd-600">The possible values are:</span></span>

  - <span data-ttu-id="a29cd-601">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-601">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="a29cd-602">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-602">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a29cd-603">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="a29cd-604">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-604">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="a29cd-605">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="a29cd-605">Turns off HTTPS.</span></span> <span data-ttu-id="a29cd-606">只有在驗證為時，此選項才適用 `None` 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-606">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="a29cd-607">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="a29cd-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a29cd-608">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-608">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-609">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-609">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a29cd-610">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-610">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a29cd-611">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-611">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a29cd-612">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="a29cd-612">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a29cd-613">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-613">SDK version</span></span> | <span data-ttu-id="a29cd-614">預設值</span><span class="sxs-lookup"><span data-stu-id="a29cd-614">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a29cd-615">3.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-615">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a29cd-616">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-616">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="a29cd-617">2.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-617">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="a29cd-618">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-618">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="a29cd-619">reactredux</span><span class="sxs-lookup"><span data-stu-id="a29cd-619">reactredux</span></span>

- <span data-ttu-id="a29cd-620">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-620">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="a29cd-621">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-621">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a29cd-622">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-622">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a29cd-623">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-623">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a29cd-624">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="a29cd-624">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a29cd-625">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-625">SDK version</span></span> | <span data-ttu-id="a29cd-626">預設值</span><span class="sxs-lookup"><span data-stu-id="a29cd-626">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a29cd-627">3.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-627">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a29cd-628">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-628">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="a29cd-629">2.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-629">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="a29cd-630">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-630">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="a29cd-631">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="a29cd-631">Turns off HTTPS.</span></span>

<span data-ttu-id="a29cd-632">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-632">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="a29cd-633">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="a29cd-633">razorclasslib</span></span>

- <span data-ttu-id="a29cd-634">_ *`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-634">_ *`--no-restore`*\*</span></span>

  <span data-ttu-id="a29cd-635">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-635">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="a29cd-636">除了對此程式庫的元件之外，還支援新增傳統的 Razor 頁面和 Views。</span><span class="sxs-lookup"><span data-stu-id="a29cd-636">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="a29cd-637">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a29cd-637">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="a29cd-638">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-638">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="a29cd-639">webapi</span><span class="sxs-lookup"><span data-stu-id="a29cd-639">webapi</span></span>

- <span data-ttu-id="a29cd-640">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-640">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="a29cd-641">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="a29cd-641">The type of authentication to use.</span></span> <span data-ttu-id="a29cd-642">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="a29cd-642">The possible values are:</span></span>

  - <span data-ttu-id="a29cd-643">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="a29cd-643">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="a29cd-644">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-644">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="a29cd-645">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-645">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="a29cd-646">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-646">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="a29cd-647">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="a29cd-647">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a29cd-648">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-648">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a29cd-649">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-649">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="a29cd-650">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-650">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a29cd-651">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-651">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="a29cd-652">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="a29cd-652">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a29cd-653">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-653">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a29cd-654">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-654">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="a29cd-655">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-655">The Client ID for this project.</span></span> <span data-ttu-id="a29cd-656">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-656">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="a29cd-657">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-657">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="a29cd-658">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="a29cd-658">The domain for the directory tenant.</span></span> <span data-ttu-id="a29cd-659">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-659">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="a29cd-660">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-660">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="a29cd-661">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29cd-661">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a29cd-662">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="a29cd-662">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a29cd-663">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-663">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="a29cd-664">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="a29cd-664">Allows this application read-access to the directory.</span></span> <span data-ttu-id="a29cd-665">只適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-665">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a29cd-666">從產生的範本中排除 *launchSettings.json* 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-666">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="a29cd-667">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="a29cd-667">Turns off HTTPS.</span></span> <span data-ttu-id="a29cd-668">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="a29cd-668">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="a29cd-669">此選項僅適用于 `IndividualB2C` 或 `SingleOrg` 未用於驗證時。</span><span class="sxs-lookup"><span data-stu-id="a29cd-669">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="a29cd-670">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="a29cd-670">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a29cd-671">只適用于 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="a29cd-671">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a29cd-672">指定要設為目標的 [架構](../../standard/frameworks.md) 。</span><span class="sxs-lookup"><span data-stu-id="a29cd-672">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a29cd-673">無法在 .NET Core 2.2 SDK 中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="a29cd-673">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a29cd-674">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="a29cd-674">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a29cd-675">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="a29cd-675">SDK version</span></span> | <span data-ttu-id="a29cd-676">預設值</span><span class="sxs-lookup"><span data-stu-id="a29cd-676">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a29cd-677">3.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-677">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a29cd-678">3.0</span><span class="sxs-lookup"><span data-stu-id="a29cd-678">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="a29cd-679">2.1</span><span class="sxs-lookup"><span data-stu-id="a29cd-679">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="a29cd-680">建立專案時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="a29cd-680">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a29cd-681">\*\*_</span><span class="sxs-lookup"><span data-stu-id="a29cd-681">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="a29cd-682">globaljson</span><span class="sxs-lookup"><span data-stu-id="a29cd-682">globaljson</span></span>

- <span data-ttu-id="a29cd-683">_ *`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="a29cd-683">_ *`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="a29cd-684">指定要在檔案 *global.js* 中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-684">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="a29cd-685">範例</span><span class="sxs-lookup"><span data-stu-id="a29cd-685">Examples</span></span>

- <span data-ttu-id="a29cd-686">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="a29cd-686">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="a29cd-687">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="a29cd-687">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="a29cd-688">在指定的目錄中建立 .NET Standard 類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="a29cd-688">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="a29cd-689">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="a29cd-689">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="a29cd-690">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="a29cd-690">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="a29cd-691">列出可用於單一頁面應用程式 (SPA) 範本的所有範本：</span><span class="sxs-lookup"><span data-stu-id="a29cd-691">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="a29cd-692">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-692">List all templates matching the *we* substring.</span></span> <span data-ttu-id="a29cd-693">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="a29cd-693">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="a29cd-694">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-694">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="a29cd-695">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="a29cd-695">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="a29cd-696">安裝 ASP.NET Core 的 SPA 範本2.0 版：</span><span class="sxs-lookup"><span data-stu-id="a29cd-696">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="a29cd-697">列出已安裝的範本以及這些範本的詳細資料，包括如何將它們卸載：</span><span class="sxs-lookup"><span data-stu-id="a29cd-697">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="a29cd-698">在目前目錄中建立 *global.js* ，將 SDK 版本設定為3.1.101：</span><span class="sxs-lookup"><span data-stu-id="a29cd-698">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="a29cd-699">請參閱</span><span class="sxs-lookup"><span data-stu-id="a29cd-699">See also</span></span>

- [<span data-ttu-id="a29cd-700">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="a29cd-700">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="a29cd-701">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="a29cd-701">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- <span data-ttu-id="a29cd-702">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="a29cd-702">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="a29cd-703">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="a29cd-703">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
