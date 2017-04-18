---
title: "查詢 DataView 中的 DataRowView 集合 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 查詢 DataView 中的 DataRowView 集合
<xref:System.Data.DataView> 公開可列舉之 <xref:System.Data.DataRowView> 物件的集合。  <xref:System.Data.DataRowView> 代表 <xref:System.Data.DataRow> 的自訂檢視並會在控制項中顯示該 <xref:System.Data.DataRow> 的特定版本。  只有一個 <xref:System.Data.DataRow> 的版本能透過控制項顯示，例如 <xref:System.Windows.Forms.DataGridView>。  您可以透過 <xref:System.Data.DataRowView> 的 <xref:System.Data.DataRowView.Row%2A> 屬性，存取 <xref:System.Data.DataRowView> 公開的 <xref:System.Data.DataRow>。  使用 <xref:System.Data.DataRowView> 檢視值時，<xref:System.Data.DataView.RowStateFilter%2A> 屬性會判斷要公開的是哪一個基礎 <xref:System.Data.DataRow> 的資料列版本。  如需使用 <xref:System.Data.DataRow> 存取不同資料列版本的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  因為 <xref:System.Data.DataView> 公開的 <xref:System.Data.DataRowView> 物件集合是可列舉的，所以您可以使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 對其進行查詢。  
  
 下列範例會查詢 `Product` 資料表中以紅色顯示的產品並根據該查詢建立資料表。  <xref:System.Data.DataView> 會根據資料表建立並且 <xref:System.Data.DataView.RowStateFilter%2A> 屬性會設為在刪除和修改的資料行進行篩選。  接著就會使用 <xref:System.Data.DataView> 做為 LINQ 查詢中的來源，而已經修改和刪除的 <xref:System.Data.DataRowView> 物件會繫結至 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 下列範例會從繫結至 <xref:System.Windows.Forms.DataGridView> 控制項的檢視建立產品資料表。  針對以紅色顯示的產品查詢會在 <xref:System.Data.DataView> 中進行，並且排序後的結果會繫結至 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## 請參閱  
 [資料繫結和 LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)