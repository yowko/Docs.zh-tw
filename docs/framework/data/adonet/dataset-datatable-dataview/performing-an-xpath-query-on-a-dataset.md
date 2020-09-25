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
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="231fe-102">對資料集執行 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="231fe-102">Performing an XPath Query on a DataSet</span></span>

<span data-ttu-id="231fe-103">已同步處理的 <xref:System.Data.DataSet> 和可 <xref:System.Xml.XmlDataDocument> 讓您利用 Xml 路徑語言 (XPath) 查詢）來存取 **XmlDataDocument** ，而且可以更方便地執行某些功能，而不需要直接存取 **資料集** 。</span><span class="sxs-lookup"><span data-stu-id="231fe-103">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="231fe-104">**Select**例如， <xref:System.Data.DataTable> 您可以在與**Dataset**同步處理的**XmlDataDocument**上執行 XPath 查詢，而不是使用的 Select 方法來流覽**資料集**內其他資料表的關聯性，以取得的格式的 XML 專案清單 <xref:System.Xml.XmlNodeList> 。</span><span class="sxs-lookup"><span data-stu-id="231fe-104">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="231fe-105">然後， **XmlNodeList**中的節點（ <xref:System.Xml.XmlElement> 可轉換為節點）可以傳遞給**XmlDataDocument**的**GetRowFromElement**方法，以將相符的參考傳回給已同步處理之 <xref:System.Data.DataRow> **資料集中**的資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="231fe-105">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="231fe-106">例如，下列程式碼範例執行「孫代」XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="231fe-106">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="231fe-107">**資料集會**填入三個數據表： **Customers**、 **Orders**和**OrderDetails**。</span><span class="sxs-lookup"><span data-stu-id="231fe-107">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="231fe-108">在此範例中，會先在 **Customers** 和 **orders** 資料表之間，以及 **Orders** 和 **OrderDetails** 資料表之間建立父子式關聯。</span><span class="sxs-lookup"><span data-stu-id="231fe-108">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="231fe-109">接著會執行 XPath 查詢，以傳回**Customers**節點的**XmlNodeList** ，其中孫**OrderDetails**節點具有值為43的**ProductID**節點。</span><span class="sxs-lookup"><span data-stu-id="231fe-109">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="231fe-110">基本上，此範例會使用 XPath 查詢來判斷哪些客戶已訂購具有 **ProductID** 43 的產品。</span><span class="sxs-lookup"><span data-stu-id="231fe-110">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="231fe-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="231fe-111">See also</span></span>

- [<span data-ttu-id="231fe-112">資料集和 XmlDataDocument 同步處理</span><span class="sxs-lookup"><span data-stu-id="231fe-112">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- <span data-ttu-id="231fe-113">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="231fe-113">[ADO.NET Overview](../ado-net-overview.md)</span></span>
