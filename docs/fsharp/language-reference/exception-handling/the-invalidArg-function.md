---
title: 例外狀況：InvalidArg 函式
description: 瞭解F# ' invalidArg ' 函數如何產生引數例外狀況。
ms.date: 05/16/2016
ms.openlocfilehash: 6b1c5fdb5a541da336977d3a67d471302edb36b6
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083017"
---
# <a name="exceptions-the-invalidarg-function"></a>例外狀況：InvalidArg 函式

`invalidArg`函式會產生引數例外狀況。

## <a name="syntax"></a>語法

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>備註

先前語法中的參數名稱是字串，其引數名稱無效。 *錯誤訊息字串*是文字字串或類型`string`的值。 它會成為`Message` exception 物件的屬性。

所產生`invalidArg`的例外狀況`System.ArgumentException`是例外狀況。 下列程式碼說明`invalidArg`如何使用來擲回例外狀況。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

輸出如下所示，後面接著堆疊追蹤（未顯示）。

```console
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
