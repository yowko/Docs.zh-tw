---
title: "使用 XmlSchemaCollection 進行 XML 結構描述 (XSD) 驗證 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 使用 XmlSchemaCollection 進行 XML 結構描述 (XSD) 驗證
您可以使用 <xref:System.Xml.Schema.XmlSchemaCollection>，依據 XML 結構描述定義語言 \(XSD\) 結構描述來驗證 XML 文件。  <xref:System.Xml.Schema.XmlSchemaCollection> 可以提升效能，其方法是將結構描述儲存於集合中，而不用在每次執行驗證時，都要將其載入記憶體。  如果結構描述存在於結構描述集合中，則 `schemaLocation` 屬性可用於查詢集合中的結構描述。  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> 類別目前已過時，並已由 <xref:System.Xml.Schema.XmlSchemaSet> 類別取代。  如需 <xref:System.Xml.Schema.XmlSchemaSet> 類別的詳細資訊，請參閱 [用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)。  
  
 下列範例顯示資料檔案的根項目。  
  
```  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 針對此範例，`targetNamespace` 屬性的值為 `urn:bookstore-schema`，其與將結構描述加入至 <xref:System.Xml.Schema.XmlSchemaCollection> 時所使用的命名空間相同。  
  
 下列程式碼範例會將 XML 結構描述加入至 <xref:System.Xml.Schema.XmlSchemaCollection>。  
  
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
  
 當在 <xref:System.Xml.Schema.XmlSchemaCollection> 的 <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> 方法中加入 `namespaceURI` 屬性時，一般會使用 `targetNamespace` 屬性。  您可以指定 Null 參考，再將結構描述加入至 <xref:System.Xml.Schema.XmlSchemaCollection>。  針對不具命名空間的結構描述，應使用空字串 \(""\)。  <xref:System.Xml.Schema.XmlSchemaCollection> 僅可有一個不具命名空間的結構描述。  
  
 下列程式碼範例會將 XML 結構描述 \( HeadCount.xsd\) 加入至 <xref:System.Xml.Schema.XmlSchemaCollection>，並驗證 HeadCount.xml。  
  
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
  
 以下列出了要進行驗證的輸入檔 \(HeadCount.xml\) 內容。  
  
```  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 以下列出了要進行驗證 XML 結構描述檔案 \(HeadCount.xsd\) 的內容。  
  
```  
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
  
 下列程式碼範例會建立 <xref:System.Xml.XmlValidatingReader>，它會使用 <xref:System.Xml.XmlTextReader>。  輸入檔 sample4.xml 會針對 XML 結構描述 sample4.xsd 進行驗證。  
  
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
  
 以下列出了要驗證之輸入檔 \(sample4.xml\) 的內容。  
  
```  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 以下列出了要據以驗證之 XML 結構描述檔案 \(sample4.xsd\) 的內容。  
  
```  
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
  
## 請參閱  
 <xref:System.Xml.XmlParserContext>   
 <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=fullName>   
 <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=fullName>   
 [XmlSchemaCollection 結構描述編譯](../../../../docs/standard/data/xml/xmlschemacollection-schema-compilation.md)