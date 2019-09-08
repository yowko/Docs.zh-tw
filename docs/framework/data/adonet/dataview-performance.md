---
title: DataView 效能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 51ea09965c423f04c220260248c3501e061820cb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784136"
---
# <a name="dataview-performance"></a><span data-ttu-id="87296-102">DataView 效能</span><span class="sxs-lookup"><span data-stu-id="87296-102">DataView Performance</span></span>
<span data-ttu-id="87296-103">本主題將討論使用 <xref:System.Data.DataView.Find%2A> 類別 (Class) 之 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法以及在 Web 應用程式中快取 <xref:System.Data.DataView> 的效能提升。</span><span class="sxs-lookup"><span data-stu-id="87296-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="87296-104">Find 和 FindRows</span><span class="sxs-lookup"><span data-stu-id="87296-104">Find and FindRows</span></span>  
 <span data-ttu-id="87296-105"><xref:System.Data.DataView> 會建構索引。</span><span class="sxs-lookup"><span data-stu-id="87296-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="87296-106">索引包含根據資料表或檢視中一個或多個資料表所建立的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="87296-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="87296-107">這些索引鍵會儲存在某個結構中，讓 <xref:System.Data.DataView> 能夠快速且有效率地尋找與索引鍵值相關聯的資料列。</span><span class="sxs-lookup"><span data-stu-id="87296-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="87296-108">使用索引的作業，例如篩選和排序，會大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="87296-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="87296-109">在您建立 <xref:System.Data.DataView> 以及修改任何排序或篩選資訊時，系統就會建立 <xref:System.Data.DataView> 的索引。</span><span class="sxs-lookup"><span data-stu-id="87296-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="87296-110">如果您建立 <xref:System.Data.DataView>，然後設定排序或篩選資訊，將會導致系統至少建立索引兩次：一次是建立 <xref:System.Data.DataView> 時，另一次是修改任何排序或篩選屬性時。</span><span class="sxs-lookup"><span data-stu-id="87296-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="87296-111">如需使用<xref:System.Data.DataView>進行篩選和排序的詳細資訊，請參閱[使用 dataview 進行篩選](filtering-with-dataview-linq-to-dataset.md)和[使用 dataview 進行排序](sorting-with-dataview-linq-to-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="87296-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="87296-112">如果您想要傳回特定資料查詢的結果，但不要提供資料子集的動態檢視，就可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 或 <xref:System.Data.DataView> 方法，而非設定 <xref:System.Data.DataView.RowFilter%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="87296-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="87296-113"><xref:System.Data.DataView.RowFilter%2A> 屬性最適於資料繫結應用程式，因為這種應用程式會用繫結控制項顯示篩選結果。</span><span class="sxs-lookup"><span data-stu-id="87296-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="87296-114">設定 <xref:System.Data.DataView.RowFilter%2A> 屬性會重建資料索引，因而增加應用程式的負荷並降低效能。</span><span class="sxs-lookup"><span data-stu-id="87296-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="87296-115"><xref:System.Data.DataView.Find%2A> 和 <xref:System.Data.DataView.FindRows%2A> 方法會使用目前的索引，而不需要重建索引。</span><span class="sxs-lookup"><span data-stu-id="87296-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="87296-116">如果您只要呼叫 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 一次，就應該使用現有的 <xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="87296-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="87296-117">如果您要呼叫 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 多次，就應該建立新的 <xref:System.Data.DataView> 來重建您想要搜尋之資料行的索引，然後呼叫 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="87296-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="87296-118">如需<xref:System.Data.DataView.Find%2A>和<xref:System.Data.DataView.FindRows%2A>方法的詳細資訊，請參閱尋找資料[列](./dataset-datatable-dataview/finding-rows.md)。</span><span class="sxs-lookup"><span data-stu-id="87296-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](./dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="87296-119">下列範例會使用 <xref:System.Data.DataView.Find%2A> 方法來尋找具有姓氏 "Zhu" 的連絡人。</span><span class="sxs-lookup"><span data-stu-id="87296-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="87296-120">下列範例會使用 <xref:System.Data.DataView.FindRows%2A> 方法來尋找所有紅色的產品。</span><span class="sxs-lookup"><span data-stu-id="87296-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="87296-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87296-121">ASP.NET</span></span>  
 <span data-ttu-id="87296-122">ASP.NET 具有一套快取機制，可讓您在記憶體中儲存需要大量伺服器資源才能建立的物件。</span><span class="sxs-lookup"><span data-stu-id="87296-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="87296-123">快取這些資源類型可大幅改善應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="87296-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="87296-124">快取是使用每個應用程式私用的快取執行個體 (Instance) 由 <xref:System.Web.Caching.Cache> 類別所實作的。</span><span class="sxs-lookup"><span data-stu-id="87296-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="87296-125">由於建立新的 <xref:System.Data.DataView> 物件可能會耗用大量資源，因此您可能會想要在 Web 應用程式中使用這項快取功能，避免每次重新整理網頁時必須重建 <xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="87296-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="87296-126">在下列範例中，<xref:System.Data.DataView> 會經過快取，避免重新整理頁面時必須重新排序資料。</span><span class="sxs-lookup"><span data-stu-id="87296-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
```vb  
If (Cache("ordersView") = Nothing) Then  
  
Dim dataSet As New DataSet()  
  
   FillDataSet(dataSet)  
  
   Dim orders As DataTable = dataSet.Tables("SalesOrderHeader")  
  
   Dim query = _  
                    From order In orders.AsEnumerable() _  
                    Where order.Field(Of Boolean)("OnlineOrderFlag") = True _  
                    Order By order.Field(Of Decimal)("TotalDue") _  
                    Select order  
  
   Dim view As DataView = query.AsDataView()  
  
   Cache.Insert("ordersView", view)  
  
End If  
  
Dim ordersView = CType(Cache("ordersView"), DataView)  
  
GridView1.DataSource = ordersView  
GridView1.DataBind()  
```  
  
```csharp  
if (Cache["ordersView"] == null)  
{  
   // Fill the DataSet.                  
   DataSet dataSet = FillDataSet();  
  
   DataTable orders = dataSet.Tables["SalesOrderHeader"];  
  
   EnumerableRowCollection<DataRow> query =  
                        from order in orders.AsEnumerable()  
                        where order.Field<bool>("OnlineOrderFlag") == true  
                        orderby order.Field<decimal>("TotalDue")  
                        select order;  
  
   DataView view = query.AsDataView();  
   Cache.Insert("ordersView", view);  
}  
  
DataView ordersView = (DataView)Cache["ordersView"];  
  
GridView1.DataSource = ordersView;  
GridView1.DataBind();  
```  
  
## <a name="see-also"></a><span data-ttu-id="87296-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87296-127">See also</span></span>

- [<span data-ttu-id="87296-128">資料繫結和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="87296-128">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
