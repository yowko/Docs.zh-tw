---
description: 瞭解 C 中的非受控類型#
title: Unmanaged 型別 - C# 參考
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 4374872af13c94e1a1af6b9f2c431f076c6f7dff
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471795"
---
# <a name="unmanaged-types-c-reference"></a>Unmanaged 型別 (C# 參考)

如果類型為下列任何一種類型，則類型為 **非受控型** 別：

- `sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 或 `bool`
- 任何 [enum](enum.md) 型別
- 任何[指標](../../programming-guide/unsafe-code-pointers/pointer-types.md)型別
- 只有包含一個型別引數的型別 (類型的任何使用者定義 [結構](struct.md) 類型，其中只包含非受控類型的欄位，而在 c # 7.3 和更早版本中，則不是結構化類型) 

從 c # 7.3 開始，您可以使用[ `unmanaged` 條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)指定型別參數為非指標、不可為 null 的非 null 非受控型別。

從 c # 8.0 開始，包含非受控型別之欄位 *的結構化結構類型* 也不受管理，如下列範例所示：

[!code-csharp[unmanaged constructed types](snippets/shared/UnmanagedTypes.cs#ProgramExample)]

泛型結構可能是非受控和非受控結構類型的來源。 上述範例會定義泛型結構 `Coords<T>` ，並提供非受控結構類型的範例。 非受控類型的範例為 `Coords<object>` 。 它不是未受管理的，因為它具有 `object` 不受管理的類型欄位。 如果您想要讓 *所有* 的結構化型別都是非受控型別，請 `unmanaged` 在泛型結構的定義中使用條件約束：

[!code-csharp[unmanaged constraint in type definition](snippets/shared/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [記憶體與延伸相關類型](../../../standard/memory-and-spans/index.md)
- [sizeof 運算子](../operators/sizeof.md)
- [stackalloc](../operators/stackalloc.md)
