---
title: 遞迴函式：rec 關鍵字
description: "瞭解 F # ' rec ' 關鍵字如何與 ' let ' 關鍵字搭配使用，以定義遞迴函數。"
ms.date: 05/16/2016
ms.openlocfilehash: c9a3b7dc27f4ed86948a08b7783d7e8e8b60e57f
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2020
ms.locfileid: "87426972"
---
# <a name="recursive-functions-the-rec-keyword"></a>遞迴函式：rec 關鍵字

`rec`關鍵字會與關鍵字搭配使用 `let` ，以定義遞迴函數。

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

遞迴函式（呼叫本身的函數）會在 F # 語言中明確識別。 這會讓在函式的範圍中定義的識別碼可供使用。

下列程式碼說明遞迴函式，該函式會使用數學定義來計算<sup>第</sup> *n*個斐的量值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> 實際上，如同前一個範例的程式碼並不理想，因為它 unecessarily 了已計算的旁邊值。 這是因為它不是尾遞迴，這會在本文中進一步說明。

方法在型別內隱含遞迴;不需要新增 `rec` 關鍵字。 類別內的 Let 系結不會隱含遞迴。

## <a name="tail-recursion"></a>尾遞迴

針對某些遞迴函式，必須將更多的「純」定義重構為[尾遞迴](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)。 這可防止不必要 recomputations。 例如，先前的斐數列數位產生器可以重寫如下：

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

這是比較複雜的實作為。 產生一個大波的數位，是一種「單純」演算法的絕佳範例，其實是以數學方式來表示，但實際上沒有效率。 有幾個層面讓它在 F # 中有效率，同時仍然以遞迴方式定義：

* 名為的遞迴內部函 `loop` 式，這是慣用 F # 模式。
* 兩個累計參數，會將累積的值傳遞給遞迴呼叫。
* 檢查的值 `n` ，以傳回特定的累積。

如果這個範例是以迴圈反復撰寫，則程式碼看起來會類似兩個不同的值累積數位，直到符合特定條件為止。

這是尾遞迴的原因是因為遞迴呼叫不需要在呼叫堆疊上儲存任何值。 所有要計算的中繼值都會透過內建函式的輸入進行累計。 這也可讓 F # 編譯器將程式碼優化，就像您撰寫像是迴圈一樣快速 `while` 。

撰寫 F # 程式碼通常會以遞迴方式處理具有內部和外部函式的某個專案，如先前範例所示。 內部函式會使用尾遞迴，而外部函式則具有較佳的呼叫端介面。

## <a name="mutually-recursive-functions"></a>相互遞迴函式

有時候函式是*互斥*的，這表示呼叫會形成圓形，其中一個函式會呼叫另一個函式，然後呼叫第一個函式，而其間的呼叫數目則為。 您必須在一個系結中定義這類函式 `let` ， `and` 並使用關鍵字將它們連結在一起。

下列範例顯示兩個相互遞迴的函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>另請參閱

- [函式](index.md)
