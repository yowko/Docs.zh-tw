---
title: 註釋具類型資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 1974ac71e367203b8b94375e43d4fde13f2df51f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="b6696-102">註釋具類型資料集</span><span class="sxs-lookup"><span data-stu-id="b6696-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="b6696-103">註釋可讓您在無需修改基礎結構描述的情況下，修改具型別之 <xref:System.Data.DataSet> 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="b6696-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="b6696-104">修改您的基礎結構描述中的項目名稱可能會造成具型別的**資料集**來執行不存在於資料來源，也會遺失的資料來源中存在的物件參考的物件參考。</span><span class="sxs-lookup"><span data-stu-id="b6696-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="b6696-105">使用註釋，您可以自訂物件的名稱將具型別的**資料集**為更有意義的名稱，使程式碼更容易閱讀，將具型別的**資料集**便於使用，同時保留的用戶端基礎結構描述不變。</span><span class="sxs-lookup"><span data-stu-id="b6696-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="b6696-106">例如，下列結構描述項目為**客戶**資料表**Northwind**資料庫會導致**DataRow**物件名稱的**CustomersRow**和<xref:System.Data.DataRowCollection>名為**客戶**。</span><span class="sxs-lookup"><span data-stu-id="b6696-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="b6696-107">A **DataRowCollection**名稱**客戶**是用戶端程式碼中，有意義，但**DataRow**名稱**CustomersRow**容易發生錯誤因為它是單一物件。</span><span class="sxs-lookup"><span data-stu-id="b6696-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="b6696-108">此外，在一般情況下，物件會正確參考**列**識別項，而是會直接稱為**客戶**物件。</span><span class="sxs-lookup"><span data-stu-id="b6696-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="b6696-109">解決方法是結構描述註解，並找出新名稱**DataRow**和**DataRowCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="b6696-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="b6696-110">下列為上述結構描述的標註版本。</span><span class="sxs-lookup"><span data-stu-id="b6696-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="b6696-111">指定**Customer**值**客戶**會導致**DataRow**物件名稱的**客戶**。</span><span class="sxs-lookup"><span data-stu-id="b6696-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="b6696-112">指定**Customers**值**客戶**保留**DataRowCollection**名稱**客戶**。</span><span class="sxs-lookup"><span data-stu-id="b6696-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="b6696-113">下列表格顯示可供使用的註釋。</span><span class="sxs-lookup"><span data-stu-id="b6696-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="b6696-114">註釋</span><span class="sxs-lookup"><span data-stu-id="b6696-114">Annotation</span></span>|<span data-ttu-id="b6696-115">描述</span><span class="sxs-lookup"><span data-stu-id="b6696-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="b6696-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="b6696-116">**typedName**</span></span>|<span data-ttu-id="b6696-117">物件名稱。</span><span class="sxs-lookup"><span data-stu-id="b6696-117">Name of the object.</span></span>|  
|<span data-ttu-id="b6696-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="b6696-118">**typedPlural**</span></span>|<span data-ttu-id="b6696-119">物件集合名稱。</span><span class="sxs-lookup"><span data-stu-id="b6696-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="b6696-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="b6696-120">**typedParent**</span></span>|<span data-ttu-id="b6696-121">在父關聯性中所參考的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="b6696-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="b6696-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="b6696-122">**typedChildren**</span></span>|<span data-ttu-id="b6696-123">從子關聯性傳回物件的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="b6696-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="b6696-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="b6696-124">**nullValue**</span></span>|<span data-ttu-id="b6696-125">值，如果基礎值為**DBNull**。</span><span class="sxs-lookup"><span data-stu-id="b6696-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="b6696-126">請參閱下的表針對**nullValue**註解。</span><span class="sxs-lookup"><span data-stu-id="b6696-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="b6696-127">預設值是 **_throw**。</span><span class="sxs-lookup"><span data-stu-id="b6696-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="b6696-128">下表顯示可以針對指定的值**nullValue**註解。</span><span class="sxs-lookup"><span data-stu-id="b6696-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="b6696-129">nullValue 值</span><span class="sxs-lookup"><span data-stu-id="b6696-129">nullValue Value</span></span>|<span data-ttu-id="b6696-130">描述</span><span class="sxs-lookup"><span data-stu-id="b6696-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="b6696-131">*取代值*</span><span class="sxs-lookup"><span data-stu-id="b6696-131">*Replacement Value*</span></span>|<span data-ttu-id="b6696-132">指定要傳回的值。</span><span class="sxs-lookup"><span data-stu-id="b6696-132">Specify a value to be returned.</span></span> <span data-ttu-id="b6696-133">傳回值必須與項目的型別相符。</span><span class="sxs-lookup"><span data-stu-id="b6696-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="b6696-134">例如，使用 `nullValue="0"` 可為 null 整數欄位傳回 0。</span><span class="sxs-lookup"><span data-stu-id="b6696-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="b6696-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="b6696-135">**_throw**</span></span>|<span data-ttu-id="b6696-136">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b6696-136">Throw an exception.</span></span> <span data-ttu-id="b6696-137">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="b6696-137">This is the default.</span></span>|  
|<span data-ttu-id="b6696-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="b6696-138">**_null**</span></span>|<span data-ttu-id="b6696-139">如果遇到基本型別，則會傳回 Null 參考或發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b6696-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="b6696-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="b6696-140">**_empty**</span></span>|<span data-ttu-id="b6696-141">字串，則傳回**String.Empty**，否則會傳回空的建構函式從建立物件。</span><span class="sxs-lookup"><span data-stu-id="b6696-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="b6696-142">如果遇到基本型別，則會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b6696-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="b6696-143">下表顯示在具類型之物件的預設值**資料集**和可用的註釋。</span><span class="sxs-lookup"><span data-stu-id="b6696-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="b6696-144">物件/方法/事件</span><span class="sxs-lookup"><span data-stu-id="b6696-144">Object/Method/Event</span></span>|<span data-ttu-id="b6696-145">預設</span><span class="sxs-lookup"><span data-stu-id="b6696-145">Default</span></span>|<span data-ttu-id="b6696-146">註釋</span><span class="sxs-lookup"><span data-stu-id="b6696-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="b6696-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="b6696-147">**DataTable**</span></span>|<span data-ttu-id="b6696-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="b6696-148">TableNameDataTable</span></span>|<span data-ttu-id="b6696-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="b6696-149">typedPlural</span></span>|  
|<span data-ttu-id="b6696-150">**DataTable**方法</span><span class="sxs-lookup"><span data-stu-id="b6696-150">**DataTable** Methods</span></span>|<span data-ttu-id="b6696-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="b6696-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="b6696-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="b6696-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="b6696-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="b6696-153">DeleteTableNameRow</span></span>|<span data-ttu-id="b6696-154">typedName</span><span class="sxs-lookup"><span data-stu-id="b6696-154">typedName</span></span>|  
|<span data-ttu-id="b6696-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="b6696-155">**DataRowCollection**</span></span>|<span data-ttu-id="b6696-156">TableName</span><span class="sxs-lookup"><span data-stu-id="b6696-156">TableName</span></span>|<span data-ttu-id="b6696-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="b6696-157">typedPlural</span></span>|  
|<span data-ttu-id="b6696-158">**dataRow**</span><span class="sxs-lookup"><span data-stu-id="b6696-158">**DataRow**</span></span>|<span data-ttu-id="b6696-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="b6696-159">TableNameRow</span></span>|<span data-ttu-id="b6696-160">typedName</span><span class="sxs-lookup"><span data-stu-id="b6696-160">typedName</span></span>|  
|<span data-ttu-id="b6696-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="b6696-161">**DataColumn**</span></span>|<span data-ttu-id="b6696-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="b6696-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="b6696-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="b6696-163">DataRow.ColumnName</span></span>|<span data-ttu-id="b6696-164">typedName</span><span class="sxs-lookup"><span data-stu-id="b6696-164">typedName</span></span>|  
|<span data-ttu-id="b6696-165">**Property**</span><span class="sxs-lookup"><span data-stu-id="b6696-165">**Property**</span></span>|<span data-ttu-id="b6696-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="b6696-166">PropertyName</span></span>|<span data-ttu-id="b6696-167">typedName</span><span class="sxs-lookup"><span data-stu-id="b6696-167">typedName</span></span>|  
|<span data-ttu-id="b6696-168">**子**存取子</span><span class="sxs-lookup"><span data-stu-id="b6696-168">**Child** Accessor</span></span>|<span data-ttu-id="b6696-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="b6696-169">GetChildTableNameRows</span></span>|<span data-ttu-id="b6696-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="b6696-170">typedChildren</span></span>|  
|<span data-ttu-id="b6696-171">**父**存取子</span><span class="sxs-lookup"><span data-stu-id="b6696-171">**Parent** Accessor</span></span>|<span data-ttu-id="b6696-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="b6696-172">TableNameRow</span></span>|<span data-ttu-id="b6696-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="b6696-173">typedParent</span></span>|  
|<span data-ttu-id="b6696-174">**資料集**事件</span><span class="sxs-lookup"><span data-stu-id="b6696-174">**DataSet** Events</span></span>|<span data-ttu-id="b6696-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="b6696-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="b6696-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="b6696-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="b6696-177">typedName</span><span class="sxs-lookup"><span data-stu-id="b6696-177">typedName</span></span>|  
  
 <span data-ttu-id="b6696-178">若使用具型別**資料集**註解，您必須包含下列**xmlns** XML 結構描述定義語言 (XSD) 結構描述中的參考。</span><span class="sxs-lookup"><span data-stu-id="b6696-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="b6696-179">(若要從資料庫資料表建立 xsd，請參閱<xref:System.Data.DataSet.WriteXmlSchema%2A>或[使用 Visual Studio 中的資料集](http://msdn.microsoft.com/library/8bw9ksd6.aspx))。</span><span class="sxs-lookup"><span data-stu-id="b6696-179">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="b6696-180">以下是範例的註解式結構描述會公開**客戶**資料表**Northwind**資料庫的關聯性**訂單**包含資料表中。</span><span class="sxs-lookup"><span data-stu-id="b6696-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="b6696-181">下列程式碼範例會使用強型別**資料集**從範例結構描述建立。</span><span class="sxs-lookup"><span data-stu-id="b6696-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="b6696-182">它會使用其中一個<xref:System.Data.SqlClient.SqlDataAdapter>填入**客戶**資料表，而另一個<xref:System.Data.SqlClient.SqlDataAdapter>填入**訂單**資料表。</span><span class="sxs-lookup"><span data-stu-id="b6696-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="b6696-183">強型別**資料集**定義**Datarelation**。</span><span class="sxs-lookup"><span data-stu-id="b6696-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6696-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6696-184">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="b6696-185">具類型的 DataSet</span><span class="sxs-lookup"><span data-stu-id="b6696-185">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="b6696-186">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="b6696-186">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="b6696-187">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b6696-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
