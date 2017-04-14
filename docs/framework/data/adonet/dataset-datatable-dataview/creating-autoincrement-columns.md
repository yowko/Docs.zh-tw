---
title: "建立 AutoIncrement 資料行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 建立 AutoIncrement 資料行
若要確保資料行的值是唯一的，您可以在將新資料列加入至資料表時，將資料行值設為自動累加。  若要建立自動遞增的 <xref:System.Data.DataColumn>，請將資料行的 <xref:System.Data.DataColumn.AutoIncrement%2A> 屬性設為 **true**。  <xref:System.Data.DataColumn> 接下來會以 <xref:System.Data.DataColumn.AutoIncrementSeed%2A> 屬性中所定義的值開頭，並在每個資料列增加 **AutoIncrement** 資料行值，而此值是以資料行之 <xref:System.Data.DataColumn.AutoIncrementStep%2A> 屬性中所定義的值為準。  
  
 若為 **AutoIncrement** 資料行，則建議將 **DataColumn** 的 <xref:System.Data.DataColumn.ReadOnly%2A> 屬性設為 **true**。  
  
 下列範例示範如何建立以 200 值做為開頭的資料行，並以增量 3 累加。  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## 請參閱  
 <xref:System.Data.DataColumn>   
 [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)