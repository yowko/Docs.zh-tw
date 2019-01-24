---
title: () 運算子 - C# 參考
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 3a0af33739c9cb4d090842219eba4ece9700ef89
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362778"
---
# <a name="-operator-c-reference"></a>() 運算子 (C# 參考)

括號，`()`，通常用於方法或委派的引動過程，或在轉換運算式中使用。

您也可以使用括號來指定評估運算式中作業的順序。 如需詳細資訊，請參閱[運算子](../../programming-guide/statements-expressions-operators/operators.md)一文的[新增括號](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses)小節。 對於按優先順序層級排序的運算子清單，請參閱 [C# 運算子](index.md)。

## <a name="method-invocation"></a>方法引動過程

以下範例示範如何叫用方法 (使用或不使用引數)，以及委派：

[!code-csharp-interactive[use for invocation](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

當您使用 [`new`](../keywords/new-operator.md) 運算子叫用[建構函式](../../programming-guide/classes-and-structs/constructors.md)時，您也會使用括號。

如需這些方法的詳細資訊，請參閱[方法](../../programming-guide/classes-and-structs/methods.md)。 如需委派的詳細資訊，請參閱[委派](../../programming-guide/delegates/index.md)。

## <a name="cast-expression"></a>轉換運算式

`(T)E` 形式的轉換運算式會叫用轉換運算子，將運算式 `E` 的值轉換成型別 `T`。 如果沒有從型別 `E` 轉換成型別 `T` 的明確轉換存在，就會發生編譯時期錯誤。 如需如何定義轉換運算子的資訊，請參閱 [explicit](../keywords/explicit.md) 和 [implicit](../keywords/implicit.md) 關鍵字文章。

下列範例將示範數字型別之間的型別轉換：

[!code-csharp-interactive[use for cast](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

如需在數字型別之間進行預先定義明確轉換的詳細資訊，請參閱[明確數值轉換表](../keywords/explicit-numeric-conversions-table.md)。

如需詳細資訊，請參閱[轉換和類型轉換](../../programming-guide/types/casting-and-type-conversions.md)和[轉換運算子](../../programming-guide/statements-expressions-operators/conversion-operators.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

無法多載 `()` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[叫用運算式](~/_csharplang/spec/expressions.md#invocation-expressions)和[轉換運算式](~/_csharplang/spec/expressions.md#cast-expressions)小節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)