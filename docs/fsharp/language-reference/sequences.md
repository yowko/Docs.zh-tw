---
title: 序列 (F#)
description: '了解如何使用 F # 序列，當您使用較大，已排序集合的資料，但不一定要使用的所有項目。'
ms.date: 05/16/2016
ms.openlocfilehash: ebebec3a69fd0f4fb8e3ad8d554541fa1cc8945e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sequences"></a>序列

> [!NOTE]
本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

A*順序*邏輯的一連串的項目所有的一種類型。 當您使用較大，已排序集合的資料，但不是一定會預期使用的所有項目時，順序會特別有用。 個別序列項目會計算只做為必要項，讓序列可以提供較佳的效能比情況中，並非可用所有的項目中的清單。 順序由`seq<'T>`類型，這是別名的`System.Collections.Generic.IEnumerable`。 因此，任何.NET Framework 型別可實作`System.IEnumerable`可用做為序列。 [Seq 模組](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)提供操作與順序有關的支援。

## <a name="sequence-expressions"></a>循序項運算式
A*序列運算式*是一個順序評估的運算式。 循序項運算式中可能需要數種格式。 最簡單的形式指定的範圍。 例如，`seq { 1 .. 5 }`建立序列，其中包含五個項目，包括 1 到 5 的端點。 您也可以指定遞增 （或遞減） 之間兩個雙句點。 例如，下列程式碼會建立 10 個倍數的順序。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

F # 運算式會產生序列的值是由循序項運算式所組成。 他們可以使用`yield`關鍵字來產生變成順序一部分的值。

以下是範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

您可以使用`->`運算子，而不是`yield`，在此情況下，您可以省略`do`關鍵字，如下列範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

下列程式碼會產生一份座標組，以及索引到陣列，代表方格。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if`序列中使用的運算式是篩選器。 例如，若要產生唯一的質數，假設您有函式的序列`isprime`型別的`int -> bool`，建構的序列，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

當您使用`yield`或`->`反覆項目，在每個反覆項目必須以產生單一項目的序列。 如果每個反覆項目會產生一連串的項目，使用`yield!`。 在此情況下，每個反覆運算上產生的項目會串連來產生最後的序列。

您可以結合在一起在循序項運算式中的多個運算式。 每個運算式所產生的項目串連在一起。 如需範例，請參閱本主題的 「 範例 」 一節。

## <a name="examples"></a>範例
第一個範例會使用循序項運算式包含反覆項目、 篩選和 yield 產生陣列。 此程式碼會列印一串質數介於 1 到 100 到主控台。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

下列程式碼會使用`yield`建立三個項目，各包含兩個因素與產品的 tuple 所組成的乘法表。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

下列範例示範如何使用`yield!`結合成單一的最後一個序列的個別序列。 在此情況下，在二進位樹狀目錄中的每個樹狀子目錄的序列會在遞迴函式，以產生最終的順序串連。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]
    
## <a name="using-sequences"></a>使用順序
時序支援許多相同的函式做為[列出](lists.md)。 序列也支援分組，並且使用索引鍵產生函式計算等作業。 序列也支援更多樣化的函式來擷取子。

許多資料類型，例如清單、 陣列、 集合和對應是以隱含方式序列，因為它們是可列舉集合。 函式會將序列，當做引數搭配任一常見 F # 資料類型，除了可實作任何.NET Framework 資料型別的`System.Collections.Generic.IEnumerable<'T>`。 以此對照接受清單做為引數只能接受清單的函式。 型別`seq<'T>`是類型縮寫`IEnumerable<'T>`。 這表示任何型別實作泛型`System.Collections.Generic.IEnumerable<'T>`，其中包括陣列、 清單、 設定和 F # 和也大部分.NET Framework 集合型別中的對應相容`seq`輸入，然後就可以使用預期的順序。


## <a name="module-functions"></a>模組函式
[Seq 模組](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)中[Microsoft.FSharp.Collections 命名空間](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)包含序列所使用的功能。 這些函式使用清單、 陣列、 對應和集合，因為所有這些類型是可列舉的並因此可被視為序列。


## <a name="creating-sequences"></a>建立順序
您可以建立序列之前所述，使用循序項運算式，或使用某些函式。

您可以使用來建立空的序列[Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)，或者您可以建立一連串的只有一個指定的項目使用[Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

您可以使用[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)建立項目建立使用您提供的函式的順序。 您也會提供用於序列的大小。 此函式一樣是[List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)，不同之處在於您逐一查看序列之前不會建立項目。 下列程式碼說明如何使用`Seq.init`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

輸出為

```
0 10 20 30 40
```

使用[Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)和[Seq.ofList&#60;t&#62;函式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)，您可以建立從陣列和清單的順序。 不過，您也可以轉換陣列和清單順序使用轉換運算子。 這兩種技術是以下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

使用[Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)，您可以從弱型別的集合，例如所定義的建立順序`System.Collections`。 這類弱型別的集合都具有項目型別`System.Object`會使用非泛型列舉和`System.Collections.Generic.IEnumerable&#96;1`型別。 下列程式碼說明如何使用`Seq.cast`轉換`System.Collections.ArrayList`成序列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

您可以使用，以定義無限序列[Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)函式。 對於時序，您可以提供函式，並產生的項目索引的每個項目。 無限期的順序有可能因為延遲評估;視需要透過呼叫您指定的函式，會建立項目。 下列程式碼範例會產生浮點數，在此情況下替代倒數連續整數平方的一系列的無限的序列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)產生一連串的計算函式取用狀態，並將其轉換為產生的序列中每個後續項目。 狀態為只是用來計算每個項目，並可隨著每個項目會計算值。 第二個引數`Seq.unfold`是用來啟動順序的起始值。 `Seq.unfold` 使用狀態，可讓您藉由傳回終止順序選項的型別`None`值。 下列程式碼顯示的順序，兩個範例`seq1`和`fib`，由產生`unfold`作業。 首先， `seq1`，是只具有最多 100 的數字的簡單順序。 第二個， `fib`，會使用`unfold`來計算 Fibonacci 順序。 費式數列序列中的每個項目是先前的兩個 Fibonacci 數字的總和，因為狀態值是序列中前兩個數字所組成的 tuple。 初始值是`(1,1)`，序列中的前兩個數字。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

其輸出如下：

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

下列程式碼會使用許多順序模組函式產生，並計算的無限序列值此處所述的範例。 程式碼可能需要幾分鐘才能完成。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]
    
## <a name="searching-and-finding-elements"></a>搜尋和尋找項目
序列支援的功能適用於清單： [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1)， [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)， [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)， [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3)， [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d)， [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)，和[Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。 這些函式可供順序的版本會評估順序，只會一直要搜尋的項目。 如需範例，請參閱[列出](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。


## <a name="obtaining-subsequences"></a>取得子
[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)和[Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)是類似的對應函式清單，請使用不同之處在於篩選並選擇，才會進行評估的順序項目。

[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)從另一個序列，會建立序列，但將序列限制為指定的項目數。 [Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)會建立新的序列，包含指定數字的序列開頭的項目。 如果有較少序列中的項目比您指定要採取，`Seq.take`會擲回`System.InvalidOperationException`。 之間的差異`Seq.take`和`Seq.truncate`在於`Seq.truncate`的元素數目少於的數字就是指定不會產生錯誤。

下列程式碼所示的行為和之間的差異`Seq.truncate`和`Seq.take`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

輸出中，會發生此錯誤之前，如下所示。

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

使用[Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)，您可以指定述詞的函式 （布林值的函式），並建立另一個原始序列的述詞的這些元素組成的序列中的順序`true`，但停止傳回的述詞的第一個項目之前`false`。 [Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)傳回序列，略過指定的數目的另一個序列的第一個項目，並傳回其餘項目。 [Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)傳回略過另一個序列的第一個項目，只要傳回的述詞的序列`true`，然後傳回其餘項目，則述詞傳回的第一個元素開始`false`.

下列程式碼範例說明的行為和之間的差異`Seq.takeWhile`， `Seq.skip`，和`Seq.skipWhile`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

輸出如下。

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>轉換順序
[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)會建立新的序列，後續的輸入序列的項目會群 tuple。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)就像是`Seq.pairwise`，不過，而不是產生一連串的 tuple，它會產生一連串的陣列，其中包含的相鄰元素的複本 (*視窗*) 序列。 您每個陣列中指定您想要的相鄰項目數目。

下列程式碼範例示範 `Seq.windowed` 的用法。 在此情況下視窗中的項目數為 3。 此範例會使用`printSeq`，定義在先前的程式碼範例。

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
[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)和[Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16)採用兩個或三個序列，並產生一連串的 tuple。 這些函式是對應的函式用於像[列出](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。 沒有任何對應的功能，來分隔一個序列分成兩個或多個序列。 如果您需要這項功能的序列，將序列轉換為清單，並使用[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)。


## <a name="sorting-comparing-and-grouping"></a>排序、 比較和群組
List 支援排序函式也會使用序列。 這包括[Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e)和[Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)。 這些函式逐一查看整個序列。

使用比較兩個序列[Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)函式。 函式接著會比較連續元素，並停止當它遇到第一對不相等。 任何其他項目不會構成的比較。

下列程式碼示範 `Seq.compareWith` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

先前的程式碼中，第一個項目會計算和檢查，且結果為-1。

[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)接受函式產生一個值，稱為*金鑰*每個項目。 每個項目產生金鑰，在每個項目上呼叫此函式。 `Seq.countBy` 則會傳回序列，其中包含的索引鍵值，以及產生索引鍵的每個值的項目數目的計數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

輸出如下。

```
(1, 34) (2, 33) (0, 33)
```

上述輸出會顯示已 34 的項目所產生的索引鍵為 1，將原始序列所產生的索引鍵 2 的 33 值和 33 所產生的索引鍵 0 的值。

您可以藉由呼叫來群組序列的項目[Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)。 `Seq.groupBy` 會將序列和函式會產生金鑰的項目。 此函式順序的每個項目上執行。 `Seq.groupBy` 傳回序列的 tuple，其中每個 tuple 的第一個元素是機碼，而第二個是一串產生該索引鍵的項目。

下列程式碼範例示範使用`Seq.groupBy`分割成三個群組具有相異索引鍵的值 0、 1 和 2 從 1 到 100 之間的數字的序列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

輸出如下。

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

您可以建立一連串以消除重複的項目，藉由呼叫[Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)。 您可以使用或者[Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)，其採用索引鍵產生函式呼叫的每個項目。 產生的序列包含具有唯一的索引鍵; 原始序列的項目更新產生的較早的項目重複的索引鍵的項目都會被捨棄。

下列程式碼範例說明使用`Seq.distinct`。 `Seq.distinct` 示範藉由產生代表二進位數字的順序，然後顯示 僅不同的項目為 0 和 1。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

下列程式碼示範`Seq.distinctBy`開頭包含負數和正數的序列，並為索引鍵產生函式使用絕對值函式。 遺漏對應到在順序中，負數，因為負數稍早在序列中都會出現，而且因此而不是正數，具有相同的絕對選取所有正數所產生的順序。值或索引鍵。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]
    
## <a name="readonly-and-cached-sequences"></a>在 Readonly 和快取的順序
[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)建立序列的唯讀複本。 `Seq.readonly` 當您具有讀寫集合，例如陣列、 且不想修改原始集合，則會是很有用。 此函式可以用來保留資料的封裝。 在下列程式碼範例中，會建立包含陣列的類型。 屬性會公開的陣列，但是它會使用建立陣列中的順序傳回而不是傳回陣列， `Seq.readonly`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)建立序列的儲存的版本。 使用`Seq.cache`以避免重新評估的順序，或當您使用順序的多個執行緒，但您必須確定每個項目會處理一次。 若您正在使用多個執行緒的順序，您可以擁有的列舉，並計算的值將原始序列中，執行緒，而且其餘的執行緒可以使用快取的順序。


## <a name="performing-computations-on-sequences"></a>序列上執行計算
簡單的算術運算是類似的清單，例如[Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)， [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)， [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)， [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)，依此類推。

[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)， [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)，和[Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)都和對應函式可用於清單一樣。 時序支援列出支援這些函式的完整變化的子集。 如需詳細資訊和範例，請參閱[列出](lists.md)。

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[F# 類型](fsharp-types.md)
