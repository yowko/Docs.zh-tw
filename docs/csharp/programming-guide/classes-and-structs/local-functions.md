---
title: 區域函式 - C# 程式設計手冊
description: 'C # 中的區域函式是在另一個成員中嵌套的私用方法，而且可以從其包含成員呼叫。'
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 9987d6d5ad57c1dceb3a4bffbae22a81c240c794
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864523"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="2a5cc-103">區域函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="2a5cc-103">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="2a5cc-104">從 C# 7.0 開始，C# 支援「區域函式」\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-104">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="2a5cc-105">區域函式是另一個成員中巢狀型別的私用方法。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-105">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="2a5cc-106">它們只可以從其包含成員呼叫。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-106">They can only be called from their containing member.</span></span> <span data-ttu-id="2a5cc-107">區域函式可以宣告於下列項目中，以及從下列項目呼叫：</span><span class="sxs-lookup"><span data-stu-id="2a5cc-107">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="2a5cc-108">方法，特別是迭代器方法和非同步方法</span><span class="sxs-lookup"><span data-stu-id="2a5cc-108">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="2a5cc-109">建構函式</span><span class="sxs-lookup"><span data-stu-id="2a5cc-109">Constructors</span></span>
- <span data-ttu-id="2a5cc-110">屬性存取子</span><span class="sxs-lookup"><span data-stu-id="2a5cc-110">Property accessors</span></span>
- <span data-ttu-id="2a5cc-111">事件存取子</span><span class="sxs-lookup"><span data-stu-id="2a5cc-111">Event accessors</span></span>
- <span data-ttu-id="2a5cc-112">匿名方法</span><span class="sxs-lookup"><span data-stu-id="2a5cc-112">Anonymous methods</span></span>
- <span data-ttu-id="2a5cc-113">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="2a5cc-113">Lambda expressions</span></span>
- <span data-ttu-id="2a5cc-114">完成項</span><span class="sxs-lookup"><span data-stu-id="2a5cc-114">Finalizers</span></span>
- <span data-ttu-id="2a5cc-115">其他區域函式</span><span class="sxs-lookup"><span data-stu-id="2a5cc-115">Other local functions</span></span>

<span data-ttu-id="2a5cc-116">不過，區域函式不能宣告於運算式主體成員內。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-116">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="2a5cc-117">在某些情況下，您可以使用 Lambda 運算式來實作區域函式也支援的功能。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-117">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="2a5cc-118">如需比較，請參閱區域函式[與 lambda 運算式](#local-functions-vs-lambda-expressions)。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-118">For a comparison, see [Local functions vs. lambda expressions](#local-functions-vs-lambda-expressions).</span></span>

<span data-ttu-id="2a5cc-119">區域函式讓程式碼的意圖更為清楚。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-119">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="2a5cc-120">讀取您程式碼的任何人都可以看到方法無法呼叫，但包含方法除外。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-120">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="2a5cc-121">對於 Team 專案，它們也可讓另一個開發人員無法從類別或結構的其他位置錯誤地直接呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-121">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>

## <a name="local-function-syntax"></a><span data-ttu-id="2a5cc-122">區域函式語法</span><span class="sxs-lookup"><span data-stu-id="2a5cc-122">Local function syntax</span></span>

<span data-ttu-id="2a5cc-123">區域函式定義為包含成員內的巢狀方法。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-123">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="2a5cc-124">其定義具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="2a5cc-124">Its definition has the following syntax:</span></span>

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="2a5cc-125">區域函式可以使用 [async](../../language-reference/keywords/async.md) 和 [unsafe](../../language-reference/keywords/unsafe.md) 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-125">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

<span data-ttu-id="2a5cc-126">請注意，在區域函式中可以存取包含成員中所定義的所有區域變數 (包含其方法參數)。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-126">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span>

<span data-ttu-id="2a5cc-127">不同于方法定義，區域函式定義不能包含成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-127">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="2a5cc-128">因為所有區域函式都是私用，所以包含 `private` 這類關鍵字的存取修飾詞會產生編譯器錯誤 CS0106「修飾詞 'private' 對此項目無效」。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

> [!NOTE]
> <span data-ttu-id="2a5cc-129">在 c # 8.0 之前，區域函式不能包含 `static` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-129">Prior to C# 8.0, local functions cannot include the `static` modifier.</span></span> <span data-ttu-id="2a5cc-130">包含 `static` 關鍵字會產生編譯器錯誤 CS0106「修飾詞 'static' 對此項目無效」。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="2a5cc-131">此外，屬性無法套用至區域函式或其參數和型別參數。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span>

<span data-ttu-id="2a5cc-132">下列範例定義名為 `AppendPathSeparator` 的區域函式，而此區域函式是名為 `GetText` 之方法的私用項目：</span><span class="sxs-lookup"><span data-stu-id="2a5cc-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a><span data-ttu-id="2a5cc-133">區域函式和例外狀況</span><span class="sxs-lookup"><span data-stu-id="2a5cc-133">Local functions and exceptions</span></span>

<span data-ttu-id="2a5cc-134">區域函式的其中一個有用功能是它們可以允許立即顯示例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="2a5cc-135">對於方法迭代器，只有在列舉傳回的序列時，才會顯示例外狀況，而不是擷取迭代器時。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="2a5cc-136">對於非同步方法，等候傳回的工作時，會觀察到非同步方法中擲回的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span>

<span data-ttu-id="2a5cc-137">下列範例定義 `OddSequence` 方法，以列舉所指定範圍之間的奇數。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="2a5cc-138">因為它會將一個大於 100 的數字傳遞至 `OddSequence` 列舉值方法，所以此方法會擲回 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="2a5cc-139">顯示範例輸出時，只有在您逐一查看數字時，才會顯示例外狀況，而不是擷取列舉值時。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

<span data-ttu-id="2a5cc-140">相反地，您可以在執行驗證時以及從區域函式傳回迭代器來擷取迭代器之前擲回例外狀況，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="2a5cc-141">透過類似的方式，可以使用區域函式來處理非同步作業外的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="2a5cc-142">非同步方法中擲回的例外狀況通常需要您檢查 <xref:System.AggregateException> 的內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="2a5cc-143">區域函式允許您的程式碼快速失敗，並允許擲回並同步觀察到您的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="2a5cc-144">下列範例使用名為 `GetMultipleAsync` 的非同步方法暫停指定的秒數，並傳回該秒數之隨機倍數的值。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="2a5cc-145">延遲上限是 5 秒；如果值大於 5，則會產生 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="2a5cc-146">如下列範例所示，在 `GetMultipleAsync` 方法開始執行之後，會將值 6 傳遞給 `GetMultipleAsync` 方法時所擲回的例外狀況包裝在 <xref:System.AggregateException> 中。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

<span data-ttu-id="2a5cc-147">與使用方法迭代器執行的作業相同，我們可以從這個範例重構程式碼先進行驗證，再呼叫非同步方法。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="2a5cc-148">如下列範例輸出所示，<xref:System.ArgumentOutOfRangeException> 不會包裝在 <xref:System.AggregateException> 中。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a><span data-ttu-id="2a5cc-149">區域函式與 Lambda 運算式的比較</span><span class="sxs-lookup"><span data-stu-id="2a5cc-149">Local functions vs. lambda expressions</span></span>

<span data-ttu-id="2a5cc-150">第一眼，區域函式和 [Lambda 運算式](../statements-expressions-operators/lambda-expressions.md)十分類似。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-150">At first glance, local functions and [lambda expressions](../statements-expressions-operators/lambda-expressions.md) are very similar.</span></span> <span data-ttu-id="2a5cc-151">在許多情況下，選擇使用 Lambda 運算式或區域函式與樣式和個人喜好設定相關。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-151">In many cases, the choice between using lambda expressions and local functions is a matter of style and personal preference.</span></span> <span data-ttu-id="2a5cc-152">不過，您應該注意可使用任一選項的實際差異。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-152">However, there are real differences in where you can use one or the other that you should be aware of.</span></span>

<span data-ttu-id="2a5cc-153">讓我們檢查階乘演算法的區域函式與 Lambda 運算式實作差異。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-153">Let's examine the differences between the local function and lambda expression implementations of the factorial algorithm.</span></span> <span data-ttu-id="2a5cc-154">首先是使用區域函式的版本：</span><span class="sxs-lookup"><span data-stu-id="2a5cc-154">First the version using a local function:</span></span>

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

<span data-ttu-id="2a5cc-155">針對使用 Lambda 運算式的實作版本進行對比：</span><span class="sxs-lookup"><span data-stu-id="2a5cc-155">Contrast that implementation with a version that uses lambda expressions:</span></span>

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

<span data-ttu-id="2a5cc-156">區域函式具有名稱。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-156">The local functions have names.</span></span> <span data-ttu-id="2a5cc-157">Lambda 運算式是指派給 `Func` 或 `Action` 類型變數的匿名方法。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-157">The lambda expressions are anonymous methods that are assigned to variables that are `Func` or `Action` types.</span></span> <span data-ttu-id="2a5cc-158">當您宣告區域函式時，引數類型和傳回型別是函式宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-158">When you declare a local function, the argument types and return type are part of the function declaration.</span></span> <span data-ttu-id="2a5cc-159">引數類型和傳回型別是 Lambda 運算式之變數型別宣告的一部分，而不是 Lambda 運算式主體的一部分。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-159">Instead of being part of the body of the lambda expression, the argument types and return type are part of the lambda expression's variable type declaration.</span></span> <span data-ttu-id="2a5cc-160">這兩個差異可能會導致更清楚的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-160">Those two differences may result in clearer code.</span></span>

<span data-ttu-id="2a5cc-161">區域函式的明確指派規則與 Lambda 運算式不同。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-161">Local functions have different rules for definite assignment than lambda expressions.</span></span> <span data-ttu-id="2a5cc-162">您可以從所在範圍的任何程式碼位置參考區域函式宣告。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-162">A local function declaration can be referenced from any code location where it is in scope.</span></span> <span data-ttu-id="2a5cc-163">Lambda 運算式必須先指派給委派變數，才可以存取（或透過參考 lambda 運算式的委派呼叫）。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-163">A lambda expression must be assigned to a delegate variable before it can be accessed (or called through the delegate referencing the lambda expression).</span></span> <span data-ttu-id="2a5cc-164">請注意，使用 lambda 運算式的版本必須在定義 lambda 運算式之前先行宣告和初始化 `nthFactorial` 。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-164">Notice that the version using the lambda expression must declare and initialize the lambda expression `nthFactorial` before defining it.</span></span> <span data-ttu-id="2a5cc-165">如果沒有這麼做的話，系統會在指派 `nthFactorial` 之前就加以參考，而導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-165">Not doing so results in a compile time error for referencing `nthFactorial` before assigning it.</span></span> <span data-ttu-id="2a5cc-166">這些差異表示使用區域函式時，您可以更輕鬆地建立遞迴演算法。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-166">These differences mean that recursive algorithms are easier to create using local functions.</span></span> <span data-ttu-id="2a5cc-167">您可以宣告並定義呼叫其本身的區域函式。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-167">You can declare and define a local function that calls itself.</span></span> <span data-ttu-id="2a5cc-168">Lambda 運算式必須加以宣告並指派預設值，才可以重新指派給參考相同 Lambda 運算式的主體。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-168">Lambda expressions must be declared, and assigned a default value before they can be re-assigned to a body that references the same lambda expression.</span></span>

<span data-ttu-id="2a5cc-169">明確指派規則也會影響區域函式或 Lambda 運算式所擷取的任何變數。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-169">Definite assignment rules also affect any variables that are captured by the local function or lambda expression.</span></span> <span data-ttu-id="2a5cc-170">區域函式和 Lambda 運算式規則都要求在將區域函式或 Lambda 運算式轉換成委派時，明確指派任何擷取的變數。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-170">Both local functions and lambda expression rules demand that any captured variables are definitely assigned at the point when the local function or lambda expression is converted to a delegate.</span></span> <span data-ttu-id="2a5cc-171">差別在於 Lambda 運算式會在宣告時會轉換成委派。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-171">The difference is that lambda expressions are converted to delegates when they are declared.</span></span> <span data-ttu-id="2a5cc-172">區域函式只會在用作委派時，才會轉換成委派。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-172">Local functions are converted to delegates only when used as a delegate.</span></span> <span data-ttu-id="2a5cc-173">如果您宣告區域函式，並只透過類似方法的呼叫方式來參考它，則不會轉換成委派。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-173">If you declare a local function and only reference it by calling it like a method, it will not be converted to a delegate.</span></span> <span data-ttu-id="2a5cc-174">該規則可讓您在區域函式之封入範圍內的任何便利位置宣告區域函式。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-174">That rule enables you to declare a local function at any convenient location in its enclosing scope.</span></span> <span data-ttu-id="2a5cc-175">通常會在父方法結尾的任何傳回陳述式之後宣告區域函式。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-175">It's common to declare local functions at the end of the parent method, after any return statements.</span></span>

<span data-ttu-id="2a5cc-176">第三，編譯器可以執行靜態分析，讓區域函式明確指派封入範圍內所擷取的變數。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-176">Third, the compiler can perform static analysis that enables local functions to definitely assign captured variables in the enclosing scope.</span></span> <span data-ttu-id="2a5cc-177">請思考此範例：</span><span class="sxs-lookup"><span data-stu-id="2a5cc-177">Consider this example:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="2a5cc-178">編譯器可判斷 `LocalFunction` 是否在呼叫時明確指派 `y`。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-178">The compiler can determine that `LocalFunction` definitely assigns `y` when called.</span></span> <span data-ttu-id="2a5cc-179">由於 `LocalFunction` 是在 `return` 陳述式之前呼叫，因此會在 `return` 陳述式明確指派 `y`。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-179">Because `LocalFunction` is called before the `return` statement, `y` is definitely assigned at the `return` statement.</span></span>

<span data-ttu-id="2a5cc-180">啟用範例分析的分析允許第四點差異。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-180">The analysis that enables the example analysis enables the fourth difference.</span></span> <span data-ttu-id="2a5cc-181">根據其使用方式，區域函式可避免 Lambda 運算式一律需要的堆積配置。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-181">Depending on their use, local functions can avoid heap allocations that are always necessary for lambda expressions.</span></span> <span data-ttu-id="2a5cc-182">如果區域函式永遠不會轉換成委派，而且區域函式所擷取的變數無法由其他 Lambda 或轉換成委派的區域函式擷取，則編譯器可以避免堆積配置。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-182">If a local function is never converted to a delegate, and none of the variables captured by the local function is captured by other lambdas or local functions that are converted to delegates, the compiler can avoid heap allocations.</span></span>

<span data-ttu-id="2a5cc-183">請考慮使用以下非同步範例：</span><span class="sxs-lookup"><span data-stu-id="2a5cc-183">Consider this async example:</span></span>

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

<span data-ttu-id="2a5cc-184">此 Lambda 運算式的 closure 包含 `address`、`index` 和 `name` 變數。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-184">The closure for this lambda expression contains the `address`, `index` and `name` variables.</span></span> <span data-ttu-id="2a5cc-185">如果是區域函式，實作關閉的物件可以是 `struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-185">In the case of local functions, the object that implements the closure may be a `struct` type.</span></span> <span data-ttu-id="2a5cc-186">該結構類型會以傳址方式傳遞至區域函式。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-186">That struct type would be passed by reference to the local function.</span></span> <span data-ttu-id="2a5cc-187">這項實作差異可節省配置資源。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-187">This difference in implementation would save on an allocation.</span></span>

<span data-ttu-id="2a5cc-188">Lambda 運算式所需的具現化代表額外的記憶體配置，這可能會在具時效性的程式碼路徑中成為影響效能的因素。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-188">The instantiation necessary for lambda expressions means extra memory allocations, which may be a performance factor in time-critical code paths.</span></span> <span data-ttu-id="2a5cc-189">區域函式不會造成這項額外負荷。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-189">Local functions do not incur this overhead.</span></span> <span data-ttu-id="2a5cc-190">在上述範例中，區域函式版本會比 Lambda 運算式版本少 2 個配置。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-190">In the example above, the local functions version has 2 fewer allocations than the lambda expression version.</span></span>

> [!NOTE]
> <span data-ttu-id="2a5cc-191">這個方法的對等區域函式也會使用關閉的類別。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-191">The local function equivalent of this method also uses a class for the closure.</span></span> <span data-ttu-id="2a5cc-192">不論區域函式的關閉實作為 `class` 還是 `struct` 都是實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-192">Whether the closure for a local function is implemented as a `class` or a `struct` is an implementation detail.</span></span> <span data-ttu-id="2a5cc-193">區域函式可以使用 `struct`，而 Lambda 一律會使用 `class`。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-193">A local function may use a `struct` whereas a lambda will always use a `class`.</span></span>

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

<span data-ttu-id="2a5cc-194">此範例中未示範的最後一個優點，在於可以使用 `yield return` 語法來產生一連串的值，以將區域函式實作為迭代器。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-194">One final advantage not demonstrated in this sample is that local functions can be implemented as iterators, using the `yield return` syntax to produce a sequence of values.</span></span> <span data-ttu-id="2a5cc-195">Lambda 運算式中不可以有 `yield return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-195">The `yield return` statement is not allowed in lambda expressions.</span></span>

<span data-ttu-id="2a5cc-196">雖然區域函式與 Lambda 運算式看似相同，但它們實際上有不同的用途與用法。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-196">While local functions may seem redundant to lambda expressions, they actually serve different purposes and have different uses.</span></span> <span data-ttu-id="2a5cc-197">如果您要撰寫的函式只會從其他方法的內容進行呼叫時，使用區域函式會更有效率。</span><span class="sxs-lookup"><span data-stu-id="2a5cc-197">Local functions are more efficient for the case when you want to write a function that is called only from the context of another method.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a5cc-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a5cc-198">See also</span></span>

- [<span data-ttu-id="2a5cc-199">方法</span><span class="sxs-lookup"><span data-stu-id="2a5cc-199">Methods</span></span>](methods.md)
