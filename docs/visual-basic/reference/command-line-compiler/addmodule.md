---
title: "/addmodule | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/addmodule compiler option [Visual Basic]"
  - "addmodule compiler option [Visual Basic]"
  - "-addmodule compiler option [Visual Basic]"
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# /addmodule
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

讓編譯器允許您目前正在編譯的專案使用指定檔案中的所有型別資訊。  
  
## 語法  
  
```  
/addmodule:fileList  
```  
  
## 引數  
 `fileList`  
 必要項。  以逗號分隔的檔案清單，包含中繼資料 \(Metadata\) 但不含組件資訊清單 \(Assembly Manifest\)。  包含空格的檔案名稱必須以引號 \(" "\) 括住。  
  
## 備註  
 必須以 `/target:module` 選項建立 `fileList` 參數所列出的檔案，或使用另一個編譯器的 `/target:module` 對等用法建立。  
  
 所有用 `/addmodule` 加入的模組，必須與執行階段時的輸出檔位在相同的目錄。  也就是說，您可以在編譯時間指定任何目錄中的模組，但是該模組必須位於執行階段時的應用程式目錄中。  否則的話，會發生 <xref:System.TypeLoadException> 錯誤。  
  
 如果您使用 `/addmodule` 指定 \(隱含或明確\) `/target:module` 以外的任何 [\/target](../../../visual-basic/reference/command-line-compiler/target.md) 選項，傳遞至 `/addmodule` 的檔案會成為專案組件的一部分。  需要有組件才能執行用 `/addmodule` 加入一個或多個檔案的輸出檔。  
  
 請使用 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md) 從包含組件的檔案中匯入中繼資料。  
  
> [!NOTE]
>  `/addmodule` 選項無法在 Visual Studio 開發環境內使用；只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會建立模組。  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 下列程式碼會匯入模組的型別。  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 當您執行 `t1` 時，它會輸出 `802`。  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)