---
title: 註釋具類型資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 79d3913827d5df6f0ac4e77bfdb8f37b553a86d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203744"
---
# <a name="annotating-typed-datasets"></a>註釋具類型資料集

註釋可讓您在無需修改基礎結構描述的情況下，修改具型別之 <xref:System.Data.DataSet> 中的項目名稱。 修改基礎架構中的元素名稱，會導致具類型的 **資料集** 參考不存在於資料來源中的物件，以及遺失存在於資料來源中的物件參考。  
  
 您可以使用批註，以更有意義的名稱自訂具型別 **資料集** 內的物件名稱，使程式碼更容易閱讀，並讓用戶端更容易使用具類型的 **資料集** ，同時讓基礎架構保持不變。 例如， **Northwind**資料庫之**Customers**資料表的下列 Schema 元素會產生**DataRow**物件名稱**CustomersRow**和一個 <xref:System.Data.DataRowCollection> 命名的**客戶**。  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 用戶端程式代碼中有意義的**客戶** **DataRowCollection**名稱，但**CustomersRow**的**DataRow**名稱會誤導，因為它是單一物件。 此外，在常見的案例中，物件不會被參考資料 **列** 識別碼，而是直接稱為 **客戶** 物件。 解決方法是為 **DataRow** 和 **DataRowCollection** 物件的架構加上批註，並識別新的名稱。 下列為上述結構描述的標註版本。  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 指定**customer**的**typedName**值將會導致**客戶**的**DataRow**物件名稱。 指定**客戶**的**typedPlural**值會保留**客戶**的**DataRowCollection**名稱。  
  
 下列表格顯示可供使用的註釋。  
  
|Annotation|描述|  
|----------------|-----------------|  
|**typedName**|物件的名稱。|  
|**typedPlural**|物件集合名稱。|  
|**typedParent**|在父關聯性中所參考的物件名稱。|  
|**typedChildren**|從子關聯性傳回物件的方法名稱。|  
|**nullValue**|值，如果基礎值為 **DBNull**。 請參閱下表中的 **nullValue** 批註。 預設值為 **_throw**。|  
  
 下表顯示可針對 **nullValue** 批註指定的值。  
  
|nullValue 值|描述|  
|---------------------|-----------------|  
|*取代值*|指定要傳回的值。 傳回值必須與項目的型別相符。 例如，使用 `nullValue="0"` 可為 null 整數欄位傳回 0。|  
|**_throw**|擲回例外狀況。 此為預設值。|  
|**_null**|如果遇到基本型別，則會傳回 Null 參考或發生例外狀況。|  
|**_empty**|如果是字串，則傳回 **字串空白**，否則會傳回從空白的函式建立的物件。 如果遇到基本型別，則會發生例外狀況。|  
  
 下表顯示具型別 **資料集** 內物件的預設值，以及可用的批註。  
  
|物件/方法/事件|預設|Annotation|  
|---------------------------|-------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**DataTable** 方法|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**屬性**|PropertyName|typedName|  
|**子** 系訪問|GetChildTableNameRows|typedChildren|  
|**父系** 訪問|TableNameRow|typedParent|  
|**資料集** 事件|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 若要使用具類型的 **資料集** 注釋，您必須在 XML 架構定義語言中包含下列 **XMLNS** 參考 (XSD) 架構。 若要從資料庫資料表建立 xsd，請參閱 <xref:System.Data.DataSet.WriteXmlSchema%2A> 或 [使用 Visual Studio 中的資料集](/visualstudio/data-tools/dataset-tools-in-visual-studio)。  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 以下是批註式架構範例，其公開**Northwind**資料庫的**Customers**資料表與內含之**Orders**資料表的關聯。  
  
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
  
 下列程式碼範例會使用從範例架構建立的強型別 **資料集** 。 它會使用一個 <xref:System.Data.SqlClient.SqlDataAdapter> 來填入 **Customers** 資料表，另一個用 <xref:System.Data.SqlClient.SqlDataAdapter> 來填入 **Orders** 資料表。 強型別 **資料集** 定義了 **datarelation**。  
  
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
