---
title: Get 語句（Visual Basic）
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
ms.openlocfilehash: d76155b8ff29e4f5e9206ae8fc689fa4fcaf3b8c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581824"
---
# <a name="get-statement"></a>Get 陳述式
宣告用來取出屬性值的 `Get` 屬性程式。  
  
## <a name="syntax"></a>語法  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`attributelist`|選擇項。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|在此屬性中的最多一個 `Get` 和 `Set` 語句上為選擇性。 可以是下列其中一項：<br /><br /> -   [保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私](../../../visual-basic/language-reference/modifiers/private.md)用<br />-   `Protected Friend`<br /><br /> 請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`statements`|選擇項。 呼叫 `Get` 屬性程式時，所執行的一或多個語句。|  
|`End Get`|必要項。 結束 `Get` 屬性程式的定義。|  
  
## <a name="remarks"></a>備註  
 除非屬性標示為 `WriteOnly`，否則每個屬性都必須有 `Get` 的屬性程式。 @No__t_0 程式是用來傳回屬性的目前值。  
  
 當運算式要求屬性的值時，Visual Basic 會自動呼叫屬性的 `Get` 程式。  
  
 屬性宣告的主體只能包含屬性的 `Get`，以及[屬性語句](../../../visual-basic/language-reference/statements/property-statement.md)和 `End Property` 語句之間的 `Set` 程式。 它不能儲存那些程式以外的任何專案。 特別是，它無法儲存屬性的目前值。 您必須將此值儲存在屬性之外，因為如果您將它儲存在其中一個屬性程式中，另一個屬性程式就無法存取它。 一般的方法是將值儲存在與屬性相同層級所宣告的[私](../../../visual-basic/language-reference/modifiers/private.md)用變數中。 您必須在套用的屬性內定義 `Get` 程式。  
  
 除非您在 `Get` 語句中使用 `accessmodifier`，否則 `Get` 程式預設為其包含屬性的存取層級。  
  
## <a name="rules"></a>規則  
  
- **混合存取層級。** 如果您要定義讀寫屬性，您可以選擇性地為 `Get` 或 `Set` 程式指定不同的存取層級，但不能同時為兩者。 如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。 例如，如果屬性是 `Friend` 宣告的，您可以宣告 `Get` 程式 `Private` 但不會 `Public`。  
  
     如果您要定義 `ReadOnly` 屬性，`Get` 程式會代表整個屬性。 您無法為 `Get` 宣告不同的存取層級，因為這會為屬性設定兩個存取層級。  
  
- **傳回類型。** [Property 語句](../../../visual-basic/language-reference/statements/property-statement.md)可以宣告它所傳回之值的資料類型。 @No__t_0 程式會自動傳回該資料類型。 您可以指定任何資料類型，或是列舉、結構、類別或介面的名稱。  
  
     如果 `Property` 語句未指定 `returntype`，程式會傳回 `Object`。  
  
## <a name="behavior"></a>行為  
  
- **從程式傳回。** 當 `Get` 程式回到呼叫程式碼時，會在要求屬性值的語句中繼續執行。  
  
     `Get` 屬性程式可以使用[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)或將傳回值指派給屬性名稱來傳回值。 如需詳細資訊，請參閱[Function 語句](../../../visual-basic/language-reference/statements/function-statement.md)中的「傳回值」。  
  
     @No__t_0 和 `Return` 語句會導致立即離開屬性程式。 任何數目的 `Exit Property` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合 `Exit Property` 和 `Return` 語句。  
  
- **傳回值。** 若要從 `Get` 程式傳回值，您可以將值指派給屬性名稱，或將它包含在[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)中。 @No__t_0 語句會同時指派 `Get` 程式傳回值並結束程式。  
  
     如果您使用 `Exit Property` 而不指派屬性名稱的值，則 `Get` 程式會傳回屬性之資料類型的預設值。 如需詳細資訊，請參閱[Function 語句](../../../visual-basic/language-reference/statements/function-statement.md)中的「傳回值」。  
  
     下列範例說明唯讀屬性 `quoteForTheDay` 可以傳回 `quoteValue` 的私用變數中保留之值的兩種方式。  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>範例  
 下列範例會使用 `Get` 語句來傳回屬性的值。  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>請參閱

- [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [逐步解說：定義類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
