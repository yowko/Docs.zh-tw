---
title: "使用 XPathNavigator 存取 XML 資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c57b46e6-5c77-408f-bc4e-67a5dcc9cc05
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 27f5bccc2ab5f229e8b726b3bff18ea7a590f5c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-xml-data-using-xpathnavigator"></a><span data-ttu-id="f8bac-102">使用 XPathNavigator 存取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="f8bac-102">Accessing XML Data using XPathNavigator</span></span>
<span data-ttu-id="f8bac-103"><xref:System.Xml.XPath.XPathNavigator> 類別提供了一組可以在 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中巡覽節點、擷取 XML 資料及存取強型別 XML 資料的方法。</span><span class="sxs-lookup"><span data-stu-id="f8bac-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8bac-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="f8bac-104">In This Section</span></span>  
 [<span data-ttu-id="f8bac-105">使用 XPathNavigator 巡覽節點集</span><span class="sxs-lookup"><span data-stu-id="f8bac-105">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="f8bac-106">說明 <xref:System.Xml.XPath.XPathNavigator> 類別的節點集巡覽方法，其可用於巡覽 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的節點。</span><span class="sxs-lookup"><span data-stu-id="f8bac-106">Describes the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="f8bac-107">巡覽屬性及命名空間節點使用 XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f8bac-107">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="f8bac-108">說明 <xref:System.Xml.XPath.XPathNavigator> 類別的屬性及命名空間節點巡覽方法。</span><span class="sxs-lookup"><span data-stu-id="f8bac-108">Describes the attribute and namespace node navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="f8bac-109">使用 XPathNavigator 擷取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="f8bac-109">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="f8bac-110">說明從 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中擷取 XML 資料的各種方法。</span><span class="sxs-lookup"><span data-stu-id="f8bac-110">Describes the various methods of extracting XML data from an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="f8bac-111">存取強型別使用 XPathNavigator XML 資料</span><span class="sxs-lookup"><span data-stu-id="f8bac-111">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="f8bac-112">說明如何使用 <xref:System.Xml.XPath.XPathDocument> 類別，在 <xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XPath.XPathNavigator> 物件中存取強型別 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="f8bac-112">Describes accessing strongly-typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="f8bac-113">使用者定義函式和變數</span><span class="sxs-lookup"><span data-stu-id="f8bac-113">User Defined Functions and Variables</span></span>](../../../../docs/standard/data/xml/user-defined-functions-and-variables.md)  
 <span data-ttu-id="f8bac-114">描述如何實作自訂 <xref:System.Xml.Xsl.XsltContext> 類別以及支援擴充函式和變數的 <xref:System.Xml.Xsl.IXsltContextFunction> 和 <xref:System.Xml.Xsl.IXsltContextVariable> 介面。</span><span class="sxs-lookup"><span data-stu-id="f8bac-114">Describes implementing a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8bac-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8bac-115">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="f8bac-116">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="f8bac-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="f8bac-117">使用 XPathDocument 及 XmlDocument 讀取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="f8bac-117">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="f8bac-118">選取、 評估及使用 XPathNavigator 比對 XML 資料</span><span class="sxs-lookup"><span data-stu-id="f8bac-118">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="f8bac-119">使用 XPathNavigator 編輯 XML 資料</span><span class="sxs-lookup"><span data-stu-id="f8bac-119">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="f8bac-120">使用 xpathnavigator 進行結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="f8bac-120">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
