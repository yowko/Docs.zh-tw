---
title: Lambda 運算式：Fun 關鍵字
description: 了解如何使用F#'有趣' 關鍵字定義 lambda 運算式，這是匿名函式。
ms.date: 05/16/2016
ms.openlocfilehash: 6ad15173bb8643bff330e3ca3823cba5d43ad445
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941020"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Lambda 運算式：Fun 關鍵字 (F#)

`fun`關鍵字用以定義 lambda 運算式，也就是匿名函式。

## <a name="syntax"></a>語法

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>備註

*參數清單*通常是由名稱和 （選擇性） 參數的型別所組成。 更廣泛地*參數清單*可以包含任何F#模式。 可能的模式的完整清單，請參閱 <<c0> [ 模式比對](../pattern-matching.md)。 有效的參數清單包含下列的範例。

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

當您想要在清單或另一個集合上執行作業，而且想要避免額外的工作定義的函式，lambda 運算式是特別有用。 許多F#程式庫函式會採用函式值，做為引數，而且您可以使用 lambda 運算式，在這些情況下特別方便。 下列程式碼將 lambda 運算式套用至項目清單。 在此情況下，匿名函式會將 1 加入至清單的每個項目。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>另請參閱

- [函式](index.md)