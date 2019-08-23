---
title: Or 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 1d11a6d009f6ecfea9fb1a86b00c67b87d5555dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955845"
---
# <a name="or-operator-visual-basic"></a>Or 運算子 (Visual Basic)
在兩個`Boolean`運算式上執行邏輯分離, 或在兩個數值運算式上執行位析取。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 Any `Boolean`或 numeric 運算式。 為了`Boolean`進行比較`result` , 是兩個`Boolean`值的內含邏輯分離。 對於位運算而言`result` , 是代表兩個數值位模式之內含位分離的數值。  
  
 `expression1`  
 必要項。 Any `Boolean`或 numeric 運算式。  
  
 `expression2`  
 必要項。 Any `Boolean`或 numeric 運算式。  
  
## <a name="remarks"></a>備註  
 為了`Boolean`進行比較`result` `expression1` ,只有和`expression2`都評估為`False`時才為。 `False` 下表說明如何`result`決定。  
  
|如果`expression1`為|和`expression2`為|的值`result`為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> 在比較中`Or` , 運算子一律會評估兩個運算式, 這可能包括進行程序呼叫。 `Boolean` [OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)會執行最少運算, 這表示如果`expression1`為`True`, `expression2`則不會評估。  
  
 對於位運算, `Or`運算子會在兩個數值運算式中執行相同位置位的位比較, 並根據下表設定中`result`的對應位。  
  
|如果中的`expression1`位是|中的`expression2`和位為|中`result`的位是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> 由於邏輯和位運算子的優先順序比其他算術和關係運算子低, 因此應該將任何位運算括在括弧中, 以確保正確執行。  
  
## <a name="data-types"></a>資料類型  
 如果運算元是由`Boolean`一個運算式和一個數值運算式所組成, Visual Basic 會`Boolean`將運算式轉換為數值 (-1 代表`True` , 0 則代表`False`), 並執行位運算。  
  
 為了進行`Boolean`比較, 結果的資料類型是。 `Boolean` 針對位比較, 結果資料類型是適用于和`expression1` `expression2`之資料類型的數數值型別。 請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「關聯式和位比較」資料表。  
  
## <a name="overloading"></a>多載化  
 運算子可以多載, 這表示當運算元具有該類別或結構的類型時, 類別或結構可以重新定義其行為。 `Or` 如果您的程式碼在這類類別或結構上使用這個運算子, 請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Or`運算子, 在兩個運算式上執行內含邏輯分離。 結果是`Boolean`值, 表示兩個運算式的其中一個是否為`True`。  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 上述範例會分別產生、 `True` `True`和`False`的結果。  
  
## <a name="example"></a>範例  
 下列範例會使用`Or`運算子, 在兩個數值運算式的個別位上執行內含邏輯分離。 如果運算元中的其中一個對應位設為 1, 則結果模式中的位會設定為。  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 上述範例會分別產生10、14和14的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Visual Basic 中的邏輯和位運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
