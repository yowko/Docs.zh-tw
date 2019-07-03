---
title: '?: 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 2717505a0a09b9ac1c6ad43153c52771c13f7b5c
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025207"
---
# <a name="-operator-c-reference"></a>?: 運算子 (C# 參考)

條件運算子 `?:` (通稱為三元條件運算子) 會評估布林運算式，然後根據布林運算式評估為 `true` 或 `false`，傳回評估兩個運算式其中之一的結果。 從 C# 7.2 開始，[條件 ref 運算式](#conditional-ref-expression)會傳回兩個運算式其中之一結果的參考。

條件運算子的語法如下：

```csharp
condition ? consequent : alternative
```

`condition` 運算式必須評估為 `true` 或 `false`。 如果 `condition` 評估為 `true`，就會接著評估 `consequent` 運算式，且其結果會成為運算的結果。 如果 `condition` 評估為 `false`，則會接著評估 `alternative` 運算式，且其結果會成為運算的結果。 系統只會評估 `consequent` 或 `alternative`。

`consequent` 和 `alternative` 的型別必須相同，或是必須有從一個型別轉換成另一型別的隱含轉換。

條件運算子是右向關聯運算子，亦即，以下形式的運算式

```csharp
a ? b : c ? d : e
```

評估為

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> 您可以使用下列助憶鍵裝置來記住條件運算子的評估方式：
>
> ```text
> is this condition true ? yes : no
> ```

下列範例示範條件運算子的用法：

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>條件 ref 運算式

從 C# 7.2 開始，您可以使用條件 ref 運算式來傳回兩個運算式其中之一結果的參考。 您可以將該參考指派給 [ref 區域變數](../keywords/ref.md#ref-locals)或[ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals)，或使用它作為[參考傳回值](../keywords/ref.md#reference-return-values)或作為 [`ref` 方法參數](../keywords/ref.md#passing-an-argument-by-reference)。

條件 ref 運算式的語法如下：

```csharp
condition ? ref consequent : ref alternative
```

與原始條件運算子相同，條件 ref 運算式只會評估兩個運算式其中之一：`consequent` 或 `alternative`。

就條件 ref 運算式而言，`consequent` 與 `alternative` 的型別必須相同。

下列範例示範條件 ref 運算式的用法：

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

如需詳細資訊，請參閱[功能提案注意事項](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md) \(英文\)。

## <a name="conditional-operator-and-an-ifelse-statement"></a>條件運算子和 `if..else` 陳述式

當您需要依據條件計算某個值時，透過 [if-else](../keywords/if-else.md) 陳述式使用條件運算子可能使程式碼更為簡潔。 下列範例示範兩種將整數分類為負值或非負值的方法：

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>運算子是否可多載

條件運算子不能多載。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[條件運算子](~/_csharplang/spec/expressions.md#conditional-operator)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [if-else 陳述式](../keywords/if-else.md)
- [?. 和 ?[] 運算子](member-access-operators.md#null-conditional-operators--and-)
- [?? 運算子](null-coalescing-operator.md)
- [ref 關鍵字](../keywords/ref.md)
