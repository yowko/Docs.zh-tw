---
title: "&#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible | Microsoft Docs"
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
  - "vbc31103"
  - "bc31103"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31103"
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

陳述式嘗試擷取屬性的值，但它沒有該屬性之 `Get` 程序的存取權。  
  
 如果 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)標記為比 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)更嚴格的存取層級，則在下列情況下，嘗試讀取屬性值可能會失敗：  
  
-   `Get` 陳述式標記為 [Private](../../../visual-basic/language-reference/modifiers/private.md)，且呼叫程式碼位於所定義之屬性所在的類別或結構外。  
  
-   `Get` 陳述式標記為 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)，且呼叫程式碼不在所定義之屬性所在的類別或結構內，也不在衍生類別中。  
  
-   `Get` 陳述式標記為 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)，且呼叫程式碼不在所定義之屬性所在的同一個組件中。  
  
 **錯誤 ID：**BC31103  
  
### 若要更正這個錯誤  
  
-   如果您具有定義該屬性之原始程式碼的控制權，請考慮將 `Get` 程序宣告為與屬性本身同等的存取層級。  
  
-   如果您沒有定義該屬性之原始程式碼的控制權，或者必須對 `Get` 程序的存取層級做出比屬性本身更嚴格的限制，則請嘗試將讀取屬性值的陳述式移到對該屬性有較佳存取權的程式碼區域。  
  
## 請參閱  
 [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)