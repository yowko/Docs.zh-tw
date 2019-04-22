---
title: If 運算子 (Visual Basic)
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
ms.openlocfilehash: 9ab01755d75c91ce87acf83e7f406b26c466aef6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834630"
---
# <a name="if-operator-visual-basic"></a>If 運算子 (Visual Basic)
使用最少運算評估，有條件地傳回兩個值之一。 `If`與三個引數或兩個引數，就可以呼叫運算子。  
  
## <a name="syntax"></a>語法  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>如果使用三個引數來呼叫運算子  
 當`If`稱為藉由使用三個引數，第一個引數必須評估為值，可以轉換成`Boolean`。 `Boolean`值將決定哪些其他兩個引數會評估並傳回。 下列清單時，才適用`If`使用三個引數呼叫運算子。  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`argument1`|必要項。 `Boolean`. 判斷其中一個要評估及傳回的其他引數。|  
|`argument2`|必要項。 `Object`. 評估並傳回 if`argument1`評估為`True`。|  
|`argument3`|必要項。 `Object`. 評估並傳回 if`argument1`評估為`False`或者`argument1`是[Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`變數評估為[Nothing](../../../visual-basic/language-reference/nothing.md)。|  
  
 `If`運算子，會使用三個引數呼叫的運作方式類似`IIf`函式不同之處在於它會使用最少運算評估。 `IIf`函式一律會評估其引數，這三個，而`If`有三個引數的運算子會評估只有兩個。 第一個`If`引數會評估和結果轉換成`Boolean`的值，`True`或`False`。 如果值為`True`，`argument2`會評估並傳回其值，但`argument3`不會評估。 如果的值`Boolean`運算式`False`，`argument3`會評估並傳回其值，但`argument2`不會評估。 下列範例說明使用`If`三個引數使用時：  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 下列範例說明值的最少運算評估。 此範例示範兩次嘗試將變數`number`變數所`divisor`除非`divisor`為零。 在此情況下，應該會傳回 「 0 」，並不應該嘗試執行除法運算，因為會造成執行階段錯誤。 因為`If`運算式會使用最少運算的評估，它會評估第二個或第三個引數，第一個引數的值而定。 如果第一個引數為 true，除數為零並不安全地評估第二個引數，並執行除法。 如果第一個引數為 false，會評估第三個引數，就會傳回 0。 因此，除數為 0 時，不會嘗試執行除法並不會產生錯誤。 不過，因為`IIf`不會使用最少運算評估，即使在第一個引數為 false 時，才評估第二個引數。 這會導致執行階段除以零錯誤。  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a>如果兩個引數呼叫運算子  
 第一個引數`If`可以省略。 這可讓操作員使用只有兩個引數來呼叫。 下列清單時，才適用`If`使用兩個引數呼叫運算子。  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`argument2`|必要項。 `Object`. 必須是參考或可為 null 的型別。 評估並傳回其評估結果為任何項目以外時`Nothing`。|  
|`argument3`|必要項。 `Object`. 評估並傳回 if`argument2`評估為`Nothing`。|  
  
 當`Boolean`省略引數，第一個引數必須是參考或可為 null 的型別。 如果第一個引數評估為`Nothing`，會傳回第二個引數的值。 在其他情況下，會傳回第一個引數的值。 下列範例說明這項評估的運作方式。  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [可為 Null 的值類型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
