---
title: "WithEvents (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.WithEvents"
  - "WithEvents"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "WithEvents keyword"
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# WithEvents (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定一或多個宣告的成員變數 \(Member Variable\) 會參考可以引發事件之類別的執行個體。  
  
## 備註  
 使用 `WithEvents` 定義變數時，您可以宣告方式指定方法會使用 `Handles` 關鍵字處理變數的事件。  
  
 `WithEvents` 只能用於類別或模組層級。  這表示 `WithEvents` 變數的宣告內容必須是類別或模組，而不可以是原始程式檔 \(Source File\)、命名空間 \(Namespace\)、結構或程序。  
  
 您不可以在結構成員上使用 `WithEvents`。  
  
 您只能使用 `WithEvents` 宣告個別變數，不能宣告陣列。  
  
## 規則  
  
-   **元素型別**： 您必須將 `WithEvents` 變數宣告為物件變數，使這些變數得以接受類別執行個體。  但是，您無法將它們宣告為 `Object`。  您必須將它們宣告為可以引發事件的特定類別。  
  
 `WithEvents` 修飾詞 \(Modifier\) 可以用於以下內容中：[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## 請參閱  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)