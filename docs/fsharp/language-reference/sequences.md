---
title: 序列
description: '瞭解如何使用 F # 序列（當您有大量、依序排列的資料集合，但不一定會預期使用所有元素）。'
ms.date: 08/13/2020
ms.openlocfilehash: c84e0aebcc79a595c0ae3b9075648fb629bdd65c
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559033"
---
# <a name="sequences"></a>序列

「 *序列* 」（sequence）是一種元素的邏輯系列，全都是一種類型。 當您有大量的資料收集，但不一定會預期使用所有元素時，序列特別有用。 個別順序元素只會在必要時計算，因此在不使用所有元素的情況下，序列可以提供比清單更佳的效能。 順序是以類型表示 `seq<'T>` ，這是的別名 <xref:System.Collections.Generic.IEnumerable%601> 。 因此，任何實介面的 .NET 型別都 <xref:System.Collections.Generic.IEnumerable%601> 可以用來做為序列。 [Seq 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html)可支援涉及序列的操作。

## <a name="sequence-expressions"></a>序列運算式

*順序運算式*是評估為序列的運算式。 順序運算式可採用許多形式。 最簡單的形式會指定範圍。 例如， `seq { 1 .. 5 }` 建立包含五個元素的序列，包括端點1和5。 您也可以指定遞增 (，或在兩個雙句點之間遞減) 。 例如，下列程式碼會建立10的倍數序列。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

順序運算式是由產生序列值的 F # 運算式所組成。 您也可以透過程式設計的方式產生值：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

先前的範例使用 `->` 運算子，可讓您指定其值將成為序列一部分的運算式。 您只能使用 `->` （如果其後的程式碼的每個部分都傳回值）。

或者，您也可以指定 `do` 關鍵字，並選擇性 `yield` 的方法如下：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

下列程式碼會產生一份座標組清單，以及代表方格的陣列中的索引。 請注意，第一個 `for` 運算式需要 `do` 指定。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if`序列中使用的運算式是篩選準則。 例如，若要產生只有一個質數的序列，假設您有一個 `isprime` 類型的函式 `int -> bool` ，請依照下列方式來建立順序。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

如先前所述，在 `do` 這裡是必要的，因為沒有 `else` 與搭配使用的分支 `if` 。 如果您嘗試使用 `->` ，您會收到錯誤，指出並非所有分支都會傳回值。

## <a name="the-yield-keyword"></a>`yield!` 關鍵字

有時，您可能會想要在另一個序列中包含一系列的元素。 若要在另一個序列內包含序列，您必須使用 `yield!` 關鍵字：

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

另一種思考方式 `yield!` 是將內部序列壓平合併，然後將它包含在包含順序中。

`yield!`在運算式中使用時，所有其他的單一值都必須使用 `yield` 關鍵字：

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

上述範例會產生的值， `x` 以及每個的所有值 `1` `x` `x` 。

## <a name="examples"></a>範例

第一個範例會使用包含反復專案、篩選和 yield 的序列運算式來產生陣列。 此程式碼會將1和100之間的質數序列列印到主控台。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

下列範例會建立一個由三個元素的元組組成的乘法資料表，其中每個專案都包含兩個因素和產品：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

下列範例示範如何使用，將 `yield!` 個別序列合併成單一的最終順序。 在此情況下，二進位樹狀結構中的每個子樹的序列會串連在遞迴函式中，以產生最終的順序。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>使用順序

序列支援許多與 [清單](lists.md)相同的功能。 序列也支援使用按鍵產生函數進行分組和計算等作業。 序列也支援更多樣化的函式來解壓縮個子序列。

許多資料類型（例如清單、陣列、集合和地圖）都是可列舉的集合，因此是隱含的序列。 接受序列做為引數的函式可搭配任何一般 F # 資料型別使用，除了任何執行的 .NET 資料類型之外 `System.Collections.Generic.IEnumerable<'T>` 。 將其與接受清單作為引數的函式相比較，該函式只能接受清單。 此類型 `seq<'T>` 是的類型縮寫 `IEnumerable<'T>` 。 這表示任何實作為泛型的型別（ `System.Collections.Generic.IEnumerable<'T>` 包括 F # 中的陣列、清單、集合和對應，以及大部分的 .net 集合型別）都與型別相容， `seq` 而且可以在預期順序的任何地方使用。

## <a name="module-functions"></a>模組函式

[Fsharp.core 命名空間](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections.html)中的[Seq 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html)包含使用順序的函式。 這些函式也適用于清單、陣列、對應和集合，因為所有這些類型都是可列舉的，因此可視為序列。

## <a name="creating-sequences"></a>建立序列

您可以使用順序運算式（如先前所述），或使用特定函數來建立順序。

您可以使用 [seq. 空白](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#empty)來建立空的序列，也可以使用 [seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#singleton)來建立只有一個指定元素的序列。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

您可以使用 [Seq.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#init) 來建立使用您提供的函式來建立元素的序列。 您也會提供序列的大小。 此函式就像 [List.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#init)一樣，不同的是在您逐一查看序列之前，不會建立元素。 下列程式碼說明如何使用 `Seq.init` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

輸出為

```console
0 10 20 30 40
```

您可以使用 [list.ofarray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofArray) 和 [seq. ofList&#60; t&#62; 函數](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofList)，從陣列和清單建立序列。 不過，您也可以使用轉換運算子，將陣列和清單轉換成序列。 下列程式碼中會顯示這兩種技術。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

藉由使用 [Seq 轉換](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cast)，您可以從弱型別集合中建立序列，例如中定義的序列 `System.Collections` 。 這類弱型別集合具有元素類型 `System.Object` ，而且是使用非泛型型別來列舉 `System.Collections.Generic.IEnumerable&#96;1` 。 下列程式碼說明如何使用將 `Seq.cast` 轉換 `System.Collections.ArrayList` 成序列。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

您可以使用 [Seq.initInfinite](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#initInfinite) 函數來定義無限序列。 針對這類序列，您會提供一個函式，以從專案的索引產生每個元素。 由於延遲評估，因此可能會有無限的順序;您可以藉由呼叫您指定的函式，視需要建立元素。 下列程式碼範例會產生無限的浮點數序列，在此案例中為連續整數平方的 reciprocals 序列。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#unfold) 會從計算函式產生順序，此函式會接受狀態並將其轉換為產生序列中的每個後續元素。 此狀態只是用來計算每個專案的值，而且可在每個元素計算時變更。 的第二個引數 `Seq.unfold` 是用來啟動序列的起始值。 `Seq.unfold` 使用狀態的選項類型，可讓您藉由傳回值來終止序列 `None` 。 下列程式碼顯示兩個序列範例， `seq1` 以及 `fib` 由作業產生的 `unfold` 。 第一個， `seq1` 是最多20個數字的簡單序列。 第二個會 `fib` 使用 `unfold` 來計算斐波里的序列。 因為量值序列中的每個元素都是前兩個斐的兩個量值的總和，所以狀態值是由序列中前兩個數字組成的元組。 初始值是 `(1,1)` 序列中的前兩個數字。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

輸出如下所示：

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

下列程式碼範例會使用此處所述的許多序列模組函式來產生和計算無限序列的值。 程式碼可能需要幾分鐘的時間來執行。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>搜尋和尋找元素

序列支援清單的可用功能： [Seq. exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists)、 [array.exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists)、 [seq. find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#find)、 [findIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#findIndex)、 [Seq. pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pick)、 [tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFind)和 [array.tryfindindex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFindIndex)。 這些可用於序列的函式版本，只會評估序列到所搜尋的專案。 如需範例，請參閱 [清單](lists.md)。

## <a name="obtaining-subsequences"></a>取得個子序列

[Seq. filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#filter) 和 [seq。 choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#choose) 如同可用於清單的對應函式，不同的是，在評估 sequence 元素之前，不會發生篩選和選擇。

[Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#truncate) 會從另一個序列建立序列，但會將序列限制為指定的元素數目。 [Seq： take 會](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#take) 建立新的序列，其中只包含序列開頭的指定元素數目。 如果序列中的專案數少於您所指定的時間，則會擲回 `Seq.take` `System.InvalidOperationException` 。 和之間的差異在於， `Seq.take` `Seq.truncate` `Seq.truncate` 如果元素數目少於您指定的數目，則不會產生錯誤。

下列程式碼顯示和之間的行為和差異 `Seq.truncate` `Seq.take` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

發生錯誤之前的輸出會如下所示。

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

藉由使用 [takeWhile](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#takeWhile)，您可以將述詞函式指定 (布耳函數) ，然後根據述詞為原始序列的這些元素所組成的另一個序列建立序列，但在述詞傳回 `true` 的第一個專案之前停止 `false` 。 [Seq. skip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skip) 會傳回序列，以略過另一個序列的第一個專案，並傳回其餘專案的指定數目。 [SkipWhile](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skipWhile) 會傳回一個序列，只要述詞傳回，就會略過另一個序列的第一個元素 `true` ，然後傳回其餘的元素，從述詞傳回的第一個專案開始 `false` 。

下列程式碼範例說明、和之間的行為和 `Seq.takeWhile` 差異 `Seq.skip` `Seq.skipWhile` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

輸出如下。

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>轉換序列

[Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pairwise) 會建立新的序列，以將輸入序列的後續元素分組到元組中。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#windowed) 就像這樣，不同的是， `Seq.pairwise` 除了產生一系列的元組之外，它也會產生一連串陣列，其中包含從序列 (*視窗*) 的相鄰元素複本。 您可以指定每個陣列中所需的相鄰元素數目。

下列程式碼範例示範 `Seq.windowed` 的用法。 在此情況下，視窗中的元素數目為3。 此範例會使用在 `printSeq` 上一個程式碼範例中定義的。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

輸出如下。

初始順序：

```console
1.0 1.5 2.0 1.5 1.0 1.5

Windows of length 3:
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|]

Moving average:
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>具有多個序列的作業

[Seq.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip) 和 [Seq.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip3) 採用兩個或三個序列，並產生一系列的元組。 這些函式就像是適用于 [清單](lists.md)的對應函數。 沒有對應的功能可將一個序列分隔為兩個或多個序列。 如果您需要順序的此功能，請將序列轉換為清單，並使用 [ [解壓縮](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip)]。

## <a name="sorting-comparing-and-grouping"></a>排序、比較和分組

清單支援的排序函式也適用于序列。 這包括 [Seq. sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sort) 和 [seq. sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sortBy)。 這些函數會逐一查看整個序列。

您可以使用 [seq.comparewith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#compareWith) 函數來比較兩個序列。 函式會輪流比較後續的專案，並在遇到第一個不相等的配對時停止。 任何額外的元素都不會影響到比較。

下列程式碼示範 `Seq.compareWith` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

在先前的程式碼中，只會計算和檢查第一個元素，而結果為-1。

[Seq.countby](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#countBy) 所採用的函式會為每個專案產生一個稱為索引 *鍵* 的值。 藉由在每個專案上呼叫此函式來產生每個專案的索引鍵。 `Seq.countBy` 然後傳回包含索引鍵值的序列，以及產生每個索引鍵值的元素數目計數。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

輸出如下。

```console
(1, 34) (2, 33) (0, 33)
```

先前的輸出顯示，產生金鑰1、33值產生金鑰2的原始序列有34個元素，以及產生金鑰0的33值。

您可以藉由呼叫 [Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#groupBy)，來群組序列的元素。 `Seq.groupBy` 接受從專案產生索引鍵的序列和函式。 函數會在序列的每個專案上執行。 `Seq.groupBy` 傳回一系列的元組，其中每個元組的第一個元素是索引鍵，而第二個專案是產生該索引鍵的元素序列。

下列程式碼範例示範 `Seq.groupBy` 如何使用將數位序列從1到100分割成具有相異索引鍵值0、1和2的三個群組。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

輸出如下。

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

您可以藉由呼叫 [Seq. distinct](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinct)來建立可消除重複專案的序列。 或者，您可以使用 [Seq. seq.distinctby](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinctBy)，它會接受在每個專案上呼叫按鍵產生函數。 產生的序列包含原始序列中具有唯一索引鍵的元素;稍後會捨棄產生重複索引鍵的元素給先前的元素。

下列程式碼範例說明如何使用 `Seq.distinct` 。 `Seq.distinct` 是藉由產生代表二進位數的序列來示範，然後顯示唯一的相異元素為0和1。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

下列程式碼示範如何 `Seq.distinctBy` 從包含負數和正數的序列開始，並使用絕對值函式作為索引鍵產生函數。 產生的序列遺漏了對應到序列中之負數的所有正數，因為負數會出現在序列中，因此會被選取，而不是具有相同絕對值或索引鍵的正數。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Readonly 和快取順序

[Seq. readonly](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#readonly) 會建立序列的唯讀複本。 `Seq.readonly` 當您有讀寫集合（例如陣列），而且您不想要修改原創組合時，會很有用。 此函數可以用來保留資料封裝。 在下列程式碼範例中，會建立包含陣列的型別。 屬性會公開陣列，而不是傳回陣列，而是使用來傳回從陣列建立的序列 `Seq.readonly` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq. cache](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cache) 會建立序列的儲存版本。 使用 `Seq.cache` 可避免重新評估序列，或當您有多個使用序列的執行緒時，但您必須確定每個專案只會在一次時採取動作。 當您有多個執行緒正在使用的序列時，您可以有一個執行緒來列舉和計算原始序列的值，而其餘的執行緒可以使用快取的序列。

## <a name="performing-computations-on-sequences"></a>在序列上執行計算

簡單的算數運算和清單類似，例如 [seq. average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#average)、 [seq. sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sum)、 [averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#averageBy)、 [seq. sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sumBy)等等。

[Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#fold)、 [seq. 減低](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#reduce)和 [seq. scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#scan) 就像是可用於清單的對應函式。 序列支援這些函式的完整變化子集，這些功能會列出支援。 如需詳細資訊和範例，請參閱 [清單](lists.md)。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [F# 類型](fsharp-types.md)
