---
title: For Each...Next 陳述式
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
ms.openlocfilehash: 0feb938121a97b06509b472652e6a753841ab2b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404650"
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
|`element`|語句中的必要項 `For Each` 。 在語句中為選擇性 `Next` 。 變數。 用來逐一查看集合的元素。|
|`datatype`|如果 [`Option Infer`](option-infer-statement.md) 為 on （預設值）或已經宣告，則為選擇性 `element` ; 如果 `Option Infer` 已關閉，而且尚未宣告，則為必要 `element` 。 `element` 的資料類型。|
|`group`|必要。 類型為的變數，其為集合類型或物件。 表示 `statements` 要重複的集合。|
|`statements`|選擇性。 `For Each` `Next` 在和中的每個專案上執行的一或多個語句 `group` 。|
|`Continue For`|選擇性。 將控制權轉移到迴圈的開頭 `For Each` 。|
|`Exit For`|選擇性。 將控制權轉移給 `For Each` 迴圈。|
|`Next`|必要。 終止迴圈的定義 `For Each` 。|

## <a name="simple-example"></a>簡單範例

`For Each` `Next` 當您想要針對集合或陣列的每個元素重複一組語句時，請使用 ... 迴圈。

> [!TIP]
> [適用于 .。。](for-next-statement.md)當您可以將迴圈的每個反復專案與控制項變數產生關聯，並判斷該變數的初始值和最後一個值時，下一個語句就很好用。 不過，當您處理集合時，初始和最終值的概念並沒有意義，而且您不一定知道集合具有多少元素。 在這種情況下，「 `For Each` ...」 `Next` 迴圈通常是較佳的選擇。

在下列範例中， `For Each` .。。`Next` 語句會逐一查看清單集合的所有元素。

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

如需更多範例，請參閱[集合](../../../standard/collections/index.md)和[陣列](../../programming-guide/language-features/arrays/index.md)。

## <a name="nested-loops"></a>巢狀迴圈

您可以藉 `For Each` 由在另一個迴圈中放入迴圈來加以嵌套。

下列範例示範 nested `For Each` .。。`Next` 構造.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

當您嵌套迴圈時，每個迴圈都必須有唯一的 `element` 變數。

您也可以在彼此之間嵌套不同類型的控制結構。 如需詳細資訊，請參閱[嵌套控制項結構](../../programming-guide/language-features/control-flow/nested-control-structures.md)。

## <a name="exit-for-and-continue-for"></a>結束並繼續進行

[Exit For](exit-statement.md)語句會導致執行 `For` 結束 .。。`Next` 迴圈，並將控制權轉移至語句後面的語句 `Next` 。

`Continue For`語句會立即將控制權轉移到迴圈的下一個反復專案。 如需詳細資訊，請參閱[Continue 語句](continue-statement.md)。

下列範例顯示如何使用 `Continue For` 和 `Exit For` 語句。

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

您可以將任意數目的 `Exit For` 語句放在 `For Each` 迴圈中。 在嵌套迴圈中使用時 `For Each` ， `Exit For` 會導致執行結束最內層的迴圈，並將控制權轉移至下一個較高層級的嵌套。

`Exit For`通常是在評估某個條件之後使用，例如，在 `If` ... `Then`...`Else`表示. 在下列情況下，您可能會想要使用 `Exit For` ：

- 繼續進行反覆運算是不必要或不可能的。 這可能是由錯誤值或終止要求所造成。

- 在中 `Try` `Catch` 攔截到例外狀況 .。。...`Finally`.您可以 `Exit For` 在區塊結尾使用 `Finally` 。

- 有一個無止盡的迴圈，這是一種迴圈，可能會執行很長或甚至無限次的次數。 如果您偵測到這種情況，您可以使用 `Exit For` 來將迴圈轉義。 如需詳細資訊，請參閱[Do .。。Loop 語句](do-loop-statement.md)。

## <a name="iterators"></a>迭代器

您可以使用*反覆運算器*，在集合上執行自訂反復專案。 Iterator 可以是函數或 `Get` 存取子。 它會使用 `Yield` 語句，一次傳回一個集合的每個專案。

您可以使用語句來呼叫反覆運算器 `For Each...Next` 。 `For Each` 迴圈的每個反覆項目都會呼叫迭代器。 當 `Yield` 反覆運算器中到達語句時， `Yield` 會傳回語句中的運算式，並保留程式碼中的目前位置。 下一次呼叫迭代器時，便會從這個位置重新開始執行。

下列範例會使用 iterator 函數。 Iterator 函數的 `Yield` 語句位於[For .。。下一個](for-next-statement.md)迴圈。 在 `ListEvenNumbers` 方法中，語句主體的每個反復專案都會建立對 iterator 函式的 `For Each` 呼叫，該函數會繼續進行下一個 `Yield` 語句。

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

如需詳細資訊，請參閱[反覆運算](../../programming-guide/concepts/iterators.md)器、 [Yield 語句](yield-statement.md)和[Iterator](../modifiers/iterator.md)。

## <a name="technical-implementation"></a>技術實作

當 `For Each` .。。`Next` 語句會執行，Visual Basic 在迴圈開始之前，只會評估集合一次。 如果您的語句區塊變更 `element` 或 `group` ，這些變更不會影響迴圈的反復專案。

當集合中的所有專案都連續指派給時 `element` ，迴圈就會 `For Each` 停止，並將控制權傳遞給語句後面的語句 `Next` 。

如果[Option 推斷](option-infer-statement.md)為 on （其預設設定），則 Visual Basic 編譯器可以推斷的資料類型 `element` 。 如果它已關閉，而且 `element` 尚未在迴圈外宣告，您必須在語句中宣告它 `For Each` 。 若要明確宣告的資料類型 `element` ，請使用 `As` 子句。 除非元素的資料類型是在 `For Each` ... 結構外定義，否則 `Next` 其範圍就是迴圈的主體。 請注意，您無法在 `element` 迴圈的外部和內部宣告。

您可以選擇性地 `element` 在語句中指定 `Next` 。 這可以改善程式的可讀性，特別是當您有嵌套的 `For Each` 迴圈時。 您必須指定與對應語句中出現的相同變數 `For Each` 。

您可能想要避免在迴圈內變更的值 `element` 。 這麼做可能會讓您更難以讀取和偵錯工具代碼。 變更的值 `group` 不會影響集合或其元素，這些專案是在第一次進入迴圈時決定的。

當您要嵌套迴圈時，如果在 `Next` 內部層級的之前遇到外部嵌套層級的語句 `Next` ，編譯器會發出錯誤信號。 不過，只有當您 `element` 在每個語句中指定時，編譯器才會偵測到這個重迭的錯誤 `Next` 。

如果您的程式碼相依于依特定順序來進行集合，則 `For Each` `Next` 除非您知道集合所公開之列舉值物件的特性，否則，... 迴圈不是最佳選擇。 「遍歷」的順序不是由 Visual Basic，而是由 <xref:System.Collections.IEnumerator.MoveNext%2A> 列舉值物件的方法決定。 因此，您可能無法預測集合的哪一個專案是要在中傳回的第一個元素 `element` ，或是在指定的專案之後要傳回的下一個專案。 您可以使用不同的迴圈結構（例如 `For` ... `Next` 或 `Do` ...）來達到更可靠的 `Loop` 結果。

執行時間必須能夠將中的元素轉換 `group` 成 `element` 。 [ `Option Strict` ] 語句控制是否允許擴展和縮小轉換（ `Option Strict` 已關閉、其預設值），或只允許擴輾轉換（ `Option Strict` on）。 如需詳細資訊，請參閱[縮小轉換](#narrowing-conversions)。

的資料類型 `group` 必須是參考類型，或可列舉的陣列。 最常見的意思 `group` 是指的物件會執行命名空間的 <xref:System.Collections.IEnumerable> 介面 `System.Collections` 或 <xref:System.Collections.Generic.IEnumerable%601> `System.Collections.Generic` 命名空間的介面。 `System.Collections.IEnumerable`定義 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法，其會傳回集合的列舉值物件。 列舉值物件會執行 `System.Collections.IEnumerator` `System.Collections` 命名空間的介面，並公開 <xref:System.Collections.IEnumerator.Current%2A> 屬性和 <xref:System.Collections.IEnumerator.Reset%2A> 和 <xref:System.Collections.IEnumerator.MoveNext%2A> 方法。 Visual Basic 會使用這些來遍歷集合。

### <a name="narrowing-conversions"></a>縮小轉換

當 `Option Strict` 設定為時 `On` ，縮小轉換通常會造成編譯器錯誤。 不過，在語句中， `For Each` 從中的專案轉換 `group` 成 `element` 會在執行時間進行評估和執行，而縮小轉換所造成的編譯器錯誤則會隱藏起來。

在下列範例中，當為 on 時，將指派為的 `m` 初始值 `n` 不會編譯，因為將 `Option Strict` 轉換 `Long` 成 `Integer` 是縮小轉換。 不過，在語句中， `For Each` 即使指派 `number` 必須從轉換成，也不會報告編譯器錯誤 `Long` `Integer` 。 在 `For Each` 包含大量數位的語句中，當套用至大量時，就會發生執行階段錯誤 <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> 。

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>IEnumerator 呼叫

當執行 `For Each` ... `Next` 迴圈開始時，Visual Basic 會驗證是否 `group` 參考有效的集合物件。 如果沒有，則會擲回例外狀況。 否則，它會呼叫 <xref:System.Collections.IEnumerator.MoveNext%2A> 列舉值物件的方法和 <xref:System.Collections.IEnumerator.Current%2A> 屬性，以傳回第一個元素。 如果 `MoveNext` 指出沒有下一個專案，也就是說，如果集合是空的，迴圈就會 `For Each` 停止，並將控制權傳遞給語句後面的語句 `Next` 。 否則，Visual Basic 會將設定 `element` 為第一個元素，並執行語句區塊。

每次 Visual Basic 遇到 `Next` 語句時，它會回到 `For Each` 語句。 同樣地，它會呼叫 `MoveNext` 並傳回 `Current` 下一個元素，然後再根據結果執行區塊或停止迴圈。 此程式會繼續 `MoveNext` 進行，直到指出沒有下一個元素或 `Exit For` 遇到語句為止。

**修改集合。** 通常傳回的列舉值物件 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 不會讓您藉由新增、刪除、取代或重新排列任何元素來變更集合。 如果您在初始化 ... 迴圈之後變更集合 `For Each` `Next` ，列舉值物件將會變成無效，而下一次存取專案的嘗試會造成 <xref:System.InvalidOperationException> 例外狀況。

不過，這項修改封鎖不是由 Visual Basic 所決定，而是由介面的實作為來執行 <xref:System.Collections.IEnumerable> 。 您可以 `IEnumerable` 使用允許在反復專案期間進行修改的方式來執行。 如果您考慮進行這類動態修改，請確定您瞭解所 `IEnumerable` 使用之集合上的執行特性。

**修改集合元素。** <xref:System.Collections.IEnumerator.Current%2A>列舉值物件的屬性是[ReadOnly](../modifiers/readonly.md)，它會傳回每個集合元素的本機複本。 這表示您無法在 `For Each` ... 迴圈中修改元素本身。 `Next` 您所做的任何修改只會影響的本機複本 `Current` ，而且不會反映回基礎集合中。 不過，如果專案是參考型別，您可以修改它所指向之實例的成員。 下列範例會修改 `BackColor` 每個元素的 `thisControl` 成員。 但是，您無法自行修改 `thisControl` 。

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

上一個範例可以修改 `BackColor` 每個專案的成員 `thisControl` ，但它無法 `thisControl` 自行修改。

**遍歷陣列。** 因為類別會實 <xref:System.Array> 作為 <xref:System.Collections.IEnumerable> 介面，所以所有陣列都會公開 <xref:System.Array.GetEnumerator%2A> 方法。 這表示您可以使用 `For Each` ... 迴圈逐一查看陣列。 `Next` 不過，您只能讀取陣列元素。 您無法加以變更。

## <a name="example"></a>範例

下列範例會列出 C：\ 中的所有資料夾目錄，方法是使用 <xref:System.IO.DirectoryInfo> 類別。

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>範例

下列範例說明排序集合的程序。 此範例 `Car` 會排序儲存在中之類別的實例 <xref:System.Collections.Generic.List%601> 。 `Car` 類別實作 <xref:System.IComparable%601> 介面，而這個介面要求實作 <xref:System.IComparable%601.CompareTo%2A> 方法。

對方法的每個呼叫 <xref:System.IComparable%601.CompareTo%2A> 都會進行單一比較，用於排序。 當目前物件和另一個物件比較時，在 `CompareTo` 方法中的使用者撰寫程式碼會傳回值。 如果目前物件比另一個物件小則傳回的值小於零，如果目前物件比另一個物件大則傳回的值大於零，如果它們相等則傳回零。 這可讓您以程式碼定義大於、小於、等於的準則。

在 `ListCars` 方法中，`cars.Sort()` 陳述式會排序清單。 對 <xref:System.Collections.Generic.List%601> 之 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的這個呼叫，會導致 `CompareTo` 方法對 `List` 的 `Car` 物件自動呼叫。

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>另請參閱

- [集合](../../../standard/collections/index.md)
- [For...Next 陳述式](for-next-statement.md)
- [迴圈結構](../../programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While 陳述式](while-end-while-statement.md)
- [Do...Loop 陳述式](do-loop-statement.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [物件初始設定式：具名和匿名型別](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [集合初始化運算式](../../programming-guide/language-features/collection-initializers/index.md)
- [陣列](../../programming-guide/language-features/arrays/index.md)
