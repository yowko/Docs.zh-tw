---
title: "Interface Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Interface"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interface statement [Visual Basic]"
  - "interfaces, interface definition"
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# Interface Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告介面的名稱並引入組成介面之成員的定義。  
  
## 語法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`attributelist`|選擇項。  請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇項。  可以是下列其中一項：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇項。  請參閱 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`name`|必要項。  這個介面的名稱。  請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇項。  指定這是泛型介面。|  
|`typelist`|如果使用 [Of](../../../visual-basic/language-reference/statements/of-clause.md) 關鍵字，則為必要項。  這個介面的型別參數清單。  每個型別參數都可以使用 `In` 和 `Out` 泛型修飾詞宣告為 Variant。  請參閱[型別清單](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Inherits`|選擇項。  表示此介面會繼承其他介面的屬性和成員。  請參閱 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)。|  
|`interfacenames`|如果使用 `Inherits` 陳述式，則此為必要項。  衍生這個介面的來源介面名稱。|  
|`modifiers`|選擇項。  所定義之介面成員的適當修飾詞。|  
|`Property`|選擇項。  定義屬於介面成員的屬性。|  
|`Function`|選擇項。  定義屬於介面成員的 `Function` 程序。|  
|`Sub`|選擇項。  定義屬於介面成員的 `Sub` 程序。|  
|`Event`|選擇項。  定義屬於介面成員的事件。|  
|`Interface`|選擇項。  定義此介面內的巢狀介面。  巢狀介面定義必須以 `End Interface` 陳述式做結尾。|  
|`Class`|選擇項。  定義屬於介面成員的類別。  成員類別定義必須以 `End Class` 陳述式做結尾。|  
|`Structure`|選擇項。  定義屬於介面成員的結構。  成員結構定義必須以 `End Structure` 陳述式做結尾。|  
|`membername`|對於被定義為介面成員的每個屬性、程序、事件、介面、類別或結構而言為必要項。  成員的名稱。|  
|`End Interface`|結束 `Interface` 定義。|  
  
## 備註  
 「*介面*」會定義類別和結構可以實作的一組成員，例如屬性和程序。  介面只會定義成員的簽章，而非內部運作。  
  
 類別或結構會為介面所定義的每個成員提供程式碼，以便實作介面。  最後，當應用程式根據該類別或結構建立介面時，此物件會存在並於記憶體中執行。  如需詳細資訊，請參閱 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)和 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 `Interface` 只能用於命名空間或模組層級。  這表示介面的「*宣告內容*」必須是原始程式檔 \(Source File\)、命名空間、類別、結構、模組或介面，而不能是程序或區塊。  如需詳細資訊，請參閱[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 介面會預設為 [Friend](../../../visual-basic/language-reference/modifiers/friend.md) 存取。  您可以使用存取修飾詞調整存取層級。  如需詳細資訊，請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## 規則  
  
-   **巢狀介面** ：您可以在一個介面內部定義其他介面。  外部介面會稱為「*包含介面*」，而內部介面則稱為「*巢狀介面*」。  
  
-   **成員宣告** 當您宣告屬性或程序做為介面的成員時，只定義該屬性或程序的「*簽章*」\(Signature\)。  這包含了項目型別 \(屬性或程序\)、參數和參數型別，以及傳回型別。  因為如此，成員定義只會使用一行程式碼，並且結束介面中無效的陳述式，例如 `End Function` 或 `End Property`。  
  
     相對地，當您定義列舉型別或結構時，或是巢狀類別或介面時，則必須包含資料成員。  
  
-   **成員修飾詞** 定義模組成員時，您不能使用任何存取修飾詞，也不能指定 [Shared](../../../visual-basic/language-reference/modifiers/shared.md) 或除了 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md) 以外的任何程序修飾詞。  您可以使用 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) 宣告任何成員，而且可以在定義屬性時，使用 [Default](../../../visual-basic/language-reference/modifiers/default.md)、[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) 或 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)。  
  
-   **繼承** 如果介面使用 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)，則可以指定一個或多個基底介面。  即使兩個介面每個都定義同名的成員，也可以繼承這兩個介面。  如果這樣做，則實作程式碼必須使用名稱限定，以指定它所實作的成員。  
  
     介面無法繼承另一個具有較受限存取層級的介面。  例如，`Public` 介面無法繼承 `Friend` 介面。  
  
     介面無法繼承自內部的巢狀介面。  
  
-   **實作** 當類別使用 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) 陳述式實作這個介面時，它必須實作每個定義在此介面中的成員。  此外，實作程式碼中的每個簽章必須完全符合這個介面中所定義的對應簽章。  不過，實作程式碼中的成員名稱不必符合介面中所定義的成員名稱。  
  
     當類別正在實作程序時，它無法將此程序指定為 `Shared`。  
  
-   **預設屬性** 介面最多可以指定一個屬性做為「*預設屬性*」\(Default Property\)，不需使用屬性名稱即可參考此屬性。  您可以利用 [Default](../../../visual-basic/language-reference/modifiers/default.md) 修飾詞宣告屬性，以便指定此種屬性。  
  
     請注意，這表示只有在介面未繼承預設屬性時，才可以定義預設屬性。  
  
## 行為  
  
-   **存取層級** 所有介面隱含有 [Public](../../../visual-basic/language-reference/modifiers/public.md) 存取。  您在定義成員時，不能使用任何存取修飾詞。  不過，實作介面的類別可以為每個實作的成員宣告存取層級。  
  
     如果您指派類別執行個體給變數，則成員的存取層級可視此變數的資料型別為基礎介面或實作類別而定。  下列範例將說明這點。  
  
     [!code-vb[VbVbalrStatements#39](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_1.vb)]  
  
     如果您透過 `varAsInterface` 存取類別成員，則這些成員都具有公用存取。  不過，如果透過 `varAsClass` 存取成員，則 `Sub` 程序 `doSomething` 具有私用存取。  
  
-   **範圍。** ：介面的命名空間、類別、結構或模組都會在範圍中。  
  
     每個介面成員的範圍都是整個介面。  
  
-   **存留期** ：介面本身沒有存留期，成員也沒有存留期。  當類別實作介面且將某個物件建立為該類別的執行個體時，該物件會在執行所在的應用程式中有存留期。  如需詳細資訊，請參閱 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) 中「存留期」的部分。  
  
## 範例  
 下列範例會使用 `Interface` 陳述式定義名為 `thisInterface` 的介面，這個介面必須以 `Property` 陳述式和 `Function` 陳述式實作。  
  
 [!code-vb[VbVbalrStatements#40](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_2.vb)]  
  
 請注意，`Property` 和 `Function` 陳述式不會引入介面中以 `End Property` 和 `End Function` 結尾的區塊。  介面只會定義成員的簽章。  完整的 `Property` 和 `Function` 區塊會出現在實作 `thisInterface` 的類別中。  
  
## 請參閱  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [泛型介面中的變異數](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)