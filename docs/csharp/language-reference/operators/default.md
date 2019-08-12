---
title: 預設運算子 - C# 參考
ms.custom: seodec18
description: 使用預設運算子來產生型別的預設值
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 5623cb9dc3790b5bb99635c41cb3f122f4c71d8e
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796937"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="cb752-103">預設運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cb752-103">default operator (C# reference)</span></span>

<span data-ttu-id="cb752-104">`default` 運算子會產生型別的[預設值](../keywords/default-values-table.md)。</span><span class="sxs-lookup"><span data-stu-id="cb752-104">The `default` operator produces the [default value](../keywords/default-values-table.md) of a type.</span></span> <span data-ttu-id="cb752-105">`default` 運算子的引數必須是型別或或型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="cb752-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="cb752-106">下列範例會示範 `default` 運算子的使用方式：</span><span class="sxs-lookup"><span data-stu-id="cb752-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="cb752-107">您也可以在 [`switch` 陳述式](../keywords/switch.md)使用 `default` 關鍵字作為預設案例標籤。</span><span class="sxs-lookup"><span data-stu-id="cb752-107">You also use the `default` keyword as the default case label within the [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="cb752-108">預設常值</span><span class="sxs-lookup"><span data-stu-id="cb752-108">default literal</span></span>

<span data-ttu-id="cb752-109">從 C# 7.1 開始，當編譯器可以推斷運算式型別時，您可以使用 `default` 常值來產生型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="cb752-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="cb752-110">`default` 常值運算式會產生與對`default(T)` 運算式相同的值，其中 `T` 是推斷出來的型別。</span><span class="sxs-lookup"><span data-stu-id="cb752-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="cb752-111">在下列任一情況中，您都可以使用 `default` 常值：</span><span class="sxs-lookup"><span data-stu-id="cb752-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="cb752-112">在指派或初始化變數時。</span><span class="sxs-lookup"><span data-stu-id="cb752-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="cb752-113">在選擇性方法參數的預設值宣告中。</span><span class="sxs-lookup"><span data-stu-id="cb752-113">In the declaration of the default value for an optional method parameter.</span></span>
- <span data-ttu-id="cb752-114">在提供引數值的方法呼叫中。</span><span class="sxs-lookup"><span data-stu-id="cb752-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="cb752-115">在 `return` 陳述式中，或作為陳述式主體成員中的運算式。</span><span class="sxs-lookup"><span data-stu-id="cb752-115">In a `return` statement or as an expression in an expression-bodied member.</span></span>

<span data-ttu-id="cb752-116">下列範例會示範 `default` 常值的使用方式：</span><span class="sxs-lookup"><span data-stu-id="cb752-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="cb752-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="cb752-117">C# language specification</span></span>

<span data-ttu-id="cb752-118">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[預設值運算式](~/_csharplang/spec/expressions.md#default-value-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="cb752-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="cb752-119">如需有關 `default` 常值的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.1/target-typed-default.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="cb752-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb752-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb752-120">See also</span></span>

- [<span data-ttu-id="cb752-121">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cb752-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cb752-122">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="cb752-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="cb752-123">預設值表</span><span class="sxs-lookup"><span data-stu-id="cb752-123">Default values table</span></span>](../keywords/default-values-table.md)
