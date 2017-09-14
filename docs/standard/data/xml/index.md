---
title: "XML 文件和資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 88d993122bf1498b08d2e523a71f7f1bed505c9a
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="xml-documents-and-data"></a><span data-ttu-id="795a0-102">XML 文件和資料</span><span class="sxs-lookup"><span data-stu-id="795a0-102">XML Documents and Data</span></span>
<span data-ttu-id="795a0-103">.NET Framework 提供一組完整且整合的類別，好讓您輕鬆地建置可感知 XML 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="795a0-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="795a0-104">下列命名空間中的類別支援 XML 的剖析與撰寫、記憶體中 XML 資料的編輯、資料驗證和 XSLT 轉換。</span><span class="sxs-lookup"><span data-stu-id="795a0-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 <span data-ttu-id="795a0-105">如需完整清單，請參閱 [System.Xml 命名空間](http://msdn.microsoft.com/library/gg145036.aspx)網頁。</span><span class="sxs-lookup"><span data-stu-id="795a0-105">For a full list, see the [System.Xml Namespaces](http://msdn.microsoft.com/library/gg145036.aspx) webpage.</span></span>  
  
 <span data-ttu-id="795a0-106">這些命名空間中的類別支援全球資訊網協會 (W3C) 的建議。</span><span class="sxs-lookup"><span data-stu-id="795a0-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="795a0-107">例如: </span><span class="sxs-lookup"><span data-stu-id="795a0-107">For example:</span></span>  
  
-   <span data-ttu-id="795a0-108"><xref:System.Xml.XmlDocument?displayProperty=fullName> 類別會實作 [W3C 文件物件模型 (DOM) 層級 1 核心](http://www.w3.org/TR/REC-DOM-Level-1/)和 [DOM 層級 2 核心](http://www.w3.org/TR/DOM-Level-2-Core/)的建議事項。</span><span class="sxs-lookup"><span data-stu-id="795a0-108">The <xref:System.Xml.XmlDocument?displayProperty=fullName> class implements the [W3C Document Object Model (DOM) Level 1 Core](http://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](http://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>  
  
-   <span data-ttu-id="795a0-109"><xref:System.Xml.XmlReader?displayProperty=fullName> 和 <xref:System.Xml.XmlWriter?displayProperty=fullName> 類別支援 [W3C XML 1.0](http://www.w3.org/TR/2006/REC-xml-20060816/) 和 [XML 中的命名空間](http://www.w3.org/TR/REC-xml-names/)的建議事項。</span><span class="sxs-lookup"><span data-stu-id="795a0-109">The <xref:System.Xml.XmlReader?displayProperty=fullName> and <xref:System.Xml.XmlWriter?displayProperty=fullName> classes support the [W3C XML 1.0](http://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](http://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>  
  
-   <span data-ttu-id="795a0-110"><xref:System.Xml.Schema.XmlSchemaSet?displayProperty=fullName> 類別中的結構描述支援 [W3C XML 結構描述第一部分：結構](http://www.w3.org/TR/xmlschema-1/)和 [XML 結構描述第二部分：資料類型](http://www.w3.org/TR/xmlschema-2/)的建議事項。</span><span class="sxs-lookup"><span data-stu-id="795a0-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=fullName> class support the [W3C XML Schema Part 1: Structures](http://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](http://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
-   <span data-ttu-id="795a0-111"><xref:System.Xml.Xsl?displayProperty=fullName> 命名空間中的類別支援符合 [W3C XSLT 1.0](http://www.w3.org/TR/xslt) 建議事項的 XSLT 轉換。</span><span class="sxs-lookup"><span data-stu-id="795a0-111">Classes in the <xref:System.Xml.Xsl?displayProperty=fullName> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](http://www.w3.org/TR/xslt) recommendation.</span></span>  
  
 <span data-ttu-id="795a0-112">.NET Framework 中的 XML 類別提供以下優點：</span><span class="sxs-lookup"><span data-stu-id="795a0-112">The XML classes in the .NET Framework provide these benefits:</span></span>  
  
-   <span data-ttu-id="795a0-113">**生產力。**</span><span class="sxs-lookup"><span data-stu-id="795a0-113">**Productivity.**</span></span> <span data-ttu-id="795a0-114">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) 可輕鬆地透過 XML 編寫程式，並提供類似於 SQL 的查詢體驗。</span><span class="sxs-lookup"><span data-stu-id="795a0-114">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>  
  
-   <span data-ttu-id="795a0-115">**擴充性。**</span><span class="sxs-lookup"><span data-stu-id="795a0-115">**Extensibility.**</span></span> <span data-ttu-id="795a0-116">.NET Framework 中的 XML 類別可利用抽象基底類別和虛擬方法進行擴充。</span><span class="sxs-lookup"><span data-stu-id="795a0-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="795a0-117">例如，您可以建立將快取資料流儲存在本機磁碟之 <xref:System.Xml.XmlUrlResolver> 類別的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="795a0-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>  
  
-   <span data-ttu-id="795a0-118">**可外掛式架構。**</span><span class="sxs-lookup"><span data-stu-id="795a0-118">**Pluggable architecture.**</span></span> <span data-ttu-id="795a0-119">.NET Framework 提供的架構可讓元件在其中彼此互相利用，而且資料也可以在不同的元件之間進行資料流處理。</span><span class="sxs-lookup"><span data-stu-id="795a0-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="795a0-120">例如，類似 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 的資料存放區可透過 <xref:System.Xml.Xsl.XslCompiledTransform> 類別進行轉換，接著輸出可以資料流方式傳輸至另一個存放區，或當做 Web 服務的資料流傳回。</span><span class="sxs-lookup"><span data-stu-id="795a0-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>  
  
-   <span data-ttu-id="795a0-121">**效能。**</span><span class="sxs-lookup"><span data-stu-id="795a0-121">**Performance.**</span></span> <span data-ttu-id="795a0-122">為了提高應用程式效能，.NET Framework 中的某些 XML 類別可支援資料流形式的模型，並擁有下列特性：</span><span class="sxs-lookup"><span data-stu-id="795a0-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>  
  
    -   <span data-ttu-id="795a0-123">順向的最小快取、提取模型剖析 (<xref:System.Xml.XmlReader>)。</span><span class="sxs-lookup"><span data-stu-id="795a0-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="795a0-124">順向驗證 (<xref:System.Xml.XmlReader>)。</span><span class="sxs-lookup"><span data-stu-id="795a0-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="795a0-125">資料指標樣式導覽，可將節點的建立最小化為單一虛擬節點，同時提供文件的隨機存取 (<xref:System.Xml.XPath.XPathNavigator>)。</span><span class="sxs-lookup"><span data-stu-id="795a0-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>  
  
     <span data-ttu-id="795a0-126">為了要在每次需要 XSLT 處理時都提高效能，您可以使用 <xref:System.Xml.XPath.XPathDocument> 類別，它是最佳化的唯讀 XPath 查詢存放區，其設計目的是要與 <xref:System.Xml.Xsl.XslCompiledTransform> 類別有效率地一起運作。</span><span class="sxs-lookup"><span data-stu-id="795a0-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
-   <span data-ttu-id="795a0-127">**與 ADO.NET 整合。**</span><span class="sxs-lookup"><span data-stu-id="795a0-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="795a0-128">XML 類別與 [ADO.NET](../../../../docs/framework/data/adonet/index.md) 緊密整合在一起，可讓關聯式資料和 XML 結合在一起。</span><span class="sxs-lookup"><span data-stu-id="795a0-128">The XML classes and [ADO.NET](../../../../docs/framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="795a0-129"><xref:System.Data.DataSet> 類別是一項擷取自資料庫的記憶體中資料快取。</span><span class="sxs-lookup"><span data-stu-id="795a0-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="795a0-130"><xref:System.Data.DataSet> 類別可使用 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 類別來讀取及寫入 XML，將其內部的關聯式結構描述結構保存為 XML 結構描述 (XSD)，還可以推斷 XML 文件的結構描述結構。</span><span class="sxs-lookup"><span data-stu-id="795a0-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="795a0-131">本章節內容</span><span class="sxs-lookup"><span data-stu-id="795a0-131">In This Section</span></span>  
 [<span data-ttu-id="795a0-132">XML 處理選項</span><span class="sxs-lookup"><span data-stu-id="795a0-132">XML Processing Options</span></span>](../../../../docs/standard/data/xml/xml-processing-options.md)  
 <span data-ttu-id="795a0-133">討論用來處理 XML 資料的選項。</span><span class="sxs-lookup"><span data-stu-id="795a0-133">Discusses options for processing XML data.</span></span>  
  
 [<span data-ttu-id="795a0-134">處理記憶體中的 XML 資料</span><span class="sxs-lookup"><span data-stu-id="795a0-134">Processing XML Data In-Memory</span></span>](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 <span data-ttu-id="795a0-135">討論用來處理記憶體中 XML 資料的三個模型。</span><span class="sxs-lookup"><span data-stu-id="795a0-135">Discusses the three models for processing XML data in-memory.</span></span> <span data-ttu-id="795a0-136">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)、<xref:System.Xml.XmlDocument> 類別 (根據 W3C 文件物件模型) 和 <xref:System.Xml.XPath.XPathDocument> 類別 (根據 XPath 資料模型)。</span><span class="sxs-lookup"><span data-stu-id="795a0-136">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>  
  
 [<span data-ttu-id="795a0-137">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="795a0-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 <span data-ttu-id="795a0-138">說明如何使用 XSLT 處理器。</span><span class="sxs-lookup"><span data-stu-id="795a0-138">Describes how to use the XSLT processor.</span></span>  
  
 [<span data-ttu-id="795a0-139">XML 結構描述物件模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="795a0-139">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="795a0-140">說明藉由提供 <xref:System.Xml.Schema.XmlSchema> 類別來載入和編輯結構描述，用以建置及管理 XML 結構描述 (XSD) 的類別。</span><span class="sxs-lookup"><span data-stu-id="795a0-140">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>  
  
 [<span data-ttu-id="795a0-141">XML 與關聯式資料和 ADO.NET 互相整合</span><span class="sxs-lookup"><span data-stu-id="795a0-141">XML Integration with Relational Data and ADO.NET</span></span>](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 <span data-ttu-id="795a0-142">說明 .NET Framework 如何透過 <xref:System.Data.DataSet> 物件和 <xref:System.Xml.XmlDataDocument> 物件，啟用即時、同步方式來存取關聯式及階層式表示的資料。</span><span class="sxs-lookup"><span data-stu-id="795a0-142">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>  
  
 [<span data-ttu-id="795a0-143">管理 XML 文件中的命名空間</span><span class="sxs-lookup"><span data-stu-id="795a0-143">Managing Namespaces in an XML Document</span></span>](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 <span data-ttu-id="795a0-144">說明 <xref:System.Xml.XmlNamespaceManager> 類別如何用來儲存及維護命名空間資訊。</span><span class="sxs-lookup"><span data-stu-id="795a0-144">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>  
  
 [<span data-ttu-id="795a0-145">System.Xml 類別中的類型支援</span><span class="sxs-lookup"><span data-stu-id="795a0-145">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 <span data-ttu-id="795a0-146">說明 XML 資料類型如何對應到 CLR 類型、如何轉換 XML 資料類型，以及 <xref:System.Xml> 類別中的其他類型支援功能。</span><span class="sxs-lookup"><span data-stu-id="795a0-146">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="795a0-147">相關章節</span><span class="sxs-lookup"><span data-stu-id="795a0-147">Related Sections</span></span>  
 [<span data-ttu-id="795a0-148">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="795a0-148">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="795a0-149">提供如何使用 ADO.NET 來存取資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="795a0-149">Provides information on how to access data using ADO.NET.</span></span>  
  
 [<span data-ttu-id="795a0-150">安全性</span><span class="sxs-lookup"><span data-stu-id="795a0-150">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="795a0-151">提供 .NET Framework 安全性系統的概觀。</span><span class="sxs-lookup"><span data-stu-id="795a0-151">Provides an overview of the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="795a0-152">XML 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="795a0-152">XML Developer Center</span></span>](http://go.microsoft.com/fwlink/?linkid=42458)  
 <span data-ttu-id="795a0-153">為 XML 開發人員提供其他技術資訊、下載、新聞群組及其他資源。</span><span class="sxs-lookup"><span data-stu-id="795a0-153">Provides additional technical information, downloads, newsgroups, and other resources for XML developers.</span></span>

