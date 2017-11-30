---
title: "推斷 XML 結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b18e7ffd-3c04-482d-9934-ba2f6a59b2c9
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb4994608b4f85c8ad4eeb3113b36729156a1a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-an-xml-schema"></a><span data-ttu-id="1235e-102">推斷 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="1235e-102">Inferring an XML Schema</span></span>
<span data-ttu-id="1235e-103">說明如何使用結構描述物件模型 (SOM) <xref:System.Xml.Schema.XmlSchemaInference> 類別從 XML 文件結構來推斷 XML 結構描述定義語言 (XSD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="1235e-103">Describes how to use the Schema Object Model (SOM) <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XML Schema definition language (XSD) schema from the structure of an XML document.</span></span>  
  
 <span data-ttu-id="1235e-104"><xref:System.Xml.Schema.XmlSchemaInference> 命名空間中的結構描述物件模型 (SOM) <xref:System.Xml.Schema?displayProperty=nameWithType> 類別可讓您從 XML 文件的結構來推斷 XML 結構描述定義語言 (XSD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="1235e-104">The Schema Object Model (SOM) <xref:System.Xml.Schema.XmlSchemaInference> class in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace allows you to infer an XML Schema definition language (XSD) schema from the structure of an XML document.</span></span> <span data-ttu-id="1235e-105"><xref:System.Xml.Schema.XmlSchemaInference> 類別會輸出可驗證 XML 文件的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="1235e-105">The <xref:System.Xml.Schema.XmlSchemaInference> class outputs an XML schema that can validate the XML document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1235e-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="1235e-106">In This Section</span></span>  
 [<span data-ttu-id="1235e-107">從 XML 文件推斷結構描述</span><span class="sxs-lookup"><span data-stu-id="1235e-107">Inferring Schemas from XML Documents</span></span>](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
 <span data-ttu-id="1235e-108">說明如何使用 <xref:System.Xml.Schema.XmlSchemaInference> 類別來從 XML 文件的結構推斷結構描述。</span><span class="sxs-lookup"><span data-stu-id="1235e-108">Describes how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer a schema from the structure of an XML document.</span></span>  
  
 [<span data-ttu-id="1235e-109">推斷結構描述節點型別與結構的規則</span><span class="sxs-lookup"><span data-stu-id="1235e-109">Rules for Inferring Schema Node Types and Structure</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)  
 <span data-ttu-id="1235e-110">說明推斷程序如何將 XML 文件中所發現的節點型別轉譯為結構描述結構。</span><span class="sxs-lookup"><span data-stu-id="1235e-110">Describes how the inference process translates the node types encountered in an XML document into a schema structure.</span></span>  
  
 [<span data-ttu-id="1235e-111">推斷簡單型別的規則</span><span class="sxs-lookup"><span data-stu-id="1235e-111">Rules for Inferring Simple Types</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)  
 <span data-ttu-id="1235e-112">說明 <xref:System.Xml.Schema.XmlSchemaInference> 類別如何推斷屬性和項目的資料型別。</span><span class="sxs-lookup"><span data-stu-id="1235e-112">Describes how the <xref:System.Xml.Schema.XmlSchemaInference> class infers the data type for attributes and elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1235e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1235e-113">See Also</span></span>  
 [<span data-ttu-id="1235e-114">XML 結構描述物件模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="1235e-114">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [<span data-ttu-id="1235e-115">從 XML 文件推斷結構描述</span><span class="sxs-lookup"><span data-stu-id="1235e-115">Inferring Schemas from XML Documents</span></span>](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
 [<span data-ttu-id="1235e-116">推斷結構描述節點型別與結構的規則</span><span class="sxs-lookup"><span data-stu-id="1235e-116">Rules for Inferring Schema Node Types and Structure</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
