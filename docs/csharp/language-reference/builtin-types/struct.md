---
title: 結構類型 - C# 引用
ms.date: 04/21/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: dbe9b47625589de834b7a8021640885ca0920b96
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021264"
---
# <a name="structure-types-c-reference"></a><span data-ttu-id="0ef61-102">結構類型(C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0ef61-102">Structure types (C# reference)</span></span>

<span data-ttu-id="0ef61-103">*結構類型*(或*結構型態*)是一種可以封裝資料和相關功能[的值類型](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-103">A *structure type* (or *struct type*) is a [value type](value-types.md) that can encapsulate data and related functionality.</span></span> <span data-ttu-id="0ef61-104">使用 關鍵`struct`字 定義結構類型:</span><span class="sxs-lookup"><span data-stu-id="0ef61-104">You use the `struct` keyword to define a structure type:</span></span>

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

<span data-ttu-id="0ef61-105">結構類型具有*值語意*。</span><span class="sxs-lookup"><span data-stu-id="0ef61-105">Structure types have *value semantics*.</span></span> <span data-ttu-id="0ef61-106">也就是說,結構類型的變數包含類型的實例。</span><span class="sxs-lookup"><span data-stu-id="0ef61-106">That is, a variable of a structure type contains an instance of the type.</span></span> <span data-ttu-id="0ef61-107">默認情況下,在賦值時複製變數值,將參數傳遞給方法,並返回方法結果。</span><span class="sxs-lookup"><span data-stu-id="0ef61-107">By default, variable values are copied on assignment, passing an argument to a method, and returning a method result.</span></span> <span data-ttu-id="0ef61-108">對於結構類型變數,將複製類型的實例。</span><span class="sxs-lookup"><span data-stu-id="0ef61-108">In the case of a structure-type variable, an instance of the type is copied.</span></span> <span data-ttu-id="0ef61-109">有關詳細資訊,請參考[值類型](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-109">For more information, see [Value types](value-types.md).</span></span>

<span data-ttu-id="0ef61-110">通常,使用結構類型來設計提供很少或沒有行為的小型以數據為中心的類型。</span><span class="sxs-lookup"><span data-stu-id="0ef61-110">Typically, you use structure types to design small data-centric types that provide little or no behavior.</span></span> <span data-ttu-id="0ef61-111">例如,.NET 使用結構類型來表示數位([整數](integral-numeric-types.md)與[實體 )](floating-point-numeric-types.md),[布林值](bool.md)[, Unicode 字元](char.md),[時間實例](xref:System.DateTime)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-111">For example, .NET uses structure types to represent a number (both [integer](integral-numeric-types.md) and [real](floating-point-numeric-types.md)), a [Boolean value](bool.md), a [Unicode character](char.md), a [time instance](xref:System.DateTime).</span></span> <span data-ttu-id="0ef61-112">如果您專注於類型的行為,請考慮定義[類別](../keywords/class.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-112">If you're focused on the behavior of a type, consider defining a [class](../keywords/class.md).</span></span> <span data-ttu-id="0ef61-113">類別類型具有*引言語意*。</span><span class="sxs-lookup"><span data-stu-id="0ef61-113">Class types have *reference semantics*.</span></span> <span data-ttu-id="0ef61-114">也就是說,類類型的變數包含對類型實例的引用,而不是實例本身。</span><span class="sxs-lookup"><span data-stu-id="0ef61-114">That is, a variable of a class type contains a reference to an instance of the type, not the instance itself.</span></span>

<span data-ttu-id="0ef61-115">由於結構類型具有值語義,因此我們建議您定義*不可變*結構類型。</span><span class="sxs-lookup"><span data-stu-id="0ef61-115">Because structure types have value semantics, we recommend you to define *immutable* structure types.</span></span>

## <a name="readonly-struct"></a><span data-ttu-id="0ef61-116">`readonly`結構</span><span class="sxs-lookup"><span data-stu-id="0ef61-116">`readonly` struct</span></span>

<span data-ttu-id="0ef61-117">從 C# 7.2`readonly`開始, 使用修飾符聲明結構類型不可變:</span><span class="sxs-lookup"><span data-stu-id="0ef61-117">Beginning with C# 7.2, you use the `readonly` modifier to declare that a structure type is immutable:</span></span>

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

<span data-ttu-id="0ef61-118">`readonly`結構的所有資料成員必須唯讀如下:</span><span class="sxs-lookup"><span data-stu-id="0ef61-118">All data members of a `readonly` struct must be read-only as follows:</span></span>

- <span data-ttu-id="0ef61-119">任何欄位聲明必須具有[`readonly`變更器](../keywords/readonly.md)</span><span class="sxs-lookup"><span data-stu-id="0ef61-119">Any field declaration must have the [`readonly` modifier](../keywords/readonly.md)</span></span>
- <span data-ttu-id="0ef61-120">任何屬性(包括自動實作的屬性)都必須是唯讀的</span><span class="sxs-lookup"><span data-stu-id="0ef61-120">Any property, including auto-implemented ones, must be read-only</span></span>

<span data-ttu-id="0ef61-121">這保證了`readonly`結構的成員不會修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="0ef61-121">That guarantees that no member of a `readonly` struct modifies the state of the struct.</span></span>

> [!NOTE]
> <span data-ttu-id="0ef61-122">在`readonly`結構中,可變引用類型的數據成員仍然可以更改其自己的狀態。</span><span class="sxs-lookup"><span data-stu-id="0ef61-122">In a `readonly` struct, a data member of a mutable reference type still can mutate its own state.</span></span> <span data-ttu-id="0ef61-123">例如,不能替換<xref:System.Collections.Generic.List%601>實例,但可以向實例添加新元素。</span><span class="sxs-lookup"><span data-stu-id="0ef61-123">For example, you can't replace a <xref:System.Collections.Generic.List%601> instance, but you can add new elements to it.</span></span>

## <a name="readonly-instance-members"></a><span data-ttu-id="0ef61-124">`readonly`實體成員</span><span class="sxs-lookup"><span data-stu-id="0ef61-124">`readonly` instance members</span></span>

<span data-ttu-id="0ef61-125">從 C# 8.0 開始`readonly`,還可以使用 修改器聲明實例成員不修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="0ef61-125">Beginning with C# 8.0, you can also use the `readonly` modifier to declare that an instance member doesn't modify the state of a struct.</span></span> <span data-ttu-id="0ef61-126">如果無法將整個結構類型聲明為`readonly`,請`readonly`使用 修改器標記不修改結構狀態的實例成員。</span><span class="sxs-lookup"><span data-stu-id="0ef61-126">If you can't declare the whole structure type as `readonly`, use the `readonly` modifier to mark the instance members that don't modify the state of the struct.</span></span> <span data-ttu-id="0ef61-127">在`readonly`結構中,每個實例成員都是隱式`readonly`的。</span><span class="sxs-lookup"><span data-stu-id="0ef61-127">In a `readonly` struct, every instance member is implicitly `readonly`.</span></span>

<span data-ttu-id="0ef61-128">在`readonly`實例成員中,不能分配給結構的實例欄位。</span><span class="sxs-lookup"><span data-stu-id="0ef61-128">Within a `readonly` instance member, you can't assign to structure's instance fields.</span></span> <span data-ttu-id="0ef61-129">但是,成員`readonly`可以調用非`readonly`成員。</span><span class="sxs-lookup"><span data-stu-id="0ef61-129">However, a `readonly` member can call a non-`readonly` member.</span></span> <span data-ttu-id="0ef61-130">在這種情況下,編譯器將創建結構實例的副本,並調用該副本上的非`readonly`成員。</span><span class="sxs-lookup"><span data-stu-id="0ef61-130">In that case the compiler creates a copy of the structure instance and calls the non-`readonly` member on that copy.</span></span> <span data-ttu-id="0ef61-131">因此,不會修改原始結構實例。</span><span class="sxs-lookup"><span data-stu-id="0ef61-131">As a result, the original structure instance is not modified.</span></span>

<span data-ttu-id="0ef61-132">通常,您將`readonly`修改器應用於以下類型的實體成員:</span><span class="sxs-lookup"><span data-stu-id="0ef61-132">Typically, you apply the `readonly` modifier to the following kinds of instance members:</span></span>

- <span data-ttu-id="0ef61-133">方法:</span><span class="sxs-lookup"><span data-stu-id="0ef61-133">methods:</span></span>

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  <span data-ttu-id="0ef61-134">還可以將`readonly`修改器應用於重寫<xref:System.Object?displayProperty=nameWithType>在 中 聲明的方法的方法:</span><span class="sxs-lookup"><span data-stu-id="0ef61-134">You can also apply the `readonly` modifier to methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>:</span></span>

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- <span data-ttu-id="0ef61-135">屬性與索引器:</span><span class="sxs-lookup"><span data-stu-id="0ef61-135">properties and indexers:</span></span>

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  <span data-ttu-id="0ef61-136">如果需要將`readonly`修改器應用於屬性或索引器的兩個訪問器,請將其應用於屬性或索引器的聲明。</span><span class="sxs-lookup"><span data-stu-id="0ef61-136">If you need to apply the `readonly` modifier to both accessors of a property or indexer, apply it in the declaration of the property or indexer.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0ef61-137">`get`編譯器聲明[自動實現屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)的訪問`readonly`許可權為`readonly`,而不考慮 屬性聲明中修飾符的存在。</span><span class="sxs-lookup"><span data-stu-id="0ef61-137">The compiler declares a `get` accessor of an [auto-implemented property](../../programming-guide/classes-and-structs/auto-implemented-properties.md) as `readonly`, regardless of presence of the `readonly` modifier in a property declaration.</span></span>

<span data-ttu-id="0ef61-138">不能將`readonly`修改器應用於結構類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="0ef61-138">You can't apply the `readonly` modifier to static members of a structure type.</span></span>

<span data-ttu-id="0ef61-139">編譯器可以使用`readonly`修改器進行性能優化。</span><span class="sxs-lookup"><span data-stu-id="0ef61-139">The compiler may make use of the `readonly` modifier for performance optimizations.</span></span> <span data-ttu-id="0ef61-140">有關詳細資訊,請參閱[編寫安全高效的 C# 代碼](../../write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-140">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="limitations-with-the-design-of-a-structure-type"></a><span data-ttu-id="0ef61-141">結構類型設計的限制</span><span class="sxs-lookup"><span data-stu-id="0ef61-141">Limitations with the design of a structure type</span></span>

<span data-ttu-id="0ef61-142">設計結構類型時,具有與[類](../keywords/class.md)類型相同的功能,但以下情況除外:</span><span class="sxs-lookup"><span data-stu-id="0ef61-142">When you design a structure type, you have the same capabilities as with a [class](../keywords/class.md) type, with the following exceptions:</span></span>

- <span data-ttu-id="0ef61-143">不能聲明無參數構造函數。</span><span class="sxs-lookup"><span data-stu-id="0ef61-143">You can't declare a parameterless constructor.</span></span> <span data-ttu-id="0ef61-144">每個結構類型都已提供一個隱式無參數建構函數,該建構函數產生類型的[預設值](default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-144">Every structure type already provides an implicit parameterless constructor that produces the [default value](default-values.md) of the type.</span></span>

- <span data-ttu-id="0ef61-145">不能在其聲明中初始化實例欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="0ef61-145">You can't initialize an instance field or property at its declaration.</span></span> <span data-ttu-id="0ef61-146">但是,您可以在其聲明上初始化[靜態](../keywords/static.md)或[const](../keywords/const.md)欄位或靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="0ef61-146">However, you can initialize a [static](../keywords/static.md) or [const](../keywords/const.md) field or a static property at its declaration.</span></span>

- <span data-ttu-id="0ef61-147">結構類型的構造函數必須初始化類型的所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="0ef61-147">A constructor of a structure type must initialize all instance fields of the type.</span></span>

- <span data-ttu-id="0ef61-148">結構類型不能從其他類或結構類型繼承,也不能是類的基礎。</span><span class="sxs-lookup"><span data-stu-id="0ef61-148">A structure type can't inherit from other class or structure type and it can't be the base of a class.</span></span> <span data-ttu-id="0ef61-149">但是,結構類型可以實現[介面](../keywords/interface.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-149">However, a structure type can implement [interfaces](../keywords/interface.md).</span></span>

- <span data-ttu-id="0ef61-150">無法在結構型態中宣告[終結器](../../programming-guide/classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-150">You can't declare a [finalizer](../../programming-guide/classes-and-structs/destructors.md) within a structure type.</span></span>

## <a name="instantiation-of-a-structure-type"></a><span data-ttu-id="0ef61-151">結構類型的實體化</span><span class="sxs-lookup"><span data-stu-id="0ef61-151">Instantiation of a structure type</span></span>

<span data-ttu-id="0ef61-152">在 C# 中,必須先初始化聲明變數,然後才能使用它。</span><span class="sxs-lookup"><span data-stu-id="0ef61-152">In C#, you must initialize a declared variable before it can be used.</span></span> <span data-ttu-id="0ef61-153">因為結構類型的變數不能`null`(除非它是可 null[值類型的](nullable-value-types.md)變數),因此必須實例化相應類型的實例。</span><span class="sxs-lookup"><span data-stu-id="0ef61-153">Because a structure-type variable can't be `null` (unless it's a variable of a [nullable value type](nullable-value-types.md)), you must instantiate an instance of the corresponding type.</span></span> <span data-ttu-id="0ef61-154">有幾種方法可以做到這一點。</span><span class="sxs-lookup"><span data-stu-id="0ef61-154">There are several ways to do that.</span></span>

<span data-ttu-id="0ef61-155">通常,通過使用運算符調用適當的構造函數來[`new`](../operators/new-operator.md)實例化結構類型。</span><span class="sxs-lookup"><span data-stu-id="0ef61-155">Typically, you instantiate a structure type by calling an appropriate constructor with the [`new`](../operators/new-operator.md) operator.</span></span> <span data-ttu-id="0ef61-156">每個結構類型至少有一個構造函數。</span><span class="sxs-lookup"><span data-stu-id="0ef61-156">Every structure type has at least one constructor.</span></span> <span data-ttu-id="0ef61-157">這是一個隱式無參數建構函數,它產生類型的[預設值](default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-157">That's an implicit parameterless constructor, which produces the [default value](default-values.md) of the type.</span></span> <span data-ttu-id="0ef61-158">您還可以使用[預設值運算式](../operators/default.md)生成類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="0ef61-158">You can also use a [default value expression](../operators/default.md) to produce the default value of a type.</span></span>

<span data-ttu-id="0ef61-159">如果結構類型的所有實例欄位都可訪問,也可以在沒有`new`運算元的情況下實例化它。</span><span class="sxs-lookup"><span data-stu-id="0ef61-159">If all instance fields of a structure type are accessible, you can also instantiate it without the `new` operator.</span></span> <span data-ttu-id="0ef61-160">在這種情況下,您必須在首次使用實例之前初始化所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="0ef61-160">In that case you must initialize all instance fields before the first use of the instance.</span></span> <span data-ttu-id="0ef61-161">下列範例顯示如何執行該項工作：</span><span class="sxs-lookup"><span data-stu-id="0ef61-161">The following example shows how to do that:</span></span>

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

<span data-ttu-id="0ef61-162">在[內建值類型](value-types.md#built-in-value-types)的情況下,使用相應的文本指定類型的值。</span><span class="sxs-lookup"><span data-stu-id="0ef61-162">In the case of the [built-in value types](value-types.md#built-in-value-types), use the corresponding literals to specify a value of the type.</span></span>

## <a name="passing-structure-type-variables-by-reference"></a><span data-ttu-id="0ef61-163">透過參考傳遞結構型態變數</span><span class="sxs-lookup"><span data-stu-id="0ef61-163">Passing structure-type variables by reference</span></span>

<span data-ttu-id="0ef61-164">將結構類型變數作為參數傳遞給方法或從方法返回結構類型值時,將複製結構類型的整個實例。</span><span class="sxs-lookup"><span data-stu-id="0ef61-164">When you pass a structure-type variable to a method as an argument or return a structure-type value from a method, the whole instance of a structure type is copied.</span></span> <span data-ttu-id="0ef61-165">這可能會影響代碼在涉及大型結構類型的高性能方案中的性能。</span><span class="sxs-lookup"><span data-stu-id="0ef61-165">That can affect the performance of your code in high-performance scenarios that involve large structure types.</span></span> <span data-ttu-id="0ef61-166">可以通過引用傳遞結構類型變數來避免值複製。</span><span class="sxs-lookup"><span data-stu-id="0ef61-166">You can avoid value copying by passing a structure-type variable by reference.</span></span> <span data-ttu-id="0ef61-167">使用[`ref`](../keywords/ref.md#passing-an-argument-by-reference)、[`out`](../keywords/out-parameter-modifier.md)[`in`](../keywords/in-parameter-modifier.md)或方法參數修改器指示必須透過引用傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="0ef61-167">Use the [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md), or [`in`](../keywords/in-parameter-modifier.md) method parameter modifiers to indicate that an argument must be passed by reference.</span></span> <span data-ttu-id="0ef61-168">使用[ref 返回](../../programming-guide/classes-and-structs/ref-returns.md)通過引用返回方法結果。</span><span class="sxs-lookup"><span data-stu-id="0ef61-168">Use [ref returns](../../programming-guide/classes-and-structs/ref-returns.md) to return a method result by reference.</span></span> <span data-ttu-id="0ef61-169">有關詳細資訊,請參閱[編寫安全高效的 C# 代碼](../../write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-169">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="ref-struct"></a><span data-ttu-id="0ef61-170">`ref`結構</span><span class="sxs-lookup"><span data-stu-id="0ef61-170">`ref` struct</span></span>

<span data-ttu-id="0ef61-171">從 C# 7.2 開始`ref`,您可以在 結構類型的聲明中使用修飾符。</span><span class="sxs-lookup"><span data-stu-id="0ef61-171">Beginning with C# 7.2, you can use the `ref` modifier in the declaration of a structure type.</span></span> <span data-ttu-id="0ef61-172">`ref`結構類型的實例在堆疊上分配,無法轉義到託管堆。</span><span class="sxs-lookup"><span data-stu-id="0ef61-172">Instances of a `ref` struct type are allocated on the stack and can't escape to the managed heap.</span></span> <span data-ttu-id="0ef61-173">為確保,編譯器限制`ref`結構類型的使用,如下所示:</span><span class="sxs-lookup"><span data-stu-id="0ef61-173">To ensure that, the compiler limits the usage of `ref` struct types as follows:</span></span>

- <span data-ttu-id="0ef61-174">`ref`結構不能是陣列的元素類型。</span><span class="sxs-lookup"><span data-stu-id="0ef61-174">A `ref` struct can't be the element type of an array.</span></span>
- <span data-ttu-id="0ef61-175">`ref`結構不能是類或非`ref`結構欄位的已聲明類型。</span><span class="sxs-lookup"><span data-stu-id="0ef61-175">A `ref` struct can't be a declared type of a field of a class or a non-`ref` struct.</span></span>
- <span data-ttu-id="0ef61-176">`ref`結構不能實現介面。</span><span class="sxs-lookup"><span data-stu-id="0ef61-176">A `ref` struct can't implement interfaces.</span></span>
- <span data-ttu-id="0ef61-177">`ref`結構不能載入到<xref:System.ValueType?displayProperty=nameWithType>或<xref:System.Object?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0ef61-177">A `ref` struct can't be boxed to <xref:System.ValueType?displayProperty=nameWithType> or <xref:System.Object?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="0ef61-178">`ref`結構不能是類型參數。</span><span class="sxs-lookup"><span data-stu-id="0ef61-178">A `ref` struct can't be a type argument.</span></span>
- <span data-ttu-id="0ef61-179">`ref` [lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)或[局部函數](../../programming-guide/classes-and-structs/local-functions.md)無法捕獲結構變數。</span><span class="sxs-lookup"><span data-stu-id="0ef61-179">A `ref` struct variable can't be captured by a [lambda expression](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or a [local function](../../programming-guide/classes-and-structs/local-functions.md).</span></span>
- <span data-ttu-id="0ef61-180">`ref`結構變數不能在[`async`](../keywords/async.md)方法中使用。</span><span class="sxs-lookup"><span data-stu-id="0ef61-180">A `ref` struct variable can't be used in an [`async`](../keywords/async.md) method.</span></span> <span data-ttu-id="0ef61-181">但是,您可以在同步方法`ref`中使用結構變數,例如,在返回<xref:System.Threading.Tasks.Task>或<xref:System.Threading.Tasks.Task%601>中。</span><span class="sxs-lookup"><span data-stu-id="0ef61-181">However, you can use `ref` struct variables in synchronous methods, for example, in those that return <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="0ef61-182">`ref`結構變數不能用於[發上層器](../../iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef61-182">A `ref` struct variable can't be used in [iterators](../../iterators.md).</span></span>

<span data-ttu-id="0ef61-183">通常,當您需要一`ref`種類型時,定義`ref`結構類型,該類型還包括結構類型的資料成員:</span><span class="sxs-lookup"><span data-stu-id="0ef61-183">Typically, you define a `ref` struct type when you need a type that also includes data members of `ref` struct types:</span></span>

[!code-csharp[ref struct](snippets/StructType.cs#RefStruct)]

<span data-ttu-id="0ef61-184">`ref`要將結構聲明為[`readonly`](#readonly-struct),在類型聲明`readonly`中`ref`組合 與修`readonly`飾符(`ref`修改符必須位於 修改器之前):</span><span class="sxs-lookup"><span data-stu-id="0ef61-184">To declare a `ref` struct as [`readonly`](#readonly-struct), combine the `readonly` and `ref` modifiers in the type declaration (the `readonly` modifier must come before the `ref` modifier):</span></span>

[!code-csharp[readonly ref struct](snippets/StructType.cs#ReadonlyRef)]

<span data-ttu-id="0ef61-185">在 .NET`ref`中, 結構的<xref:System.Span%601?displayProperty=nameWithType>範<xref:System.ReadOnlySpan%601?displayProperty=nameWithType>例是與 。</span><span class="sxs-lookup"><span data-stu-id="0ef61-185">In .NET, examples of a `ref` struct are <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

## <a name="conversions"></a><span data-ttu-id="0ef61-186">轉換</span><span class="sxs-lookup"><span data-stu-id="0ef61-186">Conversions</span></span>

<span data-ttu-id="0ef61-187">對於任何結構類型([`ref`結構](#ref-struct)類型除外),存在<xref:System.ValueType?displayProperty=nameWithType><xref:System.Object?displayProperty=nameWithType>與和 類型轉換的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換。</span><span class="sxs-lookup"><span data-stu-id="0ef61-187">For any structure type (except [`ref` struct](#ref-struct) types), there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.ValueType?displayProperty=nameWithType> and <xref:System.Object?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="0ef61-188">結構類型和它實現的任何介面之間也存在裝箱和取消裝箱轉換。</span><span class="sxs-lookup"><span data-stu-id="0ef61-188">There exist also boxing and unboxing conversions between a structure type and any interface that it implements.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0ef61-189">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0ef61-189">C# language specification</span></span>

<span data-ttu-id="0ef61-190">有關詳細資訊,請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[「結構」](~/_csharplang/spec/structs.md)部分。</span><span class="sxs-lookup"><span data-stu-id="0ef61-190">For more information, see the [Structs](~/_csharplang/spec/structs.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="0ef61-191">有關 C# 7.2 及更高版本中引入的功能的詳細資訊,請參閱以下功能建議說明:</span><span class="sxs-lookup"><span data-stu-id="0ef61-191">For more information about features introduced in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="0ef61-192">唯讀結構</span><span class="sxs-lookup"><span data-stu-id="0ef61-192">Readonly structs</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [<span data-ttu-id="0ef61-193">唯讀執行個體成員</span><span class="sxs-lookup"><span data-stu-id="0ef61-193">Readonly instance members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [<span data-ttu-id="0ef61-194">參考樣式類型的編譯時間安全性</span><span class="sxs-lookup"><span data-stu-id="0ef61-194">Compile-time safety for ref-like types</span></span>](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a><span data-ttu-id="0ef61-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ef61-195">See also</span></span>

- [<span data-ttu-id="0ef61-196">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0ef61-196">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0ef61-197">設計指南 ─ 在類別和結構之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="0ef61-197">Design guidelines - Choosing between class and struct</span></span>](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [<span data-ttu-id="0ef61-198">設計指南 - 結構設計</span><span class="sxs-lookup"><span data-stu-id="0ef61-198">Design guidelines - Struct design</span></span>](../../../standard/design-guidelines/struct.md)
- [<span data-ttu-id="0ef61-199">類別和結構</span><span class="sxs-lookup"><span data-stu-id="0ef61-199">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
