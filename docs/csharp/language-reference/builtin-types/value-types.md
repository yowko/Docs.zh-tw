---
title: 數值型別 - C# 引用
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399578"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="182d5-102">數值型別（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="182d5-102">Value types (C# reference)</span></span>

<span data-ttu-id="182d5-103">*數值型別*和[參考型別](../keywords/reference-types.md)是 C# 類型的兩個主要類別。</span><span class="sxs-lookup"><span data-stu-id="182d5-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="182d5-104">數值型別的變數包含類型的實例。</span><span class="sxs-lookup"><span data-stu-id="182d5-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="182d5-105">這與參考型別的變數不同，該變數包含對類型實例的引用。</span><span class="sxs-lookup"><span data-stu-id="182d5-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="182d5-106">預設情況下，在[賦值](../operators/assignment-operator.md)時，將參數傳遞給方法，並返回方法結果，將複製變數值。</span><span class="sxs-lookup"><span data-stu-id="182d5-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="182d5-107">對於數值型別變數，將複製相應的類型實例。</span><span class="sxs-lookup"><span data-stu-id="182d5-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="182d5-108">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="182d5-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="182d5-109">如前面的示例所示，數值型別變數上的操作僅影響存儲在變數中的數值型別的實例。</span><span class="sxs-lookup"><span data-stu-id="182d5-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="182d5-110">如果數值型別包含參考型別的資料成員，則在複製數值型別實例時，僅複製對參考型別實例的引用。</span><span class="sxs-lookup"><span data-stu-id="182d5-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="182d5-111">副本和原始數值型別實例都有權訪問同一參考型別實例。</span><span class="sxs-lookup"><span data-stu-id="182d5-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="182d5-112">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="182d5-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="182d5-113">為了使代碼不易出錯且更健壯，請定義和使用不可變的數值型別。</span><span class="sxs-lookup"><span data-stu-id="182d5-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="182d5-114">本文僅出於演示目的使用可變數值型別。</span><span class="sxs-lookup"><span data-stu-id="182d5-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="182d5-115">數值型別</span><span class="sxs-lookup"><span data-stu-id="182d5-115">Kinds of value types</span></span>

<span data-ttu-id="182d5-116">數值型別可以是以下兩種類型之一：</span><span class="sxs-lookup"><span data-stu-id="182d5-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="182d5-117">結構[類型](struct.md)，它封裝資料和相關功能</span><span class="sxs-lookup"><span data-stu-id="182d5-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="182d5-118">[枚舉類型](enum.md)，由一組命名常量定義，表示選擇或選項群組合</span><span class="sxs-lookup"><span data-stu-id="182d5-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="182d5-119">[空數值型別](nullable-value-types.md)`T?`表示其基礎數值型別`T`的所有值和附加[空](../keywords/null.md)值。</span><span class="sxs-lookup"><span data-stu-id="182d5-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="182d5-120">不能分配給`null`數值型別的變數，除非它是一個空數值型別。</span><span class="sxs-lookup"><span data-stu-id="182d5-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="182d5-121">內置數值型別</span><span class="sxs-lookup"><span data-stu-id="182d5-121">Built-in value types</span></span>

<span data-ttu-id="182d5-122">C# 提供以下內置數值型別，也稱為*簡單類型*：</span><span class="sxs-lookup"><span data-stu-id="182d5-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="182d5-123">整數數值類型</span><span class="sxs-lookup"><span data-stu-id="182d5-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="182d5-124">浮點數值類型</span><span class="sxs-lookup"><span data-stu-id="182d5-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="182d5-125">代表布林值的[布林](bool.md)</span><span class="sxs-lookup"><span data-stu-id="182d5-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="182d5-126">表示 Unicode UTF-16 字元的[字元](char.md)</span><span class="sxs-lookup"><span data-stu-id="182d5-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="182d5-127">所有簡單類型都是結構類型，與其他結構類型不同，因為它們允許某些附加操作：</span><span class="sxs-lookup"><span data-stu-id="182d5-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="182d5-128">可以使用文本提供簡單類型的值。</span><span class="sxs-lookup"><span data-stu-id="182d5-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="182d5-129">例如，`'A'` 是 `char` 型別的常值，而 `2001` 則是 `int` 型別的常值。</span><span class="sxs-lookup"><span data-stu-id="182d5-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="182d5-130">您可以使用 [const](../keywords/const.md) 關鍵字來宣告簡單型別的常數。</span><span class="sxs-lookup"><span data-stu-id="182d5-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="182d5-131">不可能有其他結構類型的常量。</span><span class="sxs-lookup"><span data-stu-id="182d5-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="182d5-132">常量運算式（其運算元都是簡單類型的常量）在編譯時計算。</span><span class="sxs-lookup"><span data-stu-id="182d5-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="182d5-133">從 C# 7.0 開始，C# 支援[值 tups](../../tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="182d5-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="182d5-134">值元組是數值型別，但不是簡單類型。</span><span class="sxs-lookup"><span data-stu-id="182d5-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="182d5-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="182d5-135">C# language specification</span></span>

<span data-ttu-id="182d5-136">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="182d5-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="182d5-137">實值型別</span><span class="sxs-lookup"><span data-stu-id="182d5-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="182d5-138">簡單型別</span><span class="sxs-lookup"><span data-stu-id="182d5-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="182d5-139">變數</span><span class="sxs-lookup"><span data-stu-id="182d5-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="182d5-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="182d5-140">See also</span></span>

- [<span data-ttu-id="182d5-141">C# 參考</span><span class="sxs-lookup"><span data-stu-id="182d5-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="182d5-142">參考型別</span><span class="sxs-lookup"><span data-stu-id="182d5-142">Reference types</span></span>](../keywords/reference-types.md)
