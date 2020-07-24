---
title: 轉換資料型別 (C#)
description: '轉換方法會變更輸入物件的類型。 請參閱 c # 中的 LINQ 查詢中的轉換作業，例如可列舉的 Enumerable.asenumerable 和可列舉的 OfType。'
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 3291690f9aaee945ca7feb04ebbc676db2612894
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105490"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="60c3a-104">轉換資料型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="60c3a-104">Converting Data Types (C#)</span></span>
<span data-ttu-id="60c3a-105">轉換方法會變更輸入物件的類型。</span><span class="sxs-lookup"><span data-stu-id="60c3a-105">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="60c3a-106">LINQ 查詢中的轉換作業可用於各種應用程式。</span><span class="sxs-lookup"><span data-stu-id="60c3a-106">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="60c3a-107">下列是一些範例：</span><span class="sxs-lookup"><span data-stu-id="60c3a-107">Following are some examples:</span></span>

- <span data-ttu-id="60c3a-108"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> 方法可以用來隱藏類型之標準查詢運算子的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="60c3a-108">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="60c3a-109"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> 方法可以用來啟用非參數化集合以進行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="60c3a-109">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="60c3a-110"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> 方法可以用來強制立即執行查詢，而不是延後到列舉查詢。</span><span class="sxs-lookup"><span data-stu-id="60c3a-110">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="60c3a-111">方法</span><span class="sxs-lookup"><span data-stu-id="60c3a-111">Methods</span></span>
 <span data-ttu-id="60c3a-112">下表列出執行資料型別轉換的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="60c3a-112">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="60c3a-113">此表格中名稱開頭為"As" 的轉換方法會變更來源集合的靜態類型，而不是列舉它。</span><span class="sxs-lookup"><span data-stu-id="60c3a-113">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="60c3a-114">名稱開頭為 "To" 的方法會列舉來源集合，並將項目放入對應的集合類型。</span><span class="sxs-lookup"><span data-stu-id="60c3a-114">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="60c3a-115">方法名稱</span><span class="sxs-lookup"><span data-stu-id="60c3a-115">Method Name</span></span>|<span data-ttu-id="60c3a-116">說明</span><span class="sxs-lookup"><span data-stu-id="60c3a-116">Description</span></span>|<span data-ttu-id="60c3a-117">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="60c3a-117">C# Query Expression Syntax</span></span>|<span data-ttu-id="60c3a-118">相關資訊</span><span class="sxs-lookup"><span data-stu-id="60c3a-118">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="60c3a-119">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="60c3a-119">AsEnumerable</span></span>|<span data-ttu-id="60c3a-120">傳回 <xref:System.Collections.Generic.IEnumerable%601> 類型的輸入。</span><span class="sxs-lookup"><span data-stu-id="60c3a-120">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="60c3a-121">不適用。</span><span class="sxs-lookup"><span data-stu-id="60c3a-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="60c3a-122">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="60c3a-122">AsQueryable</span></span>|<span data-ttu-id="60c3a-123">將 (泛型) <xref:System.Collections.IEnumerable> 轉換成 (泛型) <xref:System.Linq.IQueryable>。</span><span class="sxs-lookup"><span data-stu-id="60c3a-123">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="60c3a-124">不適用。</span><span class="sxs-lookup"><span data-stu-id="60c3a-124">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="60c3a-125">轉換</span><span class="sxs-lookup"><span data-stu-id="60c3a-125">Cast</span></span>|<span data-ttu-id="60c3a-126">將集合的項目轉型為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="60c3a-126">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="60c3a-127">使用類型明確的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="60c3a-127">Use an explicitly typed range variable.</span></span> <span data-ttu-id="60c3a-128">例如:</span><span class="sxs-lookup"><span data-stu-id="60c3a-128">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="60c3a-129">OfType</span><span class="sxs-lookup"><span data-stu-id="60c3a-129">OfType</span></span>|<span data-ttu-id="60c3a-130">根據可轉型為所指定類型的能力來篩選值。</span><span class="sxs-lookup"><span data-stu-id="60c3a-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="60c3a-131">不適用。</span><span class="sxs-lookup"><span data-stu-id="60c3a-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="60c3a-132">ToArray</span><span class="sxs-lookup"><span data-stu-id="60c3a-132">ToArray</span></span>|<span data-ttu-id="60c3a-133">將集合轉換為陣列。</span><span class="sxs-lookup"><span data-stu-id="60c3a-133">Converts a collection to an array.</span></span> <span data-ttu-id="60c3a-134">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="60c3a-134">This method forces query execution.</span></span>|<span data-ttu-id="60c3a-135">不適用。</span><span class="sxs-lookup"><span data-stu-id="60c3a-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="60c3a-136">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="60c3a-136">ToDictionary</span></span>|<span data-ttu-id="60c3a-137">根據索引鍵選取器函式，將項目放入 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="60c3a-137">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="60c3a-138">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="60c3a-138">This method forces query execution.</span></span>|<span data-ttu-id="60c3a-139">不適用。</span><span class="sxs-lookup"><span data-stu-id="60c3a-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="60c3a-140">ToList</span><span class="sxs-lookup"><span data-stu-id="60c3a-140">ToList</span></span>|<span data-ttu-id="60c3a-141">將集合轉換成 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="60c3a-141">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="60c3a-142">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="60c3a-142">This method forces query execution.</span></span>|<span data-ttu-id="60c3a-143">不適用。</span><span class="sxs-lookup"><span data-stu-id="60c3a-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="60c3a-144">ToLookup</span><span class="sxs-lookup"><span data-stu-id="60c3a-144">ToLookup</span></span>|<span data-ttu-id="60c3a-145">根據索引鍵選取器函式，將項目放入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="60c3a-145">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="60c3a-146">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="60c3a-146">This method forces query execution.</span></span>|<span data-ttu-id="60c3a-147">不適用。</span><span class="sxs-lookup"><span data-stu-id="60c3a-147">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="60c3a-148">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="60c3a-148">Query Expression Syntax Example</span></span>

<span data-ttu-id="60c3a-149">下列程式碼範例會使用明確類型的範圍變數，將類型轉換成子類型，然後才存取僅適用于子類型的成員。</span><span class="sxs-lookup"><span data-stu-id="60c3a-149">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="60c3a-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="60c3a-150">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="60c3a-151">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="60c3a-151">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="60c3a-152">from 子句</span><span class="sxs-lookup"><span data-stu-id="60c3a-152">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="60c3a-153">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="60c3a-153">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="60c3a-154">如何使用 LINQ 查詢 ArrayList （c #）</span><span class="sxs-lookup"><span data-stu-id="60c3a-154">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
