---
title: Get 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: d6a6fdfd191de76871619dea3bd1794b487698aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605104"
---
# <a name="get-statement"></a>Get 陳述式
宣告`Get`屬性程序用來擷取屬性的值。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`attributelist`|選擇性。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|上一個選擇性`Get`和`Set`這個屬性中的陳述式。 可以是下列其中一項：<br /><br /> -   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私用](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`statements`|選擇性。 一或多個陳述式時執行`Get`呼叫屬性程序。|  
|`End Get`|必要。 結束的定義`Get`屬性程序。|  
  
## <a name="remarks"></a>備註  
 每個屬性必須有`Get`屬性程序除非屬性標記為`WriteOnly`。 `Get`程序用來傳回屬性的目前值。  
  
 Visual Basic 會自動呼叫屬性`Get`運算式要求屬性的值時的程序。  
  
 屬性宣告的主體可以包含屬性的`Get`和`Set`程序之間[Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)和`End Property`陳述式。 無法將儲存這些程序之外的任何項目。 特別是，它無法儲存屬性的目前值。 您必須先儲存此值超出屬性，因為如果您將其儲存在任一屬性程序，其他屬性程序無法存取它。 一般的方法是將值儲存[私人](../../../visual-basic/language-reference/modifiers/private.md)屬性與相同層級宣告的變數。 您必須定義`Get`它所套用的屬性內的程序。  
  
 `Get`程序會預設為其包含屬性的存取層級，除非您使用`accessmodifier`中`Get`陳述式。  
  
## <a name="rules"></a>規則  
  
-   **混合的存取層級。** 如果您要定義讀 / 寫屬性，您可以選擇其中一個指定的不同存取層`Get`或`Set`程序，但非兩者。 如果您這麼做時，程序的存取層級必須比屬性存取層級更受限。 例如，如果屬性宣告`Friend`，您可以宣告`Get`程序`Private`，但不是`Public`。  
  
     如果您要定義`ReadOnly`屬性，`Get`程序都代表整個屬性。 您無法宣告不同的存取層級`Get`，因為，則會設定兩個屬性的存取層級。  
  
-   **傳回型別。** [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)可以宣告其傳回的值的資料類型。 `Get`程序會自動傳回資料類型。 您可以指定任何資料類型或列舉、 結構、 類別或介面的名稱。  
  
     如果`Property`陳述式未指定`returntype`，程序會傳回`Object`。  
  
## <a name="behavior"></a>行為  
  
-   **傳回從程序。** 當`Get`程序傳回呼叫程式碼，會繼續執行要求的屬性值的陳述式中。  
  
     `Get` 屬性程序可以傳回值使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)或傳回值指派至屬性名稱。 如需詳細資訊，請參閱 「 傳回的值 」 中[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。  
  
     `Exit Property`和`Return`陳述式會導致屬性程序立即結束。 任何數目的`Exit Property`和`Return`陳述式可以出現在任何地方程序，且您可以混合`Exit Property`和`Return`陳述式。  
  
-   **傳回值。** 若要傳回值，以從`Get`程序中，您可以將值指派給屬性名稱，或將它併入[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。 `Return`陳述式會同時指派`Get`程序傳回值，然後結束程序。  
  
     如果您使用`Exit Property`而不將值指派至屬性名稱，`Get`程序會傳回屬性的資料類型的預設值。 如需詳細資訊，請參閱 「 傳回的值 」 中[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。  
  
     下列範例說明兩種方式的唯讀屬性`quoteForTheDay`可以保存在私用變數值傳回`quoteValue`。  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a>範例  
 下列範例會使用`Get`陳述式來傳回屬性的值。  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [逐步解說：定義類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
