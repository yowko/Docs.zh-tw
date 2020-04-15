---
title: 結構類型 - C# 引用
ms.date: 04/14/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 8013aab5580ac007875debc78208532a2d0ad1dc
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388996"
---
# <a name="structure-types-c-reference"></a><span data-ttu-id="27397-102">結構類型(C# 參考)</span><span class="sxs-lookup"><span data-stu-id="27397-102">Structure types (C# reference)</span></span>

<span data-ttu-id="27397-103">*結構類型*(或*結構型態*)是一種可以封裝資料和相關功能[的值類型](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="27397-103">A *structure type* (or *struct type*) is a [value type](value-types.md) that can encapsulate data and related functionality.</span></span> <span data-ttu-id="27397-104">使用 關鍵`struct`字 定義結構類型:</span><span class="sxs-lookup"><span data-stu-id="27397-104">You use the `struct` keyword to define a structure type:</span></span>

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

<span data-ttu-id="27397-105">結構類型具有*值語意*。</span><span class="sxs-lookup"><span data-stu-id="27397-105">Structure types have *value semantics*.</span></span> <span data-ttu-id="27397-106">也就是說,結構類型的變數包含類型的實例。</span><span class="sxs-lookup"><span data-stu-id="27397-106">That is, a variable of a structure type contains an instance of the type.</span></span> <span data-ttu-id="27397-107">默認情況下,在賦值時複製變數值,將參數傳遞給方法,並返回方法結果。</span><span class="sxs-lookup"><span data-stu-id="27397-107">By default, variable values are copied on assignment, passing an argument to a method, and returning a method result.</span></span> <span data-ttu-id="27397-108">對於結構類型變數,將複製類型的實例。</span><span class="sxs-lookup"><span data-stu-id="27397-108">In the case of a structure-type variable, an instance of the type is copied.</span></span> <span data-ttu-id="27397-109">有關詳細資訊,請參考[值類型](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="27397-109">For more information, see [Value types](value-types.md).</span></span>

<span data-ttu-id="27397-110">通常,使用結構類型來設計提供很少或沒有行為的小型以數據為中心的類型。</span><span class="sxs-lookup"><span data-stu-id="27397-110">Typically, you use structure types to design small data-centric types that provide little or no behavior.</span></span> <span data-ttu-id="27397-111">例如,.NET 使用結構類型來表示數位([整數](integral-numeric-types.md)與[實體 )](floating-point-numeric-types.md),[布林值](bool.md)[, Unicode 字元](char.md),[時間實例](xref:System.DateTime)。</span><span class="sxs-lookup"><span data-stu-id="27397-111">For example, .NET uses structure types to represent a number (both [integer](integral-numeric-types.md) and [real](floating-point-numeric-types.md)), a [Boolean value](bool.md), a [Unicode character](char.md), a [time instance](xref:System.DateTime).</span></span> <span data-ttu-id="27397-112">如果您專注於類型的行為,請考慮定義[類別](../keywords/class.md)。</span><span class="sxs-lookup"><span data-stu-id="27397-112">If you're focused on the behavior of a type, consider defining a [class](../keywords/class.md).</span></span> <span data-ttu-id="27397-113">類別類型具有*引言語意*。</span><span class="sxs-lookup"><span data-stu-id="27397-113">Class types have *reference semantics*.</span></span> <span data-ttu-id="27397-114">也就是說,類類型的變數包含對類型實例的引用,而不是實例本身。</span><span class="sxs-lookup"><span data-stu-id="27397-114">That is, a variable of a class type contains a reference to an instance of the type, not the instance itself.</span></span>

<span data-ttu-id="27397-115">由於結構類型具有值語義,因此我們建議您定義*不可變*結構類型。</span><span class="sxs-lookup"><span data-stu-id="27397-115">Because structure types have value semantics, we recommend you to define *immutable* structure types.</span></span>

## <a name="readonly-struct"></a><span data-ttu-id="27397-116">`readonly`結構</span><span class="sxs-lookup"><span data-stu-id="27397-116">`readonly` struct</span></span>

<span data-ttu-id="27397-117">從 C# 7.2`readonly`開始, 使用修飾符聲明結構類型不可變:</span><span class="sxs-lookup"><span data-stu-id="27397-117">Beginning with C# 7.2, you use the `readonly` modifier to declare that a structure type is immutable:</span></span>

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

<span data-ttu-id="27397-118">`readonly`結構的所有資料成員必須唯讀如下:</span><span class="sxs-lookup"><span data-stu-id="27397-118">All data members of a `readonly` struct must be read-only as follows:</span></span>

- <span data-ttu-id="27397-119">任何欄位聲明必須具有[`readonly`變更器](../keywords/readonly.md)</span><span class="sxs-lookup"><span data-stu-id="27397-119">Any field declaration must have the [`readonly` modifier](../keywords/readonly.md)</span></span>
- <span data-ttu-id="27397-120">任何屬性(包括自動實作的屬性)都必須是唯讀的</span><span class="sxs-lookup"><span data-stu-id="27397-120">Any property, including auto-implemented ones, must be read-only</span></span>

<span data-ttu-id="27397-121">這保證了`readonly`結構的成員不會修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="27397-121">That guarantees that no member of a `readonly` struct modifies the state of the struct.</span></span>

> [!NOTE]
> <span data-ttu-id="27397-122">在`readonly`結構中,可變引用類型的數據成員仍然可以更改其自己的狀態。</span><span class="sxs-lookup"><span data-stu-id="27397-122">In a `readonly` struct, a data member of a mutable reference type still can mutate its own state.</span></span> <span data-ttu-id="27397-123">例如,不能替換<xref:System.Collections.Generic.List%601>實例,但可以向實例添加新元素。</span><span class="sxs-lookup"><span data-stu-id="27397-123">For example, you cannot replace a <xref:System.Collections.Generic.List%601> instance, but you can add new elements to it.</span></span>

## <a name="readonly-instance-members"></a><span data-ttu-id="27397-124">`readonly`實體成員</span><span class="sxs-lookup"><span data-stu-id="27397-124">`readonly` instance members</span></span>

<span data-ttu-id="27397-125">從 C# 8.0 開始`readonly`,還可以使用 修改器聲明實例成員不修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="27397-125">Beginning with C# 8.0, you can also use the `readonly` modifier to declare that an instance member doesn't modify the state of a struct.</span></span> <span data-ttu-id="27397-126">如果無法將整個結構類型聲明為`readonly`,請`readonly`使用 修改器標記不修改結構狀態的實例成員。</span><span class="sxs-lookup"><span data-stu-id="27397-126">If you cannot declare the whole structure type as `readonly`, use the `readonly` modifier to mark the instance members that don't modify the state of the struct.</span></span> <span data-ttu-id="27397-127">在`readonly`結構中,每個實例成員都是隱式`readonly`的。</span><span class="sxs-lookup"><span data-stu-id="27397-127">In a `readonly` struct, every instance member is implicitly `readonly`.</span></span>

<span data-ttu-id="27397-128">在實例`readonly`成員中,不能分配給結構的實例欄位。</span><span class="sxs-lookup"><span data-stu-id="27397-128">Within a `readonly` instance member, you cannot assign to structure's instance fields.</span></span> <span data-ttu-id="27397-129">但是,成員`readonly`可以調用非`readonly`成員。</span><span class="sxs-lookup"><span data-stu-id="27397-129">However, a `readonly` member can call a non-`readonly` member.</span></span> <span data-ttu-id="27397-130">在這種情況下,編譯器將創建結構實例的副本,並調用該副本上的非`readonly`成員。</span><span class="sxs-lookup"><span data-stu-id="27397-130">In that case the compiler creates a copy of the structure instance and calls the non-`readonly` member on that copy.</span></span> <span data-ttu-id="27397-131">因此,不會修改原始結構實例。</span><span class="sxs-lookup"><span data-stu-id="27397-131">As a result, the original structure instance is not modified.</span></span>

<span data-ttu-id="27397-132">通常,您將`readonly`修改器應用於以下類型的實體成員:</span><span class="sxs-lookup"><span data-stu-id="27397-132">Typically, you apply the `readonly` modifier to the following kinds of instance members:</span></span>

- <span data-ttu-id="27397-133">方法:</span><span class="sxs-lookup"><span data-stu-id="27397-133">methods:</span></span>

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  <span data-ttu-id="27397-134">還可以將`readonly`修改器應用於重寫<xref:System.Object?displayProperty=nameWithType>在 中 聲明的方法的方法:</span><span class="sxs-lookup"><span data-stu-id="27397-134">You can also apply the `readonly` modifier to methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>:</span></span>

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- <span data-ttu-id="27397-135">屬性與索引器:</span><span class="sxs-lookup"><span data-stu-id="27397-135">properties and indexers:</span></span>

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  <span data-ttu-id="27397-136">如果需要將`readonly`修改器應用於屬性或索引器的兩個訪問器,請將其應用於屬性或索引器的聲明。</span><span class="sxs-lookup"><span data-stu-id="27397-136">If you need to apply the `readonly` modifier to both accessors of a property or indexer, apply it in the declaration of the property or indexer.</span></span>

  > [!NOTE]
  > <span data-ttu-id="27397-137">`get`編譯器聲明[自動實現屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)的訪問`readonly`許可權為`readonly`,而不考慮 屬性聲明中修飾符的存在。</span><span class="sxs-lookup"><span data-stu-id="27397-137">The compiler declares a `get` accessor of an [auto-implemented property](../../programming-guide/classes-and-structs/auto-implemented-properties.md) as `readonly`, regardless of presence of the `readonly` modifier in a property declaration.</span></span>

<span data-ttu-id="27397-138">不能將`readonly`修改符應用於結構類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="27397-138">You cannot apply the `readonly` modifier to static members of a structure type.</span></span>

<span data-ttu-id="27397-139">編譯器可以使用`readonly`修改器進行性能優化。</span><span class="sxs-lookup"><span data-stu-id="27397-139">The compiler may make use of the `readonly` modifier for performance optimizations.</span></span> <span data-ttu-id="27397-140">有關詳細資訊,請參閱[編寫安全高效的 C# 代碼](../../write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="27397-140">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="limitations-with-the-design-of-a-structure-type"></a><span data-ttu-id="27397-141">結構類型設計的限制</span><span class="sxs-lookup"><span data-stu-id="27397-141">Limitations with the design of a structure type</span></span>

<span data-ttu-id="27397-142">設計結構類型時,具有與[類](../keywords/class.md)類型相同的功能,但以下情況除外:</span><span class="sxs-lookup"><span data-stu-id="27397-142">When you design a structure type, you have the same capabilities as with a [class](../keywords/class.md) type, with the following exceptions:</span></span>

- <span data-ttu-id="27397-143">不能聲明無參數構造函數。</span><span class="sxs-lookup"><span data-stu-id="27397-143">You cannot declare a parameterless constructor.</span></span> <span data-ttu-id="27397-144">每個結構類型都已提供一個隱式無參數建構函數,該建構函數產生類型的[預設值](default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="27397-144">Every structure type already provides an implicit parameterless constructor that produces the [default value](default-values.md) of the type.</span></span>

- <span data-ttu-id="27397-145">不能在其聲明上初始化實例欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="27397-145">You cannot initialize an instance field or property at its declaration.</span></span> <span data-ttu-id="27397-146">但是,您可以在其聲明上初始化[靜態](../keywords/static.md)或[const](../keywords/const.md)欄位或靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="27397-146">However, you can initialize a [static](../keywords/static.md) or [const](../keywords/const.md) field or a static property at its declaration.</span></span>

- <span data-ttu-id="27397-147">結構類型的構造函數必須初始化類型的所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="27397-147">A constructor of a structure type must initialize all instance fields of the type.</span></span>

- <span data-ttu-id="27397-148">結構類型不能從其他類或結構類型繼承,也不能是類的基礎。</span><span class="sxs-lookup"><span data-stu-id="27397-148">A structure type cannot inherit from other class or structure type and it cannot be the base of a class.</span></span> <span data-ttu-id="27397-149">但是,結構類型可以實現[介面](../keywords/interface.md)。</span><span class="sxs-lookup"><span data-stu-id="27397-149">However, a structure type can implement [interfaces](../keywords/interface.md).</span></span>

- <span data-ttu-id="27397-150">無法在結構型態中宣告[終結器](../../programming-guide/classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="27397-150">You cannot declare a [finalizer](../../programming-guide/classes-and-structs/destructors.md) within a structure type.</span></span>

## <a name="instantiation-of-a-structure-type"></a><span data-ttu-id="27397-151">結構類型的實體化</span><span class="sxs-lookup"><span data-stu-id="27397-151">Instantiation of a structure type</span></span>

<span data-ttu-id="27397-152">在 C# 中,必須先初始化聲明變數,然後才能使用它。</span><span class="sxs-lookup"><span data-stu-id="27397-152">In C#, you must initialize a declared variable before it can be used.</span></span> <span data-ttu-id="27397-153">因為結構類型變數不能`null`(除非它是可 null[值類型的](nullable-value-types.md)變數),因此必須實例化相應類型的實例。</span><span class="sxs-lookup"><span data-stu-id="27397-153">Because a structure-type variable cannot be `null` (unless it's a variable of a [nullable value type](nullable-value-types.md)), you must instantiate an instance of the corresponding type.</span></span> <span data-ttu-id="27397-154">有幾種方法可以做到這一點。</span><span class="sxs-lookup"><span data-stu-id="27397-154">There are several ways to do that.</span></span>

<span data-ttu-id="27397-155">通常,通過使用運算符調用適當的構造函數來[`new`](../operators/new-operator.md)實例化結構類型。</span><span class="sxs-lookup"><span data-stu-id="27397-155">Typically, you instantiate a structure type by calling an appropriate constructor with the [`new`](../operators/new-operator.md) operator.</span></span> <span data-ttu-id="27397-156">每個結構類型至少有一個構造函數。</span><span class="sxs-lookup"><span data-stu-id="27397-156">Every structure type has at least one constructor.</span></span> <span data-ttu-id="27397-157">這是一個隱式無參數建構函數,它產生類型的[預設值](default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="27397-157">That's an implicit parameterless constructor, which produces the [default value](default-values.md) of the type.</span></span> <span data-ttu-id="27397-158">您還可以使用[預設值運算式](../operators/default.md)生成類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="27397-158">You can also use a [default value expression](../operators/default.md) to produce the default value of a type.</span></span>

<span data-ttu-id="27397-159">如果結構類型的所有實例欄位都可訪問,也可以在沒有`new`運算元的情況下實例化它。</span><span class="sxs-lookup"><span data-stu-id="27397-159">If all instance fields of a structure type are accessible, you can also instantiate it without the `new` operator.</span></span> <span data-ttu-id="27397-160">在這種情況下,您必須在首次使用實例之前初始化所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="27397-160">In that case you must initialize all instance fields before the first use of the instance.</span></span> <span data-ttu-id="27397-161">下列範例顯示如何執行該項工作：</span><span class="sxs-lookup"><span data-stu-id="27397-161">The following example shows how to do that:</span></span>

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

<span data-ttu-id="27397-162">在[內建值類型](value-types.md#built-in-value-types)的情況下,使用相應的文本指定類型的值。</span><span class="sxs-lookup"><span data-stu-id="27397-162">In the case of the [built-in value types](value-types.md#built-in-value-types), use the corresponding literals to specify a value of the type.</span></span>

## <a name="passing-structure-type-variables-by-reference"></a><span data-ttu-id="27397-163">透過參考傳遞結構型態變數</span><span class="sxs-lookup"><span data-stu-id="27397-163">Passing structure-type variables by reference</span></span>

<span data-ttu-id="27397-164">將結構類型變數作為參數傳遞給方法或從方法返回結構類型值時,將複製結構類型的整個實例。</span><span class="sxs-lookup"><span data-stu-id="27397-164">When you pass a structure-type variable to a method as an argument or return a structure-type value from a method, the whole instance of a structure type is copied.</span></span> <span data-ttu-id="27397-165">這可能會影響代碼在涉及大型結構類型的高性能方案中的性能。</span><span class="sxs-lookup"><span data-stu-id="27397-165">That can affect the performance of your code in high-performance scenarios that involve large structure types.</span></span> <span data-ttu-id="27397-166">可以通過引用傳遞結構類型變數來避免值複製。</span><span class="sxs-lookup"><span data-stu-id="27397-166">You can avoid value copying by passing a structure-type variable by reference.</span></span> <span data-ttu-id="27397-167">使用[`ref`](../keywords/ref.md#passing-an-argument-by-reference)、[`out`](../keywords/out-parameter-modifier.md)[`in`](../keywords/in-parameter-modifier.md)或方法參數修改器指示必須透過引用傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="27397-167">Use the [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md), or [`in`](../keywords/in-parameter-modifier.md) method parameter modifiers to indicate that an argument must be passed by reference.</span></span> <span data-ttu-id="27397-168">使用[ref 返回](../../programming-guide/classes-and-structs/ref-returns.md)通過引用返回方法結果。</span><span class="sxs-lookup"><span data-stu-id="27397-168">Use [ref returns](../../programming-guide/classes-and-structs/ref-returns.md) to return a method result by reference.</span></span> <span data-ttu-id="27397-169">有關詳細資訊,請參閱[編寫安全高效的 C# 代碼](../../write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="27397-169">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="27397-170">轉換</span><span class="sxs-lookup"><span data-stu-id="27397-170">Conversions</span></span>

<span data-ttu-id="27397-171">對於任何結構類型,都存在與和<xref:System.ValueType?displayProperty=nameWithType><xref:System.Object?displayProperty=nameWithType>類型轉換的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換。</span><span class="sxs-lookup"><span data-stu-id="27397-171">For any structure type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.ValueType?displayProperty=nameWithType> and <xref:System.Object?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="27397-172">結構類型和它實現的任何介面之間也存在裝箱和取消裝箱轉換。</span><span class="sxs-lookup"><span data-stu-id="27397-172">There exist also boxing and unboxing conversions between a structure type and any interface that it implements.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="27397-173">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="27397-173">C# language specification</span></span>

<span data-ttu-id="27397-174">有關詳細資訊,請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[「結構」](~/_csharplang/spec/structs.md)部分。</span><span class="sxs-lookup"><span data-stu-id="27397-174">For more information, see the [Structs](~/_csharplang/spec/structs.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="27397-175">有關 C# 7.2 及更高版本中引入的功能的詳細資訊,請參閱以下功能建議說明:</span><span class="sxs-lookup"><span data-stu-id="27397-175">For more information about features introduced in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="27397-176">唯讀結構</span><span class="sxs-lookup"><span data-stu-id="27397-176">Readonly structs</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [<span data-ttu-id="27397-177">唯讀執行個體成員</span><span class="sxs-lookup"><span data-stu-id="27397-177">Readonly instance members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="27397-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27397-178">See also</span></span>

- [<span data-ttu-id="27397-179">C# 參考</span><span class="sxs-lookup"><span data-stu-id="27397-179">C# reference</span></span>](../index.md)
- [<span data-ttu-id="27397-180">設計指南 ─ 在類別和結構之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="27397-180">Design guidelines - Choosing between class and struct</span></span>](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [<span data-ttu-id="27397-181">設計指南 - 結構設計</span><span class="sxs-lookup"><span data-stu-id="27397-181">Design guidelines - Struct design</span></span>](../../../standard/design-guidelines/struct.md)
- [<span data-ttu-id="27397-182">類別和結構</span><span class="sxs-lookup"><span data-stu-id="27397-182">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
