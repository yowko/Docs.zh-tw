---
title: 值的選項
description: 瞭解F#值選項類型，這是選項類型的結構版本。
ms.date: 02/06/2019
ms.openlocfilehash: 4dc3f7217943345b7aaf1165fd648ab2e01bd727
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424011"
---
# <a name="value-options"></a><span data-ttu-id="e6c99-103">值的選項</span><span class="sxs-lookup"><span data-stu-id="e6c99-103">Value Options</span></span>

<span data-ttu-id="e6c99-104">當下列兩種情況F#成立時，會使用值選項輸入：</span><span class="sxs-lookup"><span data-stu-id="e6c99-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="e6c99-105">案例適用于[ F#選項](options.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c99-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="e6c99-106">使用結構可在您的案例中提供效能優勢。</span><span class="sxs-lookup"><span data-stu-id="e6c99-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="e6c99-107">並非所有的效能相關案例都是使用結構來「解決」。</span><span class="sxs-lookup"><span data-stu-id="e6c99-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="e6c99-108">使用時，您必須考慮複製的額外成本，而不是參考型別。</span><span class="sxs-lookup"><span data-stu-id="e6c99-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="e6c99-109">不過，大型F#程式通常會具現化許多可流經最忙碌路徑的選擇性類型，在這種情況下，結構通常可以在程式的存留期內產生較佳的整體效能。</span><span class="sxs-lookup"><span data-stu-id="e6c99-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, and in such cases, structs can often yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="e6c99-110">定義</span><span class="sxs-lookup"><span data-stu-id="e6c99-110">Definition</span></span>

<span data-ttu-id="e6c99-111">Value 選項會定義為[結構的區分](discriminated-unions.md#struct-discriminated-unions)等位，與參考選項類型類似。</span><span class="sxs-lookup"><span data-stu-id="e6c99-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="e6c99-112">其定義可以透過這種方式來考慮：</span><span class="sxs-lookup"><span data-stu-id="e6c99-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="e6c99-113">Value 選項符合結構相等和比較。</span><span class="sxs-lookup"><span data-stu-id="e6c99-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="e6c99-114">主要差異在於編譯的名稱、型別名稱和大小寫名稱全都表示它是實值型別。</span><span class="sxs-lookup"><span data-stu-id="e6c99-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="e6c99-115">使用值選項</span><span class="sxs-lookup"><span data-stu-id="e6c99-115">Using Value Options</span></span>

<span data-ttu-id="e6c99-116">值選項的使用方式就像[選項](options.md)一樣。</span><span class="sxs-lookup"><span data-stu-id="e6c99-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="e6c99-117">`ValueSome` 可用來表示值存在，而且當值不存在時，會使用 `ValueNone`：</span><span class="sxs-lookup"><span data-stu-id="e6c99-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

```fsharp
let tryParseDateTime (s: string) =
    match System.DateTime.TryParse(s) with
    | (true, dt) -> ValueSome dt
    | (false, _) -> ValueNone

let possibleDateString1 = "1990-12-25"
let possibleDateString2 = "This is not a date"

let result1 = tryParseDateTime possibleDateString1
let result2 = tryParseDateTime possibleDateString2

match (result1, result2) with
| ValueSome d1, ValueSome d2 -> printfn "Both are dates!"
| ValueSome d1, ValueNone -> printfn "Only the first is a date!"
| ValueNone, ValueSome d2 -> printfn "Only the second is a date!"
| ValueNone, ValueNone -> printfn "None of them are dates!"
```

<span data-ttu-id="e6c99-118">如同[選項](options.md)，傳回 `ValueOption` 之函式的命名慣例是在其前面加上 `try`。</span><span class="sxs-lookup"><span data-stu-id="e6c99-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="e6c99-119">值選項屬性和方法</span><span class="sxs-lookup"><span data-stu-id="e6c99-119">Value Option properties and methods</span></span>

<span data-ttu-id="e6c99-120">目前有一個屬性用於值選項： `Value`。</span><span class="sxs-lookup"><span data-stu-id="e6c99-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="e6c99-121">叫用此屬性時，如果沒有任何值存在，就會引發 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="e6c99-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="e6c99-122">值選項函數</span><span class="sxs-lookup"><span data-stu-id="e6c99-122">Value Option functions</span></span>

<span data-ttu-id="e6c99-123">目前有一個模組系結函數適用于值選項，`defaultValueArg`：</span><span class="sxs-lookup"><span data-stu-id="e6c99-123">There is currently one module-bound function for Value Options, `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

<span data-ttu-id="e6c99-124">如同 `defaultArg` 函式，`defaultValueArg` 會傳回指定值選項的基礎值（如果有的話）。否則，它會傳回指定的預設值。</span><span class="sxs-lookup"><span data-stu-id="e6c99-124">As with the `defaultArg` function, `defaultValueArg` returns the underlying value of the given Value Option if it exists; otherwise, it returns the specified default value.</span></span>

<span data-ttu-id="e6c99-125">目前沒有適用于值選項的其他模組系結函數。</span><span class="sxs-lookup"><span data-stu-id="e6c99-125">At this time, there are no other module-bound functions for Value Options.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6c99-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="e6c99-126">See also</span></span>

- [<span data-ttu-id="e6c99-127">選項</span><span class="sxs-lookup"><span data-stu-id="e6c99-127">Options</span></span>](options.md)
