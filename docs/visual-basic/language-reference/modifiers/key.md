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
ms.openlocfilehash: e13a773f0b585a5c8803a77c7aaad441d90dfe75
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842300"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
`Key`關鍵字可讓您指定之屬性的匿名型別行為。 只有屬性指定為索引鍵屬性中的匿名型別執行個體或計算的雜湊程式碼的值之間的等號比較測試。 無法變更索引鍵屬性的值。  
  
 您將匿名類型的屬性指定為索引鍵屬性上加上關鍵字`Key`前面其宣告的初始化清單中。 在下列範例中，`Airline`並`FlightNo`是索引鍵屬性，但`Gate`不是。  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 建立新的匿名型別時，它會直接繼承<xref:System.Object>。 編譯器會覆寫三個繼承的成員： <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。 產生的覆寫程式碼<xref:System.Object.Equals%2A>和<xref:System.Object.GetHashCode%2A>根據索引鍵屬性。 如果類型中沒有索引鍵屬性<xref:System.Object.GetHashCode%2A>和<xref:System.Object.Equals%2A>不會覆寫。  
  
## <a name="equality"></a>相等  
 兩個匿名型別執行個體相等，如果它們是相同類型的執行個體，而且其索引鍵屬性的值是否相等。 在下列範例中，`flight2`等於`flight1`上一個範例中因為它們是執行個體的相同匿名型別，而且它們有相符的索引鍵屬性的值。 不過，`flight3`不等於`flight1`因為它有不同的值，針對索引鍵的屬性， `FlightNo`。 執行個體`flight4`不是相同的型別`flight1`因為它們將不同的屬性指定為索引鍵屬性。  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 只有非索引鍵屬性，相同的名稱、 類型、 順序和值，以宣告兩個執行個體的兩個執行個體不相等。 沒有索引鍵屬性的執行個體等於只有本身。  
  
 如需詳細的條件下這兩個匿名型別執行個體有相同匿名型別的執行個體的詳細資訊，請參閱[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="hash-code-calculation"></a>計算雜湊程式碼  
 像是<xref:System.Object.Equals%2A>，定義於雜湊函式<xref:System.Object.GetHashCode%2A>匿名型別是根據索引鍵屬性的型別。 下列範例顯示程式碼值的雜湊索引鍵屬性之間的互動。  
  
 具有所有索引鍵屬性的相同值的匿名型別執行個體中將有相同的雜湊碼值，即使非索引鍵屬性沒有相符的值。 下列陳述式會傳回`True`。  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 匿名類型的一或多個索引鍵屬性的值不同的執行個體具有不同的雜湊碼值。 下列陳述式會傳回`False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 將不同的屬性指定為索引鍵屬性的匿名型別的執行個體不是相同類型的執行個體。 名稱和值的所有屬性都相同，即使具有不同的雜湊程式碼的值。 下列陳述式會傳回`False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>唯讀的值  
 無法變更索引鍵屬性的值。 例如，在`flight1`在先前範例中，`Airline`並`FlightNo`欄位是唯讀的但`Gate`可以變更。  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>另請參閱

- [匿名類型定義](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [如何：推斷屬性名稱和匿名類型宣告中的類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
