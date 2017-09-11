---
title: "投影作業 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 529d6c4c3a85ec78d3b6804518dbc8973921e195
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="projection-operations-c"></a><span data-ttu-id="e42a7-102">投影作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e42a7-102">Projection Operations (C#)</span></span>
<span data-ttu-id="e42a7-103">投影是指將物件轉換成新形式的作業，而這個形式通常僅包含後續即將使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="e42a7-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="e42a7-104">透過使用投影，您可以建構根據每個物件所建立的新型別。</span><span class="sxs-lookup"><span data-stu-id="e42a7-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="e42a7-105">您可以投影屬性並對其執行數學函式。</span><span class="sxs-lookup"><span data-stu-id="e42a7-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="e42a7-106">您也可以投影原始物件，而不進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="e42a7-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="e42a7-107">執行投影的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="e42a7-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e42a7-108">方法</span><span class="sxs-lookup"><span data-stu-id="e42a7-108">Methods</span></span>  
  
|<span data-ttu-id="e42a7-109">方法名稱</span><span class="sxs-lookup"><span data-stu-id="e42a7-109">Method Name</span></span>|<span data-ttu-id="e42a7-110">描述</span><span class="sxs-lookup"><span data-stu-id="e42a7-110">Description</span></span>|<span data-ttu-id="e42a7-111">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="e42a7-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="e42a7-112">更多資訊</span><span class="sxs-lookup"><span data-stu-id="e42a7-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="e42a7-113">選取</span><span class="sxs-lookup"><span data-stu-id="e42a7-113">Select</span></span>|<span data-ttu-id="e42a7-114">投影以轉換函式為基礎的值。</span><span class="sxs-lookup"><span data-stu-id="e42a7-114">Projects values that are based on a transform function.</span></span>|`select`|<span data-ttu-id="e42a7-115"><xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="e42a7-115"><xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="e42a7-116"><xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="e42a7-116"><xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="e42a7-117">SelectMany</span><span class="sxs-lookup"><span data-stu-id="e42a7-117">SelectMany</span></span>|<span data-ttu-id="e42a7-118">投影一連串以轉換函式為基礎的值，然後將這些值壓平合併成一個序列。</span><span class="sxs-lookup"><span data-stu-id="e42a7-118">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="e42a7-119">使用多個 `from` 子句</span><span class="sxs-lookup"><span data-stu-id="e42a7-119">Use multiple `from` clauses</span></span>|<span data-ttu-id="e42a7-120"><xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="e42a7-120"><xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="e42a7-121"><xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="e42a7-121"><xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="e42a7-122">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="e42a7-122">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="e42a7-123">選取</span><span class="sxs-lookup"><span data-stu-id="e42a7-123">Select</span></span>  
 <span data-ttu-id="e42a7-124">下列範例使用 `select` 子句，來投影字串清單中每個字串的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="e42a7-124">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a><span data-ttu-id="e42a7-125">SelectMany</span><span class="sxs-lookup"><span data-stu-id="e42a7-125">SelectMany</span></span>  
 <span data-ttu-id="e42a7-126">下列範例使用多個 `from` 子句，來投影字串清單中每個字串的每個字。</span><span class="sxs-lookup"><span data-stu-id="e42a7-126">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="e42a7-127">Select 與 SelectMany 的比較</span><span class="sxs-lookup"><span data-stu-id="e42a7-127">Select versus SelectMany</span></span>  
 <span data-ttu-id="e42a7-128">`Select()` 和 `SelectMany()` 的工作是從來源值產生一或多個結果值。</span><span class="sxs-lookup"><span data-stu-id="e42a7-128">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="e42a7-129">`Select()` 會針對每個來源值產生一個結果值。</span><span class="sxs-lookup"><span data-stu-id="e42a7-129">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="e42a7-130">因此，整體結果是集合與來源集合中的項目數相同。</span><span class="sxs-lookup"><span data-stu-id="e42a7-130">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="e42a7-131">相反地，`SelectMany()` 會產生單一整體結果，其中包含串連自每個來源值的子集合。</span><span class="sxs-lookup"><span data-stu-id="e42a7-131">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="e42a7-132">當做引數傳遞至 `SelectMany()` 的轉換函式必須傳回每個來源值的可列舉值序列。</span><span class="sxs-lookup"><span data-stu-id="e42a7-132">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="e42a7-133">`SelectMany()` 會接著串連這些可列舉的序列，以建立一個大型的序列。</span><span class="sxs-lookup"><span data-stu-id="e42a7-133">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="e42a7-134">下列兩個圖顯示這兩個方法的動作之間的概念差異。</span><span class="sxs-lookup"><span data-stu-id="e42a7-134">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="e42a7-135">在每個案例中，假設選取器 (轉換) 函式會從每個來源值選取花朵陣列。</span><span class="sxs-lookup"><span data-stu-id="e42a7-135">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="e42a7-136">下圖描述 `Select()` 如何傳回其中的項目數與來源集合相同的集合。</span><span class="sxs-lookup"><span data-stu-id="e42a7-136">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="e42a7-137">![Select&#40;&#41; 之動作的概念圖例](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="e42a7-137">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="e42a7-138">下圖描述 `SelectMany()` 如何將中繼陣列序列串連成一個最終結果值，其中包含每個中繼陣列中的所有值。</span><span class="sxs-lookup"><span data-stu-id="e42a7-138">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="e42a7-139">![顯示 SelectMany&#40;&#41; 之動作的圖形。](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span><span class="sxs-lookup"><span data-stu-id="e42a7-139">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="e42a7-140">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e42a7-140">Code Example</span></span>  
 <span data-ttu-id="e42a7-141">下列範例會比較 `Select()` 和 `SelectMany()` 的行為。</span><span class="sxs-lookup"><span data-stu-id="e42a7-141">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="e42a7-142">程式碼會從來源集合的每個花名清單中擷取前兩個項目，以建立「花束」(Bouquet)。</span><span class="sxs-lookup"><span data-stu-id="e42a7-142">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="e42a7-143">在此範例中，轉換函式 <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> 所使用的「單一值」本身就是值集合。</span><span class="sxs-lookup"><span data-stu-id="e42a7-143">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="e42a7-144">這需要額外的 `foreach` 迴圈，以列舉每個子序列中的每個字串。</span><span class="sxs-lookup"><span data-stu-id="e42a7-144">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********              
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e42a7-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e42a7-145">See Also</span></span>  
 <span data-ttu-id="e42a7-146"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="e42a7-146"><xref:System.Linq></span></span>   
<span data-ttu-id="e42a7-147"> [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="e42a7-147"> [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="e42a7-148"> [Select 子句](../../../../csharp/language-reference/keywords/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e42a7-148"> [select clause](../../../../csharp/language-reference/keywords/select-clause.md) </span></span>  
<span data-ttu-id="e42a7-149"> [如何：從多個來源填入物件集合 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md) </span><span class="sxs-lookup"><span data-stu-id="e42a7-149"> [How to: Populate Object Collections from Multiple Sources (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md) </span></span>  
<span data-ttu-id="e42a7-150"> [如何：使用群組將檔案分割成許多檔案 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span><span class="sxs-lookup"><span data-stu-id="e42a7-150"> [How to: Split a File Into Many Files by Using Groups (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span></span>
