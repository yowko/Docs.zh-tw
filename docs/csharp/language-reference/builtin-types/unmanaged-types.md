---
title: Unmanaged 型別 - C# 參考
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512068"
---
# <a name="unmanaged-types-c-reference"></a>Unmanaged 型別 (C# 參考)

**unmanaged 型別**是任何不屬於參考型別或建構型別 (包含至少一個型別引數的型別) 的型別，並且在巢狀結構的任何層級中都不包含參考型別或建構型別欄位。 換句話說，unmanaged 型別是以下其中一個型別：

- `sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 或 `bool`
- 任何 [enum](../keywords/enum.md) 型別
- 任何[指標](../../programming-guide/unsafe-code-pointers/pointer-types.md)型別
- 任何使用者定義，並非建構型別且只包含 unmanaged 型別欄位的 [struct](../keywords/struct.md) 型別

從 C# 7.3 開始，您可以使用 [`unmanaged` 條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)指定型別參數是非指標 unmanaged 型別。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [記憶體與延伸相關類型](../../../standard/memory-and-spans/index.md)
- [sizeof 運算子](../operators/sizeof.md)
- [stackalloc 運算子](../operators/stackalloc.md)
