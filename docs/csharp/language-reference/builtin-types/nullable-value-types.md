---
title: 空數值型別 - C# 引用
description: 瞭解 C# 可空數值型別以及如何使用它們
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: a84b3d60269491846b783e5046a84a1d14e258a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399585"
---
# <a name="nullable-value-types-c-reference"></a>空數值型別（C# 引用）

*空數值型別*`T?`表示其基礎[數值型別](value-types.md)`T`的所有值和附加[空](../keywords/null.md)值。 例如，您可以將以下三個值`bool?`中的任何一個分配給變數： `true`、`false`或`null`。 基礎數值型別`T`不能為空數值型別本身。

> [!NOTE]
> C# 8.0 引入了可無可參考型別功能。 有關詳細資訊，請參閱[空參考型別](../../nullable-references.md)。 空數值型別從 C# 2 開始可用。

任何空數值型別都是泛型<xref:System.Nullable%601?displayProperty=nameWithType>結構的實例。 在以下任何可互換表單中，可以引用具有基礎類型的`T`空數值型別：`Nullable<T>`或`T?`。

當您需要表示基礎數值型別的未定義值時，通常使用空數值型別。 例如，布林或`bool`的 變數只能是 或`true``false`。 但是，在某些應用程式中，變數值可能是未定義或缺少的。 例如，資料庫欄位可能包含`true`或`false`，或者它可能不包含任何值，`NULL`即 。 您可以在該方案中使用`bool?`類型。

## <a name="declaration-and-assignment"></a>宣告與指派

由於數值型別是隱式轉換為相應的空數值型別，因此可以將值分配給可空數值型別的變數，就像對其基礎數值型別執行此操作一樣。 您也可以指派 `null` 值。 例如：

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

null 數值型別的預設值表示`null`，即它是屬性<xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>返回`false`的實例。

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>檢查空數值型別的實例

從 C# 7.0 開始，可以使用[`is`具有類型模式的運算子](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching)來檢查基礎類型的空數值型別的實例`null`並檢索基礎類型的值：

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

始終可以使用以下唯讀屬性來檢查和獲取可 null 數值型別變數的值：

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>指示空數值型別的實例是否具有其基礎類型的值。

- 若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。 若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。

下面的示例使用 屬性`HasValue`在顯示變數之前測試變數是否包含值：

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

您還可以將空數值型別的變數與`null`而不是使用`HasValue`屬性進行比較，如以下示例所示：

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>從空數值型別轉換為基礎類型

如果要將空數值型別的值分配給非空數值型別變數，則可能需要指定要分配的值以代替`null`。 使用[空聚運運算子`??`](../operators/null-coalescing-operator.md)執行此操作（您也可以將<xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType>方法用於相同的目的）：

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

如果要使用 基礎數值型別的[預設值](default-values.md)代替`null`， 請使用<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>方法。

您還可以顯式將空數值型別轉換為非空類型，如下例所示：

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

在運行時，如果空數值型別的值為`null`，則顯式強制轉換 。 <xref:System.InvalidOperationException>

不可空數值型別`T`隱式轉換為相應的空數值型別。 `T?`

## <a name="lifted-operators"></a>提升運算子

預定義的未元運算子和二進位[運算子](../operators/index.md)或數值型別`T`支援的任何重載運算子也受相應的空數值型別`T?`的支援。 這些操作者，也稱為*提升運算子*，如果一`null`個或兩個運算元是;`null`如果一個或兩個運算元是，則生產。否則，運算子使用其運算元的包含值來計算結果。 例如：

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> 對於`bool?`類型，預定義`&`運算子和`|`運算子不遵循本節中描述的規則：即使其中一個運算元為`null`，運算子評估的結果也可以為非 null。 如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。

對於[比較運算子](../operators/comparison-operators.md)`<` `>`、、`<=`和`>=`，如果一個或兩個運算元`null`是 ，則`false`結果是 ;否則，將比較運算元的包含值。 請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。 下列範例會顯示 10

- 既不大於也不等於`null`
- 也不小於`null`

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

對於[相等運算子](../operators/equality-operators.md#equality-operator-)`==`，`null`如果兩個運算元均為 ，則結果是`true`，如果只有一個運算元是`null`，則結果是; `false`否則，將比較運算元的包含值。

對於[不等式運算子](../operators/equality-operators.md#inequality-operator-)`!=`，如果兩個運算元均為`null`，則結果是`false`，如果只有一個運算元是`null`，則結果是; `true`否則，將比較運算元的包含值。

如果兩種數值型別之間存在[使用者定義的轉換](../operators/user-defined-conversion-operators.md)，則在相應的空數值型別之間也可以使用相同的轉換。

## <a name="boxing-and-unboxing"></a>Boxing 和 Unboxing

空數值型別的`T?`實例[按如下方式裝箱](../../programming-guide/types/boxing-and-unboxing.md)：

- 若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。
- 如果<xref:System.Nullable%601.HasValue%2A>返回`true`，則基礎數值型別的`T`相應值將裝箱，而不是<xref:System.Nullable%601>實例。

您可以將數值型別的`T`裝箱值解箱到相應的空數值型別`T?`，如下例所示：

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>如何識別可無效數值型別

下面的示例演示如何確定<xref:System.Type?displayProperty=nameWithType>實例是否表示構造的 null 數值型別，即具有指定類型參數<xref:System.Nullable%601?displayProperty=nameWithType>`T`的類型 ：

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

如示例所示，您可以使用[類型的](../operators/type-testing-and-cast.md#typeof-operator)運算子創建<xref:System.Type?displayProperty=nameWithType>實例。

如果要確定實例是否為空數值型別，請不要使用 方法<xref:System.Object.GetType%2A?displayProperty=nameWithType>獲取使用上述代碼測試<xref:System.Type>實例。 當您在<xref:System.Object.GetType%2A?displayProperty=nameWithType>null 數值型別的實例上調用 方法時，實例將[裝箱](#boxing-and-unboxing)到<xref:System.Object>。 由於空數值型別的非空實例的裝箱等效于基礎類型的值裝箱，因此<xref:System.Object.GetType%2A>返回表示空數值型別的基礎類型的<xref:System.Type>實例：

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

此外，不要使用[is](../operators/type-testing-and-cast.md#is-operator)運算子來確定實例是否具有空數值型別。 如以下示例所示，您無法與`is`運算子區分空數值型別實例的類型及其基礎類型實例：

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

可以使用以下示例中提供的代碼來確定實例是否具有空數值型別：

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> 本節中描述的方法不適用於[空參考型別](../../nullable-references.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [可為 Null 的型別](~/_csharplang/spec/types.md#nullable-types)
- [提升運算子](~/_csharplang/spec/expressions.md#lifted-operators)
- [隱式空轉換](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [顯式可無效轉換](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [提升轉換運算子](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- ["提升"究竟是什麼意思？](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [可為 Null 的參考型別](../../nullable-references.md)
