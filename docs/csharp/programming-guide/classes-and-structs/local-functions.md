---
title: 區域函式 - C# 程式設計手冊
description: 'C # 中的區域函式是在另一個成員中嵌套的私用方法，可從其包含成員中呼叫。'
ms.date: 10/16/2020
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 75accda2e40443073274ece4d8964c13a0945dad
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332896"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="c4462-103">區域函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c4462-103">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="c4462-104">從 C# 7.0 開始，C# 支援「區域函式」\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4462-104">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="c4462-105">區域函式是另一個成員中巢狀型別的私用方法。</span><span class="sxs-lookup"><span data-stu-id="c4462-105">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="c4462-106">它們只可以從其包含成員呼叫。</span><span class="sxs-lookup"><span data-stu-id="c4462-106">They can only be called from their containing member.</span></span> <span data-ttu-id="c4462-107">區域函式可以宣告於下列項目中，以及從下列項目呼叫：</span><span class="sxs-lookup"><span data-stu-id="c4462-107">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="c4462-108">方法，特別是迭代器方法和非同步方法</span><span class="sxs-lookup"><span data-stu-id="c4462-108">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="c4462-109">建構函式</span><span class="sxs-lookup"><span data-stu-id="c4462-109">Constructors</span></span>
- <span data-ttu-id="c4462-110">屬性存取子</span><span class="sxs-lookup"><span data-stu-id="c4462-110">Property accessors</span></span>
- <span data-ttu-id="c4462-111">事件存取子</span><span class="sxs-lookup"><span data-stu-id="c4462-111">Event accessors</span></span>
- <span data-ttu-id="c4462-112">匿名方法</span><span class="sxs-lookup"><span data-stu-id="c4462-112">Anonymous methods</span></span>
- <span data-ttu-id="c4462-113">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="c4462-113">Lambda expressions</span></span>
- <span data-ttu-id="c4462-114">完成項</span><span class="sxs-lookup"><span data-stu-id="c4462-114">Finalizers</span></span>
- <span data-ttu-id="c4462-115">其他區域函式</span><span class="sxs-lookup"><span data-stu-id="c4462-115">Other local functions</span></span>

<span data-ttu-id="c4462-116">不過，區域函式不能宣告於運算式主體成員內。</span><span class="sxs-lookup"><span data-stu-id="c4462-116">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="c4462-117">在某些情況下，您可以使用 Lambda 運算式來實作區域函式也支援的功能。</span><span class="sxs-lookup"><span data-stu-id="c4462-117">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="c4462-118">如需比較，請參閱 [區域函數與 lambda 運算式](#local-functions-vs-lambda-expressions)。</span><span class="sxs-lookup"><span data-stu-id="c4462-118">For a comparison, see [Local functions vs. lambda expressions](#local-functions-vs-lambda-expressions).</span></span>

<span data-ttu-id="c4462-119">區域函式讓程式碼的意圖更為清楚。</span><span class="sxs-lookup"><span data-stu-id="c4462-119">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="c4462-120">讀取您的程式碼的任何人都可以看到，除了包含的方法之外，無法呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="c4462-120">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="c4462-121">對於 Team 專案，它們也可讓另一個開發人員無法從類別或結構的其他位置錯誤地直接呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="c4462-121">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>

## <a name="local-function-syntax"></a><span data-ttu-id="c4462-122">區域函式語法</span><span class="sxs-lookup"><span data-stu-id="c4462-122">Local function syntax</span></span>

<span data-ttu-id="c4462-123">區域函式定義為包含成員內的巢狀方法。</span><span class="sxs-lookup"><span data-stu-id="c4462-123">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="c4462-124">其定義具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="c4462-124">Its definition has the following syntax:</span></span>

```csharp
<modifiers> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="c4462-125">您可以使用下列修飾詞搭配區域函數：</span><span class="sxs-lookup"><span data-stu-id="c4462-125">You can use the following modifiers with a local function:</span></span>

- [`async`](../../language-reference/keywords/async.md)
- [`unsafe`](../../language-reference/keywords/unsafe.md)
- <span data-ttu-id="c4462-126">[`static`](../../language-reference/keywords/static.md) C # 8.0 和更新版本中的 () 。</span><span class="sxs-lookup"><span data-stu-id="c4462-126">[`static`](../../language-reference/keywords/static.md) (in C# 8.0 and later).</span></span> <span data-ttu-id="c4462-127">靜態區域函式無法捕捉本機變數或實例狀態。</span><span class="sxs-lookup"><span data-stu-id="c4462-127">A static local function can't capture local variables or instance state.</span></span>
- <span data-ttu-id="c4462-128">[`extern`](../../language-reference/keywords/extern.md) C # 9.0 和更新版本中的 () 。</span><span class="sxs-lookup"><span data-stu-id="c4462-128">[`extern`](../../language-reference/keywords/extern.md) (in C# 9.0 and later).</span></span> <span data-ttu-id="c4462-129">外部區域函數必須是 `static` 。</span><span class="sxs-lookup"><span data-stu-id="c4462-129">An external local function must be `static`.</span></span>

<span data-ttu-id="c4462-130">在包含成員中定義的所有區域變數（包含其方法參數）都可在非靜態區域函數中存取。</span><span class="sxs-lookup"><span data-stu-id="c4462-130">All local variables that are defined in the containing member, including its method parameters, are accessible in a non-static local function.</span></span>

<span data-ttu-id="c4462-131">不同于方法定義，區域函式定義不能包含成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="c4462-131">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="c4462-132">因為所有區域函式都是私用，所以包含 `private` 這類關鍵字的存取修飾詞會產生編譯器錯誤 CS0106「修飾詞 'private' 對此項目無效」。</span><span class="sxs-lookup"><span data-stu-id="c4462-132">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

<span data-ttu-id="c4462-133">下列範例定義名為 `AppendPathSeparator` 的區域函式，而此區域函式是名為 `GetText` 之方法的私用項目：</span><span class="sxs-lookup"><span data-stu-id="c4462-133">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="Basic" :::

<span data-ttu-id="c4462-134">從 c # 9.0 開始，您可以將屬性套用至區域函數、其參數和型別參數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c4462-134">Beginning with C# 9.0, you can apply attributes to a local function, its parameters and type parameters, as the following example shows:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="WithAttributes" :::

<span data-ttu-id="c4462-135">上述範例使用 [特殊屬性](../../language-reference/attributes/nullable-analysis.md) 來協助編譯器在可為 null 的內容中進行靜態分析。</span><span class="sxs-lookup"><span data-stu-id="c4462-135">The preceding example uses a [special attribute](../../language-reference/attributes/nullable-analysis.md) to assist the compiler in static analysis in a nullable context.</span></span>

## <a name="local-functions-and-exceptions"></a><span data-ttu-id="c4462-136">區域函式和例外狀況</span><span class="sxs-lookup"><span data-stu-id="c4462-136">Local functions and exceptions</span></span>

<span data-ttu-id="c4462-137">區域函式的其中一個有用功能是它們可以允許立即顯示例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4462-137">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="c4462-138">對於方法迭代器，只有在列舉傳回的序列時，才會顯示例外狀況，而不是擷取迭代器時。</span><span class="sxs-lookup"><span data-stu-id="c4462-138">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="c4462-139">對於非同步方法，等候傳回的工作時，會觀察到非同步方法中擲回的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4462-139">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span>

<span data-ttu-id="c4462-140">下列範例 `OddSequence` 會定義列舉指定範圍中奇數數位的方法。</span><span class="sxs-lookup"><span data-stu-id="c4462-140">The following example defines an `OddSequence` method that enumerates odd numbers in a specified range.</span></span> <span data-ttu-id="c4462-141">因為它會將一個大於 100 的數字傳遞至 `OddSequence` 列舉值方法，所以此方法會擲回 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="c4462-141">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="c4462-142">顯示範例輸出時，只有在您逐一查看數字時，才會顯示例外狀況，而不是擷取列舉值時。</span><span class="sxs-lookup"><span data-stu-id="c4462-142">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

:::code language="csharp" source="snippets/local-functions/IteratorWithoutLocal.cs" :::

<span data-ttu-id="c4462-143">如果您將 iterator 邏輯放入區域函式中，當您抓取列舉值時，就會擲回引數驗證例外狀況，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c4462-143">If you put iterator logic into a local function, argument validation exceptions are thrown when you retrieve the enumerator, as the following example shows:</span></span>

:::code language="csharp" source="snippets/local-functions/IteratorWithLocal.cs" :::

<span data-ttu-id="c4462-144">您可以透過與非同步作業類似的方式來使用區域函數。</span><span class="sxs-lookup"><span data-stu-id="c4462-144">You can use local functions in a similar way with asynchronous operations.</span></span> <span data-ttu-id="c4462-145">等候對應的工作時，非同步方法介面中擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4462-145">Exceptions thrown in an async method surface when the corresponding task is awaited.</span></span> <span data-ttu-id="c4462-146">區域函式允許您的程式碼快速失敗，並允許擲回並同步觀察到您的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4462-146">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="c4462-147">下列範例使用名為 `GetMultipleAsync` 的非同步方法暫停指定的秒數，並傳回該秒數之隨機倍數的值。</span><span class="sxs-lookup"><span data-stu-id="c4462-147">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="c4462-148">延遲上限是 5 秒；如果值大於 5，則會產生 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="c4462-148">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="c4462-149">如下列範例所示，只有在等候工作時，才會觀察到將值6傳遞給方法時所擲回的例外狀況 `GetMultipleAsync` 。</span><span class="sxs-lookup"><span data-stu-id="c4462-149">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is observed only when the task is awaited.</span></span>

:::code language="csharp" source="snippets/local-functions/AsyncWithoutLocal.cs" :::

<span data-ttu-id="c4462-150">如同方法反覆運算器，您可以重構上述範例，並將非同步作業的程式碼放在區域函式中。</span><span class="sxs-lookup"><span data-stu-id="c4462-150">Like with the method iterator, you can refactor the preceding example and put the code of asynchronous operation in a local function.</span></span> <span data-ttu-id="c4462-151">如下列範例的輸出所示，當 <xref:System.ArgumentOutOfRangeException> 呼叫方法時，就會擲 `GetMultiple` 回。</span><span class="sxs-lookup"><span data-stu-id="c4462-151">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is thrown as soon as the `GetMultiple` method is called.</span></span>

:::code language="csharp" source="snippets/local-functions/AsyncWithLocal.cs" :::

## <a name="local-functions-vs-lambda-expressions"></a><span data-ttu-id="c4462-152">區域函式與 Lambda 運算式的比較</span><span class="sxs-lookup"><span data-stu-id="c4462-152">Local functions vs. lambda expressions</span></span>

<span data-ttu-id="c4462-153">第一眼，區域函式和 [Lambda 運算式](../../language-reference/operators/lambda-expressions.md)十分類似。</span><span class="sxs-lookup"><span data-stu-id="c4462-153">At first glance, local functions and [lambda expressions](../../language-reference/operators/lambda-expressions.md) are very similar.</span></span> <span data-ttu-id="c4462-154">在許多情況下，選擇使用 Lambda 運算式或區域函式與樣式和個人喜好設定相關。</span><span class="sxs-lookup"><span data-stu-id="c4462-154">In many cases, the choice between using lambda expressions and local functions is a matter of style and personal preference.</span></span> <span data-ttu-id="c4462-155">不過，您應該注意可使用任一選項的實際差異。</span><span class="sxs-lookup"><span data-stu-id="c4462-155">However, there are real differences in where you can use one or the other that you should be aware of.</span></span>

<span data-ttu-id="c4462-156">讓我們檢查階乘演算法的區域函式與 Lambda 運算式實作差異。</span><span class="sxs-lookup"><span data-stu-id="c4462-156">Let's examine the differences between the local function and lambda expression implementations of the factorial algorithm.</span></span> <span data-ttu-id="c4462-157">以下是使用區域函式的版本：</span><span class="sxs-lookup"><span data-stu-id="c4462-157">Here's the version using a local function:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLocal" :::

<span data-ttu-id="c4462-158">此版本會使用 lambda 運算式：</span><span class="sxs-lookup"><span data-stu-id="c4462-158">This version uses lambda expressions:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLambda" :::

### <a name="naming"></a><span data-ttu-id="c4462-159">命名</span><span class="sxs-lookup"><span data-stu-id="c4462-159">Naming</span></span>

<span data-ttu-id="c4462-160">區域函式的明確命名方式就像方法一樣。</span><span class="sxs-lookup"><span data-stu-id="c4462-160">Local functions are explicitly named like methods.</span></span> <span data-ttu-id="c4462-161">Lambda 運算式是匿名方法，而且需要指派給類型的變數 `delegate` ，通常是 `Action` 或 `Func` 類型。</span><span class="sxs-lookup"><span data-stu-id="c4462-161">Lambda expressions are anonymous methods and need to be assigned to variables of a `delegate` type, typically either `Action` or `Func` types.</span></span> <span data-ttu-id="c4462-162">當您宣告區域函式時，此程式就像是撰寫一般方法;您可以宣告傳回型別和函式簽章。</span><span class="sxs-lookup"><span data-stu-id="c4462-162">When you declare a local function, the process is like writing a normal method; you declare a return type and a function signature.</span></span>

### <a name="function-signatures-and-lambda-expression-types"></a><span data-ttu-id="c4462-163">函數簽章和 lambda 運算式類型</span><span class="sxs-lookup"><span data-stu-id="c4462-163">Function signatures and lambda expression types</span></span>

<span data-ttu-id="c4462-164">Lambda 運算式依賴 `Action` / `Func` 它們所指派的變數類型來決定引數和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="c4462-164">Lambda expressions rely on the type of the `Action`/`Func` variable that they're assigned to determine the argument and return types.</span></span> <span data-ttu-id="c4462-165">在區域函式中，因為語法很像是撰寫一般方法，所以引數型別和傳回型別都已經是函式宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="c4462-165">In local functions, since the syntax is much like writing a normal method, argument types and return type are already part of the function declaration.</span></span>

### <a name="definite-assignment"></a><span data-ttu-id="c4462-166">明確指派</span><span class="sxs-lookup"><span data-stu-id="c4462-166">Definite assignment</span></span>

<span data-ttu-id="c4462-167">Lambda 運算式是在執行時間宣告和指派的物件。</span><span class="sxs-lookup"><span data-stu-id="c4462-167">Lambda expressions are objects that are declared and assigned at runtime.</span></span> <span data-ttu-id="c4462-168">若要使用 lambda 運算式，必須明確指派它：將指派給它的 `Action` / `Func` 變數必須宣告，並且指派 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="c4462-168">In order for a lambda expression to be used, it needs to be definitely assigned: the `Action`/`Func` variable that it will be assigned to must be declared and the lambda expression assigned to it.</span></span> <span data-ttu-id="c4462-169">請注意，在 `LambdaFactorial` 定義 lambda 運算式之前，必須先將其宣告和初始化 `nthFactorial` 。</span><span class="sxs-lookup"><span data-stu-id="c4462-169">Notice that `LambdaFactorial` must declare and initialize the lambda expression `nthFactorial` before defining it.</span></span> <span data-ttu-id="c4462-170">如果沒有這麼做的話，系統會在指派 `nthFactorial` 之前就加以參考，而導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4462-170">Not doing so results in a compile time error for referencing `nthFactorial` before assigning it.</span></span>

<span data-ttu-id="c4462-171">區域函數是在編譯時期定義。</span><span class="sxs-lookup"><span data-stu-id="c4462-171">Local functions are defined at compile time.</span></span> <span data-ttu-id="c4462-172">因為它們不會指派給變數，所以可以從 **其範圍**內的任何程式碼位置參考這些變數。在第一個範例中 `LocalFunctionFactorial` ，我們可以在語句的上方或下方宣告我們的區域函式 `return` ，而不會觸發任何編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4462-172">As they're not assigned to variables, they can be referenced from any code location **where it is in scope**; in our first example `LocalFunctionFactorial`, we could declare our local function either above or below the `return` statement and not trigger any compiler errors.</span></span>

<span data-ttu-id="c4462-173">這些差異表示使用區域函式時，您可以更輕鬆地建立遞迴演算法。</span><span class="sxs-lookup"><span data-stu-id="c4462-173">These differences mean that recursive algorithms are easier to create using local functions.</span></span> <span data-ttu-id="c4462-174">您可以宣告並定義呼叫其本身的區域函式。</span><span class="sxs-lookup"><span data-stu-id="c4462-174">You can declare and define a local function that calls itself.</span></span> <span data-ttu-id="c4462-175">Lambda 運算式必須加以宣告並指派預設值，才可以重新指派給參考相同 Lambda 運算式的主體。</span><span class="sxs-lookup"><span data-stu-id="c4462-175">Lambda expressions must be declared, and assigned a default value before they can be re-assigned to a body that references the same lambda expression.</span></span>

### <a name="implementation-as-a-delegate"></a><span data-ttu-id="c4462-176">以委派的形式執行</span><span class="sxs-lookup"><span data-stu-id="c4462-176">Implementation as a delegate</span></span>

<span data-ttu-id="c4462-177">Lambda 運算式在宣告時，會轉換為委派。</span><span class="sxs-lookup"><span data-stu-id="c4462-177">Lambda expressions are converted to delegates when they're declared.</span></span> <span data-ttu-id="c4462-178">區域函式更有彈性，因為它們可以像傳統方法 *或* 委派一樣撰寫。</span><span class="sxs-lookup"><span data-stu-id="c4462-178">Local functions are more flexible in that they can be written like a traditional method *or* as a delegate.</span></span> <span data-ttu-id="c4462-179">區域函式只 ***會在當做委派時轉換*** 為委派。</span><span class="sxs-lookup"><span data-stu-id="c4462-179">Local functions are only converted to delegates when ***used*** as a delegate.</span></span>

<span data-ttu-id="c4462-180">如果您宣告區域函式，並只透過類似方法的呼叫方式來參考它，則不會轉換成委派。</span><span class="sxs-lookup"><span data-stu-id="c4462-180">If you declare a local function and only reference it by calling it like a method, it will not be converted to a delegate.</span></span>

### <a name="variable-capture"></a><span data-ttu-id="c4462-181">變數捕捉</span><span class="sxs-lookup"><span data-stu-id="c4462-181">Variable capture</span></span>

<span data-ttu-id="c4462-182">[明確指派](../../../../_csharplang/spec/variables.md#definite-assignment)的規則也會影響區域函數或 lambda 運算式所捕捉的任何變數。</span><span class="sxs-lookup"><span data-stu-id="c4462-182">The rules of [definite assignment](../../../../_csharplang/spec/variables.md#definite-assignment) also affect any variables that are captured by the local function or lambda expression.</span></span> <span data-ttu-id="c4462-183">編譯器可以執行靜態分析，讓區域函式在封閉範圍中絕對指派已捕捉的變數。</span><span class="sxs-lookup"><span data-stu-id="c4462-183">The compiler can perform static analysis that enables local functions to definitely assign captured variables in the enclosing scope.</span></span> <span data-ttu-id="c4462-184">請考慮此範例：</span><span class="sxs-lookup"><span data-stu-id="c4462-184">Consider this example:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="c4462-185">編譯器可判斷 `LocalFunction` 是否在呼叫時明確指派 `y`。</span><span class="sxs-lookup"><span data-stu-id="c4462-185">The compiler can determine that `LocalFunction` definitely assigns `y` when called.</span></span> <span data-ttu-id="c4462-186">由於 `LocalFunction` 是在 `return` 陳述式之前呼叫，因此會在 `return` 陳述式明確指派 `y`。</span><span class="sxs-lookup"><span data-stu-id="c4462-186">Because `LocalFunction` is called before the `return` statement, `y` is definitely assigned at the `return` statement.</span></span>

<span data-ttu-id="c4462-187">請注意，當區域函式捕捉到封閉範圍中的變數時，區域函式會實作為委派型別。</span><span class="sxs-lookup"><span data-stu-id="c4462-187">Note that when a local function captures variables in the enclosing scope, the local function is implemented as a delegate type.</span></span>

### <a name="heap-allocations"></a><span data-ttu-id="c4462-188">堆積配置</span><span class="sxs-lookup"><span data-stu-id="c4462-188">Heap allocations</span></span>

<span data-ttu-id="c4462-189">根據其使用方式，區域函式可避免 Lambda 運算式一律需要的堆積配置。</span><span class="sxs-lookup"><span data-stu-id="c4462-189">Depending on their use, local functions can avoid heap allocations that are always necessary for lambda expressions.</span></span> <span data-ttu-id="c4462-190">如果區域函式永遠不會轉換成委派，而且區域函數所捕捉的任何變數都不是由轉換成委派的其他 lambda 或區域函數所捕捉，則編譯器可以避免堆積配置。</span><span class="sxs-lookup"><span data-stu-id="c4462-190">If a local function is never converted to a delegate, and none of the variables captured by the local function are captured by other lambdas or local functions that are converted to delegates, the compiler can avoid heap allocations.</span></span>

<span data-ttu-id="c4462-191">請考慮使用以下非同步範例：</span><span class="sxs-lookup"><span data-stu-id="c4462-191">Consider this async example:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLambda" :::

<span data-ttu-id="c4462-192">此 Lambda 運算式的 closure 包含 `address`、`index` 和 `name` 變數。</span><span class="sxs-lookup"><span data-stu-id="c4462-192">The closure for this lambda expression contains the `address`, `index` and `name` variables.</span></span> <span data-ttu-id="c4462-193">如果是區域函式，實作關閉的物件可以是 `struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="c4462-193">In the case of local functions, the object that implements the closure may be a `struct` type.</span></span> <span data-ttu-id="c4462-194">該結構類型會以傳址方式傳遞至區域函式。</span><span class="sxs-lookup"><span data-stu-id="c4462-194">That struct type would be passed by reference to the local function.</span></span> <span data-ttu-id="c4462-195">這項實作差異可節省配置資源。</span><span class="sxs-lookup"><span data-stu-id="c4462-195">This difference in implementation would save on an allocation.</span></span>

<span data-ttu-id="c4462-196">Lambda 運算式所需的具現化代表額外的記憶體配置，這可能會在具時效性的程式碼路徑中成為影響效能的因素。</span><span class="sxs-lookup"><span data-stu-id="c4462-196">The instantiation necessary for lambda expressions means extra memory allocations, which may be a performance factor in time-critical code paths.</span></span> <span data-ttu-id="c4462-197">區域函式不會造成這項額外負荷。</span><span class="sxs-lookup"><span data-stu-id="c4462-197">Local functions do not incur this overhead.</span></span> <span data-ttu-id="c4462-198">在上述範例中，區域函式版本的配置比 lambda 運算式版本少兩倍。</span><span class="sxs-lookup"><span data-stu-id="c4462-198">In the example above, the local functions version has two fewer allocations than the lambda expression version.</span></span>

<span data-ttu-id="c4462-199">如果您知道您的本機函式將不會轉換成委派，而且任何由轉換成委派的 lambda 或區域函式不會捕捉它所捕捉的任何變數，您可以保證您的區域函式會將它宣告為區域函式，以避免在堆積上進行配置 `static` 。</span><span class="sxs-lookup"><span data-stu-id="c4462-199">If you know that your local function won't be converted to a delegate and none of the variables captured by it are captured by other lambdas or local functions that are converted to delegates, you can guarantee that your local function avoids being allocated on the heap by declaring it as a `static` local function.</span></span> <span data-ttu-id="c4462-200">請注意，這項功能會在 c # 8.0 和更新版本中提供。</span><span class="sxs-lookup"><span data-stu-id="c4462-200">Note that this feature is available in C# 8.0 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="c4462-201">這個方法的對等區域函式也會使用關閉的類別。</span><span class="sxs-lookup"><span data-stu-id="c4462-201">The local function equivalent of this method also uses a class for the closure.</span></span> <span data-ttu-id="c4462-202">不論區域函式的關閉實作為 `class` 還是 `struct` 都是實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c4462-202">Whether the closure for a local function is implemented as a `class` or a `struct` is an implementation detail.</span></span> <span data-ttu-id="c4462-203">區域函式可以使用 `struct`，而 Lambda 一律會使用 `class`。</span><span class="sxs-lookup"><span data-stu-id="c4462-203">A local function may use a `struct` whereas a lambda will always use a `class`.</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLocal" :::

### <a name="usage-of-the-yield-keyword"></a><span data-ttu-id="c4462-204">關鍵字的用法 `yield`</span><span class="sxs-lookup"><span data-stu-id="c4462-204">Usage of the `yield` keyword</span></span>

<span data-ttu-id="c4462-205">此範例中未示範的最後一個優點，在於可以使用 `yield return` 語法來產生一連串的值，以將區域函式實作為迭代器。</span><span class="sxs-lookup"><span data-stu-id="c4462-205">One final advantage not demonstrated in this sample is that local functions can be implemented as iterators, using the `yield return` syntax to produce a sequence of values.</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="YieldReturn" :::

<span data-ttu-id="c4462-206">`yield return`Lambda 運算式中不允許使用語句，請參閱[編譯器錯誤 CS1621](../../misc/cs1621.md)。</span><span class="sxs-lookup"><span data-stu-id="c4462-206">The `yield return` statement is not allowed in lambda expressions, see [compiler error CS1621](../../misc/cs1621.md).</span></span>

<span data-ttu-id="c4462-207">雖然區域函式與 Lambda 運算式看似相同，但它們實際上有不同的用途與用法。</span><span class="sxs-lookup"><span data-stu-id="c4462-207">While local functions may seem redundant to lambda expressions, they actually serve different purposes and have different uses.</span></span> <span data-ttu-id="c4462-208">如果您要撰寫的函式只會從其他方法的內容進行呼叫時，使用區域函式會更有效率。</span><span class="sxs-lookup"><span data-stu-id="c4462-208">Local functions are more efficient for the case when you want to write a function that is called only from the context of another method.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4462-209">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4462-209">See also</span></span>

- [<span data-ttu-id="c4462-210">方法</span><span class="sxs-lookup"><span data-stu-id="c4462-210">Methods</span></span>](methods.md)
