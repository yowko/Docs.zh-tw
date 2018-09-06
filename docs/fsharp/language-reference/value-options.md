---
title: '值的選項 （F #）'
description: '深入了解 F # 值選項類型，也就是結構類型版本的選項。'
ms.date: 06/16/2018
ms.openlocfilehash: 5647ef61725401b10a6045b14eef11f5b041e3e9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747495"
---
# <a name="value-options"></a><span data-ttu-id="4ab91-103">值的選項</span><span class="sxs-lookup"><span data-stu-id="4ab91-103">Value Options</span></span>

<span data-ttu-id="4ab91-104">在下列兩種情況下保存時，會使用 F # 中的值選項類型：</span><span class="sxs-lookup"><span data-stu-id="4ab91-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="4ab91-105">案例是適用於[F # 選項](options.md)。</span><span class="sxs-lookup"><span data-stu-id="4ab91-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="4ab91-106">使用結構可提供效能優勢，在您的案例。</span><span class="sxs-lookup"><span data-stu-id="4ab91-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="4ab91-107">並非所有效能敏感的狀況下會 「 都解決 」 使用結構。</span><span class="sxs-lookup"><span data-stu-id="4ab91-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="4ab91-108">您必須考慮複製時使用它們，而不參考類型的額外成本。</span><span class="sxs-lookup"><span data-stu-id="4ab91-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="4ab91-109">不過，大型的 F # 程式通常具現化許多選擇性類型流經忙碌的路徑，因為結構有時可以產生更好的整體效能程式存留期。</span><span class="sxs-lookup"><span data-stu-id="4ab91-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, because structs can sometimes yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="4ab91-110">定義</span><span class="sxs-lookup"><span data-stu-id="4ab91-110">Definition</span></span>

<span data-ttu-id="4ab91-111">值選項指[結構差別聯集](discriminated-unions.md#struct-discriminated-unions)類似參考選項類型：</span><span class="sxs-lookup"><span data-stu-id="4ab91-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpValueOption`1")>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone: 'T voption
    | ValueSome: 'T -> 'T voption

    member Value : 'T

and 'T voption = ValueOption<'T>
```

<span data-ttu-id="4ab91-112">結構化相等和比較符合值 選項。</span><span class="sxs-lookup"><span data-stu-id="4ab91-112">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="4ab91-113">主要差異在於編譯的名稱、 型別名稱和大小寫名稱所有指出它是實值型別。</span><span class="sxs-lookup"><span data-stu-id="4ab91-113">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="4ab91-114">使用值的選項</span><span class="sxs-lookup"><span data-stu-id="4ab91-114">Using Value Options</span></span>

<span data-ttu-id="4ab91-115">就像使用值選項[選項](options.md)。</span><span class="sxs-lookup"><span data-stu-id="4ab91-115">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="4ab91-116">`ValueSome` 用來表示值已存在，及`ValueNone`值不存在時，會使用：</span><span class="sxs-lookup"><span data-stu-id="4ab91-116">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

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

<span data-ttu-id="4ab91-117">如同[選項](options.md)，傳回的函式的命名慣例`ValueOption`會加上前置詞與`try`。</span><span class="sxs-lookup"><span data-stu-id="4ab91-117">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="4ab91-118">值選項屬性和方法</span><span class="sxs-lookup"><span data-stu-id="4ab91-118">Value Option properties and methods</span></span>

<span data-ttu-id="4ab91-119">此時沒有一個屬性的值選項： `Value`。</span><span class="sxs-lookup"><span data-stu-id="4ab91-119">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="4ab91-120"><xref:System.InvalidOperationException>沒有值是否存在叫用這個屬性時引發。</span><span class="sxs-lookup"><span data-stu-id="4ab91-120">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="4ab91-121">值選項函式</span><span class="sxs-lookup"><span data-stu-id="4ab91-121">Value Option functions</span></span>

<span data-ttu-id="4ab91-122">目前沒有一個模組繫結函式的值選項`defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="4ab91-122">There is currently one module-bound function for Value Options, `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T 
```

<span data-ttu-id="4ab91-123">如同`defaultArg`函式，`defaultValueArg`傳回指定的 [值] 選項的基礎值，如果存在的話，否則會傳回指定的預設值。</span><span class="sxs-lookup"><span data-stu-id="4ab91-123">As with the `defaultArg` function, `defaultValueArg` returns the underlying value of the given Value Option if it exists; otherwise, it returns the specified default value.</span></span>

<span data-ttu-id="4ab91-124">在此階段中，沒有其他模組繫結函數的值選項。</span><span class="sxs-lookup"><span data-stu-id="4ab91-124">At this time, there are no other module-bound functions for Value Options.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ab91-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ab91-125">See also</span></span>

- [<span data-ttu-id="4ab91-126">選項</span><span class="sxs-lookup"><span data-stu-id="4ab91-126">Options</span></span>](options.md)