---
title: .NET Core 3.1 的新功能
description: 深入瞭解 .NET Core 3.1 中的新功能。
dev_langs:
- csharp
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 42d4f7e8800bf2d13d584084f8a41bad2ada534f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608129"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="b26ff-103">.NET Core 3.1 的新功能</span><span class="sxs-lookup"><span data-stu-id="b26ff-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="b26ff-104">本文說明 .NET Core 3.1 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="b26ff-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="b26ff-105">此版本包含 .NET Core 3.0 的微小改進，著重于小型但重要的修正程式。</span><span class="sxs-lookup"><span data-stu-id="b26ff-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="b26ff-106">.NET Core 3.1 最重要的功能是 [ (LTS) 版本的長期支援 ](#long-term-support) 。</span><span class="sxs-lookup"><span data-stu-id="b26ff-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="b26ff-107">如果您使用 Visual Studio 2019，則必須更新至 [Visual Studio 2019 16.4 版或更新版本](https://visualstudio.microsoft.com/downloads/) ，才能使用 .net Core 3.1 專案。</span><span class="sxs-lookup"><span data-stu-id="b26ff-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4 or later](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="b26ff-108">如需 Visual Studio 16.4 版新功能的詳細資訊，請參閱 [Visual Studio 2019 16.4 版中的新功能](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164)。</span><span class="sxs-lookup"><span data-stu-id="b26ff-108">For information on what's new in Visual Studio version 16.4, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="b26ff-109">Visual Studio for Mac 也支援並包含 Visual Studio for Mac 8.4 中的 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="b26ff-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="b26ff-110">如需版本的詳細資訊，請參閱 [.Net Core 3.1 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。</span><span class="sxs-lookup"><span data-stu-id="b26ff-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="b26ff-111">在 Windows、macOS 或 Linux 上[下載並開始使用 .Net Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) 。</span><span class="sxs-lookup"><span data-stu-id="b26ff-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="b26ff-112">長期支援</span><span class="sxs-lookup"><span data-stu-id="b26ff-112">Long-term support</span></span>

<span data-ttu-id="b26ff-113">.NET Core 3.1 是 LTS 版本，可在未來三年提供 Microsoft 的支援。</span><span class="sxs-lookup"><span data-stu-id="b26ff-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="b26ff-114">強烈建議您將應用程式移至 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="b26ff-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="b26ff-115">其他主要版本的目前生命週期如下所示：</span><span class="sxs-lookup"><span data-stu-id="b26ff-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="b26ff-116">版本</span><span class="sxs-lookup"><span data-stu-id="b26ff-116">Release</span></span> | <span data-ttu-id="b26ff-117">附註</span><span class="sxs-lookup"><span data-stu-id="b26ff-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="b26ff-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b26ff-118">.NET Core 3.0</span></span> | <span data-ttu-id="b26ff-119">2020年3月3日結束生命週期。</span><span class="sxs-lookup"><span data-stu-id="b26ff-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="b26ff-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b26ff-120">.NET Core 2.2</span></span> | <span data-ttu-id="b26ff-121">2019年12月23日結束生命週期。</span><span class="sxs-lookup"><span data-stu-id="b26ff-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="b26ff-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b26ff-122">.NET Core 2.1</span></span> | <span data-ttu-id="b26ff-123">2021年8月21日結束生命週期。</span><span class="sxs-lookup"><span data-stu-id="b26ff-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="b26ff-124">如需詳細資訊，請參閱 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="b26ff-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="b26ff-125">macOS appHost 和公證</span><span class="sxs-lookup"><span data-stu-id="b26ff-125">macOS appHost and notarization</span></span>

<span data-ttu-id="b26ff-126">*僅限 macOS*</span><span class="sxs-lookup"><span data-stu-id="b26ff-126">*macOS only*</span></span>

<span data-ttu-id="b26ff-127">從適用于 macOS 的公證 .NET Core SDK 3.1 開始，預設會停用 appHost 設定。</span><span class="sxs-lookup"><span data-stu-id="b26ff-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="b26ff-128">如需詳細資訊，請參閱 [MacOS Catalina 公證和 .Net Core 下載和專案的影響](../install/macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="b26ff-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="b26ff-129">當 appHost 設定啟用時，.NET Core 會在您建立或發行時產生原生的符合-O 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="b26ff-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="b26ff-130">當您的應用程式從使用命令的原始程式碼執行 `dotnet run` ，或直接啟動符合-O 可執行檔時，您的應用程式會在 appHost 的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="b26ff-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="b26ff-131">如果沒有 appHost，使用者就可以使用命令來啟動與 [framework 相依](../deploying/index.md#publish-framework-dependent) 的應用程式 `dotnet <filename.dll>` 。</span><span class="sxs-lookup"><span data-stu-id="b26ff-131">Without the appHost, the only way a user can start a [framework-dependent](../deploying/index.md#publish-framework-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="b26ff-132">當您發行 [獨立](../deploying/index.md#publish-self-contained)應用程式時，一律會建立 appHost。</span><span class="sxs-lookup"><span data-stu-id="b26ff-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="b26ff-133">您可以在專案層級設定 appHost，或使用參數切換特定命令的 appHost `dotnet` `-p:UseAppHost` ：</span><span class="sxs-lookup"><span data-stu-id="b26ff-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="b26ff-134">專案檔</span><span class="sxs-lookup"><span data-stu-id="b26ff-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="b26ff-135">命令列參數</span><span class="sxs-lookup"><span data-stu-id="b26ff-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="b26ff-136">如需有關此設定的詳細資訊 `UseAppHost` ，請參閱 [適用于 Microsoft .Net 的 MSBuild 屬性](../project-sdk/msbuild-props.md#useapphost)。</span><span class="sxs-lookup"><span data-stu-id="b26ff-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="b26ff-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b26ff-137">Windows Forms</span></span>

<span data-ttu-id="b26ff-138">*僅限 Windows*</span><span class="sxs-lookup"><span data-stu-id="b26ff-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="b26ff-139">Windows Forms 中有重大變更。</span><span class="sxs-lookup"><span data-stu-id="b26ff-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="b26ff-140">舊版控制項已包含在 Visual Studio 設計工具工具箱中無法使用的 Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="b26ff-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="b26ff-141">這些已取代為 .NET Framework 2.0 中的新控制項。</span><span class="sxs-lookup"><span data-stu-id="b26ff-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="b26ff-142">這些已從適用于 .NET Core 3.1 的桌面 SDK 移除。</span><span class="sxs-lookup"><span data-stu-id="b26ff-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="b26ff-143">已移除控制項</span><span class="sxs-lookup"><span data-stu-id="b26ff-143">Removed control</span></span> | <span data-ttu-id="b26ff-144">建議取代</span><span class="sxs-lookup"><span data-stu-id="b26ff-144">Recommended replacement</span></span> | <span data-ttu-id="b26ff-145">已移除相關聯的 Api</span><span class="sxs-lookup"><span data-stu-id="b26ff-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="b26ff-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="b26ff-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="b26ff-147">DataGridCell</span><span class="sxs-lookup"><span data-stu-id="b26ff-147">DataGridCell</span></span><br/><span data-ttu-id="b26ff-148">DataGridRow</span><span class="sxs-lookup"><span data-stu-id="b26ff-148">DataGridRow</span></span><br/><span data-ttu-id="b26ff-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="b26ff-149">DataGridTableCollection</span></span><br/><span data-ttu-id="b26ff-150">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="b26ff-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="b26ff-151">DataGridTableStyle</span><span class="sxs-lookup"><span data-stu-id="b26ff-151">DataGridTableStyle</span></span><br/><span data-ttu-id="b26ff-152">System.windows.forms.datagridcolumnstyle></span><span class="sxs-lookup"><span data-stu-id="b26ff-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="b26ff-153">DataGridLineStyle</span><span class="sxs-lookup"><span data-stu-id="b26ff-153">DataGridLineStyle</span></span><br/><span data-ttu-id="b26ff-154">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="b26ff-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="b26ff-155">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="b26ff-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="b26ff-156">DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="b26ff-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="b26ff-157">DataGridTextBox</span><span class="sxs-lookup"><span data-stu-id="b26ff-157">DataGridTextBox</span></span><br/><span data-ttu-id="b26ff-158">System.windows.forms.gridcolumnstylescollection></span><span class="sxs-lookup"><span data-stu-id="b26ff-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="b26ff-159">System.windows.forms.gridtablestylescollection></span><span class="sxs-lookup"><span data-stu-id="b26ff-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="b26ff-160">HitTestType</span><span class="sxs-lookup"><span data-stu-id="b26ff-160">HitTestType</span></span> |
| <span data-ttu-id="b26ff-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="b26ff-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="b26ff-162">System.windows.forms.toolbar.appearance</span><span class="sxs-lookup"><span data-stu-id="b26ff-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="b26ff-163">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="b26ff-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="b26ff-164">System.windows.forms.toolbarbuttonclickeventargs></span><span class="sxs-lookup"><span data-stu-id="b26ff-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="b26ff-165">ToolBarButtonClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="b26ff-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="b26ff-166">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="b26ff-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="b26ff-167">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="b26ff-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="b26ff-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="b26ff-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="b26ff-169">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="b26ff-169">MenuItemCollection</span></span> |
| <span data-ttu-id="b26ff-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="b26ff-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="b26ff-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="b26ff-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="b26ff-172">建議您將應用程式更新為 .NET Core 3.1，並移至取代控制項。</span><span class="sxs-lookup"><span data-stu-id="b26ff-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="b26ff-173">取代控制項是一個簡單的程式，基本上是「尋找和取代」型別。</span><span class="sxs-lookup"><span data-stu-id="b26ff-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="b26ff-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="b26ff-174">C++/CLI</span></span>

<span data-ttu-id="b26ff-175">*僅限 Windows*</span><span class="sxs-lookup"><span data-stu-id="b26ff-175">*Windows only*</span></span>

<span data-ttu-id="b26ff-176">已加入支援，以建立 c + +/CLI (也稱為「managed c + +」 ) 專案。</span><span class="sxs-lookup"><span data-stu-id="b26ff-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="b26ff-177">這些專案所產生的二進位檔會與 .NET Core 3.0 和更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="b26ff-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="b26ff-178">若要在 Visual Studio 2019 16.4 版中加入 c + +/CLI 的支援，請安裝 [使用 c + + 的桌面開發工作負載](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)。</span><span class="sxs-lookup"><span data-stu-id="b26ff-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="b26ff-179">此工作負載會將兩個範本新增至 Visual Studio：</span><span class="sxs-lookup"><span data-stu-id="b26ff-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="b26ff-180">CLR 類別庫 ( .NET Core) </span><span class="sxs-lookup"><span data-stu-id="b26ff-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="b26ff-181">CLR 空專案 ( .NET Core) </span><span class="sxs-lookup"><span data-stu-id="b26ff-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="b26ff-182">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b26ff-182">Next steps</span></span>

- [<span data-ttu-id="b26ff-183">查看 .NET Core 3.0 和3.1 之間的重大變更。</span><span class="sxs-lookup"><span data-stu-id="b26ff-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="b26ff-184">查看 .NET Core 3.1 中 Windows Forms 應用程式的重大變更。</span><span class="sxs-lookup"><span data-stu-id="b26ff-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
