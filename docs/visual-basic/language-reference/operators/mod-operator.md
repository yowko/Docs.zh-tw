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
ms.openlocfilehash: c801facd95d93652414409549bb5ff2fa633748b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611531"
---
# <a name="mod-operator-visual-basic"></a>Mod 運算子 (Visual Basic)
將兩個數字相除, 然後只傳回餘數。

## <a name="syntax"></a>語法

```vb
result = number1 Mod number2
```
  
## <a name="parts"></a>組件  
 `result` 必要項。 任何數值變數或屬性。

 `number1` 必要項。 任何數值運算式。

 `number2` 必要項。 任何數值運算式。

## <a name="supported-types"></a>支援的類型
 所有數值類型。 這包括不帶正負號的和浮點類型`Decimal`, 以及。

## <a name="result"></a>結果

結果是`number1` `number2`除以之後的餘數。 例如, 運算式`14 Mod 4`會評估為2。

> [!NOTE]
> 在數學中,*餘數*與*模數*之間會有不同的結果, 而負數的結果則有所不同。 Visual Basic `Mod` 、.NET Framework `op_Modulus`運算子和基礎[rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL 指令中的運算子都會執行餘數運算。

作業的結果`Mod`會保留被除數、 `number1`和的正負號, 因此它可以是正數或負數。 結果一律在範圍 (-`number2`、 `number2`)、獨佔。 例如：

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
 `number1`如果或`number2`是浮點值, 則會傳回除法的浮點餘數。 結果的資料類型是最小的資料類型, 可以保存與`number1`和`number2`資料類型相除所產生的所有可能值。

 如果`number1` 或`number2`評估為[沒有任何](../../../visual-basic/language-reference/nothing.md)值, 則會將它視為零。

 相關的運算子包括下列各項:

- [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)會傳回除法的整數商。 例如, 運算式`14 \ 4`會評估為3。

- [/運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)會傳回完整的商, 包括餘數, 做為浮點數。 例如, 運算式`14 / 4`會評估為3.5。

## <a name="attempted-division-by-zero"></a>嘗試除數為零
 如果`number2`評估為零, 則`Mod`運算子的行為取決於運算元的資料類型:
 - 如果<xref:System.DivideByZeroException> `BC30542    Division by zero occurred while evaluating this expression` `number2`無法在編譯時期判斷, 則整數除法會擲回例外狀況, 如果在編譯時期評估為零, 則會產生編譯時期錯誤。 `number2`
 - 浮點除法<xref:System.Double.NaN?displayProperty=nameWithType>會傳回。

## <a name="equivalent-formula"></a>對等公式
 運算式`a Mod b`相當於下列其中一個公式:

 `a - (b * (a \ b))`

 `a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>浮點不精確
 當您使用浮點數時, 請記住, 記憶體中不一定有精確的十進位標記法。 這可能會導致某些作業產生非預期的結果, 例如值比較和`Mod`運算子。 如需詳細資訊, 請參閱針對[資料類型進行疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。

## <a name="overloading"></a>多載化
 運算子可以多載, 這表示類別或結構可以重新定義其行為。 `Mod` 如果您的程式`Mod`代碼適用于包含這類多載的類別或結構實例, 請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。

## <a name="example"></a>範例
 下列範例會使用`Mod`運算子來將兩個數字相除, 然後只傳回餘數。 如果任一個數位是浮點數, 則結果會是代表餘數的浮點數。

 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>範例
 下列範例示範浮點運算元的潛在不精確。 在第一個語句中, 運算元是`Double`, 而0.2 是具有儲存值0.20000000000000001 的無限重複二進位分數。 在第二個語句中, 常值`D`類型字元會強制`Decimal`執行這兩個運算元, 而0.2 具有精確的標記法。

 [!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [資料類型的疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
