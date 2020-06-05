---
title: Byte 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 97acd1bc2ff29bac6588216b9ee4a4f187078815
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374313"
---
# <a name="byte-data-type-visual-basic"></a>Byte 資料類型（Visual Basic）

保存不帶正負號的8位（1個位元組）整數，其值介於0到255之間。

## <a name="remarks"></a>備註

使用 `Byte` 資料類型來包含二進位資料。  
  
`Byte` 的預設值為 0。

## <a name="literal-assignments"></a>常值指派

您可以藉 `Byte` 由指派十進位常值、十六進位常值、八進位常值，或二進位常值（從 Visual Basic 2017）來宣告和初始化變數。 如果整數常值超出的範圍 `Byte` （亦即，如果小於 <xref:System.Byte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Byte.MaxValue?displayProperty=nameWithType> ），就會發生編譯錯誤。

在下列範例中，等於201的整數（以十進位、十六進位和二進位常值表示）會從[整數](integer-data-type.md)隱含地轉換為 `byte` 值。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> 您可以使用前置詞 `&h` 或 `&H` 來表示十六進位常值、前置詞 `&b` 或表示 `&B` 二進位常值，以及前置詞 `&o` 或 `&O` 來表示八進位常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元 `_` 做為數位分隔符號來增強可讀性，如下列範例所示。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

從 Visual Basic 15.5 開始，您也可以使用底線字元（ `_` ）做為前置詞和十六進位、二進位或八進位數位之間的前置分隔符號。 例如：

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>程式設計提示

- **負數。** 因為 `Byte` 是不帶正負號的類型，所以不能代表負數。 如果您 `-` 在評估為類型的運算式上使用一元減號（）運算子 `Byte` ，Visual Basic 會將運算式轉換為 `Short` first。
  
- **格式轉換。** 當 Visual Basic 讀取或寫入檔案時，或當它呼叫 Dll、方法和屬性時，可以在資料格式之間自動轉換。 儲存在變數和陣列中的二進位資料 `Byte` 會在這類格式轉換期間保留。 您不應該將 `String` 變數用於二進位資料，因為在 ANSI 和 Unicode 格式之間轉換時，其內容可能會損毀。

- **加寬.** `Byte`資料類型會擴大為 `Short` 、 `UShort` 、 `Integer` 、 `UInteger` 、 `Long` 、、、 `ULong` `Decimal` `Single` 或 `Double` 。 這表示您可以轉換 `Byte` 成這些類型的任何一種，而不會遇到 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。
  
- **輸入字元。** `Byte`沒有常數值型別字元或識別項型別字元。

- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.Byte?displayProperty=nameWithType> 結構。

## <a name="example"></a>範例

 在下列範例中， `b` 是一個 `Byte` 變數。 語句會示範變數的範圍，以及對其進行位移位運算子的應用。

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>另請參閱

- <xref:System.Byte?displayProperty=nameWithType>
- [資料類型](index.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [轉換摘要](../keywords/conversion-summary.md)
- [有效率地使用資料類型](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
