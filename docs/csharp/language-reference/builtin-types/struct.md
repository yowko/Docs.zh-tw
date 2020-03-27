---
title: 結構類型 - C# 引用
ms.date: 03/26/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 6a2c97b93a8f6d1d62bd8a96865a4fe6587f55d3
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345137"
---
# <a name="structure-types-c-reference"></a><span data-ttu-id="d612c-102">結構類型（C# 參考）</span><span class="sxs-lookup"><span data-stu-id="d612c-102">Structure types (C# reference)</span></span>

<span data-ttu-id="d612c-103">*結構類型*（或*結構類型*）是一種可以封裝資料和相關功能[的數值型別](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d612c-103">A *structure type* (or *struct type*) is a [value type](value-types.md) that can encapsulate data and related functionality.</span></span> <span data-ttu-id="d612c-104">使用 關鍵字`struct`定義結構類型：</span><span class="sxs-lookup"><span data-stu-id="d612c-104">You use the `struct` keyword to define a structure type:</span></span>

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

<span data-ttu-id="d612c-105">結構類型具有*值語義*。</span><span class="sxs-lookup"><span data-stu-id="d612c-105">Structure types have *value semantics*.</span></span> <span data-ttu-id="d612c-106">也就是說，結構類型的變數包含類型的實例。</span><span class="sxs-lookup"><span data-stu-id="d612c-106">That is, a variable of a structure type contains an instance of the type.</span></span> <span data-ttu-id="d612c-107">預設情況下，在賦值時複製變數值，將參數傳遞給方法，並返回方法結果。</span><span class="sxs-lookup"><span data-stu-id="d612c-107">By default, variable values are copied on assignment, passing an argument to a method, and returning a method result.</span></span> <span data-ttu-id="d612c-108">對於結構類型變數，將複製類型的實例。</span><span class="sxs-lookup"><span data-stu-id="d612c-108">In the case of a structure-type variable, an instance of the type is copied.</span></span> <span data-ttu-id="d612c-109">有關詳細資訊，請參閱[數值型別](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d612c-109">For more information, see [Value types](value-types.md).</span></span>

<span data-ttu-id="d612c-110">通常，使用結構類型來設計提供很少或沒有行為的小型以資料為中心的類型。</span><span class="sxs-lookup"><span data-stu-id="d612c-110">Typically, you use structure types to design small data-centric types that provide little or no behavior.</span></span> <span data-ttu-id="d612c-111">例如，.NET 使用結構類型來表示數位（[整數](integral-numeric-types.md)和[實數](floating-point-numeric-types.md)）、[布林值](bool.md)[、Unicode 字元](char.md)、[時間實例](xref:System.DateTime)。</span><span class="sxs-lookup"><span data-stu-id="d612c-111">For example, .NET uses structure types to represent a number (both [integer](integral-numeric-types.md) and [real](floating-point-numeric-types.md)), a [Boolean value](bool.md), a [Unicode character](char.md), a [time instance](xref:System.DateTime).</span></span> <span data-ttu-id="d612c-112">如果您專注于類型的行為，請考慮定義[類](../keywords/class.md)。</span><span class="sxs-lookup"><span data-stu-id="d612c-112">If you're focused on the behavior of a type, consider defining a [class](../keywords/class.md).</span></span> <span data-ttu-id="d612c-113">類類型具有*引用語義*。</span><span class="sxs-lookup"><span data-stu-id="d612c-113">Class types have *reference semantics*.</span></span> <span data-ttu-id="d612c-114">也就是說，類類型的變數包含對類型實例的引用，而不是實例本身。</span><span class="sxs-lookup"><span data-stu-id="d612c-114">That is, a variable of a class type contains a reference to an instance of the type, not the instance itself.</span></span>

<span data-ttu-id="d612c-115">由於結構類型具有值語義，因此我們建議您定義*不可變*結構類型。</span><span class="sxs-lookup"><span data-stu-id="d612c-115">Because structure types have value semantics, we recommend you to define *immutable* structure types.</span></span>

## <a name="readonly-struct"></a><span data-ttu-id="d612c-116">`readonly`結構</span><span class="sxs-lookup"><span data-stu-id="d612c-116">`readonly` struct</span></span>

<span data-ttu-id="d612c-117">從 C# 7.2 開始，`readonly`使用修飾符聲明結構類型不可變：</span><span class="sxs-lookup"><span data-stu-id="d612c-117">Beginning with C# 7.2, you use the `readonly` modifier to declare that a structure type is immutable:</span></span>

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

<span data-ttu-id="d612c-118">`readonly`結構的所有資料成員必須唯讀如下：</span><span class="sxs-lookup"><span data-stu-id="d612c-118">All data members of a `readonly` struct must be read-only as follows:</span></span>

- <span data-ttu-id="d612c-119">任何欄位聲明都必須具有[`readonly`修改器](../keywords/readonly.md)</span><span class="sxs-lookup"><span data-stu-id="d612c-119">Any field declaration must have the [`readonly` modifier](../keywords/readonly.md)</span></span>
- <span data-ttu-id="d612c-120">任何屬性（包括自動實現的屬性）都必須是唯讀的</span><span class="sxs-lookup"><span data-stu-id="d612c-120">Any property, including auto-implemented ones, must be read-only</span></span>

<span data-ttu-id="d612c-121">這保證了`readonly`結構的成員不會修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="d612c-121">That guarantees that no member of a `readonly` struct modifies the state of the struct.</span></span>

> [!NOTE]
> <span data-ttu-id="d612c-122">在`readonly`結構中，可變參考型別的資料成員仍然可以更改其自己的狀態。</span><span class="sxs-lookup"><span data-stu-id="d612c-122">In a `readonly` struct, a data member of a mutable reference type still can mutate its own state.</span></span> <span data-ttu-id="d612c-123">例如，不能替換<xref:System.Collections.Generic.List%601>實例，但可以向實例添加新元素。</span><span class="sxs-lookup"><span data-stu-id="d612c-123">For example, you cannot replace a <xref:System.Collections.Generic.List%601> instance, but you can add new elements to it.</span></span>

## <a name="limitations-with-the-design-of-a-structure-type"></a><span data-ttu-id="d612c-124">結構類型設計的限制</span><span class="sxs-lookup"><span data-stu-id="d612c-124">Limitations with the design of a structure type</span></span>

<span data-ttu-id="d612c-125">設計結構類型時，具有與[類](../keywords/class.md)類型相同的功能，但以下情況除外：</span><span class="sxs-lookup"><span data-stu-id="d612c-125">When you design a structure type, you have the same capabilities as with a [class](../keywords/class.md) type, with the following exceptions:</span></span>

- <span data-ttu-id="d612c-126">不能聲明無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="d612c-126">You cannot declare a parameterless constructor.</span></span> <span data-ttu-id="d612c-127">每個結構類型都已提供一個隱式無參數建構函式，該建構函式組建類型的[預設值](default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="d612c-127">Every structure type already provides an implicit parameterless constructor that produces the [default value](default-values.md) of the type.</span></span>

- <span data-ttu-id="d612c-128">不能在其聲明上初始化實例欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="d612c-128">You cannot initialize an instance field or property at its declaration.</span></span> <span data-ttu-id="d612c-129">但是，您可以在其聲明上初始化[靜態](../keywords/static.md)或[const](../keywords/const.md)欄位或靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="d612c-129">However, you can initialize a [static](../keywords/static.md) or [const](../keywords/const.md) field or a static property at its declaration.</span></span>

- <span data-ttu-id="d612c-130">結構類型的建構函式必須初始化類型的所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="d612c-130">A constructor of a structure type must initialize all instance fields of the type.</span></span>

- <span data-ttu-id="d612c-131">結構類型不能從其他類或結構類型繼承，也不能是類的基礎。</span><span class="sxs-lookup"><span data-stu-id="d612c-131">A structure type cannot inherit from other class or structure type and it cannot be the base of a class.</span></span> <span data-ttu-id="d612c-132">但是，結構類型可以實現[介面](../keywords/interface.md)。</span><span class="sxs-lookup"><span data-stu-id="d612c-132">However, a structure type can implement [interfaces](../keywords/interface.md).</span></span>

- <span data-ttu-id="d612c-133">不能在結構類型中聲明[終端子](../../programming-guide/classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="d612c-133">You cannot declare a [finalizer](../../programming-guide/classes-and-structs/destructors.md) within a structure type.</span></span>

## <a name="instantiation-of-a-structure-type"></a><span data-ttu-id="d612c-134">結構類型的具現化</span><span class="sxs-lookup"><span data-stu-id="d612c-134">Instantiation of a structure type</span></span>

<span data-ttu-id="d612c-135">在 C# 中，必須先初始化聲明變數，然後才能使用它。</span><span class="sxs-lookup"><span data-stu-id="d612c-135">In C#, you must initialize a declared variable before it can be used.</span></span> <span data-ttu-id="d612c-136">因為結構類型變數不能`null`（除非它是可 null[數值型別的](nullable-value-types.md)變數），因此必須具現化相應類型的實例。</span><span class="sxs-lookup"><span data-stu-id="d612c-136">Because a structure-type variable cannot be `null` (unless it's a variable of a [nullable value type](nullable-value-types.md)), you must instantiate an instance of the corresponding type.</span></span> <span data-ttu-id="d612c-137">有幾種方法可以做到這一點。</span><span class="sxs-lookup"><span data-stu-id="d612c-137">There are several ways to do that.</span></span>

<span data-ttu-id="d612c-138">通常，通過使用運算子調用適當的建構函式來[`new`](../operators/new-operator.md)具現化結構類型。</span><span class="sxs-lookup"><span data-stu-id="d612c-138">Typically, you instantiate a structure type by calling an appropriate constructor with the [`new`](../operators/new-operator.md) operator.</span></span> <span data-ttu-id="d612c-139">每個結構類型至少有一個建構函式。</span><span class="sxs-lookup"><span data-stu-id="d612c-139">Every structure type has at least one constructor.</span></span> <span data-ttu-id="d612c-140">這是一個隱式無參數建構函式，它組建類型的[預設值](default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="d612c-140">That's an implicit parameterless constructor, which produces the [default value](default-values.md) of the type.</span></span> <span data-ttu-id="d612c-141">您還可以使用[預設值運算式](../operators/default.md)組建類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="d612c-141">You can also use a [default value expression](../operators/default.md) to produce the default value of a type.</span></span>

<span data-ttu-id="d612c-142">如果結構類型的所有實例欄位都可訪問，也可以在沒有`new`運算子的情況下具現化它。</span><span class="sxs-lookup"><span data-stu-id="d612c-142">If all instance fields of a structure type are accessible, you can also instantiate it without the `new` operator.</span></span> <span data-ttu-id="d612c-143">在這種情況下，您必須在首次使用實例之前初始化所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="d612c-143">In that case you must initialize all instance fields before the first use of the instance.</span></span> <span data-ttu-id="d612c-144">下列範例顯示如何執行該項工作：</span><span class="sxs-lookup"><span data-stu-id="d612c-144">The following example shows how to do that:</span></span>

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

<span data-ttu-id="d612c-145">在[內置數值型別](value-types.md#built-in-value-types)的情況下，使用相應的文本指定類型的值。</span><span class="sxs-lookup"><span data-stu-id="d612c-145">In the case of the [built-in value types](value-types.md#built-in-value-types), use the corresponding literals to specify a value of the type.</span></span>

## <a name="passing-structure-type-variables-by-reference"></a><span data-ttu-id="d612c-146">通過引用傳遞結構類型變數</span><span class="sxs-lookup"><span data-stu-id="d612c-146">Passing structure-type variables by reference</span></span>

<span data-ttu-id="d612c-147">將結構類型變數作為參數傳遞給方法或從方法返回結構類型值時，將複製結構類型的整個實例。</span><span class="sxs-lookup"><span data-stu-id="d612c-147">When you pass a structure-type variable to a method as an argument or return a structure-type value from a method, the whole instance of a structure type is copied.</span></span> <span data-ttu-id="d612c-148">這可能會影響代碼在涉及大型結構類型的高性能方案中的性能。</span><span class="sxs-lookup"><span data-stu-id="d612c-148">That can affect the performance of your code in high-performance scenarios that involve large structure types.</span></span> <span data-ttu-id="d612c-149">可以通過引用傳遞結構類型變數來避免值複製。</span><span class="sxs-lookup"><span data-stu-id="d612c-149">You can avoid value copying by passing a structure-type variable by reference.</span></span> <span data-ttu-id="d612c-150">使用[`ref`](../keywords/ref.md#passing-an-argument-by-reference)、[`out`](../keywords/out-parameter-modifier.md)或[`in`](../keywords/in-parameter-modifier.md)方法參數修改器指示必須通過引用傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="d612c-150">Use the [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md), or [`in`](../keywords/in-parameter-modifier.md) method parameter modifiers to indicate that an argument must be passed by reference.</span></span> <span data-ttu-id="d612c-151">使用[ref 返回](../../programming-guide/classes-and-structs/ref-returns.md)通過引用返回方法結果。</span><span class="sxs-lookup"><span data-stu-id="d612c-151">Use [ref returns](../../programming-guide/classes-and-structs/ref-returns.md) to return a method result by reference.</span></span> <span data-ttu-id="d612c-152">有關詳細資訊，請參閱[編寫安全高效的 C# 代碼](../../write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="d612c-152">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="d612c-153">轉換</span><span class="sxs-lookup"><span data-stu-id="d612c-153">Conversions</span></span>

<span data-ttu-id="d612c-154">對於任何結構類型，都存在與 和<xref:System.ValueType?displayProperty=nameWithType><xref:System.Object?displayProperty=nameWithType>類型轉換的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換。</span><span class="sxs-lookup"><span data-stu-id="d612c-154">For any structure type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.ValueType?displayProperty=nameWithType> and <xref:System.Object?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="d612c-155">結構類型和它實現的任何介面之間也存在裝箱和取消裝箱轉換。</span><span class="sxs-lookup"><span data-stu-id="d612c-155">There exist also boxing and unboxing conversions between a structure type and any interface that it implements.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d612c-156">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d612c-156">C# language specification</span></span>

<span data-ttu-id="d612c-157">有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的["結構"](~/_csharplang/spec/structs.md)部分。</span><span class="sxs-lookup"><span data-stu-id="d612c-157">For more information, see the [Structs](~/_csharplang/spec/structs.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d612c-158">有關`readonly`結構的詳細資訊，請參閱[功能建議注釋](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)。</span><span class="sxs-lookup"><span data-stu-id="d612c-158">For more information about `readonly` structs, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs).</span></span>

## <a name="see-also"></a><span data-ttu-id="d612c-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d612c-159">See also</span></span>

- [<span data-ttu-id="d612c-160">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d612c-160">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d612c-161">設計指南 - 在類和結構之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="d612c-161">Design guidelines - Choosing between class and struct</span></span>](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [<span data-ttu-id="d612c-162">設計指南 - 結構設計</span><span class="sxs-lookup"><span data-stu-id="d612c-162">Design guidelines - Struct design</span></span>](../../../standard/design-guidelines/struct.md)
- [<span data-ttu-id="d612c-163">類和結構</span><span class="sxs-lookup"><span data-stu-id="d612c-163">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
