---
title: 如何：新增 LINQ 查詢的自訂方法 (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: cd282b4b8ee4add759070317d9dbc3f78c07abf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="a922a-102">如何：新增 LINQ 查詢的自訂方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="a922a-102">How to: Add Custom Methods for LINQ Queries (C#)</span></span>
<span data-ttu-id="a922a-103">您可以將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，來延伸您可以用於 LINQ 查詢的方法組。</span><span class="sxs-lookup"><span data-stu-id="a922a-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="a922a-104">例如，除了標準平均值或最多作業，您可以建立自訂的彙總方法，計算一系列值的單一值。</span><span class="sxs-lookup"><span data-stu-id="a922a-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="a922a-105">您也可以建立一個方法，用為自訂篩選器或一系列值的特定資料轉換，並傳回新的序列。</span><span class="sxs-lookup"><span data-stu-id="a922a-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="a922a-106">這類方法的範例包括 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Reverse%2A>。</span><span class="sxs-lookup"><span data-stu-id="a922a-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="a922a-107">當您延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面時，可將自訂方法套用至任何可列舉的集合。</span><span class="sxs-lookup"><span data-stu-id="a922a-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="a922a-108">如需詳細資訊，請參閱[擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="a922a-108">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="a922a-109">新增彙總方法</span><span class="sxs-lookup"><span data-stu-id="a922a-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="a922a-110">彙總方法會計算一組值的單一值。</span><span class="sxs-lookup"><span data-stu-id="a922a-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="a922a-111">LINQ 提供數種彙總方法，包括 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Max%2A>。</span><span class="sxs-lookup"><span data-stu-id="a922a-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="a922a-112">您可將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，建立自己的彙總方法。</span><span class="sxs-lookup"><span data-stu-id="a922a-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="a922a-113">下列程式碼範例示範如何建立呼叫 `Median` 的擴充方法，來計算一系列類型為 `double` 的中位數。</span><span class="sxs-lookup"><span data-stu-id="a922a-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
```csharp  
public static class LINQExtension  
{  
    public static double Median(this IEnumerable<double> source)  
    {  
        if (source.Count() == 0)  
        {  
            throw new InvalidOperationException("Cannot compute median for an empty set.");  
        }  
  
        var sortedList = from number in source  
                         orderby number  
                         select number;  
  
        int itemIndex = (int)sortedList.Count() / 2;  
  
        if (sortedList.Count() % 2 == 0)  
        {  
            // Even number of items.  
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;  
        }  
        else  
        {  
            // Odd number of items.  
            return sortedList.ElementAt(itemIndex);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a922a-114">您可以使用從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他彙總方法同樣的方式，為任何可列舉集合呼叫此擴充方法。</span><span class="sxs-lookup"><span data-stu-id="a922a-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="a922a-115">下列程式碼範例示範如何使用 `Median` 方法處理 `double` 類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="a922a-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
```csharp  
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };  
  
var query1 = numbers1.Median();  
  
Console.WriteLine("double: Median = " + query1);  
```  

```csharp  
/*  
 This code produces the following output:  
  
 Double: Median = 4.85  
*/  
```  
  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="a922a-116">多載彙總方法以接受各種類型</span><span class="sxs-lookup"><span data-stu-id="a922a-116">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="a922a-117">您可以多載自己的彙總方法，讓它接受各種類型的序列。</span><span class="sxs-lookup"><span data-stu-id="a922a-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="a922a-118">標準方法是為每種類型建立多載。</span><span class="sxs-lookup"><span data-stu-id="a922a-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="a922a-119">另一種方法是建立採用泛型型別的多載，使用委派將它轉換成特定的類型。</span><span class="sxs-lookup"><span data-stu-id="a922a-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="a922a-120">您也可以結合這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="a922a-120">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="a922a-121">為每種類型建立多載</span><span class="sxs-lookup"><span data-stu-id="a922a-121">To create an overload for each type</span></span>  
 <span data-ttu-id="a922a-122">您可以為想要支援的每種類型建立特定的多載。</span><span class="sxs-lookup"><span data-stu-id="a922a-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="a922a-123">下列程式碼範例示範適合 `integer` 類型之 `Median` 方法的多載。</span><span class="sxs-lookup"><span data-stu-id="a922a-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
```csharp  
//int overload  
  
public static double Median(this IEnumerable<int> source)  
{  
    return (from num in source select (double)num).Median();  
}  
```   
 <span data-ttu-id="a922a-124">您現在可以呼叫 `integer` 和 `double` 類型的 `Median` 多載，如下列程式碼所示︰</span><span class="sxs-lookup"><span data-stu-id="a922a-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
```csharp  
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };  
  
var query1 = numbers1.Median();  
  
Console.WriteLine("double: Median = " + query1);  
```  
  
```csharp  
int[] numbers2 = { 1, 2, 3, 4, 5 };  
  
var query2 = numbers2.Median();  
  
Console.WriteLine("int: Median = " + query2);  
```  
  
```csharp  
/*  
 This code produces the following output:  
  
 Double: Median = 4.85  
 Integer: Median = 3  
*/  
```  

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="a922a-125">建立一般多載</span><span class="sxs-lookup"><span data-stu-id="a922a-125">To create a generic overload</span></span>  
 <span data-ttu-id="a922a-126">您也可以建立接受一系列泛型物件的多載。</span><span class="sxs-lookup"><span data-stu-id="a922a-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="a922a-127">這個多載會接受委派作為參數，並使用它將泛型型別物件的序列轉換成特定的類型。</span><span class="sxs-lookup"><span data-stu-id="a922a-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="a922a-128">下列程式碼顯示 `Median` 方法的多載，接受 <xref:System.Func%602> 委派為參數。</span><span class="sxs-lookup"><span data-stu-id="a922a-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="a922a-129">這個委派會接受泛型型別 T 的物件，並傳回 `double` 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="a922a-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```csharp  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 <span data-ttu-id="a922a-130">您現在可以針對一系列的類型物件呼叫 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="a922a-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="a922a-131">如果類型沒有自己的方法多載，您就必須傳遞委派參數。</span><span class="sxs-lookup"><span data-stu-id="a922a-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="a922a-132">在 C# 中，您可以針對此目的使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="a922a-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="a922a-133">另僅限 Visual Basic，如果您使用 `Aggregate` 或 `Group By` 子句而不是方法呼叫，您可以傳遞此子句範圍內的任何值或運算式。</span><span class="sxs-lookup"><span data-stu-id="a922a-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="a922a-134">下列程式碼範例示範如何呼叫 `Median` 方法，處理整數陣列及字串陣列。</span><span class="sxs-lookup"><span data-stu-id="a922a-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="a922a-135">針對字串，會計算陣列字串長度的中間值。</span><span class="sxs-lookup"><span data-stu-id="a922a-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="a922a-136">此範例會示範如何將 <xref:System.Func%602> 委派參數傳遞至每個案例的 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="a922a-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
```csharp  
int[] numbers3 = { 1, 2, 3, 4, 5 };  
  
/*   
  You can use the num=>num lambda expression as a parameter for the Median method   
  so that the compiler will implicitly convert its value to double.  
  If there is no implicit conversion, the compiler will display an error message.            
*/  
  
var query3 = numbers3.Median(num => num);  
  
Console.WriteLine("int: Median = " + query3);  
  
string[] numbers4 = { "one", "two", "three", "four", "five" };  
  
// With the generic overload, you can also use numeric properties of objects.  
  
var query4 = numbers4.Median(str => str.Length);  
  
Console.WriteLine("String: Median = " + query4);  
  
/*  
 This code produces the following output:  
  
 Integer: Median = 3  
 String: Median = 4  
*/  
```   
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="a922a-137">新增傳回集合的方法</span><span class="sxs-lookup"><span data-stu-id="a922a-137">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="a922a-138">您可以使用傳回一系列值的自訂查詢方法來延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面。</span><span class="sxs-lookup"><span data-stu-id="a922a-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="a922a-139">在此情況下，方法必須傳回型別 <xref:System.Collections.Generic.IEnumerable%601> 的集合。</span><span class="sxs-lookup"><span data-stu-id="a922a-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="a922a-140">此等方法可用來將篩選條件或資料轉換套用至一系列的值。</span><span class="sxs-lookup"><span data-stu-id="a922a-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="a922a-141">下例示範如何建立名為 `AlternateElements` 的擴充方法，傳回集合中的每隔個項目，從第一個項目開始。</span><span class="sxs-lookup"><span data-stu-id="a922a-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
```csharp  
// Extension method for the IEnumerable<T> interface.   
// The method returns every other element of a sequence.  
  
public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)  
{  
    List<T> list = new List<T>();  
  
    int i = 0;  
  
    foreach (var element in source)  
    {  
        if (i % 2 == 0)  
        {  
            list.Add(element);  
        }  
  
        i++;  
    }  
  
    return list;  
}  
```  
 <span data-ttu-id="a922a-142">您可為任何可列舉集合呼叫此擴充方法，就和您從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他方法一樣，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="a922a-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
```csharp  
string[] strings = { "a", "b", "c", "d", "e" };  
  
var query = strings.AlternateElements();  
  
foreach (var element in query)  
{  
    Console.WriteLine(element);  
}  
/*  
 This code produces the following output:  
  
 a  
 c  
 e  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="a922a-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="a922a-143">See Also</span></span>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="a922a-144">擴充方法</span><span class="sxs-lookup"><span data-stu-id="a922a-144">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
