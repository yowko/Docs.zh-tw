---
title: 使用可為 null 的C#實數值型別-程式設計指南
ms.custom: seodec18
description: 瞭解如何使用可為C# null 的實數值型別
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396170"
---
# <a name="using-nullable-value-types-c-programming-guide"></a>使用可為 null 的C#實數值型別（程式設計手冊）

可為 null 的實數值型別是類型，代表基礎數值型別的所有值 `T`，以及額外的[null](../../language-reference/keywords/null.md)值。 如需詳細資訊，請參閱[可為 null 的實數值型別](index.md)主題。

> [!NOTE]
> C#8.0 引進了可為 null 的參考型別功能。 如需詳細資訊，請參閱[可為 null 的參考型別](../../nullable-references.md)。 從C# 2 開始可以使用可為 null 的實數值型別。

您可以使用下列任何可交換的形式來參考可為 null 的實數值型別： `Nullable<T>` 或 `T?`。 `T` 必須是實值型別。

## <a name="declaration-and-assignment"></a>宣告與指派

當實值型別可以隱含地轉換成對應的可為 null 實值型別時，您可以將值指派給可為 null 的型別，就像它的基礎實值型別一樣。 您也可以指派 `null` 值。 例如:

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>檢查可為 Null 型別的值

使用下列 readonly 屬性來檢查 null 實數值型別的實例是否為 null，並取出基礎類型的值：

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 指出可為 Null 型別的執行個體是否有其基礎型別的值。

- 若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。 若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。

下列範例中的程式碼會使用 `HasValue` 屬性，在顯示之前測試變數是否包含值：

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

您也可以比較可為 null 的實值型別與 `null` 的變數，而不是使用 `HasValue` 屬性，如下列範例所示：

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

從C# 7.0 開始，您可以使用[模式](../../pattern-matching.md)比對來檢查並取得可為 null 的實數值型別的值：

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>從可為 null 的實數值型別轉換成基礎類型

如果您需要將可為 null 的實值型別值指派給不可為 null 的型別，請使用[null 聯合運算子 `??`](../../language-reference/operators/null-coalescing-operator.md)來指定如果可為 null 的實值型別值為 null 時要指派的值（您也可以使用 <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> 方法來這麼做）:

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

如果可為 null 的實值型別的值為時要使用的值為 `null` 應該是基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。

您可以將可為 null 的實值型別明確轉換成不可為 null 的型別。 例如:

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

在執行時間，如果可為 null 的實值型別值為 `null`，則明確的轉換會擲回 <xref:System.InvalidOperationException>。

不可為 Null 的實值型別會隱含轉換成對應的可為 Null 型別。

## <a name="operators"></a>運算子

預先定義的一元和二元運算子，以及任何存在於實數值型別的使用者定義運算子，也可能會由對應的可為 null 類型使用。 如果一個或兩個運算元 `null`，這些運算子會產生 `null`;否則，運算子會使用包含的值來計算結果。 例如:

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> 若為 `bool?` 類型，預先定義的 `&` 和 @no__t 2 運算子不會遵循本節所述的規則：即使其中一個運算元是 `null`，運算子評估的結果也可以是非 null。 如需詳細資訊，請參閱[布林值邏輯運算子](../../language-reference/operators/boolean-logical-operators.md)一文的[可為 Null 的布林值邏輯運算子](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。
  
對於關係運算子（`<`，`>`，`<=`，`>=`），如果其中一個或兩個運算元都是 `null`，則結果會是 `false`。 請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。 下列範例會顯示 10

- 不能大於或等於 `null`，
- 或小於 `null`。

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

上述範例也顯示兩個 null 實值型別的相等比較會評估為 `true`。

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[增益運算子](~/_csharplang/spec/expressions.md#lifted-operators)一節。

## <a name="boxing-and-unboxing"></a>Boxing 和 Unboxing

根據下列規則，可為 Null 的實值型別將為 [boxed](../types/boxing-and-unboxing.md)：

- 若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。
- 若 <xref:System.Nullable%601.HasValue%2A> 傳回 `true`，則基礎實值型別 `T` 的值為 boxed，而非 <xref:System.Nullable%601> 的執行個體。

您可以將已為 boxed 的實值型別 unbox 為對應的可為 Null 型別，如下列範例所示：

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>另請參閱

- [可為 Null 的實值型別](index.md)
- [「增益」(Lift) 的真正意義是什麼？(英文)](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
