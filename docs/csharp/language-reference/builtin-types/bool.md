---
title: 布林型 - C# 參考
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2ba2e54a6b0f24402fc3728dfe19b548a2368830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846441"
---
# <a name="bool-c-reference"></a><span data-ttu-id="ca60d-102">布林（C# 參考）</span><span class="sxs-lookup"><span data-stu-id="ca60d-102">bool (C# reference)</span></span>

<span data-ttu-id="ca60d-103">類型`bool`關鍵字是 .NET<xref:System.Boolean?displayProperty=nameWithType>結構類型的別名，表示布林值，可以是`true`或`false`。</span><span class="sxs-lookup"><span data-stu-id="ca60d-103">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="ca60d-104">要使用`bool`類型的值執行邏輯操作，請使用[布林邏輯](../operators/boolean-logical-operators.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="ca60d-104">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="ca60d-105">類型`bool`是[比較](../operators/comparison-operators.md)和[相等](../operators/equality-operators.md)運算子的結果類型。</span><span class="sxs-lookup"><span data-stu-id="ca60d-105">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="ca60d-106">運算式`bool`可以是[if](../keywords/if-else.md)中的控制條件運算式，在 中[執行](../keywords/do.md)，[對於](../keywords/while.md)[語句和](../keywords/for.md)條件[運算子`?:`](../operators/conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="ca60d-106">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="ca60d-107">`bool`類型的預設值為`false`。</span><span class="sxs-lookup"><span data-stu-id="ca60d-107">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="ca60d-108">常值</span><span class="sxs-lookup"><span data-stu-id="ca60d-108">Literals</span></span>

<span data-ttu-id="ca60d-109">可以使用`true`和`false`文本來初始化`bool`變數或傳遞`bool`值：</span><span class="sxs-lookup"><span data-stu-id="ca60d-109">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="ca60d-110">三值布林邏輯</span><span class="sxs-lookup"><span data-stu-id="ca60d-110">Three-valued Boolean logic</span></span>

<span data-ttu-id="ca60d-111">如果需要支援三值`bool?`邏輯，請使用可 null 類型，例如，當您使用支援三值布林類型的資料庫時。</span><span class="sxs-lookup"><span data-stu-id="ca60d-111">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="ca60d-112">針對 `bool?` 運算元，預先定義的 `&` 和 `|` 運算子支援三值邏輯。</span><span class="sxs-lookup"><span data-stu-id="ca60d-112">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="ca60d-113">如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="ca60d-113">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="ca60d-114">有關空數值型別的詳細資訊，請參閱[空數值型別](nullable-value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ca60d-114">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="ca60d-115">轉換</span><span class="sxs-lookup"><span data-stu-id="ca60d-115">Conversions</span></span>

<span data-ttu-id="ca60d-116">C# 僅提供兩個涉及`bool`該類型的轉換。</span><span class="sxs-lookup"><span data-stu-id="ca60d-116">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="ca60d-117">這些是對相應空`bool?`類型的隱式轉換，是從`bool?`該類型的顯式轉換。</span><span class="sxs-lookup"><span data-stu-id="ca60d-117">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="ca60d-118">但是，.NET 提供了可用於轉換為`bool`類型或從類型轉換的其他方法。</span><span class="sxs-lookup"><span data-stu-id="ca60d-118">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="ca60d-119">有關詳細資訊，請參閱<xref:System.Boolean?displayProperty=nameWithType>API 參考頁的"[轉換到布林值"和"從布林值轉換"](/dotnet/api/system.boolean#converting-to-and-from-boolean-values)部分。</span><span class="sxs-lookup"><span data-stu-id="ca60d-119">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ca60d-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ca60d-120">C# language specification</span></span>

<span data-ttu-id="ca60d-121">有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[Bool 類型](~/_csharplang/spec/types.md#the-bool-type)部分。</span><span class="sxs-lookup"><span data-stu-id="ca60d-121">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca60d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca60d-122">See also</span></span>

- [<span data-ttu-id="ca60d-123">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ca60d-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ca60d-124">實值型別</span><span class="sxs-lookup"><span data-stu-id="ca60d-124">Value types</span></span>](value-types.md)
- [<span data-ttu-id="ca60d-125">true 和 false 運算子</span><span class="sxs-lookup"><span data-stu-id="ca60d-125">true and false operators</span></span>](../operators/true-false-operators.md)
