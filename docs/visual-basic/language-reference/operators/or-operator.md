---
title: Or 運算子
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
ms.openlocfilehash: 8f28026b526c29a6122725b2689e53b7f6ee7327
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348245"
---
# <a name="or-operator-visual-basic"></a>Or 運算子 (Visual Basic)
在兩個 `Boolean` 運算式上執行邏輯分離，或在兩個數值運算式上執行位析取。  
  
## <a name="syntax"></a>語法  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要。 任何 `Boolean` 或數值運算式。 針對 `Boolean` 比較，`result` 是兩個 `Boolean` 值的內含邏輯分離。 對於位運算而言，`result` 是數值，代表兩個數值位模式的內含位分離。  
  
 `expression1`  
 必要。 任何 `Boolean` 或數值運算式。  
  
 `expression2`  
 必要。 任何 `Boolean` 或數值運算式。  
  
## <a name="remarks"></a>備註  
 針對 `Boolean` 比較，只有在 `expression1` 和 `expression2` 都評估為 `False`時，才會 `False` `result`。 下表說明如何決定 `result`。  
  
|如果 `expression1` 為|而 `expression2` 為|`result` 的值為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> 在 `Boolean` 比較中，`Or` 運算子一律會評估兩個運算式，這可能包括進行程序呼叫。 [OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)會執行最少運算，這表示如果 `True` *`expression1`，則*不會評估 `expression2`。  
  
 對於位運算，`Or` 運算子會在兩個數值運算式中執行相同位置位的位比較，並根據下表設定 `result` 中的對應位。  
  
|如果 `expression1` 中的位為|`expression2` 中的和位是|`result` 中的位是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> 由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此應該將任何位運算括在括弧中，以確保正確執行。  
  
## <a name="data-types"></a>資料類型  
 如果運算元包含一個 `Boolean` 運算式和一個數值運算式，Visual Basic 會將 `Boolean` 運算式轉換成數值（-1 代表 `True`，0代表 `False`），並執行位運算。  
  
 若要進行 `Boolean` 比較，會 `Boolean`結果的資料類型。 針對位比較，結果資料類型是適用于 `expression1` 和 `expression2`的資料類型的數數值型別。 請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「關聯式和位比較」資料表。  
  
## <a name="overloading"></a>多載化  
 `Or` 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Or` 運算子，在兩個運算式上執行內含邏輯分離。 結果為 `Boolean` 值，表示是否 `True`兩個運算式的其中一個。  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 上述範例會分別產生 `True`、`True`和 `False`的結果。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Or` 運算子，在兩個數值運算式的個別位上執行內含邏輯分離。 如果運算元中的其中一個對應位設為1，則結果模式中的位會設定為。  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 上述範例會分別產生10、14和14的結果。  
  
## <a name="see-also"></a>請參閱

- [邏輯/位運算子（Visual Basic）](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Visual Basic 中的邏輯和位運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
