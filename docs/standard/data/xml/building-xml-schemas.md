---
title: "建置 XML 結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e49c2130702fc7df223f2eab0ea0500b1c27b660
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="building-xml-schemas"></a><span data-ttu-id="367b8-102">建置 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="367b8-102">Building XML Schemas</span></span>
<span data-ttu-id="367b8-103"><xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的類別會對應至全球資訊網協會 (W3C) XML 結構描述建議事項中定義的結構，並可用於建置記憶體中的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="367b8-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="367b8-104">建置 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="367b8-104">Building an XML Schema</span></span>  
 <span data-ttu-id="367b8-105">在下面的程式碼範例中，會使用 SOM API 建置記憶體中的客戶 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="367b8-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="367b8-106">建立項目及屬性</span><span class="sxs-lookup"><span data-stu-id="367b8-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="367b8-107">程式碼範例會從下往上建置客戶結構描述，首先建立項目子系、屬性及其對應的型別，然後再建立最上層項目。</span><span class="sxs-lookup"><span data-stu-id="367b8-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="367b8-108">在下列程式碼範例中，會使用 SOM 的 `FirstName` 及 `LastName` 類別，建立 `CustomerId` 及 <xref:System.Xml.Schema.XmlSchemaElement> 項目，以及客戶結構描述的 <xref:System.Xml.Schema.XmlSchemaAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="367b8-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="367b8-109">除了 <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> 及 <xref:System.Xml.Schema.XmlSchemaElement> 類別的 <xref:System.Xml.Schema.XmlSchemaAttribute> 屬性 (其對應至 XML 結構描述中 `<xs:element />` 及 `<xs:attribute />` 項目的 name 屬性 (Attribute))，結構描述所允許的所有其他屬性 (`defaultValue`、`fixedValue` 及 `form` 等)，在 <xref:System.Xml.Schema.XmlSchemaElement> 及 <xref:System.Xml.Schema.XmlSchemaAttribute> 類別中都有對應的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="367b8-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="367b8-110">建立結構描述型別</span><span class="sxs-lookup"><span data-stu-id="367b8-110">Creating Schema Types</span></span>  
 <span data-ttu-id="367b8-111">項目及屬性的內容是由其型別來定義。</span><span class="sxs-lookup"><span data-stu-id="367b8-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="367b8-112">若要建立其型別為其中一個內建結構描述型別的項目及屬性 (Attribute)，請使用 <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 類別，以內建型別之對應的限定名稱設定 <xref:System.Xml.Schema.XmlSchemaElement> 或 <xref:System.Xml.Schema.XmlSchemaAttribute> 類別的 <xref:System.Xml.XmlQualifiedName> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="367b8-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="367b8-113">若要建立項目及屬性的使用者定義型別，請使用 <xref:System.Xml.Schema.XmlSchemaSimpleType> 或 <xref:System.Xml.Schema.XmlSchemaComplexType> 類別，建立新的簡單或複雜型別。</span><span class="sxs-lookup"><span data-stu-id="367b8-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="367b8-114">若要建立做為項目或屬性 (Attribute) 之匿名子系的未命名簡單或複雜型別 (僅簡單型別適用於屬性 (Attribute))，請將 <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> 或 <xref:System.Xml.Schema.XmlSchemaElement> 類別的 <xref:System.Xml.Schema.XmlSchemaAttribute> 屬性設為未命名的簡單或複雜型別，而不是 <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 或 <xref:System.Xml.Schema.XmlSchemaElement> 類別的 <xref:System.Xml.Schema.XmlSchemaAttribute> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="367b8-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="367b8-115">XML 結構描述允許匿名及具名簡單型別，利用限制其他簡單型別 (內建的或使用者定義的) 衍生，或建構為其他簡單型別的清單或聯集。</span><span class="sxs-lookup"><span data-stu-id="367b8-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="367b8-116"><xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> 類別可用於藉由限制內建 `xs:string` 型別，來建立簡單型別。</span><span class="sxs-lookup"><span data-stu-id="367b8-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="367b8-117">您也可以使用 <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> 或 <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> 類別，建立清單或聯集型別。</span><span class="sxs-lookup"><span data-stu-id="367b8-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="367b8-118"><xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> 屬性可表示它是簡單型別限制、清單還是聯集。</span><span class="sxs-lookup"><span data-stu-id="367b8-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="367b8-119">在下列程式碼範例中，`FirstName` 項目的型別為內建型別 `xs:string`，`LastName` 項目的型別為限制內建型別 `xs:string` 的具名簡單型別 (`MaxLength` Facet 值為 20)，而 `CustomerId` 屬性的型別為內建型別 `xs:positiveInteger`。</span><span class="sxs-lookup"><span data-stu-id="367b8-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="367b8-120">`Customer` 項目為匿名的複雜型別，其物件是 `FirstName` 及 `LastName` 項目的序列，而且其屬性包含 `CustomerId` 屬性。</span><span class="sxs-lookup"><span data-stu-id="367b8-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="367b8-121">您也可以將 <xref:System.Xml.Schema.XmlSchemaChoice> 或 <xref:System.Xml.Schema.XmlSchemaAll> 類別做為複雜型別的物件，以複寫 `<xs:choice />` 或 `<xs:all />` 語意。</span><span class="sxs-lookup"><span data-stu-id="367b8-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="367b8-122">建立及編譯結構描述</span><span class="sxs-lookup"><span data-stu-id="367b8-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="367b8-123">此時，已使用 SOM API 在記憶體中建立項目子系及屬性、其對應的型別，以及最上層 `Customer` 項目。</span><span class="sxs-lookup"><span data-stu-id="367b8-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="367b8-124">在下列程式碼範例中，會使用 <xref:System.Xml.Schema.XmlSchema> 類別建立結構描述項目，使用 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 屬性將最上層項目及型別加入其中，並使用 <xref:System.Xml.Schema.XmlSchemaSet> 類別編譯完整的結構描述，然後寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="367b8-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="367b8-125"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> 方法會根據 XML 結構描述的規則，驗證客戶結構描述，並使 Post-Schema-Compilation 屬性可用。</span><span class="sxs-lookup"><span data-stu-id="367b8-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="367b8-126">SOM API 中的所有 Post-Schema-Compilation 屬性都與 Post-Schema-Validation-Infoset 不同。</span><span class="sxs-lookup"><span data-stu-id="367b8-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="367b8-127">加入 <xref:System.Xml.Schema.ValidationEventHandler> 的 <xref:System.Xml.Schema.XmlSchemaSet> 是一種委派屬性，它會呼叫回呼方法 `ValidationCallback`，以處理結構描述驗證警告及錯誤。</span><span class="sxs-lookup"><span data-stu-id="367b8-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="367b8-128">以下是完整的程式碼範例，以及寫入主控台的客戶結構描述。</span><span class="sxs-lookup"><span data-stu-id="367b8-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
            <xs:element name="LastName" type="tns:LastNameType" />  
         </xs:sequence>  
         <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="LastNameType">  
      <xs:restriction base="xs:string">  
         <xs:maxLength value="20" />  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="367b8-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="367b8-129">See Also</span></span>  
 [<span data-ttu-id="367b8-130">XML 結構描述物件模型概觀</span><span class="sxs-lookup"><span data-stu-id="367b8-130">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="367b8-131">讀取和寫入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="367b8-131">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="367b8-132">周遊 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="367b8-132">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="367b8-133">編輯 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="367b8-133">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="367b8-134">併入或匯入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="367b8-134">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="367b8-135">結構描述編譯的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="367b8-135">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="367b8-136">後結構描述編譯資訊集</span><span class="sxs-lookup"><span data-stu-id="367b8-136">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
