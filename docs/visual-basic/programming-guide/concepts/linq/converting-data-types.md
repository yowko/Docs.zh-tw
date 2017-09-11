---
title: "轉換資料類型 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 948779e1648291b00a68bfd83d57750d48a9a6d8
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="8de1c-102">轉換資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8de1c-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="8de1c-103">轉換方法變更輸入物件的類型。</span><span class="sxs-lookup"><span data-stu-id="8de1c-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="8de1c-104">LINQ 查詢中的轉換作業可用於各種不同的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8de1c-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="8de1c-105">以下是一些範例︰</span><span class="sxs-lookup"><span data-stu-id="8de1c-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="8de1c-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>方法可用來隱藏的類型的標準查詢運算子的自訂實作。</xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="8de1c-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>方法可用來啟用非參數化的 LINQ 查詢的集合。</xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="8de1c-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>， <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>， <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>，和<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>方法可以用來強制立即執行查詢而不是等到列舉查詢的延後。</xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8de1c-109">方法</span><span class="sxs-lookup"><span data-stu-id="8de1c-109">Methods</span></span>  
 <span data-ttu-id="8de1c-110">下表列出執行資料型別轉換的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="8de1c-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="8de1c-111">此表格中名稱開頭為"As"變更來源集合的靜態型別，但不是會列舉它的轉換方法。</span><span class="sxs-lookup"><span data-stu-id="8de1c-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="8de1c-112">方法名稱開頭為 「 目標 」 列舉來源集合，並將項目放入對應的集合型別。</span><span class="sxs-lookup"><span data-stu-id="8de1c-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="8de1c-113">方法名稱</span><span class="sxs-lookup"><span data-stu-id="8de1c-113">Method Name</span></span>|<span data-ttu-id="8de1c-114">說明</span><span class="sxs-lookup"><span data-stu-id="8de1c-114">Description</span></span>|<span data-ttu-id="8de1c-115">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="8de1c-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="8de1c-116">更多資訊</span><span class="sxs-lookup"><span data-stu-id="8de1c-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="8de1c-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="8de1c-117">AsEnumerable</span></span>|<span data-ttu-id="8de1c-118">傳回輸入型別為<xref:System.Collections.Generic.IEnumerable%601>。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="8de1c-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="8de1c-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="8de1c-119">Not applicable.</span></span>|<span data-ttu-id="8de1c-120"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-120"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8de1c-121">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="8de1c-121">AsQueryable</span></span>|<span data-ttu-id="8de1c-122">將轉換 （一般）<xref:System.Collections.IEnumerable>到 （一般） <xref:System.Linq.IQueryable>。</xref:System.Linq.IQueryable> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="8de1c-122">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="8de1c-123">不適用。</span><span class="sxs-lookup"><span data-stu-id="8de1c-123">Not applicable.</span></span>|<span data-ttu-id="8de1c-124"><xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-124"><xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8de1c-125">Cast</span><span class="sxs-lookup"><span data-stu-id="8de1c-125">Cast</span></span>|<span data-ttu-id="8de1c-126">將轉換為指定型別集合的項目。</span><span class="sxs-lookup"><span data-stu-id="8de1c-126">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<span data-ttu-id="8de1c-127"><xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-127"><xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="8de1c-128"><xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-128"><xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8de1c-129">OfType</span><span class="sxs-lookup"><span data-stu-id="8de1c-129">OfType</span></span>|<span data-ttu-id="8de1c-130">篩選值，視其可以轉換為指定型別而定。</span><span class="sxs-lookup"><span data-stu-id="8de1c-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="8de1c-131">不適用。</span><span class="sxs-lookup"><span data-stu-id="8de1c-131">Not applicable.</span></span>|<span data-ttu-id="8de1c-132"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-132"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="8de1c-133"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-133"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8de1c-134">ToArray</span><span class="sxs-lookup"><span data-stu-id="8de1c-134">ToArray</span></span>|<span data-ttu-id="8de1c-135">將集合轉換成陣列。</span><span class="sxs-lookup"><span data-stu-id="8de1c-135">Converts a collection to an array.</span></span> <span data-ttu-id="8de1c-136">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="8de1c-136">This method forces query execution.</span></span>|<span data-ttu-id="8de1c-137">不適用。</span><span class="sxs-lookup"><span data-stu-id="8de1c-137">Not applicable.</span></span>|<span data-ttu-id="8de1c-138"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-138"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8de1c-139">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="8de1c-139">ToDictionary</span></span>|<span data-ttu-id="8de1c-140">將元素插入<xref:System.Collections.Generic.Dictionary%602>根據索引鍵選取器函式。</xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="8de1c-140">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="8de1c-141">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="8de1c-141">This method forces query execution.</span></span>|<span data-ttu-id="8de1c-142">不適用。</span><span class="sxs-lookup"><span data-stu-id="8de1c-142">Not applicable.</span></span>|<span data-ttu-id="8de1c-143"><xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-143"><xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8de1c-144">ToList</span><span class="sxs-lookup"><span data-stu-id="8de1c-144">ToList</span></span>|<span data-ttu-id="8de1c-145">將集合轉換成<xref:System.Collections.Generic.List%601>。</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="8de1c-145">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="8de1c-146">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="8de1c-146">This method forces query execution.</span></span>|<span data-ttu-id="8de1c-147">不適用。</span><span class="sxs-lookup"><span data-stu-id="8de1c-147">Not applicable.</span></span>|<span data-ttu-id="8de1c-148"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-148"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8de1c-149">ToLookup</span><span class="sxs-lookup"><span data-stu-id="8de1c-149">ToLookup</span></span>|<span data-ttu-id="8de1c-150">將元素插入<xref:System.Linq.Lookup%602>（一對多字典） 會根據索引鍵選取器函式。</xref:System.Linq.Lookup%602></span><span class="sxs-lookup"><span data-stu-id="8de1c-150">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="8de1c-151">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="8de1c-151">This method forces query execution.</span></span>|<span data-ttu-id="8de1c-152">不適用。</span><span class="sxs-lookup"><span data-stu-id="8de1c-152">Not applicable.</span></span>|<span data-ttu-id="8de1c-153"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8de1c-153"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="8de1c-154">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="8de1c-154">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="8de1c-155">下列程式碼範例使用`From As`子句，才能存取的成員為僅適用於子型別轉換子的型別。</span><span class="sxs-lookup"><span data-stu-id="8de1c-155">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8de1c-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8de1c-156">See Also</span></span>  
 <span data-ttu-id="8de1c-157"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="8de1c-157"><xref:System.Linq></span></span>   
<span data-ttu-id="8de1c-158"> [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="8de1c-158"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="8de1c-159"> [From 子句](../../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="8de1c-159"> [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="8de1c-160"> [如何︰ 使用 LINQ (Visual Basic) 查詢 ArrayList](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)</span><span class="sxs-lookup"><span data-stu-id="8de1c-160"> [How to: Query an ArrayList with LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)</span></span>
