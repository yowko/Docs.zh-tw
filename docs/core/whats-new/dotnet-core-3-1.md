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
# <a name="whats-new-in-net-core-31"></a>.NET Core 3.1 的新功能

本文介紹了 .NET Core 3.1 中的新增功能。 此版本包含對 .NET Core 3.0 的一些改進，重點關注小型但重要的修補程式。 關於 .NET Core 3.1 最重要的功能是它是[長期支援 （LTS）](#long-term-support)版本。

如果您使用的是 Visual Studio 2019，則必須更新到[Visual Studio 2019 版本 16.4](https://visualstudio.microsoft.com/downloads/)才能使用 .NET Core 3.1 專案。 有關 Visual Studio 中的新增功能的詳細資訊，請參閱[Visual Studio 2019 版 16.4 中的新增功能](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164)。

適用于 Mac 的視覺化工作室還支援並包括 Mac 8.4 視覺工作室中的 .NET Core 3.1。

有關該版本的詳細資訊，請參閱[.NET Core 3.1 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。

- 在 Windows、macOS 或 Linux 上[下載並開始使用 .NET 酷睿 3.1。](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="long-term-support"></a>長期支援

.NET Core 3.1 是一個 LTS 版本，支援微軟未來三年。 強烈建議您將應用移動到 .NET Core 3.1。 其他主要版本的當前生命週期如下：

| 版本 | 附註 |
| ------- | ---- |
| .NET Core 3.0 | 2020年3月3日結束。     |
| .NET Core 2.2 | 2019 年 12 月 23 日結束。 |
| .NET Core 2.1 | 2021年8月21日生命終結。    |

有關詳細資訊，請參閱[.NET 核心支援策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

## <a name="macos-apphost-and-notarization"></a>macOS 應用程式Host 和公證

*僅限 macOS*

從 macOS 的公證 .NET Core SDK 3.1 開始，預設情況下將禁用 appHost 設置。 有關詳細資訊，請參閱[macOS Catalina 公證及其對 .NET 核心下載和專案的影響](../install/macos-notarization-issues.md)。

啟用應用Host設置後，.NET Core 會在生成或發佈時生成本機 Mach-O 可執行檔。 當應用從帶有`dotnet run`該命令的原始程式碼運行時，或者直接啟動 Mach-O 可執行檔，則應用在 appHost 的上下文中運行。

如果沒有 appHost，使用者可以啟動[與運行時相關的](../deploying/index.md#publish-runtime-dependent)應用的唯一方法是使用 該`dotnet <filename.dll>`命令。 發佈應用[自包含](../deploying/index.md#publish-self-contained)時，始終會創建應用Host。

您可以在專案級別配置 appHost，也可以使用`dotnet``-p:UseAppHost`參數切換特定命令的應用Host：

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

有關該`UseAppHost`設置的詳細資訊，請參閱[Microsoft.NET.Sdk 的 MSBuild 屬性](../project-sdk/msbuild-props.md#useapphost)。

## <a name="windows-forms"></a>Windows Forms

*僅限 Windows*

> [!WARNING]
> Windows 表單中有重大更改。

舊版控制項包含在 Visual Studio 設計器工具箱中已不可用的 Windows 表單中。 這些控制項被重新替換在 .NET 框架 2.0 中。 這些已從 .NET 核心 3.1 的桌面 SDK 中刪除。

| 已刪除控制項 | 推薦更換 | 已刪除關聯的 API |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | 資料網格塞爾<br/>資料網格行<br/>資料網格表收集<br/>資料網格列集合<br/>資料網格表樣式<br/>資料網格列線樣式<br/>資料格線樣式<br/>資料網格父行標籤<br/>資料網格父行標籤樣式<br/>資料網格布林柱<br/>資料網格文字方塊<br/>網格柱樣式集合<br/>網格表樣式集合<br/>點擊測試類型 |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | 工具列外觀 |
| 工具列按鈕   | <xref:System.Windows.Forms.ToolStripButton>   | 工具列點擊事件<br/>工具列按鈕按一下事件處理常式<br/>工具列按鈕樣式<br/>工具列文本對齊 |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | 功能表項目目集合 |
| MainMenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

我們建議您將應用程式更新為 .NET Core 3.1 並移動到替換控制項。 替換控制項是一個簡單明瞭的過程，實質上是"查找和替換"的類型。

## <a name="ccli"></a>C++/CLI

*僅限 Windows*

已添加用於創建C++/CLI（也稱為"託管C++"）專案的支援。 這些專案生成的二進位檔案與 .NET Core 3.0 和更高版本相容。

要在 Visual Studio 2019 版本 16.4 中添加對 C++/CLI 的支援，請使用[C++工作負載安裝桌面開發](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)。 此工作負載向視覺化工作室添加了兩個範本：

- CLR 類庫 （.NET 核心）
- CLR 空專案 （.NET 核心）

## <a name="next-steps"></a>後續步驟

- [查看 .NET 核心 3.0 和 3.1 之間的重大更改。](../compatibility/3.0-3.1.md)
- [查看 .NET Core 3.1 中 Windows 表單應用的重大變化。](../compatibility/winforms.md#net-core-31)
