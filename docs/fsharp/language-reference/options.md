---
title: 選項。
description: '瞭解當命名值或變數的實際值可能不存在時，如何使用 F # 選項類型。'
ms.date: 08/13/2020
ms.openlocfilehash: 0618590c10f6ecac51a23483ca0ab6cd66f2df4f
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557564"
---
# <a name="options"></a>選項。

當命名值或變數的實際值可能不存在時，就會使用 F # 中的選項類型。 選項具有基礎類型，而且可以保存該類型的值，或可能沒有值。

## <a name="remarks"></a>備註

下列程式碼說明產生選項類型的函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

您可以看到，如果輸入 `a` 大於0， `Some(a)` 就會產生。  否則， `None` 就會產生。

`None`當某個選項沒有實際值時，就會使用此值。 否則，運算式會 `Some( ... )` 為選項提供值。 值 `Some` 和在 `None` 模式比對中很有用，如下列函式所示 `exists` ， `true` 如果選項有值，則傳回， `false` 如果沒有，則會傳回。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>使用選項

當搜尋不會傳回相符的結果時，通常會使用選項，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

在先前的程式碼中，會以遞迴方式搜尋清單。 函式 `tryFindMatch` 會採用會傳回布林值的述詞函式 `pred` ，以及要搜尋的清單。 如果找到滿足述詞的元素，遞迴就會結束，而且函數會傳回值做為運算式中的選項 `Some(head)` 。 當空白清單相符時，遞迴就會結束。 在該時間點 `head` ，找不到值，而且 `None` 會傳回。

許多 F # 程式庫函式會在集合中搜尋可能存在或可能不存在的值，以傳回 `option` 型別。 依照慣例，這些函數會以前置詞開頭 `try` ，例如 [`Seq.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFindIndex) 。

當值可能不存在時，選項可能也很有用，例如，當您嘗試建立值時，可能會擲回例外狀況。 下列程式碼範例會說明這點。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile`上一個範例中的函式有型別， `string -> File option` 因為 `File` 如果成功開啟檔案，且發生例外狀況，則會傳回物件 `None` 。 根據情況而定，它可能不是攔截例外狀況的適當設計選項，而不是允許它傳播。

此外，您仍然可以傳遞 `null` 或值為 null 的值，以作為 `Some` 選項的大小寫。 這通常是要避免的，通常是在一般 F # 程式設計中，但由於 .NET 中的參考型別本質的緣故，因此可能會發生這種情況。

## <a name="option-properties-and-methods"></a>選項屬性和方法

選項類型支援下列屬性和方法。

|屬性或方法|類型|描述|
|------------------|----|-----------|
|[None](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#None)|`'T option`|靜態屬性，可讓您建立具有值的選項值 `None` 。|
|[IsNone](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#IsNone)|`bool`|`true`如果選項具有值，則傳回 `None` 。|
|[IsSome](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#IsSome)|`bool`|`true`如果選項的值不是，則會傳回 `None` 。|
|[一些](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#Some)|`'T option`|靜態成員，它會建立一個值不是的選項 `None` 。|
|[ReplTest1](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#Value)|`'T`|傳回基礎值， `System.NullReferenceException` 如果值為，則會擲回 `None` 。|

## <a name="option-module"></a>選項模組

有一個模組 [選項](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html)，它包含對選項執行作業的實用函式。 某些函式會重複屬性的功能，但在需要函式的內容中很有用。 [IsSome](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#isSome) 和 [isNone](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#isNone) 都是可測試選項是否保留值的模組函數。 [選項。 get 會取得](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#get) 值（如果有的話）。 如果沒有任何值，則會擲回 `System.ArgumentException` 。

如果有值，則 [bind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#bind) 函式會在值上執行函數。 函數必須正好採用一個引數，而且其參數類型必須是選項類型。 函數的傳回值是另一個選項類型。

選項模組也包含對應至可供清單、陣列、序列和其他集合類型使用之函數的函式。 這些函數包括 [`Option.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#map) 、 [`Option.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#iter) 、 [`Option.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#forall) 、 [`Option.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#exists) 、 [`Option.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#foldBack) 、 [`Option.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#fold) 和 [`Option.count`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#count) 。 這些函數可讓您使用選項，就像是零或一個專案的集合。 如需詳細資訊和範例，請參閱 [清單](lists.md)中的集合函數討論。

## <a name="converting-to-other-types"></a>轉換成其他類型

選項可以轉換成清單或陣列。 當某個選項轉換成其中一個資料結構時，產生的資料結構會有零個或一個元素。 若要將選項轉換成陣列，請使用 [`Option.toArray`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#toArray) 。 若要將選項轉換成清單，請使用 [`Option.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#toList) 。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [F# 類型](fsharp-types.md)
