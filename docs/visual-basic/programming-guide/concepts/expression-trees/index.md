---
title: 運算式樹狀架構 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: c1e576439956a735962978d37430949ed6bc39d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832487"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="321b9-102">運算式樹狀架構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="321b9-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="321b9-103">運算式樹狀架構代表類似樹狀目錄之資料結構中的程式碼，其中，每個節點都是一個運算式，例如，方法呼叫或二進位運算 (如 `x < y`)。</span><span class="sxs-lookup"><span data-stu-id="321b9-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="321b9-104">您可以編譯和執行運算式樹狀架構所代表的程式碼。</span><span class="sxs-lookup"><span data-stu-id="321b9-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="321b9-105">這會啟用動態修改可執行程式碼、在各種資料庫中執行 LINQ 查詢，以及建立動態查詢。</span><span class="sxs-lookup"><span data-stu-id="321b9-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="321b9-106">如需 LINQ 中運算式樹狀架構的詳細資訊，請參閱[如何：使用運算式樹狀架構建置動態查詢 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="321b9-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="321b9-107">運算式樹狀架構也用於動態語言執行階段中，以提供動態語言與 .NET Framework 之間的互通性，並讓編譯器寫入器發出運算式樹狀架構，而不是 Microsoft Intermediate Language (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="321b9-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="321b9-108">如需 DLR 的詳細資訊，請參閱 [Dynamic Language Runtime 概觀](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="321b9-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="321b9-109">您可以根據匿名 Lambda 運算式讓 C# 或 Visual Basic 編譯器建立運算式樹狀架構，也可以使用 <xref:System.Linq.Expressions> 命名空間以手動建立運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="321b9-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="321b9-110">從 Lambda 運算式建立運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="321b9-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="321b9-111">將 Lambda 運算式指派給類型為 <xref:System.Linq.Expressions.Expression%601> 的變數時，編譯器會發出程式碼，以建置代表 Lambda 運算式的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="321b9-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="321b9-112">Visual Basic 編譯器只能從運算式 Lambda (或單行 Lambda) 產生運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="321b9-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="321b9-113">它無法剖析陳述式 Lambda (或多行 Lambda)。</span><span class="sxs-lookup"><span data-stu-id="321b9-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="321b9-114">如需 Visual Basic 中之 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="321b9-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="321b9-115">下列程式碼範例示範如何讓 Visual Basic 編譯器建立代表 Lambda 運算式 `Function(num) num < 5` 的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="321b9-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="321b9-116">使用 API 建立運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="321b9-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="321b9-117">若要使用 API 建立運算式樹狀架構，請使用 <xref:System.Linq.Expressions.Expression> 類別。</span><span class="sxs-lookup"><span data-stu-id="321b9-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="321b9-118">這個類別包含可建立之特定類型運算式樹狀架構節點的靜態 factory 方法，例如，<xref:System.Linq.Expressions.ParameterExpression> (代表變數或參數) 或 <xref:System.Linq.Expressions.MethodCallExpression> (代表方法呼叫)。</span><span class="sxs-lookup"><span data-stu-id="321b9-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="321b9-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> 和其他運算式特定類型也定義在 <xref:System.Linq.Expressions> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="321b9-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="321b9-120">這些類型衍生自抽象類型 <xref:System.Linq.Expressions.Expression>。</span><span class="sxs-lookup"><span data-stu-id="321b9-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="321b9-121">下列程式碼範例示範如何使用 API 建立代表 Lambda 運算式 `Function(num) num < 5` 的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="321b9-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 <span data-ttu-id="321b9-122">在.NET Framework 4 或更新版中，運算式樹狀架構 API 也可用於指派及控制流程運算式，例如迴圈、條件式區塊及 `try-catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="321b9-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="321b9-123">使用 API 建立的運算式樹狀架構，可以比使用 Visual Basic 編譯器從 Lambda 運算式建立的運算式樹狀架構更加複雜。</span><span class="sxs-lookup"><span data-stu-id="321b9-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="321b9-124">下列範例示範如何建立可計算數字階乘的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="321b9-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.   
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

<span data-ttu-id="321b9-125">如需詳細資訊，請參閱[在 Visual Studio 2010 中使用運算式樹狀架構產生動態方法 (英文)](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/)，這也適用於更新版本的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="321b9-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="321b9-126">剖析運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="321b9-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="321b9-127">下列程式碼範例示範如何將代表 Lambda 運算式 `Function(num) num < 5` 的運算式樹狀架構分解成各部組件。</span><span class="sxs-lookup"><span data-stu-id="321b9-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="321b9-128">運算式樹狀架構的不變性</span><span class="sxs-lookup"><span data-stu-id="321b9-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="321b9-129">運算式樹狀架構應該是不變的。</span><span class="sxs-lookup"><span data-stu-id="321b9-129">Expression trees should be immutable.</span></span> <span data-ttu-id="321b9-130">這表示，如果您要修改運算式樹狀架構，則必須複製現有運算式樹狀架構，並取代其中的節點，以建構新的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="321b9-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="321b9-131">您可以使用運算式樹狀架構訪問項來周遊現有運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="321b9-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="321b9-132">如需詳細資訊，請參閱[如何：修改運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="321b9-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="321b9-133">編譯運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="321b9-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="321b9-134"><xref:System.Linq.Expressions.Expression%601> 類型提供 <xref:System.Linq.Expressions.Expression%601.Compile%2A> 方法，以將運算式樹狀架構所代表的程式碼編譯為可執行委派。</span><span class="sxs-lookup"><span data-stu-id="321b9-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="321b9-135">下列程式碼範例示範如何編譯運算式樹狀架構，並執行產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="321b9-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 <span data-ttu-id="321b9-136">如需詳細資訊，請參閱[如何：執行運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="321b9-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321b9-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="321b9-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="321b9-138">如何：執行運算式樹狀架構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="321b9-138">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="321b9-139">如何：修改運算式樹狀架構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="321b9-139">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="321b9-140">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="321b9-140">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="321b9-141">Dynamic Language Runtime 概觀</span><span class="sxs-lookup"><span data-stu-id="321b9-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="321b9-142">程式設計概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="321b9-142">Programming Concepts (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
