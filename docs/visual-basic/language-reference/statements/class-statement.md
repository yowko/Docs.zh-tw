---
title: Class 陳述式
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
ms.openlocfilehash: bdb73772dfe0e6d49d89a4ef006b1bceac14c8ee
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397151"
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
|`attributelist`|選擇性。 請參閱[屬性清單](attribute-list.md)。|  
|`accessmodifier`|選擇性。 可以是下列其中一項：<br /><br /> -   [公立](../modifiers/public.md)<br />-   [免受](../modifiers/protected.md)<br />-   [給](../modifiers/friend.md)<br />-   [私人](../modifiers/private.md)<br />-   [受保護的 Friend](../modifiers/protected-friend.md)<br />- [私用保護](../modifiers/private-protected.md)<br/><br/> 請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇性。 請參閱[Shadows](../modifiers/shadows.md)。|  
|`MustInherit`|選擇性。 請參閱[MustInherit](../modifiers/mustinherit.md)。|  
|`NotInheritable`|選擇性。 請參閱[NotInheritable](../modifiers/notinheritable.md)。|  
|`Partial`|選擇性。 表示類別的部分定義。 請參閱[部分](../modifiers/partial.md)。|  
|`name`|必要。 這個類別的名稱。 請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇性。 指定這是泛型類別。|  
|`typelist`|如果您使用 of 關鍵字，則[為必要項](of-clause.md)。 這個類別的型別參數清單。 請參閱[類型清單](type-list.md)。|  
|`Inherits`|選擇性。 表示這個類別會繼承另一個類別的成員。 請參閱[Inherits 語句](inherits-statement.md)。|  
|`classname`|如果您使用語句，則為必要 `Inherits` 。 這個類別衍生來源的類別名稱。|  
|`Implements`|選擇性。 表示這個類別會執行一或多個介面的成員。 請參閱[Implements 語句](implements-statement.md)。|  
|`interfacenames`|如果您使用語句，則為必要 `Implements` 。 這個類別所執行之介面的名稱。|  
|`statements`|選擇性。 定義此類別之成員的語句。|  
|`End Class`|必要。 結束 `Class` 定義。|  
  
## <a name="remarks"></a>備註  
 `Class`語句會定義新的資料類型。 「*類別*」（class）是物件導向程式設計（OOP）的基礎建立組塊。 如需詳細資訊，請參閱[物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)。  
  
 您 `Class` 只能在命名空間或模組層級使用。 這表示類別的宣告*內容*必須是原始程式檔、命名空間、類別、結構、模組或介面，而且不能是程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。  
  
 類別的每個實例都有一個存留期，與所有其他實例無關。 此存留期是由[新的 Operator](../operators/new-operator.md)子句或函數（例如）所建立 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A> 。 當所有指向實例的變數都已設定為「[無](../nothing.md)」或其他類別的實例時，它就會結束。  
  
 類別預設為[Friend](../modifiers/friend.md)存取。 您可以使用存取修飾詞來調整其存取層級。 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
- **嵌入.** 您可以在另一個類別中定義一個類別。 外部類別稱為「*包含類別*」，而內部類別稱為「*嵌套類別*」。  
  
- **繼承性.** 如果類別使用[Inherits 語句](inherits-statement.md)，您只能指定一個基類或介面。 類別無法繼承自一個以上的元素。  
  
     類別無法繼承自另一個具有更嚴格存取層級的類別。 例如， `Public` 類別無法繼承自 `Friend` 類別。  
  
     類別無法繼承自其內嵌套的類別。  
  
- **實作.** 如果類別使用[Implements 語句](implements-statement.md)，您就必須執行您在中指定的每個介面所定義的每個成員 `interfacenames` 。 例外狀況是基類成員的重新實作。 如需詳細資訊，請參閱[Implements](implements-clause.md)中的 "重新實作"。  
  
- **Default 屬性。** 類別最多可以指定一個屬性做為其*預設屬性*。 如需詳細資訊，請參閱[Default](../modifiers/default.md)。  
  
## <a name="behavior"></a>行為  
  
- **存取層級。** 在類別中，您可以使用自己的存取層級來宣告每個成員。 類別成員預設為[公用](../modifiers/public.md)存取，但變數和常數除外，預設為[私](../modifiers/private.md)用存取。 當類別的存取權比它的其中一個成員更受限制時，類別存取層級的優先順序會較高。  
  
- **範圍.** 類別會在其包含的命名空間、類別、結構或模組的範圍內。  
  
     每個類別成員的範圍都是整個類別。  
  
     **期.** Visual Basic 不支援靜態類別。 靜態類別的功能對等項是由模組所提供。 如需詳細資訊，請參閱[Module 語句](module-statement.md)。  
  
     類別成員有存留期，視宣告的方式和位置而定。 如需詳細資訊，請參閱[Visual Basic 中的存留期](../../programming-guide/language-features/declared-elements/lifetime.md)。  
  
- **加.** 類別外的程式碼必須使用該類別的名稱來限定成員名稱。  
  
     如果嵌套類別內的程式碼會對程式設計專案進行不合格的參考，Visual Basic 會先在嵌套類別中搜尋該專案，然後在其包含的類別中，依此類推，直到最外層的包含元素。  
  
## <a name="classes-and-modules"></a>類別和模組  
 這些元素有許多相似之處，但也有一些重要的差異。  
  
- **庫.** 舊版的 Visual Basic 會辨識兩種類型的模組：*類別模組*（cls 檔）和*標準模組*（bas 檔案）。 目前的版本會分別呼叫這些*類別*和*模組*。  
  
- **共用成員。** 您可以控制類別的成員是否為共用或實例成員。  
  
- **物件方向。** 類別是物件導向，但模組則不是。 您可以建立一或多個類別的實例。 如需詳細資訊，請參閱[物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Class` 語句來定義類別和數個成員。  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>另請參閱

- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)
- [結構與類別](../../programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface 陳述式](interface-statement.md)
- [Module 陳述式](module-statement.md)
- [Property Statement](property-statement.md)
- [物件存留期：物件的建立和終結](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [作法：使用泛型類別](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
