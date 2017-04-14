---
title: "複製 DataSet 內容 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 複製 DataSet 內容
您可以建立 <xref:System.Data.DataSet> 的複本，這樣就可以在不影響原始資料的情況下使用資料，也可以從 **DataSet** 使用資料的子集。  複製 **DataSet** 時，您可以：  
  
-   建立與 **DataSet** 完全相同的複本，包括結構描述、資料、資料列狀態資訊和資料列版本。  
  
-   建立一個 **DataSet**，其中包含現有 **DataSet** 的結構描述，但只有修改過的資料列。  您可以傳回所有修改過的資料列，或指定特定的 **DataRowState**。  如需資料列狀態的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
-   只複製 **DataSet** 的結構描述或關聯式結構，而不複製任何資料列。  使用 <xref:System.Data.DataTable.ImportRow%2A>，可以將資料列匯入現有的 <xref:System.Data.DataTable>。  
  
 若要建立包含結構描述和資料的 **DataSet** 完整複本，請使用 **DataSet** 的 <xref:System.Data.DataSet.Copy%2A> 方法。  下列程式碼範例顯示如何建立 **DataSet** 的完整複本。  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 若要建立 **DataSet** 的複本，其中包含結構描述和只表示 **Added**、**Modified** 或 **Deleted** 資料列的資料，請使用 **DataSet** 的 <xref:System.Data.DataSet.GetChanges%2A> 方法。  呼叫 **GetChanges** 時，您也可以使用 **GetChanges** 傳遞 **DataRowState** 的值，而只傳回具有指定資料列狀態的資料列。  下列程式碼範例顯示如何在呼叫 **GetChanges** 時傳遞 **DataRowState**。  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 若要建立只包含結構描述的 **DataSet** 複本，請使用 **DataSet** 的 <xref:System.Data.DataSet.Clone%2A> 方法。  您也可以使用 **DataTable** 的 **ImportRow** 方法，將現有資料列加入複製的 **DataSet**。  **ImportRow** 會將資料、資料列狀態和資料列版本資訊加入至指定資料表。  資料行值只會被加入資料行名稱相符且資料型別相容之處。  
  
 下列程式碼範例建立 **DataSet** 的複製品，然後將原始 **DataSet** 的資料列加入 **DataSet** 複製品中的 **Customers** 資料表，該表中 **CountryRegion** 資料行的值為 "Germany"。  
  
```vb  
  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## 請參閱  
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)