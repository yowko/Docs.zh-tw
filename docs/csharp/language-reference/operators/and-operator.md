---
title: '&amp; 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 67d60709e1c6c76071ecfb7aac74c83dec6f372a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310040"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="97417-102">&amp; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="97417-102">&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="97417-103">`&` 運算子支援兩種形式：一元傳址運算子或二元邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="97417-103">The `&` operator is supported in two forms: a unary address-of operator or a binary logical operator.</span></span>

## <a name="unary-address-of-operator"></a><span data-ttu-id="97417-104">一元傳址運算子</span><span class="sxs-lookup"><span data-stu-id="97417-104">Unary address-of operator</span></span>

<span data-ttu-id="97417-105">一元 `&` 運算子會傳回其運算元的位址。</span><span class="sxs-lookup"><span data-stu-id="97417-105">The unary `&` operator returns the address of its operand.</span></span> <span data-ttu-id="97417-106">如需詳細資訊，請參閱[如何：取得變數位址](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="97417-106">For more information, see [How to: obtain the address of a variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span></span>

<span data-ttu-id="97417-107">傳址運算子 `&` 需要 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="97417-107">The address-of operator `&` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="integer-logical-bitwise-and-operator"></a><span data-ttu-id="97417-108">整數邏輯位元 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="97417-108">Integer logical bitwise AND operator</span></span>

<span data-ttu-id="97417-109">若為整數型別，`&` 運算子會計算其運算元的邏輯位元 AND：</span><span class="sxs-lookup"><span data-stu-id="97417-109">For integer types, the `&` operator computes the logical bitwise AND of its operands:</span></span>

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> <span data-ttu-id="97417-110">上述範例會使用在 [C# 7.0 中推出](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements)並[在 C# 7.2 增強的](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals)二進位常值。</span><span class="sxs-lookup"><span data-stu-id="97417-110">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

<span data-ttu-id="97417-111">因為對整數型別進行的運算通常也可對列舉行別進行，所以 `&` 運算子也支援 [enum](../keywords/enum.md) 運算元。</span><span class="sxs-lookup"><span data-stu-id="97417-111">Because operations on integer types are generally allowed on enumeration types, the `&` operator also supports [enum](../keywords/enum.md) operands.</span></span>

## <a name="boolean-logical-and-operator"></a><span data-ttu-id="97417-112">布林值邏輯 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="97417-112">Boolean logical AND operator</span></span>

<span data-ttu-id="97417-113">若為 [bool](../keywords/bool.md) 運算元，`&` 運算子會計算其運算元的邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="97417-113">For [bool](../keywords/bool.md) operands, the `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="97417-114">若 `x` 及 `y` 皆為 `true`，那麼 `x & y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="97417-114">The result of `x & y` is `true` if both `x` and `y` are `true`.</span></span> <span data-ttu-id="97417-115">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="97417-115">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="97417-116">即使第一個運算元的值為 `false`，`&` 運算子仍會求這兩個運算元的值，所以不論第二個運算元的值為何，其結果必定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="97417-116">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span> <span data-ttu-id="97417-117">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="97417-117">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

<span data-ttu-id="97417-118">[條件式 AND 運算子](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` 也會計算其運算元的邏輯 AND，但在第一個運算元的值評估為 `false` 時，則不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="97417-118">The [conditional AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="97417-119">若是可為 Null 的 bool 運算元，`&` 運算子的行為與 SQL 的三值邏輯一致。</span><span class="sxs-lookup"><span data-stu-id="97417-119">For nullable bool operands, the behavior of the `&` operator is consistent with SQL's three-valued logic.</span></span> <span data-ttu-id="97417-120">如需詳細資訊，請參閱[布林值邏輯運算子](boolean-logical-operators.md)一文的[可為 Null 的布林值邏輯運算子](boolean-logical-operators.md#nullable-boolean-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="97417-120">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="97417-121">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="97417-121">Operator overloadability</span></span>

<span data-ttu-id="97417-122">使用者定義型別可以[多載](../keywords/operator.md)二元 `&` 運算子。</span><span class="sxs-lookup"><span data-stu-id="97417-122">User-defined types can [overload](../keywords/operator.md) the binary `&` operator.</span></span> <span data-ttu-id="97417-123">多載二元 `&` 運算子時，[AND 指派運算子](and-assignment-operator.md) `&=` 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="97417-123">When a binary `&` operator is overloaded, the [AND assignment operator](and-assignment-operator.md) `&=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="97417-124">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="97417-124">C# language specification</span></span>

<span data-ttu-id="97417-125">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[傳址運算子](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)及[邏輯運算子](~/_csharplang/spec/expressions.md#logical-operators)章節。</span><span class="sxs-lookup"><span data-stu-id="97417-125">For more information, see [The address-of operator](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) and [Logical operators](~/_csharplang/spec/expressions.md#logical-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="97417-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97417-126">See also</span></span>

- [<span data-ttu-id="97417-127">C# 參考</span><span class="sxs-lookup"><span data-stu-id="97417-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="97417-128">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="97417-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="97417-129">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="97417-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="97417-130">布林值邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="97417-130">Boolean logical operators</span></span>](boolean-logical-operators.md)
- [<span data-ttu-id="97417-131">指標類型</span><span class="sxs-lookup"><span data-stu-id="97417-131">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="97417-132">| 運算子</span><span class="sxs-lookup"><span data-stu-id="97417-132">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="97417-133">^ 運算子</span><span class="sxs-lookup"><span data-stu-id="97417-133">^ operator</span></span>](xor-operator.md)
- [<span data-ttu-id="97417-134">~ 運算子</span><span class="sxs-lookup"><span data-stu-id="97417-134">~ operator</span></span>](bitwise-complement-operator.md)
