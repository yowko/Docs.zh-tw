---
title: "例外狀況：failwith 函式 (F#)"
description: "了解如何 'failwith' 函式會產生 F # 例外狀況。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2e0c1f28-cc6c-4ecd-bb93-3816c4dd7cd3
ms.openlocfilehash: 295a4d754e0df015ba67daa9cf80d7df5b40199c
ms.sourcegitcommit: ffb9aa26cd5211dc6d96ebb42968d8357048880e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="exceptions-the-failwith-function"></a>例外狀況：failwith 函式

`failwith`函式會產生 F # 例外狀況。


## <a name="syntax"></a>語法

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>備註
*錯誤訊息字串*先前語法中是字串常值或值型別的`string`。 它會變成`Message`例外狀況的屬性。

所產生的例外狀況`failwith`是`System.Exception`例外狀況，也就是具有名稱的參考`Failure`F # 程式碼中。 下列程式碼說明如何使用`failwith`擲回例外狀況。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]
    
## <a name="see-also"></a>另請參閱
[例外狀況處理](index.md)

[例外狀況類型](exception-types.md)

[例外狀況：`try...with` 運算式](the-try-with-expression.md)

[例外狀況：`try...finally` 運算式](the-try-finally-expression.md)

[例外狀況：`raise` 函式](the-raise-function.md)
