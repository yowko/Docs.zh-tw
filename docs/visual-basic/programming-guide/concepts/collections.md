---
title: "集合 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b3c8de3e22075d576f86bcd4eb599946740ebe16
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="collections-visual-basic"></a><span data-ttu-id="52400-102">集合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52400-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="52400-103">在許多應用程式中，您想要建立和管理相關物件的群組。</span><span class="sxs-lookup"><span data-stu-id="52400-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="52400-104">有兩種方式可以群組物件：建立物件的陣列和建立物件的集合。</span><span class="sxs-lookup"><span data-stu-id="52400-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="52400-105">陣列是最適用於建立和處理固定數目的強類型物件。</span><span class="sxs-lookup"><span data-stu-id="52400-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="52400-106">如需陣列的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="52400-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="52400-107">集合會提供較具彈性的方式來使用物件群組。</span><span class="sxs-lookup"><span data-stu-id="52400-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="52400-108">與陣列不同的是，您使用的物件群組可依程式變更的需要來動態增減。</span><span class="sxs-lookup"><span data-stu-id="52400-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="52400-109">對於某些集合，您可以將鍵值指派給您放入集合的任何物件，讓您可以藉由使用鍵值快速擷取物件。</span><span class="sxs-lookup"><span data-stu-id="52400-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="52400-110">集合是類別，因此您必須在將項目加入該集合之前，宣告類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="52400-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="52400-111">如果您的集合包含一個資料類型的項目，您可以使用其中一個類別中<xref:System.Collections.Generic?displayProperty=fullName>命名空間。</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="52400-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="52400-112">泛型集合會強制類型安全，如此就不會加入其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="52400-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="52400-113">當您從泛型集合中擷取項目時，並不需要判斷其資料類型或將其轉換。</span><span class="sxs-lookup"><span data-stu-id="52400-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52400-114">如需本主題的範例，包括[匯入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)陳述式`System.Collections.Generic`和`System.Linq`命名空間。</span><span class="sxs-lookup"><span data-stu-id="52400-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="52400-115">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="52400-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="52400-116">使用簡單的集合</span><span class="sxs-lookup"><span data-stu-id="52400-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="52400-117">類型的集合</span><span class="sxs-lookup"><span data-stu-id="52400-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="52400-118">System.Collections.Generic 類別</span><span class="sxs-lookup"><span data-stu-id="52400-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="52400-119">System.Collections.Concurrent 類別</span><span class="sxs-lookup"><span data-stu-id="52400-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="52400-120">System.Collections 類別</span><span class="sxs-lookup"><span data-stu-id="52400-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="52400-121">Visual Basic 的集合類別</span><span class="sxs-lookup"><span data-stu-id="52400-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="52400-122">實作索引鍵/值組的集合</span><span class="sxs-lookup"><span data-stu-id="52400-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="52400-123">使用 LINQ 來存取集合</span><span class="sxs-lookup"><span data-stu-id="52400-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="52400-124">為集合排序</span><span class="sxs-lookup"><span data-stu-id="52400-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="52400-125">定義自訂的集合</span><span class="sxs-lookup"><span data-stu-id="52400-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="52400-126">迭代器</span><span class="sxs-lookup"><span data-stu-id="52400-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="52400-127">使用簡單的集合</span><span class="sxs-lookup"><span data-stu-id="52400-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="52400-128">本章節中的範例使用泛型<xref:System.Collections.Generic.List%601>類別，讓您使用強型別物件的清單。</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="52400-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="52400-129">下列範例會建立一份字串，並接著逐一字串使用[每個...下一步](../../../visual-basic/language-reference/statements/for-each-next-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="52400-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
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
  
 <span data-ttu-id="52400-130">如果事先已知集合的內容，您可以使用*集合初始設定式*來初始化集合。</span><span class="sxs-lookup"><span data-stu-id="52400-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="52400-131">如需詳細資訊，請參閱[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="52400-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="52400-132">下列範例與前一個範例相同，但有一點除外，就是集合初始設定式是用來將項目加入集合中。</span><span class="sxs-lookup"><span data-stu-id="52400-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
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
  
 <span data-ttu-id="52400-133">您可以使用[的...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)陳述式來取代`For Each`陳述式來逐一查看集合。</span><span class="sxs-lookup"><span data-stu-id="52400-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="52400-134">您可以藉由依索引位置存取集合項目來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="52400-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="52400-135">項目的索引以 0 開始，並以項目計數減 1 結束。</span><span class="sxs-lookup"><span data-stu-id="52400-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="52400-136">下列範例逐一查看集合的項目使用`For…Next`而不是`For Each`。</span><span class="sxs-lookup"><span data-stu-id="52400-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="52400-137">下列範例透過指定要移除的物件，從集合中移除項目。</span><span class="sxs-lookup"><span data-stu-id="52400-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
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
  
 <span data-ttu-id="52400-138">下列範例會移除泛型清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="52400-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="52400-139">而不是`For Each`陳述式，[的...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)會以遞減的順序逐一查看的陳述式。</span><span class="sxs-lookup"><span data-stu-id="52400-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="52400-140">這是因為<xref:System.Collections.Generic.List%601.RemoveAt%2A>方法會移除的項目有較低的索引值後面的項目。</xref:System.Collections.Generic.List%601.RemoveAt%2A></span><span class="sxs-lookup"><span data-stu-id="52400-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
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
  
 <span data-ttu-id="52400-141">類型的項目中<xref:System.Collections.Generic.List%601>，您也可以定義自己的類別。</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="52400-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="52400-142">在下列範例中，`Galaxy`類別，可由<xref:System.Collections.Generic.List%601>定義程式碼中。</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="52400-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
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
## <a name="kinds-of-collections"></a><span data-ttu-id="52400-143">集合的種類</span><span class="sxs-lookup"><span data-stu-id="52400-143">Kinds of Collections</span></span>   
 <span data-ttu-id="52400-144">.NET Framework 會提供很多常見的集合。</span><span class="sxs-lookup"><span data-stu-id="52400-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="52400-145">各個類型的集合都是針對特定用途來設計。</span><span class="sxs-lookup"><span data-stu-id="52400-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="52400-146">下列集合類別的群組將在本節介紹：</span><span class="sxs-lookup"><span data-stu-id="52400-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="52400-147">@System.Collections.Generic類別</span><span class="sxs-lookup"><span data-stu-id="52400-147">@System.Collections.Generic classes</span></span>  
  
-   <span data-ttu-id="52400-148">@System.Collections.Concurrent類別</span><span class="sxs-lookup"><span data-stu-id="52400-148">@System.Collections.Concurrent classes</span></span>  
  
-   <span data-ttu-id="52400-149">@System.Collections類別</span><span class="sxs-lookup"><span data-stu-id="52400-149">@System.Collections classes</span></span>  
  
-   <span data-ttu-id="52400-150">Visual Basic`Collection`類別</span><span class="sxs-lookup"><span data-stu-id="52400-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="52400-151">System.Collections.Generic 類別</span><span class="sxs-lookup"><span data-stu-id="52400-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="52400-152">您可以使用其中一個類別中，以建立泛型集合<xref:System.Collections.Generic>命名空間。</xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="52400-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="52400-153">當集合中每個項目的資料類型相同時，泛型集合就相當有用。</span><span class="sxs-lookup"><span data-stu-id="52400-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="52400-154">泛型集合會透過只允許加入所需資料類型的方式，強制使用強式類型。</span><span class="sxs-lookup"><span data-stu-id="52400-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="52400-155">下表列出部分常用的類別<xref:System.Collections.Generic?displayProperty=fullName>命名空間︰</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="52400-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="52400-156">類別</span><span class="sxs-lookup"><span data-stu-id="52400-156">Class</span></span>|<span data-ttu-id="52400-157">描述</span><span class="sxs-lookup"><span data-stu-id="52400-157">Description</span></span>|  
|---|---|  
|<span data-ttu-id="52400-158"><xref:System.Collections.Generic.Dictionary%602></xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="52400-158"><xref:System.Collections.Generic.Dictionary%602></span></span>|<span data-ttu-id="52400-159">表示根據索引鍵所整理的索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="52400-159">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<span data-ttu-id="52400-160"><xref:System.Collections.Generic.List%601></xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="52400-160"><xref:System.Collections.Generic.List%601></span></span>|<span data-ttu-id="52400-161">表示可以依照索引存取的物件清單。</span><span class="sxs-lookup"><span data-stu-id="52400-161">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="52400-162">提供搜尋、排序和修改清單的方法。</span><span class="sxs-lookup"><span data-stu-id="52400-162">Provides methods to search, sort, and modify lists.</span></span>|  
|<span data-ttu-id="52400-163"><xref:System.Collections.Generic.Queue%601></xref:System.Collections.Generic.Queue%601></span><span class="sxs-lookup"><span data-stu-id="52400-163"><xref:System.Collections.Generic.Queue%601></span></span>|<span data-ttu-id="52400-164">表示物件的先進先出 (FIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="52400-164">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<span data-ttu-id="52400-165"><xref:System.Collections.Generic.SortedList%602></xref:System.Collections.Generic.SortedList%602></span><span class="sxs-lookup"><span data-stu-id="52400-165"><xref:System.Collections.Generic.SortedList%602></span></span>|<span data-ttu-id="52400-166">代表根據關聯索引鍵所排序的索引鍵/值組的集合<xref:System.Collections.Generic.IComparer%601>實作。</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="52400-166">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<span data-ttu-id="52400-167"><xref:System.Collections.Generic.Stack%601></xref:System.Collections.Generic.Stack%601></span><span class="sxs-lookup"><span data-stu-id="52400-167"><xref:System.Collections.Generic.Stack%601></span></span>|<span data-ttu-id="52400-168">表示物件的後進先出 (LIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="52400-168">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="52400-169">如需詳細資訊，請參閱[常用的集合類型](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55)，[選取集合類別](../../../standard/collections/selecting-a-collection-class.md)，和<xref:System.Collections.Generic?displayProperty=fullName>.</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="52400-169">For additional information, see [Commonly Used Collection Types](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=fullName>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="52400-170">System.Collections.Concurrent 類別</span><span class="sxs-lookup"><span data-stu-id="52400-170">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="52400-171">在.NET Framework 4 或更新版本中，在集合<xref:System.Collections.Concurrent>命名空間提供了有效率的安全執行緒作業，從多個執行緒存取集合項目。</xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="52400-171">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="52400-172">中的類別<xref:System.Collections.Concurrent>應該使用命名空間，而不是在對應的型別<xref:System.Collections.Generic?displayProperty=fullName>和<xref:System.Collections?displayProperty=fullName>每當多個執行緒同時存取集合的命名空間。</xref:System.Collections?displayProperty=fullName> </xref:System.Collections.Generic?displayProperty=fullName> </xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="52400-172">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=fullName> and <xref:System.Collections?displayProperty=fullName> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="52400-173">如需詳細資訊，請參閱[安全執行緒集合](../../../standard/collections/threadsafe/index.md)和<xref:System.Collections.Concurrent>.</xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="52400-173">For more information, see [Thread-Safe Collections](../../../standard/collections/threadsafe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="52400-174">中包含一些類別<xref:System.Collections.Concurrent>命名空間是<xref:System.Collections.Concurrent.BlockingCollection%601>， <xref:System.Collections.Concurrent.ConcurrentDictionary%602>， <xref:System.Collections.Concurrent.ConcurrentQueue%601>，和<xref:System.Collections.Concurrent.ConcurrentStack%601>.</xref:System.Collections.Concurrent.ConcurrentStack%601> </xref:System.Collections.Concurrent.ConcurrentQueue%601> </xref:System.Collections.Concurrent.ConcurrentDictionary%602> </xref:System.Collections.Concurrent.BlockingCollection%601> </xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="52400-174">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="52400-175">System.Collections 類別</span><span class="sxs-lookup"><span data-stu-id="52400-175">System.Collections Classes</span></span>    
 <span data-ttu-id="52400-176">中的類別<xref:System.Collections?displayProperty=fullName>命名空間不會儲存項目做特別型別的物件，而物件的型別`Object`。</xref:System.Collections?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="52400-176">The classes in the <xref:System.Collections?displayProperty=fullName> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="52400-177">可能的話，您應該使用中的泛型集合<xref:System.Collections.Generic?displayProperty=fullName>命名空間或<xref:System.Collections.Concurrent>命名空間，而不是在舊版的型別`System.Collections`命名空間。</xref:System.Collections.Concurrent> </xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="52400-177">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=fullName> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="52400-178">下表列出部分常用的類別中`System.Collections`命名空間︰</span><span class="sxs-lookup"><span data-stu-id="52400-178">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="52400-179">類別</span><span class="sxs-lookup"><span data-stu-id="52400-179">Class</span></span>|<span data-ttu-id="52400-180">描述</span><span class="sxs-lookup"><span data-stu-id="52400-180">Description</span></span>|  
|---|---|  
|<span data-ttu-id="52400-181"><xref:System.Collections.ArrayList></xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="52400-181"><xref:System.Collections.ArrayList></span></span>|<span data-ttu-id="52400-182">代表會視需要動態增加大小的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="52400-182">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<span data-ttu-id="52400-183"><xref:System.Collections.Hashtable></xref:System.Collections.Hashtable></span><span class="sxs-lookup"><span data-stu-id="52400-183"><xref:System.Collections.Hashtable></span></span>|<span data-ttu-id="52400-184">代表根據索引鍵的雜湊程式碼，所整理的索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="52400-184">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<span data-ttu-id="52400-185"><xref:System.Collections.Queue></xref:System.Collections.Queue></span><span class="sxs-lookup"><span data-stu-id="52400-185"><xref:System.Collections.Queue></span></span>|<span data-ttu-id="52400-186">表示物件的先進先出 (FIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="52400-186">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<span data-ttu-id="52400-187"><xref:System.Collections.Stack></xref:System.Collections.Stack></span><span class="sxs-lookup"><span data-stu-id="52400-187"><xref:System.Collections.Stack></span></span>|<span data-ttu-id="52400-188">表示物件的後進先出 (LIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="52400-188">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="52400-189"><xref:System.Collections.Specialized>命名空間提供特製化和強型別集合類別，例如字串集合和連結清單和混合式的字典。</xref:System.Collections.Specialized></span><span class="sxs-lookup"><span data-stu-id="52400-189">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="52400-190">Visual Basic Collection 類別</span><span class="sxs-lookup"><span data-stu-id="52400-190">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="52400-191">您可以使用 Visual Basic<xref:Microsoft.VisualBasic.Collection>類別，即可存取集合項目使用的數字索引或`String`索引鍵。</xref:Microsoft.VisualBasic.Collection></span><span class="sxs-lookup"><span data-stu-id="52400-191">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="52400-192">不論是否指定索引鍵，您都可以在集合物件中加入項目。</span><span class="sxs-lookup"><span data-stu-id="52400-192">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="52400-193">如果加入不具索引鍵的項目，則必須使用它的數值索引加以存取。</span><span class="sxs-lookup"><span data-stu-id="52400-193">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="52400-194">Visual Basic`Collection`類別會以型別來儲存其所有項目`Object`，所以您可以新增任何資料類型的項目。</span><span class="sxs-lookup"><span data-stu-id="52400-194">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="52400-195">無法確定加入的資料類型皆適當無誤。</span><span class="sxs-lookup"><span data-stu-id="52400-195">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="52400-196">當您使用 Visual Basic`Collection`類別，在集合中的第一個項目具有其索引為 1。</span><span class="sxs-lookup"><span data-stu-id="52400-196">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="52400-197">這與 .NET Framework 集合類別不同，後者的起始索引為 0。</span><span class="sxs-lookup"><span data-stu-id="52400-197">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="52400-198">可能的話，您應該使用中的泛型集合<xref:System.Collections.Generic?displayProperty=fullName>命名空間或<xref:System.Collections.Concurrent>命名空間，而不是 Visual Basic`Collection`類別</xref:System.Collections.Concurrent></xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="52400-198">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=fullName> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="52400-199">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Collection>。</xref:Microsoft.VisualBasic.Collection></span><span class="sxs-lookup"><span data-stu-id="52400-199">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="52400-200">實作索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="52400-200">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="52400-201"><xref:System.Collections.Generic.Dictionary%602>泛型集合可讓您使用每個項目的索引鍵來存取集合中的項目。</xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="52400-201">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="52400-202">加入字典中的每一個項目都是由值及其關聯索引鍵所組成。</span><span class="sxs-lookup"><span data-stu-id="52400-202">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="52400-203">擷取使用它的索引鍵的值是快速，因為`Dictionary`類別會實作為雜湊表。</span><span class="sxs-lookup"><span data-stu-id="52400-203">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="52400-204">下列範例會建立`Dictionary`集合，逐一查看字典使用`For Each`陳述式。</span><span class="sxs-lookup"><span data-stu-id="52400-204">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
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
  
 <span data-ttu-id="52400-205">若要改用集合初始設定式，以建立`Dictionary`集合中，您可以取代`BuildDictionary`和`AddToDictionary`方法，使用下列方法。</span><span class="sxs-lookup"><span data-stu-id="52400-205">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
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
  
 <span data-ttu-id="52400-206">下列範例會使用<xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>方法和<xref:System.Collections.Generic.Dictionary%602.Item%2A>屬性`Dictionary`快速尋找項目索引鍵。</xref:System.Collections.Generic.Dictionary%602.Item%2A> </xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A></span><span class="sxs-lookup"><span data-stu-id="52400-206">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="52400-207">`Item`屬性可讓您存取中的項目`elements`集合使用`elements(symbol)`在 Visual Basic 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="52400-207">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
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
  
 <span data-ttu-id="52400-208">下列範例會改為使用<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>方法快速尋找項目索引鍵。</xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A></span><span class="sxs-lookup"><span data-stu-id="52400-208">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
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
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="52400-209">使用 LINQ 存取集合</span><span class="sxs-lookup"><span data-stu-id="52400-209">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="52400-210">LINQ (Language-Integrated Query (LINQ)) 可用來存取集合。</span><span class="sxs-lookup"><span data-stu-id="52400-210">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="52400-211">LINQ 查詢提供篩選、排序和分組功能。</span><span class="sxs-lookup"><span data-stu-id="52400-211">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="52400-212">如需詳細資訊，請參閱[在 Visual Basic 中撰寫 LINQ 入門](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="52400-212">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="52400-213">下列範例會執行 LINQ 查詢，針對泛型`List`。</span><span class="sxs-lookup"><span data-stu-id="52400-213">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="52400-214">LINQ 查詢會傳回包含結果的不同集合。</span><span class="sxs-lookup"><span data-stu-id="52400-214">The LINQ query returns a different collection that contains the results.</span></span>  
  
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
## <a name="sorting-a-collection"></a><span data-ttu-id="52400-215">為集合排序</span><span class="sxs-lookup"><span data-stu-id="52400-215">Sorting a Collection</span></span>  
 <span data-ttu-id="52400-216">下列範例說明排序集合的程序。</span><span class="sxs-lookup"><span data-stu-id="52400-216">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="52400-217">此範例來排序的執行個體`Car` <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601>中儲存的類別</span><span class="sxs-lookup"><span data-stu-id="52400-217">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="52400-218">`Car`類別會實作<xref:System.IComparable%601>介面，需要<xref:System.IComparable%601.CompareTo%2A>實作方法。</xref:System.IComparable%601.CompareTo%2A> </xref:System.IComparable%601></span><span class="sxs-lookup"><span data-stu-id="52400-218">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="52400-219">每次呼叫<xref:System.IComparable%601.CompareTo%2A>方法會讓您用來排序的單一比較。</xref:System.IComparable%601.CompareTo%2A></span><span class="sxs-lookup"><span data-stu-id="52400-219">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="52400-220">使用者撰寫的程式碼`CompareTo`方法會傳回目前物件與另一個物件的每個比較的值。</span><span class="sxs-lookup"><span data-stu-id="52400-220">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="52400-221">如果目前物件比另一個物件小則傳回的值小於零，如果目前物件比另一個物件大則傳回的值大於零，如果它們相等則傳回零。</span><span class="sxs-lookup"><span data-stu-id="52400-221">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="52400-222">這可讓您以程式碼定義大於、小於、等於的準則。</span><span class="sxs-lookup"><span data-stu-id="52400-222">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="52400-223">在`ListCars`方法，`cars.Sort()`陳述式會將清單排序。</span><span class="sxs-lookup"><span data-stu-id="52400-223">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="52400-224">這個呼叫<xref:System.Collections.Generic.List%601.Sort%2A>方法<xref:System.Collections.Generic.List%601>造成`CompareTo`自動呼叫的方法`Car`物件`List`。</xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.List%601.Sort%2A></span><span class="sxs-lookup"><span data-stu-id="52400-224">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
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
## <a name="defining-a-custom-collection"></a><span data-ttu-id="52400-225">定義自訂集合</span><span class="sxs-lookup"><span data-stu-id="52400-225">Defining a Custom Collection</span></span>  
 <span data-ttu-id="52400-226">您可以藉由實作定義集合<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Collections.IEnumerable>介面。</xref:System.Collections.IEnumerable> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="52400-226">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="52400-227">如需詳細資訊，請參閱[列舉集合](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f)。</span><span class="sxs-lookup"><span data-stu-id="52400-227">For additional information, see [Enumerating a Collection](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="52400-228">雖然您可以定義自訂的集合，通常最好改為使用隨附於.NET Framework 中，如下所述的集合是[類型的集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)本主題前面的。</span><span class="sxs-lookup"><span data-stu-id="52400-228">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) earlier in this topic.</span></span>  
  
 <span data-ttu-id="52400-229">下列範例會定義自訂集合類別，名為`AllColors`。</span><span class="sxs-lookup"><span data-stu-id="52400-229">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="52400-230">這個類別會實作<xref:System.Collections.IEnumerable>介面，需要<xref:System.Collections.IEnumerable.GetEnumerator%2A>實作方法。</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="52400-230">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="52400-231">`GetEnumerator`方法傳回的執行個體`ColorEnumerator`類別。</span><span class="sxs-lookup"><span data-stu-id="52400-231">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="52400-232">`ColorEnumerator`實作<xref:System.Collections.IEnumerator>介面，需要<xref:System.Collections.IEnumerator.Current%2A>屬性，<xref:System.Collections.IEnumerator.MoveNext%2A>方法，和<xref:System.Collections.IEnumerator.Reset%2A>實作方法。</xref:System.Collections.IEnumerator.Reset%2A> </xref:System.Collections.IEnumerator.MoveNext%2A> </xref:System.Collections.IEnumerator.Current%2A> </xref:System.Collections.IEnumerator></span><span class="sxs-lookup"><span data-stu-id="52400-232">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
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
##  <a name="iterators"></a><span data-ttu-id="52400-233">Iterator</span><span class="sxs-lookup"><span data-stu-id="52400-233">Iterators</span></span>  
 <span data-ttu-id="52400-234">*迭代器*用來對集合執行自訂的反覆項目。</span><span class="sxs-lookup"><span data-stu-id="52400-234">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="52400-235">迭代器可以是一種方法或`get`存取子。</span><span class="sxs-lookup"><span data-stu-id="52400-235">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="52400-236">迭代器會使用[產生](../../../visual-basic/language-reference/statements/yield-statement.md)陳述式來傳回每個項目一次一個的集合。</span><span class="sxs-lookup"><span data-stu-id="52400-236">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="52400-237">您可以使用呼叫迭代器[每個...下一步](../../../visual-basic/language-reference/statements/for-each-next-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="52400-237">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="52400-238">每個反覆項目`For Each`迴圈就會呼叫迭代器。</span><span class="sxs-lookup"><span data-stu-id="52400-238">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="52400-239">當`Yield`陳述式為止迭代器、 運算式會傳回，而且保留在程式碼中目前的位置。</span><span class="sxs-lookup"><span data-stu-id="52400-239">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="52400-240">下一次呼叫迭代器時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="52400-240">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="52400-241">如需詳細資訊，請參閱[Iterator (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="52400-241">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="52400-242">下列範例使用了 iterator 方法。</span><span class="sxs-lookup"><span data-stu-id="52400-242">The following example uses an iterator method.</span></span> <span data-ttu-id="52400-243">Iterator 方法具有`Yield`陳述式內[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。</span><span class="sxs-lookup"><span data-stu-id="52400-243">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="52400-244">在`ListEvenNumbers`方法中，每個反覆項目`For Each`陳述式主體會建立呼叫 iterator 方法繼續進行下一個`Yield`陳述式。</span><span class="sxs-lookup"><span data-stu-id="52400-244">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52400-245">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52400-245">See Also</span></span>  
 <span data-ttu-id="52400-246">[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md) </span><span class="sxs-lookup"><span data-stu-id="52400-246">[Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md) </span></span>  
<span data-ttu-id="52400-247"> [程式設計概念 (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="52400-247"> [Programming Concepts (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="52400-248"> [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="52400-248"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="52400-249"> [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="52400-249"> [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="52400-250"> [平行 LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455) </span><span class="sxs-lookup"><span data-stu-id="52400-250"> [Parallel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455) </span></span>  
<span data-ttu-id="52400-251"> [集合和資料結構](../../../standard/collections/index.md) </span><span class="sxs-lookup"><span data-stu-id="52400-251"> [Collections and Data Structures](../../../standard/collections/index.md) </span></span>  
<span data-ttu-id="52400-252"> [建立和操作集合](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069) </span><span class="sxs-lookup"><span data-stu-id="52400-252"> [Creating and Manipulating Collections](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069) </span></span>  
<span data-ttu-id="52400-253"> [選取集合類別](../../../standard/collections/selecting-a-collection-class.md) </span><span class="sxs-lookup"><span data-stu-id="52400-253"> [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md) </span></span>  
<span data-ttu-id="52400-254"> [集合內比較和排序](../../../standard/collections/comparisons-and-sorts-within-collections.md) </span><span class="sxs-lookup"><span data-stu-id="52400-254"> [Comparisons and Sorts Within Collections](../../../standard/collections/comparisons-and-sorts-within-collections.md) </span></span>  
<span data-ttu-id="52400-255"> [何時使用泛型集合](../../../standard/collections/when-to-use-generic-collections.md)</span><span class="sxs-lookup"><span data-stu-id="52400-255"> [When to Use Generic Collections](../../../standard/collections/when-to-use-generic-collections.md)</span></span>
