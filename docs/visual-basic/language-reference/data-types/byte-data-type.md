---
title: Byte 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344083"
---
# <a name="byte-data-type-visual-basic"></a>Byte 資料類型（Visual Basic）

保存不帶正負號的8位（1個位元組）整數，其值介於0到255之間。

## <a name="remarks"></a>備註

請使用 `Byte` 資料類型來包含二進位資料。  
  
`Byte` 的預設值為 0。

## <a name="literal-assignments"></a>常值指派

您可以藉由指派十進位常值、十六進位常值、八進位常值，或二進位常值（從 Visual Basic 2017）來宣告和初始化 `Byte` 變數。 如果整數常值超出 `Byte` 的範圍（亦即，如果小於 <xref:System.Byte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Byte.MaxValue?displayProperty=nameWithType>），就會發生編譯錯誤。

在下列範例中，等於201的整數（以十進位、十六進位和二進位常值表示）會從[整數](integer-data-type.md)隱含地轉換成 `byte` 值。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> 您可以使用前置詞 `&h` 或 `&H` 來表示十六進位常值、前置詞 `&b` 或 `&B` 來表示二進位常值，而前置詞 `&o` 或 `&O` 表示八進位常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元（`_`）做為數位分隔符號，以增強可讀性，如下列範例所示。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

從 Visual Basic 15.5 開始，您也可以使用底線字元（`_`）做為前置詞和十六進位、二進位或八進位數位之間的前置分隔符號。 例如：

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>程式設計提示

- **負數。** 因為 `Byte` 是不帶正負號的類型，所以不能代表負數。 如果您在評估為類型 `Byte`的運算式上使用一元減號（`-`）運算子，Visual Basic 會先將運算式轉換成 `Short`。
  
- **格式轉換。** 當 Visual Basic 讀取或寫入檔案時，或當它呼叫 Dll、方法和屬性時，可以在資料格式之間自動轉換。 在這類格式轉換期間，會保留儲存在 `Byte` 變數和陣列中的二進位資料。 您不應該使用二進位資料的 `String` 變數，因為在 ANSI 和 Unicode 格式之間轉換時，其內容可能會損毀。

- **加寬.** `Byte` 資料類型會擴大至 `Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`或 `Double`。 這表示您可以將 `Byte` 轉換成這些類型的任何一種，而不會遇到 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。
  
- **輸入字元。** `Byte` 沒有常數值型別字元或識別項型別字元。

- **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Byte?displayProperty=nameWithType> 結構。

## <a name="example"></a>範例

 在下列範例中，`b` 是 `Byte` 變數。 語句會示範變數的範圍，以及對其進行位移位運算子的應用。

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>請參閱

- <xref:System.Byte?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
