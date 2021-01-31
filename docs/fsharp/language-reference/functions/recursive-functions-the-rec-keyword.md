---
title: 遞迴函式：rec 關鍵字
description: "瞭解如何搭配 ' let ' 關鍵字使用 F # ' rec ' 關鍵字來定義遞迴函數。"
ms.date: 08/12/2020
ms.openlocfilehash: 27f215f7b6f09646e847898c2618cfac10175e6e
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215708"
---
# <a name="recursive-functions-the-rec-keyword"></a>遞迴函式：rec 關鍵字

`rec`關鍵字會與關鍵字一起使用 `let` ，以定義遞迴函數。

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

遞迴函式-呼叫本身的函式會在 F # 語言中使用關鍵字明確識別 `rec` 。 關鍵字讓系結的 `rec` 名稱 `let` 可在其主體中使用。

下列範例顯示的遞迴函式，會使用數學定義來計算 <sup>第</sup> *n* 個斐的量值。

```fsharp
let rec fib n =
    match n with
    | 0 | 1 -> n
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> 在實務上，上述範例之類的程式碼並不理想，因為它 unecessarily 已計算的旁邊值。 這是因為它不是 tail 遞迴，這會在本文中進一步說明。

方法會在其定義的類型內隱含遞迴，這表示不需要加入 `rec` 關鍵字。 例如：

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> n
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

不過，在類別中的系結並非隱含遞迴。 所有系結 `let` 函數都需要 `rec` 關鍵字。

## <a name="tail-recursion"></a>尾遞迴

針對某些遞迴函式，必須將更多「單純」定義重構為 [結尾遞迴](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)的定義。 這可避免不必要的 recomputations。 例如，您可以如下所示重新撰寫先前的量值產生器：

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

這是更複雜的執行。 產生數量詞是一種非常簡單的「一般」演算法的絕佳範例，但實際上並沒有效率。 在 F # 中，有幾個層面會讓它有效率，但仍會以遞迴方式定義：

* 名為的遞迴內建函式 `loop` ，它是慣用 F # 模式。
* 將累積值傳遞給遞迴呼叫的兩個累積參數。
* 檢查的值 `n` ，以傳回特定的累積。

如果此範例是使用迴圈反復寫入，則程式碼看起來會像是兩個不同的值累積數目，直到符合特定條件為止。

這是結尾遞迴的原因，是因為遞迴呼叫不需要在呼叫堆疊上儲存任何值。 所有計算的中繼值都會透過輸入至內建函式來累積。 這也可讓 F # 編譯器將程式碼優化，就像您撰寫迴圈一樣快 `while` 。

通常會撰寫 F # 程式碼，以遞迴方式處理具有內部和外部函式的某個內容，如先前範例所示。 內部函式會使用尾遞迴，而外部函式則是更好的呼叫端介面。

## <a name="mutually-recursive-functions"></a>相互遞迴函數

有時候函式是 *相互遞迴* 的，這表示呼叫會形成圓形，其中一個函式會呼叫另一個函式，而後者會呼叫另一個函式，並在其間有任意數目的呼叫。 您必須在一個系結中一起定義這類函數 `let` ， `and` 並使用關鍵字將它們連結在一起。

下列範例顯示兩個互相遞迴的函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a>遞迴值

您也可以將系結的 `let` 值定義為遞迴。 這有時候是為了記錄而進行的。 使用 F # 5 和函式 `nameof` ，您可以執行下列動作：

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a>請參閱

- [函式](index.md)
