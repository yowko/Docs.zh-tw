---
title: Null 值
description: 瞭解如何在程式F#設計語言中使用 null 值。
ms.date: 03/22/2019
ms.openlocfilehash: 2038c0a461fec9884c51edd50c3c9f336104e30e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630811"
---
# <a name="null-values"></a><span data-ttu-id="d272d-103">Null 值</span><span class="sxs-lookup"><span data-stu-id="d272d-103">Null Values</span></span>

<span data-ttu-id="d272d-104">本主題描述如何在中F#使用 null 值。</span><span class="sxs-lookup"><span data-stu-id="d272d-104">This topic describes how the null value is used in F#.</span></span>

## <a name="null-value"></a><span data-ttu-id="d272d-105">Null 值</span><span class="sxs-lookup"><span data-stu-id="d272d-105">Null Value</span></span>

<span data-ttu-id="d272d-106">Null 值通常不會用於F#值或變數。</span><span class="sxs-lookup"><span data-stu-id="d272d-106">The null value is not normally used in F# for values or variables.</span></span> <span data-ttu-id="d272d-107">不過, 在某些情況下, null 會顯示為異常值。</span><span class="sxs-lookup"><span data-stu-id="d272d-107">However, null appears as an abnormal value in certain situations.</span></span> <span data-ttu-id="d272d-108">如果類型定義于中F#, 除非將[AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)屬性套用至類型, 否則不允許使用 null 做為一般值。</span><span class="sxs-lookup"><span data-stu-id="d272d-108">If a type is defined in F#, null is not permitted as a regular value unless the [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) attribute is applied to the type.</span></span> <span data-ttu-id="d272d-109">如果類型是以其他 .NET 語言定義, null 是可能的值, 而當您與這類類型互通時, 您的F#程式碼可能會遇到 null 值。</span><span class="sxs-lookup"><span data-stu-id="d272d-109">If a type is defined in some other .NET language, null is a possible value, and when you are interoperating with such types, your F# code might encounter null values.</span></span>

<span data-ttu-id="d272d-110">針對F#中定義且完全使用的類型F#, 使用連結F#庫直接建立 null 值的唯一方法是使用[unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)或[array.zerocreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)。</span><span class="sxs-lookup"><span data-stu-id="d272d-110">For a type defined in F# and used strictly from F#, the only way to create a null value using the F# library directly is to use [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) or [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2).</span></span> <span data-ttu-id="d272d-111">不過, 針對從F#其他 .net 語言使用的類型, 或如果您使用該類型搭配未寫入F#的 API (例如 .NET Framework, 則可能會出現 null 值)。</span><span class="sxs-lookup"><span data-stu-id="d272d-111">However, for an F# type that is used from other .NET languages, or if you are using that type with an API that is not written in F#, such as the .NET Framework, null values can occur.</span></span>

<span data-ttu-id="d272d-112">當您可能在`option`另一個F# .net 語言中使用具有可能 null 值的參考變數時, 可以使用中的類型。</span><span class="sxs-lookup"><span data-stu-id="d272d-112">You can use the `option` type in F# when you might use a reference variable with a possible null value in another .NET language.</span></span> <span data-ttu-id="d272d-113">若不是 null, F# `option`則使用類型, 如果沒有物件, `None`您可以使用選項值。</span><span class="sxs-lookup"><span data-stu-id="d272d-113">Instead of null, with an F# `option` type, you use the option value `None` if there is no object.</span></span> <span data-ttu-id="d272d-114">當有物件時, `Some(obj)`您可以使用`obj`選項值搭配物件。</span><span class="sxs-lookup"><span data-stu-id="d272d-114">You use the option value `Some(obj)` with an object `obj` when there is an object.</span></span> <span data-ttu-id="d272d-115">如需詳細資訊，請參閱[選項](../options.md)。</span><span class="sxs-lookup"><span data-stu-id="d272d-115">For more information, see [Options](../options.md).</span></span> <span data-ttu-id="d272d-116">請注意`null` , 如果 (for `Some x`) `x`剛好是`null`, 您仍然可以將值封裝成一個選項。</span><span class="sxs-lookup"><span data-stu-id="d272d-116">Note that you can still pack a `null` value into an Option if, for `Some x`, `x` happens to be `null`.</span></span> <span data-ttu-id="d272d-117">因此, 當值為`None` `null`時, 請務必使用。</span><span class="sxs-lookup"><span data-stu-id="d272d-117">Because of this, it is important you use `None` when a value is `null`.</span></span>

<span data-ttu-id="d272d-118">關鍵字是F#語言中的有效關鍵字, 而且當您使用以其他 .net 語言撰寫的 .NET Framework api 或其他 api 時, 您必須使用它。 `null`</span><span class="sxs-lookup"><span data-stu-id="d272d-118">The `null` keyword is a valid keyword in the F# language, and you have to use it when you are working with .NET Framework APIs or other APIs that are written in another .NET language.</span></span> <span data-ttu-id="d272d-119">當您呼叫 .NET API 並傳遞 null 值做為引數, 以及從 .NET 方法呼叫解讀傳回值或輸出參數時, 這兩種情況下, 您可能會需要 null 值。</span><span class="sxs-lookup"><span data-stu-id="d272d-119">The two situations in which you might need a null value are when you call a .NET API and pass a null value as an argument, and when you interpret the return value or an output parameter from a .NET method call.</span></span>

<span data-ttu-id="d272d-120">若要將 null 值傳遞給 .net 方法, 只要在呼叫`null`程式碼中使用關鍵字即可。</span><span class="sxs-lookup"><span data-stu-id="d272d-120">To pass a null value to a .NET method, just use the `null` keyword in the calling code.</span></span> <span data-ttu-id="d272d-121">下列程式碼範例會說明這點。</span><span class="sxs-lookup"><span data-stu-id="d272d-121">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

<span data-ttu-id="d272d-122">若要解讀從 .NET 方法取得的 null 值, 請使用模式比對 (如果可以的話)。</span><span class="sxs-lookup"><span data-stu-id="d272d-122">To interpret a null value that is obtained from a .NET method, use pattern matching if you can.</span></span> <span data-ttu-id="d272d-123">下列程式碼範例示範如何使用模式比對, 來解讀`ReadLine`當它嘗試讀取超過輸入資料流程的結尾時, 所傳回的 null 值。</span><span class="sxs-lookup"><span data-stu-id="d272d-123">The following code example shows how to use pattern matching to interpret the null value that is returned from `ReadLine` when it tries to read past the end of an input stream.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

<span data-ttu-id="d272d-124">類型的F# Null 值也可以用其他方式產生, 例如當您使用`Array.zeroCreate`時, 會呼叫。 `Unchecked.defaultof`</span><span class="sxs-lookup"><span data-stu-id="d272d-124">Null values for F# types can also be generated in other ways, such as when you use `Array.zeroCreate`, which calls `Unchecked.defaultof`.</span></span> <span data-ttu-id="d272d-125">您必須謹慎處理這類程式碼, 才能將 null 值封裝起來。</span><span class="sxs-lookup"><span data-stu-id="d272d-125">You must be careful with such code to keep the null values encapsulated.</span></span> <span data-ttu-id="d272d-126">在僅供使用的F#程式庫中, 您不需要在每個函式中檢查是否有 null 值。</span><span class="sxs-lookup"><span data-stu-id="d272d-126">In a library intended only for F#, you do not have to check for null values in every function.</span></span> <span data-ttu-id="d272d-127">如果您要撰寫與其他 .net 語言互通的程式庫, 您可能必須新增 null 輸入參數的檢查, 並擲`ArgumentNullException`回, 就如同您在或 Visual Basic 程式碼中C#所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="d272d-127">If you are writing a library for interoperation with other .NET languages, you might have to add checks for null input parameters and throw an `ArgumentNullException`, just as you do in C# or Visual Basic code.</span></span>

<span data-ttu-id="d272d-128">您可以使用下列程式碼來檢查任意值是否為 null。</span><span class="sxs-lookup"><span data-stu-id="d272d-128">You can use the following code to check if an arbitrary value is null.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a><span data-ttu-id="d272d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d272d-129">See also</span></span>

- [<span data-ttu-id="d272d-130">值</span><span class="sxs-lookup"><span data-stu-id="d272d-130">Values</span></span>](index.md)
- [<span data-ttu-id="d272d-131">比對運算式</span><span class="sxs-lookup"><span data-stu-id="d272d-131">Match Expressions</span></span>](../match-expressions.md)
