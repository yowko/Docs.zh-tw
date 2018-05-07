---
title: 例外狀況：raise 函式 (F#)
description: "了解如何使用 F # 'raise' 函式來指示已發生錯誤或例外狀況。"
ms.date: 05/16/2016
ms.openlocfilehash: bad18bfbccd738a12e16a0e026ade22e96d4cfcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-the-raise-function"></a>例外狀況：raise 函式

`raise`函數用來指示已發生錯誤或例外狀況。 例外狀況物件中擷取錯誤的相關資訊。


## <a name="syntax"></a>語法

```fsharp
raise (expression)
```

## <a name="remarks"></a>備註
`raise`函式會產生例外狀況物件，並起始堆疊回溯處理序。 堆疊回溯處理程序是由 common language runtime (CLR)，管理，使此程序的行為都相同，因為它是任何其他.NET 語言。 堆疊回溯處理序會搜尋符合產生的例外狀況的例外狀況處理常式。 搜尋會開始在目前`try...with`運算式，如果有的話。 在每個模式`with`勾選區塊，順序。 找到相符的例外狀況處理常式時，例外狀況會被視為處理;否則，回溯堆疊時，`with`呼叫鏈結的區塊會檢查，直到找到相符的處理常式。 任何`finally`一樣堆疊回溯時，發生在呼叫鏈結中的區塊也執行序列中。

`raise`函式相當於`throw`C# 或 c + +。 使用`reraise`中傳送相同的例外狀況呼叫鏈結的 catch 處理常式。

下列程式碼範例說明使用`raise`產生例外狀況的函式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise`函式也可用來引發.NET 例外狀況，如下列範例所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a>另請參閱
[例外狀況處理](index.md)

[例外狀況類型](exception-types.md)

[例外狀況：`try...with` 運算式](the-try-with-expression.md)

[例外狀況：`try...finally` 運算式](the-try-finally-expression.md)

[例外狀況：`failwith` 函式](the-failwith-function.md)

[例外狀況：`invalidArg` 函式](the-invalidArg-function.md)
