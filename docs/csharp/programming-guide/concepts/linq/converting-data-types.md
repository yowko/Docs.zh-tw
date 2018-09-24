---
title: 轉換資料型別 (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 54ef612ad4e92058d9af4d96b7b3cde9732b2f9c
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46580573"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="78526-102">轉換資料型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="78526-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="78526-103">轉換方法會變更輸入物件的類型。</span><span class="sxs-lookup"><span data-stu-id="78526-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="78526-104">LINQ 查詢中的轉換作業可用於各種應用程式。</span><span class="sxs-lookup"><span data-stu-id="78526-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="78526-105">下列是一些範例：</span><span class="sxs-lookup"><span data-stu-id="78526-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="78526-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> 方法可以用來隱藏類型之標準查詢運算子的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="78526-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="78526-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> 方法可以用來啟用非參數化集合以進行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="78526-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="78526-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> 方法可以用來強制立即執行查詢，而不是延後到列舉查詢。</span><span class="sxs-lookup"><span data-stu-id="78526-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78526-109">方法</span><span class="sxs-lookup"><span data-stu-id="78526-109">Methods</span></span>  
 <span data-ttu-id="78526-110">下表列出執行資料型別轉換的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="78526-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="78526-111">此表格中名稱開頭為"As" 的轉換方法會變更來源集合的靜態類型，而不是列舉它。</span><span class="sxs-lookup"><span data-stu-id="78526-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="78526-112">名稱開頭為 "To" 的方法會列舉來源集合，並將項目放入對應的集合類型。</span><span class="sxs-lookup"><span data-stu-id="78526-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="78526-113">方法名稱</span><span class="sxs-lookup"><span data-stu-id="78526-113">Method Name</span></span>|<span data-ttu-id="78526-114">描述</span><span class="sxs-lookup"><span data-stu-id="78526-114">Description</span></span>|<span data-ttu-id="78526-115">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="78526-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="78526-116">更多資訊</span><span class="sxs-lookup"><span data-stu-id="78526-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="78526-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="78526-117">AsEnumerable</span></span>|<span data-ttu-id="78526-118">傳回 <xref:System.Collections.Generic.IEnumerable%601> 類型的輸入。</span><span class="sxs-lookup"><span data-stu-id="78526-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="78526-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="78526-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="78526-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="78526-120">AsQueryable</span></span>|<span data-ttu-id="78526-121">將 (泛型) <xref:System.Collections.IEnumerable> 轉換成 (泛型) <xref:System.Linq.IQueryable>。</span><span class="sxs-lookup"><span data-stu-id="78526-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="78526-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="78526-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="78526-123">Cast</span><span class="sxs-lookup"><span data-stu-id="78526-123">Cast</span></span>|<span data-ttu-id="78526-124">將集合的項目轉型為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="78526-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="78526-125">使用類型明確的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="78526-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="78526-126">例如: </span><span class="sxs-lookup"><span data-stu-id="78526-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="78526-127">OfType</span><span class="sxs-lookup"><span data-stu-id="78526-127">OfType</span></span>|<span data-ttu-id="78526-128">根據可轉型為所指定類型的能力來篩選值。</span><span class="sxs-lookup"><span data-stu-id="78526-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="78526-129">不適用。</span><span class="sxs-lookup"><span data-stu-id="78526-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="78526-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="78526-130">ToArray</span></span>|<span data-ttu-id="78526-131">將集合轉換為陣列。</span><span class="sxs-lookup"><span data-stu-id="78526-131">Converts a collection to an array.</span></span> <span data-ttu-id="78526-132">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="78526-132">This method forces query execution.</span></span>|<span data-ttu-id="78526-133">不適用。</span><span class="sxs-lookup"><span data-stu-id="78526-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="78526-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="78526-134">ToDictionary</span></span>|<span data-ttu-id="78526-135">根據索引鍵選取器函式，將項目放入 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="78526-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="78526-136">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="78526-136">This method forces query execution.</span></span>|<span data-ttu-id="78526-137">不適用。</span><span class="sxs-lookup"><span data-stu-id="78526-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="78526-138">ToList</span><span class="sxs-lookup"><span data-stu-id="78526-138">ToList</span></span>|<span data-ttu-id="78526-139">將集合轉換成 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="78526-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="78526-140">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="78526-140">This method forces query execution.</span></span>|<span data-ttu-id="78526-141">不適用。</span><span class="sxs-lookup"><span data-stu-id="78526-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="78526-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="78526-142">ToLookup</span></span>|<span data-ttu-id="78526-143">根據索引鍵選取器函式，將項目放入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="78526-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="78526-144">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="78526-144">This method forces query execution.</span></span>|<span data-ttu-id="78526-145">不適用。</span><span class="sxs-lookup"><span data-stu-id="78526-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="78526-146">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="78526-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="78526-147">下列程式碼範例會先使用類型明確的範圍變數將類型轉型為子類型，再存取只能在子類型上使用的成員。</span><span class="sxs-lookup"><span data-stu-id="78526-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="78526-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="78526-148">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="78526-149">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="78526-149">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [<span data-ttu-id="78526-150">from 子句</span><span class="sxs-lookup"><span data-stu-id="78526-150">from clause</span></span>](../../../../csharp/language-reference/keywords/from-clause.md)  
- [<span data-ttu-id="78526-151">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="78526-151">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="78526-152">如何：使用 LINQ 查詢 ArrayList (C#)</span><span class="sxs-lookup"><span data-stu-id="78526-152">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
