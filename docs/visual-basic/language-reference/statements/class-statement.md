---
title: Class 陳述式 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 2e4514686afcbbe0e9ff0b3326c1be212db4f9f8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005161"
---
# <a name="class-statement-visual-basic"></a>Class 陳述式 (Visual Basic)
宣告類別的名稱，並引進類別所組成之變數、屬性、事件和程式的定義。  
  
## <a name="syntax"></a>語法  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`attributelist`|選擇性。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇性。 可以是下列其中一項：<br /><br /> -   [公用](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私](../../../visual-basic/language-reference/modifiers/private.md)用<br />@no__t 0[保護的 Friend](../../language-reference/modifiers/protected-friend.md)<br />- [私用保護](../../language-reference/modifiers/private-protected.md)<br/><br/> 請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇性。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`MustInherit`|選擇性。 請參閱[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。|  
|`NotInheritable`|選擇性。 請參閱[NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)。|  
|`Partial`|選擇性。 表示類別的部分定義。 請參閱[部分](../../../visual-basic/language-reference/modifiers/partial.md)。|  
|`name`|必要項。 這個類別的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇性。 指定這是泛型類別。|  
|`typelist`|如果您使用 of 關鍵字，則[為必要項](../../../visual-basic/language-reference/statements/of-clause.md)。 這個類別的型別參數清單。 請參閱[類型清單](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Inherits`|選擇性。 表示這個類別會繼承另一個類別的成員。 請參閱[Inherits 語句](../../../visual-basic/language-reference/statements/inherits-statement.md)。|  
|`classname`|如果您使用 `Inherits` 語句，則為必要。 這個類別衍生來源的類別名稱。|  
|`Implements`|選擇性。 表示這個類別會執行一或多個介面的成員。 請參閱[Implements 語句](../../../visual-basic/language-reference/statements/implements-statement.md)。|  
|`interfacenames`|如果您使用 `Implements` 語句，則為必要。 這個類別所執行之介面的名稱。|  
|`statements`|選擇性。 定義此類別之成員的語句。|  
|`End Class`|必要項。 終止 `Class` 定義。|  
  
## <a name="remarks"></a>備註  
 @No__t-0 語句會定義新的資料類型。 「*類別*」（class）是物件導向程式設計（OOP）的基礎建立組塊。 如需詳細資訊，請參閱[物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
 您只能在命名空間或模組層級使用 `Class`。 這表示類別的宣告*內容*必須是原始程式檔、命名空間、類別、結構、模組或介面，而且不能是程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 類別的每個實例都有一個存留期，與所有其他實例無關。 此存留期是由[新的 Operator](../../../visual-basic/language-reference/operators/new-operator.md)子句或函數（如 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>）所建立。 當所有指向實例的變數都已設定為「[無](../../../visual-basic/language-reference/nothing.md)」或其他類別的實例時，它就會結束。  
  
 類別預設為[Friend](../../../visual-basic/language-reference/modifiers/friend.md)存取。 您可以使用存取修飾詞來調整其存取層級。 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
- **嵌入.** 您可以在另一個類別中定義一個類別。 外部類別稱為「*包含類別*」，而內部類別稱為「*嵌套類別*」。  
  
- **繼承**： 如果類別使用[Inherits 語句](../../../visual-basic/language-reference/statements/inherits-statement.md)，您只能指定一個基類或介面。 類別無法繼承自一個以上的元素。  
  
     類別無法繼承自另一個具有更嚴格存取層級的類別。 例如，@no__t 0 類別無法繼承自 @no__t 1 類別。  
  
     類別無法繼承自其內嵌套的類別。  
  
- **實作.** 如果類別使用[Implements 語句](../../../visual-basic/language-reference/statements/implements-statement.md)，您必須執行您在 `interfacenames` 中指定的每個介面所定義的每個成員。 例外狀況是基類成員的重新實作。 如需詳細資訊，請參閱[Implements](../../../visual-basic/language-reference/statements/implements-clause.md)中的 "重新實作"。  
  
- **Default 屬性。** 類別最多可以指定一個屬性做為其*預設屬性*。 如需詳細資訊，請參閱[Default](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## <a name="behavior"></a>行為  
  
- **存取層級。** 在類別中，您可以使用自己的存取層級來宣告每個成員。 類別成員預設為[公用](../../../visual-basic/language-reference/modifiers/public.md)存取，但變數和常數除外，預設為[私](../../../visual-basic/language-reference/modifiers/private.md)用存取。 當類別的存取權比它的其中一個成員更受限制時，類別存取層級的優先順序會較高。  
  
- **範圍.** 類別會在其包含的命名空間、類別、結構或模組的範圍內。  
  
     每個類別成員的範圍都是整個類別。  
  
     **期.** Visual Basic 不支援靜態類別。 靜態類別的功能對等項是由模組所提供。 如需詳細資訊，請參閱[Module 語句](../../../visual-basic/language-reference/statements/module-statement.md)。  
  
     類別成員有存留期，視宣告的方式和位置而定。 如需詳細資訊，請參閱[Visual Basic 中的存留期](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
- **加.** 類別外的程式碼必須使用該類別的名稱來限定成員名稱。  
  
     如果嵌套類別內的程式碼會對程式設計專案進行不合格的參考，Visual Basic 會先在嵌套類別中搜尋該專案，然後在其包含的類別中，依此類推，直到最外層的包含元素。  
  
## <a name="classes-and-modules"></a>類別和模組  
 這些元素有許多相似之處，但也有一些重要的差異。  
  
- **庫.** 舊版的 Visual Basic 會辨識兩種類型的模組：*類別模組*（cls 檔）和*標準模組*（bas 檔案）。 目前的版本會分別呼叫這些*類別*和*模組*。  
  
- **共用成員。** 您可以控制類別的成員是否為共用或實例成員。  
  
- **物件方向。** 類別是物件導向，但模組則不是。 您可以建立一或多個類別的實例。 如需詳細資訊，請參閱[物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Class` 語句來定義類別和數個成員。  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>另請參閱

- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [結構和類別](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- @no__t 0Object 存留期：如何建立和終結物件 @ no__t-0
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
