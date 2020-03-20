---
title: 註釋具類型資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 757a87f92d8dc6049de1844fed892d95dc57c990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151516"
---
# <a name="annotating-typed-datasets"></a>註釋具類型資料集
註釋可讓您在無需修改基礎結構描述的情況下，修改具型別之 <xref:System.Data.DataSet> 中的項目名稱。 修改基礎架構中元素的名稱將導致鍵入的**DataSet**參考資料源中不存在的物件，並丟失對資料來源中確實存在物件的引用。  
  
 使用注釋，您可以使用更有意義的名稱自訂鍵入的**DataSet**中的物件名稱，使代碼更具可讀性，並使鍵入的**DataSet**更易於用戶端使用，同時保留基礎架構不變。 例如 **，Northwind**資料庫**的客戶**表的以下架構元素將導致**客戶行**的<xref:System.Data.DataRowCollection>**DataRow**物件名稱和命名的**客戶**。  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 **客戶** **DataRow 集合**名稱在用戶端代碼中有意義，但**客戶行** **DataRow**名稱具有誤導性，因為它是單個物件。 此外，在常見方案中，將引用該物件而不帶**行**識別碼，而將簡單地稱為**客戶**物件。 解決方案是對架構進行批號，並標識**DataRow**和**DataRowCollection**物件的新名稱。 下列為上述結構描述的標註版本。  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 指定**客戶的****類型名稱**值將導致**客戶**的**DataRow**物件名稱。 指定客戶的**鍵入的複數**值**Customers**將保留**客戶****的資料羅集合**名稱。  
  
 下列表格顯示可供使用的註釋。  
  
|Annotation|描述|  
|----------------|-----------------|  
|**typedName**|物件的名稱。|  
|**typedPlural**|物件集合名稱。|  
|**typedParent**|在父關聯性中所參考的物件名稱。|  
|**typedChildren**|從子關聯性傳回物件的方法名稱。|  
|**空值**|如果基礎值為**DBNull**，則值。 有關**nullValue**注釋，請參閱下表。 預設值為 **_throw**。|  
  
 下表顯示了可以為**nullValue**注釋指定的值。  
  
|nullValue 值|描述|  
|---------------------|-----------------|  
|*重置值*|指定要傳回的值。 傳回值必須與項目的型別相符。 例如，使用 `nullValue="0"` 可為 null 整數欄位傳回 0。|  
|**_throw**|擲回例外狀況。 這是預設值。|  
|**_null**|如果遇到基本型別，則會傳回 Null 參考或發生例外狀況。|  
|**_empty**|對於字串，返回**String.empty**，否則返回從空建構函式創建的物件。 如果遇到基本型別，則會發生例外狀況。|  
  
 下表顯示了類型**化 DataSet**中物件的預設值和可用的批註。  
  
|物件/方法/事件|預設|Annotation|  
|---------------------------|-------------|----------------|  
|**資料表**|TableNameDataTable|typedPlural|  
|**資料表**方法|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**資料行**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**屬性**|PropertyName|typedName|  
|**兒童**訪問|GetChildTableNameRows|typedChildren|  
|**父級**訪問|TableNameRow|typedParent|  
|**資料集**事件|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 要使用鍵入的**DataSet**注釋，必須在 XML 架構定義語言 （XSD） 架構中包括以下**xmlns**引用。 要從資料庫表創建 xsd，請參閱<xref:System.Data.DataSet.WriteXmlSchema%2A>或使用[視覺化工作室中的資料集](/visualstudio/data-tools/dataset-tools-in-visual-studio)。  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 下面是一個帶批號的示例架構，該架構公開了**Northwind**資料庫**的客戶**表，該表與包含**的訂單**表相關。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""
      xmlns:xs="http://www.w3.org/2001/XMLSchema"
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"
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
  
 以下代碼示例使用從示例架構創建的強型別**資料集**。 它使用一<xref:System.Data.SqlClient.SqlDataAdapter>個填充**客戶**表，另一<xref:System.Data.SqlClient.SqlDataAdapter>個用於填充**訂單**表。 強型別**資料集**定義**資料關係**。  
  
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
    customers.Customers.NewCustomer()  
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
    customers.Customers.NewCustomer();  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [具類型資料集](typed-datasets.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
