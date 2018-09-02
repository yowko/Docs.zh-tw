---
title: SByte 資料類型 (Visual Basic)
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ab72b2ac2678640697e3cfab426e5a7d6d889a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467172"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte 資料類型 (Visual Basic)

保存帶正負號 8 位元 （1 個位元組） 整數，範圍介於-128 到 127。  
  
## <a name="remarks"></a>備註

使用`SByte`包含不需要完整的資料寬度的整數值的資料型別`Integer`或甚至是一半的資料寬度`Short`。 在某些情況下，common language runtime 可以封裝程式`SByte`緊密合作，並將記憶體耗用量儲存的變數。

`SByte` 的預設值為 0。

## <a name="literal-assignments"></a>常值的指派
  
您可以宣告並初始化`SByte`變數指派十進位常值、 十六進位常值、 八進位的常值，或 （Visual Basic 2017 年起） 二進位常值。

在下列範例中，以十進位、 十六進位表示的-102 和二進位常值指派給`SByte`值。 這個範例需要您使用編譯`/removeintchecks`編譯器參數。

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> 使用前置詞`&h`或是`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位的常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元`_`，作為數字分隔符號，以提升可讀性，如下列範例所示。

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 作為前置分隔符號之間的前置詞和十六進位、 二進位或八進位數字。 例如: 

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

如果整數常值超出 `SByte` 的範圍 (亦即，如果小於 <xref:System.SByte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.SByte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。 當整數常值沒有後置詞時，[整數](integer-data-type.md)推斷而來。 如果整數常值超出範圍`Integer`型別[長](long-data-type.md)推斷而來。 這表示，在上一個範例中，將數值常值`0x9A`並`0b10011010`會解譯為 32 位元帶正負號整數值 156，而超過<xref:System.SByte.MaxValue?displayProperty=nameWithType>。 若要成功編譯會將指派從非十進位整數到如下的程式碼`SByte`，您可以執行下列其中一項：

- 停用整數範圍檢查，藉由使用編譯`/removeintchecks`編譯器參數。

- 使用[型別字元](../../programming-guide\language-features\data-types/type-characters.md)明確地定義您想要指派給常值`SByte`。 下列範例會指派為負的常值`Short`值`SByte`。 請注意，對於負數的數字，高序位位元的數值常值的高序位文字必須設定。 在我們的範例中，這位元的常值 15`Short`值。

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>程式設計提示
  
-   **CLS 合規性。** `SByte`資料類型不是屬於[Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) （cls） 標準，所以符合 CLS 標準的程式碼無法取用使用它的元件。

-   **擴展。** `SByte`資料類型可擴展為`Short`， `Integer`， `Long`， `Decimal`， `Single`，和`Double`。 這表示您可以將轉換`SByte`任何一種類型，而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。
  
-   **類型字元。** `SByte` 沒有任何常值類型字元或識別項類型字元。  
  
-   **Framework 型別。** 在 .NET Framework 中對應的類型為 <xref:System.SByte?displayProperty=nameWithType> 結構。
  
## <a name="see-also"></a>另請參閱

 <xref:System.SByte?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/index.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Integer 資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long 資料類型](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
