---
title: 解譯運算式
description: 了解如何撰寫程式碼來查看運算式樹狀架構的結構。
ms.date: 06/20/2016
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: c9d80ca234e298df2f2e7ce48fbf92cb817fc8a7
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925678"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="390db-103">解譯運算式</span><span class="sxs-lookup"><span data-stu-id="390db-103">Interpreting Expressions</span></span>

[<span data-ttu-id="390db-104">上一個主題 -- 執行運算式</span><span class="sxs-lookup"><span data-stu-id="390db-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="390db-105">現在，讓我們撰寫一些程式碼來查看「運算式樹狀架構」的結構。</span><span class="sxs-lookup"><span data-stu-id="390db-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="390db-106">運算式樹狀架構中的每個節點，都會是衍生自 `Expression` 的類別物件。</span><span class="sxs-lookup"><span data-stu-id="390db-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="390db-107">該設計可讓您透過較簡單的遞迴作業，來瀏覽運算式樹狀架構中的所有節點。</span><span class="sxs-lookup"><span data-stu-id="390db-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="390db-108">一般做法是從根節點開始，並判斷該節點所屬類型。</span><span class="sxs-lookup"><span data-stu-id="390db-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="390db-109">如果節點類型具有子系，則以遞迴方式瀏覽子系。</span><span class="sxs-lookup"><span data-stu-id="390db-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="390db-110">在每個子節點，重複根節點所使用的程序︰判斷類型；如果類型具有子系，則瀏覽每個子系。</span><span class="sxs-lookup"><span data-stu-id="390db-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="390db-111">查看沒有子系的運算式</span><span class="sxs-lookup"><span data-stu-id="390db-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="390db-112">首先讓我們瀏覽一個相當簡單之運算式樹狀架構中的每個節點。</span><span class="sxs-lookup"><span data-stu-id="390db-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="390db-113">下列程式碼會建立一個常數運算式，然後查看其屬性：</span><span class="sxs-lookup"><span data-stu-id="390db-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="390db-114">這會列印：</span><span class="sxs-lookup"><span data-stu-id="390db-114">This will print the following:</span></span>

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="390db-115">現在，讓我們撰寫查看此運算式的程式碼，並撰寫好一些相關的重要屬性。</span><span class="sxs-lookup"><span data-stu-id="390db-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="390db-116">該程式碼如下：</span><span class="sxs-lookup"><span data-stu-id="390db-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="390db-117">查看簡單的加法運算式</span><span class="sxs-lookup"><span data-stu-id="390db-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="390db-118">讓我們從本節簡介中的加法範例開始。</span><span class="sxs-lookup"><span data-stu-id="390db-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="390db-119">我不會使用 `var` 宣告此運算式樹狀架構，因為指派的右邊具隱含類型，所以無法執行此作業。</span><span class="sxs-lookup"><span data-stu-id="390db-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="390db-120">若要更深入了解，請閱讀[這篇文章](implicitly-typed-lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="390db-120">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="390db-121">根節點是 `LambdaExpression`。</span><span class="sxs-lookup"><span data-stu-id="390db-121">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="390db-122">若要取得 `=>` 運算子右邊的相關程式碼，您必須找到 `LambdaExpression` 的其中一個子系。</span><span class="sxs-lookup"><span data-stu-id="390db-122">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="390db-123">我們將對本節中的所有運算式執行此作業。</span><span class="sxs-lookup"><span data-stu-id="390db-123">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="390db-124">父節點無法協助我們找到 `LambdaExpression` 的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="390db-124">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="390db-125">為了查看此運算式中的每個節點，我們必須以遞迴方式瀏覽一些節點。</span><span class="sxs-lookup"><span data-stu-id="390db-125">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="390db-126">以下是第一個簡單的實作：</span><span class="sxs-lookup"><span data-stu-id="390db-126">Here's a simple first implementation:</span></span>

```csharp
Expression<Func<int, int, int>> addition = (a, b) => a + b;

Console.WriteLine($"This expression is a {addition.NodeType} expression type");
Console.WriteLine($"The name of the lambda is {((addition.Name == null) ? "<null>" : addition.Name)}");
Console.WriteLine($"The return type is {addition.ReturnType.ToString()}");
Console.WriteLine($"The expression has {addition.Parameters.Count} arguments. They are:");
foreach(var argumentExpression in addition.Parameters)
{
    Console.WriteLine($"\tParameter Type: {argumentExpression.Type.ToString()}, Name: {argumentExpression.Name}");
}

var additionBody = (BinaryExpression)addition.Body;
Console.WriteLine($"The body is a {additionBody.NodeType} expression");
Console.WriteLine($"The left side is a {additionBody.Left.NodeType} expression");
var left = (ParameterExpression)additionBody.Left;
Console.WriteLine($"\tParameter Type: {left.Type.ToString()}, Name: {left.Name}");
Console.WriteLine($"The right side is a {additionBody.Right.NodeType} expression");
var right= (ParameterExpression)additionBody.Right;
Console.WriteLine($"\tParameter Type: {right.Type.ToString()}, Name: {right.Name}");
```

<span data-ttu-id="390db-127">此範例會列印下列輸出：</span><span class="sxs-lookup"><span data-stu-id="390db-127">This sample prints the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 arguments. They are:
        Parameter Type: System.Int32, Name: a
        Parameter Type: System.Int32, Name: b
The body is a/an Add expression
The left side is a Parameter expression
        Parameter Type: System.Int32, Name: a
The right side is a Parameter expression
        Parameter Type: System.Int32, Name: b
```

<span data-ttu-id="390db-128">您會發現上述程式碼範例中有許多重複的地方。</span><span class="sxs-lookup"><span data-stu-id="390db-128">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="390db-129">讓我們加以清除，以建立更具一般用途的運算式節點造訪者。</span><span class="sxs-lookup"><span data-stu-id="390db-129">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="390db-130">這需要撰寫遞迴演算法。</span><span class="sxs-lookup"><span data-stu-id="390db-130">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="390db-131">任何節點都可能是具有子系的類型。</span><span class="sxs-lookup"><span data-stu-id="390db-131">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="390db-132">具有子系的任何節點都需要我們瀏覽這些子系，並判斷該節點的類型。</span><span class="sxs-lookup"><span data-stu-id="390db-132">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="390db-133">以下是利用遞迴來瀏覽加法運算的已清除版本：</span><span class="sxs-lookup"><span data-stu-id="390db-133">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

```csharp
// Base Visitor class:
public abstract class Visitor
{
    private readonly Expression node;

    protected Visitor(Expression node)
    {
        this.node = node;
    }

    public abstract void Visit(string prefix);

    public ExpressionType NodeType => this.node.NodeType;
    public static Visitor CreateFromExpression(Expression node)
    {
        switch(node.NodeType)
        {
            case ExpressionType.Constant:
                return new ConstantVisitor((ConstantExpression)node);
            case ExpressionType.Lambda:
                return new LambdaVisitor((LambdaExpression)node);
            case ExpressionType.Parameter:
                return new ParameterVisitor((ParameterExpression)node);
            case ExpressionType.Add:
                return new BinaryVisitor((BinaryExpression)node);
            default:
                Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
                return default(Visitor);
        }
    }
}

// Lambda Visitor
public class LambdaVisitor : Visitor
{
    private readonly LambdaExpression node;
    public LambdaVisitor(LambdaExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression type");
        Console.WriteLine($"{prefix}The name of the lambda is {((node.Name == null) ? "<null>" : node.Name)}");
        Console.WriteLine($"{prefix}The return type is {node.ReturnType.ToString()}");
        Console.WriteLine($"{prefix}The expression has {node.Parameters.Count} argument(s). They are:");
        // Visit each parameter:
        foreach (var argumentExpression in node.Parameters)
        {
            var argumentVisitor = Visitor.CreateFromExpression(argumentExpression);
            argumentVisitor.Visit(prefix + "\t");
        }
        Console.WriteLine($"{prefix}The expression body is:");
        // Visit the body:
        var bodyVisitor = Visitor.CreateFromExpression(node.Body);
        bodyVisitor.Visit(prefix + "\t");
    }
}

// Binary Expression Visitor:
public class BinaryVisitor : Visitor
{
    private readonly BinaryExpression node;
    public BinaryVisitor(BinaryExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This binary expression is a {NodeType} expression");
        var left = Visitor.CreateFromExpression(node.Left);
        Console.WriteLine($"{prefix}The Left argument is:");
        left.Visit(prefix + "\t");
        var right = Visitor.CreateFromExpression(node.Right);
        Console.WriteLine($"{prefix}The Right argument is:");
        right.Visit(prefix + "\t");
    }
}

// Parameter visitor:
public class ParameterVisitor : Visitor
{
    private readonly ParameterExpression node;
    public ParameterVisitor(ParameterExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}Type: {node.Type.ToString()}, Name: {node.Name}, ByRef: {node.IsByRef}");
    }
}

// Constant visitor:
public class ConstantVisitor : Visitor
{
    private readonly ConstantExpression node;
    public ConstantVisitor(ConstantExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}The type of the constant value is {node.Type}");
        Console.WriteLine($"{prefix}The value of the constant value is {node.Value}");
    }
}
```

<span data-ttu-id="390db-134">此演算法是可瀏覽任意 `LambdaExpression` 的演算法基礎。</span><span class="sxs-lookup"><span data-stu-id="390db-134">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="390db-135">其中有許多漏洞，那就是，我所建立的程式碼只會尋找可能遇到之運算式樹狀架構節點集中非常小的樣本。</span><span class="sxs-lookup"><span data-stu-id="390db-135">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="390db-136">不過，您仍然可以從其產生的結果獲得相當程度的了解</span><span class="sxs-lookup"><span data-stu-id="390db-136">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="390db-137">(`Visitor.CreateFromExpression` 方法中的預設案例會在遇到新的節點類型時，將訊息列印至錯誤主控台。</span><span class="sxs-lookup"><span data-stu-id="390db-137">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="390db-138">這樣一來，您就知道要新增運算式類型)。</span><span class="sxs-lookup"><span data-stu-id="390db-138">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="390db-139">當您在以上所示的加法運算式中執行此造訪者時，您會得到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="390db-139">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="390db-140">現在您已建立更一般的造訪者實作，您可以瀏覽並處理更多不同類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="390db-140">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="390db-141">查看內含多層的加法運算式</span><span class="sxs-lookup"><span data-stu-id="390db-141">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="390db-142">讓我們嘗試更複雜的範例，但仍將節點類型僅限於加法：</span><span class="sxs-lookup"><span data-stu-id="390db-142">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="390db-143">在造訪者演算法中執行此運算之前，請試著考慮輸出的可能結果。</span><span class="sxs-lookup"><span data-stu-id="390db-143">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="390db-144">請記住，`+` 運算子是「二元運算子」︰它必須具有兩個子系，分別代表左右運算元。</span><span class="sxs-lookup"><span data-stu-id="390db-144">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="390db-145">您可以透過幾個可能的方法來建構正確的樹狀：</span><span class="sxs-lookup"><span data-stu-id="390db-145">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="390db-146">如您所見，這可分為兩組可能的解，以強調最可能發生的情況。</span><span class="sxs-lookup"><span data-stu-id="390db-146">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="390db-147">第一組代表「右向關聯」運算式。</span><span class="sxs-lookup"><span data-stu-id="390db-147">The first represents *right associative* expressions.</span></span> <span data-ttu-id="390db-148">第二組代表「左向關聯」運算式。</span><span class="sxs-lookup"><span data-stu-id="390db-148">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="390db-149">這兩種格式的優點在於，可根據任意數目的加法運算式來調整格式。</span><span class="sxs-lookup"><span data-stu-id="390db-149">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span> 

<span data-ttu-id="390db-150">如果您透過造訪者執行此運算式，您會看到下列輸出，確認此簡單的加法運算式為「左向關聯」。</span><span class="sxs-lookup"><span data-stu-id="390db-150">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span> 

<span data-ttu-id="390db-151">為了執行此範例，並查看完整的運算式樹狀架構，我必須對來源運算式樹狀架構進行一項變更。</span><span class="sxs-lookup"><span data-stu-id="390db-151">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="390db-152">當運算式樹狀架構包含所有常數時，所產生的樹狀只會包含常數值 `10`。</span><span class="sxs-lookup"><span data-stu-id="390db-152">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="390db-153">編譯器會執行所有加法，並將運算式縮減為最簡單的形式。</span><span class="sxs-lookup"><span data-stu-id="390db-153">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="390db-154">只要在運算式中新增一個變數，便足以查看原始樹狀：</span><span class="sxs-lookup"><span data-stu-id="390db-154">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="390db-155">建立此總和的造訪者並執行該造訪者，您將會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="390db-155">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This binary expression is a Add expression
                        The Left argument is:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                        The Right argument is:
                                This is an Parameter expression type
                                Type: System.Int32, Name: a, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
        The Right argument is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 4
```

<span data-ttu-id="390db-156">您也可以透過造訪者程式碼執行任何其他範例，並查看它所表示的樹狀。</span><span class="sxs-lookup"><span data-stu-id="390db-156">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="390db-157">以下是上述 `sum3` 運算式的範例 (以及可防止編譯器計算常數的額外參數)：</span><span class="sxs-lookup"><span data-stu-id="390db-157">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="390db-158">以下是造訪者的輸出：</span><span class="sxs-lookup"><span data-stu-id="390db-158">Here's the output from the visitor:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 1
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="390db-159">請注意，輸出時不會包含括號。</span><span class="sxs-lookup"><span data-stu-id="390db-159">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="390db-160">運算式樹狀架構中沒有節點可表示輸入運算式中的括號。</span><span class="sxs-lookup"><span data-stu-id="390db-160">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="390db-161">運算式樹狀架構的結構包含傳達此優先順序的所有必要資訊。</span><span class="sxs-lookup"><span data-stu-id="390db-161">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="390db-162">擴充此範例</span><span class="sxs-lookup"><span data-stu-id="390db-162">Extending from this sample</span></span>

<span data-ttu-id="390db-163">此範例只會處理最基本的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="390db-163">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="390db-164">您在本節中所看到的程式碼，只會處理常數整數和二元 `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="390db-164">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="390db-165">在最後一個範例中，讓我們更新造訪者以處理更複雜的運算式。</span><span class="sxs-lookup"><span data-stu-id="390db-165">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="390db-166">請將它調整成適用於：</span><span class="sxs-lookup"><span data-stu-id="390db-166">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="390db-167">此程式碼代表數學「階乘」函式的一個可能實作。</span><span class="sxs-lookup"><span data-stu-id="390db-167">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="390db-168">我撰寫此程式碼的方式，會強調透過將 Lambda 運算式指派給 Expressions 以建立運算式樹狀架構的兩個限制。</span><span class="sxs-lookup"><span data-stu-id="390db-168">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="390db-169">首先，不允許陳述式 Lambda。</span><span class="sxs-lookup"><span data-stu-id="390db-169">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="390db-170">這表示我無法使用迴圈、區塊、if/else 陳述式，以及 C# 中常見的其他控制結構。</span><span class="sxs-lookup"><span data-stu-id="390db-170">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="390db-171">僅限使用運算式。</span><span class="sxs-lookup"><span data-stu-id="390db-171">I'm limited to using expressions.</span></span> <span data-ttu-id="390db-172">其次，我無法以遞迴方式呼叫相同的運算式。</span><span class="sxs-lookup"><span data-stu-id="390db-172">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="390db-173">如果運算式已是委派，則可以這樣做，但我無法在其運算式樹狀架構形式中呼叫運算式。</span><span class="sxs-lookup"><span data-stu-id="390db-173">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="390db-174">在[建立運算式樹狀架構](expression-trees-building.md)一節中，您將學習如何克服這些限制的技術。</span><span class="sxs-lookup"><span data-stu-id="390db-174">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>

<span data-ttu-id="390db-175">在此運算式中，您將會遇到下列所有類型的節點：</span><span class="sxs-lookup"><span data-stu-id="390db-175">In this expression, you'll encounter nodes of all these types:</span></span>

1. <span data-ttu-id="390db-176">等號 (二元運算式)</span><span class="sxs-lookup"><span data-stu-id="390db-176">Equal (binary expression)</span></span>
2. <span data-ttu-id="390db-177">乘法 (二元運算式)</span><span class="sxs-lookup"><span data-stu-id="390db-177">Multiply (binary expression)</span></span>
3. <span data-ttu-id="390db-178">條件式 (?</span><span class="sxs-lookup"><span data-stu-id="390db-178">Conditional (the ?</span></span> <span data-ttu-id="390db-179">: 運算式)</span><span class="sxs-lookup"><span data-stu-id="390db-179">: expression)</span></span>
4. <span data-ttu-id="390db-180">方法呼叫運算式 (呼叫 `Range()` 和 `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="390db-180">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="390db-181">修改造訪者演算法的其中一個方式，就是繼續執行，並在每次到達 `default` 子句時撰寫節點類型。</span><span class="sxs-lookup"><span data-stu-id="390db-181">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="390db-182">反覆運算幾次之後，您將會看到每個可能的節點。</span><span class="sxs-lookup"><span data-stu-id="390db-182">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="390db-183">此時就具備所有必要項目。</span><span class="sxs-lookup"><span data-stu-id="390db-183">Then, you have all you need.</span></span> <span data-ttu-id="390db-184">結果看起來類似如下：</span><span class="sxs-lookup"><span data-stu-id="390db-184">The result would be something like this:</span></span>

```csharp
public static Visitor CreateFromExpression(Expression node)
{
    switch(node.NodeType)
    {
        case ExpressionType.Constant:
            return new ConstantVisitor((ConstantExpression)node);
        case ExpressionType.Lambda:
            return new LambdaVisitor((LambdaExpression)node);
        case ExpressionType.Parameter:
            return new ParameterVisitor((ParameterExpression)node);
        case ExpressionType.Add:
        case ExpressionType.Equal:
        case ExpressionType.Multiply:
            return new BinaryVisitor((BinaryExpression)node);
        case ExpressionType.Conditional:
            return new ConditionalVisitor((ConditionalExpression)node);
        case ExpressionType.Call:
            return new MethodCallVisitor((MethodCallExpression)node);
        default:
            Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
            return default(Visitor);
    }
}
```

<span data-ttu-id="390db-185">ConditionalVisitor 和 MethodCallVisitor 會處理下列兩個節點：</span><span class="sxs-lookup"><span data-stu-id="390db-185">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

```csharp
public class ConditionalVisitor : Visitor
{
    private readonly ConditionalExpression node;
    public ConditionalVisitor(ConditionalExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        var testVisitor = Visitor.CreateFromExpression(node.Test);
        Console.WriteLine($"{prefix}The Test for this expression is:");
        testVisitor.Visit(prefix + "\t");
        var trueVisitor = Visitor.CreateFromExpression(node.IfTrue);
        Console.WriteLine($"{prefix}The True clause for this expression is:");
        trueVisitor.Visit(prefix + "\t");
        var falseVisitor = Visitor.CreateFromExpression(node.IfFalse);
        Console.WriteLine($"{prefix}The False clause for this expression is:");
        falseVisitor.Visit(prefix + "\t");
    }
}

public class MethodCallVisitor : Visitor
{
    private readonly MethodCallExpression node;
    public MethodCallVisitor(MethodCallExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        if (node.Object == null)
            Console.WriteLine($"{prefix}This is a static method call");
        else
        {
            Console.WriteLine($"{prefix}The receiver (this) is:");
            var receiverVisitor = Visitor.CreateFromExpression(node.Object);
            receiverVisitor.Visit(prefix + "\t");
        }

        var methodInfo = node.Method;
        Console.WriteLine($"{prefix}The method name is {methodInfo.DeclaringType}.{methodInfo.Name}");
        // There is more here, like generic arguments, and so on.
        Console.WriteLine($"{prefix}The Arguments are:");
        foreach(var arg in node.Arguments)
        {
            var argVisitor = Visitor.CreateFromExpression(arg);
            argVisitor.Visit(prefix + "\t");
        }
    }
}
```

<span data-ttu-id="390db-186">而且運算式樹狀架構的輸出會是：</span><span class="sxs-lookup"><span data-stu-id="390db-186">And the output for the expression tree would be:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: n, ByRef: False
The expression body is:
        This expression is a Conditional expression
        The Test for this expression is:
                This binary expression is a Equal expression
                The Left argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: n, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 0
        The True clause for this expression is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 1
        The False clause for this expression is:
                This expression is a Call expression
                This is a static method call
                The method name is System.Linq.Enumerable.Aggregate
                The Arguments are:
                        This expression is a Call expression
                        This is a static method call
                        The method name is System.Linq.Enumerable.Range
                        The Arguments are:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                                This is an Parameter expression type
                                Type: System.Int32, Name: n, ByRef: False
                        This expression is a Lambda expression type
                        The name of the lambda is <null>
                        The return type is System.Int32
                        The expression has 2 arguments. They are:
                                This is an Parameter expression type
                                Type: System.Int32, Name: product, ByRef: False
                                This is an Parameter expression type
                                Type: System.Int32, Name: factor, ByRef: False
                        The expression body is:
                                This binary expression is a Multiply expression
                                The Left argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: product, ByRef: False
                                The Right argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: factor, ByRef: False
```

## <a name="extending-the-sample-library"></a><span data-ttu-id="390db-187">擴充範例程式庫</span><span class="sxs-lookup"><span data-stu-id="390db-187">Extending the Sample Library</span></span>

<span data-ttu-id="390db-188">本節中的範例示範用以瀏覽及查看運算式樹狀架構中所有節點的核心技術。</span><span class="sxs-lookup"><span data-stu-id="390db-188">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="390db-189">我隱藏了您可能需要的許多動作，以便專注於瀏覽及存取運算式樹狀架構中所有節點的核心工作。</span><span class="sxs-lookup"><span data-stu-id="390db-189">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span> 

<span data-ttu-id="390db-190">首先，造訪者只會處理整數常數。</span><span class="sxs-lookup"><span data-stu-id="390db-190">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="390db-191">這些常數值可以屬於任何其他數值類型，而且 C# 語言支援在這些類型之間進行轉換和提升。</span><span class="sxs-lookup"><span data-stu-id="390db-191">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="390db-192">此程式碼的更強固版本會反映所有這些功能。</span><span class="sxs-lookup"><span data-stu-id="390db-192">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="390db-193">即使最後一個範例也會識別可能的節點類型子集。</span><span class="sxs-lookup"><span data-stu-id="390db-193">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="390db-194">您仍可將許多會造成失敗的運算式提供給它。</span><span class="sxs-lookup"><span data-stu-id="390db-194">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="390db-195">完整的實作包含在 .NET Standard 的名稱 <xref:System.Linq.Expressions.ExpressionVisitor> 之下，並可處理所有可能的節點類型。</span><span class="sxs-lookup"><span data-stu-id="390db-195">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="390db-196">最後，我在本文中使用的程式庫是為了示範和學習所建立。</span><span class="sxs-lookup"><span data-stu-id="390db-196">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="390db-197">它不會經過最佳化。</span><span class="sxs-lookup"><span data-stu-id="390db-197">It's not optimized.</span></span> <span data-ttu-id="390db-198">我的撰寫目的是為了讓所使用的結構相當清楚，並強調用來瀏覽節點和分析其內容的技術。</span><span class="sxs-lookup"><span data-stu-id="390db-198">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="390db-199">生產環境的實作會比我更注重效能。</span><span class="sxs-lookup"><span data-stu-id="390db-199">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="390db-200">即使有這些限制，您也應該可以適當地撰寫容易閱讀和了解運算式樹狀架構的演算法。</span><span class="sxs-lookup"><span data-stu-id="390db-200">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="390db-201">下一個主題 -- 建立運算式</span><span class="sxs-lookup"><span data-stu-id="390db-201">Next -- Building Expressions</span></span>](expression-trees-building.md)
