---
title: "If 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c553da5abf5453ba881671806b976125355c1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="if-operator-visual-basic"></a>If 運算子 (Visual Basic)
使用最少運算評估，有條件地傳回兩個值之一。 `If`可以呼叫具有三個引數或兩個引數的運算子。  
  
## <a name="syntax"></a>語法  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>如果使用三個引數呼叫運算子  
 當`If`稱為藉由使用三個引數，第一個引數必須評估為值，可以轉換成`Boolean`。 確認`Boolean`值將決定哪些其他兩個引數會評估並傳回。 下列清單時，才適用`If`使用三個引數呼叫運算子。  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`argument1`|必要項。 `Boolean`. 決定其要評估並傳回的其他引數。|  
|`argument2`|必要項。 `Object`. 評估並傳回如果`argument1`評估為`True`。|  
|`argument3`|必要項。 `Object`. 評估並傳回如果`argument1`評估為`False`或`argument1`是[Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`變數評估為[Nothing](../../../visual-basic/language-reference/nothing.md)。|  
  
 `If`運算子搭配三個引數呼叫的運作方式類似`IIf`函式不同之處在於它會使用最少運算評估。 `IIf`函式一律會評估其引數，這三個，而`If`有三個引數的運算子會評估只有兩個。 第一個`If`評估引數和結果轉換為`Boolean`值`True`或`False`。 如果值為`True`，`argument2`會評估並傳回其值，但`argument3`則不會評估。 如果值`Boolean`運算式是`False`，`argument3`會評估並傳回其值，但`argument2`則不會評估。 下列範例說明使用`If`使用三個引數時：  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 下列範例說明的值最短路徑評估。 此範例顯示兩次嘗試將變數`number`變數所`divisor`除非`divisor`為零。 在此情況下，應傳回 0，並不會嘗試應該要對執行除法運算，因為會造成執行階段錯誤。 因為`If`運算式會使用最少運算評估，它會評估第二個或第三個引數，根據第一個引數的值。 如果第一個引數為 true，除數為零並不安全地評估第二個引數，並執行除法。 如果第一個引數為 false，會評估第三個引數，就會傳回 0。 因此，除數為 0 時，不會嘗試執行除法，也不會產生錯誤。 不過，因為`IIf`不會使用最少運算評估，即使在第一個引數為 false 時，才評估第二個引數。 這會導致執行階段除以零錯誤。  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## <a name="if-operator-called-with-two-arguments"></a>如果兩個引數呼叫運算子  
 第一個引數`If`可以省略。 這可讓使用只有兩個引數呼叫運算子。 下列清單時，才適用`If`使用兩個引數呼叫運算子。  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`argument2`|必要項。 `Object`. 必須是參考或可為 null 的類型。 評估並傳回其評估結果為任何項目以外時`Nothing`。|  
|`argument3`|必要項。 `Object`. 評估並傳回如果`argument2`評估為`Nothing`。|  
  
 當`Boolean`省略引數，第一個引數必須參考或可為 null 的類型。 如果第一個引數評估為`Nothing`，會傳回第二個引數的值。 在其他情況下，會傳回第一個引數的值。 下列範例說明這項評估的運作方式。  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>  
 [可為 Null 的值類型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
