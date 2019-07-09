---
title: 運算子多載 - C# 參考
description: 了解如何多載 C# 運算子和哪些 C# 運算子可多載。
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: f9085f2a550dfacc670857a70f5b22de9e028107
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610591"
---
# <a name="operator-overloading-c-reference"></a>運算子多載 (C# 參考)

使用者定義型別可以多載預先定義的 C# 運算子。 也就是說，當其中一個或這兩個運算元屬於某類型時，該類型可以提供作業的自訂實作。 [可多載運算子](#overloadable-operators)一節會說明可多載的 C# 運算子。

使用 `operator` 關鍵字來宣告運算子。 運算子宣告必須滿足下列規則：

- 它包含 `public` 和 `static` 修飾詞。
- 一元運算子接受一個參數。 二元運算子接受兩個參數。 在每個案例中，至少一個參數必須有類型 `T` 或 `T?`，其中 `T` 是包含運算子宣告的類型。

下列範例會定義簡化的結構以表示有理數。 結構會多載一些[算術運算子](arithmetic-operators.md)：

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

## <a name="overloadable-operators"></a>可多載的運算子

下表提供 C# 運算子多載性的相關資訊：

| 運算子 | Overloadability |
| --------- | --------------- |
|[+](arithmetic-operators.md#unary-plus-and-minus-operators)、[-](arithmetic-operators.md#unary-plus-and-minus-operators)、[!](boolean-logical-operators.md#logical-negation-operator-)、[~](bitwise-and-shift-operators.md#bitwise-complement-operator-)、[++](arithmetic-operators.md#increment-operator-)、[--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md)、[false](true-false-operators.md)|可多載這些一元運算子。|
|[+](addition-operator.md)、[-](subtraction-operator.md)、[\*](arithmetic-operators.md#multiplication-operator-)、[/](arithmetic-operators.md#division-operator-)、[%](arithmetic-operators.md#remainder-operator-)、[&](boolean-logical-operators.md#logical-and-operator-)、[&#124;](boolean-logical-operators.md#logical-or-operator-)、[^](boolean-logical-operators.md#logical-exclusive-or-operator-)、[\<\<](bitwise-and-shift-operators.md#left-shift-operator-)、[>>](bitwise-and-shift-operators.md#right-shift-operator-)、[==](equality-operators.md#equality-operator-)、[!=](equality-operators.md#inequality-operator-)、[\<](comparison-operators.md#less-than-operator-)、[>](comparison-operators.md#greater-than-operator-)、[\<=](comparison-operators.md#less-than-or-equal-operator-)、[>=](comparison-operators.md#greater-than-or-equal-operator-)|可多載這些二元運算子。 某些運算子必須成對多載，如需詳細資訊，請參閱本表後的附註。|
|[&&](boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](boolean-logical-operators.md#conditional-logical-or-operator-)|條件邏輯運算子不能多載。 不過，如果具有多載 [`true` 和 `false` 運算子](true-false-operators.md) 的類型也以某種方式多載 `&` 或 <code>&#124;</code> 運算子，就可以分別針對該類型的運算元評估 `&&` 或 <code>&#124;&#124;</code> 運算子。 如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。|
|[&#91;&#93;](member-access-operators.md#indexer-operator-)|元素存取不會視為可多載的運算子，但您可定義[索引子](../../programming-guide/indexers/index.md)。|
|[(T)x](type-testing-and-conversion-operators.md#cast-operator-)|雖然轉換運算子無法多載，但您可以定義新的轉換運算子 (請參閱[明確](../keywords/explicit.md)和[隱含](../keywords/implicit.md))。|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|無法明確多載複合指派運算子。 不過，當您多載二元運算子時，也會隱含多載對應的複合指派運算子 (若有)。 例如，`+=` 是使用 `+` 進行評估 (可多載)。|
|[=](assignment-operator.md)、[.](member-access-operators.md#member-access-operator-)、[?:](conditional-operator.md)、[??](null-coalescing-operator.md)、[->](pointer-related-operators.md#pointer-member-access-operator--)、[=>](lambda-operator.md)、[f(x)](member-access-operators.md#invocation-operator-)、[as](type-testing-and-conversion-operators.md#as-operator)、[checked](../keywords/checked.md)、[unchecked](../keywords/unchecked.md)、[default](../../programming-guide/statements-expressions-operators/default-value-expressions.md)、[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md)、[is](type-testing-and-conversion-operators.md#is-operator)、[nameof](../keywords/nameof.md)、[new](new-operator.md)、[sizeof](../keywords/sizeof.md)、[typeof](type-testing-and-conversion-operators.md#typeof-operator)|這些運算子無法多載。|

> [!NOTE]
> 比較運算子必須成對多載。 也就是說，如果多載了成對運算子的其中之一，即必須也多載另一個運算子。 這類成對運算子如下：
>
> - `==` 和 `!=` 運算子
> - `<` 和 `>` 運算子
> - `<=` 和 `>=` 運算子

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [運算子多載](~/_csharplang/spec/expressions.md#operator-overloading)
- [運算子](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [Why are overloaded operators always static in C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/) (為什麼多載運算子在 C# 中一律為靜態？)
