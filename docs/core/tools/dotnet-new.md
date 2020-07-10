---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
no-loc:
- Blazor
- WebAssembly
ms.date: 04/10/2020
ms.openlocfilehash: ec41b3b79ed5eded7c9124d3e4d95c658ee39580
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173116"
---
# <a name="dotnet-new"></a><span data-ttu-id="f6d42-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f6d42-103">dotnet new</span></span>

<span data-ttu-id="f6d42-104">**本文適用于：** ✔️ .net CORE 2.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="f6d42-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f6d42-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f6d42-105">Name</span></span>

<span data-ttu-id="f6d42-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="f6d42-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f6d42-107">概要</span><span class="sxs-lookup"><span data-stu-id="f6d42-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="f6d42-108">描述</span><span class="sxs-lookup"><span data-stu-id="f6d42-108">Description</span></span>

<span data-ttu-id="f6d42-109">`dotnet new`命令會根據範本建立 .Net Core 專案或其他成品。</span><span class="sxs-lookup"><span data-stu-id="f6d42-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="f6d42-110">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="f6d42-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="f6d42-111">隱含還原</span><span class="sxs-lookup"><span data-stu-id="f6d42-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="f6d42-112">引數</span><span class="sxs-lookup"><span data-stu-id="f6d42-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="f6d42-113">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="f6d42-114">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="f6d42-115">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="f6d42-116">您可以執行 `dotnet new --list` 或 `dotnet new -l` 來查看所有已安裝的範本清單。</span><span class="sxs-lookup"><span data-stu-id="f6d42-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="f6d42-117">如果 `TEMPLATE` 值不完全符合所傳回資料表之 [樣板**Templates** ] 或 [**簡短名稱**] 資料行中的文字，則會在這兩個數據行上執行子字串相符。</span><span class="sxs-lookup"><span data-stu-id="f6d42-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="f6d42-118">從 .NET Core 3.0 SDK 開始，當您 `dotnet new` 在下列情況下叫用命令時，CLI 會在 NuGet.org 中搜尋範本：</span><span class="sxs-lookup"><span data-stu-id="f6d42-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="f6d42-119">如果 CLI 在叫用時找不到相符的範本 `dotnet new` ，甚至不是部分。</span><span class="sxs-lookup"><span data-stu-id="f6d42-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="f6d42-120">如果有較新版本的範本可用，則為。</span><span class="sxs-lookup"><span data-stu-id="f6d42-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="f6d42-121">在此情況下，會建立專案或成品，但 CLI 會警告您有關範本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="f6d42-122">下表顯示隨 .NET Core SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="f6d42-123">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="f6d42-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="f6d42-124">按一下 [簡短名稱] 連結，以查看特定的範本選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="f6d42-125">範本</span><span class="sxs-lookup"><span data-stu-id="f6d42-125">Templates</span></span>                                    | <span data-ttu-id="f6d42-126">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="f6d42-126">Short name</span></span>                      | <span data-ttu-id="f6d42-127">語言</span><span class="sxs-lookup"><span data-stu-id="f6d42-127">Language</span></span>     | <span data-ttu-id="f6d42-128">Tags</span><span class="sxs-lookup"><span data-stu-id="f6d42-128">Tags</span></span>                                  | <span data-ttu-id="f6d42-129">引導</span><span class="sxs-lookup"><span data-stu-id="f6d42-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="f6d42-130">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="f6d42-130">Console Application</span></span>                          | [<span data-ttu-id="f6d42-131">控制</span><span class="sxs-lookup"><span data-stu-id="f6d42-131">console</span></span>](#console)             | <span data-ttu-id="f6d42-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f6d42-132">[C#], F#, VB</span></span> | <span data-ttu-id="f6d42-133">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="f6d42-133">Common/Console</span></span>                        | <span data-ttu-id="f6d42-134">1.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-134">1.0</span></span>        |
| <span data-ttu-id="f6d42-135">類別庫</span><span class="sxs-lookup"><span data-stu-id="f6d42-135">Class library</span></span>                                | [<span data-ttu-id="f6d42-136">classlib</span><span class="sxs-lookup"><span data-stu-id="f6d42-136">classlib</span></span>](#classlib)           | <span data-ttu-id="f6d42-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f6d42-137">[C#], F#, VB</span></span> | <span data-ttu-id="f6d42-138">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="f6d42-138">Common/Library</span></span>                        | <span data-ttu-id="f6d42-139">1.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-139">1.0</span></span>        |
| <span data-ttu-id="f6d42-140">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="f6d42-140">WPF Application</span></span>                              | [<span data-ttu-id="f6d42-141">wpf</span><span class="sxs-lookup"><span data-stu-id="f6d42-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="f6d42-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-142">[C#]</span></span>         | <span data-ttu-id="f6d42-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="f6d42-143">Common/WPF</span></span>                            | <span data-ttu-id="f6d42-144">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-144">3.0</span></span>        |
| <span data-ttu-id="f6d42-145">WPF 類別庫</span><span class="sxs-lookup"><span data-stu-id="f6d42-145">WPF Class library</span></span>                            | [<span data-ttu-id="f6d42-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="f6d42-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="f6d42-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-147">[C#]</span></span>         | <span data-ttu-id="f6d42-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="f6d42-148">Common/WPF</span></span>                            | <span data-ttu-id="f6d42-149">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-149">3.0</span></span>        |
| <span data-ttu-id="f6d42-150">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="f6d42-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="f6d42-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="f6d42-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="f6d42-152">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-152">[C#]</span></span>         | <span data-ttu-id="f6d42-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="f6d42-153">Common/WPF</span></span>                            | <span data-ttu-id="f6d42-154">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-154">3.0</span></span>        |
| <span data-ttu-id="f6d42-155">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="f6d42-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="f6d42-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="f6d42-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="f6d42-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-157">[C#]</span></span>         | <span data-ttu-id="f6d42-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="f6d42-158">Common/WPF</span></span>                            | <span data-ttu-id="f6d42-159">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-159">3.0</span></span>        |
| <span data-ttu-id="f6d42-160">Windows Forms (WinForms) 應用程式</span><span class="sxs-lookup"><span data-stu-id="f6d42-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="f6d42-161">winforms</span><span class="sxs-lookup"><span data-stu-id="f6d42-161">winforms</span></span>](#winforms)           | <span data-ttu-id="f6d42-162">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-162">[C#]</span></span>         | <span data-ttu-id="f6d42-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="f6d42-163">Common/WinForms</span></span>                       | <span data-ttu-id="f6d42-164">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-164">3.0</span></span>        |
| <span data-ttu-id="f6d42-165">Windows Forms (WinForms) 類別庫</span><span class="sxs-lookup"><span data-stu-id="f6d42-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="f6d42-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="f6d42-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="f6d42-167">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-167">[C#]</span></span>         | <span data-ttu-id="f6d42-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="f6d42-168">Common/WinForms</span></span>                       | <span data-ttu-id="f6d42-169">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-169">3.0</span></span>        |
| <span data-ttu-id="f6d42-170">背景工作服務</span><span class="sxs-lookup"><span data-stu-id="f6d42-170">Worker Service</span></span>                               | [<span data-ttu-id="f6d42-171">工作</span><span class="sxs-lookup"><span data-stu-id="f6d42-171">worker</span></span>](#web-others)           | <span data-ttu-id="f6d42-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-172">[C#]</span></span>         | <span data-ttu-id="f6d42-173">一般/背景工作/Web</span><span class="sxs-lookup"><span data-stu-id="f6d42-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="f6d42-174">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-174">3.0</span></span>        |
| <span data-ttu-id="f6d42-175">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="f6d42-175">Unit Test Project</span></span>                            | [<span data-ttu-id="f6d42-176">mstest.exe</span><span class="sxs-lookup"><span data-stu-id="f6d42-176">mstest</span></span>](#test)                 | <span data-ttu-id="f6d42-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f6d42-177">[C#], F#, VB</span></span> | <span data-ttu-id="f6d42-178">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="f6d42-178">Test/MSTest</span></span>                           | <span data-ttu-id="f6d42-179">1.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-179">1.0</span></span>        |
| <span data-ttu-id="f6d42-180">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="f6d42-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="f6d42-181">nunit</span><span class="sxs-lookup"><span data-stu-id="f6d42-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="f6d42-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f6d42-182">[C#], F#, VB</span></span> | <span data-ttu-id="f6d42-183">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="f6d42-183">Test/NUnit</span></span>                            | <span data-ttu-id="f6d42-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="f6d42-184">2.1.400</span></span>    |
| <span data-ttu-id="f6d42-185">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="f6d42-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="f6d42-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f6d42-186">[C#], F#, VB</span></span> | <span data-ttu-id="f6d42-187">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="f6d42-187">Test/NUnit</span></span>                            | <span data-ttu-id="f6d42-188">2.2</span><span class="sxs-lookup"><span data-stu-id="f6d42-188">2.2</span></span>        |
| <span data-ttu-id="f6d42-189">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="f6d42-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="f6d42-190">xunit</span><span class="sxs-lookup"><span data-stu-id="f6d42-190">xunit</span></span>](#test)                  | <span data-ttu-id="f6d42-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f6d42-191">[C#], F#, VB</span></span> | <span data-ttu-id="f6d42-192">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="f6d42-192">Test/xUnit</span></span>                            | <span data-ttu-id="f6d42-193">1.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-193">1.0</span></span>        |
| <span data-ttu-id="f6d42-194">Razor 元件</span><span class="sxs-lookup"><span data-stu-id="f6d42-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="f6d42-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-195">[C#]</span></span>         | <span data-ttu-id="f6d42-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f6d42-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="f6d42-197">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-197">3.0</span></span>        |
| <span data-ttu-id="f6d42-198">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="f6d42-198">Razor Page</span></span>                                   | [<span data-ttu-id="f6d42-199">本頁</span><span class="sxs-lookup"><span data-stu-id="f6d42-199">page</span></span>](#page)                   | <span data-ttu-id="f6d42-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-200">[C#]</span></span>         | <span data-ttu-id="f6d42-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f6d42-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="f6d42-202">2.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-202">2.0</span></span>        |
| <span data-ttu-id="f6d42-203">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="f6d42-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="f6d42-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="f6d42-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="f6d42-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-205">[C#]</span></span>         | <span data-ttu-id="f6d42-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f6d42-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="f6d42-207">2.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-207">2.0</span></span>        |
| <span data-ttu-id="f6d42-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="f6d42-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="f6d42-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-209">[C#]</span></span>         | <span data-ttu-id="f6d42-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f6d42-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="f6d42-211">2.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-211">2.0</span></span>        |
| Blazor<span data-ttu-id="f6d42-212">伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="f6d42-212"> Server App</span></span>                            | [<span data-ttu-id="f6d42-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="f6d42-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="f6d42-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-214">[C#]</span></span>         | <span data-ttu-id="f6d42-215">網路Blazor</span><span class="sxs-lookup"><span data-stu-id="f6d42-215">Web/Blazor</span></span>                            | <span data-ttu-id="f6d42-216">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-216">3.0</span></span>        |
| Blazor<span data-ttu-id="f6d42-217">WebAssembly應用程式</span><span class="sxs-lookup"><span data-stu-id="f6d42-217"> WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="f6d42-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-218">[C#]</span></span>         | <span data-ttu-id="f6d42-219">網路Blazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="f6d42-219">Web/Blazor/WebAssembly</span></span>                            | <span data-ttu-id="f6d42-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="f6d42-220">3.1.300</span></span>    |
| <span data-ttu-id="f6d42-221">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f6d42-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="f6d42-222">網路</span><span class="sxs-lookup"><span data-stu-id="f6d42-222">web</span></span>](#web)                     | <span data-ttu-id="f6d42-223">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="f6d42-223">[C#], F#</span></span>     | <span data-ttu-id="f6d42-224">Web/空白</span><span class="sxs-lookup"><span data-stu-id="f6d42-224">Web/Empty</span></span>                             | <span data-ttu-id="f6d42-225">1.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-225">1.0</span></span>        |
| <span data-ttu-id="f6d42-226">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="f6d42-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="f6d42-227">mvc</span><span class="sxs-lookup"><span data-stu-id="f6d42-227">mvc</span></span>](#web-options)             | <span data-ttu-id="f6d42-228">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="f6d42-228">[C#], F#</span></span>     | <span data-ttu-id="f6d42-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="f6d42-229">Web/MVC</span></span>                               | <span data-ttu-id="f6d42-230">1.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-230">1.0</span></span>        |
| <span data-ttu-id="f6d42-231">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="f6d42-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="f6d42-232">webapp，razor</span><span class="sxs-lookup"><span data-stu-id="f6d42-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="f6d42-233">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-233">[C#]</span></span>         | <span data-ttu-id="f6d42-234">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="f6d42-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="f6d42-235">2.2、2。0</span><span class="sxs-lookup"><span data-stu-id="f6d42-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="f6d42-236">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="f6d42-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="f6d42-237">angular</span><span class="sxs-lookup"><span data-stu-id="f6d42-237">angular</span></span>](#spa)                 | <span data-ttu-id="f6d42-238">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-238">[C#]</span></span>         | <span data-ttu-id="f6d42-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f6d42-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f6d42-240">2.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-240">2.0</span></span>        |
| <span data-ttu-id="f6d42-241">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="f6d42-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="f6d42-242">反應</span><span class="sxs-lookup"><span data-stu-id="f6d42-242">react</span></span>](#spa)                   | <span data-ttu-id="f6d42-243">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-243">[C#]</span></span>         | <span data-ttu-id="f6d42-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f6d42-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f6d42-245">2.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-245">2.0</span></span>        |
| <span data-ttu-id="f6d42-246">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="f6d42-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="f6d42-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="f6d42-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="f6d42-248">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-248">[C#]</span></span>         | <span data-ttu-id="f6d42-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f6d42-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f6d42-250">2.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-250">2.0</span></span>        |
| <span data-ttu-id="f6d42-251">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="f6d42-251">Razor Class Library</span></span>                          | [<span data-ttu-id="f6d42-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="f6d42-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="f6d42-253">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-253">[C#]</span></span>         | <span data-ttu-id="f6d42-254">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="f6d42-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="f6d42-255">2.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-255">2.1</span></span>        |
| <span data-ttu-id="f6d42-256">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="f6d42-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="f6d42-257">webapi</span><span class="sxs-lookup"><span data-stu-id="f6d42-257">webapi</span></span>](#webapi)               | <span data-ttu-id="f6d42-258">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="f6d42-258">[C#], F#</span></span>     | <span data-ttu-id="f6d42-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="f6d42-259">Web/WebAPI</span></span>                            | <span data-ttu-id="f6d42-260">1.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-260">1.0</span></span>        |
| <span data-ttu-id="f6d42-261">ASP.NET Core gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="f6d42-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="f6d42-262">grpc</span><span class="sxs-lookup"><span data-stu-id="f6d42-262">grpc</span></span>](#web-others)             | <span data-ttu-id="f6d42-263">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6d42-263">[C#]</span></span>         | <span data-ttu-id="f6d42-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="f6d42-264">Web/gRPC</span></span>                              | <span data-ttu-id="f6d42-265">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-265">3.0</span></span>        |
| <span data-ttu-id="f6d42-266">dotnet .gitignore 檔</span><span class="sxs-lookup"><span data-stu-id="f6d42-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="f6d42-267">Config</span><span class="sxs-lookup"><span data-stu-id="f6d42-267">Config</span></span>                                | <span data-ttu-id="f6d42-268">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-268">3.0</span></span>        |
| <span data-ttu-id="f6d42-269">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="f6d42-269">global.json file</span></span>                             | [<span data-ttu-id="f6d42-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="f6d42-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="f6d42-271">Config</span><span class="sxs-lookup"><span data-stu-id="f6d42-271">Config</span></span>                                | <span data-ttu-id="f6d42-272">2.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-272">2.0</span></span>        |
| <span data-ttu-id="f6d42-273">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="f6d42-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="f6d42-274">Config</span><span class="sxs-lookup"><span data-stu-id="f6d42-274">Config</span></span>                                | <span data-ttu-id="f6d42-275">1.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-275">1.0</span></span>        |
| <span data-ttu-id="f6d42-276">Dotnet 本機工具資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="f6d42-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="f6d42-277">Config</span><span class="sxs-lookup"><span data-stu-id="f6d42-277">Config</span></span>                                | <span data-ttu-id="f6d42-278">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-278">3.0</span></span>        |
| <span data-ttu-id="f6d42-279">Web 組態</span><span class="sxs-lookup"><span data-stu-id="f6d42-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="f6d42-280">Config</span><span class="sxs-lookup"><span data-stu-id="f6d42-280">Config</span></span>                                | <span data-ttu-id="f6d42-281">1.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-281">1.0</span></span>        |
| <span data-ttu-id="f6d42-282">方案檔</span><span class="sxs-lookup"><span data-stu-id="f6d42-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="f6d42-283">解決方案</span><span class="sxs-lookup"><span data-stu-id="f6d42-283">Solution</span></span>                              | <span data-ttu-id="f6d42-284">1.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-284">1.0</span></span>        |
| <span data-ttu-id="f6d42-285">通訊協定緩衝區檔案</span><span class="sxs-lookup"><span data-stu-id="f6d42-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="f6d42-286">proto</span><span class="sxs-lookup"><span data-stu-id="f6d42-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="f6d42-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="f6d42-287">Web/gRPC</span></span>                              | <span data-ttu-id="f6d42-288">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="f6d42-289">選項</span><span class="sxs-lookup"><span data-stu-id="f6d42-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="f6d42-290">若指定的命令會導致建立範本，則顯示執行時會發生的情況摘要。</span><span class="sxs-lookup"><span data-stu-id="f6d42-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="f6d42-291">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="f6d42-292">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="f6d42-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="f6d42-293">當選擇的範本會覆寫輸出目錄中的現有檔案時，這是必要的。</span><span class="sxs-lookup"><span data-stu-id="f6d42-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f6d42-294">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="f6d42-294">Prints out help for the command.</span></span> <span data-ttu-id="f6d42-295">您可以針對 `dotnet new` 命令本身或任何範本叫用它。</span><span class="sxs-lookup"><span data-stu-id="f6d42-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="f6d42-296">例如，`dotnet new mvc --help`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="f6d42-297">從或提供的安裝範本 `PATH` 套件 `NUGET_ID` 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f6d42-298">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="f6d42-299">根據預設，會 `dotnet new` 傳遞 \* 代表最新穩定封裝版本的版本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="f6d42-300">請參閱[範例](#examples)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="f6d42-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="f6d42-301">當您執行此命令時，如果已安裝某個版本的範本，此範本將會更新為指定的版本，或如果未指定任何版本，則為最新的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="f6d42-302">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="f6d42-303">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="f6d42-304">如果未指定名稱，則會列出所有範本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="f6d42-305">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="f6d42-305">The language of the template to create.</span></span> <span data-ttu-id="f6d42-306">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f6d42-307">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f6d42-308">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="f6d42-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="f6d42-309">在這些情況下，請以引號括住語言參數值。</span><span class="sxs-lookup"><span data-stu-id="f6d42-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="f6d42-310">例如，`dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="f6d42-311">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6d42-311">The name for the created output.</span></span> <span data-ttu-id="f6d42-312">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6d42-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="f6d42-313">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="f6d42-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="f6d42-314">自 .NET Core 2.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f6d42-315">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="f6d42-315">Location to place the generated output.</span></span> <span data-ttu-id="f6d42-316">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="f6d42-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="f6d42-317">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-317">Filters templates based on available types.</span></span> <span data-ttu-id="f6d42-318">預先定義的值為 `project` 、 `item` 和 `other` 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-318">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="f6d42-319">在或提供的上卸載範本套件 `PATH` `NUGET_ID` 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f6d42-320">`<PATH|NUGET_ID>`未指定值時，會顯示所有目前已安裝的範本套件及其關聯的範本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="f6d42-321">指定時 `NUGET_ID` ，請勿包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="f6d42-322">如果您未指定此選項的參數，此命令會列出已安裝的範本和其相關詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f6d42-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f6d42-323">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f6d42-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="f6d42-324">例如， *C：/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp*可以使用，但包含資料夾中的 *./garciasoftware.consoletemplate.csharp*則不會。</span><span class="sxs-lookup"><span data-stu-id="f6d42-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="f6d42-325">請勿在您的範本路徑上包含最後終止的目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="f6d42-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="f6d42-326">檢查目前已安裝的範本套件是否有可用的更新，並加以安裝。</span><span class="sxs-lookup"><span data-stu-id="f6d42-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="f6d42-327">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="f6d42-328">檢查目前是否已安裝的範本套件是否有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="f6d42-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="f6d42-329">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="f6d42-330">範本選項</span><span class="sxs-lookup"><span data-stu-id="f6d42-330">Template options</span></span>

<span data-ttu-id="f6d42-331">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-331">Each project template may have additional options available.</span></span> <span data-ttu-id="f6d42-332">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="f6d42-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="f6d42-333">console</span><span class="sxs-lookup"><span data-stu-id="f6d42-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-334">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f6d42-335">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f6d42-336">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f6d42-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f6d42-337">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f6d42-337">SDK version</span></span> | <span data-ttu-id="f6d42-338">預設值</span><span class="sxs-lookup"><span data-stu-id="f6d42-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f6d42-339">3.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f6d42-340">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f6d42-341">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="f6d42-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f6d42-342">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="f6d42-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="f6d42-343">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="f6d42-343">Not supported for F#.</span></span> <span data-ttu-id="f6d42-344">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f6d42-345">如需預設 c # 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6d42-346">若已指定，則不會在專案建立期間執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="f6d42-347">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-347">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="f6d42-348">classlib</span><span class="sxs-lookup"><span data-stu-id="f6d42-348">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-349">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-349">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f6d42-350">值：`netcoreapp<version>` 建立 .NET Core 類別庫或 `netstandard<version>` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="f6d42-350">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="f6d42-351">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-351">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f6d42-352">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="f6d42-352">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f6d42-353">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="f6d42-353">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="f6d42-354">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="f6d42-354">Not supported for F#.</span></span> <span data-ttu-id="f6d42-355">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-355">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f6d42-356">如需預設 c # 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-356">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6d42-357">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-357">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="f6d42-358">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="f6d42-358">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-359">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-359">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f6d42-360">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-360">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="f6d42-361">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-361">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f6d42-362">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="f6d42-362">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f6d42-363">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="f6d42-363">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="f6d42-364">如需預設 c # 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-364">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6d42-365">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-365">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="f6d42-366">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="f6d42-366">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f6d42-367">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="f6d42-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f6d42-368">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="f6d42-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="f6d42-369">如需預設 c # 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6d42-370">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="f6d42-371">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="f6d42-371">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-372">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-372">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f6d42-373">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-373">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="f6d42-374">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-374">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f6d42-375">從產生的範本中排除*launchSettings.js* 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-375">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6d42-376">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-376">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="f6d42-377">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="f6d42-377">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-378">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-378">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f6d42-379">自 .NET Core 3.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-379">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f6d42-380">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f6d42-380">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f6d42-381">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f6d42-381">SDK version</span></span> | <span data-ttu-id="f6d42-382">預設值</span><span class="sxs-lookup"><span data-stu-id="f6d42-382">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f6d42-383">3.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-383">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f6d42-384">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-384">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="f6d42-385">使用[dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="f6d42-385">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6d42-386">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-386">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="f6d42-387">nunit</span><span class="sxs-lookup"><span data-stu-id="f6d42-387">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-388">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="f6d42-389">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f6d42-389">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f6d42-390">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f6d42-390">SDK version</span></span> | <span data-ttu-id="f6d42-391">預設值</span><span class="sxs-lookup"><span data-stu-id="f6d42-391">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f6d42-392">3.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-392">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f6d42-393">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-393">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f6d42-394">2.2</span><span class="sxs-lookup"><span data-stu-id="f6d42-394">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="f6d42-395">2.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-395">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="f6d42-396">使用[dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="f6d42-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6d42-397">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-397">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="f6d42-398">頁面</span><span class="sxs-lookup"><span data-stu-id="f6d42-398">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="f6d42-399">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f6d42-399">Namespace for the generated code.</span></span> <span data-ttu-id="f6d42-400">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-400">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="f6d42-401">建立不含 PageModel 的頁面。</span><span class="sxs-lookup"><span data-stu-id="f6d42-401">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="f6d42-402">viewimports.cshtml，proto</span><span class="sxs-lookup"><span data-stu-id="f6d42-402">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="f6d42-403">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f6d42-403">Namespace for the generated code.</span></span> <span data-ttu-id="f6d42-404">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-404">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="f6d42-405">blazorserver</span><span class="sxs-lookup"><span data-stu-id="f6d42-405">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f6d42-406">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="f6d42-406">The type of authentication to use.</span></span> <span data-ttu-id="f6d42-407">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="f6d42-407">The possible values are:</span></span>

  - <span data-ttu-id="f6d42-408">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-408">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f6d42-409">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-409">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="f6d42-410">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-410">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f6d42-411">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-411">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f6d42-412">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-412">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="f6d42-413">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-413">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f6d42-414">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="f6d42-414">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f6d42-415">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-415">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f6d42-416">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-416">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f6d42-417">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-417">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f6d42-418">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-418">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="f6d42-419">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-419">The reset password policy ID for this project.</span></span> <span data-ttu-id="f6d42-420">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-420">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="f6d42-421">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-421">The edit profile policy ID for this project.</span></span> <span data-ttu-id="f6d42-422">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-422">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f6d42-423">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="f6d42-423">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f6d42-424">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-424">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f6d42-425">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-425">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f6d42-426">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-426">The Client ID for this project.</span></span> <span data-ttu-id="f6d42-427">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-427">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f6d42-428">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-428">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f6d42-429">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="f6d42-429">The domain for the directory tenant.</span></span> <span data-ttu-id="f6d42-430">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-430">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f6d42-431">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-431">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f6d42-432">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-432">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f6d42-433">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-433">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f6d42-434">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-434">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="f6d42-435">應用程式的重新導向 URI 基底路徑中的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="f6d42-435">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f6d42-436">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f6d42-437">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-437">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f6d42-438">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="f6d42-438">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f6d42-439">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-439">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f6d42-440">從產生的範本中排除*launchSettings.js* 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-440">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f6d42-441">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f6d42-441">Turns off HTTPS.</span></span> <span data-ttu-id="f6d42-442">只有當 `Individual` 、 `IndividualB2C` 、 `SingleOrg` 或不是用於時 `MultiOrg` ， `--auth` 才會套用此選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-442">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f6d42-443">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="f6d42-443">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f6d42-444">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-444">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6d42-445">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-445">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="f6d42-446">Web</span><span class="sxs-lookup"><span data-stu-id="f6d42-446">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f6d42-447">從產生的範本中排除*launchSettings.js* 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-447">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-448">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-448">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f6d42-449">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-449">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f6d42-450">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f6d42-450">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f6d42-451">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f6d42-451">SDK version</span></span> | <span data-ttu-id="f6d42-452">預設值</span><span class="sxs-lookup"><span data-stu-id="f6d42-452">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f6d42-453">3.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-453">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f6d42-454">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-454">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f6d42-455">2.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-455">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="f6d42-456">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-456">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f6d42-457">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f6d42-457">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="f6d42-458">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="f6d42-458">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f6d42-459">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="f6d42-459">The type of authentication to use.</span></span> <span data-ttu-id="f6d42-460">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="f6d42-460">The possible values are:</span></span>

  - <span data-ttu-id="f6d42-461">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-461">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f6d42-462">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-462">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="f6d42-463">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-463">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f6d42-464">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-464">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f6d42-465">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-465">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="f6d42-466">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-466">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f6d42-467">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="f6d42-467">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f6d42-468">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-468">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f6d42-469">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-469">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f6d42-470">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-470">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f6d42-471">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-471">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="f6d42-472">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-472">The reset password policy ID for this project.</span></span> <span data-ttu-id="f6d42-473">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-473">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="f6d42-474">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-474">The edit profile policy ID for this project.</span></span> <span data-ttu-id="f6d42-475">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-475">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f6d42-476">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="f6d42-476">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f6d42-477">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-477">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f6d42-478">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-478">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f6d42-479">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-479">The Client ID for this project.</span></span> <span data-ttu-id="f6d42-480">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-480">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f6d42-481">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-481">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f6d42-482">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="f6d42-482">The domain for the directory tenant.</span></span> <span data-ttu-id="f6d42-483">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-483">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f6d42-484">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-484">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f6d42-485">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-485">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f6d42-486">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-486">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f6d42-487">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-487">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="f6d42-488">應用程式的重新導向 URI 基底路徑中的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="f6d42-488">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f6d42-489">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-489">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f6d42-490">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-490">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f6d42-491">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="f6d42-491">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f6d42-492">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-492">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f6d42-493">從產生的範本中排除*launchSettings.js* 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-493">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f6d42-494">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f6d42-494">Turns off HTTPS.</span></span> <span data-ttu-id="f6d42-495">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="f6d42-495">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f6d42-496">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="f6d42-496">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f6d42-497">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-497">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-498">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-498">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f6d42-499">自 .NET Core 3.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-499">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f6d42-500">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f6d42-500">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f6d42-501">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f6d42-501">SDK version</span></span> | <span data-ttu-id="f6d42-502">預設值</span><span class="sxs-lookup"><span data-stu-id="f6d42-502">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f6d42-503">3.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-503">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f6d42-504">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-504">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="f6d42-505">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-505">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="f6d42-506">在專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="f6d42-506">Includes BrowserLink in the project.</span></span> <span data-ttu-id="f6d42-507">無法在 .NET Core 2.2 和 3.1 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-507">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="f6d42-508">判斷專案是否設定為使用 Debug 組建中的[Razor 執行時間編譯](/aspnet/core/mvc/views/view-compilation#runtime-compilation)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-508">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="f6d42-509">自 .NET Core 3.1.201 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-509">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="f6d42-510">角度、反應</span><span class="sxs-lookup"><span data-stu-id="f6d42-510">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f6d42-511">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="f6d42-511">The type of authentication to use.</span></span> <span data-ttu-id="f6d42-512">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-512">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="f6d42-513">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="f6d42-513">The possible values are:</span></span>

  - <span data-ttu-id="f6d42-514">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-514">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f6d42-515">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-515">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f6d42-516">從產生的範本中排除*launchSettings.js* 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-516">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6d42-517">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-517">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f6d42-518">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f6d42-518">Turns off HTTPS.</span></span> <span data-ttu-id="f6d42-519">只有在驗證為時，才會套用此選項 `None` 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-519">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f6d42-520">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="f6d42-520">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f6d42-521">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-521">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f6d42-522">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-522">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-523">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-523">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f6d42-524">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-524">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f6d42-525">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f6d42-525">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f6d42-526">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f6d42-526">SDK version</span></span> | <span data-ttu-id="f6d42-527">預設值</span><span class="sxs-lookup"><span data-stu-id="f6d42-527">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f6d42-528">3.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-528">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f6d42-529">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-529">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f6d42-530">2.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-530">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="f6d42-531">reactredux</span><span class="sxs-lookup"><span data-stu-id="f6d42-531">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f6d42-532">從產生的範本中排除*launchSettings.js* 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-533">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f6d42-534">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f6d42-535">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f6d42-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f6d42-536">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f6d42-536">SDK version</span></span> | <span data-ttu-id="f6d42-537">預設值</span><span class="sxs-lookup"><span data-stu-id="f6d42-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f6d42-538">3.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-538">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f6d42-539">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-539">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f6d42-540">2.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-540">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="f6d42-541">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f6d42-542">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f6d42-542">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="f6d42-543">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="f6d42-543">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6d42-544">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-544">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="f6d42-545">支援將傳統的 Razor 頁面和 Views 新增至此程式庫的元件。</span><span class="sxs-lookup"><span data-stu-id="f6d42-545">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="f6d42-546">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f6d42-546">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="f6d42-547">webapi</span><span class="sxs-lookup"><span data-stu-id="f6d42-547">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f6d42-548">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="f6d42-548">The type of authentication to use.</span></span> <span data-ttu-id="f6d42-549">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="f6d42-549">The possible values are:</span></span>

  - <span data-ttu-id="f6d42-550">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-550">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f6d42-551">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f6d42-552">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f6d42-553">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-553">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f6d42-554">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="f6d42-554">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f6d42-555">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-555">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f6d42-556">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-556">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f6d42-557">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-557">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f6d42-558">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-558">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f6d42-559">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="f6d42-559">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f6d42-560">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-560">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f6d42-561">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-561">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f6d42-562">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-562">The Client ID for this project.</span></span> <span data-ttu-id="f6d42-563">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f6d42-564">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-564">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f6d42-565">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="f6d42-565">The domain for the directory tenant.</span></span> <span data-ttu-id="f6d42-566">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-566">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f6d42-567">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-567">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f6d42-568">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6d42-568">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f6d42-569">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="f6d42-569">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f6d42-570">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-570">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f6d42-571">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="f6d42-571">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f6d42-572">僅適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-572">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f6d42-573">從產生的範本中排除*launchSettings.js* 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-573">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f6d42-574">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="f6d42-574">Turns off HTTPS.</span></span> <span data-ttu-id="f6d42-575">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="f6d42-575">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="f6d42-576">只有當 `IndividualB2C` 或未用於驗證時，此選項才適用 `SingleOrg` 。</span><span class="sxs-lookup"><span data-stu-id="f6d42-576">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f6d42-577">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="f6d42-577">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f6d42-578">僅適用于 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6d42-578">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6d42-579">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d42-579">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f6d42-580">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="f6d42-580">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f6d42-581">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="f6d42-581">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f6d42-582">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f6d42-582">SDK version</span></span> | <span data-ttu-id="f6d42-583">預設值</span><span class="sxs-lookup"><span data-stu-id="f6d42-583">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f6d42-584">3.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-584">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f6d42-585">3.0</span><span class="sxs-lookup"><span data-stu-id="f6d42-585">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f6d42-586">2.1</span><span class="sxs-lookup"><span data-stu-id="f6d42-586">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="f6d42-587">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f6d42-587">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="f6d42-588">globaljson</span><span class="sxs-lookup"><span data-stu-id="f6d42-588">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="f6d42-589">指定要在檔案*global.js*中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-589">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="f6d42-590">範例</span><span class="sxs-lookup"><span data-stu-id="f6d42-590">Examples</span></span>

- <span data-ttu-id="f6d42-591">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="f6d42-591">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="f6d42-592">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="f6d42-592">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="f6d42-593">在指定的目錄中建立 .NET Standard 類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="f6d42-593">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="f6d42-594">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="f6d42-594">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="f6d42-595">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="f6d42-595">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="f6d42-596">列出適用于單一頁面應用程式的所有範本 (SPA) 範本：</span><span class="sxs-lookup"><span data-stu-id="f6d42-596">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="f6d42-597">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-597">List all templates matching the *we* substring.</span></span> <span data-ttu-id="f6d42-598">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="f6d42-598">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="f6d42-599">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-599">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="f6d42-600">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="f6d42-600">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="f6d42-601">安裝適用于 ASP.NET Core 的 SPA 範本2.0 版：</span><span class="sxs-lookup"><span data-stu-id="f6d42-601">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="f6d42-602">列出已安裝的範本和其詳細資料，包括如何將它們卸載：</span><span class="sxs-lookup"><span data-stu-id="f6d42-602">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="f6d42-603">在目前目錄中建立*global.js* ，將 SDK 版本設定為3.1.101：</span><span class="sxs-lookup"><span data-stu-id="f6d42-603">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="f6d42-604">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6d42-604">See also</span></span>

- [<span data-ttu-id="f6d42-605">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="f6d42-605">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="f6d42-606">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="f6d42-606">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- <span data-ttu-id="f6d42-607">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="f6d42-607">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="f6d42-608">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="f6d42-608">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
