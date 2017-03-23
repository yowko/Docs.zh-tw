---
title: "#ExternalSource Directive | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "#Externalsource"
  - "#ExternalSource"
  - "vb.ExternalSource"
  - "Externalsource"
  - "vb.#ExternalSource"
  - "ExternalSource"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ExternalSource directive (#ExternalSource)"
  - "#ExternalSource directive"
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
caps.latest.revision: 160
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 160
---
# #ExternalSource Directive
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指示原始程式碼和原始檔外部文字之間的對應。  
  
## 語法  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## 組件  
 `StringLiteral`  
 外部原始檔的路徑。  
  
 `IntLiteral`  
 外部原始檔第一行的行號。  
  
 `LogicalLine`  
 外部原始檔中發生錯誤的程式碼行。  
  
 `#End ExternalSource`  
 結束 `#ExternalSource` 區塊。  
  
## 備註  
 這個指示詞只能由編譯器和偵錯工具使用。  
  
 原始程式檔可能包含外部的原始檔指示詞，指示原始程式檔中特定程式碼行和該原始檔外部文字 \(如 aspx 檔\) 之間的對應。  若在編譯期間指定的原始程式碼出現錯誤，則該錯誤會識別為來自外部的原始檔。  
  
 外部原始檔指示詞對編譯並無影響，而且不可以是巢狀的。  它們只在應用程式內部使用。  
  
## 請參閱  
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)