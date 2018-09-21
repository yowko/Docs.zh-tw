---
title: 資料列狀態和資料列版本
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 629e8b0bea1cd5c1dd80409acd7c03e0e033b5bc
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492979"
---
# <a name="row-states-and-row-versions"></a>資料列狀態和資料列版本
ADO.NET 使用資料列狀態和版本來管理資料表中的資料列。 資料列狀態表示資料列的狀態；修改資料列時，資料列版本會維護存放在資料列中的值，包括目前值、原始值和預設值。 例如，修改資料列中的資料行後，資料列的狀態為 `Modified`，並有兩個資料列版本：`Current` (包含目前的資料列值) 和 `Original` (包含修改資料行之前的資料列值)。  
  
 每個 <xref:System.Data.DataRow> 物件都有 <xref:System.Data.DataRow.RowState%2A> 屬性，您可以檢查該屬性來判斷資料列的目前狀態。 下列表格簡短說明每個 `RowState` 列舉值。  
  
|RowState 值|描述|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|自上次呼叫 `AcceptChanges` 或由 `DataAdapter.Fill` 建立資料列後，沒有任何變更。|  
|<xref:System.Data.DataRowState.Added>|資料列已加入至資料表，但尚未呼叫 `AcceptChanges`。|  
|<xref:System.Data.DataRowState.Modified>|有些資料列項目已變更。|  
|<xref:System.Data.DataRowState.Deleted>|已從資料表中刪除資料列，但是尚未呼叫 `AcceptChanges`。|  
|<xref:System.Data.DataRowState.Detached>|資料列不屬於任何 `DataRowCollection`。 已將新建立資料列的 `RowState` 設為 `Detached`。 呼叫 `DataRow` 方法以將新 `DataRowCollection` 加入至 `Add` 後，`RowState` 屬性的值會設為 `Added`。<br /><br /> 使用 `Detached` 方法，或是先使用 `DataRowCollection` 方法再使用 `Remove` 方法，從 `Delete` 中移除的資料列也會設定為 `AcceptChanges`。|  
  
 在 `AcceptChanges`、<xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 上呼叫 <xref:System.Data.DataRow> 時，具有 `Deleted` 資料列狀態的所有資料列都將移除。 其餘資料列的狀態將設為 `Unchanged`，而 `Original` 資料列版本中的值將以 `Current` 資料列版本值覆寫。 在呼叫 `RejectChanges` 時，所有狀態為 `Added` 的資料列都會移除。 其餘資料列的狀態將設為 `Unchanged`，而 `Current` 資料列版本中的值將以 `Original` 資料列版本值覆寫。  
  
 您可以檢視資料列的不同資料列版本，方法是使用資料行參考傳遞 <xref:System.Data.DataRowVersion> 參數，如下列範例所示。  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 下列表格簡短說明每個 `DataRowVersion` 列舉值。  
  
|DataRowVersion 值|描述|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|資料列的目前值。 對於 `RowState` 為 `Deleted` 的資料列，此資料列版本不存在。|  
|<xref:System.Data.DataRowVersion.Default>|指定資料列的預設資料列版本。 `Added`、`Modified` 或 `Deleted` 資料列的預設資料列版本為 `Current`。 `Detached` 資料列的預設資料列版本為 `Proposed`。|  
|<xref:System.Data.DataRowVersion.Original>|資料列的原始值。 對於 `RowState` 為 `Added` 的資料列，此資料列版本不存在。|  
|<xref:System.Data.DataRowVersion.Proposed>|資料列的建議值。 這個資料列版本存在於資料列的編輯作業期間，或是當資料列不屬於 `DataRowCollection` 時。|  
  
 您可以測試 `DataRow` 是否具有特定的資料列版本，方法是呼叫 <xref:System.Data.DataRow.HasVersion%2A> 方法，並將 `DataRowVersion` 當做引數傳遞。 例如，`DataRow.HasVersion(DataRowVersion.Original)` 將在呼叫 `false` 之前，針對所新建立的資料列傳回 `AcceptChanges`。  
  
 下列程式碼範例顯示資料表內所有已刪除的資料列中的值。 `Deleted` 資料列沒有 `Current` 資料列版本，因此您必須在存取資料行值時傳遞 `DataRowVersion.Original`。  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [DataAdapter 和 DataReader](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
