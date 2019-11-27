---
title: Decimal 資料類型
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
ms.openlocfilehash: 6d62bcc1d043b45c0fc30154d9dc633b998f97b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344036"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal 資料類型 (Visual Basic)

保存帶正負號的 128 位元 (16 位元組) 值，代表可變倍率 10 倍的 96 位元 (12 位元組) 整數。 縮放比例會指定小數點右邊的位數;其範圍從0到28。 若小數位數為0（不含小數點），則最大的可能值為 +/-79228162514264337593543950335 （+/-7.9228162514264337593543950335E + 28）。 若有28位小數位數，最大值為 +/-7.9228162514264337593543950335，而最小非零值為 +/-0.0000000000000000000000000001 （+/-1E-28）。

## <a name="remarks"></a>備註

`Decimal` 資料類型會提供數位的最大有效位數。 最多可支援29個有效位數，而且可以代表超過 7.9228 x 10 ^ 28 的值。 它特別適合需要大量數位但無法容忍進位誤差的計算（例如財務）。

`Decimal` 的預設值為 0。

## <a name="programming-tips"></a>程式設計提示

- **精密.** `Decimal` 不是浮點資料類型。 `Decimal` 結構會保存一個二進位整數值，加上正負號位和整數的縮放因數，以指定值的哪個部分為小數部分。 因此，`Decimal` 數位在記憶體中的表示方式比浮點類型（`Single` 和 `Double`）更精確。

- **效能。** `Decimal` 資料類型是所有數數值型別的最慢。 在選擇資料類型之前，您應該先衡量精確度與效能的重要性。

- **加寬.** `Decimal` 資料類型會擴大至 `Single` 或 `Double`。 這表示您可以將 `Decimal` 轉換成其中一種類型，而不會遇到 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。

- **尾端零。** Visual Basic 不會在 `Decimal` 常值中儲存尾端零。 不過，`Decimal` 變數會保留任何尾端零的計算。 下列範例將說明這點。

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  上述範例中的 `MsgBox` 輸出如下所示：

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **輸入字元。** 將常值類型字元 `D` 附加到常值，會強制其成為 `Decimal` 資料類型。 將識別項類型字元 `@` 附加到任何識別項，會強制其成為 `Decimal`。

- **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Decimal?displayProperty=nameWithType> 結構。

## <a name="range"></a>範圍

 您可能需要使用 `D` 類型字元，將大數值指派給 `Decimal` 變數或常數。 這項需求是因為編譯器會將常值轉譯為 `Long`，除非常數值型別字元遵循常值，如下列範例所示。

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

`bigDec1` 的宣告不會產生溢位，因為指派給它的值落在 `Long`的範圍內。 `Long` 值可指派給 `Decimal` 變數。

`bigDec2` 的宣告會產生溢位錯誤，因為指派給它的值對 `Long`而言太大。 因為數值常值無法先解讀為 `Long`，所以無法將它指派給 `Decimal` 變數。

針對 `bigDec3`，常數值型別字元 `D` 藉由強制編譯器將常值轉譯為 `Decimal` 而不是 `Long`來解決此問題。

## <a name="see-also"></a>請參閱

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [Single 資料類型](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
