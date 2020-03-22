---
title: SByte 資料類型
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400789"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte 資料類型（可視基本）

保留在 -128 到 127 之間的值範圍的已簽名 8 位（1 位元組）整數。

## <a name="remarks"></a>備註

使用`SByte`資料類型包含不需要 的完整資料寬度`Integer`甚至一半資料寬度的`Short`整數值。 在某些情況下，通用語言運行時可能能夠將`SByte`變數緊密打包在一起並節省記憶體消耗。

`SByte` 的預設值為 0。

## <a name="literal-assignments"></a>文本分配

您可以通過為其分配十進位文本、`SByte`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。

在下面的示例中，等於 -102 的整數，表示為十進位、十六進位和二進位文本`SByte`。 此示例要求您使用`/removeintchecks`編譯器開關進行編譯。

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> `&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。 例如：

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

如果整數常值超出 `SByte` 的範圍 (亦即，如果小於 <xref:System.SByte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.SByte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。 當整數文本沒有尾碼時，將推斷出[整數](integer-data-type.md)。 如果整數文本超出`Integer`類型的範圍，則推斷為[Long。](long-data-type.md) 這意味著，在前面的示例中，數位文本`0x9A`和`0b10011010`轉換為 32 位簽名整數，值為 156，超過<xref:System.SByte.MaxValue?displayProperty=nameWithType>。 要成功編譯像這樣將非十進位整數分配給 的代碼`SByte`，可以執行以下任一操作：

- 通過編譯`/removeintchecks`編譯器開關禁用整數邊界檢查。

- 使用[類型字元](../../programming-guide/language-features/data-types/type-characters.md)顯式定義要分配給 的文本`SByte`值。 下面的示例將負文本`Short`值分配給 。 `SByte` 請注意，對於負數，必須設置數位文本的高階字的高階位。 在我們的示例中，這是文本`Short`值的第 15 位。

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>程式設計提示

- **CLS 合規性。** 資料類型`SByte`不是[通用語言規範](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（CLS） 的一部分，因此符合 CLS 的代碼不能使用使用它的元件。

- **擴大。** 資料類型`SByte`擴展到`Short`、、、、、、、`Integer``Long``Decimal``Single`和`Double`。 這意味著您可以轉換為`SByte`任何這些類型的，而不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。

- **鍵入字元。** `SByte`沒有常值型別字元或識別項型別字元。

- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.SByte?displayProperty=nameWithType> 結構。

## <a name="see-also"></a>另請參閱

- <xref:System.SByte?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [整數資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long 資料類型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
