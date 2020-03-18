---
title: ?? 和？？• 運算子 - C# 參考
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
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847309"
---
# <a name="-and--operators-c-reference"></a>?? 和？？• 運算子（C# 參考）

如果 Null 聯合運算子 `??` 不是 `null`，會傳回其左方運算元的值；否則它會評估右方運算元，並傳回其結果。 如果左方運算元評估為非 Null，`??` 運算子不會評估其右方運算元。

在 C# 8.0 及更高版本中可用，空合併賦值`??=`運算子僅在左側運算元計算為`null`時，才會將其右側運算元的值分配給其左側運算元。 如果左方運算元評估為非 Null，`??=` 運算子不會評估其右方運算元。

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

運算子的`??=`左側操作符必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../programming-guide/indexers/index.md)元素。

在 C# 7.3 和更早版本中，`??`運算子的左側運算元的類型必須是[參考型別](../keywords/reference-types.md)或[空數值型別](../builtin-types/nullable-value-types.md)。 從 C# 8.0 開始，該要求替換為以下內容：`??`和`??=`運算子的左側運算元的類型不能為非空數值型別。 特別是，從 C# 8.0 開始，可以使用具有無約束類型參數的空合併運算子：

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

空合併運算子是右關聯的。 也就是說，表單的運算式

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

和`??``??=`運算子在以下方案中非常有用：

- 在具有 null[條件運算子的運算式中 ，](member-access-operators.md#null-conditional-operators--and-)可以使用`??`運算子提供替代運算式來計算，以防具有 null 條件操作的運算式的結果為`null`：

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- 當您使用[空數值型別](../builtin-types/nullable-value-types.md)並且需要提供基礎數值型別的值時，使用`??`運算子指定要提供的值，以防空類型值為`null`：

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  如果可為 Null 型別的值為 `null` 時要使用的值為基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。

- 從 C# 7.0 開始，可以使用[`throw`運算式](../keywords/throw.md#the-throw-expression)作為`??`運算子的右側運算元，以使參數檢查代碼更加簡潔：

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  上述範例中也會示範如何使用[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)定義屬性。

- 從 C# 8.0 開始，`??=`可以使用運算子替換表單的代碼

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

運算子`??`不能`??=`重載。

## <a name="c-language-specification"></a>C# 語言規格

有關運算子的詳細資訊，`??`請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[空合併運算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)部分。

有關運算子的詳細資訊，`??=`請參閱[功能建議注釋](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [?.和？[ 運算子] 運算子](member-access-operators.md#null-conditional-operators--and-)
- [？： 運算子](conditional-operator.md)
