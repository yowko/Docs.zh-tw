---
title: ?? 運算子 - C# 參考
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: a19b5558da36ffb11dabd1b9bec419a3623a0f17
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024998"
---
# <a name="-operator-c-reference"></a>?? 運算子 (C# 參考)

如果 Null 聯合運算子 `??` 不是 `null`，會傳回其左方運算元的值；否則它會評估右方運算元，並傳回其結果。 如果左方運算元評估為非 Null，`??` 運算子不會評估其右方運算元。

Null 聯合運算子是右向關聯運算子，亦即，以下形式的運算式

```csharp
a ?? b ?? c
```

評估為

```csharp
a ?? (b ?? c)
```

`??` 運算子在下列案例中很有用：

- 在使用 [Null 聯合運算子 ?. 和 ?[]](member-access-operators.md#null-conditional-operators--and-) 的運算式中，您可以使用 Null 聯合運算子在 Null 條件運算的結果為 `null` 的運算式中，提供用於評估的替代運算式：

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- 當您使用[可為 Null 的實值型別](../../programming-guide/nullable-types/index.md)，而且需要提供基礎實值型別的值時，請使用 Null 聯合運算子，在可為 Null 的實值型別為 `null` 時，指定要提供的值：

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  如果可為 Null 型別的值為 `null` 時要使用的值為基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。

- 從 C# 7.0 開始，您可以使用 [`throw` 運算式](../keywords/throw.md#the-throw-expression)作為 Null 聯合運算子的右方運算元，讓引數檢查程式碼更簡潔：

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  上述範例中也會示範如何使用[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)定義屬性。

## <a name="operator-overloadability"></a>運算子是否可多載

無法多載 Null 聯合運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Null 聯合運算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [?. 和 ?[] 運算子](member-access-operators.md#null-conditional-operators--and-)
- [?: 運算子](conditional-operator.md)
