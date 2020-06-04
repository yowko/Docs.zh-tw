---
title: Mod 運算子
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
ms.openlocfilehash: 32065567799b023556a018ae2f5ba338796e0b49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401507"
---
# <a name="mod-operator-visual-basic"></a>Mod 運算子（Visual Basic）

將兩個數字相除，然後只傳回餘數。

## <a name="syntax"></a>語法

```vb
result = number1 Mod number2
```

## <a name="parts"></a>組件

`result` \
必要。 任何數值變數或屬性。

`number1` \
必要。 任何數值運算式。

`number2` \
必要。 任何數值運算式。

## <a name="supported-types"></a>支援的類型

所有數值類型。 這包括不帶正負號的和浮點類型，以及 `Decimal` 。

## <a name="result"></a>結果

結果是除以之後的餘數 `number1` `number2` 。 例如，運算式會 `14 Mod 4` 評估為2。

> [!NOTE]
> 在數學中，*餘數*與*模數*之間會有不同的結果，而負數的結果則有所不同。 `Mod`Visual Basic、.NET Framework `op_Modulus` 運算子和基礎[rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL 指令中的運算子都會執行餘數運算。

作業的結果 `Mod` 會保留被除數、和的正負號， `number1` 因此它可以是正數或負數。 結果一律在範圍（- `number2` 、 `number2` ）、獨佔。 例如：

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

如果 `number1` 或 `number2` 是浮點值，則會傳回除法的浮點餘數。 結果的資料類型是最小的資料類型，可以保存與和資料類型相除所產生的所有可能值 `number1` `number2` 。

如果 `number1` 或 `number2` 評估為[沒有任何](../nothing.md)值，則會將它視為零。

相關的運算子包括下列各項：

- [\ 運算子（Visual Basic）](integer-division-operator.md)會傳回除法的整數商。 例如，運算式會 `14 \ 4` 評估為3。

- [/運算子（Visual Basic）](floating-point-division-operator.md)會傳回完整的商，包括餘數，做為浮點數。 例如，運算式會 `14 / 4` 評估為3.5。

## <a name="attempted-division-by-zero"></a>嘗試除數為零

如果 `number2` 評估為零，則運算子的行為 `Mod` 取決於運算元的資料類型：

- <xref:System.DivideByZeroException>如果 `number2` 無法在編譯時期判斷，則整數除法會擲回例外狀況， `BC30542 Division by zero occurred while evaluating this expression` 如果 `number2` 在編譯時期評估為零，則會產生編譯時期錯誤。
- 浮點除法會傳回 <xref:System.Double.NaN?displayProperty=nameWithType> 。

## <a name="equivalent-formula"></a>對等公式

運算式 `a Mod b` 相當於下列其中一個公式：

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>浮點不精確

當您使用浮點數時，請記住，記憶體中不一定有精確的十進位標記法。 這可能會導致某些作業產生非預期的結果，例如值比較和 `Mod` 運算子。 如需詳細資訊，請參閱針對[資料類型進行疑難排解](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)。

## <a name="overloading"></a>多載化

`Mod`運算子可以多載*overloaded*，這表示類別或結構可以重新定義其行為。 如果您的程式碼適用于包含這類多載的 `Mod` 類別或結構實例，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。

## <a name="example"></a>範例

下列範例會使用 `Mod` 運算子來將兩個數字相除，然後只傳回餘數。 如果任一個數位是浮點數，則結果會是代表餘數的浮點數。

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>範例

下列範例示範浮點運算元的潛在不精確。 在第一個語句中，運算元是 `Double` ，而0.2 是具有儲存值0.20000000000000001 的無限重複二進位分數。 在第二個語句中，常數值型別字元會 `D` 強制執行這兩個運算元 `Decimal` ，而0.2 具有精確的標記法。

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [疑難排解資料類型的問題](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic 的算術運算子](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ 運算子（Visual Basic）](integer-division-operator.md)
