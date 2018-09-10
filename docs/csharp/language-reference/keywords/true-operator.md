---
title: true 運算子 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 54b8d764dc673598474d6adbbee82e0223a16b93
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197795"
---
# <a name="true-operator-c-reference"></a><span data-ttu-id="2d46a-102">true 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2d46a-102">true Operator (C# Reference)</span></span>
<span data-ttu-id="2d46a-103">若運算元為 true 即傳回 [bool](../../../csharp/language-reference/keywords/bool.md) 值 `true`；否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="2d46a-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is true and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="2d46a-104">在 C# 2.0 之前，`true` 和 `false` 運算子是用來建立使用者定義之可為 Null 的實值型別，該類型與 `SqlBool` 這類類型相容。</span><span class="sxs-lookup"><span data-stu-id="2d46a-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="2d46a-105">不過，該語言現在針對可為 Null 的實值型別提供內建支援，因此您應盡可能使用這些類型，而不是多載 `true` 和 `false` 運算子。</span><span class="sxs-lookup"><span data-stu-id="2d46a-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="2d46a-106">如需詳細資訊，請參閱[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2d46a-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="2d46a-107">使用可為 Null 的布林值時，運算式 `a != b` 不一定等於 `!(a == b)`，因為其中一或兩個值可能為 Null。</span><span class="sxs-lookup"><span data-stu-id="2d46a-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="2d46a-108">您必須分別多載 `true` 和 `false` 運算子，才能正確識別運算式中的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="2d46a-108">You need to overload both the `true` and `false` operators separately to correctly identify the null values in the expression.</span></span> <span data-ttu-id="2d46a-109">下列範例示範如何多載和使用 `true` 和 `false` 運算子。</span><span class="sxs-lookup"><span data-stu-id="2d46a-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 <span data-ttu-id="2d46a-110">多載 `true` 和 `false` 運算子的類型可用於 [if](../../../csharp/language-reference/keywords/if-else.md)、[do](../../../csharp/language-reference/keywords/do.md)、[while](../../../csharp/language-reference/keywords/while.md) 和 [for](../../../csharp/language-reference/keywords/for.md) 陳述式以及[條件運算式](../../../csharp/language-reference/operators/conditional-operator.md)中的控制運算式。</span><span class="sxs-lookup"><span data-stu-id="2d46a-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="2d46a-111">如果類型定義 `true` 運算子，則必須同時定義 [false](../../../csharp/language-reference/keywords/false.md) 運算子。</span><span class="sxs-lookup"><span data-stu-id="2d46a-111">If a type defines operator `true`, it must also define operator [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
 <span data-ttu-id="2d46a-112">類型不能直接多載條件邏輯運算子 ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) 和 [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md))，但藉由多載一般邏輯運算子以及 `true` 和 `false` 運算子，也可達到同樣效果。</span><span class="sxs-lookup"><span data-stu-id="2d46a-112">A type cannot directly overload the conditional logical operators ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2d46a-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2d46a-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d46a-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2d46a-114">See Also</span></span>

- [<span data-ttu-id="2d46a-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2d46a-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2d46a-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2d46a-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2d46a-117">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="2d46a-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="2d46a-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="2d46a-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="2d46a-119">false</span><span class="sxs-lookup"><span data-stu-id="2d46a-119">false</span></span>](../../../csharp/language-reference/keywords/false.md)
