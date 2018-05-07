---
title: Integer 資料類型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1846153375b19b773fedaf056a009f28ab94a4d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="integer-data-type-visual-basic"></a>Integer 資料類型 (Visual Basic)
保存帶正負號的 32 位元 (4 位元組) 整數，值的範圍從 -2,147,483,648 到 2,147,483,647。  
  
## <a name="remarks"></a>備註
 `Integer` 資料類型可對 32 位元處理器提供最佳效能。 其他整數類資料類型在記憶體中載入和儲存的速度較慢。  
  
 `Integer` 的預設值為 0。  

## <a name="literal-assignments"></a>常值的指派

您可以宣告和初始化`Integer`變數將其指派十進位常值、 十六進位常值、 八進位常值，或是 （從開始使用 Visual Basic 2017） 二進位常值。 如果整數常值超出 `Integer` 的範圍 (亦即，如果小於 <xref:System.Int32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，如果整數等於 16,342，即表示 `Integer` 值指派了十進位、十六進位和二進位常值。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> 使用前置詞`&h`或`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元， `_`，當做數字分隔符號，以提升可讀性，如下列範例所示。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 做為前置詞和十六進位、 二進位或八進位的數字之間的前置分隔符號。 例如: 

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

數值常值也可以包含`I`[類型字元](../../programming-guide\language-features\data-types/type-characters.md)代表`Integer`資料類型，如下列範例所示。

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>程式設計提示

-   **Interop 考量。** 如果您要使用的元件不是撰寫.NET framework，例如 Automation 或 COM 物件，請記住，`Integer`在其他環境中都有不同的資料寬度 （16 位元）。 如果您要將 16 位元引數傳遞至這類元件，請在新的 Visual Basic 程式碼中將它宣告為 `Short`，而不是 `Integer`。  
  
-   **擴展。** `Integer` 資料類型可擴展為 `Long`、`Decimal`、`Single` 或 `Double`。 這表示，您可以將 `Integer` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。  
  
-   **類型字元。** 將常值類型字元 `I` 附加到常值，會強制其成為 `Integer` 資料類型。 將識別項類型字元 `%` 附加到任何識別項，會強制其成為 `Integer`。  
  
-   **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Int32?displayProperty=nameWithType> 結構。  
  
## <a name="range"></a>範圍

如果您嘗試將整數類資料類型的變數設定為超出該類型範圍的數字，則會發生錯誤。 如果您嘗試將它設定為分數，則數字就會四捨五入為最接近的整數值。 如果數字與兩個整數值同樣接近，則該直將會四捨五入為最接近的雙數。 這種行為會將一致四捨五入單向中點值得出的四捨五入錯誤降至最低。 下列程式碼將示範四捨五入的範例。  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>另請參閱

<xref:System.Int32?displayProperty=nameWithType>   
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Long 資料類型](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
