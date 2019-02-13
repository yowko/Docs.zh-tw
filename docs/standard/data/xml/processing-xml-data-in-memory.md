---
title: 處理記憶體中的 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e6e89cafeb4cc580edb9630ba7415a669ea750c
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904418"
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="5a65e-102">處理記憶體中的 XML 資料</span><span class="sxs-lookup"><span data-stu-id="5a65e-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="5a65e-103">Microsoft .NET Framework 包含三種處理 XML 資料的模型：<xref:System.Xml.XmlDocument> 類別、<xref:System.Xml.XPath.XPathDocument> 類別及 [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)。</span><span class="sxs-lookup"><span data-stu-id="5a65e-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span>  
  
 <span data-ttu-id="5a65e-104">
  <xref:System.Xml.XmlDocument> 類別會實作 W3C 文件物件模型 (DOM) 層級 1 核心及核心 DOM 層級 2 建議事項。</span><span class="sxs-lookup"><span data-stu-id="5a65e-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="5a65e-105">DOM 是 XML 文件的記憶體中 (快取) 樹狀結構表示。</span><span class="sxs-lookup"><span data-stu-id="5a65e-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="5a65e-106">透過 <xref:System.Xml.XmlDocument> 及其相關類別，您可以建構 XML 文件、載入並存取資料、修改資料，以及儲存變更。</span><span class="sxs-lookup"><span data-stu-id="5a65e-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="5a65e-107">
  <xref:System.Xml.XPath.XPathDocument> 類別是唯讀的記憶體中資料存放區，以 XPath 資料模型為基礎。</span><span class="sxs-lookup"><span data-stu-id="5a65e-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="5a65e-108">
  <xref:System.Xml.XPath.XPathNavigator> 類別提供了數種可在唯讀 <xref:System.Xml.XPath.XPathDocument> 類別及 <xref:System.Xml.XmlDocument> 類別包含的 XML 文件中使用游標模型的編輯選項與巡覽功能。</span><span class="sxs-lookup"><span data-stu-id="5a65e-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="5a65e-109">[LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) 是 .NET Framework 3.5 版中推出的模型，用來處理 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="5a65e-109">[LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) is a model introduced in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="5a65e-110">它是利用 [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md) 的記憶體內部模型。</span><span class="sxs-lookup"><span data-stu-id="5a65e-110">It's an in-memory model that leverages [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).</span></span> <span data-ttu-id="5a65e-111">LINQ 會擴充 C# 和 Visual Basic 的語言語法，以提供新的查詢功能。</span><span class="sxs-lookup"><span data-stu-id="5a65e-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a65e-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="5a65e-112">In This Section</span></span>  
 [<span data-ttu-id="5a65e-113">使用 DOM 模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="5a65e-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="5a65e-114">討論如何使用 <xref:System.Xml.XmlDocument> 及其相關類別來處理 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="5a65e-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="5a65e-115">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="5a65e-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="5a65e-116">討論如何使用 <xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDocument> 及 <xref:System.Xml.XPath.XPathNavigator> 類別來處理 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="5a65e-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="5a65e-117">使用 LINQ to XML 處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="5a65e-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="5a65e-118">提供 LINQ to XML 的簡短概觀，並提供 LINQ to XML 文件的連結。</span><span class="sxs-lookup"><span data-stu-id="5a65e-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5a65e-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="5a65e-119">Related Sections</span></span>  
 [<span data-ttu-id="5a65e-120">XML 文件和資料</span><span class="sxs-lookup"><span data-stu-id="5a65e-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
