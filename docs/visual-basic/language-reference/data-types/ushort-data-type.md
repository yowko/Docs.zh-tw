---
title: "UShort 資料類型 (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ushort
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 513e8ce4694788d33c5aa14e34b95e88b6d37ff1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ushort-data-type-visual-basic"></a>UShort 資料類型 (Visual Basic)

存放不帶正負號的 16 位元 （2 個位元組） 整數，範圍從 0 到 65,535。  
  
## <a name="remarks"></a>備註

 使用`UShort`資料類型可包含二進位資料太大， `Byte`。  
  
 `UShort` 的預設值為 0。  

# <a name="literal-assignments"></a>常值的指派

您可以宣告和初始化`UShort`變數將其指派十進位常值、 十六進位常值、 八進位常值，或是 （從開始使用 Visual Basic 2017） 二進位常值。 如果整數常值超出 `UShort` 的範圍 (亦即，如果小於 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，整數等於 65,034 以十進位、 十六進位表示，而二進位常值指派給`UShort`值。
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> 使用前置詞`&h`或`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元， `_`，當做數字分隔符號，以提升可讀性，如下列範例所示。

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

數值常值也可以包含`US`或`us`[類型字元](../../programming-guide\language-features\data-types/type-characters.md)代表`UShort`資料類型，如下列範例所示。

```vb
Dim number = &H035826us
```

## <a name="programming-tips"></a>程式設計提示
  
-   **負的數字。** 因為`UShort`是不帶正負號的類型，它無法表示為負數。 如果您使用一元減號 (`-`) 運算子的運算式評估為輸入`UShort`，Visual Basic 會將轉換的運算式`Integer`第一次。  
  
-   **Cls 符合性。** `UShort`資料類型不是屬於[Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) （cls） 標準，所以符合 CLS 標準的程式碼無法使用所使用的元件。
  
-   **擴展。** `UShort`資料類型可擴展成`Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，和`Double`。 這表示您可以將轉換`UShort`而不會發生這些類型的任何<xref:System.OverflowException?displayProperty=nameWithType>錯誤。  
  
-   **類型字元。** 將常值類型字元附加`US`到常值會強制其成為`UShort`資料型別。 `UShort`有任何識別項類型字元。  
  
-   **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.UInt16?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.UInt16>  
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
