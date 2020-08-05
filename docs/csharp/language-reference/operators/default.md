---
title: '預設值運算式-c # 參考'
description: 使用預設值運算式來取得類型的預設值
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: c07eb8e50dc2ec3413882fa841d2f896b28d2e8d
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556705"
---
# <a name="default-value-expressions-c-reference"></a><span data-ttu-id="9227e-103">預設值運算式 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="9227e-103">default value expressions (C# reference)</span></span>

<span data-ttu-id="9227e-104">預設值運算式會產生類型的[預設值](../builtin-types/default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="9227e-104">A default value expression produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="9227e-105">預設值運算式有兩種類型：[預設運算子](#default-operator)呼叫和[預設常](#default-literal)值。</span><span class="sxs-lookup"><span data-stu-id="9227e-105">There are two kinds of default value expressions: the [default operator](#default-operator) call and a [default literal](#default-literal).</span></span>

<span data-ttu-id="9227e-106">您也可以在 `default` [ `switch` 語句](../keywords/switch.md)中使用關鍵字做為預設的 case 標籤。</span><span class="sxs-lookup"><span data-stu-id="9227e-106">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-operator"></a><span data-ttu-id="9227e-107">default 運算子</span><span class="sxs-lookup"><span data-stu-id="9227e-107">default operator</span></span>

<span data-ttu-id="9227e-108">`default` 運算子的引數必須是型別名稱或型別參數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9227e-108">The argument to the `default` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a><span data-ttu-id="9227e-109">預設常值</span><span class="sxs-lookup"><span data-stu-id="9227e-109">default literal</span></span>

<span data-ttu-id="9227e-110">從 C# 7.1 開始，當編譯器可以推斷運算式型別時，您可以使用 `default` 常值來產生型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="9227e-110">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="9227e-111">`default` 常值運算式會產生與對`default(T)` 運算式相同的值，其中 `T` 是推斷出來的型別。</span><span class="sxs-lookup"><span data-stu-id="9227e-111">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="9227e-112">在下列任一情況中，您都可以使用 `default` 常值：</span><span class="sxs-lookup"><span data-stu-id="9227e-112">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="9227e-113">在指派或初始化變數時。</span><span class="sxs-lookup"><span data-stu-id="9227e-113">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="9227e-114">在[選擇性方法參數](../../methods.md#optional-parameters-and-arguments)的預設值宣告中。</span><span class="sxs-lookup"><span data-stu-id="9227e-114">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="9227e-115">在提供引數值的方法呼叫中。</span><span class="sxs-lookup"><span data-stu-id="9227e-115">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="9227e-116">在[ `return` 語句](../keywords/return.md)或[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)中的運算式。</span><span class="sxs-lookup"><span data-stu-id="9227e-116">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="9227e-117">下列範例會示範 `default` 常值的使用方式：</span><span class="sxs-lookup"><span data-stu-id="9227e-117">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="9227e-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9227e-118">C# language specification</span></span>

<span data-ttu-id="9227e-119">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[預設值運算式](~/_csharplang/spec/expressions.md#default-value-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="9227e-119">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="9227e-120">如需有關 `default` 常值的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.1/target-typed-default.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="9227e-120">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9227e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9227e-121">See also</span></span>

- [<span data-ttu-id="9227e-122">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="9227e-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9227e-123">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="9227e-123">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="9227e-124">C # 類型的預設值</span><span class="sxs-lookup"><span data-stu-id="9227e-124">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="9227e-125">.NET 的泛型</span><span class="sxs-lookup"><span data-stu-id="9227e-125">Generics in .NET</span></span>](../../../standard/generics/index.md)
