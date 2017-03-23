---
title: "&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc32025"
  - "vbc32025"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32025"
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`#Region` 區塊必須在類別、模組或命名空間 \(Namespace\) 層級宣告。  可摺疊區域可包含一個或多個程序，但是不可以在程序內部的開頭或結尾。  
  
 **錯誤 ID︰**BC32025  
  
### 若要更正這個錯誤  
  
1.  請確定前面的程序是以 `End Function` 或 `End Sub` 陳述式正確結束。  
  
2.  請確定 `#Region` 和 `#End Region` 指示詞位於相同的程式碼區塊中。  
  
## 請參閱  
 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md)