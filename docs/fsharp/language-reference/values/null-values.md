---
title: Null 值 (F#)
description: '了解如何使用 F # 程式語言中的 null 值。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 8d302cc78c5de582f58c6f9b9dea7b23ee7ddfea
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="null-values"></a><span data-ttu-id="c95a6-103">Null 值</span><span class="sxs-lookup"><span data-stu-id="c95a6-103">Null Values</span></span>

<span data-ttu-id="c95a6-104">本主題描述如何使用 F # 中的 null 值。</span><span class="sxs-lookup"><span data-stu-id="c95a6-104">This topic describes how the null value is used in F#.</span></span>


## <a name="null-value"></a><span data-ttu-id="c95a6-105">Null 值</span><span class="sxs-lookup"><span data-stu-id="c95a6-105">Null Value</span></span>
<span data-ttu-id="c95a6-106">Null 值已不正常 F # 中使用的值或變數。</span><span class="sxs-lookup"><span data-stu-id="c95a6-106">The null value is not normally used in F# for values or variables.</span></span> <span data-ttu-id="c95a6-107">不過，null 會顯示為在某些情況下的異常值。</span><span class="sxs-lookup"><span data-stu-id="c95a6-107">However, null appears as an abnormal value in certain situations.</span></span> <span data-ttu-id="c95a6-108">如果類型定義在 F # 中，允許 null 的不是標準值除非[AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)屬性套用至類型。</span><span class="sxs-lookup"><span data-stu-id="c95a6-108">If a type is defined in F#, null is not permitted as a regular value unless the [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) attribute is applied to the type.</span></span> <span data-ttu-id="c95a6-109">如果類型定義在其他.NET 語言中，null 是可能值，且當您進行交互操作，使用這類的類型，F # 程式碼可能會遇到 null 值。</span><span class="sxs-lookup"><span data-stu-id="c95a6-109">If a type is defined in some other .NET language, null is a possible value, and when you are interoperating with such types, your F# code might encounter null values.</span></span>

<span data-ttu-id="c95a6-110">在 F # 中定義和使用嚴格地從 F # 類型建立 null 值，並直接使用 F # 程式庫的唯一方式是使用[Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)或[Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)。</span><span class="sxs-lookup"><span data-stu-id="c95a6-110">For a type defined in F# and used strictly from F#, the only way to create a null value using the F# library directly is to use [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) or [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2).</span></span> <span data-ttu-id="c95a6-111">不過，F # 型別，會使用其他.NET 語言，或如果您正在使用在 F # 中，例如.NET Framework 中，不會寫入應用程式開發介面中的該類型可能會發生 null 值。</span><span class="sxs-lookup"><span data-stu-id="c95a6-111">However, for an F# type that is used from other .NET languages, or if you are using that type with an API that is not written in F#, such as the .NET Framework, null values can occur.</span></span>

<span data-ttu-id="c95a6-112">您可以使用`option`F # 中會使用參考變數與另一種.NET 語言中可能的 null 值的類型。</span><span class="sxs-lookup"><span data-stu-id="c95a6-112">You can use the `option` type in F# when you might use a reference variable with a possible null value in another .NET language.</span></span> <span data-ttu-id="c95a6-113">而不是 null，F #`option`類型，您使用的選項值`None`如果沒有任何物件。</span><span class="sxs-lookup"><span data-stu-id="c95a6-113">Instead of null, with an F# `option` type, you use the option value `None` if there is no object.</span></span> <span data-ttu-id="c95a6-114">您使用的選項值`Some(obj)`物件`obj`物件時。</span><span class="sxs-lookup"><span data-stu-id="c95a6-114">You use the option value `Some(obj)` with an object `obj` when there is an object.</span></span> <span data-ttu-id="c95a6-115">如需詳細資訊，請參閱[選項](../options.md)。</span><span class="sxs-lookup"><span data-stu-id="c95a6-115">For more information, see [Options](../options.md).</span></span>

<span data-ttu-id="c95a6-116">`null`關鍵字是有效的關鍵字，在 F # 語言中，而且您必須使用.NET Framework 應用程式開發介面或其他以另一種.NET 語言撰寫的應用程式開發介面時，請使用它。</span><span class="sxs-lookup"><span data-stu-id="c95a6-116">The `null` keyword is a valid keyword in the F# language, and you have to use it when you are working with .NET Framework APIs or other APIs that are written in another .NET language.</span></span> <span data-ttu-id="c95a6-117">您可能需要 null 值的兩個情況是當您呼叫.NET API，並做為引數，傳遞 null 值，而且當您解譯傳回的值或輸出參數從.NET 方法呼叫時。</span><span class="sxs-lookup"><span data-stu-id="c95a6-117">The two situations in which you might need a null value are when you call a .NET API and pass a null value as an argument, and when you interpret the return value or an output parameter from a .NET method call.</span></span>

<span data-ttu-id="c95a6-118">若要傳遞 null 值的.NET 方法，只要使用`null`呼叫的程式碼中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c95a6-118">To pass a null value to a .NET method, just use the `null` keyword in the calling code.</span></span> <span data-ttu-id="c95a6-119">下列程式碼範例會說明這點。</span><span class="sxs-lookup"><span data-stu-id="c95a6-119">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

<span data-ttu-id="c95a6-120">若要解譯 null 值取自.NET 方法，使用模式比對，如果可以的話。</span><span class="sxs-lookup"><span data-stu-id="c95a6-120">To interpret a null value that is obtained from a .NET method, use pattern matching if you can.</span></span> <span data-ttu-id="c95a6-121">下列程式碼範例示範如何使用模式比對，解譯傳回的 null 值`ReadLine`當它嘗試讀取的輸入資料流結尾。</span><span class="sxs-lookup"><span data-stu-id="c95a6-121">The following code example shows how to use pattern matching to interpret the null value that is returned from `ReadLine` when it tries to read past the end of an input stream.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

<span data-ttu-id="c95a6-122">F # 類型的 null 值，也可以產生以其他方式，例如當您使用`Array.zeroCreate`，而它會呼叫`Unchecked.defaultof`。</span><span class="sxs-lookup"><span data-stu-id="c95a6-122">Null values for F# types can also be generated in other ways, such as when you use `Array.zeroCreate`, which calls `Unchecked.defaultof`.</span></span> <span data-ttu-id="c95a6-123">您必須非常小心這類程式碼，以保留封裝 null 值。</span><span class="sxs-lookup"><span data-stu-id="c95a6-123">You must be careful with such code to keep the null values encapsulated.</span></span> <span data-ttu-id="c95a6-124">在僅供 F # 程式庫，您不必檢查每個函式中的 null 值。</span><span class="sxs-lookup"><span data-stu-id="c95a6-124">In a library intended only for F#, you do not have to check for null values in every function.</span></span> <span data-ttu-id="c95a6-125">如果您正在撰寫的程式庫的其他.NET 語言進行交互操作，您可能必須新增檢查 null 輸入參數，則擲回`ArgumentNullException`，就像您在 C# 或 Visual Basic 程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="c95a6-125">If you are writing a library for interoperation with other .NET languages, you might have to add checks for null input parameters and throw an `ArgumentNullException`, just as you do in C# or Visual Basic code.</span></span>

<span data-ttu-id="c95a6-126">您可以使用下列程式碼來檢查是否為 null 的任意值。</span><span class="sxs-lookup"><span data-stu-id="c95a6-126">You can use the following code to check if an arbitrary value is null.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a><span data-ttu-id="c95a6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c95a6-127">See Also</span></span>
[<span data-ttu-id="c95a6-128">值</span><span class="sxs-lookup"><span data-stu-id="c95a6-128">Values</span></span>](index.md)

[<span data-ttu-id="c95a6-129">比對運算式</span><span class="sxs-lookup"><span data-stu-id="c95a6-129">Match Expressions</span></span>](../match-expressions.md)
