---
title: Decimal 資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: bab5a0bd7e0a85d550362bc3c1166566f6dcb81b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512777"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal 資料類型 (Visual Basic)

保存帶正負號的128位 (16 位元組) 值, 其代表以10的變數乘冪來調整的96位 (12 位元組) 整數。 縮放比例會指定小數點右邊的位數;其範圍從0到28。 若小數位數為 0 (不含小數點), 則最大的可能值為 +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28)。 若有28位小數位數, 最大值為 +/-7.9228162514264337593543950335, 而最小非零值為 +/-0.0000000000000000000000000001 (+/-1E-28)。

## <a name="remarks"></a>備註

`Decimal`資料類型會提供數位的最大有效位數。 最多可支援29個有效位數, 而且可以代表超過 7.9228 x 10 ^ 28 的值。 它特別適合需要大量數位但無法容忍進位誤差的計算 (例如財務)。

`Decimal` 的預設值為 0。

## <a name="programming-tips"></a>程式設計提示

- **精密.** `Decimal`不是浮點資料類型。 `Decimal`結構會保存一個二進位整數值, 加上一個正負號位和一個整數縮放因素, 指定值的哪個部分是小數部分。 因此, `Decimal`數位在記憶體中的表示方式比浮點類型 (`Single`和`Double`) 更精確。

- **效能。** `Decimal`資料類型是所有數數值型別的最慢。 在選擇資料類型之前, 您應該先衡量精確度與效能的重要性。

- **加寬.** 資料類型會擴大至`Single`或`Double`。 `Decimal` 這表示您可以在`Decimal`不<xref:System.OverflowException?displayProperty=nameWithType>發生錯誤的情況下, 轉換成其中一種類型。

- **尾端零。** Visual Basic 不會在`Decimal`常值中儲存尾端零。 不過, 變數`Decimal`會保留任何尾端零的計算。 下列範例將說明這點。

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  上述範例`MsgBox`中的輸出如下所示:

  ```
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **輸入字元。** 將常值類型字元 `D` 附加到常值，會強制其成為 `Decimal` 資料類型。 將識別項類型字元 `@` 附加到任何識別項，會強制其成為 `Decimal`。

- **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Decimal?displayProperty=nameWithType> 結構。

## <a name="range"></a>Range
 您可能需要使用`D`類型字元, 將大數值`Decimal`指派給變數或常數。 這項需求是因為編譯器會將常值`Long`解讀為, 除非常數值型別字元遵循常值, 如下列範例所示。

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

的宣告`Long`不會產生溢位, 因為指派給它的值落在的範圍內。 `bigDec1` 此`Long`值可指派`Decimal`給變數。

的宣告`Long`會產生溢位錯誤,因為指派給它的值對`bigDec2`而言太大。 因為數值常值無法先解讀為`Long`, 所以無法將它指派`Decimal`給變數。

對於`bigDec3`, 常數值型別字元`D`會強制編譯器將常值`Decimal`解讀成, 而不是做為`Long`, 藉此解決此問題。

## <a name="see-also"></a>另請參閱

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [Single 資料類型](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
