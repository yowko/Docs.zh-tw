---
title: "Key (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AnonymousKey"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "anonymous types [Visual Basic], key"
  - "Key [Visual Basic]"
  - "Key keyword [Visual Basic]"
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Key (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`Key` 關鍵字可讓您指定匿名型別之屬性的行為。  只有您指定為索引鍵屬性的屬性，將會用於匿名型別執行個體間的相等性測試，或用於計算雜湊程式碼值。  索引鍵屬性的值無法變更。  
  
 為匿名型別指定索引鍵屬性的方法，是在初始設定清單中於屬性的宣告前面加上 `Key` 關鍵字。  在下列範例中，`Airline` 和 `FlightNo` 是索引鍵屬性，`Gate` 則不是。  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_1.vb)]  
  
 建立匿名型別時，匿名型別會直接繼承自 <xref:System.Object>。  編譯器 \(Compiler\) 會覆寫三個繼承的成員：<xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.ToString%2A>。  為 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 產生的覆寫程式碼，是以索引鍵屬性為基礎。  如果型別中沒有索引鍵屬性，就不會覆寫 <xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.Equals%2A>。  
  
## 相等  
 如果兩個匿名型別執行個體 \(Instance\) 屬於相同型別，而且索引鍵屬性的值也相同，則這兩個執行個體便相等。  在下列範例中，`flight2` 和前一個範例中的 `flight1` 相等，因為它們是相同匿名型別的執行個體，且有和索引鍵屬性相符的值。  然而，`flight3` 和 `flight1` 並不相等，因為它的索引鍵屬性 `FlightNo` 的值不同。  執行個體 `flight4` 和 `flight1` 的型別不同，因為它們指派做為索引鍵屬性的屬性不同。  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_2.vb)]  
  
 如果兩個執行個體只宣告非索引鍵屬性，但名稱、型別、順序和值都相等，則這兩個執行個體還是不相等。  沒有索引鍵屬性的執行個體只會與自己相等。  
  
 如需在何種條件下，兩個匿名型別的執行個體會是相同匿名型別之執行個體的詳細資訊，請參閱[Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## 計算雜湊程式碼  
 如同 <xref:System.Object.Equals%2A>，定義於 <xref:System.Object.GetHashCode%2A> 中的匿名型別雜湊函數，是以型別的索引鍵屬性為基礎。  在下列範例中，顯示了在索引鍵屬性和雜湊程式碼值間的互動。  
  
 所有索引鍵屬性值都相同之匿名型別的執行個體，就算非索引鍵屬性的值不相符，仍會有同樣的雜湊程式碼值。  下列陳述式會傳回 `True`。  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_3.vb)]  
  
 有一個或多個索引鍵屬性值不同之匿名型別的執行個體，會有不一樣的雜湊程式碼值。  下列陳述式會傳回 `False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_4.vb)]  
  
 指派不同的屬性做為索引鍵屬性之匿名型別的執行個體，不是相同屬性的執行個體。  就算所有屬性的名稱和值都相同，雜湊程式碼值仍然不同。  下列陳述式會傳回 `False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_5.vb)]  
  
## 唯讀值  
 索引鍵屬性的值無法變更。  例如，在稍早範例的 `flight1` 中，`Airline` 和 `FlightNo` 欄位是唯讀的，但 `Gate` 是可以變更的。  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_6.vb)]  
  
## 請參閱  
 [Anonymous Type Definition](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)   
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)