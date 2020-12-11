---
title: 可為 Null 的實值型別
description: '瞭解如何使用可為 null 的實值型別，表示在 F # 中也可以是 null 的實數值型別。'
ms.date: 11/19/2020
ms.openlocfilehash: e28cbfc57c5631573f46ac36462517cf011e96d2
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009634"
---
# <a name="nullable-value-types"></a><span data-ttu-id="3623b-103">可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="3623b-103">Nullable value types</span></span>

<span data-ttu-id="3623b-104">_可為 null 的實值型_ 別 `Nullable<'T>` 代表也可以是的任何 [結構](structures.md)類型 `null` 。</span><span class="sxs-lookup"><span data-stu-id="3623b-104">A _nullable value type_ `Nullable<'T>` represents any [struct](structures.md) type that could also be `null`.</span></span> <span data-ttu-id="3623b-105">當您與可選擇用來代表這些類型類型的程式庫和元件（例如整數）進行互動時，這項功能會很有説明 `null` 。</span><span class="sxs-lookup"><span data-stu-id="3623b-105">This is helpful when interacting with libraries and components that may choose to represent these kinds of types, like integers, with a `null` value for efficiency reasons.</span></span> <span data-ttu-id="3623b-106">支援此結構的基礎類型為 <xref:System.Nullable%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="3623b-106">The underlying type that backs this construct is <xref:System.Nullable%601?displayProperty=nameWithType>.</span></span>

## <a name="syntax"></a><span data-ttu-id="3623b-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3623b-107">Syntax</span></span>

```fsharp
Nullable<'T>
Nullable value
```

## <a name="declare-and-assign-with-values"></a><span data-ttu-id="3623b-108">使用值宣告並指派</span><span class="sxs-lookup"><span data-stu-id="3623b-108">Declare and assign with values</span></span>

<span data-ttu-id="3623b-109">宣告可為 null 的實值型別，就像在 F # 中宣告任何類似包裝函式的型別一樣：</span><span class="sxs-lookup"><span data-stu-id="3623b-109">Declaring a nullable value type is just like declaring any wrapper-like type in F#:</span></span>

```fsharp
open System

let x = 12
let nullableX = Nullable<int> x
```

<span data-ttu-id="3623b-110">您也可以省略泛型型別參數，並允許型別推斷來解析它：</span><span class="sxs-lookup"><span data-stu-id="3623b-110">You can also elide the generic type parameter and allow type inference to resolve it:</span></span>

```fsharp
open System

let x = 12
let nullableX = Nullable x
```

<span data-ttu-id="3623b-111">若要指派給可為 null 的實值型別，您也必須是明確的。</span><span class="sxs-lookup"><span data-stu-id="3623b-111">To assign to a nullable value type, you'll need to also be explicit.</span></span> <span data-ttu-id="3623b-112">F # 定義可為 null 的實數值型別沒有隱含轉換：</span><span class="sxs-lookup"><span data-stu-id="3623b-112">There is no implicit conversion for F#-defined nullable value types:</span></span>

```fsharp
open System

let mutable x = Nullable 12
x <- Nullable 13
```

## <a name="assign-null"></a><span data-ttu-id="3623b-113">指派 null</span><span class="sxs-lookup"><span data-stu-id="3623b-113">Assign null</span></span>

<span data-ttu-id="3623b-114">您無法直接指派 `null` 給可為 null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="3623b-114">You cannot directly assign `null` to a nullable value type.</span></span> <span data-ttu-id="3623b-115">請 `Nullable()` 改用：</span><span class="sxs-lookup"><span data-stu-id="3623b-115">Use `Nullable()` instead:</span></span>

```fsharp
let mutable a = Nullable 42
a <- Nullable()
```

<span data-ttu-id="3623b-116">這是因為沒有 `Nullable<'T>` `null` 適當的值。</span><span class="sxs-lookup"><span data-stu-id="3623b-116">This is because `Nullable<'T>` does not have `null` as a proper value.</span></span>

## <a name="pass-and-assign-to-members"></a><span data-ttu-id="3623b-117">傳遞並指派給成員</span><span class="sxs-lookup"><span data-stu-id="3623b-117">Pass and assign to members</span></span>

<span data-ttu-id="3623b-118">使用成員和 F # 值兩者之間的主要差異在於，當您使用成員時，可以隱含推斷可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="3623b-118">A key difference between working with members and F# values is that nullable value types can be implicitly inferred when you're working with members.</span></span> <span data-ttu-id="3623b-119">請考慮採用可為 null 實值型別做為輸入的下列方法：</span><span class="sxs-lookup"><span data-stu-id="3623b-119">Consider the following method that takes a nullable value type as input:</span></span>

```fsharp
type C() =
    member _.M(x: Nullable<int>) = x.HasValue
    member val NVT = Nullable 12 with get, set

let c = C()
c.M(12)
c.NVT <- 12
```

<span data-ttu-id="3623b-120">在上述範例中，您可以傳遞 `12` 給方法 `M` 。</span><span class="sxs-lookup"><span data-stu-id="3623b-120">In the previous example, you can pass `12` to the method `M`.</span></span> <span data-ttu-id="3623b-121">您也可以指派 `12` 給 auto 屬性 `NVT` 。</span><span class="sxs-lookup"><span data-stu-id="3623b-121">You can also assign `12` to the auto property `NVT`.</span></span> <span data-ttu-id="3623b-122">如果輸入可視為可為 null 的實值型別，且符合目標型別，則 F # 編譯器會隱含地轉換這類呼叫或指派。</span><span class="sxs-lookup"><span data-stu-id="3623b-122">If the input can be constructed as a nullable value type and it matches the target type, the F# compiler will implicitly convert such calls or assignments.</span></span>

## <a name="examine-a-nullable-value-type-instance"></a><span data-ttu-id="3623b-123">檢查可為 null 的實值型別實例</span><span class="sxs-lookup"><span data-stu-id="3623b-123">Examine a nullable value type instance</span></span>

<span data-ttu-id="3623b-124">不同于代表可能值的一般化結構，可為 null 的實值型別不 [會與模式](options.md)比對搭配使用。</span><span class="sxs-lookup"><span data-stu-id="3623b-124">Unlike [Options](options.md), which are a generalized construct for representing a possible value, nullable value types are not used with pattern matching.</span></span> <span data-ttu-id="3623b-125">相反地，您必須使用 [`if`](conditional-expressions-if-then-else.md) 運算式並檢查 `HasValue` 屬性。</span><span class="sxs-lookup"><span data-stu-id="3623b-125">Instead, you need to use an [`if`](conditional-expressions-if-then-else.md) expression and check the `HasValue` property.</span></span>

<span data-ttu-id="3623b-126">若要取得基礎值，請在 `Value` 檢查之後使用屬性 `HasValue` ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3623b-126">To get the underlying value, use the `Value` property after a `HasValue` check, like so:</span></span>

```fsharp
open System

let a = Nullable 42

if a.HasValue then
    printfn $"{a} is {a.Value}"
else
    printfn $"{a} has no value."
```

## <a name="nullable-operators"></a><span data-ttu-id="3623b-127">可為 null 的運算子</span><span class="sxs-lookup"><span data-stu-id="3623b-127">Nullable operators</span></span>

<span data-ttu-id="3623b-128">針對可為 null 的實數值型別（例如算術或比較）作業，可以使用 [可為 null 的運算子](symbol-and-operator-reference/nullable-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="3623b-128">Operations on nullable value types, such as arithmetic or comparison, can require the use of [nullable operators](symbol-and-operator-reference/nullable-operators.md).</span></span>

<span data-ttu-id="3623b-129">您可以使用命名空間中的轉換運算子，從一個可為 null 的實值型別轉換為另一個 `FSharp.Linq` ：</span><span class="sxs-lookup"><span data-stu-id="3623b-129">You can convert from one nullable value type to another using conversion operators from the `FSharp.Linq` namespace:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt
```

<span data-ttu-id="3623b-130">您也可以使用適當的不可為 null 運算子來轉換為基本型別，如果沒有任何值，則會對例外狀況產生風險：</span><span class="sxs-lookup"><span data-stu-id="3623b-130">You can also use an appropriate non-nullable operator to convert to a primitive type, risking an exception if it has no value:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

printfn $"value is %f{float nullableFloat}"
```

<span data-ttu-id="3623b-131">您也可以使用可為 null 的運算子作為檢查和的短期運算子 `HasValue` `Value` ：</span><span class="sxs-lookup"><span data-stu-id="3623b-131">You can also use nullable operators as a short-hand for checking `HasValue` and `Value`:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

let isBigger = nullableFloat ?> 1.0
let isBiggerLongForm = nullableFloat.HasValue && nullableFloat.Value > 1.0
```

<span data-ttu-id="3623b-132">`?>`比較會檢查左邊是否可為 null，而且只有在有值時才會成功。</span><span class="sxs-lookup"><span data-stu-id="3623b-132">The `?>` comparison checks if the left-hand side is nullable and only succeeds if it has a value.</span></span> <span data-ttu-id="3623b-133">它相當於其後的行。</span><span class="sxs-lookup"><span data-stu-id="3623b-133">It is equivalent to the line that follows it.</span></span>

## <a name="see-also"></a><span data-ttu-id="3623b-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3623b-134">See also</span></span>

- [<span data-ttu-id="3623b-135">結構</span><span class="sxs-lookup"><span data-stu-id="3623b-135">Structures</span></span>](structures.md)
- [<span data-ttu-id="3623b-136">F # 選項</span><span class="sxs-lookup"><span data-stu-id="3623b-136">F# Options</span></span>](options.md)
