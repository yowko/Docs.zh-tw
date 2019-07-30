---
title: 資源管理:Use 關鍵字
description: 瞭解F#關鍵字「使用」和「using」函式, 其可控制資源的初始化和釋放。
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627265"
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="e1274-103">資源管理:Use 關鍵字</span><span class="sxs-lookup"><span data-stu-id="e1274-103">Resource Management: The use Keyword</span></span>

<span data-ttu-id="e1274-104">本主題描述關鍵字`use` `using`和函式, 此函式可以控制資源的初始化和釋放。</span><span class="sxs-lookup"><span data-stu-id="e1274-104">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="e1274-105">資源</span><span class="sxs-lookup"><span data-stu-id="e1274-105">Resources</span></span>

<span data-ttu-id="e1274-106">「*資源*」一詞會以多種方式使用。</span><span class="sxs-lookup"><span data-stu-id="e1274-106">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="e1274-107">是的, 資源可以是應用程式所使用的資料, 例如字串、圖形等等, 但是在此內容中,*資源*指的是軟體或作業系統資源, 例如圖形裝置內容、檔案控制代碼、網路和資料庫。連接、並行物件 (例如等候控制碼等等)。</span><span class="sxs-lookup"><span data-stu-id="e1274-107">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="e1274-108">應用程式使用這些資源牽涉到從作業系統或其他資源提供者取得資源, 然後將較新的資源發行至集區, 以便提供給另一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1274-108">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="e1274-109">當應用程式未將資源釋放回通用集區時, 就會發生問題。</span><span class="sxs-lookup"><span data-stu-id="e1274-109">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="e1274-110">管理資源</span><span class="sxs-lookup"><span data-stu-id="e1274-110">Managing Resources</span></span>

<span data-ttu-id="e1274-111">若要有效率地管理應用程式中的資源, 您必須以可預測的方式立即發行資源。</span><span class="sxs-lookup"><span data-stu-id="e1274-111">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="e1274-112">.NET Framework 藉由提供`System.IDisposable`介面來協助您執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="e1274-112">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="e1274-113">執行的類型`System.IDisposable`具有方法, `System.IDisposable.Dispose`可正確地釋出資源。</span><span class="sxs-lookup"><span data-stu-id="e1274-113">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="e1274-114">妥善撰寫的應用程式保證`System.IDisposable.Dispose`當您不再需要持有有限資源的任何物件時, 會立即呼叫。</span><span class="sxs-lookup"><span data-stu-id="e1274-114">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="e1274-115">幸運的是, 大部分的 .NET 語言都提供支援, 讓F#這種情況變得更容易, 而且也不例外。</span><span class="sxs-lookup"><span data-stu-id="e1274-115">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="e1274-116">有兩個實用的語言結構支援 dispose 模式: `use`系結`using`和函式。</span><span class="sxs-lookup"><span data-stu-id="e1274-116">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="e1274-117">使用系結</span><span class="sxs-lookup"><span data-stu-id="e1274-117">use Binding</span></span>

<span data-ttu-id="e1274-118">關鍵字的形式類似`let`于系結: `use`</span><span class="sxs-lookup"><span data-stu-id="e1274-118">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="e1274-119">使用*值* = *運算式*</span><span class="sxs-lookup"><span data-stu-id="e1274-119">use *value* = *expression*</span></span>

<span data-ttu-id="e1274-120">它會提供與系結相同`let`的功能, 但會在`Dispose`值超出範圍時, 將對值的呼叫加入。</span><span class="sxs-lookup"><span data-stu-id="e1274-120">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="e1274-121">請注意, 編譯器會在值上插入 null 檢查, 因此如果值為`null`, 則不`Dispose`會嘗試呼叫。</span><span class="sxs-lookup"><span data-stu-id="e1274-121">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="e1274-122">下列範例顯示如何使用`use`關鍵字自動關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="e1274-122">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> <span data-ttu-id="e1274-123">您可以在`use`計算運算式中使用, 在此情況下會使用自`use`定義版本的運算式。</span><span class="sxs-lookup"><span data-stu-id="e1274-123">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="e1274-124">如需詳細資訊, 請參閱[序列](sequences.md)、[非同步工作流程](asynchronous-workflows.md)和[計算運算式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="e1274-124">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="using-function"></a><span data-ttu-id="e1274-125">使用函數</span><span class="sxs-lookup"><span data-stu-id="e1274-125">using Function</span></span>

<span data-ttu-id="e1274-126">`using`函數的格式如下:</span><span class="sxs-lookup"><span data-stu-id="e1274-126">The `using` function has the following form:</span></span>

<span data-ttu-id="e1274-127">`using`(*運算式*=)*函數或 lambda*</span><span class="sxs-lookup"><span data-stu-id="e1274-127">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="e1274-128">在運算式中, 會建立必須處置的物件。 `using`</span><span class="sxs-lookup"><span data-stu-id="e1274-128">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="e1274-129">*運算式*類型的結果 (必須處置的物件) 會變成函*式或 lambda*的引數、*值*, 這是需要符合所產生*之值的另一個型別引數的函數。運算式*型別, 或需要該類型之引數的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="e1274-129">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="e1274-130">在函式執行結束時, 執行時間會呼叫`Dispose`並釋出資源 (除非值為`null`, 在此情況下不會嘗試對 Dispose 進行呼叫)。</span><span class="sxs-lookup"><span data-stu-id="e1274-130">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="e1274-131">下列範例示範具有 lambda `using`運算式的運算式。</span><span class="sxs-lookup"><span data-stu-id="e1274-131">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="e1274-132">下一個範例會顯示`using`具有函數的運算式。</span><span class="sxs-lookup"><span data-stu-id="e1274-132">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="e1274-133">請注意, 函式可能是已套用一些引數的函式。</span><span class="sxs-lookup"><span data-stu-id="e1274-133">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="e1274-134">下列程式碼範例示範此工作。</span><span class="sxs-lookup"><span data-stu-id="e1274-134">The following code example demonstrates this.</span></span> <span data-ttu-id="e1274-135">它會建立包含字串`XYZ`的檔案。</span><span class="sxs-lookup"><span data-stu-id="e1274-135">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="e1274-136">`using`函式`use`和系結幾乎等同于完成相同工作的方式。</span><span class="sxs-lookup"><span data-stu-id="e1274-136">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="e1274-137">關鍵字可讓您更充分掌控呼叫的時間`Dispose`。 `using`</span><span class="sxs-lookup"><span data-stu-id="e1274-137">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="e1274-138">當您使用`using`時`Dispose` , 會在函式或 lambda 運算式的結尾呼叫, 而當您使用`use`關鍵字時`Dispose` , 會在包含程式碼區塊的結尾呼叫。</span><span class="sxs-lookup"><span data-stu-id="e1274-138">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="e1274-139">一般來說, 您應該偏好使用`use` , 而不是`using`函式。</span><span class="sxs-lookup"><span data-stu-id="e1274-139">In general, you should prefer to use `use` instead of the `using` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1274-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1274-140">See also</span></span>

- [<span data-ttu-id="e1274-141">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="e1274-141">F# Language Reference</span></span>](index.md)
