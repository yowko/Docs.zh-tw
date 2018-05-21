---
title: 從 XML 文件推斷結構描述
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8640a951acab512cbe2397df831a74700b5ad6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="4c0b9-102">從 XML 文件推斷結構描述</span><span class="sxs-lookup"><span data-stu-id="4c0b9-102">Inferring Schemas from XML Documents</span></span>
<span data-ttu-id="4c0b9-103">本主題說明如何使用 <xref:System.Xml.Schema.XmlSchemaInference> 類別，從 XML 文件結構推斷 XML 結構描述定義語言 (XSD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-103">This topic describes how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XML Schema definition language (XSD) schema from the structure of an XML document.</span></span>  
  
## <a name="the-schema-inference-process"></a><span data-ttu-id="4c0b9-104">結構描述推斷程序</span><span class="sxs-lookup"><span data-stu-id="4c0b9-104">The Schema Inference Process</span></span>  
 <span data-ttu-id="4c0b9-105"><xref:System.Xml.Schema.XmlSchemaInference> 命名空間的 <xref:System.Xml.Schema?displayProperty=nameWithType> 類別，可用來從 XML 文件結構產生一或多個 XML 結構描述定義語言 (XSD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-105">The <xref:System.Xml.Schema.XmlSchemaInference> class of the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace is used to generate one or more XML Schema definition language (XSD) schemas from the structure of an XML document.</span></span> <span data-ttu-id="4c0b9-106">產生的結構描述可用來驗證原始的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-106">The generated schemas may be used to validate the original XML document.</span></span>  
  
 <span data-ttu-id="4c0b9-107">由於 XML 文件是由 <xref:System.Xml.Schema.XmlSchemaInference> 類別所處理，因此 <xref:System.Xml.Schema.XmlSchemaInference> 類別會對可說明 XML 文件中之項目和屬性的結構描述元件進行假設。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-107">As an XML document is processed by the <xref:System.Xml.Schema.XmlSchemaInference> class, the <xref:System.Xml.Schema.XmlSchemaInference> class makes assumptions about the schema components that describe the elements and attributes in the XML document.</span></span> <span data-ttu-id="4c0b9-108"><xref:System.Xml.Schema.XmlSchemaInference> 類別也可藉由推斷特定項目或屬性的最嚴格型別，以條件約束的方式推斷結構描述元件。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-108">The <xref:System.Xml.Schema.XmlSchemaInference> class also infers schema components in a constrained way by inferring the most restrictive type for a particular element or attribute.</span></span> <span data-ttu-id="4c0b9-109">當收集到較多 XML 文件的相關資訊時，就會推斷較不嚴格的型別，而放寬這些條件約束。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-109">As more information about the XML document is gathered, these constraints are loosened by inferring less restrictive types.</span></span> <span data-ttu-id="4c0b9-110">`xs:string` 是推斷為最不嚴格的型別。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-110">The least restrictive type that can be inferred is `xs:string`.</span></span>  
  
 <span data-ttu-id="4c0b9-111">我們以下列 XML 文件片段為例。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-111">Take, for example, the following piece of an XML document.</span></span>  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 <span data-ttu-id="4c0b9-112">在上述範例中，`attribute1` 處理序發現 `6` 屬性的值為 <xref:System.Xml.Schema.XmlSchemaInference> 時，會假設此屬性的型別為 `xs:unsignedByte`。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-112">In the example above, when the `attribute1` attribute is encountered with a value of `6` by the <xref:System.Xml.Schema.XmlSchemaInference> process, it is assumed to be of type `xs:unsignedByte`.</span></span> <span data-ttu-id="4c0b9-113">`parent` 處理序發現第二個 <xref:System.Xml.Schema.XmlSchemaInference> 項目時，即會將型別修改為 `xs:string` 而放寬條件約束，因為 `attribute1` 屬性的值此時為 `A`。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-113">When the second `parent` element is encountered by the <xref:System.Xml.Schema.XmlSchemaInference> process, the constraint is loosened by modifying the type to `xs:string` because the value of the `attribute1` attribute is now `A`.</span></span> <span data-ttu-id="4c0b9-114">同樣地，所有 `minOccurs` 項目中在結構描述內進行推斷的 `child` 屬性，也會放寬為 `minOccurs="0"`，因為第二個父項目沒有項目子系。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-114">Similarly, the `minOccurs` attribute for all the `child` elements inferred in the schema are loosened to `minOccurs="0"` because the second parent element has no child elements.</span></span>  
  
## <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="4c0b9-115">從 XML 文件推斷結構描述</span><span class="sxs-lookup"><span data-stu-id="4c0b9-115">Inferring Schemas from XML Documents</span></span>  
 <span data-ttu-id="4c0b9-116"><xref:System.Xml.Schema.XmlSchemaInference> 類別可使用兩種多載 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法，從 XML 文件推斷結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-116">The <xref:System.Xml.Schema.XmlSchemaInference> class uses two overloaded <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> methods to infer a schema from an XML document.</span></span>  
  
 <span data-ttu-id="4c0b9-117">第一種 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> 方法可根據 XML 文件建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-117">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to create a schema based on an XML document.</span></span> <span data-ttu-id="4c0b9-118">第二種 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> 方法用來推斷可說明多個 XML 文件的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-118">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to infer a schema that describes multiple XML documents.</span></span> <span data-ttu-id="4c0b9-119">例如，您可以逐一將多個 XML 文件傳送給 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> 方法，以產生可說明完整 XML 文件集的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-119">For example, you can feed multiple XML documents to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method one at a time to produce a schema that describes the entire set of XML documents.</span></span>  
  
 <span data-ttu-id="4c0b9-120">第一種 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> 方法會從 <xref:System.Xml.XmlReader> 物件所含的 XML 文件推斷結構描述，並傳回含有所推斷之結構描述的 <xref:System.Xml.Schema.XmlSchemaSet> 物件。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-120">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method infers a schema from an XML document contained in an <xref:System.Xml.XmlReader> object, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span> <span data-ttu-id="4c0b9-121">第二種 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> 方法會搜尋 <xref:System.Xml.Schema.XmlSchemaSet> 物件中是否有目標命名空間與 <xref:System.Xml.XmlReader> 物件所含之 XML 文件相同的結構描述，然後進一步調整現有的結構描述，並傳回含有所推斷之結構描述的 <xref:System.Xml.Schema.XmlSchemaSet> 物件。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-121">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method searches an <xref:System.Xml.Schema.XmlSchemaSet> object for a schema with the same target namespace as the XML document contained in the <xref:System.Xml.XmlReader> object, refines the existing schema, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span>  
  
 <span data-ttu-id="4c0b9-122">對調整的結構描述所作的變更取決於在 XML 文件中找到的新結構。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-122">The changes made to the refined schema are based on new structure found in the XML document.</span></span> <span data-ttu-id="4c0b9-123">例如，當 XML 文件周遊時，就會對找到的資料型別進行相關假設，並根據這些假設建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-123">For example, as an XML document is traversed, assumptions are made about the data types found, and the schema is created based on those assumptions.</span></span> <span data-ttu-id="4c0b9-124">但若在第二次推斷傳遞時發現資料與原始假設不同，則會進一步調整結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-124">However, if data is encountered on a second inference pass that differs from the original assumption, the schema is refined.</span></span> <span data-ttu-id="4c0b9-125">下列範例將說明調整的程序。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-125">The following example illustrates the refinement process.</span></span>  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 <span data-ttu-id="4c0b9-126">此範例以下列檔案 (`item1.xml`) 做為第一個輸入。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-126">The example takes the following file, `item1.xml`, as its first input.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 <span data-ttu-id="4c0b9-127">接著，此範例會以 `item2.xml` 檔案做為第二個輸入：</span><span class="sxs-lookup"><span data-stu-id="4c0b9-127">The example then takes the `item2.xml` file as its second input:</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 <span data-ttu-id="4c0b9-128">在第一個 XML 文件中發現 `productID` 屬性時，會將 `123456789` 這個值假設為 `xs:unsignedInt` 型別。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-128">When the `productID` attribute is encountered in the first XML document, the value of `123456789` is assumed to be an `xs:unsignedInt` type.</span></span> <span data-ttu-id="4c0b9-129">但當讀取第二個 XML 文件並發現 `A53-246` 這個值時，則無法再假設 `xs:unsignedInt` 型別。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-129">However, when the second XML document is read and the value of `A53-246` is found, the `xs:unsignedInt` type can no longer be assumed.</span></span> <span data-ttu-id="4c0b9-130">會調整結構描述，而 `productID` 的型別會變更為 `xs:string`。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-130">The schema is refined and the type of `productID` is changed to `xs:string`.</span></span> <span data-ttu-id="4c0b9-131">此外，`minOccurs` 項目的 `supplierID` 屬性會設為 `0`，因為第二個 XML 文件中不含 `supplierID` 項目。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-131">In addition, the `minOccurs` attribute for the `supplierID` element is set to `0`, because the second XML document contains no `supplierID` element.</span></span>  
  
 <span data-ttu-id="4c0b9-132">以下是從第一份 XML 文件推斷的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-132">The following is the schema inferred from the first XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 <span data-ttu-id="4c0b9-133">以下是從第一份 XML 文件推斷的結構描述，並以第二份 XML 文件進一步調整。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-133">The following is the schema inferred from the first XML document, refined by the second XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a><span data-ttu-id="4c0b9-134">內嵌結構描述</span><span class="sxs-lookup"><span data-stu-id="4c0b9-134">Inline Schemas</span></span>  
 <span data-ttu-id="4c0b9-135">如果在 <xref:System.Xml.Schema.XmlSchemaInference> 處理序期間發現內嵌 XML 結構描述定義語言 (XSD) 結構描述，則會擲回 <xref:System.Xml.Schema.XmlSchemaInferenceException>。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-135">If an inline XML Schema definition language (XSD) schema is encountered during the <xref:System.Xml.Schema.XmlSchemaInference> process, an <xref:System.Xml.Schema.XmlSchemaInferenceException> is thrown.</span></span> <span data-ttu-id="4c0b9-136">例如，下列內嵌結構描述會擲回 <xref:System.Xml.Schema.XmlSchemaInferenceException>。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-136">For example, the following inline schema throws an <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span></span>  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a><span data-ttu-id="4c0b9-137">無法進一步調整的結構描述</span><span class="sxs-lookup"><span data-stu-id="4c0b9-137">Schemas that Cannot be Refined</span></span>  
 <span data-ttu-id="4c0b9-138">有些 W3C XML 結構描述建構在指定要調整的型別時會擲回例外狀況，則 XML 結構描述定義語言 (XSD) 結構描述 <xref:System.Xml.Schema.XmlSchemaInference> 處理序無法處理這類的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-138">There are W3C XML Schema constructs that the XML Schema definition language (XSD) schema <xref:System.Xml.Schema.XmlSchemaInference> process cannot handle if given a type to refine and cause an exception to be thrown.</span></span> <span data-ttu-id="4c0b9-139">最上層建構元不屬於序列的複雜型別即是一例。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-139">Such as a complex type whose top-level compositor is anything other than a sequence.</span></span> <span data-ttu-id="4c0b9-140">在結構描述物件模型 (SOM) 中，它會對應至 <xref:System.Xml.Schema.XmlSchemaComplexType> 屬性不屬於 <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> 之執行個體的 <xref:System.Xml.Schema.XmlSchemaSequence>。</span><span class="sxs-lookup"><span data-stu-id="4c0b9-140">In the Schema Object Model (SOM), this corresponds to an <xref:System.Xml.Schema.XmlSchemaComplexType> whose <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> property is not an instance of <xref:System.Xml.Schema.XmlSchemaSequence>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0b9-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c0b9-141">See Also</span></span>  
 <xref:System.Xml.Schema.XmlSchemaInference>  
 [<span data-ttu-id="4c0b9-142">XML 結構描述物件模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="4c0b9-142">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [<span data-ttu-id="4c0b9-143">推斷 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="4c0b9-143">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 [<span data-ttu-id="4c0b9-144">推斷結構描述節點類型和結構的規則</span><span class="sxs-lookup"><span data-stu-id="4c0b9-144">Rules for Inferring Schema Node Types and Structure</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)  
 [<span data-ttu-id="4c0b9-145">推斷簡單類型的規則</span><span class="sxs-lookup"><span data-stu-id="4c0b9-145">Rules for Inferring Simple Types</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
