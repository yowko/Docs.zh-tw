---
title: And 運算子 (Visual Basic)
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
ms.openlocfilehash: a1802d3a7018b1b6190ff5601eba055e16e62371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913162"
---
# <a name="and-operator-visual-basic"></a>And 運算子 (Visual Basic)
在兩個`Boolean`運算式上執行邏輯結合, 或在兩個數值運算式上進行位結合。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 Any `Boolean`或 numeric 運算式。 針對布林比較, `result`是兩個`Boolean`值的邏輯結合。 對於位運算而言`result` , 是代表兩個數值位模式之位合的數值。  
  
 `expression1`  
 必要項。 Any `Boolean`或 numeric 運算式。  
  
 `expression2`  
 必要項。 Any `Boolean`或 numeric 運算式。  
  
## <a name="remarks"></a>備註  
 對於布林值比較`result` , `True`只有在和`expression2`都`expression1`評估為`True`時才會是。 下表說明如何`result`決定。  
  
|如果`expression1`為|和`expression2`為|的值`result`為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> 在布林值比較中, `And`運算子一律會評估兩個運算式, 這可能包括進行程序呼叫。 [AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)會執行最少運算, 這表示如果`expression1`為`False`, `expression2`則不會評估。  
  
 套用至數值時, `And`運算子會在兩個數值運算式中執行相同位置位的位比較, 並根據下表設定中`result`的對應位。  
  
|如果中的`expression1`位是|中的`expression2`和位為|中`result`的位是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> 由於邏輯和位運算子的優先順序比其他算術和關係運算子低, 因此應該將任何位運算括在括弧中, 以確保結果正確。  
  
## <a name="data-types"></a>資料類型  
 如果運算元是由`Boolean`一個運算式和一個數值運算式所組成, Visual Basic 會`Boolean`將運算式轉換為數值 (-1 代表`True` , 0 則代表`False`), 並執行位運算。  
  
 針對布林值比較, 結果的資料類型為`Boolean`。 針對位比較, 結果資料類型是適用于和`expression1` `expression2`之資料類型的數數值型別。 請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「關聯式和位比較」資料表。  
  
> [!NOTE]
> 運算子可以多載, 這表示當運算元具有該類別或結構的類型時, 類別或結構可以重新定義其行為。 `And` 如果您的程式碼在這類類別或結構上使用這個運算子, 請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`And`運算子, 在兩個運算式上執行邏輯結合。 結果是`Boolean`表示兩個`True`運算式是否為的值。  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 上述範例會分別產生和`True` `False`的結果。  
  
## <a name="example"></a>範例  
 下列範例會使用`And`運算子, 在兩個數值運算式的個別位上執行邏輯結合。 如果運算元中對應的位都設定為 1, 則結果模式中的位會設定為。  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 上述範例會分別產生8、2和0的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Visual Basic 中的邏輯和位運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
