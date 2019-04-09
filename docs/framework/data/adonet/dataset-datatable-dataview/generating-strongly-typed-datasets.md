---
title: 產生強類型資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 25883b7be10c68e527e4e04182b7162574b994d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149626"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="cb1cf-102">產生強類型資料集</span><span class="sxs-lookup"><span data-stu-id="cb1cf-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="cb1cf-103">如果 XML 結構描述是採用 XML 結構描述定義語言 (XSD) 標準進行編譯，則可以使用 <xref:System.Data.DataSet> 所提供的 XSD.exe 工具產生強型別 [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="cb1cf-104">(若要從資料庫資料表建立 xsd，請參閱<xref:System.Data.DataSet.WriteXmlSchema%2A>或是[使用 Visual Studio 中的資料集](/visualstudio/data-tools/dataset-tools-in-visual-studio))。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="cb1cf-105">下列程式碼顯示產生的語法**資料集**使用此工具。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="cb1cf-106">在這個語法中，`/d`指示詞告訴工具，以產生**資料集**，和`/l:`告訴工具 （例如，C# 或 Visual Basic.NET） 使用哪一種語言。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="cb1cf-107">選擇性`/eld`指示詞會指定您可以使用[!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]來查詢產生**資料集。**</span><span class="sxs-lookup"><span data-stu-id="cb1cf-107">The optional `/eld` directive specifies that you can use [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] to query against the generated **DataSet.**</span></span> <span data-ttu-id="cb1cf-108">這個選項會在也有指定 `/d` 選項時使用。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="cb1cf-109">如需詳細資訊，請參閱 <<c0> [ 查詢具型別 DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-109">For more information, see [Querying Typed DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="cb1cf-110">選擇性`/n:`指示詞會告訴工具也會產生的命名空間**資料集**稱為**XSDSchema.Namespace**。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="cb1cf-111">命令的輸出為 XSDSchemaFileName.cs，可以在 ADO.NET 應用程式中編譯和使用。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="cb1cf-112">產生的程式碼可以編譯為程式庫或模組。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="cb1cf-113">下列程式碼顯示使用 C# 編譯器 (csc.exe)，將產生的程式碼編譯成程式庫的語法。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="cb1cf-114">`/t:` 指示詞告訴工具要編譯到程式庫，而 `/r:` 指示詞則指定編譯所需要的相依程式庫。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="cb1cf-115">該命令的輸出為 XSDSchemaFileName.dll，而在使用 `/r:` 指示詞編譯 ADO.NET 應用程式時，可以將該檔案傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="cb1cf-116">下列程式碼顯示存取 ADO.NET 應用程式內傳遞給 XSD.exe 命名空間的語法。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="cb1cf-117">下列程式碼範例會使用具型別**資料集**名為**CustomerDataSet**載入一份客戶來自**Northwind**資料庫。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="cb1cf-118">資料載入使用後**填滿**方法，此範例每個客戶中執行迴圈**客戶**資料表使用具型別**Datarow** (**DataRow**) 物件。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="cb1cf-119">這可直接存取**CustomerID**資料行，而不是透過**DataColumnCollection**。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 <span data-ttu-id="cb1cf-120">下列為 XML 結構描述範例。</span><span class="sxs-lookup"><span data-stu-id="cb1cf-120">Following is the XML Schema used for the example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb1cf-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb1cf-121">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="cb1cf-122">具類型資料集</span><span class="sxs-lookup"><span data-stu-id="cb1cf-122">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [<span data-ttu-id="cb1cf-123">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="cb1cf-123">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="cb1cf-124">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="cb1cf-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
