---
title: ++ 運算子 - C# 參考
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: db716f0d8cfe252462abeee9c80baaab880e212b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235640"
---
# <a name="-operator-c-reference"></a>++ 運算子 (C# 參考)

一元遞增運算子 `++` 的運算元遞增量為 1。 其支援兩種形式：後置遞增運算子 `x++` 和前置遞增運算子 `++x`。

## <a name="postfix-increment-operator"></a>後置遞增運算子

`x++` 的結果為運算「之前」的 `x` 值，如下列範例所示：

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixIncrement)]

## <a name="prefix-increment-operator"></a>前置遞增運算子

`++x` 的結果為運算「之後」的 `x` 值，如下列範例所示：

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixIncrement)]

## <a name="remarks"></a>備註

遞增運算子已針對所有[整數型別](../keywords/integral-types-table.md) (包 括 [char](../keywords/char.md) 型別)、[浮點型別](../keywords/floating-point-types-table.md)及任何[列舉](../keywords/enum.md)型別進行預先定義。

遞增運算子的運算元必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)存取或[索引子](../../../csharp/programming-guide/indexers/index.md)存取。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md) `++` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[後置遞增和遞減運算子](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)與[前置遞增和遞減運算子](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)小節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [-- 運算子](decrement-operator.md)
- [操作說明：遞增和遞減指標](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
