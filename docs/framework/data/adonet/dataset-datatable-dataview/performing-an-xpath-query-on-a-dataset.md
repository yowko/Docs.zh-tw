---
title: "在 DataSet 上執行 XPath 查詢 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 在 DataSet 上執行 XPath 查詢
可利用同步處理之 <xref:System.Data.DataSet> 與 <xref:System.Xml.XmlDataDocument> 間的關聯性來使用 XML 服務 \(例如 XML 路徑語言 \(XPath\) 查詢\)，而這些服務可讓您存取 **XmlDataDocument**，且執行某些功能會比直接存取 **DataSet** 更方便。  例如，不需使用 <xref:System.Data.DataTable> 的 **Select** 方法，在 **DataSet** 內巡覽與其他資料表的關聯性，而可以在與 **DataSet** 同步處理的 **XmlDataDocument** 上執行 XPath 查詢，以取得 <xref:System.Xml.XmlNodeList> 格式的 XML 項目清單。  **XmlNodeList** 中的節點在轉換為 <xref:System.Xml.XmlElement> 節點後，可以接著傳遞給 **XmlDataDocument** 的 **GetRowFromElement** 方法，以將相符的 <xref:System.Data.DataRow> 參考傳回給已同步處理之 **DataSet** 內的資料表資料列。  
  
 例如，下列程式碼範例執行「孫代」XPath 查詢。  會在 \<legacyBold\>DataSet\<\/legacyBold\> 內填入三個資料表：**Customers**、**Orders** 和 **OrderDetails**。  範例中，先在 **Customers** 和 **Orders** 資料表間建立父子關係，然後在 **Orders** 和 **OrderDetails** 資料表間建立父子關係。  接著執行 XPath 查詢以傳回 **Customers** 節點的 **XmlNodeList**，其中身為下下層的 **OrderDetails** 節點具有值為 43 的 **ProductID** 節點。  就本質上而言，此範例使用 XPath 查詢來判斷哪些客戶訂購 **ProductID** 為 43 的產品。  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],   
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);   
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## 請參閱  
 [DataSet 和 XmlDataDocument 同步處理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)