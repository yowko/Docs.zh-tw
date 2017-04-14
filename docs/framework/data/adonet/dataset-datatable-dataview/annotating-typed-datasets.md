---
title: "為具型別的 DataSet 加上附註 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# 為具型別的 DataSet 加上附註
註釋可讓您在無需修改基礎結構描述的情況下，修改具型別之 <xref:System.Data.DataSet> 中的項目名稱。  若您修改基礎結構描述中的項目名稱，可能會造成具型別的 **DataSet** 參考資料來源中不存在的物件，也有可能會遺失資料來源中已存在之物件的參考。  
  
 您可以使用註釋，將具型別的 **DataSet** 內的物件名稱自訂為更有意義的名稱，使程式碼更容易閱讀，更便於用戶端使用具型別的 **DataSet**，同時又不會更動基礎結構描述。  例如，**Northwind** 資料庫之 **Customers** 資料表中的下列結構描述項目會產生名為 **CustomersRow** 的 **DataRow** 物件，以及名為 **Customers** 的 <xref:System.Data.DataRowCollection>。  
  
```  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 若將 **DataRowCollection** 的名稱取為 **Customers**，對用戶端程式碼而言是有意義，但如果將 **DataRow** 的名稱取為 **CustomersRow** 則會產生誤解，因為它是單一物件。  而且在一般案例中，該物件並不需要 **Row** 識別項，而且只會稱為 **Customer** 物件。  這種情況的解決方案就是為結構描述加上註釋，並標示出 **DataRow** 和 **DataRowCollection** 物件的新名稱。  下列為上述結構描述的附註版本。  
  
```  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 為 **Customer** 指定 **typedName** 值會將 **DataRow** 物件的名稱改為 **Customer**。  指定 **Customers** 的 **typedPlural** 可保存 **Customers** 的 **DataRowCollection** 名稱。  
  
 下列表格顯示可供使用的註釋。  
  
|註釋|描述|  
|--------|--------|  
|**typedName**|物件名稱。|  
|**typedPlural**|物件集合名稱。|  
|**typedParent**|在父關聯性中所參考的物件名稱。|  
|**typedChildren**|從子關聯性傳回物件的方法名稱。|  
|**nullValue**|基礎值為 **DBNull** 時的值。  請參閱下列表格，取得 **nullValue** 的註釋。  預設為 **\_throw**。|  
  
 下列表格顯示可指定為 **nullValue** 註釋的值。  
  
|nullValue 值|描述|  
|-----------------|--------|  
|*取代值*|指定要傳回的值。  傳回值必須與項目的型別相符。  例如，使用 `nullValue="0"` 可為 null 整數欄位傳回 0。|  
|**\_throw**|擲回例外狀況。  這是預設值。|  
|**\_null**|如果遇到基本型別，則會傳回 Null 參考或發生例外狀況。|  
|**\_empty**|如果是字串，則傳回 **String.Empty**，否則傳回空的建構函式所建立的物件。  如果遇到基本型別，則會發生例外狀況。|  
  
 下表顯示具型別之 **DataSet** 內的物件預設值，以及可用的註釋。  
  
|物件\/方法\/事件|預設|註釋|  
|----------------|--------|--------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**DataTable** 方法|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**屬性**|PropertyName|typedName|  
|**Child** 存取子|GetChildTableNameRows|typedChildren|  
|**Parent** 存取子|TableNameRow|typedParent|  
|**DataSet** 事件|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 若要使用具型別的 **DataSet** 註釋，您必須將下列 **xmlns** 參考加入您的 XML 結構描述定義語言 \(XSD\) 的結構描述。  \(若要從資料庫資料表建立 xsd，請參閱 <xref:System.Data.DataSet.WriteXmlSchema%2A> 或[使用 Visual Studio 中的資料集](http://msdn.microsoft.com/library/8bw9ksd6.aspx)\)。  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 以下是具有註釋的結構描述範例，其公開 **Northwind** 資料庫的 **Customers** 資料表與內含之 **Orders** 資料表的關聯。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer"  
codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone"  
codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order"  
codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"  
                 codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter"  
codegen:nullValue="1980-01-01T00:00:00"   
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 下列程式碼範例使用從範例結構描述建立的強型別 **DataSet**。  它會使用 <xref:System.Data.SqlClient.SqlDataAdapter> 來填入 **Customers** 資料表，並使用另一個 <xref:System.Data.SqlClient.SqlDataAdapter> 來填入 **Orders** 資料表。  強型別的 **DataSet** 可定義 **DataRelation**。  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomeromer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",   
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new   
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =   
    customers.Customers.NewCustomeromer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## 請參閱  
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataSet>   
 [具型別的 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)