---
title: Load 方法
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 82f840ab7dd26a4888ebf024d696f2c70701eb18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173286"
---
# <a name="the-load-method"></a>Load 方法
您可以使用 <xref:System.Data.DataTable.Load%2A> 方法，載入具有資料來源之資料列的 <xref:System.Data.DataTable>。 這是多載的方法，在最簡單的形式，會接受單一參數， **DataReader**。 在此表單中，它只會載入**DataTable**與資料列。 您可以選擇性地指定**LoadOption**參數來控制如何將資料加入至**DataTable**。  
  
 **LoadOption**參數就特別有用，萬一其中**DataTable**已經包含資料列，因為它會說明如何傳入的資料，從資料來源會結合資料已在資料表中。 例如， **PreserveCurrentValues** （預設值） 指定在資料列會標示為的情況下**Added**中**DataTable**，**原始**值或每個資料行設定為相符的資料列的內容從資料來源。 **目前**值會保留資料列已新增時，所指派的值並**RowState**的資料列將會設定為**Changed**。  
  
 下列表格簡短說明 <xref:System.Data.LoadOption> 列舉值。  
  
|LoadOption 值|描述|  
|----------------------|-----------------|  
|**OverwriteRow**|內送資料列都有相同**PrimaryKey**為已在資料列的值**DataTable**，則**原始**並**目前**的每個值資料行所取代的值中的內送的資料列，而**RowState**屬性設定為**Unchanged**。<br /><br /> 還不存在於資料來源的資料列**DataTable**會加上**RowState**的值**Unchanged**。<br /><br /> 此選項會實際重新整理的內容**DataTable** ，使其符合資料來源的內容。|  
|**PreserveCurrentValues （預設值）**|如果內送資料列具有相同**PrimaryKey**為已在資料列的值**DataTable**，則**原始**值設定為內容的內送的資料列，以及**目前**值不會變更。<br /><br /> 如果**RowState**是**Added**或**Modified**，它會設定為**Modified**。<br /><br /> 如果**RowState**已**Deleted**，則仍會保持**Deleted**。<br /><br /> 還不存在於資料來源的資料列**DataTable**加入，而**RowState**設定為**Unchanged**。|  
|**UpdateCurrentValues**|如果內送資料列具有相同**PrimaryKey**已在資料列的值**DataTable**，則**目前**值複製到**原始**值，而**目前**值會設定內送資料列的內容。<br /><br /> 如果**RowState**中**DataTable**已**Added**，則**RowState**保持**Added**。 資料列標示為**Modified**或**Deleted**，則**RowState**是**Modified**。<br /><br /> 還不存在於資料來源的資料列**DataTable**加入，而**RowState**設定為**Added**。|  
  
 下列範例會使用**負載**方法，以顯示生日清單中的員工**Northwind**資料庫。  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.   
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a>另請參閱

- [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
