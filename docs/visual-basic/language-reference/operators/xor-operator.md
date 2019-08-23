---
title: Xor 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: 59f27b92996e1506be5967de88c22fb88e06f5b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965851"
---
# <a name="xor-operator-visual-basic"></a>Xor 運算子 (Visual Basic)
在兩個`Boolean`運算式上執行邏輯排除, 或在兩個數值運算式上執行位排除。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 Any `Boolean`或 numeric 變數。 針對布林比較, `result`是兩個`Boolean`值的邏輯排除 (獨佔邏輯分離)。 對於位運算而言`result` , 是代表兩個數值位模式之位排除 (獨佔位分離) 的數值。  
  
 `expression1`  
 必要項。 Any `Boolean`或 numeric 運算式。  
  
 `expression2`  
 必要項。 Any `Boolean`或 numeric 運算式。  
  
## <a name="remarks"></a>備註  
 對於布林值比較`result` , `True` `expression1`只有在只有一個和`expression2`會評估為`True`時, 才會是。 也就是說, 如果`expression1` `expression2`和都評估為相反`Boolean`的值, 則為。 下表說明如何`result`決定。  
  
|如果`expression1`為|和`expression2`為|的值`result`為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> 在布林值比較中, `Xor`運算子一律會評估兩個運算式, 這可能包括進行程序呼叫。 沒有與`Xor`的簡短對應, 因為結果一律取決於這兩個運算元。 如需最*小*運算邏輯運算子, 請參閱[AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)和[OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)。  
  
 對於位運算, `Xor`運算子會在兩個數值運算式中執行相同位置位的位比較, 並根據下表設定中`result`的對應位。  
  
|如果中的`expression1`位是|中的`expression2`和位為|中`result`的位是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> 由於邏輯和位運算子的優先順序比其他算術和關係運算子低, 因此應該將任何位運算括在括弧中, 以確保正確執行。  
  
 例如, 5 `Xor` 3 是6。 若要瞭解原因, 請將5和3轉換成其二進位表示, 101 和011。 然後使用上表來判斷 101 Xor 011 是 110, 這是十進位數6的二進位標記法。  
  
## <a name="data-types"></a>資料類型  
 如果運算元是由`Boolean`一個運算式和一個數值運算式所組成, Visual Basic 會`Boolean`將運算式轉換為數值 (-1 代表`True` , 0 則代表`False`), 並執行位運算。  
  
 為了進行`Boolean`比較, 結果的資料類型是。 `Boolean` 針對位比較, 結果資料類型是適用于和`expression1` `expression2`之資料類型的數數值型別。 請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「關聯式和位比較」資料表。  
  
## <a name="overloading"></a>多載化  
 運算子可以多載, 這表示當運算元具有該類別或結構的類型時, 類別或結構可以重新定義其行為。 `Xor` 如果您的程式碼在這類類別或結構上使用這個運算子, 請確定您瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Xor`運算子, 在兩個運算式上執行邏輯排除 (獨佔邏輯分離)。 結果會是一個`Boolean`值, 表示是否只有一個`True`運算式。  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 先前的範例會分別產生`False`、 `True`和`False`的結果。  
  
## <a name="example"></a>範例  
 下列範例會使用`Xor`運算子, 在兩個數值運算式的個別位上執行邏輯排除 (獨佔邏輯分離)。 如果運算元中只有一個對應的位設為 1, 則結果模式中的位會設定為。  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 先前的範例會分別產生2、12和14的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的邏輯和位運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
