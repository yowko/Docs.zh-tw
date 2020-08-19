---
title: Null 值
description: '瞭解如何在 F # 程式設計語言中使用 null 值。'
ms.date: 08/15/2020
ms.openlocfilehash: 3b2c7ebe7b8eff08f7c3e76b9715ccab1bbd5d36
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558344"
---
# <a name="null-values"></a><span data-ttu-id="ed210-103">Null 值</span><span class="sxs-lookup"><span data-stu-id="ed210-103">Null Values</span></span>

<span data-ttu-id="ed210-104">本主題說明如何在 F # 中使用 null 值。</span><span class="sxs-lookup"><span data-stu-id="ed210-104">This topic describes how the null value is used in F#.</span></span>

## <a name="null-value"></a><span data-ttu-id="ed210-105">Null 值</span><span class="sxs-lookup"><span data-stu-id="ed210-105">Null Value</span></span>

<span data-ttu-id="ed210-106">Null 值通常不會用於 F # 中的值或變數。</span><span class="sxs-lookup"><span data-stu-id="ed210-106">The null value is not normally used in F# for values or variables.</span></span> <span data-ttu-id="ed210-107">不過，在某些情況下，null 會顯示為異常值。</span><span class="sxs-lookup"><span data-stu-id="ed210-107">However, null appears as an abnormal value in certain situations.</span></span> <span data-ttu-id="ed210-108">如果類型是在 F # 中定義，除非將 [AllowNullLiteral](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-allownullliteralattribute.html#Value) 屬性套用至類型，否則不允許使用 null 作為一般值。</span><span class="sxs-lookup"><span data-stu-id="ed210-108">If a type is defined in F#, null is not permitted as a regular value unless the [AllowNullLiteral](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-allownullliteralattribute.html#Value) attribute is applied to the type.</span></span> <span data-ttu-id="ed210-109">如果類型是以其他 .NET 語言定義，null 是可能的值，而且當您與這類型別互通時，F # 程式碼可能會遇到 null 值。</span><span class="sxs-lookup"><span data-stu-id="ed210-109">If a type is defined in some other .NET language, null is a possible value, and when you are interoperating with such types, your F# code might encounter null values.</span></span>

<span data-ttu-id="ed210-110">針對 F # 中定義且嚴格地使用 f # 的型別，直接使用 F # 程式庫建立 null 值的唯一方法是使用 [Unchecked unchecked.defaultof](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators-unchecked.html#defaultof) 或 [array2d.zerocreate](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate)。</span><span class="sxs-lookup"><span data-stu-id="ed210-110">For a type defined in F# and used strictly from F#, the only way to create a null value using the F# library directly is to use [Unchecked.defaultof](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators-unchecked.html#defaultof) or [Array.zeroCreate](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate).</span></span> <span data-ttu-id="ed210-111">不過，針對從其他 .NET 語言使用的 F # 類型，或如果您使用的是不是以 F # 撰寫的 API （例如 .NET Framework），則可能會發生 null 值。</span><span class="sxs-lookup"><span data-stu-id="ed210-111">However, for an F# type that is used from other .NET languages, or if you are using that type with an API that is not written in F#, such as the .NET Framework, null values can occur.</span></span>

<span data-ttu-id="ed210-112">您可以使用 `option` F # 中的型別，因為您可能會在另一個 .net 語言中使用具有可能 null 值的參考變數。</span><span class="sxs-lookup"><span data-stu-id="ed210-112">You can use the `option` type in F# when you might use a reference variable with a possible null value in another .NET language.</span></span> <span data-ttu-id="ed210-113">`option`如果沒有任何物件，則您可以使用選項值（如果沒有物件），而不是 null `None` 。</span><span class="sxs-lookup"><span data-stu-id="ed210-113">Instead of null, with an F# `option` type, you use the option value `None` if there is no object.</span></span> <span data-ttu-id="ed210-114">`Some(obj)`當有物件時，您可以使用選項值與物件 `obj` 。</span><span class="sxs-lookup"><span data-stu-id="ed210-114">You use the option value `Some(obj)` with an object `obj` when there is an object.</span></span> <span data-ttu-id="ed210-115">如需詳細資訊，請參閱[選項](../options.md)。</span><span class="sxs-lookup"><span data-stu-id="ed210-115">For more information, see [Options](../options.md).</span></span> <span data-ttu-id="ed210-116">請注意，如果是，則您仍然可以 `null` 將值封裝至選項中 `Some x` `x` `null` 。</span><span class="sxs-lookup"><span data-stu-id="ed210-116">Note that you can still pack a `null` value into an Option if, for `Some x`, `x` happens to be `null`.</span></span> <span data-ttu-id="ed210-117">因此，當值為時，請務必使用此 `None` 值 `null` 。</span><span class="sxs-lookup"><span data-stu-id="ed210-117">Because of this, it is important you use `None` when a value is `null`.</span></span>

<span data-ttu-id="ed210-118">`null`關鍵字是 F # 語言中的有效關鍵字，當您使用以其他 .net 語言撰寫的 .NET Framework api 或其他 api 時，您必須使用此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ed210-118">The `null` keyword is a valid keyword in the F# language, and you have to use it when you are working with .NET Framework APIs or other APIs that are written in another .NET language.</span></span> <span data-ttu-id="ed210-119">在兩種情況下，您可能需要 null 值，就是當您呼叫 .NET API 並將 null 值當作引數傳遞時，以及當您從 .NET 方法呼叫中解讀傳回值或輸出參數時。</span><span class="sxs-lookup"><span data-stu-id="ed210-119">The two situations in which you might need a null value are when you call a .NET API and pass a null value as an argument, and when you interpret the return value or an output parameter from a .NET method call.</span></span>

<span data-ttu-id="ed210-120">若要將 null 值傳遞至 .NET 方法，只需在 `null` 呼叫程式碼中使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ed210-120">To pass a null value to a .NET method, just use the `null` keyword in the calling code.</span></span> <span data-ttu-id="ed210-121">下列程式碼範例會說明這點。</span><span class="sxs-lookup"><span data-stu-id="ed210-121">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

<span data-ttu-id="ed210-122">若要解讀從 .NET 方法取得的 null 值，請使用模式比對（如果可以的話）。</span><span class="sxs-lookup"><span data-stu-id="ed210-122">To interpret a null value that is obtained from a .NET method, use pattern matching if you can.</span></span> <span data-ttu-id="ed210-123">下列程式碼範例示範如何使用模式比對來解讀 `ReadLine` 當它嘗試讀取超過輸入資料流程結尾時所傳回的 null 值。</span><span class="sxs-lookup"><span data-stu-id="ed210-123">The following code example shows how to use pattern matching to interpret the null value that is returned from `ReadLine` when it tries to read past the end of an input stream.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

<span data-ttu-id="ed210-124">F # 類型的 Null 值也可以使用其他方式產生，例如，當您使用時，會 `Array.zeroCreate` 呼叫 `Unchecked.defaultof` 。</span><span class="sxs-lookup"><span data-stu-id="ed210-124">Null values for F# types can also be generated in other ways, such as when you use `Array.zeroCreate`, which calls `Unchecked.defaultof`.</span></span> <span data-ttu-id="ed210-125">您必須小心使用這類程式碼，以將 null 值保持封裝。</span><span class="sxs-lookup"><span data-stu-id="ed210-125">You must be careful with such code to keep the null values encapsulated.</span></span> <span data-ttu-id="ed210-126">在僅供 F # 使用的程式庫中，您不需要在每個函式中檢查是否有 null 值。</span><span class="sxs-lookup"><span data-stu-id="ed210-126">In a library intended only for F#, you do not have to check for null values in every function.</span></span> <span data-ttu-id="ed210-127">如果您要撰寫與其他 .NET 語言交互操作的程式庫，您可能必須加入 null 輸入參數的檢查並擲回 `ArgumentNullException` ，就像在 c # 或 Visual Basic 程式碼中所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="ed210-127">If you are writing a library for interoperation with other .NET languages, you might have to add checks for null input parameters and throw an `ArgumentNullException`, just as you do in C# or Visual Basic code.</span></span>

<span data-ttu-id="ed210-128">您可以使用下列程式碼來檢查任意值是否為 null。</span><span class="sxs-lookup"><span data-stu-id="ed210-128">You can use the following code to check if an arbitrary value is null.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a><span data-ttu-id="ed210-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed210-129">See also</span></span>

- [<span data-ttu-id="ed210-130">值</span><span class="sxs-lookup"><span data-stu-id="ed210-130">Values</span></span>](index.md)
- [<span data-ttu-id="ed210-131">比對運算式</span><span class="sxs-lookup"><span data-stu-id="ed210-131">Match Expressions</span></span>](../match-expressions.md)
