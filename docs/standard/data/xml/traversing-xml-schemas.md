---
title: 周遊 XML 結構描述
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6040a7aa8f3244ea0ce2e66042537bc45c347b05
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037845"
---
# <a name="traversing-xml-schemas"></a><span data-ttu-id="e5abe-102">周遊 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="e5abe-102">Traversing XML Schemas</span></span>

<span data-ttu-id="e5abe-103">使用結構描述物件模型 (SOM) API 周遊 XML 結構描述，可以提供對儲存於 SOM 之項目、屬性及型別的存取權。</span><span class="sxs-lookup"><span data-stu-id="e5abe-103">Traversing an XML schema using the Schema Object Model (SOM) API provides access to the elements, attributes, and types stored in the SOM.</span></span> <span data-ttu-id="e5abe-104">周遊載入到 SOM 的 XML 結構描述也是使用 SOM API 編輯 XML 結構描述的第一步。</span><span class="sxs-lookup"><span data-stu-id="e5abe-104">Traversing an XML schema loaded into the SOM is also the first step in editing an XML schema using the SOM API.</span></span>

## <a name="traversing-an-xml-schema"></a><span data-ttu-id="e5abe-105">周遊 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="e5abe-105">Traversing an XML Schema</span></span>

<span data-ttu-id="e5abe-106"><xref:System.Xml.Schema.XmlSchema> 類別的下列屬性可以提供對加入至 XML 結構描述之所有全域項目集合的存取權。</span><span class="sxs-lookup"><span data-stu-id="e5abe-106">The following properties of the <xref:System.Xml.Schema.XmlSchema> class provide access to the collection of all global items added to the XML schema.</span></span>

|<span data-ttu-id="e5abe-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e5abe-107">Property</span></span>|<span data-ttu-id="e5abe-108">儲存於集合或陣列中的物件型別</span><span class="sxs-lookup"><span data-stu-id="e5abe-108">Object type stored in the collection or array</span></span>|
|--------------|---------------------------------------------------|
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<span data-ttu-id="e5abe-109"><xref:System.Xml.Schema.XmlSchemaExternal>、<xref:System.Xml.Schema.XmlSchemaInclude>、<xref:System.Xml.Schema.XmlSchemaImport> 或 <xref:System.Xml.Schema.XmlSchemaRedefine></span><span class="sxs-lookup"><span data-stu-id="e5abe-109"><xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>, or <xref:System.Xml.Schema.XmlSchemaRedefine></span></span>|
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<span data-ttu-id="e5abe-110"><xref:System.Xml.Schema.XmlSchemaObject> (可提供對所有全域層級項目、屬性及型別的存取權)。</span><span class="sxs-lookup"><span data-stu-id="e5abe-110"><xref:System.Xml.Schema.XmlSchemaObject> (provides access to all global level elements, attributes, and types).</span></span>|
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<span data-ttu-id="e5abe-111"><xref:System.Xml.Schema.XmlSchemaType>、<xref:System.Xml.Schema.XmlSchemaSimpleType>、<xref:System.Xml.Schema.XmlSchemaComplexType></span><span class="sxs-lookup"><span data-stu-id="e5abe-111"><xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType></span></span>|
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<span data-ttu-id="e5abe-112"><xref:System.Xml.XmlAttribute> (提供對不屬於結構描述命名空間之屬性的存取權)</span><span class="sxs-lookup"><span data-stu-id="e5abe-112"><xref:System.Xml.XmlAttribute> (provides access to attributes that do not belong to the schema namespace)</span></span>|

> [!NOTE]
> <span data-ttu-id="e5abe-113">上述表格中列出的所有屬性 (除 <xref:System.Xml.Schema.XmlSchema.Items%2A> 屬性之外)，都是後結構描述編譯資訊集 (PSCI) 屬性，僅在編譯結構描述之後才可用。</span><span class="sxs-lookup"><span data-stu-id="e5abe-113">All of the properties listed in the table above, except for the <xref:System.Xml.Schema.XmlSchema.Items%2A> property, are Post-Schema-Compilation-Infoset (PSCI) properties that are not available until the schema has been compiled.</span></span> <span data-ttu-id="e5abe-114"><xref:System.Xml.Schema.XmlSchema.Items%2A> 屬性是前結構描述編譯屬性，其可在編譯結構描述之前使用，以存取及編輯所有全域層級項目、屬性及型別。</span><span class="sxs-lookup"><span data-stu-id="e5abe-114">The <xref:System.Xml.Schema.XmlSchema.Items%2A> property is a pre-schema-compilation property that can be used before the schema has been compiled to access and edit all global level elements, attributes, and types.</span></span>
>
> <span data-ttu-id="e5abe-115"><xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> 屬性提供對不屬於結構描述命名空間之所有屬性的存取權。</span><span class="sxs-lookup"><span data-stu-id="e5abe-115">The <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> property provides access to all the attributes that do not belong to the schema namespace.</span></span> <span data-ttu-id="e5abe-116">結構描述處理器不會處理這些屬性。</span><span class="sxs-lookup"><span data-stu-id="e5abe-116">These attributes are not processed by the schema processor.</span></span>

<span data-ttu-id="e5abe-117">接下來的程式碼範例會示範如何周遊[建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)主題中建立的客戶結構描述。</span><span class="sxs-lookup"><span data-stu-id="e5abe-117">The code example that follows demonstrates traversing the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="e5abe-118">該程式碼範例示範如何使用上述集合周遊結構描述，並將結構描述中的所有項目和屬性寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="e5abe-118">The code example demonstrates traversing the schema using the collections described above and writes all the elements and attributes in the schema to the console.</span></span>

<span data-ttu-id="e5abe-119">該範例會按下列步驟周遊客戶結構描述。</span><span class="sxs-lookup"><span data-stu-id="e5abe-119">The sample traverses the customer schema in the following steps.</span></span>

1. <span data-ttu-id="e5abe-120">將客戶結構描述加入至新 <xref:System.Xml.Schema.XmlSchemaSet> 物件，然後編譯它。</span><span class="sxs-lookup"><span data-stu-id="e5abe-120">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="e5abe-121">讀取或編譯結構描述時遇到的任何結構描述驗證警告及錯誤，都會由 <xref:System.Xml.Schema.ValidationEventHandler> 委派處理。</span><span class="sxs-lookup"><span data-stu-id="e5abe-121">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="e5abe-122">藉由重複處理 <xref:System.Xml.Schema.XmlSchema> 屬性，從 <xref:System.Xml.Schema.XmlSchemaSet> 擷取已編譯的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 物件。</span><span class="sxs-lookup"><span data-stu-id="e5abe-122">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="e5abe-123">因為已編譯結構描述，因此可存取後結構描述編譯資訊集 (PSCI) 屬性。</span><span class="sxs-lookup"><span data-stu-id="e5abe-123">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="e5abe-124">重複處理後結構描述編譯 <xref:System.Xml.Schema.XmlSchemaElement> 集合之 <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> 集合中的每個 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>，會將每個項目的名稱寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="e5abe-124">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection writing the name of each element to the console.</span></span>

4. <span data-ttu-id="e5abe-125">使用 `Customer` 類別，取得 <xref:System.Xml.Schema.XmlSchemaComplexType> 項目的複雜型別。</span><span class="sxs-lookup"><span data-stu-id="e5abe-125">Gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

5. <span data-ttu-id="e5abe-126">如果複雜型別具有任何屬性，請取得 <xref:System.Collections.IDictionaryEnumerator> 來列舉每個 <xref:System.Xml.Schema.XmlSchemaAttribute>，並將其名稱寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="e5abe-126">If the complex type has any attributes, gets an <xref:System.Collections.IDictionaryEnumerator> to enumerate over each <xref:System.Xml.Schema.XmlSchemaAttribute> and writes its name to the console.</span></span>

6. <span data-ttu-id="e5abe-127">使用 <xref:System.Xml.Schema.XmlSchemaSequence> 類別，取得複雜型別的順序物件。</span><span class="sxs-lookup"><span data-stu-id="e5abe-127">Gets the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

7. <span data-ttu-id="e5abe-128">重複處理 <xref:System.Xml.Schema.XmlSchemaElement> 集合中的每個 <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType>，會將每個項目子系的名稱寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="e5abe-128">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection writing the name of each child element to the console.</span></span>

<span data-ttu-id="e5abe-129">下列是完整的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="e5abe-129">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
[!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
[!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]

<span data-ttu-id="e5abe-130">如果 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> 屬性是使用者定義的簡單型別或複雜型別，則其可以為 <xref:System.Xml.Schema.XmlSchemaSimpleType> 或<xref:System.Xml.Schema.XmlSchemaComplexType>。</span><span class="sxs-lookup"><span data-stu-id="e5abe-130">The <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> property can be <xref:System.Xml.Schema.XmlSchemaSimpleType>, or <xref:System.Xml.Schema.XmlSchemaComplexType> if it is a user-defined simple type or a complex type.</span></span> <span data-ttu-id="e5abe-131">如果其為 W3C XML 結構描述建議事項中定義的其中一個內建資料型別，則也可以為 <xref:System.Xml.Schema.XmlSchemaDatatype>。</span><span class="sxs-lookup"><span data-stu-id="e5abe-131">It can also be <xref:System.Xml.Schema.XmlSchemaDatatype> if it is one of the built-in datatypes defined in the W3C XML Schema Recommendation.</span></span> <span data-ttu-id="e5abe-132">在客戶結構描述中，<xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 項目的 `Customer` 為 <xref:System.Xml.Schema.XmlSchemaComplexType>，`FirstName` 及 `LastName` 項目為 <xref:System.Xml.Schema.XmlSchemaSimpleType>。</span><span class="sxs-lookup"><span data-stu-id="e5abe-132">In the customer schema, the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> of the `Customer` element is <xref:System.Xml.Schema.XmlSchemaComplexType>, and the `FirstName` and `LastName` elements are <xref:System.Xml.Schema.XmlSchemaSimpleType>.</span></span>

<span data-ttu-id="e5abe-133">[建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)主題中的程式碼範例使用 <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> 集合，將屬性 `CustomerId` 加入至 `Customer` 項目。</span><span class="sxs-lookup"><span data-stu-id="e5abe-133">The code example in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic used the <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> collection to add the attribute `CustomerId` to the `Customer` element.</span></span> <span data-ttu-id="e5abe-134">這是前結構描述編譯屬性。</span><span class="sxs-lookup"><span data-stu-id="e5abe-134">This is a pre-schema-compilation property.</span></span> <span data-ttu-id="e5abe-135">對應的後結構描述編譯資訊集屬性為 <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> 集合，其保留複雜型別的所有屬性，包括透過型別衍生繼承的那些屬性。</span><span class="sxs-lookup"><span data-stu-id="e5abe-135">The corresponding Post-Schema-Compilation-Infoset property is the <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> collection, which holds all the attributes of the complex type, including the ones that are inherited through type derivation.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5abe-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5abe-136">See also</span></span>

- [<span data-ttu-id="e5abe-137">XML 結構描述物件模型概觀</span><span class="sxs-lookup"><span data-stu-id="e5abe-137">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="e5abe-138">讀取和寫入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="e5abe-138">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="e5abe-139">建置 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="e5abe-139">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="e5abe-140">編輯 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="e5abe-140">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="e5abe-141">併入或匯入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="e5abe-141">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="e5abe-142">用於結構描述編譯的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="e5abe-142">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="e5abe-143">後結構描述編譯資訊集</span><span class="sxs-lookup"><span data-stu-id="e5abe-143">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
