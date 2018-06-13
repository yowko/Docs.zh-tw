---
title: 支援運算式樹狀架構的架構類型
description: 了解支援運算式樹狀架構的架構類型、建立運算式樹狀架構，以及使用運算式樹狀架構 API 的技術。
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 3110f2a9534085aba95fcb5c8e76f66229e79f86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214941"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="20cc7-103">支援運算式樹狀架構的架構類型</span><span class="sxs-lookup"><span data-stu-id="20cc7-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="20cc7-104">上一篇 -- 說明運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="20cc7-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="20cc7-105">.NET Core Framework 中有使用運算式樹狀架構類別的大型清單。</span><span class="sxs-lookup"><span data-stu-id="20cc7-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="20cc7-106">[這裡](/dotnet/core/api/System.Linq.Expressions)可以看到完整清單。</span><span class="sxs-lookup"><span data-stu-id="20cc7-106">You can see the full list [here](/dotnet/core/api/System.Linq.Expressions).</span></span>
<span data-ttu-id="20cc7-107">讓我們了解架構類別是如何設計的，而不是執行完整的清單。</span><span class="sxs-lookup"><span data-stu-id="20cc7-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="20cc7-108">在語言設計中，運算式是估算並傳回值的程式碼本文。</span><span class="sxs-lookup"><span data-stu-id="20cc7-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="20cc7-109">運算式可以非常簡單︰常數運算式 `1` 傳回常數值 1。</span><span class="sxs-lookup"><span data-stu-id="20cc7-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="20cc7-110">它們可以很複雜︰運算式 `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` 傳回一個二次方程式的根 (方程式有解決方案的情況下)。</span><span class="sxs-lookup"><span data-stu-id="20cc7-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="20cc7-111">一切都從 System.Linq.Expression 開始</span><span class="sxs-lookup"><span data-stu-id="20cc7-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="20cc7-112">使用運算式樹狀架構的複雜性之一是許多不同種類的運算式在程式的許多地方都有效。</span><span class="sxs-lookup"><span data-stu-id="20cc7-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="20cc7-113">考慮指派運算式。</span><span class="sxs-lookup"><span data-stu-id="20cc7-113">Consider an assignment expression.</span></span> <span data-ttu-id="20cc7-114">指派的右邊可以是常數值、變數、呼叫運算式的方法，或其他。</span><span class="sxs-lookup"><span data-stu-id="20cc7-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="20cc7-115">該語言的彈性表示，當您周遊運算式樹狀結構時，可能會在樹狀結構節點中的任何位置遇到許多不同的運算式類型。</span><span class="sxs-lookup"><span data-stu-id="20cc7-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="20cc7-116">因此，當您可以使用基底運算式類型時，這是最簡單的運作方式。</span><span class="sxs-lookup"><span data-stu-id="20cc7-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="20cc7-117">不過，有時候您需要了解更多。</span><span class="sxs-lookup"><span data-stu-id="20cc7-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="20cc7-118">基底運算式類別包含此用途的 `NodeType` 屬性。</span><span class="sxs-lookup"><span data-stu-id="20cc7-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="20cc7-119">它會傳回 `ExpressionType`，其為可能的運算式類型列舉。</span><span class="sxs-lookup"><span data-stu-id="20cc7-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="20cc7-120">一旦您知道節點類型，就可以將它轉換成該類型，並執行知道運算式節點類型的特定動作。</span><span class="sxs-lookup"><span data-stu-id="20cc7-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="20cc7-121">您可以搜尋特定的節點類型，然後使用這類運算式的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="20cc7-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="20cc7-122">例如，此程式碼會列印變數存取運算式的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="20cc7-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="20cc7-123">我遵循做法先檢查節點類型，然後轉換成變數存取運算式，再檢查特定運算式類型的屬性︰</span><span class="sxs-lookup"><span data-stu-id="20cc7-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a><span data-ttu-id="20cc7-124">建立運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="20cc7-124">Creating Expression Trees</span></span>

<span data-ttu-id="20cc7-125">`System.Linq.Expression` 類別也包含許多建立運算式的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="20cc7-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="20cc7-126">這些方法會建立使用其子系所提供引數的運算式節點。</span><span class="sxs-lookup"><span data-stu-id="20cc7-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="20cc7-127">如此一來，您就可以從其分葉節點向上建置運算式。</span><span class="sxs-lookup"><span data-stu-id="20cc7-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="20cc7-128">例如，此程式碼會建立 Add 運算式︰</span><span class="sxs-lookup"><span data-stu-id="20cc7-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="20cc7-129">您可以在此簡單的範例中看到，建立和使用運算式樹狀架構牽涉到許多類型。</span><span class="sxs-lookup"><span data-stu-id="20cc7-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="20cc7-130">這種複雜性是必要的，以提供 C# 語言所提供之豐富詞彙的功能。</span><span class="sxs-lookup"><span data-stu-id="20cc7-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="20cc7-131">巡覽 API</span><span class="sxs-lookup"><span data-stu-id="20cc7-131">Navigating the APIs</span></span>
<span data-ttu-id="20cc7-132">有可對應幾乎所有 C# 語言語法項目的運算式節點類型。</span><span class="sxs-lookup"><span data-stu-id="20cc7-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="20cc7-133">每個類型都有針對該語言項目類型的特定方法。</span><span class="sxs-lookup"><span data-stu-id="20cc7-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="20cc7-134">您一次要記得很多東西。</span><span class="sxs-lookup"><span data-stu-id="20cc7-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="20cc7-135">我在這裡用的技巧是使用運算式樹狀架構，而不是嘗試記下一切︰</span><span class="sxs-lookup"><span data-stu-id="20cc7-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>
1. <span data-ttu-id="20cc7-136">查看 `ExpressionType` 列舉的成員來判斷您應該檢查的可能節點。</span><span class="sxs-lookup"><span data-stu-id="20cc7-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="20cc7-137">當您要周遊並了解運算式樹狀架構時，這真的很有幫助。</span><span class="sxs-lookup"><span data-stu-id="20cc7-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="20cc7-138">查看 `Expression` 類別的靜態成員來建立運算式。</span><span class="sxs-lookup"><span data-stu-id="20cc7-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="20cc7-139">這些方法可以從其一組子節點建置任何運算式類型。</span><span class="sxs-lookup"><span data-stu-id="20cc7-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="20cc7-140">查看 `ExpressionVisitor` 類別來建立修改的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="20cc7-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="20cc7-141">當您一一查看這三個區域時，會找到更多。</span><span class="sxs-lookup"><span data-stu-id="20cc7-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="20cc7-142">唯一不變的是，當您開始使用這三個步驟的其中一個時，您會找到您要的資訊。</span><span class="sxs-lookup"><span data-stu-id="20cc7-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="20cc7-143">下一篇 - 執行運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="20cc7-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
 
