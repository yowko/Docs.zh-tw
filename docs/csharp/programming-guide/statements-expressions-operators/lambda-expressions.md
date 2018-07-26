---
title: Lambda 運算式 (C# 程式設計手冊)
ms.date: 03/03/2017
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: e043903647075587d1e7eec21c9a7b04f596dbf6
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37937045"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="6c4f2-102">Lambda 運算式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="6c4f2-102">Lambda Expressions (C# Programming Guide)</span></span>

<span data-ttu-id="6c4f2-103">Lambda 運算式是 [匿名函式](anonymous-methods.md) ，可用來建立 [委派](../delegates/using-delegates.md) 或 [運算式樹狀架構](../concepts/expression-trees/index.md) 類型。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-103">A lambda expression is an [anonymous function](anonymous-methods.md) that you can use to create [delegates](../delegates/using-delegates.md) or [expression tree](../concepts/expression-trees/index.md) types.</span></span> <span data-ttu-id="6c4f2-104">使用 Lambda 運算式可以撰寫區域函式，這些函式可以當做引數傳遞，或是當做函式呼叫的值傳回。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-104">By using lambda expressions, you can write local functions that can be passed as arguments or returned as the value of function calls.</span></span> <span data-ttu-id="6c4f2-105">Lambda 運算式對於撰寫 LINQ 查詢運算式而言特別有用。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-105">Lambda expressions are particularly helpful for writing LINQ query expressions.</span></span>
  
<span data-ttu-id="6c4f2-106">若要建立 Lambda 運算式，請在 Lambda 運算子 [=>](../../../csharp/language-reference/operators/lambda-operator.md)的左邊指定輸入參數 (如果有的話)，並將運算式或陳述式區塊放在另一邊。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-106">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator [=>](../../../csharp/language-reference/operators/lambda-operator.md), and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="6c4f2-107">例如，Lambda 運算式 `x => x * x` 會指定名為 `x` 的參數，並傳回 `x` 的平方值。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-107">For example, the lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="6c4f2-108">您可以將這個運算式指派給委派類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-108">You can assign this expression to a delegate type, as the following example shows:</span></span>  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 <span data-ttu-id="6c4f2-109">若要建立運算式樹狀架構類型：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-109">To create an expression tree type:</span></span>  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="6c4f2-110">`=>` 運算子與指派 (`=`) 具有相同的優先順序，而且為[右向關聯](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (請參閱＜運算子＞一文中的的＜關聯性＞一節)。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-110">The `=>` operator has the same precedence as assignment (`=`) and is [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (see "Associativity" section of the Operators article).</span></span>  
  
 <span data-ttu-id="6c4f2-111">在以方法為基礎的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢中，Lambda 會用來做為標準查詢運算子方法的引數，例如 <xref:System.Linq.Enumerable.Where%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-111">Lambdas are used in method-based [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries as arguments to standard query operator methods such as <xref:System.Linq.Enumerable.Where%2A>.</span></span>  
  
 <span data-ttu-id="6c4f2-112">當您使用以方法為基礎的語法呼叫 <xref:System.Linq.Enumerable.Where%2A> 類別中的 <xref:System.Linq.Enumerable> 方法時 (就像是在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]中所執行)，此參數會是委派類型 <xref:System.Func%602?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-112">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Where%2A> method in the <xref:System.Linq.Enumerable> class (as you do in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6c4f2-113">Lambda 運算式是建立委派最方便的方式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-113">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="6c4f2-114">例如，當您在 <xref:System.Linq.Queryable?displayProperty=nameWithType> 類別中呼叫相同方法時 (就像是在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 中所執行)，參數類型就會是 <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\>，其中 Func 是最多擁有十六個輸入參數的任一個 Func 委派。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-114">When you call the same method in, for example, the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) then the parameter type is an <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\> where Func is any of the Func delegates with up to sixteen input parameters.</span></span> <span data-ttu-id="6c4f2-115">再次強調，Lambda 運算式就是建構該運算式樹狀架構非常簡潔的方式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-115">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="6c4f2-116">Lambda 會讓 `Where` 呼叫看起來很相似，但是實際上從 Lambda 建立的物件類型並不相同。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-116">The lambdas allow the `Where` calls to look similar although in fact the type of object created from the lambda is different.</span></span>  
  
 <span data-ttu-id="6c4f2-117">在上面的範例中，請注意委派簽章擁有一個 `int`類型的隱含類型輸入參數，而且會傳回 `int`。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-117">In the previous example, notice that the delegate signature has one implicitly-typed input parameter of type `int`, and returns an `int`.</span></span> <span data-ttu-id="6c4f2-118">由於 Lambda 運算式還有一個輸入參數 (`x`) 和可由編譯器隱含轉換為 `int` 類型的傳回值，因此 Lambda 運算式可以轉換為該類型的委派 </span><span class="sxs-lookup"><span data-stu-id="6c4f2-118">The lambda expression can be converted to a delegate of that type because it also has one input parameter (`x`) and a return value that the compiler can implicitly convert to type `int`.</span></span> <span data-ttu-id="6c4f2-119">(類型推斷將於下列各節中詳細討論)。使用輸入參數 5 叫用委派時，它傳回的結果會是 25。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-119">(Type inference is discussed in more detail in the following sections.) When the delegate is invoked by using an input parameter of 5, it returns a result of 25.</span></span>  
  
 <span data-ttu-id="6c4f2-120">Lambda 不可出現在 [is](../../../csharp/language-reference/keywords/is.md) 或 [as](../../../csharp/language-reference/keywords/as.md) 運算子的左邊。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-120">Lambdas are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) or [as](../../../csharp/language-reference/keywords/as.md) operator.</span></span>  
  
 <span data-ttu-id="6c4f2-121">所有適用於匿名方法的限制，也都適用於 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-121">All restrictions that apply to anonymous methods also apply to lambda expressions.</span></span> <span data-ttu-id="6c4f2-122">如需詳細資訊，請參閱[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
## <a name="expression-lambdas"></a><span data-ttu-id="6c4f2-123">運算式 Lambda</span><span class="sxs-lookup"><span data-stu-id="6c4f2-123">Expression Lambdas</span></span>

 <span data-ttu-id="6c4f2-124">在 => 運算子右邊有運算式的 Lambda 運算式稱為「運算式 Lambda」。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-124">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="6c4f2-125">運算式 Lambda 會在[運算式樹狀架構](../concepts/expression-trees/index.md)的建構過程中大量使用。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-125">Expression lambdas are used extensively in the construction of [Expression Trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="6c4f2-126">運算式 Lambda 會傳回運算式的結果，並採用下列基本形式：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>
  
```csharp
(input-parameters) => expression
```

 <span data-ttu-id="6c4f2-127">只有在 Lambda 包含一個輸入參數時，括號才是選擇項，否則括號是必要項。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="6c4f2-128">兩個或多個輸入參數會包含在括號中，並且以逗號分隔：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>  
  
```csharp
(x, y) => x == y
```

 <span data-ttu-id="6c4f2-129">有時候編譯器會很難或是無法推斷輸入類型。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-129">Sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="6c4f2-130">當這種情形發生時，您可以明確指定類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-130">When this occurs, you can specify the types explicitly as shown in the following example:</span></span>  
  
```csharp
(int x, string s) => s.Length > x
```

 <span data-ttu-id="6c4f2-131">以空括號指定零個輸入參數：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-131">Specify zero input parameters with empty parentheses:</span></span>  
  
```csharp
() => SomeMethod()
```

 <span data-ttu-id="6c4f2-132">請注意，在上面的範例中，運算式 Lambda 的主體可以包含方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-132">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="6c4f2-133">不過，如果您要建立在 .NET Framework 外部 (例如在 SQL Server 中) 評估的運算式樹狀架構，則不應在 Lambda 運算式中使用方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-133">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="6c4f2-134">這些方法在 .NET 通用語言執行平台內容之外將不具任何意義。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-134">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>  
  
## <a name="statement-lambdas"></a><span data-ttu-id="6c4f2-135">陳述式 Lambda</span><span class="sxs-lookup"><span data-stu-id="6c4f2-135">Statement Lambdas</span></span>  
 <span data-ttu-id="6c4f2-136">陳述式 Lambda 看起來就像是運算式 Lambda，不同之處在於，陳述式會包含於大括號內：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-136">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>  
  
<span data-ttu-id="6c4f2-137">(input-parameters) => { statement; }</span><span class="sxs-lookup"><span data-stu-id="6c4f2-137">(input-parameters) => { statement; }</span></span>

 <span data-ttu-id="6c4f2-138">陳述式 Lambda 的主體可以包含任意數目的陳述式，但是實際上通常不會超過兩個或三個陳述式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>  
  
[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]

 <span data-ttu-id="6c4f2-139">陳述式 Lambda 就像匿名方法，它不能用來建立運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-139">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="6c4f2-140">非同步 Lambda</span><span class="sxs-lookup"><span data-stu-id="6c4f2-140">Async Lambdas</span></span>  
 <span data-ttu-id="6c4f2-141">您可以使用 [async](../../../csharp/language-reference/keywords/async.md) 和 [await](../../../csharp/language-reference/keywords/await.md) 關鍵字，輕鬆建立結合非同步處理的 Lambda 運算式和陳述式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-141">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../../csharp/language-reference/keywords/async.md) and [await](../../../csharp/language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="6c4f2-142">例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-142">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 <span data-ttu-id="6c4f2-143">您可以使用非同步 Lambda 加入相同的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-143">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="6c4f2-144">若要加入這個處理常式，請將 `async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-144">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 <span data-ttu-id="6c4f2-145">如需如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-145">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="6c4f2-146">具有標準查詢運算子的 Lambda</span><span class="sxs-lookup"><span data-stu-id="6c4f2-146">Lambdas with the Standard Query Operators</span></span>  
 <span data-ttu-id="6c4f2-147">許多標準查詢運算子都有輸入參數，參數的類型為其中一種 <xref:System.Func%602> 系列泛型委派。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-147">Many Standard query operators have an input parameter whose type is one of the <xref:System.Func%602> family of generic delegates.</span></span> <span data-ttu-id="6c4f2-148">這些委派使用類型參數定義輸入參數的數目和類型，以及委派的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-148">These delegates use type parameters to define the number and types of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="6c4f2-149">對於封裝套用至一組來源資料中每個項目的使用者定義運算式而言，`Func` 委派非常實用。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-149">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="6c4f2-150">例如，請考慮下列委派類型：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-150">For example, consider the following delegate type:</span></span>  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 <span data-ttu-id="6c4f2-151">委派可以具現化為 `Func<int,bool> myFunc` ，其中 `int` 是輸入參數，而 `bool` 是傳回值。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-151">The delegate can be instantiated as `Func<int,bool> myFunc` where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="6c4f2-152">傳回值一律在最後一個類型參數中指定。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-152">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="6c4f2-153">`Func<int, string, bool>` 會定義具有兩個輸入參數 `int` 和 `string`且傳回類型為 `bool`的委派。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-153">`Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="6c4f2-154">叫用下列 `Func` 委派時將會傳回 true 或 false，指出輸入參數是否等於 5：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-154">The following `Func` delegate, when it is invoked, will return true or false to indicate whether the input parameter is equal to 5:</span></span>  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 <span data-ttu-id="6c4f2-155">您也可以在引數類型為 `Expression<Func>`時，於例如 System.Linq.Queryable 中定義的標準查詢運算子內提供 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-155">You can also supply a lambda expression when the argument type is an `Expression<Func>`, for example in the standard query operators that are defined in System.Linq.Queryable.</span></span> <span data-ttu-id="6c4f2-156">當您指定 `Expression<Func>` 引數時，Lambda 將會編譯為運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-156">When you specify an `Expression<Func>` argument, the lambda will be compiled to an expression tree.</span></span>  
  
 <span data-ttu-id="6c4f2-157">標準查詢運算子，也就是 <xref:System.Linq.Enumerable.Count%2A> 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-157">A standard query operator, the <xref:System.Linq.Enumerable.Count%2A> method, is shown here:</span></span>  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 <span data-ttu-id="6c4f2-158">編譯器會推斷輸入參數的類型，您也可以明確指定類型。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-158">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="6c4f2-159">這個特殊 Lambda 運算式會計算除以二之後餘數為 1 的整數 (`n`)。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-159">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>  
  
 <span data-ttu-id="6c4f2-160">下列程式碼行產生的序列會包含 `numbers` 陣列中所有位於 9 左邊的元素，因為 9 是序列中第一個不符合條件的數字：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-160">The following line of code produces a sequence that contains all elements in the `numbers` array that are to the left side of the 9 because that's the first number in the sequence that doesn't meet the condition:</span></span>  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 <span data-ttu-id="6c4f2-161">這個範例會示範將多個輸入參數包含在括號內的指定方式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-161">This example shows how to specify multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="6c4f2-162">這個方法會傳回數字陣列中的所有元素，直到遇到數值小於其位置的數字為止。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-162">The method returns all the elements in the numbers array until a number is encountered whose value is less than its position.</span></span> <span data-ttu-id="6c4f2-163">切勿混淆 Lambda 運算子 (`=>`) 與大於或等於運算子 (`>=`)。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-163">Do not confuse the lambda operator (`=>`) with the greater than or equal operator (`>=`).</span></span>  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a><span data-ttu-id="6c4f2-164">Lambda 中的類型推斷</span><span class="sxs-lookup"><span data-stu-id="6c4f2-164">Type Inference in Lambdas</span></span>  
 <span data-ttu-id="6c4f2-165">撰寫 Lambda 時，您通常不需要指定輸入參數的類型，這是因為編譯器可以根據 Lambda 主體、參數的委派類型，以及 C# 語言規格中所述的其他因素來推斷類型。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-165">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter’s delegate type, and other factors as described in the C# Language Specification.</span></span> <span data-ttu-id="6c4f2-166">對於大多數的標準查詢運算子而言，第一項輸入是來源序列中項目的類型。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-166">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="6c4f2-167">因此，如果您要查詢 `IEnumerable<Customer>`，則輸入變數就會推斷為 `Customer` 物件，這表示您可以存取其方法和屬性：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-167">So if you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 <span data-ttu-id="6c4f2-168">以下是 Lambda 的一般規則：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-168">The general rules for lambdas are as follows:</span></span>  
  
-   <span data-ttu-id="6c4f2-169">Lambda 必須包含與委派類型相同數目的參數。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-169">The lambda must contain the same number of parameters as the delegate type.</span></span>  
  
-   <span data-ttu-id="6c4f2-170">Lambda 中的每個輸入參數都必須能夠隱含轉換為其對應的委派參數。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-170">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>  
  
-   <span data-ttu-id="6c4f2-171">Lambda 的傳回值 (如果有的話) 必須能夠隱含轉換為委派的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-171">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>  
  
 <span data-ttu-id="6c4f2-172">請注意，Lambda 運算式本身並沒有類型，因為一般類型系統沒有內建的「Lambda 運算式」概念。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-172">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="6c4f2-173">不過，有時候一般所稱的 Lambda 運算式「類型」會很實用。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-173">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="6c4f2-174">在這類情況下，類型是指委派類型或是 Lambda 運算式轉換成的 <xref:System.Linq.Expressions.Expression> 類型。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-174">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>  
  
## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="6c4f2-175">Lambda 運算式中的變數範圍</span><span class="sxs-lookup"><span data-stu-id="6c4f2-175">Variable Scope in Lambda Expressions</span></span>  
 <span data-ttu-id="6c4f2-176">Lambda 可以參考「外部變數」(請參閱[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md))，這些變數必須包含在定義 Lambda 函式的方法範圍內，或是在包含 Lambda 運算式的類型範圍內。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-176">Lambdas can refer to *outer variables* (see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="6c4f2-177">以這種方式擷取的變數會加以儲存，以便在 Lambda 運算式中使用，即使這些變數可能會超出範圍而遭到記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-177">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="6c4f2-178">外部變數必須確實指派，才能用於 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-178">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="6c4f2-179">下列範例將示範這些規則：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-179">The following example demonstrates these rules:</span></span>  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 <span data-ttu-id="6c4f2-180">下列規則適用於 Lambda 運算式中的變數範圍：</span><span class="sxs-lookup"><span data-stu-id="6c4f2-180">The following rules apply to variable scope in lambda expressions:</span></span>  
  
-   <span data-ttu-id="6c4f2-181">已擷取的變數要等到參考該變數的委派符合記憶體回收的資格時，才會進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-181">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>  
  
-   <span data-ttu-id="6c4f2-182">導入 Lambda 運算式內的變數無法在外部方法中看見。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-182">Variables introduced within a lambda expression are not visible in the outer method.</span></span>  
  
-   <span data-ttu-id="6c4f2-183">Lambda 運算式無法直接從封入方法擷取 `in`、`ref` 或 `out` 參數。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-183">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>  
  
-   <span data-ttu-id="6c4f2-184">Lambda 運算式中的 return 陳述式不會造成封入方法傳回。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-184">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>  
  
-   <span data-ttu-id="6c4f2-185">如果跳躍陳述式的目標不在區塊內，則 Lambda 運算式不可包含 Lambda 函式內的 `goto` 陳述式、 `break` 陳述式或 `continue` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-185">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="6c4f2-186">即使目標位於區塊內，跳躍陳述式出現在 Lambda 函式區塊外部也一樣是錯誤。</span><span class="sxs-lookup"><span data-stu-id="6c4f2-186">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6c4f2-187">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6c4f2-187">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="6c4f2-188">精選書籍章節</span><span class="sxs-lookup"><span data-stu-id="6c4f2-188">Featured Book Chapter</span></span>  
 <span data-ttu-id="6c4f2-189">[C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx) (C# 3.0 Cookbook 第三版：250 個以上 C# 3.0 程式設計人員適用的方案) 中的 [Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) (委派、事件和 Lambda 運算式)</span><span class="sxs-lookup"><span data-stu-id="6c4f2-189">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4f2-190">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c4f2-190">See Also</span></span>  
 [<span data-ttu-id="6c4f2-191">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6c4f2-191">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6c4f2-192">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="6c4f2-192">LINQ (Language-Integrated Query)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="6c4f2-193">匿名方法</span><span class="sxs-lookup"><span data-stu-id="6c4f2-193">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="6c4f2-194">is</span><span class="sxs-lookup"><span data-stu-id="6c4f2-194">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="6c4f2-195">運算式樹狀結構</span><span class="sxs-lookup"><span data-stu-id="6c4f2-195">Expression Trees</span></span>](../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="6c4f2-196">Visual Studio 2008 C# 範例 (請參閱 LINQ 範例查詢檔案和 XQuery 程式)</span><span class="sxs-lookup"><span data-stu-id="6c4f2-196">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)  
 [<span data-ttu-id="6c4f2-197">Recursive lambda expressions (遞迴的 Lambda 運算式)</span><span class="sxs-lookup"><span data-stu-id="6c4f2-197">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
