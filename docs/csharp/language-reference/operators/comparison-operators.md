---
title: 比較運算子 - C#參考
description: 深入了解可供您檢查數值順序的 C# 比較運算子。
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: eda039d950e4be13d9c041c8bb95b6ea773b83f6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207219"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="065bd-103">比較運算子 (C#參考)</span><span class="sxs-lookup"><span data-stu-id="065bd-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="065bd-104">[ `<` （小於）](#less-than-operator-)、 [ `>` （大於）](#greater-than-operator-)、 [ `<=` （小於或等於）](#less-than-or-equal-operator-)和[ `>=` （大於或等於）](#greater-than-or-equal-operator-)比較（也稱為關聯式）運算子會比較其運算元。</span><span class="sxs-lookup"><span data-stu-id="065bd-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="065bd-105">所有[整數](../builtin-types/integral-numeric-types.md)和[浮點](../builtin-types/floating-point-numeric-types.md)數數值型別都支援這些運算子。</span><span class="sxs-lookup"><span data-stu-id="065bd-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="065bd-106">針對 `==`、`<`、`>`、`<=` 和 `>=` 運算子，如果任何運算元不是數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>)，則作業的結果是 `false`。</span><span class="sxs-lookup"><span data-stu-id="065bd-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="065bd-107">這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值，包括 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="065bd-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="065bd-108">如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。</span><span class="sxs-lookup"><span data-stu-id="065bd-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="065bd-109">[Char](../builtin-types/char.md)類型也支援比較運算子。</span><span class="sxs-lookup"><span data-stu-id="065bd-109">The [char](../builtin-types/char.md) type also supports comparison operators.</span></span> <span data-ttu-id="065bd-110">在運算元的案例中 `char` ，會比較對應的字元碼。</span><span class="sxs-lookup"><span data-stu-id="065bd-110">In the case of `char` operands, the corresponding character codes are compared.</span></span>

<span data-ttu-id="065bd-111">列舉類型也支援比較運算子。</span><span class="sxs-lookup"><span data-stu-id="065bd-111">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="065bd-112">相同[列舉](../builtin-types/enum.md)類型的運算元會比較基礎整數型別的對應值。</span><span class="sxs-lookup"><span data-stu-id="065bd-112">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="065bd-113">[ `==` 和 `!=` 運算子](equality-operators.md)會檢查其運算元是否相等。</span><span class="sxs-lookup"><span data-stu-id="065bd-113">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="065bd-114">小於運算子 \<</span><span class="sxs-lookup"><span data-stu-id="065bd-114">Less than operator \<</span></span>

<span data-ttu-id="065bd-115">`<` 運算子會傳回 `true` (如果其左邊運算元小於第右邊運算元)，否則會傳回 `false`：</span><span class="sxs-lookup"><span data-stu-id="065bd-115">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="065bd-116">大於運算子 ></span><span class="sxs-lookup"><span data-stu-id="065bd-116">Greater than operator ></span></span>

<span data-ttu-id="065bd-117">`>` 運算子會傳回 `true` (如果其左邊運算元大於第右邊運算元)，否則會傳回 `false`：</span><span class="sxs-lookup"><span data-stu-id="065bd-117">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="065bd-118">小於或等於運算子 \<=</span><span class="sxs-lookup"><span data-stu-id="065bd-118">Less than or equal operator \<=</span></span>

<span data-ttu-id="065bd-119">`<=` 運算子會傳回 `true` (如果其左邊運算元小於或等於右邊運算元)，否則會傳回 `false`：</span><span class="sxs-lookup"><span data-stu-id="065bd-119">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="065bd-120">大於或等於運算子 >=</span><span class="sxs-lookup"><span data-stu-id="065bd-120">Greater than or equal operator >=</span></span>

<span data-ttu-id="065bd-121">`>=` 運算子會傳回 `true` (如果其左邊運算元大於或等於右邊運算元)，否則會傳回 `false`：</span><span class="sxs-lookup"><span data-stu-id="065bd-121">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="065bd-122">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="065bd-122">Operator overloadability</span></span>

<span data-ttu-id="065bd-123">使用者定義型[別可以多](operator-overloading.md)載 `<` 、 `>` 、 `<=` 和 `>=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="065bd-123">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="065bd-124">如果類型多載 `<` 或 `>` 運算子之一，則也必須多載 `<` 和 `>`。</span><span class="sxs-lookup"><span data-stu-id="065bd-124">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="065bd-125">如果類型多載 `<=` 或 `>=` 運算子之一，則也必須多載 `<=` 和 `>=`。</span><span class="sxs-lookup"><span data-stu-id="065bd-125">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="065bd-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="065bd-126">C# language specification</span></span>

<span data-ttu-id="065bd-127">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="065bd-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="065bd-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="065bd-128">See also</span></span>

- [<span data-ttu-id="065bd-129">C# 參考</span><span class="sxs-lookup"><span data-stu-id="065bd-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="065bd-130">C # 運算子</span><span class="sxs-lookup"><span data-stu-id="065bd-130">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="065bd-131">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="065bd-131">Equality operators</span></span>](equality-operators.md)
