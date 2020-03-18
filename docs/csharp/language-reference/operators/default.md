---
title: 預設運算子 - C# 參考
description: 使用預設運算子組建類型的預設值
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 0d37fe952e71e74f014872231a2e58663dea9d18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399480"
---
# <a name="default-operator-c-reference"></a>預設運算子 (C# 參考)

`default` 運算子會產生型別的[預設值](../builtin-types/default-values.md)。 `default` 運算子的引數必須是型別或或型別參數的名稱。

下列範例會示範 `default` 運算子的使用方式：

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

您還將關鍵字`default`用作[`switch`語句](../keywords/switch.md)中的預設大小寫標籤。

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
