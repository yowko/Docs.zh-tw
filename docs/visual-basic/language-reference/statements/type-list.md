---
title: Type List
ms.date: 07/20/2015
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
ms.openlocfilehash: 3f2aaa65293ed2bcc6c8eeb4bd77e49907d93425
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352780"
---
# <a name="type-list-visual-basic"></a>類型清單 (Visual Basic)

指定*泛型*程式設計項目的*類型參數*。 多個參數會以逗號分隔。 以下是一個型別參數的語法。

## <a name="syntax"></a>語法

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`genericmodifier`|選擇性。 只能在泛型介面和委派中使用。 您可以使用[Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)關鍵字或逆變性來宣告類型的協變數，方法是使用[In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)關鍵字。 請參閱 [共變數和反變數](../../programming-guide/concepts/covariance-contravariance/index.md)。|
|`typename`|必要。 型別參數的名稱。 這是預留位置，要由對應的類型引數所提供的已定義類型取代。|
|`constraintlist`|選擇性。 限制可為 `typename`提供之資料類型的需求清單。 如果您有多個條件約束，請以大括弧（`{ }`）括住，並以逗號分隔。 您必須使用[As](../../../visual-basic/language-reference/statements/as-clause.md)關鍵字來引進條件約束清單。 您只需要在清單的開頭使用 `As` 一次。|

## <a name="remarks"></a>備註

每個泛型程式設計項目都必須採用至少一個型別參數。 類型參數是用戶端程式代碼在建立泛型型別的實例時所指定之特定類型（*結構化元素*）的預留位置。 您可以定義泛型類別、結構、介面、程式或委派。

如需何時定義泛型型別的詳細資訊，請參閱[Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。 如需型別參數名稱的詳細資訊，請參閱宣告的[元素名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。

## <a name="rules"></a>規則

- **後.** 如果您提供型別參數清單，您必須將它括在括弧中，而且您必須使用關鍵字[來](../../../visual-basic/language-reference/statements/of-clause.md)引進清單。 您只需要在清單的開頭使用 `Of` 一次。

- **條件.** 類型參數的*條件約束*清單可以包含下列任何組合中的專案：

  - 任何數目的介面。 提供的類型必須執行此清單中的每個介面。

  - 最多一個類別。 提供的類型必須繼承自該類別。

  - `New` 關鍵字。 提供的型別必須公開您的泛型型別可以存取的無參數的函式。 如果您透過一或多個介面來限制型別參數，這就很有用。 實介面的型別不一定會公開一個函式，而視函式的存取層級而定，泛型型別中的程式碼可能無法存取它。

  - `Class` 關鍵字或 `Structure` 關鍵字。 `Class` 關鍵字會限制泛型型別參數，要求傳遞給它的任何型別引數都是參考型別，例如字串、陣列或委派，或是從類別建立的物件。 `Structure` 關鍵字會限制泛型型別參數，要求傳遞至它的任何型別引數都是實值型別，例如結構、列舉或基本資料型別。 您不能在相同的 `constraintlist`中同時包含 `Class` 和 `Structure`。

  提供的類型必須滿足您在 `constraintlist`中包含的每個需求。

  每個型別參數的條件約束與其他型別參數上的條件約束無關。

## <a name="behavior"></a>行為

- **編譯時間替代。** 當您從泛型程式設計專案建立結構化型別時，您會為每個型別參數提供一個已定義的型別。 Visual Basic 編譯器會針對泛型專案中每個出現的 `typename`，替代提供的型別。

- **沒有條件約束。** 如果您未在類型參數上指定任何條件約束，則您的程式碼會限制為該類型參數的[Object 資料類型](../../../visual-basic/language-reference/data-types/object-data-type.md)所支援的作業和成員。

## <a name="example"></a>範例

下列範例顯示泛型字典類別的基本架構定義，包括將新專案加入字典的基本架構函數。

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a>範例

因為 `dictionary` 是泛型的，所以使用它的程式碼可以從它建立各種不同的物件，而每一個都有相同的功能，但作用於不同的資料類型。 下列範例顯示的程式程式碼，會建立具有 `String` 專案和 `Integer` 索引鍵的 `dictionary` 物件。

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a>範例

下列範例會顯示上述範例所產生的對等基本架構定義。

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a>請參閱

- [Of](../../../visual-basic/language-reference/statements/of-clause.md)
- [New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)
- [Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [共變數和反變數](../../programming-guide/concepts/covariance-contravariance/index.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
