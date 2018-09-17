---
title: false 運算子 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e73113bd37dbb68590267141ad037f78919520bc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45648921"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="5d17b-102">false 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5d17b-102">false operator (C# Reference)</span></span>

<span data-ttu-id="5d17b-103">若運算元為 `false` 即傳回 [bool](bool.md) 值 `true`；否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="5d17b-103">Returns the [bool](bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>

<span data-ttu-id="5d17b-104">在 C# 2.0 之前，`true` 和 `false` 運算子是用來建立使用者定義之可為 Null 的實值型別，該類型與 `SqlBool` 等類型相容。</span><span class="sxs-lookup"><span data-stu-id="5d17b-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="5d17b-105">不過，該語言現在針對可為 Null 的實值型別提供內建支援，因此您應盡可能使用這些類型，而不是多載 `true` 和 `false` 運算子。</span><span class="sxs-lookup"><span data-stu-id="5d17b-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="5d17b-106">如需詳細資訊，請參閱[可為 Null 的型別](../../programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5d17b-106">For more information, see [Nullable Types](../../programming-guide/nullable-types/index.md).</span></span>

<span data-ttu-id="5d17b-107">使用可為 Null 的布林值時，運算式 `a != b` 不一定等於 `!(a == b)`，因為其中一個或兩個值可能為 Null。</span><span class="sxs-lookup"><span data-stu-id="5d17b-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="5d17b-108">您必須分別多載 `true` 和 `false` 運算子，以正確處理運算式中的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="5d17b-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="5d17b-109">下列範例示範如何多載和使用 `true` 和 `false` 運算子。</span><span class="sxs-lookup"><span data-stu-id="5d17b-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

<span data-ttu-id="5d17b-110">多載 `true` 和 `false` 運算子的類型可用於 [if](if-else.md)、[do](do.md)、[while](while.md) 和 [for](for.md) 陳述式以及[條件運算式](../operators/conditional-operator.md)中的控制運算式。</span><span class="sxs-lookup"><span data-stu-id="5d17b-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](if-else.md), [do](do.md), [while](while.md), and [for](for.md) statements and in [conditional expressions](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="5d17b-111">如果類型定義了運算子 `false`，則必須同時定義運算子 [true](true.md)。</span><span class="sxs-lookup"><span data-stu-id="5d17b-111">If a type defines operator `false`, it must also define operator [true](true.md).</span></span>

<span data-ttu-id="5d17b-112">類型不能直接多載條件邏輯運算子 [&&](../operators/conditional-and-operator.md) 和 [&#124;&#124;](../operators/conditional-or-operator.md)，但藉由多載一般邏輯運算子以及 `true` 和 `false` 運算子，也可達到同樣效果。</span><span class="sxs-lookup"><span data-stu-id="5d17b-112">A type cannot directly overload the conditional logical operators [&&](../operators/conditional-and-operator.md) and [&#124;&#124;](../operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5d17b-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5d17b-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5d17b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d17b-114">See also</span></span>

- [<span data-ttu-id="5d17b-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5d17b-115">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="5d17b-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5d17b-116">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="5d17b-117">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="5d17b-117">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="5d17b-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="5d17b-118">C# Operators</span></span>](../operators/index.md)  
- [<span data-ttu-id="5d17b-119">true</span><span class="sxs-lookup"><span data-stu-id="5d17b-119">true</span></span>](true.md)  