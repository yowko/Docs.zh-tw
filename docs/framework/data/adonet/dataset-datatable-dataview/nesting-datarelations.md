---
title: "巢狀 DataRelation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 巢狀 DataRelation
關聯式資料表示中，個別資料表所包含的資料列使用一個或一組資料行彼此相關。  在 ADO.NET <xref:System.Data.DataSet> 中，是使用 <xref:System.Data.DataRelation> 來實作資料表間的關聯性。  當您建立 **DataRelation** 時，資料行的父子關係只透過這項關聯來管理，  而資料表和資料行是個別的實體。  XML 提供的階層式資料表示中，父子關係是由包含巢狀項目子系的父項目表示。  
  
 將 **DataSet** 與 <xref:System.Xml.XmlDataDocument> 同步處理時，或使用 **WriteXml** 撰寫為 XML，若要加速子物件的巢狀，**DataRelation** 會公開 **Nested** 屬性。  將 **DataRelation** 的 **Nested** 屬性設定為 **true**，會造成關聯的子資料列在寫為 XML 資料或與 **XmlDataDocument** 同步處理時，巢狀化至父資料行中。  依預設，**DataRelation** 的 **Nested** 屬性為 **false**。  
  
 例如，請考量下列 **DataSet**。  
  
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
  
 由於在這個 **DataSet** 中，**DataRelation** 物件的 **Nested** 屬性並未設定為 **true**，所以將這個 **DataSet** 表示為 XML 資料時，子物件不會巢狀化至父項目內。  使用非巢狀資料關聯來轉換包含相關 **DataSet** 之 **DataSet** 的 XML 表示可能會導致效能降低。  因此，我們建議您巢狀化資料關聯。  若要這樣做，請將 **Nested** 屬性設定為 **true**。  然後，在 XSLT 樣式表中寫入程式碼，以便使用由上而下階層式 XPath 查詢運算式來找出並轉換資料。  
  
 下列程式碼範例顯示在 **DataSet** 呼叫 **WriteXml** 的結果。  
  
```  
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
  
 請注意，**Customers** 項目和 **Orders** 項目顯示為同層級項目。  如果您希望將 **Orders** 項目顯示為其個別父項目的項目子系，則您必須將 **DataRelation** 的 **Nested** 屬性設定為 **true**，並加入以下內容：  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 下列程式碼顯示輸出結果內容，其中 **Orders** 項目巢狀化至個別父項目內。  
  
```  
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
  
## 請參閱  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [加入 DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)