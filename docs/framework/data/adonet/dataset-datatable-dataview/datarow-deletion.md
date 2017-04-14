---
title: "DataRow 刪除 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# DataRow 刪除
有兩種方法可讓您從 <xref:System.Data.DataTable> 物件刪除 <xref:System.Data.DataRow> 物件：<xref:System.Data.DataRowCollection> 物件的 **Remove** 方法和 **DataRow** 物件的 <xref:System.Data.DataRow.Delete%2A> 方法。  <xref:System.Data.DataRowCollection.Remove%2A> 方法可從 **DataRowCollection** 刪除 **DataRow**，而 <xref:System.Data.DataRow.Delete%2A> 方法只能標記要刪除的資料列。  當應用程式呼叫 **AcceptChanges** 方法時才會發生真正的移除作業。  您可以使用 <xref:System.Data.DataRow.Delete%2A>，以程式設計方式檢查有哪些資料列標示為要刪除，然後再將其實際移除。  將資料列標記為要刪除時，會將其 <xref:System.Data.DataRow.RowState%2A> 屬性設為 <xref:System.Data.DataRow.Delete%2A>。  
  
 在 foreach 迴圈中不應呼叫 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A>，而應逐一查看 <xref:System.Data.DataRowCollection> 物件。  <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A> 都不會修改集合的狀態。  
  
 <xref:System.Data.DataSet> 或 **DataTable** 與 **DataAdapter** 和關聯式資料來源搭配使用時，請使用 **DataRow** 的 **Delete** 方法來移除資料列。  **Delete** 方法會在 **DataSet** 或 **DataTable** 中將資料列標記為 **Deleted**，但是不會將它移除。  相反地，當 **DataAdapter** 遇到標記為 **Deleted** 的資料列時，它會執行自己的 **DeleteCommand** 方法來刪除資料來源中的資料列。  然後就可以使用 **AcceptChanges** 方法，將資料列永久移除。  如果您使用 **Remove** 來刪除資料列，會將資料表中的資料列完全移除，但是 **DataAdapter** 則不會刪除資料來源中的資料列。  
  
 **DataRowCollection** 的 **Remove** 方法將 **DataRow** 視為引數，並且將它從集合中移除，如下列範例所示。  
  
```vb  
workTable.Rows.Remove(workRow)  
  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 相反的，下列範例示範如何在 **DataRow** 呼叫 **Delete** 方法，將其 **RowState** 變更為 **Deleted**。  
  
```vb  
workRow.Delete  
  
```  
  
```csharp  
workRow.Delete();  
```  
  
 如果資料列被標示為刪除，而且您呼叫 **DataTable** 物件的 **AcceptChanges** 方法，則該資料列將從 **DataTable** 中移除。  相反的，如果您呼叫 **RejectChanges**，資料列的 **RowState** 將還原成被標示為 **Deleted** 之前的狀態。  
  
> [!NOTE]
>  如果 **DataRow** 的 **RowState** 是 **Added**，表示它才剛加入至資料表，接下來它將被標記為 **Deleted**，表示已從資料表中移除。  
  
## 請參閱  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataRowCollection>   
 <xref:System.Data.DataTable>   
 [管理 DataTable 中的資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)