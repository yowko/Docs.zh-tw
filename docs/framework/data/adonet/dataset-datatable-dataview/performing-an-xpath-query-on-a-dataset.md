---
title: 對資料集執行 XPath 查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 5e9a00ab78a57c3c1686d7c87ed8b45d9b2649af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150827"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>對資料集執行 XPath 查詢
同步<xref:System.Data.DataSet>和<xref:System.Xml.XmlDataDocument>之間的關係允許您使用 XML 服務（如 XML 路徑語言 （XPath） 查詢），這些服務可以訪問**XmlDataDocument，** 並且可以比直接存取**DataSet**更方便地執行某些功能。 例如，可以使用**Select**方法<xref:System.Data.DataTable>將關係導航到**DataSet**中的其他表，而是可以在與**DataSet**同步的**XmlDataDocument**上執行 XPath 查詢，以獲取 XML 元素的清單。 <xref:System.Xml.XmlNodeList> 然後，將**XmlNodeList**中的節點<xref:System.Xml.XmlElement>作為節點強制轉換，可以傳遞給**XmlDataDocument**的**GetRowFromElement**方法，以<xref:System.Data.DataRow>返回對同步**DataSet**中表行的匹配引用。  
  
 例如，下列程式碼範例執行「孫代」XPath 查詢。 **資料集**由三個表填充：**客戶**、**訂單**和**訂單詳細資訊**。 在此示例中，首先在 **"客戶**"和 **"訂單"** 表之間以及 **"訂單****詳細資訊**"表之間創建父子關係。 然後執行 XPath 查詢以返回**客戶**節點的**XmlNodeList，** 其中孫**訂單詳細資訊**節點具有值為 43**的 ProductID**節點。 實質上，該示例使用 XPath 查詢來確定哪些客戶訂購了產品**ID**為 43 的產品。  
  
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
