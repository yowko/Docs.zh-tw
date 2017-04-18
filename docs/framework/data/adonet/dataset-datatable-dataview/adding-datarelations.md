---
title: "加入 DataRelations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 加入 DataRelations
在包含多個 <xref:System.Data.DataTable> 物件的 <xref:System.Data.DataSet> 中，可以使用 <xref:System.Data.DataRelation> 物件建立資料表間的關聯性、巡覽資料表，並從相關資料表傳回子資料列或父資料列。  
  
 建立 **DataRelation** 所需的引數是即將建立之 **DataRelation** 的名稱，以及由一或多個 <xref:System.Data.DataColumn> 參考 \(參考關聯性中做為父資料行和子資料行的資料行\) 所組成的陣列。  建立 **DataRelation** 後，您可以使用它在資料表間巡覽並擷取數值。  
  
 將 **DataRelation** 加入 <xref:System.Data.DataSet> 時，預設會將 <xref:System.Data.UniqueConstraint> 加入父資料表，並將 <xref:System.Data.ForeignKeyConstraint> 加入子資料表。  如需這些預設條件約束的詳細資訊，請參閱 [DataTable 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)。  
  
 下列程式碼範例在 <xref:System.Data.DataSet> 中使用兩個 <xref:System.Data.DataTable> 物件來建立 **DataRelation**。  每個 <xref:System.Data.DataTable> 都包含一個名為 **CustID** 的資料行，做為兩個 <xref:System.Data.DataTable> 物件間的連結。  此範例會將一個 **DataRelation** 加入 <xref:System.Data.DataSet> 的 **Relations** 集合中。  範例中第一個引數指定即將被建立的 **DataRelation** 的名稱，  第二個引數設定父 **DataColumn**，第三個引數則設定子 **DataColumn**。  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 **DataRelation** 也具有 **Nested** 屬性，當設為 **true**，並且使用 <xref:System.Data.DataSet.WriteXml%2A> 將父資料表的相關資料列撰寫為 XML 項目時，會在父資料表的相關資料列中巢狀化子資料表的資料列。  如需詳細資訊，請參閱[在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
## 請參閱  
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)