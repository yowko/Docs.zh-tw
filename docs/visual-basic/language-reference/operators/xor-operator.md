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
ms.openlocfilehash: bc3df1fdee5405445b4534a6982383c49b369b01
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980434"
---
# <a name="xor-operator-visual-basic"></a>Xor 運算子 (Visual Basic)
對兩個執行邏輯排除`Boolean`運算式或兩個數值運算式的位元互斥。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何`Boolean`或數值的變數。 布林值相較之下，如`result`是兩個邏輯互斥 （獨佔邏輯分離）`Boolean`值。 對於位元運算，`result`是數值，表示兩個數值位元模式的位元互斥 （獨佔位元分離）。  
  
 `expression1`  
 必要項。 任何`Boolean`或數值運算式。  
  
 `expression2`  
 必要項。 任何`Boolean`或數值運算式。  
  
## <a name="remarks"></a>備註  
 布林值相較之下，如`result`是`True`才之一`expression1`和`expression2`評估為`True`。 亦即，如果且只有`expression1`並`expression2`評估為相反`Boolean`值。 下表將說明如何`result`決定。  
  
|如果`expression1`是|和`expression2`是|值`result`是|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  布林值相較之下，`Xor`運算子一律會評估這兩個運算式，這可能包括程序呼叫。 沒有任何最少運算的對應項目來`Xor`，因為結果一定會相依於這兩個運算元。 針對*最少運算*邏輯運算子，請參閱[AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)並[OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)。  
  
 位元運算，如`Xor`運算子會在兩個數值運算式之間執行位元比較相同位置的位元，並對應中位元設`result`根據下表。  
  
|如果位元`expression1`是|在位元和`expression2`是|中的位元`result`是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元的作業應該含括括號，以確保能夠正確執行。  
  
 例如，5 `Xor` 3 為 6。 若要查看這為何因此，轉換成其二進位的表示法、 101 和 011 的 5 和 3。 然後使用上表來判斷 101 Xor 011 是 110，這是 6 的十進位數字的二進位表示法。  
  
## <a name="data-types"></a>資料類型  
 如果包含運算元`Boolean`Visual Basic 運算式及一個數值運算式，將轉換`Boolean`為數值的運算式 (– 1`True`以 0 代表`False`) 和執行位元運算。  
  
 針對`Boolean`相較之下，結果的資料型別是`Boolean`。 如需位元的比較，將結果資料類型是數值類型適合的資料類型`expression1`和`expression2`。 請參閱 < 關聯式和位元比較 」 的表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
## <a name="overloading"></a>多載化  
 `Xor`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Xor`運算子上兩個運算式執行邏輯互斥 （獨佔邏輯分離）。 結果是`Boolean`值，表示只有其中一個運算式是否`True`。  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 前一個範例產生的結果`False`， `True`，和`False`分別。  
  
## <a name="example"></a>範例  
 下列範例會使用`Xor`運算子的兩個數值運算式的個別位元執行邏輯互斥 （獨佔邏輯分離）。 如果只有其中一個運算元的對應位元設為 1，會設定結果模式中的位元。  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 前一個範例會分別產生的 2、 第 12 和 14 的結果。  
  
## <a name="see-also"></a>另請參閱
- [邏輯/位元運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
