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
# <a name="annotating-typed-datasets"></a><span data-ttu-id="12d9b-102">註釋具類型資料集</span><span class="sxs-lookup"><span data-stu-id="12d9b-102">Annotating Typed DataSets</span></span>

<span data-ttu-id="12d9b-103">註釋可讓您在無需修改基礎結構描述的情況下，修改具型別之 <xref:System.Data.DataSet> 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="12d9b-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="12d9b-104">修改基礎架構中的元素名稱，會導致具類型的 **資料集** 參考不存在於資料來源中的物件，以及遺失存在於資料來源中的物件參考。</span><span class="sxs-lookup"><span data-stu-id="12d9b-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="12d9b-105">您可以使用批註，以更有意義的名稱自訂具型別 **資料集** 內的物件名稱，使程式碼更容易閱讀，並讓用戶端更容易使用具類型的 **資料集** ，同時讓基礎架構保持不變。</span><span class="sxs-lookup"><span data-stu-id="12d9b-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="12d9b-106">例如， **Northwind**資料庫之**Customers**資料表的下列 Schema 元素會產生**DataRow**物件名稱**CustomersRow**和一個 <xref:System.Data.DataRowCollection> 命名的**客戶**。</span><span class="sxs-lookup"><span data-stu-id="12d9b-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="12d9b-107">用戶端程式代碼中有意義的**客戶** **DataRowCollection**名稱，但**CustomersRow**的**DataRow**名稱會誤導，因為它是單一物件。</span><span class="sxs-lookup"><span data-stu-id="12d9b-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="12d9b-108">此外，在常見的案例中，物件不會被參考資料 **列** 識別碼，而是直接稱為 **客戶** 物件。</span><span class="sxs-lookup"><span data-stu-id="12d9b-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="12d9b-109">解決方法是為 **DataRow** 和 **DataRowCollection** 物件的架構加上批註，並識別新的名稱。</span><span class="sxs-lookup"><span data-stu-id="12d9b-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="12d9b-110">下列為上述結構描述的標註版本。</span><span class="sxs-lookup"><span data-stu-id="12d9b-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="12d9b-111">指定**customer**的**typedName**值將會導致**客戶**的**DataRow**物件名稱。</span><span class="sxs-lookup"><span data-stu-id="12d9b-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="12d9b-112">指定**客戶**的**typedPlural**值會保留**客戶**的**DataRowCollection**名稱。</span><span class="sxs-lookup"><span data-stu-id="12d9b-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="12d9b-113">下列表格顯示可供使用的註釋。</span><span class="sxs-lookup"><span data-stu-id="12d9b-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="12d9b-114">Annotation</span><span class="sxs-lookup"><span data-stu-id="12d9b-114">Annotation</span></span>|<span data-ttu-id="12d9b-115">描述</span><span class="sxs-lookup"><span data-stu-id="12d9b-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="12d9b-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="12d9b-116">**typedName**</span></span>|<span data-ttu-id="12d9b-117">物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="12d9b-117">Name of the object.</span></span>|  
|<span data-ttu-id="12d9b-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="12d9b-118">**typedPlural**</span></span>|<span data-ttu-id="12d9b-119">物件集合名稱。</span><span class="sxs-lookup"><span data-stu-id="12d9b-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="12d9b-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="12d9b-120">**typedParent**</span></span>|<span data-ttu-id="12d9b-121">在父關聯性中所參考的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="12d9b-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="12d9b-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="12d9b-122">**typedChildren**</span></span>|<span data-ttu-id="12d9b-123">從子關聯性傳回物件的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="12d9b-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="12d9b-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="12d9b-124">**nullValue**</span></span>|<span data-ttu-id="12d9b-125">值，如果基礎值為 **DBNull**。</span><span class="sxs-lookup"><span data-stu-id="12d9b-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="12d9b-126">請參閱下表中的 **nullValue** 批註。</span><span class="sxs-lookup"><span data-stu-id="12d9b-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="12d9b-127">預設值為 **_throw**。</span><span class="sxs-lookup"><span data-stu-id="12d9b-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="12d9b-128">下表顯示可針對 **nullValue** 批註指定的值。</span><span class="sxs-lookup"><span data-stu-id="12d9b-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="12d9b-129">nullValue 值</span><span class="sxs-lookup"><span data-stu-id="12d9b-129">nullValue Value</span></span>|<span data-ttu-id="12d9b-130">描述</span><span class="sxs-lookup"><span data-stu-id="12d9b-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="12d9b-131">*取代值*</span><span class="sxs-lookup"><span data-stu-id="12d9b-131">*Replacement Value*</span></span>|<span data-ttu-id="12d9b-132">指定要傳回的值。</span><span class="sxs-lookup"><span data-stu-id="12d9b-132">Specify a value to be returned.</span></span> <span data-ttu-id="12d9b-133">傳回值必須與項目的型別相符。</span><span class="sxs-lookup"><span data-stu-id="12d9b-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="12d9b-134">例如，使用 `nullValue="0"` 可為 null 整數欄位傳回 0。</span><span class="sxs-lookup"><span data-stu-id="12d9b-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="12d9b-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="12d9b-135">**_throw**</span></span>|<span data-ttu-id="12d9b-136">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="12d9b-136">Throw an exception.</span></span> <span data-ttu-id="12d9b-137">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="12d9b-137">This is the default.</span></span>|  
|<span data-ttu-id="12d9b-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="12d9b-138">**_null**</span></span>|<span data-ttu-id="12d9b-139">如果遇到基本型別，則會傳回 Null 參考或發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="12d9b-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="12d9b-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="12d9b-140">**_empty**</span></span>|<span data-ttu-id="12d9b-141">如果是字串，則傳回 **字串空白**，否則會傳回從空白的函式建立的物件。</span><span class="sxs-lookup"><span data-stu-id="12d9b-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="12d9b-142">如果遇到基本型別，則會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="12d9b-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="12d9b-143">下表顯示具型別 **資料集** 內物件的預設值，以及可用的批註。</span><span class="sxs-lookup"><span data-stu-id="12d9b-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="12d9b-144">物件/方法/事件</span><span class="sxs-lookup"><span data-stu-id="12d9b-144">Object/Method/Event</span></span>|<span data-ttu-id="12d9b-145">預設</span><span class="sxs-lookup"><span data-stu-id="12d9b-145">Default</span></span>|<span data-ttu-id="12d9b-146">Annotation</span><span class="sxs-lookup"><span data-stu-id="12d9b-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="12d9b-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="12d9b-147">**DataTable**</span></span>|<span data-ttu-id="12d9b-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="12d9b-148">TableNameDataTable</span></span>|<span data-ttu-id="12d9b-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="12d9b-149">typedPlural</span></span>|  
|<span data-ttu-id="12d9b-150">**DataTable** 方法</span><span class="sxs-lookup"><span data-stu-id="12d9b-150">**DataTable** Methods</span></span>|<span data-ttu-id="12d9b-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="12d9b-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="12d9b-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="12d9b-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="12d9b-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="12d9b-153">DeleteTableNameRow</span></span>|<span data-ttu-id="12d9b-154">typedName</span><span class="sxs-lookup"><span data-stu-id="12d9b-154">typedName</span></span>|  
|<span data-ttu-id="12d9b-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="12d9b-155">**DataRowCollection**</span></span>|<span data-ttu-id="12d9b-156">TableName</span><span class="sxs-lookup"><span data-stu-id="12d9b-156">TableName</span></span>|<span data-ttu-id="12d9b-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="12d9b-157">typedPlural</span></span>|  
|<span data-ttu-id="12d9b-158">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="12d9b-158">**DataRow**</span></span>|<span data-ttu-id="12d9b-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="12d9b-159">TableNameRow</span></span>|<span data-ttu-id="12d9b-160">typedName</span><span class="sxs-lookup"><span data-stu-id="12d9b-160">typedName</span></span>|  
|<span data-ttu-id="12d9b-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="12d9b-161">**DataColumn**</span></span>|<span data-ttu-id="12d9b-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="12d9b-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="12d9b-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="12d9b-163">DataRow.ColumnName</span></span>|<span data-ttu-id="12d9b-164">typedName</span><span class="sxs-lookup"><span data-stu-id="12d9b-164">typedName</span></span>|  
|<span data-ttu-id="12d9b-165">**屬性**</span><span class="sxs-lookup"><span data-stu-id="12d9b-165">**Property**</span></span>|<span data-ttu-id="12d9b-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="12d9b-166">PropertyName</span></span>|<span data-ttu-id="12d9b-167">typedName</span><span class="sxs-lookup"><span data-stu-id="12d9b-167">typedName</span></span>|  
|<span data-ttu-id="12d9b-168">**子** 系訪問</span><span class="sxs-lookup"><span data-stu-id="12d9b-168">**Child** Accessor</span></span>|<span data-ttu-id="12d9b-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="12d9b-169">GetChildTableNameRows</span></span>|<span data-ttu-id="12d9b-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="12d9b-170">typedChildren</span></span>|  
|<span data-ttu-id="12d9b-171">**父系** 訪問</span><span class="sxs-lookup"><span data-stu-id="12d9b-171">**Parent** Accessor</span></span>|<span data-ttu-id="12d9b-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="12d9b-172">TableNameRow</span></span>|<span data-ttu-id="12d9b-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="12d9b-173">typedParent</span></span>|  
|<span data-ttu-id="12d9b-174">**資料集** 事件</span><span class="sxs-lookup"><span data-stu-id="12d9b-174">**DataSet** Events</span></span>|<span data-ttu-id="12d9b-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="12d9b-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="12d9b-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="12d9b-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="12d9b-177">typedName</span><span class="sxs-lookup"><span data-stu-id="12d9b-177">typedName</span></span>|  
  
 <span data-ttu-id="12d9b-178">若要使用具類型的 **資料集** 注釋，您必須在 XML 架構定義語言中包含下列 **XMLNS** 參考 (XSD) 架構。</span><span class="sxs-lookup"><span data-stu-id="12d9b-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="12d9b-179">若要從資料庫資料表建立 xsd，請參閱 <xref:System.Data.DataSet.WriteXmlSchema%2A> 或 [使用 Visual Studio 中的資料集](/visualstudio/data-tools/dataset-tools-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="12d9b-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="12d9b-180">以下是批註式架構範例，其公開**Northwind**資料庫的**Customers**資料表與內含之**Orders**資料表的關聯。</span><span class="sxs-lookup"><span data-stu-id="12d9b-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="12d9b-181">下列程式碼範例會使用從範例架構建立的強型別 **資料集** 。</span><span class="sxs-lookup"><span data-stu-id="12d9b-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="12d9b-182">它會使用一個 <xref:System.Data.SqlClient.SqlDataAdapter> 來填入 **Customers** 資料表，另一個用 <xref:System.Data.SqlClient.SqlDataAdapter> 來填入 **Orders** 資料表。</span><span class="sxs-lookup"><span data-stu-id="12d9b-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="12d9b-183">強型別 **資料集** 定義了 **datarelation**。</span><span class="sxs-lookup"><span data-stu-id="12d9b-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12d9b-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12d9b-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="12d9b-185">具類型資料集</span><span class="sxs-lookup"><span data-stu-id="12d9b-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="12d9b-186">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="12d9b-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="12d9b-187">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="12d9b-187">[ADO.NET Overview](../ado-net-overview.md)</span></span>
