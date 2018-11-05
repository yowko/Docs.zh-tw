---
title: 類型推斷 (F#)
description: 了解 F# 編譯器如何推斷值、 變數、 參數和傳回值的類型。
ms.date: 05/16/2016
ms.openlocfilehash: fd826ac48fb9a70aa6f4ff746599c11b7e21a02e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865692"
---
# <a name="type-inference"></a>類型推斷

本主題描述如何在 F# 編譯器會推斷值、 變數、 參數和傳回值的類型。

## <a name="type-inference-in-general"></a>一般型別推斷

型別推斷的概念是您沒有指定類型的 F# 建構，但當編譯器無法確定推算的類型。 省略明確的類型資訊並不表示 F# 是動態類型的語言，或在 F# 中的值是弱型別。 F# 是靜態類型的語言，這表示編譯器會推斷每個建構的確實型別，在編譯期間。 如果沒有足夠的資訊讓編譯器推斷每個建構的類型，您必須藉由在程式碼中某處新增明確的型別註解通常提供額外的類型資訊。

## <a name="inference-of-parameter-and-return-types"></a>參數和傳回型別推斷

在參數清單中，您不必指定每個參數的型別。 是，F# 是靜態類型的語言，並因此每個值與運算式有明確的類型在編譯時期。 對於您未明確指定這些型別，編譯器會推斷內容為基礎的類型。 如果類型不是其他方式指定，它會推斷為泛型。 如果程式碼會使用值不一致，一種都不是單一推斷符合定義之值的所有使用編譯器報告錯誤的類型。

函式的傳回型別取決於函式中的最後一個運算式的類型。

例如，在下列程式碼的參數型別`a`並`b`和傳回型別會推斷為`int`因為常值`100`屬於類型`int`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

您可以藉由變更的常值會影響型別推斷。 若要`100``uint32`附加後置詞`u`，種`a`， `b`，並傳回值會被推斷為`uint32`。

您也可以影響使用隱含的類型，例如函式和方法可搭配特定類型的限制的其他建構型別推斷。

此外，您可以套用明確的型別註釋函式或方法參數或變數在運算式中，如下列範例所示。 如果不同的條件約束之間發生衝突，就會產生錯誤。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

您也可以明確指定函式的傳回值所提供的型別註釋在所有的參數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

參數是物件類型，且您想要使用的成員時，型別註釋會在參數上很實用的常見案例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>自動一般化

如果函式程式碼不相依於參數的型別，則編譯器會考慮為泛型參數。 這就叫做*自動一般化*，它可以是功能強大的輔助工具，來撰寫泛型程式碼，而不會增加複雜度。

例如，下列函式結合兩個參數轉換為 tuple 的任何類型。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

型別推斷為

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>其他資訊

型別推斷在 F# 語言規格中詳細說明。

## <a name="see-also"></a>另請參閱

- [自動一般化](generics/automatic-generalization.md)
