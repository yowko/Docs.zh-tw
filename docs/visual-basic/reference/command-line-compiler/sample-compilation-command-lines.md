---
title: 編譯命令列範例 (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b0f1fc1d269801efdbf2e89d10679dc8159851f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a>編譯命令列範例 (Visual Basic)
Visual Basic 中編譯程式從 Visual Studio 或者，您可以編譯從命令列，以產生可執行檔 (.exe) 或動態連結程式庫 (.dll) 檔案。  
  
 Visual Basic 命令列編譯器支援一組完整的選項來控制輸入和輸出檔案、 組件，以及偵錯和前置處理器選項。 每個選項可互換的兩種形式：`-option`和`/option`。 這份文件只會顯示`-option`表單。  
  
 下表列出您可以修改您自己使用的一些範例命令列。  
  
|以|使用|  
|--------|---------|  
|編譯不能包含 File.vb 並建立 File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|編譯不能包含 File.vb 並建立 File.dll|`vbc -target:library File.vb`|  
|編譯不能包含 File.vb 並建立 My.exe|`vbc -out:My.exe File.vb`|  
|編譯不能包含 File.vb 並建立名為 File.dll 的參考組件和文件庫|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|在編譯所有的 Visual Basic 檔案，在目前目錄中，以最佳化和`DEBUG`產生 File2.exe 定義，符號|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|編譯所有在目前目錄中，而不會顯示標誌或警告產生 File2.dll 的偵錯版本的 Visual Basic 檔案|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|編譯 Something.dll 目前的目錄中的所有 Visual Basic 檔案|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  當您使用 Visual Studio IDE 建置專案時，您可以顯示相關聯的相關資訊**vbc**命令與輸出 視窗中其編譯器選項。 若要顯示這項資訊，請開啟[選項對話方塊、 專案和方案、 建置和執行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後設定**MSBuild 專案組建輸出詳細等級**至**一般**或更高的層級的詳細資訊。   
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
