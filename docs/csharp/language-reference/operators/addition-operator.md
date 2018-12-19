---
title: + 運算子 - C# 參考
ms.custom: seodec18
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 92e20dad8ae6358f71137e955bb80e3641a66a54
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237749"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2906c-102">+ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2906c-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="2906c-103">`+` 運算子支援兩種形式：一元加號運算子或二元加法運算子。</span><span class="sxs-lookup"><span data-stu-id="2906c-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="2906c-104">一元加號運算子</span><span class="sxs-lookup"><span data-stu-id="2906c-104">Unary plus operator</span></span>

<span data-ttu-id="2906c-105">一元 `+` 運算子會傳回其運算元的值。</span><span class="sxs-lookup"><span data-stu-id="2906c-105">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="2906c-106">所有數值型別都支援。</span><span class="sxs-lookup"><span data-stu-id="2906c-106">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="2906c-107">數值加法</span><span class="sxs-lookup"><span data-stu-id="2906c-107">Numeric addition</span></span>

<span data-ttu-id="2906c-108">針對數值型別，`+` 運算子會計算其運算元的和：</span><span class="sxs-lookup"><span data-stu-id="2906c-108">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

## <a name="string-concatenation"></a><span data-ttu-id="2906c-109">字串串連</span><span class="sxs-lookup"><span data-stu-id="2906c-109">String concatenation</span></span>

<span data-ttu-id="2906c-110">當其中一或兩個運算元的型別為 [string](../keywords/string.md) 時，`+` 運算子會串連其運算元的字串表示：</span><span class="sxs-lookup"><span data-stu-id="2906c-110">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="2906c-111">從 C# 6 開始，[字串插補](../tokens/interpolated.md)提供更便利的方式進行字串格式設定：</span><span class="sxs-lookup"><span data-stu-id="2906c-111">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="2906c-112">委派組合</span><span class="sxs-lookup"><span data-stu-id="2906c-112">Delegate combination</span></span>

<span data-ttu-id="2906c-113">針對 [delegate](../keywords/delegate.md) 型別，`+` 運算子會傳回新的委派執行個體，(當叫用時) 它會叫用第一個運算元，然後再叫用第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="2906c-113">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="2906c-114">如果其中任一個運算元為 `null`，則 `+` 運算子會傳回另一個運算元的值 (也有可能是 `null`)。</span><span class="sxs-lookup"><span data-stu-id="2906c-114">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="2906c-115">下列範例顯示委派如何與 `+` 運算子結合：</span><span class="sxs-lookup"><span data-stu-id="2906c-115">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="2906c-116">如需委派型別的詳細資訊，請參閱[委派](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2906c-116">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2906c-117">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="2906c-117">Operator overloadability</span></span>

<span data-ttu-id="2906c-118">使用者定義的型別可以[多載](../keywords/operator.md)一元與二元 `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="2906c-118">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="2906c-119">多載二元 `+` 運算子時，[加法指派運算子](addition-assignment-operator.md) `+=` 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="2906c-119">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2906c-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2906c-120">C# language specification</span></span>

<span data-ttu-id="2906c-121">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[一元加號運算子](~/_csharplang/spec/expressions.md#unary-plus-operator)與[加法運算子](~/_csharplang/spec/expressions.md#addition-operator)小節。</span><span class="sxs-lookup"><span data-stu-id="2906c-121">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2906c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2906c-122">See also</span></span>

- [<span data-ttu-id="2906c-123">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2906c-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2906c-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2906c-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2906c-125">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="2906c-125">C# Operators</span></span>](index.md)
- [<span data-ttu-id="2906c-126">字串內插補點</span><span class="sxs-lookup"><span data-stu-id="2906c-126">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="2906c-127">如何：串連多個字串</span><span class="sxs-lookup"><span data-stu-id="2906c-127">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="2906c-128">委派</span><span class="sxs-lookup"><span data-stu-id="2906c-128">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="2906c-129">Checked 與 Unchecked</span><span class="sxs-lookup"><span data-stu-id="2906c-129">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
