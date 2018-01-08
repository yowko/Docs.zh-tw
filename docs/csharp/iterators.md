---
title: "迭代器"
description: "了解如何使用內建 C# 迭代器，以及如何建立您自己的自訂迭代器方法。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 0a78fe3aa4d88cd5ea1c98f372e4d6672cff5236
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2017
---
# <a name="iterators"></a><span data-ttu-id="4d01b-104">迭代器</span><span class="sxs-lookup"><span data-stu-id="4d01b-104">Iterators</span></span>

<span data-ttu-id="4d01b-105">您撰寫的幾乎所有程式或多或少都需要逐一查看集合。</span><span class="sxs-lookup"><span data-stu-id="4d01b-105">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="4d01b-106">您將會撰寫程式碼，以查看集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="4d01b-106">You'll write code that examines every item in a collection.</span></span> 

<span data-ttu-id="4d01b-107">您也會建立迭代器方法，也就是為該類別的項目產生迭代器的方法。</span><span class="sxs-lookup"><span data-stu-id="4d01b-107">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="4d01b-108">這些方法可用於：</span><span class="sxs-lookup"><span data-stu-id="4d01b-108">These can be used for:</span></span>

+ <span data-ttu-id="4d01b-109">在集合中的每個項目上執行動作。</span><span class="sxs-lookup"><span data-stu-id="4d01b-109">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="4d01b-110">列舉自訂集合。</span><span class="sxs-lookup"><span data-stu-id="4d01b-110">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="4d01b-111">擴充 [LINQ](linq/index.md) 或其他程式庫。</span><span class="sxs-lookup"><span data-stu-id="4d01b-111">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="4d01b-112">建立資料管線，其中的資料會透過迭代器方法有效率地流動。</span><span class="sxs-lookup"><span data-stu-id="4d01b-112">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="4d01b-113">C# 語言會為上述兩個案例提供功能。</span><span class="sxs-lookup"><span data-stu-id="4d01b-113">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="4d01b-114">本文將概述這些功能。</span><span class="sxs-lookup"><span data-stu-id="4d01b-114">This article provides an overview of those features.</span></span>

<span data-ttu-id="4d01b-115">本教學課程有多個步驟。</span><span class="sxs-lookup"><span data-stu-id="4d01b-115">This tutorial has multiple steps.</span></span> <span data-ttu-id="4d01b-116">在每個步驟之後，您可以執行應用程式並查看進度。</span><span class="sxs-lookup"><span data-stu-id="4d01b-116">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="4d01b-117">您也可以[檢視或下載完整的範例](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators)以了解此主題。</span><span class="sxs-lookup"><span data-stu-id="4d01b-117">You can also [view or download the completed sample](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators) for this topic.</span></span> <span data-ttu-id="4d01b-118">如需下載指示，請參閱[範例和教學課程](../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="4d01b-118">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="4d01b-119">使用 foreach 逐一查看</span><span class="sxs-lookup"><span data-stu-id="4d01b-119">Iterating with foreach</span></span>

<span data-ttu-id="4d01b-120">列舉集合很簡單︰`foreach` 關鍵字會列舉集合，並對集合中的每個項目執行一次內嵌陳述式：</span><span class="sxs-lookup"><span data-stu-id="4d01b-120">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="4d01b-121">這樣就全部完成了。</span><span class="sxs-lookup"><span data-stu-id="4d01b-121">That's all there is to it.</span></span> <span data-ttu-id="4d01b-122">若要逐一查看集合的所有內容，只需要 `foreach` 陳述式即可。</span><span class="sxs-lookup"><span data-stu-id="4d01b-122">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="4d01b-123">不過，`foreach` 陳述式不是魔法。</span><span class="sxs-lookup"><span data-stu-id="4d01b-123">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="4d01b-124">它需要在 .NET Core 程式庫中定義下列兩個泛型介面，才能產生逐一查看集合所需的程式碼︰`IEnumerable<T>` 和 `IEnumerator<T>`。</span><span class="sxs-lookup"><span data-stu-id="4d01b-124">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="4d01b-125">以下會更詳細說明這個機制。</span><span class="sxs-lookup"><span data-stu-id="4d01b-125">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="4d01b-126">這兩種介面也有非泛型對應項目︰`IEnumerable` 和 `IEnumerator`。</span><span class="sxs-lookup"><span data-stu-id="4d01b-126">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="4d01b-127">新式程式碼適合使用[泛型](programming-guide/generics/index.md)版本。</span><span class="sxs-lookup"><span data-stu-id="4d01b-127">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="4d01b-128">具有迭代器方法的列舉來源</span><span class="sxs-lookup"><span data-stu-id="4d01b-128">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="4d01b-129">C# 語言另一個很棒的功能是可讓您建立方法，以建立列舉的來源。</span><span class="sxs-lookup"><span data-stu-id="4d01b-129">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="4d01b-130">這些方法稱為「迭代器方法」。</span><span class="sxs-lookup"><span data-stu-id="4d01b-130">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="4d01b-131">迭代器方法定義如何在要求時於序列中產生物件。</span><span class="sxs-lookup"><span data-stu-id="4d01b-131">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="4d01b-132">您可以使用 `yield return` 內容關鍵字來定義迭代器方法。</span><span class="sxs-lookup"><span data-stu-id="4d01b-132">You use the `yield return` contextual keywords to define an iterator method.</span></span> 

<span data-ttu-id="4d01b-133">您可以撰寫這個方法，以產生從 0 到 9 的整數序列：</span><span class="sxs-lookup"><span data-stu-id="4d01b-133">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

<span data-ttu-id="4d01b-134">上述程式碼顯示不同的 `yield return` 陳述式，強調您可以在迭代器方法中使用多個不連續的 `yield return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4d01b-134">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="4d01b-135">您可以 (經常) 使用其他語言建構，來簡化迭代器方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d01b-135">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="4d01b-136">下列方法定義會產生完全相同的數值序列：</span><span class="sxs-lookup"><span data-stu-id="4d01b-136">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

<span data-ttu-id="4d01b-137">您不必決定其中一個。</span><span class="sxs-lookup"><span data-stu-id="4d01b-137">You don't have to decide one or the other.</span></span> <span data-ttu-id="4d01b-138">您可以視需要擁有許多 `yield return` 陳述式，以符合您的方法需求：</span><span class="sxs-lookup"><span data-stu-id="4d01b-138">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
    
    index = 100;
    while (index++ < 110)
        yield return index;
}
```

<span data-ttu-id="4d01b-139">這是基本語法。</span><span class="sxs-lookup"><span data-stu-id="4d01b-139">That's the basic syntax.</span></span> <span data-ttu-id="4d01b-140">讓我們來看一個真實世界範例，您可以在其中撰寫迭代器方法。</span><span class="sxs-lookup"><span data-stu-id="4d01b-140">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="4d01b-141">假設您在某個 IoT 專案中，而裝置感應器會產生很大的資料流。</span><span class="sxs-lookup"><span data-stu-id="4d01b-141">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="4d01b-142">為了熟悉資料，您可以撰寫一個方法，每 N 個資料項目取樣一個項目。</span><span class="sxs-lookup"><span data-stu-id="4d01b-142">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="4d01b-143">此小型迭代器方法即可達成目的：</span><span class="sxs-lookup"><span data-stu-id="4d01b-143">This small iterator method does the trick:</span></span>

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

<span data-ttu-id="4d01b-144">迭代器方法有一項重要限制︰相同的方法中不能同時有 `return` 陳述式和 `yield return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4d01b-144">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="4d01b-145">系統將不會編譯下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4d01b-145">The following will not compile:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
   
    // generates a compile time error: 
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;  
}
```

<span data-ttu-id="4d01b-146">這項限制通常不成問題。</span><span class="sxs-lookup"><span data-stu-id="4d01b-146">This restriction normally isn't a problem.</span></span> <span data-ttu-id="4d01b-147">您可以選擇在整個方法中使用 `yield return`，或是將原始方法分成多個方法，有些方法使用 `return`，而有些方法使用 `yield return`。</span><span class="sxs-lookup"><span data-stu-id="4d01b-147">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="4d01b-148">您可以稍微修改最後一個方法，以在所有位置使用 `yield return`：</span><span class="sxs-lookup"><span data-stu-id="4d01b-148">You can modify the last method slightly to use `yield return` everywhere:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
   
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```
 
<span data-ttu-id="4d01b-149">有時候，適當的解決方法是將一個迭代器方法分成兩個不同的方法。</span><span class="sxs-lookup"><span data-stu-id="4d01b-149">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="4d01b-150">其中一個方法使用 `return`，而第二個方法使用 `yield return`。</span><span class="sxs-lookup"><span data-stu-id="4d01b-150">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="4d01b-151">請考慮您可能需要根據布林值引數傳回空集合或前 5 個奇數的情況。</span><span class="sxs-lookup"><span data-stu-id="4d01b-151">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="4d01b-152">您可以將其撰寫成下列兩個方法：</span><span class="sxs-lookup"><span data-stu-id="4d01b-152">You could write that as these two methods:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index++ < 10)
        if (index % 2 == 1)
            yield return index;
}
```
 
<span data-ttu-id="4d01b-153">請看看上述方法。</span><span class="sxs-lookup"><span data-stu-id="4d01b-153">Look at the methods above.</span></span> <span data-ttu-id="4d01b-154">第一個方法使用標準 `return` 陳述式來傳回空集合，或第二個方法所建立的迭代器。</span><span class="sxs-lookup"><span data-stu-id="4d01b-154">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="4d01b-155">第二個方法使用 `yield return` 陳述式來建立要求的序列。</span><span class="sxs-lookup"><span data-stu-id="4d01b-155">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="4d01b-156">深入探討 `foreach`</span><span class="sxs-lookup"><span data-stu-id="4d01b-156">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="4d01b-157">`foreach` 陳述式會展開為一個標準慣例，該慣例使用 `IEnumerable<T>` 和 `IEnumerator<T>` 介面來逐一查看集合的所有項目。</span><span class="sxs-lookup"><span data-stu-id="4d01b-157">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="4d01b-158">它也會將開發人員未正確管理資源時所發生的錯誤降到最低。</span><span class="sxs-lookup"><span data-stu-id="4d01b-158">It also  minimizes errors developers make by not properly managing resources.</span></span> 

<span data-ttu-id="4d01b-159">編譯器會將第一個範例中所示的 `foreach` 迴圈轉譯為類似下列建構的程式碼：</span><span class="sxs-lookup"><span data-stu-id="4d01b-159">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="4d01b-160">上述建構代表 C# 編譯器第 5 版 (含) 以上版本所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d01b-160">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="4d01b-161">在第 5 版之前，`item` 變數有不同的範圍：</span><span class="sxs-lookup"><span data-stu-id="4d01b-161">Prior to version 5, the `item` variable had a different scope:</span></span>

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="4d01b-162">因為舊版行為可能會導致很難診斷涉及 Lambda 運算式的 Bug ，所以已變更此行為。</span><span class="sxs-lookup"><span data-stu-id="4d01b-162">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="4d01b-163">如需詳細資訊，請參閱 [Lambda 運算式](lambda-expressions.md)一節。</span><span class="sxs-lookup"><span data-stu-id="4d01b-163">See the section on [lambda expressions](lambda-expressions.md) for more information.</span></span> 

<span data-ttu-id="4d01b-164">編譯器所產生的實際程式碼稍微複雜一點，而且會處理 `GetEnumerator()` 所傳回的物件實作 `IDisposable` 介面的情況。</span><span class="sxs-lookup"><span data-stu-id="4d01b-164">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="4d01b-165">完全展開會產生類似如下的程式碼：</span><span class="sxs-lookup"><span data-stu-id="4d01b-165">The full expansion generates code more like this:</span></span>

```csharp
{
    var enumerator = collection.GetEnumerator();
    try 
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally 
    {
        // dispose of enumerator.
    }
}
```

<span data-ttu-id="4d01b-166">用來處置列舉程式的方法取決於 `enumerator` 類型的特性。</span><span class="sxs-lookup"><span data-stu-id="4d01b-166">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="4d01b-167">在一般情況下，`finally` 子句會展開為：</span><span class="sxs-lookup"><span data-stu-id="4d01b-167">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

<span data-ttu-id="4d01b-168">不過，如果 `enumerator` 的類型是密封類型，而且不會將 `enumerator` 的類型隱含轉換成 `IDisposable`，則 `finally` 子句會展開為空白區塊：</span><span class="sxs-lookup"><span data-stu-id="4d01b-168">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>
```csharp
finally 
{
} 
```

<span data-ttu-id="4d01b-169">如果會將 `enumerator` 的類型隱含轉換成 `IDisposable`，而且 `enumerator` 是不可為 null 的實值型別，`finally` 子句會展開為：</span><span class="sxs-lookup"><span data-stu-id="4d01b-169">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

<span data-ttu-id="4d01b-170">還好，您不需要記住上述所有詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4d01b-170">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="4d01b-171">`foreach` 陳述式會為您處理上述所有細微差異。</span><span class="sxs-lookup"><span data-stu-id="4d01b-171">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="4d01b-172">編譯器會為上述任何建構產生正確的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d01b-172">The compiler will generate the correct code for any of these constructs.</span></span> 


