---
title: Lambda 運算式
description: 了解如何使用 Lambda 運算式，這是可當做引數傳遞的可執行程式碼區塊。
ms.author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: e37f0e72ee02915d16509fb2ff48bd114e8ad466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217970"
---
# <a name="lambda-expressions"></a><span data-ttu-id="330f0-103">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="330f0-103">Lambda expressions</span></span> #

<span data-ttu-id="330f0-104">「Lambda 運算式」是當做物件處理的程式碼區塊 (運算式或陳述式區塊)。</span><span class="sxs-lookup"><span data-stu-id="330f0-104">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="330f0-105">它可當做方法的引數傳遞，也可由方法呼叫傳回。</span><span class="sxs-lookup"><span data-stu-id="330f0-105">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="330f0-106">Lambda 運算式可大量用於：</span><span class="sxs-lookup"><span data-stu-id="330f0-106">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="330f0-107">將要執行的程式碼傳遞至非同步方法，例如 <xref:System.Threading.Tasks.Task.Run(System.Action)>。</span><span class="sxs-lookup"><span data-stu-id="330f0-107">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span></span>

- <span data-ttu-id="330f0-108">撰寫 [LINQ 查詢運算式](linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="330f0-108">Writing [LINQ query expressions](linq/index.md).</span></span>

- <span data-ttu-id="330f0-109">建立[運算式樹狀架構](expression-trees-building.md)。</span><span class="sxs-lookup"><span data-stu-id="330f0-109">Creating [expression trees](expression-trees-building.md).</span></span>

<span data-ttu-id="330f0-110">Lambda 運算式是可表示為委派或編譯成委派之運算式樹狀架構的程式碼。</span><span class="sxs-lookup"><span data-stu-id="330f0-110">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="330f0-111">Lambda 運算式的特定委派類型取決於其參數和傳回值。</span><span class="sxs-lookup"><span data-stu-id="330f0-111">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="330f0-112">未傳回值的 Lambda 運算式會根據其參數數目對應至特定 `Action` 委派。</span><span class="sxs-lookup"><span data-stu-id="330f0-112">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="330f0-113">傳回值的 Lambda 運算式會根據其參數數目對應至特定 `Func` 委派。</span><span class="sxs-lookup"><span data-stu-id="330f0-113">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="330f0-114">例如，具有兩個參數但未傳回值的 Lambda 運算式，會對應至 <xref:System.Action%602> 委派。</span><span class="sxs-lookup"><span data-stu-id="330f0-114">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="330f0-115">具有一個參數且傳回值的 Lambda 運算式，會對應至 <xref:System.Func%602> 委派。</span><span class="sxs-lookup"><span data-stu-id="330f0-115">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="330f0-116">Lambda 運算式使用 [Lambda 宣告運算子](language-reference/operators/lambda-operator.md) `=>`，來分隔 Lambda 的參數清單及其可執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="330f0-116">A lambda expression uses `=>`, the [lambda declaration operator](language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="330f0-117">若要建立 Lambda 運算式，請在 Lambda 運算子的左邊指定輸入參數 (如果有的話)，並將運算式或陳述式區塊放在另一邊。</span><span class="sxs-lookup"><span data-stu-id="330f0-117">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="330f0-118">例如，單行 Lambda 運算式 `x => x * x` 會指定名為 `x` 的參數，並傳回 `x` 的平方值。</span><span class="sxs-lookup"><span data-stu-id="330f0-118">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="330f0-119">您可以將這個運算式指派給委派類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="330f0-119">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

<span data-ttu-id="330f0-120">您也可以將它當做方法引數直接傳遞：</span><span class="sxs-lookup"><span data-stu-id="330f0-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a><span data-ttu-id="330f0-121">運算式 Lambda</span><span class="sxs-lookup"><span data-stu-id="330f0-121">Expression lambdas</span></span> ##

 <span data-ttu-id="330f0-122">在 => 運算子右邊有運算式的 Lambda 運算式稱為「運算式 Lambda」。</span><span class="sxs-lookup"><span data-stu-id="330f0-122">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="330f0-123">運算式 Lambda 會在[運算式樹狀架構](expression-trees.md)的建構過程中大量使用。</span><span class="sxs-lookup"><span data-stu-id="330f0-123">Expression lambdas are used extensively in the construction of [expression trees](expression-trees.md).</span></span> <span data-ttu-id="330f0-124">運算式 Lambda 會傳回運算式的結果，並採用下列基本形式：</span><span class="sxs-lookup"><span data-stu-id="330f0-124">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input parameters) => expression
```

<span data-ttu-id="330f0-125">只有在 Lambda 包含一個輸入參數時，括號才是選擇項，否則括號是必要項。</span><span class="sxs-lookup"><span data-stu-id="330f0-125">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="330f0-126">以空括號指定零個輸入參數：</span><span class="sxs-lookup"><span data-stu-id="330f0-126">Specify zero input parameters with empty parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

<span data-ttu-id="330f0-127">兩個或多個輸入參數會包含在括號中，並且以逗號分隔：</span><span class="sxs-lookup"><span data-stu-id="330f0-127">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

<span data-ttu-id="330f0-128">通常，編譯器會使用型別推斷來判斷參數類型。</span><span class="sxs-lookup"><span data-stu-id="330f0-128">Ordinarily, the compiler uses type inference in determining parameter types.</span></span> <span data-ttu-id="330f0-129">不過，有時候編譯器會很難或是無法推斷輸入類型。</span><span class="sxs-lookup"><span data-stu-id="330f0-129">However, sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="330f0-130">當這種情形發生時，您可以明確指定類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="330f0-130">When this occurs, you can specify the types explicitly, as in the following example:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

<span data-ttu-id="330f0-131">請注意，在上面的範例中，運算式 Lambda 的主體可以包含方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="330f0-131">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="330f0-132">不過，如果您要建立在 .NET Framework 外部 (例如在 SQL Server 或 Entity Framework (EF) 中) 評估的運算式樹狀架構，則不應在 Lambda 運算式中使用方法呼叫，因為這些方法在 .NET 實作內容之外可能不具任何意義。</span><span class="sxs-lookup"><span data-stu-id="330f0-132">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server or Entity Framework (EF), you should refrain from using method calls in lambda expressions, since the methods may have no meaning outside the context of the .NET implementation.</span></span> <span data-ttu-id="330f0-133">如果您在此情況下確實選擇使用方法呼叫，請務必徹底測試，以確保可成功解析方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="330f0-133">If you do choose to use method calls in this case, be sure to test them thoroughly to ensure that the method calls can be successfuly resolved.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="330f0-134">陳述式 Lambda</span><span class="sxs-lookup"><span data-stu-id="330f0-134">Statement lambdas</span></span> ##

<span data-ttu-id="330f0-135">陳述式 Lambda 看起來就像是運算式 Lambda，不同之處在於，陳述式會包含於大括號內：</span><span class="sxs-lookup"><span data-stu-id="330f0-135">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp
(input parameters) => { statement; }
```

<span data-ttu-id="330f0-136">陳述式 Lambda 的主體可以包含任意數目的陳述式，但是實際上通常不會超過兩個或三個陳述式。</span><span class="sxs-lookup"><span data-stu-id="330f0-136">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

<span data-ttu-id="330f0-137">陳述式 Lambda 就像匿名方法，它不能用來建立運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="330f0-137">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="330f0-138">非同步 Lambda</span><span class="sxs-lookup"><span data-stu-id="330f0-138">Async lambdas</span></span> ##

<span data-ttu-id="330f0-139">您可以使用 [async](language-reference/keywords/async.md) 和 [await](language-reference/keywords/await.md) 關鍵字，輕鬆建立結合非同步處理的 Lambda 運算式和陳述式。</span><span class="sxs-lookup"><span data-stu-id="330f0-139">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](language-reference/keywords/async.md) and [await](language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="330f0-140">例如，下列範例會呼叫以非同步方式執行的 `ShowSquares` 方法。</span><span class="sxs-lookup"><span data-stu-id="330f0-140">For example, the example calls a `ShowSquares` method that executes asynchronously.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

<span data-ttu-id="330f0-141">如需如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 進行非同步程式設計](programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="330f0-141">For more information about how to create and use async methods, see [Asynchronous programming with async and await](programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="330f0-142">Lambda 運算式和元組</span><span class="sxs-lookup"><span data-stu-id="330f0-142">Lambda expressions and tuples</span></span> ##

<span data-ttu-id="330f0-143">從 C# 7.0 開始，C# 語言提供元組的內建支援。</span><span class="sxs-lookup"><span data-stu-id="330f0-143">Starting with C# 7.0, the C# language provides built-in support for tuples.</span></span> <span data-ttu-id="330f0-144">您可以將元組當做引數提供給 Lambda 運算式，而您的 Lambda 運算式也可以傳回元組。</span><span class="sxs-lookup"><span data-stu-id="330f0-144">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="330f0-145">在某些情況下，C# 編譯器會使用型別推斷來判斷元組元件的類型。</span><span class="sxs-lookup"><span data-stu-id="330f0-145">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span> 

<span data-ttu-id="330f0-146">若要定義元組，請以括號括住其元件的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="330f0-146">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="330f0-147">下列範例使用具有 5 個元件的元組將一連串數字傳遞至 Lambda 運算式，這會使每個值加倍，並傳回內含乘法運算結果之具有 5 個元件的元組。</span><span class="sxs-lookup"><span data-stu-id="330f0-147">The following example uses tuple with 5 components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with 5 components that contains the result of the multiplications.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

<span data-ttu-id="330f0-148">通常，元組的欄位會命名為 `Item1`、`Item2`，依此類推。不過，您可以定義具有具名元件的元組，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="330f0-148">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

<span data-ttu-id="330f0-149">如需 C# 中元組支援的詳細資訊，請參閱 [C# 元組類型](tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="330f0-149">For more information on support for tuples in C#, see [C# Tuple types](tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="330f0-150">具有標準查詢運算子的 Lambda</span><span class="sxs-lookup"><span data-stu-id="330f0-150">Lambdas with the standard query operators</span></span> ##

<span data-ttu-id="330f0-151">其他實作中的 LINQ to Objects 具有輸入參數，其類型是其中一種 <xref:System.Func%601> 系列的泛型委派。</span><span class="sxs-lookup"><span data-stu-id="330f0-151">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="330f0-152">這些委派使用型別參數定義輸入參數的數目和類型，以及委派的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="330f0-152">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="330f0-153">對於封裝套用至一組來源資料中每個項目的使用者定義運算式而言，`Func` 委派非常實用。</span><span class="sxs-lookup"><span data-stu-id="330f0-153">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="330f0-154">例如，若是 <xref:System.Func%601>，其語法如下：</span><span class="sxs-lookup"><span data-stu-id="330f0-154">For example, consider the <xref:System.Func%601> delegate, whose syntax is:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

<span data-ttu-id="330f0-155">委派可以透過下列程式碼具現化</span><span class="sxs-lookup"><span data-stu-id="330f0-155">The delegate can be instantiated with code like the following</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

<span data-ttu-id="330f0-156">其中 `int` 是輸入參數，而 `bool` 是傳回值。</span><span class="sxs-lookup"><span data-stu-id="330f0-156">where `int` is an input parameter, and `bool` is the return value.</span></span> <span data-ttu-id="330f0-157">傳回值一律在最後一個類型參數中指定。</span><span class="sxs-lookup"><span data-stu-id="330f0-157">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="330f0-158">叫用下列 `Func` 委派時將會傳回 true 或 false，指出輸入參數是否等於 5：</span><span class="sxs-lookup"><span data-stu-id="330f0-158">When the following `Func` delegate is invoked, it returns true or false to indicate whether the input parameter is equal to 5:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

<span data-ttu-id="330f0-159">您也可以在引數類型為 <xref:System.Linq.Expressions.Expression%601> 時提供 Lambda 運算式，例如在定義於 <xref:System.Linq.Queryable> 類型的標準查詢運算子中。</span><span class="sxs-lookup"><span data-stu-id="330f0-159">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="330f0-160">當您指定 <xref:System.Linq.Expressions.Expression%601> 引數時，Lambda 會編譯成運算式樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="330f0-160">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span> <span data-ttu-id="330f0-161">下列範例使用 [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) 標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="330f0-161">The following example uses the [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standard query operator.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

<span data-ttu-id="330f0-162">編譯器會推斷輸入參數的類型，您也可以明確指定類型。</span><span class="sxs-lookup"><span data-stu-id="330f0-162">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="330f0-163">這個特殊 Lambda 運算式會計算除以二之後餘數為 1 的整數 (`n`)。</span><span class="sxs-lookup"><span data-stu-id="330f0-163">This particular lambda expression counts those integers (`n`) that, when divided by two, have a remainder of 1.</span></span>

<span data-ttu-id="330f0-164">下列範例產生的序列會包含 `numbers` 陣列中所有位於 9 前面的項目，因為 9 是序列中第一個不符合條件的數字。</span><span class="sxs-lookup"><span data-stu-id="330f0-164">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

<span data-ttu-id="330f0-165">下列範例會用括號括住的方式來指定多個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="330f0-165">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="330f0-166">這個方法會傳回數字陣列中的所有項目，直到遇到其值小於陣列中的序數位置的數字為止。</span><span class="sxs-lookup"><span data-stu-id="330f0-166">The method returns all the elements in the numbers array until it encounters a number whose value is less than its ordinal position in the array.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="330f0-167">Lambda 運算式中的型別推斷</span><span class="sxs-lookup"><span data-stu-id="330f0-167">Type inference in lambda expressions</span></span> ##

<span data-ttu-id="330f0-168">撰寫 Lambda 時，您通常不需要指定輸入參數的類型，這是因為編譯器可以根據 Lambda 主體、參數類型，以及 C# 語言規格中所述的其他因素來推斷類型。</span><span class="sxs-lookup"><span data-stu-id="330f0-168">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors, as described in the C# Language Specification.</span></span> <span data-ttu-id="330f0-169">對於大多數的標準查詢運算子而言，第一項輸入是來源序列中項目的類型。</span><span class="sxs-lookup"><span data-stu-id="330f0-169">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="330f0-170">如果您要查詢 `IEnumerable<Customer>`，則輸入變數就會推斷為 `Customer` 物件，這表示您可以存取其方法和屬性：</span><span class="sxs-lookup"><span data-stu-id="330f0-170">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

<span data-ttu-id="330f0-171">以下是 Lambda 型別推斷的一般規則：</span><span class="sxs-lookup"><span data-stu-id="330f0-171">The general rules for type inference for lambdas are:</span></span>

- <span data-ttu-id="330f0-172">Lambda 必須包含與委派類型相同數目的參數。</span><span class="sxs-lookup"><span data-stu-id="330f0-172">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="330f0-173">Lambda 中的每個輸入引數都必須能夠隱含轉換為其對應的委派參數。</span><span class="sxs-lookup"><span data-stu-id="330f0-173">Each input argument in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="330f0-174">Lambda 的傳回值 (如果有的話) 必須能夠隱含轉換為委派的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="330f0-174">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>

<span data-ttu-id="330f0-175">請注意，Lambda 運算式本身並沒有類型，因為一般類型系統沒有內建的「Lambda 運算式」概念。</span><span class="sxs-lookup"><span data-stu-id="330f0-175">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="330f0-176">不過，有時候一般所稱的 Lambda 運算式「類型」會很實用。</span><span class="sxs-lookup"><span data-stu-id="330f0-176">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="330f0-177">在這類情況下，類型是指委派類型或是 Lambda 運算式轉換成的 <xref:System.Linq.Expressions.Expression> 類型。</span><span class="sxs-lookup"><span data-stu-id="330f0-177">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="330f0-178">Lambda 運算式中的變數範圍</span><span class="sxs-lookup"><span data-stu-id="330f0-178">Variable Scope in Lambda Expressions</span></span> ##

<span data-ttu-id="330f0-179">Lambda 可以參考「外部變數」(請參閱[匿名方法](programming-guide/statements-expressions-operators/anonymous-methods.md))，這些變數必須包含在定義 Lambda 函式的方法範圍內，或是在包含 Lambda 運算式的類型範圍內。</span><span class="sxs-lookup"><span data-stu-id="330f0-179">Lambdas can refer to *outer variables* (see [Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="330f0-180">以這種方式擷取的變數會加以儲存，以便在 Lambda 運算式中使用，即使這些變數可能會超出範圍而遭到記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="330f0-180">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="330f0-181">外部變數必須確實指派，才能用於 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="330f0-181">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="330f0-182">下列範例將示範這些規則。</span><span class="sxs-lookup"><span data-stu-id="330f0-182">The following example demonstrates these rules.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 <span data-ttu-id="330f0-183">下列規則適用於 Lambda 運算式中的變數範圍：</span><span class="sxs-lookup"><span data-stu-id="330f0-183">The following rules apply to variable scope in lambda expressions:</span></span>

- <span data-ttu-id="330f0-184">已擷取的變數要等到參考該變數的委派符合記憶體回收的資格時，才會進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="330f0-184">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="330f0-185">導入 Lambda 運算式內的變數無法在外部方法中看見。</span><span class="sxs-lookup"><span data-stu-id="330f0-185">Variables introduced within a lambda expression are not visible in the outer method.</span></span>

- <span data-ttu-id="330f0-186">Lambda 運算式無法直接從封入方法擷取 `in`、`ref` 或 `out` 參數。</span><span class="sxs-lookup"><span data-stu-id="330f0-186">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>

- <span data-ttu-id="330f0-187">Lambda 運算式中的 return 陳述式不會造成封入方法傳回。</span><span class="sxs-lookup"><span data-stu-id="330f0-187">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>

- <span data-ttu-id="330f0-188">如果跳躍陳述式的目標不在區塊內，則 Lambda 運算式不可包含 Lambda 函式內的 `goto` 陳述式、 `break` 陳述式或 `continue` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="330f0-188">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="330f0-189">即使目標位於區塊內，跳躍陳述式出現在 Lambda 函式區塊外部也一樣是錯誤。</span><span class="sxs-lookup"><span data-stu-id="330f0-189">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>

## <a name="see-also"></a><span data-ttu-id="330f0-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="330f0-190">See also</span></span> ##

<span data-ttu-id="330f0-191">[LINQ (Language-Integrated Query)](../standard/using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="330f0-191">[LINQ (Language-Integrated Query)](../standard/using-linq.md) </span></span>  
<span data-ttu-id="330f0-192">[匿名方法](programming-guide/statements-expressions-operators/anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="330f0-192">[Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md) </span></span>  
[<span data-ttu-id="330f0-193">運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="330f0-193">Expression trees</span></span>](expression-trees.md)
