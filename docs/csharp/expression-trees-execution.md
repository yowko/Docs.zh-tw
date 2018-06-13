---
title: 執行運算式樹狀架構
description: 將運算式樹狀架構轉換成可執行檔的中繼語言 (IL) 指令，以了解執行運算式樹狀架構。
ms.date: 06/20/2016
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 54706cd5d8ebe60bb893bc82f05aecddae370602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218159"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="5d079-103">執行運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="5d079-103">Executing Expression Trees</span></span>

[<span data-ttu-id="5d079-104">上一個課程 -- 支援運算式樹狀架構的架構類型</span><span class="sxs-lookup"><span data-stu-id="5d079-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="5d079-105">「運算式樹狀架構」是一種表示特定程式碼的資料結構。</span><span class="sxs-lookup"><span data-stu-id="5d079-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="5d079-106">它不是已編譯且可執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d079-106">It is not compiled and executable code.</span></span> <span data-ttu-id="5d079-107">如果您想要執行由運算式樹狀架構表示的 .NET 程式碼，您必須將它轉換成可執行 IL 指令。</span><span class="sxs-lookup"><span data-stu-id="5d079-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span> 
## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="5d079-108">將 Lambda 運算式轉換成函式</span><span class="sxs-lookup"><span data-stu-id="5d079-108">Lambda Expressions to Functions</span></span>
<span data-ttu-id="5d079-109">您可以將任何 LambdaExpression 或衍生自 LambdaExpression 的任何類型，轉換成可執行 IL。</span><span class="sxs-lookup"><span data-stu-id="5d079-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="5d079-110">其他運算式類型則無法直接轉換成程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d079-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="5d079-111">這項限制實際上不會造成太大影響。</span><span class="sxs-lookup"><span data-stu-id="5d079-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="5d079-112">Lambda 運算式是您想要轉換成可執行中繼語言 (IL) 以便執行的唯一運算式類型。</span><span class="sxs-lookup"><span data-stu-id="5d079-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="5d079-113">(想想直接執行 `ConstantExpression` 的用意。</span><span class="sxs-lookup"><span data-stu-id="5d079-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="5d079-114">是否有任何用處？)任何 `LamdbaExpression` 的運算式樹狀架構或衍生自 `LambdaExpression` 的類型，都可以轉換成 IL。</span><span class="sxs-lookup"><span data-stu-id="5d079-114">Would it mean anything useful?) Any expression tree that is a `LamdbaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="5d079-115">運算式類型 `Expression<TDelegate>` 是 .NET Core 程式庫中唯一的具體範例。</span><span class="sxs-lookup"><span data-stu-id="5d079-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="5d079-116">它可用來表示對應至任何委派類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="5d079-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="5d079-117">因為此類型對應至委派類型，所以 .NET 可以查看運算式，並為符合 Lambda 運算式簽章的適當委派產生 IL。</span><span class="sxs-lookup"><span data-stu-id="5d079-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="5d079-118">在大多數情況下，這會在運算式和其對應委派之間建立一個簡單的對應。</span><span class="sxs-lookup"><span data-stu-id="5d079-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="5d079-119">例如，由 `Expression<Func<int>>` 表示的運算式樹狀架構會轉換成 `Func<int>` 類型的委派。</span><span class="sxs-lookup"><span data-stu-id="5d079-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="5d079-120">對於具有任何傳回型別和引數清單的 Lambda 運算式，會有一個委派類型，它是由該 Lambda 運算式表示之可執行程式碼的目標類型。</span><span class="sxs-lookup"><span data-stu-id="5d079-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lamdba expression.</span></span>

<span data-ttu-id="5d079-121">`LamdbaExpression` 類型包含將運算式樹狀架構轉換成可執行程式碼時所使用的 `Compile` 和 `CompileToMethod` 成員。</span><span class="sxs-lookup"><span data-stu-id="5d079-121">The `LamdbaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="5d079-122">`Compile` 方法會建立委派。</span><span class="sxs-lookup"><span data-stu-id="5d079-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="5d079-123">`CompileToMethod` 方法會以表示運算式樹狀架構之編譯輸出的 IL 來更新 `MethodBuilder` 物件。</span><span class="sxs-lookup"><span data-stu-id="5d079-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="5d079-124">請注意，`CompileToMethod` 僅適用於完整桌面架構，而不適用於 .NET Core 架構。</span><span class="sxs-lookup"><span data-stu-id="5d079-124">Note that `CompileToMethod` is only available on the full desktop framework, not on the .NET Core framework.</span></span>

<span data-ttu-id="5d079-125">或者，您也可以提供 `DebugInfoGenerator`，以接收所產生之委派物件的符號偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="5d079-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="5d079-126">這可讓您將運算式樹狀架構轉換成委派物件，並具有所產生之委派的完整偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="5d079-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="5d079-127">您會使用下列程式碼，將運算式轉換成委派：</span><span class="sxs-lookup"><span data-stu-id="5d079-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="5d079-128">請注意，委派類型是以運算式類型為基礎。</span><span class="sxs-lookup"><span data-stu-id="5d079-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="5d079-129">如果您想要以強型別方式來使用委派物件，您必須了解傳回型別和引數清單。</span><span class="sxs-lookup"><span data-stu-id="5d079-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="5d079-130">`LambdaExpression.Compile()` 方法會傳回 `Delegate` 類型。</span><span class="sxs-lookup"><span data-stu-id="5d079-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="5d079-131">您必須將它轉換成正確的委派類型，才能讓任何編譯時期工具檢查傳回型別的引數清單。</span><span class="sxs-lookup"><span data-stu-id="5d079-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list of return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="5d079-132">執行和存留期</span><span class="sxs-lookup"><span data-stu-id="5d079-132">Execution and Lifetimes</span></span>

<span data-ttu-id="5d079-133">您可以藉由叫用在呼叫 `LamdbaExpression.Compile()` 時所建立的委派，來執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d079-133">You execute the code by invoking the delegate created when you called `LamdbaExpression.Compile()`.</span></span> <span data-ttu-id="5d079-134">如上所示，`add.Compile()` 會傳回委派。</span><span class="sxs-lookup"><span data-stu-id="5d079-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="5d079-135">叫用該委派 (藉由呼叫 `func()`) 即可執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d079-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="5d079-136">該委派代表運算式樹狀架構中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d079-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="5d079-137">您可以保留該委派的控制代碼，稍後再叫用它。</span><span class="sxs-lookup"><span data-stu-id="5d079-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="5d079-138">您不需要在每次想要執行運算式樹狀架構所表示的程式碼時編譯運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="5d079-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="5d079-139">(請記住，運算式樹狀架構為不可變，稍後編譯相同的運算式樹狀架構將會建立執行相同程式碼的委派)。</span><span class="sxs-lookup"><span data-stu-id="5d079-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="5d079-140">建議您不要嘗試建立任何更複雜的快取機制來提升效能，方法是避免不必要的編譯呼叫。</span><span class="sxs-lookup"><span data-stu-id="5d079-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="5d079-141">比較兩個任意運算式樹狀架構以判斷其是否代表相同的演算法，執行起來也很耗時。</span><span class="sxs-lookup"><span data-stu-id="5d079-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="5d079-142">您可能會發現避免任何額外的 `LambdaExpression.Compile()` 呼叫所省下的計算時間，超過執行程式碼以判斷兩個不同的運算式樹狀架構是否產生相同的可執行程式碼所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="5d079-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="5d079-143">警告</span><span class="sxs-lookup"><span data-stu-id="5d079-143">Caveats</span></span>

<span data-ttu-id="5d079-144">您可以使用運算式樹狀架構執行的其中一個最簡單的作業，就是將 Lambda 運算式編譯成委派並叫用該委派。</span><span class="sxs-lookup"><span data-stu-id="5d079-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="5d079-145">不過，即使這是簡單的作業，還是必須注意幾點。</span><span class="sxs-lookup"><span data-stu-id="5d079-145">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="5d079-146">Lambda 運算式會透過運算式中參考的任何區域變數建立結束型別。</span><span class="sxs-lookup"><span data-stu-id="5d079-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="5d079-147">您必須確保屬於該委派的任何變數都可用於呼叫 `Compile` 的位置，以及在執行所產生的委派時使用。</span><span class="sxs-lookup"><span data-stu-id="5d079-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="5d079-148">一般而言，編譯器會確保這點。</span><span class="sxs-lookup"><span data-stu-id="5d079-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="5d079-149">不過，如果您的運算式存取實作 `IDisposable` 的變數，您的程式碼可能會處置運算式樹狀架構仍持有的物件。</span><span class="sxs-lookup"><span data-stu-id="5d079-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="5d079-150">例如，因為 `int` 不會實作 `IDisposable`，所以下列程式碼會正常運作：</span><span class="sxs-lookup"><span data-stu-id="5d079-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="5d079-151">委派擷取了區域變數 `constant` 的參考。</span><span class="sxs-lookup"><span data-stu-id="5d079-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="5d079-152">您可以在稍後於 `CreateBoundFunc` 傳回的函式執行時，隨時存取該變數。</span><span class="sxs-lookup"><span data-stu-id="5d079-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="5d079-153">不過，請考慮實作 `IDisposable` 的這個類別 (而不是經過人為操作的類別)：</span><span class="sxs-lookup"><span data-stu-id="5d079-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

<span data-ttu-id="5d079-154">如果您將它用於以下所示的運算式中，當您執行 `Resource.Argument` 屬性所參考的程式碼時，您會得到 `ObjectDisposedException`：</span><span class="sxs-lookup"><span data-stu-id="5d079-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

<span data-ttu-id="5d079-155">此方法所傳回的委派已透過 `constant` 物件關閉，該物件已經過處置</span><span class="sxs-lookup"><span data-stu-id="5d079-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="5d079-156">(因為已在 `using` 陳述式中宣告，所以已經過處置)。</span><span class="sxs-lookup"><span data-stu-id="5d079-156">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="5d079-157">現在，當您執行此方法所傳回的委派時，執行當下會擲回 `ObjecctDisposedException`。</span><span class="sxs-lookup"><span data-stu-id="5d079-157">Now, when you execute the delegate returned from this method, you'll have a `ObjecctDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="5d079-158">以執行階段錯誤表示編譯時期建構看起來很奇怪，但這是使用運算式樹狀架構時會面臨到的情況。</span><span class="sxs-lookup"><span data-stu-id="5d079-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="5d079-159">此問題有許多變化組合，因此很難提供一般指引予以避免。</span><span class="sxs-lookup"><span data-stu-id="5d079-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="5d079-160">定義運算式時，請小心存取區域變數；建立可由公用 API 傳回的運算式樹狀架構時，請小心存取目前物件 (以 `this` 表示) 中的狀態。</span><span class="sxs-lookup"><span data-stu-id="5d079-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="5d079-161">運算式中的程式碼可能會參考其他組件中的方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="5d079-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="5d079-162">定義運算式、編譯運算式及叫用所產生的委派時，都必須存取該組件。</span><span class="sxs-lookup"><span data-stu-id="5d079-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="5d079-163">如果沒有該組件，則會發生 `ReferencedAssemblyNotFoundException`。</span><span class="sxs-lookup"><span data-stu-id="5d079-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="5d079-164">總結</span><span class="sxs-lookup"><span data-stu-id="5d079-164">Summary</span></span>

<span data-ttu-id="5d079-165">您可以編譯表示 Lambda 運算式的運算式樹狀架構，以建立可執行的委派。</span><span class="sxs-lookup"><span data-stu-id="5d079-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="5d079-166">這提供一個機制來執行由運算式樹狀架構表示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d079-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="5d079-167">運算式樹狀架構可表示針對您所建立之任何指定建構執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d079-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="5d079-168">只要您編譯和執行程式碼的環境符合您建立運算式的環境，一切就會如預期運作。</span><span class="sxs-lookup"><span data-stu-id="5d079-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="5d079-169">如果不是這種情況，則預期會發生錯誤，而且會在第一次測試使用運算式樹狀架構的任何程式碼時攔截到這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="5d079-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="5d079-170">下一個主題 -- 解譯運算式</span><span class="sxs-lookup"><span data-stu-id="5d079-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
