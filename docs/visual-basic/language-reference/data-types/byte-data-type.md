---
title: Byte 資料類型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 70e1028042807eb77fc74b30174e1962bc00f4c0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192391"
---
# <a name="byte-data-type-visual-basic"></a>Byte 資料類型 (Visual Basic)
保留範圍從 0 到 255 的不帶正負號的 8 位元 （1 個位元組） 整數。

## <a name="remarks"></a>備註

使用`Byte`包含二進位資料的資料類型。  
  
`Byte` 的預設值為 0。

## <a name="literal-assignments"></a>常值的指派

您可以宣告並初始化`Byte`變數指派十進位常值、 十六進位常值、 八進位的常值，或 （Visual Basic 2017 年起） 二進位常值。 如果整數常值超出範圍`Byte`(亦即，如果是小於<xref:System.Byte.MinValue?displayProperty=nameWithType>或大於<xref:System.Byte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、 十六進位表示的 201 和二進位常值會以隱含方式轉換來自[整數](integer-data-type.md)到`byte`值。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> 使用前置詞`&h`或是`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位的常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元`_`，作為數字分隔符號，以提升可讀性，如下列範例所示。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 作為前置分隔符號之間的前置詞和十六進位、 二進位或八進位數字。 例如: 

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>程式設計提示

-   **負數的數字。** 因為`Byte`是不帶正負號的型別，它無法表示負數。 如果您使用一元減號 (`-`) 運算子的運算式，評估為類型`Byte`，Visual Basic 會將轉換的運算式`Short`第一次。
  
-   **格式轉換。** 當 Visual Basic 中讀取或寫入檔案，或呼叫的 Dll、 方法和屬性時，它可以自動資料格式之間進行轉換。 二進位資料儲存在`Byte`這種格式轉換期間會保留變數和陣列。 您不應該使用`String`變數的二進位資料，因為其內容可能會損毀，ANSI 和 Unicode 格式之間轉換時。

-   **擴展。** `Byte`資料類型可擴展為`Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，或`Double`。 這表示您可以將轉換`Byte`任何一種類型，而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。
  
-   **類型字元。** `Byte` 沒有任何常值類型字元或識別項類型字元。

-   **Framework 型別。** 在 .NET Framework 中對應的類型為 <xref:System.Byte?displayProperty=nameWithType> 結構。

## <a name="example"></a>範例

 在下列範例中，`b`是`Byte`變數。 陳述式示範變數的範圍和應用程式的位元移位運算子。

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>另請參閱

 <xref:System.Byte?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/index.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
