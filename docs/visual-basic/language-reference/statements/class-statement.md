---
title: "Class 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Class
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
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df86ef0eec67d96f2f997dc5dac7ee2357c6362b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="class-statement-visual-basic"></a>Class 陳述式 (Visual Basic)
宣告類別的名稱，並導入的變數、 屬性、 事件和類別包含的程序定義。  
  
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
|`attributelist`|選擇項。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇項。 可以是下列其中一項：<br /><br /> -   [公用](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私用](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇項。 請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`MustInherit`|選擇項。 請參閱[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。|  
|`NotInheritable`|選擇項。 請參閱[NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)。|  
|`Partial`|選擇項。 表示類別的部分定義。 請參閱[部分](../../../visual-basic/language-reference/modifiers/partial.md)。|  
|`name`|必要項。 這個類別的名稱。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇項。 指定這是泛型類別。|  
|`typelist`|如果您使用所需[的](../../../visual-basic/language-reference/statements/of-clause.md)關鍵字。 這個類別的型別參數的清單。 請參閱[輸入清單](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Inherits`|選擇項。 表示這個類別會繼承另一個類別的成員。 請參閱[Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)。|  
|`classname`|如果您使用所需`Inherits`陳述式。 這個類別衍生自類別的名稱。|  
|`Implements`|選擇項。 指出這個類別會實作一個或多個介面的成員。 請參閱[實作陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。|  
|`interfacenames`|如果您使用所需`Implements`陳述式。 這個類別會實作介面的名稱。|  
|`statements`|選擇項。 這個類別的成員定義的陳述式。|  
|`End Class`|必要項。 終止`Class`定義。|  
  
## <a name="remarks"></a>備註  
 A`Class`陳述式定義新的資料類型。 A*類別*是物件導向程式設計 (OOP) 的基本建置組塊。 如需詳細資訊，請參閱[物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
 您可以使用`Class`只能在命名空間或模組層級。 這表示*宣告內容*類別必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，並且不能是程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 類別的每個執行個體都有獨立的所有其他執行個體的存留期間。 此存留期開始時就會建立[New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)子句或函式，例如<xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>。 結束時已設定為指向執行個體的所有變數[Nothing](../../../visual-basic/language-reference/nothing.md)或其他類別的執行個體。  
  
 類別會預設為[Friend](../../../visual-basic/language-reference/modifiers/friend.md)存取。 您可以調整其存取層級，使用存取修飾詞。 如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
-   **巢狀結構。** 您可以定義在另一個類別。 外部的類別稱為*包含類別*，而內部的類別稱為*巢狀類別*。  
  
-   **繼承**： 如果類別會使用[Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)，您可以指定一個基底類別或介面。 類別無法繼承自多個項目。  
  
     類別無法繼承自另一個類別，具有更嚴格的存取層級。 例如，`Public`類別不可繼承自`Friend`類別。  
  
     類別無法繼承自巢狀類別。  
  
-   **實作。** 如果類別會使用[Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)，您必須實作由您指定在每個介面所定義的每個成員`interfacenames`。 這個例外狀況是重新實作，則基底類別成員。 如需詳細資訊，請參閱 「 客戶 」 中的[實作](../../../visual-basic/language-reference/statements/implements-clause.md)。  
  
-   **預設屬性。** 類別可以指定最多一個屬性做為其*預設屬性*。 如需詳細資訊，請參閱[預設](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## <a name="behavior"></a>行為  
  
-   **存取層級。** 在類別中，您可以宣告具有自己的存取層級的每個成員。 類別成員預設為[公用](../../../visual-basic/language-reference/modifiers/public.md)變數和常數，除了存取的預設值為[私人](../../../visual-basic/language-reference/modifiers/private.md)存取。 當類別更有限制存取比其中一個成員時，類別存取層級的優先順序較高。  
  
-   **範圍。** 類別是在範圍中，其包含命名空間、 類別、 結構或模組。  
  
     每個類別成員的範圍是整個類別。  
  
     **存留期。** Visual Basic 不支援靜態類別。 靜態類別的功能對等項目會提供模組。 如需詳細資訊，請參閱[Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)。  
  
     類別成員具有取決於如何及在何處宣告它們的存留期。 如需詳細資訊，請參閱[在 Visual Basic 中的存留期](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
-   **限定性條件。** 在類別外部的程式碼必須限定成員名稱，該類別的名稱。  
  
     如果巢狀類別內的程式碼會不合格的程式設計項目參考，Visual Basic 會搜尋項目的第一次在巢狀類別中，然後在它的包含類別，依此類推最外層包含的項目。  
  
## <a name="classes-and-modules"></a>類別和模組  
 這些項目有許多相似處，但有一些重要的差異。  
  
-   **術語。** 舊版的 Visual Basic 辨識兩種類型的模組：*類別模組*（.cls 檔案） 和*標準模組*（.bas 檔案）。 目前的版本會呼叫這些*類別*和*模組*分別。  
  
-   **共用的成員。** 您可以控制類別的成員是共用或執行個體成員。  
  
-   **物件的方向。** 類別是物件導向，但模組不是。 您可以建立一或多個執行個體的類別。 如需詳細資訊，請參閱[物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Class`陳述式來定義類別和數個成員。  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [結構和類別](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
 [物件存留期：物件的建立和終結](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
