---
title: 巢狀 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 971a1bddc40521dc7381ecb2e39709c0fed282ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785979"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="1aec4-102">巢狀 DataRelation</span><span class="sxs-lookup"><span data-stu-id="1aec4-102">Nesting DataRelations</span></span>
<span data-ttu-id="1aec4-103">關聯式資料表示中，個別資料表所包含的資料列使用一個或一組資料行彼此相關。</span><span class="sxs-lookup"><span data-stu-id="1aec4-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="1aec4-104">在 ADO.NET <xref:System.Data.DataSet> 中，是使用 <xref:System.Data.DataRelation> 來實作資料表間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1aec4-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="1aec4-105">當您建立**DataRelation**時，資料行的父子式關聯性只會透過關聯來管理。</span><span class="sxs-lookup"><span data-stu-id="1aec4-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="1aec4-106">而資料表和資料行是個別的實體。</span><span class="sxs-lookup"><span data-stu-id="1aec4-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="1aec4-107">XML 提供的階層式資料表示中，父子關係是由包含巢狀項目子系的父項目表示。</span><span class="sxs-lookup"><span data-stu-id="1aec4-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="1aec4-108">若要在使用**WriteXml**同步<xref:System.Xml.XmlDataDocument>處理**資料集**時，加速子物件的嵌套， **DataRelation**會公開一個**嵌套**的屬性。</span><span class="sxs-lookup"><span data-stu-id="1aec4-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="1aec4-109">將**DataRelation**的**Nested**屬性設定為**true** ，會導致關聯的子資料列在寫為 XML 資料或與**XmlDataDocument**同步處理時，內嵌在父資料行中。</span><span class="sxs-lookup"><span data-stu-id="1aec4-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="1aec4-110">根據預設， **DataRelation**的**Nested**屬性為**false**。</span><span class="sxs-lookup"><span data-stu-id="1aec4-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="1aec4-111">例如，請考慮下列**資料集**。</span><span class="sxs-lookup"><span data-stu-id="1aec4-111">For example, consider the following **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="1aec4-112">因為此**資料集**的**DataRelation**物件的**Nested**屬性未設定為**true** ，所以當此**資料集**表示為 XML 資料時，子物件不會在父元素內嵌套。</span><span class="sxs-lookup"><span data-stu-id="1aec4-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="1aec4-113">使用非嵌套的資料關聯來轉換包含相關**資料集**之**資料集**的 XML 表示可能會導致效能變慢。</span><span class="sxs-lookup"><span data-stu-id="1aec4-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="1aec4-114">因此，我們建議您巢狀化資料關聯。</span><span class="sxs-lookup"><span data-stu-id="1aec4-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="1aec4-115">若要這麼做，請將**Nested**屬性設定為**true**。</span><span class="sxs-lookup"><span data-stu-id="1aec4-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="1aec4-116">然後，在 XSLT 樣式表中寫入程式碼，以便使用由上而下階層式 XPath 查詢運算式來找出並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="1aec4-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="1aec4-117">下列程式碼範例顯示在**資料集**上呼叫**WriteXml**的結果。</span><span class="sxs-lookup"><span data-stu-id="1aec4-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="1aec4-118">請注意， **Customers**元素和**Orders**元素會顯示為「同輩元素」。</span><span class="sxs-lookup"><span data-stu-id="1aec4-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="1aec4-119">如果您想要將**Orders**專案顯示為其各自父項目的子系，則**DataRelation**的**Nested**屬性必須設定為**true** ，而且您會加入下列專案：</span><span class="sxs-lookup"><span data-stu-id="1aec4-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="1aec4-120">下列程式碼顯示產生的輸出外觀，其中的**Orders**元素會放在其各自的父項目內。</span><span class="sxs-lookup"><span data-stu-id="1aec4-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1aec4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1aec4-121">See also</span></span>

- [<span data-ttu-id="1aec4-122">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="1aec4-122">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="1aec4-123">新增 DataRelation</span><span class="sxs-lookup"><span data-stu-id="1aec4-123">Adding DataRelations</span></span>](adding-datarelations.md)
- [<span data-ttu-id="1aec4-124">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="1aec4-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1aec4-125">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="1aec4-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
