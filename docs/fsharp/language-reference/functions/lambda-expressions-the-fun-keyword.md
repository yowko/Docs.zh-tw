---
title: Lambda 運算式：fun 關鍵字 (F#)
description: "了解如何使用 F # '好玩 」 關鍵字來定義 lambda 運算式，這是匿名函式。"
ms.date: 05/16/2016
ms.openlocfilehash: a37757f6b7328cd348bbf13f058a6dbc881769cf
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080169"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Lambda 運算式：fun 關鍵字 (F#)

`fun`關鍵字用以定義 lambda 運算式，也就是匿名函式。

## <a name="syntax"></a>語法

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>備註

*參數清單*通常是由名稱和 （選擇性） 參數的型別所組成。 更廣泛地*參數清單*可以包含任何的 F # 模式。 可能的模式的完整清單，請參閱 <<c0> [ 模式比對](../pattern-matching.md)。 有效的參數清單包含下列的範例。

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

*運算式*是函式，其中的最後一個運算式會產生傳回值的主體。 有效的 lambda 運算式的範例包括：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>使用 Lambda 運算式

當您想要在清單或另一個集合上執行作業，而且想要避免額外的工作定義的函式，lambda 運算式是特別有用。 許多 F # 程式庫函式會採用做為引數，函式值，可以使用 lambda 運算式，在這些情況下特別方便。 下列程式碼將 lambda 運算式套用至項目清單。 在此情況下，匿名函式會將 1 加入至清單的每個項目。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>另請參閱

- [函式](index.md)
