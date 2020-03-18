---
title: + 及 += 運算子 - C# 參考
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: cafd07f4b4aefdcc4b43750d61c155fe3d65aa46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399298"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="62176-102">+ 及 += 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="62176-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="62176-103">和`+``+=`運算子由內置[積分](../builtin-types/integral-numeric-types.md)和[浮點](../builtin-types/floating-point-numeric-types.md)數數值型別、[字串](../builtin-types/reference-types.md#the-string-type)類型和[委託](../builtin-types/reference-types.md#the-delegate-type)類型支援。</span><span class="sxs-lookup"><span data-stu-id="62176-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="62176-104">如需算術 `+` 運算子的資訊，請參閱[算術運算子](arithmetic-operators.md)一文中的[一元加號和減號運算子](arithmetic-operators.md#unary-plus-and-minus-operators)與[加法運算子 +](arithmetic-operators.md#addition-operator-) 章節。</span><span class="sxs-lookup"><span data-stu-id="62176-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="62176-105">字串串連</span><span class="sxs-lookup"><span data-stu-id="62176-105">String concatenation</span></span>

<span data-ttu-id="62176-106">當其中一或兩個運算元的型別為 [string](../builtin-types/reference-types.md#the-string-type) 時，`+` 運算子會串連其運算元的字串表示：</span><span class="sxs-lookup"><span data-stu-id="62176-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="62176-107">從 C# 6 開始，[字串插值](../tokens/interpolated.md)提供了一種更方便的字串格式方法：</span><span class="sxs-lookup"><span data-stu-id="62176-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="62176-108">委派組合</span><span class="sxs-lookup"><span data-stu-id="62176-108">Delegate combination</span></span>

<span data-ttu-id="62176-109">針對相同[委派](../builtin-types/reference-types.md#the-delegate-type)型別中的運算元，`+` 運算子會傳回新的委派執行個體，並在叫用時叫用左側運算元，然後叫用右側運算元。</span><span class="sxs-lookup"><span data-stu-id="62176-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="62176-110">如果其中任一個運算元為 `null`，則 `+` 運算子會傳回另一個運算元的值 (也有可能是 `null`)。</span><span class="sxs-lookup"><span data-stu-id="62176-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="62176-111">下列範例顯示委派如何與 `+` 運算子結合：</span><span class="sxs-lookup"><span data-stu-id="62176-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="62176-112">要執行委託刪除，[`-`](subtraction-operator.md#delegate-removal)請使用 運算子 。</span><span class="sxs-lookup"><span data-stu-id="62176-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="62176-113">如需委派型別的詳細資訊，請參閱[委派](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="62176-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="62176-114">加法指派運算子 +=</span><span class="sxs-lookup"><span data-stu-id="62176-114">Addition assignment operator +=</span></span>

<span data-ttu-id="62176-115">使用 `+=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="62176-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="62176-116">相當於</span><span class="sxs-lookup"><span data-stu-id="62176-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="62176-117">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="62176-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="62176-118">下列範例示範 `+=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="62176-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="62176-119">當您訂閱[事件](../keywords/event.md)時，您也會使用 `+=` 來指定事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="62176-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="62176-120">有關詳細資訊，請參閱[如何：訂閱和取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="62176-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="62176-121">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="62176-121">Operator overloadability</span></span>

<span data-ttu-id="62176-122">使用者定義型別可以[多載](operator-overloading.md)`+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="62176-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="62176-123">多載二元 `+` 運算子時，`+=` 運算子也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="62176-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="62176-124">使用者定義型別無法明確地多載 `+=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="62176-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="62176-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="62176-125">C# language specification</span></span>

<span data-ttu-id="62176-126">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[一元加號運算子](~/_csharplang/spec/expressions.md#unary-plus-operator)與[加法運算子](~/_csharplang/spec/expressions.md#addition-operator)小節。</span><span class="sxs-lookup"><span data-stu-id="62176-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62176-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62176-127">See also</span></span>

- [<span data-ttu-id="62176-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="62176-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="62176-129">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="62176-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="62176-130">如何串聯多個字串</span><span class="sxs-lookup"><span data-stu-id="62176-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="62176-131">事件</span><span class="sxs-lookup"><span data-stu-id="62176-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="62176-132">算術運算子</span><span class="sxs-lookup"><span data-stu-id="62176-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="62176-133">- 及 = 運算子</span><span class="sxs-lookup"><span data-stu-id="62176-133">- and -= operators</span></span>](subtraction-operator.md)
