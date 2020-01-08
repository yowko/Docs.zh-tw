---
title: 使用 DataView 進行排序 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 2998de7dee34f9b5410bfe53988e0b7cfa797784
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634751"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a><span data-ttu-id="ef185-102">使用 DataView 進行排序 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="ef185-102">Sorting with DataView (LINQ to DataSet)</span></span>
<span data-ttu-id="ef185-103">根據特定準則來排序資料，然後透過 UI 控制項呈現資料給用戶端的功能是資料繫結的重要層面。</span><span class="sxs-lookup"><span data-stu-id="ef185-103">The ability to sort data based on specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="ef185-104"><xref:System.Data.DataView> 提供了許多方式來排序資料並傳回依據特定排序準則所排序的資料列。</span><span class="sxs-lookup"><span data-stu-id="ef185-104"><xref:System.Data.DataView> provides several ways to sort data and return data rows ordered by specific ordering criteria.</span></span> <span data-ttu-id="ef185-105">除了以字串為基礎的排序功能之外，<xref:System.Data.DataView> 也可以讓您使用語言整合式查詢（LINQ）運算式來進行排序準則。</span><span class="sxs-lookup"><span data-stu-id="ef185-105">In addition to its string-based sorting capabilities, <xref:System.Data.DataView> also enables you to use Language-Integrated Query (LINQ) expressions for the sorting criteria.</span></span> <span data-ttu-id="ef185-106">LINQ 運算式除了以字串為基礎的排序，還允許更複雜且功能更強大的排序作業。</span><span class="sxs-lookup"><span data-stu-id="ef185-106">LINQ expressions allow for much more complex and powerful sorting operations than string-based sorting.</span></span> <span data-ttu-id="ef185-107">本主題將說明兩種使用 <xref:System.Data.DataView> 進行排序的方法。</span><span class="sxs-lookup"><span data-stu-id="ef185-107">This topic describes both approaches to sorting using <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a><span data-ttu-id="ef185-108">從含有排序資訊的查詢中建立 DataView</span><span class="sxs-lookup"><span data-stu-id="ef185-108">Creating DataView from a Query with Sorting Information</span></span>  
 <span data-ttu-id="ef185-109">可以從 LINQ to DataSet 查詢建立 <xref:System.Data.DataView> 物件。</span><span class="sxs-lookup"><span data-stu-id="ef185-109">A <xref:System.Data.DataView> object can be created from a LINQ to DataSet query.</span></span> <span data-ttu-id="ef185-110">如果該查詢包含 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.ThenBy%2A>或 <xref:System.Linq.Enumerable.ThenByDescending%2A> 子句，這些子句中的運算式會當做排序 <xref:System.Data.DataView>中資料的基礎使用。</span><span class="sxs-lookup"><span data-stu-id="ef185-110">If that query contains an <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, or <xref:System.Linq.Enumerable.ThenByDescending%2A> clause the expressions in these clauses are used as the basis for sorting the data in the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="ef185-111">例如，如果查詢包含 `Order By…`和 `Then By…` 子句，則產生的 <xref:System.Data.DataView> 會依照指定的兩個數據行來排序資料。</span><span class="sxs-lookup"><span data-stu-id="ef185-111">For example, if the query contains the `Order By…`and `Then By…` clauses, the resulting <xref:System.Data.DataView> would order the data by both columns specified.</span></span>  
  
 <span data-ttu-id="ef185-112">以運算式為基礎的排序會比較簡單的以字串為基礎的排序提供功能更強大且更複雜的排序。</span><span class="sxs-lookup"><span data-stu-id="ef185-112">Expression-based sorting offers more powerful and complex sorting than the simpler string-based sorting.</span></span> <span data-ttu-id="ef185-113">請注意，以字串為基礎的排序和以運算式為基礎的排序會互斥 (Mutually Exclusive)。</span><span class="sxs-lookup"><span data-stu-id="ef185-113">Note that string-based and expression-based sorting are mutually exclusive.</span></span> <span data-ttu-id="ef185-114">如果您從查詢中建立 <xref:System.Data.DataView.Sort%2A> 之後才設定以字串為基礎的 <xref:System.Data.DataView>，就會清除從查詢中推斷的以運算式為基礎的篩選，而且無法加以重設。</span><span class="sxs-lookup"><span data-stu-id="ef185-114">If the string-based <xref:System.Data.DataView.Sort%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression-based filter inferred from the query is cleared and cannot be reset.</span></span>  
  
 <span data-ttu-id="ef185-115">在您建立 <xref:System.Data.DataView> 以及修改任何排序或篩選資訊時，系統就會建立 <xref:System.Data.DataView> 的索引。</span><span class="sxs-lookup"><span data-stu-id="ef185-115">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="ef185-116">在建立 <xref:System.Data.DataView> 的 LINQ to DataSet 查詢中提供排序準則，並于稍後不修改排序資訊，以獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="ef185-116">You get the best performance by supplying sorting criteria in the LINQ to DataSet query that the <xref:System.Data.DataView> is created from and not modifying the sorting information, later.</span></span> <span data-ttu-id="ef185-117">如需詳細資訊，請參閱[DataView Performance](dataview-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="ef185-117">For more information, see [DataView Performance](dataview-performance.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef185-118">在大部分清況中，用於排序的運算式不應該具有副作用 (Side Effect) 而且必須具決定性。</span><span class="sxs-lookup"><span data-stu-id="ef185-118">In most cases, the expressions used for sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="ef185-119">此外，這些運算式不應該包含取決於固定執行次數的任何邏輯，因為排序作業可能會執行任何次數。</span><span class="sxs-lookup"><span data-stu-id="ef185-119">Also, the expressions should not contain any logic that depends on a set number of executions, because the sorting operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ef185-120">範例</span><span class="sxs-lookup"><span data-stu-id="ef185-120">Example</span></span>  
 <span data-ttu-id="ef185-121">下列範例會查詢 SalesOrderHeader 資料表並依據訂單日期排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="ef185-121">The following example queries the SalesOrderHeader table and orders the returned rows by the order date; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a><span data-ttu-id="ef185-122">範例</span><span class="sxs-lookup"><span data-stu-id="ef185-122">Example</span></span>  
 <span data-ttu-id="ef185-123">下列範例會查詢 SalesOrderHeader 資料表並依據總金額排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="ef185-123">The following example queries the SalesOrderHeader table and orders the returned row by total amount due; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a><span data-ttu-id="ef185-124">範例</span><span class="sxs-lookup"><span data-stu-id="ef185-124">Example</span></span>  
 <span data-ttu-id="ef185-125">下列範例會查詢 SalesOrderDetail 資料表並先後依據訂單數量和銷售訂單識別碼排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="ef185-125">The following example queries the SalesOrderDetail table and orders the returned rows by order quantity and then by sales order ID; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a><span data-ttu-id="ef185-126">使用以字串為基礎的 Sort 屬性</span><span class="sxs-lookup"><span data-stu-id="ef185-126">Using the String-Based Sort Property</span></span>  
 <span data-ttu-id="ef185-127"><xref:System.Data.DataView> 的以字串為基礎的排序功能仍適用于 LINQ to DataSet。</span><span class="sxs-lookup"><span data-stu-id="ef185-127">The string-based sorting functionality of <xref:System.Data.DataView> still works with LINQ to DataSet.</span></span> <span data-ttu-id="ef185-128">從 LINQ to DataSet 查詢建立 <xref:System.Data.DataView> 之後，您可以使用 <xref:System.Data.DataView.Sort%2A> 屬性來設定 <xref:System.Data.DataView>的排序。</span><span class="sxs-lookup"><span data-stu-id="ef185-128">After a <xref:System.Data.DataView> has been created from a LINQ to DataSet query, you can use the <xref:System.Data.DataView.Sort%2A> property to set the sorting on the <xref:System.Data.DataView>.</span></span>  
  
 <span data-ttu-id="ef185-129">以字串為基礎的排序和以運算式為基礎的排序功能會互斥。</span><span class="sxs-lookup"><span data-stu-id="ef185-129">The string-based and expression-based sorting functionality are mutually exclusive.</span></span> <span data-ttu-id="ef185-130">因此，設定 <xref:System.Data.DataView.Sort%2A> 屬性將會清除繼承自查詢 (從中建立 <xref:System.Data.DataView>) 的以運算式為基礎的排序。</span><span class="sxs-lookup"><span data-stu-id="ef185-130">Setting the <xref:System.Data.DataView.Sort%2A> property will clear the expression-based sort inherited from the query that the <xref:System.Data.DataView> was created from.</span></span>  
  
 <span data-ttu-id="ef185-131">如需以字串為基礎 <xref:System.Data.DataView.Sort%2A> 篩選的詳細資訊，請參閱[排序和篩選資料](./dataset-datatable-dataview/sorting-and-filtering-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ef185-131">For more information about string-based <xref:System.Data.DataView.Sort%2A> filtering, see [Sorting and Filtering Data](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="ef185-132">範例</span><span class="sxs-lookup"><span data-stu-id="ef185-132">Example</span></span>  
 <span data-ttu-id="ef185-133">下列範例會從 Contact 資料表中建立 <xref:System.Data.DataView> 並按照姓氏的遞減順序排序資料列，然後再按照名字的遞增順序排序資料列：</span><span class="sxs-lookup"><span data-stu-id="ef185-133">The follow example creates a <xref:System.Data.DataView> from the Contact table and sorts the rows by last name in descending order, then first name in ascending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a><span data-ttu-id="ef185-134">範例</span><span class="sxs-lookup"><span data-stu-id="ef185-134">Example</span></span>  
 <span data-ttu-id="ef185-135">下列範例會在 Contact 資料表中查詢是否有以字母 "S" 為開頭的姓氏。</span><span class="sxs-lookup"><span data-stu-id="ef185-135">The following example queries the Contact table for last names that start with the letter "S".</span></span>  <span data-ttu-id="ef185-136"><xref:System.Data.DataView> 是從該查詢中建立並繫結至 <xref:System.Windows.Forms.BindingSource> 物件。</span><span class="sxs-lookup"><span data-stu-id="ef185-136">A <xref:System.Data.DataView> is created from that query and bound to a <xref:System.Windows.Forms.BindingSource> object.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a><span data-ttu-id="ef185-137">清除排序</span><span class="sxs-lookup"><span data-stu-id="ef185-137">Clearing the Sort</span></span>  
 <span data-ttu-id="ef185-138">在您已經使用 <xref:System.Data.DataView> 屬性來設定排序資訊之後，就可以清除 <xref:System.Data.DataView.Sort%2A> 上的排序資訊。</span><span class="sxs-lookup"><span data-stu-id="ef185-138">The sorting information on a <xref:System.Data.DataView> can be cleared after it has been set using the <xref:System.Data.DataView.Sort%2A> property.</span></span> <span data-ttu-id="ef185-139">目前有兩種方式可以清除 <xref:System.Data.DataView> 中的排序資訊：</span><span class="sxs-lookup"><span data-stu-id="ef185-139">There are two ways to clear the sorting information in <xref:System.Data.DataView>:</span></span>  
  
- <span data-ttu-id="ef185-140">將 <xref:System.Data.DataView.Sort%2A> 屬性設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="ef185-140">Set the <xref:System.Data.DataView.Sort%2A> property to `null`.</span></span>  
  
- <span data-ttu-id="ef185-141">將 <xref:System.Data.DataView.Sort%2A> 屬性設定為空字串。</span><span class="sxs-lookup"><span data-stu-id="ef185-141">Set the <xref:System.Data.DataView.Sort%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ef185-142">範例</span><span class="sxs-lookup"><span data-stu-id="ef185-142">Example</span></span>  
 <span data-ttu-id="ef185-143">下列範例會從查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView.Sort%2A> 屬性設定為空字串，藉以清除排序：</span><span class="sxs-lookup"><span data-stu-id="ef185-143">The following example creates a <xref:System.Data.DataView> from a query and clears the sorting by setting the <xref:System.Data.DataView.Sort%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a><span data-ttu-id="ef185-144">範例</span><span class="sxs-lookup"><span data-stu-id="ef185-144">Example</span></span>  
 <span data-ttu-id="ef185-145">下列範例會從 Contact 資料表中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView.Sort%2A> 屬性設定為按照姓氏的遞減順序排序。</span><span class="sxs-lookup"><span data-stu-id="ef185-145">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort by last name in descending order.</span></span> <span data-ttu-id="ef185-146">然後，系統會將 <xref:System.Data.DataView.Sort%2A> 屬性設定為 `null`，藉以清除排序資訊：</span><span class="sxs-lookup"><span data-stu-id="ef185-146">The sorting information is then cleared by setting the <xref:System.Data.DataView.Sort%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a><span data-ttu-id="ef185-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="ef185-147">See also</span></span>

- [<span data-ttu-id="ef185-148">資料繫結和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="ef185-148">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
- [<span data-ttu-id="ef185-149">使用 DataView 進行篩選</span><span class="sxs-lookup"><span data-stu-id="ef185-149">Filtering with DataView</span></span>](filtering-with-dataview-linq-to-dataset.md)
- <span data-ttu-id="ef185-150">[排序資料](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="ef185-150">[Sorting Data](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span></span>
