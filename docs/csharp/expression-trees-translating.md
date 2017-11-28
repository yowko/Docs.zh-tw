---
title: "轉譯運算式樹狀架構"
description: "了解如何瀏覽運算式樹狀架構中的每個節點，同時建立修改後的運算式樹狀架構複本。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 602a17591d27ebfd098516453b9028bca37ad5e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="translating-expression-trees"></a>轉譯運算式樹狀架構

[上一個主題 -- 建立運算式](expression-trees-building.md)

在最後一節中，您將了解如何瀏覽運算式樹狀架構中的每個節點，同時建立修改後的運算式樹狀架構複本。 您將在下列兩種重要情況下使用這些技術。 第一種情況是為了解運算式樹狀架構所表示的演算法，以便可將該演算法轉譯至其他環境。 第二種情況發生於您想要變更已建立的演算法時。 這樣做可能是為了新增記錄、攔截及追蹤方法呼叫，或基於其他目的。

## <a name="translating-is-visiting"></a>轉譯就是瀏覽

您為了轉譯運算式樹狀架構所建立的程式碼，就是您已看到可瀏覽樹狀中所有節點的運算式。 當您轉譯運算式樹狀架構時，您會瀏覽所有節點，並在瀏覽時建立新的樹狀。 新的樹狀可能包含原始節點的參考，或是您已置於樹狀之新節點的參考。

讓我們來看實際執行情況，首先瀏覽運算式樹狀架構，然後取代一些節點來建立新的樹狀。 在此範例中，讓我們將任何常數取代為十倍大的常數。
運算式樹狀架構的其他方面則保持不變。 我們不會讀取常數值並取代為新常數，而是將常數值取代為執行乘法運算的新節點，來進行這項取代。

在這裡，找到常數節點之後，請建立新的乘法節點，其子系為原始常數和常數 `10`：

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

以替代節點取代原始節點之後，即會形成內含修改的新樹狀。 我們可藉由編譯和執行已被取代的樹狀來進行驗證。

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

建立新的樹狀結合了瀏覽現有樹狀中的所有節點，以及建立新的節點並將其插入樹狀。

此範例示範運算式樹狀架構不可變的重要性。 請注意，以上建立的新樹狀包含新建立的節點及來自現有樹狀的節點之組合。 因為無法修改現有樹狀中的節點，所以很安全。 這會大幅提升記憶體的效率。
您可以在整個樹狀中，或在多個運算式樹狀架構中使用相同的節點。 由於無法修改節點，因此可在需要時重複使用相同的節點。

## <a name="traversing-and-executing-an-addition"></a>周遊和執行加法

讓我們來進行驗證，請建立第二個造訪者來查核加法節點的樹狀並計算結果。 您可以為到目前為止所看到的造訪者進行兩項修改，來執行這項作業。 在此新版本中，造訪者會傳回加法運算到目前為止的部分總和。 對於常數運算式，這會是常數運算式的值。 對於加法運算式，結果會是在周遊這些樹狀之後的左右運算元總和。

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

這裡的程式碼很多，但概念很容易了解。
此程式碼會瀏覽第一次深度搜尋的子系。 當它遇到常數節點時，造訪者會傳回常數值。 造訪者瀏覽兩個子系之後，這些子系就會計算針對該樹狀子目錄計算得來的總和。 加法節點現在可以計算其總和。
瀏覽運算式樹狀架構中的所有節點之後，就會計算總和。 您可以執行偵錯工具中的樣本並追蹤執行情況，來追蹤執行情況。

藉由周遊此樹狀，可讓我們更輕鬆地追蹤節點的分析方式，以及總和的計算方式。 以下是彙總方法的更新版本，其中包含相當多的追蹤資訊：

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

在同一個運算式中執行此方法會產生下列輸出：

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

追蹤輸出並依照上述程式碼進行。 您應該能夠了解程式碼如何在周遊樹狀時瀏覽每個節點並計算總和，然後求得總和。

現在，讓我們來看一個不同的執行，其運算式是由 `sum1` 提供：

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

以下是查看此運算式後的輸出：

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

雖然最後的解都相同，但樹狀周遊則完全不同。 這些節點會依不同順序周遊，因為樹狀建構後所出現的第一個作業不同。

## <a name="learning-more"></a>了解詳細資訊

此範例顯示您所建立的一小部分程式碼，該程式碼會用來周遊及解譯由運算式樹狀架構表示的演算法。 如需建立一般用途程式庫，以將運算式樹狀架構轉譯為其他語言之所有必要工作的完整討論，請閱讀 Matt Warren 所撰寫的[這一系列](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx)。 該系列進一步詳細說明如何將您可能在運算式樹狀架構中找到的任何程式碼進行轉譯。

希望您現在已了解運算式樹狀架構的真正強大之處。
您可以查看一組程式碼、對該程式碼進行任何想要的變更，然後執行變更後的版本。 因為運算式樹狀架構為不可變，所以您可以使用現有樹狀的元件來建立新的樹狀。 如此即可降低建立修改後的運算式樹狀架構所需的記憶體數量。

[下一個主題 -- 總結](expression-trees-summary.md)
