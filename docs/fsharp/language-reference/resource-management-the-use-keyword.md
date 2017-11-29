---
title: "資源管理：use 關鍵字 (F#)"
description: "了解 F # 關鍵字 'use' 和 '使用' 函式，可以控制的初始設定和版本的資源。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 00c3040e-859f-4dad-a7b5-7b8d44dc232c
ms.openlocfilehash: d4e8626f07f1c77e52e8fabd5ccc07dbf1fa8ddd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="accdb-104">資源管理：use 關鍵字</span><span class="sxs-lookup"><span data-stu-id="accdb-104">Resource Management: The use Keyword</span></span>

<span data-ttu-id="accdb-105">本主題描述關鍵字`use`和`using`函式，可以控制的初始設定和版本的資源。</span><span class="sxs-lookup"><span data-stu-id="accdb-105">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="accdb-106">資源</span><span class="sxs-lookup"><span data-stu-id="accdb-106">Resources</span></span>
<span data-ttu-id="accdb-107">詞彙*資源*以一個以上的方式使用。</span><span class="sxs-lookup"><span data-stu-id="accdb-107">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="accdb-108">[是]，資源可以是應用程式使用，例如字串、 圖形和類似項目，但在此內容中的資料*資源*指的是軟體或作業系統的資源，例如圖形裝置內容、 檔案控制代碼、 網路和資料庫的連接、 並行的物件，例如等候控制代碼，依此類推。</span><span class="sxs-lookup"><span data-stu-id="accdb-108">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="accdb-109">使用這些資源應用程式所牽涉到來自作業系統或其他資源提供者，後面接著之後版本的資源集區，讓它可以提供給另一個應用程式的資源擷取。</span><span class="sxs-lookup"><span data-stu-id="accdb-109">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="accdb-110">當應用程式不會釋放回一般的集區的資源時，會發生問題。</span><span class="sxs-lookup"><span data-stu-id="accdb-110">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="accdb-111">管理資源</span><span class="sxs-lookup"><span data-stu-id="accdb-111">Managing Resources</span></span>
<span data-ttu-id="accdb-112">若要有效率地和以負責的態度管理應用程式中的資源，您必須釋放資源，立即和可預測的方式。</span><span class="sxs-lookup"><span data-stu-id="accdb-112">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="accdb-113">.NET Framework 可協助您藉由提供執行這項操作`System.IDisposable`介面。</span><span class="sxs-lookup"><span data-stu-id="accdb-113">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="accdb-114">實作的型別`System.IDisposable`具有`System.IDisposable.Dispose`方法，這個方法會正確地釋放資源。</span><span class="sxs-lookup"><span data-stu-id="accdb-114">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="accdb-115">編寫完善的應用程式保證`System.IDisposable.Dispose`持有有限的資源的任何物件已不再需要時立即呼叫。</span><span class="sxs-lookup"><span data-stu-id="accdb-115">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="accdb-116">幸運的是，大部分的.NET 語言會提供支援服務以進行簡化，而 F # 也不例外。</span><span class="sxs-lookup"><span data-stu-id="accdb-116">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="accdb-117">有兩個有用的語言建構，支援的處置模式：`use`繫結和`using`函式。</span><span class="sxs-lookup"><span data-stu-id="accdb-117">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="accdb-118">使用繫結</span><span class="sxs-lookup"><span data-stu-id="accdb-118">use Binding</span></span>
<span data-ttu-id="accdb-119">`use`關鍵字有類似的形式`let`繫結：</span><span class="sxs-lookup"><span data-stu-id="accdb-119">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="accdb-120">使用*值* = *運算式*</span><span class="sxs-lookup"><span data-stu-id="accdb-120">use *value* = *expression*</span></span>

<span data-ttu-id="accdb-121">它會提供相同的功能`let`繫結，但將呼叫加入`Dispose`值超出範圍時的值。</span><span class="sxs-lookup"><span data-stu-id="accdb-121">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="accdb-122">請注意，編譯器會插入 null 值時，檢查，因此，如果值會`null`，呼叫`Dispose`未嘗試。</span><span class="sxs-lookup"><span data-stu-id="accdb-122">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="accdb-123">下列範例示範如何使用自動關閉檔案`use`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="accdb-123">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
<span data-ttu-id="accdb-124">您可以使用`use`在計算運算式中，在此情況下的自訂的版本`use`運算式使用。</span><span class="sxs-lookup"><span data-stu-id="accdb-124">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="accdb-125">如需詳細資訊，請參閱[序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，和[計算運算式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="accdb-125">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="using-function"></a><span data-ttu-id="accdb-126">使用函式</span><span class="sxs-lookup"><span data-stu-id="accdb-126">using Function</span></span>
<span data-ttu-id="accdb-127">`using`函式具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="accdb-127">The `using` function has the following form:</span></span>

<span data-ttu-id="accdb-128">`using`(*expression1*)*函式或 lambda*</span><span class="sxs-lookup"><span data-stu-id="accdb-128">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="accdb-129">在`using`運算式*expression1*建立必須處置的物件。</span><span class="sxs-lookup"><span data-stu-id="accdb-129">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="accdb-130">結果*expression1* （必須處置的物件） 會變成引數，*值*至*函式或 lambda*，這是其中一個必須要有單一的函式其餘的值相符的型別引數所產生的*expression1*，或必須要有該類型的引數的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="accdb-130">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="accdb-131">在執行函式結束時，執行階段會呼叫`Dispose`並釋出資源 (除非值為`null`，在此情況下呼叫 Dispose 就不會嘗試)。</span><span class="sxs-lookup"><span data-stu-id="accdb-131">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="accdb-132">下列範例會示範`using`與 lambda 運算式的運算式。</span><span class="sxs-lookup"><span data-stu-id="accdb-132">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="accdb-133">下一個範例會示範`using`函式具有運算式。</span><span class="sxs-lookup"><span data-stu-id="accdb-133">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="accdb-134">請注意，函式可能會有一些已套用的引數的函式。</span><span class="sxs-lookup"><span data-stu-id="accdb-134">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="accdb-135">下列程式碼範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="accdb-135">The following code example demonstrates this.</span></span> <span data-ttu-id="accdb-136">它會建立包含字串的檔案`XYZ`。</span><span class="sxs-lookup"><span data-stu-id="accdb-136">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="accdb-137">`using`函式和`use`繫結是幾乎相同的方式可以完成相同的動作。</span><span class="sxs-lookup"><span data-stu-id="accdb-137">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="accdb-138">`using`關鍵字，可提供更充分掌控時`Dispose`呼叫。</span><span class="sxs-lookup"><span data-stu-id="accdb-138">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="accdb-139">當您使用`using`，`Dispose`呼叫結尾的函式或 lambda 運算式中，當您使用`use`關鍵字，`Dispose`呼叫包含的程式碼區塊的結尾。</span><span class="sxs-lookup"><span data-stu-id="accdb-139">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="accdb-140">一般情況下，您應該最好使用`use`而不是`using`函式。</span><span class="sxs-lookup"><span data-stu-id="accdb-140">In general, you should prefer to use `use` instead of the `using` function.</span></span>


## <a name="see-also"></a><span data-ttu-id="accdb-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="accdb-141">See Also</span></span>
[<span data-ttu-id="accdb-142">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="accdb-142">F# Language Reference</span></span>](index.md)
