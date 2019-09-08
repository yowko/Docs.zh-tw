---
title: 使用 DataView 進行排序 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 481a56f923c4218cd8689c578ce990785aee0ab3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782719"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a><span data-ttu-id="289bb-102">使用 DataView 進行排序 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="289bb-102">Sorting with DataView (LINQ to DataSet)</span></span>
<span data-ttu-id="289bb-103">根據特定準則來排序資料，然後透過 UI 控制項呈現資料給用戶端的功能是資料繫結的重要層面。</span><span class="sxs-lookup"><span data-stu-id="289bb-103">The ability to sort data based on specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="289bb-104"><xref:System.Data.DataView> 提供了許多方式來排序資料並傳回依據特定排序準則所排序的資料列。</span><span class="sxs-lookup"><span data-stu-id="289bb-104"><xref:System.Data.DataView> provides several ways to sort data and return data rows ordered by specific ordering criteria.</span></span> <span data-ttu-id="289bb-105">除了以字串為基礎的排序功能之外， <xref:System.Data.DataView>也可讓您[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]將運算式用於排序準則。</span><span class="sxs-lookup"><span data-stu-id="289bb-105">In addition to its string-based sorting capabilities, <xref:System.Data.DataView> also enables you to use [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] expressions for the sorting criteria.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]<span data-ttu-id="289bb-106">運算式除了以字串為基礎的排序，還允許更複雜且功能更強大的排序作業。</span><span class="sxs-lookup"><span data-stu-id="289bb-106">expressions allow for much more complex and powerful sorting operations than string-based sorting.</span></span> <span data-ttu-id="289bb-107">本主題將說明兩種使用 <xref:System.Data.DataView> 進行排序的方法。</span><span class="sxs-lookup"><span data-stu-id="289bb-107">This topic describes both approaches to sorting using <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a><span data-ttu-id="289bb-108">從含有排序資訊的查詢中建立 DataView</span><span class="sxs-lookup"><span data-stu-id="289bb-108">Creating DataView from a Query with Sorting Information</span></span>  
 <span data-ttu-id="289bb-109">您可以從 LINQ to DataSet 查詢建立物件。<xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="289bb-109">A <xref:System.Data.DataView> object can be created from a LINQ to DataSet query.</span></span> <span data-ttu-id="289bb-110">如果該查詢包含<xref:System.Linq.Enumerable.OrderBy%2A>、、 <xref:System.Linq.Enumerable.OrderByDescending%2A> <xref:System.Linq.Enumerable.ThenBy%2A>或<xref:System.Linq.Enumerable.ThenByDescending%2A>子句，這些子句中的運算式<xref:System.Data.DataView>會用來做為排序中資料的基礎。</span><span class="sxs-lookup"><span data-stu-id="289bb-110">If that query contains an <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, or <xref:System.Linq.Enumerable.ThenByDescending%2A> clause the expressions in these clauses are used as the basis for sorting the data in the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="289bb-111">例如，如果查詢包含`Order By…`和`Then By…`子句，則產生<xref:System.Data.DataView>的會依據指定的兩個數據行來排序資料。</span><span class="sxs-lookup"><span data-stu-id="289bb-111">For example, if the query contains the `Order By…`and `Then By…` clauses, the resulting <xref:System.Data.DataView> would order the data by both columns specified.</span></span>  
  
 <span data-ttu-id="289bb-112">以運算式為基礎的排序會比較簡單的以字串為基礎的排序提供功能更強大且更複雜的排序。</span><span class="sxs-lookup"><span data-stu-id="289bb-112">Expression-based sorting offers more powerful and complex sorting than the simpler string-based sorting.</span></span> <span data-ttu-id="289bb-113">請注意，以字串為基礎的排序和以運算式為基礎的排序會互斥 (Mutually Exclusive)。</span><span class="sxs-lookup"><span data-stu-id="289bb-113">Note that string-based and expression-based sorting are mutually exclusive.</span></span> <span data-ttu-id="289bb-114">如果您從查詢中建立 <xref:System.Data.DataView.Sort%2A> 之後才設定以字串為基礎的 <xref:System.Data.DataView>，就會清除從查詢中推斷的以運算式為基礎的篩選，而且無法加以重設。</span><span class="sxs-lookup"><span data-stu-id="289bb-114">If the string-based <xref:System.Data.DataView.Sort%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression-based filter inferred from the query is cleared and cannot be reset.</span></span>  
  
 <span data-ttu-id="289bb-115">在您建立 <xref:System.Data.DataView> 以及修改任何排序或篩選資訊時，系統就會建立 <xref:System.Data.DataView> 的索引。</span><span class="sxs-lookup"><span data-stu-id="289bb-115">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="289bb-116">在建立的 LINQ to DataSet 查詢<xref:System.Data.DataView>中提供排序準則，並在稍後不修改排序資訊，以獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="289bb-116">You get the best performance by supplying sorting criteria in the LINQ to DataSet query that the <xref:System.Data.DataView> is created from and not modifying the sorting information, later.</span></span> <span data-ttu-id="289bb-117">如需詳細資訊，請參閱[DataView Performance](dataview-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="289bb-117">For more information, see [DataView Performance](dataview-performance.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="289bb-118">在大部分清況中，用於排序的運算式不應該具有副作用 (Side Effect) 而且必須具決定性。</span><span class="sxs-lookup"><span data-stu-id="289bb-118">In most cases, the expressions used for sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="289bb-119">此外，這些運算式不應該包含取決於固定執行次數的任何邏輯，因為排序作業可能會執行任何次數。</span><span class="sxs-lookup"><span data-stu-id="289bb-119">Also, the expressions should not contain any logic that depends on a set number of executions, because the sorting operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="289bb-120">範例</span><span class="sxs-lookup"><span data-stu-id="289bb-120">Example</span></span>  
 <span data-ttu-id="289bb-121">下列範例會查詢 SalesOrderHeader 資料表並依據訂單日期排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="289bb-121">The following example queries the SalesOrderHeader table and orders the returned rows by the order date; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a><span data-ttu-id="289bb-122">範例</span><span class="sxs-lookup"><span data-stu-id="289bb-122">Example</span></span>  
 <span data-ttu-id="289bb-123">下列範例會查詢 SalesOrderHeader 資料表並依據總金額排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="289bb-123">The following example queries the SalesOrderHeader table and orders the returned row by total amount due; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a><span data-ttu-id="289bb-124">範例</span><span class="sxs-lookup"><span data-stu-id="289bb-124">Example</span></span>  
 <span data-ttu-id="289bb-125">下列範例會查詢 SalesOrderDetail 資料表並先後依據訂單數量和銷售訂單識別碼排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="289bb-125">The following example queries the SalesOrderDetail table and orders the returned rows by order quantity and then by sales order ID; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a><span data-ttu-id="289bb-126">使用以字串為基礎的 Sort 屬性</span><span class="sxs-lookup"><span data-stu-id="289bb-126">Using the String-Based Sort Property</span></span>  
 <span data-ttu-id="289bb-127">以字串為基礎的排序功能<xref:System.Data.DataView>仍然可與 LINQ to DataSet 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="289bb-127">The string-based sorting functionality of <xref:System.Data.DataView> still works with LINQ to DataSet.</span></span> <span data-ttu-id="289bb-128">從 LINQ to DataSet 查詢建立之後，您可以<xref:System.Data.DataView.Sort%2A>使用屬性來<xref:System.Data.DataView>設定上的排序。 <xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="289bb-128">After a <xref:System.Data.DataView> has been created from a LINQ to DataSet query, you can use the <xref:System.Data.DataView.Sort%2A> property to set the sorting on the <xref:System.Data.DataView>.</span></span>  
  
 <span data-ttu-id="289bb-129">以字串為基礎的排序和以運算式為基礎的排序功能會互斥。</span><span class="sxs-lookup"><span data-stu-id="289bb-129">The string-based and expression-based sorting functionality are mutually exclusive.</span></span> <span data-ttu-id="289bb-130">因此，設定 <xref:System.Data.DataView.Sort%2A> 屬性將會清除繼承自查詢 (從中建立 <xref:System.Data.DataView>) 的以運算式為基礎的排序。</span><span class="sxs-lookup"><span data-stu-id="289bb-130">Setting the <xref:System.Data.DataView.Sort%2A> property will clear the expression-based sort inherited from the query that the <xref:System.Data.DataView> was created from.</span></span>  
  
 <span data-ttu-id="289bb-131">如需以字串為基礎<xref:System.Data.DataView.Sort%2A>之篩選的詳細資訊，請參閱[排序和篩選資料](./dataset-datatable-dataview/sorting-and-filtering-data.md)。</span><span class="sxs-lookup"><span data-stu-id="289bb-131">For more information about string-based <xref:System.Data.DataView.Sort%2A> filtering, see [Sorting and Filtering Data](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="289bb-132">範例</span><span class="sxs-lookup"><span data-stu-id="289bb-132">Example</span></span>  
 <span data-ttu-id="289bb-133">下列範例會從 Contact 資料表中建立 <xref:System.Data.DataView> 並按照姓氏的遞減順序排序資料列，然後再按照名字的遞增順序排序資料列：</span><span class="sxs-lookup"><span data-stu-id="289bb-133">The follow example creates a <xref:System.Data.DataView> from the Contact table and sorts the rows by last name in descending order, then first name in ascending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a><span data-ttu-id="289bb-134">範例</span><span class="sxs-lookup"><span data-stu-id="289bb-134">Example</span></span>  
 <span data-ttu-id="289bb-135">下列範例會在 Contact 資料表中查詢是否有以字母 "S" 為開頭的姓氏。</span><span class="sxs-lookup"><span data-stu-id="289bb-135">The following example queries the Contact table for last names that start with the letter "S".</span></span>  <span data-ttu-id="289bb-136"><xref:System.Data.DataView> 是從該查詢中建立並繫結至 <xref:System.Windows.Forms.BindingSource> 物件。</span><span class="sxs-lookup"><span data-stu-id="289bb-136">A <xref:System.Data.DataView> is created from that query and bound to a <xref:System.Windows.Forms.BindingSource> object.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a><span data-ttu-id="289bb-137">清除排序</span><span class="sxs-lookup"><span data-stu-id="289bb-137">Clearing the Sort</span></span>  
 <span data-ttu-id="289bb-138">在您已經使用 <xref:System.Data.DataView> 屬性來設定排序資訊之後，就可以清除 <xref:System.Data.DataView.Sort%2A> 上的排序資訊。</span><span class="sxs-lookup"><span data-stu-id="289bb-138">The sorting information on a <xref:System.Data.DataView> can be cleared after it has been set using the <xref:System.Data.DataView.Sort%2A> property.</span></span> <span data-ttu-id="289bb-139">目前有兩種方式可以清除 <xref:System.Data.DataView> 中的排序資訊：</span><span class="sxs-lookup"><span data-stu-id="289bb-139">There are two ways to clear the sorting information in <xref:System.Data.DataView>:</span></span>  
  
- <span data-ttu-id="289bb-140">將 <xref:System.Data.DataView.Sort%2A> 屬性設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="289bb-140">Set the <xref:System.Data.DataView.Sort%2A> property to `null`.</span></span>  
  
- <span data-ttu-id="289bb-141">將 <xref:System.Data.DataView.Sort%2A> 屬性設定為空字串。</span><span class="sxs-lookup"><span data-stu-id="289bb-141">Set the <xref:System.Data.DataView.Sort%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="289bb-142">範例</span><span class="sxs-lookup"><span data-stu-id="289bb-142">Example</span></span>  
 <span data-ttu-id="289bb-143">下列範例會從查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView.Sort%2A> 屬性設定為空字串，藉以清除排序：</span><span class="sxs-lookup"><span data-stu-id="289bb-143">The following example creates a <xref:System.Data.DataView> from a query and clears the sorting by setting the <xref:System.Data.DataView.Sort%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a><span data-ttu-id="289bb-144">範例</span><span class="sxs-lookup"><span data-stu-id="289bb-144">Example</span></span>  
 <span data-ttu-id="289bb-145">下列範例會從 Contact 資料表中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView.Sort%2A> 屬性設定為按照姓氏的遞減順序排序。</span><span class="sxs-lookup"><span data-stu-id="289bb-145">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort by last name in descending order.</span></span> <span data-ttu-id="289bb-146">然後，系統會將 <xref:System.Data.DataView.Sort%2A> 屬性設定為 `null`，藉以清除排序資訊：</span><span class="sxs-lookup"><span data-stu-id="289bb-146">The sorting information is then cleared by setting the <xref:System.Data.DataView.Sort%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a><span data-ttu-id="289bb-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="289bb-147">See also</span></span>

- [<span data-ttu-id="289bb-148">資料繫結和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="289bb-148">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
- [<span data-ttu-id="289bb-149">使用 DataView 進行篩選</span><span class="sxs-lookup"><span data-stu-id="289bb-149">Filtering with DataView</span></span>](filtering-with-dataview-linq-to-dataset.md)
- <span data-ttu-id="289bb-150">[排序資料](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="289bb-150">[Sorting Data](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span></span>
