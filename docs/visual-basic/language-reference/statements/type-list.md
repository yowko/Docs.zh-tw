---
title: "類型清單 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 35e72414b236615dc230b654ccfeed290841fb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-list-visual-basic"></a>類型清單 (Visual Basic)
指定*型別參數*如*泛型*程式設計項目。 以逗號分隔多個參數。 以下是一個型別參數的語法。  
  
## <a name="syntax"></a>語法  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`genericmodifier`|選擇項。 可在泛型介面與委派中。 您可以宣告型別 covariant 使用[出](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)關鍵字或使用 contravariant[中](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)關鍵字。 請參閱 [共變數和反變數](../../programming-guide/concepts/covariance-contravariance/index.md)。|  
|`typename`|必要項。 型別參數的名稱。 這是預留位置，以對應的型別引數所提供的定義類型所取代。|  
|`constraintlist`|選擇項。 限制可以針對提供的資料類型的需求清單的`typename`。 如果您有多個條件約束，將其括在大括號 (`{ }`) 並以逗號分隔。 您必須引入與條件約束清單[為](../../../visual-basic/language-reference/statements/as-clause.md)關鍵字。 您使用`As`只能出現一次，在清單的開頭。|  
  
## <a name="remarks"></a>備註  
 每個泛型的程式設計項目必須使用至少一個的類型參數。 型別參數是特定類型的預留位置 (*建構的項目*) 用戶端程式碼指定當它建立泛型類型的執行個體。 您可以定義泛型類別、 結構、 介面、 程序或委派。  
  
 如需何時要定義泛型類型的詳細資訊，請參閱[Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。 如需型別參數名稱的詳細資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="rules"></a>規則  
  
-   **括號。** 如果您提供型別參數清單，您必須將它括在括號內，而且您必須使用引入清單[的](../../../visual-basic/language-reference/statements/of-clause.md)關鍵字。 您使用`Of`只能出現一次，在清單的開頭。  
  
-   **條件約束。** 一份*條件約束*型別參數可以利用任意組合包含下列項目：  
  
    -   任何數目的介面。 提供的型別必須實作每個介面，這份清單中。  
  
    -   最多一個類別。 提供的類型必須繼承自該類別。  
  
    -   `New` 關鍵字。 提供的型別必須公開您的泛型型別可存取的無參數建構函式。 這是適用於限制由一或多個介面的型別參數。 實作介面的類型不一定要公開建構函式，並根據建構函式的存取層級，泛型型別中的程式碼可能無法存取它。  
  
    -   任一`Class`關鍵字或`Structure`關鍵字。 `Class`關鍵字的條件約束需要傳遞給它的任何型別引數是參考類型，例如字串、 陣列或委派，或從類別建立物件的泛型型別參數。 `Structure`關鍵字限制泛型型別參數需要傳遞給它的任何型別引數是實值類型，例如結構、 列舉型別或基本資料類型。 您不能同時包含`Class`和`Structure`在同一個`constraintlist`。  
  
     提供的型別必須滿足您包含在每一項需求`constraintlist`。  
  
     每個類型參數條件約束是獨立的其他型別參數的條件約束。  
  
## <a name="behavior"></a>行為  
  
-   **編譯時期替代。** 當您從泛型的程式設計項目建立建構的類型時，您會提供每個類型參數定義的類型。 Visual Basic 編譯器會取代每個出現的該提供的型別`typename`泛型項目內。  
  
-   **條件約束不存在。** 如果您未指定任何型別參數的條件約束，您的程式碼受到作業和成員受到[物件資料類型](../../../visual-basic/language-reference/data-types/object-data-type.md)給該類型參數。  
  
## <a name="example"></a>範例  
 下列範例顯示泛型字典類別，包括將新的項目新增至字典的基本架構函數的基本架構定義。  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a>範例  
 因為`dictionary`是泛型，使用它的程式碼可以建立各種不同的物件，每個功能都相同，但根據不同的資料類型。 下列範例示範建立的程式碼行`dictionary`物件`String`項目和`Integer`索引鍵。  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a>範例  
 下列範例會顯示對應的基本架構定義，先前範例所產生。  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
 [New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)  
 [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Object 資料類型](../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [共變數和反變數](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
