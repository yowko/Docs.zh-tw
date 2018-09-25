---
title: 在 DataTable 中檢視資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: de745633060dd4f7b1610492d0ff57ec7a4f545b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46710705"
---
# <a name="viewing-data-in-a-datatable"></a>在 DataTable 中檢視資料
您可以存取的內容<xref:System.Data.DataTable>利用**資料列**並**資料行**的集合**DataTable**。 您也可以使用<xref:System.Data.DataTable.Select%2A>方法來傳回中的資料子集**DataTable**根據包括搜尋條件的準則，排序順序和資料列狀態。 此外，您可以使用<xref:System.Data.DataRowCollection.Find%2A>方法**DataRowCollection**時搜尋特定的資料列，使用主索引鍵值。  
  
 **選取 **方法**DataTable**物件會傳回一組<xref:System.Data.DataRow>符合指定的準則的物件。 **選取 **採用的篩選條件運算式，排序運算式的選擇性引數和**DataViewRowState**。 篩選條件運算式會識別要根據傳回的資料列**DataColumn**值，例如`LastName = 'Smith'`。 排序運算式會遵照標準的 SQL 慣例排序資料行，例如 `LastName ASC, FirstName ASC`。 如需有關撰寫運算式的規則，請參閱<xref:System.Data.DataColumn.Expression%2A>的屬性**DataColumn**類別。  
  
> [!TIP]
>  如果您正在執行的呼叫次數**選取 **方法**DataTable**，您可以藉由先建立提升效能<xref:System.Data.DataView>如**DataTable**。 建立**DataView**資料表的資料列的索引。 **選取**方法則配備編製索引，大幅減少產生查詢結果的時間。 如需建立資訊**DataView** for **DataTable**，請參閱[Dataview](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)。  
  
 **選取 **方法會判斷要檢視或管理的資料列的版本將會根據<xref:System.Data.DataViewRowState>。 下表描述可能**DataViewRowState**列舉值。  
  
|DataViewRowState 值|描述|  
|----------------------------|-----------------|  
|**CurrentRows**|目前資料列，包括未變更、加入和修改過的資料列。|  
|**刪除**|刪除的資料列。|  
|**ModifiedCurrent**|目前的版本，即為原始資料的修改版本 (請參閱**ModifiedOriginal**。)|  
|**ModifiedOriginal**|所有修改資料列的原始版本。 目前的版本是可透過**ModifiedCurrent**。|  
|**加入**|新的資料列。|  
|**無**|無。|  
|**OriginalRows**|原始資料列，包括未變更和刪除的資料列。|  
|**未變更**|未變更的資料列。|  
  
 在下列範例中，**資料集**物件會經過篩選，因此您只需使用資料列其**DataViewRowState**設定為**CurrentRows**。  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 **選取 **方法可用來傳回具有不同的資料列**RowState**值或欄位值。 下列範例會傳回**DataRow**參考已刪除，並傳回另一個的所有資料列的陣列**DataRow**陣列參考的所有資料列，依**CustLName**，其中**CustID**資料行大於 5。 如需有關如何檢視中的資訊資訊**Deleted**資料列中，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
