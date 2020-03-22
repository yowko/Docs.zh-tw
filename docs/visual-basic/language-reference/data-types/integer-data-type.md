---
title: Integer 資料類型
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
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400733"
---
# <a name="integer-data-type-visual-basic"></a>整數資料類型（可視基本）

保存帶正負號的 32 位元 (4 位元組) 整數，值的範圍從 -2,147,483,648 到 2,147,483,647。  
  
## <a name="remarks"></a>備註

 `Integer` 資料類型可對 32 位元處理器提供最佳效能。 其他整數類資料類型在記憶體中載入和儲存的速度較慢。  
  
 `Integer` 的預設值為 0。  

## <a name="literal-assignments"></a>文本分配

您可以通過為其分配十進位文本、`Integer`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。 如果整數常值超出 `Integer` 的範圍 (亦即，如果小於 <xref:System.Int32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、十六進位和二進位常值表示的 90,946 整數，會指派給 `Integer` 值。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> `&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。 例如：

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

數位文本還可以包括`I`表示`Integer`資料類型[的類型字元](../../programming-guide/language-features/data-types/type-characters.md)，如下例所示。

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>程式設計提示

- **Interop 考量：** 如果要與未為 .NET 框架編寫的元件（如自動化或 COM 物件）介面，請記住，`Integer`在其他環境中具有不同的資料寬度（16 位）。 如果您要將 16 位元引數傳遞至這類元件，請在新的 Visual Basic 程式碼中將它宣告為 `Short`，而不是 `Integer`。  
  
- **擴大。** `Integer` 資料類型可擴展為 `Long`、`Decimal`、`Single` 或 `Double`。 這表示，您可以將 `Integer` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。  
  
- **鍵入字元。** 將常值類型字元 `I` 附加到常值，會強制其成為 `Integer` 資料類型。 將識別項類型字元 `%` 附加到任何識別項，會強制其成為 `Integer`。  
  
- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.Int32?displayProperty=nameWithType> 結構。  
  
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

- <xref:System.Int32?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [Long 資料類型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
