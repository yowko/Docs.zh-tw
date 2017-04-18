---
title: "尋找資料列 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 尋找資料列
您可以使用 <xref:System.Data.DataView> 的 <xref:System.Data.DataView.Find%2A> 和 <xref:System.Data.DataView.FindRows%2A> 方法，依照資料列的排序索引鍵值來搜尋資料列。  **Find** 和 **FindRows** 方法內之區分大小寫的搜尋值，是由基礎 <xref:System.Data.DataTable> 的 **CaseSensitive** 屬性所決定。  搜尋值必須完全符合現有的排序索引鍵值，才能傳回結果。  
  
 **Find** 方法傳回整數以及符合搜尋準則之 <xref:System.Data.DataRowView> 的索引。  如果有多個資料列符合搜尋準則，則只會傳回第一個與 **DataRowView** 相符的索引。  如果找不到任何相符資料，則 **Find** 會傳回 \-1。  
  
 若要傳回符合多個資料列的搜尋結果，可以使用 **FindRows** 方法。  **FindRows** 的用途就像 **Find** 方法，但是它會傳回參考 **DataView** 中所有相符資料列的 **DataRowView** 陣列。  如果找不到任何相符資料，則 **DataRowView** 陣列會是空的。  
  
 若要使用 **Find** 或 **FindRows** 方法，您必須用下列方法指定排序順序：將 **ApplyDefaultSort** 設定為 **true** 或使用**Sort** 屬性。  如果沒有指定任何順序，則會擲回例外狀況。  
  
 **Find** 和 **FindRows** 方法將值的陣列視為輸入，此值的長度符合排序順序的資料行數目。  排序單一資料行時，您可傳遞單一值。  如果排序順序包含多個資料行，則您傳遞的是物件陣列。  請注意，將多個資料行排序時，物件陣列的值，必須與 **DataView** 的 **Sort** 屬性中所指定的資料行順序相符。  
  
 下列程式碼範例顯示如何針對具有單一資料行排序順序的 **DataView**，呼叫 **Find** 方法。  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 如果您的 **Sort** 屬性指定多個資料行，則您必須依照 **Sort** 屬性所指定的順序來傳遞具有每個資料行搜尋值的物件陣列，如下列程式碼範例所示。  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## 請參閱  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)