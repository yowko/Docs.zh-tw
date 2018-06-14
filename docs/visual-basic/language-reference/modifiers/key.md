---
title: Key (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 92d54e3135142bc02a17f3ce5ac078a356c139be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599840"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
`Key`關鍵字可讓您指定之屬性的匿名型別行為。 只有屬性指定為索引鍵屬性中的匿名型別執行個體或計算的雜湊程式碼的值之間的等號比較測試。 無法變更索引鍵屬性的值。  
  
 將匿名類型的屬性指定為索引鍵內容的放入關鍵字`Key`初始設定清單中宣告的前面。 在下列範例中，`Airline`和`FlightNo`是索引鍵屬性，但`Gate`不是。  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 建立新的匿名型別時，它直接繼承自<xref:System.Object>。 編譯器會覆寫繼承的三個成員： <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。 產生的覆寫程式碼<xref:System.Object.Equals%2A>和<xref:System.Object.GetHashCode%2A>根據索引鍵屬性。 如果類型中沒有索引鍵屬性<xref:System.Object.GetHashCode%2A>和<xref:System.Object.Equals%2A>不會覆寫。  
  
## <a name="equality"></a>相等  
 兩個匿名型別執行個體相等，如果相同型別的執行個體，而且其索引鍵屬性的值是否相等。 在下列範例中，`flight2`等於`flight1`前一個範例因為它們是執行個體的相同匿名類型，而且它們有相符的索引鍵屬性的值。 不過，`flight3`不等於`flight1`因為它有不同的值為索引鍵的屬性， `FlightNo`。 執行個體`flight4`不是相同的型別`flight1`因為他們指派不同的屬性為索引鍵屬性。  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 只有非索引鍵屬性，相同的名稱、 類型、 順序和值，以宣告兩個執行個體的兩個執行個體不相等。 沒有索引鍵屬性的執行個體等於只有本身。  
  
 如需條件的兩個匿名型別執行個體都是相同匿名類型的執行個體的詳細資訊，請參閱[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="hash-code-calculation"></a>計算雜湊程式碼  
 像<xref:System.Object.Equals%2A>，雜湊函式中定義<xref:System.Object.GetHashCode%2A>匿名型別是根據索引鍵類型的屬性。 下列範例顯示程式碼值的雜湊索引鍵屬性之間的互動。  
  
 匿名型別的所有索引鍵屬性的值相同的執行個體有相同的雜湊碼值，即使非索引鍵屬性沒有相符的值。 下列陳述式會傳回`True`。  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 匿名類型的一或多個索引鍵屬性的值不同的執行個體具有不同的雜湊碼值。 下列陳述式會傳回`False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 指派不同的屬性為索引鍵屬性的匿名型別的執行個體不是相同類型的執行個體。 即使名稱和所有屬性的值相同時，它們就會有不同的雜湊程式碼的值。 下列陳述式會傳回`False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a>唯讀的值  
 無法變更索引鍵屬性的值。 例如，在`flight1`先前範例中中,`Airline`和`FlightNo`欄位是唯讀的但`Gate`可以變更。  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [匿名類型定義](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
