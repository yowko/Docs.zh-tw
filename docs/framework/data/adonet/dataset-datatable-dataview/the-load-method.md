---
title: Load 方法
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: f1c819333225c22efb85946001a1fc8340d57989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150723"
---
# <a name="the-load-method"></a>Load 方法
您可以使用 <xref:System.Data.DataTable.Load%2A> 方法，載入具有資料來源之資料列的 <xref:System.Data.DataTable>。 這是一個重載方法，其最簡單的形式是接受單個參數 **，即 DataReader**。 在此表單中，它只需使用行載入**DataTable**即可。 或者，您可以指定**LoadOption**參數來控制將資料添加到**DataTable**中的方式。  
  
 **LoadOption**參數在**DataTable**已包含資料行的情況下特別有用，因為它描述了資料來源的傳入資料如何與表中已有的資料組合。 例如，**保留當前值**（預設值）指定在**資料表中**將行標記為 **"已添加**"的情況下，**原始**值或每列將設置為數據源中匹配行的內容。 "**當前**"值將保留添加行時分配的值，行的**RowState**將設置為 **"已更改**"。  
  
 下列表格簡短說明 <xref:System.Data.LoadOption> 列舉值。  
  
|LoadOption 值|描述|  
|----------------------|-----------------|  
|**OverwriteRow**|如果傳入行具有與**DataTable**中已有的行相同的**主鍵**值，則每列**的原始**值和**當前**值將替換為傳入行中的值，並且**RowState**屬性設置為 **"未更改**"。<br /><br /> **資料表中**不存在的資料來源中的行添加的**RowState**值**為"未更改**"。<br /><br /> 此選項實際上刷新**了 DataTable**的內容，以便它與資料來源的內容匹配。|  
|**PreserveCurrentValues (預設值)**|如果傳入行具有與**DataTable**中已有的行相同的**主鍵**值，則**原始**值將設置為傳入行的內容，並且不會更改 **"當前"** 值。<br /><br /> 如果 **"行狀態**已**添加**或**修改**"，則將其設置為 **"已修改**"。<br /><br /> 如果**RowState** **已刪除**，則保留**為 "已刪除**"。<br /><br /> 將添加**DataTable**中不存在的資料來源中的行，並將**RowState**設置為 **"未更改**"。|  
|**UpdateCurrentValues**|如果傳入行具有與**DataTable**中已有的行相同的**主鍵**值，則**當前**值將複製到**原始**值，然後將 **"當前**"值設置為傳入行的內容。<br /><br /> 如果**已添加** **DataTable**中的**行狀態**，則 **"行狀態**"將保持**已添加**。 對於標記為 **"已修改**或刪除"**的**行，將**修改****"行狀態**"。<br /><br /> 將添加**DataTable**中不存在的資料來源中的行，並將**RowState**設置為 **"已添加**"。|  
  
 以下示例使用**Load**方法顯示**Northwind**資料庫中員工的生日清單。  
  
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

- [在 DataTable 中操作資料](manipulating-data-in-a-datatable.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
