---
title: "Load 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a54eda8d96468d4506a5f7dafc342fa5ff128c2a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="the-load-method"></a>Load 方法
您可以使用 <xref:System.Data.DataTable.Load%2A> 方法，載入具有資料來源之資料列的 <xref:System.Data.DataTable>。 這是多載的方法，其最簡單的形式接受單一參數， **DataReader**。 在這種形式，它只會載入**DataTable**與資料列。 您可以選擇性地指定**LoadOption**參數來控制如何將資料加入至**DataTable**。  
  
 **LoadOption**參數是在情況下特別有用， **DataTable**已經包含資料列，因為它會說明如何內送資料來源的資料會結合資料已在表格中。 比方說， **PreserveCurrentValues** （預設值） 指定在資料列會標示為的情況下**Added**中**DataTable**、**原始**值或每個資料行設為相符的資料列的內容從資料來源。 **目前**值將會保留已加入資料列，所指派的值和**RowState**的資料列將會設定為**Changed**。  
  
 下列表格簡短說明 <xref:System.Data.LoadOption> 列舉值。  
  
|LoadOption 值|描述|  
|----------------------|-----------------|  
|**OverwriteRow**|如果內送資料列具有相同**PrimaryKey**為已在一個資料列的值**DataTable**、**原始**和**目前**每個值資料行所取代之傳入的資料列中的值和**RowState**屬性設定為**Unchanged**。<br /><br /> 還不存在於資料來源的資料列**DataTable**加入的**RowState**值**Unchanged**。<br /><br /> 此選項會實際重新整理的內容**DataTable**使其符合資料來源的內容。|  
|**PreserveCurrentValues (default)**|如果內送資料列具有相同**PrimaryKey**值為一個資料列已在**DataTable**、**原始**值設定為內容的內送的資料列，以及**目前**不會變更值。<br /><br /> 如果**RowState**是**Added**或**Modified**，設為**Modified**。<br /><br /> 如果**RowState**已**刪除**，它就會維持**刪除**。<br /><br /> 還不存在於資料來源的資料列**DataTable**加入，而**RowState**設**Unchanged**。|  
|**UpdateCurrentValues**|如果內送資料列具有相同**PrimaryKey**已在資料列的值**DataTable**、**目前**值複製到**原始**值，而**目前**值會設定內容的內送資料列。<br /><br /> 如果**RowState**中**DataTable**已**Added**、 **RowState**維持**Added**。 針對資料列標示為**Modified**或**刪除**、 **RowState**是**Modified**。<br /><br /> 還不存在於資料來源的資料列**DataTable**加入，而**RowState**設**Added**。|  
  
 下列範例會使用**負載**方法，以顯示中的員工生日清單**Northwind**資料庫。  
  
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
  
## <a name="see-also"></a>請參閱  
 [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
