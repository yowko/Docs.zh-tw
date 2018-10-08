---
title: 條件約束 (F#)
description: '深入了解 F # 的條件約束套用至泛型型別參數的泛型型別或函式中指定型別引數的需求。'
ms.date: 05/16/2016
ms.openlocfilehash: 9534db4ffd195022366af8c993658bd94f375f53
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837347"
---
# <a name="constraints"></a><span data-ttu-id="c373c-103">條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-103">Constraints</span></span>

<span data-ttu-id="c373c-104">本主題描述條件約束，您可以套用至泛型型別參數的泛型型別或函式中指定型別引數的需求。</span><span class="sxs-lookup"><span data-stu-id="c373c-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="c373c-105">語法</span><span class="sxs-lookup"><span data-stu-id="c373c-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="c373c-106">備註</span><span class="sxs-lookup"><span data-stu-id="c373c-106">Remarks</span></span>

<span data-ttu-id="c373c-107">有數個不同的條件約束，您可以套用至限制可用於泛型類型的類型。</span><span class="sxs-lookup"><span data-stu-id="c373c-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="c373c-108">下表列出並描述這些條件約束。</span><span class="sxs-lookup"><span data-stu-id="c373c-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="c373c-109">條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-109">Constraint</span></span>|<span data-ttu-id="c373c-110">語法</span><span class="sxs-lookup"><span data-stu-id="c373c-110">Syntax</span></span>|<span data-ttu-id="c373c-111">描述</span><span class="sxs-lookup"><span data-stu-id="c373c-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="c373c-112">類型條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-112">Type Constraint</span></span>|<span data-ttu-id="c373c-113">*型別參數*:&gt; *類型*</span><span class="sxs-lookup"><span data-stu-id="c373c-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="c373c-114">提供的型別必須等於或衍生自指定型別，或者，如果類型是介面，提供的型別必須實作介面。</span><span class="sxs-lookup"><span data-stu-id="c373c-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="c373c-115">Null 條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-115">Null Constraint</span></span>|<span data-ttu-id="c373c-116">*型別參數*: null</span><span class="sxs-lookup"><span data-stu-id="c373c-116">*type-parameter* : null</span></span>|<span data-ttu-id="c373c-117">提供的型別必須支援 null 常值。</span><span class="sxs-lookup"><span data-stu-id="c373c-117">The provided type must support the null literal.</span></span> <span data-ttu-id="c373c-118">這包括所有.NET 物件類型但不是 F # 清單、 tuple、 函式、 類別、 記錄或等位型別。</span><span class="sxs-lookup"><span data-stu-id="c373c-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="c373c-119">明確成員的條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-119">Explicit Member Constraint</span></span>|<span data-ttu-id="c373c-120">[（]*型別參數*[或...或*型別參數*)]: (*成員簽章*)</span><span class="sxs-lookup"><span data-stu-id="c373c-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="c373c-121">至少其中一個提供的型別引數必須具有指定的簽章; 的成員不適用於一般用途。</span><span class="sxs-lookup"><span data-stu-id="c373c-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="c373c-122">成員必須是明確定義型別或隱含型別延伸模組的一部分，是明確的成員限制式的有效目標。</span><span class="sxs-lookup"><span data-stu-id="c373c-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="c373c-123">建構函式條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-123">Constructor Constraint</span></span>|<span data-ttu-id="c373c-124">*型別參數*: (新： 單位-&gt; ')</span><span class="sxs-lookup"><span data-stu-id="c373c-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="c373c-125">提供的型別必須具有預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="c373c-125">The provided type must have a default constructor.</span></span>|
|<span data-ttu-id="c373c-126">實值類型條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-126">Value Type Constraint</span></span>|<span data-ttu-id="c373c-127">： 結構</span><span class="sxs-lookup"><span data-stu-id="c373c-127">: struct</span></span>|<span data-ttu-id="c373c-128">提供的型別必須是.NET 實值型別。</span><span class="sxs-lookup"><span data-stu-id="c373c-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="c373c-129">參考類型條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-129">Reference Type Constraint</span></span>|<span data-ttu-id="c373c-130">： 不結構</span><span class="sxs-lookup"><span data-stu-id="c373c-130">: not struct</span></span>|<span data-ttu-id="c373c-131">提供的型別必須是.NET 參考型別。</span><span class="sxs-lookup"><span data-stu-id="c373c-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="c373c-132">列舉型別條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="c373c-133">: enum&lt;*基礎類型*&gt;</span><span class="sxs-lookup"><span data-stu-id="c373c-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="c373c-134">提供的型別必須是列舉的類型，具有指定的基礎類型，不適用於一般用途。</span><span class="sxs-lookup"><span data-stu-id="c373c-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="c373c-135">委派條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-135">Delegate Constraint</span></span>|<span data-ttu-id="c373c-136">： 將委派&lt;*tuple 參數型別*，*傳回型別*&gt;</span><span class="sxs-lookup"><span data-stu-id="c373c-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="c373c-137">提供的型別必須是委派類型具有指定的引數和傳回值;不適用於一般用途。</span><span class="sxs-lookup"><span data-stu-id="c373c-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="c373c-138">比較條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-138">Comparison Constraint</span></span>|<span data-ttu-id="c373c-139">： 比較</span><span class="sxs-lookup"><span data-stu-id="c373c-139">: comparison</span></span>|<span data-ttu-id="c373c-140">提供的型別必須支援的比較。</span><span class="sxs-lookup"><span data-stu-id="c373c-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="c373c-141">等號比較條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-141">Equality Constraint</span></span>|<span data-ttu-id="c373c-142">： 等號比較</span><span class="sxs-lookup"><span data-stu-id="c373c-142">: equality</span></span>|<span data-ttu-id="c373c-143">提供的型別必須支援等號比較。</span><span class="sxs-lookup"><span data-stu-id="c373c-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="c373c-144">未受管理的條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-144">Unmanaged Constraint</span></span>|<span data-ttu-id="c373c-145">： 未受管理</span><span class="sxs-lookup"><span data-stu-id="c373c-145">: unmanaged</span></span>|<span data-ttu-id="c373c-146">提供的型別必須是 unmanaged 型別。</span><span class="sxs-lookup"><span data-stu-id="c373c-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="c373c-147">未受管理的類型為特定基本型別 (`sbyte`， `byte`， `char`， `nativeint`， `unativeint`， `float32`， `float`， `int16`， `uint16`， `int32`， `uint32`， `int64`， `uint64`，或`decimal`)，列舉型別`nativeptr<_>`，或其欄位為未受管理的所有類型的非泛型結構。</span><span class="sxs-lookup"><span data-stu-id="c373c-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|
<span data-ttu-id="c373c-148">您必須加入條件約束，當您的程式碼需要使用一般的條件約束的型別，但不要依賴型別上可用的功能。</span><span class="sxs-lookup"><span data-stu-id="c373c-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="c373c-149">例如，如果您使用的類型條件約束來指定類別類型時，您可以使用任何一種類型的泛型函式中該類別的方法。</span><span class="sxs-lookup"><span data-stu-id="c373c-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="c373c-150">指定條件約束時，有時必須撰寫型別參數明確，因為沒有任何限制，編譯器無法驗證您所使用的功能將會在可能會提供在執行階段類型的任何類型參數。</span><span class="sxs-lookup"><span data-stu-id="c373c-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="c373c-151">您在 F # 程式碼中使用的最常見的條件約束會指定基底類別或介面的型別條件約束。</span><span class="sxs-lookup"><span data-stu-id="c373c-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="c373c-152">其他條件約束使用 F # 程式庫來實作特定功能，例如明確成員，這個條件約束用來實作運算子多載算術的運算子，或提供主要是因為 F # 支援完整common language runtime 所支援的條件約束集合。</span><span class="sxs-lookup"><span data-stu-id="c373c-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="c373c-153">在型別推斷處理序中，某些條件約束會自動由編譯器推斷。</span><span class="sxs-lookup"><span data-stu-id="c373c-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="c373c-154">例如，如果您使用`+`函式中的運算子，編譯器會推斷的明確成員上條件約束運算式中使用的變數類型。</span><span class="sxs-lookup"><span data-stu-id="c373c-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="c373c-155">下列程式碼說明一些條件約束宣告。</span><span class="sxs-lookup"><span data-stu-id="c373c-155">The following code illustrates some constraint declarations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c373c-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c373c-156">See also</span></span>

- [<span data-ttu-id="c373c-157">泛型</span><span class="sxs-lookup"><span data-stu-id="c373c-157">Generics</span></span>](index.md)
- [<span data-ttu-id="c373c-158">條件約束</span><span class="sxs-lookup"><span data-stu-id="c373c-158">Constraints</span></span>](constraints.md)
