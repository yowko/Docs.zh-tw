---
title: "解譯運算式"
description: "解譯運算式"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 07352a2807c08ad19b8d5a47c5a42a0e1c455ab6
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---

# <a name="interpreting-expressions"></a>解譯運算式

[上一個主題 -- 執行運算式](expression-trees-execution.md)

現在，讓我們撰寫一些程式碼來查看「運算式樹狀架構」**的結構。 運算式樹狀架構中的每個節點，都會是衍生自 `Expression` 的類別物件。

該設計可讓您透過較簡單的遞迴作業，來瀏覽運算式樹狀架構中的所有節點。 一般做法是從根節點開始，並判斷該節點所屬類型。

如果節點類型具有子系，則以遞迴方式瀏覽子系。 在每個子節點，重複根節點所使用的程序︰判斷類型；如果類型具有子系，則瀏覽每個子系。

## <a name="examining-an-expression-with-no-children"></a>查看沒有子系的運算式
首先讓我們瀏覽一個相當簡單之運算式樹狀架構中的每個節點。
下列程式碼會建立一個常數運算式，然後查看其屬性：

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

這會列印：

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

現在，讓我們撰寫查看此運算式的程式碼，並撰寫好一些相關的重要屬性。 該程式碼如下：

## <a name="examining-a-simple-addition-expression"></a>查看簡單的加法運算式

讓我們從本節簡介中的加法範例開始。

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> 我不會使用 `var` 宣告此運算式樹狀架構，因為指派的右邊具隱含類型，所以無法執行此作業。 若要更深入了解，請閱讀[這篇文章](implicitly-typed-lambda-expressions.md)。

根節點是 `LambdaExpression`。 若要取得 `=>` 運算子右邊的相關程式碼，您必須找到 `LambdaExpression` 的其中一個子系。 我們將對本節中的所有運算式執行此作業。 父節點無法協助我們找到 `LambdaExpression` 的傳回型別。

為了查看此運算式中的每個節點，我們必須以遞迴方式瀏覽一些節點。 以下是第一個簡單的實作：

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

此範例會列印下列輸出：

```
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

您會發現上述程式碼範例中有許多重複的地方。
讓我們加以清除，以建立更具一般用途的運算式節點造訪者。 這需要撰寫遞迴演算法。 任何節點都可能是具有子系的類型。
具有子系的任何節點都需要我們瀏覽這些子系，並判斷該節點的類型。 以下是利用遞迴來瀏覽加法運算的已清除版本：

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

此演算法是可瀏覽任意 `LambdaExpression` 的演算法基礎。 其中有許多漏洞，那就是，我所建立的程式碼只會尋找可能遇到之運算式樹狀架構節點集中非常小的樣本。 不過，您仍然可以從其產生的結果獲得相當程度的了解 (`Visitor.CreateFromExpression` 方法中的預設案例會在遇到新的節點類型時，將訊息列印至錯誤主控台。 這樣一來，您就知道要新增運算式類型)。

當您在以上所示的加法運算式中執行此造訪者時，您會得到下列輸出：

```
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

現在您已建立更一般的造訪者實作，您可以瀏覽並處理更多不同類型的運算式。

## <a name="examining-an-addition-expression-with-many-levels"></a>查看內含多層的加法運算式

讓我們嘗試更複雜的範例，但仍將節點類型僅限於加法：

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

在造訪者演算法中執行此運算之前，請試著考慮輸出的可能結果。 請記住，`+` 運算子是「二元運算子」**︰它必須具有兩個子系，分別代表左右運算元。 您可以透過幾個可能的方法來建構正確的樹狀：

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

如您所見，這可分為兩組可能的解，以強調最可能發生的情況。 第一組代表「右向關聯」**運算式。 第二組代表「左向關聯」**運算式。
這兩種格式的優點在於，可根據任意數目的加法運算式來調整格式。 

如果您透過造訪者執行此運算式，您會看到下列輸出，確認此簡單的加法運算式為「左向關聯」**。 

為了執行此範例，並查看完整的運算式樹狀架構，我必須對來源運算式樹狀架構進行一項變更。 當運算式樹狀架構包含所有常數時，所產生的樹狀只會包含常數值 `10`。 編譯器會執行所有加法，並將運算式縮減為最簡單的形式。 只要在運算式中新增一個變數，便足以查看原始樹狀：

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

建立此總和的造訪者並執行該造訪者，您將會看到下列輸出：

```
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

您也可以透過造訪者程式碼執行任何其他範例，並查看它所表示的樹狀。 以下是上述 `sum3` 運算式的範例 (以及可防止編譯器計算常數的額外參數)：

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

以下是造訪者的輸出：

```
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

請注意，輸出時不會包含括號。 運算式樹狀架構中沒有節點可表示輸入運算式中的括號。 運算式樹狀架構的結構包含傳達此優先順序的所有必要資訊。

## <a name="extending-from-this-sample"></a>擴充此範例

此範例只會處理最基本的運算式樹狀架構。 您在本節中所看到的程式碼，只會處理常數整數和二元 `+` 運算子。 在最後一個範例中，讓我們更新造訪者以處理更複雜的運算式。 請將它調整成適用於：

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

此程式碼代表數學「階乘」**函式的一個可能實作。 我撰寫此程式碼的方式強調將 Lambda 運算式指派給 Expressions 以建立運算式樹狀架構，會有兩項限制。 首先，不允許陳述式 Lambda。 這表示我無法使用迴圈、區塊、if/else 陳述式，以及 C# 中常見的其他控制結構。 僅限使用運算式。 其次，我無法以遞迴方式呼叫相同的運算式。
如果運算式已是委派，則可以這樣做，但我無法在其運算式樹狀架構形式中呼叫運算式。 在[建立運算式樹狀架構](expression-trees-building.md)一節中，您將學習如何克服這些限制的技術。


在此運算式中，您將會遇到下列所有類型的節點：
1. 等號 (二元運算式)
2. 乘法 (二元運算式)
3. 條件式 (? : 運算式)
4. 方法呼叫運算式 (呼叫 `Range()` 和 `Aggregate()`)

修改造訪者演算法的其中一個方式，就是繼續執行，並在每次到達 `default` 子句時撰寫節點類型。 反覆運算幾次之後，您將會看到每個可能的節點。 此時就具備所有必要項目。 結果看起來類似如下：

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

ConditionalVisitor 和 MethodCallVisitor 會處理下列兩個節點：

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

而且運算式樹狀架構的輸出會是：

```
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

## <a name="extending-the-sample-library"></a>擴充範例程式庫

本節中的範例示範用以瀏覽及查看運算式樹狀架構中所有節點的核心技術。 我隱藏了您可能需要的許多動作，以便專注於瀏覽及存取運算式樹狀架構中所有節點的核心工作。 

首先，造訪者只會處理整數常數。 這些常數值可以屬於任何其他數值類型，而且 C# 語言支援在這些類型之間進行轉換和提升。 此程式碼的更強固版本會反映所有這些功能。

即使最後一個範例也會識別可能的節點類型子集。
您仍可將許多會造成失敗的運算式提供給它。
完整的實作包含在 .NET 標準程式庫中的名稱 [ExpressionVisitor](https://docs.microsoft.com/dotnet/core/api/System.Linq.Expressions.ExpressionVisitor) 之下，並可處理所有可能的節點類型。

最後，我在本文中使用的程式庫是為了示範和學習所建立。 它不會經過最佳化。 我的撰寫目的是為了讓所使用的結構相當清楚，並強調用來瀏覽節點和分析其內容的技術。 生產環境的實作會比我更注重效能。

即使有這些限制，您也應該可以適當地撰寫容易閱讀和了解運算式樹狀架構的演算法。

[下一個主題 -- 建立運算式](expression-trees-building.md)

