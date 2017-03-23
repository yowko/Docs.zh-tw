---
title: "Generic parameters used as optional parameter types must be class constrained | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc32124"
  - "bc32124"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32124"
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Generic parameters used as optional parameter types must be class constrained
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

程序是利用選擇性參數所宣告，而這個參數會使用未限制為參考型別 \(Reference Type\) 的型別參數。  
  
 您永遠都必須為每一個選擇性參數提供預設值。  如果參數具有參考型別，則選擇性的值必須是 `Nothing`，這是任何參考型別的有效值。  然而，如果參數具有實值型別 \(Value Type\)，則該型別必須是 Visual Basic 預先定義的基礎資料型別 \(Elementary Data Type\)。  這是因為複合實值型別 \(例如使用者定義的結構\) 沒有任何有效的預設值。  
  
 當您對選擇性參數使用型別參數時，必須保證它具有參考型別，以避免發生實值型別不具有效的預設值。  這表示必須利用 `Class` 關鍵字或利用特定類別的名稱，限制型別參數。  
  
 **錯誤 ID**：BC32124  
  
### 若要更正這個錯誤  
  
-   限制型別參數只接受參考型別，或者不要在選擇性參數中使用它。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Nothing](../../../visual-basic/language-reference/nothing.md)