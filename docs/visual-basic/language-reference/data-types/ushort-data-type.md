---
title: UShort 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343858"
---
# <a name="ushort-data-type-visual-basic"></a>UShort 資料類型（Visual Basic）

保留不帶正負號的16位（2位元組）整數，範圍介於0到65535之間。  
  
## <a name="remarks"></a>備註

 請使用 `UShort` 資料類型，以包含對 `Byte`而言太大的二進位資料。  
  
 `UShort` 的預設值為 0。  

## <a name="literal-assignments"></a>常值指派

您可以藉由指派十進位常值、十六進位常值、八進位常值，或二進位常值（從 Visual Basic 2017）來宣告和初始化 `UShort` 變數。 如果整數常值超出 `UShort` 的範圍 (亦即，如果小於 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、十六進位和二進位常值表示的整數等於65034，會指派給 `UShort` 值。
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> 您可以使用前置詞 `&h` 或 `&H` 來表示十六進位常值、前置詞 `&b` 或 `&B` 來表示二進位常值，而前置詞 `&o` 或 `&O` 表示八進位常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元（`_`）做為數位分隔符號，以增強可讀性，如下列範例所示。

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

從 Visual Basic 15.5 開始，您也可以使用底線字元（`_`）做為前置詞和十六進位、二進位或八進位數位之間的前置分隔符號。 例如：

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

數值常值也可以包含 `US` 或 `us`[類型字元](../../programming-guide/language-features/data-types/type-characters.md)來表示 `UShort` 資料類型，如下列範例所示。

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>程式設計提示
  
- **負數。** 因為 `UShort` 是不帶正負號的類型，所以不能代表負數。 如果您在評估為類型 `UShort`的運算式上使用一元減號（`-`）運算子，Visual Basic 會先將運算式轉換成 `Integer`。  
  
- **CLS 合規性。** `UShort` 資料類型不是[Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) （CLS）的一部分，因此符合 cls 標準的程式碼無法使用它所使用的元件。
  
- **加寬.** `UShort` 資料類型會擴大至 `Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`和 `Double`。 這表示您可以將 `UShort` 轉換成這些類型的任何一種，而不會遇到 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。  
  
- **輸入字元。** 將常數值型別字元附加到常值 `US` 會強制其成為 `UShort` 的資料類型。 `UShort` 沒有識別項型別字元。  
  
- **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.UInt16?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>請參閱

- <xref:System.UInt16>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
