---
title: 編譯命令列範例 (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7c3fac318e05c5e3d6fb9dd7117cac70ead03dc
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a>編譯命令列範例 (Visual Basic)
做為編譯替代[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式從[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]，您可以從命令列，以產生可執行檔 (.exe) 或動態連結程式庫 (.dll) 檔案進行編譯。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]命令列編譯器支援一組完整的選項來控制輸入和輸出檔案、 組件，以及偵錯和前置處理器選項。 每個選項可互換的兩種形式：`-option`和`/option`。 這份文件只會顯示`-option`表單。  
  
 下表列出您可以修改您自己使用的一些範例命令列。  
  
|以|使用|  
|--------|---------|  
|編譯不能包含 File.vb 並建立 File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|編譯不能包含 File.vb 並建立 File.dll|`vbc -target:library File.vb`|  
|編譯不能包含 File.vb 並建立 My.exe|`vbc -out:My.exe File.vb`|  
|所有編譯[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]檔案在目前目錄中，以最佳化和`DEBUG`產生 File2.exe 定義，符號|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|所有編譯[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]在目前目錄中，而不會顯示標誌或警告產生 File2.dll 的偵錯版本的檔案|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|所有編譯[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Something.dll 目前的目錄中的檔案|`vbc -target:library -out:Something.dll *.vb`|  
  
 當從命令列編譯時，您必須明確參考 Microsoft[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]透過執行階段程式庫`-reference`編譯器選項。  
  
> [!TIP]
>  當您使用 Visual Studio IDE 建置專案時，您可以顯示相關聯的相關資訊**vbc**命令與輸出 視窗中其編譯器選項。 若要顯示這項資訊，請開啟[選項對話方塊、 專案和方案、 建置和執行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後設定**MSBuild 專案組建輸出詳細等級**至**一般**或更高的層級的詳細資訊。 如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
