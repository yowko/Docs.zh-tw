---
title: 使用 XmlSchemaCollection 進行 XML 結構描述 (XSD) 驗證
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0fb14f919d0737b9d9c25bcd62a3cfb7228ff432
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916082"
---
# <a name="xml-schema-xsd-validation-with-xmlschemacollection"></a><span data-ttu-id="550a1-102">使用 XmlSchemaCollection 進行 XML 結構描述 (XSD) 驗證</span><span class="sxs-lookup"><span data-stu-id="550a1-102">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>
<span data-ttu-id="550a1-103">您可以使用 <xref:System.Xml.Schema.XmlSchemaCollection>，依據 XML 結構描述定義語言 (XSD) 結構描述來驗證 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="550a1-103">You can use the <xref:System.Xml.Schema.XmlSchemaCollection> to validate an XML document against XML Schema definition language (XSD) schemas.</span></span> <span data-ttu-id="550a1-104"><xref:System.Xml.Schema.XmlSchemaCollection> 可以提升效能，其方法是將結構描述儲存於集合中，而不用在每次執行驗證時，都要將其載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="550a1-104">The <xref:System.Xml.Schema.XmlSchemaCollection> improves performance by storing schemas in the collection so they are not loaded into memory each time validation occurs.</span></span> <span data-ttu-id="550a1-105">如果結構描述存在於結構描述集合中，則 `schemaLocation` 屬性可用於查詢集合中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="550a1-105">If the schema exists in the schema collection, the `schemaLocation` attribute is used to look up the schema in the collection.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="550a1-106"><xref:System.Xml.Schema.XmlSchemaCollection> 類別目前已過時，並已由 <xref:System.Xml.Schema.XmlSchemaSet> 類別取代。</span><span class="sxs-lookup"><span data-stu-id="550a1-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="550a1-107">如需有關 <xref:System.Xml.Schema.XmlSchemaSet> 類別的詳細資訊，請參閱[用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="550a1-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
 <span data-ttu-id="550a1-108">下列範例顯示資料檔案的根項目。</span><span class="sxs-lookup"><span data-stu-id="550a1-108">The following example shows the root element of a data file.</span></span>  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 <span data-ttu-id="550a1-109">針對此範例，`targetNamespace` 屬性的值為 `urn:bookstore-schema`，其與將結構描述加入至 <xref:System.Xml.Schema.XmlSchemaCollection> 時所使用的命名空間相同。</span><span class="sxs-lookup"><span data-stu-id="550a1-109">For this example, the value of the `targetNamespace` attribute is `urn:bookstore-schema`, which is the same namespace that is used when adding the schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span>  
  
 <span data-ttu-id="550a1-110">下列程式碼範例會將 XML 結構描述加入至 <xref:System.Xml.Schema.XmlSchemaCollection>。</span><span class="sxs-lookup"><span data-stu-id="550a1-110">The following code example adds an XML Schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span>  
  
```vb  
Dim xsc As New XmlSchemaCollection()  
' XML Schema.  
xsc.Add("urn:bookstore-schema", schema)   
reader = New XmlTextReader(filename)  
vreader = New XmlValidatingReader(reader)  
vreader.Schemas.Add(xsc)  
```  
  
```csharp  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
// XML Schema.  
xsc.Add("urn:bookstore-schema", schema);  
reader = new XmlTextReader (filename);  
vreader = new XmlValidatingReader (reader);  
vreader.Schemas.Add(xsc);  
```  
  
 <span data-ttu-id="550a1-111">當在 `targetNamespace` 的 `namespaceURI` 方法中加入 <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> 屬性時，一般會使用 <xref:System.Xml.Schema.XmlSchemaCollection> 屬性。</span><span class="sxs-lookup"><span data-stu-id="550a1-111">The `targetNamespace` attribute is generally used when you add the `namespaceURI` property in the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method for the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span> <span data-ttu-id="550a1-112">您可以指定 Null 參考，再將結構描述加入至 <xref:System.Xml.Schema.XmlSchemaCollection>。</span><span class="sxs-lookup"><span data-stu-id="550a1-112">You can specify a null reference before adding the schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span> <span data-ttu-id="550a1-113">針對不具命名空間的結構描述，應使用空字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="550a1-113">An empty string ("") should be used for schemas without a namespace.</span></span> <span data-ttu-id="550a1-114"><xref:System.Xml.Schema.XmlSchemaCollection> 僅可有一個不具命名空間的結構描述。</span><span class="sxs-lookup"><span data-stu-id="550a1-114">The <xref:System.Xml.Schema.XmlSchemaCollection> can have only one schema without a namespace.</span></span>  
  
 <span data-ttu-id="550a1-115">下列程式碼範例會將 XML 結構描述 ( HeadCount.xsd) 加入至 <xref:System.Xml.Schema.XmlSchemaCollection>，並驗證 HeadCount.xml。</span><span class="sxs-lookup"><span data-stu-id="550a1-115">The following code example adds an XML Schema, HeadCount.xsd, to the <xref:System.Xml.Schema.XmlSchemaCollection> and validates HeadCount.xml.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Schema  
  
Namespace ValidationSample  
  
   Class Sample  
  
      Public Shared Sub Main()  
         Dim tr As New XmlTextReader("HeadCount.xml")  
         Dim vr As New XmlValidatingReader(tr)  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd")  
         vr.ValidationType = ValidationType.Schema  
         AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler  
  
         While vr.Read()  
         End While  
         Console.WriteLine("Validation finished")  
      End Sub  
      ' Main  
  
      Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)  
         Console.WriteLine("***Validation error")  
         Console.WriteLine("Severity:{0}", args.Severity)  
         Console.WriteLine("Message:{0}", args.Message)  
      End Sub  
      ' ValidationHandler  
   End Class  
   ' Sample  
End Namespace  
' ValidationSample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Schema;  
  
namespace ValidationSample  
{  
   class Sample  
   {  
      public static void Main()  
      {  
         XmlTextReader tr = new XmlTextReader("HeadCount.xml");  
         XmlValidatingReader vr = new XmlValidatingReader(tr);  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd");  
         vr.ValidationType = ValidationType.Schema;  
         vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);  
  
         while(vr.Read());  
         Console.WriteLine("Validation finished");  
      }  
  
      public static void ValidationHandler(object sender, ValidationEventArgs args)  
      {  
         Console.WriteLine("***Validation error");  
         Console.WriteLine("\tSeverity:{0}", args.Severity);  
         Console.WriteLine("\tMessage  :{0}", args.Message);  
      }  
   }  
}  
```  
  
 <span data-ttu-id="550a1-116">以下列出了要進行驗證的輸入檔 (HeadCount.xml) 內容。</span><span class="sxs-lookup"><span data-stu-id="550a1-116">The following outlines the contents of the input file, HeadCount.xml, to be validated.</span></span>  
  
```xml  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 <span data-ttu-id="550a1-117">以下列出了要進行驗證 XML 結構描述檔案 (HeadCount.xsd) 的內容。</span><span class="sxs-lookup"><span data-stu-id="550a1-117">The following outlines the contents of the XML Schema file, HeadCount.xsd, to be validated against.</span></span>  
  
```xml  
<xs:schema xmlns="xsdHeadCount" targetNamespace="xsdHeadCount" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name='HeadCount' type="HEADCOUNT"/>  
   <xs:complexType name="HEADCOUNT">  
      <xs:sequence>  
         <xs:element name='Name' type='xs:string' maxOccurs='unbounded'/>  
      </xs:sequence>  
      <xs:attribute name='division' type='xs:int' use='optional' default='8'/>  
   </xs:complexType>  
</xs:schema>  
```  
  
 <span data-ttu-id="550a1-118">下列程式碼範例會建立 <xref:System.Xml.XmlValidatingReader>，它會使用 <xref:System.Xml.XmlTextReader>。</span><span class="sxs-lookup"><span data-stu-id="550a1-118">The following code example creates an <xref:System.Xml.XmlValidatingReader> that takes an <xref:System.Xml.XmlTextReader>.</span></span> <span data-ttu-id="550a1-119">輸入檔 sample4.xml 會針對 XML 結構描述 sample4.xsd 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="550a1-119">The input file, sample4.xml, is validated against the XML Schema, sample4.xsd.</span></span>  
  
```vb  
Dim tr As New XmlTextReader("sample4.xml")  
Dim vr As New XmlValidatingReader(tr)  
vr.ValidationType = ValidationType.Schema  
vr.Schemas.Add("datatypesTest", "sample4.xsd")  
AddHandler vr.ValidationEventHandler, AddressOf ValidationCallBack  
While vr.Read()  
   Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name)  
End While  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("sample4.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
vr.ValidationType = ValidationType.Schema;  
        vr.Schemas.Add("datatypesTest", "sample4.xsd");  
vr.ValidationEventHandler += new ValidationEventHandler(ValidationCallBack);  
while(vr.Read()) {  
    Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name);  
    }  
```  
  
 <span data-ttu-id="550a1-120">以下列出了要驗證之輸入檔 (sample4.xml) 的內容。</span><span class="sxs-lookup"><span data-stu-id="550a1-120">The following outlines the contents of the input file, sample4.xml, to be validated.</span></span>  
  
```xml  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 <span data-ttu-id="550a1-121">以下列出了要據以驗證之 XML 結構描述檔案 (sample4.xsd) 的內容。</span><span class="sxs-lookup"><span data-stu-id="550a1-121">The following outlines the contents of the XML Schema file, sample4.xsd, to be validated against.</span></span>  
  
```xml  
<xs:schema   
    xmlns:xs="http://www.w3.org/2001/XMLSchema"   
    xmlns:tns="datatypesTest"   
    targetNamespace="datatypesTest"  
    elementFormDefault="qualified">  
  
<xs:element name = "datatypes">  
  <xs:complexType>  
    <xs:all>  
        <xs:element name="number">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="number_1" type="xs:decimal" maxOccurs="unbounded"/>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
    </xs:all>  
  </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="550a1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="550a1-122">See also</span></span>

- <xref:System.Xml.XmlParserContext>
- <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=nameWithType>
- <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=nameWithType>
- [<span data-ttu-id="550a1-123">XmlSchemaCollection 結構描述編譯</span><span class="sxs-lookup"><span data-stu-id="550a1-123">XmlSchemaCollection Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemacollection-schema-compilation.md)
