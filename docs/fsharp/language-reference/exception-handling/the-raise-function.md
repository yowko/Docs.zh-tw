---
title: 例外狀況：raise 函式
description: 瞭解「引發F# 」函數如何用來表示發生錯誤或例外狀況。
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630283"
---
# <a name="exceptions-the-raise-function"></a>例外狀況：raise 函式

`raise`函數是用來表示發生錯誤或例外狀況。 錯誤的相關資訊會在例外狀況物件中捕捉。

## <a name="syntax"></a>語法

```fsharp
raise (expression)
```

## <a name="remarks"></a>備註

`raise`函式會產生例外狀況物件, 並起始堆疊回溯進程。 堆疊回溯程式是由 common language runtime (CLR) 所管理, 因此此進程的行為與任何其他 .NET 語言相同。 堆疊回溯程式是搜尋符合所產生之例外狀況的例外狀況處理常式。 搜尋會從目前`try...with`的運算式開始 (如果有的話)。 區塊中的`with`每個模式會依序進行檢查。 找到相符的例外狀況處理常式時, 會將例外狀況視為已處理;否則, 會先展開堆疊並`with`封鎖呼叫鏈, 直到找到相符的處理常式為止。 當`finally`堆疊回溯時, 在呼叫鏈中遇到的任何區塊也會依序執行。

函數等同于或C++中的C# `throw` `raise` 在`reraise` catch 處理常式中使用, 將相同的例外狀況向上傳播至呼叫鏈。

下列程式碼範例說明如何使用`raise`函數來產生例外狀況。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise`函數也可以用來引發 .net 例外狀況, 如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況類型](exception-types.md)
- [例外狀況：`try...with`運算式](the-try-with-expression.md)
- [例外狀況：`try...finally`運算式](the-try-finally-expression.md)
- [例外狀況：`failwith`函式](the-failwith-function.md)
- [例外狀況：`invalidArg`函式](the-invalidArg-function.md)
