---
title: If 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 28fb2afb2c4cf78ffbbb028145de647a8dc512ed
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371099"
---
# <a name="if-operator-visual-basic"></a>If 運算子 (Visual Basic)

使用短路評估來有條件地傳回兩個值的其中一個。 您 `If` 可以使用三個引數或兩個引數來呼叫運算子。

## <a name="syntax"></a>語法

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>如果呼叫了具有三個引數的運算子

`If`使用三個引數呼叫時，第一個引數必須評估為可轉換為的值 `Boolean` 。 該值 `Boolean` 會決定要評估和傳回的其他兩個引數中的哪一個。 下列清單只有在 `If` 使用三個引數呼叫運算子時才適用。

### <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`argument1`|必要。 `Boolean`. 決定要評估和傳回的其他引數。|
|`argument2`|必要。 `Object`. 評估並傳回（如果 `argument1` 評估為） `True` 。|
|`argument3`|必要。 `Object`. 如果評估為， `argument1` `False` 或如果 `argument1` 是評估為不是任何值的[可為 null](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` 變數[Nothing](../nothing.md)，則會評估並傳回。|

`If`以三個引數呼叫的運算子運作方式類似于函式 `IIf` ，不同之處在于它會使用最少運算。 `IIf`函式一律會評估它的全部三個引數，而 `If` 具有三個引數的運算子只會評估其中兩個。 `If`會評估第一個引數，並將結果轉換為 `Boolean` 值 `True` 或 `False` 。 如果值為 `True` ， `argument2` 則會評估，並傳回其值，但 `argument3` 不會進行評估。 如果運算式的值 `Boolean` 為 `False` ， `argument3` 則會評估，並傳回其值，但 `argument2` 不會進行評估。 下列範例說明使用 `If` 三個引數時的用法：

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

下列範例說明最少運算評估的值。 此範例顯示兩個嘗試除以 `number` 變數的變數 `divisor` ，但當 `divisor` 為零時。 在此情況下，應該會傳回0，而且不會嘗試執行除法，因為執行階段錯誤會產生。 因為 `If` 運算式使用的是「短路」評估，所以它會評估第二個或第三個引數（視第一個引數的值而定）。 如果第一個引數為 true，則除數不是零，而且可以安全地評估第二個引數並執行除法。 如果第一個引數為 false，則只會評估第三個引數，並傳回0。 因此，當除數為0時，不會嘗試執行除法，也不會產生錯誤結果。 不過，因為不 `IIf` 會使用最少電路評估，所以即使第一個引數為 false，也會評估第二個引數。 這會導致執行時間零除的錯誤。

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>如果使用兩個引數呼叫運算子

可以省略的第一個引數 `If` 。 這可讓您只使用兩個引數來呼叫運算子。 下列清單只適用于 `If` 使用兩個引數呼叫運算子時。

### <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`argument2`|必要。 `Object`. 必須是參考或可為 null 的實數值型別。 評估並傳回（當它評估為以外的任何專案時） `Nothing` 。|
|`argument3`|必要。 `Object`. 評估並傳回（如果 `argument2` 評估為） `Nothing` 。|

當 `Boolean` 省略引數時，第一個引數必須是參考或可為 null 的實數值型別。 如果第一個引數評估為 `Nothing` ，則會傳回第二個引數的值。 在所有其他情況下，會傳回第一個引數的值。 下列範例說明此評估的運作方式：

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [可為 null 的實數值型別](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../nothing.md)
