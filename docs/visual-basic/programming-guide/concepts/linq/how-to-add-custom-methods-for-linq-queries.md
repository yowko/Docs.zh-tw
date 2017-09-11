---
title: "如何︰ 新增 LINQ 查詢 (Visual Basic) 的自訂方法 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 166eb731d41e009c374ba55f929eed302793ecd0
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="c0157-102">如何︰ 新增 LINQ 查詢 (Visual Basic) 的自訂方法</span><span class="sxs-lookup"><span data-stu-id="c0157-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>
<span data-ttu-id="c0157-103">您可以擴充一組您可以加入的擴充方法使用 LINQ 查詢的方法<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="c0157-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="c0157-104">例如，除了標準的平均值或最大作業中，您可以建立自訂的彙總方法，以計算值序列的單一值。</span><span class="sxs-lookup"><span data-stu-id="c0157-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="c0157-105">您也可以建立自訂篩選器為特定的資料轉換的值序列的運作方式，並傳回新的順序的方法。</span><span class="sxs-lookup"><span data-stu-id="c0157-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="c0157-106">這類方法的範例包括<xref:System.Linq.Enumerable.Distinct%2A>， <xref:System.Linq.Enumerable.Skip%2A>，和<xref:System.Linq.Enumerable.Reverse%2A>.</xref:System.Linq.Enumerable.Reverse%2A> </xref:System.Linq.Enumerable.Skip%2A> </xref:System.Linq.Enumerable.Distinct%2A></span><span class="sxs-lookup"><span data-stu-id="c0157-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="c0157-107">當您延伸<xref:System.Collections.Generic.IEnumerable%601>介面，您可以將自訂的方法套用至任何可列舉集合。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="c0157-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="c0157-108">如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="c0157-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="c0157-109">加入彙總的方法</span><span class="sxs-lookup"><span data-stu-id="c0157-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="c0157-110">彙總方法會計算一組值的單一值。</span><span class="sxs-lookup"><span data-stu-id="c0157-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="c0157-111">LINQ 提供數種彙總的方法，包括<xref:System.Linq.Enumerable.Average%2A>， <xref:System.Linq.Enumerable.Min%2A>，和<xref:System.Linq.Enumerable.Max%2A>.</xref:System.Linq.Enumerable.Max%2A> </xref:System.Linq.Enumerable.Min%2A> </xref:System.Linq.Enumerable.Average%2A></span><span class="sxs-lookup"><span data-stu-id="c0157-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="c0157-112">您可以藉由新增擴充方法來建立您自己的彙總方法<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="c0157-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="c0157-113">下列程式碼範例示範如何建立擴充方法呼叫`Median`來計算類型的數字序列的中位數`double`。</span><span class="sxs-lookup"><span data-stu-id="c0157-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
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
  
 <span data-ttu-id="c0157-114">任何可列舉集合呼叫此擴充方法呼叫從其他彙總方法的方式相同<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="c0157-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0157-115">在 Visual Basic 中，您可以使用方法呼叫或標準查詢語法`Aggregate`或`Group By`子句。</span><span class="sxs-lookup"><span data-stu-id="c0157-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="c0157-116">如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)和[By 子句群組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="c0157-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="c0157-117">下列程式碼範例示範如何使用`Median`方法類型的陣列`double`。</span><span class="sxs-lookup"><span data-stu-id="c0157-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
<span data-ttu-id="c0157-118"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="c0157-118"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="c0157-119"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="c0157-119"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="c0157-120">多載接受各種類型的彙總方法</span><span class="sxs-lookup"><span data-stu-id="c0157-120">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="c0157-121">您可以多載您彙總的方法，讓它可接受各種類型的序列。</span><span class="sxs-lookup"><span data-stu-id="c0157-121">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="c0157-122">標準的方法是建立每種類型的多載。</span><span class="sxs-lookup"><span data-stu-id="c0157-122">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="c0157-123">另一種方法是建立多載會採用泛型型別，並使用委派來將它轉換成特定的型別。</span><span class="sxs-lookup"><span data-stu-id="c0157-123">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="c0157-124">您也可以結合這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="c0157-124">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="c0157-125">若要建立每種類型的多載</span><span class="sxs-lookup"><span data-stu-id="c0157-125">To create an overload for each type</span></span>  
 <span data-ttu-id="c0157-126">您可以建立您想要支援每種類型的特定多載。</span><span class="sxs-lookup"><span data-stu-id="c0157-126">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="c0157-127">下列程式碼範例顯示的多載`Median`方法`integer`型別。</span><span class="sxs-lookup"><span data-stu-id="c0157-127">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
<span data-ttu-id="c0157-128"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="c0157-128"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="c0157-129">您現在可以呼叫`Median`兩個多載`integer`和`double`型別，如下列程式碼所示︰</span><span class="sxs-lookup"><span data-stu-id="c0157-129">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
<span data-ttu-id="c0157-130"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="c0157-130"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="c0157-131"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="c0157-131"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="c0157-132"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="c0157-132"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="c0157-133">若要建立泛型多載</span><span class="sxs-lookup"><span data-stu-id="c0157-133">To create a generic overload</span></span>  
 <span data-ttu-id="c0157-134">您也可以建立多載可接受的泛型物件序列。</span><span class="sxs-lookup"><span data-stu-id="c0157-134">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="c0157-135">這個多載會接受委派做為參數，並使用該物件的泛型型別序列轉換成特定的型別。</span><span class="sxs-lookup"><span data-stu-id="c0157-135">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="c0157-136">下列程式碼顯示的多載`Median`採用方法<xref:System.Func%602>委派做為參數。</xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="c0157-136">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="c0157-137">這個委派會採用泛型型別 T 的物件，並傳回型別的物件`double`。</span><span class="sxs-lookup"><span data-stu-id="c0157-137">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 <span data-ttu-id="c0157-138">您現在可以呼叫`Median`方法序列的任何類型的物件。</span><span class="sxs-lookup"><span data-stu-id="c0157-138">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="c0157-139">如果型別沒有自己的方法多載，您必須傳遞委派參數。</span><span class="sxs-lookup"><span data-stu-id="c0157-139">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="c0157-140">在 Visual Basic 中，您可以使用 lambda 運算式，針對此目的。</span><span class="sxs-lookup"><span data-stu-id="c0157-140">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="c0157-141">此外，如果您使用`Aggregate`或`Group By`子句，而不是方法呼叫，您可以傳遞任何值或運算式，這個子句會在範圍。</span><span class="sxs-lookup"><span data-stu-id="c0157-141">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="c0157-142">下列程式碼範例示範如何呼叫`Median`整數的陣列和字串陣列的方法。</span><span class="sxs-lookup"><span data-stu-id="c0157-142">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="c0157-143">字串，計算中間值的陣列中的字串長度。</span><span class="sxs-lookup"><span data-stu-id="c0157-143">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="c0157-144">此範例顯示如何傳遞<xref:System.Func%602>委派參數`Median`每個案例的方法。</xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="c0157-144">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
<span data-ttu-id="c0157-145"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="c0157-145"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="c0157-146">加入可傳回集合的方法</span><span class="sxs-lookup"><span data-stu-id="c0157-146">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="c0157-147">您可以擴充<xref:System.Collections.Generic.IEnumerable%601>介面的自訂查詢方法，傳回的值序列。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="c0157-147">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="c0157-148">在此情況下，此方法必須傳回型別<xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>集合</span><span class="sxs-lookup"><span data-stu-id="c0157-148">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="c0157-149">這種方法可用來將篩選條件或資料轉換套用至值的序列。</span><span class="sxs-lookup"><span data-stu-id="c0157-149">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="c0157-150">下列範例示範如何建立名為擴充方法`AlternateElements`傳回每個項目在集合中，從第一個項目開始。</span><span class="sxs-lookup"><span data-stu-id="c0157-150">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
<span data-ttu-id="c0157-151"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="c0157-151"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="c0157-152">您可以呼叫這個擴充方法的任何可列舉集合，就像您就可以呼叫其他方法，從<xref:System.Collections.Generic.IEnumerable%601>介面，如下列程式碼所示︰</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="c0157-152">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0157-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0157-153">See Also</span></span>  
 <span data-ttu-id="c0157-154"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="c0157-154"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="c0157-155"> [擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="c0157-155"> [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span></span>
