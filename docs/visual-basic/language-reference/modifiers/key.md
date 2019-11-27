---
title: 索引鍵
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 92c8809779d6cab524f67ee47f355b72ab152403
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351511"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
`Key` 關鍵字可讓您指定匿名型別屬性的行為。 只有您指定為索引鍵屬性的屬性，才會參與匿名型別實例之間的相等測試，或計算雜湊碼值。 無法變更索引鍵屬性的值。  
  
 將關鍵字 `Key` 放在初始化清單中的宣告前面，即可指定匿名型別的屬性做為索引鍵屬性。 在下列範例中，`Airline` 和 `FlightNo` 是索引鍵屬性，但 `Gate` 不是。  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 建立新的匿名型別時，它會直接繼承 <xref:System.Object>。 編譯器會覆寫三個繼承的成員： <xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A>和 <xref:System.Object.ToString%2A>。 針對 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 產生的覆寫程式碼是以索引鍵屬性為基礎。 如果類型中沒有任何索引鍵屬性，則不會覆寫 <xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.Equals%2A>。  
  
## <a name="equality"></a>相等  
 如果兩個匿名型別實例都是相同類型的實例，而且其索引鍵屬性的值相等，則兩者相等。 在下列範例中，`flight2` 等於上一個範例中的 `flight1`，因為它們是相同匿名型別的實例，而且它們的索引鍵屬性具有相符的值。 不過，`flight3` 不等於 `flight1`，因為它的索引鍵屬性有不同的值，`FlightNo`。 實例 `flight4` 的類型與 `flight1` 不同，因為它們會將不同的屬性指定為索引鍵屬性。  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 如果兩個實例僅使用非索引鍵屬性來宣告，則名稱、類型、順序和值都相同，這兩個實例不相等。 沒有索引鍵屬性的實例只等於其本身。  
  
 如需有關兩個匿名型別實例在相同匿名型別實例之下的條件的詳細資訊，請參閱[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="hash-code-calculation"></a>雜湊程式碼計算  
 如同 <xref:System.Object.Equals%2A>，在匿名型別的 <xref:System.Object.GetHashCode%2A> 中定義的雜湊函式是以類型的索引鍵屬性為基礎。 下列範例會顯示索引鍵屬性與雜湊碼值之間的互動。  
  
 匿名型別的實例若具有相同的雜湊碼值，則所有索引鍵屬性的值都相同，即使非索引鍵屬性沒有相符的值。 下列語句會傳回 `True`。  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 匿名型別的實例若具有一或多個索引鍵屬性的不同值，就會有不同的雜湊碼值。 下列語句會傳回 `False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 將不同屬性指定為索引鍵屬性的匿名型別實例不是相同類型的實例。 即使所有屬性的名稱和值都相同，它們也有不同的雜湊碼值。 下列語句會傳回 `False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>唯讀值  
 無法變更索引鍵屬性的值。 例如，在先前範例的 `flight1` 中，[`Airline`] 和 [`FlightNo`] 欄位是唯讀的，但 `Gate` 可以變更。  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>請參閱

- [匿名類型定義](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
