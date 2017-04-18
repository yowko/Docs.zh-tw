---
title: "資料列錯誤資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 資料列錯誤資訊
編輯 <xref:System.Data.DataTable> 中的值時，若要避免必須在每次發生資料列錯誤時都回應，則可以將錯誤資訊加入至資料列中，供日後使用。  針對這項用途，<xref:System.Data.DataRow> 物件會為每個資料列提供 <xref:System.Data.DataRow.RowError%2A> 屬性。  將資料加入 **DataRow** 的 **RowError** 屬性中，會將 **DataRow** 的 <xref:System.Data.DataRow.HasErrors%2A> 屬性設為 **true**。  如果 **DataRow** 是 **DataTable** 的一部分，而且 **DataRow.HasErrors** 為 **true**，則 **DataTable.HasErrors** 屬性亦為 **true**。  這同樣適用於 **DataTable** 所隸屬的 **DataSet**。  當您在測試錯誤時，您可以檢查 **HasErrors** 屬性來判斷錯誤資訊是否已加入至任何資料列。  如果 **HasErrors** 為 **true**，則可以使用 **DataTable** 的 <xref:System.Data.DataTable.GetErrors%2A> 方法，只傳回和檢查發生錯誤的資料列 \(如下列範例所示\)。  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## 請參閱  
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataTable>   
 [管理 DataTable 中的資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)