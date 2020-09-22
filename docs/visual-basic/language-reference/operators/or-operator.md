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
ms.openlocfilehash: f6cfd1073ada42aa2db8be9b14c81319bc0db294
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874762"
---
# <a name="or-operator-visual-basic"></a>Or 運算子 (Visual Basic)

在兩個運算式上執行邏輯分離 `Boolean` ，或在兩個數值運算式上執行位析取。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>組件  

 `result`  
 必要。 任何 `Boolean` 或數值運算式。 為了進行 `Boolean` 比較， `result` 這是兩個值的內含邏輯分離 `Boolean` 。 在位運算中， `result` 是代表兩個數值位模式之內含位分離的數值。  
  
 `expression1`  
 必要。 任何 `Boolean` 或數值運算式。  
  
 `expression2`  
 必要。 任何 `Boolean` 或數值運算式。  
  
## <a name="remarks"></a>備註  

 `Boolean`比較而言， `result` `False` 只有在 `expression1` 和都 `expression2` 評估為時，才會是 `False` 。 下表說明如何 `result` 決定。  
  
|如果 `expression1` 為 |而且 `expression2` 是|的值 `result` 為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> 在 `Boolean` 比較中， `Or` 運算子一律會評估這兩個運算式，這可能包括進行程序呼叫。 [OrElse 運算子](orelse-operator.md)會執行*最*少運算，這表示如果 `expression1` 是，則 `True` `expression2` 不會評估。  
  
 在位運算中， `Or` 運算子會執行兩個數值運算式中相同位置位的位比較，並根據下表設定對應的位 `result` 。  
  
|如果中的位 `expression1` 為|和中的位 `expression2` 為|中的位 `result` 為|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> 由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此任何位運算都應以括弧括住，以確保正確執行。  
  
## <a name="data-types"></a>資料類型  

 如果運算元是由一個 `Boolean` 運算式和一個數值運算式組成，Visual Basic 會將 `Boolean` 運算式轉換成數值 ( –1，並將) 的值轉換為 `True` 0， `False` 並執行位運算。  
  
 為了進行 `Boolean` 比較，結果的資料類型為 `Boolean` 。 針對位比較，結果資料類型是適用于和之資料類型的數數值型別 `expression1` `expression2` 。 請參閱 [運算子結果資料類型](data-types-of-operator-results.md)中的「關聯式和位比較」資料表。  
  
## <a name="overloading"></a>多載化  

 可以多載 `Or` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `Or` 運算子，在兩個運算式上執行內含邏輯分離。 結果是一個 `Boolean` 值，表示兩個運算式中的任一個是否為 `True` 。  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 上述範例會 `True` 分別產生、 `True` 和的結果 `False` 。  
  
## <a name="example"></a>範例  

 下列範例會使用 `Or` 運算子，在兩個數值運算式的個別位上執行內含邏輯分離。 如果運算元中的對應位都設定為1，則會設定結果模式中的位。  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 上述範例會分別產生10、14和14的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [OrElse 運算子](orelse-operator.md)
- [Visual Basic 中的邏輯運算子和位元運算子](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
