---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
ms.date: 04/10/2020
ms.openlocfilehash: 1979f98a6005a414acc64c5eaa086a88aca9f033
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102823"
---
# <a name="dotnet-new"></a><span data-ttu-id="06524-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="06524-103">dotnet new</span></span>

<span data-ttu-id="06524-104">**本文適用於:✔️** .NET Core 2.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="06524-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="06524-105">名稱</span><span class="sxs-lookup"><span data-stu-id="06524-105">Name</span></span>

<span data-ttu-id="06524-106">`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。</span><span class="sxs-lookup"><span data-stu-id="06524-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="06524-107">概要</span><span class="sxs-lookup"><span data-stu-id="06524-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="06524-108">描述</span><span class="sxs-lookup"><span data-stu-id="06524-108">Description</span></span>

<span data-ttu-id="06524-109">該`dotnet new`指令基於範本創建 .NET Core 專案或其他專案。</span><span class="sxs-lookup"><span data-stu-id="06524-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="06524-110">命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。</span><span class="sxs-lookup"><span data-stu-id="06524-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="06524-111">隱式還原</span><span class="sxs-lookup"><span data-stu-id="06524-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="06524-112">引數</span><span class="sxs-lookup"><span data-stu-id="06524-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="06524-113">要在叫用命令時具現化的範本。</span><span class="sxs-lookup"><span data-stu-id="06524-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="06524-114">每個範本可能會有您可以傳遞的特定選項。</span><span class="sxs-lookup"><span data-stu-id="06524-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="06524-115">如需詳細資訊，請參閱[範本選項](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="06524-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="06524-116">您可以執行`dotnet new --list`以查看所有已安裝範本的清單。</span><span class="sxs-lookup"><span data-stu-id="06524-116">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="06524-117">如果`TEMPLATE`該值與返回表中的 **「樣本**」或 **「短名稱」** 欄中的文字不匹配,則對這兩列執行子字串匹配。</span><span class="sxs-lookup"><span data-stu-id="06524-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="06524-118">從 .NET Core 3.0 SDK 開始,當您`dotnet new`在以下條件下調用 指令時,CLI 會搜索NuGet.org中的樣本:</span><span class="sxs-lookup"><span data-stu-id="06524-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="06524-119">如果 CLI 在`dotnet new`調用 時找不到範本匹配,甚至不是部分範本。</span><span class="sxs-lookup"><span data-stu-id="06524-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="06524-120">如果有較新版本的範本可用。</span><span class="sxs-lookup"><span data-stu-id="06524-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="06524-121">在這種情況下,將創建專案或專案,但 CLI 會警告您有關範本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="06524-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="06524-122">此命令包含預設的範本清單。</span><span class="sxs-lookup"><span data-stu-id="06524-122">The command contains a default list of templates.</span></span> <span data-ttu-id="06524-123">使用 `dotnet new -l` 以取得可用範本的清單。</span><span class="sxs-lookup"><span data-stu-id="06524-123">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="06524-124">下表顯示了預安裝的 .NET Core SDK 的範本。</span><span class="sxs-lookup"><span data-stu-id="06524-124">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="06524-125">範本的預設語言會顯示在方括號內。</span><span class="sxs-lookup"><span data-stu-id="06524-125">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="06524-126">按下短名稱連結以查看特定的範本選項。</span><span class="sxs-lookup"><span data-stu-id="06524-126">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="06524-127">範本</span><span class="sxs-lookup"><span data-stu-id="06524-127">Templates</span></span>                                    | <span data-ttu-id="06524-128">簡短名稱</span><span class="sxs-lookup"><span data-stu-id="06524-128">Short name</span></span>                      | <span data-ttu-id="06524-129">Language</span><span class="sxs-lookup"><span data-stu-id="06524-129">Language</span></span>     | <span data-ttu-id="06524-130">Tags</span><span class="sxs-lookup"><span data-stu-id="06524-130">Tags</span></span>                                  | <span data-ttu-id="06524-131">介紹</span><span class="sxs-lookup"><span data-stu-id="06524-131">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="06524-132">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="06524-132">Console Application</span></span>                          | [<span data-ttu-id="06524-133">安慰</span><span class="sxs-lookup"><span data-stu-id="06524-133">console</span></span>](#console)             | <span data-ttu-id="06524-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="06524-134">[C#], F#, VB</span></span> | <span data-ttu-id="06524-135">通用/主控台</span><span class="sxs-lookup"><span data-stu-id="06524-135">Common/Console</span></span>                        | <span data-ttu-id="06524-136">1.0</span><span class="sxs-lookup"><span data-stu-id="06524-136">1.0</span></span>        |
| <span data-ttu-id="06524-137">類別庫</span><span class="sxs-lookup"><span data-stu-id="06524-137">Class library</span></span>                                | [<span data-ttu-id="06524-138">classlib</span><span class="sxs-lookup"><span data-stu-id="06524-138">classlib</span></span>](#classlib)           | <span data-ttu-id="06524-139">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="06524-139">[C#], F#, VB</span></span> | <span data-ttu-id="06524-140">通用/程式庫</span><span class="sxs-lookup"><span data-stu-id="06524-140">Common/Library</span></span>                        | <span data-ttu-id="06524-141">1.0</span><span class="sxs-lookup"><span data-stu-id="06524-141">1.0</span></span>        |
| <span data-ttu-id="06524-142">WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="06524-142">WPF Application</span></span>                              | [<span data-ttu-id="06524-143">Wpf</span><span class="sxs-lookup"><span data-stu-id="06524-143">wpf</span></span>](#wpf)                     | <span data-ttu-id="06524-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-144">[C#]</span></span>         | <span data-ttu-id="06524-145">公開/WPF</span><span class="sxs-lookup"><span data-stu-id="06524-145">Common/WPF</span></span>                            | <span data-ttu-id="06524-146">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-146">3.0</span></span>        |
| <span data-ttu-id="06524-147">WPF 類庫</span><span class="sxs-lookup"><span data-stu-id="06524-147">WPF Class library</span></span>                            | [<span data-ttu-id="06524-148">wpflib</span><span class="sxs-lookup"><span data-stu-id="06524-148">wpflib</span></span>](#wpf)                  | <span data-ttu-id="06524-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-149">[C#]</span></span>         | <span data-ttu-id="06524-150">公開/WPF</span><span class="sxs-lookup"><span data-stu-id="06524-150">Common/WPF</span></span>                            | <span data-ttu-id="06524-151">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-151">3.0</span></span>        |
| <span data-ttu-id="06524-152">WPF 自訂控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="06524-152">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="06524-153">wpf自訂控制lib</span><span class="sxs-lookup"><span data-stu-id="06524-153">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="06524-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-154">[C#]</span></span>         | <span data-ttu-id="06524-155">公開/WPF</span><span class="sxs-lookup"><span data-stu-id="06524-155">Common/WPF</span></span>                            | <span data-ttu-id="06524-156">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-156">3.0</span></span>        |
| <span data-ttu-id="06524-157">WPF 使用者控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="06524-157">WPF User Control Library</span></span>                     | [<span data-ttu-id="06524-158">wpfuser 控制lib</span><span class="sxs-lookup"><span data-stu-id="06524-158">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="06524-159">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-159">[C#]</span></span>         | <span data-ttu-id="06524-160">公開/WPF</span><span class="sxs-lookup"><span data-stu-id="06524-160">Common/WPF</span></span>                            | <span data-ttu-id="06524-161">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-161">3.0</span></span>        |
| <span data-ttu-id="06524-162">視窗表單(贏表單)應用程式</span><span class="sxs-lookup"><span data-stu-id="06524-162">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="06524-163">溫窗體</span><span class="sxs-lookup"><span data-stu-id="06524-163">winforms</span></span>](#winforms)           | <span data-ttu-id="06524-164">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-164">[C#]</span></span>         | <span data-ttu-id="06524-165">通用/雙贏</span><span class="sxs-lookup"><span data-stu-id="06524-165">Common/WinForms</span></span>                       | <span data-ttu-id="06524-166">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-166">3.0</span></span>        |
| <span data-ttu-id="06524-167">視窗表單(獲勝表單)類別庫</span><span class="sxs-lookup"><span data-stu-id="06524-167">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="06524-168">溫多利布</span><span class="sxs-lookup"><span data-stu-id="06524-168">winformslib</span></span>](#winforms)        | <span data-ttu-id="06524-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-169">[C#]</span></span>         | <span data-ttu-id="06524-170">通用/雙贏</span><span class="sxs-lookup"><span data-stu-id="06524-170">Common/WinForms</span></span>                       | <span data-ttu-id="06524-171">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-171">3.0</span></span>        |
| <span data-ttu-id="06524-172">工人服務</span><span class="sxs-lookup"><span data-stu-id="06524-172">Worker Service</span></span>                               | [<span data-ttu-id="06524-173">工人</span><span class="sxs-lookup"><span data-stu-id="06524-173">worker</span></span>](#web-others)           | <span data-ttu-id="06524-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-174">[C#]</span></span>         | <span data-ttu-id="06524-175">公用/工人/網路</span><span class="sxs-lookup"><span data-stu-id="06524-175">Common/Worker/Web</span></span>                     | <span data-ttu-id="06524-176">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-176">3.0</span></span>        |
| <span data-ttu-id="06524-177">單元測試專案</span><span class="sxs-lookup"><span data-stu-id="06524-177">Unit Test Project</span></span>                            | [<span data-ttu-id="06524-178">mstest</span><span class="sxs-lookup"><span data-stu-id="06524-178">mstest</span></span>](#test)                 | <span data-ttu-id="06524-179">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="06524-179">[C#], F#, VB</span></span> | <span data-ttu-id="06524-180">測試/MSTest</span><span class="sxs-lookup"><span data-stu-id="06524-180">Test/MSTest</span></span>                           | <span data-ttu-id="06524-181">1.0</span><span class="sxs-lookup"><span data-stu-id="06524-181">1.0</span></span>        |
| <span data-ttu-id="06524-182">NUnit 3 測試專案</span><span class="sxs-lookup"><span data-stu-id="06524-182">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="06524-183">Nunit</span><span class="sxs-lookup"><span data-stu-id="06524-183">nunit</span></span>](#nunit)                  | <span data-ttu-id="06524-184">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="06524-184">[C#], F#, VB</span></span> | <span data-ttu-id="06524-185">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="06524-185">Test/NUnit</span></span>                            | <span data-ttu-id="06524-186">2.1.400</span><span class="sxs-lookup"><span data-stu-id="06524-186">2.1.400</span></span>    |
| <span data-ttu-id="06524-187">NUnit 3 測試項目</span><span class="sxs-lookup"><span data-stu-id="06524-187">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="06524-188">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="06524-188">[C#], F#, VB</span></span> | <span data-ttu-id="06524-189">測試/NUnit</span><span class="sxs-lookup"><span data-stu-id="06524-189">Test/NUnit</span></span>                            | <span data-ttu-id="06524-190">2.2</span><span class="sxs-lookup"><span data-stu-id="06524-190">2.2</span></span>        |
| <span data-ttu-id="06524-191">xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="06524-191">xUnit Test Project</span></span>                           | [<span data-ttu-id="06524-192">森特</span><span class="sxs-lookup"><span data-stu-id="06524-192">xunit</span></span>](#test)                  | <span data-ttu-id="06524-193">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="06524-193">[C#], F#, VB</span></span> | <span data-ttu-id="06524-194">測試/XUnit</span><span class="sxs-lookup"><span data-stu-id="06524-194">Test/xUnit</span></span>                            | <span data-ttu-id="06524-195">1.0</span><span class="sxs-lookup"><span data-stu-id="06524-195">1.0</span></span>        |
| <span data-ttu-id="06524-196">剃刀元件</span><span class="sxs-lookup"><span data-stu-id="06524-196">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="06524-197">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-197">[C#]</span></span>         | <span data-ttu-id="06524-198">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="06524-198">Web/ASP.NET</span></span>                           | <span data-ttu-id="06524-199">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-199">3.0</span></span>        |
| <span data-ttu-id="06524-200">Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="06524-200">Razor Page</span></span>                                   | [<span data-ttu-id="06524-201">網頁</span><span class="sxs-lookup"><span data-stu-id="06524-201">page</span></span>](#page)                   | <span data-ttu-id="06524-202">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-202">[C#]</span></span>         | <span data-ttu-id="06524-203">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="06524-203">Web/ASP.NET</span></span>                           | <span data-ttu-id="06524-204">2.0</span><span class="sxs-lookup"><span data-stu-id="06524-204">2.0</span></span>        |
| <span data-ttu-id="06524-205">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="06524-205">MVC ViewImports</span></span>                              | [<span data-ttu-id="06524-206">viewimports</span><span class="sxs-lookup"><span data-stu-id="06524-206">viewimports</span></span>](#namespace)       | <span data-ttu-id="06524-207">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-207">[C#]</span></span>         | <span data-ttu-id="06524-208">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="06524-208">Web/ASP.NET</span></span>                           | <span data-ttu-id="06524-209">2.0</span><span class="sxs-lookup"><span data-stu-id="06524-209">2.0</span></span>        |
| <span data-ttu-id="06524-210">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="06524-210">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="06524-211">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-211">[C#]</span></span>         | <span data-ttu-id="06524-212">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="06524-212">Web/ASP.NET</span></span>                           | <span data-ttu-id="06524-213">2.0</span><span class="sxs-lookup"><span data-stu-id="06524-213">2.0</span></span>        |
| <span data-ttu-id="06524-214">布拉佐伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="06524-214">Blazor Server App</span></span>                            | [<span data-ttu-id="06524-215">布拉佐伺服器</span><span class="sxs-lookup"><span data-stu-id="06524-215">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="06524-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-216">[C#]</span></span>         | <span data-ttu-id="06524-217">網路/布拉佐爾</span><span class="sxs-lookup"><span data-stu-id="06524-217">Web/Blazor</span></span>                            | <span data-ttu-id="06524-218">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-218">3.0</span></span>        |
| <span data-ttu-id="06524-219">空的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="06524-219">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="06524-220">Web</span><span class="sxs-lookup"><span data-stu-id="06524-220">web</span></span>](#web)                     | <span data-ttu-id="06524-221">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="06524-221">[C#], F#</span></span>     | <span data-ttu-id="06524-222">Web/空白</span><span class="sxs-lookup"><span data-stu-id="06524-222">Web/Empty</span></span>                             | <span data-ttu-id="06524-223">1.0</span><span class="sxs-lookup"><span data-stu-id="06524-223">1.0</span></span>        |
| <span data-ttu-id="06524-224">ASP.NET Core Web 應用程式 (模型檢視控制器)</span><span class="sxs-lookup"><span data-stu-id="06524-224">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="06524-225">Mvc</span><span class="sxs-lookup"><span data-stu-id="06524-225">mvc</span></span>](#web-options)             | <span data-ttu-id="06524-226">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="06524-226">[C#], F#</span></span>     | <span data-ttu-id="06524-227">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="06524-227">Web/MVC</span></span>                               | <span data-ttu-id="06524-228">1.0</span><span class="sxs-lookup"><span data-stu-id="06524-228">1.0</span></span>        |
| <span data-ttu-id="06524-229">ASP.NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="06524-229">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="06524-230">網路應用程式, 剃鬚刀</span><span class="sxs-lookup"><span data-stu-id="06524-230">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="06524-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-231">[C#]</span></span>         | <span data-ttu-id="06524-232">Web/MVC/Razor 頁面</span><span class="sxs-lookup"><span data-stu-id="06524-232">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="06524-233">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="06524-233">2.2, 2.0</span></span>   |
| <span data-ttu-id="06524-234">ASP.NET Core 與 Angular</span><span class="sxs-lookup"><span data-stu-id="06524-234">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="06524-235">角</span><span class="sxs-lookup"><span data-stu-id="06524-235">angular</span></span>](#spa)                 | <span data-ttu-id="06524-236">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-236">[C#]</span></span>         | <span data-ttu-id="06524-237">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="06524-237">Web/MVC/SPA</span></span>                           | <span data-ttu-id="06524-238">2.0</span><span class="sxs-lookup"><span data-stu-id="06524-238">2.0</span></span>        |
| <span data-ttu-id="06524-239">ASP.NET Core 與 React.js</span><span class="sxs-lookup"><span data-stu-id="06524-239">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="06524-240">反應</span><span class="sxs-lookup"><span data-stu-id="06524-240">react</span></span>](#spa)                   | <span data-ttu-id="06524-241">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-241">[C#]</span></span>         | <span data-ttu-id="06524-242">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="06524-242">Web/MVC/SPA</span></span>                           | <span data-ttu-id="06524-243">2.0</span><span class="sxs-lookup"><span data-stu-id="06524-243">2.0</span></span>        |
| <span data-ttu-id="06524-244">ASP.NET Core 與 React.js 和 Redux</span><span class="sxs-lookup"><span data-stu-id="06524-244">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="06524-245">reactredux</span><span class="sxs-lookup"><span data-stu-id="06524-245">reactredux</span></span>](#reactredux)       | <span data-ttu-id="06524-246">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-246">[C#]</span></span>         | <span data-ttu-id="06524-247">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="06524-247">Web/MVC/SPA</span></span>                           | <span data-ttu-id="06524-248">2.0</span><span class="sxs-lookup"><span data-stu-id="06524-248">2.0</span></span>        |
| <span data-ttu-id="06524-249">Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="06524-249">Razor Class Library</span></span>                          | [<span data-ttu-id="06524-250">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="06524-250">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="06524-251">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-251">[C#]</span></span>         | <span data-ttu-id="06524-252">Web/Razor/程式庫/Razor 類別庫</span><span class="sxs-lookup"><span data-stu-id="06524-252">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="06524-253">2.1</span><span class="sxs-lookup"><span data-stu-id="06524-253">2.1</span></span>        |
| <span data-ttu-id="06524-254">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="06524-254">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="06524-255">韋薩皮</span><span class="sxs-lookup"><span data-stu-id="06524-255">webapi</span></span>](#webapi)               | <span data-ttu-id="06524-256">[C#]、F#</span><span class="sxs-lookup"><span data-stu-id="06524-256">[C#], F#</span></span>     | <span data-ttu-id="06524-257">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="06524-257">Web/WebAPI</span></span>                            | <span data-ttu-id="06524-258">1.0</span><span class="sxs-lookup"><span data-stu-id="06524-258">1.0</span></span>        |
| <span data-ttu-id="06524-259">ASP.NET核心 gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="06524-259">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="06524-260">grpc</span><span class="sxs-lookup"><span data-stu-id="06524-260">grpc</span></span>](#web-others)             | <span data-ttu-id="06524-261">[C#]</span><span class="sxs-lookup"><span data-stu-id="06524-261">[C#]</span></span>         | <span data-ttu-id="06524-262">網路/gRPC</span><span class="sxs-lookup"><span data-stu-id="06524-262">Web/gRPC</span></span>                              | <span data-ttu-id="06524-263">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-263">3.0</span></span>        |
| <span data-ttu-id="06524-264">協定緩衝區檔案</span><span class="sxs-lookup"><span data-stu-id="06524-264">Protocol Buffer File</span></span>                         | [<span data-ttu-id="06524-265">原</span><span class="sxs-lookup"><span data-stu-id="06524-265">proto</span></span>](#namespace)             |              | <span data-ttu-id="06524-266">網路/gRPC</span><span class="sxs-lookup"><span data-stu-id="06524-266">Web/gRPC</span></span>                              | <span data-ttu-id="06524-267">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-267">3.0</span></span>        |
| <span data-ttu-id="06524-268">點網 gitignore 檔案</span><span class="sxs-lookup"><span data-stu-id="06524-268">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="06524-269">Config</span><span class="sxs-lookup"><span data-stu-id="06524-269">Config</span></span>                                | <span data-ttu-id="06524-270">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-270">3.0</span></span>        |
| <span data-ttu-id="06524-271">global.json 檔案</span><span class="sxs-lookup"><span data-stu-id="06524-271">global.json file</span></span>                             | [<span data-ttu-id="06524-272">globaljson</span><span class="sxs-lookup"><span data-stu-id="06524-272">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="06524-273">Config</span><span class="sxs-lookup"><span data-stu-id="06524-273">Config</span></span>                                | <span data-ttu-id="06524-274">2.0</span><span class="sxs-lookup"><span data-stu-id="06524-274">2.0</span></span>        |
| <span data-ttu-id="06524-275">NuGet 組態</span><span class="sxs-lookup"><span data-stu-id="06524-275">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="06524-276">Config</span><span class="sxs-lookup"><span data-stu-id="06524-276">Config</span></span>                                | <span data-ttu-id="06524-277">1.0</span><span class="sxs-lookup"><span data-stu-id="06524-277">1.0</span></span>        |
| <span data-ttu-id="06524-278">點網本地工具清單檔案</span><span class="sxs-lookup"><span data-stu-id="06524-278">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="06524-279">Config</span><span class="sxs-lookup"><span data-stu-id="06524-279">Config</span></span>                                | <span data-ttu-id="06524-280">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-280">3.0</span></span>        |
| <span data-ttu-id="06524-281">Web 組態</span><span class="sxs-lookup"><span data-stu-id="06524-281">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="06524-282">Config</span><span class="sxs-lookup"><span data-stu-id="06524-282">Config</span></span>                                | <span data-ttu-id="06524-283">1.0</span><span class="sxs-lookup"><span data-stu-id="06524-283">1.0</span></span>        |
| <span data-ttu-id="06524-284">方案檔</span><span class="sxs-lookup"><span data-stu-id="06524-284">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="06524-285">解決方法</span><span class="sxs-lookup"><span data-stu-id="06524-285">Solution</span></span>                              | <span data-ttu-id="06524-286">1.0</span><span class="sxs-lookup"><span data-stu-id="06524-286">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="06524-287">選項。</span><span class="sxs-lookup"><span data-stu-id="06524-287">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="06524-288">顯示運行給定命令時將會發生什麼情況的摘要。</span><span class="sxs-lookup"><span data-stu-id="06524-288">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="06524-289">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="06524-289">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="06524-290">強制產生內容，即使它會變更現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="06524-290">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="06524-291">當選擇的範本將覆蓋輸出目錄中的現有檔時,這是必需的。</span><span class="sxs-lookup"><span data-stu-id="06524-291">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="06524-292">印出命令的說明。</span><span class="sxs-lookup"><span data-stu-id="06524-292">Prints out help for the command.</span></span> <span data-ttu-id="06524-293">可以為`dotnet new`命令本身或任何範本調用它。</span><span class="sxs-lookup"><span data-stu-id="06524-293">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="06524-294">例如： `dotnet new mvc --help` 。</span><span class="sxs-lookup"><span data-stu-id="06524-294">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="06524-295">從`PATH``NUGET_ID`或安裝 提供的範本包。</span><span class="sxs-lookup"><span data-stu-id="06524-295">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="06524-296">若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。</span><span class="sxs-lookup"><span data-stu-id="06524-296">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="06524-297">默認情況下,`dotnet new`將\*傳遞 版本,該版本表示最新的穩定包版本。</span><span class="sxs-lookup"><span data-stu-id="06524-297">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="06524-298">請參閱[「示例](#examples)」部分中的範例。</span><span class="sxs-lookup"><span data-stu-id="06524-298">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="06524-299">如果在運行此命令時已安裝範本的版本,則範本將更新為指定版本,如果沒有指定版本,則該範本將更新到最新的穩定版本。</span><span class="sxs-lookup"><span data-stu-id="06524-299">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="06524-300">如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-300">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="06524-301">列出包含指定名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="06524-301">Lists templates containing the specified name.</span></span> <span data-ttu-id="06524-302">如果未指定名稱,則列出所有範本。</span><span class="sxs-lookup"><span data-stu-id="06524-302">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="06524-303">要建立的範本語言。</span><span class="sxs-lookup"><span data-stu-id="06524-303">The language of the template to create.</span></span> <span data-ttu-id="06524-304">接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。</span><span class="sxs-lookup"><span data-stu-id="06524-304">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="06524-305">並非所有範本都適用。</span><span class="sxs-lookup"><span data-stu-id="06524-305">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="06524-306">某些 Shell 會將 `#` 解譯為特殊字元。</span><span class="sxs-lookup"><span data-stu-id="06524-306">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="06524-307">在這些情況下,將語言參數值括在引號中。</span><span class="sxs-lookup"><span data-stu-id="06524-307">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="06524-308">例如： `dotnet new console -lang "F#"` 。</span><span class="sxs-lookup"><span data-stu-id="06524-308">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="06524-309">所建立輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="06524-309">The name for the created output.</span></span> <span data-ttu-id="06524-310">如果未指定名稱，則會使用目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="06524-310">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="06524-311">請指定安裝期間所要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="06524-311">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="06524-312">自 .NET 核心 2.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="06524-312">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="06524-313">放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="06524-313">Location to place the generated output.</span></span> <span data-ttu-id="06524-314">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="06524-314">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="06524-315">根據可用的類型篩選範本。</span><span class="sxs-lookup"><span data-stu-id="06524-315">Filters templates based on available types.</span></span> <span data-ttu-id="06524-316">預先定義值`project``item`為`other`或 。</span><span class="sxs-lookup"><span data-stu-id="06524-316">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="06524-317">在`PATH``NUGET_ID`或 上卸載範本包。</span><span class="sxs-lookup"><span data-stu-id="06524-317">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="06524-318">未指定`<PATH|NUGET_ID>`該值時,將顯示所有當前安裝的範本包及其關聯的範本。</span><span class="sxs-lookup"><span data-stu-id="06524-318">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="06524-319">指定`NUGET_ID`時,不包括版本號。</span><span class="sxs-lookup"><span data-stu-id="06524-319">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="06524-320">如果不為此選項指定參數,該命令將列出已安裝的範本及其詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="06524-320">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="06524-321">若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="06524-321">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="06524-322">例如 *,C:/使用者\</ 使用者>/文檔/範本/加西亞軟體.ConsoleTemplate.CSharp*將工作,但 *./GarciaSoftware.ConsoleTemplate.CSharp*從包含的資料夾中不會。</span><span class="sxs-lookup"><span data-stu-id="06524-322">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="06524-323">不要在範本路徑上包含最終終止目錄斜杠。</span><span class="sxs-lookup"><span data-stu-id="06524-323">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="06524-324">檢查目前安裝的範本包是否有可用的更新並安裝它們。</span><span class="sxs-lookup"><span data-stu-id="06524-324">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="06524-325">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="06524-325">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="06524-326">檢查當前安裝的範本包是否有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="06524-326">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="06524-327">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="06524-327">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="06524-328">範本選項</span><span class="sxs-lookup"><span data-stu-id="06524-328">Template options</span></span>

<span data-ttu-id="06524-329">每個專案範本都可能會有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="06524-329">Each project template may have additional options available.</span></span> <span data-ttu-id="06524-330">核心範本有下列額外選項：</span><span class="sxs-lookup"><span data-stu-id="06524-330">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="06524-331">console</span><span class="sxs-lookup"><span data-stu-id="06524-331">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-332">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-332">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="06524-333">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="06524-333">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="06524-334">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="06524-334">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="06524-335">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="06524-335">SDK version</span></span> | <span data-ttu-id="06524-336">預設值</span><span class="sxs-lookup"><span data-stu-id="06524-336">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="06524-337">3.1</span><span class="sxs-lookup"><span data-stu-id="06524-337">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="06524-338">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-338">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="06524-339">在`LangVersion`建立的項目檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="06524-339">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="06524-340">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="06524-340">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="06524-341">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="06524-341">Not supported for F#.</span></span> <span data-ttu-id="06524-342">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="06524-342">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="06524-343">有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="06524-343">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="06524-344">如果指定,則不會在項目創建期間執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-344">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="06524-345">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="06524-345">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="06524-346">classlib</span><span class="sxs-lookup"><span data-stu-id="06524-346">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-347">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-347">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="06524-348">值：`netcoreapp<version>` 建立 .NET Core 類別庫或 `netstandard<version>` 建立 .NET Standard 類別庫。</span><span class="sxs-lookup"><span data-stu-id="06524-348">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="06524-349">預設值是 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="06524-349">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="06524-350">在`LangVersion`建立的項目檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="06524-350">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="06524-351">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="06524-351">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="06524-352">不支援 F#。</span><span class="sxs-lookup"><span data-stu-id="06524-352">Not supported for F#.</span></span> <span data-ttu-id="06524-353">自 .NET 核心 2.2 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="06524-353">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="06524-354">有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="06524-354">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="06524-355">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-355">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="06524-356">wpf, wpflib, wpf自定義控制lib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="06524-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-357">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-357">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="06524-358">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="06524-358">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="06524-359">自 .NET 核心 3.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="06524-359">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="06524-360">在`LangVersion`建立的項目檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="06524-360">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="06524-361">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="06524-361">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="06524-362">有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="06524-362">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="06524-363">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-363">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="06524-364">勝利,溫多利布</span><span class="sxs-lookup"><span data-stu-id="06524-364">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="06524-365">在`LangVersion`建立的項目檔中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="06524-365">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="06524-366">例如，使用 `--langVersion 7.3` 可使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="06524-366">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="06524-367">有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="06524-367">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="06524-368">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-368">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="06524-369">工人, grpc</span><span class="sxs-lookup"><span data-stu-id="06524-369">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-370">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-370">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="06524-371">預設值是 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="06524-371">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="06524-372">自 .NET 核心 3.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="06524-372">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="06524-373">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="06524-373">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="06524-374">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-374">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="06524-375">斯泰斯特, 迅達</span><span class="sxs-lookup"><span data-stu-id="06524-375">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-376">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-376">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="06524-377">選項可用,因為 .NET 核心 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="06524-377">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="06524-378">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="06524-378">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="06524-379">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="06524-379">SDK version</span></span> | <span data-ttu-id="06524-380">預設值</span><span class="sxs-lookup"><span data-stu-id="06524-380">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="06524-381">3.1</span><span class="sxs-lookup"><span data-stu-id="06524-381">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="06524-382">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-382">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="06524-383">使用[dotnet 套件](dotnet-pack.md)為專案啟用打包。</span><span class="sxs-lookup"><span data-stu-id="06524-383">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="06524-384">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-384">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="06524-385">Nunit</span><span class="sxs-lookup"><span data-stu-id="06524-385">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-386">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-386">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="06524-387">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="06524-387">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="06524-388">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="06524-388">SDK version</span></span> | <span data-ttu-id="06524-389">預設值</span><span class="sxs-lookup"><span data-stu-id="06524-389">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="06524-390">3.1</span><span class="sxs-lookup"><span data-stu-id="06524-390">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="06524-391">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-391">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="06524-392">2.2</span><span class="sxs-lookup"><span data-stu-id="06524-392">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="06524-393">2.1</span><span class="sxs-lookup"><span data-stu-id="06524-393">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="06524-394">使用[dotnet 套件](dotnet-pack.md)為專案啟用打包。</span><span class="sxs-lookup"><span data-stu-id="06524-394">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="06524-395">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-395">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="06524-396">頁面</span><span class="sxs-lookup"><span data-stu-id="06524-396">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="06524-397">生成的代碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="06524-397">Namespace for the generated code.</span></span> <span data-ttu-id="06524-398">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="06524-398">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="06524-399">創建沒有頁面模型的頁面。</span><span class="sxs-lookup"><span data-stu-id="06524-399">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="06524-400">檢視導入, 原型</span><span class="sxs-lookup"><span data-stu-id="06524-400">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="06524-401">生成的代碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="06524-401">Namespace for the generated code.</span></span> <span data-ttu-id="06524-402">預設值是 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="06524-402">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="06524-403">布拉佐伺服器</span><span class="sxs-lookup"><span data-stu-id="06524-403">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="06524-404">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="06524-404">The type of authentication to use.</span></span> <span data-ttu-id="06524-405">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="06524-405">The possible values are:</span></span>

  - <span data-ttu-id="06524-406">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="06524-406">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="06524-407">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-407">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="06524-408">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-408">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="06524-409">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-409">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="06524-410">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-410">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="06524-411">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-411">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="06524-412">要連接到的 Azure 活動目錄 B2C 實體。</span><span class="sxs-lookup"><span data-stu-id="06524-412">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="06524-413">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-413">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="06524-414">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="06524-414">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="06524-415">此項目的登錄和註冊策略 ID。</span><span class="sxs-lookup"><span data-stu-id="06524-415">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="06524-416">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-416">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="06524-417">此專案的重置密碼策略 ID。</span><span class="sxs-lookup"><span data-stu-id="06524-417">The reset password policy ID for this project.</span></span> <span data-ttu-id="06524-418">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-418">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="06524-419">此項目的編輯設定檔策略 ID。</span><span class="sxs-lookup"><span data-stu-id="06524-419">The edit profile policy ID for this project.</span></span> <span data-ttu-id="06524-420">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-420">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="06524-421">要連接到的 Azure 活動目錄實例。</span><span class="sxs-lookup"><span data-stu-id="06524-421">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="06524-422">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-422">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="06524-423">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="06524-423">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="06524-424">此專案的用戶端 ID。</span><span class="sxs-lookup"><span data-stu-id="06524-424">The Client ID for this project.</span></span> <span data-ttu-id="06524-425">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-425">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="06524-426">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="06524-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="06524-427">目錄租戶的域。</span><span class="sxs-lookup"><span data-stu-id="06524-427">The domain for the directory tenant.</span></span> <span data-ttu-id="06524-428">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="06524-429">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="06524-429">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="06524-430">要連接到的目錄的租戶 ID ID。</span><span class="sxs-lookup"><span data-stu-id="06524-430">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="06524-431">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="06524-432">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="06524-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="06524-433">重定向URI的應用程式基本路徑中的請求路徑。</span><span class="sxs-lookup"><span data-stu-id="06524-433">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="06524-434">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-434">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="06524-435">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="06524-435">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="06524-436">允許此應用程式讀取訪問目錄。</span><span class="sxs-lookup"><span data-stu-id="06524-436">Allows this application read-access to the directory.</span></span> <span data-ttu-id="06524-437">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-437">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="06524-438">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="06524-438">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="06524-439">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="06524-439">Turns off HTTPS.</span></span> <span data-ttu-id="06524-440">僅當 、`Individual`或`IndividualB2C`未`SingleOrg``--auth`用於`MultiOrg`時 ,此選項才適用。</span><span class="sxs-lookup"><span data-stu-id="06524-440">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="06524-441">指定本地資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="06524-441">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="06524-442">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-442">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="06524-443">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-443">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="06524-444">Web</span><span class="sxs-lookup"><span data-stu-id="06524-444">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="06524-445">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="06524-445">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-446">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-446">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="06524-447">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="06524-447">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="06524-448">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="06524-448">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="06524-449">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="06524-449">SDK version</span></span> | <span data-ttu-id="06524-450">預設值</span><span class="sxs-lookup"><span data-stu-id="06524-450">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="06524-451">3.1</span><span class="sxs-lookup"><span data-stu-id="06524-451">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="06524-452">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-452">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="06524-453">2.1</span><span class="sxs-lookup"><span data-stu-id="06524-453">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="06524-454">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-454">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="06524-455">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="06524-455">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="06524-456">mvc, 網路應用</span><span class="sxs-lookup"><span data-stu-id="06524-456">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="06524-457">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="06524-457">The type of authentication to use.</span></span> <span data-ttu-id="06524-458">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="06524-458">The possible values are:</span></span>

  - <span data-ttu-id="06524-459">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="06524-459">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="06524-460">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-460">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="06524-461">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-461">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="06524-462">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-462">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="06524-463">`MultiOrg` - 多個租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-463">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="06524-464">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-464">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="06524-465">要連接到的 Azure 活動目錄 B2C 實體。</span><span class="sxs-lookup"><span data-stu-id="06524-465">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="06524-466">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-466">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="06524-467">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="06524-467">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="06524-468">此項目的登錄和註冊策略 ID。</span><span class="sxs-lookup"><span data-stu-id="06524-468">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="06524-469">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-469">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="06524-470">此專案的重置密碼策略 ID。</span><span class="sxs-lookup"><span data-stu-id="06524-470">The reset password policy ID for this project.</span></span> <span data-ttu-id="06524-471">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-471">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="06524-472">此項目的編輯設定檔策略 ID。</span><span class="sxs-lookup"><span data-stu-id="06524-472">The edit profile policy ID for this project.</span></span> <span data-ttu-id="06524-473">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-473">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="06524-474">要連接到的 Azure 活動目錄實例。</span><span class="sxs-lookup"><span data-stu-id="06524-474">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="06524-475">搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-475">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="06524-476">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="06524-476">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="06524-477">此專案的用戶端 ID。</span><span class="sxs-lookup"><span data-stu-id="06524-477">The Client ID for this project.</span></span> <span data-ttu-id="06524-478">搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-478">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="06524-479">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="06524-479">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="06524-480">目錄租戶的域。</span><span class="sxs-lookup"><span data-stu-id="06524-480">The domain for the directory tenant.</span></span> <span data-ttu-id="06524-481">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-481">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="06524-482">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="06524-482">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="06524-483">要連接到的目錄的租戶 ID ID。</span><span class="sxs-lookup"><span data-stu-id="06524-483">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="06524-484">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-484">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="06524-485">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="06524-485">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="06524-486">重定向URI的應用程式基本路徑中的請求路徑。</span><span class="sxs-lookup"><span data-stu-id="06524-486">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="06524-487">搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-487">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="06524-488">預設值是 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="06524-488">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="06524-489">允許此應用程式讀取訪問目錄。</span><span class="sxs-lookup"><span data-stu-id="06524-489">Allows this application read-access to the directory.</span></span> <span data-ttu-id="06524-490">僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-490">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="06524-491">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="06524-491">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="06524-492">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="06524-492">Turns off HTTPS.</span></span> <span data-ttu-id="06524-493">此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。</span><span class="sxs-lookup"><span data-stu-id="06524-493">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="06524-494">指定本地資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="06524-494">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="06524-495">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-495">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-496">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-496">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="06524-497">選項可用,因為 .NET 核心 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="06524-497">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="06524-498">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="06524-498">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="06524-499">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="06524-499">SDK version</span></span> | <span data-ttu-id="06524-500">預設值</span><span class="sxs-lookup"><span data-stu-id="06524-500">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="06524-501">3.1</span><span class="sxs-lookup"><span data-stu-id="06524-501">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="06524-502">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-502">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="06524-503">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-503">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="06524-504">在專案中包括瀏覽器連結。</span><span class="sxs-lookup"><span data-stu-id="06524-504">Includes BrowserLink in the project.</span></span> <span data-ttu-id="06524-505">選項在 .NET Core 2.2 和 3.1 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="06524-505">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="06524-506">決定項目是否設定為除錯產生中使用[Razor 執行時編譯](/aspnet/core/mvc/views/view-compilation#runtime-compilation)。</span><span class="sxs-lookup"><span data-stu-id="06524-506">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="06524-507">選項可用,因為 .NET 核心 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="06524-507">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="06524-508">角,反應</span><span class="sxs-lookup"><span data-stu-id="06524-508">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="06524-509">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="06524-509">The type of authentication to use.</span></span> <span data-ttu-id="06524-510">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="06524-510">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="06524-511">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="06524-511">The possible values are:</span></span>

  - <span data-ttu-id="06524-512">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="06524-512">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="06524-513">`Individual` - 個別驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-513">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="06524-514">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="06524-514">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="06524-515">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-515">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="06524-516">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="06524-516">Turns off HTTPS.</span></span> <span data-ttu-id="06524-517">僅當身份驗證為`None`時,此選項才適用。</span><span class="sxs-lookup"><span data-stu-id="06524-517">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="06524-518">指定本地資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="06524-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="06524-519">僅適用於 `Individual` 或 `IndividualB2C` 驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="06524-520">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="06524-520">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-521">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-521">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="06524-522">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="06524-522">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="06524-523">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="06524-523">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="06524-524">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="06524-524">SDK version</span></span> | <span data-ttu-id="06524-525">預設值</span><span class="sxs-lookup"><span data-stu-id="06524-525">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="06524-526">3.1</span><span class="sxs-lookup"><span data-stu-id="06524-526">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="06524-527">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-527">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="06524-528">2.1</span><span class="sxs-lookup"><span data-stu-id="06524-528">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="06524-529">reactredux</span><span class="sxs-lookup"><span data-stu-id="06524-529">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="06524-530">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="06524-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-531">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="06524-532">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="06524-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="06524-533">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="06524-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="06524-534">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="06524-534">SDK version</span></span> | <span data-ttu-id="06524-535">預設值</span><span class="sxs-lookup"><span data-stu-id="06524-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="06524-536">3.1</span><span class="sxs-lookup"><span data-stu-id="06524-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="06524-537">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="06524-538">2.1</span><span class="sxs-lookup"><span data-stu-id="06524-538">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="06524-539">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="06524-540">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="06524-540">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="06524-541">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="06524-541">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="06524-542">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-542">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="06524-543">除了元件添加到此庫之外,還支援添加傳統的 Razor 頁面和檢視。</span><span class="sxs-lookup"><span data-stu-id="06524-543">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="06524-544">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="06524-544">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="06524-545">webapi</span><span class="sxs-lookup"><span data-stu-id="06524-545">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="06524-546">要使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="06524-546">The type of authentication to use.</span></span> <span data-ttu-id="06524-547">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="06524-547">The possible values are:</span></span>

  - <span data-ttu-id="06524-548">`None` - 無驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="06524-548">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="06524-549">`IndividualB2C` - 使用 Azure AD B2C 的個別驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-549">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="06524-550">`SingleOrg` - 單一租用戶的組織驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-550">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="06524-551">`Windows` - Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="06524-552">要連接到的 Azure 活動目錄 B2C 實體。</span><span class="sxs-lookup"><span data-stu-id="06524-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="06524-553">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="06524-554">預設值是 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="06524-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="06524-555">此項目的登錄和註冊策略 ID。</span><span class="sxs-lookup"><span data-stu-id="06524-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="06524-556">搭配 `IndividualB2C` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-556">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="06524-557">要連接到的 Azure 活動目錄實例。</span><span class="sxs-lookup"><span data-stu-id="06524-557">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="06524-558">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="06524-559">預設值是 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="06524-559">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="06524-560">此專案的用戶端 ID。</span><span class="sxs-lookup"><span data-stu-id="06524-560">The Client ID for this project.</span></span> <span data-ttu-id="06524-561">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="06524-562">預設值是 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="06524-562">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="06524-563">目錄租戶的域。</span><span class="sxs-lookup"><span data-stu-id="06524-563">The domain for the directory tenant.</span></span> <span data-ttu-id="06524-564">搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-564">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="06524-565">預設值是 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="06524-565">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="06524-566">要連接到的目錄的租戶 ID ID。</span><span class="sxs-lookup"><span data-stu-id="06524-566">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="06524-567">搭配 `SingleOrg` 驗證使用。</span><span class="sxs-lookup"><span data-stu-id="06524-567">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="06524-568">預設值是 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="06524-568">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="06524-569">允許此應用程式讀取訪問目錄。</span><span class="sxs-lookup"><span data-stu-id="06524-569">Allows this application read-access to the directory.</span></span> <span data-ttu-id="06524-570">僅適用於`SingleOrg`身份驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-570">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="06524-571">從生成的範本中排除*啟動設置.json。*</span><span class="sxs-lookup"><span data-stu-id="06524-571">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="06524-572">關閉 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="06524-572">Turns off HTTPS.</span></span> <span data-ttu-id="06524-573">`app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。</span><span class="sxs-lookup"><span data-stu-id="06524-573">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="06524-574">此選項僅適用於或不`SingleOrg`用於身份`IndividualB2C`驗證 時。</span><span class="sxs-lookup"><span data-stu-id="06524-574">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="06524-575">指定本地資料庫應使用而不是 SQLite。</span><span class="sxs-lookup"><span data-stu-id="06524-575">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="06524-576">僅適用於`IndividualB2C`身份驗證。</span><span class="sxs-lookup"><span data-stu-id="06524-576">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="06524-577">指定要定位[的框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="06524-577">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="06524-578">選項在 .NET 核心 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="06524-578">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="06524-579">下表根據您使用的 SDK 版本號列出預設值:</span><span class="sxs-lookup"><span data-stu-id="06524-579">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="06524-580">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="06524-580">SDK version</span></span> | <span data-ttu-id="06524-581">預設值</span><span class="sxs-lookup"><span data-stu-id="06524-581">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="06524-582">3.1</span><span class="sxs-lookup"><span data-stu-id="06524-582">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="06524-583">3.0</span><span class="sxs-lookup"><span data-stu-id="06524-583">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="06524-584">2.1</span><span class="sxs-lookup"><span data-stu-id="06524-584">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="06524-585">在項目創建期間不執行隱式還原。</span><span class="sxs-lookup"><span data-stu-id="06524-585">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="06524-586">globaljson</span><span class="sxs-lookup"><span data-stu-id="06524-586">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="06524-587">指定要在*global.json*檔中使用的 .NET Core SDK 的版本。</span><span class="sxs-lookup"><span data-stu-id="06524-587">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="06524-588">範例</span><span class="sxs-lookup"><span data-stu-id="06524-588">Examples</span></span>

- <span data-ttu-id="06524-589">藉由指定範本名稱，建立 C# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="06524-589">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="06524-590">在目前的目錄中建立 F# 主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="06524-590">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="06524-591">在指定的目錄中建立 .NET 標準類別庫專案:</span><span class="sxs-lookup"><span data-stu-id="06524-591">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="06524-592">未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：</span><span class="sxs-lookup"><span data-stu-id="06524-592">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="06524-593">建立新的 xUnit 專案：</span><span class="sxs-lookup"><span data-stu-id="06524-593">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="06524-594">列出可用於單頁應用程式 (SPA) 樣本的所有樣本:</span><span class="sxs-lookup"><span data-stu-id="06524-594">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="06524-595">列出所有符合 *we* 子字串的範本。</span><span class="sxs-lookup"><span data-stu-id="06524-595">List all templates matching the *we* substring.</span></span> <span data-ttu-id="06524-596">找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。</span><span class="sxs-lookup"><span data-stu-id="06524-596">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="06524-597">嘗試叫用符合 *ng* 的範本。</span><span class="sxs-lookup"><span data-stu-id="06524-597">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="06524-598">如果無法判別單一相符項目，則列出部分相符的範本。</span><span class="sxs-lookup"><span data-stu-id="06524-598">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="06524-599">安裝 ASP.NET核心的 SPA 樣本版本 2.0:</span><span class="sxs-lookup"><span data-stu-id="06524-599">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="06524-600">列出已安裝的範本及其詳細資訊,包括如何卸載它們:</span><span class="sxs-lookup"><span data-stu-id="06524-600">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="06524-601">在目前的目錄中建立*全域.json*將 SDK 版本設定為 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="06524-601">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="06524-602">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06524-602">See also</span></span>

- [<span data-ttu-id="06524-603">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="06524-603">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="06524-604">建立適用於 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="06524-604">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- <span data-ttu-id="06524-605">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="06524-605">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="06524-606">dotnet new 的可用範本</span><span class="sxs-lookup"><span data-stu-id="06524-606">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
