---
title: "轉換資料型別 (C#) | Microsoft Docs"
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
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
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
ms.openlocfilehash: eca8e10816ecb0a7a98299a81a9efdc5b5ad2630
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="converting-data-types-c"></a><span data-ttu-id="465e7-102">轉換資料型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="465e7-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="465e7-103">轉換方法會變更輸入物件的類型。</span><span class="sxs-lookup"><span data-stu-id="465e7-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="465e7-104">LINQ 查詢中的轉換作業可用於各種應用程式。</span><span class="sxs-lookup"><span data-stu-id="465e7-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="465e7-105">下列是一些範例：</span><span class="sxs-lookup"><span data-stu-id="465e7-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="465e7-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> 方法可以用來隱藏類型之標準查詢運算子的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="465e7-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="465e7-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> 方法可以用來啟用非參數化集合以進行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="465e7-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="465e7-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> 方法可以用來強制立即執行查詢，而不是延後到列舉查詢。</span><span class="sxs-lookup"><span data-stu-id="465e7-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="465e7-109">方法</span><span class="sxs-lookup"><span data-stu-id="465e7-109">Methods</span></span>  
 <span data-ttu-id="465e7-110">下表列出執行資料型別轉換的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="465e7-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="465e7-111">此表格中名稱開頭為"As" 的轉換方法會變更來源集合的靜態類型，而不是列舉它。</span><span class="sxs-lookup"><span data-stu-id="465e7-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="465e7-112">名稱開頭為 "To" 的方法會列舉來源集合，並將項目放入對應的集合類型。</span><span class="sxs-lookup"><span data-stu-id="465e7-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="465e7-113">方法名稱</span><span class="sxs-lookup"><span data-stu-id="465e7-113">Method Name</span></span>|<span data-ttu-id="465e7-114">描述</span><span class="sxs-lookup"><span data-stu-id="465e7-114">Description</span></span>|<span data-ttu-id="465e7-115">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="465e7-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="465e7-116">更多資訊</span><span class="sxs-lookup"><span data-stu-id="465e7-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="465e7-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="465e7-117">AsEnumerable</span></span>|<span data-ttu-id="465e7-118">傳回為 <xref:System.Collections.Generic.IEnumerable%601> 的輸入類型。</span><span class="sxs-lookup"><span data-stu-id="465e7-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="465e7-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="465e7-119">Not applicable.</span></span>|<span data-ttu-id="465e7-120"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="465e7-120"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="465e7-121">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="465e7-121">AsQueryable</span></span>|<span data-ttu-id="465e7-122">將 (泛型) <xref:System.Collections.IEnumerable> 轉換為 (泛型) <xref:System.Linq.IQueryable>。</span><span class="sxs-lookup"><span data-stu-id="465e7-122">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="465e7-123">不適用。</span><span class="sxs-lookup"><span data-stu-id="465e7-123">Not applicable.</span></span>|<span data-ttu-id="465e7-124"><xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="465e7-124"><xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="465e7-125">Cast</span><span class="sxs-lookup"><span data-stu-id="465e7-125">Cast</span></span>|<span data-ttu-id="465e7-126">將集合的項目轉型為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="465e7-126">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="465e7-127">使用類型明確的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="465e7-127">Use an explicitly typed range variable.</span></span> <span data-ttu-id="465e7-128">例如: </span><span class="sxs-lookup"><span data-stu-id="465e7-128">For example:</span></span><br /><br /> `from string str in words`|<span data-ttu-id="465e7-129"><xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="465e7-129"><xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="465e7-130"><xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="465e7-130"><xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="465e7-131">OfType</span><span class="sxs-lookup"><span data-stu-id="465e7-131">OfType</span></span>|<span data-ttu-id="465e7-132">根據可轉型為所指定類型的能力來篩選值。</span><span class="sxs-lookup"><span data-stu-id="465e7-132">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="465e7-133">不適用。</span><span class="sxs-lookup"><span data-stu-id="465e7-133">Not applicable.</span></span>|<span data-ttu-id="465e7-134"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="465e7-134"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="465e7-135"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="465e7-135"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="465e7-136">ToArray</span><span class="sxs-lookup"><span data-stu-id="465e7-136">ToArray</span></span>|<span data-ttu-id="465e7-137">將集合轉換為陣列。</span><span class="sxs-lookup"><span data-stu-id="465e7-137">Converts a collection to an array.</span></span> <span data-ttu-id="465e7-138">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="465e7-138">This method forces query execution.</span></span>|<span data-ttu-id="465e7-139">不適用。</span><span class="sxs-lookup"><span data-stu-id="465e7-139">Not applicable.</span></span>|<span data-ttu-id="465e7-140"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="465e7-140"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="465e7-141">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="465e7-141">ToDictionary</span></span>|<span data-ttu-id="465e7-142">根據索引鍵選取器函式，將項目放入 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="465e7-142">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="465e7-143">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="465e7-143">This method forces query execution.</span></span>|<span data-ttu-id="465e7-144">不適用。</span><span class="sxs-lookup"><span data-stu-id="465e7-144">Not applicable.</span></span>|<span data-ttu-id="465e7-145"><xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="465e7-145"><xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="465e7-146">ToList</span><span class="sxs-lookup"><span data-stu-id="465e7-146">ToList</span></span>|<span data-ttu-id="465e7-147">將集合轉換為 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="465e7-147">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="465e7-148">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="465e7-148">This method forces query execution.</span></span>|<span data-ttu-id="465e7-149">不適用。</span><span class="sxs-lookup"><span data-stu-id="465e7-149">Not applicable.</span></span>|<span data-ttu-id="465e7-150"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="465e7-150"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="465e7-151">ToLookup</span><span class="sxs-lookup"><span data-stu-id="465e7-151">ToLookup</span></span>|<span data-ttu-id="465e7-152">根據索引鍵選取器函式，將項目放入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="465e7-152">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="465e7-153">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="465e7-153">This method forces query execution.</span></span>|<span data-ttu-id="465e7-154">不適用。</span><span class="sxs-lookup"><span data-stu-id="465e7-154">Not applicable.</span></span>|<span data-ttu-id="465e7-155"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="465e7-155"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="465e7-156">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="465e7-156">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="465e7-157">下列程式碼範例會先使用類型明確的範圍變數將類型轉型為子類型，再存取只能在子類型上使用的成員。</span><span class="sxs-lookup"><span data-stu-id="465e7-157">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
```csharp  
class Plant  
{  
    public string Name { get; set; }  
}  
  
class CarnivorousPlant : Plant  
{  
    public string TrapType { get; set; }  
}  
  
static void Cast()  
{  
    Plant[] plants = new Plant[] {  
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },  
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },  
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },  
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }  
    };  
  
    var query = from CarnivorousPlant cPlant in plants  
                where cPlant.TrapType == "Snap Trap"  
                select cPlant;  
  
    foreach (Plant plant in query)  
        Console.WriteLine(plant.Name);  
  
    /* This code produces the following output:  
  
        Venus Fly Trap  
        Waterwheel Plant  
    */  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="465e7-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="465e7-158">See Also</span></span>  
 <span data-ttu-id="465e7-159"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="465e7-159"><xref:System.Linq></span></span>   
<span data-ttu-id="465e7-160"> [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="465e7-160"> [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="465e7-161"> [from 子句](../../../../csharp/language-reference/keywords/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="465e7-161"> [from clause](../../../../csharp/language-reference/keywords/from-clause.md) </span></span>  
<span data-ttu-id="465e7-162"> [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="465e7-162"> [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
<span data-ttu-id="465e7-163"> [如何：使用 LINQ 查詢 ArrayList (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)</span><span class="sxs-lookup"><span data-stu-id="465e7-163"> [How to: Query an ArrayList with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)</span></span>
