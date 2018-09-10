---
title: 將實體宣告和實體參考讀入 DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e30b52b8cdfb4d185687d58c80f4475730031c86
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264268"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="91192-102">將實體宣告和實體參考讀入 DOM</span><span class="sxs-lookup"><span data-stu-id="91192-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="91192-103">實體是一種宣告，陳述 XML 中用來代替內容或標記的名稱。</span><span class="sxs-lookup"><span data-stu-id="91192-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="91192-104">實體有兩個部分。</span><span class="sxs-lookup"><span data-stu-id="91192-104">There are two parts to entities.</span></span> <span data-ttu-id="91192-105">首先，您必須使用實體宣告，將名稱繫結於取代內容。</span><span class="sxs-lookup"><span data-stu-id="91192-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="91192-106">實體宣告可透過文件類型定義 (DTD) 或 XML 結構描述中的 `<!ENTITY name "value">` 語法來建立。</span><span class="sxs-lookup"><span data-stu-id="91192-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="91192-107">第二，實體宣告中定義的名稱隨後會用於 XML。</span><span class="sxs-lookup"><span data-stu-id="91192-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="91192-108">用於 XML 時，它便稱為實體參考。</span><span class="sxs-lookup"><span data-stu-id="91192-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="91192-109">例如，下列實體宣告會宣告名稱 `publisher` 的實體，而此實體會與 "Microsoft Press" 的內容產生關聯。</span><span class="sxs-lookup"><span data-stu-id="91192-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="91192-110">下列範例顯示在 XML 中，將這個實體宣告當成實體參考的用法。</span><span class="sxs-lookup"><span data-stu-id="91192-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="91192-111">有些剖析器在文件載入記憶體時會自動擴充實體。</span><span class="sxs-lookup"><span data-stu-id="91192-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="91192-112">因此，當 XML 讀入記憶體時，會記住並且儲存實體宣告。</span><span class="sxs-lookup"><span data-stu-id="91192-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="91192-113">接下來當剖析器發現用來識別一般實體參考的 `&;` 字元時，剖析器會在實體宣告表中查看該名稱。</span><span class="sxs-lookup"><span data-stu-id="91192-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="91192-114">`&publisher;` 參考會由它所代表的內容取代。</span><span class="sxs-lookup"><span data-stu-id="91192-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="91192-115">使用下列 XML，</span><span class="sxs-lookup"><span data-stu-id="91192-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="91192-116">擴充實體參考，並且以 Microsoft Press 內容取代 `&publisher;`，會產生下列擴充的 XML。</span><span class="sxs-lookup"><span data-stu-id="91192-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="91192-117">**輸出**</span><span class="sxs-lookup"><span data-stu-id="91192-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="91192-118">實體有許多種類。</span><span class="sxs-lookup"><span data-stu-id="91192-118">There are many kinds of entities.</span></span> <span data-ttu-id="91192-119">下圖將說明實體型別和術語的解析。</span><span class="sxs-lookup"><span data-stu-id="91192-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="91192-120">![實體類型階層流程圖](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="91192-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="91192-121">XML 文件物件模型 (DOM) 的 Microsoft .Net Framework 實作預設會保留實體參考，並且在 XML 載入時不會擴充實體。</span><span class="sxs-lookup"><span data-stu-id="91192-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="91192-122">這表示當文件載入 DOM 時，會建立含有參考變數 `&publisher;` 的 **XmlEntityReference** 節點，其中包含代表 DTD 中所宣告之實體內容的子節點。</span><span class="sxs-lookup"><span data-stu-id="91192-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="91192-123">使用 `<!ENTITY publisher "Microsoft Press">` 實體宣告時，下圖會顯示從這個宣告中建立的 **XmlEntity** 和 **XmlText** 節點。</span><span class="sxs-lookup"><span data-stu-id="91192-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="91192-124">![從實體宣告建立的節點](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="91192-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="91192-125">實體參考是否會擴充的差異在於記憶體中 DOM 樹狀結構中產生了哪些節點。</span><span class="sxs-lookup"><span data-stu-id="91192-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="91192-126">[保留實體參考](../../../../docs/standard/data/xml/entity-references-are-preserved.md)和[實體參考已擴充且沒有保留](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md)主題會說明所產生之節點的差異。</span><span class="sxs-lookup"><span data-stu-id="91192-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91192-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91192-127">See also</span></span>

- [<span data-ttu-id="91192-128">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="91192-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
