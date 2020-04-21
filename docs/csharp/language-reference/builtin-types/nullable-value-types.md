---
title: 空白值型態 - C# 參考
description: 瞭解 C# 可空數型態與如何使用它們
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: fcd49d7d25b0ad23363db8cb61596004b2e87a8d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738990"
---
# <a name="nullable-value-types-c-reference"></a>空白值型態(C# 引用)

*空值類型*`T?`表示其基礎[值類型](value-types.md)`T`的所有值和附加[空](../keywords/null.md)值。 例如,您可以將以下三個值`bool?`中的任何一個分配給變數: `true``false`、`null`或 。 基礎值類型`T`不能為空值類型本身。

> [!NOTE]
> C# 8.0 引入了可無可引用類型功能。 有關詳細資訊,請參閱[空參考類型](nullable-reference-types.md)。 空值類型從 C# 2 開始可用。

任何空值類型都是泛型<xref:System.Nullable%601?displayProperty=nameWithType>結構的實例。 在以下任何可相互換表單中,可以參考具有基礎類型的`T`空值類型:`Nullable<T>``T?`或 。

當您需要表示基礎值類型的未定義值時,通常使用空值類型。 例如,布林`bool`或的變數只能是`true``false`或 。 但是,在某些應用程式中,變數值可能是未定義或缺少的。 例如,資料庫欄位可能包含`true``false`或 ,或者它可能不包含任何`NULL`值, 即 。 您可以在該方案中使用`bool?`類型。

## <a name="declaration-and-assignment"></a>宣告與指派

由於值類型是隱式轉換為相應的空值類型,因此可以將值分配給可空值類型的變數,就像對其基礎值類型執行此操作一樣。 您還可以分配該`null`值。 例如：

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

null 值類型的預設值`null`表示,即它是<xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>屬性`false`返回的實例。

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>檢查空值類型的實體

從 C# 7.0 開始,可以使用`null`[`is`具有類型模式的運算子](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching)來檢查基礎類型的空值類型的實體與基礎類型的值:

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

將使用以下唯讀屬性來檢查與取得可 null 值類型變數的值:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>指示空值類型的實例是否具有其基礎類型的值。

- 若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。 若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。

下面的範例使用`HasValue`屬性 在顯示變數之前測試變數是否包含值:

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

您還可以將空值類型的變數與`null`而不是使用`HasValue`屬性進行比較,如以下範例所示:

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>從空白型別轉換為基礎型態

如果要將空數型態的值分配給非空值類型變數,則可能需要指定要分配的值以代替`null`。 使用[空聚接運算子`??`](../operators/null-coalescing-operator.md)執行此動作(您也可以<xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType>將方法用於相同的目的):

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

如果要使用 基礎值類型的[預設值](default-values.md)`null`代替<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>, 請使用方法。

您還可以顯式將空值類型轉換為非空類型,如下例所示:

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

在執行時,如果空數型態為`null`,則顯示式強制轉換<xref:System.InvalidOperationException>。

不可空值類型`T`隱式轉換為相應的空值類型`T?`。

## <a name="lifted-operators"></a>提高運算子

預定義的未元運算元和二進位[運算元](../operators/index.md)或值類型`T`支援的任何重載運算符也受相應的空值類型`T?`的支援。 這些操作者,也稱為*提升運算符*,如果`null`一個或兩個操作數是`null`; 如果一個或兩個操作數是,則生產。否則,運算符使用其操作數的包含值來計算結果。 例如：

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> 對於`bool?`類型,預`&`定義 運算元`|`和 運算符不遵循本節中描述的規則:即使其中一個操作數`null`為 ,運算符評估的結果也可以為非 null。 如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。

對於[比較運算子](../operators/comparison-operators.md)`<``>``<=`、、`>=`和 ,如果一個或兩`null`個操作數`false`是 ,則 結果是 ;否則,將比較操作數的包含值。 請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。 下列範例會顯示 10

- 既不大於也不等於`null`
- 也不小於`null`

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

對於[相等運算符](../operators/equality-operators.md#equality-operator-)`==``null`, 如果兩個操作數均為 ,`true`則結果是 ,如果只有一`null`個操作數是`false`,則結果是;否則,將比較操作數的包含值。

對於[不等式運算符](../operators/equality-operators.md#inequality-operator-)`!=`,如果兩個操作數`null`均為 ,則`false`結果是 ,如果只有一個`null`操作數是 ,`true`則結果是;否則,將比較操作數的包含值。

如果兩種值類型之間存在[使用者定義的轉換](../operators/user-defined-conversion-operators.md),則在相應的空值類型之間也可以使用相同的轉換。

## <a name="boxing-and-unboxing"></a>Boxing 和 Unboxing

空白型態型`T?`態的 實體[:](../../programming-guide/types/boxing-and-unboxing.md)

- 若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。
- 如果<xref:System.Nullable%601.HasValue%2A>返回`true`,則基礎值類型`T`的 相應值將裝箱<xref:System.Nullable%601>,而不是 實例。

您可以將值型態`T`的 裝箱值解箱到相應的空`T?`值類型 ,如下例所示:

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>如何辨識可無效值類型

下面的範例展示如何確定<xref:System.Type?displayProperty=nameWithType>實體是否表示建構的 null 值類型,即具有指定<xref:System.Nullable%601?displayProperty=nameWithType>`T`類型參數的類型 :

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

如範例所示,您可以使用[類型的](../operators/type-testing-and-cast.md#typeof-operator)運算符創建<xref:System.Type?displayProperty=nameWithType>實例。

如果要確定實例是否為空值類型,請不要使用<xref:System.Object.GetType%2A?displayProperty=nameWithType>方法 獲取使用上述<xref:System.Type>代碼測試 實例。 當您在<xref:System.Object.GetType%2A?displayProperty=nameWithType>null 值類型的實體上調用 方法時,實體將[裝箱](#boxing-and-unboxing)到<xref:System.Object>。 由於空值類型的非空實例的裝箱等效於基礎類型的值裝箱,因此<xref:System.Object.GetType%2A>傳回表示空值類型的基礎類型<xref:System.Type>的 實體:

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

此外,不要使用[is](../operators/type-testing-and-cast.md#is-operator)運算元來確定實例是否具有空值類型。 如以下範例所示,您無法與`is`運算子區分空值類型實體的類型及其基礎類型實例:

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

可以使用以下範例中的代碼來確定實體是否具有空值類型:

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> 將最後選取的檔案不適用於[空引檔型態](nullable-reference-types.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [可為 Null 的型別](~/_csharplang/spec/types.md#nullable-types)
- [提高運算子](~/_csharplang/spec/expressions.md#lifted-operators)
- [隱含式空轉換](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [明確可不正確轉換](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [提高轉換運算子](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- ["提升"究竟是什麼意思?](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [可為 Null 的參考型別](nullable-reference-types.md)
