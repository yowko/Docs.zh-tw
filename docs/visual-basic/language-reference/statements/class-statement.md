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
ms.openlocfilehash: 7fbf2b15105a9fdcda5c7f6653753a4da54b394b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622335"
---
# <a name="class-statement-visual-basic"></a>Class 陳述式 (Visual Basic)
宣告類別的名稱，並引進變數、 屬性、 事件和類別包含的程序的定義。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`accessmodifier`|選擇性。 可以是下列其中一項：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私用](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [為 protected 的 Friend](../../language-reference/modifiers/protected-friend.md)<br />- [受保護的私用](../../language-reference/modifiers/private-protected.md)<br/><br/> 請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇性。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`MustInherit`|選擇性。 請參閱[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。|  
|`NotInheritable`|選擇性。 請參閱[NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)。|  
|`Partial`|選擇性。 表示類別的部分定義。 請參閱[部分](../../../visual-basic/language-reference/modifiers/partial.md)。|  
|`name`|必要項。 這個類別的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇性。 指定這為泛型類別。|  
|`typelist`|如果您使用所需[的](../../../visual-basic/language-reference/statements/of-clause.md)關鍵字。 這個類別的型別參數的清單。 請參閱[輸入清單](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Inherits`|選擇性。 指出這個類別會繼承另一個類別的成員。 請參閱[Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)。|  
|`classname`|如果您使用所需`Inherits`陳述式。 從這個類別衍生的類別名稱。|  
|`Implements`|選擇性。 指出這個類別會實作一或多個介面的成員。 請參閱[實作陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。|  
|`interfacenames`|如果您使用所需`Implements`陳述式。 這個類別會實作介面的名稱。|  
|`statements`|選擇性。 陳述式會定義這個類別的成員。|  
|`End Class`|必要項。 終止`Class`定義。|  
  
## <a name="remarks"></a>備註  
 A`Class`陳述式會定義新的資料型別。 A*類別*是物件導向程式設計 (OOP) 的基本建置組塊。 如需詳細資訊，請參閱 <<c0> [ 物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
 您可以使用`Class`只能在命名空間或模組層級。 這表示*宣告內容*類別必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，而且不可以是程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 每個類別執行個體都獨立於其他所有執行個體的存留期間。 此存留期開始時就會建立[New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)子句或這類函式<xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>。 指向 執行個體的所有變數，已都設定為時，它會結束[Nothing](../../../visual-basic/language-reference/nothing.md)或其他類別的執行個體。  
  
 類別預設會將[Friend](../../../visual-basic/language-reference/modifiers/friend.md)存取。 您可以調整它們的存取層級，使用存取修飾詞。 如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
- **巢狀結構。** 您可以定義在另一個類別。 外部的類別稱為*包含類別*，而內部的類別稱為*巢狀類別*。  
  
- **繼承**： 如果類別使用[Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)，您可以指定只有一個基底類別或介面。 類別無法繼承自多個項目。  
  
     類別無法繼承自另一個類別，具有更嚴格的存取層級。 例如，`Public`類別無法繼承自`Friend`類別。  
  
     類別無法繼承自巢狀類別。  
  
- **實作。** 如果類別使用[Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)，您必須實作由您指定在每個介面所定義的每個成員`interfacenames`。 這個例外狀況是重新實作的基底類別成員。 如需詳細資訊，請參閱 「 重新實作 」 中[實作](../../../visual-basic/language-reference/statements/implements-clause.md)。  
  
- **預設屬性。** 類別可以指定最多一個屬性作為其*屬性預設*。 如需詳細資訊，請參閱 <<c0> [ 預設](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## <a name="behavior"></a>行為  
  
- **存取層級。** 在類別中，您可以宣告具有它自己的存取層級的每個成員。 類別成員預設為[公開金鑰](../../../visual-basic/language-reference/modifiers/public.md)變數和常數，除了存取哪些預設[私人](../../../visual-basic/language-reference/modifiers/private.md)存取。 當類別具有限制存取比多個成員時，類別的存取層級的優先順序較高。  
  
- **範圍。** 類別是在其包含命名空間、 類別、 結構或模組的範圍中。  
  
     每個類別成員的範圍是整個類別。  
  
     **存留期。** Visual Basic 不支援靜態類別。 模組會提供靜態類別的對等功能等。 如需詳細資訊，請參閱 < [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)。  
  
     類別成員具有根據它們所宣告的方式和位置的存留期。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Basic 中的存留期](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
- **限定性條件。** 在類別外部的程式碼必須限定成員名稱，該類別的名稱。  
  
     如果巢狀類別內的程式碼進行程式設計的項目參考未限定，Visual Basic 搜尋項目第一次在巢狀類別中，然後在它的包含類別，等到最外層的包含項目。  
  
## <a name="classes-and-modules"></a>類別和模組  
 這些項目有許多相似之處，但有一些重要的差異。  
  
- **術語。** 舊版的 Visual Basic 會辨識兩種模組類型：*類別的模組*（.cls 檔案） 和*標準模組*（.bas 檔案）。 目前的版本會呼叫這些*類別*並*模組*分別。  
  
- **共用的成員。** 您可以控制類別的成員是否共用，或執行個體成員。  
  
- **物件導向。** 類別是物件導向，但模組不是。 您可以建立一或多個類別的執行個體。 如需詳細資訊，請參閱 <<c0> [ 物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Class`陳述式來定義的類別和數個成員。  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>另請參閱

- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [結構和類別](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [物件存留期：如何建立和終結物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
