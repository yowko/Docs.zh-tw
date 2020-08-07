---
title: '類型測試運算子和轉換運算式-c # 參考'
description: 了解可用來檢查運算式結果型別的 C# 運算子，並視需要將它轉換成其他型別。
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
- as
- typeof
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: 328a40f0213cbb55f86e16625507c1a5a5d775fb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855825"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a>類型測試運算子和轉換運算式 (c # 參考) 

您可以使用下列運算子和運算式來執行類型檢查或類型轉換：

- [is 運算子](#is-operator)：檢查運算式的執行階段型別是否與給定型別相容
- [as 運算子](#as-operator)：如果運算式的執行階段型別與給定型別相容，就將它明確地轉換成該型別
- [cast 運算式](#cast-expression)：執行明確轉換
- [typeof 運算子](#typeof-operator)：取得型別的 <xref:System.Type?displayProperty=nameWithType> 執行個體

## <a name="is-operator"></a>is 運算子

`is` 運算子會檢查運算式結果的執行階段型別是否與給定型別相容。 從 c # 7.0 開始， `is` 運算子也會針對模式測試運算式結果。

使用型別測試 `is` 運算子運算式有下列格式

```csharp
E is T
```

其中 `E` 是會傳回值的運算式，而 `T` 是型別名稱或型別參數。 `E` 不能是匿名方法或 Lambda 運算式。

如果 `E` 的結果是非 Null 且可轉換成型別 `T` (藉由參考轉換、Boxing 轉換或 Unboxing 轉換)，則 `E is T` 運算式傳回 `true`；否則傳回 `false`。 `is` 運算子不會考慮使用者定義轉換。

下列範例示範當運算式結果的執行階段型別衍生自給定型別 (表示型別之間存在參考轉換) 時，`is` 運算子傳回 `true`：

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

下一個範例顯示 `is` 運算子會將裝箱和取消裝箱轉換納入考慮，但不會考慮[數值轉換](../builtin-types/numeric-conversions.md)：

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

如需 C# 轉換的資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[轉換](~/_csharplang/spec/conversions.md)一章。

### <a name="type-testing-with-pattern-matching"></a>包含模式比對的型別測試

從 c # 7.0 開始， `is` 運算子也會針對模式測試運算式結果。 尤其是，它支援下列格式的型別模式：

```csharp
E is T v
```

其中 `E` 是會傳回值的運算式，`T` 是型別名稱或型別參數，而 `v` 是型別為 `T` 的新區域變數。 如果 `E` 的結果是非 Null，且可轉換成 `T` (藉由參考、Boxing 或 Unboxing 轉換)，則 `E is T v` 運算式會傳回 `true`，且 `E` 的結果會指派至變數 `v`。

下列範例示範包含型別模式的 `is` 運算子用法：

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

如需型別模式和其他支援模式的詳細資訊，請參閱[使用 is 的模式比對](../keywords/is.md#pattern-matching-with-is)。

## <a name="as-operator"></a>as 運算子

`as` 運算子將運算式的結果明確地轉換成給定參考或可為 Null 的實值型別。 如果無法轉換，則 `as` 運算子會傳回 `null`。 不同于[cast 運算式](#cast-expression)， `as` 運算子絕對不會擲回例外狀況。

以下格式的運算式

```csharp
E as T
```

其中 `E` 是會傳回值的運算式，而 `T` 是型別名稱或型別參數，產生的結果與下列相同

```csharp
E is T ? (T)(E) : (T)null
```

但只會評估 `E` 一次。

`as` 運算子只考慮參考、可為 Null、Boxing 和 Unboxing 轉換。 您無法使用 `as` 運算子來執行使用者定義轉換。 若要這麼做，請使用[cast 運算式](#cast-expression)。

下列範例示範 `as` 運算子的用法：

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> 如上述範例所示，您需要將 `as` 陳述式的結果與 `null` 比較，以檢查轉換是否成功。 從 c # 7.0 開始，您可以使用[is 運算子](#type-testing-with-pattern-matching)來測試轉換是否成功，如果成功，請將其結果指派給新的變數。

## <a name="cast-expression"></a>轉換運算式

格式為 `(T)E` 的轉換運算式會執行明確轉換，將運算式 `E` 的結果轉換成型別 `T`。 如果沒有從型別 `E` 轉換成型別 `T` 的明確轉換存在，就會發生編譯時期錯誤。 在執行階段，明確轉換可能不會成功，且轉換運算式可能會擲回例外狀況。

下列範例示範明確的數值和參考轉換：

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

如需支援之明確轉換的資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[明確轉換](~/_csharplang/spec/conversions.md#explicit-conversions)一節。 如需如何定義自訂明確或隱含型別轉換的資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。

### <a name="other-usages-of-"></a>() 的其他用法

您也使用括號來[呼叫方法或叫用委派](member-access-operators.md#invocation-expression-)。

括弧的其他用法是調整評估運算式中作業的順序。 如需詳細資訊，請參閱 [C# 運算子](index.md)。

## <a name="typeof-operator"></a>typeof 運算子

`typeof` 運算子會取得型別的 <xref:System.Type?displayProperty=nameWithType> 執行個體。 `typeof` 運算子的引數必須是型別名稱或型別參數，如下列範例所示：

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

您也可以使用運算子搭配未系結 `typeof` 的泛型型別。 未繫結泛型型別的名稱必須包含適當數目的逗號，也就是比型別參數數目少一。 下列範例顯示搭配使用 `typeof` 運算子和未繫結泛型型別的用法：

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

運算式不能作為 `typeof` 運算子的引數。 若要取得 <xref:System.Type?displayProperty=nameWithType> 運算式結果之執行時間類型的實例，請使用 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法。

### <a name="type-testing-with-the-typeof-operator"></a>使用 `typeof` 運算子的型別測試

使用 `typeof` 運算子來檢查運算式結果的執行階段型別，是否完全符合給定型別。 下列範例示範使用 `typeof` 運算子和 [is 運算子](#is-operator)，執行型別檢查之間的差異：

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>運算子是否可多載

`is`、 `as` 和 `typeof` 運算子無法多載。

使用者定義型別不可多載 `()` 運算子，但可定義可由轉換運算式執行的自訂型別轉換。 如需詳細資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [is 運算子](~/_csharplang/spec/expressions.md#the-is-operator)
- [as 運算子](~/_csharplang/spec/expressions.md#the-as-operator)
- [轉換運算式](~/_csharplang/spec/expressions.md#cast-expressions)
- [Typeof 運算子](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [如何使用模式比對和 is 和 as 運算子，安全地轉換](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [.NET 的泛型](../../../standard/generics/index.md)
