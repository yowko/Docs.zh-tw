---
title: .NET Core 3.1 的新功能
description: 深入瞭解 .NET Core 3.1 中的新功能。
dev_langs:
- csharp
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 9caecdcc3516db2bd71420184fbd21f7837552a7
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437930"
---
# <a name="whats-new-in-net-core-31"></a>.NET Core 3.1 的新功能

本文說明 .NET Core 3.1 中的新功能。 此版本包含 .NET Core 3.0 的微小改進，著重于小型但重要的修正程式。 .NET Core 3.1 最重要的功能是 [ (LTS) 版本的長期支援 ](#long-term-support) 。

如果您使用 Visual Studio 2019，則必須更新至 [Visual Studio 2019 16.4 版或更新版本](https://visualstudio.microsoft.com/downloads/) ，才能使用 .net Core 3.1 專案。 如需 Visual Studio 16.4 版新功能的詳細資訊，請參閱 [Visual Studio 2019 16.4 版中的新功能](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164)。

Visual Studio for Mac 也支援並包含 Visual Studio for Mac 8.4 中的 .NET Core 3.1。

如需版本的詳細資訊，請參閱 [.Net Core 3.1 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。

- 在 Windows、macOS 或 Linux 上[下載並開始使用 .Net Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) 。

## <a name="long-term-support"></a>長期支援

.NET Core 3.1 是 LTS 版本，可在未來三年提供 Microsoft 的支援。 強烈建議您將應用程式移至 .NET Core 3.1。 其他主要版本的目前生命週期如下所示：

| 版本 | 注意 |
| ------- | ---- |
| .NET Core 3.0 | 2020年3月3日結束生命週期。     |
| .NET Core 2.2 | 2019年12月23日結束生命週期。 |
| .NET Core 2.1 | 2021年8月21日結束生命週期。    |

如需詳細資訊，請參閱 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

## <a name="macos-apphost-and-notarization"></a>macOS appHost 和公證

*僅限 macOS*

從適用于 macOS 的公證 .NET Core SDK 3.1 開始，預設會停用 appHost 設定。 如需詳細資訊，請參閱 [MacOS Catalina 公證和 .Net Core 下載和專案的影響](../install/macos-notarization-issues.md)。

當 appHost 設定啟用時，.NET Core 會在您建立或發行時產生原生的符合-O 可執行檔。 當您的應用程式從使用命令的原始程式碼執行 `dotnet run` ，或直接啟動符合-O 可執行檔時，您的應用程式會在 appHost 的環境中執行。

如果沒有 appHost，使用者就可以使用命令來啟動與 [framework 相依](../deploying/index.md#publish-framework-dependent) 的應用程式 `dotnet <filename.dll>` 。 當您發行 [獨立](../deploying/index.md#publish-self-contained)應用程式時，一律會建立 appHost。

您可以在專案層級設定 appHost，或使用參數切換特定命令的 appHost `dotnet` `-p:UseAppHost` ：

- 專案檔

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- 命令列參數

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

如需有關此設定的詳細資訊 `UseAppHost` ，請參閱 [適用于 Microsoft .Net 的 MSBuild 屬性](../project-sdk/msbuild-props.md#useapphost)。

## <a name="windows-forms"></a>Windows Forms

*僅限 Windows*

> [!WARNING]
> Windows Forms 中有重大變更。

舊版控制項已包含在 Visual Studio 設計工具工具箱中無法使用的 Windows Forms。 這些已取代為 .NET Framework 2.0 中的新控制項。 這些已從適用于 .NET Core 3.1 的桌面 SDK 移除。

| 已移除控制項 | 建議取代 | 已移除相關聯的 Api |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | DataGridCell<br/>DataGridRow<br/>DataGridTableCollection<br/>DataGridColumnCollection<br/>DataGridTableStyle<br/>System.windows.forms.datagridcolumnstyle><br/>DataGridLineStyle<br/>DataGridParentRowsLabel<br/>DataGridParentRowsLabelStyle<br/>DataGridBoolColumn<br/>DataGridTextBox<br/>System.windows.forms.gridcolumnstylescollection><br/>System.windows.forms.gridtablestylescollection><br/>HitTestType |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | System.windows.forms.toolbar.appearance |
| ToolBarButton   | <xref:System.Windows.Forms.ToolStripButton>   | System.windows.forms.toolbarbuttonclickeventargs><br/>ToolBarButtonClickEventHandler<br/>ToolBarButtonStyle<br/>ToolBarTextAlign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | MenuItemCollection |
| MainMenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

建議您將應用程式更新為 .NET Core 3.1，並移至取代控制項。 取代控制項是一個簡單的程式，基本上是「尋找和取代」型別。

## <a name="ccli"></a>C++/CLI

*僅限 Windows*

已加入支援，以建立 c + +/CLI (也稱為「managed c + +」 ) 專案。 這些專案所產生的二進位檔會與 .NET Core 3.0 和更新版本相容。

若要在 Visual Studio 2019 16.4 版中加入 c + +/CLI 的支援，請安裝 [使用 c + + 的桌面開發工作負載](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)。 此工作負載會將兩個範本新增至 Visual Studio：

- CLR 類別庫 ( .NET Core) 
- CLR 空專案 ( .NET Core) 

## <a name="next-steps"></a>後續步驟

- [查看 .NET Core 3.0 和3.1 之間的重大變更。](../compatibility/3.1.md)
- [查看 .NET Core 3.1 中 Windows Forms 應用程式的重大變更。](../compatibility/winforms.md#net-core-31)
