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
# <a name="-operator-c-reference"></a><span data-ttu-id="6c397-102">() 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6c397-102">() operator (C# Reference)</span></span>

<span data-ttu-id="6c397-103">括號，`()`，通常用於方法或委派的引動過程，或在轉換運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="6c397-103">Parentheses, `()`, are typically used for method or delegate invocation or in cast expressions.</span></span>

<span data-ttu-id="6c397-104">您也可以使用括號來指定評估運算式中作業的順序。</span><span class="sxs-lookup"><span data-stu-id="6c397-104">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="6c397-105">如需詳細資訊，請參閱[運算子](../../programming-guide/statements-expressions-operators/operators.md)一文的[新增括號](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses)小節。</span><span class="sxs-lookup"><span data-stu-id="6c397-105">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="6c397-106">對於按優先順序層級排序的運算子清單，請參閱 [C# 運算子](index.md)。</span><span class="sxs-lookup"><span data-stu-id="6c397-106">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="method-invocation"></a><span data-ttu-id="6c397-107">方法引動過程</span><span class="sxs-lookup"><span data-stu-id="6c397-107">Method invocation</span></span>

<span data-ttu-id="6c397-108">以下範例示範如何叫用方法 (使用或不使用引數)，以及委派：</span><span class="sxs-lookup"><span data-stu-id="6c397-108">The following example demonstrates how to invoke a method, with or without arguments, and a delegate:</span></span>

[!code-csharp-interactive[use for invocation](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

<span data-ttu-id="6c397-109">當您使用 [`new`](../keywords/new-operator.md) 運算子叫用[建構函式](../../programming-guide/classes-and-structs/constructors.md)時，您也會使用括號。</span><span class="sxs-lookup"><span data-stu-id="6c397-109">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with a [`new`](../keywords/new-operator.md) operator.</span></span>

<span data-ttu-id="6c397-110">如需這些方法的詳細資訊，請參閱[方法](../../programming-guide/classes-and-structs/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="6c397-110">For more information about methods, see [Methods](../../programming-guide/classes-and-structs/methods.md).</span></span> <span data-ttu-id="6c397-111">如需委派的詳細資訊，請參閱[委派](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6c397-111">For more information about delegates, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="cast-expression"></a><span data-ttu-id="6c397-112">轉換運算式</span><span class="sxs-lookup"><span data-stu-id="6c397-112">Cast expression</span></span>

<span data-ttu-id="6c397-113">`(T)E` 形式的轉換運算式會叫用轉換運算子，將運算式 `E` 的值轉換成型別 `T`。</span><span class="sxs-lookup"><span data-stu-id="6c397-113">A cast expression of the form `(T)E` invokes a conversion operator to convert the value of expression `E` to type `T`.</span></span> <span data-ttu-id="6c397-114">如果沒有從型別 `E` 轉換成型別 `T` 的明確轉換存在，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="6c397-114">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="6c397-115">如需如何定義轉換運算子的資訊，請參閱 [explicit](../keywords/explicit.md) 和 [implicit](../keywords/implicit.md) 關鍵字文章。</span><span class="sxs-lookup"><span data-stu-id="6c397-115">For information about how to define a conversion operator, see the [explicit](../keywords/explicit.md) and [implicit](../keywords/implicit.md) keyword articles.</span></span>

<span data-ttu-id="6c397-116">下列範例將示範數字型別之間的型別轉換：</span><span class="sxs-lookup"><span data-stu-id="6c397-116">The following example demonstrates type conversion between numeric types:</span></span>

[!code-csharp-interactive[use for cast](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

<span data-ttu-id="6c397-117">如需在數字型別之間進行預先定義明確轉換的詳細資訊，請參閱[明確數值轉換表](../keywords/explicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="6c397-117">For more information about predefined explicit conversions between numeric types, see [Explicit numeric conversions table](../keywords/explicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="6c397-118">如需詳細資訊，請參閱[轉換和類型轉換](../../programming-guide/types/casting-and-type-conversions.md)和[轉換運算子](../../programming-guide/statements-expressions-operators/conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="6c397-118">For more information, see [Casting and type conversions](../../programming-guide/types/casting-and-type-conversions.md) and [Conversion operators](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="6c397-119">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="6c397-119">Operator overloadability</span></span>

<span data-ttu-id="6c397-120">無法多載 `()` 運算子。</span><span class="sxs-lookup"><span data-stu-id="6c397-120">The operator `()` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6c397-121">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6c397-121">C# language specification</span></span>

<span data-ttu-id="6c397-122">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[叫用運算式](~/_csharplang/spec/expressions.md#invocation-expressions)和[轉換運算式](~/_csharplang/spec/expressions.md#cast-expressions)小節。</span><span class="sxs-lookup"><span data-stu-id="6c397-122">For more information, see the [Invocation expressions](~/_csharplang/spec/expressions.md#invocation-expressions) and [Cast expressions](~/_csharplang/spec/expressions.md#cast-expressions) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c397-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c397-123">See also</span></span>

- [<span data-ttu-id="6c397-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6c397-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6c397-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6c397-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6c397-126">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="6c397-126">C# Operators</span></span>](index.md)