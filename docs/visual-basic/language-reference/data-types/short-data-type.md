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
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400726"
---
# <a name="short-data-type-visual-basic"></a>短資料類型（視覺基本）

持有 16 位（2 位元組）整數，其值範圍從 -32，768 到 32，767。  
  
## <a name="remarks"></a>備註  

 使用`Short`資料類型包含不需要 的完整資料寬度的`Integer`整數值。 在某些情況下，通用語言運行時可以將`Short`變數緊密打包在一起並節省記憶體消耗。  
  
 `Short` 的預設值為 0。  
  
## <a name="literal-assignments"></a>文本分配

您可以通過為其分配十進位文本、`Short`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。 如果整數常值超出 `Short` 的範圍 (亦即，如果小於 <xref:System.Int16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下面的示例中，等於 1，034 的整數表示為十進位、十六進位和二進位文本，從[整數](integer-data-type.md)隱式轉換為`Short`值。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> `&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。 例如：

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

數位文本還可以包括`S`表示`Short`資料類型[的類型字元](../../programming-guide/language-features/data-types/type-characters.md)，如下例所示。

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>程式設計提示

- **擴大。** 資料類型`Short`擴展到`Integer` `Long`、、、、、`Decimal``Single`或`Double`。 這表示，您可以將 `Short` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。  
  
- **鍵入字元。** 將常值類型字元 `S` 附加到常值，會強制其成為 `Short` 資料類型。 `Short`沒有識別項型別字元。  
  
- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.Int16?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Int16?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [整數資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long 資料類型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
