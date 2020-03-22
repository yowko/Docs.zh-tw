---
title: Long 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400810"
---
# <a name="long-data-type-visual-basic"></a>長資料類型（可視基本）

持有已簽名的 64 位（8 位元組）整數，價值範圍為 -9，223，372，036，854，775，808 到 9，223，372，036，854，775，807 （9.2...E=18）。

## <a name="remarks"></a>備註

使用`Long`資料類型包含太大而不適合資料類型的`Integer`整數。

`Long` 的預設值為 0。

## <a name="literal-assignments"></a>文本分配

您可以通過為其分配十進位文本、`Long`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。 如果整數常值超出 `Long` 的範圍 (亦即，如果小於 <xref:System.Int64.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int64.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，如果整數等於 4,294,967,296，即表示 `Long` 值指派了十進位、十六進位和二進位常值。

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> `&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。 例如：

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

數位文本還可以包括`L`表示`Long`資料類型[的類型字元](../../programming-guide/language-features/data-types/type-characters.md)，如下例所示。

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>程式設計提示

- **Interop 考量：** 如果要與未為 .NET 框架編寫的元件（例如自動化或 COM 物件）介面，請記住，`Long`在其他環境中具有不同的資料寬度（32 位）。 如果要將 32 位參數傳遞給此類元件，請將其聲明為`Integer`而不是在新的 Visual `Long` Basic 代碼中。

- **擴大。** 資料類型`Long`擴展到`Decimal`或`Single`。 `Double` 這表示，您可以將 `Long` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。

- **鍵入字元。** 將常值類型字元 `L` 附加到常值，會強制其成為 `Long` 資料類型。 將識別項類型字元 `&` 附加到任何識別項，會強制其成為 `Long`。

- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.Int64?displayProperty=nameWithType> 結構。

## <a name="see-also"></a>另請參閱

- <xref:System.Int64>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [整數資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
