---
title: 刪除 DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 2092d7319a398bbdeaef764d677818f78ddf9de9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153348"
---
# <a name="datarow-deletion"></a>刪除 DataRow

您可以使用兩種方法 <xref:System.Data.DataRow> 從物件刪除物件 <xref:System.Data.DataTable> ：物件的 **Remove** 方法 <xref:System.Data.DataRowCollection> ，以及 <xref:System.Data.DataRow.Delete%2A> **DataRow** 物件的方法。 方法會 <xref:System.Data.DataRowCollection.Remove%2A> 從**DataRowCollection**中刪除**DataRow** ，但是此 <xref:System.Data.DataRow.Delete%2A> 方法只會標示要刪除的資料列。 當應用程式呼叫 **AcceptChanges** 方法時，就會發生實際的移除動作。 您可以使用 <xref:System.Data.DataRow.Delete%2A>，以程式設計方式檢查有哪些資料列標示為要刪除，然後再將其實際移除。 將資料列標記為要刪除時，會將其 <xref:System.Data.DataRow.RowState%2A> 屬性設為 <xref:System.Data.DataRow.Delete%2A>。  
  
 在 foreach 迴圈中不應呼叫 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A>，而應逐一查看 <xref:System.Data.DataRowCollection> 物件。 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A> 都不會修改集合的狀態。  
  
 使用 <xref:System.Data.DataSet> 或**DataTable**搭配**DataAdapter**和關聯式資料來源時，請使用**DataRow**的**Delete**方法來移除資料列。 **Delete**方法會將資料列標示為**已刪除**的**資料集**或**DataTable** ，但不會將它移除。 相反地，當 **DataAdapter** 遇到標示為 **Deleted**的資料列時，它會執行其 **DeleteCommand** 方法來刪除資料來源中的資料列。 然後，您可以使用 **AcceptChanges** 方法永久移除該資料列。 如果您使用 [ **移除** ] 來刪除資料列，則會從資料表中移除資料列，但 **DataAdapter** 不會刪除資料來源中的資料列。  
  
 **DataRowCollection**的**Remove**方法會將**DataRow**視為引數，並將它從集合中移除，如下列範例所示。  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 相反地，下列範例示範如何在**DataRow**上呼叫**Delete**方法，以將其**RowState**變更為**Deleted**。  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 如果資料列標示為刪除，而且您呼叫**datatable**物件的**AcceptChanges**方法，就會從**datatable**中移除該資料列。 相反地，如果您呼叫 **RejectChanges**，資料列的 **RowState** 會還原為標示為 **已刪除**之前的內容。  
  
> [!NOTE]
> 如果**加入** **DataRow**的**RowState** ，表示它剛加入資料表中，然後標示為**已刪除**，則會從資料表中移除它。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [在 DataTable 中操作資料](manipulating-data-in-a-datatable.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
