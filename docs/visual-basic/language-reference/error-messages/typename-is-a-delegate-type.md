---
title: "&#39;&lt;typename&gt;&#39; is a delegate type | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
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
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; is a delegate type
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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
 [How to: Invoke a Delegate Method](../Topic/How%20to:%20Invoke%20a%20Delegate%20Method%20\(Visual%20Basic\).md)