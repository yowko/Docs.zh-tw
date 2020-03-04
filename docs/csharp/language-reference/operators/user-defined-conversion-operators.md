---
title: 使用者定義轉換運算子 - C# 參考
description: 了解如何在 C# 中定義自訂的隱含和明確型別轉換。
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: cddb3139742329303989c6fed9e9b64474e6b1f9
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238854"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="21ddc-103">使用者定義轉換運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="21ddc-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="21ddc-104">使用者定義型別可定義要互換型別的自訂隱含轉換和明確轉換。</span><span class="sxs-lookup"><span data-stu-id="21ddc-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="21ddc-105">隱含轉換不需要特殊的語法即可叫用，且可能在各種不同的情況下發生，例如在指派和方法引動過程中發生。</span><span class="sxs-lookup"><span data-stu-id="21ddc-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="21ddc-106">預先C#定義的隱含轉換一律會成功，而且永遠不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="21ddc-106">Predefined C# implicit conversions always succeed and never throw an exception.</span></span> <span data-ttu-id="21ddc-107">使用者定義的隱含轉換也應該以類似方式運作。</span><span class="sxs-lookup"><span data-stu-id="21ddc-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="21ddc-108">如果自訂的轉換可能擲回例外狀況或遺失資訊，請將其定義為明確轉換。</span><span class="sxs-lookup"><span data-stu-id="21ddc-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="21ddc-109">[is](type-testing-and-cast.md#is-operator) 和 [as](type-testing-and-cast.md#as-operator) 運算子不會考慮使用者定義的轉換。</span><span class="sxs-lookup"><span data-stu-id="21ddc-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="21ddc-110">使用[轉換運算子 ()](type-testing-and-cast.md#cast-operator-) 叫用使用者定義的明確轉換。</span><span class="sxs-lookup"><span data-stu-id="21ddc-110">Use the [cast operator ()](type-testing-and-cast.md#cast-operator-) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="21ddc-111">使用 `operator` 和 `implicit` 或 `explicit` 關鍵字，分別定義隱含或明確轉換。</span><span class="sxs-lookup"><span data-stu-id="21ddc-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="21ddc-112">您用來定義轉換的型別必須是來源型別或該轉換的目標型別。</span><span class="sxs-lookup"><span data-stu-id="21ddc-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="21ddc-113">您可以將兩個使用者定義型別之間的轉換定義為兩個型別其中之一。</span><span class="sxs-lookup"><span data-stu-id="21ddc-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="21ddc-114">下面範例說明如何定義隱含和明確轉換：</span><span class="sxs-lookup"><span data-stu-id="21ddc-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](~/samples/snippets/csharp/language-reference/operators/UserDefinedConversions.cs)]

<span data-ttu-id="21ddc-115">您也可以使用 `operator` 關鍵字來多載預先定義的 C# 運算子。</span><span class="sxs-lookup"><span data-stu-id="21ddc-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="21ddc-116">如需詳細資訊，請參閱[運算子多載](operator-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="21ddc-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="21ddc-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="21ddc-117">C# language specification</span></span>

<span data-ttu-id="21ddc-118">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="21ddc-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="21ddc-119">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="21ddc-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="21ddc-120">使用者定義轉換</span><span class="sxs-lookup"><span data-stu-id="21ddc-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="21ddc-121">隱含轉換</span><span class="sxs-lookup"><span data-stu-id="21ddc-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="21ddc-122">明確轉換</span><span class="sxs-lookup"><span data-stu-id="21ddc-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="21ddc-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21ddc-123">See also</span></span>

- [<span data-ttu-id="21ddc-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="21ddc-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="21ddc-125">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="21ddc-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="21ddc-126">運算子多載</span><span class="sxs-lookup"><span data-stu-id="21ddc-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="21ddc-127">型別測試和轉換運算子</span><span class="sxs-lookup"><span data-stu-id="21ddc-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="21ddc-128">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="21ddc-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="21ddc-129">設計方針-轉換運算子</span><span class="sxs-lookup"><span data-stu-id="21ddc-129">Design guidelines - Conversion operators</span></span>](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [<span data-ttu-id="21ddc-130">C# 中鏈結的使用者定義明確轉換</span><span class="sxs-lookup"><span data-stu-id="21ddc-130">Chained user-defined explicit conversions in C#</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
