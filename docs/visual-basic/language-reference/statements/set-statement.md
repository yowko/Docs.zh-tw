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
ms.openlocfilehash: b3524769567a56a87184bf916a3e5ccb1fd4fa1c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871749"
---
# <a name="set-statement-visual-basic"></a>Set 陳述式 (Visual Basic)

宣告 `Set` 用來將值指派給屬性的屬性程式。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>組件  

 `attributelist`  
 選擇性。 請參閱 [屬性清單](attribute-list.md)。  
  
 `accessmodifier`  
 選擇性 `Get` 地在這個屬性中最多一個和 `Set` 語句上。 可以是下列其中一項：  
  
- [保護](../modifiers/protected.md)  
  
- [Friend](../modifiers/friend.md)  
  
- [私人](../modifiers/private.md)  
  
- `Protected Friend`  
  
 請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `value`  
 必要。 包含屬性之新值的參數。  
  
 `datatype`  
 如果 `Option Strict` 為，則為必要項 `On` 。 參數的資料類型 `value` 。 指定的資料類型必須與宣告此語句之屬性的資料類型相同 `Set` 。  
  
 `statements`  
 選擇性。 呼叫屬性程式時執行的一或多個語句 `Set` 。  
  
 `End Set`  
 必要。 終止屬性程式的定義 `Set` 。  
  
## <a name="remarks"></a>備註  

 除非已標記屬性，否則每個屬性都必須有 `Set` 屬性程式 `ReadOnly` 。 此 `Set` 程式是用來設定屬性的值。  
  
 `Set`當指派語句提供要儲存在屬性中的值時，Visual Basic 會自動呼叫屬性的程式。  
  
 Visual Basic 會 `Set` 在屬性指派期間將參數傳遞給程式。 如果您未提供的參數 `Set` ，則 (IDE) 的整合式開發環境會使用名為的隱含參數 `value` 。 參數會保存要指派給屬性的值。 您通常會在私用區域變數中儲存此值，並在 `Get` 呼叫程式時傳回。  
  
 屬性宣告的主體只能包含屬性和屬性（property） `Get` `Set` [語句](property-statement.md) 和語句之間的程式 `End Property` 。 它無法儲存那些程式以外的任何其他作業。 尤其是，它無法儲存屬性的目前值。 您必須將此值儲存在屬性之外，因為如果您將它儲存在其中一個屬性程式中，則其他屬性程式就無法存取它。 常見的方法是將值儲存在與屬性相同層級宣告的 [私](../modifiers/private.md) 用變數中。 您必須在 `Set` 套用它的屬性內定義程式。  
  
 `Set`除非您 `accessmodifier` 在語句中使用，否則程式會預設為其包含屬性的存取層級 `Set` 。  
  
## <a name="rules"></a>規則  
  
- **混合存取層級。** 如果您要定義讀寫屬性，則可以選擇性地為或程式指定不同的存取層級 `Get` `Set` ，但不能同時指定兩者。 如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。 例如，如果已宣告屬性 `Friend` ，您可以宣告程式 `Set` `Private` ，但不可以 `Public` 。  
  
     如果您要定義 `WriteOnly` 屬性，此程式 `Set` 代表整個屬性。 您無法針對設定不同的存取層級 `Set` ，因為這樣會為屬性設定兩個存取層級。  
  
## <a name="behavior"></a>行為  
  
- **從屬性程式傳回。** 當程式 `Set` 返回呼叫程式碼時，執行會繼續遵循提供要儲存之值的語句。  
  
     `Set` 屬性程式可以使用 [Return 語句](return-statement.md) 或 [Exit 語句](exit-statement.md)傳回。  
  
     `Exit Property`和 `Return` 語句會導致立即結束屬性程式。 任何數目的 `Exit Property` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合使用和 `Exit Property` `Return` 語句。  
  
## <a name="example"></a>範例  

 下列範例會使用 `Set` 語句來設定屬性的值。  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>另請參閱

- [Get 陳述式](get-statement.md)
- [Property Statement](property-statement.md)
- [Sub 陳述式](sub-statement.md)
- [屬性程序](../../programming-guide/language-features/procedures/property-procedures.md)
