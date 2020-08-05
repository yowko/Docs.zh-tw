---
title: '?: 運算子 - C# 參考'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 8e6753a08bbd96f980b3c5901e763f2dfad055c6
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555353"
---
# <a name="-operator-c-reference"></a>?: 運算子 (C# 參考)

條件運算子 `?:` （也稱為三元條件運算子）會評估布林運算式，並根據布林運算式是否評估為或，傳回兩個運算式其中之一的結果 `true` `false` 。

條件運算子的語法如下：

```csharp
condition ? consequent : alternative
```

`condition` 運算式必須評估為 `true` 或 `false`。 如果 `condition` 評估為 `true`，則會接著評估 `consequent` 運算式，且其結果會成為運算的結果。 如果 `condition` 評估為 `false`，則會接著評估 `alternative` 運算式，且其結果會成為運算的結果。 系統只會評估 `consequent` 或 `alternative`。

`consequent` 和 `alternative` 的型別必須相同，或是必須有從一個型別轉換成另一型別的隱含轉換。

條件運算子是右向關聯運算子，亦即，以下形式的運算式

```csharp
a ? b : c ? d : e
```

會評估為

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

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>條件 ref 運算式

從 c # 7.2 開始，您可以使用條件 ref 運算式，有條件地指派[ref 區域變數](../keywords/ref.md#ref-locals)或[ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals)。 您也可以使用條件 ref 運算式做為[參考傳回值](../keywords/ref.md#reference-return-values)，或做為[ `ref` 方法引數](../keywords/ref.md#passing-an-argument-by-reference)。

條件 ref 運算式的語法如下：

```csharp
condition ? ref consequent : ref alternative
```

與原始條件運算子相同，條件 ref 運算式只會評估兩個運算式其中之一：`consequent` 或 `alternative`。

就條件 ref 運算式而言，`consequent` 與 `alternative` 的型別必須相同。

下列範例示範條件 ref 運算式的用法：

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>條件運算子和 `if..else` 陳述式

當您需要有條件地計算值時，使用條件運算子（而不是[else 語句）](../keywords/if-else.md)可能會導致更簡潔的程式碼。 下列範例示範兩種將整數分類為負值或非負值的方法：

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別無法多載條件運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[條件運算子](~/_csharplang/spec/expressions.md#conditional-operator)一節。

如需條件 ref 運算式的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [if-else 陳述式](../keywords/if-else.md)
- [?.和?[] 運算子](member-access-operators.md#null-conditional-operators--and-)
- [??還有？= 運算子](null-coalescing-operator.md)
- [ref 關鍵字](../keywords/ref.md)
