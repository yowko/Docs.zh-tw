---
title: Sub 陳述式 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 7dc0ea1f1b30f5ffb0db8917538adf440c5ef891
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583193"
---
# <a name="sub-statement-visual-basic"></a>Sub 陳述式 (Visual Basic)

宣告定義 `Sub` 程式的名稱、參數和程式碼。

## <a name="syntax"></a>語法

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a>組件

- `attributelist`

  選擇項。 請參閱[屬性清單](attribute-list.md)。

- `Partial`

  選擇項。 表示部分方法的定義。 請參閱[部分方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)。

- `accessmodifier`

  選擇項。 可以是下列其中一項：

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

- `proceduremodifiers`

  選擇項。 可以是下列其中一項：

  - [多載](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [New](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  選擇項。 請參閱[共用](../modifiers/shared.md)。

- `Shadows`

  選擇項。 請參閱[Shadows](../modifiers/shadows.md)。

- `Async`

  選擇項。 請參閱[Async](../modifiers/async.md)。

- `name`

  必要項。 程式的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。 若要建立類別的函式程式，請將 `Sub` 程式的名稱設定為 `New` 關鍵字。 如需詳細資訊，請參閱[物件存留期：物件的建立和終結方式](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。

- `typeparamlist`

  選擇項。 泛型程式的類型參數清單。 請參閱[類型清單](type-list.md)。

- `parameterlist`

  選擇項。 本機變數名稱的清單，代表此程式的參數。 請參閱[參數清單](parameter-list.md)。

- `Implements`

  選擇項。 指出此程式會執行一或多個 `Sub` 程式，其中每一個都是在由這個程式的包含類別或結構所實的介面中定義。 請參閱[Implements 語句](implements-statement.md)。

- `implementslist`

  如果使用 `Implements`，則為必要項。 實作之 `Sub` 程序的清單。

  `implementedprocedure [ , implementedprocedure ... ]`

  每個 `implementedprocedure` 都具有下列語法和組件：

  `interface.definedname`

  |組件|描述|
  |---|---|
  |`interface`|必要項。 此程式的包含類別或結構所實作為介面的名稱。|
  |`definedname`|必要項。 名稱，據以在 `interface` 中定義程序。|

- `Handles`

  選擇項。 指出此程式可以處理一或多個特定事件。 請參閱[控制碼](handles-clause.md)。

- `eventlist`

  如果使用 `Handles`，則為必要項。 此程式處理的事件清單。

  `eventspecifier [ , eventspecifier ... ]`

  每個 `eventspecifier` 都具有下列語法和組件：

  `eventvariable.event`

  |組件|描述|
  |---|---|
  |`eventvariable`|必要項。 以引發事件之類別或結構的資料類型宣告的物件變數。|
  |`event`|必要項。 這個程式處理的事件名稱。|

- `statements`

  選擇項。 要在此程式內執行的語句區塊。

- `End Sub`

  終止這個程式的定義。

## <a name="remarks"></a>備註

所有可執行檔程式碼都必須在程式內。 當您不想要將值傳回給呼叫程式碼時，請使用 `Sub` 程式。 當您想要傳回值時，請使用 `Function` 程式。

## <a name="defining-a-sub-procedure"></a>定義 Sub 程式

您只能在模組層級定義 `Sub` 程式。 Sub 程式的宣告內容必須是類別、結構、模組或介面，而且不能是原始程式檔、命名空間、程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。

`Sub` 程式預設為公開存取。 您可以使用存取修飾詞來調整其存取層級。

如果程式使用 `Implements` 關鍵字，則包含的類別或結構必須具有緊接在其 `Class` 或 `Structure` 語句後面的 `Implements` 語句。 @No__t_0 語句必須包含 `implementslist` 中指定的每個介面。 不過，介面用來定義 `Sub` （在 `definedname` 中）的名稱不一定要符合此程式的名稱（在 `name` 中）。

## <a name="returning-from-a-sub-procedure"></a>從 Sub 程式傳回

當 `Sub` 程式傳回呼叫程式碼時，會在呼叫它的語句後面繼續執行語句。

下列範例顯示從 `Sub` 程式傳回的。

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

@No__t_0 和 `Return` 語句會導致立即離開 `Sub` 程式。 任何數目的 `Exit Sub` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合 `Exit Sub` 和 `Return` 語句。

## <a name="calling-a-sub-procedure"></a>呼叫 Sub 程式

您可以使用語句中的程式名稱來呼叫 `Sub` 程式，然後在該名稱後面加上括弧中的引數清單。 只有在未提供任何引數時，才可以省略括弧。 不過，如果您一律包含括弧，則程式碼會更容易閱讀。

@No__t_0 程式和 `Function` 程式都可以有參數，並執行一連串的語句。 不過，`Function` 程式會傳回值，而 `Sub` 程式則不會。 因此，您不能在運算式中使用 `Sub` 程式。

當您呼叫 `Sub` 程式時，可以使用 `Call` 關鍵字，但不建議在大部分的情況下使用該關鍵字。 如需詳細資訊，請參閱[Call 語句](call-statement.md)。

Visual Basic 有時會重新排列算術運算式，以提高內部效率。 基於這個理由，如果您的引數清單包含呼叫其他程式的運算式，您就不應該假設這些運算式會以特定順序呼叫。

## <a name="async-sub-procedures"></a>非同步 Sub 程式

藉由使用非同步功能，您可以叫用非同步函式，而不需使用明確回呼，或手動將程式碼分割成多個函數或 lambda 運算式。

如果您使用[Async](../modifiers/async.md)修飾詞來標記程式，您可以在程式中使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)運算子。 當控制項到達 `Async` 程式中的 `Await` 運算式時，控制項會回到呼叫端，而程式中的進度會暫停，直到等候的工作完成為止。 當工作完成時，可以在程式中繼續執行。

> [!NOTE]
> 當遇到第一個尚未完成的等候物件或到達 `Async` 程式的結尾（以先發生者為准）時，`Async` 程式會傳回呼叫端。

您也可以使用 `Async` 修飾詞來標記[函數語句](function-statement.md)。 @No__t_0 函式的傳回型別可以是 <xref:System.Threading.Tasks.Task%601> 或 <xref:System.Threading.Tasks.Task>。 本主題稍後的範例會顯示具有 <xref:System.Threading.Tasks.Task%601> 傳回類型的 `Async` 函式。

`Async` `Sub` 程式主要用於事件處理常式，因此無法傳回值。 無法等候 `Async` `Sub` 程式，`Async` `Sub` 程式的呼叫端無法攔截 `Sub` 程式擲回的例外狀況。

@No__t_0 程式無法宣告任何[ByRef](../modifiers/byref.md)參數。

如需 `Async` 程式的詳細資訊，請參閱[使用 async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)和[非同步傳回類型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。

## <a name="example"></a>範例

下列範例會使用 `Sub` 語句來定義構成 `Sub` 程式主體的名稱、參數和代碼。

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>範例

在下列範例中，`DelayAsync` 是具有 <xref:System.Threading.Tasks.Task%601> 傳回類型的 `Async` `Function`。 `DelayAsync` 具有傳回整數的 `Return` 陳述式。 因此，`DelayAsync` 的函式宣告必須具有 `Task(Of Integer)` 的傳回類型。 因為傳回型別是 `Task(Of Integer)`，所以 `DoSomethingAsync` 中 `Await` 運算式的評估會產生整數，如下列語句所示： `Dim result As Integer = Await delayTask`。

@No__t_0 的程式是 `Async Sub` 程式的範例。 因為 `DoSomethingAsync` 是 `Async` 函式，所以必須等候 `DoSomethingAsync` 呼叫的工作，如下列語句所示： `Await DoSomethingAsync()`。 @No__t_0 `Sub` 程式必須使用 `Async` 修飾詞加以定義，因為它有 `Await` 運算式。

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>請參閱

- [Implements 陳述式](implements-statement.md)
- [Function 陳述式](function-statement.md)
- [參數清單](parameter-list.md)
- [Dim 陳述式](dim-statement.md)
- [Call 陳述式](call-statement.md)
- [Of](of-clause.md)
- [參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [程序的疑難排解](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [部分方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
