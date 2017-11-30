---
title: "使用 XPath 資料模型處理 XML 資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d2c8db03d494be13a93df06a359e4e4294c22a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="process-xml-data-using-the-xpath-data-model"></a><span data-ttu-id="a5a42-102">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="a5a42-102">Process XML Data Using the XPath Data Model</span></span>
<span data-ttu-id="a5a42-103"><xref:System.Xml?displayProperty=nameWithType> 命名空間會使用 <xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XPath.XPathDocument> 類別，以程式設計方式來表示 XML 文件、片段、節點或記憶體中的節點集。</span><span class="sxs-lookup"><span data-stu-id="a5a42-103">The <xref:System.Xml?displayProperty=nameWithType> namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets in-memory, using the <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> classes.</span></span>  
  
 <span data-ttu-id="a5a42-104"><xref:System.Xml.XPath.XPathDocument> 類別會使用 XPath 資料模型，以快速且唯讀的方式來表示記憶體中的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a5a42-104">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="a5a42-105"><xref:System.Xml.XmlDocument> 類別則會實作 W3C 文件物件模型 (DOM) 層級 1 核心及核心 DOM 層級 2，來呈現記憶體中可編輯的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a5a42-105">The <xref:System.Xml.XmlDocument> class provides an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="a5a42-106">這兩個類別都會實作 <xref:System.Xml.XPath.IXPathNavigable> 介面，並傳回用於選取、評估、巡覽，以及可在某些情況下編輯基礎 XML 資料的 <xref:System.Xml.XPath.XPathNavigator> 物件。</span><span class="sxs-lookup"><span data-stu-id="a5a42-106">Both classes implement the <xref:System.Xml.XPath.IXPathNavigable> interface and return an <xref:System.Xml.XPath.XPathNavigator> object used to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="a5a42-107">下列各節將根據會傳回 <xref:System.Xml.XPath.XPathNavigator> 類別的類別來說明此類別的功能。</span><span class="sxs-lookup"><span data-stu-id="a5a42-107">The following sections describe the functionality of the <xref:System.Xml.XPath.XPathNavigator> class based on the class that returns it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a5a42-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="a5a42-108">In This Section</span></span>  
 [<span data-ttu-id="a5a42-109">使用 XPathDocument 及 XmlDocument 讀取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="a5a42-109">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 <span data-ttu-id="a5a42-110">說明如何建立唯讀 <xref:System.Xml.XPath.XPathDocument> 類別物件以讀取 XML 文件，以及如何建立可編輯的 <xref:System.Xml.XmlDocument> 類別物件以讀取及編輯 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a5a42-110">Describes how to create a read-only <xref:System.Xml.XPath.XPathDocument> class object to read an XML document and how to create an editable <xref:System.Xml.XmlDocument> class object to read and edit an XML document.</span></span> <span data-ttu-id="a5a42-111">本主題還說明如何從每個類別傳回 <xref:System.Xml.XPath.XPathNavigator> 物件，以巡覽及編輯 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a5a42-111">This topic also describes how return an <xref:System.Xml.XPath.XPathNavigator> object from each class to navigate and edit an XML document.</span></span>  
  
 [<span data-ttu-id="a5a42-112">選取、 評估及使用 XPathNavigator 比對 XML 資料</span><span class="sxs-lookup"><span data-stu-id="a5a42-112">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="a5a42-113">說明 <xref:System.Xml.XPath.XPathNavigator> 類別的方法，其用於使用 XPath 查詢來選取 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的節點、評估及檢查 XPath 運算式的結果，以及決定 XML 文件中的節點是否符合指定的 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="a5a42-113">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an XML document matches a given XPath expression.</span></span>  
  
 [<span data-ttu-id="a5a42-114">使用 XPathNavigator 存取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="a5a42-114">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="a5a42-115">說明 <xref:System.Xml.XPath.XPathNavigator> 類別的方法，其用於巡覽 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的節點、擷取 XML 資料及存取強型別 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="a5a42-115">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="a5a42-116">使用 XPathNavigator 編輯 XML 資料</span><span class="sxs-lookup"><span data-stu-id="a5a42-116">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="a5a42-117">說明 <xref:System.Xml.XPath.XPathNavigator> 類別的方法，其用於插入、修改及移除 <xref:System.Xml.XmlDocument> 物件中包含之 XML 文件中的節點與值。</span><span class="sxs-lookup"><span data-stu-id="a5a42-117">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="a5a42-118">使用 xpathnavigator 進行結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="a5a42-118">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="a5a42-119">說明驗證 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中包含之 XML 內容的方式。</span><span class="sxs-lookup"><span data-stu-id="a5a42-119">Describes the ways to validate the XML content contained in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a42-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5a42-120">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="a5a42-121">使用 DOM 模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="a5a42-121">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
