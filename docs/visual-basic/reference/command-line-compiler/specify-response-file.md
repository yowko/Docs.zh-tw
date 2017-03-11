---
title: "@ (Specify Response File) (Visual Basic) | Microsoft Docs"
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
  - "@ (Specify Response File) compiler option [Visual Basic]"
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# @ (Specify Response File) (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定包含編譯器選項和原始程式碼檔以供編譯的檔案。  
  
## 語法  
  
```  
@response_file  
```  
  
## 引數  
 `response_file`  
 必要項。  列出編譯器選項或原始程式碼檔以供編譯的檔案。  如果檔案名稱包含空格，請加上英文雙引號 \(" "\)。  
  
## 備註  
 編譯器會處理回應檔指定的編譯器選項和原始程式碼檔，就好像這些選項和程式碼檔早已由命令列所指定一樣。  
  
 若要在編譯中指定多個回應檔，則可指定多個回應檔選項，如下所示。  
  
```  
@file1.rsp @file2.rsp  
```  
  
 在回應檔中，數個編譯器選項和原始程式碼檔可以出現在同一行中。  不過，單一編譯器選項規格必須出現在一行內 \(不能擴展至多行\)。  回應檔可以有以 `#` 符號為開頭的註解。  
  
 您可以結合命令列所指定的選項和一個 \(含\) 以上回應檔所指定的選項。  當編譯器遇到命令時，就會開始處理這些命令選項。  因此，命令列引數可以覆寫先前在回應檔中列出的選項。  反之亦然，回應檔中的選項也可以覆寫先前在命令列或其他回應檔中列出的選項。  
  
 Visual Basic 會提供與 Vbc.exe 檔位在相同目錄中的 Vbc.rsp 檔。  除非使用 `/noconfig` 選項，否則預設會包含 Vbc.rsp 檔案。  如需詳細資訊，請參閱 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)。  
  
> [!NOTE]
>  `@` 選項無法在 Visual Studio 開發環境內使用，只有在命令列編譯時才能使用。  
  
## 範例  
 下列是來自回應檔範例的程式碼。  
  
```  
# build the first output file  
/target:exe   
/out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## 範例  
 下列範例會示範如何將 `@` 選項與名為 `File1.rsp` 的回應檔搭配使用。  
  
```  
vbc @file1.rsp  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)