---
title: HOW TO：新增自訂方法的 LINQ 查詢 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: e45dfc6b516f1e5f5e9f7f667bbbfd5768330ffa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645583"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="f9230-102">HOW TO：新增自訂方法的 LINQ 查詢 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9230-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>
<span data-ttu-id="f9230-103">您可以將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，來延伸您可以用於 LINQ 查詢的方法組。</span><span class="sxs-lookup"><span data-stu-id="f9230-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="f9230-104">例如，除了標準平均值或最多作業，您可以建立自訂的彙總方法，計算一系列值的單一值。</span><span class="sxs-lookup"><span data-stu-id="f9230-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="f9230-105">您也可以建立一個方法，用為自訂篩選器或一系列值的特定資料轉換，並傳回新的序列。</span><span class="sxs-lookup"><span data-stu-id="f9230-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="f9230-106">這類方法的範例包括 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Reverse%2A>。</span><span class="sxs-lookup"><span data-stu-id="f9230-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="f9230-107">當您延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面時，可將自訂方法套用至任何可列舉的集合。</span><span class="sxs-lookup"><span data-stu-id="f9230-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="f9230-108">如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="f9230-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="f9230-109">新增彙總方法</span><span class="sxs-lookup"><span data-stu-id="f9230-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="f9230-110">彙總方法會計算一組值的單一值。</span><span class="sxs-lookup"><span data-stu-id="f9230-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="f9230-111">LINQ 提供數種彙總方法，包括 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Max%2A>。</span><span class="sxs-lookup"><span data-stu-id="f9230-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="f9230-112">您可將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，建立自己的彙總方法。</span><span class="sxs-lookup"><span data-stu-id="f9230-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="f9230-113">下列程式碼範例示範如何建立呼叫 `Median` 的擴充方法，來計算一系列類型為 `double` 的中位數。</span><span class="sxs-lookup"><span data-stu-id="f9230-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module LINQExtension  
  
    ' Extension method for the IEnumerable(of T) interface.   
    ' The method accepts only values of the Double type.  
    <Extension()>   
    Function Median(ByVal source As IEnumerable(Of Double)) As Double  
        If source.Count = 0 Then  
            Throw New InvalidOperationException("Cannot compute median for an empty set.")  
        End If  
  
        Dim sortedSource = From number In source   
                           Order By number  
  
        Dim itemIndex = sortedSource.Count \ 2  
  
        If sortedSource.Count Mod 2 = 0 Then  
            ' Even number of items in list.  
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2  
        Else  
            ' Odd number of items in list.  
            Return sortedSource(itemIndex)  
        End If  
    End Function  
End Module  
```  
  
 <span data-ttu-id="f9230-114">您可以使用從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他彙總方法同樣的方式，為任何可列舉集合呼叫此擴充方法。</span><span class="sxs-lookup"><span data-stu-id="f9230-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9230-115">在 Visual Basic 中，您可以使用方法呼叫或標準查詢語法`Aggregate`或`Group By`子句。</span><span class="sxs-lookup"><span data-stu-id="f9230-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="f9230-116">如需詳細資訊，請參閱 <<c0> [ 彙總子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)並[By 子句群組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="f9230-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="f9230-117">下列程式碼範例示範如何使用 `Median` 方法處理 `double` 類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="f9230-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
```  
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="f9230-118">多載彙總方法以接受各種類型</span><span class="sxs-lookup"><span data-stu-id="f9230-118">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="f9230-119">您可以多載自己的彙總方法，讓它接受各種類型的序列。</span><span class="sxs-lookup"><span data-stu-id="f9230-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="f9230-120">標準方法是為每種類型建立多載。</span><span class="sxs-lookup"><span data-stu-id="f9230-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="f9230-121">另一種方法是建立採用泛型型別的多載，使用委派將它轉換成特定的類型。</span><span class="sxs-lookup"><span data-stu-id="f9230-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="f9230-122">您也可以結合這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="f9230-122">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="f9230-123">為每種類型建立多載</span><span class="sxs-lookup"><span data-stu-id="f9230-123">To create an overload for each type</span></span>  
 <span data-ttu-id="f9230-124">您可以為想要支援的每種類型建立特定的多載。</span><span class="sxs-lookup"><span data-stu-id="f9230-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="f9230-125">下列程式碼範例示範適合 `integer` 類型之 `Median` 方法的多載。</span><span class="sxs-lookup"><span data-stu-id="f9230-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 <span data-ttu-id="f9230-126">您現在可以呼叫 `integer` 和 `double` 類型的 `Median` 多載，如下列程式碼所示︰</span><span class="sxs-lookup"><span data-stu-id="f9230-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
Dim numbers2() As Integer = {1, 2, 3, 4, 5}  
  
Dim query2 = Aggregate num In numbers2 Into Median()  
  
Console.WriteLine("Integer: Median = " & query2)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
' Integer: Median = 3  
```  
  
 
#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="f9230-127">建立一般多載</span><span class="sxs-lookup"><span data-stu-id="f9230-127">To create a generic overload</span></span>  
 <span data-ttu-id="f9230-128">您也可以建立接受一系列泛型物件的多載。</span><span class="sxs-lookup"><span data-stu-id="f9230-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="f9230-129">這個多載會接受委派作為參數，並使用它將泛型型別物件的序列轉換成特定的類型。</span><span class="sxs-lookup"><span data-stu-id="f9230-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="f9230-130">下列程式碼顯示 `Median` 方法的多載，接受 <xref:System.Func%602> 委派為參數。</span><span class="sxs-lookup"><span data-stu-id="f9230-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="f9230-131">這個委派會接受泛型型別 T 的物件，並傳回 `double` 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="f9230-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 <span data-ttu-id="f9230-132">您現在可以針對一系列的類型物件呼叫 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="f9230-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="f9230-133">如果類型沒有自己的方法多載，您就必須傳遞委派參數。</span><span class="sxs-lookup"><span data-stu-id="f9230-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="f9230-134">在 Visual Basic 中，您可以針對此目的使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="f9230-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="f9230-135">此外，如果您使用`Aggregate`或`Group By`子句而不是方法呼叫中的，您可以傳遞任何值或運算式，這個子句位於範圍內。</span><span class="sxs-lookup"><span data-stu-id="f9230-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="f9230-136">下列程式碼範例示範如何呼叫 `Median` 方法，處理整數陣列及字串陣列。</span><span class="sxs-lookup"><span data-stu-id="f9230-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="f9230-137">針對字串，會計算陣列字串長度的中間值。</span><span class="sxs-lookup"><span data-stu-id="f9230-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="f9230-138">此範例會示範如何將 <xref:System.Func%602> 委派參數傳遞至每個案例的 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="f9230-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
```vb  
Dim numbers3() As Integer = {1, 2, 3, 4, 5}  
  
' You can use num as a parameter for the Median method   
' so that the compiler will implicitly convert its value to double.  
' If there is no implicit conversion, the compiler will  
' display an error message.  
  
Dim query3 = Aggregate num In numbers3 Into Median(num)  
  
Console.WriteLine("Integer: Median = " & query3)  
  
Dim numbers4() As String = {"one", "two", "three", "four", "five"}  
  
' With the generic overload, you can also use numeric properties of objects.  
  
Dim query4 = Aggregate str In numbers4 Into Median(str.Length)  
  
Console.WriteLine("String: Median = " & query4)  
  
' This code produces the following output:  
'  
' Integer: Median = 3  
' String: Median = 4  
```  
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="f9230-139">新增傳回集合的方法</span><span class="sxs-lookup"><span data-stu-id="f9230-139">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="f9230-140">您可以使用傳回一系列值的自訂查詢方法來延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面。</span><span class="sxs-lookup"><span data-stu-id="f9230-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="f9230-141">在此情況下，方法必須傳回型別 <xref:System.Collections.Generic.IEnumerable%601> 的集合。</span><span class="sxs-lookup"><span data-stu-id="f9230-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f9230-142">此等方法可用來將篩選條件或資料轉換套用至一系列的值。</span><span class="sxs-lookup"><span data-stu-id="f9230-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="f9230-143">下例示範如何建立名為 `AlternateElements` 的擴充方法，傳回集合中的每隔個項目，從第一個項目開始。</span><span class="sxs-lookup"><span data-stu-id="f9230-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
```vb  
' Extension method for the IEnumerable(of T) interface.   
' The method returns every other element of a sequence.  
  
<Extension()>   
Function AlternateElements(Of T)(  
    ByVal source As IEnumerable(Of T)  
    ) As IEnumerable(Of T)  
  
    Dim list As New List(Of T)  
    Dim i = 0  
    For Each element In source  
        If (i Mod 2 = 0) Then  
            list.Add(element)  
        End If  
        i = i + 1  
    Next  
    Return list  
End Function  
```  
 <span data-ttu-id="f9230-144">您可為任何可列舉集合呼叫此擴充方法，就和您從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他方法一樣，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="f9230-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
```vb  
Dim strings() As String = {"a", "b", "c", "d", "e"}  
  
Dim query = strings.AlternateElements()  
  
For Each element In query  
    Console.WriteLine(element)  
Next  
  
' This code produces the following output:  
'  
' a  
' c  
' e  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9230-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9230-145">See also</span></span>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="f9230-146">擴充方法</span><span class="sxs-lookup"><span data-stu-id="f9230-146">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
