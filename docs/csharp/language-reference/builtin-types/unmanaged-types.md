---
title: Unmanaged 型別 - C# 參考
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 469309276c440493f6ed5b655139167f9a8b0885
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239738"
---
# <a name="unmanaged-types-c-reference"></a>Unmanaged 型別 (C# 參考)

如果類型為下列任何類型，則其為**非受控類型**：

- `sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 或 `bool`
- 任何 [enum](enum.md) 型別
- 任何[指標](../../programming-guide/unsafe-code-pointers/pointer-types.md)型別
- 只有包含非受控[](struct.md)類型欄位和（在7.3 和更早版本中C# ）的任何使用者定義結構類型不是結構化類型（至少包含一個類型引數的類型）

從C# 7.3 開始，您可以使用[`unmanaged` 條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)，指定型別參數為非指標、不可為 null 的非受控型別。

從C# 8.0 開始，僅包含非受控類型欄位*的結構化結構類型*也是未受管理的，如下列範例所示：

[!code-csharp[unmanaged constructed types](~/samples/snippets/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

泛型結構可能是非受控和非受控結構類型的來源。 上述範例會定義泛型結構 `Coords<T>`，並提供非受控結構化類型的範例。 非受控類型的範例是 `Coords<object>`。 它不是未受管理的，因為它具有不受管理的 `object` 類型欄位。 如果您想要*所有*結構化類型都是非受控類型，請在泛型結構的定義中使用 `unmanaged` 條件約束：

[!code-csharp[unmanaged constraint in type definition](~/samples/snippets/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/unsafe-code.md#pointer-types)的[指標型別](~/_csharplang/spec/introduction.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [記憶體與延伸相關類型](../../../standard/memory-and-spans/index.md)
- [sizeof 運算子](../operators/sizeof.md)
- [stackalloc 運算子](../operators/stackalloc.md)
