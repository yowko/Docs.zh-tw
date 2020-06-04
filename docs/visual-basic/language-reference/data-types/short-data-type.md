---
title: Short 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 176d27c86127dac1d9c9c0231790f7a5c2a2fefc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415553"
---
# <a name="short-data-type-visual-basic"></a>Short 資料類型（Visual Basic）

保存帶正負號的16位（2位元組）整數，其範圍介於-32768 到32767之間。  
  
## <a name="remarks"></a>備註  

 使用 `Short` 資料類型來包含不需要完整資料寬度的整數值 `Integer` 。 在某些情況下，通用語言執行時間可以將您的 `Short` 變數緊密地封裝在一起，並節省記憶體耗用量。  
  
 `Short` 的預設值為 0。  
  
## <a name="literal-assignments"></a>常值指派

您可以藉 `Short` 由指派十進位常值、十六進位常值、八進位常值，或二進位常值（從 Visual Basic 2017）來宣告和初始化變數。 如果整數常值超出 `Short` 的範圍 (亦即，如果小於 <xref:System.Int16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，等於1034的整數（以十進位、十六進位和二進位常值表示）會從[整數](integer-data-type.md)隱含地轉換為 `Short` 值。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> 您可以使用前置詞 `&h` 或 `&H` 來表示十六進位常值、前置詞 `&b` 或表示 `&B` 二進位常值，以及前置詞 `&o` 或 `&O` 來表示八進位常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元 `_` 做為數位分隔符號來增強可讀性，如下列範例所示。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

從 Visual Basic 15.5 開始，您也可以使用底線字元（ `_` ）做為前置詞和十六進位、二進位或八進位數位之間的前置分隔符號。 例如：

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

數值常值也可以包含 `S` [型別字符](../../programming-guide/language-features/data-types/type-characters.md)來表示 `Short` 資料型別，如下列範例所示。

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>程式設計提示

- **加寬.** `Short`資料類型會擴大為 `Integer` 、 `Long` 、 `Decimal` 、 `Single` 或 `Double` 。 這表示，您可以將 `Short` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。  
  
- **輸入字元。** 將常值類型字元 `S` 附加到常值，會強制其成為 `Short` 資料類型。 `Short`沒有識別項型別字元。  
  
- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.Int16?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Int16?displayProperty=nameWithType>
- [資料類型](index.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [轉換摘要](../keywords/conversion-summary.md)
- [Integer 資料類型](integer-data-type.md)
- [Long 資料類型](long-data-type.md)
- [有效率地使用資料類型](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
