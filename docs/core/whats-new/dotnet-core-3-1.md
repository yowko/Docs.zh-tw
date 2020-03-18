---
title: .NET Core 3.1 的新功能
description: 瞭解 .NET 核心 3.1 中的新功能。
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 323a2390f079c17b81db01e4e3787916251943bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156552"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="2a8f4-103">.NET Core 3.1 的新功能</span><span class="sxs-lookup"><span data-stu-id="2a8f4-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="2a8f4-104">本文介紹了 .NET Core 3.1 中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="2a8f4-105">此版本包含對 .NET Core 3.0 的一些改進，重點關注小型但重要的修補程式。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="2a8f4-106">關於 .NET Core 3.1 最重要的功能是它是[長期支援 （LTS）](#long-term-support)版本。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="2a8f4-107">如果您使用的是 Visual Studio 2019，則必須更新到[Visual Studio 2019 版本 16.4](https://visualstudio.microsoft.com/downloads/)才能使用 .NET Core 3.1 專案。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="2a8f4-108">有關 Visual Studio 中的新增功能的詳細資訊，請參閱[Visual Studio 2019 版 16.4 中的新增功能](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164)。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-108">For more information on what's new in Visual Studio, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="2a8f4-109">適用于 Mac 的視覺化工作室還支援並包括 Mac 8.4 視覺工作室中的 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="2a8f4-110">有關該版本的詳細資訊，請參閱[.NET Core 3.1 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="2a8f4-111">在 Windows、macOS 或 Linux 上[下載並開始使用 .NET 酷睿 3.1。](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="2a8f4-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="2a8f4-112">長期支援</span><span class="sxs-lookup"><span data-stu-id="2a8f4-112">Long-term support</span></span>

<span data-ttu-id="2a8f4-113">.NET Core 3.1 是一個 LTS 版本，支援微軟未來三年。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="2a8f4-114">強烈建議您將應用移動到 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="2a8f4-115">其他主要版本的當前生命週期如下：</span><span class="sxs-lookup"><span data-stu-id="2a8f4-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="2a8f4-116">版本</span><span class="sxs-lookup"><span data-stu-id="2a8f4-116">Release</span></span> | <span data-ttu-id="2a8f4-117">附註</span><span class="sxs-lookup"><span data-stu-id="2a8f4-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="2a8f4-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2a8f4-118">.NET Core 3.0</span></span> | <span data-ttu-id="2a8f4-119">2020年3月3日結束。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="2a8f4-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2a8f4-120">.NET Core 2.2</span></span> | <span data-ttu-id="2a8f4-121">2019 年 12 月 23 日結束。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="2a8f4-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2a8f4-122">.NET Core 2.1</span></span> | <span data-ttu-id="2a8f4-123">2021年8月21日生命終結。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="2a8f4-124">有關詳細資訊，請參閱[.NET 核心支援策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="2a8f4-125">macOS 應用程式Host 和公證</span><span class="sxs-lookup"><span data-stu-id="2a8f4-125">macOS appHost and notarization</span></span>

<span data-ttu-id="2a8f4-126">*僅限 macOS*</span><span class="sxs-lookup"><span data-stu-id="2a8f4-126">*macOS only*</span></span>

<span data-ttu-id="2a8f4-127">從 macOS 的公證 .NET Core SDK 3.1 開始，預設情況下將禁用 appHost 設置。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="2a8f4-128">有關詳細資訊，請參閱[macOS Catalina 公證及其對 .NET 核心下載和專案的影響](../install/macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="2a8f4-129">啟用應用Host設置後，.NET Core 會在生成或發佈時生成本機 Mach-O 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="2a8f4-130">當應用從帶有`dotnet run`該命令的原始程式碼運行時，或者直接啟動 Mach-O 可執行檔，則應用在 appHost 的上下文中運行。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="2a8f4-131">如果沒有 appHost，使用者可以啟動[與運行時相關的](../deploying/index.md#publish-runtime-dependent)應用的唯一方法是使用 該`dotnet <filename.dll>`命令。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-131">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="2a8f4-132">發佈應用[自包含](../deploying/index.md#publish-self-contained)時，始終會創建應用Host。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="2a8f4-133">您可以在專案級別配置 appHost，也可以使用`dotnet``-p:UseAppHost`參數切換特定命令的應用Host：</span><span class="sxs-lookup"><span data-stu-id="2a8f4-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="2a8f4-134">專案檔</span><span class="sxs-lookup"><span data-stu-id="2a8f4-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="2a8f4-135">命令列參數</span><span class="sxs-lookup"><span data-stu-id="2a8f4-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="2a8f4-136">有關該`UseAppHost`設置的詳細資訊，請參閱[Microsoft.NET.Sdk 的 MSBuild 屬性](../project-sdk/msbuild-props.md#useapphost)。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="2a8f4-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a8f4-137">Windows Forms</span></span>

<span data-ttu-id="2a8f4-138">*僅限 Windows*</span><span class="sxs-lookup"><span data-stu-id="2a8f4-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="2a8f4-139">Windows 表單中有重大更改。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="2a8f4-140">舊版控制項包含在 Visual Studio 設計器工具箱中已不可用的 Windows 表單中。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="2a8f4-141">這些控制項被重新替換在 .NET 框架 2.0 中。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="2a8f4-142">這些已從 .NET 核心 3.1 的桌面 SDK 中刪除。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="2a8f4-143">已刪除控制項</span><span class="sxs-lookup"><span data-stu-id="2a8f4-143">Removed control</span></span> | <span data-ttu-id="2a8f4-144">推薦更換</span><span class="sxs-lookup"><span data-stu-id="2a8f4-144">Recommended replacement</span></span> | <span data-ttu-id="2a8f4-145">已刪除關聯的 API</span><span class="sxs-lookup"><span data-stu-id="2a8f4-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="2a8f4-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="2a8f4-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="2a8f4-147">資料網格塞爾</span><span class="sxs-lookup"><span data-stu-id="2a8f4-147">DataGridCell</span></span><br/><span data-ttu-id="2a8f4-148">資料網格行</span><span class="sxs-lookup"><span data-stu-id="2a8f4-148">DataGridRow</span></span><br/><span data-ttu-id="2a8f4-149">資料網格表收集</span><span class="sxs-lookup"><span data-stu-id="2a8f4-149">DataGridTableCollection</span></span><br/><span data-ttu-id="2a8f4-150">資料網格列集合</span><span class="sxs-lookup"><span data-stu-id="2a8f4-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="2a8f4-151">資料網格表樣式</span><span class="sxs-lookup"><span data-stu-id="2a8f4-151">DataGridTableStyle</span></span><br/><span data-ttu-id="2a8f4-152">資料網格列線樣式</span><span class="sxs-lookup"><span data-stu-id="2a8f4-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="2a8f4-153">資料格線樣式</span><span class="sxs-lookup"><span data-stu-id="2a8f4-153">DataGridLineStyle</span></span><br/><span data-ttu-id="2a8f4-154">資料網格父行標籤</span><span class="sxs-lookup"><span data-stu-id="2a8f4-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="2a8f4-155">資料網格父行標籤樣式</span><span class="sxs-lookup"><span data-stu-id="2a8f4-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="2a8f4-156">資料網格布林柱</span><span class="sxs-lookup"><span data-stu-id="2a8f4-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="2a8f4-157">資料網格文字方塊</span><span class="sxs-lookup"><span data-stu-id="2a8f4-157">DataGridTextBox</span></span><br/><span data-ttu-id="2a8f4-158">網格柱樣式集合</span><span class="sxs-lookup"><span data-stu-id="2a8f4-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="2a8f4-159">網格表樣式集合</span><span class="sxs-lookup"><span data-stu-id="2a8f4-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="2a8f4-160">點擊測試類型</span><span class="sxs-lookup"><span data-stu-id="2a8f4-160">HitTestType</span></span> |
| <span data-ttu-id="2a8f4-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="2a8f4-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="2a8f4-162">工具列外觀</span><span class="sxs-lookup"><span data-stu-id="2a8f4-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="2a8f4-163">工具列按鈕</span><span class="sxs-lookup"><span data-stu-id="2a8f4-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="2a8f4-164">工具列點擊事件</span><span class="sxs-lookup"><span data-stu-id="2a8f4-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="2a8f4-165">工具列按鈕按一下事件處理常式</span><span class="sxs-lookup"><span data-stu-id="2a8f4-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="2a8f4-166">工具列按鈕樣式</span><span class="sxs-lookup"><span data-stu-id="2a8f4-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="2a8f4-167">工具列文本對齊</span><span class="sxs-lookup"><span data-stu-id="2a8f4-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="2a8f4-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="2a8f4-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="2a8f4-169">功能表項目目集合</span><span class="sxs-lookup"><span data-stu-id="2a8f4-169">MenuItemCollection</span></span> |
| <span data-ttu-id="2a8f4-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="2a8f4-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="2a8f4-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="2a8f4-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="2a8f4-172">我們建議您將應用程式更新為 .NET Core 3.1 並移動到替換控制項。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="2a8f4-173">替換控制項是一個簡單明瞭的過程，實質上是"查找和替換"的類型。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="2a8f4-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="2a8f4-174">C++/CLI</span></span>

<span data-ttu-id="2a8f4-175">*僅限 Windows*</span><span class="sxs-lookup"><span data-stu-id="2a8f4-175">*Windows only*</span></span>

<span data-ttu-id="2a8f4-176">已添加用於創建C++/CLI（也稱為"託管C++"）專案的支援。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="2a8f4-177">這些專案生成的二進位檔案與 .NET Core 3.0 和更高版本相容。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="2a8f4-178">要在 Visual Studio 2019 版本 16.4 中添加對 C++/CLI 的支援，請使用[C++工作負載安裝桌面開發](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="2a8f4-179">此工作負載向視覺化工作室添加了兩個範本：</span><span class="sxs-lookup"><span data-stu-id="2a8f4-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="2a8f4-180">CLR 類庫 （.NET 核心）</span><span class="sxs-lookup"><span data-stu-id="2a8f4-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="2a8f4-181">CLR 空專案 （.NET 核心）</span><span class="sxs-lookup"><span data-stu-id="2a8f4-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="2a8f4-182">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2a8f4-182">Next steps</span></span>

- [<span data-ttu-id="2a8f4-183">查看 .NET 核心 3.0 和 3.1 之間的重大更改。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="2a8f4-184">查看 .NET Core 3.1 中 Windows 表單應用的重大變化。</span><span class="sxs-lookup"><span data-stu-id="2a8f4-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
