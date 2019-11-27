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
ms.openlocfilehash: 78a65843a449bd15d5615710e1685f40d94c37f7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350246"
---
# <a name="and-operator-visual-basic"></a>And 運算子 (Visual Basic)
在兩個 `Boolean` 運算式上執行邏輯結合，或在兩個數值運算式上進行位結合。  
  
## <a name="syntax"></a>語法  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要。 任何 `Boolean` 或數值運算式。 針對布林比較，`result` 是兩個 `Boolean` 值的邏輯結合。 對於位運算而言，`result` 是代表兩個數值位模式之位合的數值。  
  
 `expression1`  
 必要。 任何 `Boolean` 或數值運算式。  
  
 `expression2`  
 必要。 任何 `Boolean` 或數值運算式。  
  
## <a name="remarks"></a>備註  
 對於布林值比較，只有在 `expression1` 和 `expression2` 都評估為 `True`時，才會 `True` `result`。 下表說明如何決定 `result`。  
  
|如果 `expression1` 為|而 `expression2` 為|`result` 的值為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> 在布林值比較中，`And` 運算子一律會評估兩個運算式，這可能包括進行程序呼叫。 [AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)會執行最少運算，這表示如果 `False` *`expression1`，則*不會評估 `expression2`。  
  
 套用至數值時，`And` 運算子會在兩個數值運算式中執行相同位置位的位比較，並根據下表設定 `result` 中的對應位。  
  
|如果 `expression1` 中的位為|`expression2` 中的和位是|`result` 中的位是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> 由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此應該將任何位運算括在括弧中，以確保結果正確。  
  
## <a name="data-types"></a>資料類型  
 如果運算元包含一個 `Boolean` 運算式和一個數值運算式，Visual Basic 會將 `Boolean` 運算式轉換成數值（-1 代表 `True`，0代表 `False`），並執行位運算。  
  
 若為布林值比較，結果的資料類型會是 `Boolean`。 針對位比較，結果資料類型是適用于 `expression1` 和 `expression2`的資料類型的數數值型別。 請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「關聯式和位比較」資料表。  
  
> [!NOTE]
> `And` 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `And` 運算子，在兩個運算式上執行邏輯結合。 結果為 `Boolean` 值，表示兩個運算式是否都 `True`。  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 上述範例會分別產生 `True` 和 `False`的結果。  
  
## <a name="example"></a>範例  
 下列範例會使用 `And` 運算子，在兩個數值運算式的個別位上執行邏輯結合。 如果運算元中對應的位都設定為1，則結果模式中的位會設定為。  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 上述範例會分別產生8、2和0的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位運算子（Visual Basic）](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Visual Basic 中的邏輯和位運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
