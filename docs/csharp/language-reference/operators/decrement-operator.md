---
title: -- 運算子 (C# 參考)
ms.date: 11/26/2018
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 0858321d6fe192a55bc548f169c558542238a981
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153330"
---
# <a name="---operator-c-reference"></a>-- 運算子 (C# 參考)

一元遞減運算子 (`--`) 的運算元遞減量為 1。 它有兩種支援形式：後置遞減運算子 `x--` 和前置遞減運算子 `--x`。

## <a name="postfix-decrement-operator"></a>後置遞減運算子

`x--` 的結果為運算「之前」的 `x` 值，如下列範例所示：

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixDecrement)]

## <a name="prefix-decrement-operator"></a>前置遞減運算子

`--x` 的結果為運算「之後」的 `x` 值，如下列範例所示：

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixDecrement)]

## <a name="remarks"></a>備註

遞減運算子是所有[整數型別](../keywords/integral-types-table.md) (包括 [char](../keywords/char.md) 型別)、[浮點型別](../keywords/floating-point-types-table.md)及任何[列舉](../keywords/enum.md)型別的預先定義運算子。

遞減運算子的運算元必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)存取或[索引子](../../../csharp/programming-guide/indexers/index.md)存取。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md) `--` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[後置遞增和遞減運算子](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)與[前置遞增和遞減運算子](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)小節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [++ 運算子](increment-operator.md)
- [操作說明：遞增和遞減指標](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
