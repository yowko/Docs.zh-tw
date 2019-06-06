---
title: '- 及 -= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 9f43a863de69122e251204668af2ea989fcc993c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300082"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="70535-102">- 及 -= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="70535-102">- and -= operators (C# Reference)</span></span>

<span data-ttu-id="70535-103">`-` 運算子受到內建數值型別和 [delegate](../keywords/delegate.md) 型別所支援。</span><span class="sxs-lookup"><span data-stu-id="70535-103">The `-` operator is supported by the built-in numeric types and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="70535-104">如需算術 `-` 運算子的資訊，請參閱[算術運算子](arithmetic-operators.md)一文中的[一元加號和減號運算子](arithmetic-operators.md#unary-plus-and-minus-operators)與[減法運算子 -](arithmetic-operators.md#subtraction-operator--) 章節。</span><span class="sxs-lookup"><span data-stu-id="70535-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="70535-105">委派移除</span><span class="sxs-lookup"><span data-stu-id="70535-105">Delegate removal</span></span>

<span data-ttu-id="70535-106">針對相同 [delegate](../keywords/delegate.md) 型別中的運算元，`-` 運算子會傳回委派執行個體，其計算方式如下：</span><span class="sxs-lookup"><span data-stu-id="70535-106">For operands of the same [delegate](../keywords/delegate.md) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="70535-107">如果兩個運算元都為非 Null，且第二個運算元的引動過程清單是第一個運算元之引動過程清單的適當連續子清單，則作業結果會是新引動過程清單藉由從第一個運算元之引動過程清單來移除第二個運算元的項目所取得。</span><span class="sxs-lookup"><span data-stu-id="70535-107">If both operands are non-null and the invocation list of the second operand is a proper contiguous sublist of the invocation list of the first operand, the result of the operation is a new invocation list that is obtained by removing the second operand's entries from the invocation list of the first operand.</span></span> <span data-ttu-id="70535-108">如果第二個運算元清單與第一個運算元清單中的多個連續子清單相符，則只會移除最右邊的相符子清單。</span><span class="sxs-lookup"><span data-stu-id="70535-108">If the second operand's list matches multiple contiguous sublists in the first operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="70535-109">如果移除導致空白清單，則結果是 `null`。</span><span class="sxs-lookup"><span data-stu-id="70535-109">If removal results in an empty list, the result is `null`.</span></span>
- <span data-ttu-id="70535-110">如果第二個運算元的引動過程清單不是第一個運算元之引動過程清單的適當連續子清單，則作業的結果會是第一個運算元。</span><span class="sxs-lookup"><span data-stu-id="70535-110">If the invocation list of the second operand is not a proper contiguous sublist of the invocation list of the first operand, the result of the operation is the first operand.</span></span>
- <span data-ttu-id="70535-111">如果第一個運算元是 `null`，則作業的結果是 `null`。</span><span class="sxs-lookup"><span data-stu-id="70535-111">If the first operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="70535-112">如果第二個運算元是 `null`，則作業的結果是第一個運算元。</span><span class="sxs-lookup"><span data-stu-id="70535-112">If the second operand is `null`, the result of the operation is the first operand.</span></span>

<span data-ttu-id="70535-113">下列範例顯示 `-` 作業如何執行委派移除：</span><span class="sxs-lookup"><span data-stu-id="70535-113">The following example shows how the `-` operation performs delegate removal:</span></span>

[!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="70535-114">減法指派運算子 -=</span><span class="sxs-lookup"><span data-stu-id="70535-114">Subtraction assignment operator -=</span></span>

<span data-ttu-id="70535-115">使用 `-=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="70535-115">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="70535-116">相當於</span><span class="sxs-lookup"><span data-stu-id="70535-116">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="70535-117">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="70535-117">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="70535-118">下列範例示範 `-=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="70535-118">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="70535-119">當您取消訂閱[事件](../keywords/event.md)時，您也會使用 `-=` 來指定要移除的事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="70535-119">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="70535-120">如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="70535-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="70535-121">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="70535-121">Operator overloadability</span></span>

<span data-ttu-id="70535-122">使用者定義型別可以[多載](../keywords/operator.md) `-` 運算子。</span><span class="sxs-lookup"><span data-stu-id="70535-122">A user-defined type can [overload](../keywords/operator.md) the `-` operator.</span></span> <span data-ttu-id="70535-123">多載二元 `-` 運算子時，`-=` 運算子也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="70535-123">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="70535-124">使用者定義型別無法明確地多載 `-=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="70535-124">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="70535-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="70535-125">C# language specification</span></span>

<span data-ttu-id="70535-126">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[一元減號運算子](~/_csharplang/spec/expressions.md#unary-minus-operator)與[減法運算子](~/_csharplang/spec/expressions.md#subtraction-operator)章節。</span><span class="sxs-lookup"><span data-stu-id="70535-126">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70535-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70535-127">See also</span></span>

- [<span data-ttu-id="70535-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="70535-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="70535-129">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="70535-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="70535-130">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="70535-130">C# Operators</span></span>](index.md)
- [<span data-ttu-id="70535-131">委派</span><span class="sxs-lookup"><span data-stu-id="70535-131">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="70535-132">事件</span><span class="sxs-lookup"><span data-stu-id="70535-132">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="70535-133">Checked 與 Unchecked</span><span class="sxs-lookup"><span data-stu-id="70535-133">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
- [<span data-ttu-id="70535-134">算術運算子</span><span class="sxs-lookup"><span data-stu-id="70535-134">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="70535-135"> + 及 += 運算子</span><span class="sxs-lookup"><span data-stu-id="70535-135">+ and += operators</span></span>](addition-operator.md)
