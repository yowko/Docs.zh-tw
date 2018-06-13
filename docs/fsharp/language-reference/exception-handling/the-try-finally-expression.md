---
title: 例外狀況：try...finally 運算式 (F#)
description: "深入了解如何 F # ' try finally' 運算式可讓您執行清除程式碼，即使一段程式碼擲回例外狀況。"
ms.date: 05/16/2016
ms.openlocfilehash: a5fdec7b3986fc9a85c34b08d20dc31947c92b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563489"
---
# <a name="exceptions-the-tryfinally-expression"></a>例外狀況：try...finally 運算式

`try...finally`運算式可讓您執行清除程式碼，即使一段程式碼擲回例外狀況。


## <a name="syntax"></a>語法

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>備註
`try...finally`運算式可用來執行中的程式碼*expression2*中先前的語法，不論是否在執行期間會產生例外狀況*expression1*。

型別*expression2*並沒有提供完整的運算式; 的值時不會發生例外狀況傳回的類型是中的最後一個值*expression1*。 例外狀況發生時，會傳回任何值，並控制流程將轉移至下一個相符例外狀況處理常式的呼叫堆疊。 如果不找到任何例外狀況處理常式，在程式終止。 相符的處理常式中的程式碼會執行，或在程式終止中的程式碼之前`finally`分支執行。

下列程式碼會示範如何使用`try...finally`運算式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

以下是輸出到主控台。

```
Closing stream
Exception handled.
```

您可以從輸出中看到之前已處理外部例外狀況，, 關閉資料流和檔案`test.txt`包含文字`test1`，指出已排清緩衝區，並寫入磁碟，即使例外狀況傳送控制外部例外狀況處理常式。

請注意，`try...with`建構是從個別建構`try...finally`建構。 因此，如果您的程式碼需要`with`區塊和`finally`區塊中，您必須將巢狀化的兩個建構，如下列程式碼範例所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

在計算運算式的內容，包括 循序項運算式及非同步工作流程， **try … 最後**運算式可能會有自訂的實作。 如需詳細資訊，請參閱[計算運算式](../computation-expressions.md)。


## <a name="see-also"></a>另請參閱
[例外狀況處理](index.md)

[例外狀況：`try...with` 運算式](the-try-with-expression.md)
