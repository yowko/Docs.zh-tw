---
title: 答案
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 582ed5bb67b9c7504e736710aa4649cffb12ef45
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867994"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)

`Key`關鍵字可讓您指定匿名型別的屬性行為。 只有您指定為索引鍵屬性的屬性，才會參與匿名型別實例之間的相等測試或雜湊程式碼值的計算。 無法變更索引鍵屬性的值。  
  
 您可以將匿名型別的屬性指定為索引鍵屬性，方法是在 `Key` 初始化清單中將關鍵字放在其宣告的前面。 在下列範例中， `Airline` 和是索引 `FlightNo` 鍵屬性，但 `Gate` 不是。  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 建立新的匿名型別時，它會直接繼承自 <xref:System.Object> 。 編譯器會覆寫三個繼承的成員： <xref:System.Object.Equals%2A> 、 <xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.ToString%2A> 。 針對和產生的覆寫程式碼會以索引 <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> 鍵屬性為基礎。 如果類型中沒有任何索引鍵屬性，則 <xref:System.Object.GetHashCode%2A> <xref:System.Object.Equals%2A> 不會覆寫。  
  
## <a name="equality"></a>等式  

 如果兩個匿名型別實例是相同類型的實例，而且其索引鍵屬性的值相等，則這兩個實例相等。 在下列範例中， `flight2` 等於先前的 `flight1` 範例，因為它們是相同匿名型別的實例，而且它們的索引鍵屬性具有相符的值。 但是， `flight3` 不等於， `flight1` 因為它的索引鍵屬性有不同的值 `FlightNo` 。 實例與 `flight4` 的類型 `flight1` 不同，因為它們會將不同的屬性指定為索引鍵屬性。  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 如果兩個實例只使用非索引鍵屬性來宣告，且名稱、類型、順序和值都相同，則這兩個實例不相等。 沒有索引鍵屬性的實例只等於本身。  
  
 如需兩個匿名型別實例是相同匿名型別的實例之條件的詳細資訊，請參閱 [匿名型別](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="hash-code-calculation"></a>雜湊碼計算  

 <xref:System.Object.Equals%2A>在中，針對匿名型別所定義的雜湊函 <xref:System.Object.GetHashCode%2A> 式是以型別的索引鍵屬性為基礎。 下列範例顯示索引鍵屬性與雜湊程式碼值之間的互動。  
  
 具有相同值的所有索引鍵屬性之匿名型別的實例具有相同的雜湊碼值，即使非索引鍵的屬性沒有相符的值也一樣。 下列陳述式會傳回 `True`。  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 匿名型別的實例如果有一個或多個索引鍵屬性的值不同，則會有不同的雜湊程式碼值。 下列陳述式會傳回 `False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 將不同的屬性指定為索引鍵屬性之匿名型別的實例，不是相同類型的實例。 即使所有屬性的名稱和值都相同，也會有不同的雜湊程式碼值。 下列陳述式會傳回 `False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>唯讀值  

 無法變更索引鍵屬性的值。 例如，在 `flight1` 先前的範例中， `Airline` 和 `FlightNo` 欄位是唯讀的，但 `Gate` 可以變更。  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>另請參閱

- [匿名型別定義](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [如何：在匿名類型宣告中推斷屬性名稱和類型](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [匿名類型](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
