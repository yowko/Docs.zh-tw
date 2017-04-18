---
title: "Load 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Load 方法
您可以使用 <xref:System.Data.DataTable.Load%2A> 方法，載入具有資料來源之資料列的 <xref:System.Data.DataTable>。  這是一種多載方法，在其最簡單的形式中，便可以接受單一參數 **DataReader**。  在這種形式下，它只會載入含有資料列的 **DataTable**。  此外，您也可以選擇指定 **LoadOption** 參數來控制將資料加入 **DataTable** 的方式。  
  
 在 **DataTable** 已含有資料列的情況下，特別適合使用 **LoadOption** 參數，因為它會說明資料來源的內送資料，將使用何種方式來與已在資料表內的資料進行結合。  例如，**PreserveCurrentValues** \(預設值\) 會指定在 **DataTable** 中的資料列標記為 **Added** 的情況下，每個資料行的 **Original** 值會設定為資料來源中之對應列的內容。  **Current** 值會保留資料列加入時所指定的值，而資料列的 **RowState** 會設定為 **Changed**。  
  
 下列表格簡短說明 <xref:System.Data.LoadOption> 列舉值。  
  
|LoadOption 值|描述|  
|------------------|--------|  
|**OverwriteRow**|若內送資料列的 **PrimaryKey** 值與 **DataTable** 中既有之資料列的值相同，則每個資料行的 **Original** 與 **Current** 值都會由內送資料列的值來取代，並且 **RowState** 屬性會設定為 **Unchanged**。<br /><br /> 資料來源中原本不在 **DataTable** 內的資料列都會加入，並將 **RowState** 值設為 **Unchanged**。<br /><br /> 此選項會實際重新整理 **DataTable** 的內容，以符合資料來源的內容。|  
|**PreserveCurrentValues \(預設值\)**|若內送資料列的 **PrimaryKey** 值與 **DataTable** 中既有之資料列的值相同，則 **Original** 值會設定為內送資料列的內容，而 **Current** 值將保持不變。<br /><br /> 若 **RowState** 為 **Added** 或 **Modified**，則會設定為 **Modified**。<br /><br /> 若 **RowState** 原本為 **Deleted**，則會保留為 **Deleted**。<br /><br /> 資料來源中原本不在 **DataTable** 內的資料列都會加入，並將 **RowState** 設為 **Unchanged**。|  
|**UpdateCurrentValues**|若內送資料列的 **PrimaryKey** 值與 **DataTable** 中既有之資料列的值相同，則 **Current** 值會複製到 **Original** 值上，然後 **Current** 值會設定為內送資料列的內容。<br /><br /> 若 **DataTable** 中的 **RowState** 為 **Added**，則 **RowState** 會保持為 **Added**。  對於標記為 **Modified** 或 **Deleted** 的資料列，**RowState** 皆為 **Modified**。<br /><br /> 資料來源中原本不在 **DataTable** 內的資料列都會加入，並將 **RowState** 設為 **Added**。|  
  
 下列範例將使用 **Load** 方法，顯示 **Northwind** 資料庫中的員工生日清單。  
  
 \[Visual Basic\]  
  
```  
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
  
## 請參閱  
 [管理 DataTable 中的資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)