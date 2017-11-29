---
title: "搜尋運算式 (F#)"
description: "了解如何在 F # 比對運算式提供分支運算式的比較，以一組模式為基礎的控制項。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8854b713-255a-408d-942a-e80ab52fd2a4
ms.openlocfilehash: c8b9be744cfa7bc76f0d663b12abd66f8757fc56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="match-expressions"></a>比對運算式

`match`運算式提供分支運算式的比較，以一組模式為基礎的控制項。

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

模式比對運算式允許複雜分支根據比較結果的測試運算式與一組模式。 在`match`運算式，*測試運算式*與進行比較，每個模式中開啟，並找到相符項目時，對應*結果運算式*評估及產生的值傳回做為比對運算式的值。

模式比對上一個語法中顯示的函式是在哪個模式中執行比對立即的引數的 lambda 運算式。 模式比對上一個語法中顯示的函式就相當於下列項目。

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```    

如需 lambda 運算式的詳細資訊，請參閱[Lambda 運算式：`fun`關鍵字](functions/lambda-expressions-the-fun-keyword.md)。

完整的模式設定應該涵蓋所有可能的相符的輸入變數。 通常，您可以使用萬用字元模式 (`_`) 來比對任何先前不相符的輸入的值與上一個模式。

下列程式碼將說明部分的方式`match`運算式使用。 參考資料和可用的所有可能模式的範例，請參閱[模式比對](pattern-matching.md)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>模式成立條件

您可以使用`when`子句指定的變數必須符合才能符合模式的其他條件。 這類子句指*防護*。 後面的運算式`when`除非相符項目對該保護與相關聯的模式，將不評估關鍵字。

下列範例說明如何使用指定的數值範圍變數模式的成立條件。 請注意，多個條件會組合使用布林運算子。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

請注意，因為常值以外的值不能用在模式中，您必須使用`when`子句，如果您有要比較的輸入，針對某個值的某些部分。 如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

## <a name="see-also"></a>另請參閱

[F# 語言參考](index.md)

[使用中模式](active-patterns.md)

[模式比對](pattern-matching.md)
