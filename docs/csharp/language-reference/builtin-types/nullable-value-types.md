---
title: '可為 null 的實值型別-c # 參考'
description: '深入瞭解 c # 可為 null 的實值型別，以及如何使用它們'
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 3ab2dff6b7399b0458a69d4498b2ebda24f6c5cc
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471831"
---
# <a name="nullable-value-types-c-reference"></a>可為 null 的實數值型別 (c # 參考) 

*可為 null*的實值型別 `T?` 代表其基礎實[值型](value-types.md)別的所有值 `T` ，以及一個額外的[null](../keywords/null.md)值。 例如，您可以將下列三個值的任何一個指派給 `bool?` 變數： `true` 、 `false` 或 `null` 。 基礎實值型別 `T` 不能是可為 null 的實值型別本身。

> [!NOTE]
> C # 8.0 引進可為 null 的參考型別功能。 如需詳細資訊，請參閱 [可為 null 的參考型別](nullable-reference-types.md)。 從 c # 2 開始可以使用可為 null 的實數值型別。

任何可為 null 的實值型別都是泛型結構的實例 <xref:System.Nullable%601?displayProperty=nameWithType> 。 您可以使用下列任何可交換形式的基礎類型來參考可為 null 的實數值型別 `T` ： `Nullable<T>` 或 `T?` 。

當您需要代表基礎實值型別的未定義值時，通常會使用可為 null 的實值型別。 例如，布林值或 `bool` 變數只能是 `true` 或 `false` 。 不過，在某些應用程式中，變數值不能定義或遺失。 例如，資料庫欄位可能包含 `true` 或 `false` ，或可能完全不包含任何值，也就是 `NULL` 。 `bool?`在該案例中，您可以使用類型。

## <a name="declaration-and-assignment"></a>宣告與指派

因為實值型別可隱含轉換成對應的可為 null 實值型別，所以您可以將值指派給可為 null 實值型別的變數，就像您針對其基礎實值型別所做的一樣。 您也可以指派 `null` 值。 例如：

[!code-csharp[declare and assign](snippets/shared/NullableValueTypes.cs#Declaration)]

可為 null 之實值型別的預設值代表 `null` ，也就是其屬性會傳回的實例 <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> `false` 。

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>檢查可為 null 實值型別的實例

從 c # 7.0 開始，您可以使用[ `is` 運算子搭配型別模式](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching)來檢查可為 null 實值型別的實例 `null` ，並取出基礎型別的值：

[!code-csharp-interactive[use pattern matching](snippets/shared/NullableValueTypes.cs#PatternMatching)]

您一律可以使用下列唯讀屬性來檢查並取得可為 null 實值型別變數的值：

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 指出可為 null 實值型別的實例是否具有其基礎類型的值。

- 若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。 若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。

下列範例 `HasValue` 會使用屬性來測試變數是否包含值，然後才顯示它：

[!code-csharp-interactive[use HasValue](snippets/shared/NullableValueTypes.cs#HasValue)]

您也可以比較可為 null 實值型別的變數 `null` ，而不使用 `HasValue` 屬性，如下列範例所示：

[!code-csharp-interactive[use comparison with null](snippets/shared/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>從可為 null 的實值型別轉換為基礎類型

如果您想要將可為 null 實值型別的值指派給不可為 null 的實值型別變數，您可能需要指定要指派的值來取代 `null` 。 使用[null 聯合運算子 `??` ](../operators/null-coalescing-operator.md)來執行該作業 (您也可以 <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> 針對相同的目的) 使用方法：

[!code-csharp-interactive[?? operator](snippets/shared/NullableValueTypes.cs#NullCoalescing)]

如果您想要使用基礎數值型別的 [預設](default-values.md) 值來取代 `null` ，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。

您也可以明確地將可為 null 的實值型別轉換為不可為 null 的型別，如下列範例所示：

[!code-csharp[explicit cast](snippets/shared/NullableValueTypes.cs#Cast)]

在執行時間，如果可為 null 的實值型別值為 `null` ，明確的轉換會擲回 <xref:System.InvalidOperationException> 。

不可為 null 的實值型別 `T` 可隱含轉換成對應的可為 null 實值型別 `T?` 。

## <a name="lifted-operators"></a>提起運算子

對應的可為 null 實值型別也支援預先定義的一元和二元 [運算子](../operators/index.md) 或實數值型別所支援的任何多載運算子 `T` `T?` 。 如果一或兩個運算元都是，則這些運算子（也稱為 *提升運算子*） `null` 會產生 `null` ; 否則，運算子會使用其運算元的包含值來計算結果。 例如：

[!code-csharp[lifted operators](snippets/shared/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> 針對 `bool?` 類型，預先定義的 `&` 和 `|` 運算子不會遵循本節所述的規則：即使其中一個運算元為，運算子評估的結果也可以是非 null `null` 。 如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。

針對 [比較運算子](../operators/comparison-operators.md) `<` 、、 `>` `<=` 和 `>=` ，如果其中一個或兩個運算元都是 `null` ，則結果為 `false` ; 否則會比較運算元的包含值。 請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。 下列範例會顯示 10

- 不大於或等於 `null`
- 或小於 `null`

[!code-csharp-interactive[relational and equality operators](snippets/shared/NullableValueTypes.cs#ComparisonOperators)]

針對 [相等運算子](../operators/equality-operators.md#equality-operator-) `==` ，如果兩個運算元都是， `null` 結果就是 `true` ，如果只有一個運算元是，則結果為， `null` 否則會 `false` 比較運算元的包含值。

針對不 [等比較運算子](../operators/equality-operators.md#inequality-operator-) `!=` ，如果兩個運算元都是， `null` 結果就是 `false` ，如果只有一個運算元是，則結果為， `null` 否則會 `true` 比較運算元的包含值。

如果兩個實值型別之間有 [使用者定義的轉換](../operators/user-defined-conversion-operators.md) ，也可以在對應的可為 null 實值型別之間使用相同的轉換。

## <a name="boxing-and-unboxing"></a>Box 處理和 Unbox 處理

可為 null 的實值型別的實例 `T?` 會以下列方式 [裝箱](../../programming-guide/types/boxing-and-unboxing.md) ：

- 若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。
- 如果 <xref:System.Nullable%601.HasValue%2A> 傳回 `true` ，則會將基礎實值型別的對應值 `T` 裝箱，而不是的實例 <xref:System.Nullable%601> 。

您可以將實數值型別的已裝箱值取消封裝 `T` 為對應的可為 null 實值型別 `T?` ，如下列範例所示：

[!code-csharp-interactive[boxing and unboxing](snippets/shared/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>如何識別可為 null 的實值型別

下列範例示範如何判斷 <xref:System.Type?displayProperty=nameWithType> 實例是否代表一個可為 null 的實值型別，也就是 <xref:System.Nullable%601?displayProperty=nameWithType> 具有指定型別參數的型別 `T` ：

[!code-csharp-interactive[whether Type is nullable](snippets/shared/NullableValueTypes.cs#IsTypeNullable)]

如範例所示，您可以使用 [typeof](../operators/type-testing-and-cast.md#typeof-operator) 運算子來建立 <xref:System.Type?displayProperty=nameWithType> 實例。

如果您想要判斷某個實例是否屬於可為 null 的實值型別，請不要使用 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法來取得 <xref:System.Type> 要使用上述程式碼測試的實例。 當您 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 在可為 null 的實值型別實例上呼叫方法時，實例就會被 [封裝](#boxing-and-unboxing) 成 <xref:System.Object> 。 當可為 null 實值型別的非 null 實例的裝箱相當於基礎類型值的裝箱時，會傳回 <xref:System.Object.GetType%2A> <xref:System.Type> 表示可為 null 實值型別之基礎型別的實例：

[!code-csharp-interactive[GetType example](snippets/shared/NullableValueTypes.cs#GetType)]

此外，請勿使用「 [是](../operators/type-testing-and-cast.md#is-operator) 」運算子來判斷實例是否為可為 null 的實值型別。 如下列範例所示，您無法使用運算子來區別可為 null 的實值型別實例及其基礎型別實例的類型 `is` ：

[!code-csharp-interactive[is operator example](snippets/shared/NullableValueTypes.cs#IsOperator)]

您可以使用下列範例中所示的程式碼，判斷實例是否為可為 null 的實值型別：

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/shared/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> 在 [可為 null 的參考型別](nullable-reference-types.md)案例中，本節所述的方法不適用。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [可為 Null 的型別](~/_csharplang/spec/types.md#nullable-types)
- [提起運算子](~/_csharplang/spec/expressions.md#lifted-operators)
- [隱含可為 null 的轉換](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [明確可為 null 的轉換](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [提升的轉換運算子](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [「提升」是什麼意思？](/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [可為 Null 的參考型別](nullable-reference-types.md)
