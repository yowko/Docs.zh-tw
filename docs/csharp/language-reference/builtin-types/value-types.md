---
title: 實數值型別C# -參考
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 76f4a3ed929e3ac8e3e6cc74158e75af7a6c8cf2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625943"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="b3403-102">實數值型別C# （參考）</span><span class="sxs-lookup"><span data-stu-id="b3403-102">Value types (C# reference)</span></span>

<span data-ttu-id="b3403-103">實*數值型別*和[參考型別](../keywords/reference-types.md)是兩個主要的C#類型類別。</span><span class="sxs-lookup"><span data-stu-id="b3403-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="b3403-104">實值型別的變數包含型別的實例。</span><span class="sxs-lookup"><span data-stu-id="b3403-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="b3403-105">這與參考型別的變數不同，後者包含型別之實例的參考。</span><span class="sxs-lookup"><span data-stu-id="b3403-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="b3403-106">根據預設，在[指派](../operators/assignment-operator.md)時，將引數傳遞至方法，並傳回方法結果，會複製變數值。</span><span class="sxs-lookup"><span data-stu-id="b3403-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="b3403-107">在實數值型別變數的情況下，會複製對應的類型實例。</span><span class="sxs-lookup"><span data-stu-id="b3403-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="b3403-108">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="b3403-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="b3403-109">如上述範例所示，實數值型別變數上的作業只會影響實數值型別的實例，並儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="b3403-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="b3403-110">如果實值型別包含引用型別的資料成員，則在複製實值型別實例時，只會複製參考型別的實例參考。</span><span class="sxs-lookup"><span data-stu-id="b3403-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="b3403-111">複製和原始實數值型別實例都具有相同的參考類型實例的存取權。</span><span class="sxs-lookup"><span data-stu-id="b3403-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="b3403-112">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="b3403-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="b3403-113">若要讓您的程式碼較不容易出錯且更健全，請定義和使用不可變的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="b3403-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="b3403-114">本文只會針對示範用途使用可變的實值型別。</span><span class="sxs-lookup"><span data-stu-id="b3403-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="b3403-115">實數值型別的種類</span><span class="sxs-lookup"><span data-stu-id="b3403-115">Kinds of value types</span></span>

<span data-ttu-id="b3403-116">實值型別可以是下列兩種類型的其中一種：</span><span class="sxs-lookup"><span data-stu-id="b3403-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="b3403-117">封裝資料和相關功能的[結構類型](struct.md)</span><span class="sxs-lookup"><span data-stu-id="b3403-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="b3403-118">[列舉類型](enum.md)，這是由一組已命名的常數所定義，代表選擇或選擇的組合</span><span class="sxs-lookup"><span data-stu-id="b3403-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="b3403-119">[可為 null 的實數值型別](nullable-value-types.md)`T?` 代表其基礎數值型別的所有值，`T` 和額外的[null](../keywords/null.md)值。</span><span class="sxs-lookup"><span data-stu-id="b3403-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="b3403-120">您無法將 `null` 指派給實數值型別的變數，除非它是可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="b3403-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="b3403-121">內建實數值型別</span><span class="sxs-lookup"><span data-stu-id="b3403-121">Built-in value types</span></span>

<span data-ttu-id="b3403-122">C#提供下列內建實數值型別，也稱為*簡單類型*：</span><span class="sxs-lookup"><span data-stu-id="b3403-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="b3403-123">整數數數值型別</span><span class="sxs-lookup"><span data-stu-id="b3403-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="b3403-124">浮點數數值型別</span><span class="sxs-lookup"><span data-stu-id="b3403-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="b3403-125">表示布林值的[bool](bool.md)</span><span class="sxs-lookup"><span data-stu-id="b3403-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="b3403-126">代表 Unicode UTF-16 字元的[char](char.md)</span><span class="sxs-lookup"><span data-stu-id="b3403-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="b3403-127">所有簡單型別都是結構型別，而且與其他結構型別不同，因為它們允許特定的其他作業：</span><span class="sxs-lookup"><span data-stu-id="b3403-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="b3403-128">您可以使用常值來提供簡單類型的值。</span><span class="sxs-lookup"><span data-stu-id="b3403-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="b3403-129">例如，`'A'` 是 `char` 型別的常值，而 `2001` 則是 `int` 型別的常值。</span><span class="sxs-lookup"><span data-stu-id="b3403-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="b3403-130">您可以使用 [const](../keywords/const.md) 關鍵字來宣告簡單型別的常數。</span><span class="sxs-lookup"><span data-stu-id="b3403-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="b3403-131">不可能有其他結構類型的常數。</span><span class="sxs-lookup"><span data-stu-id="b3403-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="b3403-132">常數運算式（其運算元為簡單類型的所有常數）會在編譯時期進行評估。</span><span class="sxs-lookup"><span data-stu-id="b3403-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="b3403-133">從C# 7.0 開始， C#支援[值元組](../../tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="b3403-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="b3403-134">值元組是實數值型別，但不是簡單類型。</span><span class="sxs-lookup"><span data-stu-id="b3403-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b3403-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b3403-135">C# language specification</span></span>

<span data-ttu-id="b3403-136">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="b3403-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="b3403-137">值類型</span><span class="sxs-lookup"><span data-stu-id="b3403-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="b3403-138">簡單型別</span><span class="sxs-lookup"><span data-stu-id="b3403-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="b3403-139">變數</span><span class="sxs-lookup"><span data-stu-id="b3403-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="b3403-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3403-140">See also</span></span>

- [<span data-ttu-id="b3403-141">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b3403-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="b3403-142">參考型別</span><span class="sxs-lookup"><span data-stu-id="b3403-142">Reference types</span></span>](../keywords/reference-types.md)
