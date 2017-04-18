---
title: "DataView | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataView
<xref:System.Data.DataView> 允許您為儲存在 <xref:System.Data.DataTable> 內的資料建立不同的檢視，這是資料繫結應用程式中常用的功能。  **DataView** 可讓您以不同排序順序公開資料表中的資料，也可按資料列狀態或篩選條件運算式來篩選資料。  
  
 **DataView** 會在基礎 **DataTable** 中提供動態的資料檢視：內容、順序和成員資格會在發生變更時反映變更。  此行為不同於 **DataTable** 的 **Select** 方法，它是基於特定的篩選條件及 \(或\) 排序順序，從資料表傳回 <xref:System.Data.DataRow> 陣列：這個內容反映基礎資料表的變更，但其成員資格和順序仍維持靜態。  **DataView** 因具有動態功能，所以相當適合用於資料繫結應用程式。  
  
 **DataView** 提供您單一資料組的動態檢視，與資料庫檢視很類似，您可以對其套用不同的排序和篩選準則。  然而，不像資料庫檢視，您無法將 **DataView** 當成資料表使用，也不能提供聯結資料表檢視。  此外，您也不能排除來源資料表中的資料行，也不能附加來源資料表中不存在的資料行 \(如計算資料行\)。  
  
 您可以使用 <xref:System.Data.DataView.DataViewManager%2A> 管理 **DataSet** 內所有資料表的檢視設定。  **DataViewManager** 提供的簡單方法可讓您管理每個資料表的預設檢視設定。  將控制項繫結至一個以上的 **DataSet** 資料表時，理想的方式是選擇繫結至 **DataViewManager**。  
  
## 在本節中  
 [建立 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 說明如何建立 **DataTable** 的 **DataView**。  
  
 [排序和篩選資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 說明如何設定 **DataView** 的屬性，傳回符合特定篩選準則的資料列子集，或以特定排序順序傳回資料。  
  
 [DataRow 和 DataRowView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 說明如何存取 **DataView** 公開 \(Expose\) 的資料。  
  
 [尋找資料列](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 說明如何在 **DataView** 內尋找特定資料列。  
  
 [ChildView 和關聯性](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 說明如何使用 **DataView**，從父子關係建立資料檢視。  
  
 [修改 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 說明如何透過 **DataView** 修改基礎 **DataTable** 中的資料，包含啟用和停用更新。  
  
 [處理 DataView 事件](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 說明如何使用 **ListChanged** 事件接收 **DataView** 的內容或順序更新時的告知。  
  
 [管理 DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 說明如何使用 **DataViewManager** 來管理 **DataSet** 中每個資料表的 **DataView** 設定。  
  
## 相關章節  
 [ASP.NET Web Applications](http://msdn.microsoft.com/zh-tw/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 提供 ASP.NET 應用程式、Web Form 和 Web 服務的建立概觀和詳細的步驟程序。  
  
 [Windows Applications](http://msdn.microsoft.com/zh-tw/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 提供有關使用 Windows Form 和主控台應用程式的詳細資訊。  
  
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 說明 **DataSet** 物件，以及如何使用它來管理應用程式資料。  
  
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 說明 **DataTable** 物件，以及如何將它單獨使用或當成 **DataSet** 的一部分使用以管理應用程式資料。  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 說明 ADO.NET 的架構和元件，以及如何使用 ADO.NET 來存取現有資料來源和管理應用程式資料。  
  
## 請參閱  
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)