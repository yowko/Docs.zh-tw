---
title: 區域函式與 Lambda 運算式的比較
description: 了解區域函式可能比 Lambda 運算式更適用的原因。
ms.date: 06/27/2016
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 4fb8ea78b783871a19a8d5578d571e00da37642a
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472603"
---
# <a name="local-functions-compared-to-lambda-expressions"></a><span data-ttu-id="c8da7-103">區域函式與 Lambda 運算式的比較</span><span class="sxs-lookup"><span data-stu-id="c8da7-103">Local functions compared to lambda expressions</span></span>

<span data-ttu-id="c8da7-104">第一眼，[區域函式](programming-guide/classes-and-structs/local-functions.md)和 [Lambda 運算式](lambda-expressions.md)十分類似。</span><span class="sxs-lookup"><span data-stu-id="c8da7-104">At first glance, [local functions](programming-guide/classes-and-structs/local-functions.md) and [lambda expressions](lambda-expressions.md) are very similar.</span></span> <span data-ttu-id="c8da7-105">在許多情況下，選擇使用 Lambda 運算式或區域函式與樣式和個人喜好設定相關。</span><span class="sxs-lookup"><span data-stu-id="c8da7-105">In many cases, the choice between using lambda expressions and local functions is a matter of style and personal preference.</span></span> <span data-ttu-id="c8da7-106">不過，您應該注意可使用任一選項的實際差異。</span><span class="sxs-lookup"><span data-stu-id="c8da7-106">However, there are real differences in where you can use one or the other that you should be aware of.</span></span>

<span data-ttu-id="c8da7-107">讓我們檢查階乘演算法的區域函式與 Lambda 運算式實作差異。</span><span class="sxs-lookup"><span data-stu-id="c8da7-107">Let's examine the differences between the local function and lambda expression implementations of the factorial algorithm.</span></span> <span data-ttu-id="c8da7-108">首先是使用區域函式的版本：</span><span class="sxs-lookup"><span data-stu-id="c8da7-108">First the version using a local function:</span></span>

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

<span data-ttu-id="c8da7-109">針對使用 Lambda 運算式的實作版本進行對比：</span><span class="sxs-lookup"><span data-stu-id="c8da7-109">Contrast that implementation with a version that uses lambda expressions:</span></span>

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

<span data-ttu-id="c8da7-110">區域函式具有名稱。</span><span class="sxs-lookup"><span data-stu-id="c8da7-110">The local functions have names.</span></span> <span data-ttu-id="c8da7-111">Lambda 運算式是指派給 `Func` 或 `Action` 類型變數的匿名方法。</span><span class="sxs-lookup"><span data-stu-id="c8da7-111">The lambda expressions are anonymous methods that are assigned to variables that are `Func` or `Action` types.</span></span> <span data-ttu-id="c8da7-112">當您宣告區域函式時，引數類型和傳回型別是函式宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="c8da7-112">When you declare a local function, the argument types and return type are part of the function declaration.</span></span> <span data-ttu-id="c8da7-113">引數類型和傳回型別是 Lambda 運算式之變數型別宣告的一部分，而不是 Lambda 運算式主體的一部分。</span><span class="sxs-lookup"><span data-stu-id="c8da7-113">Instead of being part of the body of the lambda expression, the argument types and return type are part of the lambda expression's variable type declaration.</span></span> <span data-ttu-id="c8da7-114">這兩個差異可能會導致更清楚的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c8da7-114">Those two differences may result in clearer code.</span></span>

<span data-ttu-id="c8da7-115">區域函式的明確指派規則與 Lambda 運算式不同。</span><span class="sxs-lookup"><span data-stu-id="c8da7-115">Local functions have different rules for definite assignment than lambda expressions.</span></span> <span data-ttu-id="c8da7-116">您可以從所在範圍的任何程式碼位置參考區域函式宣告。</span><span class="sxs-lookup"><span data-stu-id="c8da7-116">A local function declaration can be referenced from any code location where it is in scope.</span></span> <span data-ttu-id="c8da7-117">Lambda 運算式必須指派給委派變數，才能提供存取 (或透過參考 Lambda 運算式的委派進行呼叫)。請注意，若為使用 Lambda 運算式的版本，則必須在定義 Lambda 運算式 `nthFactorial` 之前，將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="c8da7-117">A lambda expression must be assigned to a delegate variable before it can be accessed (or called through the delgate referencing the lambda expression.) Notice that the version using the lambda expression must declare and initialize the lambda expression, `nthFactorial` before defining it.</span></span> <span data-ttu-id="c8da7-118">如果沒有這麼做的話，系統會在指派 `nthFactorial` 之前就加以參考，而導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8da7-118">Not doing so results in a compile time error for referencing `nthFactorial` before assigning it.</span></span>
<span data-ttu-id="c8da7-119">這些差異表示使用區域函式時，您可以更輕鬆地建立遞迴演算法。</span><span class="sxs-lookup"><span data-stu-id="c8da7-119">These differences mean that recursive algorithms are easier to create using local functions.</span></span> <span data-ttu-id="c8da7-120">您可以宣告並定義呼叫其本身的區域函式。</span><span class="sxs-lookup"><span data-stu-id="c8da7-120">You can declare and define a local function that calls itself.</span></span> <span data-ttu-id="c8da7-121">Lambda 運算式必須加以宣告並指派預設值，才可以重新指派給參考相同 Lambda 運算式的主體。</span><span class="sxs-lookup"><span data-stu-id="c8da7-121">Lambda expressions must be declared, and assigned a default value before they can be re-assigned to a body that references the same lambda expression.</span></span>

<span data-ttu-id="c8da7-122">明確指派規則也會影響區域函式或 Lambda 運算式所擷取的任何變數。</span><span class="sxs-lookup"><span data-stu-id="c8da7-122">Definite assignment rules also affect any variables that are captured by the local function or lambda expression.</span></span> <span data-ttu-id="c8da7-123">區域函式和 Lambda 運算式規則都要求在將區域函式或 Lambda 運算式轉換成委派時，明確指派任何擷取的變數。</span><span class="sxs-lookup"><span data-stu-id="c8da7-123">Both local functions and lambda expression rules demand that any captured variables are definitely assigned at the point when the local function or lambda expression is converted to a delegate.</span></span> <span data-ttu-id="c8da7-124">差別在於 Lambda 運算式會在宣告時會轉換成委派。</span><span class="sxs-lookup"><span data-stu-id="c8da7-124">The difference is that lambda expressions are converted to delegates when they are declared.</span></span> <span data-ttu-id="c8da7-125">區域函式只會在用作委派時，才會轉換成委派。</span><span class="sxs-lookup"><span data-stu-id="c8da7-125">Local functions are converted to delegates only when used as a delegate.</span></span> <span data-ttu-id="c8da7-126">如果您宣告區域函式，並只透過類似方法的呼叫方式來參考它，則不會轉換成委派。</span><span class="sxs-lookup"><span data-stu-id="c8da7-126">If you declare a local function and only reference it by calling it like a method, it will not be converted to a delegate.</span></span> <span data-ttu-id="c8da7-127">該規則可讓您在區域函式之封入範圍內的任何便利位置宣告區域函式。</span><span class="sxs-lookup"><span data-stu-id="c8da7-127">That rule enables you to declare a local function at any convenient location in its enclosing scope.</span></span> <span data-ttu-id="c8da7-128">通常會在父方法結尾的任何傳回陳述式之後宣告區域函式。</span><span class="sxs-lookup"><span data-stu-id="c8da7-128">It's common to declare local functions at the end of the parent method, after any return statements.</span></span>

<span data-ttu-id="c8da7-129">第三，編譯器可以執行靜態分析，讓區域函式明確指派封入範圍內所擷取的變數。</span><span class="sxs-lookup"><span data-stu-id="c8da7-129">Third, the compiler can perform static analysis that enables local functions to definitely assign captured variables in the enclosing scope.</span></span> <span data-ttu-id="c8da7-130">請考量以下範例：</span><span class="sxs-lookup"><span data-stu-id="c8da7-130">Consider this example:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="c8da7-131">編譯器可判斷 `LocalFunction` 是否在呼叫時明確指派 `y`。</span><span class="sxs-lookup"><span data-stu-id="c8da7-131">The compiler can determine that `LocalFunction` definitely assigns `y` when called.</span></span> <span data-ttu-id="c8da7-132">由於 `LocalFunction` 是在 `return` 陳述式之前呼叫，因此會在 `return` 陳述式明確定義 `y`。</span><span class="sxs-lookup"><span data-stu-id="c8da7-132">Because `LocalFunction` is called before the `return` statement, `y` is definitiely assigned at the `return` statement.</span></span>

<span data-ttu-id="c8da7-133">啟用範例分析的分析允許第四點差異。</span><span class="sxs-lookup"><span data-stu-id="c8da7-133">The analysis that enables the example analysis enables the fourth difference.</span></span>
<span data-ttu-id="c8da7-134">根據其使用方式，區域函式可避免 Lambda 運算式一律需要的堆積配置。</span><span class="sxs-lookup"><span data-stu-id="c8da7-134">Depending on their use, local functions can avoid heap allocations that are always necessary for lambda expressions.</span></span> <span data-ttu-id="c8da7-135">如果區域函式永遠不會轉換成委派，而且區域函式所擷取的變數無法由其他 Lambda 或轉換成委派的區域函式擷取，則編譯器可以避免堆積配置。</span><span class="sxs-lookup"><span data-stu-id="c8da7-135">If a local function is never converted to a delegate, and none of the variables captured by the local function is captured by other lambdas or local functions that are converted to delegates, the compiler can avoid heap allocations.</span></span> 

<span data-ttu-id="c8da7-136">請考慮使用以下非同步範例：</span><span class="sxs-lookup"><span data-stu-id="c8da7-136">Consider this async example:</span></span>

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

<span data-ttu-id="c8da7-137">此 Lambda 運算式的 closure 包含 `address`、`index` 和 `name` 變數。</span><span class="sxs-lookup"><span data-stu-id="c8da7-137">The closure for this lambda expression contains the `address`, `index` and `name` variables.</span></span> <span data-ttu-id="c8da7-138">如果是區域函式，實作關閉的物件可以是 `struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="c8da7-138">In the case of local functions, the object that implements the closure may be a `struct` type.</span></span> <span data-ttu-id="c8da7-139">該結構類型會以傳址方式傳遞至區域函式。</span><span class="sxs-lookup"><span data-stu-id="c8da7-139">That struct type would be passed by reference to the local function.</span></span> <span data-ttu-id="c8da7-140">這項實作差異可節省配置資源。</span><span class="sxs-lookup"><span data-stu-id="c8da7-140">This difference in implementation would save on an allocation.</span></span>

<span data-ttu-id="c8da7-141">Lambda 運算式所需的具現化代表額外的記憶體配置，這可能會在具時效性的程式碼路徑中成為影響效能的因素。</span><span class="sxs-lookup"><span data-stu-id="c8da7-141">The instantiation necessary for lambda expressions means extra memory allocations, which may be a performance factor in time-critical code paths.</span></span>
<span data-ttu-id="c8da7-142">區域函式不會造成這項額外負荷。</span><span class="sxs-lookup"><span data-stu-id="c8da7-142">Local functions do not incur this overhead.</span></span> <span data-ttu-id="c8da7-143">在上述範例中，區域函式版本會比 Lambda 運算式版本少 2 個配置。</span><span class="sxs-lookup"><span data-stu-id="c8da7-143">In the example above, the local functions version has 2 fewer allocations than the lambda expression version.</span></span>

> [!NOTE]
> <span data-ttu-id="c8da7-144">這個方法的對等區域函式也會使用關閉的類別。</span><span class="sxs-lookup"><span data-stu-id="c8da7-144">The local function equivalent of this method also uses a class for the closure.</span></span> <span data-ttu-id="c8da7-145">不論區域函式的關閉實作為 `class` 還是 `struct` 都是實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c8da7-145">Whether the closure for a local function is implemented as a `class` or a `struct` is an implementation detail.</span></span> <span data-ttu-id="c8da7-146">區域函式可以使用 `struct`，而 Lambda 一律會使用 `class`。</span><span class="sxs-lookup"><span data-stu-id="c8da7-146">A local function may use a `struct` whereas a lambda will always use a `class`.</span></span>

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

<span data-ttu-id="c8da7-147">此範例中未示範的最後一個優點，在於可以使用 `yield return` 語法來產生一連串的值，以將區域函式實作為迭代器。</span><span class="sxs-lookup"><span data-stu-id="c8da7-147">One final advantage not demonstrated in this sample is that local functions can be implemented as iterators, using the `yield return` syntax to produce a sequence of values.</span></span> <span data-ttu-id="c8da7-148">Lambda 運算式中不可以有 `yield return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c8da7-148">The `yield return` statement is not allowed in lambda expressions.</span></span>

<span data-ttu-id="c8da7-149">雖然區域函式與 Lambda 運算式看似相同，但它們實際上有不同的用途與用法。</span><span class="sxs-lookup"><span data-stu-id="c8da7-149">While local functions may seem redundant to lambda expressions, they actually serve different purposes and have different uses.</span></span>
<span data-ttu-id="c8da7-150">如果您要撰寫的函式只會從其他方法的內容進行呼叫時，使用區域函式會更有效率。</span><span class="sxs-lookup"><span data-stu-id="c8da7-150">Local functions are more efficient for the case when you want to write a function that is called only from the context of another method.</span></span>
