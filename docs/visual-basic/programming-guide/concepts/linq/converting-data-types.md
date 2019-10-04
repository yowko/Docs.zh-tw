---
title: 轉換資料類型（Visual Basic）
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 4d0658983b5873c635d1926444293b0ddf5b0a87
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835178"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="ed2ab-102">轉換資料類型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="ed2ab-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="ed2ab-103">轉換方法會變更輸入物件的類型。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="ed2ab-104">LINQ 查詢中的轉換作業可用於各種應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="ed2ab-105">以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="ed2ab-105">The following are some examples:</span></span>
  
- <span data-ttu-id="ed2ab-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> 方法可以用來隱藏類型之標準查詢運算子的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="ed2ab-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> 方法可以用來啟用非參數化集合以進行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="ed2ab-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> 方法可以用來強制立即執行查詢，而不是延後到列舉查詢。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ed2ab-109">方法</span><span class="sxs-lookup"><span data-stu-id="ed2ab-109">Methods</span></span>  
 <span data-ttu-id="ed2ab-110">下表列出執行資料型別轉換的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="ed2ab-111">此表格中名稱開頭為"As" 的轉換方法會變更來源集合的靜態類型，而不是列舉它。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="ed2ab-112">名稱開頭為 "To" 的方法會列舉來源集合，並將項目放入對應的集合類型。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="ed2ab-113">方法名稱</span><span class="sxs-lookup"><span data-stu-id="ed2ab-113">Method Name</span></span>|<span data-ttu-id="ed2ab-114">描述</span><span class="sxs-lookup"><span data-stu-id="ed2ab-114">Description</span></span>|<span data-ttu-id="ed2ab-115">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="ed2ab-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ed2ab-116">更多資訊</span><span class="sxs-lookup"><span data-stu-id="ed2ab-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="ed2ab-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="ed2ab-117">AsEnumerable</span></span>|<span data-ttu-id="ed2ab-118">傳回 <xref:System.Collections.Generic.IEnumerable%601> 類型的輸入。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="ed2ab-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ed2ab-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="ed2ab-120">AsQueryable</span></span>|<span data-ttu-id="ed2ab-121">將 (泛型) <xref:System.Collections.IEnumerable> 轉換成 (泛型) <xref:System.Linq.IQueryable>。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="ed2ab-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ed2ab-123">Cast</span><span class="sxs-lookup"><span data-stu-id="ed2ab-123">Cast</span></span>|<span data-ttu-id="ed2ab-124">將集合的項目轉型為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ed2ab-125">OfType</span><span class="sxs-lookup"><span data-stu-id="ed2ab-125">OfType</span></span>|<span data-ttu-id="ed2ab-126">根據可轉型為所指定類型的能力來篩選值。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="ed2ab-127">不適用。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ed2ab-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="ed2ab-128">ToArray</span></span>|<span data-ttu-id="ed2ab-129">將集合轉換為陣列。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-129">Converts a collection to an array.</span></span> <span data-ttu-id="ed2ab-130">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-130">This method forces query execution.</span></span>|<span data-ttu-id="ed2ab-131">不適用。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ed2ab-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="ed2ab-132">ToDictionary</span></span>|<span data-ttu-id="ed2ab-133">根據索引鍵選取器函式，將項目放入 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="ed2ab-134">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-134">This method forces query execution.</span></span>|<span data-ttu-id="ed2ab-135">不適用。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ed2ab-136">ToList</span><span class="sxs-lookup"><span data-stu-id="ed2ab-136">ToList</span></span>|<span data-ttu-id="ed2ab-137">將集合轉換成 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="ed2ab-138">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-138">This method forces query execution.</span></span>|<span data-ttu-id="ed2ab-139">不適用。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ed2ab-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="ed2ab-140">ToLookup</span></span>|<span data-ttu-id="ed2ab-141">根據索引鍵選取器函式，將項目放入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="ed2ab-142">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-142">This method forces query execution.</span></span>|<span data-ttu-id="ed2ab-143">不適用。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="ed2ab-144">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="ed2ab-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="ed2ab-145">下列程式碼範例會使用 `From As` 子句，將類型轉換成子類型，然後才存取僅適用于子類型的成員。</span><span class="sxs-lookup"><span data-stu-id="ed2ab-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed2ab-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed2ab-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ed2ab-147">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed2ab-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ed2ab-148">From 子句</span><span class="sxs-lookup"><span data-stu-id="ed2ab-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="ed2ab-149">如何：使用 LINQ （Visual Basic）查詢 ArrayList </span><span class="sxs-lookup"><span data-stu-id="ed2ab-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
