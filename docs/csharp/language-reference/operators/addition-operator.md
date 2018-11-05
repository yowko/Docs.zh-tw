---
title: + 運算子 (C# 參考)
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: ae2774d96bc50afa271fffdea445e640e68c3647
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192293"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ed963-102">+ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ed963-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="ed963-103">`+` 運算子支援兩種形式：一元加號運算子或二元加法運算子。</span><span class="sxs-lookup"><span data-stu-id="ed963-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

<span data-ttu-id="ed963-104">使用者定義的型別可以[多載](../keywords/operator.md)一元與二元 `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="ed963-104">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="ed963-105">多載二元 `+` 運算子時，[加法指派運算子](addition-assignment-operator.md) `+=` 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="ed963-105">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="ed963-106">一元加號運算子</span><span class="sxs-lookup"><span data-stu-id="ed963-106">Unary plus operator</span></span>

<span data-ttu-id="ed963-107">一元 `+` 運算子會傳回其運算元的值。</span><span class="sxs-lookup"><span data-stu-id="ed963-107">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="ed963-108">所有數值型別都支援。</span><span class="sxs-lookup"><span data-stu-id="ed963-108">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="ed963-109">數值加法</span><span class="sxs-lookup"><span data-stu-id="ed963-109">Numeric addition</span></span>

<span data-ttu-id="ed963-110">針對數值型別，`+` 運算子會計算其運算元的和：</span><span class="sxs-lookup"><span data-stu-id="ed963-110">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

## <a name="string-concatenation"></a><span data-ttu-id="ed963-111">字串串連</span><span class="sxs-lookup"><span data-stu-id="ed963-111">String concatenation</span></span>

<span data-ttu-id="ed963-112">當其中一或兩個運算元的型別為 [string](../keywords/string.md) 時，`+` 運算子會串連其運算元的字串表示：</span><span class="sxs-lookup"><span data-stu-id="ed963-112">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="ed963-113">從 C# 6 開始，[字串插補](../tokens/interpolated.md)提供更便利的方式進行字串格式設定：</span><span class="sxs-lookup"><span data-stu-id="ed963-113">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="ed963-114">委派組合</span><span class="sxs-lookup"><span data-stu-id="ed963-114">Delegate combination</span></span>

<span data-ttu-id="ed963-115">針對 [delegate](../keywords/delegate.md) 型別，`+` 運算子會傳回新的委派執行個體，(當叫用時) 它會叫用第一個運算元，然後再叫用第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="ed963-115">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="ed963-116">如果其中任一個運算元為 `null`，則 `+` 運算子會傳回另一個運算元的值 (也有可能是 `null`)。</span><span class="sxs-lookup"><span data-stu-id="ed963-116">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="ed963-117">下列範例顯示委派如何與 `+` 運算子結合：</span><span class="sxs-lookup"><span data-stu-id="ed963-117">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="ed963-118">如需委派型別的詳細資訊，請參閱[委派](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ed963-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ed963-119">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ed963-119">C# language specification</span></span>

<span data-ttu-id="ed963-120">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[一元加號運算子](~/_csharplang/spec/expressions.md#unary-plus-operator)與[加法運算子](~/_csharplang/spec/expressions.md#addition-operator)小節。</span><span class="sxs-lookup"><span data-stu-id="ed963-120">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed963-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed963-121">See also</span></span>

- [<span data-ttu-id="ed963-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ed963-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ed963-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ed963-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ed963-124">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="ed963-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="ed963-125">字串內插補點</span><span class="sxs-lookup"><span data-stu-id="ed963-125">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="ed963-126">如何：串連多個字串</span><span class="sxs-lookup"><span data-stu-id="ed963-126">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="ed963-127">委派</span><span class="sxs-lookup"><span data-stu-id="ed963-127">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="ed963-128">Checked 與 Unchecked</span><span class="sxs-lookup"><span data-stu-id="ed963-128">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
