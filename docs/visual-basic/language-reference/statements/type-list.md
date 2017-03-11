---
title: "Type List (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "StructureConstraint"
  - "vb.StructureConstraint"
  - "ClassConstraint"
  - "vb.ClassConstraint"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "class constraint"
  - "constraints, Visual Basic generic types"
  - "generic parameters"
  - "generics [Visual Basic], constraints"
  - "generics [Visual Basic], type list"
  - "structure constraint"
  - "constraints, in type parameters"
  - "generics [Visual Basic], generic types"
  - "parameters, type"
  - "constraints, Structure keyword"
  - "type parameters, constraints"
  - "types [Visual Basic], generic"
  - "parameters, generic"
  - "generics [Visual Basic], type parameters"
  - "type parameters"
  - "constraints, Class keyword"
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 33
---
# Type List (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定「*泛型*」程式設計項目的「*型別參數*」。  參數之間以逗號來分隔。  下列是其中一個型別參數的語法。  
  
## 語法  
  
```  
  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`genericmodifier`|選擇項。  只能用於泛型介面和委派。  您可以使用 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) 關鍵字宣告型別 Covariant，或使用 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) 關鍵字宣告型別 Contravariant。  請參閱 [共變數和反變數](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)。|  
|`typename`|必要項。  型別參數的名稱。  這是替代符號 \(Placeholder\)，會替換為對應型別引數所提供的已定義型別。|  
|`constraintlist`|選擇項。  需求清單，其限制可提供給 `typename` 的資料型別。  如果有多個條件約束 \(Constraint\)，則請將它們封入大括號 \(`{ }`\) 中，並以逗號隔開。  您必須使用 [As](../../../visual-basic/language-reference/statements/as-clause.md) 關鍵字來引入條件約束清單。  只可在清單開頭，使用一次 `As`。|  
  
## 備註  
 每個泛型程式設計項目都至少必須取用一個型別參數。  型別參數是特定型別的替代符號 \(「*建構的項目*」\)，用戶端程式碼會在建立泛型型別的執行個體時指定此特定型別。  可定義泛型類別 \(Class\)、結構、介面、程序或委派 \(Delegate\)。  
  
 如需何時定義泛型型別的詳細資訊，請參閱 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。  如需型別參數名稱的詳細資訊，請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## 規則  
  
-   **括弧** 如果您提供型別參數清單，必須將它封入括號中，也必須使用 [Of](../../../visual-basic/language-reference/statements/of-clause.md) 關鍵字來引入該清單。  只可在清單開頭，使用一次 `Of`。  
  
-   **條件約束** 型別參數上的「*條件約束*」\(Constraint\) 清單可包含下列任何項目的組合：  
  
    -   任意數目的介面。  提供的型別必須實作這個清單中的每個介面。  
  
    -   最多一個類別。  提供的型別必須繼承自該類別。  
  
    -   `New` 關鍵字。  提供的型別必須公開 \(Expose\) 泛型型別可存取的無參數建構函式。  您限制一或多個介面的型別參數時，這十分有用。  實作介面的型別不一定要公開建構函式，且視建構函式的存取層級而定，泛型型別內的程式碼可能無法加以存取。  
  
    -   `Class` 關鍵字或 `Structure` 關鍵字兩者其中一個。  `Class` 關鍵字會約束傳遞給泛型型別參數的型別引數必須是參考型別，例如字串、陣列、委派或從類別建立的物件。  `Structure` 關鍵字則約束傳遞給泛型型別參數的型別引數必須是實值型別，例如結構、列舉或基礎資料型別 \(Elementary Data Type\)。  您不能在同一 `constraintlist` 中同時包括 `Class` 和 `Structure`。  
  
     提供的型別必須滿足 `constraintlist` 中所含的每個需求。  
  
     每個型別參數的條件約束都與其他型別參數的條件約束無關。  
  
## 行為  
  
-   **編譯時期的替代作業** ：從泛型程式設計項目建立建構的型別時，您會提供每個型別參數的已定義型別。  Visual Basic 編譯器會替換泛型項目內每次出現之 `typename` 相對應提供的型別。  
  
-   **缺少條件約束** 如果未指定型別參數的任何條件約束，則會將程式碼限制成該型別參數之 [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)所支援的作業和成員。  
  
## 範例  
 下列範例會顯示泛型字典類別的基本架構定義，包括將新項目加入至字典的基本架構函式。  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/type-list_1.vb)]  
  
## 範例  
 因為 `dictionary` 是泛型的，所以使用它的程式碼可據以建立各種物件，且每個功能都相同，但可在不同資料型別上作用。  下列範例會顯示程式碼，用以建立具有 `String` 項目和 `Integer` 索引鍵的 `dictionary` 物件。  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/type-list_2.vb)]  
  
## 範例  
 下列範例會顯示以上範例所產生的對等基本架構定義。  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/type-list_3.vb)]  
  
## 請參閱  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)   
 [New Operator](../../../visual-basic/language-reference/operators/new-operator.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [共變數和反變數](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)