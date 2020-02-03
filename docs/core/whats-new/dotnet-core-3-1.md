---
title: .NET Core 3.1 的新功能
description: 深入瞭解 .NET Core 3.1 中的新功能。
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 0905cbebb2d966570be4ac3aefb40f4377b97061
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742583"
---
# <a name="whats-new-in-net-core-31"></a>.NET Core 3.1 的新功能

本文說明 .NET Core 3.1 中的新功能。 此版本包含 .NET Core 3.0 的次要改良功能，著重于小型但重要的修正程式。 .NET Core 3.1 最重要的功能是，它是[長期支援（LTS）](#long-term-support)版本。

如果您使用 Visual Studio 2019，您必須更新為[Visual Studio 2019 16.4 版](https://visualstudio.microsoft.com/downloads/)，才能使用 .net Core 3.1 專案。 如需 Visual Studio 新功能的詳細資訊，請參閱[Visual Studio 2019 16.4 版的新功能](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164)。

Visual Studio for Mac 也支援並包含 Visual Studio for Mac 8.4 中的 .NET Core 3.1。

如需版本的詳細資訊，請參閱[.Net Core 3.1 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。

- 下載 Windows、macOS 或 Linux 上[的 .Net Core 3.1 並開始使用](https://dotnet.microsoft.com/download/dotnet-core/3.1)。

## <a name="long-term-support"></a>長期支援

.NET Core 3.1 是 LTS 版本，在接下來的三年來提供 Microsoft 支援。 強烈建議您將應用程式移至 .NET Core 3.1。 其他主要版本的目前生命週期如下所示：

| 發行 | 附註 |
| ------- | ---- |
| .NET Core 3.0 | 2020年3月3日結束生命週期。     |
| .NET Core 2.2 | 2019年12月23日結束生命週期。 |
| .NET Core 2.1 | 2021年8月21日結束生命週期。    |

如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

## <a name="windows-forms"></a>Windows Form

*僅限 Windows*

> [!WARNING]
> Windows Forms 中有重大變更。

舊版控制項已包含在 Visual Studio 設計工具工具箱中無法使用的 Windows Forms 中。 這些已取代為 .NET Framework 2.0 中的新控制項。 這些已從適用于 .NET Core 3.1 的桌面 SDK 移除。

| 已移除控制項 | 建議取代 | 已移除相關聯的 Api |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | DataGridCell<br/>DataGridRow<br/>DataGridTableCollection<br/>DataGridColumnCollection<br/>DataGridTableStyle<br/>System.windows.forms.datagridcolumnstyle><br/>DataGridLineStyle<br/>DataGridParentRowsLabel<br/>DataGridParentRowsLabelStyle<br/>DataGridBoolColumn<br/>DataGridTextBox<br/>System.windows.forms.gridcolumnstylescollection><br/>System.windows.forms.gridtablestylescollection><br/>HitTestType |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | System.windows.forms.toolbar.appearance |
| ToolBarButton   | <xref:System.Windows.Forms.ToolStripButton>   | System.windows.forms.toolbarbuttonclickeventargs><br/>ToolBarButtonClickEventHandler<br/>ToolBarButtonStyle<br/>ToolBarTextAlign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | MenuItemCollection |
| MainMenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

我們建議您將應用程式更新為 .NET Core 3.1，並移至取代控制項。 取代控制項是直接的程式，基本上是「尋找和取代」類型。

## <a name="ccli"></a>C++/CLI

*僅限 Windows*

已新增建立C++/cli （也稱為「受控C++」）專案的支援。 從這些專案產生的二進位檔與 .NET Core 3.0 和更新版本相容。

若要在 Visual Studio C++2019 16.4 版中新增對/cli 的支援，請[使用C++工作負載安裝桌面開發](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)。 此工作負載會在 Visual Studio 中新增兩個範本：

- CLR 類別庫（.NET Core）
- CLR 空專案（.NET Core）

## <a name="next-steps"></a>後續步驟

- [檢查 .NET Core 3.0 和3.1 之間的重大變更。](../compatibility/3.0-3.1.md)
- [請參閱 .NET Core 3.1 中適用于 Windows Forms 應用程式的重大變更。](../compatibility/winforms.md#net-core-31)
