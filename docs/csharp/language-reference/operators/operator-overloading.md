---
title: 運算子多載 - C# 參考
description: 了解如何多載 C# 運算子和哪些 C# 運算子可多載。
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: 18da3a22d22f338d2f319d394d50d08e4d35e7eb
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121434"
---
# <a name="operator-overloading-c-reference"></a>運算子多載 (C# 參考)

使用者定義型別可以多載預先定義的 C# 運算子。 也就是說,類型可以提供操作的自定義實現,以防其中一個或兩個操作數是該類型的。 [可多載運算子](#overloadable-operators)一節會說明可多載的 C# 運算子。

使用 `operator` 關鍵字來宣告運算子。 運算子宣告必須滿足下列規則：

- 它包含 `public` 和 `static` 修飾詞。
- 一個未輸入運算元有一個輸入參數。 二進位運算元有兩個輸入參數。 在每個案例中，至少一個參數必須有類型 `T` 或 `T?`，其中 `T` 是包含運算子宣告的類型。

下列範例會定義簡化的結構以表示有理數。 結構會多載一些[算術運算子](arithmetic-operators.md)：

[!code-csharp[fraction example](snippets/OperatorOverloading.cs)]

可以通過定義從`int``Fraction`的[隱式轉換](user-defined-conversion-operators.md)來擴展前面的示例。 多載運算子即可支援這兩種類型的引數。 亦即，您可以將整數新增至分數，並取得分數的結果。

您也可以使用 `operator` 關鍵字定義自訂型別轉換。 如需詳細資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。

## <a name="overloadable-operators"></a>可多載的運算子

下表提供 C# 運算子多載性的相關資訊：

| 操作員 | Overloadability |
| --------- | --------------- |
|[+x](arithmetic-operators.md#unary-plus-and-minus-operators)、[-x](arithmetic-operators.md#unary-plus-and-minus-operators)、[!x](boolean-logical-operators.md#logical-negation-operator-)、[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-)、[++](arithmetic-operators.md#increment-operator-)、[--](arithmetic-operators.md#decrement-operator---)、[true](true-false-operators.md)、[false](true-false-operators.md)|可多載這些一元運算子。|
|[x + y](addition-operator.md)、[x - y](subtraction-operator.md)、[x \* y](arithmetic-operators.md#multiplication-operator-)、[x / y](arithmetic-operators.md#division-operator-)、[x % y](arithmetic-operators.md#remainder-operator-)、[x & y](boolean-logical-operators.md#logical-and-operator-)、[x &#124; y](boolean-logical-operators.md#logical-or-operator-)、[x ^ y](boolean-logical-operators.md#logical-exclusive-or-operator-)、[x \<\< y](bitwise-and-shift-operators.md#left-shift-operator-)、[x >> y](bitwise-and-shift-operators.md#right-shift-operator-)、[x == y](equality-operators.md#equality-operator-)、[x != y](equality-operators.md#inequality-operator-)、[x \< y](comparison-operators.md#less-than-operator-)、[x > y](comparison-operators.md#greater-than-operator-)、[x \<= y](comparison-operators.md#less-than-or-equal-operator-)、[x >= y](comparison-operators.md#greater-than-or-equal-operator-)|可多載這些二元運算子。 某些運算子必須成對多載，如需詳細資訊，請參閱本表後的附註。|
|[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-)、[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|條件邏輯運算子不能多載。 但是,如果具有過載[`true`和`false`運算元](true-false-operators.md)的類型也以某種方式重載`&`或<code>&#124;</code>運算符,`&&`則可以分別計算<code>&#124;&#124;</code>或運算符的該類型的操作數。 如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。|
|[a&#91;i&#93;](member-access-operators.md#indexer-operator-)|元素存取不會視為可多載的運算子，但您可定義[索引子](../../programming-guide/indexers/index.md)。|
|[(T)x](type-testing-and-cast.md#cast-expression)|不能重載強制轉換運算子,但您可以定義可以由強制轉換表達式執行的自定義類型轉換。 如需詳細資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。|
|[+=](arithmetic-operators.md#compound-assignment)、、、、、、、、、&#124;[ \< \< ](bitwise-and-shift-operators.md#compound-assignment) [ \* ](arithmetic-operators.md#compound-assignment) [&#124;=](boolean-logical-operators.md#compound-assignment) [^=](boolean-logical-operators.md#compound-assignment) 、、、、、、、、、、、、、、、、、、、、、、、、、 [/=](arithmetic-operators.md#compound-assignment) [%=](arithmetic-operators.md#compound-assignment) [&=](boolean-logical-operators.md#compound-assignment) [-=](arithmetic-operators.md#compound-assignment)[>>=](bitwise-and-shift-operators.md#compound-assignment)|無法明確多載複合指派運算子。 不過，當您多載二元運算子時，也會隱含多載對應的複合指派運算子 (若有)。 例如，`+=` 是使用 `+` 進行評估 (可多載)。|
|[\x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x.y](member-access-operators.md#member-access-expression-), [c ? t : f](conditional-operator.md), x ? [y](null-coalescing-operator.md), x ? ? ? ? ? [= y](null-coalescing-operator.md), [x.y,](member-access-operators.md#range-operator-) [x->](pointer-related-operators.md#pointer-member-access-operator--) [=>](lambda-operator.md)y , [, f(x) ,](member-access-operators.md#invocation-expression-)[作為](type-testing-and-cast.md#as-operator),[等待](await.md),[檢查](../keywords/checked.md),[沒有選取](../keywords/unchecked.md),[預設](default.md),[委託](delegate-operator.md),[是](type-testing-and-cast.md#is-operator),[名稱,](nameof.md)[新](new-operator.md),[大小](sizeof.md),[堆疊](stackalloc.md),[類型](type-testing-and-cast.md#typeof-operator)|這些運算子無法多載。|

> [!NOTE]
> 比較運算子必須成對多載。 也就是說，如果多載了成對運算子的其中之一，即必須也多載另一個運算子。 這類成對運算子如下：
>
> - `==` 和 `!=` 運算子
> - `<` 和 `>` 運算子
> - `<=` 和 `>=` 運算子

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [運算子多載](~/_csharplang/spec/expressions.md#operator-overloading)
- [操作員](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [使用者定義轉換運算子](user-defined-conversion-operators.md)
- [設計指南 - 管理員載入](../../../standard/design-guidelines/operator-overloads.md)
- [設計指南 ─相等運算子](../../../standard/design-guidelines/equality-operators.md)
- [為什麼多載運算子在 C# 中一律為靜態？](https://docs.microsoft.com/archive/blogs/ericlippert/why-are-overloaded-operators-always-static-in-c)
