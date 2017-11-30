---
title: "Short 資料類型 (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
f1_keywords: vb.Short
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
ms.openlocfilehash: fef948debed69cf9fb7b0e6bb65eb0ddbe497a92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="short-data-type-visual-basic"></a>Short 資料類型 (Visual Basic)
保存帶正負號的 16 位元 （2 個位元組） 整數，範圍從-32,768 到 32,767。  
  
## <a name="remarks"></a>備註  
 使用`Short`資料類型可包含不需要完整的資料寬度的整數值`Integer`。 組件的 common language runtime 可以在某些情況下，您`Short`緊密，並將記憶體耗用量儲存變數。  
  
 `Short` 的預設值為 0。  
  
## <a name="literal-assignments"></a>常值的指派

您可以宣告和初始化`Short`變數將其指派十進位常值、 十六進位常值、 八進位常值，或是 （從開始使用 Visual Basic 2017） 二進位常值。 如果整數常值超出 `Short` 的範圍 (亦即，如果小於 <xref:System.Int16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，整數等於會以十進位、 十六進位表示的 1,034 和二進位常值會隱含地轉換從[整數](integer-data-type.md)至`Short`值。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> 使用前置詞`&h`或`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元， `_`，當做數字分隔符號，以提升可讀性，如下列範例所示。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

數值常值也可以包含`S`[類型字元](../../programming-guide\language-features\data-types/type-characters.md)代表`Short`資料類型，如下列範例所示。

```vb
Dim number = &H0326S
```

## <a name="programming-tips"></a>程式設計提示

-   **擴展。** `Short`資料類型可擴展成`Integer`， `Long`， `Decimal`， `Single`，或`Double`。 這表示，您可以將 `Short` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。  
  
-   **類型字元。** 將常值類型字元 `S` 附加到常值，會強制其成為 `Short` 資料類型。 `Short`有任何識別項類型字元。  
  
-   **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Int16?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>請參閱

 <xref:System.Int16?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Integer 資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long 資料類型](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
