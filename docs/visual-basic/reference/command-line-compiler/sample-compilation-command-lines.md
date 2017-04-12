---
title: "範例編譯命令列 (Visual Basic) |Microsoft 文件"
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
- command line, compilers
- compilation, command-line
- command-line compilers
- compiling source code, from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 918787b3377f2e5a636a6b098046ac2f455efcdd
ms.lasthandoff: 03/13/2017

---
# <a name="sample-compilation-command-lines-visual-basic"></a>編譯命令列範例 (Visual Basic)
除了編譯[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式從[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]，您可以從要產生可執行檔 (.exe) 或動態連結程式庫 (.dll) 檔案的命令列進行編譯。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]命令列編譯器支援一組完整的選項來控制輸入和輸出檔案、 組件，以及偵錯和前置處理器的選項。 每個選項可互換的兩種形式︰`-``option`和`/``option`。 這份文件只會顯示`/``option`表單。  
  
 下表列出您可以修改您自己使用的一些範例命令列。  
  
|以|用法|  
|--------|---------|  
|編譯 File.vb 並建立 File.exe|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|編譯 File.vb 並建立 File.dll|`vbc /target:library File.vb`|  
|編譯 File.vb 並建立 My.exe|`vbc /out:My.exe File.vb`|  
|所有編譯[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]檔案在目前目錄中，以最佳化和`DEBUG`符號定義之後，產生 File2.exe|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|所有編譯[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]中目前的目錄，而不會顯示標誌或警告產生 File2.dll 的偵錯版本的檔案|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|所有編譯[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Something.dll 目前的目錄中的檔案|`vbc /target:library /out:Something.dll *.vb`|  
  
 當從命令列進行編譯，您必須明確參考 Microsoft[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]透過執行階段程式庫`/reference`編譯器選項。  
  
> [!TIP]
>  當您使用 Visual Studio IDE 建置專案時，您可以顯示相關聯的相關資訊**vbc**命令與相關的編譯器選項，在 [輸出] 視窗中。 若要顯示這項資訊，請開啟[選項對話方塊、 專案和方案、 建置和執行](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後設定**MSBuild 專案建置輸出詳細程度**至**正常**或更高的層級的詳細資訊。 如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
