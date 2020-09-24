---
title: 轉換資料型別 (C#)
description: '轉換方法會變更輸入物件的類型。 請參閱 c # 中 LINQ 查詢的轉換作業，例如可列舉的. Enumerable.asenumerable 和可列舉的。 OfType。'
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: f9e3b354fd6eeba6564067550ea3821e4946d92f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159133"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="18498-104">轉換資料型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="18498-104">Converting Data Types (C#)</span></span>

<span data-ttu-id="18498-105">轉換方法會變更輸入物件的類型。</span><span class="sxs-lookup"><span data-stu-id="18498-105">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="18498-106">LINQ 查詢中的轉換作業可用於各種應用程式。</span><span class="sxs-lookup"><span data-stu-id="18498-106">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="18498-107">下列是一些範例：</span><span class="sxs-lookup"><span data-stu-id="18498-107">Following are some examples:</span></span>

- <span data-ttu-id="18498-108"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> 方法可以用來隱藏類型之標準查詢運算子的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="18498-108">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="18498-109"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> 方法可以用來啟用非參數化集合以進行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="18498-109">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="18498-110"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> 方法可以用來強制立即執行查詢，而不是延後到列舉查詢。</span><span class="sxs-lookup"><span data-stu-id="18498-110">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="18498-111">方法</span><span class="sxs-lookup"><span data-stu-id="18498-111">Methods</span></span>

 <span data-ttu-id="18498-112">下表列出執行資料型別轉換的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="18498-112">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="18498-113">此表格中名稱開頭為"As" 的轉換方法會變更來源集合的靜態類型，而不是列舉它。</span><span class="sxs-lookup"><span data-stu-id="18498-113">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="18498-114">名稱開頭為 "To" 的方法會列舉來源集合，並將項目放入對應的集合類型。</span><span class="sxs-lookup"><span data-stu-id="18498-114">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="18498-115">方法名稱</span><span class="sxs-lookup"><span data-stu-id="18498-115">Method Name</span></span>|<span data-ttu-id="18498-116">描述</span><span class="sxs-lookup"><span data-stu-id="18498-116">Description</span></span>|<span data-ttu-id="18498-117">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="18498-117">C# Query Expression Syntax</span></span>|<span data-ttu-id="18498-118">相關資訊</span><span class="sxs-lookup"><span data-stu-id="18498-118">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="18498-119">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="18498-119">AsEnumerable</span></span>|<span data-ttu-id="18498-120">傳回 <xref:System.Collections.Generic.IEnumerable%601> 類型的輸入。</span><span class="sxs-lookup"><span data-stu-id="18498-120">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="18498-121">不適用。</span><span class="sxs-lookup"><span data-stu-id="18498-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="18498-122">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="18498-122">AsQueryable</span></span>|<span data-ttu-id="18498-123">將 (泛型) <xref:System.Collections.IEnumerable> 轉換成 (泛型) <xref:System.Linq.IQueryable>。</span><span class="sxs-lookup"><span data-stu-id="18498-123">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="18498-124">不適用。</span><span class="sxs-lookup"><span data-stu-id="18498-124">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="18498-125">轉換</span><span class="sxs-lookup"><span data-stu-id="18498-125">Cast</span></span>|<span data-ttu-id="18498-126">將集合的項目轉型為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="18498-126">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="18498-127">使用類型明確的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="18498-127">Use an explicitly typed range variable.</span></span> <span data-ttu-id="18498-128">例如：</span><span class="sxs-lookup"><span data-stu-id="18498-128">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="18498-129">OfType</span><span class="sxs-lookup"><span data-stu-id="18498-129">OfType</span></span>|<span data-ttu-id="18498-130">根據可轉型為所指定類型的能力來篩選值。</span><span class="sxs-lookup"><span data-stu-id="18498-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="18498-131">不適用。</span><span class="sxs-lookup"><span data-stu-id="18498-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="18498-132">ToArray</span><span class="sxs-lookup"><span data-stu-id="18498-132">ToArray</span></span>|<span data-ttu-id="18498-133">將集合轉換為陣列。</span><span class="sxs-lookup"><span data-stu-id="18498-133">Converts a collection to an array.</span></span> <span data-ttu-id="18498-134">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="18498-134">This method forces query execution.</span></span>|<span data-ttu-id="18498-135">不適用。</span><span class="sxs-lookup"><span data-stu-id="18498-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="18498-136">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="18498-136">ToDictionary</span></span>|<span data-ttu-id="18498-137">根據索引鍵選取器函式，將項目放入 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="18498-137">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="18498-138">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="18498-138">This method forces query execution.</span></span>|<span data-ttu-id="18498-139">不適用。</span><span class="sxs-lookup"><span data-stu-id="18498-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="18498-140">ToList</span><span class="sxs-lookup"><span data-stu-id="18498-140">ToList</span></span>|<span data-ttu-id="18498-141">將集合轉換成 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="18498-141">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="18498-142">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="18498-142">This method forces query execution.</span></span>|<span data-ttu-id="18498-143">不適用。</span><span class="sxs-lookup"><span data-stu-id="18498-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="18498-144">ToLookup</span><span class="sxs-lookup"><span data-stu-id="18498-144">ToLookup</span></span>|<span data-ttu-id="18498-145">根據索引鍵選取器函式，將項目放入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="18498-145">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="18498-146">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="18498-146">This method forces query execution.</span></span>|<span data-ttu-id="18498-147">不適用。</span><span class="sxs-lookup"><span data-stu-id="18498-147">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="18498-148">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="18498-148">Query Expression Syntax Example</span></span>

<span data-ttu-id="18498-149">下列程式碼範例會使用明確類型的範圍變數，將類型轉換成子型別，然後才會存取子類型上可用的成員。</span><span class="sxs-lookup"><span data-stu-id="18498-149">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="18498-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18498-150">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="18498-151">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="18498-151">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="18498-152">from 子句</span><span class="sxs-lookup"><span data-stu-id="18498-152">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="18498-153">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="18498-153">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="18498-154">如何使用 LINQ (c # ) 查詢 ArrayList </span><span class="sxs-lookup"><span data-stu-id="18498-154">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
