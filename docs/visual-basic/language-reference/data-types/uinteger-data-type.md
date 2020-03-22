---
title: UInteger 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400782"
---
# <a name="uinteger-data-type"></a>UInteger 資料類型

保存未簽名的 32 位（4 位元組）整數，其值範圍為 0 到 4，294，967，295。

## <a name="remarks"></a>備註

資料類型`UInteger`提供最有效的資料寬度中的最大未簽名值。

`UInteger` 的預設值為 0。

## <a name="literal-assignments"></a>文本分配

您可以通過為其分配十進位文本、`UInteger`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。 如果整數常值超出 `UInteger` 的範圍 (亦即，如果小於 <xref:System.UInt32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、十六進位和二進位常值表示的 3,000,000,000 整數，會指派給 `UInteger` 值。

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> `&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。 例如：

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

數位文本還可以包括`UI`或`ui`[類型字元](../../programming-guide/language-features/data-types/type-characters.md)來表示`UInteger`資料類型，如下例所示。

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>程式設計提示

和`UInteger``Integer`資料類型在 32 位處理器上提供最佳性能，因為較小的整數類型 （、、`UShort``Short``Byte`和`SByte`）即使使用較少的位，也需要更多的時間來載入、存儲和提取。

- **負數。** 因為它是`UInteger`無符號類型，它不能表示負數。 如果在計算為鍵入`-``UInteger`的運算式上使用一元減號 （ ） 運算子，Visual Basic 將運算式轉換為`Long`第一個運算式。

- **CLS 合規性。** 資料類型`UInteger`不是[通用語言規範](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（CLS） 的一部分，因此符合 CLS 的代碼不能使用使用它的元件。

- **Interop 考量：** 如果要與未為 .NET 框架編寫的元件（例如自動化或 COM 物件）介面，請記住，例如在其他`uint`環境中具有不同資料寬度（16 位）的類型。 如果要將 16 位參數傳遞給此類元件，請將其聲明為`UShort`託管 Visual `UInteger` Basic 代碼中而不是。

- **擴大。** 資料類型`UInteger`擴展到`Long` `ULong`、、、`Decimal``Single`和`Double`。 這意味著您可以轉換為`UInteger`任何這些類型的，而不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。

- **鍵入字元。** 將常值型別字元`UI`追加到文本強制它到`UInteger`資料類型。 `UInteger`沒有識別項型別字元。

- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.UInt32?displayProperty=nameWithType> 結構。

## <a name="see-also"></a>另請參閱

- <xref:System.UInt32>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
