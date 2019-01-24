---
title: -= 運算子 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 3b6890be4460a599a5d2f5f5f6ee1627be933f0b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333326"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="1fef0-102">-= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1fef0-102">-= operator (C# Reference)</span></span>

<span data-ttu-id="1fef0-103">減法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="1fef0-103">The subtraction assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fef0-104">備註</span><span class="sxs-lookup"><span data-stu-id="1fef0-104">Remarks</span></span>

<span data-ttu-id="1fef0-105">使用 `-=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="1fef0-105">An expression using the `-=` assignment operator, such as</span></span>

```csharp
x -= y
```

 <span data-ttu-id="1fef0-106">相當於</span><span class="sxs-lookup"><span data-stu-id="1fef0-106">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="1fef0-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="1fef0-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="1fef0-108">[- 運算子](subtraction-operator.md) 的意義取決於 `x` 和 `y` 的類型 (數字運算元表示減法、委派運算元表示委派移除等等)。</span><span class="sxs-lookup"><span data-stu-id="1fef0-108">The meaning of the [- operator](subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>

<span data-ttu-id="1fef0-109">無法直接多載 `-=` 運算子，但使用者定義型別可以多載 [- 運算子](subtraction-operator.md) (請參閱 [operator](../keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="1fef0-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](subtraction-operator.md) (see [operator](../keywords/operator.md)).</span></span>

<span data-ttu-id="1fef0-110">-= 運算子也會用於 C# 中，以取消事件的訂閱。</span><span class="sxs-lookup"><span data-stu-id="1fef0-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="1fef0-111">如需詳細資訊，請參閱[＜How to：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="1fef0-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="1fef0-112">範例</span><span class="sxs-lookup"><span data-stu-id="1fef0-112">Example</span></span>

[!code-csharp[csRefOperators#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#6)]

## <a name="see-also"></a><span data-ttu-id="1fef0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fef0-113">See also</span></span>

- [<span data-ttu-id="1fef0-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1fef0-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1fef0-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1fef0-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1fef0-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="1fef0-116">C# operators</span></span>](index.md)
