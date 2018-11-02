---
title: Null 值 (F#)
description: '了解 F # 程式設計語言中使用 null 值的方式。'
ms.date: 05/16/2016
ms.openlocfilehash: 8751ac402c43ddb07fb62e08b6c6d5403cbe9acc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43787893"
---
# <a name="null-values"></a><span data-ttu-id="d1c95-103">Null 值</span><span class="sxs-lookup"><span data-stu-id="d1c95-103">Null Values</span></span>

<span data-ttu-id="d1c95-104">本主題說明 F # 中使用 null 值的方式。</span><span class="sxs-lookup"><span data-stu-id="d1c95-104">This topic describes how the null value is used in F#.</span></span>

## <a name="null-value"></a><span data-ttu-id="d1c95-105">Null 值</span><span class="sxs-lookup"><span data-stu-id="d1c95-105">Null Value</span></span>

<span data-ttu-id="d1c95-106">Null 值不通常是 F # 中的值或變數。</span><span class="sxs-lookup"><span data-stu-id="d1c95-106">The null value is not normally used in F# for values or variables.</span></span> <span data-ttu-id="d1c95-107">不過，null 會出現在某些情況下異常值。</span><span class="sxs-lookup"><span data-stu-id="d1c95-107">However, null appears as an abnormal value in certain situations.</span></span> <span data-ttu-id="d1c95-108">如果類型定義在 F # 中，允許 null 的不是標準值除非[AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)屬性會套用至型別。</span><span class="sxs-lookup"><span data-stu-id="d1c95-108">If a type is defined in F#, null is not permitted as a regular value unless the [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) attribute is applied to the type.</span></span> <span data-ttu-id="d1c95-109">如果類型定義某些其他.NET 語言中，null 是可能值，而 F # 程式碼時您會在這種型別與交互操作，可能會遇到 null 值。</span><span class="sxs-lookup"><span data-stu-id="d1c95-109">If a type is defined in some other .NET language, null is a possible value, and when you are interoperating with such types, your F# code might encounter null values.</span></span>

<span data-ttu-id="d1c95-110">在 F # 中定義，用於從 F # 是型別，建立 null 值，直接使用 F # 程式庫的唯一方式是使用[Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)或是[Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)。</span><span class="sxs-lookup"><span data-stu-id="d1c95-110">For a type defined in F# and used strictly from F#, the only way to create a null value using the F# library directly is to use [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) or [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2).</span></span> <span data-ttu-id="d1c95-111">不過，F # 型別，會使用從其他.NET 語言，或如果您使用該類型不以 F # 中，例如.NET Framework 撰寫的 api 可能會發生 null 值。</span><span class="sxs-lookup"><span data-stu-id="d1c95-111">However, for an F# type that is used from other .NET languages, or if you are using that type with an API that is not written in F#, such as the .NET Framework, null values can occur.</span></span>

<span data-ttu-id="d1c95-112">您可以使用`option`F # 中會使用最可能的 null 值，另一種.NET 語言的參考變數的類型。</span><span class="sxs-lookup"><span data-stu-id="d1c95-112">You can use the `option` type in F# when you might use a reference variable with a possible null value in another .NET language.</span></span> <span data-ttu-id="d1c95-113">而不是 null，使用 F #`option`類型，您使用的選項值`None`是否有任何物件。</span><span class="sxs-lookup"><span data-stu-id="d1c95-113">Instead of null, with an F# `option` type, you use the option value `None` if there is no object.</span></span> <span data-ttu-id="d1c95-114">您使用的選項值`Some(obj)`的物件`obj`物件時。</span><span class="sxs-lookup"><span data-stu-id="d1c95-114">You use the option value `Some(obj)` with an object `obj` when there is an object.</span></span> <span data-ttu-id="d1c95-115">如需詳細資訊，請參閱 <<c0> [ 選項](../options.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c95-115">For more information, see [Options](../options.md).</span></span>

<span data-ttu-id="d1c95-116">`null`關鍵字是有效的關鍵字，在 F # 語言中，而且您必須使用.NET Framework Api 或以另一種.NET 語言所撰寫的其他 Api 時，請使用它。</span><span class="sxs-lookup"><span data-stu-id="d1c95-116">The `null` keyword is a valid keyword in the F# language, and you have to use it when you are working with .NET Framework APIs or other APIs that are written in another .NET language.</span></span> <span data-ttu-id="d1c95-117">當您呼叫.NET API，並做為引數，傳遞 null 值，並當您解譯傳回的值或.NET 方法呼叫的輸出參數時，就會是兩個，您可能需要 null 值的情況。</span><span class="sxs-lookup"><span data-stu-id="d1c95-117">The two situations in which you might need a null value are when you call a .NET API and pass a null value as an argument, and when you interpret the return value or an output parameter from a .NET method call.</span></span>

<span data-ttu-id="d1c95-118">若要將 null 值傳遞至.NET 方法，只要使用`null`呼叫程式碼中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d1c95-118">To pass a null value to a .NET method, just use the `null` keyword in the calling code.</span></span> <span data-ttu-id="d1c95-119">下列程式碼範例會說明這點。</span><span class="sxs-lookup"><span data-stu-id="d1c95-119">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

<span data-ttu-id="d1c95-120">若要解譯取自於.NET 方法的 null 值，使用模式比對，如果可以的話。</span><span class="sxs-lookup"><span data-stu-id="d1c95-120">To interpret a null value that is obtained from a .NET method, use pattern matching if you can.</span></span> <span data-ttu-id="d1c95-121">下列程式碼範例示範如何使用將從傳回的 null 值的模式比對`ReadLine`當它嘗試讀取超過結尾的輸入資料流。</span><span class="sxs-lookup"><span data-stu-id="d1c95-121">The following code example shows how to use pattern matching to interpret the null value that is returned from `ReadLine` when it tries to read past the end of an input stream.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

<span data-ttu-id="d1c95-122">F # 類型的 null 值也可能以其他方式，例如當您使用會產生`Array.zeroCreate`，其會呼叫`Unchecked.defaultof`。</span><span class="sxs-lookup"><span data-stu-id="d1c95-122">Null values for F# types can also be generated in other ways, such as when you use `Array.zeroCreate`, which calls `Unchecked.defaultof`.</span></span> <span data-ttu-id="d1c95-123">您必須小心這類的程式碼，以保留封裝的 null 值。</span><span class="sxs-lookup"><span data-stu-id="d1c95-123">You must be careful with such code to keep the null values encapsulated.</span></span> <span data-ttu-id="d1c95-124">在僅供 F # 程式庫，您不必檢查每個函式中的 null 值。</span><span class="sxs-lookup"><span data-stu-id="d1c95-124">In a library intended only for F#, you do not have to check for null values in every function.</span></span> <span data-ttu-id="d1c95-125">如果您正在撰寫的程式庫與其他.NET 語言的交互操作，您可能必須新增 null 檢查輸入參數，則擲回`ArgumentNullException`，就像您在 C# 或 Visual Basic 程式碼中。</span><span class="sxs-lookup"><span data-stu-id="d1c95-125">If you are writing a library for interoperation with other .NET languages, you might have to add checks for null input parameters and throw an `ArgumentNullException`, just as you do in C# or Visual Basic code.</span></span>

<span data-ttu-id="d1c95-126">您可以使用下列程式碼來檢查是否為任意值為 null。</span><span class="sxs-lookup"><span data-stu-id="d1c95-126">You can use the following code to check if an arbitrary value is null.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a><span data-ttu-id="d1c95-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1c95-127">See also</span></span>

- [<span data-ttu-id="d1c95-128">值</span><span class="sxs-lookup"><span data-stu-id="d1c95-128">Values</span></span>](index.md)
- [<span data-ttu-id="d1c95-129">比對運算式</span><span class="sxs-lookup"><span data-stu-id="d1c95-129">Match Expressions</span></span>](../match-expressions.md)
