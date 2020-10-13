---
title: '預設值運算式-c # 參考'
description: 使用預設值運算式取得型別的預設值
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 92ad8e919567e1f9f57e6875d53c4055eb960829
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997651"
---
# <a name="default-value-expressions-c-reference"></a>預設值運算式 (c # 參考) 

預設值運算式會產生型別的 [預設值](../builtin-types/default-values.md) 。 預設值運算式有兩種： [預設運算子](#default-operator) 呼叫和 [預設常](#default-literal)值。

您也可以在 `default` [ `switch` 語句](../keywords/switch.md)中使用關鍵字做為預設的 case 標籤。

## <a name="default-operator"></a>default 運算子

`default` 運算子的引數必須是型別名稱或型別參數，如下列範例所示：

[!code-csharp-interactive[default of T](snippets/shared/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a>預設常值

從 C# 7.1 開始，當編譯器可以推斷運算式型別時，您可以使用 `default` 常值來產生型別的預設值。 `default` 常值運算式會產生與對`default(T)` 運算式相同的值，其中 `T` 是推斷出來的型別。 在下列任一情況中，您都可以使用 `default` 常值：

- 在指派或初始化變數時。
- 在 [選擇性方法參數](../../methods.md#optional-parameters-and-arguments)的預設值聲明中。
- 在提供引數值的方法呼叫中。
- 在[ `return` 語句](../keywords/return.md)中，或做為[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)中的運算式。

下列範例會示範 `default` 常值的使用方式：

[!code-csharp-interactive[default literal](snippets/shared/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[預設值運算式](~/_csharplang/spec/expressions.md#default-value-expressions)一節。

如需有關 `default` 常值的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.1/target-typed-default.md) \(英文\)。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [C # 類型的預設值](../builtin-types/default-values.md)
- [.NET 的泛型](../../../standard/generics/index.md)
