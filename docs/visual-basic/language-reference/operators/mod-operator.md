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
ms.openlocfilehash: 5120823f4e001fc3aff71f267176311e2465597a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mod-operator-visual-basic"></a>Mod 運算子 (Visual Basic)
兩數相除並只傳回餘數。  
  
## <a name="syntax"></a>語法  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>組件  
 `number1`  
 必要。 任何數值運算式。  
  
 `number2`  
 必要。 任何數值運算式。  
  
## <a name="supported-types"></a>支援的型別  
 所有數字類型。 這包括不帶正負號和浮點類型和`Decimal`。  
  
## <a name="result"></a>結果

結果是後的餘數`number1`除以`number2`。 例如，運算式`14 Mod 4`評估為 2。  

> [!NOTE]
> 之間的差異*餘數*和*模數*在數學上，使用不同的結果為負數。 `Mod`運算子在 Visual Basic 中，.NET Framework`op_Modulus`運算子，以及基礎 [rem]<xref:System.Reflection.Emit.OpCodes.Rem> IL 指令的所有執行其餘作業。

結果`Mod`作業會保留除數的正負號`number1`，因此它可能是正數或負數。 結果一定是範圍 (-`number2`， `number2`)、 獨佔。 例如: 

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
 如果有任一個`number1`或`number2`是浮點數的值，會傳回浮點除法的餘數。 結果的資料類型是最小的資料型別，可以產生除法運算的資料類型的所有可能值`number1`和`number2`。  
  
 如果`number1`或`number2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。  
  
 相關的運算子包括：  
  
-   [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)傳回除法的整數商數。 例如，運算式`14 \ 4`評估結果為 3。  
  
-   [/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)傳回完整的商數，包括其餘部分，做為浮點數。 例如，運算式`14 / 4`會評估為 3.5。  
  
## <a name="attempted-division-by-zero"></a>嘗試的除以零  
 如果`number2`評估為零，行為`Mod`運算子的運算元資料類型而定。 發生整數除以擲回<xref:System.DivideByZeroException>例外狀況。 傳回浮點除法<xref:System.Double.NaN>。  
  
## <a name="equivalent-formula"></a>對等的公式  
 運算式`a Mod b`相當於下列公式：  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>浮點不精確而受到  
 當您使用浮點數時，請記得它們在記憶體中不一定有的精確的十進位表示法。 這可能會導致非預期的結果從某些作業，例如值比較而`Mod`運算子。 如需詳細資訊，請參閱[疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## <a name="overloading"></a>多載化  
 `Mod`運算子可以是*多載*，這表示類別或結構可以重新定義它的行為。 如果您的程式碼適用於`Mod`至類別或結構，其中包含這類多載，這個執行個體，請務必了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Mod`運算子將兩數相除並只傳回餘數。 如果任一個數字是浮點數，結果會是代表餘數的浮點數。  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範可能會不精確而受到浮點數運算元。 在第一個陳述式中，運算元都是`Double`，而且 0.2 無限重複的二進位小數 0.20000000000000001 預存值。 在第二個陳述式中，常值類型字元`D`強制兩個運算元`Decimal`，0.2 且精確地表示法。  
  
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
