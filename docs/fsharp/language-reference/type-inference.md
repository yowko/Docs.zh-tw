---
title: 類型推斷
description: 瞭解F#編譯器如何推斷值、變數、參數和傳回值的類型。
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630190"
---
# <a name="type-inference"></a>類型推斷

本主題描述F#編譯器如何推斷值、變數、參數和傳回值的類型。

## <a name="type-inference-in-general"></a>一般型別推斷

類型推斷的概念是, 您不需要指定F#結構的類型, 除非編譯器無法最終推算類型。 省略明確類型資訊並不表示是F#動態類型的語言, 或中F#的值是弱式類型。 F#是靜態類型語言, 這表示編譯器會在編譯期間會推算每個結構的確切類型。 如果沒有足夠的資訊可讓編譯器推算出每個結構的類型, 您就必須提供額外的類型資訊, 通常是在程式碼中的某處新增明確的類型注釋。

## <a name="inference-of-parameter-and-return-types"></a>參數和傳回類型的推斷

在參數清單中, 您不需要指定每個參數的類型。 此外, F#是靜態類型的語言, 因此每個值和運算式在編譯時期都有一個明確的類型。 針對您未明確指定的類型, 編譯器會根據內容來推斷類型。 如果未另行指定類型, 則會將它推斷為泛型。 如果程式碼以不一致的方式使用值, 在這種情況下, 如果沒有任何單一推斷類型滿足值的所有使用, 編譯器就會報告錯誤。

函式的傳回型別是由函式中最後一個運算式的型別所決定。

例如, 在下列程式碼中, 參數類型`a`和`b`和傳回類型`int`都會推斷為, 因為常`100`值的類型`int`為。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

您可以藉由變更常值來影響型別推斷。 如果您藉`uint32`由`100` `u`附加`b`尾碼來`uint32`建立, 則會將、和傳回值的類型推斷為。`a`

您也可以使用其他表示類型限制的結構 (例如僅適用于特定類型的函數和方法), 來影響型別推斷。

此外, 您可以將明確類型注釋套用至函式或方法參數或運算式中的變數, 如下列範例所示。 如果在不同的條件約束之間發生衝突, 則會產生錯誤。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

您也可以在所有參數之後提供類型注釋, 以明確指定函式的傳回值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

類型注釋對參數很有用的常見情況是, 當參數是物件類型, 而您想要使用成員時。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>自動一般化

如果函式程式碼不相依于參數的類型, 則編譯器會將參數視為泛型。 這稱為「*自動一般化*」, 它可以是在不增加複雜度的情況下撰寫一般程式碼的強大輔助工具。

例如, 下列函式會將任何類型的兩個參數結合成一個元組。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

類型會推斷為

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>其他資訊

類型推斷會在F#語言規格中以更詳細的方式加以描述。

## <a name="see-also"></a>另請參閱

- [自動一般化](./generics/automatic-generalization.md)
