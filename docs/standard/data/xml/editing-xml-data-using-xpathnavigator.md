---
title: "使用 XPathNavigator 編輯 XML 資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1f91616-3115-4264-9821-c66589d11d11
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 488651181aaec34c52f368d8829b1c556e6e746e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="editing-xml-data-using-xpathnavigator"></a><span data-ttu-id="6f7d8-102">使用 XPathNavigator 編輯 XML 資料</span><span class="sxs-lookup"><span data-stu-id="6f7d8-102">Editing XML Data using XPathNavigator</span></span>
<span data-ttu-id="6f7d8-103"><xref:System.Xml.XPath.XPathNavigator> 類別提供一些可從 <xref:System.Xml.XmlDocument> 物件所包含之 XML 文件插入、修改及移除節點與值的方法。</span><span class="sxs-lookup"><span data-stu-id="6f7d8-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="6f7d8-104">若要使用其中任一方法來插入、修改及移除節點與值，<xref:System.Xml.XPath.XPathNavigator> 物件必須可編輯，也就是說，其 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 屬性必須為 True。</span><span class="sxs-lookup"><span data-stu-id="6f7d8-104">In order to use any of these methods to insert, modify, and remove nodes and values, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be true.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f7d8-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="6f7d8-105">In This Section</span></span>  
 [<span data-ttu-id="6f7d8-106">使用 XPathNavigator 插入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="6f7d8-106">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="6f7d8-107">說明如何使用 <xref:System.Xml.XmlDocument> 類別，將同層級節點、子節點、屬性節點及值插入至 <xref:System.Xml.XPath.XPathNavigator> 物件中。</span><span class="sxs-lookup"><span data-stu-id="6f7d8-107">Describes how to insert sibling, child, attribute nodes and values in to an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="6f7d8-108">使用 XPathNavigator 修改 XML 資料</span><span class="sxs-lookup"><span data-stu-id="6f7d8-108">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="6f7d8-109">說明如何使用 <xref:System.Xml.XmlDocument> 類別，修改 <xref:System.Xml.XPath.XPathNavigator> 物件中的節點及值。</span><span class="sxs-lookup"><span data-stu-id="6f7d8-109">Describes how to modify nodes and values in an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="6f7d8-110">使用 XPathNavigator 移除 XML 資料</span><span class="sxs-lookup"><span data-stu-id="6f7d8-110">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="6f7d8-111">說明如何使用 <xref:System.Xml.XmlDocument> 類別，移除 <xref:System.Xml.XPath.XPathNavigator> 物件中的節點及值。</span><span class="sxs-lookup"><span data-stu-id="6f7d8-111">Describes how to remove nodes and values from an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7d8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f7d8-112">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="6f7d8-113">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="6f7d8-113">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="6f7d8-114">使用 XPathDocument 及 XmlDocument 讀取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="6f7d8-114">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="6f7d8-115">選取、 評估及使用 XPathNavigator 比對 XML 資料</span><span class="sxs-lookup"><span data-stu-id="6f7d8-115">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="6f7d8-116">使用 XPathNavigator 存取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="6f7d8-116">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="6f7d8-117">使用 xpathnavigator 進行結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="6f7d8-117">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
