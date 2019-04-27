---
title: 清單
description: 深入了解F#清單、 排序、 不可變的系列相同類型的元素。
ms.date: 05/16/2016
ms.openlocfilehash: cc4e292280cca0dca37f69cf5a46ec2822d08d5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904120"
---
# <a name="lists"></a>清單

> [!NOTE]
> 本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

在 F# 中，list 是包含一系列經過排序且類型相同的固定元素。 若要執行基本作業清單，使用中的函式[List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)。

## <a name="creating-and-initializing-lists"></a>建立及初始化 list

您可以藉由明確列出元素 (以逗號分隔並括以方括號) 來定義 list，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

您也可以在元素之間加入分行符號；若您選擇加入分行符號，就不一定需要使用分號。 當元素初始化運算式比較長，或當您想要為每個元素加入逗號時，以後一種語法編寫的程式碼會比較容易閱讀。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

通常 list 的所有元素都應必須是同一類型。 但當 list 指定的元素具有衍生類型的基底類型時，就不在此限。 下列的 `Button` 與 `CheckBox` 因為都是從 `Control` 衍生而來，所以可接受。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

如下列程式碼所示，您也可以使用以整數指定的範圍 (以範圍運算子 `..` 分隔) 來定義 list 元素。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

空 list 由不含任何內容的一對方括號指定。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

您也可以使用順序運算式建立 list。 請參閱[循序項運算式](sequences.md#sequence-expressions)如需詳細資訊。 例如下列程式碼會建立從 1 到 10 之整數平方的 list。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>使用 list 的運算子

您可以使用 `::` (cons) 運算子。 若 `list1` 為 `[2; 3; 4]`，下列程式碼將 `list2` 建立為 `[100; 2; 3; 4]`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

您可以使用 `@` 運算子串流具有相容類型的 list，如下列程式碼所示。 當 `list1` 為 `[2; 3; 4]` 及 `list2` 為 `[100; 2; 3; 4]` 時，此程式碼會將 `list3` 建立為 `[2; 3; 4; 100; 2; 3; 4]`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

用於執行 list 運算的函式位於[List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)。

由於 F# 中的 list 為固定，因此任何修改作業都會產生新的 list，而不會修改現有的 list。

列出在F#會實作為單向連結串列，亦即存取只有清單的標頭的作業都是 o （1），，和元素存取為 O (*n*)。

## <a name="properties"></a>屬性

list 類型支援下列屬性：

|屬性|類型|描述|
|--------|----|-----------|
|[標頭](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|第一個元素。|
|[空白](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|此為靜態屬性，會傳回適當類型的空 list。|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true` 表示 list 不含任何元素。|
|[Item](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|使用位於指定索引的元素 (以零為基底)。|
|[長度](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|元素數。|
|[結尾](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|list 沒有第一個元素。|

下列是使用這些屬性的一些範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>使用 list

使用 list 編寫程式讓您只需要編寫小量的程式碼，就可以執行複雜的運算。 本節說明一些使用函式編寫程式時不可或缺的常用 list 運算。

### <a name="recursion-with-lists"></a>list 的遞迴功能

list 是唯一適合遞迴程式設計技巧的函式。 假設有一項作業必須對 list 的每個元素執行。 您可以利用遞迴方式執行此作業，方法是先對 list 的 head 執行運算，再傳遞 list 的 tail (此 list 只含原始 list，而不含第一個元素，所以比較小)，然後再執行下一個遞迴層級的程式碼。

若要編寫這類遞迴函式，可以在模式比對中使用 cons 運算子 (`::`)，以區分 list 的 head 與 tail。

下列程式碼範例示範如何使用模式比對，實作執行 list 運算的遞迴函式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

前述程式碼對於小型 list 的效果很好，但對於大型的 list，可能會發生堆疊溢位。 下列程式碼是前述程式碼的改良版，運用了遞迴函式標準技巧中的 accumulator 引數。 使用 accumulator 引數可以遞迴函式的 tail，進而達到節省空間的目的。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

函式 `RemoveAllMultiples` 為遞迴函式，可接受兩個 list。 第一個 list 包含倍數要移除的數字；第二個 list 是數字要移除的 list。 下列範例會使用此遞迴函式消除 list 中的所有非質數，而只保留質數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

其輸出如下：

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>模組函式

[List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)提供存取項目清單的函式。 head 元素是最方便存取的元素。 使用屬性[Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)或在模組函式[List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2)。 您可以使用，以存取清單的結尾[結尾](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)屬性或[List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601)函式。 若要尋找的項目索引，使用[List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1)函式。 `List.nth` 會周遊 list。 因此，它是 O (*n*)。 若您的程式碼需要頻繁地使用 `List.nth`，您或可改用 array，而不要使用 list。 array 中的元素存取為 O(1)。

### <a name="boolean-operations-on-lists"></a>List 的布林運算

[List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107)函式會判斷清單是否有任何項目。

[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)函式適用於布林值的清單，並傳回元素的測試`true`任何項目是否滿足測試。 [List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e)類似，但會在後續的配對，兩個清單中的項目上運作。

下列程式碼示範 `List.exists` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

其輸出如下：

```
For list [0; 1; 2; 3], contains zero is true
```

下列範例示範 `List.exists2` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

其輸出如下：

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

您可以使用[List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7)如果您想要測試是否清單的所有元素都符合條件。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

其輸出如下：

```
true
false
```

同樣地， [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e)判斷兩個清單中的對應位置中的所有項目是否全都符合牽涉到的每對元素的布林運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

其輸出如下：

```
true
false
```

### <a name="sort-operations-on-lists"></a>List 的排序運算

[List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d)， [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)，並[List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7)函式清單進行排序。 排序函式可指定要使用這三個函式中的哪一個函式。 `List.sort` 會使用預設的泛型比較。 泛型比較會依不同的泛型比較函式而使用不同的全域運算子來比較值。 其可與多種元素類型搭配使用，例如簡單的數值類型、tuple、記錄、差別聯集、list、array 及所有實作 `System.IComparable` 的類型。 對於實作 `System.IComparable` 的類型，泛型比較會使用 `System.IComparable.CompareTo()` 函式。 泛型比較也會搭配字串，但會使用不涉及文化的排序順序。 請勿對不支援的類型 (例如函式類型) 使用泛型比較。 此外，預設泛型比較對小型結構類型的效能最好；若需要經常比較及排序比較大的結構類型，可考慮實作 `System.IComparable` 及佈建成效更好的 `System.IComparable.CompareTo()` 方法實作。

`List.sortBy` 可接受函式傳回的值做為排序準則；而 `List.sortWith` 可接受比較函式做為引數。 當您要使用的類型不支援比較時，或比較需要更複雜的比較語意 (例如使用涉及文化的字串) 時，即可使用後兩個函式。

下列範例示範 `List.sort` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

其輸出如下：

```
[-2; 1; 4; 5; 8]
```

下列範例示範 `List.sortBy` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

其輸出如下：

```
[1; -2; 4; 5; 8]
```

下列範例示範 `List.sortWith` 的用法。 此範例會使用自訂比較函式 `compareWidgets` 先比較自訂類型的第一個欄位，當第一個欄位的值相等時，再比較其他欄位。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

其輸出如下：

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>List 的搜尋運算

list 支援多種搜尋運算。 最簡單且[List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06)，可讓您尋找符合指定的條件的第一個元素。

下列程式碼範例示範如何使用 `List.find` 從 list 中尋找第一個可以被 5 整除的數字。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

The result is 5.

如果項目必須先經過轉換，呼叫[List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2)，後者會採用函式，會傳回選項，而且會尋找第一個選項值，是`Some(x)`。 `List.pick` 不會傳回元素，而會傳回結果 `x`。 若找不到相符的元素，`List.pick` 會擲出 `System.Collections.Generic.KeyNotFoundException`。 下列程式碼示範 `List.pick` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

其輸出如下：

```
"b"
```

搜尋作業的另一個群組[List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d)和相關的函式，會傳回選項值。 `List.tryFind` 函式會傳回 list 中第一個滿足條件的元素 (如其存在)；若找不到，即會傳回選項值 `None`。 變化[List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec)傳回之項目的索引; 如果有找到，而不是項目本身。 下列程式碼是這些函式的示範。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

其輸出如下：

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>List 的算術運算

內建常用的算術運算，例如 sum 及 average [List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)。 若要使用[List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9)，清單項目類型都必須支援`+`運算子，且具有零值。 所有內建算術類型皆滿足這些條件。 若要使用[List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1)，項目型別必須支援整除，這會排除整數類資料類型，但允許浮點數型別。 [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d)並[List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403)函式會採用做為參數的函式及此函式的結果來計算 sum 或 average 的值。

下列程式碼示範 `List.sum`、`List.sumBy` 及 `List.average` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

輸出為 `1.000000`。

下列程式碼示範 `List.averageBy` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

輸出為 `5.5`。

### <a name="lists-and-tuples"></a>List 與 Tuple

zip 及 unzip 函式可以操作包含 tuple 的 list。 這些函式會將各自包含一個值的兩個 list 合併成一份元組清單，或將一份元組清單分割成兩個只含單一值的 list。 最簡單[List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c)函式會採用兩個清單的單一項目，並產生一份元組配對。 另一個版本， [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b)、 接受三個清單的單一項目，並產生一份有三個元素的元組。 下列程式碼範例示範 `List.zip` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

其輸出如下：

```
[(1, -1); (2, -2); (3; -3)]
```

下列程式碼範例示範 `List.zip3` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

其輸出如下：

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

對應的 unzip 版本[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)並[List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)、 採用的 tuple 清單，並傳回清單中的 tuple，其中第一個清單中包含會先在每個 tuple 的所有項目，而第二個清單包含每個 tuple 以及等等的第二個項目。

下列程式碼範例示範如何使用[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

其輸出如下：

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

下列程式碼範例示範如何使用[List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

其輸出如下：

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>List 元素的運算

F# 支援多種 list 元素運算。 最簡單的是[List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f)，可讓您在清單中的每個項目上呼叫的函式。 包含變化[List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40)，這可讓您執行的兩個清單項目上的作業[List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60)，這就像是`List.iter`不同之處在於每個項目的索引傳遞做為對於每個項目，呼叫的函式的引數及[List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c)，這是結合的功能`List.iter2`和`List.iteri`。 下列程式碼範例會示範這些函數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

其輸出如下：

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

另一個常用的函式轉換 list 元素是[List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)，可讓您將函數套用至清單的每個項目，並將所有結果都放入新的清單。 [List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57)並[List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8)是接受多個 list 的變化。 您也可以使用[List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14)並[List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49)，如果除了項目，此函式需要傳遞每個項目的索引。 `List.mapi2` 與 `List.mapi` 的唯一差別在於 `List.mapi2` 可與兩個 list 搭配使用。 下列範例說明[List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

其輸出如下：

```
[2; 3; 4]
```

下列範例示範 `List.map2` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

其輸出如下：

```
[5; 7; 9]
```

下列範例示範 `List.map3` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

其輸出如下：

```
[7; 10; 13]
```

下列範例示範 `List.mapi` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

其輸出如下：

```
[1; 3; 5]
```

下列範例示範 `List.mapi2` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

其輸出如下：

```
[0; 7; 18]
```

[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f)就像是`List.map`，差異在於每個項目會產生的清單，且所有 list 會都串連成最終的 list。 在下列程式碼中，list 的每個元素都會產生三個數字。 所有數字都會收集到一個 list 中。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

其輸出如下：

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

您也可以使用[List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248)，其會採用布林條件，並產生新的清單，其中只包含符合指定的條件的項目。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

所得 list 為 `[2; 4; 6]`。

對應和篩選的組合[List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d)可讓您同時轉換及選取項目在相同的時間。 `List.choose` 會套用可以傳回選項給每個 list 元素的函式，並會在函式傳回選項值 `Some` 時，為元素傳回新的結果清單。

下列程式碼示範如何使用 `List.choose` 選取不在單字清單內的大寫單字。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

其輸出如下：

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>多個 List 的運算

多個 list 可以相互結合。 若要將兩個 list 合而為一，使用[List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426)。 若要加入兩個以上的清單，請使用[List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Fold 與 Scan 運算

有些 list 運算涉及所有 list 元素間彼此的相依性。 Fold 與 scan 運算就像是`List.iter`並`List.map`在於您叫用每個項目，函式，但這些作業提供額外的參數呼叫*累加*，實現資訊在計算中。

使用 `List.fold` 對 list 執行運算。

下列程式碼範例示範如何使用[List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0)來執行各種作業。

清單會經過周遊；accumulator `acc` 一值會隨著運算進行而傳遞。 第一個引數在接受 accumulator 及 list 元素之後，會傳回 list 元素的暫時結果。 第二個引數是 accumulator 的初始值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

這些函式若對多個 list 執行，函式名稱中會有一位數字記錄其版本。 例如， [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343)對兩個 list 執行運算。

下列範例示範 `List.fold2` 的用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold` 並[List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8)的差異在於，`List.fold`傳回最後的值的額外的參數，但`List.scan`傳回額外的參數 （以及最終的值） 的中間值的清單。

所有這些函式都會包含一個反向的變化，例如[List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7)，其不同的順序，在其中周遊 list 和引數的順序。 此外，`List.fold`並`List.foldBack`會有變化， [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343)並[List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2)，可接受兩個長度相同。 對每個元素執行的函式，皆可使用兩個 list 的對應元素執行特定動作。 如下列範例所示，兩個 list 的元素類型可以不同，其中一個 list 包含銀行帳戶的異動金額，另一個 list 則包含異動的類型 (存款或提款)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

對於加總這類運算，因為 `List.fold` 與 `List.foldBack` 的結果與周遊順序無關，所以兩者的效果相同。 在下列範例中，`List.foldBack` 會用於新增 list 中的元素。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

下列範例會回到銀行帳戶範例。 這次會新增「利息運算」異動類型。 最終結餘取決於異動的順序。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

函式[List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b)有點像`List.fold`並`List.scan`，不過個別的 accumulator，而`List.reduce`會接受項目型別，而不是兩個引數的函式只是一個，而這些引數的另一個做為 accumulator，亦即會儲存中繼計算結果。 `List.reduce` 會從運算頭兩個 list 元素開始，然後再並用運算結果與下一個元素。 因為沒有任何具有專屬類型的 accumulator，所以可以使用 `List.reduce` 取代 `List.fold`，但前提是 accumulator 與元素類型必須屬於相同類型。 下列程式碼示範 `List.reduce` 的用法。 若提供的 list 不含任何元素，`List.reduce` 會擲出例外狀況。

在下列程式碼中，第一個 Lambda 運算式呼叫的引數設定為 2 與 4，並傳回 6；下一個呼叫的引數設定為 6 與 10，所以結果為 16。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>List 與其他收集類型的相互轉換

`List` 模組提供可以讓 sequence 與 array 相互轉換的函式。 若要將轉換至或從序列，請使用[List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0)或是[List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0)。 若要從陣列的來回轉換，請使用[List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547)或是[List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032)。

### <a name="additional-operations"></a>其他運算

如需其他 list 運算的資訊，請參閱程式庫參考主題[Collections.List 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [F# 類型](fsharp-types.md)
- [序列](sequences.md)
- [陣列](arrays.md)
- [選項](options.md)
