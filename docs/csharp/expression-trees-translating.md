---
title: 轉譯運算式樹狀架構
description: 了解如何瀏覽運算式樹狀架構中的每個節點，同時建立修改後的運算式樹狀架構複本。
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: bd4aec2ef34e4dc972ae867c6b5070f92dcbc498
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45678942"
---
# <a name="translating-expression-trees"></a><span data-ttu-id="4c428-103">轉譯運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="4c428-103">Translating Expression Trees</span></span>

[<span data-ttu-id="4c428-104">上一個主題 -- 建立運算式</span><span class="sxs-lookup"><span data-stu-id="4c428-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="4c428-105">在最後一節中，您將了解如何瀏覽運算式樹狀架構中的每個節點，同時建立修改後的運算式樹狀架構複本。</span><span class="sxs-lookup"><span data-stu-id="4c428-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="4c428-106">您將在下列兩種重要情況下使用這些技術。</span><span class="sxs-lookup"><span data-stu-id="4c428-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="4c428-107">第一種情況是為了解運算式樹狀架構所表示的演算法，以便可將該演算法轉譯至其他環境。</span><span class="sxs-lookup"><span data-stu-id="4c428-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="4c428-108">第二種情況發生於您想要變更已建立的演算法時。</span><span class="sxs-lookup"><span data-stu-id="4c428-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="4c428-109">這樣做可能是為了新增記錄、攔截及追蹤方法呼叫，或基於其他目的。</span><span class="sxs-lookup"><span data-stu-id="4c428-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="4c428-110">轉譯就是瀏覽</span><span class="sxs-lookup"><span data-stu-id="4c428-110">Translating is Visiting</span></span>

<span data-ttu-id="4c428-111">您為了轉譯運算式樹狀架構所建立的程式碼，就是您已看到可瀏覽樹狀中所有節點的運算式。</span><span class="sxs-lookup"><span data-stu-id="4c428-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="4c428-112">當您轉譯運算式樹狀架構時，您會瀏覽所有節點，並在瀏覽時建立新的樹狀。</span><span class="sxs-lookup"><span data-stu-id="4c428-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="4c428-113">新的樹狀可能包含原始節點的參考，或是您已置於樹狀之新節點的參考。</span><span class="sxs-lookup"><span data-stu-id="4c428-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="4c428-114">讓我們來看實際執行情況，首先瀏覽運算式樹狀架構，然後取代一些節點來建立新的樹狀。</span><span class="sxs-lookup"><span data-stu-id="4c428-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="4c428-115">在此範例中，讓我們將任何常數取代為十倍大的常數。</span><span class="sxs-lookup"><span data-stu-id="4c428-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="4c428-116">運算式樹狀架構的其他方面則保持不變。</span><span class="sxs-lookup"><span data-stu-id="4c428-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="4c428-117">我們不會讀取常數值並取代為新常數，而是將常數值取代為執行乘法運算的新節點，來進行這項取代。</span><span class="sxs-lookup"><span data-stu-id="4c428-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="4c428-118">在這裡，找到常數節點之後，請建立新的乘法節點，其子系為原始常數和常數 `10`：</span><span class="sxs-lookup"><span data-stu-id="4c428-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

<span data-ttu-id="4c428-119">以替代節點取代原始節點之後，即會形成內含修改的新樹狀。</span><span class="sxs-lookup"><span data-stu-id="4c428-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="4c428-120">我們可藉由編譯和執行已被取代的樹狀來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="4c428-120">We can verify that by compiling and executing the replaced tree.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

<span data-ttu-id="4c428-121">建立新的樹狀結合了瀏覽現有樹狀中的所有節點，以及建立新的節點並將其插入樹狀。</span><span class="sxs-lookup"><span data-stu-id="4c428-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="4c428-122">此範例示範運算式樹狀架構不可變的重要性。</span><span class="sxs-lookup"><span data-stu-id="4c428-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="4c428-123">請注意，以上建立的新樹狀包含新建立的節點及來自現有樹狀的節點之組合。</span><span class="sxs-lookup"><span data-stu-id="4c428-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="4c428-124">因為無法修改現有樹狀中的節點，所以很安全。</span><span class="sxs-lookup"><span data-stu-id="4c428-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="4c428-125">這會大幅提升記憶體的效率。</span><span class="sxs-lookup"><span data-stu-id="4c428-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="4c428-126">您可以在整個樹狀中，或在多個運算式樹狀架構中使用相同的節點。</span><span class="sxs-lookup"><span data-stu-id="4c428-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="4c428-127">由於無法修改節點，因此可在需要時重複使用相同的節點。</span><span class="sxs-lookup"><span data-stu-id="4c428-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="4c428-128">周遊和執行加法</span><span class="sxs-lookup"><span data-stu-id="4c428-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="4c428-129">讓我們來進行驗證，請建立第二個造訪者來查核加法節點的樹狀並計算結果。</span><span class="sxs-lookup"><span data-stu-id="4c428-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="4c428-130">您可以為到目前為止所看到的造訪者進行兩項修改，來執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="4c428-130">You can do this by making a couple modifications to the vistor that you've seen so far.</span></span> <span data-ttu-id="4c428-131">在此新版本中，造訪者會傳回加法運算到目前為止的部分總和。</span><span class="sxs-lookup"><span data-stu-id="4c428-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="4c428-132">對於常數運算式，這會是常數運算式的值。</span><span class="sxs-lookup"><span data-stu-id="4c428-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="4c428-133">對於加法運算式，結果會是在周遊這些樹狀之後的左右運算元總和。</span><span class="sxs-lookup"><span data-stu-id="4c428-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it 
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

<span data-ttu-id="4c428-134">這裡的程式碼很多，但概念很容易了解。</span><span class="sxs-lookup"><span data-stu-id="4c428-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="4c428-135">此程式碼會瀏覽第一次深度搜尋的子系。</span><span class="sxs-lookup"><span data-stu-id="4c428-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="4c428-136">當它遇到常數節點時，造訪者會傳回常數值。</span><span class="sxs-lookup"><span data-stu-id="4c428-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="4c428-137">造訪者瀏覽兩個子系之後，這些子系就會計算針對該樹狀子目錄計算得來的總和。</span><span class="sxs-lookup"><span data-stu-id="4c428-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="4c428-138">加法節點現在可以計算其總和。</span><span class="sxs-lookup"><span data-stu-id="4c428-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="4c428-139">瀏覽運算式樹狀架構中的所有節點之後，就會計算總和。</span><span class="sxs-lookup"><span data-stu-id="4c428-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="4c428-140">您可以執行偵錯工具中的樣本並追蹤執行情況，來追蹤執行情況。</span><span class="sxs-lookup"><span data-stu-id="4c428-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="4c428-141">藉由周遊此樹狀，可讓我們更輕鬆地追蹤節點的分析方式，以及總和的計算方式。</span><span class="sxs-lookup"><span data-stu-id="4c428-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by travsersing the tree.</span></span> <span data-ttu-id="4c428-142">以下是彙總方法的更新版本，其中包含相當多的追蹤資訊：</span><span class="sxs-lookup"><span data-stu-id="4c428-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

<span data-ttu-id="4c428-143">在同一個運算式中執行此方法會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="4c428-143">Running it on the same expression yields the following output:</span></span>

```
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

<span data-ttu-id="4c428-144">追蹤輸出並依照上述程式碼進行。</span><span class="sxs-lookup"><span data-stu-id="4c428-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="4c428-145">您應該能夠了解程式碼如何在周遊樹狀時瀏覽每個節點並計算總和，然後求得總和。</span><span class="sxs-lookup"><span data-stu-id="4c428-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="4c428-146">現在，讓我們來看一個不同的執行，其運算式是由 `sum1` 提供：</span><span class="sxs-lookup"><span data-stu-id="4c428-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="4c428-147">以下是查看此運算式後的輸出：</span><span class="sxs-lookup"><span data-stu-id="4c428-147">Here's the output from examining this expression:</span></span>

```
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

<span data-ttu-id="4c428-148">雖然最後的解都相同，但樹狀周遊則完全不同。</span><span class="sxs-lookup"><span data-stu-id="4c428-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="4c428-149">這些節點會依不同順序周遊，因為樹狀建構後所出現的第一個作業不同。</span><span class="sxs-lookup"><span data-stu-id="4c428-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="4c428-150">了解詳細資訊</span><span class="sxs-lookup"><span data-stu-id="4c428-150">Learning More</span></span>

<span data-ttu-id="4c428-151">此範例顯示您所建立的一小部分程式碼，該程式碼會用來周遊及解譯由運算式樹狀架構表示的演算法。</span><span class="sxs-lookup"><span data-stu-id="4c428-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="4c428-152">如需建立一般用途程式庫，以將運算式樹狀架構轉譯為其他語言之所有必要工作的完整討論，請閱讀 Matt Warren 所撰寫的[這一系列](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4c428-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="4c428-153">該系列進一步詳細說明如何將您可能在運算式樹狀架構中找到的任何程式碼進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="4c428-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="4c428-154">希望您現在已了解運算式樹狀架構的真正強大之處。</span><span class="sxs-lookup"><span data-stu-id="4c428-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="4c428-155">您可以查看一組程式碼、對該程式碼進行任何想要的變更，然後執行變更後的版本。</span><span class="sxs-lookup"><span data-stu-id="4c428-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="4c428-156">因為運算式樹狀架構為不可變，所以您可以使用現有樹狀的元件來建立新的樹狀。</span><span class="sxs-lookup"><span data-stu-id="4c428-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="4c428-157">如此即可降低建立修改後的運算式樹狀架構所需的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="4c428-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="4c428-158">下一個主題 -- 總結</span><span class="sxs-lookup"><span data-stu-id="4c428-158">Next -- Summing up</span></span>](expression-trees-summary.md)
