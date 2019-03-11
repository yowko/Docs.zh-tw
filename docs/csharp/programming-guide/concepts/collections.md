---
title: 集合 (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: d5e3aeab2e035ec2b5f97fd41c84ffa7625ba0b4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373435"
---
# <a name="collections-c"></a><span data-ttu-id="1c11b-102">集合 (C#)</span><span class="sxs-lookup"><span data-stu-id="1c11b-102">Collections (C#)</span></span>
<span data-ttu-id="1c11b-103">在許多應用程式中，您想要建立和管理相關物件的群組。</span><span class="sxs-lookup"><span data-stu-id="1c11b-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="1c11b-104">有兩種方式可以群組物件：建立物件的陣列和建立物件的集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="1c11b-105">陣列是最適用於建立和處理固定數目的強類型物件。</span><span class="sxs-lookup"><span data-stu-id="1c11b-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="1c11b-106">如需陣列的資訊，請參閱[陣列](../../../csharp/programming-guide/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1c11b-106">For information about arrays, see [Arrays](../../../csharp/programming-guide/arrays/index.md).</span></span>  
  
 <span data-ttu-id="1c11b-107">集合會提供較具彈性的方式來使用物件群組。</span><span class="sxs-lookup"><span data-stu-id="1c11b-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="1c11b-108">與陣列不同的是，您使用的物件群組可依程式變更的需要來動態增減。</span><span class="sxs-lookup"><span data-stu-id="1c11b-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="1c11b-109">對於某些集合，您可以將鍵值指派給您放入集合的任何物件，讓您可以藉由使用鍵值快速擷取物件。</span><span class="sxs-lookup"><span data-stu-id="1c11b-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="1c11b-110">集合是類別，因此您必須在將項目加入該集合之前，宣告類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1c11b-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="1c11b-111">如果集合包含只有一個資料類型的項目，則可使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間內的其中一個類別。</span><span class="sxs-lookup"><span data-stu-id="1c11b-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1c11b-112">泛型集合會強制類型安全，如此就不會加入其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="1c11b-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="1c11b-113">當您從泛型集合中擷取項目時，並不需要判斷其資料類型或將其轉換。</span><span class="sxs-lookup"><span data-stu-id="1c11b-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c11b-114">在本主題的範例中，請包括 `System.Collections.Generic` 和 `System.Linq` 命名空間的 [using](../../../csharp/language-reference/keywords/using-directive.md) 指示詞。</span><span class="sxs-lookup"><span data-stu-id="1c11b-114">For the examples in this topic, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="1c11b-115">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1c11b-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="1c11b-116">使用簡單的集合</span><span class="sxs-lookup"><span data-stu-id="1c11b-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="1c11b-117">集合的種類</span><span class="sxs-lookup"><span data-stu-id="1c11b-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="1c11b-118">System.Collections.Generic 類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="1c11b-119">System.Collections.Concurrent 類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="1c11b-120">System.Collections 類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
-   [<span data-ttu-id="1c11b-121">實作索引鍵/值組集合</span><span class="sxs-lookup"><span data-stu-id="1c11b-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="1c11b-122">使用 LINQ 存取集合</span><span class="sxs-lookup"><span data-stu-id="1c11b-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="1c11b-123">排序集合</span><span class="sxs-lookup"><span data-stu-id="1c11b-123">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="1c11b-124">定義自訂集合</span><span class="sxs-lookup"><span data-stu-id="1c11b-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="1c11b-125">迭代器</span><span class="sxs-lookup"><span data-stu-id="1c11b-125">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="1c11b-126">使用簡單的集合</span><span class="sxs-lookup"><span data-stu-id="1c11b-126">Using a Simple Collection</span></span>  
 <span data-ttu-id="1c11b-127">本節中的範例使用泛型 <xref:System.Collections.Generic.List%601> 類別，能夠讓您使用強型別物件清單。</span><span class="sxs-lookup"><span data-stu-id="1c11b-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="1c11b-128">以下範例會建立字串清單，並使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式逐一查看字串。</span><span class="sxs-lookup"><span data-stu-id="1c11b-128">The following example creates a list of strings and then iterates through the strings by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span>  
  
```csharp  
// Create a list of strings.  
var salmons = new List<string>();  
salmons.Add("chinook");  
salmons.Add("coho");  
salmons.Add("pink");  
salmons.Add("sockeye");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="1c11b-129">如果預先知道集合的內容，即可使用「集合初始設定式」來初始化集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="1c11b-130">如需詳細資訊，請參閱[物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。</span><span class="sxs-lookup"><span data-stu-id="1c11b-130">For more information, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
 <span data-ttu-id="1c11b-131">下列範例與前一個範例相同，但有一點除外，就是集合初始設定式是用來將項目加入集合中。</span><span class="sxs-lookup"><span data-stu-id="1c11b-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="1c11b-132">您可以使用 [for](../../../csharp/language-reference/keywords/for.md) 陳述式來逐一查看集合，而不是使用 `foreach` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c11b-132">You can use a [for](../../../csharp/language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="1c11b-133">您可以藉由依索引位置存取集合項目來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="1c11b-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="1c11b-134">項目的索引以 0 開始，並以項目計數減 1 結束。</span><span class="sxs-lookup"><span data-stu-id="1c11b-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="1c11b-135">下列範例會使用 `for` 來逐一查看集合的項目，而不是使用 `foreach`。</span><span class="sxs-lookup"><span data-stu-id="1c11b-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
for (var index = 0; index < salmons.Count; index++)  
{  
    Console.Write(salmons[index] + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="1c11b-136">下列範例透過指定要移除的物件，從集合中移除項目。</span><span class="sxs-lookup"><span data-stu-id="1c11b-136">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Remove an element from the list by specifying  
// the object.  
salmons.Remove("coho");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook pink sockeye  
```  
  
 <span data-ttu-id="1c11b-137">下列範例會移除泛型清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="1c11b-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="1c11b-138">使用以遞減順序反覆運算的 [for](../../../csharp/language-reference/keywords/for.md) 陳述式，而不是 `foreach` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c11b-138">Instead of a `foreach` statement, a [for](../../../csharp/language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="1c11b-139">這是因為 <xref:System.Collections.Generic.List%601.RemoveAt%2A> 方法導致在已移除之項目後面的項目具有較低的索引值。</span><span class="sxs-lookup"><span data-stu-id="1c11b-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
```csharp  
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
// Remove odd numbers.  
for (var index = numbers.Count - 1; index >= 0; index--)  
{  
    if (numbers[index] % 2 == 1)  
    {  
        // Remove the element by specifying  
        // the zero-based index in the list.  
        numbers.RemoveAt(index);  
    }  
}  
  
// Iterate through the list.  
// A lambda expression is placed in the ForEach method  
// of the List(T) object.  
numbers.ForEach(  
    number => Console.Write(number + " "));  
// Output: 0 2 4 6 8  
```  
  
 <span data-ttu-id="1c11b-140">如需 <xref:System.Collections.Generic.List%601> 中的項目類型，您也可以定義自己的類別。</span><span class="sxs-lookup"><span data-stu-id="1c11b-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="1c11b-141">在下列範例中，<xref:System.Collections.Generic.List%601> 使用的 `Galaxy` 類別是在程式碼中定義的。</span><span class="sxs-lookup"><span data-stu-id="1c11b-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
```csharp  
private static void IterateThroughList()  
{  
    var theGalaxies = new List<Galaxy>  
        {  
            new Galaxy() { Name="Tadpole", MegaLightYears=400},  
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},  
            new Galaxy() { Name="Milky Way", MegaLightYears=0},  
            new Galaxy() { Name="Andromeda", MegaLightYears=3}  
        };  
  
    foreach (Galaxy theGalaxy in theGalaxies)  
    {  
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);  
    }  
  
    // Output:  
    //  Tadpole  400  
    //  Pinwheel  25  
    //  Milky Way  0  
    //  Andromeda  3  
}  
  
public class Galaxy  
{  
    public string Name { get; set; }  
    public int MegaLightYears { get; set; }  
}  
```  

<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a><span data-ttu-id="1c11b-142">集合的種類</span><span class="sxs-lookup"><span data-stu-id="1c11b-142">Kinds of Collections</span></span> 
 <span data-ttu-id="1c11b-143">.NET Framework 會提供很多常見的集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="1c11b-144">各個類型的集合都是針對特定用途來設計。</span><span class="sxs-lookup"><span data-stu-id="1c11b-144">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="1c11b-145">下列集合類別的群組將在本節介紹：</span><span class="sxs-lookup"><span data-stu-id="1c11b-145">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="1c11b-146"><xref:System.Collections.Generic> 類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-146"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="1c11b-147"><xref:System.Collections.Concurrent> 類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-147"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="1c11b-148"><xref:System.Collections> 類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-148"><xref:System.Collections> classes</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="1c11b-149">System.Collections.Generic 類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-149">System.Collections.Generic Classes</span></span>  
 <span data-ttu-id="1c11b-150">藉由使用 <xref:System.Collections.Generic> 命名空間的其中一個類別，您可以建立泛型集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="1c11b-151">當集合中每個項目的資料類型相同時，泛型集合就相當有用。</span><span class="sxs-lookup"><span data-stu-id="1c11b-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="1c11b-152">泛型集合會透過只允許加入所需資料類型的方式，強制使用強式類型。</span><span class="sxs-lookup"><span data-stu-id="1c11b-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="1c11b-153">下表列出 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間的一些常用類別：</span><span class="sxs-lookup"><span data-stu-id="1c11b-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  

|<span data-ttu-id="1c11b-154">類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-154">Class</span></span>|<span data-ttu-id="1c11b-155">說明</span><span class="sxs-lookup"><span data-stu-id="1c11b-155">Description</span></span>| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="1c11b-156">表示根據索引鍵所整理的索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="1c11b-157">表示可以依照索引存取的物件清單。</span><span class="sxs-lookup"><span data-stu-id="1c11b-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="1c11b-158">提供搜尋、排序和修改清單的方法。</span><span class="sxs-lookup"><span data-stu-id="1c11b-158">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="1c11b-159">表示物件的先進先出 (FIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="1c11b-160">代表根據關聯的 <xref:System.Collections.Generic.IComparer%601> 實作，依索引鍵所排序的索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="1c11b-161">表示物件的後進先出 (LIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="1c11b-162">如需其他資訊，請參閱[常用的集合類型](../../../standard/collections/commonly-used-collection-types.md)、[選取集合類別](../../../standard/collections/selecting-a-collection-class.md)和 <xref:System.Collections.Generic>。</span><span class="sxs-lookup"><span data-stu-id="1c11b-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="1c11b-163">System.Collections.Concurrent 類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-163">System.Collections.Concurrent Classes</span></span>  
 <span data-ttu-id="1c11b-164">在 .NET Framework 4 或更新版本中，<xref:System.Collections.Concurrent> 命名空間中的集合提供了有效率的安全執行緒作業，可從多個執行緒存取集合項目。</span><span class="sxs-lookup"><span data-stu-id="1c11b-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="1c11b-165">每當有多個執行緒同時存取集合時，應該使用 <xref:System.Collections.Concurrent> 命名空間中的類別來代替 <xref:System.Collections.Generic?displayProperty=nameWithType> 和 <xref:System.Collections?displayProperty=nameWithType> 命名空間中的對應類型。</span><span class="sxs-lookup"><span data-stu-id="1c11b-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="1c11b-166">如需詳細資訊，請參閱[安全執行緒集合](../../../standard/collections/thread-safe/index.md)和 <xref:System.Collections.Concurrent>。</span><span class="sxs-lookup"><span data-stu-id="1c11b-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="1c11b-167"><xref:System.Collections.Concurrent> 命名空間中包含一些類別，包括 <xref:System.Collections.Concurrent.BlockingCollection%601>、<xref:System.Collections.Concurrent.ConcurrentDictionary%602>、<xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601>。</span><span class="sxs-lookup"><span data-stu-id="1c11b-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="1c11b-168">System.Collections 類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-168">System.Collections Classes</span></span>  
 <span data-ttu-id="1c11b-169"><xref:System.Collections?displayProperty=nameWithType> 命名空間中的類別不會將項目儲存為特別類型物件，而是會儲存為 `Object` 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="1c11b-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="1c11b-170">可能的話，您應該使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間或 <xref:System.Collections.Concurrent> 命名空間中的泛型集合，而非 `System.Collections` 命名空間中的傳統類型。</span><span class="sxs-lookup"><span data-stu-id="1c11b-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="1c11b-171">下表列出 `System.Collections` 命名空間的一些常用類別：</span><span class="sxs-lookup"><span data-stu-id="1c11b-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="1c11b-172">類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-172">Class</span></span>|<span data-ttu-id="1c11b-173">說明</span><span class="sxs-lookup"><span data-stu-id="1c11b-173">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="1c11b-174">代表會視需要動態增加大小的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="1c11b-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="1c11b-175">代表根據索引鍵的雜湊程式碼，所整理的索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="1c11b-176">表示物件的先進先出 (FIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="1c11b-177">表示物件的後進先出 (LIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="1c11b-178"><xref:System.Collections.Specialized> 命名空間會提供特製化類型和強型別集合類別，例如只有字串的集合，以及連結串列和 Hybrid 字典。</span><span class="sxs-lookup"><span data-stu-id="1c11b-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="1c11b-179">實作索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-179">Implementing a Collection of Key/Value Pairs</span></span>  
 <span data-ttu-id="1c11b-180"><xref:System.Collections.Generic.Dictionary%602> 泛型集合可讓您使用每個項目的索引鍵來存取集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="1c11b-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="1c11b-181">加入字典中的每一個項目都是由值及其關聯索引鍵所組成。</span><span class="sxs-lookup"><span data-stu-id="1c11b-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="1c11b-182">使用其索引鍵擷取值的速度非常快，因為 `Dictionary` 類別是實作為雜湊表。</span><span class="sxs-lookup"><span data-stu-id="1c11b-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="1c11b-183">下列範例會使用 `foreach` 陳述式建立 `Dictionary` 集合並逐一查看字典。</span><span class="sxs-lookup"><span data-stu-id="1c11b-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>  
  
```csharp  
private static void IterateThruDictionary()  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    foreach (KeyValuePair<string, Element> kvp in elements)  
    {  
        Element theElement = kvp.Value;  
  
        Console.WriteLine("key: " + kvp.Key);  
        Console.WriteLine("values: " + theElement.Symbol + " " +  
            theElement.Name + " " + theElement.AtomicNumber);  
    }  
}  
  
private static Dictionary<string, Element> BuildDictionary()  
{  
    var elements = new Dictionary<string, Element>();  
  
    AddToDictionary(elements, "K", "Potassium", 19);  
    AddToDictionary(elements, "Ca", "Calcium", 20);  
    AddToDictionary(elements, "Sc", "Scandium", 21);  
    AddToDictionary(elements, "Ti", "Titanium", 22);  
  
    return elements;  
}  
  
private static void AddToDictionary(Dictionary<string, Element> elements,  
    string symbol, string name, int atomicNumber)  
{  
    Element theElement = new Element();  
  
    theElement.Symbol = symbol;  
    theElement.Name = name;  
    theElement.AtomicNumber = atomicNumber;  
  
    elements.Add(key: theElement.Symbol, value: theElement);  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  
  
 <span data-ttu-id="1c11b-184">若要改為使用集合初始設定式建置 `Dictionary` 集合，您可以使用下列方法取代 `BuildDictionary` 和 `AddToDictionary` 方法。</span><span class="sxs-lookup"><span data-stu-id="1c11b-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
```csharp  
private static Dictionary<string, Element> BuildDictionary2()  
{  
    return new Dictionary<string, Element>  
    {  
        {"K",  
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        {"Ca",  
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        {"Sc",  
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        {"Ti",  
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
```  
  
 <span data-ttu-id="1c11b-185">下列範例會使用 <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> 方法和 `Dictionary` 的 <xref:System.Collections.Generic.Dictionary%602.Item%2A> 屬性來依索引鍵快速尋找項目。</span><span class="sxs-lookup"><span data-stu-id="1c11b-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="1c11b-186">藉由使用 C# 中的 `elements[symbol]`，`Item` 屬性可讓您存取 `elements` 集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="1c11b-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>  
  
```csharp  
private static void FindInDictionary(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    if (elements.ContainsKey(symbol) == false)  
    {  
        Console.WriteLine(symbol + " not found");  
    }  
    else  
    {  
        Element theElement = elements[symbol];  
        Console.WriteLine("found: " + theElement.Name);  
    }  
}  
```  
  
 <span data-ttu-id="1c11b-187">下列範例會使用 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 方法依索引鍵來快速尋找項目。</span><span class="sxs-lookup"><span data-stu-id="1c11b-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
```csharp  
private static void FindInDictionary2(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    Element theElement = null;  
    if (elements.TryGetValue(symbol, out theElement) == false)  
        Console.WriteLine(symbol + " not found");  
    else  
        Console.WriteLine("found: " + theElement.Name);  
}  
```  

<a name="BKMK_LINQ"></a>
## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="1c11b-188">使用 LINQ 存取集合</span><span class="sxs-lookup"><span data-stu-id="1c11b-188">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="1c11b-189">LINQ (Language-Integrated Query (LINQ)) 可用來存取集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="1c11b-190">LINQ 查詢提供篩選、排序和分組功能。</span><span class="sxs-lookup"><span data-stu-id="1c11b-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="1c11b-191">如需詳細資訊，請參閱[開始使用 C# 中的 LINQ](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="1c11b-191">For more information, see  [Getting Started with LINQ in C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="1c11b-192">下列範例會對泛型 `List` 執行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="1c11b-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="1c11b-193">LINQ 查詢會傳回包含結果的不同集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-193">The LINQ query returns a different collection that contains the results.</span></span>  
  
```csharp  
private static void ShowLINQ()  
{  
    List<Element> elements = BuildList();  
  
    // LINQ Query.  
    var subset = from theElement in elements  
                 where theElement.AtomicNumber < 22  
                 orderby theElement.Name  
                 select theElement;  
  
    foreach (Element theElement in subset)  
    {  
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);  
    }  
  
    // Output:  
    //  Calcium 20  
    //  Potassium 19  
    //  Scandium 21  
}  
  
private static List<Element> BuildList()  
{  
    return new List<Element>  
    {  
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  

<a name="BKMK_Sorting"></a>
## <a name="sorting-a-collection"></a><span data-ttu-id="1c11b-194">為集合排序</span><span class="sxs-lookup"><span data-stu-id="1c11b-194">Sorting a Collection</span></span>  
 <span data-ttu-id="1c11b-195">下列範例說明排序集合的程序。</span><span class="sxs-lookup"><span data-stu-id="1c11b-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="1c11b-196">此範例排序儲存在 <xref:System.Collections.Generic.List%601> 中的 `Car` 類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="1c11b-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="1c11b-197">`Car` 類別實作 <xref:System.IComparable%601> 介面，而這個介面要求實作 <xref:System.IComparable%601.CompareTo%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1c11b-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="1c11b-198">每次對 <xref:System.IComparable%601.CompareTo%2A> 方法的呼叫都會進行用於排序的單一比較。</span><span class="sxs-lookup"><span data-stu-id="1c11b-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="1c11b-199">當目前物件和另一個物件比較時，在 `CompareTo` 方法中的使用者撰寫程式碼會傳回值。</span><span class="sxs-lookup"><span data-stu-id="1c11b-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="1c11b-200">如果目前物件比另一個物件小則傳回的值小於零，如果目前物件比另一個物件大則傳回的值大於零，如果它們相等則傳回零。</span><span class="sxs-lookup"><span data-stu-id="1c11b-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="1c11b-201">這可讓您以程式碼定義大於、小於、等於的準則。</span><span class="sxs-lookup"><span data-stu-id="1c11b-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="1c11b-202">在 `ListCars` 方法中，`cars.Sort()` 陳述式會排序清單。</span><span class="sxs-lookup"><span data-stu-id="1c11b-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="1c11b-203">對 <xref:System.Collections.Generic.List%601> 之 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的這個呼叫，會導致 `CompareTo` 方法對 `List` 的 `Car` 物件自動呼叫。</span><span class="sxs-lookup"><span data-stu-id="1c11b-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
```csharp  
private static void ListCars()  
{  
    var cars = new List<Car>  
    {  
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},  
        { new Car() { Name = "car2", Color = "red", Speed = 50}},  
        { new Car() { Name = "car3", Color = "green", Speed = 10}},  
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},  
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},  
        { new Car() { Name = "car6", Color = "red", Speed = 60}},  
        { new Car() { Name = "car7", Color = "green", Speed = 50}}  
    };  
  
    // Sort the cars by color alphabetically, and then by speed  
    // in descending order.  
    cars.Sort();  
  
    // View all of the cars.  
    foreach (Car thisCar in cars)  
    {  
        Console.Write(thisCar.Color.PadRight(5) + " ");  
        Console.Write(thisCar.Speed.ToString() + " ");  
        Console.Write(thisCar.Name);  
        Console.WriteLine();  
    }  
  
    // Output:  
    //  blue  50 car4  
    //  blue  30 car5  
    //  blue  20 car1  
    //  green 50 car7  
    //  green 10 car3  
    //  red   60 car6  
    //  red   50 car2  
}  
  
public class Car : IComparable<Car>  
{  
    public string Name { get; set; }  
    public int Speed { get; set; }  
    public string Color { get; set; }  
  
    public int CompareTo(Car other)  
    {  
        // A call to this method makes a single comparison that is  
        // used for sorting.  
  
        // Determine the relative order of the objects being compared.  
        // Sort by color alphabetically, and then by speed in  
        // descending order.  
  
        // Compare the colors.  
        int compare;  
        compare = String.Compare(this.Color, other.Color, true);  
  
        // If the colors are the same, compare the speeds.  
        if (compare == 0)  
        {  
            compare = this.Speed.CompareTo(other.Speed);  
  
            // Use descending order for speed.  
            compare = -compare;  
        }  
  
        return compare;  
    }  
}  
```  
  
<a name="BKMK_CustomCollection"></a>
## <a name="defining-a-custom-collection"></a><span data-ttu-id="1c11b-204">定義自訂集合</span><span class="sxs-lookup"><span data-stu-id="1c11b-204">Defining a Custom Collection</span></span>  
 <span data-ttu-id="1c11b-205">您可以透過實作 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Collections.IEnumerable> 介面來定義集合。</span><span class="sxs-lookup"><span data-stu-id="1c11b-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>  
  
 <span data-ttu-id="1c11b-206">雖然您可以定義自訂集合，但是使用包含在 .NET Framework 中的集合 (本主題稍早在[集合的種類](#BKMK_KindsOfCollections)中所述) 通常會比較好。</span><span class="sxs-lookup"><span data-stu-id="1c11b-206">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="1c11b-207">下列範例會定義名為 `AllColors` 的自訂集合類別。</span><span class="sxs-lookup"><span data-stu-id="1c11b-207">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="1c11b-208">這個類別實作 <xref:System.Collections.IEnumerable> 介面，該介面要求實作 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1c11b-208">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="1c11b-209">`GetEnumerator` 方法會傳回 `ColorEnumerator` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1c11b-209">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="1c11b-210">`ColorEnumerator` 實作 <xref:System.Collections.IEnumerator> 介面，而此介面會要求實作 <xref:System.Collections.IEnumerator.Current%2A> 屬性、<xref:System.Collections.IEnumerator.MoveNext%2A> 方法和 <xref:System.Collections.IEnumerator.Reset%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1c11b-210">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
```csharp  
private static void ListColors()  
{  
    var colors = new AllColors();  
  
    foreach (Color theColor in colors)  
    {  
        Console.Write(theColor.Name + " ");  
    }  
    Console.WriteLine();  
    // Output: red blue green  
}  
  
// Collection class.  
public class AllColors : System.Collections.IEnumerable  
{  
    Color[] _colors =  
    {  
        new Color() { Name = "red" },  
        new Color() { Name = "blue" },  
        new Color() { Name = "green" }  
    };  
  
    public System.Collections.IEnumerator GetEnumerator()  
    {  
        return new ColorEnumerator(_colors);  
  
        // Instead of creating a custom enumerator, you could  
        // use the GetEnumerator of the array.  
        //return _colors.GetEnumerator();  
    }  
  
    // Custom enumerator.  
    private class ColorEnumerator : System.Collections.IEnumerator  
    {  
        private Color[] _colors;  
        private int _position = -1;  
  
        public ColorEnumerator(Color[] colors)  
        {  
            _colors = colors;  
        }  
  
        object System.Collections.IEnumerator.Current  
        {  
            get  
            {  
                return _colors[_position];  
            }  
        }  
  
        bool System.Collections.IEnumerator.MoveNext()  
        {  
            _position++;  
            return (_position < _colors.Length);  
        }  
  
        void System.Collections.IEnumerator.Reset()  
        {  
            _position = -1;  
        }  
    }  
}  
  
// Element class.  
public class Color  
{  
    public string Name { get; set; }  
}  
```  

<a name="BKMK_Iterators"></a> 
## <a name="iterators"></a><span data-ttu-id="1c11b-211">迭代器</span><span class="sxs-lookup"><span data-stu-id="1c11b-211">Iterators</span></span>  
 <span data-ttu-id="1c11b-212">「迭代器」是用來在集合上執行自訂反覆項目。</span><span class="sxs-lookup"><span data-stu-id="1c11b-212">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="1c11b-213">迭代器可以是方法或 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="1c11b-213">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="1c11b-214">迭代器會使用 [yield return](../../../csharp/language-reference/keywords/yield.md) 陳述式，一次一個地傳回集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="1c11b-214">An iterator uses a [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="1c11b-215">您會使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式來呼叫迭代器。</span><span class="sxs-lookup"><span data-stu-id="1c11b-215">You call an iterator by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="1c11b-216">`foreach` 迴圈的每個反覆項目都會呼叫迭代器。</span><span class="sxs-lookup"><span data-stu-id="1c11b-216">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="1c11b-217">在迭代器中到達 `yield return` 陳述式時，會傳回運算式，並保留程式碼中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="1c11b-217">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="1c11b-218">下一次呼叫迭代器時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="1c11b-218">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="1c11b-219">如需詳細資訊，請參閱[迭代器 (C#)](../../../csharp/programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="1c11b-219">For more information, see [Iterators (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="1c11b-220">下列範例使用了 iterator 方法。</span><span class="sxs-lookup"><span data-stu-id="1c11b-220">The following example uses an iterator method.</span></span> <span data-ttu-id="1c11b-221">Iterator 方法具有 [for](../../../csharp/language-reference/keywords/for.md) 迴圈內的 `yield return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c11b-221">The iterator method has a `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="1c11b-222">在 `ListEvenNumbers` 方法中，`foreach` 陳述式主體的每個反覆項目都會建立對 Iterator 方法的呼叫，這個方法將繼續執行下一個 `yield return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c11b-222">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>  
  
```csharp  
private static void ListEvenNumbers()  
{  
    foreach (int number in EvenSequence(5, 18))  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    Console.WriteLine();  
    // Output: 6 8 10 12 14 16 18  
}  
  
private static IEnumerable<int> EvenSequence(  
    int firstNumber, int lastNumber)  
{  
    // Yield even numbers in the range.  
    for (var number = firstNumber; number <= lastNumber; number++)  
    {  
        if (number % 2 == 0)  
        {  
            yield return number;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c11b-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c11b-223">See also</span></span>

- [<span data-ttu-id="1c11b-224">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="1c11b-224">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="1c11b-225">程式設計概念 (C#)</span><span class="sxs-lookup"><span data-stu-id="1c11b-225">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)
- [<span data-ttu-id="1c11b-226">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="1c11b-226">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="1c11b-227">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="1c11b-227">LINQ to Objects (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="1c11b-228">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1c11b-228">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="1c11b-229">集合和資料結構</span><span class="sxs-lookup"><span data-stu-id="1c11b-229">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="1c11b-230">選取集合類別</span><span class="sxs-lookup"><span data-stu-id="1c11b-230">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="1c11b-231">在集合內比較和排序</span><span class="sxs-lookup"><span data-stu-id="1c11b-231">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="1c11b-232">何時使用泛型集合</span><span class="sxs-lookup"><span data-stu-id="1c11b-232">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
