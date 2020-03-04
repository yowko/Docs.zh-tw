---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157215"
---
# <a name="dotnet-new"></a><span data-ttu-id="b9256-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b9256-103">dotnet new</span></span>

<span data-ttu-id="b9256-104">**本文適用于：** ✔️ .net CORE 2.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="b9256-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b9256-105">名稱</span><span class="sxs-lookup"><span data-stu-id="b9256-105">Name</span></span>

<span data-ttu-id="b9256-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="b9256-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b9256-107">概要</span><span class="sxs-lookup"><span data-stu-id="b9256-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="b9256-108">描述</span><span class="sxs-lookup"><span data-stu-id="b9256-108">Description</span></span>

<span data-ttu-id="b9256-109">`dotnet new` 命令會根據範本建立 .NET Core 專案或其他成品。</span><span class="sxs-lookup"><span data-stu-id="b9256-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="b9256-110">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="b9256-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="b9256-111">引數</span><span class="sxs-lookup"><span data-stu-id="b9256-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="b9256-112">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="b9256-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="b9256-113">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="b9256-114">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="b9256-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="b9256-115">您可以執行 `dotnet new --list`，以查看所有已安裝的範本清單。</span><span class="sxs-lookup"><span data-stu-id="b9256-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="b9256-116">如果 `TEMPLATE` 值**與所傳回**資料表的 [樣板] 或 [**簡短名稱**] 資料行中的文字完全相符，則會在這兩個數據行上執行子字串相符。</span><span class="sxs-lookup"><span data-stu-id="b9256-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="b9256-117">從 .NET Core 3.0 SDK 開始，當您在下列情況下叫用 `dotnet new` 命令時，CLI 會在 NuGet.org 中搜尋範本：</span><span class="sxs-lookup"><span data-stu-id="b9256-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="b9256-118">如果 CLI 在叫用 `dotnet new`時找不到相符的範本，甚至不是部分。</span><span class="sxs-lookup"><span data-stu-id="b9256-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="b9256-119">如果有較新版本的範本可用，則為。</span><span class="sxs-lookup"><span data-stu-id="b9256-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="b9256-120">在此情況下，會建立專案或成品，但 CLI 會警告您有關範本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="b9256-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="b9256-121">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="b9256-121">The command contains a default list of templates.</span></span> <span data-ttu-id="b9256-122">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="b9256-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b9256-123">下表顯示隨 .NET Core SDK 預先安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="b9256-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="b9256-124">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="b9256-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="b9256-125">按一下 [簡短名稱] 連結，以查看特定的範本選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="b9256-126">範本</span><span class="sxs-lookup"><span data-stu-id="b9256-126">Templates</span></span>                                    | <span data-ttu-id="b9256-127">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="b9256-127">Short name</span></span>                      | <span data-ttu-id="b9256-128">Language</span><span class="sxs-lookup"><span data-stu-id="b9256-128">Language</span></span>     | <span data-ttu-id="b9256-129">Tags</span><span class="sxs-lookup"><span data-stu-id="b9256-129">Tags</span></span>                                  | <span data-ttu-id="b9256-130">引導</span><span class="sxs-lookup"><span data-stu-id="b9256-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="b9256-131">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="b9256-131">Console Application</span></span>                          | [<span data-ttu-id="b9256-132">console</span><span class="sxs-lookup"><span data-stu-id="b9256-132">console</span></span>](#console)             | <span data-ttu-id="b9256-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b9256-133">[C#], F#, VB</span></span> | <span data-ttu-id="b9256-134">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="b9256-134">Common/Console</span></span>                        | <span data-ttu-id="b9256-135">1.0</span><span class="sxs-lookup"><span data-stu-id="b9256-135">1.0</span></span>        |
| <span data-ttu-id="b9256-136">類別庫</span><span class="sxs-lookup"><span data-stu-id="b9256-136">Class library</span></span>                                | [<span data-ttu-id="b9256-137">classlib</span><span class="sxs-lookup"><span data-stu-id="b9256-137">classlib</span></span>](#classlib)           | <span data-ttu-id="b9256-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b9256-138">[C#], F#, VB</span></span> | <span data-ttu-id="b9256-139">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="b9256-139">Common/Library</span></span>                        | <span data-ttu-id="b9256-140">1.0</span><span class="sxs-lookup"><span data-stu-id="b9256-140">1.0</span></span>        |
| <span data-ttu-id="b9256-141">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="b9256-141">WPF Application</span></span>                              | [<span data-ttu-id="b9256-142">wpf</span><span class="sxs-lookup"><span data-stu-id="b9256-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="b9256-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-143">[C#]</span></span>         | <span data-ttu-id="b9256-144">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="b9256-144">Common/WPF</span></span>                            | <span data-ttu-id="b9256-145">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-145">3.0</span></span>        |
| <span data-ttu-id="b9256-146">WPF 類別庫</span><span class="sxs-lookup"><span data-stu-id="b9256-146">WPF Class library</span></span>                            | [<span data-ttu-id="b9256-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="b9256-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="b9256-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-148">[C#]</span></span>         | <span data-ttu-id="b9256-149">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="b9256-149">Common/WPF</span></span>                            | <span data-ttu-id="b9256-150">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-150">3.0</span></span>        |
| <span data-ttu-id="b9256-151">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="b9256-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="b9256-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="b9256-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="b9256-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-153">[C#]</span></span>         | <span data-ttu-id="b9256-154">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="b9256-154">Common/WPF</span></span>                            | <span data-ttu-id="b9256-155">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-155">3.0</span></span>        |
| <span data-ttu-id="b9256-156">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="b9256-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="b9256-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="b9256-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="b9256-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-158">[C#]</span></span>         | <span data-ttu-id="b9256-159">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="b9256-159">Common/WPF</span></span>                            | <span data-ttu-id="b9256-160">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-160">3.0</span></span>        |
| <span data-ttu-id="b9256-161">Windows Forms （WinForms）應用程式</span><span class="sxs-lookup"><span data-stu-id="b9256-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="b9256-162">winforms</span><span class="sxs-lookup"><span data-stu-id="b9256-162">winforms</span></span>](#winforms)           | <span data-ttu-id="b9256-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-163">[C#]</span></span>         | <span data-ttu-id="b9256-164">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="b9256-164">Common/WinForms</span></span>                       | <span data-ttu-id="b9256-165">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-165">3.0</span></span>        |
| <span data-ttu-id="b9256-166">Windows Forms （WinForms）類別庫</span><span class="sxs-lookup"><span data-stu-id="b9256-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="b9256-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="b9256-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="b9256-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-168">[C#]</span></span>         | <span data-ttu-id="b9256-169">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="b9256-169">Common/WinForms</span></span>                       | <span data-ttu-id="b9256-170">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-170">3.0</span></span>        |
| <span data-ttu-id="b9256-171">背景工作服務</span><span class="sxs-lookup"><span data-stu-id="b9256-171">Worker Service</span></span>                               | [<span data-ttu-id="b9256-172">工作</span><span class="sxs-lookup"><span data-stu-id="b9256-172">worker</span></span>](#web-others)           | <span data-ttu-id="b9256-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-173">[C#]</span></span>         | <span data-ttu-id="b9256-174">一般/背景工作/Web</span><span class="sxs-lookup"><span data-stu-id="b9256-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="b9256-175">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-175">3.0</span></span>        |
| <span data-ttu-id="b9256-176">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="b9256-176">Unit Test Project</span></span>                            | [<span data-ttu-id="b9256-177">mstest.exe</span><span class="sxs-lookup"><span data-stu-id="b9256-177">mstest</span></span>](#test)                 | <span data-ttu-id="b9256-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b9256-178">[C#], F#, VB</span></span> | <span data-ttu-id="b9256-179">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="b9256-179">Test/MSTest</span></span>                           | <span data-ttu-id="b9256-180">1.0</span><span class="sxs-lookup"><span data-stu-id="b9256-180">1.0</span></span>        |
| <span data-ttu-id="b9256-181">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="b9256-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="b9256-182">nunit</span><span class="sxs-lookup"><span data-stu-id="b9256-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="b9256-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b9256-183">[C#], F#, VB</span></span> | <span data-ttu-id="b9256-184">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="b9256-184">Test/NUnit</span></span>                            | <span data-ttu-id="b9256-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="b9256-185">2.1.400</span></span>    |
| <span data-ttu-id="b9256-186">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="b9256-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="b9256-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b9256-187">[C#], F#, VB</span></span> | <span data-ttu-id="b9256-188">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="b9256-188">Test/NUnit</span></span>                            | <span data-ttu-id="b9256-189">2.2</span><span class="sxs-lookup"><span data-stu-id="b9256-189">2.2</span></span>        |
| <span data-ttu-id="b9256-190">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="b9256-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="b9256-191">xunit</span><span class="sxs-lookup"><span data-stu-id="b9256-191">xunit</span></span>](#test)                  | <span data-ttu-id="b9256-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b9256-192">[C#], F#, VB</span></span> | <span data-ttu-id="b9256-193">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="b9256-193">Test/xUnit</span></span>                            | <span data-ttu-id="b9256-194">1.0</span><span class="sxs-lookup"><span data-stu-id="b9256-194">1.0</span></span>        |
| <span data-ttu-id="b9256-195">Razor 元件</span><span class="sxs-lookup"><span data-stu-id="b9256-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="b9256-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-196">[C#]</span></span>         | <span data-ttu-id="b9256-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b9256-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="b9256-198">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-198">3.0</span></span>        |
| <span data-ttu-id="b9256-199">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="b9256-199">Razor Page</span></span>                                   | [<span data-ttu-id="b9256-200">page</span><span class="sxs-lookup"><span data-stu-id="b9256-200">page</span></span>](#page)                   | <span data-ttu-id="b9256-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-201">[C#]</span></span>         | <span data-ttu-id="b9256-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b9256-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="b9256-203">2.0</span><span class="sxs-lookup"><span data-stu-id="b9256-203">2.0</span></span>        |
| <span data-ttu-id="b9256-204">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="b9256-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="b9256-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="b9256-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="b9256-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-206">[C#]</span></span>         | <span data-ttu-id="b9256-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b9256-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="b9256-208">2.0</span><span class="sxs-lookup"><span data-stu-id="b9256-208">2.0</span></span>        |
| <span data-ttu-id="b9256-209">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b9256-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="b9256-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-210">[C#]</span></span>         | <span data-ttu-id="b9256-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b9256-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="b9256-212">2.0</span><span class="sxs-lookup"><span data-stu-id="b9256-212">2.0</span></span>        |
| <span data-ttu-id="b9256-213">Blazor 伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="b9256-213">Blazor Server App</span></span>                            | [<span data-ttu-id="b9256-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="b9256-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="b9256-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-215">[C#]</span></span>         | <span data-ttu-id="b9256-216">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="b9256-216">Web/Blazor</span></span>                            | <span data-ttu-id="b9256-217">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-217">3.0</span></span>        |
| <span data-ttu-id="b9256-218">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b9256-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="b9256-219">web</span><span class="sxs-lookup"><span data-stu-id="b9256-219">web</span></span>](#web)                     | <span data-ttu-id="b9256-220">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b9256-220">[C#], F#</span></span>     | <span data-ttu-id="b9256-221">Web/空白</span><span class="sxs-lookup"><span data-stu-id="b9256-221">Web/Empty</span></span>                             | <span data-ttu-id="b9256-222">1.0</span><span class="sxs-lookup"><span data-stu-id="b9256-222">1.0</span></span>        |
| <span data-ttu-id="b9256-223">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="b9256-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="b9256-224">mvc</span><span class="sxs-lookup"><span data-stu-id="b9256-224">mvc</span></span>](#web-options)             | <span data-ttu-id="b9256-225">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b9256-225">[C#], F#</span></span>     | <span data-ttu-id="b9256-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b9256-226">Web/MVC</span></span>                               | <span data-ttu-id="b9256-227">1.0</span><span class="sxs-lookup"><span data-stu-id="b9256-227">1.0</span></span>        |
| <span data-ttu-id="b9256-228">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="b9256-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="b9256-229">webapp，razor</span><span class="sxs-lookup"><span data-stu-id="b9256-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="b9256-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-230">[C#]</span></span>         | <span data-ttu-id="b9256-231">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="b9256-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="b9256-232">2.2、2。0</span><span class="sxs-lookup"><span data-stu-id="b9256-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="b9256-233">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="b9256-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="b9256-234">angular</span><span class="sxs-lookup"><span data-stu-id="b9256-234">angular</span></span>](#spa)                 | <span data-ttu-id="b9256-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-235">[C#]</span></span>         | <span data-ttu-id="b9256-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b9256-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="b9256-237">2.0</span><span class="sxs-lookup"><span data-stu-id="b9256-237">2.0</span></span>        |
| <span data-ttu-id="b9256-238">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="b9256-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="b9256-239">反應</span><span class="sxs-lookup"><span data-stu-id="b9256-239">react</span></span>](#spa)                   | <span data-ttu-id="b9256-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-240">[C#]</span></span>         | <span data-ttu-id="b9256-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b9256-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="b9256-242">2.0</span><span class="sxs-lookup"><span data-stu-id="b9256-242">2.0</span></span>        |
| <span data-ttu-id="b9256-243">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="b9256-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="b9256-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="b9256-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="b9256-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-245">[C#]</span></span>         | <span data-ttu-id="b9256-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b9256-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="b9256-247">2.0</span><span class="sxs-lookup"><span data-stu-id="b9256-247">2.0</span></span>        |
| <span data-ttu-id="b9256-248">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="b9256-248">Razor Class Library</span></span>                          | [<span data-ttu-id="b9256-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="b9256-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="b9256-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-250">[C#]</span></span>         | <span data-ttu-id="b9256-251">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="b9256-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="b9256-252">2.1</span><span class="sxs-lookup"><span data-stu-id="b9256-252">2.1</span></span>        |
| <span data-ttu-id="b9256-253">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="b9256-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="b9256-254">webapi</span><span class="sxs-lookup"><span data-stu-id="b9256-254">webapi</span></span>](#webapi)               | <span data-ttu-id="b9256-255">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="b9256-255">[C#], F#</span></span>     | <span data-ttu-id="b9256-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b9256-256">Web/WebAPI</span></span>                            | <span data-ttu-id="b9256-257">1.0</span><span class="sxs-lookup"><span data-stu-id="b9256-257">1.0</span></span>        |
| <span data-ttu-id="b9256-258">ASP.NET Core gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="b9256-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="b9256-259">grpc</span><span class="sxs-lookup"><span data-stu-id="b9256-259">grpc</span></span>](#web-others)             | <span data-ttu-id="b9256-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="b9256-260">[C#]</span></span>         | <span data-ttu-id="b9256-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="b9256-261">Web/gRPC</span></span>                              | <span data-ttu-id="b9256-262">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-262">3.0</span></span>        |
| <span data-ttu-id="b9256-263">通訊協定緩衝區檔案</span><span class="sxs-lookup"><span data-stu-id="b9256-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="b9256-264">proto</span><span class="sxs-lookup"><span data-stu-id="b9256-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="b9256-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="b9256-265">Web/gRPC</span></span>                              | <span data-ttu-id="b9256-266">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-266">3.0</span></span>        |
| <span data-ttu-id="b9256-267">dotnet .gitignore 檔</span><span class="sxs-lookup"><span data-stu-id="b9256-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="b9256-268">Config</span><span class="sxs-lookup"><span data-stu-id="b9256-268">Config</span></span>                                | <span data-ttu-id="b9256-269">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-269">3.0</span></span>        |
| <span data-ttu-id="b9256-270">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="b9256-270">global.json file</span></span>                             | [<span data-ttu-id="b9256-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="b9256-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="b9256-272">Config</span><span class="sxs-lookup"><span data-stu-id="b9256-272">Config</span></span>                                | <span data-ttu-id="b9256-273">2.0</span><span class="sxs-lookup"><span data-stu-id="b9256-273">2.0</span></span>        |
| <span data-ttu-id="b9256-274">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="b9256-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="b9256-275">Config</span><span class="sxs-lookup"><span data-stu-id="b9256-275">Config</span></span>                                | <span data-ttu-id="b9256-276">1.0</span><span class="sxs-lookup"><span data-stu-id="b9256-276">1.0</span></span>        |
| <span data-ttu-id="b9256-277">dotnet 本機工具資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="b9256-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="b9256-278">Config</span><span class="sxs-lookup"><span data-stu-id="b9256-278">Config</span></span>                                | <span data-ttu-id="b9256-279">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-279">3.0</span></span>        |
| <span data-ttu-id="b9256-280">Web 組態</span><span class="sxs-lookup"><span data-stu-id="b9256-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="b9256-281">Config</span><span class="sxs-lookup"><span data-stu-id="b9256-281">Config</span></span>                                | <span data-ttu-id="b9256-282">1.0</span><span class="sxs-lookup"><span data-stu-id="b9256-282">1.0</span></span>        |
| <span data-ttu-id="b9256-283">方案檔</span><span class="sxs-lookup"><span data-stu-id="b9256-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="b9256-284">解決方法</span><span class="sxs-lookup"><span data-stu-id="b9256-284">Solution</span></span>                              | <span data-ttu-id="b9256-285">1.0</span><span class="sxs-lookup"><span data-stu-id="b9256-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="b9256-286">選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="b9256-287">顯示執行指定的命令時，會發生什麼情況的摘要。</span><span class="sxs-lookup"><span data-stu-id="b9256-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="b9256-288">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="b9256-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="b9256-289">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="b9256-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b9256-290">當選擇的範本會覆寫輸出目錄中的現有檔案時，這是必要的。</span><span class="sxs-lookup"><span data-stu-id="b9256-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b9256-291">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="b9256-291">Prints out help for the command.</span></span> <span data-ttu-id="b9256-292">可以針對 `dotnet new` 命令本身或任何範本加以叫用。</span><span class="sxs-lookup"><span data-stu-id="b9256-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="b9256-293">例如： `dotnet new mvc --help` 。</span><span class="sxs-lookup"><span data-stu-id="b9256-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="b9256-294">從提供的 `PATH` 或 `NUGET_ID` 安裝範本套件。</span><span class="sxs-lookup"><span data-stu-id="b9256-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b9256-295">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="b9256-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="b9256-296">根據預設，`dotnet new` 會傳遞版本的 \*，這代表最新的穩定套件版本。</span><span class="sxs-lookup"><span data-stu-id="b9256-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="b9256-297">請參閱[範例](#examples)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="b9256-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="b9256-298">當您執行此命令時，如果已安裝某個版本的範本，此範本將會更新為指定的版本，或如果未指定任何版本，則為最新的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="b9256-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="b9256-299">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="b9256-300">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="b9256-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="b9256-301">如果未指定名稱，則會列出所有範本。</span><span class="sxs-lookup"><span data-stu-id="b9256-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="b9256-302">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="b9256-302">The language of the template to create.</span></span> <span data-ttu-id="b9256-303">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="b9256-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b9256-304">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="b9256-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b9256-305">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="b9256-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b9256-306">在這些情況下，請以引號括住語言參數值。</span><span class="sxs-lookup"><span data-stu-id="b9256-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="b9256-307">例如： `dotnet new console -lang "F#"` 。</span><span class="sxs-lookup"><span data-stu-id="b9256-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="b9256-308">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="b9256-308">The name for the created output.</span></span> <span data-ttu-id="b9256-309">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="b9256-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="b9256-310">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="b9256-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="b9256-311">自 .NET Core 2.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="b9256-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="b9256-312">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="b9256-312">Location to place the generated output.</span></span> <span data-ttu-id="b9256-313">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="b9256-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="b9256-314">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="b9256-314">Filters templates based on available types.</span></span> <span data-ttu-id="b9256-315">預先定義的值為「專案」、「項目」或「其他」。</span><span class="sxs-lookup"><span data-stu-id="b9256-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="b9256-316">在 `PATH` 或 `NUGET_ID` 提供的上卸載範本套件。</span><span class="sxs-lookup"><span data-stu-id="b9256-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b9256-317">若未指定 `<PATH|NUGET_ID>` 值，則會顯示所有目前已安裝的範本套件及其相關聯的範本。</span><span class="sxs-lookup"><span data-stu-id="b9256-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="b9256-318">指定 `NUGET_ID`時，請勿包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="b9256-319">如果您未指定此選項的參數，此命令會列出已安裝的範本和其相關詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b9256-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b9256-320">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b9256-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b9256-321">例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="b9256-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="b9256-322">請勿在您的範本路徑上包含最後終止的目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="b9256-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="b9256-323">檢查目前已安裝的範本套件是否有可用的更新，並加以安裝。</span><span class="sxs-lookup"><span data-stu-id="b9256-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="b9256-324">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="b9256-325">檢查目前是否已安裝的範本套件是否有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="b9256-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="b9256-326">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="b9256-327">範本選項</span><span class="sxs-lookup"><span data-stu-id="b9256-327">Template options</span></span>

<span data-ttu-id="b9256-328">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-328">Each project template may have additional options available.</span></span> <span data-ttu-id="b9256-329">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="b9256-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="b9256-330">console</span><span class="sxs-lookup"><span data-stu-id="b9256-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-331">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b9256-332">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="b9256-333">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="b9256-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="b9256-334">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="b9256-334">SDK version</span></span> | <span data-ttu-id="b9256-335">預設值</span><span class="sxs-lookup"><span data-stu-id="b9256-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="b9256-336">3.1</span><span class="sxs-lookup"><span data-stu-id="b9256-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="b9256-337">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="b9256-338">設定所建立之專案檔中的 `LangVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b9256-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="b9256-339">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="b9256-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="b9256-340">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="b9256-340">Not supported for F#.</span></span> <span data-ttu-id="b9256-341">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="b9256-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="b9256-342">如需預設C#版本清單，請參閱預設[值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="b9256-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="b9256-343">若已指定，則不會在專案建立期間執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="b9256-344">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="b9256-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="b9256-345">classlib</span><span class="sxs-lookup"><span data-stu-id="b9256-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-346">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b9256-347">值：`netcoreapp<version>` 建立 .NET Core 類別庫或 `netstandard<version>` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="b9256-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b9256-348">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="b9256-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="b9256-349">設定所建立之專案檔中的 `LangVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b9256-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="b9256-350">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="b9256-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="b9256-351">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="b9256-351">Not supported for F#.</span></span> <span data-ttu-id="b9256-352">自 .NET Core 2.2 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="b9256-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="b9256-353">如需預設C#版本清單，請參閱預設[值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="b9256-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="b9256-354">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="b9256-355">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="b9256-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-356">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b9256-357">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="b9256-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="b9256-358">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="b9256-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="b9256-359">設定所建立之專案檔中的 `LangVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b9256-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="b9256-360">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="b9256-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="b9256-361">如需預設C#版本清單，請參閱預設[值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="b9256-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="b9256-362">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="b9256-363">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="b9256-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="b9256-364">設定所建立之專案檔中的 `LangVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b9256-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="b9256-365">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="b9256-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="b9256-366">如需預設C#版本清單，請參閱預設[值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="b9256-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="b9256-367">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="b9256-368">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="b9256-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-369">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b9256-370">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="b9256-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="b9256-371">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="b9256-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="b9256-372">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="b9256-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="b9256-373">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="b9256-374">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="b9256-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-375">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b9256-376">自 .NET Core 3.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="b9256-377">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="b9256-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="b9256-378">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="b9256-378">SDK version</span></span> | <span data-ttu-id="b9256-379">預設值</span><span class="sxs-lookup"><span data-stu-id="b9256-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="b9256-380">3.1</span><span class="sxs-lookup"><span data-stu-id="b9256-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="b9256-381">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="b9256-382">使用[dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="b9256-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="b9256-383">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="b9256-384">nunit</span><span class="sxs-lookup"><span data-stu-id="b9256-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-385">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="b9256-386">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="b9256-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="b9256-387">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="b9256-387">SDK version</span></span> | <span data-ttu-id="b9256-388">預設值</span><span class="sxs-lookup"><span data-stu-id="b9256-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="b9256-389">3.1</span><span class="sxs-lookup"><span data-stu-id="b9256-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="b9256-390">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="b9256-391">2.2</span><span class="sxs-lookup"><span data-stu-id="b9256-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="b9256-392">2.1</span><span class="sxs-lookup"><span data-stu-id="b9256-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="b9256-393">使用[dotnet pack](dotnet-pack.md)啟用專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="b9256-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="b9256-394">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="b9256-395">頁面</span><span class="sxs-lookup"><span data-stu-id="b9256-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="b9256-396">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b9256-396">Namespace for the generated code.</span></span> <span data-ttu-id="b9256-397">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="b9256-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="b9256-398">建立不含 PageModel 的頁面。</span><span class="sxs-lookup"><span data-stu-id="b9256-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="b9256-399">viewimports.cshtml，proto</span><span class="sxs-lookup"><span data-stu-id="b9256-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="b9256-400">產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b9256-400">Namespace for the generated code.</span></span> <span data-ttu-id="b9256-401">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="b9256-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="b9256-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="b9256-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="b9256-403">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b9256-403">The type of authentication to use.</span></span> <span data-ttu-id="b9256-404">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="b9256-404">The possible values are:</span></span>

  - <span data-ttu-id="b9256-405">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="b9256-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="b9256-406">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="b9256-407">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="b9256-408">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="b9256-409">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="b9256-410">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="b9256-411">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="b9256-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b9256-412">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b9256-413">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="b9256-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="b9256-414">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b9256-415">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="b9256-416">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="b9256-417">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="b9256-418">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="b9256-419">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="b9256-420">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="b9256-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b9256-421">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b9256-422">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="b9256-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="b9256-423">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-423">The Client ID for this project.</span></span> <span data-ttu-id="b9256-424">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b9256-425">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="b9256-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="b9256-426">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="b9256-426">The domain for the directory tenant.</span></span> <span data-ttu-id="b9256-427">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b9256-428">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="b9256-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="b9256-429">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b9256-430">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b9256-431">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="b9256-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="b9256-432">應用程式的重新導向 URI 基底路徑中的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="b9256-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b9256-433">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b9256-434">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="b9256-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="b9256-435">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="b9256-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="b9256-436">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="b9256-437">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="b9256-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="b9256-438">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b9256-438">Turns off HTTPS.</span></span> <span data-ttu-id="b9256-439">只有在 `Individual`、`IndividualB2C`、`SingleOrg`或 `MultiOrg` 不是用於 `--auth`時，才適用此選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="b9256-440">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b9256-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b9256-441">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="b9256-442">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="b9256-443">Web</span><span class="sxs-lookup"><span data-stu-id="b9256-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="b9256-444">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="b9256-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-445">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b9256-446">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="b9256-447">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="b9256-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="b9256-448">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="b9256-448">SDK version</span></span> | <span data-ttu-id="b9256-449">預設值</span><span class="sxs-lookup"><span data-stu-id="b9256-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="b9256-450">3.1</span><span class="sxs-lookup"><span data-stu-id="b9256-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="b9256-451">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="b9256-452">2.1</span><span class="sxs-lookup"><span data-stu-id="b9256-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="b9256-453">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="b9256-454">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b9256-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="b9256-455">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="b9256-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="b9256-456">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b9256-456">The type of authentication to use.</span></span> <span data-ttu-id="b9256-457">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="b9256-457">The possible values are:</span></span>

  - <span data-ttu-id="b9256-458">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="b9256-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="b9256-459">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="b9256-460">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="b9256-461">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="b9256-462">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="b9256-463">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="b9256-464">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="b9256-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b9256-465">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b9256-466">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="b9256-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="b9256-467">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b9256-468">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="b9256-469">此專案的重設密碼原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="b9256-470">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="b9256-471">此專案的編輯設定檔原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="b9256-472">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="b9256-473">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="b9256-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b9256-474">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b9256-475">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="b9256-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="b9256-476">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-476">The Client ID for this project.</span></span> <span data-ttu-id="b9256-477">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b9256-478">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="b9256-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="b9256-479">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="b9256-479">The domain for the directory tenant.</span></span> <span data-ttu-id="b9256-480">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b9256-481">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="b9256-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="b9256-482">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b9256-483">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b9256-484">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="b9256-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="b9256-485">應用程式的重新導向 URI 基底路徑中的要求路徑。</span><span class="sxs-lookup"><span data-stu-id="b9256-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b9256-486">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b9256-487">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="b9256-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="b9256-488">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="b9256-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="b9256-489">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="b9256-490">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="b9256-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="b9256-491">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b9256-491">Turns off HTTPS.</span></span> <span data-ttu-id="b9256-492">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="b9256-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="b9256-493">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b9256-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b9256-494">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-495">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b9256-496">自 .NET Core 3.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="b9256-497">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="b9256-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="b9256-498">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="b9256-498">SDK version</span></span> | <span data-ttu-id="b9256-499">預設值</span><span class="sxs-lookup"><span data-stu-id="b9256-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="b9256-500">3.1</span><span class="sxs-lookup"><span data-stu-id="b9256-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="b9256-501">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="b9256-502">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="b9256-503">在專案中包含 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="b9256-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="b9256-504">無法在 .NET Core 2.2 和 3.1 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="b9256-505">角度、反應</span><span class="sxs-lookup"><span data-stu-id="b9256-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="b9256-506">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b9256-506">The type of authentication to use.</span></span> <span data-ttu-id="b9256-507">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-507">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="b9256-508">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="b9256-508">The possible values are:</span></span>

  - <span data-ttu-id="b9256-509">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="b9256-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="b9256-510">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="b9256-511">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="b9256-511">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="b9256-512">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="b9256-513">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b9256-513">Turns off HTTPS.</span></span> <span data-ttu-id="b9256-514">只有在 `None`驗證時，才適用此選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="b9256-515">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b9256-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b9256-516">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b9256-517">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-518">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b9256-519">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="b9256-520">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="b9256-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="b9256-521">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="b9256-521">SDK version</span></span> | <span data-ttu-id="b9256-522">預設值</span><span class="sxs-lookup"><span data-stu-id="b9256-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="b9256-523">3.1</span><span class="sxs-lookup"><span data-stu-id="b9256-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="b9256-524">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="b9256-525">2.1</span><span class="sxs-lookup"><span data-stu-id="b9256-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="b9256-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="b9256-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="b9256-527">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="b9256-527">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-528">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b9256-529">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="b9256-530">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="b9256-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="b9256-531">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="b9256-531">SDK version</span></span> | <span data-ttu-id="b9256-532">預設值</span><span class="sxs-lookup"><span data-stu-id="b9256-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="b9256-533">3.1</span><span class="sxs-lookup"><span data-stu-id="b9256-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="b9256-534">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="b9256-535">2.1</span><span class="sxs-lookup"><span data-stu-id="b9256-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="b9256-536">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="b9256-537">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b9256-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="b9256-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="b9256-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="b9256-539">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="b9256-540">支援將傳統的 Razor 頁面和 Views 新增至此程式庫的元件。</span><span class="sxs-lookup"><span data-stu-id="b9256-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="b9256-541">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="b9256-542">webapi</span><span class="sxs-lookup"><span data-stu-id="b9256-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="b9256-543">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b9256-543">The type of authentication to use.</span></span> <span data-ttu-id="b9256-544">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="b9256-544">The possible values are:</span></span>

  - <span data-ttu-id="b9256-545">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="b9256-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="b9256-546">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="b9256-547">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="b9256-548">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="b9256-549">要連接的 Azure Active Directory B2C 實例。</span><span class="sxs-lookup"><span data-stu-id="b9256-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b9256-550">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b9256-551">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="b9256-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="b9256-552">此專案的登入和註冊原則識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b9256-553">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="b9256-554">要連接的 Azure Active Directory 實例。</span><span class="sxs-lookup"><span data-stu-id="b9256-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b9256-555">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b9256-556">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="b9256-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="b9256-557">此專案的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-557">The Client ID for this project.</span></span> <span data-ttu-id="b9256-558">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b9256-559">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="b9256-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="b9256-560">目錄租使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="b9256-560">The domain for the directory tenant.</span></span> <span data-ttu-id="b9256-561">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b9256-562">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="b9256-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="b9256-563">要連接之目錄的 TenantId 識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9256-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b9256-564">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b9256-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b9256-565">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="b9256-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="b9256-566">允許此應用程式讀取目錄的許可權。</span><span class="sxs-lookup"><span data-stu-id="b9256-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="b9256-567">僅適用于 `SingleOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="b9256-568">從產生的範本排除*launchsettings.json。*</span><span class="sxs-lookup"><span data-stu-id="b9256-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="b9256-569">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b9256-569">Turns off HTTPS.</span></span> <span data-ttu-id="b9256-570">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="b9256-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b9256-571">此選項僅適用于未使用 `IndividualB2C` 或 `SingleOrg` 進行驗證的情況。</span><span class="sxs-lookup"><span data-stu-id="b9256-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="b9256-572">指定應該使用 LocalDB，而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="b9256-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b9256-573">僅適用于 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9256-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b9256-574">指定要設為目標的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b9256-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b9256-575">無法在 .NET Core 2.2 SDK 中使用選項。</span><span class="sxs-lookup"><span data-stu-id="b9256-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="b9256-576">下表根據您所使用的 SDK 版本號碼，列出預設值：</span><span class="sxs-lookup"><span data-stu-id="b9256-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="b9256-577">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="b9256-577">SDK version</span></span> | <span data-ttu-id="b9256-578">預設值</span><span class="sxs-lookup"><span data-stu-id="b9256-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="b9256-579">3.1</span><span class="sxs-lookup"><span data-stu-id="b9256-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="b9256-580">3.0</span><span class="sxs-lookup"><span data-stu-id="b9256-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="b9256-581">2.1</span><span class="sxs-lookup"><span data-stu-id="b9256-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="b9256-582">在專案建立期間不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b9256-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="b9256-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="b9256-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="b9256-584">指定要在*global json*檔案中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="b9256-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="b9256-585">範例</span><span class="sxs-lookup"><span data-stu-id="b9256-585">Examples</span></span>

- <span data-ttu-id="b9256-586">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="b9256-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="b9256-587">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="b9256-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="b9256-588">在指定的目錄中建立 .NET Standard 類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="b9256-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="b9256-589">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="b9256-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="b9256-590">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="b9256-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="b9256-591">列出適用于單一頁面應用程式（SPA）範本的所有範本：</span><span class="sxs-lookup"><span data-stu-id="b9256-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="b9256-592">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="b9256-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="b9256-593">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="b9256-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="b9256-594">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="b9256-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="b9256-595">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="b9256-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="b9256-596">安裝適用于 ASP.NET Core 的 SPA 範本2.0 版：</span><span class="sxs-lookup"><span data-stu-id="b9256-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="b9256-597">列出已安裝的範本和其詳細資料，包括如何將它們卸載：</span><span class="sxs-lookup"><span data-stu-id="b9256-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="b9256-598">在目前目錄中建立*json* ，將 SDK 版本設定為3.1.101：</span><span class="sxs-lookup"><span data-stu-id="b9256-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="b9256-599">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9256-599">See also</span></span>

- [<span data-ttu-id="b9256-600">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="b9256-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="b9256-601">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="b9256-601">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- <span data-ttu-id="b9256-602">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="b9256-602">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="b9256-603">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="b9256-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
