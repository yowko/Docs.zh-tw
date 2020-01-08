---
title: .NET Core 3.1 的新功能
description: 深入瞭解 .NET Core 3.1 中的新功能。
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a9f47c2909375251460b45792822e491d56fb242
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342855"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="b7f1d-103">.NET Core 3.1 的新功能</span><span class="sxs-lookup"><span data-stu-id="b7f1d-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="b7f1d-104">本文說明 .NET Core 3.1 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="b7f1d-105">此版本包含 .NET Core 3.0 的次要改良功能，著重于小型但重要的修正程式。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="b7f1d-106">.NET Core 3.1 最重要的功能是，它是[長期支援（LTS）](#long-term-support)版本。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="b7f1d-107">如果您使用 Visual Studio 2019，您必須更新為[Visual Studio 2019 16.4 版](https://visualstudio.microsoft.com/downloads/)，才能使用 .net Core 3.1 專案。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="b7f1d-108">如需 Visual Studio 新功能的詳細資訊，請參閱[Visual Studio 的 Blog](https://devblogs.microsoft.com/visualstudio/tis-the-season-visual-studio-2019/)。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-108">For more information on what is new in Visual Studio, see the [Visual Studio Blog](https://devblogs.microsoft.com/visualstudio/tis-the-season-visual-studio-2019/).</span></span>

<span data-ttu-id="b7f1d-109">Visual Studio for Mac 也支援 Visual Studio for Mac 8.4 Preview 通道中的 .NET Core 3.1，並將其包含在其中。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-109">Visual Studio for Mac also supports and includes .NET Core 3.1, in the Visual Studio for Mac 8.4 Preview channel.</span></span> <span data-ttu-id="b7f1d-110">您必須加入宣告預覽頻道，才能使用 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-110">You'll need to opt into the Preview channel to use .NET Core 3.1.</span></span>

<span data-ttu-id="b7f1d-111">如需版本的詳細資訊，請參閱[.Net Core 3.1 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-111">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="b7f1d-112">下載 Windows、macOS 或 Linux 上[的 .Net Core 3.1 並開始使用](https://dotnet.microsoft.com/download/dotnet-core/3.1)。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-112">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="b7f1d-113">長期支援</span><span class="sxs-lookup"><span data-stu-id="b7f1d-113">Long-term support</span></span>

<span data-ttu-id="b7f1d-114">.NET Core 3.1 是 LTS 版本，在接下來的三年來提供 Microsoft 支援。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-114">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="b7f1d-115">強烈建議您將應用程式移至 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-115">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="b7f1d-116">其他主要版本的目前生命週期如下所示：</span><span class="sxs-lookup"><span data-stu-id="b7f1d-116">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="b7f1d-117">Release</span><span class="sxs-lookup"><span data-stu-id="b7f1d-117">Release</span></span> | <span data-ttu-id="b7f1d-118">注意</span><span class="sxs-lookup"><span data-stu-id="b7f1d-118">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="b7f1d-119">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b7f1d-119">.NET Core 3.0</span></span> | <span data-ttu-id="b7f1d-120">2020年3月3日結束生命週期。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-120">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="b7f1d-121">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b7f1d-121">.NET Core 2.2</span></span> | <span data-ttu-id="b7f1d-122">2019年12月23日結束生命週期。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-122">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="b7f1d-123">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b7f1d-123">.NET Core 2.1</span></span> | <span data-ttu-id="b7f1d-124">2021年8月21日結束生命週期。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-124">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="b7f1d-125">如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-125">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="b7f1d-126">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="b7f1d-126">Windows Forms</span></span>

<span data-ttu-id="b7f1d-127">*僅限 Windows*</span><span class="sxs-lookup"><span data-stu-id="b7f1d-127">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="b7f1d-128">Windows Forms 中有重大變更。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-128">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="b7f1d-129">舊版控制項已包含在 Visual Studio 設計工具工具箱中無法使用的 Windows Forms 中。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-129">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="b7f1d-130">這些已取代為 .NET Framework 2.0 中的新控制項。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-130">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="b7f1d-131">這些已從適用于 .NET Core 3.1 的桌面 SDK 移除。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-131">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="b7f1d-132">已移除控制項</span><span class="sxs-lookup"><span data-stu-id="b7f1d-132">Removed control</span></span> | <span data-ttu-id="b7f1d-133">建議取代</span><span class="sxs-lookup"><span data-stu-id="b7f1d-133">Recommended replacement</span></span> | <span data-ttu-id="b7f1d-134">已移除相關聯的 Api</span><span class="sxs-lookup"><span data-stu-id="b7f1d-134">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="b7f1d-135">DataGrid</span><span class="sxs-lookup"><span data-stu-id="b7f1d-135">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="b7f1d-136">DataGridCell</span><span class="sxs-lookup"><span data-stu-id="b7f1d-136">DataGridCell</span></span><br/><span data-ttu-id="b7f1d-137">DataGridRow</span><span class="sxs-lookup"><span data-stu-id="b7f1d-137">DataGridRow</span></span><br/><span data-ttu-id="b7f1d-138">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="b7f1d-138">DataGridTableCollection</span></span><br/><span data-ttu-id="b7f1d-139">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="b7f1d-139">DataGridColumnCollection</span></span><br/><span data-ttu-id="b7f1d-140">DataGridTableStyle</span><span class="sxs-lookup"><span data-stu-id="b7f1d-140">DataGridTableStyle</span></span><br/><span data-ttu-id="b7f1d-141">System.windows.forms.datagridcolumnstyle></span><span class="sxs-lookup"><span data-stu-id="b7f1d-141">DataGridColumnStyle</span></span><br/><span data-ttu-id="b7f1d-142">DataGridLineStyle</span><span class="sxs-lookup"><span data-stu-id="b7f1d-142">DataGridLineStyle</span></span><br/><span data-ttu-id="b7f1d-143">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="b7f1d-143">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="b7f1d-144">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="b7f1d-144">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="b7f1d-145">DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="b7f1d-145">DataGridBoolColumn</span></span><br/><span data-ttu-id="b7f1d-146">DataGridTextBox</span><span class="sxs-lookup"><span data-stu-id="b7f1d-146">DataGridTextBox</span></span><br/><span data-ttu-id="b7f1d-147">System.windows.forms.gridcolumnstylescollection></span><span class="sxs-lookup"><span data-stu-id="b7f1d-147">GridColumnStylesCollection</span></span><br/><span data-ttu-id="b7f1d-148">System.windows.forms.gridtablestylescollection></span><span class="sxs-lookup"><span data-stu-id="b7f1d-148">GridTableStylesCollection</span></span><br/><span data-ttu-id="b7f1d-149">HitTestType</span><span class="sxs-lookup"><span data-stu-id="b7f1d-149">HitTestType</span></span> |
| <span data-ttu-id="b7f1d-150">ToolBar</span><span class="sxs-lookup"><span data-stu-id="b7f1d-150">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="b7f1d-151">System.windows.forms.toolbar.appearance</span><span class="sxs-lookup"><span data-stu-id="b7f1d-151">ToolBarAppearance</span></span> |
| <span data-ttu-id="b7f1d-152">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="b7f1d-152">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="b7f1d-153">System.windows.forms.toolbarbuttonclickeventargs></span><span class="sxs-lookup"><span data-stu-id="b7f1d-153">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="b7f1d-154">ToolBarButtonClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="b7f1d-154">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="b7f1d-155">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="b7f1d-155">ToolBarButtonStyle</span></span><br/><span data-ttu-id="b7f1d-156">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="b7f1d-156">ToolBarTextAlign</span></span> |
| <span data-ttu-id="b7f1d-157">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="b7f1d-157">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="b7f1d-158">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="b7f1d-158">MenuItemCollection</span></span> |
| <span data-ttu-id="b7f1d-159">MainMenu</span><span class="sxs-lookup"><span data-stu-id="b7f1d-159">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="b7f1d-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="b7f1d-160">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="b7f1d-161">我們建議您將應用程式更新為 .NET Core 3.1，並移至取代控制項。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-161">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="b7f1d-162">取代控制項是直接的程式，基本上是「尋找和取代」類型。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-162">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="b7f1d-163">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="b7f1d-163">C++/CLI</span></span>

<span data-ttu-id="b7f1d-164">*僅限 Windows*</span><span class="sxs-lookup"><span data-stu-id="b7f1d-164">*Windows only*</span></span>

<span data-ttu-id="b7f1d-165">已新增建立C++/cli （也稱為「受控C++」）專案的支援。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-165">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="b7f1d-166">從這些專案產生的二進位檔與 .NET Core 3.0 和更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-166">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="b7f1d-167">若要在 Visual Studio C++2019 16.4 中新增對/cli 的支援，請[使用C++工作負載安裝桌面開發](https://docs.microsoft.com/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-167">To add support for C++/CLI in Visual Studio 2019 16.4, install the [Desktop development with C++ workload](https://docs.microsoft.com/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="b7f1d-168">此工作負載會在 Visual Studio 中新增兩個範本：</span><span class="sxs-lookup"><span data-stu-id="b7f1d-168">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="b7f1d-169">CLR 類別庫（.NET Core）</span><span class="sxs-lookup"><span data-stu-id="b7f1d-169">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="b7f1d-170">CLR 空專案（.NET Core）</span><span class="sxs-lookup"><span data-stu-id="b7f1d-170">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="b7f1d-171">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b7f1d-171">Next steps</span></span>

- [<span data-ttu-id="b7f1d-172">檢查 .NET Core 3.0 和3.1 之間的重大變更。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-172">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="b7f1d-173">查看 Windows Forms 應用程式的 .NET Framework 和 .NET Core 3.0 之間的重大變更。</span><span class="sxs-lookup"><span data-stu-id="b7f1d-173">Review the breaking changes between .NET Framework and .NET Core 3.0 for Windows Forms apps.</span></span>](../porting/winforms-breaking-changes.md)
