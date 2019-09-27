---
title: For Each...Next 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: f56e5defa2328011d222bfca05334b610e805055
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332780"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next 陳述式 (Visual Basic)

針對集合中的每個元素重複一組語句。

## <a name="syntax"></a>語法

```vb
For Each element [ As datatype ] In group
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ element ]
```

## <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`element`|在 `For Each` 語句中為必要項。 在 `Next` 語句中為選擇性。 變. 用來逐一查看集合的元素。|
|`datatype`|如果[`Option Infer`](option-infer-statement.md)是 on （預設值）或 `element` 已宣告，則為選擇性;如果 `Option Infer` 已關閉，而且 `element` 尚未宣告，則為必要。 `element`的資料型別。|
|`group`|必要項。 類型為的變數，其為集合類型或物件。 表示要重複 @no__t 0 的集合。|
|`statements`|選擇性。 在 `group` 中的每個專案上執行的 `For Each` 和 `Next` 之間的一個或多個語句。|
|`Continue For`|選擇性。 將控制權轉移至 `For Each` 迴圈的開頭。|
|`Exit For`|選擇性。 將控制權從 `For Each` 迴圈轉移出去。|
|`Next`|必要項。 終止 `For Each` 迴圈的定義。|

## <a name="simple-example"></a>簡單範例

當您想要針對集合或陣列的每個元素重複一組語句時，請使用 `For Each` ... @no__t 1 迴圈。

> [!TIP]
> [適用于 。](../../../visual-basic/language-reference/statements/for-next-statement.md)當您可以將迴圈的每個反復專案與控制項變數產生關聯，並判斷該變數的初始值和最後一個值時，下一個語句就很好用。 不過，當您處理集合時，初始和最終值的概念並沒有意義，而且您不一定知道集合具有多少元素。 在這種情況下，`For Each` ... @no__t 1 迴圈通常是較佳的選擇。

在下列範例中，`For Each` ... `Next` 語句會逐一查看清單集合的所有元素。

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

如需更多範例，請參閱[集合](../../../standard/collections/index.md)和[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。

## <a name="nested-loops"></a>嵌套迴圈

您可以藉由將一個迴圈放在另一個迴圈中，來將 `For Each` 個迴圈。

下列範例示範 nested `For Each` ... `Next` 構造.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

當您嵌套迴圈時，每個迴圈都必須有唯一的 @no__t 0 變數。

您也可以在彼此之間嵌套不同類型的控制結構。 如需詳細資訊，請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。

## <a name="exit-for-and-continue-for"></a>結束並繼續進行

[Exit For](../../../visual-basic/language-reference/statements/exit-statement.md)語句會導致執行結束 `For` ... `Next` 迴圈，並將控制權轉移至 `Next` 語句後面的語句。

@No__t 0 語句會立即將控制權轉移到迴圈的下一個反復專案。 如需詳細資訊，請參閱[Continue 語句](../../../visual-basic/language-reference/statements/continue-statement.md)。

下列範例顯示如何使用 `Continue For` 和 `Exit For` 語句。

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

您可以將任意數目的 `Exit For` 語句放在 @no__t 1 迴圈中。 在 nested `For Each` 迴圈中使用時，`Exit For` 會使執行結束最內層的迴圈，並將控制權轉移至下一個較高層級的嵌套。

`Exit For` 通常會在評估某些條件之後使用，例如，在 `If` ... `Then` ... `Else` 結構中。 在下列情況中，您可能會想要使用 `Exit For`：

- 繼續進行反覆運算是不必要或不可能的。 這可能是由錯誤值或終止要求所造成。

- @No__t-0 ... `Catch` ... `Finally` 中攔截到例外狀況。您可以使用 `Finally` 區塊結尾的 `Exit For`。

- 有一個無止盡的迴圈，這是一種迴圈，可能會執行很長或甚至無限次的次數。 如果您偵測到這種情況，您可以使用 `Exit For` 來取消迴圈。 如需詳細資訊，請參閱[Do 。Loop 語句](../../../visual-basic/language-reference/statements/do-loop-statement.md)。

## <a name="iterators"></a>迭代器

您可以使用*反覆運算器*，在集合上執行自訂反復專案。 Iterator 可以是函數或 @no__t 0 的存取子。 它會使用 `Yield` 語句，一次傳回一個集合的每個專案。

您可以使用 `For Each...Next` 語句來呼叫反覆運算器。 `For Each` 迴圈的每個反覆項目都會呼叫迭代器。 當反覆運算器中到達 @no__t 0 的語句時，會傳回 `Yield` 語句中的運算式，並保留程式碼中的目前位置。 下一次呼叫迭代器時，便會從這個位置重新開始執行。

下列範例會使用 iterator 函數。 Iterator 函數的 `Yield` 語句位於[For 。下一個](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。 在 `ListEvenNumbers` 方法中，@no__t 1 語句主體的每個反復專案都會建立對 iterator 函式的呼叫，該函數會繼續進行下一個 `Yield` 語句。

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

如需詳細資訊，請參閱[反覆運算](../../programming-guide/concepts/iterators.md)器、 [Yield 語句](../../../visual-basic/language-reference/statements/yield-statement.md)和[Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)。

## <a name="technical-implementation"></a>技術實作

當 `For Each` ... `Next` 語句會執行，Visual Basic 在迴圈開始之前，只會評估集合一次。 如果您的語句區塊 `element` 或 `group` 變更，這些變更不會影響迴圈的反復專案。

當集合中的所有元素連續指派給 `element` 時，@no__t 1 迴圈就會停止，並將控制權傳遞至 `Next` 語句之後的語句。

如果[Option 推斷](option-infer-statement.md)為 on （其預設設定），則 Visual Basic 編譯器可以推斷 `element` 的資料類型。 如果已關閉，而且 `element` 尚未在迴圈外宣告，您就必須在 `For Each` 語句中宣告它。 若要明確宣告 `element` 的資料類型，請使用 `As` 子句。 除非元素的資料類型是在 `For Each` ... `Next` 結構之外定義，否則其範圍就是迴圈的主體。 請注意，您無法在迴圈的外部和內部宣告 `element`。

您可以選擇性地在 `Next` 語句中指定 `element`。 這可以改善程式的可讀性，特別是當您有嵌套的 `For Each` 迴圈時。 您必須指定與對應的 `For Each` 語句中出現的相同變數。

您可能想要避免在迴圈內變更 `element` 的值。 這麼做可能會讓您更難以讀取和偵錯工具代碼。 變更 `group` 的值並不會影響集合或其元素，這是在第一次進入迴圈時決定的。

當您要建立迴圈時，如果內部層級的 `Next` 之前遇到外部嵌套層級的 `Next` 語句，則編譯器會發出錯誤信號。 不過，只有當您在每個 `Next` 語句中指定 `element` 時，編譯器才會偵測到這個重迭的錯誤。

如果您的程式碼相依于依特定順序來進行集合，除非您知道集合所公開之列舉值物件的特性，否則 `For Each` ... `Next` 迴圈不是最佳選擇。 定序的順序不是由 Visual Basic，而是由列舉值物件的 <xref:System.Collections.IEnumerator.MoveNext%2A> 方法所決定。 因此，您可能無法預測集合的哪個元素是第一個要傳回的專案 `element`，或在指定的專案之後要傳回的下一個專案。 您可以使用不同的迴圈結構（例如 `For` ... `Next` 或 `Do` ... `Loop`）來達到更可靠的結果。

執行時間必須能夠將 `group` 中的元素轉換成 `element`。 [@No__t-0] 語句控制是否允許擴展和縮小轉換（`Option Strict` 已關閉、其預設值），或只允許擴輾轉換（`Option Strict` 是 on）。 如需詳細資訊，請參閱[縮小轉換](#narrowing-conversions)。

@No__t-0 的資料類型必須是參考類型，或可列舉的陣列。 最常見的意思是，`group` 指的是一個物件，它會執行 `System.Collections` 命名空間的 @no__t 1 介面，或 `System.Collections.Generic` 命名空間的 @no__t 3 介面。 `System.Collections.IEnumerable` 會定義 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法，這會傳回集合的列舉值物件。 列舉值物件會執行 @no__t 1 命名空間的 @no__t 0 介面，並公開 <xref:System.Collections.IEnumerator.Current%2A> 屬性和 <xref:System.Collections.IEnumerator.Reset%2A> 和 @no__t 4 方法。 Visual Basic 會使用這些來遍歷集合。

### <a name="narrowing-conversions"></a>縮小轉換

當 `Option Strict` 設定為 `On` 時，縮小轉換通常會造成編譯器錯誤。 不過，在 @no__t 0 的語句中，從 `group` 的專案轉換為 `element` 會在執行時間進行評估和執行，而且會隱藏縮小轉換所造成的編譯器錯誤。

在下列範例中，當 `Option Strict` 為 on 時，`m` 的指派 `n` 的初始值不會進行編譯，因為 `Long` 轉換成 `Integer` 是縮小轉換。 不過，在 `For Each` 語句中，不會報告任何編譯器錯誤，即使指派給 `number` 也需要從 `Long` 到 `Integer` 的相同轉換。 在包含大量數位的 `For Each` 語句中，當 <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> 套用至大數位時，就會發生執行階段錯誤。

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>IEnumerator 呼叫

當 `For Each` ... `Next` 迴圈開始執行時，Visual Basic 會確認 `group` 是指有效的集合物件。 如果沒有，則會擲回例外狀況。 否則，它會呼叫 <xref:System.Collections.IEnumerator.MoveNext%2A> 方法和列舉值物件的 @no__t 1 屬性，以傳回第一個元素。 如果 `MoveNext` 指出沒有下一個專案，也就是，如果集合是空的，則 @no__t 1 迴圈會停止，並將控制權傳遞至 `Next` 語句之後的語句。 否則，Visual Basic 會將 `element` 設定為第一個元素，並執行語句區塊。

每次 Visual Basic 遇到 @no__t 0 的語句時，它會回到 `For Each` 語句。 同樣地，它會呼叫 `MoveNext`，並 `Current` 傳回下一個專案，然後再執行區塊或停止迴圈，視結果而定。 此程式會繼續進行，直到 `MoveNext` 指出沒有下一個元素，或遇到 @no__t 1 的語句為止。

**修改集合。** @No__t-0 所傳回的列舉值物件，通常不會讓您藉由新增、刪除、取代或重新排列任何元素來變更集合。 如果您在初始化 `For Each` ... `Next` 迴圈之後變更集合，則列舉值物件會變成無效，而下次嘗試存取專案會導致 @no__t 2 例外狀況。

不過，這項修改封鎖不是由 Visual Basic 所決定，而是由 @no__t 0 介面的實作為。 您可以使用允許在反復專案期間進行修改的方式來執行 `IEnumerable`。 如果您考慮進行這類動態修改，請確定您瞭解所使用之集合上的 `IEnumerable` 實特性。

**修改集合元素。** 列舉值物件的 <xref:System.Collections.IEnumerator.Current%2A> 屬性是[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)，它會傳回每個集合元素的本機複本。 這表示您無法在 `For Each` ... `Next` 迴圈中修改元素本身。 您所做的任何修改只會影響 `Current` 的本機複本，而且不會反映回基礎集合中。 不過，如果專案是參考型別，您可以修改它所指向之實例的成員。 下列範例會修改每個 `thisControl` 元素的 @no__t 0 成員。 但是，您無法修改 `thisControl` 本身。

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

上一個範例可以修改每個 `thisControl` 元素的 `BackColor` 成員，不過它無法修改 `thisControl` 本身。

**遍歷陣列。** 因為 @no__t 0 類別會執行 @no__t 1 介面，所以所有陣列都會公開 @no__t 2 方法。 這表示您可以使用 `For Each` ... `Next` 迴圈逐一查看陣列。 不過，您只能讀取陣列元素。 您無法加以變更。

## <a name="example"></a>範例

下列範例會列出 C：\ 中的所有資料夾目錄，方法是使用 <xref:System.IO.DirectoryInfo> 類別。

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>範例

下列範例說明排序集合的程序。 此範例會排序儲存在 <xref:System.Collections.Generic.List%601> 中 @no__t 0 類別的實例。 `Car` 類別實作 <xref:System.IComparable%601> 介面，而這個介面要求實作 <xref:System.IComparable%601.CompareTo%2A> 方法。

@No__t-0 方法的每個呼叫都會進行用於排序的單一比較。 當目前物件和另一個物件比較時，在 `CompareTo` 方法中的使用者撰寫程式碼會傳回值。 如果目前物件比另一個物件小則傳回的值小於零，如果目前物件比另一個物件大則傳回的值大於零，如果它們相等則傳回零。 這可讓您以程式碼定義大於、小於、等於的準則。

在 `ListCars` 方法中，`cars.Sort()` 陳述式會排序清單。 對 <xref:System.Collections.Generic.List%601> 之 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的這個呼叫，會導致 `CompareTo` 方法對 `List` 的 `Car` 物件自動呼叫。

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>另請參閱

- [集合](../../../standard/collections/index.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- @no__t 0Object 初始化運算式：名稱和匿名型別 @ no__t-0
- [集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
