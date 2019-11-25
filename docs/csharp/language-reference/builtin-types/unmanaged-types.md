---
title: Unmanaged 型別 - C# 參考
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 81eef59ceb20bcae6c749dd59578ce35da253826
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204478"
---
# <a name="unmanaged-types-c-reference"></a>Unmanaged 型別 (C# 參考)

A type is an **unmanaged type** if it's any of the following types:

- `sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 或 `bool`
- 任何 [enum](../keywords/enum.md) 型別
- 任何[指標](../../programming-guide/unsafe-code-pointers/pointer-types.md)型別
- Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)

Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.

Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

A generic struct may be the source of both unmanaged and not unmanaged constructed types. The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types. The example of not an unmanaged type is `Coords<object>`. It's not unmanaged because it has the fields of the `object` type, which is not unmanaged. If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [記憶體與延伸相關類型](../../../standard/memory-and-spans/index.md)
- [sizeof 運算子](../operators/sizeof.md)
- [stackalloc 運算子](../operators/stackalloc.md)
