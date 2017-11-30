---
title: "類型推斷 (F#)"
description: "了解 F # 編譯器推斷類型的值、 變數、 參數和傳回值的方式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2d5fa4b1-732a-4d71-a62d-07f7ee79fe06
ms.openlocfilehash: c23954c0a0828cc7d2aae0553d37d5ee1dfbe152
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="type-inference"></a>類型推斷

本主題描述如何在 F # 編譯器會推斷值、 變數、 參數和傳回值的類型。

## <a name="type-inference-in-general"></a>一般類型推斷
型別推斷概念是，您不需要指定 F # 以外時，編譯器無法做出推算的類型建構的類型。 省略明確的型別資訊並不表示 F # 是動態類型的語言，或 F # 中的值是弱型別。 F # 是靜態類型的語言，這表示，編譯器會推算的確切每個建構類型，在編譯期間。 如果沒有足夠的資訊讓編譯器推斷每個建構類型，您必須在程式碼中某處加入明確的型別註解通常提供其他類型資訊。


## <a name="inference-of-parameter-and-return-types"></a>參數和傳回型別推斷
在參數清單中，您不必指定每個參數的型別。 和棒的是，F # 是靜態類型的語言，因此每個值與運算式具有明確類型在編譯時間。 針對未明確指定的類型，編譯器會推斷內容為基礎的類型。 如果類型不是其他指定，它會推斷為泛型。 如果程式碼會使用值不一致，這類方式沒有任何單一推斷滿足使用的所有值，編譯器會報告錯誤的類型。

函式的傳回型別取決於函式中的最後一個運算式的類型。

例如，在下列程式碼的參數型別`a`和`b`和傳回型別會推斷為`int`因為常值`100`的型別`int`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

您可以藉由變更常值會影響型別推斷。 如果您進行`100``uint32`藉由附加後置詞`u`，類型的`a`， `b`，並傳回值會被推斷為`uint32`。

您可能也會影響使用的其他建構隱含限制的類型，例如函式和方法可搭配特定類型的型別推斷。

此外，您可以套用明確的類型註釋函式或方法參數或變數在運算式中，如下列範例所示。 不同的條件約束之間發生衝突時，就會產生錯誤。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

您可以同時也可以明確指定函式的傳回值，藉由在所有參數提供型別附註。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

常見的案例，其中類型註釋是有用的參數時，參數是物件類型，而且您想要使用的成員。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a>自動一般化
如果函式程式碼不是參數的類型而定，編譯器會考慮泛型參數。 這稱為*自動一般化*，而且它可以是功能強大的輔助工具，而不會增加複雜性撰寫泛型的程式碼。

例如，下列函式結合成一個 tuple 的任何類型的兩個參數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

被推斷的類型

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>其他資訊
F # 語言規格中的更詳細地描述型別推斷。


## <a name="see-also"></a>另請參閱
[自動一般化](generics/automatic-generalization.md)
