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
# <a name="annotating-typed-datasets"></a><span data-ttu-id="20d46-102">註釋具類型資料集</span><span class="sxs-lookup"><span data-stu-id="20d46-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="20d46-103">註釋可讓您在無需修改基礎結構描述的情況下，修改具型別之 <xref:System.Data.DataSet> 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="20d46-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="20d46-104">修改基礎架構中元素的名稱將導致鍵入的**DataSet**參考資料源中不存在的物件，並丟失對資料來源中確實存在物件的引用。</span><span class="sxs-lookup"><span data-stu-id="20d46-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="20d46-105">使用注釋，您可以使用更有意義的名稱自訂鍵入的**DataSet**中的物件名稱，使代碼更具可讀性，並使鍵入的**DataSet**更易於用戶端使用，同時保留基礎架構不變。</span><span class="sxs-lookup"><span data-stu-id="20d46-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="20d46-106">例如 **，Northwind**資料庫**的客戶**表的以下架構元素將導致**客戶行**的<xref:System.Data.DataRowCollection>**DataRow**物件名稱和命名的**客戶**。</span><span class="sxs-lookup"><span data-stu-id="20d46-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="20d46-107">**客戶** **DataRow 集合**名稱在用戶端代碼中有意義，但**客戶行** **DataRow**名稱具有誤導性，因為它是單個物件。</span><span class="sxs-lookup"><span data-stu-id="20d46-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="20d46-108">此外，在常見方案中，將引用該物件而不帶**行**識別碼，而將簡單地稱為**客戶**物件。</span><span class="sxs-lookup"><span data-stu-id="20d46-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="20d46-109">解決方案是對架構進行批號，並標識**DataRow**和**DataRowCollection**物件的新名稱。</span><span class="sxs-lookup"><span data-stu-id="20d46-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="20d46-110">下列為上述結構描述的標註版本。</span><span class="sxs-lookup"><span data-stu-id="20d46-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="20d46-111">指定**客戶的\*\*\*\*類型名稱**值將導致**客戶**的**DataRow**物件名稱。</span><span class="sxs-lookup"><span data-stu-id="20d46-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="20d46-112">指定客戶的**鍵入的複數**值**Customers**將保留**客戶\*\*\*\*的資料羅集合**名稱。</span><span class="sxs-lookup"><span data-stu-id="20d46-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="20d46-113">下列表格顯示可供使用的註釋。</span><span class="sxs-lookup"><span data-stu-id="20d46-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="20d46-114">Annotation</span><span class="sxs-lookup"><span data-stu-id="20d46-114">Annotation</span></span>|<span data-ttu-id="20d46-115">描述</span><span class="sxs-lookup"><span data-stu-id="20d46-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="20d46-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="20d46-116">**typedName**</span></span>|<span data-ttu-id="20d46-117">物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="20d46-117">Name of the object.</span></span>|  
|<span data-ttu-id="20d46-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="20d46-118">**typedPlural**</span></span>|<span data-ttu-id="20d46-119">物件集合名稱。</span><span class="sxs-lookup"><span data-stu-id="20d46-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="20d46-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="20d46-120">**typedParent**</span></span>|<span data-ttu-id="20d46-121">在父關聯性中所參考的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="20d46-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="20d46-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="20d46-122">**typedChildren**</span></span>|<span data-ttu-id="20d46-123">從子關聯性傳回物件的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="20d46-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="20d46-124">**空值**</span><span class="sxs-lookup"><span data-stu-id="20d46-124">**nullValue**</span></span>|<span data-ttu-id="20d46-125">如果基礎值為**DBNull**，則值。</span><span class="sxs-lookup"><span data-stu-id="20d46-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="20d46-126">有關**nullValue**注釋，請參閱下表。</span><span class="sxs-lookup"><span data-stu-id="20d46-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="20d46-127">預設值為 **_throw**。</span><span class="sxs-lookup"><span data-stu-id="20d46-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="20d46-128">下表顯示了可以為**nullValue**注釋指定的值。</span><span class="sxs-lookup"><span data-stu-id="20d46-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="20d46-129">nullValue 值</span><span class="sxs-lookup"><span data-stu-id="20d46-129">nullValue Value</span></span>|<span data-ttu-id="20d46-130">描述</span><span class="sxs-lookup"><span data-stu-id="20d46-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="20d46-131">*重置值*</span><span class="sxs-lookup"><span data-stu-id="20d46-131">*Replacement Value*</span></span>|<span data-ttu-id="20d46-132">指定要傳回的值。</span><span class="sxs-lookup"><span data-stu-id="20d46-132">Specify a value to be returned.</span></span> <span data-ttu-id="20d46-133">傳回值必須與項目的型別相符。</span><span class="sxs-lookup"><span data-stu-id="20d46-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="20d46-134">例如，使用 `nullValue="0"` 可為 null 整數欄位傳回 0。</span><span class="sxs-lookup"><span data-stu-id="20d46-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="20d46-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="20d46-135">**_throw**</span></span>|<span data-ttu-id="20d46-136">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="20d46-136">Throw an exception.</span></span> <span data-ttu-id="20d46-137">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="20d46-137">This is the default.</span></span>|  
|<span data-ttu-id="20d46-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="20d46-138">**_null**</span></span>|<span data-ttu-id="20d46-139">如果遇到基本型別，則會傳回 Null 參考或發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="20d46-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="20d46-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="20d46-140">**_empty**</span></span>|<span data-ttu-id="20d46-141">對於字串，返回**String.empty**，否則返回從空建構函式創建的物件。</span><span class="sxs-lookup"><span data-stu-id="20d46-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="20d46-142">如果遇到基本型別，則會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="20d46-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="20d46-143">下表顯示了類型**化 DataSet**中物件的預設值和可用的批註。</span><span class="sxs-lookup"><span data-stu-id="20d46-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="20d46-144">物件/方法/事件</span><span class="sxs-lookup"><span data-stu-id="20d46-144">Object/Method/Event</span></span>|<span data-ttu-id="20d46-145">預設</span><span class="sxs-lookup"><span data-stu-id="20d46-145">Default</span></span>|<span data-ttu-id="20d46-146">Annotation</span><span class="sxs-lookup"><span data-stu-id="20d46-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="20d46-147">**資料表**</span><span class="sxs-lookup"><span data-stu-id="20d46-147">**DataTable**</span></span>|<span data-ttu-id="20d46-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="20d46-148">TableNameDataTable</span></span>|<span data-ttu-id="20d46-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="20d46-149">typedPlural</span></span>|  
|<span data-ttu-id="20d46-150">**資料表**方法</span><span class="sxs-lookup"><span data-stu-id="20d46-150">**DataTable** Methods</span></span>|<span data-ttu-id="20d46-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="20d46-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="20d46-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="20d46-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="20d46-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="20d46-153">DeleteTableNameRow</span></span>|<span data-ttu-id="20d46-154">typedName</span><span class="sxs-lookup"><span data-stu-id="20d46-154">typedName</span></span>|  
|<span data-ttu-id="20d46-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="20d46-155">**DataRowCollection**</span></span>|<span data-ttu-id="20d46-156">TableName</span><span class="sxs-lookup"><span data-stu-id="20d46-156">TableName</span></span>|<span data-ttu-id="20d46-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="20d46-157">typedPlural</span></span>|  
|<span data-ttu-id="20d46-158">**資料行**</span><span class="sxs-lookup"><span data-stu-id="20d46-158">**DataRow**</span></span>|<span data-ttu-id="20d46-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="20d46-159">TableNameRow</span></span>|<span data-ttu-id="20d46-160">typedName</span><span class="sxs-lookup"><span data-stu-id="20d46-160">typedName</span></span>|  
|<span data-ttu-id="20d46-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="20d46-161">**DataColumn**</span></span>|<span data-ttu-id="20d46-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="20d46-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="20d46-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="20d46-163">DataRow.ColumnName</span></span>|<span data-ttu-id="20d46-164">typedName</span><span class="sxs-lookup"><span data-stu-id="20d46-164">typedName</span></span>|  
|<span data-ttu-id="20d46-165">**屬性**</span><span class="sxs-lookup"><span data-stu-id="20d46-165">**Property**</span></span>|<span data-ttu-id="20d46-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="20d46-166">PropertyName</span></span>|<span data-ttu-id="20d46-167">typedName</span><span class="sxs-lookup"><span data-stu-id="20d46-167">typedName</span></span>|  
|<span data-ttu-id="20d46-168">**兒童**訪問</span><span class="sxs-lookup"><span data-stu-id="20d46-168">**Child** Accessor</span></span>|<span data-ttu-id="20d46-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="20d46-169">GetChildTableNameRows</span></span>|<span data-ttu-id="20d46-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="20d46-170">typedChildren</span></span>|  
|<span data-ttu-id="20d46-171">**父級**訪問</span><span class="sxs-lookup"><span data-stu-id="20d46-171">**Parent** Accessor</span></span>|<span data-ttu-id="20d46-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="20d46-172">TableNameRow</span></span>|<span data-ttu-id="20d46-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="20d46-173">typedParent</span></span>|  
|<span data-ttu-id="20d46-174">**資料集**事件</span><span class="sxs-lookup"><span data-stu-id="20d46-174">**DataSet** Events</span></span>|<span data-ttu-id="20d46-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="20d46-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="20d46-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="20d46-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="20d46-177">typedName</span><span class="sxs-lookup"><span data-stu-id="20d46-177">typedName</span></span>|  
  
 <span data-ttu-id="20d46-178">要使用鍵入的**DataSet**注釋，必須在 XML 架構定義語言 （XSD） 架構中包括以下**xmlns**引用。</span><span class="sxs-lookup"><span data-stu-id="20d46-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="20d46-179">要從資料庫表創建 xsd，請參閱<xref:System.Data.DataSet.WriteXmlSchema%2A>或使用[視覺化工作室中的資料集](/visualstudio/data-tools/dataset-tools-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="20d46-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="20d46-180">下面是一個帶批號的示例架構，該架構公開了**Northwind**資料庫**的客戶**表，該表與包含**的訂單**表相關。</span><span class="sxs-lookup"><span data-stu-id="20d46-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="20d46-181">以下代碼示例使用從示例架構創建的強型別**資料集**。</span><span class="sxs-lookup"><span data-stu-id="20d46-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="20d46-182">它使用一<xref:System.Data.SqlClient.SqlDataAdapter>個填充**客戶**表，另一<xref:System.Data.SqlClient.SqlDataAdapter>個用於填充**訂單**表。</span><span class="sxs-lookup"><span data-stu-id="20d46-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="20d46-183">強型別**資料集**定義**資料關係**。</span><span class="sxs-lookup"><span data-stu-id="20d46-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20d46-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20d46-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="20d46-185">具類型資料集</span><span class="sxs-lookup"><span data-stu-id="20d46-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="20d46-186">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="20d46-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="20d46-187">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="20d46-187">[ADO.NET Overview](../ado-net-overview.md)</span></span>
