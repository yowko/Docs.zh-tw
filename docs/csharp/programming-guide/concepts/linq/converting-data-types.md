---
title: 轉換資料型別 (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: ddd9407c3b7e25dbfb8fc0bddb5daab7db2e4e53
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418622"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="61223-102">轉換資料型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="61223-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="61223-103">轉換方法會變更輸入物件的類型。</span><span class="sxs-lookup"><span data-stu-id="61223-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="61223-104">LINQ 查詢中的轉換作業可用於各種應用程式。</span><span class="sxs-lookup"><span data-stu-id="61223-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="61223-105">下列是一些範例：</span><span class="sxs-lookup"><span data-stu-id="61223-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="61223-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> 方法可以用來隱藏類型之標準查詢運算子的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="61223-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="61223-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> 方法可以用來啟用非參數化集合以進行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="61223-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="61223-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> 方法可以用來強制立即執行查詢，而不是延後到列舉查詢。</span><span class="sxs-lookup"><span data-stu-id="61223-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61223-109">方法</span><span class="sxs-lookup"><span data-stu-id="61223-109">Methods</span></span>  
 <span data-ttu-id="61223-110">下表列出執行資料型別轉換的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="61223-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="61223-111">此表格中名稱開頭為"As" 的轉換方法會變更來源集合的靜態類型，而不是列舉它。</span><span class="sxs-lookup"><span data-stu-id="61223-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="61223-112">名稱開頭為 "To" 的方法會列舉來源集合，並將項目放入對應的集合類型。</span><span class="sxs-lookup"><span data-stu-id="61223-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="61223-113">方法名稱</span><span class="sxs-lookup"><span data-stu-id="61223-113">Method Name</span></span>|<span data-ttu-id="61223-114">描述</span><span class="sxs-lookup"><span data-stu-id="61223-114">Description</span></span>|<span data-ttu-id="61223-115">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="61223-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="61223-116">更多資訊</span><span class="sxs-lookup"><span data-stu-id="61223-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="61223-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="61223-117">AsEnumerable</span></span>|<span data-ttu-id="61223-118">傳回 <xref:System.Collections.Generic.IEnumerable%601> 類型的輸入。</span><span class="sxs-lookup"><span data-stu-id="61223-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="61223-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="61223-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61223-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="61223-120">AsQueryable</span></span>|<span data-ttu-id="61223-121">將 (泛型) <xref:System.Collections.IEnumerable> 轉換成 (泛型) <xref:System.Linq.IQueryable>。</span><span class="sxs-lookup"><span data-stu-id="61223-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="61223-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="61223-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61223-123">Cast</span><span class="sxs-lookup"><span data-stu-id="61223-123">Cast</span></span>|<span data-ttu-id="61223-124">將集合的項目轉型為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="61223-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="61223-125">使用類型明確的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="61223-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="61223-126">例如:</span><span class="sxs-lookup"><span data-stu-id="61223-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61223-127">OfType</span><span class="sxs-lookup"><span data-stu-id="61223-127">OfType</span></span>|<span data-ttu-id="61223-128">根據可轉型為所指定類型的能力來篩選值。</span><span class="sxs-lookup"><span data-stu-id="61223-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="61223-129">不適用。</span><span class="sxs-lookup"><span data-stu-id="61223-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61223-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="61223-130">ToArray</span></span>|<span data-ttu-id="61223-131">將集合轉換為陣列。</span><span class="sxs-lookup"><span data-stu-id="61223-131">Converts a collection to an array.</span></span> <span data-ttu-id="61223-132">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="61223-132">This method forces query execution.</span></span>|<span data-ttu-id="61223-133">不適用。</span><span class="sxs-lookup"><span data-stu-id="61223-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61223-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="61223-134">ToDictionary</span></span>|<span data-ttu-id="61223-135">根據索引鍵選取器函式，將項目放入 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="61223-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="61223-136">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="61223-136">This method forces query execution.</span></span>|<span data-ttu-id="61223-137">不適用。</span><span class="sxs-lookup"><span data-stu-id="61223-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61223-138">ToList</span><span class="sxs-lookup"><span data-stu-id="61223-138">ToList</span></span>|<span data-ttu-id="61223-139">將集合轉換成 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="61223-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="61223-140">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="61223-140">This method forces query execution.</span></span>|<span data-ttu-id="61223-141">不適用。</span><span class="sxs-lookup"><span data-stu-id="61223-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61223-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="61223-142">ToLookup</span></span>|<span data-ttu-id="61223-143">根據索引鍵選取器函式，將項目放入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="61223-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="61223-144">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="61223-144">This method forces query execution.</span></span>|<span data-ttu-id="61223-145">不適用。</span><span class="sxs-lookup"><span data-stu-id="61223-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="61223-146">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="61223-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="61223-147">下列程式碼範例會先使用類型明確的範圍變數將類型轉型為子類型，再存取只能在子類型上使用的成員。</span><span class="sxs-lookup"><span data-stu-id="61223-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="61223-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="61223-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="61223-149">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="61223-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="61223-150">from 子句</span><span class="sxs-lookup"><span data-stu-id="61223-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="61223-151">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="61223-151">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="61223-152">如何：使用 LINQ 查詢 ArrayList (C#)</span><span class="sxs-lookup"><span data-stu-id="61223-152">How to: Query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
