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
ms.openlocfilehash: 75ad6d87f1785fea13a282d953f117c9c234e203
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349560"
---
# <a name="set-statement-visual-basic"></a>Set 陳述式 (Visual Basic)
宣告用來將值指派給屬性的 `Set` 屬性程式。  
  
## <a name="syntax"></a>語法  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>組件  
 `attributelist`  
 選擇性。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
 `accessmodifier`  
 在此屬性中的最多一個 `Get` 和 `Set` 語句上為選擇性。 可以是下列其中一項：  
  
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `value`  
 必要。 包含屬性之新值的參數。  
  
 `datatype`  
 如果 `Option Strict` `On`，則為必要。 `value` 參數的資料類型。 指定的資料類型必須與宣告此 `Set` 語句之屬性的資料類型相同。  
  
 `statements`  
 選擇性。 呼叫 `Set` 屬性程式時，所執行的一或多個語句。  
  
 `End Set`  
 必要。 結束 `Set` 屬性程式的定義。  
  
## <a name="remarks"></a>備註  
 除非屬性標示為 `ReadOnly`，否則每個屬性都必須有 `Set` 的屬性程式。 `Set` 程式是用來設定屬性的值。  
  
 當指派語句提供要儲存在屬性中的值時，Visual Basic 會自動呼叫屬性的 `Set` 程式。  
  
 Visual Basic 在屬性指派期間，將參數傳遞給 `Set` 程式。 如果您未提供 `Set`的參數，整合式開發環境（IDE）會使用名為 `value`的隱含參數。 參數會保留要指派給屬性的值。 您通常會將此值儲存在私用區域變數中，並在每次呼叫 `Get` 程式時傳回它。  
  
 屬性宣告的主體只能包含屬性的 `Get`，以及[屬性語句](../../../visual-basic/language-reference/statements/property-statement.md)和 `End Property` 語句之間的 `Set` 程式。 它不能儲存那些程式以外的任何專案。 特別是，它無法儲存屬性的目前值。 您必須將此值儲存在屬性之外，因為如果您將它儲存在其中一個屬性程式中，另一個屬性程式就無法存取它。 一般的方法是將值儲存在與屬性相同層級所宣告的[私](../../../visual-basic/language-reference/modifiers/private.md)用變數中。 您必須在套用的屬性內定義 `Set` 程式。  
  
 除非您在 `Set` 語句中使用 `accessmodifier`，否則 `Set` 程式預設為其包含屬性的存取層級。  
  
## <a name="rules"></a>規則  
  
- **混合存取層級。** 如果您要定義讀寫屬性，您可以選擇性地為 `Get` 或 `Set` 程式指定不同的存取層級，但不能同時為兩者。 如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。 例如，如果屬性是 `Friend`宣告的，您可以宣告 `Set` 程式 `Private`但不會 `Public`。  
  
     如果您要定義 `WriteOnly` 屬性，`Set` 程式會代表整個屬性。 您無法為 `Set`宣告不同的存取層級，因為這會為屬性設定兩個存取層級。  
  
## <a name="behavior"></a>行為  
  
- **從屬性程式傳回。** 當 `Set` 程式回到呼叫程式碼時，執行會在提供要儲存之值的語句後面繼續進行。  
  
     `Set` 屬性程式可以使用[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)或[Exit 語句](../../../visual-basic/language-reference/statements/exit-statement.md)傳回。  
  
     `Exit Property` 和 `Return` 語句會導致立即離開屬性程式。 任何數目的 `Exit Property` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合 `Exit Property` 和 `Return` 語句。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Set` 語句來設定屬性的值。  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>請參閱

- [Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
