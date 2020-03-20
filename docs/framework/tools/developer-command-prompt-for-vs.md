---
title: Visual Studio 的開發人員命令提示字元
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715876"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio 的開發人員命令提示字元

Visual Studio 的開發人員命令提示允許您更輕鬆地使用 .NET 框架工具。 它是自動設置特定環境變數的命令提示符。 打開開發人員命令提示符後，可以輸入[.NET 框架工具](index.md)的命令，如`ildasm``clrver`或 。

## <a name="prerequisites"></a>必要條件

- [視覺工作室 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>搜尋您電腦上的命令提示字元

您可能有多個命令提示，具體取決於 Visual Studio 的版本以及已安裝的任何其他 SDK 和工作負載。 如果以下步驟不起作用，您可以嘗試[手動查找電腦上的檔](#manually-locate-the-files-on-your-machine)，或[從 Visual Studio 內部啟動命令提示](#start-the-command-prompt-from-inside-visual-studio)。

### <a name="windows-10"></a>Windows 10

1. 選擇鍵盤上的 **"開始**![視窗"徽標鍵。](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) 並滾動到字母**V**。

1. 展開**視覺化工作室 2019**資料夾。

1. 為**VS 2019 選擇開發人員命令提示**（或要使用的命令提示）。

   或者，您可以在工作列上的搜索框中開始鍵入命令提示符的名稱，並在結果清單開始顯示搜索匹配項時選擇所需的結果。

   ![顯示 Windows 10 上的搜索行為的動畫 gif](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. 按下 Windows 標誌鍵 ![鍵盤上的 Windows 標誌鍵](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) 前往 [開始]**** 畫面。 位於您的鍵盤上，作為範例。

1. 在 **"開始"** 螢幕上，**按"Ctrl"**+**選項卡**打開 **"應用"** 清單，然後按**V**。這將顯示一個清單，其中包含所有已安裝的 Visual Studio 命令提示。

1. 為**VS 2019 選擇開發人員命令提示**（或要使用的命令提示）。

### <a name="windows-7"></a>Windows 7

1. 選擇 **"開始"，** 然後展開**所有程式**。

1. 選擇**Visual Studio 2019** > **視覺化工作室工具** > **開發人員命令提示符 VS 2019**，或要使用的命令提示符。

   ![Windows 7 啟動功能表，命令提示符突出顯示](./media/developer-command-prompt-for-vs/windows7-menu.png)

如果安裝了其他 SDK，如[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)或[以前的版本](https://developer.microsoft.com/windows/downloads/sdk-archive)，您可能會看到其他命令提示。 查看個別工具的文件以判斷要使用哪個版本的命令提示字元。

## <a name="manually-locate-the-files-on-your-machine"></a>以手動方式尋找您電腦上的檔案

通常，已安裝的命令提示的快捷方式將放置在 Visual Studio 的 **"開始功能表"** 資料夾中，例如*在 %程式資料%*Microsoft_Windows_開始功能表\程式\Visual Studio 2019_Visual Studio 工具*中。 但是，如果由於某種原因搜索命令提示未產生預期結果，則可以嘗試手動查找電腦上的快捷方式。 嘗試搜索命令提示檔的名稱，如*VsDevCmd.bat*， 或轉到"工具"資料夾，例如 *%程式檔 （x86）%_Microsoft Visual Studio_2019_社區\通用7\工具*（路徑會根據您的 Visual Studio 版本、版本和安裝位置更改）。

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>從視覺化工作室內部啟動命令提示

為了便於訪問，您可以將開發人員命令提示符或任何其他命令提示符添加到 Visual Studio 中的"工具"功能表中。 若要讓工具可供使用，請將它新增至外部工具清單。 以下為其步驟：

1. 開啟 Visual Studio。

1. 在 [開始] 視窗中，選擇 [不使用程式碼繼續]****。

1. 在功能表列上，選擇 **"工具** > **外部工具**"。

1. 在 [外部工具]**** 對話方塊中，選擇 [加入]**** 按鈕。 新項目隨即出現。

1. 輸入新功能表項目的 [標題]****，例如 `Command Prompt`。

1. 在 **"命令"** 欄位中，指定要啟動的檔，如`%comspec%`或`C:\Windows\System32\cmd.exe`。

1. 在 **"參數"** 欄位中，指定要使用的特定命令提示的位置，例如`/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`。 此命令啟動與 Visual Studio 2019 社區一起安裝的開發人員命令提示。 根據您的 Visual Studio 版本和安裝位置變更這個值。

1. 在 **"初始目錄"** 欄位中，指定命令提示符將在其中啟動的目錄。 通過選擇欄位旁邊的箭頭來選擇專案**目錄**等值。

1. 選擇 [確定] **** 按鈕。

   ![外部工具對話方塊，欄位值已填寫。](./media/developer-command-prompt-for-vs/add-external-tool.png)

   這會新增功能表項目，而且您可以從 [工具] 功能表存取命令提示字元。

   ![Visual Studio 中的命令提示字元功能表項目](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>另請參閱

- [.NET Framework 工具](index.md)
- [管理外部工具](/visualstudio/ide/managing-external-tools)
- [使用命令列中的 Microsoft C++工具集](/cpp/build/building-on-the-command-line)
