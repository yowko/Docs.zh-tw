---
title: 遞迴函式:Rec 關鍵字
description: 瞭解 ' rec F# ' 關鍵字如何與 ' let ' 關鍵字搭配使用, 以定義遞迴函數。
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630647"
---
# <a name="recursive-functions-the-rec-keyword"></a>遞迴函式:Rec 關鍵字

`rec`關鍵字會`let`與關鍵字搭配使用, 以定義遞迴函數。

## <a name="syntax"></a>語法

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a>備註

遞迴函式, 呼叫本身的函數會在F#語言中明確識別。 這會讓在函式的範圍中定義的識別碼可供使用。

下列程式碼說明一個遞迴函式, 它會計算<sup>第</sup> *n*個斐的量值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> 實際上, 上述程式碼不會浪費記憶體和處理器時間, 因為它牽涉到先前計算值的重新計算。

方法在型別內隱含遞迴;不需要新增`rec`關鍵字。 類別內的 Let 系結不會隱含遞迴。

## <a name="mutually-recursive-functions"></a>相互遞迴函式

有時候函式是*互斥*的, 這表示呼叫會形成圓形, 其中一個函式會呼叫另一個函式, 然後呼叫第一個函式, 而其間的呼叫數目則為。 您必須在一個`let`系結中定義這類函式, 並`and`使用關鍵字將它們連結在一起。

下列範例顯示兩個相互遞迴的函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>另請參閱

- [函式](index.md)
