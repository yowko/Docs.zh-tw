---
title: 註釋具類型資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 8ce7cd859ce0c9a5874751e9928e5bced33593d6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205245"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="22889-102">註釋具類型資料集</span><span class="sxs-lookup"><span data-stu-id="22889-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="22889-103">註釋可讓您在無需修改基礎結構描述的情況下，修改具型別之 <xref:System.Data.DataSet> 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="22889-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="22889-104">修改基礎架構中的元素名稱, 會導致具類型的**資料集**參考不存在於資料來源中的物件, 也會遺失資料來源中的物件參考。</span><span class="sxs-lookup"><span data-stu-id="22889-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="22889-105">您可以使用批註, 以更有意義的名稱自訂具類型**資料集**內物件的名稱, 使程式碼更容易閱讀, 並讓用戶端更輕鬆地使用具類型的**資料集**, 同時讓基礎架構保持不變。</span><span class="sxs-lookup"><span data-stu-id="22889-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="22889-106">例如, **Northwind**資料庫的**Customers**資料表的下列 schema 元素會產生**DataRow**物件<xref:System.Data.DataRowCollection>名稱**CustomersRow**和名為**Customers**。</span><span class="sxs-lookup"><span data-stu-id="22889-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="22889-107">用戶端程式代碼中的**DataRowCollection**名稱是有意義的, 但是**CustomersRow**的**DataRow**名稱會誤導, 因為它是單一物件。</span><span class="sxs-lookup"><span data-stu-id="22889-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="22889-108">此外, 在常見的案例中, 物件會在沒有資料**列**識別碼的情況下被參考, 而是直接稱為**Customer**物件。</span><span class="sxs-lookup"><span data-stu-id="22889-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="22889-109">解決方案是要標注架構, 並識別**DataRow**和**DataRowCollection**物件的新名稱。</span><span class="sxs-lookup"><span data-stu-id="22889-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="22889-110">下列為上述結構描述的標註版本。</span><span class="sxs-lookup"><span data-stu-id="22889-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="22889-111">指定**customer**的**typedName**值會產生**DataRow**物件名稱**customer**。</span><span class="sxs-lookup"><span data-stu-id="22889-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="22889-112">指定**客戶**的**typedPlural**值會保留**客戶**的**DataRowCollection**名稱。</span><span class="sxs-lookup"><span data-stu-id="22889-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="22889-113">下列表格顯示可供使用的註釋。</span><span class="sxs-lookup"><span data-stu-id="22889-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="22889-114">註釋</span><span class="sxs-lookup"><span data-stu-id="22889-114">Annotation</span></span>|<span data-ttu-id="22889-115">描述</span><span class="sxs-lookup"><span data-stu-id="22889-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="22889-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="22889-116">**typedName**</span></span>|<span data-ttu-id="22889-117">物件名稱。</span><span class="sxs-lookup"><span data-stu-id="22889-117">Name of the object.</span></span>|  
|<span data-ttu-id="22889-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="22889-118">**typedPlural**</span></span>|<span data-ttu-id="22889-119">物件集合名稱。</span><span class="sxs-lookup"><span data-stu-id="22889-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="22889-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="22889-120">**typedParent**</span></span>|<span data-ttu-id="22889-121">在父關聯性中所參考的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="22889-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="22889-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="22889-122">**typedChildren**</span></span>|<span data-ttu-id="22889-123">從子關聯性傳回物件的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="22889-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="22889-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="22889-124">**nullValue**</span></span>|<span data-ttu-id="22889-125">如果基礎值為**DBNull**, 則為值。</span><span class="sxs-lookup"><span data-stu-id="22889-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="22889-126">請參閱下表中的**nullValue**批註。</span><span class="sxs-lookup"><span data-stu-id="22889-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="22889-127">預設值為 **_throw**。</span><span class="sxs-lookup"><span data-stu-id="22889-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="22889-128">下表顯示可針對**nullValue**注釋指定的值。</span><span class="sxs-lookup"><span data-stu-id="22889-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="22889-129">nullValue 值</span><span class="sxs-lookup"><span data-stu-id="22889-129">nullValue Value</span></span>|<span data-ttu-id="22889-130">說明</span><span class="sxs-lookup"><span data-stu-id="22889-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="22889-131">*取代值*</span><span class="sxs-lookup"><span data-stu-id="22889-131">*Replacement Value*</span></span>|<span data-ttu-id="22889-132">指定要傳回的值。</span><span class="sxs-lookup"><span data-stu-id="22889-132">Specify a value to be returned.</span></span> <span data-ttu-id="22889-133">傳回值必須與項目的型別相符。</span><span class="sxs-lookup"><span data-stu-id="22889-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="22889-134">例如，使用 `nullValue="0"` 可為 null 整數欄位傳回 0。</span><span class="sxs-lookup"><span data-stu-id="22889-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="22889-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="22889-135">**_throw**</span></span>|<span data-ttu-id="22889-136">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="22889-136">Throw an exception.</span></span> <span data-ttu-id="22889-137">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="22889-137">This is the default.</span></span>|  
|<span data-ttu-id="22889-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="22889-138">**_null**</span></span>|<span data-ttu-id="22889-139">如果遇到基本型別，則會傳回 Null 參考或發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="22889-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="22889-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="22889-140">**_empty**</span></span>|<span data-ttu-id="22889-141">如果是字串, 則傳回**String**, 否則會傳回從空白的函式建立的物件。</span><span class="sxs-lookup"><span data-stu-id="22889-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="22889-142">如果遇到基本型別，則會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="22889-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="22889-143">下表顯示具類型**資料集**內物件的預設值, 以及可用的注釋。</span><span class="sxs-lookup"><span data-stu-id="22889-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="22889-144">物件/方法/事件</span><span class="sxs-lookup"><span data-stu-id="22889-144">Object/Method/Event</span></span>|<span data-ttu-id="22889-145">預設</span><span class="sxs-lookup"><span data-stu-id="22889-145">Default</span></span>|<span data-ttu-id="22889-146">註釋</span><span class="sxs-lookup"><span data-stu-id="22889-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="22889-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="22889-147">**DataTable**</span></span>|<span data-ttu-id="22889-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="22889-148">TableNameDataTable</span></span>|<span data-ttu-id="22889-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="22889-149">typedPlural</span></span>|  
|<span data-ttu-id="22889-150">**DataTable**方法</span><span class="sxs-lookup"><span data-stu-id="22889-150">**DataTable** Methods</span></span>|<span data-ttu-id="22889-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="22889-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="22889-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="22889-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="22889-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="22889-153">DeleteTableNameRow</span></span>|<span data-ttu-id="22889-154">typedName</span><span class="sxs-lookup"><span data-stu-id="22889-154">typedName</span></span>|  
|<span data-ttu-id="22889-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="22889-155">**DataRowCollection**</span></span>|<span data-ttu-id="22889-156">TableName</span><span class="sxs-lookup"><span data-stu-id="22889-156">TableName</span></span>|<span data-ttu-id="22889-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="22889-157">typedPlural</span></span>|  
|<span data-ttu-id="22889-158">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="22889-158">**DataRow**</span></span>|<span data-ttu-id="22889-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="22889-159">TableNameRow</span></span>|<span data-ttu-id="22889-160">typedName</span><span class="sxs-lookup"><span data-stu-id="22889-160">typedName</span></span>|  
|<span data-ttu-id="22889-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="22889-161">**DataColumn**</span></span>|<span data-ttu-id="22889-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="22889-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="22889-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="22889-163">DataRow.ColumnName</span></span>|<span data-ttu-id="22889-164">typedName</span><span class="sxs-lookup"><span data-stu-id="22889-164">typedName</span></span>|  
|<span data-ttu-id="22889-165">**Property**</span><span class="sxs-lookup"><span data-stu-id="22889-165">**Property**</span></span>|<span data-ttu-id="22889-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="22889-166">PropertyName</span></span>|<span data-ttu-id="22889-167">typedName</span><span class="sxs-lookup"><span data-stu-id="22889-167">typedName</span></span>|  
|<span data-ttu-id="22889-168">**子**系存取</span><span class="sxs-lookup"><span data-stu-id="22889-168">**Child** Accessor</span></span>|<span data-ttu-id="22889-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="22889-169">GetChildTableNameRows</span></span>|<span data-ttu-id="22889-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="22889-170">typedChildren</span></span>|  
|<span data-ttu-id="22889-171">**父系**存取</span><span class="sxs-lookup"><span data-stu-id="22889-171">**Parent** Accessor</span></span>|<span data-ttu-id="22889-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="22889-172">TableNameRow</span></span>|<span data-ttu-id="22889-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="22889-173">typedParent</span></span>|  
|<span data-ttu-id="22889-174">**資料集**事件</span><span class="sxs-lookup"><span data-stu-id="22889-174">**DataSet** Events</span></span>|<span data-ttu-id="22889-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="22889-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="22889-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="22889-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="22889-177">typedName</span><span class="sxs-lookup"><span data-stu-id="22889-177">typedName</span></span>|  
  
 <span data-ttu-id="22889-178">若要使用具類型的**資料集**批註, 您必須在 XML 架構定義語言 (XSD) 架構中包含下列**xmlns**參考。</span><span class="sxs-lookup"><span data-stu-id="22889-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="22889-179">若要從資料庫資料表建立 xsd, 請<xref:System.Data.DataSet.WriteXmlSchema%2A>參閱或使用[Visual Studio 中的資料集](/visualstudio/data-tools/dataset-tools-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="22889-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="22889-180">以下是批註式架構範例, 它會公開**Northwind**資料庫的**Customers**資料表與內含之**Orders**資料表的關聯性。</span><span class="sxs-lookup"><span data-stu-id="22889-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="22889-181">下列程式碼範例使用從範例架構建立的強型別**資料集**。</span><span class="sxs-lookup"><span data-stu-id="22889-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="22889-182">它會使用<xref:System.Data.SqlClient.SqlDataAdapter>其中一個填入**Customers**資料表, 另<xref:System.Data.SqlClient.SqlDataAdapter>一個用來填入**Orders**資料表。</span><span class="sxs-lookup"><span data-stu-id="22889-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="22889-183">強型別**資料集**會定義**datarelation**。</span><span class="sxs-lookup"><span data-stu-id="22889-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22889-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22889-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="22889-185">具類型的 DataSet</span><span class="sxs-lookup"><span data-stu-id="22889-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="22889-186">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="22889-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="22889-187">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="22889-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
