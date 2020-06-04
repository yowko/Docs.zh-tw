---
title: Sub 陳述式
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
ms.openlocfilehash: e50b79c31c92ac116d6c82bcececba3340894d74
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404170"
---
# <a name="sub-statement-visual-basic"></a>Sub 陳述式 (Visual Basic)

宣告定義程式的名稱、參數和程式碼 `Sub` 。

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

  選擇性。 請參閱[屬性清單](attribute-list.md)。

- `Partial`

  選擇性。 表示部分方法的定義。 請參閱[部分方法](../../programming-guide/language-features/procedures/partial-methods.md)。

- `accessmodifier`

  選擇性。 可以是下列其中一項：

  - [公開](../modifiers/public.md)

  - [免受](../modifiers/protected.md)

  - [給](../modifiers/friend.md)

  - [私用](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [私用保護](../modifiers/private-protected.md)

  請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。

- `proceduremodifiers`

  選擇性。 可以是下列其中一項：

  - [多載](../modifiers/overloads.md)

  - [覆寫](../modifiers/overrides.md)

  - [Overrides](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [New](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  選擇性。 請參閱[共用](../modifiers/shared.md)。

- `Shadows`

  選擇性。 請參閱[Shadows](../modifiers/shadows.md)。

- `Async`

  選擇性。 請參閱[Async](../modifiers/async.md)。

- `name`

  必要。 程式的名稱。 請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。 若要建立類別的方法，請將程式的名稱設定 `Sub` 為 `New` 關鍵字。 如需詳細資訊，請參閱[物件存留期：物件的建立和終結方式](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。

- `typeparamlist`

  選擇性。 泛型程式的類型參數清單。 請參閱[類型清單](type-list.md)。

- `parameterlist`

  選擇性。 本機變數名稱的清單，代表此程式的參數。 請參閱[參數清單](parameter-list.md)。

- `Implements`

  選擇性。 指出此程式會執行一或多個 `Sub` 程式，其中每一個都是在介面中所定義的介面中，其包含類別或結構。 請參閱[Implements 語句](implements-statement.md)。

- `implementslist`

  如果使用 `Implements`，則為必要項。 實作之 `Sub` 程序的清單。

  `implementedprocedure [ , implementedprocedure ... ]`

  每個 `implementedprocedure` 都具有下列語法和組件：

  `interface.definedname`

  |部分|描述|
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

  |部分|描述|
  |---|---|
  |`eventvariable`|必要。 以引發事件之類別或結構的資料類型宣告的物件變數。|
  |`event`|必要。 這個程式處理的事件名稱。|

- `statements`

  選擇性。 要在此程式內執行的語句區塊。

- `End Sub`

  終止這個程式的定義。

## <a name="remarks"></a>備註

所有可執行檔程式碼都必須在程式內。 `Sub`當您不想要將值傳回給呼叫程式碼時，請使用程式。 `Function`當您想要傳回值時，請使用程式。

## <a name="defining-a-sub-procedure"></a>定義 Sub 程式

您 `Sub` 只能在模組層級定義程式。 Sub 程式的宣告內容必須是類別、結構、模組或介面，而且不能是原始程式檔、命名空間、程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。

`Sub`程式預設為公用存取。 您可以使用存取修飾詞來調整其存取層級。

如果程式使用 `Implements` 關鍵字，則包含的類別或結構必須有緊接在 `Implements` 其或語句後面的 `Class` 語句 `Structure` 。 `Implements`語句必須包含中所指定的每個介面 `implementslist` 。 不過，介面用來定義 `Sub` （在中）的名稱 `definedname` 不一定要符合此程式的名稱（在中為 `name` ）。

## <a name="returning-from-a-sub-procedure"></a>從 Sub 程式傳回

當程式 `Sub` 返回呼叫程式碼時，執行會在呼叫它的語句後面繼續進行語句。

下列範例顯示從程式傳回的 `Sub` 。

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

`Exit Sub`和 `Return` 語句會導致程式立即結束 `Sub` 。 任何數目的 `Exit Sub` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合使用 `Exit Sub` 和 `Return` 語句。

## <a name="calling-a-sub-procedure"></a>呼叫 Sub 程式

您可以 `Sub` 使用語句中的程式名稱，然後在該名稱後面加上括弧中的引數清單，來呼叫程式。 只有在未提供任何引數時，才可以省略括弧。 不過，如果您一律包含括弧，則程式碼會更容易閱讀。

程式 `Sub` 和程式 `Function` 可以有參數，並執行一系列的語句。 不過，程式 `Function` 會傳回值，而程式則 `Sub` 不會傳回。 因此，您不能 `Sub` 在運算式中使用程式。

`Call`當您呼叫程式時，可以使用關鍵字 `Sub` ，但不建議在大部分的情況下使用該關鍵字。 如需詳細資訊，請參閱[Call 語句](call-statement.md)。

Visual Basic 有時會重新排列算術運算式，以提高內部效率。 基於這個理由，如果您的引數清單包含呼叫其他程式的運算式，您就不應該假設這些運算式會以特定順序呼叫。

## <a name="async-sub-procedures"></a>非同步 Sub 程式

藉由使用非同步功能，您可以叫用非同步函式，而不需使用明確回呼，或手動將程式碼分割成多個函數或 lambda 運算式。

如果您使用[Async](../modifiers/async.md)修飾詞來標記程式，您可以在程式中使用[Await](../operators/await-operator.md)運算子。 當控制項到達程式 `Await` 中的運算式時 `Async` ，控制項會回到呼叫端，而程式中的進度會暫停，直到等候的工作完成為止。 當工作完成時，可以在程式中繼續執行。

> [!NOTE]
> `Async`當遇到第一個尚未完成的等候物件或到達程式的結尾（以先發生者為准）時，程式會傳回給呼叫端 `Async` 。

您也可以使用修飾詞來標記[函數語句](function-statement.md) `Async` 。 `Async`函數可以具有或的傳回類型 <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> 。 本主題稍後的範例 `Async` 會顯示具有傳回類型的函式 <xref:System.Threading.Tasks.Task%601> 。

`Async``Sub`程式主要用於事件處理常式，因此無法傳回值。 無法等候程式 `Async` `Sub` ，而且程式的呼叫端 `Async` `Sub` 無法攔截程式擲回的例外狀況 `Sub` 。

程式 `Async` 無法宣告任何[ByRef](../modifiers/byref.md)參數。

如需有關程式的詳細資訊 `Async` ，請參閱[使用 Async 和 Await 進行非同步程式設計](../../programming-guide/concepts/async/index.md)、[非同步程式中的控制流程](../../programming-guide/concepts/async/control-flow-in-async-programs.md)和[非同步傳回類型](../../programming-guide/concepts/async/async-return-types.md)。

## <a name="example"></a>範例

下列範例 `Sub` 會使用語句來定義構成程式主體的名稱、參數和代碼 `Sub` 。

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>範例

在下列範例中， `DelayAsync` 是 `Async` `Function` 具有傳回類型的 <xref:System.Threading.Tasks.Task%601> 。 `DelayAsync` 具有傳回整數的 `Return` 陳述式。 因此，的函式宣告 `DelayAsync` 必須有傳回型別 `Task(Of Integer)` 。 因為傳回型別是 `Task(Of Integer)` ，所以 `Await` 中的運算式評估會 `DoSomethingAsync` 產生整數，如下列語句所示： `Dim result As Integer = Await delayTask` 。

此程式 `startButton_Click` 是程式的範例 `Async Sub` 。 因為 `DoSomethingAsync` 是函式 `Async` ，所以的呼叫工作必須等候 `DoSomethingAsync` ，如下列語句所示： `Await DoSomethingAsync()` 。 程式 `startButton_Click` `Sub` 必須以修飾詞定義， `Async` 因為它有一個 `Await` 運算式。

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>另請參閱

- [Implements 陳述式](implements-statement.md)
- [Function 陳述式](function-statement.md)
- [參數清單](parameter-list.md)
- [Dim 陳述式](dim-statement.md)
- [Call 陳述式](call-statement.md)
- [的](of-clause.md)
- [參數陣列](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [作法：使用泛型類別](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [程序的疑難排解](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [部分方法](../../programming-guide/language-features/procedures/partial-methods.md)
