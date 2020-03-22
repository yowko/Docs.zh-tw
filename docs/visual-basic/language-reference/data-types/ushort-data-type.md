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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400691"
---
# <a name="ushort-data-type-visual-basic"></a>UShort 資料類型（可視基本）

保存未簽名的 16 位（2 位元組）整數，其值範圍為 0 到 65，535。  
  
## <a name="remarks"></a>備註

 使用`UShort`資料類型包含的二進位資料太大。 `Byte`  
  
 `UShort` 的預設值為 0。  

## <a name="literal-assignments"></a>文本分配

您可以通過為其分配十進位文本、`UShort`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。 如果整數常值超出 `UShort` 的範圍 (亦即，如果小於 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下面的示例中，等於 65，034 的整數，表示為十進位、十六進位和二進位文本`UShort`。
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> `&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。 例如：

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

數位文本還可以包括`US`或`us`[類型字元](../../programming-guide/language-features/data-types/type-characters.md)來表示`UShort`資料類型，如下例所示。

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>程式設計提示
  
- **負數。** 因為它是`UShort`無符號類型，它不能表示負數。 如果在計算為鍵入`-``UShort`的運算式上使用一元減號 （ ） 運算子，Visual Basic 將運算式轉換為`Integer`第一個運算式。  
  
- **CLS 合規性。** 資料類型`UShort`不是[通用語言規範](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（CLS） 的一部分，因此符合 CLS 的代碼不能使用使用它的元件。
  
- **擴大。** 資料類型`UShort`擴展到`Integer`、、、、、、、、`Single``Double``UInteger``Long``ULong``Decimal`和 。 這意味著您可以轉換為`UShort`任何這些類型的，而不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。  
  
- **鍵入字元。** 將常值型別字元`US`追加到文本強制它到`UShort`資料類型。 `UShort`沒有識別項型別字元。  
  
- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.UInt16?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.UInt16>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
