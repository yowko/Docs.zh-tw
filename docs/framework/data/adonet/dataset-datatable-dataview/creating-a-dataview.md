---
title: "建立 DataView | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 建立 DataView
建立 <xref:System.Data.DataView> 的方法有兩種。  您可以使用 **DataView** 建構函式，或建立 <xref:System.Data.DataTable> 之 <xref:System.Data.DataTable.DefaultView%2A> 屬性的參考。  **DataView** 建構函式可以是空的，也可採用任一 **DataTable** 做為單一引數，或以 **DataTable** 配合篩選準則、排序準則和資料列狀態篩選。  如需其他能與 **DataView** 搭配使用之引數的詳細資訊，請參閱 [排序和篩選資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)。  
  
 由於在建立 **DataView** 時和修改任一 **Sort**、**RowFilter** 或 **RowStateFilter** 屬性時，都會建置 **DataView** 的索引，所以您可在建立 **DataView** 時，透過提供任何初始排序順序或篩選準則做為建構函式引數的方式，來達到最佳效能。  如果建立 **DataView** 而不指定排序或篩選準則，然後設定 **Sort**、**RowFilter** 或 **RowStateFilter** 屬性，則日後至少會建置索引兩次：一次是建立 **DataView** 時，另一次是修改任何排序或篩選屬性時。  
  
 請注意，如果用來建立 **DataView** 的建構函式不擷取任何引數，則您必須先設定 **Table** 屬性才能使用 **DataView**。  
  
 下列程式碼範例示範如何使用 **DataView** 建構函式建立 **DataView**。  **DataTable** 中一併提供 **RowFilter**、**Sort** 資料行和 **DataViewRowState**。  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 下列程式碼範例示範如何使用資料表的 **DefaultView** 屬性，取得對 **DataTable** 預設 **DataView** 的參考。  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## 請參閱  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [排序和篩選資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)