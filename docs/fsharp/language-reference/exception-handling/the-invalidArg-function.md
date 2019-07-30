---
title: 例外狀況：InvalidArg 函式
description: 瞭解F# ' invalidArg ' 函數如何產生引數例外狀況。
ms.date: 05/16/2016
ms.openlocfilehash: 010dbfe313f539093b4ee7a19984ef54500b072d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630301"
---
# <a name="exceptions-the-invalidarg-function"></a>例外狀況：InvalidArg 函式

`invalidArg`函式會產生引數例外狀況。

## <a name="syntax"></a>語法

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>備註

先前語法中的參數名稱是字串, 其引數名稱無效。 *錯誤訊息字串*是文字字串或類型`string`的值。 它會成為`Message` exception 物件的屬性。

所產生`invalidArg`的例外狀況`System.ArgumentException`是例外狀況。 下列程式碼說明`invalidArg`如何使用來擲回例外狀況。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

輸出如下所示, 後面接著堆疊追蹤 (未顯示)。

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況類型](exception-types.md)
- [例外狀況：`try...with`運算式](the-try-with-expression.md)
- [例外狀況：`try...finally`運算式](the-try-finally-expression.md)
- [例外狀況：`raise` 函式](the-raise-function.md)
- [例外狀況：`failwith`函式](the-failwith-function.md)
