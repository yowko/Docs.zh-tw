---
title: '比對運算式 （F #）'
description: '了解如何將 F # 比對運算式提供分支運算式的比較，使用一組模式為基礎的控制項。'
ms.date: 04/19/2018
ms.openlocfilehash: e4cb82f20fe82bff562736557c2346562c557f59
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44221840"
---
# <a name="match-expressions"></a>比對運算式

`match`運算式提供分支運算式的比較，使用一組模式為基礎的控制項。

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

允許根據比較結果的測試運算式與一組模式設定的分支複雜模式比對運算式。 在`match`運算式中，*測試運算式*相較於每個模式中開啟，並找到相符項目時，對應*結果運算式*評估及產生的值傳回做為比對運算式的值。

模式比對前一個語法中顯示的函式是在哪個模式比對會立即執行的引數的 lambda 運算式。 模式比對前一個語法中顯示的函式就相當於下列項目。

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

如需有關 lambda 運算式的詳細資訊，請參閱[Lambda 運算式：`fun`關鍵字](functions/lambda-expressions-the-fun-keyword.md)。

模式的完整集合應該涵蓋所有可能的相符項目輸入變數。 通常，您可以使用萬用字元模式 (`_`) 與最後一個模式來比對任何先前不相符的輸入的值。

下列程式碼說明的方式的一些`match`運算式的使用方式。 參考和可用的所有可能模式的範例，請參閱[模式比對](pattern-matching.md)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>模式的成立條件

您可以使用`when`子句來指定其他條件變數必須滿足才能符合模式。 這類子句指*防護*。 後面的運算式`when`關鍵字不會評估除非相符項目對該防護相關聯的模式。

下列範例說明如何使用成立條件來指定數字的範圍變數的模式。 請注意，使用布林運算子來合併多個條件。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

請注意，因為常值以外的值不能用在模式中，您必須使用`when`子句，如果您有要比較的輸入，針對某個值的某個部分。 這是由下列程式碼所示：

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

請注意，當等位模式都會受到防護，成立條件會套用至**所有**模式，而不只是最後一個。 例如，假設下列程式碼防護`when a > 12`同時適用於`A a`和`B a`:

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
