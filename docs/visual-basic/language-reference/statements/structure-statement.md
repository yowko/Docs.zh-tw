---
title: "Structure Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Structure"
  - "Structure"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "user-defined types, Structure statement"
  - "compound data types"
  - "Structure keyword"
  - "Structure statement"
  - "UDT (user-defined types)"
  - "types [Visual Basic], user-defined"
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# Structure Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告結構的名稱，並引入組成結構之變數、屬性 \(Property\)、事件和程序的定義。  
  
## 語法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`attributelist`|選擇項。  請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇項。  可以是下列其中一項：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇項。  請參閱 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`Partial`|選擇項。  表示結構的部分定義。  請參閱 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)。|  
|`name`|必要項。  這個結構的名稱。  請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇項。  指定這是泛型結構。|  
|`typelist`|如果使用 [Of](../../../visual-basic/language-reference/statements/of-clause.md) 關鍵字，則為必要項。  這個結構的型別參數清單。  請參閱[型別清單](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Implements`|選擇項。  表示此結構會實作一個或多個介面的成員。  請參閱 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)。|  
|`interfacenames`|如果使用 `Implements` 陳述式，則此為必要項。  這個結構所實作的介面名稱。|  
|`datamemberdeclarations`|必要項。  沒有或多個 `Const`、`Dim`、`Enum` 或 `Event` 陳述式，宣告結構的 *資料成員*。|  
|`methodmemberdeclarations`|選擇項。  零或多個 `Function`、`Operator`、`Property` 或 `Sub` 程序的宣告，可做為結構的「*方法成員*」。|  
|`End Structure`|必要項。  結束 `Structure` 定義。|  
  
## 備註  
 `Structure` 陳述式定義可自訂的複合 \(Composite\) 實值型別。  「*結構*」是舊版 Visual Basic 的廣義使用者定義型別 \(UDT\)。  如需詳細資訊，請參閱[Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)。  
  
 結構支援許多和類別相同的功能。  例如，結構可以具有屬性和程序、可以實作介面，也可以具有參數型建構函式。  但是，結構與繼承 \(Inheritance\)、宣告和使用方式等區域中的類別之間有明顯的差異。  而且，類別是參考型別 \(Reference Type\)，而結構是實值型別 \(Value Type\)。  如需詳細資訊，請參閱[Structures and Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)。  
  
 `Structure` 只能用於命名空間或模組層級。  這表示結構的「*宣告內容*」必須是原始程式檔 \(Source File\)、命名空間 \(Namespace\)、類別、結構、模組或介面，並且不可以是程序或區塊。  如需詳細資訊，請參閱[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 結構預設值為 [Friend](../../../visual-basic/language-reference/modifiers/friend.md) 存取。  您可以使用存取修飾詞調整存取層級。  如需詳細資訊，請參閱[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## 規則  
  
-   **巢狀**：可以在另一個結構內定義某個結構。  外部結構會稱為「*包含結構*」，而內部結構則稱為「*巢狀結構*」。  然而，無法透過包含結構存取巢狀結構的成員。  您必須改為宣告具有巢狀結構資料型別的變數。  
  
-   **成員宣告**：您必須宣告結構的每個成員。  因為無法從結構中繼承，所以結構成員不得為 [Protected](../../../visual-basic/language-reference/modifiers/protected.md) 或 `Protected Friend`。  然而，結構本身可以是 `Protected` 或 `Protected Friend`。  
  
     您可以在結構中宣告零或多個非共用變數或非共用的非自訂事件。  您不能只有常數、屬性 \(Property\) 和程序，即使其中有些是非共用的。  
  
-   **初始設定**：：您不能將結構之任何非共用資料成員的值初始化為該資料成員宣告的一部分。  您必須在結構上以參數型建構函式來初始化這類資料成員，或在建立結構的執行個體後將值指派給成員。  
  
-   **繼承**結構不可以繼承非 <xref:System.ValueType> 的其他任何型別，所有結構都是從該型別繼承。  特別地是，某個結構不可以繼承另一個結構。  
  
     即使指定 <xref:System.ValueType>，也不可以在結構定義中使用 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)。  
  
-   **實作**如果結構使用 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)，則必須實作 `interfacenames` 中所指定之每個介面定義的每個成員。  
  
-   **預設屬性**使用 [Default](../../../visual-basic/language-reference/modifiers/default.md) 修飾詞，結構最多可以將一個屬性指定成它的「*預設屬性*」\(Default Property\)。  如需詳細資訊，請參閱[Default](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## 行為  
  
-   **存取層級**：在結構內，可宣告每個成員都具有它自己的存取層級。  所有結構成員預設值為 [Public](../../../visual-basic/language-reference/modifiers/public.md) 存取。  請注意，如果結構本身具有較嚴格的存取層級，則即使使用存取修飾詞調整成員的存取層級，也會自動限制成員的存取。  
  
-   **範圍。**：結構是位在包含命名空間、類別、結構或模組中的範圍內。  
  
     每一個結構成員的範圍是整個結構。  
  
-   **存留期**：結構本身不會有存留期。  而是，該結構的每個執行個體具有與其他所有執行個體無關的存留期。  
  
     [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) 子句建立執行個體時，會開始該執行個體的存留期。  保留變數的存留期時，則它會結束。  
  
     無法擴充結構執行個體的存留期。  靜態 \(Static\) 結構功能的大約值是由模組所提供。  如需詳細資訊，請參閱[Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)。  
  
     結構成員的存留期依據宣告方式和位置而定。  如需詳細資訊，請參閱 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) 中「存留期」的部分。  
  
-   **限定性條件。**：結構外面的程式碼必須使用該結構名稱限定成員名稱。  
  
     如果巢狀結構內的程式碼進行程式設計項目的資格不符參考，則 Visual Basic 依序會在巢狀結構、包含結構，以及最外層包含項目的外面搜尋項目。  如需詳細資訊，請參閱[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
-   **記憶體消耗量**：：和所有複合資料型別一樣，將成員的表面儲存配置加總起來不一定就是結構的總記憶體耗用量。  除此之外，您也不能就將記憶體中的儲存順序視為與您宣告的順序相同。  如果需要控制結構的儲存體配置，可將 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性 \(Attribute\) 套用到 `Structure` 陳述式。  
  
## 範例  
 下列範例使用 `Structure` 陳述式定義員工的一組相關資料。  它顯示使用 `Public`、`Friend` 和 `Private` 成員，以反映資料項目的敏感度，  也顯示出程序、屬性和事件成員。  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/structure-statement_1.vb)]  
  
## 請參閱  
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Structures and Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)