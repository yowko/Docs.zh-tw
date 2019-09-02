---
title: 產生強類型資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 9bff69e28aa17da87da7e94d4e110c0375f043ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203700"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="6841f-102">產生強類型資料集</span><span class="sxs-lookup"><span data-stu-id="6841f-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="6841f-103">假設 xml 架構符合 xml 架構定義語言 (XSD) 標準, 您可以<xref:System.Data.DataSet>使用 Windows 軟體發展工具組 (SDK) 所提供的 xsd.exe 工具來產生強型別。</span><span class="sxs-lookup"><span data-stu-id="6841f-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the Windows Software Development Kit (SDK).</span></span>  
  
 <span data-ttu-id="6841f-104">(若要從資料庫資料表建立 xsd, 請<xref:System.Data.DataSet.WriteXmlSchema%2A>參閱或使用[Visual Studio 中的資料集](/visualstudio/data-tools/dataset-tools-in-visual-studio))。</span><span class="sxs-lookup"><span data-stu-id="6841f-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="6841f-105">下列程式碼顯示使用此工具產生**資料集**的語法。</span><span class="sxs-lookup"><span data-stu-id="6841f-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="6841f-106">在此語法中, `/d`指示詞會告訴工具產生**資料集**, 而`/l:`會告訴工具所要使用的語言 (例如, C#或 Visual Basic .net)。</span><span class="sxs-lookup"><span data-stu-id="6841f-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="6841f-107">選擇性`/eld`指示詞會指定您可以使用 LINQ to DataSet 來查詢所產生的**資料集。**</span><span class="sxs-lookup"><span data-stu-id="6841f-107">The optional `/eld` directive specifies that you can use LINQ to DataSet to query against the generated **DataSet.**</span></span> <span data-ttu-id="6841f-108">這個選項會在也有指定 `/d` 選項時使用。</span><span class="sxs-lookup"><span data-stu-id="6841f-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="6841f-109">如需詳細資訊, 請參閱[查詢具類型的資料集](../querying-typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="6841f-109">For more information, see [Querying Typed DataSets](../querying-typed-datasets.md).</span></span> <span data-ttu-id="6841f-110">選擇性`/n:`指示詞會告訴工具, 也會產生稱為**XSDSchema**之**資料集**的命名空間。</span><span class="sxs-lookup"><span data-stu-id="6841f-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="6841f-111">命令的輸出為 XSDSchemaFileName.cs，可以在 ADO.NET 應用程式中編譯和使用。</span><span class="sxs-lookup"><span data-stu-id="6841f-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="6841f-112">產生的程式碼可以編譯為程式庫或模組。</span><span class="sxs-lookup"><span data-stu-id="6841f-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="6841f-113">下列程式碼顯示使用 C# 編譯器 (csc.exe)，將產生的程式碼編譯成程式庫的語法。</span><span class="sxs-lookup"><span data-stu-id="6841f-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="6841f-114">`/t:` 指示詞告訴工具要編譯到程式庫，而 `/r:` 指示詞則指定編譯所需要的相依程式庫。</span><span class="sxs-lookup"><span data-stu-id="6841f-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="6841f-115">該命令的輸出為 XSDSchemaFileName.dll，而在使用 `/r:` 指示詞編譯 ADO.NET 應用程式時，可以將該檔案傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="6841f-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="6841f-116">下列程式碼顯示存取 ADO.NET 應用程式內傳遞給 XSD.exe 命名空間的語法。</span><span class="sxs-lookup"><span data-stu-id="6841f-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="6841f-117">下列程式碼範例會使用名為**CustomerDataSet**的具類型**資料集**, 從**Northwind**資料庫載入客戶清單。</span><span class="sxs-lookup"><span data-stu-id="6841f-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="6841f-118">一旦使用**Fill**方法載入資料, 此範例就會使用具類型的**CustomersRow** (**DataRow**) 物件, 在**Customers**資料表中的每個客戶上執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="6841f-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="6841f-119">這可讓您直接存取**CustomerID**資料行, 而不是透過**DataColumnCollection**。</span><span class="sxs-lookup"><span data-stu-id="6841f-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="6841f-120">下列為 XML 結構描述範例。</span><span class="sxs-lookup"><span data-stu-id="6841f-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6841f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6841f-121">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="6841f-122">具類型的 DataSet</span><span class="sxs-lookup"><span data-stu-id="6841f-122">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="6841f-123">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="6841f-123">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="6841f-124">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6841f-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
