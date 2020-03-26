---
title: Unmanaged 型別 - C# 參考
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 9dd2ab4e044b8a86bfe72a6fcf2481b8e1e80bf4
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507226"
---
# <a name="unmanaged-types-c-reference"></a>Unmanaged 型別 (C# 參考)

類型是**非託管類型**（如果是以下任何類型）：

- `sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 或 `bool`
- 任何 [enum](enum.md) 型別
- 任何[指標](../../programming-guide/unsafe-code-pointers/pointer-types.md)型別
- 任何使用者定義的[結構](struct.md)類型，僅包含非託管類型的欄位，並且在 C# 7.3 和更早版本中，不是構造類型（至少包含一個類型參數的類型）

從 C# 7.3 開始，可以使用[`unmanaged`約束](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)指定類型參數是非指標、不可空的不可託管類型。

從 C# 8.0 開始，僅包含非託管類型的欄位的*構造*結構類型也是非託管的，如下例所示：

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

泛型結構可能是非託管類型和非非託管構造類型的源。 前面的示例定義了泛型結構，`Coords<T>`並介紹了非託管構造類型的示例。 非託管類型的示例為`Coords<object>`。 它不是非託管的，因為它具有`object`類型的欄位，該欄位不是非託管的。 如果希望*所有*構造類型都是非託管類型，請使用泛型結構`unmanaged`定義中的約束：

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [記憶體與延伸相關類型](../../../standard/memory-and-spans/index.md)
- [sizeof 運算子](../operators/sizeof.md)
- [stackalloc](../operators/stackalloc.md)
