---
title: 預設運算子 - C# 參考
description: 使用預設運算子組建類型的預設值
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 0d37fe952e71e74f014872231a2e58663dea9d18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399480"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="110da-103">預設運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="110da-103">default operator (C# reference)</span></span>

<span data-ttu-id="110da-104">`default` 運算子會產生型別的[預設值](../builtin-types/default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="110da-104">The `default` operator produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="110da-105">`default` 運算子的引數必須是型別或或型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="110da-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="110da-106">下列範例會示範 `default` 運算子的使用方式：</span><span class="sxs-lookup"><span data-stu-id="110da-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="110da-107">您還將關鍵字`default`用作[`switch`語句](../keywords/switch.md)中的預設大小寫標籤。</span><span class="sxs-lookup"><span data-stu-id="110da-107">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="110da-108">預設常值</span><span class="sxs-lookup"><span data-stu-id="110da-108">default literal</span></span>

<span data-ttu-id="110da-109">從 C# 7.1 開始，當編譯器可以推斷運算式型別時，您可以使用 `default` 常值來產生型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="110da-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="110da-110">`default` 常值運算式會產生與對`default(T)` 運算式相同的值，其中 `T` 是推斷出來的型別。</span><span class="sxs-lookup"><span data-stu-id="110da-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="110da-111">在下列任一情況中，您都可以使用 `default` 常值：</span><span class="sxs-lookup"><span data-stu-id="110da-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="110da-112">在指派或初始化變數時。</span><span class="sxs-lookup"><span data-stu-id="110da-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="110da-113">在[可選方法參數](../../methods.md#optional-parameters-and-arguments)的預設值的聲明中。</span><span class="sxs-lookup"><span data-stu-id="110da-113">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="110da-114">在提供引數值的方法呼叫中。</span><span class="sxs-lookup"><span data-stu-id="110da-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="110da-115">在[`return`語句](../keywords/return.md)中或作為[運算式體成員中的](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)運算式。</span><span class="sxs-lookup"><span data-stu-id="110da-115">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="110da-116">下列範例會示範 `default` 常值的使用方式：</span><span class="sxs-lookup"><span data-stu-id="110da-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="110da-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="110da-117">C# language specification</span></span>

<span data-ttu-id="110da-118">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[預設值運算式](~/_csharplang/spec/expressions.md#default-value-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="110da-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="110da-119">如需有關 `default` 常值的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.1/target-typed-default.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="110da-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="110da-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="110da-120">See also</span></span>

- [<span data-ttu-id="110da-121">C# 參考</span><span class="sxs-lookup"><span data-stu-id="110da-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="110da-122">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="110da-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="110da-123">C# 類型的預設值</span><span class="sxs-lookup"><span data-stu-id="110da-123">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="110da-124">.NET 的泛型</span><span class="sxs-lookup"><span data-stu-id="110da-124">Generics in .NET</span></span>](../../../standard/generics/index.md)
