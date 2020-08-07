---
title: '?? 還有？= 運算子-c # 參考'
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
ms.openlocfilehash: 58c60dad3badc62f850f737a3d210ec486809272
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916732"
---
# <a name="-and--operators-c-reference"></a>?? 還有？= 運算子 (c # 參考) 

如果 Null 聯合運算子 `??` 不是 `null`，會傳回其左方運算元的值；否則它會評估右方運算元，並傳回其結果。 如果左側運算元評估為非 Null，則 `??` 運算子不會評估右側運算元。

在 c # 8.0 和更新版本中提供，如果左運算元評估為，則 null 聯合指派運算子只會將 `??=` 其右運算元的值指派給其左邊的運算元 `null` 。 如果左側運算元評估為非 Null，則 `??=` 運算子不會評估右側運算元。

[!code-csharp[null-coalescing assignment](snippets/shared/NullCoalescingOperator.cs#Assignment)]

運算子的左邊運算元 `??=` 必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../programming-guide/indexers/index.md)元素。

在 c # 7.3 和更早版本中，運算子的左邊運算元類型 `??` 必須是[參考型別](../keywords/reference-types.md)或[可為 null 的實數值型別](../builtin-types/nullable-value-types.md)。 從 c # 8.0 開始，這項需求會取代為下列內容：和運算子左邊運算元的類型 `??` `??=` 不可以是不可為 null 的實數值型別。 特別是，從 c # 8.0 開始，您可以使用 null 聯合運算子搭配不受限制的類型參數：

[!code-csharp[unconstrained type parameter](snippets/shared/NullCoalescingOperator.cs#UnconstrainedType)]

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

`??`和 `??=` 運算子在下列案例中可能會很有用：

- 在具有[null 條件運算子？. 和？ []](member-access-operators.md#null-conditional-operators--and-)的運算式中，您可以使用 `??` 運算子來提供另一個運算式，以便在具有 null 條件運算的運算式結果為時進行評估 `null` ：

  [!code-csharp-interactive[with null-conditional](snippets/shared/NullCoalescingOperator.cs#WithNullConditional)]

- 當您使用[可為 null 的實數值型別](../builtin-types/nullable-value-types.md)，而且需要提供基礎實數值型別的值時，請使用 `??` 運算子來指定要提供的值，以防可為 null 的類型值為 `null` ：

  [!code-csharp-interactive[with nullable types](snippets/shared/NullCoalescingOperator.cs#WithNullableTypes)]

  如果可為 Null 型別的值為 `null` 時要使用的值為基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。

- 從 c # 7.0 開始，您可以使用[ `throw` 運算式](../keywords/throw.md#the-throw-expression)做為運算子的右手運算元， `??` 讓引數檢查程式碼更簡潔：

  [!code-csharp[with throw expression](snippets/shared/NullCoalescingOperator.cs#WithThrowExpression)]

  上述範例中也會示範如何使用[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)定義屬性。

- 從 c # 8.0 開始，您可以使用 `??=` 運算子來取代表單的程式碼

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  取代為下列程式碼：

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>運算子是否可多載

運算子 `??` 和無法多載 `??=` 。

## <a name="c-language-specification"></a>C# 語言規格

如需運算子的詳細資訊 `??` ，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)[的 null 聯合運算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)一節。

如需運算子的詳細資訊 `??=` ，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [?.和?[] 運算子](member-access-operators.md#null-conditional-operators--and-)
- [？：運算子](conditional-operator.md)
