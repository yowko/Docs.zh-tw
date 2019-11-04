---
title: 條件約束
description: 瞭解適用F#于泛型型別參數的條件約束，以指定泛型型別或函式中的型別引數需求。
ms.date: 05/16/2016
ms.openlocfilehash: 70a8bec1ad67d7e814cb7a96b1876bb22399c5e7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425024"
---
# <a name="constraints"></a><span data-ttu-id="d3acd-103">條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-103">Constraints</span></span>

<span data-ttu-id="d3acd-104">本主題描述可套用至泛型型別參數的條件約束，以指定泛型型別或函式中的型別引數需求。</span><span class="sxs-lookup"><span data-stu-id="d3acd-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3acd-105">語法</span><span class="sxs-lookup"><span data-stu-id="d3acd-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="d3acd-106">備註</span><span class="sxs-lookup"><span data-stu-id="d3acd-106">Remarks</span></span>

<span data-ttu-id="d3acd-107">有幾個不同的條件約束可供您套用，以限制可用於泛型型別的類型。</span><span class="sxs-lookup"><span data-stu-id="d3acd-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="d3acd-108">下表列出並描述這些條件約束。</span><span class="sxs-lookup"><span data-stu-id="d3acd-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="d3acd-109">條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-109">Constraint</span></span>|<span data-ttu-id="d3acd-110">語法</span><span class="sxs-lookup"><span data-stu-id="d3acd-110">Syntax</span></span>|<span data-ttu-id="d3acd-111">描述</span><span class="sxs-lookup"><span data-stu-id="d3acd-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="d3acd-112">類型條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-112">Type Constraint</span></span>|<span data-ttu-id="d3acd-113">*類型參數*：&gt;*類型*</span><span class="sxs-lookup"><span data-stu-id="d3acd-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="d3acd-114">提供的類型必須等於或衍生自指定的類型，或者，如果類型是介面，則提供的類型必須執行介面。</span><span class="sxs-lookup"><span data-stu-id="d3acd-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="d3acd-115">Null 條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-115">Null Constraint</span></span>|<span data-ttu-id="d3acd-116">*類型參數*： null</span><span class="sxs-lookup"><span data-stu-id="d3acd-116">*type-parameter* : null</span></span>|<span data-ttu-id="d3acd-117">提供的類型必須支援 null 常值。</span><span class="sxs-lookup"><span data-stu-id="d3acd-117">The provided type must support the null literal.</span></span> <span data-ttu-id="d3acd-118">這包括所有 .NET 物件類型，但F#不包含清單、元組、函式、類別、記錄或聯集類型。</span><span class="sxs-lookup"><span data-stu-id="d3acd-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="d3acd-119">明確成員條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-119">Explicit Member Constraint</span></span>|<span data-ttu-id="d3acd-120">[（]*類型參數*[或 .。。或*類型參數*）]：（*成員簽*章）</span><span class="sxs-lookup"><span data-stu-id="d3acd-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="d3acd-121">提供的型別引數中至少必須有一個具有指定簽章的成員;不適用於一般用途。</span><span class="sxs-lookup"><span data-stu-id="d3acd-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="d3acd-122">成員必須在類型或隱含類型延伸的一部分上明確定義，才能成為明確成員條件約束的有效目標。</span><span class="sxs-lookup"><span data-stu-id="d3acd-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="d3acd-123">構造函式條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-123">Constructor Constraint</span></span>|<span data-ttu-id="d3acd-124">*類型參數*：（新的： unit-&gt; ' a）</span><span class="sxs-lookup"><span data-stu-id="d3acd-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="d3acd-125">提供的類型必須具有無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="d3acd-125">The provided type must have a parameterless constructor.</span></span>|
|<span data-ttu-id="d3acd-126">實值型別條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-126">Value Type Constraint</span></span>|<span data-ttu-id="d3acd-127">：結構</span><span class="sxs-lookup"><span data-stu-id="d3acd-127">: struct</span></span>|<span data-ttu-id="d3acd-128">提供的類型必須是 .NET 實數值型別。</span><span class="sxs-lookup"><span data-stu-id="d3acd-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="d3acd-129">參考型別條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-129">Reference Type Constraint</span></span>|<span data-ttu-id="d3acd-130">： not 結構</span><span class="sxs-lookup"><span data-stu-id="d3acd-130">: not struct</span></span>|<span data-ttu-id="d3acd-131">提供的型別必須是 .NET 引用型別。</span><span class="sxs-lookup"><span data-stu-id="d3acd-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="d3acd-132">列舉類型條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="d3acd-133">：列舉&lt;*基礎類型*&gt;</span><span class="sxs-lookup"><span data-stu-id="d3acd-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="d3acd-134">提供的類型必須是具有指定基礎類型的列舉類型。不適用於一般用途。</span><span class="sxs-lookup"><span data-stu-id="d3acd-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="d3acd-135">委派條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-135">Delegate Constraint</span></span>|<span data-ttu-id="d3acd-136">：委派&lt;*元組-參數類型*、傳回*類型*&gt;</span><span class="sxs-lookup"><span data-stu-id="d3acd-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="d3acd-137">提供的類型必須是具有指定的引數和傳回值的委派類型。不適用於一般用途。</span><span class="sxs-lookup"><span data-stu-id="d3acd-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="d3acd-138">比較準則約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-138">Comparison Constraint</span></span>|<span data-ttu-id="d3acd-139">：比較</span><span class="sxs-lookup"><span data-stu-id="d3acd-139">: comparison</span></span>|<span data-ttu-id="d3acd-140">提供的類型必須支援比較。</span><span class="sxs-lookup"><span data-stu-id="d3acd-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="d3acd-141">相等條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-141">Equality Constraint</span></span>|<span data-ttu-id="d3acd-142">：相等</span><span class="sxs-lookup"><span data-stu-id="d3acd-142">: equality</span></span>|<span data-ttu-id="d3acd-143">提供的類型必須支援相等。</span><span class="sxs-lookup"><span data-stu-id="d3acd-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="d3acd-144">非受控條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-144">Unmanaged Constraint</span></span>|<span data-ttu-id="d3acd-145">：非受控</span><span class="sxs-lookup"><span data-stu-id="d3acd-145">: unmanaged</span></span>|<span data-ttu-id="d3acd-146">提供的型別必須是非受控型別。</span><span class="sxs-lookup"><span data-stu-id="d3acd-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="d3acd-147">非受控類型是特定的基本型別（`sbyte`、`byte`、`char`、`nativeint`、`unativeint`、`float32`、`float`、`int16`、`uint16`、`int32`、`uint32`、`int64`、`uint64`或 `decimal`）、列舉類型、`nativeptr<_>`，或其欄位皆為非受控類型的非泛型結構。</span><span class="sxs-lookup"><span data-stu-id="d3acd-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="d3acd-148">當您的程式碼必須使用條件約束類型（而非一般類型）上可用的功能時，您必須加入條件約束。</span><span class="sxs-lookup"><span data-stu-id="d3acd-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="d3acd-149">例如，如果您使用類型條件約束來指定類別類型，您可以在泛型函數或類型中使用該類別的任何一個方法。</span><span class="sxs-lookup"><span data-stu-id="d3acd-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="d3acd-150">明確寫入型別參數時，有時需要指定條件約束，因為沒有條件約束，編譯器無法驗證您所使用的功能是否可用於該型別的執行時間可能會提供的任何型別。實參.</span><span class="sxs-lookup"><span data-stu-id="d3acd-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="d3acd-151">您在程式碼中F#使用的最常見條件約束是指定基類或介面的類型條件約束。</span><span class="sxs-lookup"><span data-stu-id="d3acd-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="d3acd-152">連結F#庫會使用其他條件約束來執行特定功能，例如明確成員條件約束（用來執行算術運算子的運算子多載），主要是因為F#支援 common language runtime 所支援的一組完整條件約束。</span><span class="sxs-lookup"><span data-stu-id="d3acd-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="d3acd-153">在型別推斷程式期間，編譯器會自動推斷某些條件約束。</span><span class="sxs-lookup"><span data-stu-id="d3acd-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="d3acd-154">例如，如果您在函數中使用 `+` 運算子，則編譯器會在運算式中使用的變數類型上推斷明確成員條件約束。</span><span class="sxs-lookup"><span data-stu-id="d3acd-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="d3acd-155">下列程式碼說明一些條件約束宣告：</span><span class="sxs-lookup"><span data-stu-id="d3acd-155">The following code illustrates some constraint declarations:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d3acd-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="d3acd-156">See also</span></span>

- [<span data-ttu-id="d3acd-157">泛型</span><span class="sxs-lookup"><span data-stu-id="d3acd-157">Generics</span></span>](index.md)
- [<span data-ttu-id="d3acd-158">條件約束</span><span class="sxs-lookup"><span data-stu-id="d3acd-158">Constraints</span></span>](constraints.md)
