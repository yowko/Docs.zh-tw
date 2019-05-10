---
title: Set 陳述式 (Visual Basic)
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
ms.openlocfilehash: fb51dfbae4d9c4ef205e67ac15c5027e62a9a938
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663189"
---
# <a name="set-statement-visual-basic"></a>Set 陳述式 (Visual Basic)
宣告`Set`用來將值指派給屬性的屬性程序。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>組件  
 `attributelist`  
 選擇性。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
 `accessmodifier`  
 上最多一個的選擇性`Get`和`Set`這個屬性中的陳述式。 可以是下列其中一項：  
  
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `value`  
 必要項。 包含屬性的新值的參數。  
  
 `datatype`  
 需要`Option Strict`是`On`。 資料類型的`value`參數。 指定的資料類型必須是屬性的資料型別相同，這`Set`宣告陳述式。  
  
 `statements`  
 選擇性。 一或多個陳述式時執行`Set`呼叫屬性程序。  
  
 `End Set`  
 必要項。 結束的定義`Set`屬性程序。  
  
## <a name="remarks"></a>備註  
 每個屬性必須有`Set`屬性程序屬性標示為除非`ReadOnly`。 `Set`程序用來設定屬性的值。  
  
 Visual Basic 會自動呼叫屬性的`Set`程序時在指派陳述式提供所要儲存在屬性值。  
  
 Visual Basic 會將傳遞的參數`Set`屬性指派期間的程序。 如果您未提供的參數`Set`，整合式的開發環境 (IDE) 會使用名為的隱含參數`value`。 參數包含要指派給屬性的值。 您通常會將此值儲存在私用的本機變數，並將它傳回每當`Get`呼叫程序。  
  
 屬性宣告的主體可以包含屬性的`Get`並`Set`之間的程序[Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)而`End Property`陳述式。 它無法儲存這些程序以外的任何項目。 特別是，它無法儲存屬性的目前值。 您必須先儲存外部屬性，這個值，因為如果您將其儲存在其中一個屬性程序，其他的屬性程序無法存取它。 一般的方法是將值儲存在[私人](../../../visual-basic/language-reference/modifiers/private.md)屬性與相同層級宣告的變數。 您必須定義`Set`它所套用的屬性內的程序。  
  
 `Set`程序預設值為其包含屬性的存取層級，除非您使用`accessmodifier`在`Set`陳述式。  
  
## <a name="rules"></a>規則  
  
- **混合的存取層級。** 如果您正在定義的讀寫屬性，您可以選擇性地針對指定不同的存取層級`Get`或`Set`程序，但非兩者。 如果您這麼做時，程序的存取層級必須比屬性的存取層級更具限制性。 例如，如果屬性宣告`Friend`，您可以宣告`Set`程序`Private`，而非`Public`。  
  
     如果您要定義`WriteOnly`屬性，`Set`程序都代表整個屬性。 您無法宣告不同的存取層級`Set`，因為，則會設定屬性的兩個存取層級。  
  
## <a name="behavior"></a>行為  
  
- **傳回從屬性程序。** 當`Set`程序傳回給呼叫程式碼，會繼續執行下列陳述式，提供要儲存的值。  
  
     `Set` 屬性程序可以傳回使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)或[Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)。  
  
     `Exit Property`和`Return`陳述式造成屬性程序立即結束。 任意數目的`Exit Property`並`Return`陳述式可以出現在任何位置的程序中，您可以混合`Exit Property`和`Return`陳述式。  
  
## <a name="example"></a>範例  
 下列範例會使用`Set`陳述式來設定屬性的值。  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>另請參閱

- [Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
