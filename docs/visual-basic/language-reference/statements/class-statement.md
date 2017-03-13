---
title: "Class Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Class"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "class modules"
  - "Class statement"
  - "classes [Visual Basic], fields"
  - "fields, of classes"
  - "class types, class statements"
  - "classes [Visual Basic], creating"
  - "classes [Visual Basic], data members"
  - "data members, of classes"
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# Class Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告類別的名稱，並引入組成類別的變數、屬性 \(Property\)、事件和程序的定義。  
  
## 語法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`attributelist`|選擇項。  請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇項。  可以是下列其中一項：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇項。  請參閱 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`MustInherit`|選擇項。  請參閱 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。|  
|`NotInheritable`|選擇項。  請參閱 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)。|  
|`Partial`|選擇項。  表示類別的部分定義。  請參閱 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)。|  
|`name`|必要項。  這個類別的名稱。  請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇項。  指定這是泛型類別。|  
|`typelist`|如果使用 [Of](../../../visual-basic/language-reference/statements/of-clause.md) 關鍵字，則為必要項。  這個類別的型別參數清單。  請參閱[型別清單](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Inherits`|選擇項。  表示此類別會繼承另一個類別的成員。  請參閱 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)。|  
|`classname`|如果使用 `Inherits` 陳述式，則此為必要項。  衍生這個類別的類別名稱。|  
|`Implements`|選擇項。  表示此類別會實作一或多個介面的成員。  請參閱 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)。|  
|`interfacenames`|如果使用 `Implements` 陳述式，則此為必要項。  此類別所實作的介面名稱。|  
|`statements`|選擇項。  定義此類別之成員的陳述式。|  
|`End Class`|必要項。  結束 `Class` 定義。|  
  
## 備註  
 `Class` 陳述式會定義新的資料型別。  「*類別*」是物件導向程式設計 \(OOP\) 的基礎建置組塊 \(Building Block\)。  如需詳細資訊，請參閱 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
 `Class` 只能用於命名空間或模組層級。  這表示類別的「*宣告內容*」必須是原始程式檔 \(Source File\)、命名空間、類別、結構、模組或介面，而不能是程序或區塊。  如需詳細資訊，請參閱[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 類別的每個執行個體都有與其他執行個體無關的存留期 \(Lifetime\)。  使用 [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) 子句或 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A> 這類的函式建立執行個體時，這個存留期就會開始。  當指向執行個體的所有變數都已設為 [Nothing](../../../visual-basic/language-reference/nothing.md) 或其他類別的執行個體時，就會結束這個存留期。  
  
 類別會預設為 [Friend](../../../visual-basic/language-reference/modifiers/friend.md) 存取。  您可以使用存取修飾詞調整存取層級。  如需詳細資訊，請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## 規則  
  
-   **巢狀** ：您可以在某個類別內定義另一個類別。  外部類別稱為「*包含類別*」，內部類別則稱為「*巢狀類別*」。  
  
-   **繼承** 如果類別使用 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)，您就只能指定一個基底類別或繼承。  類別無法繼承自多個項目。  
  
     類別無法繼承自具有更受限制之存取層級的另一個類別。  例如，`Public` 類別無法繼承自 `Friend` 類別。  
  
     類別無法繼承自在其中形成巢狀的類別。  
  
-   **實作** 如果類別會使用 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)，則您必須實作在 `interfacenames` 中指定之每個介面所定義的每個成員。  這個動作的例外狀況是重新實作基底類別成員。  如需詳細資訊，請參閱 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) 中「重新實作」的內容。  
  
-   **預設屬性** 類別最多可以指定一個屬性做為它的「*預設屬性*」\(Default Property\)。  如需詳細資訊，請參閱[Default](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## 行為  
  
-   **存取層級** ：在類別內，您可以使用成員本身的存取層級宣告各個成員。  類別成員會預設值為 [Public](../../../visual-basic/language-reference/modifiers/public.md) 存取，但預設值為 [Private](../../../visual-basic/language-reference/modifiers/private.md) 存取的變數和常數除外。  當類別所擁有的存取比它的其中一個成員更受限制時，會優先使用類別存取層級。  
  
-   **範圍。** ：類別所在的範圍會涵蓋它所包含的命名空間、類別、結構或模組。  
  
     每一個類別成員的範圍都是整個類別。  
  
     **存留期** ：Visual Basic 不支援靜態類別。  模組會提供相當於靜態類別的功能。  如需詳細資訊，請參閱 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)。  
  
     類別成員所擁有的存留期則會依據宣告這些存留期的方法和地點而定。  如需詳細資訊，請參閱 [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
-   **限定性條件。** ：類別外的程式碼必須以該類別的名稱，限定成員的名稱。  
  
     如果巢狀類別內部的程式碼會對程式設計項目產生未限定的參考，Visual Basic 會先在巢狀類別中搜尋項目，然後在其包含類別中進行搜尋，依此類推，直到結束對最外層之包含項目的搜尋為止。  
  
## 類別和模組  
 這些項目有許多相似點，但也有一些重要的差異。  
  
-   **用語** 舊版的 Visual Basic 可以辨認兩種模組：「*類別模組*」\(Class Module，.cls 檔案\) 和「*標準模組*」\(Standard Module，.bas 檔案\)。  目前的版本會分別呼叫這些「*類別*」和「*模組*」。  
  
-   **共用成員** ：您可以控制類別成員是共用成員或執行個體成員。  
  
-   **物件導向** ：類別為物件導向，但模組不是。  您可以對類別建立一或多個執行個體。  如需詳細資訊，請參閱 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## 範例  
 下列範例會使用 `Class` 陳述式，定義類別和數個成員。  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## 請參閱  
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Structures and Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)