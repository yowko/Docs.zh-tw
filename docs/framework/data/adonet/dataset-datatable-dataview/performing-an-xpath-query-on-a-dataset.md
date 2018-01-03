---
title: "對資料集執行 XPath 查詢"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 62c5cef51e125443d87c47f7f62dc76aa5d352b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="044f8-102">對資料集執行 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="044f8-102">Performing an XPath Query on a DataSet</span></span>
<span data-ttu-id="044f8-103">同步處理之間的關聯性<xref:System.Data.DataSet>和<xref:System.Xml.XmlDataDocument>可讓您使用 XML 服務，例如 XML 路徑語言 (XPath) 查詢，存取**XmlDataDocument**且執行某些功能更方便比存取**資料集**直接。</span><span class="sxs-lookup"><span data-stu-id="044f8-103">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="044f8-104">例如，而不是使用**選取**方法<xref:System.Data.DataTable>巡覽關聯性中的其他資料表到**資料集**，您可以針對執行 XPath 查詢**XmlDataDocument**同步處理與**資料集**，若要取得的 XML 項目清單的形式<xref:System.Xml.XmlNodeList>。</span><span class="sxs-lookup"><span data-stu-id="044f8-104">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="044f8-105">中的節點**XmlNodeList**轉換為<xref:System.Xml.XmlElement>節點，然後傳遞至**Xmldatadocument**方法**XmlDataDocument**，表示傳回比對<xref:System.Data.DataRow>處於同步處理資料表的資料列的參考**資料集**。</span><span class="sxs-lookup"><span data-stu-id="044f8-105">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="044f8-106">例如，下列程式碼範例執行「孫代」XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="044f8-106">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="044f8-107">**資料集**會填入三個資料表：**客戶**，**訂單**，和**OrderDetails**。</span><span class="sxs-lookup"><span data-stu-id="044f8-107">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="044f8-108">在範例中，父子式關聯性第一次建立之間**客戶**和**訂單**資料表，以及**訂單**和**OrderDetails**資料表。</span><span class="sxs-lookup"><span data-stu-id="044f8-108">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="044f8-109">接著執行 XPath 查詢以傳回**XmlNodeList**的**客戶**節點的孫系**OrderDetails**節點有**ProductID**節點具有值為 43。</span><span class="sxs-lookup"><span data-stu-id="044f8-109">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="044f8-110">基本上，範例會使用 XPath 查詢來判斷哪些客戶訂購的產品**ProductID**為 43。</span><span class="sxs-lookup"><span data-stu-id="044f8-110">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="044f8-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="044f8-111">See Also</span></span>  
 [<span data-ttu-id="044f8-112">資料集和 XmlDataDocument 同步處理</span><span class="sxs-lookup"><span data-stu-id="044f8-112">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [<span data-ttu-id="044f8-113">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="044f8-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
