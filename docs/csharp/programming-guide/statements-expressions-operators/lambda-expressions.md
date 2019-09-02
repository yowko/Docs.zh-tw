---
title: Lambda 運算式 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 1a608a9102e5fb19e40294761c0de98f7e008133
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168985"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="9c0d2-102">Lambda 運算式 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="9c0d2-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="9c0d2-103">「Lambda 運算式」  是下列兩種形式之一的運算式：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-103">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="9c0d2-104">以運算式作為主體的[運算式 Lambda](#expression-lambdas)：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-104">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="9c0d2-105">以陳述式區塊作為主體的[陳述式 Lambda](#statement-lambdas)：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-105">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="9c0d2-106">請使用 [Lambda 宣告運算子 `=>` ](../../language-reference/operators/lambda-operator.md) 來分隔 Lambda 的參數清單及其主體。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-106">Use the [lambda declaration operator `=>`](../../language-reference/operators/lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="9c0d2-107">若要建立 Lambda 運算式，請在 Lambda 運算子 的左邊指定輸入參數 (如果有的話)，並在另一邊指定運算式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-107">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="9c0d2-108">任何 Lambda 運算式可轉換成[委派](../../language-reference/builtin-types/reference-types.md#the-delegate-type)型別。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-108">Any lambda expression can be converted to a [delegate](../../language-reference/builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="9c0d2-109">Lambda 運算式可以轉換成的委派型別，是由其參數和傳回值的型別所定義。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-109">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="9c0d2-110">如果 Lambda 運算式不會傳回值，則其可轉換成其中一個 `Action` 委派型別；否則可轉換成其中一個 `Func` 委派型別。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-110">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="9c0d2-111">例如，具有兩個參數且不會傳回值的 Lambda 運算式，可以轉換成 <xref:System.Action%602> 委派。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-111">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="9c0d2-112">具有一個參數且會傳回值的 Lambda 運算式，可以轉換成 <xref:System.Func%602> 委派。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-112">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="9c0d2-113">在下列範例中，Lambda 運算式 `x => x * x` 會指定名為 `x` 的參數，並傳回 `x` 平方的值，此運算式已指派給委派型別的變數：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-113">In the following example, the lambda expression `x => x * x`, which specifies a parameter that’s named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="9c0d2-114">Lambda 運算式也可以轉換成[運算式樹狀架構](../concepts/expression-trees/index.md)型別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-114">Expression lambdas also can be converted to the [expression tree](../concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="9c0d2-115">您可以在任何需要委派型別或運算式樹狀架構執行個體的程式碼中使用 Lambda 運算式，例如作為 <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> 方法的引數，以傳遞應該在背景中執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-115">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="9c0d2-116">當您撰寫 [LINQ 查詢運算式](../../linq/index.md)時，也可以使用 Lambda 運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-116">You also can use lambda expressions when you write [LINQ query expressions](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="9c0d2-117">當您使用以方法為基礎的語法呼叫 <xref:System.Linq.Enumerable?displayProperty=nameWithType> 類別中的 <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> 方法時 (例如在 LINQ to Objects 和 LINQ to XML中所執行)，此參數會是委派型別 <xref:System.Func%602?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-117">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9c0d2-118">當您在 <xref:System.Linq.Queryable?displayProperty=nameWithType> 類別中呼叫 <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> 方法時 (例如在 LINQ to SQL 中所執行)，參數型別是運算式樹狀架構型別 [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-118">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="9c0d2-119">在這兩種情況下，您都可以使用相同的 Lambda 運算式來指定參數值。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-119">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="9c0d2-120">那會讓兩個 `Select` 呼叫看起來很相似，但是實際上從 Lambda 建立的物件型別並不相同。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-120">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="9c0d2-121">運算式 Lambda</span><span class="sxs-lookup"><span data-stu-id="9c0d2-121">Expression lambdas</span></span>

<span data-ttu-id="9c0d2-122">在 `=>` 運算子右邊有運算式的 Lambda 運算式稱為「運算式 Lambda」  。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-122">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="9c0d2-123">運算式 Lambda 會在[運算式樹狀架構](../concepts/expression-trees/index.md)的建構過程中大量使用。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-123">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="9c0d2-124">運算式 Lambda 會傳回運算式的結果，並採用下列基本形式：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-124">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="9c0d2-125">只有在 Lambda 包含一個輸入參數時，括號才是選擇項，否則括號是必要項。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-125">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="9c0d2-126">以空括號指定零個輸入參數：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-126">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="9c0d2-127">兩個或多個輸入參數會包含在括號中，並且以逗號分隔：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-127">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="9c0d2-128">有時候編譯器無法推斷輸入類型。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-128">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="9c0d2-129">您可以明確指定類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-129">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="9c0d2-130">輸入參數類型必須全部為明確或全部為隱含；否則，會發生 [CS0748](../../misc/cs0748.md) 編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-130">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="9c0d2-131">運算式 Lambda 的主體可以包含方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-131">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="9c0d2-132">不過，如果您要建立在 .NET 通用語言執行平台外部 (例如在 SQL Server 中) 評估的運算式樹狀架構，則不應在 Lambda 運算式中使用方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-132">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="9c0d2-133">這些方法在 .NET 通用語言執行平台內容之外將不具任何意義。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-133">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="9c0d2-134">陳述式 Lambda</span><span class="sxs-lookup"><span data-stu-id="9c0d2-134">Statement lambdas</span></span>

<span data-ttu-id="9c0d2-135">陳述式 Lambda 看起來就像是運算式 Lambda，不同之處在於，陳述式會包含於大括號內：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-135">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="9c0d2-136">陳述式 Lambda 的主體可以包含任意數目的陳述式，但是實際上通常不會超過兩個或三個陳述式。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-136">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="9c0d2-137">陳述式 Lambda 無法用來建立運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-137">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="9c0d2-138">非同步 Lambda</span><span class="sxs-lookup"><span data-stu-id="9c0d2-138">Async lambdas</span></span>

<span data-ttu-id="9c0d2-139">您可以使用 [async](../../language-reference/keywords/async.md) 和 [await](../../language-reference/operators/await.md) 關鍵字，輕鬆建立結合非同步處理的 Lambda 運算式和陳述式。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-139">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/operators/await.md) keywords.</span></span> <span data-ttu-id="9c0d2-140">例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-140">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="9c0d2-141">您可以使用非同步 Lambda 加入相同的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-141">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="9c0d2-142">若要加入這個處理常式，請將 `async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-142">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="9c0d2-143">如需如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 進行非同步程式設計](../concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-143">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="9c0d2-144">Lambda 運算式和元組</span><span class="sxs-lookup"><span data-stu-id="9c0d2-144">Lambda expressions and tuples</span></span>

<span data-ttu-id="9c0d2-145">從 C# 7.0 開始，C# 語言提供[元組](../../tuples.md)的內建支援。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-145">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="9c0d2-146">您可以將元組當做引數提供給 Lambda 運算式，而您的 Lambda 運算式也可以傳回元組。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-146">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="9c0d2-147">在某些情況下，C# 編譯器會使用型別推斷來判斷元組元件的類型。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-147">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="9c0d2-148">若要定義元組，請以括號括住其元件的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-148">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="9c0d2-149">下列範例使用具有 3 個元件的元組將一連串數字傳遞至 Lambda 運算式，這會使每個值加倍，並傳回具有三個元件的元組，其中包含乘法運算的結果。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-149">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="9c0d2-150">通常，元組的欄位會命名為 `Item1`、`Item2`，依此類推。不過，您可以定義具有具名元件的元組，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-150">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="9c0d2-151">如需 C# 元組的詳細資訊，請參閱 [C# 元組型別](../../tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-151">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="9c0d2-152">具有標準查詢運算子的 Lambda</span><span class="sxs-lookup"><span data-stu-id="9c0d2-152">Lambdas with the standard query operators</span></span>

<span data-ttu-id="9c0d2-153">其他實作中的 LINQ to Objects 具有輸入參數，其類型是其中一種 <xref:System.Func%601> 系列的泛型委派。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-153">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="9c0d2-154">這些委派使用型別參數定義輸入參數的數目和類型，以及委派的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-154">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="9c0d2-155">對於封裝套用至一組來源資料中每個項目的使用者定義運算式而言，`Func` 委派非常實用。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-155">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="9c0d2-156">例如，請考慮 <xref:System.Func%602> 委派類型：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-156">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="9c0d2-157">委派可以具現化為 `Func<int, bool>` 執行個體，其中 `int` 是輸入參數，而 `bool` 是傳回值。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-157">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="9c0d2-158">傳回值一律在最後一個類型參數中指定。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-158">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="9c0d2-159">例如，`Func<int, string, bool>` 定義具有兩個輸入參數 (`int` 和 `string`) 的委派與 `bool` 的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-159">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="9c0d2-160">叫用下列 `Func` 委派時會傳回布林值，指出輸入參數是否等於 5：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-160">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="9c0d2-161">您也可以在引數類型為 <xref:System.Linq.Expressions.Expression%601> 時提供 Lambda 運算式，例如在定義於 <xref:System.Linq.Queryable> 類型的標準查詢運算子中。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-161">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="9c0d2-162">當您指定 <xref:System.Linq.Expressions.Expression%601> 引數時，Lambda 會編譯成運算式樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-162">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="9c0d2-163">下列範例使用 <xref:System.Linq.Enumerable.Count%2A> 標準查詢運算子：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-163">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="9c0d2-164">編譯器會推斷輸入參數的類型，您也可以明確指定類型。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-164">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="9c0d2-165">這個特殊 Lambda 運算式會計算除以二之後餘數為 1 的整數 (`n`)。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-165">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="9c0d2-166">下列範例產生的序列會包含 `numbers` 陣列中所有位於 9 前面的元素，因為 9 是序列中第一個不符合條件的數字：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-166">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="9c0d2-167">下列範例會用括號括住的方式來指定多個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-167">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="9c0d2-168">這個方法會傳回 `numbers` 陣列中的所有元素，直到遇到其值小於陣列中的序數位置的數字為止：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-168">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="9c0d2-169">Lambda 運算式中的型別推斷</span><span class="sxs-lookup"><span data-stu-id="9c0d2-169">Type inference in lambda expressions</span></span>

<span data-ttu-id="9c0d2-170">撰寫 Lambda 時，您通常不需要指定輸入參數的類型，這是因為編譯器可以根據 Lambda 主體、參數類型，以及 C# 語言規格中所述的其他因素來推斷類型。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-170">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="9c0d2-171">對於大多數的標準查詢運算子而言，第一項輸入是來源序列中項目的類型。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-171">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="9c0d2-172">如果您要查詢 `IEnumerable<Customer>`，則輸入變數就會推斷為 `Customer` 物件，這表示您可以存取其方法和屬性：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-172">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="9c0d2-173">Lambda 型別推斷的一般規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-173">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="9c0d2-174">Lambda 必須包含與委派類型相同數目的參數。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-174">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="9c0d2-175">Lambda 中的每個輸入參數都必須能夠隱含轉換為其對應的委派參數。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-175">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="9c0d2-176">Lambda 的傳回值 (如果有的話) 必須能夠隱含轉換為委派的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-176">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="9c0d2-177">請注意，Lambda 運算式本身並沒有類型，因為一般類型系統沒有內建的「Lambda 運算式」概念。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-177">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="9c0d2-178">不過，有時候一般所稱的 Lambda 運算式「類型」會很實用。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-178">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="9c0d2-179">在這類情況下，類型是指委派類型或是 Lambda 運算式轉換成的 <xref:System.Linq.Expressions.Expression> 類型。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-179">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="9c0d2-180">Lambda 運算式中的擷取外部變數和變數範圍</span><span class="sxs-lookup"><span data-stu-id="9c0d2-180">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="9c0d2-181">Lambda 可以參考「外部變數」  。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-181">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="9c0d2-182">這些是在定義 Lambda 運算式的方法範圍內，或是在包含 Lambda 運算式的型別範圍內的變數。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-182">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="9c0d2-183">以這種方式擷取的變數會加以儲存，以便在 Lambda 運算式中使用，即使這些變數可能會超出範圍而遭到記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-183">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="9c0d2-184">外部變數必須確實指派，才能用於 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-184">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="9c0d2-185">下列範例將示範這些規則：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-185">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="9c0d2-186">下列規則適用於 Lambda 運算式中的變數範圍：</span><span class="sxs-lookup"><span data-stu-id="9c0d2-186">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="9c0d2-187">已擷取的變數要等到參考該變數的委派符合記憶體回收的資格時，才會進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-187">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="9c0d2-188">導入 Lambda 運算式內的變數無法在封入方法中看見。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-188">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="9c0d2-189">Lambda 運算式無法直接從封入方法擷取 [in](../../language-reference/keywords/in-parameter-modifier.md)、[ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-189">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="9c0d2-190">Lambda 運算式中的 [return](../../language-reference/keywords/return.md) 陳述式不會造成封入方法傳回。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-190">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="9c0d2-191">如果該跳躍陳述式的目標位於 Lambda 運算式區塊之外，則 Lambda 運算式不能包含 [goto](../../language-reference/keywords/goto.md)、[break](../../language-reference/keywords/break.md) 或 [continue](../../language-reference/keywords/continue.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-191">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="9c0d2-192">即使目標位於區塊內，跳躍陳述式出現在 Lambda 運算式區塊外部也一樣是錯誤。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-192">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9c0d2-193">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9c0d2-193">C# language specification</span></span>

<span data-ttu-id="9c0d2-194">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[匿名函式運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-194">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="9c0d2-195">精選書籍章節</span><span class="sxs-lookup"><span data-stu-id="9c0d2-195">Featured book chapter</span></span>

<span data-ttu-id="9c0d2-196">[C# 3.0 Cookbook 第三版：250 個以上 C# 3.0 程式設計人員適用的方案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)中的[委派、事件與 Lambda 運算式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="9c0d2-196">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0d2-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c0d2-197">See also</span></span>

- [<span data-ttu-id="9c0d2-198">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9c0d2-198">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9c0d2-199">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="9c0d2-199">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="9c0d2-200">運算式樹狀結構</span><span class="sxs-lookup"><span data-stu-id="9c0d2-200">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="9c0d2-201">區域函式與 Lambda 運算式的比較</span><span class="sxs-lookup"><span data-stu-id="9c0d2-201">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="9c0d2-202">隱含型別 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="9c0d2-202">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="9c0d2-203">Visual Studio 2008 C# 範例 (請參閱 LINQ 範例查詢檔案和 XQuery 程式)</span><span class="sxs-lookup"><span data-stu-id="9c0d2-203">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="9c0d2-204">Recursive lambda expressions (遞迴的 Lambda 運算式)</span><span class="sxs-lookup"><span data-stu-id="9c0d2-204">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
