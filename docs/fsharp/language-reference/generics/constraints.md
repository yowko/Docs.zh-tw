---
title: 條件約束 (F#)
description: '深入了解 F # 條件約束套用至泛型類型參數，以指定泛型型別或函式中的型別引數的需求。'
ms.date: 05/16/2016
ms.openlocfilehash: f0722cafe27a4e2c38dfbf091973edb136cf5228
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562306"
---
# <a name="constraints"></a><span data-ttu-id="b67e1-103">條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-103">Constraints</span></span>

<span data-ttu-id="b67e1-104">本主題描述條件約束，您可以套用至泛型類型參數的泛型型別或函式中指定型別引數的需求。</span><span class="sxs-lookup"><span data-stu-id="b67e1-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>


## <a name="syntax"></a><span data-ttu-id="b67e1-105">語法</span><span class="sxs-lookup"><span data-stu-id="b67e1-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="b67e1-106">備註</span><span class="sxs-lookup"><span data-stu-id="b67e1-106">Remarks</span></span>
<span data-ttu-id="b67e1-107">有數個不同的條件約束，您可以套用來限制可用於泛型類型的類型。</span><span class="sxs-lookup"><span data-stu-id="b67e1-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="b67e1-108">下表列出並描述這些條件約束。</span><span class="sxs-lookup"><span data-stu-id="b67e1-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="b67e1-109">條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-109">Constraint</span></span>|<span data-ttu-id="b67e1-110">語法</span><span class="sxs-lookup"><span data-stu-id="b67e1-110">Syntax</span></span>|<span data-ttu-id="b67e1-111">描述</span><span class="sxs-lookup"><span data-stu-id="b67e1-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="b67e1-112">類型條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-112">Type Constraint</span></span>|<span data-ttu-id="b67e1-113">*型別參數*:&gt; *類型*</span><span class="sxs-lookup"><span data-stu-id="b67e1-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="b67e1-114">提供的型別必須是等於或衍生型別指定，或者，如果類型是介面，提供的類型必須實作的介面。</span><span class="sxs-lookup"><span data-stu-id="b67e1-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="b67e1-115">Null 條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-115">Null Constraint</span></span>|<span data-ttu-id="b67e1-116">*型別參數*: null</span><span class="sxs-lookup"><span data-stu-id="b67e1-116">*type-parameter* : null</span></span>|<span data-ttu-id="b67e1-117">提供的類型必須支援 null 常值。</span><span class="sxs-lookup"><span data-stu-id="b67e1-117">The provided type must support the null literal.</span></span> <span data-ttu-id="b67e1-118">這包括所有.NET 物件類型但不是 F # 清單、 tuple、 函式、 類別、 記錄或等位型別。</span><span class="sxs-lookup"><span data-stu-id="b67e1-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="b67e1-119">明確成員條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-119">Explicit Member Constraint</span></span>|<span data-ttu-id="b67e1-120">（[)]*型別參數*[或...或*型別參數*)]: (* 成員簽章 *)</span><span class="sxs-lookup"><span data-stu-id="b67e1-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature *)</span></span>|<span data-ttu-id="b67e1-121">至少其中一個提供的型別引數必須具有指定的簽章; 的成員不提供一般用途。</span><span class="sxs-lookup"><span data-stu-id="b67e1-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="b67e1-122">成員必須是明確定義明確的成員條件約束的有效目標的類型或隱含型別延伸模組的一部分。</span><span class="sxs-lookup"><span data-stu-id="b67e1-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="b67e1-123">建構函式條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-123">Constructor Constraint</span></span>|<span data-ttu-id="b67e1-124">*型別參數*: (new： 單位-&gt; ')</span><span class="sxs-lookup"><span data-stu-id="b67e1-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="b67e1-125">提供的類型必須有預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="b67e1-125">The provided type must have a default constructor.</span></span>|
|<span data-ttu-id="b67e1-126">實值類型條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-126">Value Type Constraint</span></span>|<span data-ttu-id="b67e1-127">： 結構</span><span class="sxs-lookup"><span data-stu-id="b67e1-127">: struct</span></span>|<span data-ttu-id="b67e1-128">提供的類型必須是.NET 實值類型。</span><span class="sxs-lookup"><span data-stu-id="b67e1-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="b67e1-129">參考類型條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-129">Reference Type Constraint</span></span>|<span data-ttu-id="b67e1-130">： 不結構</span><span class="sxs-lookup"><span data-stu-id="b67e1-130">: not struct</span></span>|<span data-ttu-id="b67e1-131">提供的類型必須是.NET 參考類型。</span><span class="sxs-lookup"><span data-stu-id="b67e1-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="b67e1-132">列舉型別條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="b67e1-133">： 列舉&lt;*基礎類型*&gt;</span><span class="sxs-lookup"><span data-stu-id="b67e1-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="b67e1-134">提供的類型必須是列舉型別具有指定的基礎類型。不提供一般用途。</span><span class="sxs-lookup"><span data-stu-id="b67e1-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="b67e1-135">委派的條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-135">Delegate Constraint</span></span>|<span data-ttu-id="b67e1-136">： 委派&lt;*tuple 參數型別*，*傳回型別*&gt;</span><span class="sxs-lookup"><span data-stu-id="b67e1-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="b67e1-137">提供的類型必須是委派類型具有指定的引數和傳回值;不提供一般用途。</span><span class="sxs-lookup"><span data-stu-id="b67e1-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="b67e1-138">比較條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-138">Comparison Constraint</span></span>|<span data-ttu-id="b67e1-139">： 比較</span><span class="sxs-lookup"><span data-stu-id="b67e1-139">: comparison</span></span>|<span data-ttu-id="b67e1-140">提供的類型必須支援的比較。</span><span class="sxs-lookup"><span data-stu-id="b67e1-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="b67e1-141">等號比較條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-141">Equality Constraint</span></span>|<span data-ttu-id="b67e1-142">： 等號比較</span><span class="sxs-lookup"><span data-stu-id="b67e1-142">: equality</span></span>|<span data-ttu-id="b67e1-143">提供的類型必須支援等號比較。</span><span class="sxs-lookup"><span data-stu-id="b67e1-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="b67e1-144">未受管理的條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-144">Unmanaged Constraint</span></span>|<span data-ttu-id="b67e1-145">： 未受管理</span><span class="sxs-lookup"><span data-stu-id="b67e1-145">: unmanaged</span></span>|<span data-ttu-id="b67e1-146">提供的類型必須是 unmanaged 的類型。</span><span class="sxs-lookup"><span data-stu-id="b67e1-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="b67e1-147">Unmanaged 的類型為特定基本型別 (`sbyte`， `byte`， `char`， `nativeint`， `unativeint`， `float32`， `float`， `int16`， `uint16`， `int32`， `uint32`， `int64`， `uint64`，或`decimal`)，列舉型別`nativeptr&lt;_&gt;`，或其欄位是不受管理的所有類型的非泛型結構。</span><span class="sxs-lookup"><span data-stu-id="b67e1-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr&lt;_&gt;`, or a non-generic structure whose fields are all unmanaged types.</span></span>|
<span data-ttu-id="b67e1-148">您必須加入條件約束時使用的功能一般是用於條件約束類型但不是在型別，對您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b67e1-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="b67e1-149">比方說，如果您使用的類型條件約束指定類別類型時，您可以使用其中一個該類別中的泛型函式或類型的方法。</span><span class="sxs-lookup"><span data-stu-id="b67e1-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="b67e1-150">指定條件約束時，有時需要明確地撰寫型別參數因為如果沒有限制，編譯器無法驗證您所使用的功能將會在任何可能會提供在執行階段類型的類型參數。</span><span class="sxs-lookup"><span data-stu-id="b67e1-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="b67e1-151">您在 F # 程式碼中使用的最常見的條件約束會指定基底類別或介面的型別條件約束。</span><span class="sxs-lookup"><span data-stu-id="b67e1-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="b67e1-152">其他條件約束的 F # 程式庫用來實作特定功能，例如 明確成員條件約束，用來實作運算子多載算術運算子，或提供主要是因為 F # 支援的完整一組條件約束所支援的通用語言執行平台。</span><span class="sxs-lookup"><span data-stu-id="b67e1-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="b67e1-153">類型推斷程序，在某些條件約束會自動由編譯器所推斷。</span><span class="sxs-lookup"><span data-stu-id="b67e1-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="b67e1-154">例如，如果您使用`+`運算子函式中的，編譯器會推斷變數的運算式中使用的型別上的明確成員條件約束。</span><span class="sxs-lookup"><span data-stu-id="b67e1-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="b67e1-155">下列程式碼將說明一些條件約束宣告。</span><span class="sxs-lookup"><span data-stu-id="b67e1-155">The following code illustrates some constraint declarations.</span></span>

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a><span data-ttu-id="b67e1-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b67e1-156">See Also</span></span>
[<span data-ttu-id="b67e1-157">泛型</span><span class="sxs-lookup"><span data-stu-id="b67e1-157">Generics</span></span>](index.md)

[<span data-ttu-id="b67e1-158">條件約束</span><span class="sxs-lookup"><span data-stu-id="b67e1-158">Constraints</span></span>](constraints.md)
