---
title: ULong 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400698"
---
# <a name="ulong-data-type-visual-basic"></a>ULONG 資料型別（可視基本）

持有未簽名的 64 位（8 位元組）整數，價值範圍為 0 到 18，446，744，073，709，551，615（超過 1.84 倍 10 = 19）。

## <a name="remarks"></a>備註

使用`ULong`資料類型包含對於 的`UInteger`二進位資料太大或最大可能的不帶正負號的整數值。

`ULong` 的預設值為 0。

## <a name="literal-assignments"></a>文本分配

您可以通過為其分配十進位文本、`ULong`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。 如果整數常值超出 `ULong` 的範圍 (亦即，如果小於 <xref:System.UInt64.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、十六進位和二進位常值表示的 7,934,076,125 整數，會指派給 `ULong` 值。

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> `&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。 例如：

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

數位文本還可以包括`UL`或`ul`[類型字元](../../programming-guide/language-features/data-types/type-characters.md)來表示`ULong`資料類型，如下例所示。

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>程式設計提示

- **負數。** 因為它是`ULong`無符號類型，它不能表示負數。 如果在計算為鍵入`-``ULong`的運算式上使用一元減號 （ ） 運算子，Visual Basic 將運算式轉換為`Decimal`第一個運算式。

- **CLS 合規性。** 資料類型`ULong`不是[通用語言規範](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（CLS） 的一部分，因此符合 CLS 的代碼不能使用使用它的元件。

- **Interop 考量：** 如果要與未為 .NET 框架編寫的元件（例如自動化或 COM 物件）介面，請記住，例如在其他`ulong`環境中具有不同資料寬度（32 位）的類型。 如果要將 32 位參數傳遞給此類元件，請將其聲明為`UInteger`託管 Visual `ULong` Basic 代碼中而不是。

  此外，自動化不支援 Windows 95、Windows 98、Windows ME 或 Windows 2000 上的 64 位整數。 不能將 Visual Basic`ULong`參數傳遞給這些平臺上的自動化元件。

- **擴大。** 資料類型`ULong`擴展到`Decimal`.`Single`和`Double`。 這意味著您可以轉換為`ULong`任何這些類型的，而不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。

- **鍵入字元。** 將常值型別字元`UL`追加到文本強制它到`ULong`資料類型。 `ULong`沒有識別項型別字元。

- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.UInt64?displayProperty=nameWithType> 結構。

## <a name="see-also"></a>另請參閱

- <xref:System.UInt64>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
