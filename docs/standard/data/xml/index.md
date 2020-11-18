---
title: XML 文件和資料
ms.date: 03/30/2017
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: db122d1f2fa4ad192bbcc92769873850916a4220
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830242"
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="59754-102">XML 文件和資料</span><span class="sxs-lookup"><span data-stu-id="59754-102">XML Documents and Data</span></span>

<span data-ttu-id="59754-103">.NET Framework 提供一組完整且整合的類別，好讓您輕鬆地建置可感知 XML 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="59754-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="59754-104">下列命名空間中的類別支援 XML 的剖析與撰寫、記憶體中 XML 資料的編輯、資料驗證和 XSLT 轉換。</span><span class="sxs-lookup"><span data-stu-id="59754-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

<span data-ttu-id="59754-105">如需完整清單，請在 [.NET API 瀏覽器](../../../../api/index.md?term=system.xml)搜尋 "System.Xml"。</span><span class="sxs-lookup"><span data-stu-id="59754-105">For a full list, search for "System.Xml" on the [.NET API browser](../../../../api/index.md?term=system.xml).</span></span>

<span data-ttu-id="59754-106">這些命名空間中的類別支援全球資訊網協會 (W3C) 的建議。</span><span class="sxs-lookup"><span data-stu-id="59754-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="59754-107">例如：</span><span class="sxs-lookup"><span data-stu-id="59754-107">For example:</span></span>

- <span data-ttu-id="59754-108"><xref:System.Xml.XmlDocument?displayProperty=nameWithType> 類別會實作 [W3C 文件物件模型 (DOM) 層級 1 核心](https://www.w3.org/TR/REC-DOM-Level-1/)和 [DOM 層級 2 核心](https://www.w3.org/TR/DOM-Level-2-Core/)的建議事項。</span><span class="sxs-lookup"><span data-stu-id="59754-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>

- <span data-ttu-id="59754-109"><xref:System.Xml.XmlReader?displayProperty=nameWithType> 和 <xref:System.Xml.XmlWriter?displayProperty=nameWithType> 類別支援 [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) 和 [XML 中的命名空間](https://www.w3.org/TR/REC-xml-names/)的建議事項。</span><span class="sxs-lookup"><span data-stu-id="59754-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>

- <span data-ttu-id="59754-110"><xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> 類別中的結構描述支援 [W3C XML 結構描述第一部分：結構](https://www.w3.org/TR/xmlschema-1/)和 [XML 結構描述第二部分：資料類型](https://www.w3.org/TR/xmlschema-2/)的建議事項。</span><span class="sxs-lookup"><span data-stu-id="59754-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>

- <span data-ttu-id="59754-111"><xref:System.Xml.Xsl?displayProperty=nameWithType> 命名空間中的類別支援符合 [W3C XSLT 1.0](https://www.w3.org/TR/xslt) 建議事項的 XSLT 轉換。</span><span class="sxs-lookup"><span data-stu-id="59754-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](https://www.w3.org/TR/xslt) recommendation.</span></span>

<span data-ttu-id="59754-112">.NET Framework 中的 XML 類別提供以下優點：</span><span class="sxs-lookup"><span data-stu-id="59754-112">The XML classes in the .NET Framework provide these benefits:</span></span>

- <span data-ttu-id="59754-113">**生產力。**</span><span class="sxs-lookup"><span data-stu-id="59754-113">**Productivity.**</span></span> <span data-ttu-id="59754-114">[LINQ to XML (C#)](../../linq/linq-xml-overview.md) 和 [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md) 可輕鬆地透過 XML 編寫程式，並提供類似於 SQL 的查詢體驗。</span><span class="sxs-lookup"><span data-stu-id="59754-114">[LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>

- <span data-ttu-id="59754-115">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="59754-115">**Extensibility.**</span></span> <span data-ttu-id="59754-116">.NET Framework 中的 XML 類別可利用抽象基底類別和虛擬方法進行擴充。</span><span class="sxs-lookup"><span data-stu-id="59754-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="59754-117">例如，您可以建立將快取資料流儲存在本機磁碟之 <xref:System.Xml.XmlUrlResolver> 類別的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="59754-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>

- <span data-ttu-id="59754-118">**可外掛式架構。**</span><span class="sxs-lookup"><span data-stu-id="59754-118">**Pluggable architecture.**</span></span> <span data-ttu-id="59754-119">.NET Framework 提供的架構可讓元件在其中彼此互相利用，而且資料也可以在不同的元件之間進行資料流處理。</span><span class="sxs-lookup"><span data-stu-id="59754-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="59754-120">例如，類似 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 的資料存放區可透過 <xref:System.Xml.Xsl.XslCompiledTransform> 類別進行轉換，接著輸出可以資料流方式傳輸至另一個存放區，或當做 Web 服務的資料流傳回。</span><span class="sxs-lookup"><span data-stu-id="59754-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>

- <span data-ttu-id="59754-121">**效能。**</span><span class="sxs-lookup"><span data-stu-id="59754-121">**Performance.**</span></span> <span data-ttu-id="59754-122">為了提高應用程式效能，.NET Framework 中的某些 XML 類別可支援資料流形式的模型，並擁有下列特性：</span><span class="sxs-lookup"><span data-stu-id="59754-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>

  - <span data-ttu-id="59754-123">順向的最小快取、提取模型剖析 (<xref:System.Xml.XmlReader>)。</span><span class="sxs-lookup"><span data-stu-id="59754-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="59754-124">順向驗證 (<xref:System.Xml.XmlReader>)。</span><span class="sxs-lookup"><span data-stu-id="59754-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="59754-125">資料指標樣式導覽，可將節點的建立最小化為單一虛擬節點，同時提供文件的隨機存取 (<xref:System.Xml.XPath.XPathNavigator>)。</span><span class="sxs-lookup"><span data-stu-id="59754-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>

  <span data-ttu-id="59754-126">為了要在每次需要 XSLT 處理時都提高效能，您可以使用 <xref:System.Xml.XPath.XPathDocument> 類別，它是最佳化的唯讀 XPath 查詢存放區，其設計目的是要與 <xref:System.Xml.Xsl.XslCompiledTransform> 類別有效率地一起運作。</span><span class="sxs-lookup"><span data-stu-id="59754-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

- <span data-ttu-id="59754-127">**與 ADO.NET 整合。**</span><span class="sxs-lookup"><span data-stu-id="59754-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="59754-128">XML 類別與 [ADO.NET](../../../framework/data/adonet/index.md) 緊密整合在一起，可讓關聯式資料和 XML 結合在一起。</span><span class="sxs-lookup"><span data-stu-id="59754-128">The XML classes and [ADO.NET](../../../framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="59754-129"><xref:System.Data.DataSet> 類別是一項擷取自資料庫的記憶體中資料快取。</span><span class="sxs-lookup"><span data-stu-id="59754-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="59754-130"><xref:System.Data.DataSet> 類別可使用 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 類別來讀取及寫入 XML，將其內部的關聯式結構描述結構保存為 XML 結構描述 (XSD)，還可以推斷 XML 文件的結構描述結構。</span><span class="sxs-lookup"><span data-stu-id="59754-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="59754-131">本節內容</span><span class="sxs-lookup"><span data-stu-id="59754-131">In This Section</span></span>

<span data-ttu-id="59754-132">[XML 處理選項](xml-processing-options.md) 討論用來處理 XML 資料的選項。</span><span class="sxs-lookup"><span data-stu-id="59754-132">[XML Processing Options](xml-processing-options.md) Discusses options for processing XML data.</span></span>

<span data-ttu-id="59754-133">[處理記憶體中的 XML 資料](processing-xml-data-in-memory.md) 討論用來處理記憶體中 XML 資料的三個模型： [LINQ to XML (c # ) ](../../linq/linq-xml-overview.md) 和 [LINQ to XML (](../../linq/linq-xml-overview.md)VISUAL BASIC) 、 <xref:System.Xml.XmlDocument> 根據 W3C (檔物件模型的類別) ，以及 <xref:System.Xml.XPath.XPathDocument> 根據 XPath 資料模型 (的類別) 。</span><span class="sxs-lookup"><span data-stu-id="59754-133">[Processing XML Data In-Memory](processing-xml-data-in-memory.md) Discusses the three models for processing XML data in-memory: [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>

<span data-ttu-id="59754-134">[XSLT 轉換](xslt-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="59754-134">[XSLT Transformations](xslt-transformations.md)</span></span>\
<span data-ttu-id="59754-135">說明如何使用 XSLT 處理器。</span><span class="sxs-lookup"><span data-stu-id="59754-135">Describes how to use the XSLT processor.</span></span>

<span data-ttu-id="59754-136">[XML 架構物件模型 (SOM) ](xml-schema-object-model-som.md)</span><span class="sxs-lookup"><span data-stu-id="59754-136">[XML Schema Object Model (SOM)](xml-schema-object-model-som.md)</span></span>\
<span data-ttu-id="59754-137">說明藉由提供 <xref:System.Xml.Schema.XmlSchema> 類別來載入和編輯結構描述，用以建置及管理 XML 結構描述 (XSD) 的類別。</span><span class="sxs-lookup"><span data-stu-id="59754-137">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>

<span data-ttu-id="59754-138">[XML 與關聯式資料和 ADO.NET 的整合](xml-integration-with-relational-data-and-adonet.md)</span><span class="sxs-lookup"><span data-stu-id="59754-138">[XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md)</span></span>\
<span data-ttu-id="59754-139">說明 .NET Framework 如何透過 <xref:System.Data.DataSet> 物件和 <xref:System.Xml.XmlDataDocument> 物件，啟用即時、同步方式來存取關聯式及階層式表示的資料。</span><span class="sxs-lookup"><span data-stu-id="59754-139">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>

<span data-ttu-id="59754-140">[管理 XML 檔中的命名空間](managing-namespaces-in-an-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="59754-140">[Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md)</span></span>\
<span data-ttu-id="59754-141">說明 <xref:System.Xml.XmlNamespaceManager> 類別如何用來儲存及維護命名空間資訊。</span><span class="sxs-lookup"><span data-stu-id="59754-141">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>

<span data-ttu-id="59754-142">[System.Xml 類別中的類型支援](type-support-in-the-system-xml-classes.md)</span><span class="sxs-lookup"><span data-stu-id="59754-142">[Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md)</span></span>\
<span data-ttu-id="59754-143">說明 XML 資料類型如何對應到 CLR 類型、如何轉換 XML 資料類型，以及 <xref:System.Xml> 類別中的其他類型支援功能。</span><span class="sxs-lookup"><span data-stu-id="59754-143">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>

## <a name="related-sections"></a><span data-ttu-id="59754-144">相關章節</span><span class="sxs-lookup"><span data-stu-id="59754-144">Related Sections</span></span>

<span data-ttu-id="59754-145">[ADO.NET](../../../framework/data/adonet/index.md)</span><span class="sxs-lookup"><span data-stu-id="59754-145">[ADO.NET](../../../framework/data/adonet/index.md)</span></span>\
<span data-ttu-id="59754-146">提供如何使用 ADO.NET 來存取資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="59754-146">Provides information on how to access data using ADO.NET.</span></span>

<span data-ttu-id="59754-147">[安全](../../security/index.md)</span><span class="sxs-lookup"><span data-stu-id="59754-147">[Security](../../security/index.md)</span></span>\
<span data-ttu-id="59754-148">提供 .NET Framework 安全性系統的概觀。</span><span class="sxs-lookup"><span data-stu-id="59754-148">Provides an overview of the .NET Framework security system.</span></span>
