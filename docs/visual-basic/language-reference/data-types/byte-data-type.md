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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400740"
---
# <a name="byte-data-type-visual-basic"></a>位元組資料類型（可視基本）

保存未簽名的 8 位（1 位元組）整數，其值範圍為 0 到 255。

## <a name="remarks"></a>備註

使用`Byte`資料類型包含二進位資料。  
  
`Byte` 的預設值為 0。

## <a name="literal-assignments"></a>文本分配

您可以通過為其分配十進位文本、`Byte`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。 如果積分文本超出 的範圍`Byte`（即，如果它小於<xref:System.Byte.MinValue?displayProperty=nameWithType>或大於<xref:System.Byte.MaxValue?displayProperty=nameWithType>），則會發生編譯錯誤。

在下面的示例中，等於 201 的整數表示為十進位、十六進位和二進位文本，從[整數](integer-data-type.md)隱式轉換為`byte`值。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> `&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。 例如：

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>程式設計提示

- **負數。** 因為它是`Byte`無符號類型，它不能表示負數。 如果在計算為鍵入`-``Byte`的運算式上使用一元減號 （ ） 運算子，Visual Basic 將運算式轉換為`Short`第一個運算式。
  
- **格式轉換。** 當 Visual Basic 讀取或寫入檔時，或者當它調用 DLL、方法和屬性時，它可以在資料格式之間自動轉換。 存儲在變數和陣列`Byte`中的二進位資料在此類格式轉換期間保留。 不應將`String`變數用於二進位資料，因為其內容在 ANSI 和 Unicode 格式之間的轉換過程中可能會損壞。

- **擴大。** 資料類型`Byte``Short`擴展到 、 `UShort` `Integer`、 、 `UInteger`、 `Long` `ULong`、 `Decimal` `Single`、 `Double`、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 這意味著您可以轉換為`Byte`任何這些類型的，而不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。
  
- **鍵入字元。** `Byte`沒有常值型別字元或識別項型別字元。

- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.Byte?displayProperty=nameWithType> 結構。

## <a name="example"></a>範例

 在下面的示例中，`b`是一個`Byte`變數。 這些語句演示了變數的範圍以及位移位運算子對變數的應用。

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>另請參閱

- <xref:System.Byte?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
