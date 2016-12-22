---
title: "How to: Invoke the Command-Line Compiler (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "command-line arguments"
  - "vbc.exe"
  - "Visual Basic compiler, starting"
  - "command line, arguments"
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Invoke the Command-Line Compiler (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您可在命令列 \(又稱為 MS\-DOS 命令提示字元\) 中，輸入可執行檔的名稱來叫用命令列編譯器。  如果您從預設 \[Windows 命令提示字元\] 進行編譯，則必須輸入可執行檔的完整路徑。  若要覆寫這個預設行為，您可以使用 \[[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 命令提示字元\] 或修改 PATH 環境變數。  這兩者都能讓您只輸入編譯器名稱，即可從任何目錄進行編譯。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### 若要使用 Visual Studio 命令提示字元叫用編譯器  
  
1.  開啟 Microsoft Visual Studio 程式群組內的 Visual Studio Tools 程式資料夾。  
  
2.  您可以使用[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]Visual Studio安裝時，從任何目錄，在您的機器，存取編譯器的命令提示字元。  
  
3.  叫用 \[[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 命令提示字元\]。  
  
4.  在命令列輸入 `vbc.exe` *sourceFileName*，然後按 ENTER。  
  
     例如，如果已將原始程式碼儲存在稱為 `SourceFiles` 的目錄中，您會開啟 \[命令提示字元\]，並輸入 `cd SourceFiles` 以切換至該目錄。  如果目錄包含了名為 `Source.vb` 的原始程式檔，您可藉由輸入 `vbc.exe Source.vb` 來加以編譯。  
  
### 若要將 PATH 環境變數設定為 Windows 命令提示字元的編譯器  
  
1.  使用 Windows 的 \[搜尋\] 功能，在本機磁碟尋找 Vbc.exe。  
  
     編譯器所在目錄的確實名稱，是根據 Windows 目錄的位置及安裝的 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] 版本而定。  如果安裝了多個版本的 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]，則必須決定要使用哪個版本 \(通常會使用最新版\)。  
  
2.  從 \[**開始**\] 功能表中，以滑鼠右鍵按一下 \[**我的電腦**\]，然後按一下捷徑功能表中的 \[**屬性**\]。  
  
3.  按一下 \[**進階**\] 索引標籤，然後按一下 \[**環境變數**\]。  
  
4.  在 \[**系統變數**\] 窗格中，從清單中選取 \[**路徑**\] 並按一下 \[**編輯**\]。  
  
5.  在 \[**編輯系統變數**\] 對話方塊中，將游標移到 \[**變數值**\] 欄位中字串的結尾，並輸入一個分號 \(;\)，然後再輸入步驟 1 中所找到的完整目錄名稱。  
  
6.  按一下 \[**確定**\]，確認您的編輯並關閉對話方塊。  
  
     變更 PATH 環境變數之後，即可在 Windows \[命令提示字元\] 中，從電腦的任何目錄執行 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器。  
  
### 若要使用 Windows 命令提示字元叫用編譯器  
  
1.  從 \[**開始**\] 功能表中，按一下 \[**附屬應用程式**\] 資料夾，然後開啟 \[**Windows 命令提示字元**\]。  
  
2.  在命令列輸入 `vbc.exe` *sourceFileName*，然後按 ENTER。  
  
     例如，如果已將原始程式碼儲存在稱為 `SourceFiles` 的目錄中，您會開啟 \[命令提示字元\]，並輸入 `cd SourceFiles` 以切換至該目錄。  如果目錄包含了名為 `Source.vb` 的原始程式檔，您可藉由輸入 `vbc.exe Source.vb` 來加以編譯。  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)