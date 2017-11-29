---
title: "刪除 DataRow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f9eb89d711cbf66f3b6816e597c14359be1f3639
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="datarow-deletion"></a>刪除 DataRow
有兩種方法可用來刪除<xref:System.Data.DataRow>物件從<xref:System.Data.DataTable>物件：**移除**方法<xref:System.Data.DataRowCollection>物件，而<xref:System.Data.DataRow.Delete%2A>方法**DataRow**物件。 而<xref:System.Data.DataRowCollection.Remove%2A>方法刪除**DataRow**從**DataRowCollection**、<xref:System.Data.DataRow.Delete%2A>方法只會標記為要刪除的資料列。 當應用程式呼叫時，就會發生實際移除**AcceptChanges**方法。 您可以使用 <xref:System.Data.DataRow.Delete%2A>，以程式設計方式檢查有哪些資料列標示為要刪除，然後再將其實際移除。 將資料列標記為要刪除時，會將其 <xref:System.Data.DataRow.RowState%2A> 屬性設為 <xref:System.Data.DataRow.Delete%2A>。  
  
 在 foreach 迴圈中不應呼叫 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A>，而應逐一查看 <xref:System.Data.DataRowCollection> 物件。 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A> 都不會修改集合的狀態。  
  
 當使用<xref:System.Data.DataSet>或**DataTable**搭配**DataAdapter**和關聯式資料來源，使用**刪除**方法**DataRow**若要移除的資料列。 **刪除**方法會標示資料列做為**刪除**中**資料集**或**DataTable**但不會移除它。 相反地，當**DataAdapter**遇到標記為一個資料列**刪除**，它會執行其**DeleteCommand**方法來刪除資料來源的資料列。 資料列然後可以永久移除使用**AcceptChanges**方法。 如果您使用**移除**刪除資料列，從資料表中，完全移除資料列但**DataAdapter**將不會刪除資料來源中的資料列。  
  
 **移除**方法**DataRowCollection**採用**DataRow**做為引數和它從集合中移除，如下列範例所示。  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 相反地，下列範例示範如何呼叫**刪除**方法**DataRow**若要變更其**RowState**至**刪除**.  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 如果資料列被標示為刪除，而且您呼叫**AcceptChanges**方法**DataTable**物件、 資料列會移除從**DataTable**。 相反地，如果您呼叫**RejectChanges**、 **RowState**的資料列會還原為之前被標示為**刪除**。  
  
> [!NOTE]
>  如果**RowState**的**DataRow**是**Added**，亦即它剛新增到資料表，它會標示為**刪除**，它是從資料表中移除。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
