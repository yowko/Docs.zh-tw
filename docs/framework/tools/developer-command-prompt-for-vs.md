---
title: Visual Studio 的開發人員命令提示字元
description: 瞭解如何使用適用于 Visual Studio 的開發人員命令提示字元，讓您更輕鬆地使用 .NET 工具。 它會自動設定特定的環境變數。
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
ms.openlocfilehash: 92416820f47cb778dfcc916b8626df4aa328814c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167177"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio 的開發人員命令提示字元

Visual Studio 的開發人員命令提示字元可讓您更輕鬆地使用 .NET Framework 工具。 它是自動設定特定環境變數的命令提示字元。 開啟開發人員命令提示字元之後，您可以輸入[.NET Framework 工具](index.md)的命令，例如 `ildasm` 或 `clrver` 。

## <a name="prerequisites"></a>必要條件

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>搜尋您電腦上的命令提示字元

您可能會有多個命令提示字元，視 Visual Studio 版本以及您已安裝的任何其他 Sdk 和工作負載而定。 如果下列步驟沒有作用，您可以嘗試以[手動方式尋找您電腦上的](#manually-locate-the-files-on-your-machine)檔案，或[從 Visual Studio 內啟動命令提示](#start-the-command-prompt-from-inside-visual-studio)字元。

### <a name="windows-10"></a>Windows 10

1. 選取**Start** ![ 鍵盤上的 [啟動 Windows 標誌鍵]。](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) 並滾動到字母**V**。

1. 展開 [ **Visual Studio 2019** ] 資料夾。

1. 選擇 [**適用于 VS 2019 的開發人員命令提示字元**] （或您想要使用的命令提示字元）。

   或者，您可以在工作列的 [搜尋] 方塊中，開始輸入命令提示字元的名稱，然後選擇您想要的結果，因為結果清單會開始顯示搜尋相符專案。

   ![顯示 Windows 10 搜尋行為的動畫 gif](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. 按下 Windows 標誌鍵 ![鍵盤上的 Windows 標誌鍵](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) 前往 [開始]**** 畫面。 位於您的鍵盤上，作為範例。

1. 在 [**開始**] 畫面上，按**Ctrl** + **Tab**以開啟 [**應用程式**] 清單，然後按**V**。這會顯示一份清單，其中包含所有已安裝的 Visual Studio 命令提示字元。

1. 選擇 [**適用于 VS 2019 的開發人員命令提示字元**] （或您想要使用的命令提示字元）。

### <a name="windows-7"></a>Windows 7

1. 選擇 [**開始**]，然後展開 [**所有程式**]。

1. 選擇**Visual Studio 2019**  >  **Visual Studio Tools**  >  **適用于 VS 2019**的 Visual Studio 2019 Visual Studio Tools 開發人員命令提示字元，或您想要使用的命令提示字元。

   ![已反白顯示命令提示字元的 Windows 7 [開始] 功能表](./media/developer-command-prompt-for-vs/windows7-menu.png)

如果您已安裝其他 Sdk （例如[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)或[舊版](https://developer.microsoft.com/windows/downloads/sdk-archive)），您可能會看到其他的命令提示字元。 查看個別工具的文件以判斷要使用哪個版本的命令提示字元。

## <a name="manually-locate-the-files-on-your-machine"></a>以手動方式尋找您電腦上的檔案

您已安裝之命令提示字元的快捷方式通常會放在 Visual Studio 的 [**開始功能表**] 資料夾中，例如 *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Tools*。 但如果基於某些原因，搜尋命令提示字元並不會產生預期的結果，您可以嘗試在您的電腦上手動找出快捷方式。 請嘗試搜尋命令提示字元檔案的名稱（例如*VsDevCmd.bat*），或移至 [工具] 資料夾，例如 *% ProgramFiles （x86）% \ Microsoft Visual Studio\2019\Community\Common7\Tools* （根據您的 Visual Studio 版本、版本和安裝位置的路徑變更）。

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>從內部啟動命令提示字元 Visual Studio

為方便存取，您可以將開發人員命令提示字元或任何其他命令提示字元新增至 Visual Studio 中的 [工具] 功能表。 若要讓工具可供使用，請將它新增至外部工具清單。 以下是步驟：

1. 開啟 Visual Studio。

1. 在 [開始] 視窗中，選擇 [不使用程式碼繼續]****。

1. 在功能表列上，選擇 [**工具**] [  >  **外部工具**]。

1. 在 [外部工具]**** 對話方塊中，選擇 [加入]**** 按鈕。 新項目隨即出現。

1. 輸入新功能表項目的 [標題]****，例如 `Command Prompt`。

1. 在 [**命令**] 欄位中，指定您要啟動的檔案，例如 `%comspec%` 或 `C:\Windows\System32\cmd.exe` 。

1. 在 [**引數**] 欄位中，指定要在哪裡尋找您要使用的特定命令提示字元，例如 `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"` 。 此命令會啟動隨 Visual Studio 2019 的社區安裝的開發人員命令提示字元。 根據您的 Visual Studio 版本和安裝位置變更這個值。

1. 在 [**初始目錄**] 欄位中，指定要在其中啟動命令提示字元的目錄。 選取欄位旁的箭號，以選擇 [**專案目錄**] 之類的值。

1. 選擇 [確定] **** 按鈕。

   ![填入域值的 [外部工具] 對話方塊。](./media/developer-command-prompt-for-vs/add-external-tool.png)

   這會新增功能表項目，而且您可以從 [工具] 功能表存取命令提示字元。

   ![Visual Studio 中的命令提示字元功能表項目](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>另請參閱

- [.NET Framework 工具](index.md)
- [管理外部工具](/visualstudio/ide/managing-external-tools)
- [從命令列使用 Microsoft c + + 工具組](/cpp/build/building-on-the-command-line)
