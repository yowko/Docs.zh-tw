---
title: "例外狀況：invalidArg 函式 (F#)"
description: "了解如何 F # 'invalidArg' 函式會產生引數例外狀況。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d375b704-6b27-493e-bd1d-ee217a53c4b5
ms.openlocfilehash: 107bef361a6bd034e3d6a2227e18cf64b1b04576
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-invalidarg-function"></a>例外狀況：invalidArg 函式

`invalidArg`函式會產生引數例外狀況。


## <a name="syntax"></a>語法

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>備註
先前語法中的參數名稱為其引數不正確的參數名稱的字串。 *錯誤訊息字串*是常值字串，或是類型的值`string`。 它會變成`Message`例外狀況物件的屬性。

產生的例外狀況`invalidArg`是`System.ArgumentException`例外狀況。 下列程式碼說明如何使用`invalidArg`擲回例外狀況。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

輸出是下列項目，後面接著 （未顯示） 的堆疊追蹤。

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>另請參閱
[例外狀況處理](index.md)

[例外狀況類型](exception-types.md)

[例外狀況：`try...with` 運算式](the-try-with-expression.md)

[例外狀況：`try...finally` 運算式](the-try-finally-expression.md)

[例外狀況：`raise` 函式](the-raise-function.md)

[例外狀況：`failwith` 函式](the-failwith-function.md)
