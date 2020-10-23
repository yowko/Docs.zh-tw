---
description: 深入瞭解 C 中的實值型別、類型和內建的型別#
title: '實值型別-c # 參考'
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 6fb33ad2eb3f6a5e8f6506527f3807f31bf33fdc
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471647"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="5be2d-103">數值型別 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="5be2d-103">Value types (C# reference)</span></span>

<span data-ttu-id="5be2d-104">實*數值型別*和[參考型別](../keywords/reference-types.md)是 c # 型別的兩個主要類別。</span><span class="sxs-lookup"><span data-stu-id="5be2d-104">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="5be2d-105">實值型別的變數包含型別的實例。</span><span class="sxs-lookup"><span data-stu-id="5be2d-105">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="5be2d-106">這與參考型別的變數不同，後者包含型別實例的參考。</span><span class="sxs-lookup"><span data-stu-id="5be2d-106">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="5be2d-107">根據預設，在 [指派](../operators/assignment-operator.md)時，將引數傳遞至方法，並傳回方法結果，會複製變數值。</span><span class="sxs-lookup"><span data-stu-id="5be2d-107">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="5be2d-108">在實數值型別變數的情況下，會複製對應的型別實例。</span><span class="sxs-lookup"><span data-stu-id="5be2d-108">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="5be2d-109">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="5be2d-109">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/shared/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="5be2d-110">如先前的範例所示，實數值型別變數的作業只會影響儲存在變數中的實值型別實例。</span><span class="sxs-lookup"><span data-stu-id="5be2d-110">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="5be2d-111">如果實值型別包含參考型別的資料成員，則在複製值型別實例時，只會複製參考型別的實例參考。</span><span class="sxs-lookup"><span data-stu-id="5be2d-111">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="5be2d-112">複製和原始實數值型別實例都可以存取相同的參考型別實例。</span><span class="sxs-lookup"><span data-stu-id="5be2d-112">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="5be2d-113">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="5be2d-113">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/shared/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="5be2d-114">若要讓您的程式碼較不容易出錯且更健全，請定義和使用不可變的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="5be2d-114">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="5be2d-115">本文僅針對示範目的使用可變的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="5be2d-115">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="5be2d-116">實數值型別的種類</span><span class="sxs-lookup"><span data-stu-id="5be2d-116">Kinds of value types</span></span>

<span data-ttu-id="5be2d-117">實值型別可以是下列兩種類型之一：</span><span class="sxs-lookup"><span data-stu-id="5be2d-117">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="5be2d-118">封裝資料和相關功能的[結構類型](struct.md)</span><span class="sxs-lookup"><span data-stu-id="5be2d-118">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="5be2d-119">[列舉型](enum.md)別，它是由一組命名常數所定義，代表一個選擇或一個選擇組合。</span><span class="sxs-lookup"><span data-stu-id="5be2d-119">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="5be2d-120">[可為 null](nullable-value-types.md)的實值型別 `T?` 代表其基礎實值型別的所有值 `T` ，以及一個額外的[null](../keywords/null.md)值。</span><span class="sxs-lookup"><span data-stu-id="5be2d-120">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="5be2d-121">您無法指派 `null` 給實值型別的變數，除非它是可為 null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="5be2d-121">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="5be2d-122">內建實數值型別</span><span class="sxs-lookup"><span data-stu-id="5be2d-122">Built-in value types</span></span>

<span data-ttu-id="5be2d-123">C # 提供下列內建實數值型別，也稱為 *簡單類型*：</span><span class="sxs-lookup"><span data-stu-id="5be2d-123">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="5be2d-124">整數數值類型</span><span class="sxs-lookup"><span data-stu-id="5be2d-124">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="5be2d-125">浮點數值類型</span><span class="sxs-lookup"><span data-stu-id="5be2d-125">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="5be2d-126">表示布林值的[bool](bool.md)</span><span class="sxs-lookup"><span data-stu-id="5be2d-126">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="5be2d-127">代表 Unicode UTF-16 字元的[char](char.md)</span><span class="sxs-lookup"><span data-stu-id="5be2d-127">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="5be2d-128">所有簡單類型都是結構類型，而且與其他結構類型不同，因為它們允許某些額外的作業：</span><span class="sxs-lookup"><span data-stu-id="5be2d-128">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="5be2d-129">您可以使用常值提供簡單類型的值。</span><span class="sxs-lookup"><span data-stu-id="5be2d-129">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="5be2d-130">例如，`'A'` 是 `char` 型別的常值，而 `2001` 則是 `int` 型別的常值。</span><span class="sxs-lookup"><span data-stu-id="5be2d-130">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="5be2d-131">您可以使用 [const](../keywords/const.md) 關鍵字來宣告簡單型別的常數。</span><span class="sxs-lookup"><span data-stu-id="5be2d-131">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="5be2d-132">不可能有其他結構類型的常數。</span><span class="sxs-lookup"><span data-stu-id="5be2d-132">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="5be2d-133">常數運算式（其運算元都是簡單類型的常數）會在編譯時期評估。</span><span class="sxs-lookup"><span data-stu-id="5be2d-133">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="5be2d-134">從 c # 7.0 開始，c # 支援 [值元組](value-tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="5be2d-134">Beginning with C# 7.0, C# supports [value tuples](value-tuples.md).</span></span> <span data-ttu-id="5be2d-135">值元組是實數值型別，但不是簡單類型。</span><span class="sxs-lookup"><span data-stu-id="5be2d-135">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5be2d-136">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5be2d-136">C# language specification</span></span>

<span data-ttu-id="5be2d-137">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="5be2d-137">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5be2d-138">值類型</span><span class="sxs-lookup"><span data-stu-id="5be2d-138">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="5be2d-139">簡單型別</span><span class="sxs-lookup"><span data-stu-id="5be2d-139">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="5be2d-140">變數</span><span class="sxs-lookup"><span data-stu-id="5be2d-140">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="5be2d-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5be2d-141">See also</span></span>

- [<span data-ttu-id="5be2d-142">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="5be2d-142">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="5be2d-143">參考型別</span><span class="sxs-lookup"><span data-stu-id="5be2d-143">Reference types</span></span>](../keywords/reference-types.md)
