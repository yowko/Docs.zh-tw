---
title: 刪除 DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 3f48339539f08bbc1c2c15035741375bd9ade553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784717"
---
# <a name="datarow-deletion"></a>刪除 DataRow
有兩種方法可用來刪除<xref:System.Data.DataRow> <xref:System.Data.DataTable>物件中的物件： <xref:System.Data.DataRowCollection>物件的**Remove** <xref:System.Data.DataRow.Delete%2A>方法，以及**DataRow**物件的方法。 方法會從**DataRowCollection** <xref:System.Data.DataRow.Delete%2A>刪除**DataRow** ，而方法只會標示要刪除的資料列。 <xref:System.Data.DataRowCollection.Remove%2A> 當應用程式呼叫**AcceptChanges**方法時，就會發生實際的移除。 您可以使用 <xref:System.Data.DataRow.Delete%2A>，以程式設計方式檢查有哪些資料列標示為要刪除，然後再將其實際移除。 將資料列標記為要刪除時，會將其 <xref:System.Data.DataRow.RowState%2A> 屬性設為 <xref:System.Data.DataRow.Delete%2A>。  
  
 在 foreach 迴圈中不應呼叫 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A>，而應逐一查看 <xref:System.Data.DataRowCollection> 物件。 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A> 都不會修改集合的狀態。  
  
 <xref:System.Data.DataSet>當使用或**DataTable**搭配**DataAdapter**和關聯式資料來源時，請使用**DataRow**的**Delete**方法來移除資料列。 **Delete**方法會將資料列標示為已在**DataSet**或**DataTable**中**刪除**，但不會將它移除。 相反地，當**DataAdapter**遇到標記為**已刪除**的資料列時，它會執行其**DeleteCommand**方法，以刪除資料來源中的資料列。 然後，您可以使用**AcceptChanges**方法來永久移除該資料列。 如果您使用 [**移除**] 來刪除資料列，就會從資料表中移除該資料列，但**DataAdapter**不會刪除資料來源中的資料列。  
  
 **DataRowCollection**的**Remove**方法會採用**DataRow**做為引數，並將它從集合中移除，如下列範例所示。  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 相反地，下列範例將示範如何在**DataRow**上呼叫**Delete**方法，以將其**RowState**變更為**Deleted**。  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 如果將資料列標示為要刪除，而且您呼叫**datatable**物件的**AcceptChanges**方法，則會從**datatable**移除該資料列。 相反地，如果您呼叫**RejectChanges**，則資料列的**RowState**會還原為標示為**已刪除**之前的內容。  
  
> [!NOTE]
> 如果**加入**了**DataRow**的**RowState** ，表示它剛加入至資料表，然後將它標示為**已刪除**，則會從資料表中移除它。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [在 DataTable 中操作資料](manipulating-data-in-a-datatable.md)
- [ADO.NET 概觀](../ado-net-overview.md)
