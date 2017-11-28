---
title: "DataView 效能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3b1f702740b1085302e413120f2bdd23c1613b25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dataview-performance"></a>DataView 效能
本主題將討論使用 <xref:System.Data.DataView.Find%2A> 類別 (Class) 之 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法以及在 Web 應用程式中快取 <xref:System.Data.DataView> 的效能提升。  
  
## <a name="find-and-findrows"></a>Find 和 FindRows  
 <xref:System.Data.DataView> 會建構索引。 索引包含根據資料表或檢視中一個或多個資料表所建立的索引鍵。 這些索引鍵會儲存在某個結構中，讓 <xref:System.Data.DataView> 能夠快速且有效率地尋找與索引鍵值相關聯的資料列。 使用索引的作業 (例如篩選和排序) 會產生大幅的效能提升。 在您建立 <xref:System.Data.DataView> 以及修改任何排序或篩選資訊時，系統就會建立 <xref:System.Data.DataView> 的索引。 如果您建立 <xref:System.Data.DataView>，然後設定排序或篩選資訊，將會導致系統至少建立索引兩次：一次是建立 <xref:System.Data.DataView> 時，另一次是修改任何排序或篩選屬性時。 如需有關篩選與排序<xref:System.Data.DataView>，請參閱[使用 dataview 進行篩選](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)和[使用 dataview 進行排序](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)。  
  
 如果您想要傳回特定資料查詢的結果，但不要提供資料子集的動態檢視，就可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 或 <xref:System.Data.DataView> 方法，而非設定 <xref:System.Data.DataView.RowFilter%2A> 屬性。 <xref:System.Data.DataView.RowFilter%2A> 屬性最適於資料繫結應用程式，因為這種應用程式會用繫結控制項顯示篩選結果。 設定 <xref:System.Data.DataView.RowFilter%2A> 屬性會重建資料索引，因而增加應用程式的負荷並降低效能。 <xref:System.Data.DataView.Find%2A> 和 <xref:System.Data.DataView.FindRows%2A> 方法會使用目前的索引，而不需要重建索引。 如果您只要呼叫 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 一次，就應該使用現有的 <xref:System.Data.DataView>。 如果您要呼叫 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 多次，就應該建立新的 <xref:System.Data.DataView> 來重建您想要搜尋之資料行的索引，然後呼叫 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 方法。 如需有關<xref:System.Data.DataView.Find%2A>和<xref:System.Data.DataView.FindRows%2A>方法，請參閱[尋找資料列](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)。  
  
 下列範例會使用 <xref:System.Data.DataView.Find%2A> 方法來尋找具有姓氏 "Zhu" 的連絡人。  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 下列範例會使用 <xref:System.Data.DataView.FindRows%2A> 方法來尋找所有紅色的產品。  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 ASP.NET 具有一套快取機制，可讓您在記憶體中儲存需要大量伺服器資源才能建立的物件。 快取這些資源類型可大幅改善應用程式的效能。 快取是使用每個應用程式私用的快取執行個體 (Instance) 由 <xref:System.Web.Caching.Cache> 類別所實作的。 由於建立新的 <xref:System.Data.DataView> 物件可能會耗用大量資源，因此您可能會想要在 Web 應用程式中使用這項快取功能，避免每次重新整理網頁時必須重建 <xref:System.Data.DataView>。  
  
 在下列範例中，<xref:System.Data.DataView> 會經過快取，避免重新整理頁面時必須重新排序資料。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [資料繫結和 LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
