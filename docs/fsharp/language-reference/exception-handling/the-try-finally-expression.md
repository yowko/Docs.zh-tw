---
title: 例外狀況：try...finally 運算式 (F#)
description: "了解如何在 F # 'try...最後' 運算式可讓您執行清除程式碼，即使程式碼區塊擲回例外狀況。"
ms.date: 05/16/2016
ms.openlocfilehash: 546a6b0619de6f51044600dc1ead73c6d5211299
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45515168"
---
# <a name="exceptions-the-tryfinally-expression"></a>例外狀況：try...finally 運算式

`try...finally`運算式可讓您執行清除程式碼，即使程式碼區塊擲回例外狀況。

## <a name="syntax"></a>語法

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>備註

`try...finally`運算式可用於執行中的程式碼*expression2*在前述的語法，不論是否在執行期間會產生例外狀況*expression1*。

型別*expression2*並不含完整的運算式; 的值時不會發生例外狀況傳回的類型是中的最後一個值*expression1*。 例外狀況發生時，會傳回任何值，並傳送至下一個相符例外狀況處理常式的呼叫堆疊的控制流程。 如果不找到任何例外狀況處理常式，則會終止程式。 在執行中相符的處理常式的程式碼或程式終止中的程式碼之前`finally`會執行分支。

下列程式碼示範如何使用`try...finally`運算式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

在主控台輸出如下所示。

```
Closing stream
Exception handled.
```

之前已處理外部例外狀況，您可以從輸出中看到，關閉資料流和檔案`test.txt`包含文字`test1`，指出已排清緩衝區，並寫入磁碟，即使例外狀況傳送控制外部例外狀況處理常式。

請注意，`try...with`個別從建構`try...finally`建構。 因此，如果您的程式碼需要兩`with`區塊和`finally`區塊中，您必須將巢狀化的兩個建構，如下列程式碼範例所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

在 計算運算式的內容，包括循序項運算式與非同步的工作流程**try...最後**運算式可能會有的自訂實作。 如需詳細資訊，請參閱 <<c0> [ 計算運算式](../computation-expressions.md)。

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況：`try...with` 運算式](the-try-with-expression.md)
