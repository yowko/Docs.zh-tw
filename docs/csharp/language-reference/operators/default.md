---
title: default 运算符 - C# 參考
description: 使用 default 運算子產生類型的預設值
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 651c4698514aee8cf4dab75ea32c98493e19a30b
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964612"
---
# <a name="default-operator-c-reference"></a>default 运算符 (C# 參考)

`default` 運算子會產生型別的[預設值](../builtin-types/default-values.md)。 `default` 運算子的引數必須是型別或或型別參數的名稱。

下列範例會示範 `default` 運算子的使用方式：

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

您也可以使用 `default` 關鍵字做為[`switch` 語句](../keywords/switch.md)內的預設 case 標籤。

## <a name="default-literal"></a>預設常值

從 C# 7.1 開始，當編譯器可以推斷運算式型別時，您可以使用 `default` 常值來產生型別的預設值。 `default` 常值運算式會產生與對`default(T)` 運算式相同的值，其中 `T` 是推斷出來的型別。 在下列任一情況中，您都可以使用 `default` 常值：

- 在指派或初始化變數時。
- 在[選擇性方法參數](../../methods.md#optional-parameters-and-arguments)的預設值宣告中。
- 在提供引數值的方法呼叫中。
- 在[`return` 語句](../keywords/return.md)或[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)中的運算式。

下列範例會示範 `default` 常值的使用方式：

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[預設值運算式](~/_csharplang/spec/expressions.md#default-value-expressions)一節。

如需有關 `default` 常值的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.1/target-typed-default.md) \(英文\)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [類型的C#預設值](../builtin-types/default-values.md)
- [.NET 的泛型](../../../standard/generics/index.md)
