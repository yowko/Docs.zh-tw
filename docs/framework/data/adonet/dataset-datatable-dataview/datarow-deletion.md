---
title: 刪除 DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 57f51ada00bf24617ca3e295a010aae64f0aa849
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879862"
---
# <a name="datarow-deletion"></a>刪除 DataRow
有兩種方法可用來刪除<xref:System.Data.DataRow>物件從<xref:System.Data.DataTable>物件：**移除**方法<xref:System.Data.DataRowCollection>物件，而<xref:System.Data.DataRow.Delete%2A>方法**DataRow**物件。 然而<xref:System.Data.DataRowCollection.Remove%2A>方法會刪除**DataRow**從**DataRowCollection**，則<xref:System.Data.DataRow.Delete%2A>方法只能標記要刪除的資料列。 當應用程式呼叫時，就會發生真正的移除作業**AcceptChanges**方法。 您可以使用 <xref:System.Data.DataRow.Delete%2A>，以程式設計方式檢查有哪些資料列標示為要刪除，然後再將其實際移除。 將資料列標記為要刪除時，會將其 <xref:System.Data.DataRow.RowState%2A> 屬性設為 <xref:System.Data.DataRow.Delete%2A>。  
  
 在 foreach 迴圈中不應呼叫 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A>，而應逐一查看 <xref:System.Data.DataRowCollection> 物件。 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A> 都不會修改集合的狀態。  
  
 使用時<xref:System.Data.DataSet>或是**DataTable**搭配**DataAdapter**和關聯式資料來源，使用**刪除**方法**DataRow**若要移除的資料列。 **刪除**方法會將資料列做為標記**Deleted**中**資料集**或**DataTable**但不會移除它。 相反地，當**DataAdapter**遇到標記為一個資料列**已刪除**，它會執行其**DeleteCommand**方法來刪除資料來源的資料列。 資料列可以再永久移除使用**AcceptChanges**方法。 如果您使用**移除**若要刪除的資料列，資料列完全移除資料表，但**DataAdapter**將不會刪除在資料來源的資料列。  
  
 **移除**方法**DataRowCollection**採用**DataRow**做為引數並將它移除，從集合中，如下列範例所示。  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 相反地，下列範例示範如何呼叫**刪除**方法**DataRow**若要變更其**RowState**至**Deleted**.  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 如果資料列被標示為刪除，而且您呼叫**AcceptChanges**方法**DataTable**物件，會移除資料列，從**DataTable**。 相反地，如果您呼叫**RejectChanges**，則**RowState**的資料列會還原為之前被標示為**Deleted**。  
  
> [!NOTE]
>  如果**RowState**的**DataRow**會**Added**，亦即它剛新增至資料表，則會標記為**Deleted**，它是從資料表中移除。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
