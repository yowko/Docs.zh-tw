---
title: 使用 XML 結構描述
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83fddd00f44b184fa066f6c47b90b01fac7ef7bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-xml-schemas"></a><span data-ttu-id="3d0d2-102">使用 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="3d0d2-102">Working with XML Schemas</span></span>
<span data-ttu-id="3d0d2-103">若要定義 XML 文件的結構及其項目關聯性、資料類型及內容條件約束，可以使用文件類型定義 (DTD) 或 XML 結構描述定義語言 (XSD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-103">To define the structure of an XML document, as well as its element relationships, data types, and content constraints, you use a document type definition (DTD) or XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="3d0d2-104">儘管當 XML 文件滿足全球資訊網協會 (W3C) 可延伸標記語言 (XML) 1.0 版建議事項定義的所有語法要求時，會將其視為格式正確，但是它必須格式正確且符合由其 DTD 或結構描述所定義的條件約束才會被視為有效。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-104">Although an XML document is considered to be well-formed if it meets all the syntactical requirements defined by the World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0 Recommendation, it is not considered valid unless it is both well-formed and conforms to the constraints defined by its DTD or schema.</span></span> <span data-ttu-id="3d0d2-105">因此，儘管所有有效 XML 文件的格式都正確，但是並非所有格式正確的 XML 文件都有效。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-105">Therefore, although all valid XML documents are well-formed, not all well-formed XML documents are valid.</span></span>  
  
 <span data-ttu-id="3d0d2-106">如需 XML 的詳細資訊，請參閱 [W3C XML 1.0 建議事項](https://www.w3.org/TR/REC-xml/) (英文)。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-106">For more information about XML, see the [W3C XML 1.0 Recommendation](https://www.w3.org/TR/REC-xml/).</span></span> <span data-ttu-id="3d0d2-107">如需 XML 結構描述的詳細資訊，請參閱 [W3C XML 結構描述第一部：結構建議事項](https://www.w3.org/TR/xmlschema-1/)及 [W3C XML 結構描述第二部：資料型別建議事項](https://www.w3.org/TR/xmlschema-2/)的建議。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-107">For more information about XML Schema, see the [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) and the [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d0d2-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="3d0d2-108">In This Section</span></span>  
 [<span data-ttu-id="3d0d2-109">XML 結構描述物件模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="3d0d2-109">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="3d0d2-110">討論 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的結構描述物件模型 (SOM)，其提供了一組類別，可讓您從檔案讀取結構描述定義語言 (XSD) 結構描述，或以程式設計方式建立記憶體中結構描述。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-110">Discusses the Schema Object Model (SOM) in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that provides a set of classes that allows you to read a Schema definition language (XSD) schema from a file or programmatically create a schema in-memory.</span></span>  
  
 [<span data-ttu-id="3d0d2-111">用於結構描述編譯的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3d0d2-111">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 <span data-ttu-id="3d0d2-112">討論 <xref:System.Xml.Schema.XmlSchemaSet> 類別，其為可儲存及驗證 XSD 結構描述的快取。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-112">Discusses the <xref:System.Xml.Schema.XmlSchemaSet> class that is a cache where XSD schemas can be stored and validated.</span></span>  
  
 [<span data-ttu-id="3d0d2-113">XmlSchemaValidator 推入型驗證</span><span class="sxs-lookup"><span data-stu-id="3d0d2-113">XmlSchemaValidator Push-Based Validation</span></span>](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 <span data-ttu-id="3d0d2-114">討論 <xref:System.Xml.Schema.XmlSchemaValidator> 類別，其可提供有效的高效能機制，來針對 XSD 結構描述並以推入式方式驗證 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-114">Discusses the <xref:System.Xml.Schema.XmlSchemaValidator> class that provides an efficient, high-performance mechanism to validate XML data against XSD schemas in a push-based manner.</span></span>  
  
 [<span data-ttu-id="3d0d2-115">推斷 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="3d0d2-115">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 <span data-ttu-id="3d0d2-116">討論如何使用 <xref:System.Xml.Schema.XmlSchemaInference> 類別，從 XML 文件的結構推斷 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-116">Discusses how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XSD schema from the structure of an XML document.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3d0d2-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="3d0d2-117">Reference</span></span>  
 <span data-ttu-id="3d0d2-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="3d0d2-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3d0d2-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="3d0d2-119">Related Sections</span></span>  
 [<span data-ttu-id="3d0d2-120">驗證 DOM 中的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="3d0d2-120">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 <span data-ttu-id="3d0d2-121">討論如何驗證文件物件模型 (DOM) 中的 XML。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-121">Discusses how to validate the XML in the Document Object Model (DOM).</span></span> <span data-ttu-id="3d0d2-122">您可以在將 XML 載入至 DOM 時進行驗證，或者驗證 DOM 中先前未驗證的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-122">You can validate the XML as it is loaded into the DOM, or validate a previously unvalidated XML document in the DOM.</span></span>  
  
 [<span data-ttu-id="3d0d2-123">使用 XPathNavigator 進行結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="3d0d2-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="3d0d2-124">討論如何對使用 <xref:System.Xml.XPath.XPathNavigator> 類別巡覽及編輯的 XML 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="3d0d2-124">Discusses how to validate XML being navigated and edited using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
