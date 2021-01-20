---
title: 'Lambda 運算式-c # 參考'
description: 瞭解 lambda 運算式。 有運算式 lambda 有運算式做為其主體，或具有語句區塊做為主體的語句 lambda。
ms.date: 09/25/2020
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 2ae63396c0b1bb0bf1fe5c33b1103f69f6dcf664
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615863"
---
# <a name="lambda-expressions-c-reference"></a><span data-ttu-id="c0864-104">Lambda 運算式 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="c0864-104">Lambda expressions (C# reference)</span></span>

<span data-ttu-id="c0864-105">您可以使用 *lambda 運算式* 來建立匿名函式。</span><span class="sxs-lookup"><span data-stu-id="c0864-105">You use a *lambda expression* to create an anonymous function.</span></span> <span data-ttu-id="c0864-106">請使用 [Lambda 宣告運算子 `=>`](lambda-operator.md) 來分隔 Lambda 的參數清單及其主體。</span><span class="sxs-lookup"><span data-stu-id="c0864-106">Use the [lambda declaration operator `=>`](lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="c0864-107">Lambda 運算式可以是下列兩種形式的任一個：</span><span class="sxs-lookup"><span data-stu-id="c0864-107">A lambda expression can be of any of the following two forms:</span></span>

- <span data-ttu-id="c0864-108">以運算式作為主體的[運算式 Lambda](#expression-lambdas)：</span><span class="sxs-lookup"><span data-stu-id="c0864-108">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="c0864-109">以陳述式區塊作為主體的[陳述式 Lambda](#statement-lambdas)：</span><span class="sxs-lookup"><span data-stu-id="c0864-109">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="c0864-110">若要建立 Lambda 運算式，請在 Lambda 運算子 的左邊指定輸入參數 (如果有的話)，並在另一邊指定運算式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="c0864-110">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="c0864-111">任何 Lambda 運算式可轉換成[委派](../builtin-types/reference-types.md#the-delegate-type)型別。</span><span class="sxs-lookup"><span data-stu-id="c0864-111">Any lambda expression can be converted to a [delegate](../builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="c0864-112">Lambda 運算式可以轉換成的委派型別，是由其參數和傳回值的型別所定義。</span><span class="sxs-lookup"><span data-stu-id="c0864-112">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="c0864-113">如果 Lambda 運算式不會傳回值，則其可轉換成其中一個 `Action` 委派型別；否則可轉換成其中一個 `Func` 委派型別。</span><span class="sxs-lookup"><span data-stu-id="c0864-113">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="c0864-114">例如，具有兩個參數且不會傳回值的 Lambda 運算式，可以轉換成 <xref:System.Action%602> 委派。</span><span class="sxs-lookup"><span data-stu-id="c0864-114">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="c0864-115">具有一個參數且會傳回值的 Lambda 運算式，可以轉換成 <xref:System.Func%602> 委派。</span><span class="sxs-lookup"><span data-stu-id="c0864-115">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="c0864-116">在下列範例中，lambda 運算式 `x => x * x` 會指定名為的參數，並傳回 `x` `x` 平方值，並指派給委派類型的變數：</span><span class="sxs-lookup"><span data-stu-id="c0864-116">In the following example, the lambda expression `x => x * x`, which specifies a parameter that's named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](snippets/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="c0864-117">運算式 lambda 也可以轉換成 [運算式樹狀](../../programming-guide/concepts/expression-trees/index.md) 架構類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c0864-117">Expression lambdas can also be converted to the [expression tree](../../programming-guide/concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](snippets/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="c0864-118">您可以在任何需要委派型別或運算式樹狀架構執行個體的程式碼中使用 Lambda 運算式，例如作為 <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> 方法的引數，以傳遞應該在背景中執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c0864-118">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="c0864-119">當您 [在 c # 中撰寫 LINQ](../../linq/index.md)時，您也可以使用 lambda 運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c0864-119">You can also use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](snippets/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="c0864-120">當您使用以方法為基礎的語法呼叫 <xref:System.Linq.Enumerable?displayProperty=nameWithType> 類別中的 <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> 方法時 (例如在 LINQ to Objects 和 LINQ to XML中所執行)，此參數會是委派型別 <xref:System.Func%602?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c0864-120">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c0864-121">當您在類別中呼叫 <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> 方法時 <xref:System.Linq.Queryable?displayProperty=nameWithType> （例如在 LINQ to SQL 中），參數類型為運算式樹狀架構類型 [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) 。</span><span class="sxs-lookup"><span data-stu-id="c0864-121">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="c0864-122">在這兩種情況下，您都可以使用相同的 Lambda 運算式來指定參數值。</span><span class="sxs-lookup"><span data-stu-id="c0864-122">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="c0864-123">那會讓兩個 `Select` 呼叫看起來很相似，但是實際上從 Lambda 建立的物件型別並不相同。</span><span class="sxs-lookup"><span data-stu-id="c0864-123">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="c0864-124">運算式 Lambda</span><span class="sxs-lookup"><span data-stu-id="c0864-124">Expression lambdas</span></span>

<span data-ttu-id="c0864-125">在 `=>` 運算子右邊有運算式的 Lambda 運算式稱為「運算式 Lambda」。</span><span class="sxs-lookup"><span data-stu-id="c0864-125">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="c0864-126">運算式 Lambda 會傳回運算式的結果，並採用下列基本形式：</span><span class="sxs-lookup"><span data-stu-id="c0864-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="c0864-127">運算式 Lambda 的主體可以包含方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="c0864-127">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="c0864-128">但是，如果您要建立的 [運算式樹狀](../../programming-guide/concepts/expression-trees/index.md) 架構是在 .Net Common Language RUNTIME (CLR) 的內容之外進行評估，例如在 SQL Server 中，您不應該在 lambda 運算式中使用方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="c0864-128">However, if you are creating [expression trees](../../programming-guide/concepts/expression-trees/index.md) that are evaluated outside the context of the .NET Common Language Runtime (CLR), such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="c0864-129">方法不會在 .NET Common Language Runtime (CLR) 的內容之外，沒有任何意義。</span><span class="sxs-lookup"><span data-stu-id="c0864-129">The methods will have no meaning outside the context of the .NET Common Language Runtime (CLR).</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="c0864-130">陳述式 Lambda</span><span class="sxs-lookup"><span data-stu-id="c0864-130">Statement lambdas</span></span>

<span data-ttu-id="c0864-131">語句 lambda 類似于運算式 lambda，不同之處在于其語句是以大括弧括住：</span><span class="sxs-lookup"><span data-stu-id="c0864-131">A statement lambda resembles an expression lambda except that its statements are enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="c0864-132">陳述式 Lambda 的主體可以包含任意數目的陳述式，但是實際上通常不會超過兩個或三個陳述式。</span><span class="sxs-lookup"><span data-stu-id="c0864-132">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetStatementLambda":::

<span data-ttu-id="c0864-133">您無法使用語句 lambda 來建立運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="c0864-133">You cannot use statement lambdas to create expression trees.</span></span>

## <a name="input-parameters-of-a-lambda-expression"></a><span data-ttu-id="c0864-134">Lambda 運算式的輸入參數</span><span class="sxs-lookup"><span data-stu-id="c0864-134">Input parameters of a lambda expression</span></span>

<span data-ttu-id="c0864-135">您可以用括弧括住 lambda 運算式的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="c0864-135">You enclose input parameters of a lambda expression in parentheses.</span></span> <span data-ttu-id="c0864-136">以空括號指定零個輸入參數：</span><span class="sxs-lookup"><span data-stu-id="c0864-136">Specify zero input parameters with empty parentheses:</span></span>  

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetZeroParameters":::

<span data-ttu-id="c0864-137">如果 lambda 運算式只有一個輸入參數，則括弧是選擇性的：</span><span class="sxs-lookup"><span data-stu-id="c0864-137">If a lambda expression has only one input parameter, parentheses are optional:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetOneParameter":::

<span data-ttu-id="c0864-138">兩個或多個輸入參數會以逗號分隔：</span><span class="sxs-lookup"><span data-stu-id="c0864-138">Two or more input parameters are separated by commas:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetTwoParameters":::

<span data-ttu-id="c0864-139">有時編譯器無法推斷輸入參數的類型。</span><span class="sxs-lookup"><span data-stu-id="c0864-139">Sometimes the compiler can't infer the types of input parameters.</span></span> <span data-ttu-id="c0864-140">您可以明確指定類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c0864-140">You can specify the types explicitly as shown in the following example:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetExplicitlyTypedParameters":::

<span data-ttu-id="c0864-141">輸入參數類型必須全部為明確或全部為隱含；否則，會發生 [CS0748](../../misc/cs0748.md) 編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0864-141">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="c0864-142">從 c # 9.0 開始，您可以使用 [ [捨棄](../../discards.md) ] 來指定運算式中未使用之 lambda 運算式的兩個或多個輸入參數：</span><span class="sxs-lookup"><span data-stu-id="c0864-142">Beginning with C# 9.0, you can use [discards](../../discards.md) to specify two or more input parameters of a lambda expression that aren't used in the expression:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetDiscards":::

<span data-ttu-id="c0864-143">當您使用 lambda 運算式來 [提供事件處理常式](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)時，lambda 捨棄參數可能很有用。</span><span class="sxs-lookup"><span data-stu-id="c0864-143">Lambda discard parameters may be useful when you use a lambda expression to [provide an event handler](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c0864-144">為了回溯相容性，如果只命名單一輸入參數 `_` ，則會將 lambda 運算式內的 `_` 視為該參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0864-144">For backwards compatibility, if only a single input parameter is named `_`, then, within a lambda expression, `_` is treated as the name of that parameter.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="c0864-145">非同步 Lambda</span><span class="sxs-lookup"><span data-stu-id="c0864-145">Async lambdas</span></span>

<span data-ttu-id="c0864-146">您可以使用 [async](../keywords/async.md) 和 [await](await.md) 關鍵字，輕鬆建立結合非同步處理的 Lambda 運算式和陳述式。</span><span class="sxs-lookup"><span data-stu-id="c0864-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../keywords/async.md) and [await](await.md) keywords.</span></span> <span data-ttu-id="c0864-147">例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c0864-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="c0864-148">您可以使用非同步 Lambda 加入相同的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c0864-148">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="c0864-149">若要加入這個處理常式，請將 `async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c0864-149">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="c0864-150">如需如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 進行非同步程式設計](../../programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c0864-150">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="c0864-151">Lambda 運算式和元組</span><span class="sxs-lookup"><span data-stu-id="c0864-151">Lambda expressions and tuples</span></span>

<span data-ttu-id="c0864-152">從 c # 7.0 開始，c # 語言提供 [元組](../builtin-types/value-tuples.md)的內建支援。</span><span class="sxs-lookup"><span data-stu-id="c0864-152">Starting with C# 7.0, the C# language provides built-in support for [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="c0864-153">您可以將元組當做引數提供給 Lambda 運算式，而您的 Lambda 運算式也可以傳回元組。</span><span class="sxs-lookup"><span data-stu-id="c0864-153">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="c0864-154">在某些情況下，C# 編譯器會使用型別推斷來判斷元組元件的類型。</span><span class="sxs-lookup"><span data-stu-id="c0864-154">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="c0864-155">若要定義元組，請以括號括住其元件的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="c0864-155">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="c0864-156">下列範例使用具有 3 個元件的元組將一連串數字傳遞至 Lambda 運算式，這會使每個值加倍，並傳回具有三個元件的元組，其中包含乘法運算的結果。</span><span class="sxs-lookup"><span data-stu-id="c0864-156">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="c0864-157">一般來說，元組的欄位會命名為 `Item1` 、等等 `Item2` 。不過，您可以定義具有命名元件的元組，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c0864-157">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="c0864-158">如需 c # 元組的詳細資訊，請參閱 [元組類型](../../language-reference/builtin-types/value-tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="c0864-158">For more information about C# tuples, see [Tuple types](../../language-reference/builtin-types/value-tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="c0864-159">具有標準查詢運算子的 Lambda</span><span class="sxs-lookup"><span data-stu-id="c0864-159">Lambdas with the standard query operators</span></span>

<span data-ttu-id="c0864-160">其他實作中的 LINQ to Objects 具有輸入參數，其類型是其中一種 <xref:System.Func%601> 系列的泛型委派。</span><span class="sxs-lookup"><span data-stu-id="c0864-160">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="c0864-161">這些委派使用型別參數定義輸入參數的數目和類型，以及委派的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="c0864-161">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="c0864-162">對於封裝套用至一組來源資料中每個項目的使用者定義運算式而言，`Func` 委派非常實用。</span><span class="sxs-lookup"><span data-stu-id="c0864-162">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="c0864-163">例如，請考慮 <xref:System.Func%602> 委派類型：</span><span class="sxs-lookup"><span data-stu-id="c0864-163">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="c0864-164">委派可以具現化為 `Func<int, bool>` 執行個體，其中 `int` 是輸入參數，而 `bool` 是傳回值。</span><span class="sxs-lookup"><span data-stu-id="c0864-164">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="c0864-165">傳回值一律在最後一個類型參數中指定。</span><span class="sxs-lookup"><span data-stu-id="c0864-165">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="c0864-166">例如，`Func<int, string, bool>` 定義具有兩個輸入參數 (`int` 和 `string`) 的委派與 `bool` 的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="c0864-166">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="c0864-167">叫用下列 `Func` 委派時會傳回布林值，指出輸入參數是否等於 5：</span><span class="sxs-lookup"><span data-stu-id="c0864-167">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="c0864-168">您也可以在引數類型為 <xref:System.Linq.Expressions.Expression%601> 時提供 Lambda 運算式，例如在定義於 <xref:System.Linq.Queryable> 類型的標準查詢運算子中。</span><span class="sxs-lookup"><span data-stu-id="c0864-168">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="c0864-169">當您指定 <xref:System.Linq.Expressions.Expression%601> 引數時，Lambda 會編譯成運算式樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="c0864-169">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="c0864-170">下列範例使用 <xref:System.Linq.Enumerable.Count%2A> 標準查詢運算子：</span><span class="sxs-lookup"><span data-stu-id="c0864-170">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="c0864-171">編譯器會推斷輸入參數的類型，您也可以明確指定類型。</span><span class="sxs-lookup"><span data-stu-id="c0864-171">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="c0864-172">這個特殊 Lambda 運算式會計算除以二之後餘數為 1 的整數 (`n`)。</span><span class="sxs-lookup"><span data-stu-id="c0864-172">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="c0864-173">下列範例產生的序列會包含 `numbers` 陣列中所有位於 9 前面的元素，因為 9 是序列中第一個不符合條件的數字：</span><span class="sxs-lookup"><span data-stu-id="c0864-173">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="c0864-174">下列範例會用括號括住的方式來指定多個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="c0864-174">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="c0864-175">這個方法會傳回 `numbers` 陣列中的所有元素，直到遇到其值小於陣列中的序數位置的數字為止：</span><span class="sxs-lookup"><span data-stu-id="c0864-175">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="c0864-176">Lambda 運算式中的型別推斷</span><span class="sxs-lookup"><span data-stu-id="c0864-176">Type inference in lambda expressions</span></span>

<span data-ttu-id="c0864-177">撰寫 Lambda 時，您通常不需要指定輸入參數的類型，這是因為編譯器可以根據 Lambda 主體、參數類型，以及 C# 語言規格中所述的其他因素來推斷類型。</span><span class="sxs-lookup"><span data-stu-id="c0864-177">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="c0864-178">對於大多數的標準查詢運算子而言，第一項輸入是來源序列中項目的類型。</span><span class="sxs-lookup"><span data-stu-id="c0864-178">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="c0864-179">如果您要查詢 `IEnumerable<Customer>`，則輸入變數就會推斷為 `Customer` 物件，這表示您可以存取其方法和屬性：</span><span class="sxs-lookup"><span data-stu-id="c0864-179">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="c0864-180">Lambda 型別推斷的一般規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="c0864-180">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="c0864-181">Lambda 必須包含與委派類型相同數目的參數。</span><span class="sxs-lookup"><span data-stu-id="c0864-181">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="c0864-182">Lambda 中的每個輸入參數都必須能夠隱含轉換為其對應的委派參數。</span><span class="sxs-lookup"><span data-stu-id="c0864-182">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="c0864-183">Lambda 的傳回值 (如果有的話) 必須能夠隱含轉換為委派的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="c0864-183">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="c0864-184">請注意，Lambda 運算式本身並沒有類型，因為一般類型系統沒有內建的「Lambda 運算式」概念。</span><span class="sxs-lookup"><span data-stu-id="c0864-184">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="c0864-185">不過，有時候一般所稱的 Lambda 運算式「類型」會很實用。</span><span class="sxs-lookup"><span data-stu-id="c0864-185">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="c0864-186">在這類情況下，類型是指委派類型或是 Lambda 運算式轉換成的 <xref:System.Linq.Expressions.Expression> 類型。</span><span class="sxs-lookup"><span data-stu-id="c0864-186">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="c0864-187">Lambda 運算式中的擷取外部變數和變數範圍</span><span class="sxs-lookup"><span data-stu-id="c0864-187">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="c0864-188">Lambda 可以參考「外部變數」。</span><span class="sxs-lookup"><span data-stu-id="c0864-188">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="c0864-189">這些是在定義 Lambda 運算式的方法範圍內，或是在包含 Lambda 運算式的型別範圍內的變數。</span><span class="sxs-lookup"><span data-stu-id="c0864-189">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="c0864-190">以這種方式擷取的變數會加以儲存，以便在 Lambda 運算式中使用，即使這些變數可能會超出範圍而遭到記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="c0864-190">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="c0864-191">外部變數必須確實指派，才能用於 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="c0864-191">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="c0864-192">下列範例將示範這些規則：</span><span class="sxs-lookup"><span data-stu-id="c0864-192">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](snippets/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="c0864-193">下列規則適用於 Lambda 運算式中的變數範圍：</span><span class="sxs-lookup"><span data-stu-id="c0864-193">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="c0864-194">已擷取的變數要等到參考該變數的委派符合記憶體回收的資格時，才會進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="c0864-194">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="c0864-195">導入 Lambda 運算式內的變數無法在封入方法中看見。</span><span class="sxs-lookup"><span data-stu-id="c0864-195">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="c0864-196">Lambda 運算式無法直接從封入方法擷取 [in](../keywords/in-parameter-modifier.md)、[ref](../keywords/ref.md) 或 [out](../keywords/out-parameter-modifier.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="c0864-196">A lambda expression cannot directly capture an [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md), or [out](../keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="c0864-197">Lambda 運算式中的 [return](../keywords/return.md) 陳述式不會造成封入方法傳回。</span><span class="sxs-lookup"><span data-stu-id="c0864-197">A [return](../keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="c0864-198">如果該跳躍陳述式的目標位於 Lambda 運算式區塊之外，則 Lambda 運算式不能包含 [goto](../keywords/goto.md)、[break](../keywords/break.md) 或 [continue](../keywords/continue.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c0864-198">A lambda expression cannot contain a [goto](../keywords/goto.md), [break](../keywords/break.md), or [continue](../keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="c0864-199">即使目標位於區塊內，跳躍陳述式出現在 Lambda 運算式區塊外部也一樣是錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0864-199">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

<span data-ttu-id="c0864-200">從 c # 9.0 開始，您可以將 `static` 修飾詞套用至 lambda 運算式，以避免不慎捕捉 lambda 的區域變數或實例狀態：</span><span class="sxs-lookup"><span data-stu-id="c0864-200">Beginning with C# 9.0, you can apply the `static` modifier to a lambda expression to prevent unintentional capture of local variables or instance state by the lambda:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetStatic":::

<span data-ttu-id="c0864-201">靜態 lambda 無法從封入範圍中捕捉本機變數或實例狀態，但可能會參考靜態成員和常數定義。</span><span class="sxs-lookup"><span data-stu-id="c0864-201">A static lambda can't capture local variables or instance state from enclosing scopes, but may reference static members and constant definitions.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c0864-202">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c0864-202">C# language specification</span></span>

<span data-ttu-id="c0864-203">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[匿名函式運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="c0864-203">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="c0864-204">如需 c # 9.0 中新增之功能的詳細資訊，請參閱下列功能提案附注：</span><span class="sxs-lookup"><span data-stu-id="c0864-204">For more information about features added in C# 9.0, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="c0864-205">Lambda 捨棄參數</span><span class="sxs-lookup"><span data-stu-id="c0864-205">Lambda discard parameters</span></span>](~/_csharplang/proposals/csharp-9.0/lambda-discard-parameters.md)
- [<span data-ttu-id="c0864-206">靜態匿名函式</span><span class="sxs-lookup"><span data-stu-id="c0864-206">Static anonymous functions</span></span>](~/_csharplang/proposals/csharp-9.0/static-anonymous-functions.md)

## <a name="see-also"></a><span data-ttu-id="c0864-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0864-207">See also</span></span>

- [<span data-ttu-id="c0864-208">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="c0864-208">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c0864-209">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="c0864-209">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="c0864-210">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="c0864-210">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="c0864-211">運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="c0864-211">Expression Trees</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="c0864-212">區域函式與 Lambda 運算式的比較</span><span class="sxs-lookup"><span data-stu-id="c0864-212">Local functions vs. lambda expressions</span></span>](../../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [<span data-ttu-id="c0864-213">Visual Studio 2008 C# 範例 (請參閱 LINQ 範例查詢檔案和 XQuery 程式)</span><span class="sxs-lookup"><span data-stu-id="c0864-213">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
