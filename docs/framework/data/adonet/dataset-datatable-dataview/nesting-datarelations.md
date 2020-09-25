---
title: 巢狀 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 8db75f486c7c08b6a02401af35c9edf9969f9063
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201274"
---
# <a name="nesting-datarelations"></a>巢狀 DataRelation

關聯式資料表示中，個別資料表所包含的資料列使用一個或一組資料行彼此相關。 在 ADO.NET <xref:System.Data.DataSet> 中，是使用 <xref:System.Data.DataRelation> 來實作資料表間的關聯性。 當您建立 **DataRelation**時，資料行的父子式關聯性只會透過關聯進行管理。 而資料表和資料行是個別的實體。 XML 提供的階層式資料表示中，父子關係是由包含巢狀項目子系的父項目表示。  
  
 為了在 **資料集** 與 <xref:System.Xml.XmlDataDocument> 或使用 **WriteXml**撰寫為 XML 資料的同步處理時，協助子物件的嵌套， **DataRelation** 會公開一個 **嵌套** 屬性。 將**DataRelation**的**Nested**屬性設定為**true** ，會在寫入為 XML 資料或與**XmlDataDocument**同步處理時，將關聯的子資料列嵌套在父資料行中。 依預設， **DataRelation**的**Nested**屬性為**false**。  
  
 例如，請考慮下列 **資料集**。  
  
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
  
 因為此**資料集**的**DataRelation**物件的**Nested**屬性不是設定為**true** ，所以當此**資料集**表示為 XML 資料時，子物件不會嵌套在父元素內。 將包含相關**資料集**之**資料集**的 XML 表示轉換為非嵌套資料關聯可能會導致效能變慢。 因此，我們建議您巢狀化資料關聯。 若要這樣做，請將 **Nested** 屬性設定為 **true**。 然後，在 XSLT 樣式表中寫入程式碼，以便使用由上而下階層式 XPath 查詢運算式來找出並轉換資料。  
  
 下列程式碼範例顯示在**資料集**上呼叫**WriteXml**的結果。  
  
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
  
 請注意， **Customers** 專案和 **Orders** 元素會顯示為「同輩」元素。 如果您想要讓**Orders**元素顯示為其各自父項目的子系，則**DataRelation**的**Nested**屬性必須設定為**true** ，而您可以新增下列專案：  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 下列程式碼顯示產生的輸出看起來的樣子，其中 **Orders** 元素會嵌套在其各自的父項目內。  
  
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
  
## <a name="see-also"></a>另請參閱

- [在資料集中使用 XML](using-xml-in-a-dataset.md)
- [加入 DataRelation](adding-datarelations.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
