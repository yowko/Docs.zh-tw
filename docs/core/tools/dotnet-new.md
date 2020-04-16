---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
ms.date: 04/10/2020
ms.openlocfilehash: 4ad0d7e54f93582237ed9457b562957018916d36
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463604"
---
# <a name="dotnet-new"></a><span data-ttu-id="85d58-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="85d58-103">dotnet new</span></span>

<span data-ttu-id="85d58-104">**本文適用於:✔️** .NET Core 2.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="85d58-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="85d58-105">名稱</span><span class="sxs-lookup"><span data-stu-id="85d58-105">Name</span></span>

<span data-ttu-id="85d58-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="85d58-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="85d58-107">概要</span><span class="sxs-lookup"><span data-stu-id="85d58-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="85d58-108">描述</span><span class="sxs-lookup"><span data-stu-id="85d58-108">Description</span></span>

<span data-ttu-id="85d58-109">該`dotnet new`指令基於範本創建 .NET Core 專案或其他專案。</span><span class="sxs-lookup"><span data-stu-id="85d58-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="85d58-110">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="85d58-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="85d58-111">引數</span><span class="sxs-lookup"><span data-stu-id="85d58-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="85d58-112">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="85d58-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="85d58-113">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="85d58-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="85d58-114">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="85d58-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="85d58-115">您可以執行`dotnet new --list`以查看所有已安裝範本的清單。</span><span class="sxs-lookup"><span data-stu-id="85d58-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="85d58-116">如果`TEMPLATE`該值與返回表中的 **「樣本**」或 **「短名稱」** 欄中的文字不匹配,則對這兩列執行子字串匹配。</span><span class="sxs-lookup"><span data-stu-id="85d58-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="85d58-117">從 .NET Core 3.0 SDK 開始,當您`dotnet new`在以下條件下調用 指令時,CLI 會搜索NuGet.org中的樣本:</span><span class="sxs-lookup"><span data-stu-id="85d58-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="85d58-118">如果 CLI 在`dotnet new`調用 時找不到範本匹配,甚至不是部分範本。</span><span class="sxs-lookup"><span data-stu-id="85d58-118">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="85d58-119">如果有較新版本的範本可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-119">If there's a newer version of the template available.</span></span> <span data-ttu-id="85d58-120">在這種情況下,將創建專案或專案,但 CLI 會警告您有關範本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="85d58-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="85d58-121">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="85d58-121">The command contains a default list of templates.</span></span> <span data-ttu-id="85d58-122">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="85d58-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="85d58-123">下表顯示了預安裝的 .NET Core SDK 的範本。</span><span class="sxs-lookup"><span data-stu-id="85d58-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="85d58-124">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="85d58-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="85d58-125">按下短名稱連結以查看特定的範本選項。</span><span class="sxs-lookup"><span data-stu-id="85d58-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="85d58-126">範本</span><span class="sxs-lookup"><span data-stu-id="85d58-126">Templates</span></span>                                    | <span data-ttu-id="85d58-127">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="85d58-127">Short name</span></span>                      | <span data-ttu-id="85d58-128">Language</span><span class="sxs-lookup"><span data-stu-id="85d58-128">Language</span></span>     | <span data-ttu-id="85d58-129">Tags</span><span class="sxs-lookup"><span data-stu-id="85d58-129">Tags</span></span>                                  | <span data-ttu-id="85d58-130">介紹</span><span class="sxs-lookup"><span data-stu-id="85d58-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="85d58-131">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="85d58-131">Console Application</span></span>                          | [<span data-ttu-id="85d58-132">安慰</span><span class="sxs-lookup"><span data-stu-id="85d58-132">console</span></span>](#console)             | <span data-ttu-id="85d58-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="85d58-133">[C#], F#, VB</span></span> | <span data-ttu-id="85d58-134">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="85d58-134">Common/Console</span></span>                        | <span data-ttu-id="85d58-135">1.0</span><span class="sxs-lookup"><span data-stu-id="85d58-135">1.0</span></span>        |
| <span data-ttu-id="85d58-136">類別庫</span><span class="sxs-lookup"><span data-stu-id="85d58-136">Class library</span></span>                                | [<span data-ttu-id="85d58-137">classlib</span><span class="sxs-lookup"><span data-stu-id="85d58-137">classlib</span></span>](#classlib)           | <span data-ttu-id="85d58-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="85d58-138">[C#], F#, VB</span></span> | <span data-ttu-id="85d58-139">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="85d58-139">Common/Library</span></span>                        | <span data-ttu-id="85d58-140">1.0</span><span class="sxs-lookup"><span data-stu-id="85d58-140">1.0</span></span>        |
| <span data-ttu-id="85d58-141">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="85d58-141">WPF Application</span></span>                              | [<span data-ttu-id="85d58-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="85d58-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="85d58-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-143">[C#]</span></span>         | <span data-ttu-id="85d58-144">公開/WPF</span><span class="sxs-lookup"><span data-stu-id="85d58-144">Common/WPF</span></span>                            | <span data-ttu-id="85d58-145">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-145">3.0</span></span>        |
| <span data-ttu-id="85d58-146">WPF 類庫</span><span class="sxs-lookup"><span data-stu-id="85d58-146">WPF Class library</span></span>                            | [<span data-ttu-id="85d58-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="85d58-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="85d58-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-148">[C#]</span></span>         | <span data-ttu-id="85d58-149">公開/WPF</span><span class="sxs-lookup"><span data-stu-id="85d58-149">Common/WPF</span></span>                            | <span data-ttu-id="85d58-150">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-150">3.0</span></span>        |
| <span data-ttu-id="85d58-151">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="85d58-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="85d58-152">wpf自訂控制lib</span><span class="sxs-lookup"><span data-stu-id="85d58-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="85d58-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-153">[C#]</span></span>         | <span data-ttu-id="85d58-154">公開/WPF</span><span class="sxs-lookup"><span data-stu-id="85d58-154">Common/WPF</span></span>                            | <span data-ttu-id="85d58-155">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-155">3.0</span></span>        |
| <span data-ttu-id="85d58-156">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="85d58-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="85d58-157">wpfuser 控制lib</span><span class="sxs-lookup"><span data-stu-id="85d58-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="85d58-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-158">[C#]</span></span>         | <span data-ttu-id="85d58-159">公開/WPF</span><span class="sxs-lookup"><span data-stu-id="85d58-159">Common/WPF</span></span>                            | <span data-ttu-id="85d58-160">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-160">3.0</span></span>        |
| <span data-ttu-id="85d58-161">視窗表單(贏表單)應用程式</span><span class="sxs-lookup"><span data-stu-id="85d58-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="85d58-162">溫窗體</span><span class="sxs-lookup"><span data-stu-id="85d58-162">winforms</span></span>](#winforms)           | <span data-ttu-id="85d58-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-163">[C#]</span></span>         | <span data-ttu-id="85d58-164">通用/雙贏</span><span class="sxs-lookup"><span data-stu-id="85d58-164">Common/WinForms</span></span>                       | <span data-ttu-id="85d58-165">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-165">3.0</span></span>        |
| <span data-ttu-id="85d58-166">視窗表單(獲勝表單)類別庫</span><span class="sxs-lookup"><span data-stu-id="85d58-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="85d58-167">溫多利布</span><span class="sxs-lookup"><span data-stu-id="85d58-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="85d58-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-168">[C#]</span></span>         | <span data-ttu-id="85d58-169">通用/雙贏</span><span class="sxs-lookup"><span data-stu-id="85d58-169">Common/WinForms</span></span>                       | <span data-ttu-id="85d58-170">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-170">3.0</span></span>        |
| <span data-ttu-id="85d58-171">工人服務</span><span class="sxs-lookup"><span data-stu-id="85d58-171">Worker Service</span></span>                               | [<span data-ttu-id="85d58-172">工人</span><span class="sxs-lookup"><span data-stu-id="85d58-172">worker</span></span>](#web-others)           | <span data-ttu-id="85d58-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-173">[C#]</span></span>         | <span data-ttu-id="85d58-174">公用/工人/網路</span><span class="sxs-lookup"><span data-stu-id="85d58-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="85d58-175">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-175">3.0</span></span>        |
| <span data-ttu-id="85d58-176">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="85d58-176">Unit Test Project</span></span>                            | [<span data-ttu-id="85d58-177">mstest</span><span class="sxs-lookup"><span data-stu-id="85d58-177">mstest</span></span>](#test)                 | <span data-ttu-id="85d58-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="85d58-178">[C#], F#, VB</span></span> | <span data-ttu-id="85d58-179">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="85d58-179">Test/MSTest</span></span>                           | <span data-ttu-id="85d58-180">1.0</span><span class="sxs-lookup"><span data-stu-id="85d58-180">1.0</span></span>        |
| <span data-ttu-id="85d58-181">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="85d58-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="85d58-182">Nunit</span><span class="sxs-lookup"><span data-stu-id="85d58-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="85d58-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="85d58-183">[C#], F#, VB</span></span> | <span data-ttu-id="85d58-184">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="85d58-184">Test/NUnit</span></span>                            | <span data-ttu-id="85d58-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="85d58-185">2.1.400</span></span>    |
| <span data-ttu-id="85d58-186">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="85d58-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="85d58-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="85d58-187">[C#], F#, VB</span></span> | <span data-ttu-id="85d58-188">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="85d58-188">Test/NUnit</span></span>                            | <span data-ttu-id="85d58-189">2.2</span><span class="sxs-lookup"><span data-stu-id="85d58-189">2.2</span></span>        |
| <span data-ttu-id="85d58-190">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="85d58-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="85d58-191">森特</span><span class="sxs-lookup"><span data-stu-id="85d58-191">xunit</span></span>](#test)                  | <span data-ttu-id="85d58-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="85d58-192">[C#], F#, VB</span></span> | <span data-ttu-id="85d58-193">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="85d58-193">Test/xUnit</span></span>                            | <span data-ttu-id="85d58-194">1.0</span><span class="sxs-lookup"><span data-stu-id="85d58-194">1.0</span></span>        |
| <span data-ttu-id="85d58-195">剃刀元件</span><span class="sxs-lookup"><span data-stu-id="85d58-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="85d58-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-196">[C#]</span></span>         | <span data-ttu-id="85d58-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="85d58-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="85d58-198">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-198">3.0</span></span>        |
| <span data-ttu-id="85d58-199">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="85d58-199">Razor Page</span></span>                                   | [<span data-ttu-id="85d58-200">網頁</span><span class="sxs-lookup"><span data-stu-id="85d58-200">page</span></span>](#page)                   | <span data-ttu-id="85d58-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-201">[C#]</span></span>         | <span data-ttu-id="85d58-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="85d58-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="85d58-203">2.0</span><span class="sxs-lookup"><span data-stu-id="85d58-203">2.0</span></span>        |
| <span data-ttu-id="85d58-204">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="85d58-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="85d58-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="85d58-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="85d58-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-206">[C#]</span></span>         | <span data-ttu-id="85d58-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="85d58-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="85d58-208">2.0</span><span class="sxs-lookup"><span data-stu-id="85d58-208">2.0</span></span>        |
| <span data-ttu-id="85d58-209">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="85d58-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="85d58-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-210">[C#]</span></span>         | <span data-ttu-id="85d58-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="85d58-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="85d58-212">2.0</span><span class="sxs-lookup"><span data-stu-id="85d58-212">2.0</span></span>        |
| <span data-ttu-id="85d58-213">布拉佐伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="85d58-213">Blazor Server App</span></span>                            | [<span data-ttu-id="85d58-214">布拉佐伺服器</span><span class="sxs-lookup"><span data-stu-id="85d58-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="85d58-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-215">[C#]</span></span>         | <span data-ttu-id="85d58-216">網路/布拉佐爾</span><span class="sxs-lookup"><span data-stu-id="85d58-216">Web/Blazor</span></span>                            | <span data-ttu-id="85d58-217">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-217">3.0</span></span>        |
| <span data-ttu-id="85d58-218">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="85d58-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="85d58-219">Web</span><span class="sxs-lookup"><span data-stu-id="85d58-219">web</span></span>](#web)                     | <span data-ttu-id="85d58-220">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="85d58-220">[C#], F#</span></span>     | <span data-ttu-id="85d58-221">Web/空白</span><span class="sxs-lookup"><span data-stu-id="85d58-221">Web/Empty</span></span>                             | <span data-ttu-id="85d58-222">1.0</span><span class="sxs-lookup"><span data-stu-id="85d58-222">1.0</span></span>        |
| <span data-ttu-id="85d58-223">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="85d58-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="85d58-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="85d58-224">mvc</span></span>](#web-options)             | <span data-ttu-id="85d58-225">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="85d58-225">[C#], F#</span></span>     | <span data-ttu-id="85d58-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="85d58-226">Web/MVC</span></span>                               | <span data-ttu-id="85d58-227">1.0</span><span class="sxs-lookup"><span data-stu-id="85d58-227">1.0</span></span>        |
| <span data-ttu-id="85d58-228">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="85d58-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="85d58-229">網路應用程式, 剃鬚刀</span><span class="sxs-lookup"><span data-stu-id="85d58-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="85d58-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-230">[C#]</span></span>         | <span data-ttu-id="85d58-231">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="85d58-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="85d58-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="85d58-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="85d58-233">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="85d58-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="85d58-234">角</span><span class="sxs-lookup"><span data-stu-id="85d58-234">angular</span></span>](#spa)                 | <span data-ttu-id="85d58-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-235">[C#]</span></span>         | <span data-ttu-id="85d58-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="85d58-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="85d58-237">2.0</span><span class="sxs-lookup"><span data-stu-id="85d58-237">2.0</span></span>        |
| <span data-ttu-id="85d58-238">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="85d58-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="85d58-239">反應</span><span class="sxs-lookup"><span data-stu-id="85d58-239">react</span></span>](#spa)                   | <span data-ttu-id="85d58-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-240">[C#]</span></span>         | <span data-ttu-id="85d58-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="85d58-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="85d58-242">2.0</span><span class="sxs-lookup"><span data-stu-id="85d58-242">2.0</span></span>        |
| <span data-ttu-id="85d58-243">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="85d58-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="85d58-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="85d58-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="85d58-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-245">[C#]</span></span>         | <span data-ttu-id="85d58-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="85d58-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="85d58-247">2.0</span><span class="sxs-lookup"><span data-stu-id="85d58-247">2.0</span></span>        |
| <span data-ttu-id="85d58-248">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="85d58-248">Razor Class Library</span></span>                          | [<span data-ttu-id="85d58-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="85d58-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="85d58-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-250">[C#]</span></span>         | <span data-ttu-id="85d58-251">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="85d58-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="85d58-252">2.1</span><span class="sxs-lookup"><span data-stu-id="85d58-252">2.1</span></span>        |
| <span data-ttu-id="85d58-253">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="85d58-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="85d58-254">韋薩皮</span><span class="sxs-lookup"><span data-stu-id="85d58-254">webapi</span></span>](#webapi)               | <span data-ttu-id="85d58-255">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="85d58-255">[C#], F#</span></span>     | <span data-ttu-id="85d58-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="85d58-256">Web/WebAPI</span></span>                            | <span data-ttu-id="85d58-257">1.0</span><span class="sxs-lookup"><span data-stu-id="85d58-257">1.0</span></span>        |
| <span data-ttu-id="85d58-258">ASP.NET核心 gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="85d58-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="85d58-259">grpc</span><span class="sxs-lookup"><span data-stu-id="85d58-259">grpc</span></span>](#web-others)             | <span data-ttu-id="85d58-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="85d58-260">[C#]</span></span>         | <span data-ttu-id="85d58-261">網路/gRPC</span><span class="sxs-lookup"><span data-stu-id="85d58-261">Web/gRPC</span></span>                              | <span data-ttu-id="85d58-262">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-262">3.0</span></span>        |
| <span data-ttu-id="85d58-263">協定緩衝區檔案</span><span class="sxs-lookup"><span data-stu-id="85d58-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="85d58-264">原</span><span class="sxs-lookup"><span data-stu-id="85d58-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="85d58-265">網路/gRPC</span><span class="sxs-lookup"><span data-stu-id="85d58-265">Web/gRPC</span></span>                              | <span data-ttu-id="85d58-266">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-266">3.0</span></span>        |
| <span data-ttu-id="85d58-267">點網 gitignore 檔案</span><span class="sxs-lookup"><span data-stu-id="85d58-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="85d58-268">Config</span><span class="sxs-lookup"><span data-stu-id="85d58-268">Config</span></span>                                | <span data-ttu-id="85d58-269">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-269">3.0</span></span>        |
| <span data-ttu-id="85d58-270">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="85d58-270">global.json file</span></span>                             | [<span data-ttu-id="85d58-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="85d58-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="85d58-272">Config</span><span class="sxs-lookup"><span data-stu-id="85d58-272">Config</span></span>                                | <span data-ttu-id="85d58-273">2.0</span><span class="sxs-lookup"><span data-stu-id="85d58-273">2.0</span></span>        |
| <span data-ttu-id="85d58-274">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="85d58-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="85d58-275">Config</span><span class="sxs-lookup"><span data-stu-id="85d58-275">Config</span></span>                                | <span data-ttu-id="85d58-276">1.0</span><span class="sxs-lookup"><span data-stu-id="85d58-276">1.0</span></span>        |
| <span data-ttu-id="85d58-277">點網本地工具清單檔案</span><span class="sxs-lookup"><span data-stu-id="85d58-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="85d58-278">Config</span><span class="sxs-lookup"><span data-stu-id="85d58-278">Config</span></span>                                | <span data-ttu-id="85d58-279">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-279">3.0</span></span>        |
| <span data-ttu-id="85d58-280">Web 組態</span><span class="sxs-lookup"><span data-stu-id="85d58-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="85d58-281">Config</span><span class="sxs-lookup"><span data-stu-id="85d58-281">Config</span></span>                                | <span data-ttu-id="85d58-282">1.0</span><span class="sxs-lookup"><span data-stu-id="85d58-282">1.0</span></span>        |
| <span data-ttu-id="85d58-283">方案檔</span><span class="sxs-lookup"><span data-stu-id="85d58-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="85d58-284">解決方法</span><span class="sxs-lookup"><span data-stu-id="85d58-284">Solution</span></span>                              | <span data-ttu-id="85d58-285">1.0</span><span class="sxs-lookup"><span data-stu-id="85d58-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="85d58-286">選項。</span><span class="sxs-lookup"><span data-stu-id="85d58-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="85d58-287">顯示運行給定命令時將會發生什麼情況的摘要。</span><span class="sxs-lookup"><span data-stu-id="85d58-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="85d58-288">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="85d58-289">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="85d58-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="85d58-290">當選擇的範本將覆蓋輸出目錄中的現有檔時,這是必需的。</span><span class="sxs-lookup"><span data-stu-id="85d58-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="85d58-291">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="85d58-291">Prints out help for the command.</span></span> <span data-ttu-id="85d58-292">可以為`dotnet new`命令本身或任何範本調用它。</span><span class="sxs-lookup"><span data-stu-id="85d58-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="85d58-293">例如： `dotnet new mvc --help` 。</span><span class="sxs-lookup"><span data-stu-id="85d58-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="85d58-294">從`PATH``NUGET_ID`或安裝 提供的範本包。</span><span class="sxs-lookup"><span data-stu-id="85d58-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="85d58-295">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="85d58-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="85d58-296">默認情況下,`dotnet new`將\*傳遞 版本,該版本表示最新的穩定包版本。</span><span class="sxs-lookup"><span data-stu-id="85d58-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="85d58-297">請參閱[「示例](#examples)」部分中的範例。</span><span class="sxs-lookup"><span data-stu-id="85d58-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="85d58-298">如果在運行此命令時已安裝範本的版本,則範本將更新為指定版本,如果沒有指定版本,則該範本將更新到最新的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="85d58-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="85d58-299">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="85d58-300">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="85d58-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="85d58-301">如果未指定名稱,則列出所有範本。</span><span class="sxs-lookup"><span data-stu-id="85d58-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="85d58-302">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="85d58-302">The language of the template to create.</span></span> <span data-ttu-id="85d58-303">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="85d58-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="85d58-304">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="85d58-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="85d58-305">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="85d58-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="85d58-306">在這些情況下,將語言參數值括在引號中。</span><span class="sxs-lookup"><span data-stu-id="85d58-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="85d58-307">例如： `dotnet new console -lang "F#"` 。</span><span class="sxs-lookup"><span data-stu-id="85d58-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="85d58-308">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="85d58-308">The name for the created output.</span></span> <span data-ttu-id="85d58-309">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="85d58-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="85d58-310">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="85d58-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="85d58-311">自 .NET 核心 2.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="85d58-312">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="85d58-312">Location to place the generated output.</span></span> <span data-ttu-id="85d58-313">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="85d58-313">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="85d58-314">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="85d58-314">Filters templates based on available types.</span></span> <span data-ttu-id="85d58-315">預先定義值`project``item`為`other`或 。</span><span class="sxs-lookup"><span data-stu-id="85d58-315">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="85d58-316">在`PATH``NUGET_ID`或 上卸載範本包。</span><span class="sxs-lookup"><span data-stu-id="85d58-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="85d58-317">未指定`<PATH|NUGET_ID>`該值時,將顯示所有當前安裝的範本包及其關聯的範本。</span><span class="sxs-lookup"><span data-stu-id="85d58-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="85d58-318">指定`NUGET_ID`時,不包括版本號。</span><span class="sxs-lookup"><span data-stu-id="85d58-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="85d58-319">如果不為此選項指定參數,該命令將列出已安裝的範本及其詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="85d58-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="85d58-320">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="85d58-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="85d58-321">例如 *,C:/使用者\</ 使用者>/文檔/範本/加西亞軟體.ConsoleTemplate.CSharp*將工作,但 *./GarciaSoftware.ConsoleTemplate.CSharp*從包含的資料夾中不會。</span><span class="sxs-lookup"><span data-stu-id="85d58-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="85d58-322">不要在範本路徑上包含最終終止目錄斜杠。</span><span class="sxs-lookup"><span data-stu-id="85d58-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="85d58-323">檢查目前安裝的範本包是否有可用的更新並安裝它們。</span><span class="sxs-lookup"><span data-stu-id="85d58-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="85d58-324">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="85d58-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="85d58-325">檢查當前安裝的範本包是否有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="85d58-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="85d58-326">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="85d58-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="85d58-327">範本選項</span><span class="sxs-lookup"><span data-stu-id="85d58-327">Template options</span></span>

<span data-ttu-id="85d58-328">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="85d58-328">Each project template may have additional options available.</span></span> <span data-ttu-id="85d58-329">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="85d58-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="85d58-330">console</span><span class="sxs-lookup"><span data-stu-id="85d58-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-331">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="85d58-332">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="85d58-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="85d58-333">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="85d58-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="85d58-334">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="85d58-334">SDK version</span></span> | <span data-ttu-id="85d58-335">預設值</span><span class="sxs-lookup"><span data-stu-id="85d58-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="85d58-336">3.1</span><span class="sxs-lookup"><span data-stu-id="85d58-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="85d58-337">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="85d58-338">在`LangVersion`建立的項目檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="85d58-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="85d58-339">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="85d58-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="85d58-340">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="85d58-340">Not supported for F#.</span></span> <span data-ttu-id="85d58-341">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="85d58-342">有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="85d58-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="85d58-343">如果指定,則不會在項目創建期間執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="85d58-344">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="85d58-345">classlib</span><span class="sxs-lookup"><span data-stu-id="85d58-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-346">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="85d58-347">值：`netcoreapp<version>` 建立 .NET Core 類別庫或 `netstandard<version>` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="85d58-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="85d58-348">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="85d58-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="85d58-349">在`LangVersion`建立的項目檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="85d58-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="85d58-350">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="85d58-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="85d58-351">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="85d58-351">Not supported for F#.</span></span> <span data-ttu-id="85d58-352">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="85d58-353">有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="85d58-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="85d58-354">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="85d58-355">wpf, wpflib, wpf自定義控制lib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="85d58-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-356">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="85d58-357">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="85d58-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="85d58-358">自 .NET 核心 3.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="85d58-359">在`LangVersion`建立的項目檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="85d58-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="85d58-360">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="85d58-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="85d58-361">有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="85d58-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="85d58-362">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="85d58-363">勝利,溫多利布</span><span class="sxs-lookup"><span data-stu-id="85d58-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="85d58-364">在`LangVersion`建立的項目檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="85d58-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="85d58-365">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="85d58-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="85d58-366">有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="85d58-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="85d58-367">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="85d58-368">工人, grpc</span><span class="sxs-lookup"><span data-stu-id="85d58-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-369">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="85d58-370">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="85d58-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="85d58-371">自 .NET 核心 3.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="85d58-372">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="85d58-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="85d58-373">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="85d58-374">斯泰斯特, 迅達</span><span class="sxs-lookup"><span data-stu-id="85d58-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-375">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="85d58-376">選項可用,因為 .NET 核心 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="85d58-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="85d58-377">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="85d58-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="85d58-378">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="85d58-378">SDK version</span></span> | <span data-ttu-id="85d58-379">預設值</span><span class="sxs-lookup"><span data-stu-id="85d58-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="85d58-380">3.1</span><span class="sxs-lookup"><span data-stu-id="85d58-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="85d58-381">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="85d58-382">使用[dotnet 套件](dotnet-pack.md)為專案啟用打包。</span><span class="sxs-lookup"><span data-stu-id="85d58-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="85d58-383">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="85d58-384">Nunit</span><span class="sxs-lookup"><span data-stu-id="85d58-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-385">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="85d58-386">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="85d58-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="85d58-387">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="85d58-387">SDK version</span></span> | <span data-ttu-id="85d58-388">預設值</span><span class="sxs-lookup"><span data-stu-id="85d58-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="85d58-389">3.1</span><span class="sxs-lookup"><span data-stu-id="85d58-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="85d58-390">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="85d58-391">2.2</span><span class="sxs-lookup"><span data-stu-id="85d58-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="85d58-392">2.1</span><span class="sxs-lookup"><span data-stu-id="85d58-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="85d58-393">使用[dotnet 套件](dotnet-pack.md)為專案啟用打包。</span><span class="sxs-lookup"><span data-stu-id="85d58-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="85d58-394">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="85d58-395">頁面</span><span class="sxs-lookup"><span data-stu-id="85d58-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="85d58-396">生成的代碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="85d58-396">Namespace for the generated code.</span></span> <span data-ttu-id="85d58-397">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="85d58-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="85d58-398">創建沒有頁面模型的頁面。</span><span class="sxs-lookup"><span data-stu-id="85d58-398">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="85d58-399">檢視導入, 原型</span><span class="sxs-lookup"><span data-stu-id="85d58-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="85d58-400">生成的代碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="85d58-400">Namespace for the generated code.</span></span> <span data-ttu-id="85d58-401">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="85d58-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="85d58-402">布拉佐伺服器</span><span class="sxs-lookup"><span data-stu-id="85d58-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="85d58-403">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="85d58-403">The type of authentication to use.</span></span> <span data-ttu-id="85d58-404">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="85d58-404">The possible values are:</span></span>

  - <span data-ttu-id="85d58-405">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="85d58-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="85d58-406">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="85d58-407">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="85d58-408">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="85d58-409">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="85d58-410">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="85d58-411">要連接到的 Azure 活動目錄 B2C 實體。</span><span class="sxs-lookup"><span data-stu-id="85d58-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="85d58-412">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="85d58-413">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="85d58-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="85d58-414">此項目的登錄和註冊策略 ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="85d58-415">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="85d58-416">此專案的重置密碼策略 ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="85d58-417">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="85d58-418">此項目的編輯設定檔策略 ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="85d58-419">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="85d58-420">要連接到的 Azure 活動目錄實例。</span><span class="sxs-lookup"><span data-stu-id="85d58-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="85d58-421">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="85d58-422">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="85d58-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="85d58-423">此專案的用戶端 ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-423">The Client ID for this project.</span></span> <span data-ttu-id="85d58-424">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="85d58-425">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="85d58-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="85d58-426">目錄租戶的域。</span><span class="sxs-lookup"><span data-stu-id="85d58-426">The domain for the directory tenant.</span></span> <span data-ttu-id="85d58-427">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="85d58-428">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="85d58-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="85d58-429">要連接到的目錄的租戶 ID ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="85d58-430">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="85d58-431">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="85d58-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="85d58-432">重定向URI的應用程式基本路徑中的請求路徑。</span><span class="sxs-lookup"><span data-stu-id="85d58-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="85d58-433">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="85d58-434">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="85d58-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="85d58-435">允許此應用程式讀取訪問目錄。</span><span class="sxs-lookup"><span data-stu-id="85d58-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="85d58-436">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="85d58-437">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="85d58-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="85d58-438">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="85d58-438">Turns off HTTPS.</span></span> <span data-ttu-id="85d58-439">僅當 、`Individual`或`IndividualB2C`未`SingleOrg``--auth`用於`MultiOrg`時 ,此選項才適用。</span><span class="sxs-lookup"><span data-stu-id="85d58-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="85d58-440">指定本地資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="85d58-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="85d58-441">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="85d58-442">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="85d58-443">Web</span><span class="sxs-lookup"><span data-stu-id="85d58-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="85d58-444">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="85d58-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-445">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="85d58-446">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="85d58-447">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="85d58-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="85d58-448">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="85d58-448">SDK version</span></span> | <span data-ttu-id="85d58-449">預設值</span><span class="sxs-lookup"><span data-stu-id="85d58-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="85d58-450">3.1</span><span class="sxs-lookup"><span data-stu-id="85d58-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="85d58-451">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="85d58-452">2.1</span><span class="sxs-lookup"><span data-stu-id="85d58-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="85d58-453">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="85d58-454">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="85d58-454">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="85d58-455">mvc, 網路應用</span><span class="sxs-lookup"><span data-stu-id="85d58-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="85d58-456">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="85d58-456">The type of authentication to use.</span></span> <span data-ttu-id="85d58-457">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="85d58-457">The possible values are:</span></span>

  - <span data-ttu-id="85d58-458">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="85d58-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="85d58-459">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="85d58-460">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="85d58-461">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="85d58-462">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="85d58-463">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="85d58-464">要連接到的 Azure 活動目錄 B2C 實體。</span><span class="sxs-lookup"><span data-stu-id="85d58-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="85d58-465">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="85d58-466">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="85d58-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="85d58-467">此項目的登錄和註冊策略 ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="85d58-468">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="85d58-469">此專案的重置密碼策略 ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="85d58-470">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="85d58-471">此項目的編輯設定檔策略 ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="85d58-472">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="85d58-473">要連接到的 Azure 活動目錄實例。</span><span class="sxs-lookup"><span data-stu-id="85d58-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="85d58-474">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="85d58-475">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="85d58-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="85d58-476">此專案的用戶端 ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-476">The Client ID for this project.</span></span> <span data-ttu-id="85d58-477">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="85d58-478">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="85d58-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="85d58-479">目錄租戶的域。</span><span class="sxs-lookup"><span data-stu-id="85d58-479">The domain for the directory tenant.</span></span> <span data-ttu-id="85d58-480">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="85d58-481">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="85d58-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="85d58-482">要連接到的目錄的租戶 ID ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="85d58-483">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="85d58-484">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="85d58-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="85d58-485">重定向URI的應用程式基本路徑中的請求路徑。</span><span class="sxs-lookup"><span data-stu-id="85d58-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="85d58-486">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="85d58-487">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="85d58-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="85d58-488">允許此應用程式讀取訪問目錄。</span><span class="sxs-lookup"><span data-stu-id="85d58-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="85d58-489">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="85d58-490">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="85d58-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="85d58-491">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="85d58-491">Turns off HTTPS.</span></span> <span data-ttu-id="85d58-492">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="85d58-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="85d58-493">指定本地資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="85d58-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="85d58-494">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-495">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="85d58-496">選項可用,因為 .NET 核心 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="85d58-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="85d58-497">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="85d58-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="85d58-498">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="85d58-498">SDK version</span></span> | <span data-ttu-id="85d58-499">預設值</span><span class="sxs-lookup"><span data-stu-id="85d58-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="85d58-500">3.1</span><span class="sxs-lookup"><span data-stu-id="85d58-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="85d58-501">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="85d58-502">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="85d58-503">在專案中包括瀏覽器連結。</span><span class="sxs-lookup"><span data-stu-id="85d58-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="85d58-504">選項在 .NET Core 2.2 和 3.1 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="85d58-505">決定項目是否設定為除錯產生中使用[Razor 執行時編譯](/aspnet/core/mvc/views/view-compilation#runtime-compilation)。</span><span class="sxs-lookup"><span data-stu-id="85d58-505">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="85d58-506">選項可用,因為 .NET 核心 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="85d58-506">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="85d58-507">角,反應</span><span class="sxs-lookup"><span data-stu-id="85d58-507">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="85d58-508">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="85d58-508">The type of authentication to use.</span></span> <span data-ttu-id="85d58-509">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="85d58-509">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="85d58-510">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="85d58-510">The possible values are:</span></span>

  - <span data-ttu-id="85d58-511">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="85d58-511">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="85d58-512">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-512">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="85d58-513">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="85d58-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="85d58-514">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-514">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="85d58-515">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="85d58-515">Turns off HTTPS.</span></span> <span data-ttu-id="85d58-516">僅當身份驗證為`None`時,此選項才適用。</span><span class="sxs-lookup"><span data-stu-id="85d58-516">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="85d58-517">指定本地資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="85d58-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="85d58-518">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="85d58-519">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="85d58-519">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-520">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="85d58-521">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-521">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="85d58-522">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="85d58-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="85d58-523">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="85d58-523">SDK version</span></span> | <span data-ttu-id="85d58-524">預設值</span><span class="sxs-lookup"><span data-stu-id="85d58-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="85d58-525">3.1</span><span class="sxs-lookup"><span data-stu-id="85d58-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="85d58-526">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-526">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="85d58-527">2.1</span><span class="sxs-lookup"><span data-stu-id="85d58-527">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="85d58-528">reactredux</span><span class="sxs-lookup"><span data-stu-id="85d58-528">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="85d58-529">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="85d58-529">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-530">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-530">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="85d58-531">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-531">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="85d58-532">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="85d58-532">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="85d58-533">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="85d58-533">SDK version</span></span> | <span data-ttu-id="85d58-534">預設值</span><span class="sxs-lookup"><span data-stu-id="85d58-534">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="85d58-535">3.1</span><span class="sxs-lookup"><span data-stu-id="85d58-535">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="85d58-536">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-536">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="85d58-537">2.1</span><span class="sxs-lookup"><span data-stu-id="85d58-537">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="85d58-538">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-538">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="85d58-539">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="85d58-539">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="85d58-540">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="85d58-540">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="85d58-541">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="85d58-542">除了元件添加到此庫之外,還支援添加傳統的 Razor 頁面和檢視。</span><span class="sxs-lookup"><span data-stu-id="85d58-542">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="85d58-543">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="85d58-543">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="85d58-544">webapi</span><span class="sxs-lookup"><span data-stu-id="85d58-544">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="85d58-545">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="85d58-545">The type of authentication to use.</span></span> <span data-ttu-id="85d58-546">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="85d58-546">The possible values are:</span></span>

  - <span data-ttu-id="85d58-547">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="85d58-547">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="85d58-548">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="85d58-549">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="85d58-550">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-550">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="85d58-551">要連接到的 Azure 活動目錄 B2C 實體。</span><span class="sxs-lookup"><span data-stu-id="85d58-551">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="85d58-552">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-552">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="85d58-553">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="85d58-553">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="85d58-554">此項目的登錄和註冊策略 ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-554">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="85d58-555">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-555">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="85d58-556">要連接到的 Azure 活動目錄實例。</span><span class="sxs-lookup"><span data-stu-id="85d58-556">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="85d58-557">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-557">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="85d58-558">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="85d58-558">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="85d58-559">此專案的用戶端 ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-559">The Client ID for this project.</span></span> <span data-ttu-id="85d58-560">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-560">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="85d58-561">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="85d58-561">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="85d58-562">目錄租戶的域。</span><span class="sxs-lookup"><span data-stu-id="85d58-562">The domain for the directory tenant.</span></span> <span data-ttu-id="85d58-563">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="85d58-564">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="85d58-564">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="85d58-565">要連接到的目錄的租戶 ID ID。</span><span class="sxs-lookup"><span data-stu-id="85d58-565">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="85d58-566">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="85d58-566">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="85d58-567">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="85d58-567">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="85d58-568">允許此應用程式讀取訪問目錄。</span><span class="sxs-lookup"><span data-stu-id="85d58-568">Allows this application read-access to the directory.</span></span> <span data-ttu-id="85d58-569">僅適用於`SingleOrg`身份驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-569">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="85d58-570">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="85d58-570">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="85d58-571">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="85d58-571">Turns off HTTPS.</span></span> <span data-ttu-id="85d58-572">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="85d58-572">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="85d58-573">此選項僅適用於或不`SingleOrg`用於身份`IndividualB2C`驗證 時。</span><span class="sxs-lookup"><span data-stu-id="85d58-573">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="85d58-574">指定本地資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="85d58-574">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="85d58-575">僅適用於`IndividualB2C`身份驗證。</span><span class="sxs-lookup"><span data-stu-id="85d58-575">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85d58-576">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="85d58-576">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="85d58-577">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="85d58-577">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="85d58-578">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="85d58-578">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="85d58-579">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="85d58-579">SDK version</span></span> | <span data-ttu-id="85d58-580">預設值</span><span class="sxs-lookup"><span data-stu-id="85d58-580">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="85d58-581">3.1</span><span class="sxs-lookup"><span data-stu-id="85d58-581">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="85d58-582">3.0</span><span class="sxs-lookup"><span data-stu-id="85d58-582">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="85d58-583">2.1</span><span class="sxs-lookup"><span data-stu-id="85d58-583">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="85d58-584">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="85d58-584">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="85d58-585">globaljson</span><span class="sxs-lookup"><span data-stu-id="85d58-585">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="85d58-586">指定要在*global.json*檔中使用的 .NET Core SDK 的版本。</span><span class="sxs-lookup"><span data-stu-id="85d58-586">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="85d58-587">範例</span><span class="sxs-lookup"><span data-stu-id="85d58-587">Examples</span></span>

- <span data-ttu-id="85d58-588">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="85d58-588">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="85d58-589">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="85d58-589">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="85d58-590">在指定的目錄中建立 .NET 標準類別庫專案:</span><span class="sxs-lookup"><span data-stu-id="85d58-590">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="85d58-591">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="85d58-591">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="85d58-592">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="85d58-592">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="85d58-593">列出可用於單頁應用程式 (SPA) 樣本的所有樣本:</span><span class="sxs-lookup"><span data-stu-id="85d58-593">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="85d58-594">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="85d58-594">List all templates matching the *we* substring.</span></span> <span data-ttu-id="85d58-595">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="85d58-595">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="85d58-596">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="85d58-596">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="85d58-597">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="85d58-597">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="85d58-598">安裝 ASP.NET核心的 SPA 樣本版本 2.0:</span><span class="sxs-lookup"><span data-stu-id="85d58-598">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="85d58-599">列出已安裝的範本及其詳細資訊,包括如何卸載它們:</span><span class="sxs-lookup"><span data-stu-id="85d58-599">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="85d58-600">在目前的目錄中建立*全域.json*將 SDK 版本設定為 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="85d58-600">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="85d58-601">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85d58-601">See also</span></span>

- [<span data-ttu-id="85d58-602">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="85d58-602">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="85d58-603">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="85d58-603">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- <span data-ttu-id="85d58-604">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="85d58-604">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="85d58-605">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="85d58-605">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
