---
title: 使用可為 Null 的型別 - C# 程式設計手冊
ms.custom: seodec18
description: 了解如何使用可為 Null 的型別
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 75b8889f5f1f1b0dab4aa365daa34ef5ae226b02
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588828"
---
# <a name="using-nullable-types-c-programming-guide"></a>使用可為 Null 的型別 (C# 程式設計指南)

可為 Null 的型別為代表所有基礎實值型別 `T` 值的型別，以及一個額外的 [null](../../language-reference/keywords/null.md) 值。 如需詳細資訊，請參閱[可為 Null 的型別](index.md)主題。

您可以下列任何一種形式參考可為 Null 的型別：`Nullable<T>` 或 `T?`。 這兩種形式可互換。  
  
## <a name="declaration-and-assignment"></a>宣告與指派

與實值型別可隱含轉換為對應可為 Null 的型別相同，您可以用為其基礎實值型別指派值的相同方式，將值指派給可為 Null 的型別。 您也可以指派 `null` 值。  例如：
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>檢查可為 Null 型別的值

使用下列唯讀屬性檢查可為 Null 型別的執行個體，擷取 null 或基礎型別的值：  
  
- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 指出可為 Null 型別的執行個體是否有其基礎型別的值。
  
- 若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。 若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。
  
下列範例中的程式碼會使用 `HasValue` 屬性，在顯示之前測試變數是否包含值：
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
您也可以使用 `null` 而非 `HasValue` 屬性，比較可為 Null 型別的變數，如以下範例所示：  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

從 C# 7.0 開始，您可以使用[模式比對](../../pattern-matching.md)檢查及取得可為 Null 型別的值：

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a>從可為 Null 型別轉換至基礎型別

若您需要將可為 Null 型別的值指派給不可為 Null 的型別，請使用 [null-coalescing 運算子 `??`](../../language-reference/operators/null-coalescing-operator.md) 指定當可為 Null 型別的值為 null 時，要指派的值 (您也可以使用 <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> 方法進行同樣的動作)：
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

若可為 Null 型別的值為 Null 時要使用的值為基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。
  
您也可以明確將可為 Null 的型別轉換為不可為 Null 的型別。 例如：  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

在執行階段，若可為 Null 型別的值為 Null，則明確轉換會擲回 <xref:System.InvalidOperationException>。

不可為 Null 的實值型別會隱含轉換成對應的可為 Null 型別。
  
## <a name="operators"></a>運算子

預先定義的一元和二元運算子，以及針對實值型別而存在的任何使用者定義的運算子，也能為可為 Null 的型別所用。 若其中一或兩個運算元皆為 Null，這些運算子便會產生 Null 值；否則，運算子會使用包含的值來計算結果。 例如：  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> 針對 `bool?` 型別，預先定義的 `&` 和 `|` 運算子不會遵循本節中描述的規則：即使其中一個運算元為 Null，運算子評估的結果也可能為非 Null。 如需詳細資訊，請參閱[布林邏輯運算子](../../language-reference/operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。
  
針對關係運算子 (`<`、`>`、`<=`、`>=`)，若其中一或兩個運算元皆為 Null，則結果為 `false`。 請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。 下列範例會顯示 10

- 既不大於，也不等於 Null，
- 也不小於 Null。
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
上述範例也顯示兩個可為 Null 的型別，當其值皆為 Null 時，其相等比較評估結果為 `true`。

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[增益運算子](~/_csharplang/spec/expressions.md#lifted-operators)一節。

## <a name="boxing-and-unboxing"></a>Boxing 和 Unboxing

根據下列規則，可為 Null 的實值型別將為 [boxed](../types/boxing-and-unboxing.md)：

- 若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。  
- 若 <xref:System.Nullable%601.HasValue%2A> 傳回 `true`，則基礎實值型別 `T` 的值為 boxed，而非 <xref:System.Nullable%601> 的執行個體。

您可以將已為 boxed 的實值型別 unbox 為對應的可為 Null 型別，如下列範例所示：

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>另請參閱

- [可為 Null 的型別](index.md)
- [C# 程式設計指南](../index.md)
- [「增益」(Lift) 的真正意義是什麼？(英文)](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
