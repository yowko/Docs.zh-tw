---
title: "區域函式與 Lambda 運算式的比較"
description: "了解區域函式可能比 Lambda 運算式更適用的原因。"
keywords: "C#, .NET, .NET Core, 最新功能, 新功能, 區域函式, Lambda 運算式"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.translationtype: HT
ms.sourcegitcommit: 9bb17207ba72bb22f5d6db55e9d1bd77e3013445
ms.openlocfilehash: 0730e7b7d6e3ef7b5c534d16baacde6a7dafacfc
ms.contentlocale: zh-tw
ms.lasthandoff: 08/25/2017

---
# <a name="local-functions-compared-to-lambda-expressions"></a><span data-ttu-id="24018-104">區域函式與 Lambda 運算式的比較</span><span class="sxs-lookup"><span data-stu-id="24018-104">Local functions compared to Lambda expressions</span></span>

<span data-ttu-id="24018-105">第一眼，[區域函式](programming-guide/classes-and-structs/local-functions.md)和 [Lambda 運算式](lambda-expressions.md)十分類似。</span><span class="sxs-lookup"><span data-stu-id="24018-105">At first glance, [local functions](programming-guide/classes-and-structs/local-functions.md) and [lambda expressions](lambda-expressions.md) are very similar.</span></span>
<span data-ttu-id="24018-106">根據您的需求，區域函式可能是較好且更簡單的方案。</span><span class="sxs-lookup"><span data-stu-id="24018-106">Depending on your needs, local functions may be a much better and simpler solution.</span></span>

<span data-ttu-id="24018-107">讓我們檢查階乘演算法的區域函式與 Lambda 運算式實作差異。</span><span class="sxs-lookup"><span data-stu-id="24018-107">Let's examine the differences between the local function and lambda expression implementations of the factorial algorithm.</span></span> <span data-ttu-id="24018-108">首先是使用區域函式的版本：</span><span class="sxs-lookup"><span data-stu-id="24018-108">First the version using a local function:</span></span>

<span data-ttu-id="24018-109">[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "使用區域函式的遞迴階乘")]</span><span class="sxs-lookup"><span data-stu-id="24018-109">[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]</span></span>

<span data-ttu-id="24018-110">針對使用 Lambda 運算式的實作版本進行對比：</span><span class="sxs-lookup"><span data-stu-id="24018-110">Contrast that implementation with a version that uses lambda expressions:</span></span>

<span data-ttu-id="24018-111">[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "使用 Lambda 運算式的遞迴階乘")]</span><span class="sxs-lookup"><span data-stu-id="24018-111">[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]</span></span>

<span data-ttu-id="24018-112">首先，Lambda 運算式是由具現化委派並叫用該委派的方式所實作。</span><span class="sxs-lookup"><span data-stu-id="24018-112">First, lambda expressions are implemented by instantiating a delegate and invoking that delegate.</span></span> <span data-ttu-id="24018-113">區域函式則是以方法呼叫的形式來實作。</span><span class="sxs-lookup"><span data-stu-id="24018-113">Local functions are implemented as method calls.</span></span>
<span data-ttu-id="24018-114">Lambda 運算式所需的具現化代表額外的記憶體配置，這可能會在具時效性的程式碼路徑中成為影響效能的因素。</span><span class="sxs-lookup"><span data-stu-id="24018-114">The instantiation necessary for lambda expressions means extra memory allocations, which may be a performance factor in time critical code paths.</span></span>
<span data-ttu-id="24018-115">區域函式不會造成這項額外負荷。</span><span class="sxs-lookup"><span data-stu-id="24018-115">Local functions do not incur this overhead.</span></span> <span data-ttu-id="24018-116">在上述範例中，區域函式版本會比 Lambda 運算式版本少 2 個配置。</span><span class="sxs-lookup"><span data-stu-id="24018-116">In the example above, the local functions version has 2 fewer allocations than the lambda expression version.</span></span>

<span data-ttu-id="24018-117">區域函式會實作為具有編譯器產生名稱的私用方法，因此這個遞迴方法就已足夠。</span><span class="sxs-lookup"><span data-stu-id="24018-117">This recursive method is simple enough that the local function is implemented as a private method with a compiler generated name.</span></span> <span data-ttu-id="24018-118">與其他私用方法的唯一差異在於它位於外部函式的語意範圍內。</span><span class="sxs-lookup"><span data-stu-id="24018-118">Its only difference from other private methods is that it is semantically scoped inside the outer function.</span></span>

<span data-ttu-id="24018-119">第二，您可以在定義區域函式之前，即進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="24018-119">Second, local functions can be called before they are defined.</span></span> <span data-ttu-id="24018-120">Lambda 運算式則必須在定義之前，先進行宣告。</span><span class="sxs-lookup"><span data-stu-id="24018-120">Lambda expressions must be declared before they are defined.</span></span> <span data-ttu-id="24018-121">這表示在遞迴演算法中可以更輕鬆地使用區域函式，如上所示。</span><span class="sxs-lookup"><span data-stu-id="24018-121">This means local functions are easier to use in recursive algorithms, as shown above.</span></span>

<span data-ttu-id="24018-122">請注意，若為使用 Lambda 運算式的版本，則必須在定義 Lambda 運算式 `nthFactorial` 之前，將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="24018-122">Notice that the version using the lambda expression must declare and initialize the lambda expression, `nthFactorial` before defining it.</span></span> <span data-ttu-id="24018-123">如果沒有這麼做的話，系統會在指派 `nthFactorial` 之前就加以參考，而導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="24018-123">Not doing so results in a compile time error for referencing `nthFactorial` before assigning it.</span></span>
<span data-ttu-id="24018-124">使用區域函式時，您可以更輕鬆地建立遞迴演算法。</span><span class="sxs-lookup"><span data-stu-id="24018-124">Recursive algorithms are easier to create using local functions.</span></span>

<span data-ttu-id="24018-125">第三，使用 Lambda 運算式時，編譯器必須一律建立匿名類別和該類別的執行個體，以儲存由關閉擷取的任何變數。</span><span class="sxs-lookup"><span data-stu-id="24018-125">Third, for lambda expressions, the compiler must always create an anonymous class and an instance of that class to store any variables captured by the closure.</span></span> <span data-ttu-id="24018-126">請考慮使用以下非同步範例：</span><span class="sxs-lookup"><span data-stu-id="24018-126">Consider this async example:</span></span>

<span data-ttu-id="24018-127">[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "使用 Lambda 運算式傳回方法的工作")]</span><span class="sxs-lookup"><span data-stu-id="24018-127">[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]</span></span>

<span data-ttu-id="24018-128">此 Lambda 運算式的 closure 包含 `address`、`index` 和 `name` 變數。</span><span class="sxs-lookup"><span data-stu-id="24018-128">The closure for this lambda expression contains the `address`, `index` and `name` variables.</span></span> <span data-ttu-id="24018-129">如果是區域函式，實作關閉的物件可以是 `struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="24018-129">In the case of local functions, the object that implements the closure may be a `struct` type.</span></span> <span data-ttu-id="24018-130">這就不需要配置。</span><span class="sxs-lookup"><span data-stu-id="24018-130">That would save on an allocation.</span></span>

> [!NOTE]
> <span data-ttu-id="24018-131">這個方法的對等區域函式也會使用關閉的類別。</span><span class="sxs-lookup"><span data-stu-id="24018-131">The local function equivalent of this method also uses a class for the closure.</span></span> <span data-ttu-id="24018-132">不論區域函式的關閉實作為 `class` 還是 `struct` 都是實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="24018-132">Whether the closure for a local function is implemented as a `class` or a `struct` is an implementation detail.</span></span> <span data-ttu-id="24018-133">區域函式可以使用 `struct`，而 Lambda 一律會使用 `class`。</span><span class="sxs-lookup"><span data-stu-id="24018-133">A local function may use a `struct` whereas a lambda will always use a `class`.</span></span>

<span data-ttu-id="24018-134">[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "工作傳回方法與區域函式")]</span><span class="sxs-lookup"><span data-stu-id="24018-134">[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]</span></span>

<span data-ttu-id="24018-135">此範例中未示範的最後一個優點，在於可以使用 `yield return` 語法來產生一連串的值，以將區域函式實作為迭代器。</span><span class="sxs-lookup"><span data-stu-id="24018-135">One final advantage not demonstrated in this sample is that local functions can be implemented as iterators, using the `yield return` syntax to produce a sequence of values.</span></span>

<span data-ttu-id="24018-136">雖然區域函式與 Lambda 運算式看似相同，但它們實際上有不同的用途與用法。</span><span class="sxs-lookup"><span data-stu-id="24018-136">While local functions may seem redundant to lambda expressions, they actually serve different purposes and have different uses.</span></span>
<span data-ttu-id="24018-137">如果您要撰寫的函式只會從其他方法的內容進行呼叫時，使用區域函式會更有效率。</span><span class="sxs-lookup"><span data-stu-id="24018-137">Local functions are more efficient for the case when you want to write a function that is called only from the context of another method.</span></span>

