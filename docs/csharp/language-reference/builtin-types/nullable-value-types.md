---
title: 可為 null 的C#實數值型別-參考
description: 瞭解C#可為 null 的實值型別，以及如何使用它們
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 42673d16ac68bbf119e57e4c357b1b2b2a0b5c51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740942"
---
# <a name="nullable-value-types-c-reference"></a>可為 null 的C#實數值型別（參考）

可為 null 的實數值型別 `T?` 代表其基礎[數值型別](value-types.md)的所有值，`T` 和額外的[null](../keywords/null.md)值。 例如，您可以將下列三個值的任何一個指派給 `bool?` 變數： `true`、`false`或 `null`。 基礎數值型別 `T` 不能是可為 null 的實數值型別本身。

> [!NOTE]
> C#8.0 引進了可為 null 的參考型別功能。 如需詳細資訊，請參閱[可為 null 的參考型別](../../nullable-references.md)。 開頭為C# 2 的可為 null 的實數值型別。

任何可為 null 的實值型別都是泛型 <xref:System.Nullable%601?displayProperty=nameWithType> 結構的實例。 您可以使用下列任何可互換的形式，參考具有基礎類型 `T` 的可為 null 的實數值型別： `Nullable<T>` 或 `T?`。

當您需要代表基礎實數值型別的未定義值時，通常會使用可為 null 的實數值型別。 例如，布林值或 `bool`變數只能是 `true` 或 `false`。 不過，在某些應用程式中，變數值可以是未定義或遺失。 例如，資料庫欄位可能包含 `true` 或 `false`，或完全不包含任何值，也就是 `NULL`。 在該案例中，您可以使用 `bool?` 類型。

## <a name="declaration-and-assignment"></a>宣告與指派

當實值型別可隱含轉換成對應的可為 null 實值型別時，您可以將值指派給可為 null 實值型別的變數，就像它的基礎實值型別一樣。 您也可以指派 `null` 值。 例如：

[!code-csharp[declare and assign](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Declaration)]

可為 null 的實數值型別的預設值表示 `null`，也就是其 <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 屬性會傳回 `false`的實例。

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>檢查可為 null 實數值型別的實例

從C# 7.0 開始，您可以使用[`is` 運算子搭配類型模式](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching)，以檢查可為 null 實數值型別的實例，以進行 `null` 並取出基礎類型的值：

[!code-csharp-interactive[use pattern matching](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#PatternMatching)]

您一律可以使用下列唯讀屬性來檢查並取得可為 null 的實數值型別變數的值：

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 指出可為 null 的實數值型別的實例是否具有其基礎類型的值。

- 若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。 若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。

下列範例會使用 `HasValue` 屬性來測試變數是否包含值，然後才顯示它：

[!code-csharp-interactive[use HasValue](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#HasValue)]

您也可以將可為 null 的實數值型別的變數與 `null` 比較，而不是使用 `HasValue` 屬性，如下列範例所示：

[!code-csharp-interactive[use comparison with null](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>從可為 null 的實數值型別轉換成基礎類型

如果您想要將可為 null 的實值型別值指派給不可為 null 的實值型別變數，您可能需要指定要指派來取代 `null`的值。 使用[null 聯合運算子 `??`](../operators/null-coalescing-operator.md)來執行此動作（您也可以使用 <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> 方法來達到相同目的）：

[!code-csharp-interactive[?? operator](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#NullCoalescing)]

如果您想要使用基礎數值型別的[預設](default-values.md)值來取代 `null`，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。

您也可以將可為 null 的實值型別明確轉換成不可為 null 的型別，如下列範例所示：

[!code-csharp[explicit cast](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Cast)]

在執行時間，如果可為 null 的實值型別的值是 `null`，則明確的轉換會擲回 <xref:System.InvalidOperationException>。

不可為 null 的實數值型別 `T` 可以隱含地轉換成對應的可為 null 實數值型別 `T?`。

## <a name="lifted-operators"></a>提升運算子

預先定義的一元和二元運算子，或實值型別所支援的任何多載運算子，也都受到對應的可為 null 實值型別支援 `T?``T`。 如果 `null`一個或兩個運算元，這些運算子（也稱為「*提升運算子*」）就會產生 `null`;否則，運算子會使用其運算元的包含值來計算結果。 例如：

[!code-csharp[lifted operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> 針對 `bool?` 類型，預先定義的 `&` 和 `|` 運算子不會遵循本節所述的規則：即使其中一個運算元已 `null`，運算子評估的結果也可以是非 null。 如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。

若為[比較運算子](../operators/comparison-operators.md)`<`、`>`、`<=`和 `>=`，如果其中一個或兩個運算元都 `null`，則結果會是 `false`。否則，會比較運算元的包含值。 請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。 下列範例會顯示 10

- 不大於或等於 `null`
- 或小於 `null`

[!code-csharp-interactive[relational and equality operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#ComparisonOperators)]

上述範例也顯示兩個可為 null 的實值型別實例的相等比較，兩者都 `null` 評估為 `true`。

如果兩個實數值型別之間有[使用者定義的轉換](../operators/user-defined-conversion-operators.md)，也可以在對應的可為 null 實數值型別之間使用相同的轉換。

## <a name="boxing-and-unboxing"></a>Boxing 和 Unboxing

可為 null 的實值型別 `T?` 的實例如下[所示：](../../programming-guide/types/boxing-and-unboxing.md)

- 若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。
- 如果 <xref:System.Nullable%601.HasValue%2A> 傳回 `true`，則基礎實數值型別 `T` 的對應值會被裝箱，而不是 <xref:System.Nullable%601>的實例。

您可以將實數值型別的已裝箱值取消封裝，`T` 至對應的可為 null 實數值型別 `T?`，如下列範例所示：

[!code-csharp-interactive[boxing and unboxing](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>如何識別可為 null 的實數值型別

下列範例示範如何判斷 <xref:System.Type?displayProperty=nameWithType> 實例是否代表可為 null 的實值型別，也就是具有指定之型別參數的 <xref:System.Nullable%601?displayProperty=nameWithType> 型別 `T`：

[!code-csharp-interactive[whether Type is nullable](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsTypeNullable)]

如範例所示，您可以使用[typeof](../operators/type-testing-and-cast.md#typeof-operator)運算子來建立 <xref:System.Type?displayProperty=nameWithType> 實例。

如果您想要判斷實例是否屬於可為 null 的實值型別，請不要使用 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法來取得要使用上述程式碼測試的 <xref:System.Type> 實例。 當您在可為 null 的實值型別實例上呼叫 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法時，實例會被[封裝](#boxing-and-unboxing)成 <xref:System.Object>。 當可為 null 的實數值型別之非 null 實例的裝箱相當於基礎類型值的裝箱時，<xref:System.Object.GetType%2A> 會傳回代表可為 null 實數值型別之基礎類型的 <xref:System.Type> 實例：

[!code-csharp-interactive[GetType example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#GetType)]

此外，請不要使用[is](../operators/type-testing-and-cast.md#is-operator)運算子來判斷實例是否屬於可為 null 的實值型別。 如下列範例所示，您無法使用 `is` 運算子來區別可為 null 的實數值型別實例和其基礎類型實例的類型：

[!code-csharp-interactive[is operator example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsOperator)]

您可以使用下列範例所顯示的程式碼，來判斷實例是否為可為 null 的實數值型別：

[!code-csharp-interactive[whether an instance is of a nullable type](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> 在[可為 null 的參考型別](../../nullable-references.md)的情況下，本節中所述的方法並不適用。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [可為 Null 的型別](~/_csharplang/spec/types.md#nullable-types)
- [提升運算子](~/_csharplang/spec/expressions.md#lifted-operators)
- [隱含可為 null 的轉換](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [明確可為 null 的轉換](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [提升的轉換運算子](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [「增益」(Lift) 的真正意義是什麼？(英文)](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [可為 Null 的參考類型](../../nullable-references.md)
