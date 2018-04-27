---
title: 如何：叫用命令列編譯器 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1ccf08ba58fa6af60bd8ffd7cba79b205dc0f3d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>如何：叫用命令列編譯器 (Visual Basic)
您可以在命令列中，也稱為 MS-DOS 命令提示字元中輸入可執行檔的名稱來叫用命令列編譯器。 如果您從預設 Windows 命令提示字元進行編譯，您必須輸入的可執行檔的完整的路徑。 若要覆寫此預設行為，您可以使用[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]命令提示字元，或修改的 PATH 環境變數。 兩者都可讓您只要輸入編譯器名稱從任何目錄進行編譯。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a>要叫用編譯器使用 Visual Studio 命令提示字元  
  
1.  開啟 Microsoft Visual Studio 程式群組中的 Visual Studio Tools 程式資料夾。  
  
2.  您可以使用[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]編譯器存取從您的電腦上的任何目錄，如果在安裝 Visual Studio 命令提示字元。  
  
3.  叫用[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]命令提示字元。  
  
4.  在命令列中，輸入`vbc.exe` *sourceFileName*然後按 ENTER 鍵。  
  
     例如，如果您呼叫的目錄中儲存您的原始程式碼`SourceFiles`，您會開啟命令提示字元，然後輸入`cd SourceFiles`變更到該目錄。 如果目錄包含原始程式檔名為`Source.vb`，您無法編譯，則輸入`vbc.exe Source.vb`。  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>編譯器的 Windows 命令提示字元中設定的 PATH 環境變數  
  
1.  使用 「 Windows 搜尋 」 功能來尋找 Vbc.exe 本機磁碟上。  
  
     編譯器所在的目錄完整名稱取決於 Windows 目錄的位置和 <.NET Framework > 安裝的版本。 如果您有多個版本的 <.NET Framework > 安裝，您必須決定要使用 （通常是最新版本） 的版本。  
  
2.  從您**啟動**功能表上，以滑鼠右鍵按一下**我的電腦**，然後按一下 **屬性**從捷徑功能表。  
  
3.  按一下**進階**索引標籤，然後再按一下**環境變數**。  
  
4.  在**系統**變數窗格中，選取**路徑**從清單按一下**編輯**。  
  
5.  在**編輯系統**變數對話方塊中，將插入點移至在字串結尾**變數值**欄位並輸入分號 （;） 後面的步驟 1 中的完整目錄名稱。  
  
6.  按一下**確定**確認您的編輯，並關閉對話方塊。  
  
     變更 PATH 環境變數之後，您可以執行 Visual Basic 編譯器在 Windows 命令提示字元從任何目錄電腦上。  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>要叫用編譯器使用 Windows 命令提示字元  
  
1.  從**啟動**功能表，然後按一下**附屬應用程式**資料夾，然後再開啟**Windows 命令提示字元**。  
  
2.  在命令列中，輸入`vbc.exe` *sourceFileName*然後按 ENTER 鍵。  
  
     例如，如果您呼叫的目錄中儲存您的原始程式碼`SourceFiles`，您會開啟命令提示字元，然後輸入`cd SourceFiles`變更到該目錄。 如果目錄包含原始程式檔名為`Source.vb`，您無法編譯，則輸入`vbc.exe Source.vb`。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
