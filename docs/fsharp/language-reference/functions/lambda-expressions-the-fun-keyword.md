---
title: "Lambda 運算式：fun 關鍵字 (F#)"
description: "了解如何使用 F # 'fun' 關鍵字來定義 lambda 運算式，這是匿名函式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e5d3565c-d7cc-433f-a619-886ed92523a7
ms.openlocfilehash: 09f1c1787bbb4b86ec40f9e973e08104919631aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Lambda 運算式：fun 關鍵字 (F#)

`fun`關鍵字用來定義 lambda 運算式，也就是匿名函式。


## <a name="syntax"></a>語法

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>備註
*參數清單*通常包含名稱和 （選擇性） 參數的型別。 較常見地，*參數清單*可以是任何 F # 模式所組成。 如需可能模式的完整清單，請參閱[模式比對](../pattern-matching.md)。 有效參數清單都包含下列的範例。

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

*運算式*是函式，其中在最後一個運算式會產生傳回值的主體。 有效的 lambda 運算式的範例包括：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a>使用 Lambda 運算式
當您想要在清單或另一個集合上執行作業，而且想要避免額外的工作定義函式的 lambda 運算式時特別有用的。 許多 F # 程式庫函式會接受做為引數，函式值，可以使用 lambda 運算式，在這些情況下特別方便。 下列程式碼將 lambda 運算式套用至清單的元素。 在此情況下，匿名函式會將 1 加入至清單的每個項目。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a>另請參閱
[函式](index.md)
