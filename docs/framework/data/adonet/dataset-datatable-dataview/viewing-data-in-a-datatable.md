---
title: "檢視 DataTable 中的資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 檢視 DataTable 中的資料
您可以使用 **DataTable** 的 **Rows** 和 **Columns** 集合，以存取 <xref:System.Data.DataTable> 的內容。  也可以根據條件 \(包括搜尋條件、排序順序及資料列狀態\)，使用 <xref:System.Data.DataTable.Select%2A> 方法傳回 **DataTable** 中資料的子集。  此外，使用主索引鍵值來搜尋某個資料列時，可以使用 **DataRowCollection** 的 <xref:System.Data.DataRowCollection.Find%2A> 方法。  
  
 **DataTable** 物件的 **Select** 方法會傳回符合指定條件的一組 <xref:System.Data.DataRow> 物件。  **Select** 使用篩選條件運算式、排序運算式和 **DataViewRowState** 的選擇性引數。  篩選條件運算式會根據 **DataColumn** 值 \(例如 `LastName = 'Smith'`\)，辨識要傳回的資料列。  排序運算式會遵照標準的 SQL 慣例排序資料行，例如 `LastName ASC, FirstName ASC`。  如需撰寫運算式的相關規則，請參閱 **DataColumn** 類別的 <xref:System.Data.DataColumn.Expression%2A> 屬性。  
  
> [!TIP]
>  如果您正在執行多個對 **DataTable** 之 **Select** 方法的呼叫，則可藉由先建立 **DataTable** 的 <xref:System.Data.DataView> 以增加效能。  建立 **DataView** 可索引資料表的資料列。  **Select** 方法接下來便可使用該索引，這樣可大幅減少產生查詢結果的時間。  如需建立 **DataTable** 之 **DataView** 的相關資訊，請參閱 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)。  
  
 **Select** 方法會依據 <xref:System.Data.DataViewRowState>，判斷要檢視或管理的資料列版本。  下表即說明可能的 **DataViewRowState** 列舉值。  
  
|DataViewRowState 值|描述|  
|------------------------|--------|  
|**CurrentRows**|目前資料列，包括未變更、加入和修改過的資料列。|  
|**Deleted**|刪除的資料列。|  
|**ModifiedCurrent**|目前的版本，即為原始資料的修改版本  \(請參閱 **ModifiedOriginal**\)。|  
|**ModifiedOriginal**|所有修改資料列的原始版本。  目前版本可透過 **ModifiedCurrent** 來使用。|  
|**Added**|新的資料列。|  
|**無**|無。|  
|**OriginalRows**|原始資料列，包括未變更和刪除的資料列。|  
|**Unchanged**|未變更的資料列。|  
  
 下列範例中，**DataSet** 物件已經過篩選，因此您只需使用將 **DataViewRowState** 設為 **CurrentRows** 的資料列。  
  
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
  
 您可以使用 **Select** 方法傳回具有不同的 **RowState** 值或欄位值的資料列。  下列範例將傳回會參考所有已刪除之資料列的 **DataRow** 陣列，並傳回另一個會參考所有資料列的 **DataRow** 陣列 \(以 **CustLName** 排序\)，其中 **CustID** 資料行大於 5。  如需如何在 **Deleted** 資料列中檢視資訊的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
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
  
## 請參閱  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataViewRowState>   
 [管理 DataTable 中的資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)