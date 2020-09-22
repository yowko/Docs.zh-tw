---
title: And 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: b4d6d08cca2907befeab2e31c6804b69849c9e38
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874857"
---
# <a name="and-operator-visual-basic"></a>And 運算子 (Visual Basic)

在兩個運算式上執行邏輯結合 `Boolean` ，或在兩個數值運算式上執行位合。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>組件  

 `result`  
 必要。 任何 `Boolean` 或數值運算式。 針對布林值比較， `result` 這是兩個值的邏輯結合 `Boolean` 。 在位運算中， `result` 是代表兩個數值位模式之位合的數值。  
  
 `expression1`  
 必要。 任何 `Boolean` 或數值運算式。  
  
 `expression2`  
 必要。 任何 `Boolean` 或數值運算式。  
  
## <a name="remarks"></a>備註  

 針對布林值比較 `result` ， `True` 只有在 `expression1` 和都 `expression2` 評估為 `True` 時，才為。 下表說明如何 `result` 決定。  
  
|如果 `expression1` 為 |而且 `expression2` 是|的值 `result` 為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> 在布林值比較中， `And` 運算子一律會評估這兩個運算式，這可能包括進行程序呼叫。 [AndAlso 運算子](andalso-operator.md)會執行*最*少運算，這表示如果 `expression1` 是，則 `False` `expression2` 不會評估。  
  
 當套用至數值時， `And` 運算子會執行兩個數值運算式中相同位置位的位比較，並根據下表設定對應的位 `result` 。  
  
|如果中的位 `expression1` 為|和中的位 `expression2` 為|中的位 `result` 為|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> 由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此任何位運算都應以括弧括住，以確保正確的結果。  
  
## <a name="data-types"></a>資料類型  

 如果運算元是由一個 `Boolean` 運算式和一個數值運算式組成，Visual Basic 會將 `Boolean` 運算式轉換成數值 ( –1，並將) 的值轉換為 `True` 0， `False` 並執行位運算。  
  
 若為布林值比較，結果的資料類型為 `Boolean` 。 針對位比較，結果資料類型是適用于和之資料類型的數數值型別 `expression1` `expression2` 。 請參閱 [運算子結果資料類型](data-types-of-operator-results.md)中的「關聯式和位比較」資料表。  
  
> [!NOTE]
> 可以多載 `And` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `And` 運算子，在兩個運算式上執行邏輯結合。 結果是一個 `Boolean` 值，表示兩個運算式是否都是 `True` 。  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 上述範例會分別產生和的結果 `True` `False` 。  
  
## <a name="example"></a>範例  

 下列範例會使用 `And` 運算子，在兩個數值運算式的個別位上執行邏輯結合。 如果運算元中的對應位都設定為1，則會設定結果模式中的位。  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 上述範例會分別產生8、2和0的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [AndAlso 運算子](andalso-operator.md)
- [Visual Basic 中的邏輯運算子和位元運算子](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
