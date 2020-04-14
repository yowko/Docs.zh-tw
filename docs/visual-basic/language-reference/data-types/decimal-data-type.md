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
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243319"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal 資料類型 (Visual Basic)

保存帶正負號的 128 位元 (16 位元組) 值，代表可變倍率 10 倍的 96 位元 (12 位元組) 整數。 縮放因數指定小數點右側的數字數;範圍從 0 到 28。 其刻度為 0(無小數位數),最大可能值為 +/-79,228,162,514,264,337,593,543,950,335 (+/-7.922816251423355353535535553355+28)。 對於 28 位小數,最大值為 +//922816251426433759355439555555555555303335,最小非零值為 +//000000000000000000000000001(+//-1E-28)。

## <a name="remarks"></a>備註

數據類型`Decimal`為數位提供最多數量的重要數位。 它最多支援 29 位有效數位,可以表示大於 7.9228 x 10^28 的值。 它特別適用於需要大量數位但不能容忍捨入錯誤的計算(如財務)。

`Decimal` 的預設值為 0。

## <a name="programming-tips"></a>程式設計提示

- **精度。** `Decimal`不是浮點數據類型。 結構`Decimal`包含二進位整數值,以及符號位和整數縮放因數,指定值的哪一部分是十進位數。 因此,與浮`Decimal`點類型`Single``Double`(和 ) 相比,數位在記憶體中的表示法更精確。

- **效能。** 數據類型`Decimal`是所有數值類型中最慢的。 在選擇數據類型之前,應權衡精度與性能的重要性。

- **擴大。** 資料型`Decimal`態延伸`Single`到`Double`或 。 這意味著您可以轉換為`Decimal`其中任<xref:System.OverflowException?displayProperty=nameWithType>一類型,而不會遇到錯誤。

- **尾隨零。** 視覺基礎不會在`Decimal`文本中存儲尾隨零。 但是,`Decimal`變數保留在計算中獲取的任何尾隨零。 下列範例將說明這點。

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  上`MsgBox`例中的輸出如下:

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **鍵入字元。** 將常值類型字元 `D` 附加到常值，會強制其成為 `Decimal` 資料類型。 將識別項類型字元 `@` 附加到任何識別項，會強制其成為 `Decimal`。

- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.Decimal?displayProperty=nameWithType> 結構。

## <a name="range"></a>範圍

 您可能需要使用`D`類型字元將大值分配給`Decimal`變數或常量。 此要求是因為編譯器將文本解釋為`Long`除非文本類型字元遵循文本,如下例所示。

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

的聲明`bigDec1`不會生成溢出,因為分配給它的值`Long`在 可以將`Long`該值分配`Decimal`給 變數。

的聲明`bigDec2`生成溢出錯誤,因為分配給它的值`Long`對於 來說太大。 由於數位文字不能首先解釋為`Long`, 無法將其`Decimal`分配給 變數。

對於`bigDec3`,文本類型字`D`元 通過強制編譯器將文本`Decimal`解釋為 而不是解說,從而解決`Long`了問題。

## <a name="see-also"></a>另請參閱

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [Single 資料類型](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
