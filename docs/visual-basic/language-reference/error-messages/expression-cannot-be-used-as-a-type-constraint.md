---
title: "&#39;&lt;expression&gt;&#39; cannot be used as a type constraint | Microsoft Docs"
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
  - "bc32061"
  - "vbc32061"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32061"
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;expression&gt;&#39; cannot be used as a type constraint
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

條件約束清單會包括不代表型別參數上之有效條件約束的運算式。  
  
 條件約束清單，會對傳送至型別參數的型別引數強制一些必要需求。  您可以利用任意組合指定下列需求：  
  
-   型別引數必須實作一或多個介面。  
  
-   型別引數至少必須繼承自一個類別  
  
-   型別引數必須公開建立程式碼可以存取的無參數建構函式 \(包含 `New` 條件約束\)  
  
 如果在條件約束清單中未包含任何特定類別或介面，可以指定下列其中一項，加入一般需求：  
  
-   型別引數必須是實值型別 \(包含 `Structure` 條件約束\)  
  
-   型別引數必須是參考型別 \(包含 `Class` 條件約束\)  
  
 您不能同時指定 `Structure` 和 `Class` 做為相同的類型參數，而且也不能指定任何一項超過一次以上。  
  
 **錯誤 ID**：BC32061  
  
### 若要更正這個錯誤  
  
-   驗證運算式和其項目的拼字是否正確。  
  
-   如果運算式不合於上述的需求清單，請將它從條件約束清單中移除。  
  
-   如果運算式參考介面或類別，請驗證編譯器 \(Compiler\) 是否有權存取該介面或類別。  您可能需要限定其名稱，而且也可能需要將參考加入至專案。  如需詳細資訊，請參閱[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的＜專案的參考＞。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)