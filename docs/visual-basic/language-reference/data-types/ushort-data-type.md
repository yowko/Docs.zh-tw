---
title: UShort 資料類型 (Visual Basic)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 038aad2c41f655d0699dab33df276132a70e3ede
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511876"
---
# <a name="ushort-data-type-visual-basic"></a>UShort 資料類型 (Visual Basic)

保存不帶正負號的 16 位元 （2 個位元組） 整數，值範圍從 0 到 65,535。  
  
## <a name="remarks"></a>備註

 使用`UShort`資料類型可包含二進位資料太大， `Byte`。  
  
 `UShort` 的預設值為 0。  

# <a name="literal-assignments"></a>常值的指派

您可以宣告並初始化`UShort`變數指派十進位常值、 十六進位常值、 八進位的常值，或 （Visual Basic 2017 年起） 二進位常值。 如果整數常值超出 `UShort` 的範圍 (亦即，如果小於 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、 十六進位表示的 65,034 整數和二進位常值指派給`UShort`值。
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> 使用前置詞`&h`或是`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位的常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元`_`，作為數字分隔符號，以提升可讀性，如下列範例所示。

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 作為前置分隔符號之間的前置詞和十六進位、 二進位或八進位數字。 例如: 

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

也可以包含數值常值`US`或是`us`[型別字元](../../programming-guide\language-features\data-types/type-characters.md)表示`UShort`資料型別，如下列範例所示。

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>程式設計提示
  
-   **負數的數字。** 因為`UShort`是不帶正負號的型別，它無法表示負數。 如果您使用一元減號 (`-`) 運算子的運算式，評估為類型`UShort`，Visual Basic 會將轉換的運算式`Integer`第一次。  
  
-   **CLS 合規性。** `UShort`資料類型不是屬於[Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) （cls） 標準，所以符合 CLS 標準的程式碼無法取用使用它的元件。
  
-   **擴展。** `UShort`資料類型可擴展為`Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，以及`Double`。 這表示您可以將轉換`UShort`任何一種類型，而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。  
  
-   **類型字元。** 將常值類型字元附加`US`成常值會強制其成為`UShort`資料型別。 `UShort` 有任何識別項類型字元。  
  
-   **Framework 型別。** 在 .NET Framework 中對應的類型為 <xref:System.UInt16?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.UInt16>  
 [資料類型](../../../visual-basic/language-reference/data-types/index.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
