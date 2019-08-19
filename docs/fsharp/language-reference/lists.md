---
title: 清單
description: 瞭解F#清單, 這是一系列相同類型的已排序、不可變的元素。
ms.date: 05/16/2016
ms.openlocfilehash: e8c4a464306cfedfd36a4685507684d3a1a97a2e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630737"
---
# <a name="lists"></a>清單

> [!NOTE]
> 本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

在 F# 中，list 是包含一系列經過排序且類型相同的固定元素。 若要對清單執行基本作業, 請使用[清單模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)中的函數。

## <a name="creating-and-initializing-lists"></a>建立及初始化 list

您可以藉由明確列出元素 (以逗號分隔並括以方括號) 來定義 list，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

您也可以在元素之間加入分行符號；若您選擇加入分行符號，就不一定需要使用分號。 當元素初始化運算式比較長，或當您想要為每個元素加入逗號時，以後一種語法編寫的程式碼會比較容易閱讀。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

通常 list 的所有元素都應必須是同一類型。 但當 list 指定的元素具有衍生類型的基底類型時，就不在此限。 下列的 `Button` 與 `CheckBox` 因為都是從 `Control` 衍生而來，所以可接受。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

如下列程式碼所示，您也可以使用以整數指定的範圍 (以範圍運算子 `..` 分隔) 來定義 list 元素。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

空 list 由不含任何內容的一對方括號指定。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

您也可以使用順序運算式建立 list。 如需詳細資訊, 請參閱[序列運算式](sequences.md#sequence-expressions)。 例如下列程式碼會建立從 1 到 10 之整數平方的 list。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>使用 list 的運算子

您可以使用 `::` (cons) 運算子。 若 `list1` 為 `[2; 3; 4]`，下列程式碼將 `list2` 建立為 `[100; 2; 3; 4]`。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

您可以使用 `@` 運算子串流具有相容類型的 list，如下列程式碼所示。 當 `list1` 為 `[2; 3; 4]` 及 `list2` 為 `[100; 2; 3; 4]` 時，此程式碼會將 `list3` 建立為 `[2; 3; 4; 100; 2; 3; 4]`。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

[清單模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)中提供了在清單上執行作業的功能。

由於 F# 中的 list 為固定，因此任何修改作業都會產生新的 list，而不會修改現有的 list。

中F#的清單會實作為單向連結清單, 這表示只存取清單標頭的作業是 o (1), 而元素存取是 o (*n*)。

## <a name="properties"></a>屬性

list 類型支援下列屬性：

|屬性|類型|描述|
|--------|----|-----------|
|[前端](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|第一個元素。|
|[空](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|此為靜態屬性，會傳回適當類型的空 list。|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true` 表示 list 不含任何元素。|
|[Item](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|使用位於指定索引的元素 (以零為基底)。|
|[長度](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|元素數。|
|[尾](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|list 沒有第一個元素。|

下列是使用這些屬性的一些範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>使用 list

使用 list 編寫程式讓您只需要編寫小量的程式碼，就可以執行複雜的運算。 本節說明一些使用函式編寫程式時不可或缺的常用 list 運算。

### <a name="recursion-with-lists"></a>list 的遞迴功能

list 是唯一適合遞迴程式設計技巧的函式。 假設有一項作業必須對 list 的每個元素執行。 您可以利用遞迴方式執行此作業，方法是先對 list 的 head 執行運算，再傳遞 list 的 tail (此 list 只含原始 list，而不含第一個元素，所以比較小)，然後再執行下一個遞迴層級的程式碼。

若要編寫這類遞迴函式，可以在模式比對中使用 cons 運算子 (`::`)，以區分 list 的 head 與 tail。

下列程式碼範例示範如何使用模式比對，實作執行 list 運算的遞迴函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

前述程式碼對於小型 list 的效果很好，但對於大型的 list，可能會發生堆疊溢位。 下列程式碼是前述程式碼的改良版，運用了遞迴函式標準技巧中的 accumulator 引數。 使用 accumulator 引數可以遞迴函式的 tail，進而達到節省空間的目的。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

函式 `RemoveAllMultiples` 為遞迴函式，可接受兩個 list。 第一個 list 包含倍數要移除的數字；第二個 list 是數字要移除的 list。 下列範例會使用此遞迴函式消除 list 中的所有非質數，而只保留質數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

其輸出如下：

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>模組函式

[List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)提供可存取清單元素的函式。 head 元素是最方便存取的元素。 使用屬性[標頭](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)或模組函數[清單. head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2)。 您可以使用[tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)屬性或[list. tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601)函數來存取清單的結尾。 若要依索引尋找元素, 請使用[List. n](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1)函數。 `List.nth` 會周遊 list。 因此, 它是 O (*n*)。 若您的程式碼需要頻繁地使用 `List.nth`，您或可改用 array，而不要使用 list。 array 中的元素存取為 O(1)。

### <a name="boolean-operations-on-lists"></a>List 的布林運算

[IsEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107)函數會判斷清單是否有任何元素。

[清單 exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)函式會將布林測試套用至清單的元素, 並`true`在任何專案符合測試時傳回。 [List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e)類似, 但會在兩個清單中的後續元素配對上運作。

下列程式碼示範 `List.exists` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

其輸出如下：

```
For list [0; 1; 2; 3], contains zero is true
```

下列範例示範 `List.exists2` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

其輸出如下：

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

如果您想要測試清單中的所有元素是否符合條件, 您可以使用[forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

其輸出如下：

```
true
false
```

同樣地, [array.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e)會判斷兩個清單中對應位置的所有元素是否都符合包含每一對元素的布林運算式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

其輸出如下：

```
true
false
```

### <a name="sort-operations-on-lists"></a>List 的排序運算

[List. sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d)、 [sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)和[list.sortwith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7)函數排序清單。 排序函式可指定要使用這三個函式中的哪一個函式。 `List.sort` 會使用預設的泛型比較。 泛型比較會依不同的泛型比較函式而使用不同的全域運算子來比較值。 其可與多種元素類型搭配使用，例如簡單的數值類型、tuple、記錄、差別聯集、list、array 及所有實作 `System.IComparable` 的類型。 對於實作 `System.IComparable` 的類型，泛型比較會使用 `System.IComparable.CompareTo()` 函式。 泛型比較也會搭配字串，但會使用不涉及文化的排序順序。 請勿對不支援的類型 (例如函式類型) 使用泛型比較。 此外，預設泛型比較對小型結構類型的效能最好；若需要經常比較及排序比較大的結構類型，可考慮實作 `System.IComparable` 及佈建成效更好的 `System.IComparable.CompareTo()` 方法實作。

`List.sortBy` 可接受函式傳回的值做為排序準則；而 `List.sortWith` 可接受比較函式做為引數。 當您要使用的類型不支援比較時，或比較需要更複雜的比較語意 (例如使用涉及文化的字串) 時，即可使用後兩個函式。

下列範例示範 `List.sort` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

其輸出如下：

```
[-2; 1; 4; 5; 8]
```

下列範例示範 `List.sortBy` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

其輸出如下：

```
[1; -2; 4; 5; 8]
```

下列範例示範 `List.sortWith` 的用法。 此範例會使用自訂比較函式 `compareWidgets` 先比較自訂類型的第一個欄位，當第一個欄位的值相等時，再比較其他欄位。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

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

list 支援多種搜尋運算。 最簡單的[清單](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), 可讓您尋找符合指定條件的第一個元素。

下列程式碼範例示範如何使用 `List.find` 從 list 中尋找第一個可以被 5 整除的數字。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

The result is 5.

如果必須先轉換專案, 請呼叫[List](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), 它會採用會傳回選項的函式, 並尋找第一個選項值, 也就是`Some(x)`。 `List.pick` 不會傳回元素，而會傳回結果 `x`。 若找不到相符的元素，`List.pick` 會擲出 `System.Collections.Generic.KeyNotFoundException`。 下列程式碼示範 `List.pick` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

其輸出如下：

```
"b"
```

另一個搜尋作業群組[tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d)和相關函式會傳回選項值。 `List.tryFind` 函式會傳回 list 中第一個滿足條件的元素 (如其存在)；若找不到，即會傳回選項值 `None`。 [Array.tryfindindex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec)會傳回專案的索引 (如果找到的話), 而不是元素本身。 下列程式碼是這些函式的示範。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

其輸出如下：

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>List 的算術運算

[清單模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)內建常見的算數運算, 例如 sum 和 average。 若要使用[list. sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), list 元素類型必須支援`+`運算子, 且值為零。 所有內建算術類型皆滿足這些條件。 若要使用[List. average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), 元素類型必須支援不含餘數的除法, 這會排除整數類型, 但允許浮點類型。 [SumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d)和[averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403)函式會採用函式做為參數, 並使用此函數的結果來計算總和或平均值的值。

下列程式碼示範 `List.sum`、`List.sumBy` 及 `List.average` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

輸出為 `1.000000`。

下列程式碼示範 `List.averageBy` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

輸出為 `5.5`。

### <a name="lists-and-tuples"></a>List 與 Tuple

zip 及 unzip 函式可以操作包含 tuple 的 list。 這些函式會將各自包含一個值的兩個 list 合併成一份元組清單，或將一份元組清單分割成兩個只含單一值的 list。 最簡單的[清單 .zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c)函式會採用兩個單一專案清單, 並產生一組成對的元組。 另一個版本[list.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b)會接受單一專案的三個清單, 並產生具有三個元素的單一元組清單。 下列程式碼範例示範 `List.zip` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

其輸出如下：

```
[(1, -1); (2, -2); (3; -3)]
```

下列程式碼範例示範 `List.zip3` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

其輸出如下：

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

對應的解壓縮版本 list.unzip3、[清單解壓縮](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)和[列出](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)元組中的元組和傳回清單, 其中第一個清單會包含每個元組中第一個專案的所有專案, 而第二個清單則包含每個的第二個元素。元組等等。

下列程式碼範例示範如何使用[List. 解壓縮](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

其輸出如下：

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

下列程式碼範例示範如何使用[list.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

其輸出如下：

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>List 元素的運算

F# 支援多種 list 元素運算。 最簡單的是[iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), 可讓您在清單的每個元素上呼叫函式。 變化包括[array.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), 可讓您在兩個清單的專案上執行作業, [list.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), 這類似`List.iter` , 不同之處在于每個元素的索引都會當做引數傳遞給每個的呼叫函式元素和[array.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), 這是`List.iter2`和`List.iteri`功能的組合。 下列程式碼範例會示範這些函數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

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

轉換清單元素的另一個常用函式是 [[清單](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)], 可讓您將函式套用至清單的每個元素, 並將所有的結果放入新的清單中。 [List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57)和[list. list.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8)是採用多個清單的變化。 您也可以使用 [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) 和 [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), 如果除了元素之外, 還必須傳遞每個專案的索引給函式。 `List.mapi2` 與 `List.mapi` 的唯一差別在於 `List.mapi2` 可與兩個 list 搭配使用。 下列範例說明了[清單。](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

其輸出如下：

```
[2; 3; 4]
```

下列範例示範 `List.map2` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

其輸出如下：

```
[5; 7; 9]
```

下列範例示範 `List.map3` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

其輸出如下：

```
[7; 10; 13]
```

下列範例示範 `List.mapi` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

其輸出如下：

```
[1; 3; 5]
```

下列範例示範 `List.mapi2` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

其輸出如下：

```
[0; 7; 18]
```

[List. collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f)就像`List.map`, 不同的是, 每個元素都會產生一個清單, 而所有這些清單都會串連成最後一個清單。 在下列程式碼中，list 的每個元素都會產生三個數字。 所有數字都會收集到一個 list 中。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

其輸出如下：

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

您也可以使用 [[清單] 篩選](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), 它會採用布林值條件, 並產生只包含符合指定條件之元素的新清單。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

所得 list 為 `[2; 4; 6]`。

[對應] 和 [篩選]、 [[清單](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d)] 的組合, 可讓您同時轉換及選取元素。 `List.choose` 會套用可以傳回選項給每個 list 元素的函式，並會在函式傳回選項值 `Some` 時，為元素傳回新的結果清單。

下列程式碼示範如何使用 `List.choose` 選取不在單字清單內的大寫單字。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

其輸出如下：

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>多個 List 的運算

多個 list 可以相互結合。 若要將兩個清單聯結成一個, 請使用[List. append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426)。 若要加入兩個以上的清單, 請使用[List. concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c)。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Fold 與 Scan 運算

有些 list 運算涉及所有 list 元素間彼此的相依性。 折迭和掃描工作就像`List.iter`和`List.map`在中, 您會在每個專案上叫用函式, 但這些作業會提供一個額外的參數, 稱為透過計算來攜帶資訊的*累計*。

使用 `List.fold` 對 list 執行運算。

下列程式碼範例示範如何使用[List. 折頁](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0)來執行各種作業。

清單會經過周遊；accumulator `acc` 一值會隨著運算進行而傳遞。 第一個引數在接受 accumulator 及 list 元素之後，會傳回 list 元素的暫時結果。 第二個引數是 accumulator 的初始值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

這些函式若對多個 list 執行，函式名稱中會有一位數字記錄其版本。 例如, [list.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343)會在兩個清單上執行計算。

下列範例示範 `List.fold2` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold`和 [[清單](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8)] 中的不同`List.fold` , 它會傳回額外參數的最後一個值`List.scan` , 但會傳回額外參數的中繼值清單 (以及最後的值)。

其中每個函式都包含反向變化 (例如[list.foldback](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7)), 這會依清單的進行順序和引數的順序而有所不同。 此外, `List.fold`和`List.foldBack`具有[list.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343)和[list.foldback2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2)這兩個長度相同的清單。 對每個元素執行的函式，皆可使用兩個 list 的對應元素執行特定動作。 如下列範例所示，兩個 list 的元素類型可以不同，其中一個 list 包含銀行帳戶的異動金額，另一個 list 則包含異動的類型 (存款或提款)。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

對於加總這類運算，因為 `List.fold` 與 `List.foldBack` 的結果與周遊順序無關，所以兩者的效果相同。 在下列範例中，`List.foldBack` 會用於新增 list 中的元素。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

下列範例會回到銀行帳戶範例。 這次會新增「利息運算」異動類型。 最終結餘取決於異動的順序。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

函式[清單。 [縮小](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b)] 有點`List.fold`類似`List.scan`和, 不同之處在于, 不是以個別`List.reduce`的累計方式來傳遞, 而是採用接受元素類型之兩個引數的函式, 而不是只有一個, 而是其中一個引數會當做累計, 這表示它會儲存計算的中繼結果。 `List.reduce` 會從運算頭兩個 list 元素開始，然後再並用運算結果與下一個元素。 因為沒有任何具有專屬類型的 accumulator，所以可以使用 `List.reduce` 取代 `List.fold`，但前提是 accumulator 與元素類型必須屬於相同類型。 下列程式碼示範 `List.reduce` 的用法。 若提供的 list 不含任何元素，`List.reduce` 會擲出例外狀況。

在下列程式碼中，第一個 Lambda 運算式呼叫的引數設定為 2 與 4，並傳回 6；下一個呼叫的引數設定為 6 與 10，所以結果為 16。

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>List 與其他收集類型的相互轉換

`List` 模組提供可以讓 sequence 與 array 相互轉換的函式。 若要在序列之間轉換, 請使用[list.toseq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0)或[list.ofseq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0)。 若要在陣列之間進行轉換, 請使用[toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547)或[list.ofarray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032)。

### <a name="additional-operations"></a>其他運算

如需有關清單上其他作業的詳細資訊, 請參閱程式庫參考主題[集合。清單模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [F# 類型](fsharp-types.md)
- [序列](sequences.md)
- [陣列](arrays.md)
- [選項](options.md)
