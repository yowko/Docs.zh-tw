---
title: UInteger 資料類型 (Visual Basic)
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
ms.openlocfilehash: c63b9a25c1830f142002e9854e9ce275f55ef54b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154815"
---
# <a name="uinteger-data-type"></a>UInteger 資料類型

保存不帶正負號的 32 位元 （4 個位元組） 整數，範圍從 0 到 4,294,967,295。  
  
## <a name="remarks"></a>備註

 `UInteger`資料類型提供的不帶正負號的最大值，最有效率的資料寬度。  
  
 `UInteger` 的預設值為 0。  
  
## <a name="literal-assignments"></a>常值的指派

您可以宣告並初始化`UInteger`變數指派十進位常值、 十六進位常值、 八進位的常值，或 （Visual Basic 2017 年起） 二進位常值。 如果整數常值超出 `UInteger` 的範圍 (亦即，如果小於 <xref:System.UInt32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、十六進位和二進位常值表示的 3,000,000,000 整數，會指派給 `UInteger` 值。
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> 使用前置詞`&h`或是`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位的常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元`_`，作為數字分隔符號，以提升可讀性，如下列範例所示。

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 作為前置分隔符號之間的前置詞和十六進位、 二進位或八進位數字。 例如: 

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

也可以包含數值常值`UI`或是`ui`[型別字元](../../programming-guide/language-features/data-types/type-characters.md)表示`UInteger`資料型別，如下列範例所示。

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>程式設計提示

 `UInteger`並`Integer`資料類型提供最佳效能 32 位元的處理器，因為較小的整數類型 (`UShort`， `Short`， `Byte`，和`SByte`)，即使他們使用較少的位元，需要更多時間載入、 儲存和擷取。  
  
-   **負數的數字。** 因為`UInteger`是不帶正負號的型別，它無法表示負數。 如果您使用一元減號 (`-`) 運算子的運算式，評估為類型`UInteger`，Visual Basic 會將轉換的運算式`Long`第一次。  
  
-   **CLS 合規性。** `UInteger`資料類型不是屬於[Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) （cls） 標準，所以符合 CLS 標準的程式碼無法取用使用它的元件。
  
-   **Interop 考量。** 如果您要使用的元件不是撰寫.NET framework，例如 Automation 或 COM 物件，請記住，這類類型`uint`在其他環境中可以有不同的資料寬度 （16 位元）。 如果您將 16 位元引數傳遞給這類元件，將它宣告為`UShort`而不是`UInteger`中受管理的 Visual Basic 程式碼。  
  
-   **擴展。** `UInteger`資料類型可擴展為`Long`， `ULong`， `Decimal`， `Single`，和`Double`。 這表示您可以將轉換`UInteger`任何一種類型，而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。  
  
-   **類型字元。** 將常值類型字元附加`UI`成常值會強制其成為`UInteger`資料型別。 `UInteger` 有任何識別項類型字元。  
  
-   **Framework 型別。** 在 .NET Framework 中對應的類型為 <xref:System.UInt32?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.UInt32>  
 [資料類型](../../../visual-basic/language-reference/data-types/index.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [操作說明：呼叫 Windows 函式使用不帶正負號的類型](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
