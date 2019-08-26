---
title: 編輯 XML 結構描述
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d0d67c82e753b044f759b4d1139c5f6b4837b31
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948476"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="c848c-102">編輯 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="c848c-102">Editing XML Schemas</span></span>
<span data-ttu-id="c848c-103">編輯 XML 結構描述是結構描述物件模型 (SOM) 的其中一項最重要功能。</span><span class="sxs-lookup"><span data-stu-id="c848c-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="c848c-104">SOM 的所有前結構描述編譯屬性都可用於變更 XML 結構描述中的現有值。</span><span class="sxs-lookup"><span data-stu-id="c848c-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="c848c-105">然後可重新編譯該 XML 結構描述以反映這些變更。</span><span class="sxs-lookup"><span data-stu-id="c848c-105">The XML schema can then be recompiled to reflect the changes.</span></span>  
  
 <span data-ttu-id="c848c-106">編輯載入 SOM 中之結構描述的第一步是往返結構描述。</span><span class="sxs-lookup"><span data-stu-id="c848c-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="c848c-107">在嘗試編輯結構描述之前，您應該熟悉如何使用 SOM API 往返結構描述。</span><span class="sxs-lookup"><span data-stu-id="c848c-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="c848c-108">您也應該熟悉後結構描述編譯資訊集 (PSCI) 的前結構描述編譯屬性及後結構描述編譯屬性。</span><span class="sxs-lookup"><span data-stu-id="c848c-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>  
  
## <a name="editing-an-xml-schema"></a><span data-ttu-id="c848c-109">編輯 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="c848c-109">Editing an XML Schema</span></span>  
 <span data-ttu-id="c848c-110">在此區段中會提供兩個程式碼範例，它們都會編輯在[建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)主題中建立的客戶結構描述。</span><span class="sxs-lookup"><span data-stu-id="c848c-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="c848c-111">第一個程式碼範例會將新 `PhoneNumber` 項目加入至 `Customer` 項目，第二個程式碼範例會將新 `Title` 屬性加入至 `FirstName` 項目。</span><span class="sxs-lookup"><span data-stu-id="c848c-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="c848c-112">第一個範例還會使用後結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> 集合，做為當第二個程式碼範例使用前結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 集合時周遊客戶結構描述的方式。</span><span class="sxs-lookup"><span data-stu-id="c848c-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
### <a name="phonenumber-element-example"></a><span data-ttu-id="c848c-113">PhoneNumber 項目範例</span><span class="sxs-lookup"><span data-stu-id="c848c-113">PhoneNumber Element Example</span></span>  
 <span data-ttu-id="c848c-114">此第一個程式碼範例將新 `PhoneNumber` 項目加入至客戶結構描述的 `Customer` 項目。</span><span class="sxs-lookup"><span data-stu-id="c848c-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="c848c-115">該程式碼範例會使用下列步驟編輯客戶結構描述。</span><span class="sxs-lookup"><span data-stu-id="c848c-115">The code example edits the customer schema in the following steps.</span></span>  
  
1. <span data-ttu-id="c848c-116">將客戶結構描述加入至新 <xref:System.Xml.Schema.XmlSchemaSet> 物件，然後編譯它。</span><span class="sxs-lookup"><span data-stu-id="c848c-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="c848c-117">讀取或編譯結構描述時遇到的任何結構描述驗證警告及錯誤，都會由 <xref:System.Xml.Schema.ValidationEventHandler> 委派處理。</span><span class="sxs-lookup"><span data-stu-id="c848c-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="c848c-118">藉由重複處理 <xref:System.Xml.Schema.XmlSchema> 屬性，從 <xref:System.Xml.Schema.XmlSchemaSet> 擷取已編譯的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 物件。</span><span class="sxs-lookup"><span data-stu-id="c848c-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="c848c-119">因為已編譯結構描述，因此可存取後結構描述編譯資訊集 (PSCI) 屬性。</span><span class="sxs-lookup"><span data-stu-id="c848c-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="c848c-120">使用 `PhoneNumber` 類別建立 <xref:System.Xml.Schema.XmlSchemaElement> 項目，使用 `xs:string` 及 <xref:System.Xml.Schema.XmlSchemaSimpleType> 類別建立 <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> 簡單型別限制，將模式 Facet 加入至該限制的 <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> 屬性，並將該限制加入至簡單型別的 <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> 屬性，再將該簡單型別加入至 <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> 項目的 `PhoneNumber`。</span><span class="sxs-lookup"><span data-stu-id="c848c-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>  
  
4. <span data-ttu-id="c848c-121">在後結構描述編譯 <xref:System.Xml.Schema.XmlSchemaElement> 集合的 <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> 集合中，重複處理每個 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c848c-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>  
  
5. <span data-ttu-id="c848c-122">如果項目的 <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> 是 `"Customer"`，則使用 `Customer` 類別取得 <xref:System.Xml.Schema.XmlSchemaComplexType> 項目的複雜型別，並使用 <xref:System.Xml.Schema.XmlSchemaSequence> 類別取得該複雜型別的順序物件。</span><span class="sxs-lookup"><span data-stu-id="c848c-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
6. <span data-ttu-id="c848c-123">使用包含現有 `PhoneNumber` 及 `FirstName` 項目之序列的前結構描述編譯 `LastName` 集合，將新 <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> 項目加入該序列。</span><span class="sxs-lookup"><span data-stu-id="c848c-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>  
  
7. <span data-ttu-id="c848c-124">最後，使用 <xref:System.Xml.Schema.XmlSchema> 類別的 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 及 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法，重新處理及編譯修改的 <xref:System.Xml.Schema.XmlSchemaSet> 物件，並將它寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="c848c-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="c848c-125">下列是完整的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="c848c-125">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 <span data-ttu-id="c848c-126">下列是在[建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)主題中建立之已修改的客戶結構描述。</span><span class="sxs-lookup"><span data-stu-id="c848c-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>  
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
```  
  
### <a name="title-attribute-example"></a><span data-ttu-id="c848c-127">標題屬性範例</span><span class="sxs-lookup"><span data-stu-id="c848c-127">Title Attribute Example</span></span>  
 <span data-ttu-id="c848c-128">此第二個程式碼範例將新 `Title` 屬性加入至客戶結構描述的 `FirstName` 項目。</span><span class="sxs-lookup"><span data-stu-id="c848c-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="c848c-129">在第一個程式碼範例中，`FirstName` 項目的型別是 `xs:string`。</span><span class="sxs-lookup"><span data-stu-id="c848c-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="c848c-130">若要讓 `FirstName` 項目具有屬性及字串內容，必須將其型別變為具有簡單內容延伸程式內容模型的複雜型別。</span><span class="sxs-lookup"><span data-stu-id="c848c-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>  
  
 <span data-ttu-id="c848c-131">該程式碼範例會使用下列步驟編輯客戶結構描述。</span><span class="sxs-lookup"><span data-stu-id="c848c-131">The code example edits the customer schema in the following steps.</span></span>  
  
1. <span data-ttu-id="c848c-132">將客戶結構描述加入至新 <xref:System.Xml.Schema.XmlSchemaSet> 物件，然後編譯它。</span><span class="sxs-lookup"><span data-stu-id="c848c-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="c848c-133">讀取或編譯結構描述時遇到的任何結構描述驗證警告及錯誤，都會由 <xref:System.Xml.Schema.ValidationEventHandler> 委派處理。</span><span class="sxs-lookup"><span data-stu-id="c848c-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="c848c-134">藉由重複處理 <xref:System.Xml.Schema.XmlSchema> 屬性，從 <xref:System.Xml.Schema.XmlSchemaSet> 擷取已編譯的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 物件。</span><span class="sxs-lookup"><span data-stu-id="c848c-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="c848c-135">因為已編譯結構描述，因此可存取後結構描述編譯資訊集 (PSCI) 屬性。</span><span class="sxs-lookup"><span data-stu-id="c848c-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="c848c-136">使用 `FirstName` 類別，建立 <xref:System.Xml.Schema.XmlSchemaComplexType> 項目的新複雜型別。</span><span class="sxs-lookup"><span data-stu-id="c848c-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
4. <span data-ttu-id="c848c-137">使用 `xs:string` 及 <xref:System.Xml.Schema.XmlSchemaSimpleContent> 類別，建立基底型別為 <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> 的新簡單內容延伸程式。</span><span class="sxs-lookup"><span data-stu-id="c848c-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>  
  
5. <span data-ttu-id="c848c-138">使用 `Title` 類別，建立 <xref:System.Xml.Schema.XmlSchemaAttribute> 為 <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> 的新 `xs:string` 屬性，並將該屬性加入至簡單內容延伸程式。</span><span class="sxs-lookup"><span data-stu-id="c848c-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>  
  
6. <span data-ttu-id="c848c-139">將簡單內容的內容模型設為簡單內容延伸程式，並將複雜型別的內容模型設為簡單內容。</span><span class="sxs-lookup"><span data-stu-id="c848c-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>  
  
7. <span data-ttu-id="c848c-140">將新的複雜型別加入至前結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="c848c-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
8. <span data-ttu-id="c848c-141">重複處理前結構描述編譯 <xref:System.Xml.Schema.XmlSchemaObject> 集合中的每個 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c848c-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c848c-142">因為 `FirstName` 項目不是結構描述中的全域項目，所以它不可用在 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 或 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> 集合中。</span><span class="sxs-lookup"><span data-stu-id="c848c-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="c848c-143">程式碼範例會藉由先尋找 `FirstName` 項目，以尋找 `Customer` 項目。</span><span class="sxs-lookup"><span data-stu-id="c848c-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>  
>   
>  <span data-ttu-id="c848c-144">第一個程式碼範例會使用後結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> 集合，以往返結構描述。</span><span class="sxs-lookup"><span data-stu-id="c848c-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="c848c-145">在此範例中，前結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 集合用於往返結構描述。</span><span class="sxs-lookup"><span data-stu-id="c848c-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="c848c-146">當兩個集合都提供對結構描述中全域項目的存取權時，重複處理 <xref:System.Xml.Schema.XmlSchema.Items%2A> 集合會浪費更多時間，因為您必須重複處理結構描述中的所有全域項目，且其不具有任何 PSCI 屬性。</span><span class="sxs-lookup"><span data-stu-id="c848c-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="c848c-147">PSCI 集合 (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>、<xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>、<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType> 等) 可提供其全域項目、屬性、型別及其 PSCI 屬性的直接存取權。</span><span class="sxs-lookup"><span data-stu-id="c848c-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>  
  
1. <span data-ttu-id="c848c-148">如果 <xref:System.Xml.Schema.XmlSchemaObject> 項目的 <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> 為 `"Customer"`，則使用 `Customer` 類別取得 <xref:System.Xml.Schema.XmlSchemaComplexType> 項目的複雜型別，並使用 <xref:System.Xml.Schema.XmlSchemaSequence> 類別取得該複雜型別的順序物件。</span><span class="sxs-lookup"><span data-stu-id="c848c-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
2. <span data-ttu-id="c848c-149">重複處理前結構描述編譯 <xref:System.Xml.Schema.XmlSchemaParticle> 集合中的每個 <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c848c-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
3. <span data-ttu-id="c848c-150">如果 <xref:System.Xml.Schema.XmlSchemaParticle> 項目的 <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> 為 `"FirstName"`，則將 <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 項目的 `FirstName` 設為新的 `FirstName` 複雜型別。</span><span class="sxs-lookup"><span data-stu-id="c848c-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>  
  
4. <span data-ttu-id="c848c-151">最後，使用 <xref:System.Xml.Schema.XmlSchema> 類別的 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 及 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法，重新處理及編譯修改的 <xref:System.Xml.Schema.XmlSchemaSet> 物件，並將它寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="c848c-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="c848c-152">下列是完整的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="c848c-152">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 <span data-ttu-id="c848c-153">下列是在[建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)主題中建立之已修改的客戶結構描述。</span><span class="sxs-lookup"><span data-stu-id="c848c-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
```xml  
<?xml version="1.0" encoding=" utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />  
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
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c848c-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c848c-154">See also</span></span>

- [<span data-ttu-id="c848c-155">XML 結構描述物件模型概觀</span><span class="sxs-lookup"><span data-stu-id="c848c-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="c848c-156">讀取和寫入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="c848c-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="c848c-157">建置 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="c848c-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="c848c-158">周遊 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="c848c-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="c848c-159">併入或匯入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="c848c-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="c848c-160">用於結構描述編譯的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="c848c-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="c848c-161">後結構描述編譯資訊集</span><span class="sxs-lookup"><span data-stu-id="c848c-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
