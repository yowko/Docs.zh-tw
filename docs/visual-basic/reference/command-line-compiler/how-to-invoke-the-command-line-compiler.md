---
title: HOW TO：叫用命令列編譯器 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 67cad0df3f10ff1fa1f6a58546fe150232fe1283
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302799"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>HOW TO：叫用命令列編譯器 (Visual Basic)
您可以叫用命令列編譯器，命令列中，也稱為 MS-DOS 命令提示字元中輸入的可執行檔名稱。 如果您從預設的 Windows 命令提示字元進行編譯，您必須輸入可執行檔的完整的路徑。 若要覆寫此預設行為，您可以使用 Visual Studio 中，開發人員命令提示字元，或修改 PATH 環境變數。 兩者都可讓您只要鍵入編譯器名稱從任何目錄進行編譯。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>若要叫用編譯器使用 for Visual Studio 的開發人員命令提示字元  
  
1. 開啟 Microsoft Visual Studio 程式群組中的 Visual Studio Tools 程式資料夾。  
  
2. 如果已安裝 Visual Studio，您可以使用 Visual Studio 開發人員命令提示字元存取編譯器從任何目錄，您的電腦。  
  
3. 叫用 Visual studio 的開發人員命令提示字元。  
  
4. 在命令列中，輸入`vbc.exe` *sourceFileName*然後按 ENTER 鍵。  
  
     例如，如果您在名為目錄中儲存您的原始程式碼`SourceFiles`，您會開啟命令提示字元並輸入`cd SourceFiles`變更至該目錄。 如果目錄包含名為原始程式檔`Source.vb`，您可以輸入來編譯`vbc.exe Source.vb`。  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>若要設定 PATH 環境變數，編譯器的 Windows 命令提示字元  
  
1. 使用 「 Windows Search 」 功能來尋找 Vbc.exe 本機磁碟上。  
  
     編譯器所在的目錄完整名稱是根據 Windows 目錄的位置和 [.NET Framework] 安裝的版本而定。 如果您有多個版本的 「 安裝的.NET Framework"，您必須決定要使用 （通常是最新版本） 的版本。  
  
2. 從您**開始** 功能表中，以滑鼠右鍵按一下**我的電腦**，然後按一下**屬性**從捷徑功能表。  
  
3. 按一下 **進階**索引標籤，然後再按一下**環境變數**。  
  
4. 在 **系統**變數窗格中，選取**路徑**從清單，然後按一下**編輯**。  
  
5. 在 **編輯系統**變數對話方塊中，將插入點移至 在字串結尾**變數值**欄位並輸入分號 （;） 後面接著在步驟 1 中找到完整的目錄名稱。  
  
6. 按一下 **確定**，確認您的編輯，並關閉對話方塊。  
  
     變更 PATH 環境變數之後，您可以執行 Visual Basic 編譯器在 Windows 命令提示字元從任何目錄電腦上。  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>若要叫用編譯器使用 Windows 命令提示字元  
  
1. 從**開始**功能表，然後按一下**附屬應用程式**資料夾，然後再開啟**Windows 命令提示字元**。  
  
2. 在命令列中，輸入`vbc.exe` *sourceFileName*然後按 ENTER 鍵。  
  
     例如，如果您在名為目錄中儲存您的原始程式碼`SourceFiles`，您會開啟命令提示字元並輸入`cd SourceFiles`變更至該目錄。 如果目錄包含名為原始程式檔`Source.vb`，您可以輸入來編譯`vbc.exe Source.vb`。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
