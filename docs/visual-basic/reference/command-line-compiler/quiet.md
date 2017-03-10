---
title: "/quiet | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/quiet"
  - "quiet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-quiet compiler option [Visual Basic]"
  - "/quiet compiler option [Visual Basic]"
  - "quiet compiler option [Visual Basic]"
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# /quiet
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

防止編譯器顯示與語法相關的錯誤和警告碼。  
  
## 語法  
  
```  
/quiet  
```  
  
## 備註  
 預設 `/quiet` 為不作用。  當編譯器報告與語法相關的錯誤或警告時，也會從原始程式碼輸出程式行。  對於剖析編譯器輸出的應用程式來說，當編譯器只輸出診斷文字時可能會更為方便。  
  
 在下列範例中，如果編譯時未使用 `/quiet`，`Module1` 輸出的錯誤會包含原始程式碼。  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 輸出：  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 如果編譯時使用了 `/quiet`，編譯器只會輸出下列資料：  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  `/quiet` 選項無法在 Visual Studio 開發環境內使用；只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會編譯 `T2.vb`，而且不會顯示與語法相關的編譯器診斷程式碼：  
  
```  
vbc /quiet t2.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)