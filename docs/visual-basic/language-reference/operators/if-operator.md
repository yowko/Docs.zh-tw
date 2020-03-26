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
ms.openlocfilehash: 3b45a5afe331bd00c2b92f8c305351b77bc319cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249483"
---
# <a name="if-operator-visual-basic"></a>If 運算子 (Visual Basic)

使用短路評估有條件地返回兩個值之一。 可以使用`If`三個參數或兩個參數調用運算子。

## <a name="syntax"></a>語法

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>如果運算子使用三個參數調用

使用`If`三個參數調用時，第一個參數必須計算為可以轉換為 的值`Boolean`。 該`Boolean`值將確定計算並返回其他兩個參數中的哪一個。 僅當使用三個參數調用運算子`If`時，以下清單才適用。

### <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`argument1`|必要。 `Boolean`. 確定要計算和返回的其他參數。|
|`argument2`|必要。 `Object`. 如果`argument1`評估為`True`，則評估並返回。|
|`argument3`|必要。 `Object`. `argument1`如果計算為`False`或`argument1`如果為"[無"](../../../visual-basic/language-reference/nothing.md)[的可無變數](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean`，則計算並返回。|

使用`If`三個參數調用的運算子的工作方式類似于函數`IIf`，只不過它使用短路計算。 函數`IIf`始終計算其所有三個參數，而具有三個`If`參數的運算子只計算其中兩個參數。 計算第`If`一個`Boolean`參數，並將結果強制轉換為值或`True``False`。 如果值為`True`，`argument2`則計算其值，但不`argument3`計算該值。 如果`Boolean`運算式的值為`False`，`argument3`則計算其值並返回其值，但不`argument2`計算。 以下示例說明了使用三個參數`If`時的使用：

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

下面的示例說明了短路評估的價值。 該示例顯示兩次嘗試將變數`number`除以變數`divisor`除以`divisor`變數，但為零時除外。 在這種情況下，應返回 0，並且不應嘗試執行除法，因為將導致執行階段錯誤。 由於`If`運算式使用短路計算，因此根據第一個參數的值計算第二個或第三個參數。 如果第一個參數為 true，則除法不是零，可以安全地計算第二個參數並執行除法。 如果第一個參數為 false，則僅計算第三個參數並返回 0。 因此，當除法器為 0 時，不會嘗試執行除法，也沒有錯誤結果。 但是，由於`IIf`不使用短路計算，因此即使第一個參數為 false，也會計算第二個參數。 這將導致運行時除以零錯誤。

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>如果運算子使用兩個參數調用

`If`可以省略的第一個參數。 這樣，只需使用兩個參數就可以調用運算子。 僅當使用兩個參數調用運算子`If`時，以下清單才適用。

### <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`argument2`|必要。 `Object`. 必須是引用值或空數值型別。 當它評估到 以外的任何`Nothing`內容時，它進行評估並返回。|
|`argument3`|必要。 `Object`. 如果`argument2`評估為`Nothing`，則評估並返回。|

省略`Boolean`參數時，第一個參數必須是引用數值型別或空數值型別。 如果第一個參數計算到`Nothing`，則返回第二個參數的值。 在所有其他情況下，將返回第一個參數的值。 以下示例說明了此評估的工作原理：

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [空數值型別](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [什麼](../nothing.md)
