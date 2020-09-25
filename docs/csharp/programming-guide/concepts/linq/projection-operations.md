---
title: 投影作業 (C#)
description: 瞭解投影作業。 這些作業會將物件轉換成新的表單，此表單通常只會包含稍後將使用的屬性。
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: 6128b1bb2e7ba3dbb1b428d475acc307ba931013
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185999"
---
# <a name="projection-operations-c"></a><span data-ttu-id="1d303-104">投影作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="1d303-104">Projection Operations (C#)</span></span>

<span data-ttu-id="1d303-105">投影是指將物件轉換成新形式的作業，而這個形式通常僅包含後續即將使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="1d303-105">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="1d303-106">透過使用投影，您可以建構根據每個物件所建立的新型別。</span><span class="sxs-lookup"><span data-stu-id="1d303-106">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="1d303-107">您可以投影屬性並對其執行數學函式。</span><span class="sxs-lookup"><span data-stu-id="1d303-107">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="1d303-108">您也可以投影原始物件，而不進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="1d303-108">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="1d303-109">執行投影的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="1d303-109">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d303-110">方法</span><span class="sxs-lookup"><span data-stu-id="1d303-110">Methods</span></span>  
  
|<span data-ttu-id="1d303-111">方法名稱</span><span class="sxs-lookup"><span data-stu-id="1d303-111">Method Name</span></span>|<span data-ttu-id="1d303-112">描述</span><span class="sxs-lookup"><span data-stu-id="1d303-112">Description</span></span>|<span data-ttu-id="1d303-113">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="1d303-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="1d303-114">相關資訊</span><span class="sxs-lookup"><span data-stu-id="1d303-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="1d303-115">選取</span><span class="sxs-lookup"><span data-stu-id="1d303-115">Select</span></span>|<span data-ttu-id="1d303-116">投影以轉換函式為基礎的值。</span><span class="sxs-lookup"><span data-stu-id="1d303-116">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1d303-117">SelectMany</span><span class="sxs-lookup"><span data-stu-id="1d303-117">SelectMany</span></span>|<span data-ttu-id="1d303-118">投影一連串以轉換函式為基礎的值，然後將這些值壓平合併成一個序列。</span><span class="sxs-lookup"><span data-stu-id="1d303-118">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="1d303-119">使用多個 `from` 子句</span><span class="sxs-lookup"><span data-stu-id="1d303-119">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="1d303-120">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="1d303-120">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="1d303-121">選取</span><span class="sxs-lookup"><span data-stu-id="1d303-121">Select</span></span>  

 <span data-ttu-id="1d303-122">下列範例使用 `select` 子句，來投影字串清單中每個字串的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="1d303-122">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="1d303-123">SelectMany</span><span class="sxs-lookup"><span data-stu-id="1d303-123">SelectMany</span></span>  

 <span data-ttu-id="1d303-124">下列範例使用多個 `from` 子句，來投影字串清單中每個字串的每個字。</span><span class="sxs-lookup"><span data-stu-id="1d303-124">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="1d303-125">Select 與 SelectMany 的比較</span><span class="sxs-lookup"><span data-stu-id="1d303-125">Select versus SelectMany</span></span>  

 <span data-ttu-id="1d303-126">`Select()` 和 `SelectMany()` 的工作是從來源值產生一或多個結果值。</span><span class="sxs-lookup"><span data-stu-id="1d303-126">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="1d303-127">`Select()` 會針對每個來源值產生一個結果值。</span><span class="sxs-lookup"><span data-stu-id="1d303-127">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="1d303-128">因此，整體結果是集合與來源集合中的項目數相同。</span><span class="sxs-lookup"><span data-stu-id="1d303-128">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="1d303-129">相反地，`SelectMany()` 會產生單一整體結果，其中包含串連自每個來源值的子集合。</span><span class="sxs-lookup"><span data-stu-id="1d303-129">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="1d303-130">當做引數傳遞至 `SelectMany()` 的轉換函式必須傳回每個來源值的可列舉值序列。</span><span class="sxs-lookup"><span data-stu-id="1d303-130">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="1d303-131">`SelectMany()` 會接著串連這些可列舉的序列，以建立一個大型的序列。</span><span class="sxs-lookup"><span data-stu-id="1d303-131">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="1d303-132">下列兩個圖顯示這兩個方法的動作之間的概念差異。</span><span class="sxs-lookup"><span data-stu-id="1d303-132">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="1d303-133">在每個案例中，假設選取器 (轉換) 函式會從每個來源值選取花朵陣列。</span><span class="sxs-lookup"><span data-stu-id="1d303-133">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="1d303-134">下圖描述 `Select()` 如何傳回其中的項目數與來源集合相同的集合。</span><span class="sxs-lookup"><span data-stu-id="1d303-134">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![顯示 Select&#40;&#41; 之動作的圖形](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="1d303-136">下圖描述 `SelectMany()` 如何將中繼陣列序列串連成一個最終結果值，其中包含每個中繼陣列中的所有值。</span><span class="sxs-lookup"><span data-stu-id="1d303-136">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![顯示 SelectMany&#40;&#41; 之動作的圖形。](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="1d303-138">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="1d303-138">Code Example</span></span>  

 <span data-ttu-id="1d303-139">下列範例會比較 `Select()` 和 `SelectMany()` 的行為。</span><span class="sxs-lookup"><span data-stu-id="1d303-139">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="1d303-140">程式碼會從來源集合的每個花名清單中擷取前兩個項目，以建立「花束」(Bouquet)。</span><span class="sxs-lookup"><span data-stu-id="1d303-140">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="1d303-141">在此範例中，轉換函式 <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> 所使用的「單一值」本身就是值集合。</span><span class="sxs-lookup"><span data-stu-id="1d303-141">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="1d303-142">這需要額外的 `foreach` 迴圈，以列舉每個子序列中的每個字串。</span><span class="sxs-lookup"><span data-stu-id="1d303-142">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d303-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d303-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="1d303-144">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="1d303-144">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="1d303-145">select 子句</span><span class="sxs-lookup"><span data-stu-id="1d303-145">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
- [<span data-ttu-id="1d303-146">如何從多個來源填入物件集合 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="1d303-146">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="1d303-147">如何使用群組 (LINQ)  (c # 將檔案分割成許多檔案 ) </span><span class="sxs-lookup"><span data-stu-id="1d303-147">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
