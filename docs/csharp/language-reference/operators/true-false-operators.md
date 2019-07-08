---
title: true 和 false 運算子 - C# 參考
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 7cbfca932b5f9f8a6f658e84204da5005da5ffb8
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609831"
---
# <a name="true-and-false-operators-c-reference"></a><span data-ttu-id="2c291-102">true 和 false 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2c291-102">true and false operators (C# reference)</span></span>

<span data-ttu-id="2c291-103">`true` 運算子傳回 [bool](../keywords/bool.md) 值 `true` 以指出運算元必然為 true。</span><span class="sxs-lookup"><span data-stu-id="2c291-103">The `true` operator returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span> <span data-ttu-id="2c291-104">`false` 運算子傳回 `bool` 值 `true` 以指出運算元必然為 false。</span><span class="sxs-lookup"><span data-stu-id="2c291-104">The `false` operator returns the `bool` value `true` to indicate that an operand is definitely false.</span></span> <span data-ttu-id="2c291-105">`true` 和 `false` 運算子並不保證會彼此互補。</span><span class="sxs-lookup"><span data-stu-id="2c291-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span> <span data-ttu-id="2c291-106">也就是說，`true` 和 `false` 運算子可能會針對相同的運算元傳回 `bool` 值 `false`。</span><span class="sxs-lookup"><span data-stu-id="2c291-106">That is, both the `true` and `false` operator might return the `bool` value `false` for the same operand.</span></span> <span data-ttu-id="2c291-107">如果某個型別會定義這兩個運算子之一，它也必須定義另一個運算子。</span><span class="sxs-lookup"><span data-stu-id="2c291-107">If a type defines one of the two operators, it must also define another operator.</span></span>

> [!TIP]
> <span data-ttu-id="2c291-108">當您處理支援三值布林值類型的資料庫時，如果您需要支援三值邏輯，請使用 `bool?` 類型。</span><span class="sxs-lookup"><span data-stu-id="2c291-108">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="2c291-109">C# 能提供搭配 `bool?` 運算元來支援三值邏輯的 `&` 和 `|` 運算子。</span><span class="sxs-lookup"><span data-stu-id="2c291-109">C# provides the `&` and `|` operators that support the three-valued logic with the `bool?` operands.</span></span> <span data-ttu-id="2c291-110">如需詳細資訊，請參閱[布林值邏輯運算子](boolean-logical-operators.md)一文的[可為 Null 的布林值邏輯運算子](boolean-logical-operators.md#nullable-boolean-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="2c291-110">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="boolean-expressions"></a><span data-ttu-id="2c291-111">布林運算式</span><span class="sxs-lookup"><span data-stu-id="2c291-111">Boolean expressions</span></span>

<span data-ttu-id="2c291-112">具有已定義 `true` 運算子的型別可以是 [if](../keywords/if-else.md)、[do](../keywords/do.md)、[while](../keywords/while.md) 及 [for](../keywords/for.md) 陳述式，以及[條件運算子 `?:`](conditional-operator.md)中之控制條件運算式的結果型別。</span><span class="sxs-lookup"><span data-stu-id="2c291-112">A type with the defined `true` operator can be the type of a result of a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](conditional-operator.md).</span></span> <span data-ttu-id="2c291-113">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[布林運算式](~/_csharplang/spec/expressions.md#boolean-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="2c291-113">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="user-defined-conditional-logical-operators"></a><span data-ttu-id="2c291-114">使用者定義條件式邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="2c291-114">User-defined conditional logical operators</span></span>

<span data-ttu-id="2c291-115">如果具有已定義 `true` 和 `false` 運算子的型別會以某種方式[多載](operator-overloading.md)[邏輯 OR 運算子](boolean-logical-operators.md#logical-or-operator-) `|` 或 [邏輯 AND 運算子](boolean-logical-operators.md#logical-and-operator-) `&`，系統便可針對該型別的運算元評估[條件邏輯 OR 運算子](boolean-logical-operators.md#conditional-logical-or-operator-) `||` 或 [條件邏輯 AND 運算子](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`。</span><span class="sxs-lookup"><span data-stu-id="2c291-115">If a type with the defined `true` and `false` operators [overloads](operator-overloading.md) the [logical OR operator](boolean-logical-operators.md#logical-or-operator-) `|` or the [logical AND operator](boolean-logical-operators.md#logical-and-operator-) `&` in a certain way, the [conditional logical OR operator](boolean-logical-operators.md#conditional-logical-or-operator-) `||` or [conditional logical AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="2c291-116">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="2c291-116">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="example"></a><span data-ttu-id="2c291-117">範例</span><span class="sxs-lookup"><span data-stu-id="2c291-117">Example</span></span>

<span data-ttu-id="2c291-118">下列範例顯示同時定義了 `true` 和 `false` 運算子的型別。</span><span class="sxs-lookup"><span data-stu-id="2c291-118">The following example presents the type that defines both `true` and `false` operators.</span></span> <span data-ttu-id="2c291-119">該型別也多載邏輯 AND 運算子 `&`，使得系統也能針對該型別的運算元評估 `&&` 運算子。</span><span class="sxs-lookup"><span data-stu-id="2c291-119">The type also overloads the logical AND operator `&` in such a way that the operator `&&` also can be evaluated for the operands of that type.</span></span>

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

<span data-ttu-id="2c291-120">請注意 `&&` 運算子的最少運算行為。</span><span class="sxs-lookup"><span data-stu-id="2c291-120">Notice the short-circuiting behavior of the `&&` operator.</span></span> <span data-ttu-id="2c291-121">當 `GetFuelLaunchStatus` 方法傳回 `LaunchStatus.Red` 時，系統並不會評估 `&&` 運算子的右邊運算元。</span><span class="sxs-lookup"><span data-stu-id="2c291-121">When the `GetFuelLaunchStatus` method returns `LaunchStatus.Red`, the right-hand operand of the `&&` operator is not evaluated.</span></span> <span data-ttu-id="2c291-122">這是因為 `LaunchStatus.Red` 必然為 false。</span><span class="sxs-lookup"><span data-stu-id="2c291-122">That is because `LaunchStatus.Red` is definitely false.</span></span> <span data-ttu-id="2c291-123">然後邏輯 AND 的結果並不取決於右邊運算元的值。</span><span class="sxs-lookup"><span data-stu-id="2c291-123">Then the result of the logical AND doesn't depend on the value of the right-hand operand.</span></span> <span data-ttu-id="2c291-124">此範例的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="2c291-124">The output of the example is as follows:</span></span>

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a><span data-ttu-id="2c291-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c291-125">See also</span></span>

- [<span data-ttu-id="2c291-126">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2c291-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2c291-127">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="2c291-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="2c291-128">true 常值</span><span class="sxs-lookup"><span data-stu-id="2c291-128">true literal</span></span>](../keywords/true-literal.md)
- [<span data-ttu-id="2c291-129">false 常值</span><span class="sxs-lookup"><span data-stu-id="2c291-129">false literal</span></span>](../keywords/false-literal.md)
