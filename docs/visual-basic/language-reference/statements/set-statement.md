---
title: Set 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: 49d4c36805b64d7232a94e818256723a0437b6ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404183"
---
# <a name="set-statement-visual-basic"></a>Set 陳述式 (Visual Basic)
宣告 `Set` 用來將值指派給屬性的屬性程式。  
  
## <a name="syntax"></a>語法  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>組件  
 `attributelist`  
 選擇性。 請參閱[屬性清單](attribute-list.md)。  
  
 `accessmodifier`  
 在 `Get` 此屬性中最多隻可有一個和語句的選擇性 `Set` 。 可以是下列其中一項：  
  
- [免受](../modifiers/protected.md)  
  
- [給](../modifiers/friend.md)  
  
- [私用](../modifiers/private.md)  
  
- `Protected Friend`  
  
 請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `value`  
 必要。 包含屬性之新值的參數。  
  
 `datatype`  
 如果 `Option Strict` 為，則為必要 `On` 。 參數的資料類型 `value` 。 指定的資料類型必須與宣告此語句之屬性的資料類型相同 `Set` 。  
  
 `statements`  
 選擇性。 呼叫屬性程式時所執行的一或多個語句 `Set` 。  
  
 `End Set`  
 必要。 終止屬性程式的定義 `Set` 。  
  
## <a name="remarks"></a>備註  
 `Set`除非已標記屬性，否則每個屬性都必須具有屬性程式 `ReadOnly` 。 此 `Set` 程式是用來設定屬性的值。  
  
 `Set`當指派語句提供要儲存在屬性中的值時，Visual Basic 會自動呼叫屬性的程式。  
  
 Visual Basic 會 `Set` 在屬性指派期間將參數傳遞至程式。 如果您未提供的參數 `Set` ，整合式開發環境（IDE）會使用名為的隱含參數 `value` 。 參數會保留要指派給屬性的值。 您通常會將此值儲存在私用區域變數中，並在每次 `Get` 呼叫程式時傳回它。  
  
 屬性宣告的主體只能包含屬性 `Get` `Set` [語句](property-statement.md)與語句之間的和程式 `End Property` 。 它不能儲存那些程式以外的任何專案。 特別是，它無法儲存屬性的目前值。 您必須將此值儲存在屬性之外，因為如果您將它儲存在其中一個屬性程式中，另一個屬性程式就無法存取它。 一般的方法是將值儲存在與屬性相同層級所宣告的[私](../modifiers/private.md)用變數中。 您必須在 `Set` 所套用的屬性內定義程式。  
  
 `Set`除非您 `accessmodifier` 在語句中使用，否則程式會預設為其包含屬性的存取層級 `Set` 。  
  
## <a name="rules"></a>規則  
  
- **混合存取層級。** 如果您要定義讀寫屬性，則可以選擇性地為或程式指定不同的存取層級 `Get` `Set` ，但不能同時為兩者。 如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。 例如，如果已宣告屬性 `Friend` ，您可以宣告程式 `Set` `Private` ，而不是 `Public` 。  
  
     如果您要定義 `WriteOnly` 屬性，程式會 `Set` 代表整個屬性。 您不能為設定不同的存取層級 `Set` ，因為這會為屬性設定兩個存取層級。  
  
## <a name="behavior"></a>行為  
  
- **從屬性程式傳回。** 當程式 `Set` 返回呼叫程式碼時，執行會在提供要儲存之值的語句後面繼續進行。  
  
     `Set`屬性程式可以使用[Return 語句](return-statement.md)或[Exit 語句](exit-statement.md)傳回。  
  
     `Exit Property`和 `Return` 語句會導致立即離開屬性程式。 任何數目的 `Exit Property` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合使用 `Exit Property` 和 `Return` 語句。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Set` 語句來設定屬性的值。  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>另請參閱

- [Get 陳述式](get-statement.md)
- [Property Statement](property-statement.md)
- [Sub 陳述式](sub-statement.md)
- [屬性程序](../../programming-guide/language-features/procedures/property-procedures.md)
