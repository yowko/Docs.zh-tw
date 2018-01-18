---
title: "巢狀 DataRelation"
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
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c057e836e8903fc2f5cb28f74858be97d2ffcc14
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="nesting-datarelations"></a><span data-ttu-id="91e05-102">巢狀 DataRelation</span><span class="sxs-lookup"><span data-stu-id="91e05-102">Nesting DataRelations</span></span>
<span data-ttu-id="91e05-103">關聯式資料表示中，個別資料表所包含的資料列使用一個或一組資料行彼此相關。</span><span class="sxs-lookup"><span data-stu-id="91e05-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="91e05-104">在 ADO.NET <xref:System.Data.DataSet> 中，是使用 <xref:System.Data.DataRelation> 來實作資料表間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="91e05-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="91e05-105">當您建立**DataRelation**，僅透過關聯性所管理的資料行的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="91e05-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="91e05-106">而資料表和資料行是個別的實體。</span><span class="sxs-lookup"><span data-stu-id="91e05-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="91e05-107">XML 提供的階層式資料表示中，父子關係是由包含巢狀項目子系的父項目表示。</span><span class="sxs-lookup"><span data-stu-id="91e05-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="91e05-108">若要加速子物件的巢狀時**資料集**與同步處理<xref:System.Xml.XmlDataDocument>或寫為 XML 資料使用**WriteXml**、 **DataRelation**公開**巢狀**屬性。</span><span class="sxs-lookup"><span data-stu-id="91e05-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="91e05-109">設定**巢狀**屬性**DataRelation**至**true**造成子資料列寫入為 XML 資料時，父資料行內巢狀關聯或與同步處理**XmlDataDocument**。</span><span class="sxs-lookup"><span data-stu-id="91e05-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="91e05-110">**巢狀**屬性**DataRelation**是**false**，根據預設。</span><span class="sxs-lookup"><span data-stu-id="91e05-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="91e05-111">例如，請考慮下列**資料集**。</span><span class="sxs-lookup"><span data-stu-id="91e05-111">For example, consider the following **DataSet**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 <span data-ttu-id="91e05-112">因為**巢狀**屬性**DataRelation**物件未設定為**true**這個**資料集**，無巢狀的子物件父項目內時這**資料集**表示為 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="91e05-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="91e05-113">轉換的 XML 表示法**資料集**，其中包含相關**資料集**使用非巢狀資料關聯可能會導致效能變慢。</span><span class="sxs-lookup"><span data-stu-id="91e05-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="91e05-114">因此，我們建議您巢狀化資料關聯。</span><span class="sxs-lookup"><span data-stu-id="91e05-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="91e05-115">若要這樣做，請設定**巢狀**屬性**true**。</span><span class="sxs-lookup"><span data-stu-id="91e05-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="91e05-116">然後，在 XSLT 樣式表中寫入程式碼，以便使用由上而下階層式 XPath 查詢運算式來找出並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="91e05-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="91e05-117">下列程式碼範例示範呼叫結果**WriteXml**上**資料集**。</span><span class="sxs-lookup"><span data-stu-id="91e05-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 <span data-ttu-id="91e05-118">請注意，**客戶**項目和**訂單**項目會顯示為同層級項目。</span><span class="sxs-lookup"><span data-stu-id="91e05-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="91e05-119">如果您想**訂單**項目顯示為其個別父項目子系**巢狀**屬性**DataRelation**必須設為**true**並加入下列：</span><span class="sxs-lookup"><span data-stu-id="91e05-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="91e05-120">下列程式碼將示範所產生的輸出外觀，與**訂單**項目巢狀其個別父項目。</span><span class="sxs-lookup"><span data-stu-id="91e05-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a><span data-ttu-id="91e05-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="91e05-121">See Also</span></span>  
 [<span data-ttu-id="91e05-122">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="91e05-122">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="91e05-123">新增 DataRelation</span><span class="sxs-lookup"><span data-stu-id="91e05-123">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 [<span data-ttu-id="91e05-124">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="91e05-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="91e05-125">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="91e05-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
