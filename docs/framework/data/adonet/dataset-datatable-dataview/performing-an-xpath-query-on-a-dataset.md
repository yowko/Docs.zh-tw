---
title: 對資料集執行 XPath 查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: d7897815874f2e9de2f4c24d3c141d464a296b31
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201235"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>對資料集執行 XPath 查詢

已同步處理的 <xref:System.Data.DataSet> 和可 <xref:System.Xml.XmlDataDocument> 讓您利用 Xml 路徑語言 (XPath) 查詢）來存取 **XmlDataDocument** ，而且可以更方便地執行某些功能，而不需要直接存取 **資料集** 。 **Select**例如， <xref:System.Data.DataTable> 您可以在與**Dataset**同步處理的**XmlDataDocument**上執行 XPath 查詢，而不是使用的 Select 方法來流覽**資料集**內其他資料表的關聯性，以取得的格式的 XML 專案清單 <xref:System.Xml.XmlNodeList> 。 然後， **XmlNodeList**中的節點（ <xref:System.Xml.XmlElement> 可轉換為節點）可以傳遞給**XmlDataDocument**的**GetRowFromElement**方法，以將相符的參考傳回給已同步處理之 <xref:System.Data.DataRow> **資料集中**的資料表資料列。  
  
 例如，下列程式碼範例執行「孫代」XPath 查詢。 **資料集會**填入三個數據表： **Customers**、 **Orders**和**OrderDetails**。 在此範例中，會先在 **Customers** 和 **orders** 資料表之間，以及 **Orders** 和 **OrderDetails** 資料表之間建立父子式關聯。 接著會執行 XPath 查詢，以傳回**Customers**節點的**XmlNodeList** ，其中孫**OrderDetails**節點具有值為43的**ProductID**節點。 基本上，此範例會使用 XPath 查詢來判斷哪些客戶已訂購具有 **ProductID** 43 的產品。  
  
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
  
## <a name="see-also"></a>另請參閱

- [資料集和 XmlDataDocument 同步處理](dataset-and-xmldatadocument-synchronization.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
