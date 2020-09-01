---
description: 瞭解 C 中的內建布林類型#
title: 'bool 型別-c # 參考'
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 23e5bc34f1751b0a706c20dae340920239fcda9d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126459"
---
# <a name="bool-c-reference"></a><span data-ttu-id="e0c60-103">bool (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="e0c60-103">bool (C# reference)</span></span>

<span data-ttu-id="e0c60-104">`bool`Type 關鍵字是 <xref:System.Boolean?displayProperty=nameWithType> 代表布林值（可以是或）之 .net 結構類型的別名 `true` `false` 。</span><span class="sxs-lookup"><span data-stu-id="e0c60-104">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="e0c60-105">若要執行具有類型值的邏輯作業 `bool` ，請使用 [布林值邏輯](../operators/boolean-logical-operators.md) 運算子。</span><span class="sxs-lookup"><span data-stu-id="e0c60-105">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="e0c60-106">此 `bool` 類型是比較和[等號](../operators/equality-operators.md)[比較](../operators/comparison-operators.md)運算子的結果型別。</span><span class="sxs-lookup"><span data-stu-id="e0c60-106">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="e0c60-107">`bool`運算式可以是[if](../keywords/if-else.md)、 [do](../keywords/do.md)、 [while](../keywords/while.md)和[for](../keywords/for.md)語句和[條件運算子 `?:` ](../operators/conditional-operator.md)中的控制條件運算式。</span><span class="sxs-lookup"><span data-stu-id="e0c60-107">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="e0c60-108">此類型的預設值 `bool` 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="e0c60-108">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="e0c60-109">常值</span><span class="sxs-lookup"><span data-stu-id="e0c60-109">Literals</span></span>

<span data-ttu-id="e0c60-110">您可以使用 `true` 和 `false` 常值來初始化 `bool` 變數或傳遞 `bool` 值：</span><span class="sxs-lookup"><span data-stu-id="e0c60-110">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="e0c60-111">三值布林值邏輯</span><span class="sxs-lookup"><span data-stu-id="e0c60-111">Three-valued Boolean logic</span></span>

<span data-ttu-id="e0c60-112">`bool?`如果您需要支援三值的邏輯（例如，當您使用支援三值布林類型的資料庫時），請使用可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="e0c60-112">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="e0c60-113">針對 `bool?` 運算元，預先定義的 `&` 和 `|` 運算子支援三值邏輯。</span><span class="sxs-lookup"><span data-stu-id="e0c60-113">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="e0c60-114">如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="e0c60-114">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="e0c60-115">如需可為 null 實值型別的詳細資訊，請參閱[可為 null 的實數值型別](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="e0c60-115">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="e0c60-116">轉換</span><span class="sxs-lookup"><span data-stu-id="e0c60-116">Conversions</span></span>

<span data-ttu-id="e0c60-117">C # 只會提供兩個牽涉到類型的轉換 `bool` 。</span><span class="sxs-lookup"><span data-stu-id="e0c60-117">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="e0c60-118">這些是對應至可為 null 之型別的隱含轉換 `bool?` ，以及來自型別的明確轉換 `bool?` 。</span><span class="sxs-lookup"><span data-stu-id="e0c60-118">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="e0c60-119">不過，.NET 提供其他方法，可讓您用來在類型之間進行轉換 `bool` 。</span><span class="sxs-lookup"><span data-stu-id="e0c60-119">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="e0c60-120">如需詳細資訊，請參閱 API 參考頁面的 [轉換為和來源布林值](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) 一節 <xref:System.Boolean?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e0c60-120">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e0c60-121">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e0c60-121">C# language specification</span></span>

<span data-ttu-id="e0c60-122">如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[bool 類型](~/_csharplang/spec/types.md#the-bool-type)一節。</span><span class="sxs-lookup"><span data-stu-id="e0c60-122">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0c60-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0c60-123">See also</span></span>

- [<span data-ttu-id="e0c60-124">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="e0c60-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e0c60-125">值類型</span><span class="sxs-lookup"><span data-stu-id="e0c60-125">Value types</span></span>](value-types.md)
- [<span data-ttu-id="e0c60-126">true 和 false 運算子</span><span class="sxs-lookup"><span data-stu-id="e0c60-126">true and false operators</span></span>](../operators/true-false-operators.md)
