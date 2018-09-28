---
title: 序列 (F#)
description: '了解如何使用 F # 時序，當您使用較大，已排序集合的資料，但不一定會預期要使用的所有項目。'
ms.date: 05/16/2016
ms.openlocfilehash: cfe8d1e350a8ac46b7700c12aa84d250f8b35855
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47425936"
---
# <a name="sequences"></a>序列

> [!NOTE]
本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

A*順序*是邏輯的一連串的項目所有的一種類型。 當您使用較大，已排序集合的資料，但不是一定會使用所有的項目時，順序會特別有用。 個別序列項目會計算只做為必要項，因此序列可以提供較佳的效能比在中，並非所有項目所使用的情況下的清單。 序列由`seq<'T>`類型，這是別名的`System.Collections.Generic.IEnumerable`。 因此，任何.NET Framework 型別可實作`System.IEnumerable`可用來當做一系列。 [Seq 模組](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)支援牽涉到序列的操作。

## <a name="sequence-expressions"></a>循序項運算式

A*序列運算式*是評估為一連串的運算式。 循序項運算式可以採取數種格式。 最簡單的形式指定的範圍。 比方說，`seq { 1 .. 5 }`建立序列，其中包含五個項目，包括 1 到 5 的端點。 您也可以指定遞增值 （或遞減） 之間兩個雙句點。 例如，下列程式碼會建立 10 個倍數的順序。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

循序項運算式會組成 F # 運算式會產生序列的值。 他們可以使用`yield`關鍵字來產生值，成為順序的一部分。

以下是範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

您可以使用`->`運算子來取代`yield`，在此情況下，您可以省略`do`關鍵字，如下列範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

下列程式碼會產生陣列，代表方格座標組，以及索引的清單。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if`序列中所使用的運算式是一個篩選條件。 例如，若要產生唯一的質數，假設您有一個函式的一連串`isprime`型別的`int -> bool`，建構的序列，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

當您使用`yield`或`->`反覆項目，在每個反覆項目必須產生序列的單一項目。 如果每個反覆項目產生一連串的項目，使用`yield!`。 在此情況下，產生每個反覆運算上的項目會串連以產生最終的順序。

您可以結合在一起序列運算式中的多個運算式。 每個運算式所產生的項目會串連在一起。 如需範例，請參閱本主題的 < 範例 > 一節。

## <a name="examples"></a>範例

第一個範例會使用序列運算式中包含反覆項目、 篩選和產生陣列 yield。 此程式碼會列印一連串的質數，介於 1 到 100 到主控台。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

下列程式碼會使用`yield`建立三個項目，其中包含兩個因素和產品的每個 tuple 所組成的乘法表。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

下列範例示範如何使用`yield!`結合成單一的最終序列的個別序列。 在此情況下，二進位樹狀目錄中的每個樹狀子目錄的序列會串連在遞迴函式以產生最終的順序。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>使用順序

序列支援許多功能都與相同[列出](lists.md)。 序列也支援等分組，並且使用索引鍵產生函式來計算作業。 序列也會支援不同的函式來擷取子序列。

許多資料類型，例如清單、 陣列、 集合和對應是以隱含方式序列，因為它們是可列舉集合。 序列，當成引數適用於任何一般 F # 資料類型，除了可實作任何.NET Framework 資料型別的函式`System.Collections.Generic.IEnumerable<'T>`。 與此相反接受清單做為引數只能接受清單的函式。 型別`seq<'T>`是類型縮寫`IEnumerable<'T>`。 這表示，任何型別實作泛型`System.Collections.Generic.IEnumerable<'T>`，其中包括陣列、 清單、 設定和中 F # 和也大部分.NET Framework 集合類型，對應相容`seq`輸入，然後就可以使用預期的順序。

## <a name="module-functions"></a>模組函式

[Seq 模組](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)中[Microsoft.FSharp.Collections 命名空間](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)包含使用序列函數。 這些函式使用清單、 陣列、 對應和集合，因為所有這些類型是可列舉的且因此可視為序列。

## <a name="creating-sequences"></a>建立順序

如前所述，使用循序項運算式，或使用某些函式，您可以建立順序。

您可以使用，以建立空的序列[Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)，或您可以使用，以便建立只有一個指定的項目序列[Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

您可以使用[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)建立順序，這會使用您提供的函式建立的元素。 您也會提供序列的大小。 此函式是如同[List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)，不同之處在於您逐一查看序列之前，不會建立項目。 下列程式碼說明如何使用`Seq.init`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

輸出為

```
0 10 20 30 40
```

使用[Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)並[Seq.ofList&#60;t&#62;函式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)，您可以建立從陣列和清單的順序。 不過，您也可以轉換陣列和清單順序使用轉換運算子。 這兩種技術是以下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

藉由使用[Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)，您可以從弱型別集合，例如中定義的建立順序`System.Collections`。 這類弱型別的集合都具有項目型別`System.Object`並使用非泛型列舉`System.Collections.Generic.IEnumerable&#96;1`型別。 下列程式碼說明如何使用`Seq.cast`要轉換`System.Collections.ArrayList`成序列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

您也可以使用來定義 「 無限序列[Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)函式。 針對這類序列中，您可以提供產生每個項目中的項目索引的函式。 無限的順序有可能因為延遲評估;視需要透過呼叫您指定的函式，會建立項目。 下列程式碼範例會產生無限序列的浮點數，在此情況下替代一系列的連續整數的平方和的倒數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)計算函式，以取得狀態，並將其轉換為產生序列中的每個後續項目從產生的序列。 狀態為只是用來計算每個項目，並可隨著每個項目會計算值。 第二個引數`Seq.unfold`是用來啟動順序的起始值。 `Seq.unfold` 使用選項類型的狀態，可讓您藉由傳回終止的序列`None`值。 下列程式碼顯示的順序，兩個範例`seq1`並`fib`，所產生`unfold`作業。 第一天， `seq1`，是只是簡單的順序顯示最多 100 的數字。 第二`fib`，使用`unfold`計算 Fibonacci 序列。 Fibonacci 序列中的每個項目是先前的兩個費式數列數字的總和，因為狀態值就會是序列中前兩個數字所組成的 tuple。 初始值是`(1,1)`，序列中的前兩個數字。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

其輸出如下：

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

下列程式碼會使用許多此處所述產生，並計算無限序列的值序列模組函式的範例。 程式碼可能需要幾分鐘的時間來執行。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>搜尋和尋找項目

序列支援功能的清單： [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1)， [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)， [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)， [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3)， [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d)， [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)，以及[Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。 這些函式可供順序版本評估只到要搜尋的項目序列。 如需範例，請參閱[列出](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。

## <a name="obtaining-subsequences"></a>取得子序列

[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)並[Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)就像是對應的函式所提供的清單，不同之處在於篩選和選擇，才會進行評估序列項目。

[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)從另一個序列，會建立序列，但將序列限制為指定的元素數目。 [Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)會建立新的序列，其中包含從序列開頭的項目中指定數字。 如果有較少項目序列中的比您所要採取，指定`Seq.take`會擲回`System.InvalidOperationException`。 之間的差異`Seq.take`並`Seq.truncate`在於`Seq.truncate`不會產生錯誤，如果您指定少於的數字的項目數。

下列程式碼所示的行為和之間的差異`Seq.truncate`和`Seq.take`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

輸出中，會發生此錯誤之前，如下所示。

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

藉由使用[Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)，您可以指定述詞的函式 （布林值的函式），並建立另一個述詞的原始序列的項目所組成的序列中的順序`true`，但停止所述詞傳回的第一個項目之前`false`。 [Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)傳回序列，會略過指定的數目的另一個序列的第一個項目，並傳回其餘項目。 [Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)會傳回另一個序列的第一個項目會略過，只要述詞傳回的序列`true`，然後傳回其餘項目，從第一個元素的述詞會傳回`false`.

下列程式碼範例說明的行為和之間的差異`Seq.takeWhile`， `Seq.skip`，和`Seq.skipWhile`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

輸出如下。

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>轉換序列

[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)會建立新的輸入序列的後續項目會分組 tuple 的順序。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)就像是`Seq.pairwise`，不過，而不是產生一系列 tuple，它會產生一系列包含相鄰的項目複本的陣列 (*視窗*) 序列。 您每個陣列中指定您想要的相鄰項目數目。

下列程式碼範例示範 `Seq.windowed` 的用法。 在此情況下在視窗中的項目數為 3。 此範例會使用`printSeq`，其定義於上述程式碼範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

輸出如下。

初始順序：

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>使用多個序列的作業

[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)並[Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16)採用兩個或三個序列，然後產生一系列 tuple。 這些函式就像是對應的函式可供[列出](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。 沒有任何對應的功能，將活動順序分成兩個或多個序列的單一序列。 如果您需要這項功能的順序時，將序列轉換為清單，並使用[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)。

## <a name="sorting-comparing-and-grouping"></a>排序、 比較和群組

支援清單的排序函式也會使用序列。 這包括[Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e)並[Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)。 這些函式逐一查看整個序列。

使用比較兩個序列[Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)函式。 函式會比較後續項目，並遇到第一個不相等配對時，就會停止。 比較並不會提供任何額外的項目。

下列程式碼示範 `Seq.compareWith` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

在先前的程式碼中的第一個項目會計算，而且檢查，且結果為-1。

[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)會產生名為值的函式*金鑰*每個項目。 每個項目會產生金鑰，藉由在每個項目上呼叫此函式。 `Seq.countBy` 則會傳回序列，其中包含索引鍵的值，以及產生索引鍵的每個值的元素數目計數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

輸出如下。

```
(1, 34) (2, 33) (0, 33)
```

先前的輸出會顯示已 34 項目所產生的索引鍵為 1，將原始序列的 33 所產生的索引鍵 2 的值和 33 所產生的索引鍵 0 的值。

您可以藉由呼叫來分組序列的項目[Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)。 `Seq.groupBy` 採用序列及從項目產生索引鍵的函式。 此函式會執行序列的每個項目。 `Seq.groupBy` 傳回 tuple，其中每個 tuple 的第一個項目是索引鍵，而第二個是一串產生該索引鍵的項目的序列。

下列程式碼範例示範使用`Seq.groupBy`分割成三個群組具有相異索引鍵的值 0、 1 和 2 從 1 到 100 之間的數字的順序。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

輸出如下。

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

您可以建立一連串可消除重複的項目，藉由呼叫[Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)。 或者您可以使用[Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)，後者會採用索引鍵產生函式呼叫的每個項目。 產生的序列包含具有唯一的索引鍵，將原始序列的項目更新產生的較早的項目重複的索引鍵的項目都會被捨棄。

下列程式碼範例示範如何將`Seq.distinct`。 `Seq.distinct` 示範，產生代表二進位數字的序列，並接著顯示 只獨特的項目為 0 和 1。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

下列程式碼示範`Seq.distinctBy`開頭包含負數和正數的序列，並使用絕對值函數當做索引鍵產生函式。 遺漏所有對應至在順序中，負數的數字，因為負數的數字順序稍早出現，因此選取而不是正數，具有相同的絕對正數字所產生的順序。值或索引鍵。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>在 Readonly 和快取的序列

[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)建立序列的唯讀複本。 `Seq.readonly` 您有讀寫集合，例如陣列、 而且不想修改原始集合時很有用。 此函式可用來保留資料的封裝。 在下列程式碼範例中，會建立包含陣列的類型。 屬性會公開的陣列，但它會傳回而不是傳回陣列，使用建立從陣列的一連串`Seq.readonly`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)建立序列的儲存的版本。 使用`Seq.cache`以避免重新評估的順序，或當您有多個執行緒的使用順序，但您必須確定每個項目採取一次。 若您正在使用多個執行緒的順序，您可以有一個執行緒的列舉，並計算原始序列中的值和其餘的執行緒可以使用快取的順序。

## <a name="performing-computations-on-sequences"></a>在序列上執行計算

簡單的算數運算是類似的清單，例如[Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)， [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)， [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)， [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)，依此類推。

[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)， [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)，以及[Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)就像是對應的函式所提供的清單。 序列支援列出支援這些函式的完整變化的子集。 如需詳細資訊和範例，請參閱 <<c0> [ 列出](lists.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [F# 類型](fsharp-types.md)
