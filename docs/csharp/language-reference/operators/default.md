---
title: 預設運算子 - C# 參考
description: 使用 default 運算子產生類型的預設值
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: ba4c02caa53a9d532be4012a4543a25cd41b6023
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239309"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="f8464-103">預設運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f8464-103">default operator (C# reference)</span></span>

<span data-ttu-id="f8464-104">`default` 運算子會產生型別的[預設值](../builtin-types/default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="f8464-104">The `default` operator produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="f8464-105">`default` 運算子的引數必須是型別或或型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8464-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="f8464-106">下列範例會示範 `default` 運算子的使用方式：</span><span class="sxs-lookup"><span data-stu-id="f8464-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/snippets/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="f8464-107">您也可以使用 `default` 關鍵字做為[`switch` 語句](../keywords/switch.md)內的預設 case 標籤。</span><span class="sxs-lookup"><span data-stu-id="f8464-107">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="f8464-108">預設常值</span><span class="sxs-lookup"><span data-stu-id="f8464-108">default literal</span></span>

<span data-ttu-id="f8464-109">從 C# 7.1 開始，當編譯器可以推斷運算式型別時，您可以使用 `default` 常值來產生型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="f8464-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="f8464-110">`default` 常值運算式會產生與對`default(T)` 運算式相同的值，其中 `T` 是推斷出來的型別。</span><span class="sxs-lookup"><span data-stu-id="f8464-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="f8464-111">在下列任一情況中，您都可以使用 `default` 常值：</span><span class="sxs-lookup"><span data-stu-id="f8464-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="f8464-112">在指派或初始化變數時。</span><span class="sxs-lookup"><span data-stu-id="f8464-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="f8464-113">在[選擇性方法參數](../../methods.md#optional-parameters-and-arguments)的預設值宣告中。</span><span class="sxs-lookup"><span data-stu-id="f8464-113">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="f8464-114">在提供引數值的方法呼叫中。</span><span class="sxs-lookup"><span data-stu-id="f8464-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="f8464-115">在[`return` 語句](../keywords/return.md)或[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)中的運算式。</span><span class="sxs-lookup"><span data-stu-id="f8464-115">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="f8464-116">下列範例會示範 `default` 常值的使用方式：</span><span class="sxs-lookup"><span data-stu-id="f8464-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/snippets/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="f8464-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f8464-117">C# language specification</span></span>

<span data-ttu-id="f8464-118">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/expressions.md#default-value-expressions)的[預設值運算式](~/_csharplang/spec/introduction.md)一節。</span><span class="sxs-lookup"><span data-stu-id="f8464-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="f8464-119">如需有關 `default` 常值的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.1/target-typed-default.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f8464-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8464-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8464-120">See also</span></span>

- [<span data-ttu-id="f8464-121">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f8464-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f8464-122">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="f8464-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="f8464-123">類型的C#預設值</span><span class="sxs-lookup"><span data-stu-id="f8464-123">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="f8464-124">.NET 的泛型</span><span class="sxs-lookup"><span data-stu-id="f8464-124">Generics in .NET</span></span>](../../../standard/generics/index.md)
