---
title: Mod 運算子 (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 456c19fc8e28517a0662b58e338028e1c75cd8c8
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638632"
---
# <a name="mod-operator-visual-basic"></a>Mod 運算子 (Visual Basic)
兩個數目相除，然後只傳回餘數。  
  
## <a name="syntax"></a>語法  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>組件  
 `number1`  
 必要。 任何數值運算式。  
  
 `number2`  
 必要。 任何數值運算式。  
  
## <a name="supported-types"></a>支援的類型  
 所有的數字類型。 這包括的不帶正負號和浮點類型和`Decimal`。  
  
## <a name="result"></a>結果

結果就是後的餘數`number1`除以`number2`。 例如，運算式`14 Mod 4`評估結果為 2。  

> [!NOTE]
> 之間的差異*餘數*並*模數*數學，使用不同的結果為負數。 `Mod`運算子，在 Visual Basic 中，.NET Framework`op_Modulus`運算子，以及基礎[rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL 指令的所有執行其餘作業。

結果`Mod`作業會保留被除數的正負號`number1`，因此它可能是正數或負數。 結果一律是在範圍 (-`number2`， `number2`)、 獨佔。 例如: 

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>備註  
 如果有任一`number1`或`number2`是浮點數的值，則會傳回浮點除法的餘數。 結果的資料類型是最小的資料類型，可保存所有可能的值所產生的資料類型的除法`number1`和`number2`。  
  
 如果`number1`或是`number2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。  
  
 相關的運算子包括：  
  
-   [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)傳回除法的整數商數。 例如，運算式`14 \ 4`評估結果為 3。  
  
-   [/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)傳回完整商數，包括其餘部分，做為浮點數。 例如，運算式`14 / 4`會評估為 3.5。  
  
## <a name="attempted-division-by-zero"></a>嘗試的除以零  
 如果`number2`評估為零，就會有的行為`Mod`運算子的運算元資料類型而定。 整數的除法就會擲回<xref:System.DivideByZeroException>例外狀況。 傳回浮點除法<xref:System.Double.NaN>。  
  
## <a name="equivalent-formula"></a>對等的公式  
 運算式`a Mod b`相當於下列公式：  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>浮點數不精確  
 當您使用浮點數時，請記得它們在記憶體中不一定有精確的十進位表示法。 這可能會導致非預期的結果從某些作業，例如要做數值比較，`Mod`運算子。 如需詳細資訊，請參閱 <<c0> [ 疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## <a name="overloading"></a>多載化  
 `Mod`運算子只能*多載*，這表示類別或結構可以重新定義其行為。 如果您的程式碼適用於`Mod`類別或結構，其中包含這類多載的執行個體，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 <<c0> [ 運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Mod`運算子將兩個數字，並只傳回餘數。 如果任一個數字是浮點數，結果會是浮點數表示餘數。  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範可能會不精確的浮點運算元。 第一個陳述式中，運算元都是`Double`，0.2，無限地重複的二進位分數 0.20000000000000001 預存值。 在第二個陳述式中，常值類型字元`D`強制兩個運算元`Decimal`，0.2 且精確的表示法。  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [資料類型的疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
