---
title: "&#39;&lt;typename&gt;&#39; is a delegate type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc32008"
  - "vbc32008"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32008"
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &#39;&lt;typename&gt;&#39; is a delegate type
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

'\<typename\>' 是委派型別。委派建構只允許單一 AddressOf 運算式當做引數清單。通常 AddressOf 運算式可用來代替委派建構。  
  
 建立委派類別執行個體的 `New` 子句將無效的引數清單提供給委派建構函式。  
  
 建立新的委派執行個體時，您只能提供單一 `AddressOf` 運算式。  
  
 如果您不傳遞任何引數給委派建構函式、傳遞一個以上的引數，或傳遞的單一引數為無效 `AddressOf` 運算式，就會產生這個錯誤。  
  
 **錯誤 ID**：BC32008  
  
### 若要更正這個錯誤  
  
-   請在 `New` 子句委派類別的引數清單中，使用單一 `AddressOf` 運算式。  
  
## 請參閱  
 [New Operator](../../../visual-basic/language-reference/operators/new-operator.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [How to: Invoke a Delegate Method](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)