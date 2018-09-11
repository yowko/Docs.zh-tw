---
title: 資源管理：use 關鍵字 (F#)
description: "了解 F # 關鍵字 'use' 和 'using' 函式，可以控制的初始設定和版本的資源。"
ms.date: 05/16/2016
ms.openlocfilehash: ffa1cb515139a3705920d9d9f79be1a69602f7d8
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268220"
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="f2995-103">資源管理：use 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f2995-103">Resource Management: The use Keyword</span></span>

<span data-ttu-id="f2995-104">本主題說明關鍵字`use`而`using`函式，可以控制的初始設定和版本的資源。</span><span class="sxs-lookup"><span data-stu-id="f2995-104">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="f2995-105">資源</span><span class="sxs-lookup"><span data-stu-id="f2995-105">Resources</span></span>

<span data-ttu-id="f2995-106">詞彙*資源*以一個以上的方式使用。</span><span class="sxs-lookup"><span data-stu-id="f2995-106">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="f2995-107">是，資源可以是應用程式使用，例如字串、 圖形和類似項目，但此內容中的資料*資源*是指軟體或作業系統的資源，例如圖形裝置內容、 檔案控制代碼、 網路和資料庫連接、 並行處理的物件，例如等候控制代碼，依此類推。</span><span class="sxs-lookup"><span data-stu-id="f2995-107">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="f2995-108">使用這些資源的應用程式牽涉到取得來自作業系統或其他資源提供者，後面接著之後版本的資源集區，讓它可以提供給另一個應用程式的資源的作業。</span><span class="sxs-lookup"><span data-stu-id="f2995-108">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="f2995-109">當應用程式不會釋放回一般的集區的資源時，會發生問題。</span><span class="sxs-lookup"><span data-stu-id="f2995-109">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="f2995-110">管理資源</span><span class="sxs-lookup"><span data-stu-id="f2995-110">Managing Resources</span></span>

<span data-ttu-id="f2995-111">若要有效率地和負起責任管理應用程式中的資源，您必須釋放資源，立即與可預測的方式。</span><span class="sxs-lookup"><span data-stu-id="f2995-111">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="f2995-112">.NET Framework 可協助您執行此作業藉由提供`System.IDisposable`介面。</span><span class="sxs-lookup"><span data-stu-id="f2995-112">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="f2995-113">型別可實作`System.IDisposable`具有`System.IDisposable.Dispose`方法，這個方法會正確地釋放資源。</span><span class="sxs-lookup"><span data-stu-id="f2995-113">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="f2995-114">撰寫得當的應用程式保證`System.IDisposable.Dispose`時不再需要保留有限的資源的任何物件會立即呼叫。</span><span class="sxs-lookup"><span data-stu-id="f2995-114">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="f2995-115">幸運的是，大部分的.NET 語言提供支援更加容易，而 F # 也不例外。</span><span class="sxs-lookup"><span data-stu-id="f2995-115">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="f2995-116">有兩個實用的語言建構可支援的處置模式：`use`繫結和`using`函式。</span><span class="sxs-lookup"><span data-stu-id="f2995-116">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="f2995-117">使用繫結</span><span class="sxs-lookup"><span data-stu-id="f2995-117">use Binding</span></span>

<span data-ttu-id="f2995-118">`use`關鍵字有類似的形式`let`繫結：</span><span class="sxs-lookup"><span data-stu-id="f2995-118">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="f2995-119">使用 *值* = *運算式*</span><span class="sxs-lookup"><span data-stu-id="f2995-119">use *value* = *expression*</span></span>

<span data-ttu-id="f2995-120">它提供與相同的功能`let`繫結，但會增加呼叫`Dispose`值超出範圍時的值。</span><span class="sxs-lookup"><span data-stu-id="f2995-120">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="f2995-121">請注意，編譯器會插入 null 值，檢查，因此，如果值是`null`，呼叫`Dispose`未嘗試。</span><span class="sxs-lookup"><span data-stu-id="f2995-121">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="f2995-122">下列範例示範如何使用自動關閉檔案`use`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f2995-122">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
<span data-ttu-id="f2995-123">您可以使用`use`在計算運算式中，在此情況下的自訂的版本`use`運算式的使用方式。</span><span class="sxs-lookup"><span data-stu-id="f2995-123">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="f2995-124">如需詳細資訊，請參閱 <<c0> [ 序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，並[計算運算式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f2995-124">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="using-function"></a><span data-ttu-id="f2995-125">使用函式</span><span class="sxs-lookup"><span data-stu-id="f2995-125">using Function</span></span>

<span data-ttu-id="f2995-126">`using`函式具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="f2995-126">The `using` function has the following form:</span></span>

<span data-ttu-id="f2995-127">`using` (*expression1*)*函式或 lambda*</span><span class="sxs-lookup"><span data-stu-id="f2995-127">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="f2995-128">在 `using`運算式*expression1*建立必須處置的物件。</span><span class="sxs-lookup"><span data-stu-id="f2995-128">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="f2995-129">結果*expression1* （必須處置的物件） 會變成引數，*值*至*函式或 lambda*，這是預期單一任一函式剩餘的值相符的類型引數所產生*expression1*，或該類型的引數的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="f2995-129">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="f2995-130">在執行函式結束時，執行階段會呼叫`Dispose`，並且釋放資源 (除非值為`null`，在此情況下對 Dispose 的呼叫就不會嘗試)。</span><span class="sxs-lookup"><span data-stu-id="f2995-130">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="f2995-131">下列範例示範`using`使用 lambda 運算式的運算式。</span><span class="sxs-lookup"><span data-stu-id="f2995-131">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="f2995-132">下一個範例顯示`using`函式的運算式。</span><span class="sxs-lookup"><span data-stu-id="f2995-132">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="f2995-133">請注意，此函式可能是有一些已套用的引數的函式。</span><span class="sxs-lookup"><span data-stu-id="f2995-133">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="f2995-134">下列程式碼範例示範此工作。</span><span class="sxs-lookup"><span data-stu-id="f2995-134">The following code example demonstrates this.</span></span> <span data-ttu-id="f2995-135">它會建立包含字串的檔案`XYZ`。</span><span class="sxs-lookup"><span data-stu-id="f2995-135">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="f2995-136">`using`函式和`use`繫結會幾乎相等的方法可以完成相同的動作。</span><span class="sxs-lookup"><span data-stu-id="f2995-136">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="f2995-137">`using`關鍵字，可提供更充分掌控時`Dispose`呼叫。</span><span class="sxs-lookup"><span data-stu-id="f2995-137">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="f2995-138">當您使用`using`，`Dispose`當您使用時呼叫的函式或 lambda 運算式的結尾`use`關鍵字，`Dispose`呼叫包含的程式碼區塊的結尾。</span><span class="sxs-lookup"><span data-stu-id="f2995-138">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="f2995-139">一般情況下，您應該想要使用`use`而不是`using`函式。</span><span class="sxs-lookup"><span data-stu-id="f2995-139">In general, you should prefer to use `use` instead of the `using` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2995-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2995-140">See also</span></span>

- [<span data-ttu-id="f2995-141">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="f2995-141">F# Language Reference</span></span>](index.md)
