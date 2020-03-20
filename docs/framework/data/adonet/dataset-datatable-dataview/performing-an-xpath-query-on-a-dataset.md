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
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="1311d-102">對資料集執行 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="1311d-102">Performing an XPath Query on a DataSet</span></span>
<span data-ttu-id="1311d-103">同步<xref:System.Data.DataSet>和<xref:System.Xml.XmlDataDocument>之間的關係允許您使用 XML 服務（如 XML 路徑語言 （XPath） 查詢），這些服務可以訪問**XmlDataDocument，** 並且可以比直接存取**DataSet**更方便地執行某些功能。</span><span class="sxs-lookup"><span data-stu-id="1311d-103">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="1311d-104">例如，可以使用**Select**方法<xref:System.Data.DataTable>將關係導航到**DataSet**中的其他表，而是可以在與**DataSet**同步的**XmlDataDocument**上執行 XPath 查詢，以獲取 XML 元素的清單。 <xref:System.Xml.XmlNodeList></span><span class="sxs-lookup"><span data-stu-id="1311d-104">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="1311d-105">然後，將**XmlNodeList**中的節點<xref:System.Xml.XmlElement>作為節點強制轉換，可以傳遞給**XmlDataDocument**的**GetRowFromElement**方法，以<xref:System.Data.DataRow>返回對同步**DataSet**中表行的匹配引用。</span><span class="sxs-lookup"><span data-stu-id="1311d-105">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="1311d-106">例如，下列程式碼範例執行「孫代」XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="1311d-106">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="1311d-107">**資料集**由三個表填充：**客戶**、**訂單**和**訂單詳細資訊**。</span><span class="sxs-lookup"><span data-stu-id="1311d-107">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="1311d-108">在此示例中，首先在 **"客戶**"和 **"訂單"** 表之間以及 **"訂單\*\*\*\*詳細資訊**"表之間創建父子關係。</span><span class="sxs-lookup"><span data-stu-id="1311d-108">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="1311d-109">然後執行 XPath 查詢以返回**客戶**節點的**XmlNodeList，** 其中孫**訂單詳細資訊**節點具有值為 43**的 ProductID**節點。</span><span class="sxs-lookup"><span data-stu-id="1311d-109">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="1311d-110">實質上，該示例使用 XPath 查詢來確定哪些客戶訂購了產品**ID**為 43 的產品。</span><span class="sxs-lookup"><span data-stu-id="1311d-110">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1311d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1311d-111">See also</span></span>

- [<span data-ttu-id="1311d-112">資料集和 XmlDataDocument 同步處理</span><span class="sxs-lookup"><span data-stu-id="1311d-112">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- <span data-ttu-id="1311d-113">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="1311d-113">[ADO.NET Overview](../ado-net-overview.md)</span></span>
