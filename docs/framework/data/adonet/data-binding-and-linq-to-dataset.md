---
title: "資料繫結和 LINQ to DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 資料繫結和 LINQ to DataSet
「*資料繫結*」\(Data Binding\) 是指在應用程式 UI 與商務邏輯之間建立連接的程序。  如果繫結具有正確的設定而且資料提供了適當的通知，當資料變更其值時，繫結至資料的項目就會自動反映變更。  <xref:System.Data.DataSet> 是記憶體中的資料表示，可提供一致的關聯式程式撰寫模型 \(Programming Model\)，不論它所包含的資料來源為何都一樣。  ADO.NET 2.0 <xref:System.Data.DataView> 可讓您排序和篩選儲存在 <xref:System.Data.DataTable> 中的資料。  這項功能通常用於資料繫結的應用程式。  您可以透過使用 <xref:System.Data.DataView>，以不同排序順序公開 \(Expose\) 資料表中的資料，而且可以按照資料列狀態或根據篩選條件運算式來篩選資料。  如需 <xref:System.Data.DataView> 物件的詳細資訊，請參閱 [DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可讓開發人員使用 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]，針對 <xref:System.Data.DataSet> 建立複雜且功能強大的查詢。  但是，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢會傳回 <xref:System.Data.DataRow> 物件的列舉值，而這對於繫結案例而言較不好用。若要使繫結動作更簡易，您可以從 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 建立 <xref:System.Data.DataView>。  雖然這個 <xref:System.Data.DataView> 使用查詢中指定的篩選和排序方式，但是較適合資料繫結。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 擴充了 <xref:System.Data.DataView> 的功能，因為其提供 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 運算式的篩選和排序功能，如此便能完成比字串類篩選和排序更複雜、更強大的篩選和排序作業。  
  
 請注意，<xref:System.Data.DataView> 代表查詢本身而不是查詢頂端的檢視。  <xref:System.Data.DataView> 會繫結至 UI 控制項 \(例如 <xref:System.Windows.Forms.DataGrid> 或 <xref:System.Windows.Forms.DataGridView>\)，以便提供簡單的資料繫結模型。  <xref:System.Data.DataView> 也可以從 <xref:System.Data.DataTable> 中建立，以便提供該資料表的預設檢視。  
  
## 本章節內容  
 [建立 DataView 物件](../../../../docs/framework/data/adonet/creating-a-dataview-object-linq-to-dataset.md)  
 提供有關建立 <xref:System.Data.DataView> 的資訊。  
  
 [使用 DataView 進行篩選](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 說明如何使用 <xref:System.Data.DataView> 進行篩選。  
  
 [使用 DataView 進行排序](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)  
 說明如何使用 <xref:System.Data.DataView> 進行排序。  
  
 [查詢 DataView 中的 DataRowView 集合](../../../../docs/framework/data/adonet/querying-the-datarowview-collection-in-a-dataview.md)  
 提供查詢由 <xref:System.Data.DataView> 所公開之 <xref:System.Data.DataRowView> 集合的相關資訊。  
  
 [DataView 效能](../../../../docs/framework/data/adonet/dataview-performance.md)  
 提供有關 <xref:System.Data.DataView> 和效能的資訊。  
  
 [HOW TO：將 DataView 物件繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/data/adonet/how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 說明如何將 <xref:System.Data.DataView> 物件繫結至 <xref:System.Windows.Forms.DataGridView>。  
  
## 請參閱  
 [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)