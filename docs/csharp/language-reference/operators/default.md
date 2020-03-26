---
title: 預設值運算式 - C# 引用
description: 使用預設值運算式獲取類型的預設值
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 2adfd8d24066e9dad50c3c18407d3ade71b4b68e
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507174"
---
# <a name="default-value-expressions-c-reference"></a>預設值運算式（C# 引用）

預設值運算式組建類型的[預設值](../builtin-types/default-values.md)。 有兩種類型的預設值運算式：[預設運算子](#default-operator)調用和[預設文本](#default-literal)。

您還將關鍵字`default`用作[`switch`語句](../keywords/switch.md)中的預設大小寫標籤。

## <a name="default-operator"></a>default 運算子

`default` 運算子的引數必須是型別名稱或型別參數，如下列範例所示：

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a>預設常值

從 C# 7.1 開始，當編譯器可以推斷運算式型別時，您可以使用 `default` 常值來產生型別的預設值。 `default` 常值運算式會產生與對`default(T)` 運算式相同的值，其中 `T` 是推斷出來的型別。 在下列任一情況中，您都可以使用 `default` 常值：

- 在指派或初始化變數時。
- 在[可選方法參數](../../methods.md#optional-parameters-and-arguments)的預設值的聲明中。
- 在提供引數值的方法呼叫中。
- 在[`return`語句](../keywords/return.md)中或作為[運算式體成員中的](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)運算式。

下列範例會示範 `default` 常值的使用方式：

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[預設值運算式](~/_csharplang/spec/expressions.md#default-value-expressions)一節。

如需有關 `default` 常值的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.1/target-typed-default.md) \(英文\)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [C# 類型的預設值](../builtin-types/default-values.md)
- [.NET 的泛型](../../../standard/generics/index.md)
