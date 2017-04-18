---
title: "How to︰ 叫用命令列編譯器 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line, arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 69c95289f91f712bd3fda03a7f582d879141591a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>如何：叫用命令列編譯器 (Visual Basic)
您可以在命令列中，也稱為 MS-DOS 命令提示字元中輸入可執行檔的名稱來叫用命令列編譯器。 如果您從預設的 Windows 命令提示字元進行編譯，您必須輸入的可執行檔的完整的路徑。 若要覆寫這個預設行為，您可以使用[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]命令提示字元，或修改 PATH 環境變數。 這兩種方法可讓您只要輸入編譯器名稱從任何目錄進行編譯。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a>若要叫用編譯器使用 Visual Studio 命令提示字元  
  
1.  開啟 Microsoft Visual Studio 程式群組中的 Visual Studio Tools 程式資料夾。  
  
2.  您可以使用[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]存取編譯器從您的電腦上的任何目錄，如果已安裝 Visual Studio 命令提示字元。  
  
3.  叫用[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]命令提示字元。  
  
4.  在命令列中，輸入`vbc.exe` *sourceFileName* ，然後按 ENTER。  
  
     例如，如果您將原始程式碼儲存在目錄中名為`SourceFiles`，您會開啟命令提示字元並輸入`cd SourceFiles`，變更至該目錄。 如果目錄包含原始程式檔名為`Source.vb`，您可以輸入來編譯`vbc.exe Source.vb`。  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>若要設定 PATH 環境變數給編譯器的 Windows 命令提示字元  
  
1.  使用 「 Windows 搜尋 」 功能來尋找 Vbc.exe 本機磁碟上。  
  
     編譯器所在的目錄完整名稱取決於 Windows 目錄的位置和版本的[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]安裝。 如果您有多個版本的[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]安裝，您必須決定要使用 （通常是最新版本） 的版本。  
  
2.  從您**啟動**] 功能表上，以滑鼠右鍵按一下**我的電腦**，然後按一下 [**屬性**從捷徑功能表。  
  
3.  按一下 **進階**索引標籤，然後再按一下**環境變數**。  
  
4.  在**系統**變數窗格中，選取**路徑**從清單按一下**編輯**。  
  
5.  在**編輯系統**變數對話方塊中，將插入點移至 在字串結尾**變數值**欄位並輸入分號 （;） 在步驟 1 中找到完整的目錄名稱。  
  
6.  按一下 **確定**，確認您的編輯並關閉對話方塊。  
  
     變更 PATH 環境變數之後，您可以執行[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器在 Windows 命令提示字元，從任何電腦上的目錄。  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>若要叫用編譯器使用 Windows 命令提示字元  
  
1.  從**啟動**功能表中，按一下**附屬應用程式**資料夾，然後再開啟**Windows 命令提示字元**。  
  
2.  在命令列中，輸入`vbc.exe` *sourceFileName* ，然後按 ENTER。  
  
     例如，如果您將原始程式碼儲存在目錄中名為`SourceFiles`，您會開啟命令提示字元並輸入`cd SourceFiles`，變更至該目錄。 如果目錄包含原始程式檔名為`Source.vb`，您可以輸入來編譯`vbc.exe Source.vb`。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
