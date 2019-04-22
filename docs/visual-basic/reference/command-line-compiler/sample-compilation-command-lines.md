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
ms.openlocfilehash: 0771ed41d6c58ce7cc98435b405f5819e45393db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824296"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>編譯命令列範例 (Visual Basic)
為編譯 Visual Basic 程式從 Visual Studio 內的替代方法，您可以編譯從命令列來產生可執行檔 (.exe) 檔案或動態連結程式庫 (.dll) 檔案。  
  
 Visual Basic 命令列編譯器支援一組完整的選項來控制輸入和輸出檔案、 組件，以及偵錯和前置處理器選項。 每個選項是可互換的兩種形式：`-option`和`/option`。 此文件只說明`-option`表單。  
  
 下表列出一些您可以修改供自己使用的範例命令列。  
  
|以|使用|  
|--------|---------|  
|編譯 File.vb 並建立 File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|編譯 File.vb 並建立 file.dll 的 File.cs|`vbc -target:library File.vb`|  
|編譯 File.vb 並建立 My.exe|`vbc -out:My.exe File.vb`|  
|編譯 File.vb 和建立文件庫和名為 file.dll 的 File.cs 參考組件|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|在編譯所有的 Visual Basic 檔案，在目前目錄中，以最佳化和`DEBUG`符號定義，產生 File2.exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|編譯產生 File2.dll 偵錯版本，而不會顯示標誌或警告的目前目錄中的所有 Visual Basic 檔案|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|編譯 Something.dll 目前的目錄中的所有 Visual Basic 檔案|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  當您使用 Visual Studio IDE 建置專案時，您可以顯示相關聯的相關資訊**vbc**命令搭配其編譯器選項，在 [輸出] 視窗中。 若要顯示這項資訊，請開啟[選項對話方塊、 專案和解決方案、 建置和執行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後將**MSBuild 專案建置輸出詳細等級**來**一般**或較高層級的詳細資訊。   
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
