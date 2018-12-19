---
title: true 和 false 運算子 - C# 參考
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 0a75566fdb6222157ecda12a50fd78e22f92fcb4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245729"
---
# <a name="true-and-false-operators-c-reference"></a><span data-ttu-id="fa6d3-102">true 和 false 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="fa6d3-102">true and false operators (C# Reference)</span></span>

<span data-ttu-id="fa6d3-103">`true` 運算子傳回 [bool](bool.md) 值 `true` 以指出運算元必然為 true。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-103">The `true` operator returns the [bool](bool.md) value `true` to indicate that an operand is definitely true.</span></span> <span data-ttu-id="fa6d3-104">`false` 運算子傳回 `bool` 值 `true` 以指出運算元必然為 false。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-104">The `false` operator returns the `bool` value `true` to indicate that an operand is definitely false.</span></span> <span data-ttu-id="fa6d3-105">`true` 和 `false` 運算子並不保證會彼此互補。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span> <span data-ttu-id="fa6d3-106">也就是說，`true` 和 `false` 運算子可能會針對相同的運算元傳回 `bool` 值 `false`。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-106">That is, both the `true` and `false` operator might return the `bool` value `false` for the same operand.</span></span> <span data-ttu-id="fa6d3-107">如果某個型別會定義這兩個運算子之一，它也必須定義另一個運算子。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-107">If a type defines one of the two operators, it must also define another operator.</span></span>

<span data-ttu-id="fa6d3-108">如果具有已定義 `true` 和 `false` 運算子的型別會以某種方式[多載](operator.md)[邏輯 OR 運算子](../operators/or-operator.md) `|` 或 [邏輯 AND 運算子](../operators/and-operator.md) `&`，系統便可針對該型別的運算元評估[條件邏輯 OR 運算子](../operators/conditional-or-operator.md) `||` 或 [條件邏輯 AND 運算子](../operators/conditional-and-operator.md) `&&`。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-108">If a type with the defined `true` and `false` operators [overloads](operator.md) the [logical OR operator](../operators/or-operator.md) `|` or the [logical AND operator](../operators/and-operator.md) `&` in a certain way, the [conditional logical OR operator](../operators/conditional-or-operator.md) `||` or [conditional logical AND operator](../operators/conditional-and-operator.md) `&&`, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="fa6d3-109">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-109">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

<span data-ttu-id="fa6d3-110">具有已定義 `true` 運算子的型別可以是 [if](if-else.md)、[do](do.md)、[while](while.md) 及 [for](for.md) 陳述式，以及[條件運算子 `?:`](../operators/conditional-operator.md)中之控制條件運算式的結果型別。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-110">A type with the defined `true` operator can be the type of a result of a controlling conditional expression in the [if](if-else.md), [do](do.md), [while](while.md), and [for](for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span> <span data-ttu-id="fa6d3-111">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[布林運算式](~/_csharplang/spec/expressions.md#boolean-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-111">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

> [!TIP]
> <span data-ttu-id="fa6d3-112">如果您需要支援三值邏輯 (例如使用支援三值邏輯型別的資料庫時)，請使用 `bool?` 型別。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-112">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued logical type.</span></span> <span data-ttu-id="fa6d3-113">如需詳細資訊，請參閱[使用可為 Null 的型別](../../programming-guide/nullable-types/using-nullable-types.md)一文的 [bool? 型別](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type)一節。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-113">For more information, see [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="fa6d3-114">下列範例顯示同時定義了 `true` 和 `false` 運算子的型別。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-114">The following example presents the type that defines both `true` and `false` operators.</span></span> <span data-ttu-id="fa6d3-115">此外，它還多載邏輯 AND 運算子 `&`，使得系統也能針對該型別的運算元評估 `&&` 運算子。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-115">Moreover, it overloads the logical AND operator `&` in such a way that the operator `&&` also can be evaluated for the operands of that type.</span></span>

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

<span data-ttu-id="fa6d3-116">請注意 `&&` 運算子的最少運算行為。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-116">Notice the short-circuiting behavior of the `&&` operator.</span></span> <span data-ttu-id="fa6d3-117">當 `GetFuelLaunchStatus` 方法傳回 `LaunchStatus.Red` 時，系統並不會評估 `&&` 運算子的第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-117">When the `GetFuelLaunchStatus` method returns `LaunchStatus.Red`, the second operand of the `&&` operator is not evaluated.</span></span> <span data-ttu-id="fa6d3-118">這是因為 `LaunchStatus.Red` 必然為 false。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-118">That is because `LaunchStatus.Red` is definitely false.</span></span> <span data-ttu-id="fa6d3-119">然後邏輯 AND 的結果並不取決於第二個運算元的值。</span><span class="sxs-lookup"><span data-stu-id="fa6d3-119">Then the result of the logical AND doesn't depend on the value of the second operand.</span></span> <span data-ttu-id="fa6d3-120">此範例的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="fa6d3-120">The output of the example is as follows:</span></span>

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a><span data-ttu-id="fa6d3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa6d3-121">See also</span></span>

- [<span data-ttu-id="fa6d3-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="fa6d3-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fa6d3-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="fa6d3-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fa6d3-124">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="fa6d3-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fa6d3-125">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="fa6d3-125">C# Operators</span></span>](../operators/index.md)
- [<span data-ttu-id="fa6d3-126">`true` 常值</span><span class="sxs-lookup"><span data-stu-id="fa6d3-126">`true` literal</span></span>](true-literal.md)
- [<span data-ttu-id="fa6d3-127">`false` 常值</span><span class="sxs-lookup"><span data-stu-id="fa6d3-127">`false` literal</span></span>](false-literal.md)