---
title: + 及 += 運算子 - C# 參考
ms.custom: seodec18
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
ms.openlocfilehash: 258adc45fc6874cca5829479eef1196ebea1e300
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347981"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="5865f-102">+ 及 += 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5865f-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="5865f-103">`+` 運算子支援內建數值型別、[string](../keywords/string.md) 型別和 [delegate](../keywords/delegate.md) 型別。</span><span class="sxs-lookup"><span data-stu-id="5865f-103">The `+` operator is supported by the built-in numeric types, [string](../keywords/string.md) type, and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="5865f-104">如需算術 `+` 運算子的資訊，請參閱[算術運算子](arithmetic-operators.md)一文中的[一元加號和減號運算子](arithmetic-operators.md#unary-plus-and-minus-operators)與[加法運算子 +](arithmetic-operators.md#addition-operator-) 章節。</span><span class="sxs-lookup"><span data-stu-id="5865f-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="5865f-105">字串串連</span><span class="sxs-lookup"><span data-stu-id="5865f-105">String concatenation</span></span>

<span data-ttu-id="5865f-106">當其中一或兩個運算元的型別為 [string](../keywords/string.md) 時，`+` 運算子會串連其運算元的字串表示：</span><span class="sxs-lookup"><span data-stu-id="5865f-106">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="5865f-107">從 C# 6 開始，[字串插補](../tokens/interpolated.md)提供更便利的方式進行字串格式設定：</span><span class="sxs-lookup"><span data-stu-id="5865f-107">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="5865f-108">委派組合</span><span class="sxs-lookup"><span data-stu-id="5865f-108">Delegate combination</span></span>

<span data-ttu-id="5865f-109">針對相同[委派](../keywords/delegate.md)型別中的運算元，`+` 運算子會傳回新的委派執行個體，並在叫用時叫用左側運算元，然後叫用右側運算元。</span><span class="sxs-lookup"><span data-stu-id="5865f-109">For operands of the same [delegate](../keywords/delegate.md) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="5865f-110">如果其中任一個運算元為 `null`，則 `+` 運算子會傳回另一個運算元的值 (也有可能是 `null`)。</span><span class="sxs-lookup"><span data-stu-id="5865f-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="5865f-111">下列範例顯示委派如何與 `+` 運算子結合：</span><span class="sxs-lookup"><span data-stu-id="5865f-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="5865f-112">若要執行委派移除，請使用 [`-` 運算子](subtraction-operator.md#delegate-removal)。</span><span class="sxs-lookup"><span data-stu-id="5865f-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="5865f-113">如需委派型別的詳細資訊，請參閱[委派](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5865f-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="5865f-114">加法指派運算子 +=</span><span class="sxs-lookup"><span data-stu-id="5865f-114">Addition assignment operator +=</span></span>

<span data-ttu-id="5865f-115">使用 `+=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="5865f-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="5865f-116">相當於</span><span class="sxs-lookup"><span data-stu-id="5865f-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="5865f-117">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="5865f-117">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="5865f-118">下列範例示範 `+=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="5865f-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="5865f-119">當您訂閱[事件](../keywords/event.md)時，您也會使用 `+=` 來指定事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="5865f-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="5865f-120">如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="5865f-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="5865f-121">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="5865f-121">Operator overloadability</span></span>

<span data-ttu-id="5865f-122">使用者定義型別可以[多載](../keywords/operator.md) `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="5865f-122">A user-defined type can [overload](../keywords/operator.md) the `+` operator.</span></span> <span data-ttu-id="5865f-123">多載二元 `+` 運算子時，`+=` 運算子也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="5865f-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="5865f-124">使用者定義型別無法明確地多載 `+=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="5865f-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5865f-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5865f-125">C# language specification</span></span>

<span data-ttu-id="5865f-126">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[一元加號運算子](~/_csharplang/spec/expressions.md#unary-plus-operator)與[加法運算子](~/_csharplang/spec/expressions.md#addition-operator)小節。</span><span class="sxs-lookup"><span data-stu-id="5865f-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5865f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5865f-127">See also</span></span>

- [<span data-ttu-id="5865f-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5865f-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5865f-129">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="5865f-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="5865f-130">字串內插補點</span><span class="sxs-lookup"><span data-stu-id="5865f-130">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="5865f-131">如何：串連多個字串</span><span class="sxs-lookup"><span data-stu-id="5865f-131">How to: concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="5865f-132">委派</span><span class="sxs-lookup"><span data-stu-id="5865f-132">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="5865f-133">事件</span><span class="sxs-lookup"><span data-stu-id="5865f-133">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="5865f-134">算術運算子</span><span class="sxs-lookup"><span data-stu-id="5865f-134">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="5865f-135"> - 及 -= 運算子</span><span class="sxs-lookup"><span data-stu-id="5865f-135">- and -= operators</span></span>](subtraction-operator.md)
