---
title: "DataTableReader | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTableReader
<xref:System.Data.DataTableReader> 會以一個或多個唯讀順向結果集的形式來呈現 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的內容。  
  
 從 **DataTable** 建立 **DataTableReader** 時，得到的 **DataTableReader** 物件會包含一個結果集，其資料則與建立該結果集的 **DataTable** 資料相同，但已標記成刪除的所有資料列不在此限。  會以原始的 **DataTable** 順序顯示資料行。  
  
 如果 **DataTableReader** 是透過呼叫 <xref:System.Data.DataSet.CreateDataReader%2A> 而建立，它可能會包含多個結果集。  結果的順序即是 **DataSet** 物件之 <xref:System.Data.DataSet.Tables%2A> 集合中的 **DataTables** 順序。  
  
## 在本節中  
 [建立 DataReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 討論如何建立 **DataTableReader** 物件。  
  
 [巡覽 DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 說明如何使用 **Read** 方法來移動 **DataTableReader** 的內容。  
  
## 請參閱  
 [擷取和修改 ADO.NET 中的資料](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)