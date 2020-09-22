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
ms.openlocfilehash: 3da6c099b3f43a144484eaddf58605609eb0bbfe
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866198"
---
# <a name="get-statement"></a>Get 陳述式

宣告 `Get` 用來取得屬性值的屬性程式。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`attributelist`|選擇性。 請參閱 [屬性清單](attribute-list.md)。|  
|`accessmodifier`|選擇性 `Get` 地在這個屬性中最多一個和 `Set` 語句上。 可以是下列其中一項：<br /><br /> -   [保護](../modifiers/protected.md)<br />-   [朋友](../modifiers/friend.md)<br />-   [私人](../modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。|  
|`statements`|選擇性。 呼叫屬性程式時執行的一或多個語句 `Get` 。|  
|`End Get`|必要。 終止屬性程式的定義 `Get` 。|  
  
## <a name="remarks"></a>備註  

 除非已標記屬性，否則每個屬性都必須有 `Get` 屬性程式 `WriteOnly` 。 此 `Get` 程式用來傳回屬性目前的值。  
  
 `Get`當運算式要求屬性的值時，Visual Basic 會自動呼叫屬性的程式。  
  
 屬性宣告的主體只能包含屬性和屬性（property） `Get` `Set` [語句](property-statement.md) 和語句之間的程式 `End Property` 。 它無法儲存那些程式以外的任何其他作業。 尤其是，它無法儲存屬性的目前值。 您必須將此值儲存在屬性之外，因為如果您將它儲存在其中一個屬性程式中，則其他屬性程式就無法存取它。 常見的方法是將值儲存在與屬性相同層級宣告的 [私](../modifiers/private.md) 用變數中。 您必須在 `Get` 套用它的屬性內定義程式。  
  
 `Get`除非您 `accessmodifier` 在語句中使用，否則程式會預設為其包含屬性的存取層級 `Get` 。  
  
## <a name="rules"></a>規則  
  
- **混合存取層級。** 如果您要定義讀寫屬性，則可以選擇性地為或程式指定不同的存取層級 `Get` `Set` ，但不能同時指定兩者。 如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。 例如，如果已宣告屬性 `Friend` ，您可以宣告程式 `Get` `Private` ，但不可以 `Public` 。  
  
     如果您要定義 `ReadOnly` 屬性，此程式 `Get` 代表整個屬性。 您無法針對設定不同的存取層級 `Get` ，因為這樣會為屬性設定兩個存取層級。  
  
- **傳回型別。** [Property 語句](property-statement.md)可以宣告其傳回值的資料類型。 此 `Get` 程式會自動傳回該資料類型。 您可以指定任何資料類型或列舉、結構、類別或介面的名稱。  
  
     如果 `Property` 語句未指定，則程式會傳回 `returntype` `Object` 。  
  
## <a name="behavior"></a>行為  
  
- **從程式傳回。** 當程式 `Get` 返回呼叫程式碼時，會在要求屬性值的語句中繼續執行。  
  
     `Get` 屬性程式可以使用 [Return 語句](return-statement.md) 傳回值，或藉由將傳回值指派給屬性名稱來傳回值。 如需詳細資訊，請參閱 [Function 語句](function-statement.md)中的「傳回值」。  
  
     `Exit Property`和 `Return` 語句會導致立即結束屬性程式。 任何數目的 `Exit Property` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合使用和 `Exit Property` `Return` 語句。  
  
- **傳回值。** 若要從程式傳回值 `Get` ，您可以將值指派給屬性名稱，或將它包含在 [return 語句](return-statement.md)中。 `Return`語句會同時指派程式傳回 `Get` 值並結束程式。  
  
     如果您在 `Exit Property` 未指派值給屬性名稱的情況下使用，則程式會傳回 `Get` 屬性之資料類型的預設值。 如需詳細資訊，請參閱 [Function 語句](function-statement.md)中的「傳回值」。  
  
     下列範例說明唯讀屬性 `quoteForTheDay` 可傳回保存在私用變數中之值的兩種方式 `quoteValue` 。  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>範例  

 下列範例會使用 `Get` 語句來傳回屬性的值。  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>另請參閱

- [Set 語句](set-statement.md)
- [Property Statement](property-statement.md)
- [Exit 陳述式](exit-statement.md)
- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)
- [逐步解說：定義類別](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
