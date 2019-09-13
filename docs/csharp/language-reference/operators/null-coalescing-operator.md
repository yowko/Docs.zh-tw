---
title: ?? 還有？= 運算子- C#參考
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 1e94038a41a6a6cc19be6c67bff2891397793fb3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924686"
---
# <a name="-and--operators-c-reference"></a>?? 還有？= 運算子（C#參考）

如果 Null 聯合運算子 `??` 不是 `null`，會傳回其左方運算元的值；否則它會評估右方運算元，並傳回其結果。 如果左方運算元評估為非 Null，`??` 運算子不會評估其右方運算元。

在 8.0 C#和更新版本中，如果左運算元評估為`??=` `null`，則 null 聯合指派運算子只會將其右運算元的值指派給其左邊的運算元。 如果左方運算元評估為非 Null，`??=` 運算子不會評估其右方運算元。

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

`??=`運算子的左邊運算元必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../programming-guide/indexers/index.md)元素。 如需有關 null 聯合指派的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)。

在C# 7.3 和更早版本中， `??`運算子的左邊運算元類型必須是參考型別或[可為 null 的實數值型別](../../programming-guide/nullable-types/index.md)。 從C# 8.0 開始，會以下列內容取代該需求： `??`和`??=`運算子的左邊運算元類型不能是不可為 null 的實數值型別。 特別的是，您可以在8.0 和更新版本中C#使用 null 聯合運算子搭配不受限制的類型參數：

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

Null 聯合運算子是右向關聯。 也就是表單的運算式

```csharp
a ?? b ?? c
d ??= e ??= f
```

評估為

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>範例

`??` 和`??=`運算子在下列案例中可能會很有用：

- 在使用 [Null 聯合運算子 ?. 和 ?[]](member-access-operators.md#null-conditional-operators--and-) 的運算式中，您可以使用 Null 聯合運算子在 Null 條件運算的結果為 `null` 的運算式中，提供用於評估的替代運算式：

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- 當您使用[可為 Null 的實值型別](../../programming-guide/nullable-types/index.md)，而且需要提供基礎實值型別的值時，請使用 Null 聯合運算子，在可為 Null 的實值型別為 `null` 時，指定要提供的值：

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  如果可為 Null 型別的值為 `null` 時要使用的值為基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。

- 從 C# 7.0 開始，您可以使用 [`throw` 運算式](../keywords/throw.md#the-throw-expression)作為 Null 聯合運算子的右方運算元，讓引數檢查程式碼更簡潔：

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  上述範例中也會示範如何使用[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)定義屬性。

- 從C# 8.0 開始，您可以使用`??=`運算子來取代表單的程式碼

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  使用下列程式碼：

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>運算子是否可多載

運算子`??` 和`??=`無法多載。

## <a name="c-language-specification"></a>C# 語言規格

如需`??`運算子的詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)[的 null 聯合運算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [?. 和 ?[] 運算子](member-access-operators.md#null-conditional-operators--and-)
- [?: 運算子](conditional-operator.md)
