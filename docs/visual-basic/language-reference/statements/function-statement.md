---
title: Function 陳述式
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 8140c7e6267e66c69c20d413a11d04372400c581
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345925"
---
# <a name="function-statement-visual-basic"></a>Function 陳述式 (Visual Basic)

宣告定義 `Function` 程式的名稱、參數和程式碼。

## <a name="syntax"></a>語法

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a>組件

- `attributelist`

  選擇性。 請參閱[屬性清單](attribute-list.md)。

- `accessmodifier`

  選擇性。 可以是下列其中一項：

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

- `proceduremodifiers`

  選擇性。 可以是下列其中一項：

  - [多載](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [Overrides](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  選擇性。 請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。

- `Shadows`

  選擇性。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。

- `Async`

  選擇性。 請參閱[Async](../../../visual-basic/language-reference/modifiers/async.md)。

- `Iterator`

  選擇性。 請參閱[Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)。

- `name`

  必要。 程式的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。

- `typeparamlist`

  選擇性。 泛型程式的類型參數清單。 請參閱[類型清單](type-list.md)。

- `parameterlist`

  選擇性。 本機變數名稱的清單，代表此程式的參數。 請參閱[參數清單](parameter-list.md)。

- `returntype`

  如果 `Option Strict` `On`，則為必要。 這個程式所傳回之值的資料類型。

- `Implements`

  選擇性。 指出此程式會執行一或多個 `Function` 程式，其中每一個都是在由這個程式的包含類別或結構所實的介面中定義。 請參閱[Implements 語句](implements-statement.md)。

- `implementslist`

  如果使用 `Implements`，則為必要項。 實作之 `Function` 程序的清單。

  `implementedprocedure [ , implementedprocedure ... ]`

  每個 `implementedprocedure` 都具有下列語法和組件：

  `interface.definedname`

  |組件|描述|
  |---|---|
  |`interface`|必要。 此程式的包含類別或結構所實作為介面的名稱。|
  |`definedname`|必要。 名稱，據以在 `interface` 中定義程序。|

- `Handles`

  選擇性。 指出此程式可以處理一或多個特定事件。 請參閱[控制碼](handles-clause.md)。

- `eventlist`

  如果使用 `Handles`，則為必要項。 此程式處理的事件清單。

  `eventspecifier [ , eventspecifier ... ]`

  每個 `eventspecifier` 都具有下列語法和組件：

  `eventvariable.event`

  |組件|描述|
  |---|---|
  |`eventvariable`|必要。 以引發事件之類別或結構的資料類型宣告的物件變數。|
  |`event`|必要。 這個程式處理的事件名稱。|

- `statements`

  選擇性。 要在此程式中執行的語句區塊。

- `End Function`

  終止這個程式的定義。

## <a name="remarks"></a>備註

所有可執行檔程式碼都必須在程式內。 接著，每個程式都會在類別、結構或稱為包含類別、結構或模組的模組中宣告。

若要將值傳回給呼叫程式碼，請使用 `Function` 程式。否則，請使用 `Sub` 程式。

## <a name="defining-a-function"></a>定義函數

您只能在模組層級定義 `Function` 程式。 因此，函式的宣告內容必須是類別、結構、模組或介面，而且不能是原始程式檔、命名空間、程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。

`Function` 程式預設為公開存取。 您可以使用存取修飾詞來調整其存取層級。

`Function` 程式可以宣告此程式所傳回值的資料類型。 您可以指定任何資料類型或列舉的名稱、結構、類別或介面。 如果您未指定 `returntype` 參數，程式會傳回 `Object`。

如果此程式使用 `Implements` 關鍵字，則包含的類別或結構也必須有緊接在其 `Class` 或 `Structure` 語句後面的 `Implements` 語句。 `Implements` 語句必須包含 `implementslist`中指定的每個介面。 不過，介面用來定義 `Function` （在 `definedname`中）的名稱不需要符合此程式的名稱（在 `name`中）。

> [!NOTE]
> 您可以使用 lambda 運算式來定義內嵌函數運算式。 如需詳細資訊，請參閱[函數運算式](../../../visual-basic/language-reference/operators/function-expression.md)和[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。

## <a name="returning-from-a-function"></a>從函式傳回

當 `Function` 程式回到呼叫程式碼時，執行會繼續進行呼叫程式之語句後面的語句。

若要從函式傳回值，您可以將值指派給函數名稱，或將它包含在 `Return` 語句中。

`Return` 語句會同時指派傳回值並結束函式，如下列範例所示。

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

下列範例會將傳回值指派給函數名稱 `myFunction`，然後使用 `Exit Function` 語句傳回。

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

`Exit Function` 和 `Return` 語句會導致立即離開 `Function` 程式。 任何數目的 `Exit Function` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合 `Exit Function` 和 `Return` 語句。

如果您使用 `Exit Function`，但未指派值給 `name`，則程式會傳回 `returntype`中指定之資料類型的預設值。 如果未指定 `returntype`，程式會傳回 `Nothing`，這是 `Object`的預設值。

## <a name="calling-a-function"></a>呼叫函式

您可以在運算式中使用程式名稱，後面接著以括弧括住的引數清單，來呼叫 `Function` 程式。 只有在未提供任何引數時，才可以省略括弧。 不過，如果您一律包含括弧，則程式碼會更容易閱讀。

呼叫 `Function` 程式的方式，與呼叫任何程式庫函式（例如 `Sqrt`、`Cos`或 `ChrW`）相同。

您也可以使用 `Call` 關鍵字來呼叫函數。 在此情況下，會忽略傳回值。 在大部分的情況下，不建議使用 `Call` 關鍵字。 如需詳細資訊，請參閱[Call 語句](call-statement.md)。

Visual Basic 有時會重新排列算術運算式，以提高內部效率。 基於這個理由，當函數變更同一個運算式中的變數值時，您不應該在算術運算式中使用 `Function` 程式。

## <a name="async-functions"></a>Async 函式

*非同步*功能可讓您在不使用明確回呼的情況下叫用非同步函式，或在多個函式或 lambda 運算式中手動分割程式碼。

如果您使用[Async](../../../visual-basic/language-reference/modifiers/async.md)修飾詞來標示函式，您可以在函式中使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)運算子。 當控制項到達 `Async` 函式中的 `Await` 運算式時，控制項會回到呼叫端，而函式中的進度會暫停，直到等候的工作完成為止。 當工作完成時，可以在函式中繼續執行。

> [!NOTE]
> `Async` 程式會在遇到第一個尚未完成的等候物件，或到達 `Async` 程式結尾（以先發生者為准）時，將它傳回給呼叫端。

`Async` 函式的傳回型別可以是 <xref:System.Threading.Tasks.Task%601> 或 <xref:System.Threading.Tasks.Task>。 以下提供具有 <xref:System.Threading.Tasks.Task%601> 傳回類型之 `Async` 函式的範例。

`Async` 函數不能宣告任何[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)參數。

[Sub 語句](sub-statement.md)也可以使用 `Async` 修飾詞來標記。 這主要用於事件處理常式，無法傳回值。 無法等候 `Async` `Sub` 程式，而且 `Async` `Sub` 程式的呼叫端無法攔截 `Sub` 程式擲回的例外狀況。

如需 `Async` 函式的詳細資訊，請參閱[使用 async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)和[非同步傳回類型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。

## <a name="iterator-functions"></a>Iterator 函式

*Iterator*函式會對集合執行自訂反復專案，例如清單或陣列。 Iterator 函數會使用[Yield](yield-statement.md)語句，一次傳回一個元素。 當達到[Yield](yield-statement.md)語句時，會記住程式碼中的目前位置。 下次呼叫迭代器函式時，便會從這個位置重新開始執行。

您可以從用戶端程式代碼呼叫反覆運算器，方法是使用[For Each 。下一個](for-each-next-statement.md)語句。

Iterator 函數的傳回類型可以是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>或 <xref:System.Collections.Generic.IEnumerator%601>。

如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。

## <a name="example"></a>範例

下列範例會使用 `Function` 語句，宣告構成 `Function` 程式主體的名稱、參數和程式碼。 `ParamArray` 修飾詞可讓函式接受可變數目的引數。

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>範例

下列範例會叫用上述範例中所宣告的函式。

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>範例

在下列範例中，`DelayAsync` 是具有 <xref:System.Threading.Tasks.Task%601>傳回類型的 `Async` `Function`。 `DelayAsync` 具有傳回整數的 `Return` 陳述式。 因此，`DelayAsync` 的函式宣告必須具有 `Task(Of Integer)`的傳回類型。 因為傳回型別是 `Task(Of Integer)`，所以 `DoSomethingAsync` 中 `Await` 運算式的評估會產生整數。 這會在此語句中示範： `Dim result As Integer = Await delayTask`。

`startButton_Click` 的程式是 `Async Sub` 程式的範例。 因為 `DoSomethingAsync` 是 `Async` 函式，所以必須等候 `DoSomethingAsync` 呼叫的工作，如下列語句所示： `Await DoSomethingAsync()`。 `startButton_Click` `Sub` 程式必須使用 `Async` 修飾詞加以定義，因為它有 `Await` 運算式。

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>請參閱

- [Sub 陳述式](sub-statement.md)
- [函式程序](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [參數清單](parameter-list.md)
- [Dim 陳述式](dim-statement.md)
- [Call 陳述式](call-statement.md)
- [Of](of-clause.md)
- [參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [程序的疑難排解](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [函式運算式](../../../visual-basic/language-reference/operators/function-expression.md)
