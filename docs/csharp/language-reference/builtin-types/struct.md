---
title: '結構類型-c # 參考'
description: 瞭解 C 中的結構類型#
ms.date: 10/23/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 2ceac94c04dd8deb169e836f09928dfd9a38ac35
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025429"
---
# <a name="structure-types-c-reference"></a><span data-ttu-id="b0d72-103">結構類型 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="b0d72-103">Structure types (C# reference)</span></span>

<span data-ttu-id="b0d72-104">*結構類型* (或 *結構類型*) 是可封裝資料和相關功能的實 [值型](value-types.md)別。</span><span class="sxs-lookup"><span data-stu-id="b0d72-104">A *structure type* (or *struct type*) is a [value type](value-types.md) that can encapsulate data and related functionality.</span></span> <span data-ttu-id="b0d72-105">您可以使用 `struct` 關鍵字來定義結構類型：</span><span class="sxs-lookup"><span data-stu-id="b0d72-105">You use the `struct` keyword to define a structure type:</span></span>

[!code-csharp[struct example](snippets/shared/StructType.cs#StructExample)]

<span data-ttu-id="b0d72-106">結構類型具有 *值語義*。</span><span class="sxs-lookup"><span data-stu-id="b0d72-106">Structure types have *value semantics*.</span></span> <span data-ttu-id="b0d72-107">也就是說，結構型別的變數包含型別的實例。</span><span class="sxs-lookup"><span data-stu-id="b0d72-107">That is, a variable of a structure type contains an instance of the type.</span></span> <span data-ttu-id="b0d72-108">根據預設，變數值會在指派時複製、將引數傳遞至方法，並傳回方法結果。</span><span class="sxs-lookup"><span data-stu-id="b0d72-108">By default, variable values are copied on assignment, passing an argument to a method, and returning a method result.</span></span> <span data-ttu-id="b0d72-109">在結構類型變數的情況下，會複製類型的實例。</span><span class="sxs-lookup"><span data-stu-id="b0d72-109">In the case of a structure-type variable, an instance of the type is copied.</span></span> <span data-ttu-id="b0d72-110">如需詳細資訊，請參閱實 [數值型別](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d72-110">For more information, see [Value types](value-types.md).</span></span>

<span data-ttu-id="b0d72-111">一般而言，您會使用結構類型來設計以資料為中心的小型型別，以提供小或無的行為。</span><span class="sxs-lookup"><span data-stu-id="b0d72-111">Typically, you use structure types to design small data-centric types that provide little or no behavior.</span></span> <span data-ttu-id="b0d72-112">例如，.NET 會使用結構類型來表示 [整數](integral-numeric-types.md) 和 [實數](floating-point-numeric-types.md)) 的數位 (、 [布林值](bool.md)、 [Unicode 字元](char.md)、 [時間實例](xref:System.DateTime)。</span><span class="sxs-lookup"><span data-stu-id="b0d72-112">For example, .NET uses structure types to represent a number (both [integer](integral-numeric-types.md) and [real](floating-point-numeric-types.md)), a [Boolean value](bool.md), a [Unicode character](char.md), a [time instance](xref:System.DateTime).</span></span> <span data-ttu-id="b0d72-113">如果您是以類型的行為為焦點，請考慮定義 [類別](../keywords/class.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d72-113">If you're focused on the behavior of a type, consider defining a [class](../keywords/class.md).</span></span> <span data-ttu-id="b0d72-114">類別類型具有 *參考語義*。</span><span class="sxs-lookup"><span data-stu-id="b0d72-114">Class types have *reference semantics*.</span></span> <span data-ttu-id="b0d72-115">也就是說，類別型別的變數包含型別實例的參考，而不是實例本身。</span><span class="sxs-lookup"><span data-stu-id="b0d72-115">That is, a variable of a class type contains a reference to an instance of the type, not the instance itself.</span></span>

<span data-ttu-id="b0d72-116">因為結構類型具有值語義，所以建議您定義 *不可變* 的結構類型。</span><span class="sxs-lookup"><span data-stu-id="b0d72-116">Because structure types have value semantics, we recommend you to define *immutable* structure types.</span></span>

## <a name="readonly-struct"></a><span data-ttu-id="b0d72-117">`readonly` 結構</span><span class="sxs-lookup"><span data-stu-id="b0d72-117">`readonly` struct</span></span>

<span data-ttu-id="b0d72-118">從 c # 7.2 開始，您可以使用 `readonly` 修飾詞來宣告結構類型是不可變的。</span><span class="sxs-lookup"><span data-stu-id="b0d72-118">Beginning with C# 7.2, you use the `readonly` modifier to declare that a structure type is immutable.</span></span> <span data-ttu-id="b0d72-119">結構的所有資料成員都 `readonly` 必須是唯讀的，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b0d72-119">All data members of a `readonly` struct must be read-only as follows:</span></span>

- <span data-ttu-id="b0d72-120">任何欄位宣告都必須有[ `readonly` 修飾](../keywords/readonly.md)詞</span><span class="sxs-lookup"><span data-stu-id="b0d72-120">Any field declaration must have the [`readonly` modifier](../keywords/readonly.md)</span></span>
- <span data-ttu-id="b0d72-121">任何屬性（包括自動執行的屬性）都必須是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="b0d72-121">Any property, including auto-implemented ones, must be read-only.</span></span> <span data-ttu-id="b0d72-122">在 c # 9.0 和更新版本中，屬性可能具有[ `init` 存取](../../whats-new/csharp-9.md#init-only-setters)子。</span><span class="sxs-lookup"><span data-stu-id="b0d72-122">In C# 9.0 and later, a property may have an [`init` accessor](../../whats-new/csharp-9.md#init-only-setters).</span></span>

<span data-ttu-id="b0d72-123">這可保證結構的成員不會 `readonly` 修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="b0d72-123">That guarantees that no member of a `readonly` struct modifies the state of the struct.</span></span> <span data-ttu-id="b0d72-124">在 c # 8.0 和更新版本中，這表示其他實例成員（除了函式之外）是隱含的 [`readonly`](#readonly-instance-members) 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-124">In C# 8.0 and later, that means that other instance members except constructors are implicitly [`readonly`](#readonly-instance-members).</span></span>

> [!NOTE]
> <span data-ttu-id="b0d72-125">在 `readonly` 結構中，可變動參考型別的資料成員仍可以改變本身的狀態。</span><span class="sxs-lookup"><span data-stu-id="b0d72-125">In a `readonly` struct, a data member of a mutable reference type still can mutate its own state.</span></span> <span data-ttu-id="b0d72-126">例如，您無法取代 <xref:System.Collections.Generic.List%601> 實例，但是可以在其中加入新的元素。</span><span class="sxs-lookup"><span data-stu-id="b0d72-126">For example, you can't replace a <xref:System.Collections.Generic.List%601> instance, but you can add new elements to it.</span></span>

<span data-ttu-id="b0d72-127">下列程式碼會定義 `readonly` 具有僅限初始屬性 setter 的結構，可在 c # 9.0 和更新版本中使用：</span><span class="sxs-lookup"><span data-stu-id="b0d72-127">The following code defines a `readonly` struct with init-only property setters, available in C# 9.0 and later:</span></span>

[!code-csharp[readonly struct](snippets/shared/StructType.cs#ReadonlyStruct)]

## <a name="readonly-instance-members"></a><span data-ttu-id="b0d72-128">`readonly` 實例成員</span><span class="sxs-lookup"><span data-stu-id="b0d72-128">`readonly` instance members</span></span>

<span data-ttu-id="b0d72-129">從 c # 8.0 開始，您也可以使用 `readonly` 修飾詞來宣告實例成員不會修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="b0d72-129">Beginning with C# 8.0, you can also use the `readonly` modifier to declare that an instance member doesn't modify the state of a struct.</span></span> <span data-ttu-id="b0d72-130">如果您無法將整個結構類型宣告為 `readonly` ，請使用 `readonly` 修飾詞來標記不會修改結構狀態的實例成員。</span><span class="sxs-lookup"><span data-stu-id="b0d72-130">If you can't declare the whole structure type as `readonly`, use the `readonly` modifier to mark the instance members that don't modify the state of the struct.</span></span>

<span data-ttu-id="b0d72-131">在 `readonly` 實例成員中，您無法指派給結構的實例欄位。</span><span class="sxs-lookup"><span data-stu-id="b0d72-131">Within a `readonly` instance member, you can't assign to structure's instance fields.</span></span> <span data-ttu-id="b0d72-132">不過， `readonly` 成員可以呼叫非 `readonly` 成員。</span><span class="sxs-lookup"><span data-stu-id="b0d72-132">However, a `readonly` member can call a non-`readonly` member.</span></span> <span data-ttu-id="b0d72-133">在這種情況下，編譯器會建立結構實例的複本，並呼叫 `readonly` 該複本上的非成員。</span><span class="sxs-lookup"><span data-stu-id="b0d72-133">In that case the compiler creates a copy of the structure instance and calls the non-`readonly` member on that copy.</span></span> <span data-ttu-id="b0d72-134">因此，原始的結構實例不會被修改。</span><span class="sxs-lookup"><span data-stu-id="b0d72-134">As a result, the original structure instance is not modified.</span></span>

<span data-ttu-id="b0d72-135">一般來說，您會將 `readonly` 修飾詞套用至下列類型的實例成員：</span><span class="sxs-lookup"><span data-stu-id="b0d72-135">Typically, you apply the `readonly` modifier to the following kinds of instance members:</span></span>

- <span data-ttu-id="b0d72-136">方法：</span><span class="sxs-lookup"><span data-stu-id="b0d72-136">methods:</span></span>

  [!code-csharp[readonly method](snippets/shared/StructType.cs#ReadonlyMethod)]

  <span data-ttu-id="b0d72-137">您也可以將修飾詞套用 `readonly` 至覆寫在中宣告之方法的方法 <xref:System.Object?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="b0d72-137">You can also apply the `readonly` modifier to methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>:</span></span>

  [!code-csharp[readonly override](snippets/shared/StructType.cs#ReadonlyOverride)]

- <span data-ttu-id="b0d72-138">屬性和索引子：</span><span class="sxs-lookup"><span data-stu-id="b0d72-138">properties and indexers:</span></span>

  [!code-csharp[readonly property get](snippets/shared/StructType.cs#ReadonlyProperty)]

  <span data-ttu-id="b0d72-139">如果您需要將修飾詞套用 `readonly` 至屬性或索引子的兩個存取子，請將它套用至屬性或索引子的宣告中。</span><span class="sxs-lookup"><span data-stu-id="b0d72-139">If you need to apply the `readonly` modifier to both accessors of a property or indexer, apply it in the declaration of the property or indexer.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b0d72-140">編譯器會將 `get` [自動執行之屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md) 的存取子宣告為 `readonly` ，而不論屬性宣告中的修飾詞是否存在 `readonly` 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-140">The compiler declares a `get` accessor of an [auto-implemented property](../../programming-guide/classes-and-structs/auto-implemented-properties.md) as `readonly`, regardless of presence of the `readonly` modifier in a property declaration.</span></span>

  <span data-ttu-id="b0d72-141">在 c # 9.0 和更新版本中，您可以 `readonly` 使用存取子將修飾詞套用至屬性或索引子 `init` ：</span><span class="sxs-lookup"><span data-stu-id="b0d72-141">In C# 9.0 and later, you may apply the `readonly` modifier to a property or indexer with an `init` accessor:</span></span>

  :::code language="csharp" source="snippets/shared/StructType.cs" id="ReadonlyWithInit":::

<span data-ttu-id="b0d72-142">您無法將修飾詞套用 `readonly` 至結構類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="b0d72-142">You can't apply the `readonly` modifier to static members of a structure type.</span></span>

<span data-ttu-id="b0d72-143">編譯器可能會使用 `readonly` 修飾詞進行效能優化。</span><span class="sxs-lookup"><span data-stu-id="b0d72-143">The compiler may make use of the `readonly` modifier for performance optimizations.</span></span> <span data-ttu-id="b0d72-144">如需詳細資訊，請參閱 [撰寫安全且有效率的 c # 程式碼](../../write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d72-144">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="limitations-with-the-design-of-a-structure-type"></a><span data-ttu-id="b0d72-145">結構類型設計的限制</span><span class="sxs-lookup"><span data-stu-id="b0d72-145">Limitations with the design of a structure type</span></span>

<span data-ttu-id="b0d72-146">當您設計結構類型時，與 [類別](../keywords/class.md) 類型具有相同的功能，但有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="b0d72-146">When you design a structure type, you have the same capabilities as with a [class](../keywords/class.md) type, with the following exceptions:</span></span>

- <span data-ttu-id="b0d72-147">您無法宣告無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="b0d72-147">You can't declare a parameterless constructor.</span></span> <span data-ttu-id="b0d72-148">每個結構類型都已提供隱含的無參數函式，其會產生型別的 [預設值](default-values.md) 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-148">Every structure type already provides an implicit parameterless constructor that produces the [default value](default-values.md) of the type.</span></span>

- <span data-ttu-id="b0d72-149">您無法在宣告時初始化實例欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="b0d72-149">You can't initialize an instance field or property at its declaration.</span></span> <span data-ttu-id="b0d72-150">不過，您可以在宣告時初始化 [靜態](../keywords/static.md) 或 [const](../keywords/const.md) 欄位或靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="b0d72-150">However, you can initialize a [static](../keywords/static.md) or [const](../keywords/const.md) field or a static property at its declaration.</span></span>

- <span data-ttu-id="b0d72-151">結構類型的函式必須初始化類型的所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="b0d72-151">A constructor of a structure type must initialize all instance fields of the type.</span></span>

- <span data-ttu-id="b0d72-152">結構類型無法繼承自其他類別或結構類型，而且不能是類別的基底。</span><span class="sxs-lookup"><span data-stu-id="b0d72-152">A structure type can't inherit from other class or structure type and it can't be the base of a class.</span></span> <span data-ttu-id="b0d72-153">不過，結構類型可以執行 [介面](../keywords/interface.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d72-153">However, a structure type can implement [interfaces](../keywords/interface.md).</span></span>

- <span data-ttu-id="b0d72-154">您無法在結構 [類型中宣告](../../programming-guide/classes-and-structs/destructors.md) 完成項。</span><span class="sxs-lookup"><span data-stu-id="b0d72-154">You can't declare a [finalizer](../../programming-guide/classes-and-structs/destructors.md) within a structure type.</span></span>

## <a name="instantiation-of-a-structure-type"></a><span data-ttu-id="b0d72-155">結構類型的具現化</span><span class="sxs-lookup"><span data-stu-id="b0d72-155">Instantiation of a structure type</span></span>

<span data-ttu-id="b0d72-156">在 c # 中，您必須先初始化已宣告的變數，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="b0d72-156">In C#, you must initialize a declared variable before it can be used.</span></span> <span data-ttu-id="b0d72-157">因為結構類型變數無法 `null` (，除非它是 [可為 null 實值型](nullable-value-types.md) 別) 的變數，所以您必須具現化對應類型的實例。</span><span class="sxs-lookup"><span data-stu-id="b0d72-157">Because a structure-type variable can't be `null` (unless it's a variable of a [nullable value type](nullable-value-types.md)), you must instantiate an instance of the corresponding type.</span></span> <span data-ttu-id="b0d72-158">有幾種方法可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="b0d72-158">There are several ways to do that.</span></span>

<span data-ttu-id="b0d72-159">一般來說，您可以使用運算子呼叫適當的函式，以具現化結構類型 [`new`](../operators/new-operator.md) 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-159">Typically, you instantiate a structure type by calling an appropriate constructor with the [`new`](../operators/new-operator.md) operator.</span></span> <span data-ttu-id="b0d72-160">每個結構類型都至少有一個函數。</span><span class="sxs-lookup"><span data-stu-id="b0d72-160">Every structure type has at least one constructor.</span></span> <span data-ttu-id="b0d72-161">這是隱含無參數的函式，它會產生型別的 [預設值](default-values.md) 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-161">That's an implicit parameterless constructor, which produces the [default value](default-values.md) of the type.</span></span> <span data-ttu-id="b0d72-162">您也可以使用 [預設值運算式](../operators/default.md) 來產生型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="b0d72-162">You can also use a [default value expression](../operators/default.md) to produce the default value of a type.</span></span>

<span data-ttu-id="b0d72-163">如果結構類型的所有實例欄位都可以存取，您也可以在不使用運算子的情況下將它具現化 `new` 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-163">If all instance fields of a structure type are accessible, you can also instantiate it without the `new` operator.</span></span> <span data-ttu-id="b0d72-164">在這種情況下，您必須在第一次使用實例之前，初始化所有的實例欄位。</span><span class="sxs-lookup"><span data-stu-id="b0d72-164">In that case you must initialize all instance fields before the first use of the instance.</span></span> <span data-ttu-id="b0d72-165">下列範例顯示如何執行該項工作：</span><span class="sxs-lookup"><span data-stu-id="b0d72-165">The following example shows how to do that:</span></span>

[!code-csharp[without new](snippets/shared/StructType.cs#WithoutNew)]

<span data-ttu-id="b0d72-166">在內 [建實值](value-types.md#built-in-value-types)型別的情況下，請使用對應的常值來指定類型的值。</span><span class="sxs-lookup"><span data-stu-id="b0d72-166">In the case of the [built-in value types](value-types.md#built-in-value-types), use the corresponding literals to specify a value of the type.</span></span>

## <a name="passing-structure-type-variables-by-reference"></a><span data-ttu-id="b0d72-167">以傳址方式傳遞結構類型變數</span><span class="sxs-lookup"><span data-stu-id="b0d72-167">Passing structure-type variables by reference</span></span>

<span data-ttu-id="b0d72-168">當您將結構類型變數當作引數傳遞至方法，或是從方法傳回結構類型值時，會複製結構類型的整個實例。</span><span class="sxs-lookup"><span data-stu-id="b0d72-168">When you pass a structure-type variable to a method as an argument or return a structure-type value from a method, the whole instance of a structure type is copied.</span></span> <span data-ttu-id="b0d72-169">這可能會影響您的程式碼在涉及大型結構類型的高效能案例中的效能。</span><span class="sxs-lookup"><span data-stu-id="b0d72-169">That can affect the performance of your code in high-performance scenarios that involve large structure types.</span></span> <span data-ttu-id="b0d72-170">您可以藉由傳址方式傳遞結構類型變數，以避免值複製。</span><span class="sxs-lookup"><span data-stu-id="b0d72-170">You can avoid value copying by passing a structure-type variable by reference.</span></span> <span data-ttu-id="b0d72-171">使用 [`ref`](../keywords/ref.md#passing-an-argument-by-reference) 、 [`out`](../keywords/out-parameter-modifier.md) 或方法參數修飾詞 [`in`](../keywords/in-parameter-modifier.md) 來表示引數必須以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="b0d72-171">Use the [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md), or [`in`](../keywords/in-parameter-modifier.md) method parameter modifiers to indicate that an argument must be passed by reference.</span></span> <span data-ttu-id="b0d72-172">使用 [ref](../../programming-guide/classes-and-structs/ref-returns.md) return 以傳址方式傳回方法結果。</span><span class="sxs-lookup"><span data-stu-id="b0d72-172">Use [ref returns](../../programming-guide/classes-and-structs/ref-returns.md) to return a method result by reference.</span></span> <span data-ttu-id="b0d72-173">如需詳細資訊，請參閱 [撰寫安全且有效率的 c # 程式碼](../../write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d72-173">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="ref-struct"></a><span data-ttu-id="b0d72-174">`ref` 結構</span><span class="sxs-lookup"><span data-stu-id="b0d72-174">`ref` struct</span></span>

<span data-ttu-id="b0d72-175">從 c # 7.2 開始，您可以 `ref` 在結構類型的宣告中使用修飾詞。</span><span class="sxs-lookup"><span data-stu-id="b0d72-175">Beginning with C# 7.2, you can use the `ref` modifier in the declaration of a structure type.</span></span> <span data-ttu-id="b0d72-176">`ref`結構類型的實例會在堆疊上配置，而且無法對 managed 堆積進行 escape。</span><span class="sxs-lookup"><span data-stu-id="b0d72-176">Instances of a `ref` struct type are allocated on the stack and can't escape to the managed heap.</span></span> <span data-ttu-id="b0d72-177">為了確保這一點，編譯器會限制結構類型的使用方式，如下所示 `ref` ：</span><span class="sxs-lookup"><span data-stu-id="b0d72-177">To ensure that, the compiler limits the usage of `ref` struct types as follows:</span></span>

- <span data-ttu-id="b0d72-178">`ref`結構不能是陣列的元素類型。</span><span class="sxs-lookup"><span data-stu-id="b0d72-178">A `ref` struct can't be the element type of an array.</span></span>
- <span data-ttu-id="b0d72-179">`ref`結構不能是類別或非結構之欄位的宣告型別 `ref` 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-179">A `ref` struct can't be a declared type of a field of a class or a non-`ref` struct.</span></span>
- <span data-ttu-id="b0d72-180">`ref`結構無法執行介面。</span><span class="sxs-lookup"><span data-stu-id="b0d72-180">A `ref` struct can't implement interfaces.</span></span>
- <span data-ttu-id="b0d72-181">`ref`結構不能封裝成 <xref:System.ValueType?displayProperty=nameWithType> 或 <xref:System.Object?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-181">A `ref` struct can't be boxed to <xref:System.ValueType?displayProperty=nameWithType> or <xref:System.Object?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="b0d72-182">`ref`結構不能是型別引數。</span><span class="sxs-lookup"><span data-stu-id="b0d72-182">A `ref` struct can't be a type argument.</span></span>
- <span data-ttu-id="b0d72-183">`ref` [Lambda 運算式](../operators/lambda-expressions.md)或[區域函數](../../programming-guide/classes-and-structs/local-functions.md)無法捕捉結構變數。</span><span class="sxs-lookup"><span data-stu-id="b0d72-183">A `ref` struct variable can't be captured by a [lambda expression](../operators/lambda-expressions.md) or a [local function](../../programming-guide/classes-and-structs/local-functions.md).</span></span>
- <span data-ttu-id="b0d72-184">`ref`結構變數不能用在方法中 [`async`](../keywords/async.md) 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-184">A `ref` struct variable can't be used in an [`async`](../keywords/async.md) method.</span></span> <span data-ttu-id="b0d72-185">不過，您可以 `ref` 在同步方法中使用結構變數，例如，在傳回或的 <xref:System.Threading.Tasks.Task> 中 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-185">However, you can use `ref` struct variables in synchronous methods, for example, in those that return <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="b0d72-186">`ref`結構變數不能用在[反覆運算](../../iterators.md)器中。</span><span class="sxs-lookup"><span data-stu-id="b0d72-186">A `ref` struct variable can't be used in [iterators](../../iterators.md).</span></span>

<span data-ttu-id="b0d72-187">一般來說， `ref` 當您需要也包含結構類型之資料成員的型別時，您會定義結構類型 `ref` ：</span><span class="sxs-lookup"><span data-stu-id="b0d72-187">Typically, you define a `ref` struct type when you need a type that also includes data members of `ref` struct types:</span></span>

[!code-csharp[ref struct](snippets/shared/StructType.cs#RefStruct)]

<span data-ttu-id="b0d72-188">若要將 `ref` 結構宣告為 [`readonly`](#readonly-struct) ，請 `readonly` 在類型宣告中結合和修飾詞， `ref` (修飾詞必須在修飾詞 `readonly` `ref`) 之前：</span><span class="sxs-lookup"><span data-stu-id="b0d72-188">To declare a `ref` struct as [`readonly`](#readonly-struct), combine the `readonly` and `ref` modifiers in the type declaration (the `readonly` modifier must come before the `ref` modifier):</span></span>

[!code-csharp[readonly ref struct](snippets/shared/StructType.cs#ReadonlyRef)]

<span data-ttu-id="b0d72-189">在 .NET 中，結構的範例 `ref` 包括 <xref:System.Span%601?displayProperty=nameWithType> 和 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-189">In .NET, examples of a `ref` struct are <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

## <a name="struct-constraint"></a><span data-ttu-id="b0d72-190">結構條件約束</span><span class="sxs-lookup"><span data-stu-id="b0d72-190">struct constraint</span></span>

<span data-ttu-id="b0d72-191">您也可以 `struct` 在[ `struct` 條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)中使用關鍵字，指定型別參數為不可為 null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="b0d72-191">You also use the `struct` keyword in the [`struct` constraint](../../programming-guide/generics/constraints-on-type-parameters.md) to specify that a type parameter is a non-nullable value type.</span></span> <span data-ttu-id="b0d72-192">結構和 [列舉](enum.md) 類型都符合 `struct` 條件約束。</span><span class="sxs-lookup"><span data-stu-id="b0d72-192">Both structure and [enumeration](enum.md) types satisfy the `struct` constraint.</span></span>

## <a name="conversions"></a><span data-ttu-id="b0d72-193">轉換</span><span class="sxs-lookup"><span data-stu-id="b0d72-193">Conversions</span></span>

<span data-ttu-id="b0d72-194">若為任何結構類型 ([ `ref` 結構](#ref-struct)類型除外) ，則會在和類型之間存在的[裝箱和取消](../../programming-guide/types/boxing-and-unboxing.md)加入轉換 <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b0d72-194">For any structure type (except [`ref` struct](#ref-struct) types), there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.ValueType?displayProperty=nameWithType> and <xref:System.Object?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="b0d72-195">結構類型和它所執行的任何介面之間，也有另外的裝箱和取消程式轉換。</span><span class="sxs-lookup"><span data-stu-id="b0d72-195">There exist also boxing and unboxing conversions between a structure type and any interface that it implements.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b0d72-196">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b0d72-196">C# language specification</span></span>

<span data-ttu-id="b0d72-197">如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[結構](~/_csharplang/spec/structs.md)一節。</span><span class="sxs-lookup"><span data-stu-id="b0d72-197">For more information, see the [Structs](~/_csharplang/spec/structs.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="b0d72-198">如需有關 c # 7.2 和更新版本中所引進之功能的詳細資訊，請參閱下列功能提案附注：</span><span class="sxs-lookup"><span data-stu-id="b0d72-198">For more information about features introduced in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="b0d72-199">Readonly 結構</span><span class="sxs-lookup"><span data-stu-id="b0d72-199">Readonly structs</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [<span data-ttu-id="b0d72-200">唯讀執行個體成員</span><span class="sxs-lookup"><span data-stu-id="b0d72-200">Readonly instance members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [<span data-ttu-id="b0d72-201">參考樣式類型的編譯時間安全性</span><span class="sxs-lookup"><span data-stu-id="b0d72-201">Compile-time safety for ref-like types</span></span>](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a><span data-ttu-id="b0d72-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0d72-202">See also</span></span>

- [<span data-ttu-id="b0d72-203">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="b0d72-203">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b0d72-204">設計指導方針-在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="b0d72-204">Design guidelines - Choosing between class and struct</span></span>](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [<span data-ttu-id="b0d72-205">設計指導方針-結構設計</span><span class="sxs-lookup"><span data-stu-id="b0d72-205">Design guidelines - Struct design</span></span>](../../../standard/design-guidelines/struct.md)
- [<span data-ttu-id="b0d72-206">類別和結構</span><span class="sxs-lookup"><span data-stu-id="b0d72-206">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
