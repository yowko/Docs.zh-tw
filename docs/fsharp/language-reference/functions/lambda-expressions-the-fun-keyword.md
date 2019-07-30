---
title: Lambda 運算式:有趣的關鍵字
description: 瞭解如何使用F# ' 趣味 ' 關鍵字來定義 lambda 運算式, 這是匿名函式。
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630671"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Lambda 運算式:有趣的關鍵字 (F#)

`fun`關鍵字是用來定義 lambda 運算式, 也就是匿名函式。

## <a name="syntax"></a>語法

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>備註

*參數清單*通常包含名稱和選擇性的參數類型。 更常見的情況是,*參數清單*可以由任何F#模式組成。 如需可能模式的完整清單, 請參閱[模式](../pattern-matching.md)比對。 有效參數的清單包含下列範例。

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

*運算式*是函式的主體, 最後一個運算式會產生傳回值。 有效 lambda 運算式的範例包括下列各項:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>使用 Lambda 運算式

當您想要對清單或其他集合執行作業, 而且想要避免定義函數的額外工作時, Lambda 運算式特別有用。 許多F#程式庫函式會採用函式值做為引數, 在這些情況下使用 lambda 運算式會特別方便。 下列程式碼會將 lambda 運算式套用至清單的元素。 在此情況下, 匿名函式會將1新增至清單的每個元素。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>另請參閱

- [函式](index.md)
