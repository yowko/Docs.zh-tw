---
title: 集合 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 563cef59c0e52d41dcdeaa51b5bc4d7b8f9554f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644312"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="52535-102">集合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52535-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="52535-103">在許多應用程式中，您想要建立和管理相關物件的群組。</span><span class="sxs-lookup"><span data-stu-id="52535-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="52535-104">有兩種方式可以群組物件：建立物件的陣列和建立物件的集合。</span><span class="sxs-lookup"><span data-stu-id="52535-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="52535-105">陣列是最適用於建立和處理固定數目的強類型物件。</span><span class="sxs-lookup"><span data-stu-id="52535-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="52535-106">如需陣列的資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="52535-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="52535-107">集合會提供較具彈性的方式來使用物件群組。</span><span class="sxs-lookup"><span data-stu-id="52535-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="52535-108">與陣列不同的是，您使用的物件群組可依程式變更的需要來動態增減。</span><span class="sxs-lookup"><span data-stu-id="52535-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="52535-109">對於某些集合，您可以將鍵值指派給您放入集合的任何物件，讓您可以藉由使用鍵值快速擷取物件。</span><span class="sxs-lookup"><span data-stu-id="52535-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="52535-110">集合是類別，因此您必須在將項目加入該集合之前，宣告類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="52535-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="52535-111">如果集合包含只有一個資料類型的項目，則可使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間內的其中一個類別。</span><span class="sxs-lookup"><span data-stu-id="52535-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="52535-112">泛型集合會強制類型安全，如此就不會加入其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="52535-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="52535-113">當您從泛型集合中擷取項目時，並不需要判斷其資料類型或將其轉換。</span><span class="sxs-lookup"><span data-stu-id="52535-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52535-114">本主題中的範例，包括[匯入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)陳述式`System.Collections.Generic`和`System.Linq`命名空間。</span><span class="sxs-lookup"><span data-stu-id="52535-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="52535-115">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="52535-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="52535-116">使用簡單的集合</span><span class="sxs-lookup"><span data-stu-id="52535-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="52535-117">集合的種類</span><span class="sxs-lookup"><span data-stu-id="52535-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="52535-118">System.Collections.Generic 類別</span><span class="sxs-lookup"><span data-stu-id="52535-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="52535-119">System.Collections.Concurrent 類別</span><span class="sxs-lookup"><span data-stu-id="52535-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="52535-120">System.Collections 類別</span><span class="sxs-lookup"><span data-stu-id="52535-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="52535-121">Visual Basic Collection 類別</span><span class="sxs-lookup"><span data-stu-id="52535-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="52535-122">實作索引鍵/值組集合</span><span class="sxs-lookup"><span data-stu-id="52535-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="52535-123">使用 LINQ 存取集合</span><span class="sxs-lookup"><span data-stu-id="52535-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="52535-124">排序集合</span><span class="sxs-lookup"><span data-stu-id="52535-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="52535-125">定義自訂集合</span><span class="sxs-lookup"><span data-stu-id="52535-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="52535-126">迭代器</span><span class="sxs-lookup"><span data-stu-id="52535-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="52535-127">使用簡單的集合</span><span class="sxs-lookup"><span data-stu-id="52535-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="52535-128">本節中的範例使用泛型 <xref:System.Collections.Generic.List%601> 類別，能夠讓您使用強型別物件清單。</span><span class="sxs-lookup"><span data-stu-id="52535-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="52535-129">下列範例會建立字串清單，並再逐一查看字串使用[每個...下一步](../../../visual-basic/language-reference/statements/for-each-next-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="52535-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
```vb  
' Create a list of strings.  
Dim salmons As New List(Of String)  
salmons.Add("chinook")  
salmons.Add("coho")  
salmons.Add("pink")  
salmons.Add("sockeye")  
  
' Iterate through the list.  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="52535-130">如果預先知道集合的內容，即可使用「集合初始設定式」來初始化集合。</span><span class="sxs-lookup"><span data-stu-id="52535-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="52535-131">如需詳細資訊，請參閱[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="52535-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="52535-132">下列範例與前一個範例相同，但有一點除外，就是集合初始設定式是用來將項目加入集合中。</span><span class="sxs-lookup"><span data-stu-id="52535-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="52535-133">您可以使用[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)陳述式來取代`For Each`陳述式來逐一查看集合。</span><span class="sxs-lookup"><span data-stu-id="52535-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="52535-134">您可以藉由依索引位置存取集合項目來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="52535-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="52535-135">項目的索引以 0 開始，並以項目計數減 1 結束。</span><span class="sxs-lookup"><span data-stu-id="52535-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="52535-136">下列範例會使用 `For…Next` 來逐一查看集合的項目，而不是使用 `For Each`。</span><span class="sxs-lookup"><span data-stu-id="52535-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="52535-137">下列範例透過指定要移除的物件，從集合中移除項目。</span><span class="sxs-lookup"><span data-stu-id="52535-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
' Remove an element in the list by specifying  
' the object.  
salmons.Remove("coho")  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook pink sockeye  
```  
  
 <span data-ttu-id="52535-138">下列範例會移除泛型清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="52535-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="52535-139">而不是`For Each`陳述式， [For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)以遞減順序反覆運算的陳述式。</span><span class="sxs-lookup"><span data-stu-id="52535-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="52535-140">這是因為 <xref:System.Collections.Generic.List%601.RemoveAt%2A> 方法導致在已移除之項目後面的項目具有較低的索引值。</span><span class="sxs-lookup"><span data-stu-id="52535-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
```vb  
Dim numbers As New List(Of Integer) From  
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}  
  
' Remove odd numbers.  
For index As Integer = numbers.Count - 1 To 0 Step -1  
    If numbers(index) Mod 2 = 1 Then  
        ' Remove the element by specifying  
        ' the zero-based index in the list.  
        numbers.RemoveAt(index)  
    End If  
Next  
  
' Iterate through the list.  
' A lambda expression is placed in the ForEach method  
' of the List(T) object.  
numbers.ForEach(  
    Sub(number) Console.Write(number & " "))  
' Output: 0 2 4 6 8  
```  
  
 <span data-ttu-id="52535-141">如需 <xref:System.Collections.Generic.List%601> 中的項目類型，您也可以定義自己的類別。</span><span class="sxs-lookup"><span data-stu-id="52535-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="52535-142">在下列範例中，<xref:System.Collections.Generic.List%601> 使用的 `Galaxy` 類別是在程式碼中定義的。</span><span class="sxs-lookup"><span data-stu-id="52535-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
```vb  
Private Sub IterateThroughList()  
    Dim theGalaxies As New List(Of Galaxy) From  
        {  
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},  
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},  
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},  
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}  
        }  
  
    For Each theGalaxy In theGalaxies  
        With theGalaxy  
            Console.WriteLine(.Name & "  " & .MegaLightYears)  
        End With  
    Next  
  
    ' Output:  
    '  Tadpole  400  
    '  Pinwheel  25  
    '  Milky Way  0  
    '  Andromeda  3  
End Sub  
  
Public Class Galaxy  
    Public Property Name As String  
    Public Property MegaLightYears As Integer  
End Class  
```  
  
<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a><span data-ttu-id="52535-143">集合的種類</span><span class="sxs-lookup"><span data-stu-id="52535-143">Kinds of Collections</span></span>   
 <span data-ttu-id="52535-144">.NET Framework 會提供很多常見的集合。</span><span class="sxs-lookup"><span data-stu-id="52535-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="52535-145">各個類型的集合都是針對特定用途來設計。</span><span class="sxs-lookup"><span data-stu-id="52535-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="52535-146">下列集合類別的群組將在本節介紹：</span><span class="sxs-lookup"><span data-stu-id="52535-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="52535-147"><xref:System.Collections.Generic> 類別</span><span class="sxs-lookup"><span data-stu-id="52535-147"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="52535-148"><xref:System.Collections.Concurrent> 類別</span><span class="sxs-lookup"><span data-stu-id="52535-148"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="52535-149"><xref:System.Collections> 類別</span><span class="sxs-lookup"><span data-stu-id="52535-149"><xref:System.Collections> classes</span></span>  
  
-   <span data-ttu-id="52535-150">Visual Basic`Collection`類別</span><span class="sxs-lookup"><span data-stu-id="52535-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="52535-151">System.Collections.Generic 類別</span><span class="sxs-lookup"><span data-stu-id="52535-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="52535-152">藉由使用 <xref:System.Collections.Generic> 命名空間的其中一個類別，您可以建立泛型集合。</span><span class="sxs-lookup"><span data-stu-id="52535-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="52535-153">當集合中每個項目的資料類型相同時，泛型集合就相當有用。</span><span class="sxs-lookup"><span data-stu-id="52535-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="52535-154">泛型集合會透過只允許加入所需資料類型的方式，強制使用強式類型。</span><span class="sxs-lookup"><span data-stu-id="52535-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="52535-155">下表列出 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間的一些常用類別：</span><span class="sxs-lookup"><span data-stu-id="52535-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="52535-156">類別</span><span class="sxs-lookup"><span data-stu-id="52535-156">Class</span></span>|<span data-ttu-id="52535-157">描述</span><span class="sxs-lookup"><span data-stu-id="52535-157">Description</span></span>|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="52535-158">表示根據索引鍵所整理的索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="52535-158">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="52535-159">表示可以依照索引存取的物件清單。</span><span class="sxs-lookup"><span data-stu-id="52535-159">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="52535-160">提供搜尋、排序和修改清單的方法。</span><span class="sxs-lookup"><span data-stu-id="52535-160">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="52535-161">表示物件的先進先出 (FIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="52535-161">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="52535-162">代表根據關聯的 <xref:System.Collections.Generic.IComparer%601> 實作，依索引鍵所排序的索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="52535-162">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="52535-163">表示物件的後進先出 (LIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="52535-163">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="52535-164">如需其他資訊，請參閱[常用的集合類型](../../../standard/collections/commonly-used-collection-types.md)、[選取集合類別](../../../standard/collections/selecting-a-collection-class.md)和 <xref:System.Collections.Generic?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="52535-164">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="52535-165">System.Collections.Concurrent 類別</span><span class="sxs-lookup"><span data-stu-id="52535-165">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="52535-166">在 .NET Framework 4 或更新版本中，<xref:System.Collections.Concurrent> 命名空間中的集合提供了有效率的安全執行緒作業，可從多個執行緒存取集合項目。</span><span class="sxs-lookup"><span data-stu-id="52535-166">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="52535-167">每當有多個執行緒同時存取集合時，應該使用 <xref:System.Collections.Concurrent> 命名空間中的類別來代替 <xref:System.Collections.Generic?displayProperty=nameWithType> 和 <xref:System.Collections?displayProperty=nameWithType> 命名空間中的對應類型。</span><span class="sxs-lookup"><span data-stu-id="52535-167">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="52535-168">如需詳細資訊，請參閱[安全執行緒集合](../../../standard/collections/thread-safe/index.md)和 <xref:System.Collections.Concurrent>。</span><span class="sxs-lookup"><span data-stu-id="52535-168">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="52535-169"><xref:System.Collections.Concurrent> 命名空間中包含一些類別，包括 <xref:System.Collections.Concurrent.BlockingCollection%601>、<xref:System.Collections.Concurrent.ConcurrentDictionary%602>、<xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601>。</span><span class="sxs-lookup"><span data-stu-id="52535-169">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="52535-170">System.Collections 類別</span><span class="sxs-lookup"><span data-stu-id="52535-170">System.Collections Classes</span></span>    
 <span data-ttu-id="52535-171"><xref:System.Collections?displayProperty=nameWithType> 命名空間中的類別不會將項目儲存為特別類型物件，而是會儲存為 `Object` 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="52535-171">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="52535-172">可能的話，您應該使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間或 <xref:System.Collections.Concurrent> 命名空間中的泛型集合，而非 `System.Collections` 命名空間中的傳統類型。</span><span class="sxs-lookup"><span data-stu-id="52535-172">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="52535-173">下表列出 `System.Collections` 命名空間的一些常用類別：</span><span class="sxs-lookup"><span data-stu-id="52535-173">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="52535-174">類別</span><span class="sxs-lookup"><span data-stu-id="52535-174">Class</span></span>|<span data-ttu-id="52535-175">描述</span><span class="sxs-lookup"><span data-stu-id="52535-175">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="52535-176">代表會視需要動態增加大小的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="52535-176">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="52535-177">代表根據索引鍵的雜湊程式碼，所整理的索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="52535-177">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="52535-178">表示物件的先進先出 (FIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="52535-178">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="52535-179">表示物件的後進先出 (LIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="52535-179">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="52535-180"><xref:System.Collections.Specialized> 命名空間會提供特製化類型和強型別集合類別，例如只有字串的集合，以及連結串列和 Hybrid 字典。</span><span class="sxs-lookup"><span data-stu-id="52535-180">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="52535-181">Visual Basic Collection 類別</span><span class="sxs-lookup"><span data-stu-id="52535-181">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="52535-182">您可以使用 Visual Basic<xref:Microsoft.VisualBasic.Collection>類別來存取集合項目使用的數字索引或`String`索引鍵。</span><span class="sxs-lookup"><span data-stu-id="52535-182">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="52535-183">不論是否指定索引鍵，您都可以在集合物件中加入項目。</span><span class="sxs-lookup"><span data-stu-id="52535-183">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="52535-184">如果加入不具索引鍵的項目，則必須使用它的數值索引加以存取。</span><span class="sxs-lookup"><span data-stu-id="52535-184">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="52535-185">Visual Basic`Collection`類別為型別會儲存它的所有元素`Object`，所以您可以新增任何資料類型的項目。</span><span class="sxs-lookup"><span data-stu-id="52535-185">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="52535-186">無法確定加入的資料類型皆適當無誤。</span><span class="sxs-lookup"><span data-stu-id="52535-186">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="52535-187">當您使用 Visual Basic`Collection`類別，在集合中的第一個項目具有索引為 1。</span><span class="sxs-lookup"><span data-stu-id="52535-187">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="52535-188">這與 .NET Framework 集合類別不同，後者的起始索引為 0。</span><span class="sxs-lookup"><span data-stu-id="52535-188">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="52535-189">可能的話，您應該使用中的泛型集合<xref:System.Collections.Generic?displayProperty=nameWithType>命名空間或<xref:System.Collections.Concurrent>命名空間，而不是 Visual Basic`Collection`類別。</span><span class="sxs-lookup"><span data-stu-id="52535-189">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="52535-190">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Collection>。</span><span class="sxs-lookup"><span data-stu-id="52535-190">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="52535-191">實作索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="52535-191">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="52535-192"><xref:System.Collections.Generic.Dictionary%602> 泛型集合可讓您使用每個項目的索引鍵來存取集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="52535-192">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="52535-193">加入字典中的每一個項目都是由值及其關聯索引鍵所組成。</span><span class="sxs-lookup"><span data-stu-id="52535-193">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="52535-194">使用其索引鍵擷取值的速度非常快，因為 `Dictionary` 類別是實作為雜湊表。</span><span class="sxs-lookup"><span data-stu-id="52535-194">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="52535-195">下列範例會使用 `For Each` 陳述式建立 `Dictionary` 集合並逐一查看字典。</span><span class="sxs-lookup"><span data-stu-id="52535-195">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
```vb  
Private Sub IterateThroughDictionary()  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    For Each kvp As KeyValuePair(Of String, Element) In elements  
        Dim theElement As Element = kvp.Value  
  
        Console.WriteLine("key: " & kvp.Key)  
        With theElement  
            Console.WriteLine("values: " & .Symbol & " " &  
                .Name & " " & .AtomicNumber)  
        End With  
    Next  
End Sub  
  
Private Function BuildDictionary() As Dictionary(Of String, Element)  
    Dim elements As New Dictionary(Of String, Element)  
  
    AddToDictionary(elements, "K", "Potassium", 19)  
    AddToDictionary(elements, "Ca", "Calcium", 20)  
    AddToDictionary(elements, "Sc", "Scandium", 21)  
    AddToDictionary(elements, "Ti", "Titanium", 22)  
  
    Return elements  
End Function  
  
Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),  
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)  
    Dim theElement As New Element  
  
    theElement.Symbol = symbol  
    theElement.Name = name  
    theElement.AtomicNumber = atomicNumber  
  
    elements.Add(Key:=theElement.Symbol, value:=theElement)  
End Sub  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <span data-ttu-id="52535-196">若要改為使用集合初始設定式建置 `Dictionary` 集合，您可以使用下列方法取代 `BuildDictionary` 和 `AddToDictionary` 方法。</span><span class="sxs-lookup"><span data-stu-id="52535-196">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
```vb  
Private Function BuildDictionary2() As Dictionary(Of String, Element)  
    Return New Dictionary(Of String, Element) From  
        {  
            {"K", New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {"Ca", New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {"Sc", New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {"Ti", New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
```  
  
 <span data-ttu-id="52535-197">下列範例會使用 <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> 方法和 `Dictionary` 的 <xref:System.Collections.Generic.Dictionary%602.Item%2A> 屬性來依索引鍵快速尋找項目。</span><span class="sxs-lookup"><span data-stu-id="52535-197">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="52535-198">`Item`屬性可讓您存取中的項目`elements`集合使用`elements(symbol)`在 Visual Basic 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="52535-198">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
```vb  
Private Sub FindInDictionary(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    If elements.ContainsKey(symbol) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Dim theElement = elements(symbol)  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
 <span data-ttu-id="52535-199">下列範例會使用 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 方法依索引鍵來快速尋找項目。</span><span class="sxs-lookup"><span data-stu-id="52535-199">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
```vb  
Private Sub FindInDictionary2(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    Dim theElement As Element = Nothing  
    If elements.TryGetValue(symbol, theElement) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
<a name="BKMK_LINQ"></a> 
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="52535-200">使用 LINQ 存取集合</span><span class="sxs-lookup"><span data-stu-id="52535-200">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="52535-201">LINQ (Language-Integrated Query (LINQ)) 可用來存取集合。</span><span class="sxs-lookup"><span data-stu-id="52535-201">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="52535-202">LINQ 查詢提供篩選、排序和分組功能。</span><span class="sxs-lookup"><span data-stu-id="52535-202">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="52535-203">如需詳細資訊，請參閱[在 Visual Basic 中撰寫 LINQ 入門](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="52535-203">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="52535-204">下列範例會對泛型 `List` 執行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="52535-204">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="52535-205">LINQ 查詢會傳回包含結果的不同集合。</span><span class="sxs-lookup"><span data-stu-id="52535-205">The LINQ query returns a different collection that contains the results.</span></span>  
  
```vb  
Private Sub ShowLINQ()  
    Dim elements As List(Of Element) = BuildList()  
  
    ' LINQ Query.  
    Dim subset = From theElement In elements  
                  Where theElement.AtomicNumber < 22  
                  Order By theElement.Name  
  
    For Each theElement In subset  
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)  
    Next  
  
    ' Output:  
    '  Calcium 20  
    '  Potassium 19  
    '  Scandium 21  
End Sub  
  
Private Function BuildList() As List(Of Element)  
    Return New List(Of Element) From  
        {  
            {New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <a name="BKMK_Sorting"></a> 
## <a name="sorting-a-collection"></a><span data-ttu-id="52535-206">為集合排序</span><span class="sxs-lookup"><span data-stu-id="52535-206">Sorting a Collection</span></span>  
 <span data-ttu-id="52535-207">下列範例說明排序集合的程序。</span><span class="sxs-lookup"><span data-stu-id="52535-207">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="52535-208">此範例排序儲存在 <xref:System.Collections.Generic.List%601> 中的 `Car` 類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="52535-208">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="52535-209">`Car` 類別實作 <xref:System.IComparable%601> 介面，而這個介面要求實作 <xref:System.IComparable%601.CompareTo%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="52535-209">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="52535-210">每次對 <xref:System.IComparable%601.CompareTo%2A> 方法的呼叫都會進行用於排序的單一比較。</span><span class="sxs-lookup"><span data-stu-id="52535-210">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="52535-211">當目前物件和另一個物件比較時，在 `CompareTo` 方法中的使用者撰寫程式碼會傳回值。</span><span class="sxs-lookup"><span data-stu-id="52535-211">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="52535-212">如果目前物件比另一個物件小則傳回的值小於零，如果目前物件比另一個物件大則傳回的值大於零，如果它們相等則傳回零。</span><span class="sxs-lookup"><span data-stu-id="52535-212">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="52535-213">這可讓您以程式碼定義大於、小於、等於的準則。</span><span class="sxs-lookup"><span data-stu-id="52535-213">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="52535-214">在 `ListCars` 方法中，`cars.Sort()` 陳述式會排序清單。</span><span class="sxs-lookup"><span data-stu-id="52535-214">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="52535-215">對 <xref:System.Collections.Generic.List%601> 之 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的這個呼叫，會導致 `CompareTo` 方法對 `List` 的 `Car` 物件自動呼叫。</span><span class="sxs-lookup"><span data-stu-id="52535-215">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
```vb  
Public Sub ListCars()  
  
    ' Create some new cars.  
    Dim cars As New List(Of Car) From  
    {  
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},  
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},  
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},  
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},  
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},  
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},  
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}  
    }  
  
    ' Sort the cars by color alphabetically, and then by speed  
    ' in descending order.  
    cars.Sort()  
  
    ' View all of the cars.  
    For Each thisCar As Car In cars  
        Console.Write(thisCar.Color.PadRight(5) & " ")  
        Console.Write(thisCar.Speed.ToString & " ")  
        Console.Write(thisCar.Name)  
        Console.WriteLine()  
    Next  
  
    ' Output:  
    '  blue  50 car4  
    '  blue  30 car5  
    '  blue  20 car1  
    '  green 50 car7  
    '  green 10 car3  
    '  red   60 car6  
    '  red   50 car2  
End Sub  
  
Public Class Car  
    Implements IComparable(Of Car)  
  
    Public Property Name As String  
    Public Property Speed As Integer  
    Public Property Color As String  
  
    Public Function CompareTo(ByVal other As Car) As Integer _  
        Implements System.IComparable(Of Car).CompareTo  
        ' A call to this method makes a single comparison that is  
        ' used for sorting.  
  
        ' Determine the relative order of the objects being compared.  
        ' Sort by color alphabetically, and then by speed in  
        ' descending order.  
  
        ' Compare the colors.  
        Dim compare As Integer  
        compare = String.Compare(Me.Color, other.Color, True)  
  
        ' If the colors are the same, compare the speeds.  
        If compare = 0 Then  
            compare = Me.Speed.CompareTo(other.Speed)  
  
            ' Use descending order for speed.  
            compare = -compare  
        End If  
  
        Return compare  
    End Function  
End Class  
```  
  
<a name="BKMK_CustomCollection"></a> 
## <a name="defining-a-custom-collection"></a><span data-ttu-id="52535-216">定義自訂集合</span><span class="sxs-lookup"><span data-stu-id="52535-216">Defining a Custom Collection</span></span>  
 <span data-ttu-id="52535-217">您可以透過實作 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Collections.IEnumerable> 介面來定義集合。</span><span class="sxs-lookup"><span data-stu-id="52535-217">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="52535-218">如需詳細資訊，請參閱[列舉集合](http://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f)。</span><span class="sxs-lookup"><span data-stu-id="52535-218">For additional information, see [Enumerating a Collection](http://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="52535-219">雖然您可以定義自訂集合，但是使用包含在 .NET Framework 中的集合 (本主題稍早在[集合的種類](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)中所述) 通常會比較好。</span><span class="sxs-lookup"><span data-stu-id="52535-219">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) earlier in this topic.</span></span>  
  
 <span data-ttu-id="52535-220">下列範例會定義名為 `AllColors` 的自訂集合類別。</span><span class="sxs-lookup"><span data-stu-id="52535-220">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="52535-221">這個類別實作 <xref:System.Collections.IEnumerable> 介面，該介面要求實作 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="52535-221">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="52535-222">`GetEnumerator` 方法會傳回 `ColorEnumerator` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="52535-222">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="52535-223">`ColorEnumerator` 實作 <xref:System.Collections.IEnumerator> 介面，而此介面會要求實作 <xref:System.Collections.IEnumerator.Current%2A> 屬性、<xref:System.Collections.IEnumerator.MoveNext%2A> 方法和 <xref:System.Collections.IEnumerator.Reset%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="52535-223">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
```vb  
Public Sub ListColors()  
    Dim colors As New AllColors()  
  
    For Each theColor As Color In colors  
        Console.Write(theColor.Name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: red blue green  
End Sub  
  
' Collection class.  
Public Class AllColors  
    Implements System.Collections.IEnumerable  
  
    Private _colors() As Color =  
    {  
        New Color With {.Name = "red"},  
        New Color With {.Name = "blue"},  
        New Color With {.Name = "green"}  
    }  
  
    Public Function GetEnumerator() As System.Collections.IEnumerator _  
        Implements System.Collections.IEnumerable.GetEnumerator  
  
        Return New ColorEnumerator(_colors)  
  
        ' Instead of creating a custom enumerator, you could  
        ' use the GetEnumerator of the array.  
        'Return _colors.GetEnumerator  
    End Function  
  
    ' Custom enumerator.  
    Private Class ColorEnumerator  
        Implements System.Collections.IEnumerator  
  
        Private _colors() As Color  
        Private _position As Integer = -1  
  
        Public Sub New(ByVal colors() As Color)  
            _colors = colors  
        End Sub  
  
        Public ReadOnly Property Current() As Object _  
            Implements System.Collections.IEnumerator.Current  
            Get  
                Return _colors(_position)  
            End Get  
        End Property  
  
        Public Function MoveNext() As Boolean _  
            Implements System.Collections.IEnumerator.MoveNext  
            _position += 1  
            Return (_position < _colors.Length)  
        End Function  
  
        Public Sub Reset() Implements System.Collections.IEnumerator.Reset  
            _position = -1  
        End Sub  
    End Class  
End Class  
  
' Element class.  
Public Class Color  
    Public Property Name As String  
End Class  
```  
  
<a name="BKMK_Iterators"></a>
##  <a name="iterators"></a><span data-ttu-id="52535-224">迭代器</span><span class="sxs-lookup"><span data-stu-id="52535-224">Iterators</span></span>  
 <span data-ttu-id="52535-225">「迭代器」是用來在集合上執行自訂反覆項目。</span><span class="sxs-lookup"><span data-stu-id="52535-225">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="52535-226">迭代器可以是方法或 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="52535-226">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="52535-227">迭代器會使用[產生](../../../visual-basic/language-reference/statements/yield-statement.md)陳述式來傳回一次一個集合的每個項目。</span><span class="sxs-lookup"><span data-stu-id="52535-227">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="52535-228">您可以使用呼叫迭代器[每個...下一步](../../../visual-basic/language-reference/statements/for-each-next-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="52535-228">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="52535-229">`For Each` 迴圈的每個反覆項目都會呼叫迭代器。</span><span class="sxs-lookup"><span data-stu-id="52535-229">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="52535-230">在迭代器中到達 `Yield` 陳述式時，會傳回運算式，並保留程式碼中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="52535-230">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="52535-231">下一次呼叫迭代器時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="52535-231">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="52535-232">如需詳細資訊，請參閱[迭代器 (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="52535-232">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="52535-233">下列範例使用了 iterator 方法。</span><span class="sxs-lookup"><span data-stu-id="52535-233">The following example uses an iterator method.</span></span> <span data-ttu-id="52535-234">Iterator 方法具有`Yield`陳述式內[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。</span><span class="sxs-lookup"><span data-stu-id="52535-234">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="52535-235">在 `ListEvenNumbers` 方法中，`For Each` 陳述式主體的每個反覆項目都會建立對 Iterator 方法的呼叫，這個方法將繼續執行下一個 `Yield` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="52535-235">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
```vb  
Public Sub ListEvenNumbers()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    Console.WriteLine()  
    ' Output: 6 8 10 12 14 16 18  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As IEnumerable(Of Integer)  
  
' Yield even numbers in the range.  
    For number = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="52535-236">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52535-236">See Also</span></span>  
 [<span data-ttu-id="52535-237">集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="52535-237">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="52535-238">程式設計概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52535-238">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="52535-239">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="52535-239">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="52535-240">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52535-240">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="52535-241">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="52535-241">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="52535-242">集合和資料結構</span><span class="sxs-lookup"><span data-stu-id="52535-242">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="52535-243">建立和操作集合</span><span class="sxs-lookup"><span data-stu-id="52535-243">Creating and Manipulating Collections</span></span>](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [<span data-ttu-id="52535-244">選取集合類別</span><span class="sxs-lookup"><span data-stu-id="52535-244">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
 [<span data-ttu-id="52535-245">在集合內比較和排序</span><span class="sxs-lookup"><span data-stu-id="52535-245">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [<span data-ttu-id="52535-246">何時使用泛型集合</span><span class="sxs-lookup"><span data-stu-id="52535-246">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
