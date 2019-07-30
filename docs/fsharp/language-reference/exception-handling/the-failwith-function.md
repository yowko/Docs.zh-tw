---
title: 例外狀況：Failwith 函式
description: 瞭解 ' failwith ' 函數如何產生F#例外狀況。
ms.date: 05/16/2016
ms.openlocfilehash: f2c86362d5bdde7bab55751f019965a5f4ca6236
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630333"
---
# <a name="exceptions-the-failwith-function"></a>例外狀況：Failwith 函式

函式F#會產生例外狀況。 `failwith`

## <a name="syntax"></a>語法

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>備註

前述語法中的*錯誤訊息字串*為常值字串或類型`string`的值。 它會成為`Message`例外狀況的屬性。

所產生`failwith`的例外狀況`System.Exception`是例外狀況, 這是在程式碼中`Failure` F#具有名稱的參考。 下列程式碼說明`failwith`如何使用來擲回例外狀況。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況類型](exception-types.md)
- [例外狀況：`try...with`運算式](the-try-with-expression.md)
- [例外狀況：`try...finally`運算式](the-try-finally-expression.md)
- [例外狀況：`raise` 函式](the-raise-function.md)
