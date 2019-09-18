---
title: 作法：叫用命令列編譯器（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: a81d5b4f4eae76b0306e2d27475cb8527bda0ff2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054223"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>作法：叫用命令列編譯器（Visual Basic）

您可以叫用命令列編譯器，方法是在命令列中輸入其可執行檔的名稱，也就是 MS-DOS 提示字元。 如果您從預設的 Windows 命令提示字元進行編譯，則必須輸入可執行檔的完整路徑。 若要覆寫此預設行為，您可以使用 Visual Studio 的開發人員命令提示字元，或修改 PATH 環境變數。 這兩種方法都可讓您直接輸入編譯器名稱，從任何目錄進行編譯。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>若要使用適用于 Visual Studio 的開發人員命令提示字元叫用編譯器

1. 開啟 Microsoft Visual Studio 程式群組內的 [Visual Studio Tools 程式] 資料夾。

2. 如果安裝 Visual Studio，您可以使用 Visual Studio 的開發人員命令提示字元，從電腦上的任何目錄存取編譯器。

3. 叫用 Visual Studio 的開發人員命令提示字元。

4. 在命令列中輸入`vbc.exe` *sourceFileName* ，然後按 enter。

    例如，如果您將原始程式碼儲存在名`SourceFiles`為的目錄中，您會開啟命令提示字元，然後輸入`cd SourceFiles`以變更至該目錄。 如果目錄包含名為`Source.vb`的原始程式檔，您可以輸入`vbc.exe Source.vb`來編譯它。

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>若要將 PATH 環境變數設定為 Windows 命令提示字元的編譯器

1. 使用 Windows 搜尋功能，在您的本機磁片上尋找 Vbc。

    編譯器所在目錄的確切名稱，取決於 Windows 目錄的位置和安裝的「.NET Framework」版本。 如果您已安裝多個版本的「.NET Framework」，您必須決定要使用哪個版本（通常是最新版本）。

2. 在 **開始** 功能表中，以滑鼠右鍵按一下 **我的電腦**，然後從快捷方式功能表按一下 **屬性**。

3. 按一下 [ **Advanced** ] 索引標籤，然後按一下 [**環境變數**]。

4. 在 [**系統**變數] 窗格中，從清單中選取 [**路徑**]，然後按一下 [**編輯**]。

5. 在 [**編輯系統**變數] 對話方塊中，將插入點移至 [**變數值**] 欄位中的字串結尾，然後輸入分號（;)後面接著在步驟1中找到的完整目錄名稱。

6. 按一下 **[確定]** 以確認您的編輯，並關閉對話方塊。

     變更 PATH 環境變數之後，您可以從電腦上的任何目錄，在 Windows 命令提示字元中執行 Visual Basic 編譯器。

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>使用 Windows 命令提示字元叫用編譯器

1. 在 [**開始**] 功能表中，按一下 [**附屬**應用程式] 資料夾，然後開啟**Windows 命令提示**字元。

2. 在命令列中輸入`vbc.exe` *sourceFileName* ，然後按 enter。

     例如，如果您將原始程式碼儲存在名`SourceFiles`為的目錄中，您會開啟命令提示字元，然後輸入`cd SourceFiles`以變更至該目錄。 如果目錄包含名為`Source.vb`的原始程式檔，您可以輸入`vbc.exe Source.vb`來編譯它。

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
