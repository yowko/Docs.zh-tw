---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
ms.date: 04/10/2020
ms.openlocfilehash: 1544f519f2a5f6a1a6e042c1db720eff45f5d98c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442237"
---
# <a name="dotnet-new"></a><span data-ttu-id="d62d1-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d62d1-103">dotnet new</span></span>

<span data-ttu-id="d62d1-104">**本文適用于：** ✔️ .net CORE 2.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="d62d1-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d62d1-105">Name</span><span class="sxs-lookup"><span data-stu-id="d62d1-105">Name</span></span>

<span data-ttu-id="d62d1-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="d62d1-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d62d1-107">概要</span><span class="sxs-lookup"><span data-stu-id="d62d1-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="d62d1-108">說明</span><span class="sxs-lookup"><span data-stu-id="d62d1-108">Description</span></span>

<span data-ttu-id="d62d1-109">`dotnet new`命令會根據範本建立 .Net Core 專案或其他成品。</span><span class="sxs-lookup"><span data-stu-id="d62d1-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="d62d1-110">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="d62d1-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="d62d1-111">隱含還原</span><span class="sxs-lookup"><span data-stu-id="d62d1-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="d62d1-112">引數</span><span class="sxs-lookup"><span data-stu-id="d62d1-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="d62d1-113">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="d62d1-114">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="d62d1-115">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="d62d1-116">您可以執行 `dotnet new --list` 或 `dotnet new -l` 來查看所有已安裝的範本清單。</span><span class="sxs-lookup"><span data-stu-id="d62d1-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="d62d1-117">如果 `TEMPLATE` 值不完全符合所傳回資料表之 [樣板**Templates** ] 或 [**簡短名稱**] 資料行中的文字，則會在這兩個數據行上執行子字串相符。</span><span class="sxs-lookup"><span data-stu-id="d62d1-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="d62d1-118">從 .NET Core 3.0 SDK 開始，當您 `dotnet new` 在下列情況下叫用命令時，CLI 會在 NuGet.org 中搜尋範本：</span><span class="sxs-lookup"><span data-stu-id="d62d1-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="d62d1-119">如果 CLI 在叫用時找不到相符的範本 `dotnet new` ，甚至不是部分。</span><span class="sxs-lookup"><span data-stu-id="d62d1-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="d62d1-120">如果有較新版本的範本可用，則為。</span><span class="sxs-lookup"><span data-stu-id="d62d1-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="d62d1-121">在此情況下，會建立專案或成品，但 CLI 會警告您有關範本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="d62d1-122">下表顯示隨 .NET Core SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="d62d1-123">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="d62d1-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="d62d1-124">按一下 [簡短名稱] 連結，以查看特定的範本選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="d62d1-125">範本</span><span class="sxs-lookup"><span data-stu-id="d62d1-125">Templates</span></span>                                    | <span data-ttu-id="d62d1-126">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="d62d1-126">Short name</span></span>                      | <span data-ttu-id="d62d1-127">Language</span><span class="sxs-lookup"><span data-stu-id="d62d1-127">Language</span></span>     | <span data-ttu-id="d62d1-128">標籤</span><span class="sxs-lookup"><span data-stu-id="d62d1-128">Tags</span></span>                                  | <span data-ttu-id="d62d1-129">引導</span><span class="sxs-lookup"><span data-stu-id="d62d1-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="d62d1-130">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="d62d1-130">Console Application</span></span>                          | [<span data-ttu-id="d62d1-131">控制</span><span class="sxs-lookup"><span data-stu-id="d62d1-131">console</span></span>](#console)             | <span data-ttu-id="d62d1-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d62d1-132">[C#], F#, VB</span></span> | <span data-ttu-id="d62d1-133">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="d62d1-133">Common/Console</span></span>                        | <span data-ttu-id="d62d1-134">1.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-134">1.0</span></span>        |
| <span data-ttu-id="d62d1-135">類別庫</span><span class="sxs-lookup"><span data-stu-id="d62d1-135">Class library</span></span>                                | [<span data-ttu-id="d62d1-136">classlib</span><span class="sxs-lookup"><span data-stu-id="d62d1-136">classlib</span></span>](#classlib)           | <span data-ttu-id="d62d1-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d62d1-137">[C#], F#, VB</span></span> | <span data-ttu-id="d62d1-138">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="d62d1-138">Common/Library</span></span>                        | <span data-ttu-id="d62d1-139">1.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-139">1.0</span></span>        |
| <span data-ttu-id="d62d1-140">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="d62d1-140">WPF Application</span></span>                              | [<span data-ttu-id="d62d1-141">wpf</span><span class="sxs-lookup"><span data-stu-id="d62d1-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="d62d1-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-142">[C#]</span></span>         | <span data-ttu-id="d62d1-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="d62d1-143">Common/WPF</span></span>                            | <span data-ttu-id="d62d1-144">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-144">3.0</span></span>        |
| <span data-ttu-id="d62d1-145">WPF 類別庫</span><span class="sxs-lookup"><span data-stu-id="d62d1-145">WPF Class library</span></span>                            | [<span data-ttu-id="d62d1-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="d62d1-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="d62d1-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-147">[C#]</span></span>         | <span data-ttu-id="d62d1-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="d62d1-148">Common/WPF</span></span>                            | <span data-ttu-id="d62d1-149">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-149">3.0</span></span>        |
| <span data-ttu-id="d62d1-150">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="d62d1-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="d62d1-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="d62d1-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="d62d1-152">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-152">[C#]</span></span>         | <span data-ttu-id="d62d1-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="d62d1-153">Common/WPF</span></span>                            | <span data-ttu-id="d62d1-154">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-154">3.0</span></span>        |
| <span data-ttu-id="d62d1-155">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="d62d1-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="d62d1-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="d62d1-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="d62d1-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-157">[C#]</span></span>         | <span data-ttu-id="d62d1-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="d62d1-158">Common/WPF</span></span>                            | <span data-ttu-id="d62d1-159">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-159">3.0</span></span>        |
| <span data-ttu-id="d62d1-160">Windows Forms （WinForms）應用程式</span><span class="sxs-lookup"><span data-stu-id="d62d1-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="d62d1-161">winforms</span><span class="sxs-lookup"><span data-stu-id="d62d1-161">winforms</span></span>](#winforms)           | <span data-ttu-id="d62d1-162">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-162">[C#]</span></span>         | <span data-ttu-id="d62d1-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="d62d1-163">Common/WinForms</span></span>                       | <span data-ttu-id="d62d1-164">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-164">3.0</span></span>        |
| <span data-ttu-id="d62d1-165">Windows Forms （WinForms）類別庫</span><span class="sxs-lookup"><span data-stu-id="d62d1-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="d62d1-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="d62d1-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="d62d1-167">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-167">[C#]</span></span>         | <span data-ttu-id="d62d1-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="d62d1-168">Common/WinForms</span></span>                       | <span data-ttu-id="d62d1-169">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-169">3.0</span></span>        |
| <span data-ttu-id="d62d1-170">背景工作服務</span><span class="sxs-lookup"><span data-stu-id="d62d1-170">Worker Service</span></span>                               | [<span data-ttu-id="d62d1-171">工作</span><span class="sxs-lookup"><span data-stu-id="d62d1-171">worker</span></span>](#web-others)           | <span data-ttu-id="d62d1-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-172">[C#]</span></span>         | <span data-ttu-id="d62d1-173">一般/背景工作/Web</span><span class="sxs-lookup"><span data-stu-id="d62d1-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="d62d1-174">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-174">3.0</span></span>        |
| <span data-ttu-id="d62d1-175">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="d62d1-175">Unit Test Project</span></span>                            | [<span data-ttu-id="d62d1-176">mstest.exe</span><span class="sxs-lookup"><span data-stu-id="d62d1-176">mstest</span></span>](#test)                 | <span data-ttu-id="d62d1-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d62d1-177">[C#], F#, VB</span></span> | <span data-ttu-id="d62d1-178">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="d62d1-178">Test/MSTest</span></span>                           | <span data-ttu-id="d62d1-179">1.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-179">1.0</span></span>        |
| <span data-ttu-id="d62d1-180">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="d62d1-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="d62d1-181">nunit</span><span class="sxs-lookup"><span data-stu-id="d62d1-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="d62d1-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d62d1-182">[C#], F#, VB</span></span> | <span data-ttu-id="d62d1-183">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="d62d1-183">Test/NUnit</span></span>                            | <span data-ttu-id="d62d1-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="d62d1-184">2.1.400</span></span>    |
| <span data-ttu-id="d62d1-185">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="d62d1-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="d62d1-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d62d1-186">[C#], F#, VB</span></span> | <span data-ttu-id="d62d1-187">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="d62d1-187">Test/NUnit</span></span>                            | <span data-ttu-id="d62d1-188">2.2</span><span class="sxs-lookup"><span data-stu-id="d62d1-188">2.2</span></span>        |
| <span data-ttu-id="d62d1-189">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="d62d1-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="d62d1-190">xunit</span><span class="sxs-lookup"><span data-stu-id="d62d1-190">xunit</span></span>](#test)                  | <span data-ttu-id="d62d1-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d62d1-191">[C#], F#, VB</span></span> | <span data-ttu-id="d62d1-192">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="d62d1-192">Test/xUnit</span></span>                            | <span data-ttu-id="d62d1-193">1.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-193">1.0</span></span>        |
| <span data-ttu-id="d62d1-194">Razor 元件</span><span class="sxs-lookup"><span data-stu-id="d62d1-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="d62d1-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-195">[C#]</span></span>         | <span data-ttu-id="d62d1-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d62d1-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="d62d1-197">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-197">3.0</span></span>        |
| <span data-ttu-id="d62d1-198">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="d62d1-198">Razor Page</span></span>                                   | [<span data-ttu-id="d62d1-199">本頁</span><span class="sxs-lookup"><span data-stu-id="d62d1-199">page</span></span>](#page)                   | <span data-ttu-id="d62d1-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-200">[C#]</span></span>         | <span data-ttu-id="d62d1-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d62d1-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="d62d1-202">2.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-202">2.0</span></span>        |
| <span data-ttu-id="d62d1-203">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="d62d1-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="d62d1-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="d62d1-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="d62d1-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-205">[C#]</span></span>         | <span data-ttu-id="d62d1-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d62d1-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="d62d1-207">2.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-207">2.0</span></span>        |
| <span data-ttu-id="d62d1-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="d62d1-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="d62d1-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-209">[C#]</span></span>         | <span data-ttu-id="d62d1-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d62d1-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="d62d1-211">2.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-211">2.0</span></span>        |
| <span data-ttu-id="d62d1-212">Blazor 伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="d62d1-212">Blazor Server App</span></span>                            | [<span data-ttu-id="d62d1-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="d62d1-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="d62d1-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-214">[C#]</span></span>         | <span data-ttu-id="d62d1-215">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="d62d1-215">Web/Blazor</span></span>                            | <span data-ttu-id="d62d1-216">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-216">3.0</span></span>        |
| <span data-ttu-id="d62d1-217">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d62d1-217">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="d62d1-218">網路</span><span class="sxs-lookup"><span data-stu-id="d62d1-218">web</span></span>](#web)                     | <span data-ttu-id="d62d1-219">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="d62d1-219">[C#], F#</span></span>     | <span data-ttu-id="d62d1-220">Web/空白</span><span class="sxs-lookup"><span data-stu-id="d62d1-220">Web/Empty</span></span>                             | <span data-ttu-id="d62d1-221">1.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-221">1.0</span></span>        |
| <span data-ttu-id="d62d1-222">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="d62d1-222">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="d62d1-223">mvc</span><span class="sxs-lookup"><span data-stu-id="d62d1-223">mvc</span></span>](#web-options)             | <span data-ttu-id="d62d1-224">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="d62d1-224">[C#], F#</span></span>     | <span data-ttu-id="d62d1-225">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="d62d1-225">Web/MVC</span></span>                               | <span data-ttu-id="d62d1-226">1.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-226">1.0</span></span>        |
| <span data-ttu-id="d62d1-227">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="d62d1-227">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="d62d1-228">webapp，razor</span><span class="sxs-lookup"><span data-stu-id="d62d1-228">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="d62d1-229">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-229">[C#]</span></span>         | <span data-ttu-id="d62d1-230">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="d62d1-230">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="d62d1-231">2.2、2。0</span><span class="sxs-lookup"><span data-stu-id="d62d1-231">2.2, 2.0</span></span>   |
| <span data-ttu-id="d62d1-232">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="d62d1-232">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="d62d1-233">angular</span><span class="sxs-lookup"><span data-stu-id="d62d1-233">angular</span></span>](#spa)                 | <span data-ttu-id="d62d1-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-234">[C#]</span></span>         | <span data-ttu-id="d62d1-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d62d1-235">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d62d1-236">2.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-236">2.0</span></span>        |
| <span data-ttu-id="d62d1-237">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="d62d1-237">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="d62d1-238">反應</span><span class="sxs-lookup"><span data-stu-id="d62d1-238">react</span></span>](#spa)                   | <span data-ttu-id="d62d1-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-239">[C#]</span></span>         | <span data-ttu-id="d62d1-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d62d1-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d62d1-241">2.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-241">2.0</span></span>        |
| <span data-ttu-id="d62d1-242">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="d62d1-242">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="d62d1-243">reactredux</span><span class="sxs-lookup"><span data-stu-id="d62d1-243">reactredux</span></span>](#reactredux)       | <span data-ttu-id="d62d1-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-244">[C#]</span></span>         | <span data-ttu-id="d62d1-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d62d1-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d62d1-246">2.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-246">2.0</span></span>        |
| <span data-ttu-id="d62d1-247">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="d62d1-247">Razor Class Library</span></span>                          | [<span data-ttu-id="d62d1-248">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="d62d1-248">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="d62d1-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-249">[C#]</span></span>         | <span data-ttu-id="d62d1-250">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="d62d1-250">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="d62d1-251">2.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-251">2.1</span></span>        |
| <span data-ttu-id="d62d1-252">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="d62d1-252">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="d62d1-253">webapi</span><span class="sxs-lookup"><span data-stu-id="d62d1-253">webapi</span></span>](#webapi)               | <span data-ttu-id="d62d1-254">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="d62d1-254">[C#], F#</span></span>     | <span data-ttu-id="d62d1-255">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="d62d1-255">Web/WebAPI</span></span>                            | <span data-ttu-id="d62d1-256">1.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-256">1.0</span></span>        |
| <span data-ttu-id="d62d1-257">ASP.NET Core gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="d62d1-257">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="d62d1-258">grpc</span><span class="sxs-lookup"><span data-stu-id="d62d1-258">grpc</span></span>](#web-others)             | <span data-ttu-id="d62d1-259">[C#]</span><span class="sxs-lookup"><span data-stu-id="d62d1-259">[C#]</span></span>         | <span data-ttu-id="d62d1-260">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="d62d1-260">Web/gRPC</span></span>                              | <span data-ttu-id="d62d1-261">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-261">3.0</span></span>        |
| <span data-ttu-id="d62d1-262">dotnet .gitignore 檔</span><span class="sxs-lookup"><span data-stu-id="d62d1-262">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="d62d1-263">Config</span><span class="sxs-lookup"><span data-stu-id="d62d1-263">Config</span></span>                                | <span data-ttu-id="d62d1-264">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-264">3.0</span></span>        |
| <span data-ttu-id="d62d1-265">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="d62d1-265">global.json file</span></span>                             | [<span data-ttu-id="d62d1-266">globaljson</span><span class="sxs-lookup"><span data-stu-id="d62d1-266">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="d62d1-267">Config</span><span class="sxs-lookup"><span data-stu-id="d62d1-267">Config</span></span>                                | <span data-ttu-id="d62d1-268">2.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-268">2.0</span></span>        |
| <span data-ttu-id="d62d1-269">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="d62d1-269">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="d62d1-270">Config</span><span class="sxs-lookup"><span data-stu-id="d62d1-270">Config</span></span>                                | <span data-ttu-id="d62d1-271">1.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-271">1.0</span></span>        |
| <span data-ttu-id="d62d1-272">Dotnet 本機工具資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="d62d1-272">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="d62d1-273">Config</span><span class="sxs-lookup"><span data-stu-id="d62d1-273">Config</span></span>                                | <span data-ttu-id="d62d1-274">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-274">3.0</span></span>        |
| <span data-ttu-id="d62d1-275">Web 組態</span><span class="sxs-lookup"><span data-stu-id="d62d1-275">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="d62d1-276">Config</span><span class="sxs-lookup"><span data-stu-id="d62d1-276">Config</span></span>                                | <span data-ttu-id="d62d1-277">1.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-277">1.0</span></span>        |
| <span data-ttu-id="d62d1-278">方案檔</span><span class="sxs-lookup"><span data-stu-id="d62d1-278">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="d62d1-279">解決方法</span><span class="sxs-lookup"><span data-stu-id="d62d1-279">Solution</span></span>                              | <span data-ttu-id="d62d1-280">1.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-280">1.0</span></span>        |
| <span data-ttu-id="d62d1-281">通訊協定緩衝區檔案</span><span class="sxs-lookup"><span data-stu-id="d62d1-281">Protocol Buffer File</span></span>                         | [<span data-ttu-id="d62d1-282">proto</span><span class="sxs-lookup"><span data-stu-id="d62d1-282">proto</span></span>](#namespace)             |              | <span data-ttu-id="d62d1-283">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="d62d1-283">Web/gRPC</span></span>                              | <span data-ttu-id="d62d1-284">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-284">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="d62d1-285">選項</span><span class="sxs-lookup"><span data-stu-id="d62d1-285">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="d62d1-286">若指定的命令會導致建立範本，則顯示執行時會發生的情況摘要。</span><span class="sxs-lookup"><span data-stu-id="d62d1-286">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="d62d1-287">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-287">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="d62d1-288">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="d62d1-288">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="d62d1-289">當選擇的範本會覆寫輸出目錄中的現有檔案時，這是必要的。</span><span class="sxs-lookup"><span data-stu-id="d62d1-289">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d62d1-290">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="d62d1-290">Prints out help for the command.</span></span> <span data-ttu-id="d62d1-291">您可以針對 `dotnet new` 命令本身或任何範本叫用它。</span><span class="sxs-lookup"><span data-stu-id="d62d1-291">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="d62d1-292">例如： `dotnet new mvc --help` 。</span><span class="sxs-lookup"><span data-stu-id="d62d1-292">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="d62d1-293">從或提供的安裝範本 `PATH` 套件 `NUGET_ID` 。</span><span class="sxs-lookup"><span data-stu-id="d62d1-293">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d62d1-294">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-294">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="d62d1-295">根據預設，會 `dotnet new` 傳遞 \* 代表最新穩定封裝版本的版本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-295">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="d62d1-296">請參閱[範例](#examples)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="d62d1-296">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="d62d1-297">當您執行此命令時，如果已安裝某個版本的範本，此範本將會更新為指定的版本，或如果未指定任何版本，則為最新的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-297">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="d62d1-298">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-298">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="d62d1-299">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-299">Lists templates containing the specified name.</span></span> <span data-ttu-id="d62d1-300">如果未指定名稱，則會列出所有範本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-300">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="d62d1-301">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="d62d1-301">The language of the template to create.</span></span> <span data-ttu-id="d62d1-302">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-302">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="d62d1-303">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-303">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d62d1-304">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="d62d1-304">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="d62d1-305">在這些情況下，請以引號括住語言參數值。</span><span class="sxs-lookup"><span data-stu-id="d62d1-305">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="d62d1-306">例如： `dotnet new console -lang "F#"` 。</span><span class="sxs-lookup"><span data-stu-id="d62d1-306">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="d62d1-307">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="d62d1-307">The name for the created output.</span></span> <span data-ttu-id="d62d1-308">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d62d1-308">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="d62d1-309">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="d62d1-309">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="d62d1-310">自 .NET Core 2.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-310">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="d62d1-311">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="d62d1-311">Location to place the generated output.</span></span> <span data-ttu-id="d62d1-312">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="d62d1-312">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="d62d1-313">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-313">Filters templates based on available types.</span></span> <span data-ttu-id="d62d1-314">預先定義的值為 `project` 、 `item` 和 `other` 。</span><span class="sxs-lookup"><span data-stu-id="d62d1-314">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="d62d1-315">在或提供的上卸載範本套件 `PATH` `NUGET_ID` 。</span><span class="sxs-lookup"><span data-stu-id="d62d1-315">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d62d1-316">`<PATH|NUGET_ID>`未指定值時，會顯示所有目前已安裝的範本套件及其關聯的範本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-316">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="d62d1-317">指定時 `NUGET_ID` ，請勿包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-317">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="d62d1-318">如果您未指定此選項的參數，此命令會列出已安裝的範本和其相關詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d62d1-318">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d62d1-319">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="d62d1-319">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="d62d1-320">例如， *C：/Users/ \< USER>/documents/templates/garciasoftware.consoletemplate.csharp*可正常執行，但包含資料夾中的 *./garciasoftware.consoletemplate.csharp*則不會。</span><span class="sxs-lookup"><span data-stu-id="d62d1-320">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="d62d1-321">請勿在您的範本路徑上包含最後終止的目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="d62d1-321">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="d62d1-322">檢查目前已安裝的範本套件是否有可用的更新，並加以安裝。</span><span class="sxs-lookup"><span data-stu-id="d62d1-322">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="d62d1-323">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-323">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="d62d1-324">檢查目前是否已安裝的範本套件是否有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="d62d1-324">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="d62d1-325">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-325">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="d62d1-326">範本選項</span><span class="sxs-lookup"><span data-stu-id="d62d1-326">Template options</span></span>

<span data-ttu-id="d62d1-327">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-327">Each project template may have additional options available.</span></span> <span data-ttu-id="d62d1-328">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="d62d1-328">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="d62d1-329">console</span><span class="sxs-lookup"><span data-stu-id="d62d1-329">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-330">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-330">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d62d1-331">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-331">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d62d1-332">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="d62d1-332">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d62d1-333">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="d62d1-333">SDK version</span></span> | <span data-ttu-id="d62d1-334">預設值</span><span class="sxs-lookup"><span data-stu-id="d62d1-334">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d62d1-335">3.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-335">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d62d1-336">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-336">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d62d1-337">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d62d1-337">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d62d1-338">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="d62d1-338">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="d62d1-339">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="d62d1-339">Not supported for F#.</span></span> <span data-ttu-id="d62d1-340">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-340">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d62d1-341">如需預設 c # 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-341">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d62d1-342">若已指定，則不會在專案建立期間執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-342">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="d62d1-343">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-343">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="d62d1-344">classlib</span><span class="sxs-lookup"><span data-stu-id="d62d1-344">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-345">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-345">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d62d1-346">值：`netcoreapp<version>` 建立 .NET Core 類別庫或 `netstandard<version>` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="d62d1-346">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="d62d1-347">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-347">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d62d1-348">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d62d1-348">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d62d1-349">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="d62d1-349">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="d62d1-350">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="d62d1-350">Not supported for F#.</span></span> <span data-ttu-id="d62d1-351">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-351">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d62d1-352">如需預設 c # 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-352">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d62d1-353">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-353">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="d62d1-354">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="d62d1-354">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-355">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-355">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d62d1-356">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-356">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="d62d1-357">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-357">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d62d1-358">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d62d1-358">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d62d1-359">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="d62d1-359">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="d62d1-360">如需預設 c # 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-360">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d62d1-361">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-361">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="d62d1-362">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="d62d1-362">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d62d1-363">`LangVersion`在建立的專案檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d62d1-363">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d62d1-364">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="d62d1-364">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="d62d1-365">如需預設 c # 版本的清單，請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-365">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d62d1-366">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-366">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="d62d1-367">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="d62d1-367">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-368">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-368">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d62d1-369">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-369">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="d62d1-370">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-370">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d62d1-371">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="d62d1-371">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d62d1-372">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-372">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="d62d1-373">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="d62d1-373">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-374">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-374">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d62d1-375">自 .NET Core 3.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-375">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d62d1-376">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="d62d1-376">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d62d1-377">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="d62d1-377">SDK version</span></span> | <span data-ttu-id="d62d1-378">預設值</span><span class="sxs-lookup"><span data-stu-id="d62d1-378">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d62d1-379">3.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-379">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d62d1-380">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-380">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="d62d1-381">使用[dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="d62d1-381">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d62d1-382">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-382">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="d62d1-383">nunit</span><span class="sxs-lookup"><span data-stu-id="d62d1-383">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-384">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-384">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="d62d1-385">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="d62d1-385">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d62d1-386">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="d62d1-386">SDK version</span></span> | <span data-ttu-id="d62d1-387">預設值</span><span class="sxs-lookup"><span data-stu-id="d62d1-387">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d62d1-388">3.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-388">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d62d1-389">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-389">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d62d1-390">2.2</span><span class="sxs-lookup"><span data-stu-id="d62d1-390">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="d62d1-391">2.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-391">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="d62d1-392">使用[dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="d62d1-392">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d62d1-393">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-393">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="d62d1-394">頁面</span><span class="sxs-lookup"><span data-stu-id="d62d1-394">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="d62d1-395">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d62d1-395">Namespace for the generated code.</span></span> <span data-ttu-id="d62d1-396">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-396">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="d62d1-397">建立不含 PageModel 的頁面。</span><span class="sxs-lookup"><span data-stu-id="d62d1-397">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="d62d1-398">viewimports.cshtml，proto</span><span class="sxs-lookup"><span data-stu-id="d62d1-398">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="d62d1-399">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d62d1-399">Namespace for the generated code.</span></span> <span data-ttu-id="d62d1-400">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-400">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="d62d1-401">blazorserver</span><span class="sxs-lookup"><span data-stu-id="d62d1-401">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d62d1-402">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="d62d1-402">The type of authentication to use.</span></span> <span data-ttu-id="d62d1-403">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="d62d1-403">The possible values are:</span></span>

  - <span data-ttu-id="d62d1-404">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-404">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d62d1-405">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-405">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="d62d1-406">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-406">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d62d1-407">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-407">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d62d1-408">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-408">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="d62d1-409">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-409">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d62d1-410">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="d62d1-410">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d62d1-411">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d62d1-412">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d62d1-413">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-413">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d62d1-414">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-414">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="d62d1-415">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-415">The reset password policy ID for this project.</span></span> <span data-ttu-id="d62d1-416">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-416">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="d62d1-417">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-417">The edit profile policy ID for this project.</span></span> <span data-ttu-id="d62d1-418">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-418">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d62d1-419">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="d62d1-419">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d62d1-420">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-420">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d62d1-421">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-421">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d62d1-422">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-422">The Client ID for this project.</span></span> <span data-ttu-id="d62d1-423">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-423">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d62d1-424">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-424">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d62d1-425">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="d62d1-425">The domain for the directory tenant.</span></span> <span data-ttu-id="d62d1-426">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-426">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d62d1-427">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-427">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d62d1-428">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-428">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d62d1-429">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-429">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d62d1-430">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-430">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="d62d1-431">應用程式的重新導向 URI 基底路徑中的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="d62d1-431">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d62d1-432">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-432">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d62d1-433">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-433">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d62d1-434">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="d62d1-434">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d62d1-435">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-435">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d62d1-436">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="d62d1-436">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d62d1-437">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="d62d1-437">Turns off HTTPS.</span></span> <span data-ttu-id="d62d1-438">只有當 `Individual` 、 `IndividualB2C` 、 `SingleOrg` 或不是用於時 `MultiOrg` ， `--auth` 才會套用此選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-438">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d62d1-439">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="d62d1-439">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d62d1-440">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-440">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d62d1-441">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-441">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="d62d1-442">Web</span><span class="sxs-lookup"><span data-stu-id="d62d1-442">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d62d1-443">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="d62d1-443">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-444">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-444">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d62d1-445">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-445">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d62d1-446">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="d62d1-446">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d62d1-447">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="d62d1-447">SDK version</span></span> | <span data-ttu-id="d62d1-448">預設值</span><span class="sxs-lookup"><span data-stu-id="d62d1-448">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d62d1-449">3.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-449">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d62d1-450">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-450">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d62d1-451">2.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-451">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="d62d1-452">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-452">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d62d1-453">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="d62d1-453">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="d62d1-454">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="d62d1-454">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d62d1-455">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="d62d1-455">The type of authentication to use.</span></span> <span data-ttu-id="d62d1-456">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="d62d1-456">The possible values are:</span></span>

  - <span data-ttu-id="d62d1-457">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-457">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d62d1-458">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-458">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="d62d1-459">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-459">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d62d1-460">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-460">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d62d1-461">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-461">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="d62d1-462">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-462">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d62d1-463">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="d62d1-463">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d62d1-464">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-464">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d62d1-465">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-465">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d62d1-466">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-466">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d62d1-467">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-467">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="d62d1-468">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-468">The reset password policy ID for this project.</span></span> <span data-ttu-id="d62d1-469">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-469">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="d62d1-470">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-470">The edit profile policy ID for this project.</span></span> <span data-ttu-id="d62d1-471">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-471">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d62d1-472">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="d62d1-472">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d62d1-473">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-473">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d62d1-474">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-474">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d62d1-475">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-475">The Client ID for this project.</span></span> <span data-ttu-id="d62d1-476">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-476">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d62d1-477">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-477">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d62d1-478">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="d62d1-478">The domain for the directory tenant.</span></span> <span data-ttu-id="d62d1-479">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d62d1-480">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-480">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d62d1-481">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-481">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d62d1-482">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-482">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d62d1-483">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-483">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="d62d1-484">應用程式的重新導向 URI 基底路徑中的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="d62d1-484">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d62d1-485">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-485">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d62d1-486">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-486">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d62d1-487">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="d62d1-487">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d62d1-488">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-488">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d62d1-489">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="d62d1-489">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d62d1-490">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="d62d1-490">Turns off HTTPS.</span></span> <span data-ttu-id="d62d1-491">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="d62d1-491">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d62d1-492">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="d62d1-492">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d62d1-493">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-493">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-494">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-494">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d62d1-495">自 .NET Core 3.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-495">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d62d1-496">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="d62d1-496">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d62d1-497">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="d62d1-497">SDK version</span></span> | <span data-ttu-id="d62d1-498">預設值</span><span class="sxs-lookup"><span data-stu-id="d62d1-498">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d62d1-499">3.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-499">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d62d1-500">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-500">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="d62d1-501">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-501">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="d62d1-502">在專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="d62d1-502">Includes BrowserLink in the project.</span></span> <span data-ttu-id="d62d1-503">無法在 .NET Core 2.2 和 3.1 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-503">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="d62d1-504">判斷專案是否設定為使用 Debug 組建中的[Razor 執行時間編譯](/aspnet/core/mvc/views/view-compilation#runtime-compilation)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-504">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="d62d1-505">自 .NET Core 3.1.201 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-505">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="d62d1-506">角度、反應</span><span class="sxs-lookup"><span data-stu-id="d62d1-506">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d62d1-507">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="d62d1-507">The type of authentication to use.</span></span> <span data-ttu-id="d62d1-508">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-508">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="d62d1-509">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="d62d1-509">The possible values are:</span></span>

  - <span data-ttu-id="d62d1-510">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-510">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d62d1-511">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-511">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d62d1-512">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="d62d1-512">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d62d1-513">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-513">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d62d1-514">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="d62d1-514">Turns off HTTPS.</span></span> <span data-ttu-id="d62d1-515">只有在驗證為時，才會套用此選項 `None` 。</span><span class="sxs-lookup"><span data-stu-id="d62d1-515">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d62d1-516">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="d62d1-516">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d62d1-517">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-517">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d62d1-518">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-518">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-519">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-519">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d62d1-520">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-520">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d62d1-521">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="d62d1-521">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d62d1-522">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="d62d1-522">SDK version</span></span> | <span data-ttu-id="d62d1-523">預設值</span><span class="sxs-lookup"><span data-stu-id="d62d1-523">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d62d1-524">3.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-524">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d62d1-525">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-525">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d62d1-526">2.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-526">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="d62d1-527">reactredux</span><span class="sxs-lookup"><span data-stu-id="d62d1-527">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d62d1-528">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="d62d1-528">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-529">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-529">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d62d1-530">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-530">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d62d1-531">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="d62d1-531">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d62d1-532">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="d62d1-532">SDK version</span></span> | <span data-ttu-id="d62d1-533">預設值</span><span class="sxs-lookup"><span data-stu-id="d62d1-533">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d62d1-534">3.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-534">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d62d1-535">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-535">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d62d1-536">2.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-536">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="d62d1-537">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-537">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d62d1-538">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="d62d1-538">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="d62d1-539">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="d62d1-539">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="d62d1-540">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-540">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="d62d1-541">支援將傳統的 Razor 頁面和 Views 新增至此程式庫的元件。</span><span class="sxs-lookup"><span data-stu-id="d62d1-541">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="d62d1-542">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d62d1-542">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="d62d1-543">webapi</span><span class="sxs-lookup"><span data-stu-id="d62d1-543">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d62d1-544">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="d62d1-544">The type of authentication to use.</span></span> <span data-ttu-id="d62d1-545">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="d62d1-545">The possible values are:</span></span>

  - <span data-ttu-id="d62d1-546">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d62d1-547">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-547">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d62d1-548">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-548">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d62d1-549">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-549">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d62d1-550">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="d62d1-550">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d62d1-551">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-551">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d62d1-552">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-552">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d62d1-553">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-553">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d62d1-554">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-554">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d62d1-555">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="d62d1-555">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d62d1-556">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-556">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d62d1-557">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-557">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d62d1-558">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-558">The Client ID for this project.</span></span> <span data-ttu-id="d62d1-559">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-559">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d62d1-560">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-560">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d62d1-561">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="d62d1-561">The domain for the directory tenant.</span></span> <span data-ttu-id="d62d1-562">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-562">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d62d1-563">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-563">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d62d1-564">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62d1-564">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d62d1-565">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="d62d1-565">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d62d1-566">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-566">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d62d1-567">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="d62d1-567">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d62d1-568">僅適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-568">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d62d1-569">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="d62d1-569">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d62d1-570">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="d62d1-570">Turns off HTTPS.</span></span> <span data-ttu-id="d62d1-571">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="d62d1-571">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="d62d1-572">只有當 `IndividualB2C` 或未用於驗證時，此選項才適用 `SingleOrg` 。</span><span class="sxs-lookup"><span data-stu-id="d62d1-572">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d62d1-573">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="d62d1-573">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d62d1-574">僅適用于 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="d62d1-574">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d62d1-575">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d62d1-575">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d62d1-576">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="d62d1-576">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d62d1-577">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="d62d1-577">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d62d1-578">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="d62d1-578">SDK version</span></span> | <span data-ttu-id="d62d1-579">預設值</span><span class="sxs-lookup"><span data-stu-id="d62d1-579">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d62d1-580">3.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-580">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d62d1-581">3.0</span><span class="sxs-lookup"><span data-stu-id="d62d1-581">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d62d1-582">2.1</span><span class="sxs-lookup"><span data-stu-id="d62d1-582">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="d62d1-583">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="d62d1-583">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="d62d1-584">globaljson</span><span class="sxs-lookup"><span data-stu-id="d62d1-584">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="d62d1-585">指定要在*global json*檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-585">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="d62d1-586">範例</span><span class="sxs-lookup"><span data-stu-id="d62d1-586">Examples</span></span>

- <span data-ttu-id="d62d1-587">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="d62d1-587">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="d62d1-588">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="d62d1-588">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="d62d1-589">在指定的目錄中建立 .NET Standard 類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="d62d1-589">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="d62d1-590">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="d62d1-590">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="d62d1-591">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="d62d1-591">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="d62d1-592">列出適用于單一頁面應用程式（SPA）範本的所有範本：</span><span class="sxs-lookup"><span data-stu-id="d62d1-592">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="d62d1-593">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-593">List all templates matching the *we* substring.</span></span> <span data-ttu-id="d62d1-594">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="d62d1-594">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="d62d1-595">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-595">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="d62d1-596">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="d62d1-596">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="d62d1-597">安裝適用于 ASP.NET Core 的 SPA 範本2.0 版：</span><span class="sxs-lookup"><span data-stu-id="d62d1-597">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="d62d1-598">列出已安裝的範本和其詳細資料，包括如何將它們卸載：</span><span class="sxs-lookup"><span data-stu-id="d62d1-598">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="d62d1-599">在目前目錄中建立*json* ，將 SDK 版本設定為3.1.101：</span><span class="sxs-lookup"><span data-stu-id="d62d1-599">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="d62d1-600">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d62d1-600">See also</span></span>

- [<span data-ttu-id="d62d1-601">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="d62d1-601">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="d62d1-602">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="d62d1-602">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- <span data-ttu-id="d62d1-603">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="d62d1-603">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="d62d1-604">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="d62d1-604">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
