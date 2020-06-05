---
title: Xor 運算子
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
ms.openlocfilehash: 999050314d674fa98833083d84796e471c22971d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406336"
---
# <a name="xor-operator-visual-basic"></a>Xor 運算子 (Visual Basic)
在兩個運算式上執行邏輯排除 `Boolean` ，或在兩個數值運算式上執行位排除。  
  
## <a name="syntax"></a>語法  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要。 Any `Boolean` 或 numeric 變數。 針對布林比較， `result` 是兩個值的邏輯排除（獨佔邏輯分離） `Boolean` 。 對於位運算 `result` 而言，是代表兩個數值位模式之位排除（獨佔位分離）的數值。  
  
 `expression1`  
 必要。 任何 `Boolean` 或數值運算式。  
  
 `expression2`  
 必要。 任何 `Boolean` 或數值運算式。  
  
## <a name="remarks"></a>備註  
 對於布林值比較，只有在只有 `result` `True` 一個 `expression1` 和會 `expression2` 評估為時，才會是 `True` 。 也就是說，如果和都 `expression1` `expression2` 評估為相反的值，則為 `Boolean` 。 下表說明如何 `result` 決定。  
  
|如果 `expression1` 為 |和 `expression2` 為|的值 `result` 為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> 在布林值比較中， `Xor` 運算子一律會評估兩個運算式，這可能包括進行程序呼叫。 沒有與的簡短對應 `Xor` ，因為結果一律取決於這兩個運算元。 如需最*小*運算邏輯運算子，請參閱[AndAlso 運算子](andalso-operator.md)和[OrElse 運算子](orelse-operator.md)。  
  
 對於位運算， `Xor` 運算子會在兩個數值運算式中執行相同位置位的位比較，並根據下表設定中的對應位 `result` 。  
  
|如果中的位 `expression1` 是|中的和位 `expression2` 為|中的位 `result` 是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> 由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此應該將任何位運算括在括弧中，以確保正確執行。  
  
 例如，5 `Xor` 3 是6。 若要瞭解原因，請將5和3轉換成其二進位表示，101和011。 然後使用上表來判斷 101 Xor 011 是110，這是十進位數6的二進位標記法。  
  
## <a name="data-types"></a>資料類型  
 如果運算元是由一個 `Boolean` 運算式和一個數值運算式所組成，Visual Basic 會將 `Boolean` 運算式轉換為數值（-1 代表 `True` ，0則代表 `False` ），並執行位運算。  
  
 為了進行 `Boolean` 比較，結果的資料類型是 `Boolean` 。 針對位比較，結果資料類型是適用于和之資料類型的數數值型別 `expression1` `expression2` 。 請參閱[運算子結果的資料類型](data-types-of-operator-results.md)中的「關聯式和位比較」資料表。  
  
## <a name="overloading"></a>多載化  
 `Xor`運算子可以多載*overloaded*，這表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請確定您瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Xor` 運算子，在兩個運算式上執行邏輯排除（獨佔邏輯分離）。 結果會是一個 `Boolean` 值，表示是否只有一個運算式 `True` 。  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 先前的範例會分別產生 `False` 、 `True` 和的結果 `False` 。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Xor` 運算子，在兩個數值運算式的個別位上執行邏輯排除（獨佔邏輯分離）。 如果運算元中只有一個對應的位設為1，則結果模式中的位會設定為。  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 先前的範例會分別產生2、12和14的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 中的邏輯運算子和位元運算子](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
