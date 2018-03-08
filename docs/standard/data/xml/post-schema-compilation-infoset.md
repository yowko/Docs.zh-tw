---
title: "後結構描述編譯資訊集"
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
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5b55271306abdca95694bd8fb2ebb6e538d060ae
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2018
---
# <a name="post-schema-compilation-infoset"></a><span data-ttu-id="6e44d-102">後結構描述編譯資訊集</span><span class="sxs-lookup"><span data-stu-id="6e44d-102">Post-Schema Compilation Infoset</span></span>
<span data-ttu-id="6e44d-103">[全球資訊網協會 (W3C) XML 結構描述建議事項](https://www.w3.org/XML/Schema) (英文) 中討論為了進行前置結構描述驗證和後置結構描述編譯所必須公開的資訊集 (infoset)。</span><span class="sxs-lookup"><span data-stu-id="6e44d-103">The [World Wide Web Consortium (W3C) XML Schema Recommendation](https://www.w3.org/XML/Schema) discusses the information set (infoset) that must be exposed for pre-schema validation and post-schema compilation.</span></span> <span data-ttu-id="6e44d-104">XML 結構描述物件模型 (SOM) 會在呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法之前及之後，檢視此公開資訊集。</span><span class="sxs-lookup"><span data-stu-id="6e44d-104">The XML Schema Object Model (SOM) views this exposure before and after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span>  
  
 <span data-ttu-id="6e44d-105">前結構描述驗證資訊集建置於結構描述的編輯期間。</span><span class="sxs-lookup"><span data-stu-id="6e44d-105">The pre-schema validation infoset is built during the editing of the schema.</span></span> <span data-ttu-id="6e44d-106">後結構描述編譯資訊集是在結構描述的編譯期間，並於呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法之後產生的，而且會公開為屬性。</span><span class="sxs-lookup"><span data-stu-id="6e44d-106">The post-schema compilation infoset is generated after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called, during compilation of the schema, and is exposed as properties.</span></span>  
  
 <span data-ttu-id="6e44d-107">SOM 是表示前結構描述驗證及後結構描述編譯資訊集的物件模型，它是由 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的類別組成。</span><span class="sxs-lookup"><span data-stu-id="6e44d-107">The SOM is the object model that represents the pre-schema validation and post-schema compilation infosets; it consists of the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="6e44d-108"><xref:System.Xml.Schema> 命名空間中類別的所有讀取及寫入屬性都屬於前結構描述驗證資訊集，而 <xref:System.Xml.Schema> 命名空間中類別的所有唯讀屬性都屬於後結構描述編譯資訊集。</span><span class="sxs-lookup"><span data-stu-id="6e44d-108">All read and write properties of classes in the <xref:System.Xml.Schema> namespace belong to the pre-schema validation infoset, while all read-only properties of classes in the <xref:System.Xml.Schema> namespace belong to the post-schema compilation infoset.</span></span> <span data-ttu-id="6e44d-109">下列屬性是此規則的例外，它們同時屬於前結構描述驗證資訊集及後結構描述編譯資訊集的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e44d-109">The exception to this rule are the following properties, which are both pre-schema validation infoset and post-schema compilation infoset properties.</span></span>  
  
|<span data-ttu-id="6e44d-110">類別</span><span class="sxs-lookup"><span data-stu-id="6e44d-110">Class</span></span>|<span data-ttu-id="6e44d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6e44d-111">Property</span></span>|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<span data-ttu-id="6e44d-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="6e44d-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<span data-ttu-id="6e44d-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span><span class="sxs-lookup"><span data-stu-id="6e44d-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 <span data-ttu-id="6e44d-114">例如，<xref:System.Xml.Schema.XmlSchemaElement> 及 <xref:System.Xml.Schema.XmlSchemaComplexType> 類別都具有 `BlockResolved` 及 `FinalResolved` 屬性。</span><span class="sxs-lookup"><span data-stu-id="6e44d-114">For example, the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaComplexType> classes both have `BlockResolved` and `FinalResolved` properties.</span></span> <span data-ttu-id="6e44d-115">在編譯及驗證結構描述之後，這些屬性可用於儲存 `Block` 及 `Final` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="6e44d-115">These properties are used to hold the values for the `Block` and `Final` properties after the schema has been compiled and validated.</span></span> <span data-ttu-id="6e44d-116">`BlockResolved` 及 `FinalResolved` 是唯讀屬性，其屬於後結構描述編譯資訊集。</span><span class="sxs-lookup"><span data-stu-id="6e44d-116">`BlockResolved` and `FinalResolved` are read-only properties that are part of the post-schema compilation infoset.</span></span>  
  
 <span data-ttu-id="6e44d-117">下列範例顯示驗證結構描述之後，<xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 類別集的 <xref:System.Xml.Schema.XmlSchemaElement> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6e44d-117">The following example shows the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> class set after validating the schema.</span></span> <span data-ttu-id="6e44d-118">驗證之前，該屬性包含 `null` 參考，且 <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 是設為所討論之型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="6e44d-118">Before validation, the property contains a `null` reference, and the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is set to the name of the type in question.</span></span> <span data-ttu-id="6e44d-119">驗證之後，<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 會解析為有效型別，而且型別物件可透過 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 屬性來使用。</span><span class="sxs-lookup"><span data-stu-id="6e44d-119">After validation, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is resolved to a valid type, and the type object is available through the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property.</span></span>  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6e44d-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="6e44d-120">See Also</span></span>  
 [<span data-ttu-id="6e44d-121">XML 結構描述物件模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="6e44d-121">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
