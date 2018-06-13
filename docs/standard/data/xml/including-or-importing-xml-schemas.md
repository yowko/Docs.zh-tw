---
title: 併入或匯入 XML 結構描述
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2f83128f47a687e75a7db9bb36c487fa1f5bb6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573059"
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="32fae-102">併入或匯入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32fae-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="32fae-103">XML 結構描述可包含 `<xs:import />`, `<xs:include />` 及 `<xs:redefine />` 項目。</span><span class="sxs-lookup"><span data-stu-id="32fae-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="32fae-104">這些結構描述項目會參考其他 XML 結構描述，其可用於補充併入或匯入它們之結構描述的結構。</span><span class="sxs-lookup"><span data-stu-id="32fae-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="32fae-105"><xref:System.Xml.Schema.XmlSchemaImport>、<xref:System.Xml.Schema.XmlSchemaInclude> 及 <xref:System.Xml.Schema.XmlSchemaRedefine> 類別會對應至結構描述物件模型 (SOM) API 中的這些項目。</span><span class="sxs-lookup"><span data-stu-id="32fae-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="32fae-106">併入或匯入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32fae-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="32fae-107">下列程式碼範例會為[建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)主題中建立的客戶結構描述補充位址結構描述。</span><span class="sxs-lookup"><span data-stu-id="32fae-107">The following code example supplements the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="32fae-108">為客戶結構描述補充位址結構描述，可讓位址型別在客戶結構描述中使用。</span><span class="sxs-lookup"><span data-stu-id="32fae-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="32fae-109">您可使用 `<xs:include />` 或 `<xs:import />` 項目加入位址結構描述，以按原樣使用位址結構描述的元件，或使用 `<xs:redefine />` 項目，修改其中任何元件以滿足客戶結構描述需要。</span><span class="sxs-lookup"><span data-stu-id="32fae-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="32fae-110">因為位址結構描述與客戶結構描述的 `targetNamespace` 不同，所以會使用 `<xs:import />` 項目及匯入語意。</span><span class="sxs-lookup"><span data-stu-id="32fae-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="32fae-111">程式碼範例使用下列步驟併入位址結構描述。</span><span class="sxs-lookup"><span data-stu-id="32fae-111">The code example includes the address schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="32fae-112">將客戶結構描述及位址結構描述加入至新的 <xref:System.Xml.Schema.XmlSchemaSet> 物件，然後對它們進行編譯。</span><span class="sxs-lookup"><span data-stu-id="32fae-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="32fae-113">讀取或編譯結構描述時遇到的任何結構描述驗證警告及錯誤，都會由 <xref:System.Xml.Schema.ValidationEventHandler> 委派處理。</span><span class="sxs-lookup"><span data-stu-id="32fae-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="32fae-114">透過重複處理 <xref:System.Xml.Schema.XmlSchema> 屬性，從 <xref:System.Xml.Schema.XmlSchemaSet> 中為客戶及位址結構描述擷取已編譯的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 物件。</span><span class="sxs-lookup"><span data-stu-id="32fae-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="32fae-115">因為已編譯結構描述，因此可存取後結構描述編譯資訊集 (PSCI) 屬性。</span><span class="sxs-lookup"><span data-stu-id="32fae-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="32fae-116">建立 <xref:System.Xml.Schema.XmlSchemaImport> 物件、將 import 的 <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> 屬性設為位址結構描述的命名空間、將 import 的 <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> 屬性設為位址結構描述的 <xref:System.Xml.Schema.XmlSchema> 物件，並將 import 加入客戶結構描述的 <xref:System.Xml.Schema.XmlSchema.Includes%2A> 屬性中。</span><span class="sxs-lookup"><span data-stu-id="32fae-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4.  <span data-ttu-id="32fae-117">使用 <xref:System.Xml.Schema.XmlSchema> 類別的 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 及 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法，重新處理並編譯客戶結構描述之已修改的 <xref:System.Xml.Schema.XmlSchemaSet> 物件，並將其寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="32fae-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5.  <span data-ttu-id="32fae-118">最後，使用客戶結構描述的 <xref:System.Xml.Schema.XmlSchema.Includes%2A> 屬性，將匯入至客戶結構描述的所有結構描述遞迴寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="32fae-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="32fae-119"><xref:System.Xml.Schema.XmlSchema.Includes%2A> 屬性對所有加入至結構描述的 include、import 或 redefine 提供存取權。</span><span class="sxs-lookup"><span data-stu-id="32fae-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="32fae-120">下列是完整程式碼範例及寫入主控台的客戶與位址結構描述。</span><span class="sxs-lookup"><span data-stu-id="32fae-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 <span data-ttu-id="32fae-121">如需 `<xs:import />`、`<xs:include />` 及 `<xs:redefine />` 項目與 <xref:System.Xml.Schema.XmlSchemaImport>、<xref:System.Xml.Schema.XmlSchemaInclude> 和 <xref:System.Xml.Schema.XmlSchemaRedefine> 類別的詳細資訊，請參閱 [W3C XML 結構描述](https://www.w3.org/XML/Schema) (英文) 及 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="32fae-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fae-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="32fae-122">See Also</span></span>  
 [<span data-ttu-id="32fae-123">XML 結構描述物件模型概觀</span><span class="sxs-lookup"><span data-stu-id="32fae-123">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="32fae-124">讀取和寫入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32fae-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="32fae-125">建置 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32fae-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="32fae-126">周遊 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32fae-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="32fae-127">編輯 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32fae-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="32fae-128">用於結構描述編譯的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="32fae-128">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
