---
title: Load 方法
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: ea437d1f8ed567934acafbd8db1f8dba8eb22bcc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177536"
---
# <a name="the-load-method"></a>Load 方法

您可以使用 <xref:System.Data.DataTable.Load%2A> 方法，載入具有資料來源之資料列的 <xref:System.Data.DataTable>。 這是一種多載方法，其最簡單的形式是接受單一參數，也就是 **DataReader**。 在這種形式中，它只會載入具有資料列的 **DataTable** 。 您可以選擇性地指定 **LoadOption** 參數，以控制如何將資料加入 **DataTable**。  
  
 當**DataTable**已經包含資料列時， **LoadOption**參數特別有用，因為它會說明資料來源中的傳入資料如何與已經存在於資料表中的資料結合。 例如， **PreserveCurrentValues** (預設) 指定在**資料表**中標記為**已加入**的資料列，**原始**值或每個資料行會設定為數據源中相符資料列的內容。 **目前**的值會保留加入資料列時指派的值，而且資料列的**RowState**會設定為 [**已變更**]。  
  
 下列表格簡短說明 <xref:System.Data.LoadOption> 列舉值。  
  
|LoadOption 值|描述|  
|----------------------|-----------------|  
|**OverwriteRow**|如果內送資料列的 **PrimaryKey** 值與 **DataTable**中既有的資料列相同，則會將每個資料行的 **原始** 值和 **目前** 值取代為內送資料列中的值，並將 **RowState** 屬性設定為 **未**變更。<br /><br /> 資料來源中尚未存在 **DataTable** 中的資料列會加入，且 **RowState** 值為 [ **未**變更]。<br /><br /> 此選項實際上會重新整理 **DataTable** 的內容，使其與資料來源的內容相符。|  
|**PreserveCurrentValues (預設值)**|如果內送資料列的 **PrimaryKey** 值與 **DataTable**中的資料列相同，則會將 **原始** 值設定為內送資料列的內容，而且 **目前** 的值不會變更。<br /><br /> 如果**新增**或**修改** **RowState** ，它會設定為 [**已修改**]。<br /><br /> 如果 **RowState** 已 **刪除**，則會保持 **刪除**。<br /><br /> 資料來源中尚未存在 **DataTable** 中的資料列會加入，且 **RowState** 會設定為 **未**變更。|  
|**UpdateCurrentValues**|如果內送資料列的 **PrimaryKey** 值與 **DataTable**中的資料列相同，則會將 **目前** 的值複製到 **原始** 值，然後將 **目前** 的值設定為內送資料列的內容。<br /><br /> 如果已**加入** **DataTable**中的**RowState** ，則**RowState**會保持**新增**。 針對標示為**修改**或**刪除**的資料列，會**修改** **RowState** 。<br /><br /> 資料來源中尚未存在 **DataTable** 中的資料列會加入，且 **RowState** 會設定為 [ **已加入**]。|  
  
 下列範例會使用 **Load** 方法來顯示 **Northwind** 資料庫中員工的生日清單。  
  
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
