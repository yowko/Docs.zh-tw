---
title: Match 運算式
description: 瞭解比對F#運算式如何提供以運算式與一組模式的比較為基礎的分支控制。
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627617"
---
# <a name="match-expressions"></a>Match 運算式

`match`運算式提供的分支控制是以運算式與一組模式的比較為基礎。

## <a name="syntax"></a>語法

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a>備註

模式比對運算式可根據測試運算式與一組模式的比較, 來進行複雜的分支。 在運算式中, 會依序將*測試運算式*與每個模式進行比較, 當找到相符的結果時, 就會評估對應的*結果運算式*, 並傳回產生的值做為 match 運算式的值。 `match`

前面的語法中所顯示的模式比對函式, 是在引數上立即執行模式比對的 lambda 運算式。 先前語法中所顯示的模式比對函式相當於下列。

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

如需 lambda 運算式的詳細資訊, [請參閱 lambda 運算式:`fun`關鍵字。](./functions/lambda-expressions-the-fun-keyword.md)

一整組模式應涵蓋輸入變數的所有可能相符專案。 通常, 您會使用萬用字元模式 (`_`) 做為最後一個模式, 以比對任何先前不相符的輸入值。

下列程式碼說明使用`match`運算式的一些方式。 如需可使用之所有可能模式的參考和範例, 請參閱[模式](pattern-matching.md)比對。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>保護模式

您可以使用`when`子句來指定其他條件, 讓變數必須滿足以符合模式。 這類子句稱為「*防護*」。 除非對與該`when`防護相關聯的模式進行比對, 否則不會評估緊接在關鍵字後面的運算式。

下列範例說明如何使用 guard 來指定變數模式的數值範圍。 請注意, 您可以使用布林運算子來結合多個條件。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

請注意, 因為不能在模式中使用常值以外的值, 所以如果`when`您必須將輸入的某些部分與值進行比較, 則必須使用子句。 這會以下列程式碼顯示：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

請注意, 當「聯集」模式受到防護的涵蓋時, 此防護會套用至**所有**模式, 而不只是最後一個。 例如, 假設有下列程式碼, 則此`when a > 12`防護適用`A a`于和`B a`:

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [使用中模式](active-patterns.md)
- [模式比對](pattern-matching.md)
