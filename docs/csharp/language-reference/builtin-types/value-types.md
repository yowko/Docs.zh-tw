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
ms.openlocfilehash: 64c9e9eba2495531cfef8a603d53fb21c95c87a4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599391"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="68ab6-103">數值型別 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="68ab6-103">Value types (C# reference)</span></span>

<span data-ttu-id="68ab6-104">實 *數值型別* 和 [參考型別](../keywords/reference-types.md)是 c # 型別的兩個主要類別。</span><span class="sxs-lookup"><span data-stu-id="68ab6-104">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="68ab6-105">實值型別的變數包含型別的實例。</span><span class="sxs-lookup"><span data-stu-id="68ab6-105">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="68ab6-106">這與參考型別的變數不同，後者包含型別實例的參考。</span><span class="sxs-lookup"><span data-stu-id="68ab6-106">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="68ab6-107">根據預設，在 [指派](../operators/assignment-operator.md)時，將引數傳遞至方法，並傳回方法結果，會複製變數值。</span><span class="sxs-lookup"><span data-stu-id="68ab6-107">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="68ab6-108">在實數值型別變數的情況下，會複製對應的型別實例。</span><span class="sxs-lookup"><span data-stu-id="68ab6-108">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="68ab6-109">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="68ab6-109">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/shared/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="68ab6-110">如先前的範例所示，實數值型別變數的作業只會影響儲存在變數中的實值型別實例。</span><span class="sxs-lookup"><span data-stu-id="68ab6-110">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="68ab6-111">如果實值型別包含參考型別的資料成員，則在複製值型別實例時，只會複製參考型別的實例參考。</span><span class="sxs-lookup"><span data-stu-id="68ab6-111">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="68ab6-112">複製和原始實數值型別實例都可以存取相同的參考型別實例。</span><span class="sxs-lookup"><span data-stu-id="68ab6-112">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="68ab6-113">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="68ab6-113">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/shared/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="68ab6-114">若要讓您的程式碼較不容易出錯且更健全，請定義和使用不可變的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="68ab6-114">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="68ab6-115">本文僅針對示範目的使用可變的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="68ab6-115">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types-and-type-constraints"></a><span data-ttu-id="68ab6-116">實數值型別和類型條件約束的種類</span><span class="sxs-lookup"><span data-stu-id="68ab6-116">Kinds of value types and type constraints</span></span>

<span data-ttu-id="68ab6-117">實值型別可以是下列兩種類型之一：</span><span class="sxs-lookup"><span data-stu-id="68ab6-117">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="68ab6-118">封裝資料和相關功能的[結構類型](struct.md)</span><span class="sxs-lookup"><span data-stu-id="68ab6-118">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="68ab6-119">[列舉型](enum.md)別，它是由一組命名常數所定義，代表一個選擇或一個選擇組合。</span><span class="sxs-lookup"><span data-stu-id="68ab6-119">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="68ab6-120">[可為 null](nullable-value-types.md)的實值型別 `T?` 代表其基礎實值型別的所有值 `T` ，以及一個額外的[null](../keywords/null.md)值。</span><span class="sxs-lookup"><span data-stu-id="68ab6-120">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="68ab6-121">您無法指派 `null` 給實值型別的變數，除非它是可為 null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="68ab6-121">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

<span data-ttu-id="68ab6-122">您可以使用[ `struct` 條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)來指定型別參數為不可為 null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="68ab6-122">You can use the [`struct` constraint](../../programming-guide/generics/constraints-on-type-parameters.md) to specify that a type parameter is a non-nullable value type.</span></span> <span data-ttu-id="68ab6-123">結構和列舉類型都符合 `struct` 條件約束。</span><span class="sxs-lookup"><span data-stu-id="68ab6-123">Both structure and enumeration types satisfy the `struct` constraint.</span></span> <span data-ttu-id="68ab6-124">從 c # 7.3 開始，您可以 `System.Enum` 在稱為 [列舉條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints) 的基類條件約束 (中使用，) 指定型別參數為列舉型別。</span><span class="sxs-lookup"><span data-stu-id="68ab6-124">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="68ab6-125">內建實數值型別</span><span class="sxs-lookup"><span data-stu-id="68ab6-125">Built-in value types</span></span>

<span data-ttu-id="68ab6-126">C # 提供下列內建實數值型別，也稱為 *簡單類型*：</span><span class="sxs-lookup"><span data-stu-id="68ab6-126">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="68ab6-127">整數數值類型</span><span class="sxs-lookup"><span data-stu-id="68ab6-127">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="68ab6-128">浮點數值類型</span><span class="sxs-lookup"><span data-stu-id="68ab6-128">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="68ab6-129">表示布林值的[bool](bool.md)</span><span class="sxs-lookup"><span data-stu-id="68ab6-129">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="68ab6-130">代表 Unicode UTF-16 字元的[char](char.md)</span><span class="sxs-lookup"><span data-stu-id="68ab6-130">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="68ab6-131">所有簡單類型都是結構類型，而且與其他結構類型不同，因為它們允許某些額外的作業：</span><span class="sxs-lookup"><span data-stu-id="68ab6-131">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="68ab6-132">您可以使用常值提供簡單類型的值。</span><span class="sxs-lookup"><span data-stu-id="68ab6-132">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="68ab6-133">例如，`'A'` 是 `char` 型別的常值，而 `2001` 則是 `int` 型別的常值。</span><span class="sxs-lookup"><span data-stu-id="68ab6-133">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="68ab6-134">您可以使用 [const](../keywords/const.md) 關鍵字來宣告簡單型別的常數。</span><span class="sxs-lookup"><span data-stu-id="68ab6-134">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="68ab6-135">不可能有其他結構類型的常數。</span><span class="sxs-lookup"><span data-stu-id="68ab6-135">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="68ab6-136">常數運算式（其運算元都是簡單類型的常數）會在編譯時期評估。</span><span class="sxs-lookup"><span data-stu-id="68ab6-136">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="68ab6-137">從 c # 7.0 開始，c # 支援 [值元組](value-tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="68ab6-137">Beginning with C# 7.0, C# supports [value tuples](value-tuples.md).</span></span> <span data-ttu-id="68ab6-138">值元組是實數值型別，但不是簡單類型。</span><span class="sxs-lookup"><span data-stu-id="68ab6-138">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="68ab6-139">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="68ab6-139">C# language specification</span></span>

<span data-ttu-id="68ab6-140">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="68ab6-140">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="68ab6-141">值類型</span><span class="sxs-lookup"><span data-stu-id="68ab6-141">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="68ab6-142">簡單型別</span><span class="sxs-lookup"><span data-stu-id="68ab6-142">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="68ab6-143">變數</span><span class="sxs-lookup"><span data-stu-id="68ab6-143">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="68ab6-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68ab6-144">See also</span></span>

- [<span data-ttu-id="68ab6-145">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="68ab6-145">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="68ab6-146">參考型別</span><span class="sxs-lookup"><span data-stu-id="68ab6-146">Reference types</span></span>](../keywords/reference-types.md)
