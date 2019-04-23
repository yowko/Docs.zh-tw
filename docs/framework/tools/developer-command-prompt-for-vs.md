---
title: Visual Studio 的開發人員命令提示字元
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cc88106a54a00b4b12e5043da7961791a98102c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344360"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio 的開發人員命令提示字元

Visual Studio 的開發人員命令提示字元可讓您更輕鬆地使用 .NET Framework 工具。 它是命令提示字元，可自動設定特定的環境變數。

> [!div class="button"]
> [下載 Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>搜尋您電腦上的命令提示字元

根據您已安裝的 Visual Studio 及任何其他 SDK 版本，您可能會有多個命令提示字元。 例如，Visual Studio 64 位元版本提供 32 位元和 64 位元的命令提示字元  (大多數工具的 32 位元和 64 位元版本完全相同；然而，少數工具會分別變更 32 位元和 64 位元的環境)。如果下列步驟沒有作用，您可以嘗試[以手動方式尋找您電腦上的檔案](#manually-locate-the-files-on-your-machine)或[從 Visual Studio 內部執行命令提示字元](#run-the-command-prompt-from-inside-visual-studio)。

### <a name="in-windows-10"></a>在 Windows 10

1. 在工作列的搜尋方塊中開始鍵入工具名稱，例如 `dev` 或 `developer command prompt`。 這會顯示符合搜尋模式的已安裝應用程式清單。 如果您要尋找不同的命令提示字元，請嘗試輸入不同的搜尋字詞，例如 `prompt`。

2. 選擇 [Visual Studio 開發人員命令提示字元] (或您想要使用的命令提示字元)。

### <a name="in-windows-81"></a>在 Windows 8.1

1. 移至 [開始] 畫面，例如藉由按下鍵盤上的 Windows 標誌鍵 ![Windows 標誌](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")。

2. 在 [開始] 畫面上，按 **Ctrl** + **Tab** 以開啟 [應用程式] 清單，然後輸入 `V`。 這會顯示包含所有已安裝 Visual Studio 命令提示字元的清單。

3. 選擇 [開發人員命令提示字元] (或您想要使用的命令提示字元)。

### <a name="in-windows-8"></a>在 Windows 8

1. 移至 [開始] 畫面，例如藉由按下鍵盤上的 Windows 標誌鍵 ![Windows 標誌](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")。

2. 在 [開始] 畫面上，按下 Windows 標誌鍵 ![Windows 標誌](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`。

3. 選擇畫面底部的 [應用程式檢視] 圖示，然後輸入 `V`。 這會顯示包含所有已安裝 Visual Studio 命令提示字元的清單。

4. 選擇 [開發人員命令提示字元] (或您想要使用的命令提示字元)。

### <a name="in-windows-7"></a>在 Windows 7

1. 選擇 [開始]，展開 [所有程式]，然後展開 [Microsoft Visual Studio]。

2. 根據您已安裝的 Visual Studio 版本，請選擇 [Visual Studio Tools]、[Visual Studio 命令提示字元] 或您想要使用的命令提示字元。

如果已安裝 [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 或[舊版](https://developer.microsoft.com/windows/downloads/sdk-archive)之類的其他 SDK，您可能會看到 ARM、x86 或 x64 架構的其他命令提示字元。 查看個別工具的文件以判斷要使用哪個版本的命令提示字元。

## <a name="manually-locate-the-files-on-your-machine"></a>以手動方式尋找您電腦上的檔案

您已安裝之命令提示字元的捷徑通常會位於 Visual Studio 的 [開始功能表] 資料夾中，例如 C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools 中。 但如果基於某些原因，搜尋命令提示字元未產生預期的結果，您可以嘗試以手動方式尋找電腦上的捷徑。 嘗試搜尋 *VsDevCmd.bat* 等命令提示字元檔案名稱，或移至 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools 之類的 Tools 資料夾 (根據您的 Visual Studio 版本和安裝位置，這個路徑會變更)。

## <a name="run-the-command-prompt-from-inside-visual-studio"></a>從 Visual Studio 內部執行命令提示字元

為方便存取，您可以將 Visual Studio 開發人員命令提示字元或任何其他命令提示字元新增至 Visual Studio 的 [工具] 功能表。 若要讓工具可供使用，請將它新增至外部工具清單。 其步驟如下：

1. 開啟 Visual Studio。

2. 選取 [工具] 功能表，然後選擇 [外部工具]。

3. 在 [外部工具] 對話方塊中，選擇 [加入] 按鈕。 新項目隨即出現。

4. 輸入新功能表項目的 [標題]，例如 `Command Prompt`。

5. 在 [命令] 欄位中，指定您要啟動的檔案，例如 `%comspec%` 或 `C:\Windows\System32\cmd.exe`。

6. 在 [引數] 欄位中，指定尋找所要使用之特定命令提示字元的位置，例如 `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (此命令會啟動隨 Visual Studio 2017 Enterprise 一起安裝的開發人員命令提示字元)。 根據您的 Visual Studio 版本和安裝位置變更這個值。

7. 選擇 [初始目錄] 欄位的值，例如 [專案目錄]。

8. 選擇 [確定]  按鈕。

   這會新增功能表項目，而且您可以從 [工具] 功能表存取命令提示字元。

   ![Visual Studio 中的命令提示字元功能表項目](media/command-prompt-vs-menu.png)

## <a name="see-also"></a>另請參閱

- [工具](../../../docs/framework/tools/index.md)
- [管理外部工具](/visualstudio/ide/managing-external-tools)
