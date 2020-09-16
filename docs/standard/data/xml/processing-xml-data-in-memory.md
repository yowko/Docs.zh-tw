---
title: 處理記憶體中的 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 0f64b53588e08520d38c05ec6060f9aef58bd7d6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556482"
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="64d68-102">處理記憶體中的 XML 資料</span><span class="sxs-lookup"><span data-stu-id="64d68-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="64d68-103">Microsoft .NET Framework 包含三種處理 XML 資料的模型：<xref:System.Xml.XmlDocument> 類別、<xref:System.Xml.XPath.XPathDocument> 類別，以及 [LINQ to XML (C#)](../../linq/linq-xml-overview.md) 和 [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="64d68-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span></span>  
  
 <span data-ttu-id="64d68-104"><xref:System.Xml.XmlDocument> 類別會實作 W3C 文件物件模型 (DOM) 層級 1 核心及核心 DOM 層級 2 建議事項。</span><span class="sxs-lookup"><span data-stu-id="64d68-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="64d68-105">DOM 是 XML 文件的記憶體中 (快取) 樹狀結構表示。</span><span class="sxs-lookup"><span data-stu-id="64d68-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="64d68-106">透過 <xref:System.Xml.XmlDocument> 及其相關類別，您可以建構 XML 文件、載入並存取資料、修改資料，以及儲存變更。</span><span class="sxs-lookup"><span data-stu-id="64d68-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="64d68-107"><xref:System.Xml.XPath.XPathDocument> 類別是唯讀的記憶體中資料存放區，以 XPath 資料模型為基礎。</span><span class="sxs-lookup"><span data-stu-id="64d68-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="64d68-108"><xref:System.Xml.XPath.XPathNavigator> 類別提供了數種可在唯讀 <xref:System.Xml.XPath.XPathDocument> 類別及 <xref:System.Xml.XmlDocument> 類別包含的 XML 文件中使用游標模型的編輯選項與巡覽功能。</span><span class="sxs-lookup"><span data-stu-id="64d68-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="64d68-109">[LINQ to XML](../../linq/linq-xml-overview.md) 是 .NET Framework 3.5 版中推出的模型，用來處理 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="64d68-109">[LINQ to XML](../../linq/linq-xml-overview.md) is a model introduced in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="64d68-110">它是利用 [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md) 的記憶體內部模型。</span><span class="sxs-lookup"><span data-stu-id="64d68-110">It's an in-memory model that leverages [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).</span></span> <span data-ttu-id="64d68-111">LINQ 會擴充 C# 和 Visual Basic 的語言語法，以提供新的查詢功能。</span><span class="sxs-lookup"><span data-stu-id="64d68-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64d68-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="64d68-112">In This Section</span></span>  
 [<span data-ttu-id="64d68-113">使用 DOM 模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="64d68-113">Process XML Data Using the DOM Model</span></span>](process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="64d68-114">討論如何使用 <xref:System.Xml.XmlDocument> 及其相關類別來處理 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="64d68-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="64d68-115">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="64d68-115">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="64d68-116">討論如何使用 <xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDocument> 及 <xref:System.Xml.XPath.XPathNavigator> 類別來處理 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="64d68-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="64d68-117">使用 LINQ to XML 處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="64d68-117">Process XML Data Using LINQ to XML</span></span>](process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="64d68-118">提供 LINQ to XML 的簡短概觀，並提供 LINQ to XML 文件的連結。</span><span class="sxs-lookup"><span data-stu-id="64d68-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="64d68-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="64d68-119">Related Sections</span></span>  
 [<span data-ttu-id="64d68-120">XML 檔和資料</span><span class="sxs-lookup"><span data-stu-id="64d68-120">XML Documents and Data</span></span>](index.md)
