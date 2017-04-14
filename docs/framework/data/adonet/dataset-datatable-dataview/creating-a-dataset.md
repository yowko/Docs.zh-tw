---
title: "建立 DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 建立 DataSet
您可呼叫 <xref:System.Data.DataSet> 建構函式 \(Constructor\) 來建立 <xref:System.Data.DataSet> 的執行個體 \(Instance\)。  選擇性地指定名稱引數。  如果您不指定 <xref:System.Data.DataSet> 的名稱，則名稱會設定為 "NewDataSet"。  
  
 您也可以根據現有的 <xref:System.Data.DataSet> 建立新的 <xref:System.Data.DataSet>。  新的 <xref:System.Data.DataSet> 可以是：現有 <xref:System.Data.DataSet> 的完整複本；<xref:System.Data.DataSet> 的複製，該項目複製關聯式架構或結構描述，但是不包含任何來自現有 <xref:System.Data.DataSet> 的資料；或 <xref:System.Data.DataSet> 的子集，其中只包含來自現有的 <xref:System.Data.DataSet> 且使用 <xref:System.Data.DataSet.GetChanges%2A> 方法修改過的資料列。  如需詳細資訊，請參閱[複製 DataSet 內容](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)。  
  
 下列程式碼範例示範如何建構 <xref:System.Data.DataSet> 的執行個體。  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## 請參閱  
 [從 DataAdapter 填入資料集](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)