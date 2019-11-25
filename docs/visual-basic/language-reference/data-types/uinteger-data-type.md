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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343893"
---
# <a name="uinteger-data-type"></a>UInteger 資料類型

Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.

## <a name="remarks"></a>備註

The `UInteger` data type provides the largest unsigned value in the most efficient data width.

`UInteger` 的預設值為 0。

## <a name="literal-assignments"></a>Literal assignments

You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal. 如果整數常值超出 `UInteger` 的範圍 (亦即，如果小於 <xref:System.UInt32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、十六進位和二進位常值表示的 3,000,000,000 整數，會指派給 `UInteger` 值。

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal. 十進位常值沒有前置詞。

Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits. 例如:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>程式設計提示

The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.

- **Negative Numbers.** Because `UInteger` is an unsigned type, it cannot represent a negative number. If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.

- **CLS Compliance.** The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.

- **Interop Considerations.** If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments. If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.

- **Widening.** The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`. This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.

- **Type Characters.** Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type. `UInteger` has no identifier type character.

- **Framework Type.** 在 .NET Framework 中對應的類型為 <xref:System.UInt32?displayProperty=nameWithType> 結構。

## <a name="see-also"></a>請參閱

- <xref:System.UInt32>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
