---
title: 例外狀況：Try...try...finally 運算式
description: F#瞭解「try .。。最後，即使程式碼區塊擲回例外狀況，也可以讓您執行清除程式碼。
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082999"
---
# <a name="exceptions-the-tryfinally-expression"></a>例外狀況：Try...try...finally 運算式

`try...finally`運算式可讓您執行清理程式碼，即使程式碼區塊擲回例外狀況也一樣。

## <a name="syntax"></a>語法

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>備註

運算式可用來在上述*語法中，* 以運算式2執行程式碼，而不論是否在執行運算式的過程中產生例外狀況。 `try...finally`

*運算式*類型不會對整個運算式的值造成影響;未發生例外狀況時傳回的型別，是*運算式*類型中的最後一個值。 發生例外狀況時，不會傳回任何值，而且控制權的流程會傳送至呼叫堆疊的下一個相符的例外狀況處理常式。 如果找不到任何例外狀況處理常式，則程式會終止。 在執行比對處理常式中的程式碼或程式終止之前，會執行`finally`分支中的程式碼。

下列程式碼示範`try...finally`運算式的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

主控台的輸出如下所示。

```console
Closing stream
Exception handled.
```

如您在輸出中所見，在處理外部例外狀況之前，資料流程已關閉，而且`test.txt`檔案包含文字`test1`，這表示緩衝區已排清並寫入磁片，即使已傳送例外狀況也是一樣。控制外部例外狀況處理常式。

請注意， `try...with`結構是`try...finally`來自結構的個別結構。 因此，如果您的`with`程式碼同時需要區塊`finally`和區塊，您就必須將這兩個結構加以嵌套，如下列程式碼範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

在計算運算式（包括順序運算式和非同步工作流程）的內容中，**嘗試 .。。最後**，運算式可以有自訂的實作為。 如需詳細資訊，請參閱[計算運算式](../computation-expressions.md)。

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況：`try...with`運算式](the-try-with-expression.md)
