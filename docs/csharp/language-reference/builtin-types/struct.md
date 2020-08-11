---
title: '結構類型-c # 參考'
ms.date: 04/21/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 515b8d9adc1359581625f0d822e254d2c1df3b58
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062492"
---
# <a name="structure-types-c-reference"></a><span data-ttu-id="1aa6d-102">結構類型 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="1aa6d-102">Structure types (C# reference)</span></span>

<span data-ttu-id="1aa6d-103">*結構型*別 (或*結構型*別) 是可以封裝資料和相關功能的實[值型](value-types.md)別。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-103">A *structure type* (or *struct type*) is a [value type](value-types.md) that can encapsulate data and related functionality.</span></span> <span data-ttu-id="1aa6d-104">您可以使用 `struct` 關鍵字來定義結構型別：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-104">You use the `struct` keyword to define a structure type:</span></span>

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

<span data-ttu-id="1aa6d-105">結構類型具有*值的語義*。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-105">Structure types have *value semantics*.</span></span> <span data-ttu-id="1aa6d-106">也就是說，結構類型的變數會包含類型的實例。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-106">That is, a variable of a structure type contains an instance of the type.</span></span> <span data-ttu-id="1aa6d-107">根據預設，變數值會在指派時複製、將引數傳遞至方法，並傳回方法結果。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-107">By default, variable values are copied on assignment, passing an argument to a method, and returning a method result.</span></span> <span data-ttu-id="1aa6d-108">在結構類型變數的情況下，會複製類型的實例。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-108">In the case of a structure-type variable, an instance of the type is copied.</span></span> <span data-ttu-id="1aa6d-109">如需詳細資訊，請參閱實[數值型別](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-109">For more information, see [Value types](value-types.md).</span></span>

<span data-ttu-id="1aa6d-110">一般來說，您會使用結構類型來設計以資料為中心的小型類型，以提供些許或無行為。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-110">Typically, you use structure types to design small data-centric types that provide little or no behavior.</span></span> <span data-ttu-id="1aa6d-111">例如，.NET 會使用結構類型來代表[整數](integral-numeric-types.md)和[實際](floating-point-numeric-types.md))  (的數位、[布林值](bool.md)、 [Unicode 字元](char.md)和[時間實例](xref:System.DateTime)。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-111">For example, .NET uses structure types to represent a number (both [integer](integral-numeric-types.md) and [real](floating-point-numeric-types.md)), a [Boolean value](bool.md), a [Unicode character](char.md), a [time instance](xref:System.DateTime).</span></span> <span data-ttu-id="1aa6d-112">如果您將焦點放在類型的行為，請考慮定義[類別](../keywords/class.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-112">If you're focused on the behavior of a type, consider defining a [class](../keywords/class.md).</span></span> <span data-ttu-id="1aa6d-113">類別類型具有*參考語義*。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-113">Class types have *reference semantics*.</span></span> <span data-ttu-id="1aa6d-114">也就是說，類別類型的變數包含類型實例的參考，而不是實例本身。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-114">That is, a variable of a class type contains a reference to an instance of the type, not the instance itself.</span></span>

<span data-ttu-id="1aa6d-115">因為結構類型具有值的語義，所以我們建議您定義*不可變*的結構類型。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-115">Because structure types have value semantics, we recommend you to define *immutable* structure types.</span></span>

## <a name="readonly-struct"></a><span data-ttu-id="1aa6d-116">`readonly`結構</span><span class="sxs-lookup"><span data-stu-id="1aa6d-116">`readonly` struct</span></span>

<span data-ttu-id="1aa6d-117">從 c # 7.2 開始，您可以使用 `readonly` 修飾詞來宣告結構類型是不可變的：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-117">Beginning with C# 7.2, you use the `readonly` modifier to declare that a structure type is immutable:</span></span>

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

<span data-ttu-id="1aa6d-118">結構的所有資料成員都 `readonly` 必須是唯讀的，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-118">All data members of a `readonly` struct must be read-only as follows:</span></span>

- <span data-ttu-id="1aa6d-119">任何欄位宣告都必須有[ `readonly` 修飾](../keywords/readonly.md)詞</span><span class="sxs-lookup"><span data-stu-id="1aa6d-119">Any field declaration must have the [`readonly` modifier](../keywords/readonly.md)</span></span>
- <span data-ttu-id="1aa6d-120">任何包含自動執行的屬性都必須是唯讀的</span><span class="sxs-lookup"><span data-stu-id="1aa6d-120">Any property, including auto-implemented ones, must be read-only</span></span>

<span data-ttu-id="1aa6d-121">這可保證結構的成員不會 `readonly` 修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-121">That guarantees that no member of a `readonly` struct modifies the state of the struct.</span></span>

> [!NOTE]
> <span data-ttu-id="1aa6d-122">在 `readonly` 結構中，可變參考型別的資料成員仍然可以改變其本身的狀態。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-122">In a `readonly` struct, a data member of a mutable reference type still can mutate its own state.</span></span> <span data-ttu-id="1aa6d-123">例如，您無法取代 <xref:System.Collections.Generic.List%601> 實例，但是您可以在其中加入新的元素。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-123">For example, you can't replace a <xref:System.Collections.Generic.List%601> instance, but you can add new elements to it.</span></span>

## <a name="readonly-instance-members"></a><span data-ttu-id="1aa6d-124">`readonly`實例成員</span><span class="sxs-lookup"><span data-stu-id="1aa6d-124">`readonly` instance members</span></span>

<span data-ttu-id="1aa6d-125">從 c # 8.0 開始，您也可以使用 `readonly` 修飾詞來宣告實例成員不會修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-125">Beginning with C# 8.0, you can also use the `readonly` modifier to declare that an instance member doesn't modify the state of a struct.</span></span> <span data-ttu-id="1aa6d-126">如果您無法將整個結構類型宣告為 `readonly` ，請使用 `readonly` 修飾詞來標記不會修改結構狀態的實例成員。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-126">If you can't declare the whole structure type as `readonly`, use the `readonly` modifier to mark the instance members that don't modify the state of the struct.</span></span> <span data-ttu-id="1aa6d-127">在 `readonly` 結構中，每個實例成員都是隱含的 `readonly` 。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-127">In a `readonly` struct, every instance member is implicitly `readonly`.</span></span>

<span data-ttu-id="1aa6d-128">在 `readonly` 實例成員內，您無法指派給結構的實例欄位。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-128">Within a `readonly` instance member, you can't assign to structure's instance fields.</span></span> <span data-ttu-id="1aa6d-129">不過， `readonly` 成員可以呼叫非 `readonly` 成員。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-129">However, a `readonly` member can call a non-`readonly` member.</span></span> <span data-ttu-id="1aa6d-130">在這種情況下，編譯器會建立結構實例的複本，並呼叫 `readonly` 該複本上的非成員。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-130">In that case the compiler creates a copy of the structure instance and calls the non-`readonly` member on that copy.</span></span> <span data-ttu-id="1aa6d-131">因此，不會修改原始的結構實例。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-131">As a result, the original structure instance is not modified.</span></span>

<span data-ttu-id="1aa6d-132">一般來說，您會將 `readonly` 修飾詞套用至下列類型的實例成員：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-132">Typically, you apply the `readonly` modifier to the following kinds of instance members:</span></span>

- <span data-ttu-id="1aa6d-133">方法</span><span class="sxs-lookup"><span data-stu-id="1aa6d-133">methods:</span></span>

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  <span data-ttu-id="1aa6d-134">您也可以將修飾詞套用 `readonly` 至覆寫中所宣告方法的方法 <xref:System.Object?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-134">You can also apply the `readonly` modifier to methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>:</span></span>

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- <span data-ttu-id="1aa6d-135">屬性和索引子：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-135">properties and indexers:</span></span>

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  <span data-ttu-id="1aa6d-136">如果您需要將修飾詞套用 `readonly` 至屬性或索引子的兩個存取子，請將它套用至屬性或索引子的宣告中。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-136">If you need to apply the `readonly` modifier to both accessors of a property or indexer, apply it in the declaration of the property or indexer.</span></span>

  > [!NOTE]
  > <span data-ttu-id="1aa6d-137">`get`不論屬性宣告中的修飾詞是否存在，編譯器都會將自動實作為[屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)的存取子宣告為 `readonly` `readonly` 。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-137">The compiler declares a `get` accessor of an [auto-implemented property](../../programming-guide/classes-and-structs/auto-implemented-properties.md) as `readonly`, regardless of presence of the `readonly` modifier in a property declaration.</span></span>

<span data-ttu-id="1aa6d-138">您無法將修飾詞套用 `readonly` 至結構類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-138">You can't apply the `readonly` modifier to static members of a structure type.</span></span>

<span data-ttu-id="1aa6d-139">編譯器可能會使用 `readonly` 修飾詞來進行效能優化。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-139">The compiler may make use of the `readonly` modifier for performance optimizations.</span></span> <span data-ttu-id="1aa6d-140">如需詳細資訊，請參閱[撰寫安全且有效率的 c # 程式碼](../../write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-140">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="limitations-with-the-design-of-a-structure-type"></a><span data-ttu-id="1aa6d-141">結構類型設計的限制</span><span class="sxs-lookup"><span data-stu-id="1aa6d-141">Limitations with the design of a structure type</span></span>

<span data-ttu-id="1aa6d-142">當您設計結構類型時，您具有與[類別](../keywords/class.md)類型相同的功能，但有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-142">When you design a structure type, you have the same capabilities as with a [class](../keywords/class.md) type, with the following exceptions:</span></span>

- <span data-ttu-id="1aa6d-143">您不能宣告無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-143">You can't declare a parameterless constructor.</span></span> <span data-ttu-id="1aa6d-144">每個結構類型已經提供隱含的無參數的函式，以產生類型的[預設值](default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-144">Every structure type already provides an implicit parameterless constructor that produces the [default value](default-values.md) of the type.</span></span>

- <span data-ttu-id="1aa6d-145">您無法在其宣告中初始化實例欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-145">You can't initialize an instance field or property at its declaration.</span></span> <span data-ttu-id="1aa6d-146">不過，您可以在其宣告中初始化[靜態](../keywords/static.md)或[常數](../keywords/const.md)欄位或靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-146">However, you can initialize a [static](../keywords/static.md) or [const](../keywords/const.md) field or a static property at its declaration.</span></span>

- <span data-ttu-id="1aa6d-147">結構類型的「構造函式」必須初始化該類型的所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-147">A constructor of a structure type must initialize all instance fields of the type.</span></span>

- <span data-ttu-id="1aa6d-148">結構型別無法繼承自其他類別或結構型別，而且它不能是類別的基底。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-148">A structure type can't inherit from other class or structure type and it can't be the base of a class.</span></span> <span data-ttu-id="1aa6d-149">不過，結構類型可以執行[介面](../keywords/interface.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-149">However, a structure type can implement [interfaces](../keywords/interface.md).</span></span>

- <span data-ttu-id="1aa6d-150">您[無法在結構類型中宣告](../../programming-guide/classes-and-structs/destructors.md)完成項。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-150">You can't declare a [finalizer](../../programming-guide/classes-and-structs/destructors.md) within a structure type.</span></span>

## <a name="instantiation-of-a-structure-type"></a><span data-ttu-id="1aa6d-151">結構類型的具現化</span><span class="sxs-lookup"><span data-stu-id="1aa6d-151">Instantiation of a structure type</span></span>

<span data-ttu-id="1aa6d-152">在 c # 中，您必須先初始化已宣告的變數，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-152">In C#, you must initialize a declared variable before it can be used.</span></span> <span data-ttu-id="1aa6d-153">因為結構類型變數無法 `null` (，除非它是[可為 null 的實數值型別](nullable-value-types.md)) 的變數，您必須具現化對應類型的實例。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-153">Because a structure-type variable can't be `null` (unless it's a variable of a [nullable value type](nullable-value-types.md)), you must instantiate an instance of the corresponding type.</span></span> <span data-ttu-id="1aa6d-154">有幾種方式可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-154">There are several ways to do that.</span></span>

<span data-ttu-id="1aa6d-155">通常，您會使用運算子來呼叫適當的處理常式，以具現化結構類型 [`new`](../operators/new-operator.md) 。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-155">Typically, you instantiate a structure type by calling an appropriate constructor with the [`new`](../operators/new-operator.md) operator.</span></span> <span data-ttu-id="1aa6d-156">每個結構類型都至少有一個函式。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-156">Every structure type has at least one constructor.</span></span> <span data-ttu-id="1aa6d-157">這是隱含的無參數的函式，它會產生類型的[預設值](default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-157">That's an implicit parameterless constructor, which produces the [default value](default-values.md) of the type.</span></span> <span data-ttu-id="1aa6d-158">您也可以使用[預設值運算式](../operators/default.md)來產生類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-158">You can also use a [default value expression](../operators/default.md) to produce the default value of a type.</span></span>

<span data-ttu-id="1aa6d-159">如果結構類型的所有實例欄位都可存取，您也可以在不使用運算子的情況下將它具現化 `new` 。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-159">If all instance fields of a structure type are accessible, you can also instantiate it without the `new` operator.</span></span> <span data-ttu-id="1aa6d-160">在此情況下，您必須在第一次使用實例之前，先初始化所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-160">In that case you must initialize all instance fields before the first use of the instance.</span></span> <span data-ttu-id="1aa6d-161">下列範例顯示如何執行該項工作：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-161">The following example shows how to do that:</span></span>

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

<span data-ttu-id="1aa6d-162">在內[建實數值型別](value-types.md#built-in-value-types)的情況下，請使用對應的常值來指定類型的值。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-162">In the case of the [built-in value types](value-types.md#built-in-value-types), use the corresponding literals to specify a value of the type.</span></span>

## <a name="passing-structure-type-variables-by-reference"></a><span data-ttu-id="1aa6d-163">以傳址方式傳遞結構型別變數</span><span class="sxs-lookup"><span data-stu-id="1aa6d-163">Passing structure-type variables by reference</span></span>

<span data-ttu-id="1aa6d-164">當您將結構型別變數當做引數傳遞至方法，或從方法傳回結構型別值時，會複製結構型別的整個實例。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-164">When you pass a structure-type variable to a method as an argument or return a structure-type value from a method, the whole instance of a structure type is copied.</span></span> <span data-ttu-id="1aa6d-165">這可能會影響您的程式碼在涉及大型結構類型的高效能案例中的效能。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-165">That can affect the performance of your code in high-performance scenarios that involve large structure types.</span></span> <span data-ttu-id="1aa6d-166">您可以透過傳址方式傳遞結構型別變數，以避免值複製。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-166">You can avoid value copying by passing a structure-type variable by reference.</span></span> <span data-ttu-id="1aa6d-167">使用 [`ref`](../keywords/ref.md#passing-an-argument-by-reference) 、 [`out`](../keywords/out-parameter-modifier.md) 或方法參數修飾詞， [`in`](../keywords/in-parameter-modifier.md) 表示必須以傳址方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-167">Use the [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md), or [`in`](../keywords/in-parameter-modifier.md) method parameter modifiers to indicate that an argument must be passed by reference.</span></span> <span data-ttu-id="1aa6d-168">使用[ref](../../programming-guide/classes-and-structs/ref-returns.md) return 傳回以傳址方式傳回的方法結果。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-168">Use [ref returns](../../programming-guide/classes-and-structs/ref-returns.md) to return a method result by reference.</span></span> <span data-ttu-id="1aa6d-169">如需詳細資訊，請參閱[撰寫安全且有效率的 c # 程式碼](../../write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-169">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="ref-struct"></a><span data-ttu-id="1aa6d-170">`ref`結構</span><span class="sxs-lookup"><span data-stu-id="1aa6d-170">`ref` struct</span></span>

<span data-ttu-id="1aa6d-171">從 c # 7.2 開始，您可以在 `ref` 結構類型的宣告中使用修飾詞。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-171">Beginning with C# 7.2, you can use the `ref` modifier in the declaration of a structure type.</span></span> <span data-ttu-id="1aa6d-172">`ref`結構型別的實例會配置於堆疊上，而且無法將其跳到 managed 堆積。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-172">Instances of a `ref` struct type are allocated on the stack and can't escape to the managed heap.</span></span> <span data-ttu-id="1aa6d-173">為確保，編譯器會限制結構類型的使用 `ref` 方式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-173">To ensure that, the compiler limits the usage of `ref` struct types as follows:</span></span>

- <span data-ttu-id="1aa6d-174">`ref`結構不可以是陣列的元素類型。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-174">A `ref` struct can't be the element type of an array.</span></span>
- <span data-ttu-id="1aa6d-175">`ref`結構不可以是類別或非結構之欄位的宣告型別 `ref` 。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-175">A `ref` struct can't be a declared type of a field of a class or a non-`ref` struct.</span></span>
- <span data-ttu-id="1aa6d-176">`ref`結構無法執行介面。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-176">A `ref` struct can't implement interfaces.</span></span>
- <span data-ttu-id="1aa6d-177">`ref`無法將結構封裝成 <xref:System.ValueType?displayProperty=nameWithType> 或 <xref:System.Object?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-177">A `ref` struct can't be boxed to <xref:System.ValueType?displayProperty=nameWithType> or <xref:System.Object?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="1aa6d-178">`ref`結構不可以是類型引數。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-178">A `ref` struct can't be a type argument.</span></span>
- <span data-ttu-id="1aa6d-179">`ref` [Lambda 運算式](../operators/lambda-expressions.md)或[區域函數](../../programming-guide/classes-and-structs/local-functions.md)無法捕捉結構變數。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-179">A `ref` struct variable can't be captured by a [lambda expression](../operators/lambda-expressions.md) or a [local function](../../programming-guide/classes-and-structs/local-functions.md).</span></span>
- <span data-ttu-id="1aa6d-180">`ref`結構變數不能用在方法中 [`async`](../keywords/async.md) 。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-180">A `ref` struct variable can't be used in an [`async`](../keywords/async.md) method.</span></span> <span data-ttu-id="1aa6d-181">不過，您可以在 `ref` 同步方法中使用結構變數，例如，在傳回或的情況下 <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-181">However, you can use `ref` struct variables in synchronous methods, for example, in those that return <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="1aa6d-182">`ref`Struct 變數不能用在[反覆運算](../../iterators.md)器中。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-182">A `ref` struct variable can't be used in [iterators](../../iterators.md).</span></span>

<span data-ttu-id="1aa6d-183">`ref`當您需要也包含結構類型之資料成員的類型時，通常會定義結構類型 `ref` ：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-183">Typically, you define a `ref` struct type when you need a type that also includes data members of `ref` struct types:</span></span>

[!code-csharp[ref struct](snippets/StructType.cs#RefStruct)]

<span data-ttu-id="1aa6d-184">若要將 `ref` 結構宣告為 [`readonly`](#readonly-struct) ，請 `readonly` 在類型宣告中結合和修飾詞， `ref` (修飾詞必須在修飾詞 `readonly` `ref`) 之前：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-184">To declare a `ref` struct as [`readonly`](#readonly-struct), combine the `readonly` and `ref` modifiers in the type declaration (the `readonly` modifier must come before the `ref` modifier):</span></span>

[!code-csharp[readonly ref struct](snippets/StructType.cs#ReadonlyRef)]

<span data-ttu-id="1aa6d-185">在 .NET 中，結構的範例 `ref` 是 <xref:System.Span%601?displayProperty=nameWithType> 和 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-185">In .NET, examples of a `ref` struct are <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

## <a name="conversions"></a><span data-ttu-id="1aa6d-186">轉換</span><span class="sxs-lookup"><span data-stu-id="1aa6d-186">Conversions</span></span>

<span data-ttu-id="1aa6d-187">針對任何結構類型 (除了[ `ref` 結構](#ref-struct)類型) 之外，還有在和類型之間進行的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換 <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-187">For any structure type (except [`ref` struct](#ref-struct) types), there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.ValueType?displayProperty=nameWithType> and <xref:System.Object?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="1aa6d-188">結構型別和它所執行的任何介面之間也有一個裝箱和取消裝箱轉換。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-188">There exist also boxing and unboxing conversions between a structure type and any interface that it implements.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1aa6d-189">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1aa6d-189">C# language specification</span></span>

<span data-ttu-id="1aa6d-190">如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[結構](~/_csharplang/spec/structs.md)一節。</span><span class="sxs-lookup"><span data-stu-id="1aa6d-190">For more information, see the [Structs](~/_csharplang/spec/structs.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="1aa6d-191">如需 c # 7.2 和更新版本中引進之功能的詳細資訊，請參閱下列功能建議事項：</span><span class="sxs-lookup"><span data-stu-id="1aa6d-191">For more information about features introduced in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="1aa6d-192">Readonly 結構</span><span class="sxs-lookup"><span data-stu-id="1aa6d-192">Readonly structs</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [<span data-ttu-id="1aa6d-193">唯讀執行個體成員</span><span class="sxs-lookup"><span data-stu-id="1aa6d-193">Readonly instance members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [<span data-ttu-id="1aa6d-194">參考樣式類型的編譯時間安全性</span><span class="sxs-lookup"><span data-stu-id="1aa6d-194">Compile-time safety for ref-like types</span></span>](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a><span data-ttu-id="1aa6d-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1aa6d-195">See also</span></span>

- [<span data-ttu-id="1aa6d-196">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="1aa6d-196">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1aa6d-197">設計方針-在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="1aa6d-197">Design guidelines - Choosing between class and struct</span></span>](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [<span data-ttu-id="1aa6d-198">設計方針-結構設計</span><span class="sxs-lookup"><span data-stu-id="1aa6d-198">Design guidelines - Struct design</span></span>](../../../standard/design-guidelines/struct.md)
- [<span data-ttu-id="1aa6d-199">類別和結構</span><span class="sxs-lookup"><span data-stu-id="1aa6d-199">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
