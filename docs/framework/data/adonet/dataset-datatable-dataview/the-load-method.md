---
title: Load 方法
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: b704deeffcd06bca09b6c26d60a66218b46fc55c
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203163"
---
# <a name="the-load-method"></a>Load 方法
您可以使用 <xref:System.Data.DataTable.Load%2A> 方法，載入具有資料來源之資料列的 <xref:System.Data.DataTable>。 這是一種多載方法, 其最簡單的形式是接受單一參數, 也就是**DataReader**。 在此表單中, 它只會載入具有資料列的**DataTable** 。 (選擇性) 您可以指定**LoadOption**參數來控制資料加入至**DataTable**的方式。  
  
 在**DataTable**已經包含資料列的情況下, **LoadOption**參數特別有用, 因為它會描述資料來源的傳入資料如何與已經在資料表中的資料結合。 例如, **PreserveCurrentValues** (預設值) 指定在**DataTable**中將資料列標示為**已加入**時, 會將**原始**值或每個資料行設定為數據源中相符的資料列內容。 當加入資料列時,**目前**的值會保留指派的值, 而資料列的**RowState**會設定為**已變更**。  
  
 下列表格簡短說明 <xref:System.Data.LoadOption> 列舉值。  
  
|LoadOption 值|描述|  
|----------------------|-----------------|  
|**OverwriteRow**|如果內送資料列的**PrimaryKey**值與**DataTable**中已經存在的資料列相同, 則會將每個資料行的**原始**值和**目前**值取代為內送資料列中的值, 並將**RowState**屬性設定為**未**變更。<br /><br /> 資料來源中不存在於**DataTable**中的資料列會以 [**未**變更] 的**RowState**值來加入。<br /><br /> 此選項實際上會重新整理**DataTable**的內容, 使其符合資料來源的內容。|  
|**PreserveCurrentValues (預設值)**|如果內送資料列的**PrimaryKey**值與**DataTable**中已經存在的資料列相同, 則**原始**值會設為傳入資料列的內容, 而**目前**的值不會變更。<br /><br /> 如果**RowState**已**新增**或**修改**, 則會設定為 [**已修改**]。<br /><br /> 如果**RowState**已**刪除**, 它會保持**刪除**。<br /><br /> 不存在於**DataTable**中的資料來源中的資料列會加入, 而且**RowState**會設定為**未**變更。|  
|**UpdateCurrentValues**|如果內送資料列的**PrimaryKey**值與**DataTable**中已經存在的資料列相同, 則**目前**的值會複製到**原始**值, 而**目前**的值會設定為內送資料列的內容。<br /><br /> 如果**加入** **DataTable**中的**RowState** , 則**RowState**會保持**新增**。 針對標示為**已修改**或**已刪除**的資料列, 會**修改** **RowState** 。<br /><br /> 系統會新增資料來源中不存在於**DataTable**中的資料列, 並將**RowState**設定為 [**已加入**]。|  
  
 下列範例會使用**Load**方法, 針對**Northwind**資料庫中的員工顯示生日清單。  
  
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
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
