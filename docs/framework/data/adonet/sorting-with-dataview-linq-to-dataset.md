---
title: "使用 DataView 進行排序 (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 使用 DataView 進行排序 (LINQ to DataSet)
根據特定準則來排序資料，然後透過 UI 控制項呈現資料給用戶端的功能是資料繫結的重要層面。  <xref:System.Data.DataView> 提供了許多方式來排序資料並傳回依據特定排序準則所排序的資料列。  除了以字串為基礎的排序功能以外，<xref:System.Data.DataView> 也可讓您針對排序準則使用 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 運算式。[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 運算式比以字串為基礎的排序允許更複雜且功能更強大的排序作業。  本主題將說明兩種使用 <xref:System.Data.DataView> 進行排序的方法。  
  
## 從含有排序資訊的查詢中建立 DataView  
 您可以從 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢中建立 <xref:System.Data.DataView> 物件。  如果該查詢包含 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.ThenBy%2A> 或 <xref:System.Linq.Enumerable.ThenByDescending%2A> 子句，這些子句中的運算式就會當做在 <xref:System.Data.DataView> 中排序資料的基礎使用。  例如，如果此查詢包含 `Order By`和 `Then By`  子句，則產生的 <xref:System.Data.DataView> 就會依據這兩個指定的資料行來排序資料。  
  
 以運算式為基礎的排序會比較簡單的以字串為基礎的排序提供功能更強大且更複雜的排序。  請注意，以字串為基礎的排序和以運算式為基礎的排序會互斥 \(Mutually Exclusive\)。  如果您從查詢中建立 <xref:System.Data.DataView> 之後才設定以字串為基礎的 <xref:System.Data.DataView.Sort%2A>，就會清除從查詢中推斷的以運算式為基礎的篩選，而且無法加以重設。  
  
 在您建立 <xref:System.Data.DataView> 以及修改任何排序或篩選資訊時，系統就會建立 <xref:System.Data.DataView> 的索引。  您可以在從中建立 <xref:System.Data.DataView> 的 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢中提供排序準則，而且之後不修改排序資訊，藉以取得最佳效能。  如需詳細資訊，請參閱[DataView 效能](../../../../docs/framework/data/adonet/dataview-performance.md)。  
  
> [!NOTE]
>  在大部分清況中，用於排序的運算式不應該具有副作用 \(Side Effect\) 而且必須具決定性。  此外，這些運算式不應該包含取決於固定執行次數的任何邏輯，因為排序作業可能會執行任何次數。  
  
### 範例  
 下列範例會查詢 SalesOrderHeader 資料表並依據訂單日期排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### 範例  
 下列範例會查詢 SalesOrderHeader 資料表並依據總金額排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### 範例  
 下列範例會查詢 SalesOrderDetail 資料表並先後依據訂單數量和銷售訂單識別碼排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## 使用以字串為基礎的 Sort 屬性  
 <xref:System.Data.DataView> 以字串為基礎的排序功能仍然可搭配 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 運作。  在您已經從 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢中建立 <xref:System.Data.DataView> 之後，就可以使用 <xref:System.Data.DataView.Sort%2A> 屬性，針對 <xref:System.Data.DataView> 設定排序。  
  
 以字串為基礎的排序和以運算式為基礎的排序功能會互斥。  因此，設定 <xref:System.Data.DataView.Sort%2A> 屬性將會清除繼承自查詢 \(從中建立 <xref:System.Data.DataView>\) 的以運算式為基礎的排序。  
  
 如需以字串為基礎之 <xref:System.Data.DataView.Sort%2A> 篩選的詳細資訊，請參閱[排序和篩選資料](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)。  
  
### 範例  
 下列範例會從 Contact 資料表中建立 <xref:System.Data.DataView> 並按照姓氏的遞減順序排序資料列，然後再按照名字的遞增順序排序資料列：  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### 範例  
 下列範例會在 Contact 資料表中查詢是否有以字母 "S" 為開頭的姓氏。  <xref:System.Data.DataView> 是從該查詢中建立並繫結至 <xref:System.Windows.Forms.BindingSource> 物件。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## 清除排序  
 在您已經使用 <xref:System.Data.DataView.Sort%2A> 屬性來設定排序資訊之後，就可以清除 <xref:System.Data.DataView> 上的排序資訊。  目前有兩種方式可以清除 <xref:System.Data.DataView> 中的排序資訊：  
  
-   將 <xref:System.Data.DataView.Sort%2A> 屬性設定為 `null`。  
  
-   將 <xref:System.Data.DataView.Sort%2A> 屬性設定為空字串。  
  
### 範例  
 下列範例會從查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView.Sort%2A> 屬性設定為空字串，藉以清除排序：  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### 範例  
 下列範例會從 Contact 資料表中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView.Sort%2A> 屬性設定為按照姓氏的遞減順序排序。  然後，系統會將 <xref:System.Data.DataView.Sort%2A> 屬性設定為 `null`，藉以清除排序資訊：  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## 請參閱  
 [資料繫結和 LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)   
 [使用 DataView 進行篩選](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)   
 [Sorting Data](../../../../ocs/visual-basic/programming-guide/concepts/linq/sorting-data.md)