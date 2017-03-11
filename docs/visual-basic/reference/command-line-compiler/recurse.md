---
title: "/recurse | Microsoft Docs"
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
  - "/recurse compiler option [Visual Basic]"
  - "-recurse compiler option [Visual Basic]"
  - "recurse compiler option [Visual Basic]"
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# /recurse
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

編譯指定目錄或專案目錄之所有子目錄中的原始程式碼檔。  
  
## 語法  
  
```  
/recurse:[dir\]file  
```  
  
## 引數  
 `dir`  
 選擇項。  要做為搜尋起點的目錄。  如果您沒有指定目錄，搜尋會從專案目錄開始。  
  
 `file`  
 必要項。  要搜尋的檔案。  可以使用萬用字元。  
  
## 備註  
 您可以在檔名中使用萬用字元，來編譯專案目錄中所有相符的檔案，而不需要使用 `/recurse`。  如果沒有指定輸出檔名，編譯器會將第一個處理的輸入檔名當做輸出檔名。  依字母順序檢視時，這通常是編譯檔案清單中的第一個檔案。  基於這個理由，最佳的做法就是使用 `/out` 選項來指定輸出檔。  
  
> [!NOTE]
>  `/recurse` 選項無法在 Visual Studio 開發環境內使用；只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會編譯目前目錄中的所有 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 檔案。  
  
```  
vbc *.vb  
```  
  
 下列程式碼會編譯 `Test\ABC` 目錄和其子目錄中的所有 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 檔案，然後產生 `Test.ABC.dll`。  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/out](../../../visual-basic/reference/command-line-compiler/out.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)