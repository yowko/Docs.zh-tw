---
title: "使用 XPathNavigator 插入 XML 資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 34151590a14c48c0a84677f2d7cae662291edf40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="c19a5-102">使用 XPathNavigator 插入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="c19a5-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="c19a5-103"><xref:System.Xml.XPath.XPathNavigator> 類別提供一組方式，可在 XML 文件中插入同層級節點、子節點及屬性節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="c19a5-104">為了使用這些方法，<xref:System.Xml.XPath.XPathNavigator> 物件必須是可編輯的，也就是說，它的 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 屬性必須為 `true`。</span><span class="sxs-lookup"><span data-stu-id="c19a5-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="c19a5-105">可編輯 XML 文件的 <xref:System.Xml.XPath.XPathNavigator> 物件是由 <xref:System.Xml.XmlDocument.CreateNavigator%2A> 類別的 <xref:System.Xml.XmlDocument> 方法所建立。</span><span class="sxs-lookup"><span data-stu-id="c19a5-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="c19a5-106">由 <xref:System.Xml.XPath.XPathNavigator> 類別建立的 <xref:System.Xml.XPath.XPathDocument> 物件是唯讀的，而且如果嘗試使用由 <xref:System.Xml.XPath.XPathNavigator> 物件建立之 <xref:System.Xml.XPath.XPathDocument> 物件的編輯方法，則會導致 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="c19a5-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="c19a5-107">如需有關建立可編輯<xref:System.Xml.XPath.XPathNavigator>物件，請參閱[使用 XPathDocument 及 XmlDocument 讀取 XML 資料](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)。</span><span class="sxs-lookup"><span data-stu-id="c19a5-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="c19a5-108">插入節點</span><span class="sxs-lookup"><span data-stu-id="c19a5-108">Inserting Nodes</span></span>  
 <span data-ttu-id="c19a5-109"><xref:System.Xml.XPath.XPathNavigator> 類別提供在 XML 文件中，插入同層級節點、子節點及屬性節點的方法。</span><span class="sxs-lookup"><span data-stu-id="c19a5-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="c19a5-110">下列各節中所說明的方法，可讓您將節點及屬性插入與 <xref:System.Xml.XPath.XPathNavigator> 物件之目前位置不同的位置。</span><span class="sxs-lookup"><span data-stu-id="c19a5-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="c19a5-111">插入同層級節點</span><span class="sxs-lookup"><span data-stu-id="c19a5-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="c19a5-112"><xref:System.Xml.XPath.XPathNavigator> 類別提供下列方法來插入同層級節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="c19a5-113">這些方法可在 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在的節點前後，插入同層級節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="c19a5-114"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> 及 <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> 方法會多載，且接受 `string`、<xref:System.Xml.XmlReader> 物件或包含同層級節點的 <xref:System.Xml.XPath.XPathNavigator> 物件，以加入為參數。</span><span class="sxs-lookup"><span data-stu-id="c19a5-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="c19a5-115">這兩種方法還會傳回用於插入同層級節點的 <xref:System.Xml.XmlWriter> 物件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="c19a5-116"><xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> 及 <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> 方法會使用指定為參數的命名空間前置詞、區域名稱、命名空間 URI 及值，在 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在的節點前後，插入單一的同層級節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="c19a5-117">在下列範例中，會在 `pages` 檔案之第一個 `price` 項目的 `book` 項目子系之前，插入新的 `contosoBooks.xml` 項目。</span><span class="sxs-lookup"><span data-stu-id="c19a5-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="c19a5-118">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="c19a5-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="c19a5-119">如需 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> 及 <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.XPath.XPathNavigator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="c19a5-120">插入子節點</span><span class="sxs-lookup"><span data-stu-id="c19a5-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="c19a5-121"><xref:System.Xml.XPath.XPathNavigator> 類別提供下列方法來插入子節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="c19a5-122">這些方法會將子節點附加到 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的子節點清單結尾及開頭。</span><span class="sxs-lookup"><span data-stu-id="c19a5-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="c19a5-123">與＜插入同層級節點＞一節中的方法一樣，<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> 及 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> 方法也接受 `string`、<xref:System.Xml.XmlReader> 物件或包含子節點的 <xref:System.Xml.XPath.XPathNavigator> 物件，以加入為參數。</span><span class="sxs-lookup"><span data-stu-id="c19a5-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="c19a5-124">這兩種方法還會傳回用於插入子節點的 <xref:System.Xml.XmlWriter> 物件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="c19a5-125">與＜插入同層級節點＞一節中的方法一樣，<xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> 及 <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> 方法也會使用指定為參數的命名空間前置詞、區域名稱、命名空間 URI 及值，在 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的子節點清單結尾及開頭，插入單一子節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="c19a5-126">在下列範例中，會將新的 `pages` 項目子系附加至 `book` 檔案中第一個 `contosoBooks.xml` 項目的項目子系清單。</span><span class="sxs-lookup"><span data-stu-id="c19a5-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="c19a5-127">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="c19a5-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="c19a5-128">如需 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>、<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> 及 <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.XPath.XPathNavigator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="c19a5-129">插入屬性節點</span><span class="sxs-lookup"><span data-stu-id="c19a5-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="c19a5-130"><xref:System.Xml.XPath.XPathNavigator> 類別提供下列方法來插入屬性節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="c19a5-131">這些方法可在 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在的項目節點上，插入屬性節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="c19a5-132"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> 方法使用指定為參數的命名空間前置詞、區域名稱、命名空間 URI 及值，在 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在的項目節點上，建立屬性節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="c19a5-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 方法會傳回用於插入屬性節點的 <xref:System.Xml.XmlWriter> 物件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="c19a5-134">在下列範例中，會使用從 `discount` 方法傳回的 `currency` 物件，在 `price` 檔案中第一個 `book` 項目的 `contosoBooks.xml` 項目子系上，建立新的 <xref:System.Xml.XmlWriter> 及 <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="c19a5-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="c19a5-135">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="c19a5-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="c19a5-136">如需 <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> 及 <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.XPath.XPathNavigator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="c19a5-137">複製節點</span><span class="sxs-lookup"><span data-stu-id="c19a5-137">Copying Nodes</span></span>  
 <span data-ttu-id="c19a5-138">在某些情況下，您可能要使用其他 XML 文件的內容，填入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="c19a5-139"><xref:System.Xml.XPath.XPathNavigator> 類別及 <xref:System.Xml.XmlWriter> 類別可以從現有的 <xref:System.Xml.XmlDocument> 物件或 <xref:System.Xml.XmlReader> 物件，將節點複製到 <xref:System.Xml.XPath.XPathNavigator> 物件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="c19a5-140"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 方法都包含多載，它們可以接受 <xref:System.Xml.XPath.XPathNavigator> 物件或 <xref:System.Xml.XmlReader> 物件做為參數。</span><span class="sxs-lookup"><span data-stu-id="c19a5-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="c19a5-141"><xref:System.Xml.XmlWriter.WriteNode%2A> 類別的 <xref:System.Xml.XmlWriter> 方法包含可接受 <xref:System.Xml.XmlNode>、<xref:System.Xml.XmlReader> 或 <xref:System.Xml.XPath.XPathNavigator> 物件的多載。</span><span class="sxs-lookup"><span data-stu-id="c19a5-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="c19a5-142">下列範例會將所有 `book` 項目，從一個文件複製到另一個文件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a><span data-ttu-id="c19a5-143">插入值</span><span class="sxs-lookup"><span data-stu-id="c19a5-143">Inserting Values</span></span>  
 <span data-ttu-id="c19a5-144"><xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 及 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法，以便在 <xref:System.Xml.XmlDocument> 物件中插入節點的值。</span><span class="sxs-lookup"><span data-stu-id="c19a5-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="c19a5-145">插入不具型別值</span><span class="sxs-lookup"><span data-stu-id="c19a5-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="c19a5-146"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法只會插入做為參數傳遞的不具型別 `string` 值，並將其做為 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的值。</span><span class="sxs-lookup"><span data-stu-id="c19a5-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="c19a5-147">插入的值不具有任何型別，或未根據節點型別 (若提供結構描述資訊) 驗證新值的有效性。</span><span class="sxs-lookup"><span data-stu-id="c19a5-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="c19a5-148">在下列範例中，<xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法用於更新 `price` 檔案中的所有 `contosoBooks.xml` 項目。</span><span class="sxs-lookup"><span data-stu-id="c19a5-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="c19a5-149">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="c19a5-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="c19a5-150">插入具型別值</span><span class="sxs-lookup"><span data-stu-id="c19a5-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="c19a5-151">當節點的型別為 W3C XML 結構描述簡單型別時，會根據簡單型別的 Facet，對 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法插入的新值執行設定前的檢查。</span><span class="sxs-lookup"><span data-stu-id="c19a5-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="c19a5-152">如果根據節點的型別，新值無效 (例如，在型別為 `-1` 的項目上設定 `xs:positiveInteger` 值)，則會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c19a5-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="c19a5-153">下列範例會嘗試將 `price` 檔案中第一個 `book` 項目之 `contosoBooks.xml` 項目的值，變更為 <xref:System.DateTime> 值。</span><span class="sxs-lookup"><span data-stu-id="c19a5-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="c19a5-154">因為在 `price` 檔案中將 `xs:decimal` 項目的 XML 結構描述型別定義為 `contosoBooks.xsd`，所以這個動作會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c19a5-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="c19a5-155">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="c19a5-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="c19a5-156">該範例還採用 `contosoBooks.xsd` 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="c19a5-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="c19a5-157">InnerXml 及 OuterXml 屬性</span><span class="sxs-lookup"><span data-stu-id="c19a5-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="c19a5-158"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="c19a5-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="c19a5-159"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及指定 XML `string` 的已剖析內容。</span><span class="sxs-lookup"><span data-stu-id="c19a5-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="c19a5-160">同樣地，<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及目前節點本身。</span><span class="sxs-lookup"><span data-stu-id="c19a5-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="c19a5-161">除了本主題中所說明的方法之外，還可以使用 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性，將節點及值插入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="c19a5-162">如需有關使用<xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>和<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A>屬性插入節點及值，請參閱[使用 XPathNavigator 修改 XML 資料](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)主題。</span><span class="sxs-lookup"><span data-stu-id="c19a5-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="c19a5-163">命名空間及 xml:lang 衝突</span><span class="sxs-lookup"><span data-stu-id="c19a5-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="c19a5-164">當使用 `xml:lang` 類別的 <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> 及 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> 方法 (其採用 <xref:System.Xml.XPath.XPathNavigator> 物件做為參數) 來插入 XML 資料時，可能會發生某些與命名空間的範圍及 <xref:System.Xml.XmlReader> 宣告相關的衝突。</span><span class="sxs-lookup"><span data-stu-id="c19a5-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="c19a5-165">下列是可能的命名空間衝突。</span><span class="sxs-lookup"><span data-stu-id="c19a5-165">The following are the possible namespace conflicts.</span></span>  
  
-   <span data-ttu-id="c19a5-166">如果 <xref:System.Xml.XmlReader> 物件的內容中包含範圍中的命名空間，其中命名空間 URI 對應的前置詞不在 <xref:System.Xml.XPath.XPathNavigator> 物件的內容中，則會將新命名空間宣告加入至新插入的節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="c19a5-167">如果相同的命名空間 URI 在 <xref:System.Xml.XmlReader> 物件的內容及 <xref:System.Xml.XPath.XPathNavigator> 物件內容中都在範圍內，但它們在這兩個內容中擁有不同的對應前置詞，則會將新的命名空間宣告加入至新插入的節點，並從 <xref:System.Xml.XmlReader> 物件取得前置詞及命名空間 URI。</span><span class="sxs-lookup"><span data-stu-id="c19a5-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
-   <span data-ttu-id="c19a5-168">如果相同的命名空間前置詞在 <xref:System.Xml.XmlReader> 物件的內容及 <xref:System.Xml.XPath.XPathNavigator> 物件的內容中都在範圍內，但在這兩個內容中擁有不同的對應命名空間 URI，則會將新的命名空間宣告加入至新插入的節點，該節點會以從 <xref:System.Xml.XmlReader> 物件取得之命名空間 URI 來重新宣告該前置詞。</span><span class="sxs-lookup"><span data-stu-id="c19a5-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
-   <span data-ttu-id="c19a5-169">如果 <xref:System.Xml.XmlReader> 物件內容及 <xref:System.Xml.XPath.XPathNavigator> 物件內容中的前置詞及命名空間 URI 相同，則不會將新的命名空間宣告加入至新插入的節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c19a5-170">上述說明還適用於將空白 `string` 做為前置詞的命名空間宣告 (例如，預設命名空間宣告)。</span><span class="sxs-lookup"><span data-stu-id="c19a5-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="c19a5-171">下列是可能的 `xml:lang` 衝突。</span><span class="sxs-lookup"><span data-stu-id="c19a5-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
-   <span data-ttu-id="c19a5-172">如果在 `xml:lang` 物件的內容中包含範圍中的 <xref:System.Xml.XmlReader> 屬性，但 <xref:System.Xml.XPath.XPathNavigator> 物件的內容中沒有，則會將從 `xml:lang` 物件取得值的 <xref:System.Xml.XmlReader> 屬性加入至新插入的節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="c19a5-173">如果 `xml:lang` 物件的內容及 <xref:System.Xml.XmlReader> 物件的內容都包含範圍中的 <xref:System.Xml.XPath.XPathNavigator> 屬性，但是屬性的值不同，則會將從 `xml:lang` 物件取得值的 <xref:System.Xml.XmlReader> 屬性加入至新插入的節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="c19a5-174">如果 `xml:lang` 物件的內容及 <xref:System.Xml.XmlReader> 物件的內容都包含範圍中的 <xref:System.Xml.XPath.XPathNavigator> 屬性，但是屬性的值相同，則不會將新的 `xml:lang` 屬性加入新插入的節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
-   <span data-ttu-id="c19a5-175">如果 `xml:lang` 物件的內容包含範圍中的 <xref:System.Xml.XPath.XPathNavigator> 屬性，但是在 <xref:System.Xml.XmlReader> 物件的內容中沒有，則不會將 `xml:lang` 屬性加入至新插入的節點。</span><span class="sxs-lookup"><span data-stu-id="c19a5-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="c19a5-176">使用 XmlWriter 插入節點</span><span class="sxs-lookup"><span data-stu-id="c19a5-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="c19a5-177">多載＜插入節點及值＞一節中說明之用於插入同層級節點、子節點及屬性節點的方法。</span><span class="sxs-lookup"><span data-stu-id="c19a5-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="c19a5-178"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>、<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 方法會傳回用於插入節點的 <xref:System.Xml.XmlWriter> 物件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="c19a5-179">不支援的 XmlWriter 方法</span><span class="sxs-lookup"><span data-stu-id="c19a5-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="c19a5-180">由於 XPath 資料模型與文件物件模型 (DOM) 之間的差異，<xref:System.Xml.XmlWriter> 類別並不支援所有使用 <xref:System.Xml.XPath.XPathNavigator> 類別將資訊寫入 XML 文件的方法。</span><span class="sxs-lookup"><span data-stu-id="c19a5-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="c19a5-181">下表說明 <xref:System.Xml.XmlWriter> 類別不支援的 <xref:System.Xml.XPath.XPathNavigator> 類別方法。</span><span class="sxs-lookup"><span data-stu-id="c19a5-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="c19a5-182">方法</span><span class="sxs-lookup"><span data-stu-id="c19a5-182">Method</span></span>|<span data-ttu-id="c19a5-183">描述</span><span class="sxs-lookup"><span data-stu-id="c19a5-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="c19a5-184">會擲回 <xref:System.NotSupportedException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c19a5-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="c19a5-185">在根層級會被忽略，如果在 XML 文件的任何其他層級呼叫，則擲回 <xref:System.NotSupportedException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c19a5-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="c19a5-186">視為對等字元之 <xref:System.Xml.XmlWriter.WriteString%2A> 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="c19a5-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="c19a5-187">視為對等字元之 <xref:System.Xml.XmlWriter.WriteString%2A> 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="c19a5-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="c19a5-188">視為對等字元之 <xref:System.Xml.XmlWriter.WriteString%2A> 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="c19a5-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="c19a5-189">如需 <xref:System.Xml.XmlWriter> 類別的詳細資訊，請參閱 <xref:System.Xml.XmlWriter> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="c19a5-190">多個 XmlWriter 物件</span><span class="sxs-lookup"><span data-stu-id="c19a5-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="c19a5-191">可能有多個 <xref:System.Xml.XPath.XPathNavigator> 物件指向包含一個或多個開啟 <xref:System.Xml.XmlWriter> 物件之 XML 文件的不同部分。</span><span class="sxs-lookup"><span data-stu-id="c19a5-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="c19a5-192">單一執行緒案例中允許並支援多個 <xref:System.Xml.XmlWriter> 物件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="c19a5-193">下列各項是使用多個 <xref:System.Xml.XmlWriter> 物件時，需要考慮的重要注意事項。</span><span class="sxs-lookup"><span data-stu-id="c19a5-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
-   <span data-ttu-id="c19a5-194">當呼叫每個 <xref:System.Xml.XmlWriter> 物件的 <xref:System.Xml.XmlWriter.Close%2A> 方法時，會將由 <xref:System.Xml.XmlWriter> 物件寫入的 XML 片段加入至 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="c19a5-195">直到那時，<xref:System.Xml.XmlWriter> 物件會寫入中斷連接的片段。</span><span class="sxs-lookup"><span data-stu-id="c19a5-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="c19a5-196">如果在 XML 文件上執行作業，則不會影響在呼叫 <xref:System.Xml.XmlWriter> 之前，由 <xref:System.Xml.XmlWriter.Close%2A> 物件寫入的任何片段。</span><span class="sxs-lookup"><span data-stu-id="c19a5-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
-   <span data-ttu-id="c19a5-197">如果在特定 XML 子樹狀目錄上有開啟 <xref:System.Xml.XmlWriter> 物件，而該子樹狀目錄已刪除，則 <xref:System.Xml.XmlWriter> 物件仍然會加入至該子樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="c19a5-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="c19a5-198">該子樹狀目錄只是變成已刪除的片段。</span><span class="sxs-lookup"><span data-stu-id="c19a5-198">The subtree simply becomes a deleted fragment.</span></span>  
  
-   <span data-ttu-id="c19a5-199">如果在 XML 文件中同時開啟多個 <xref:System.Xml.XmlWriter> 物件，則會依照關閉 <xref:System.Xml.XmlWriter> 物件的順序 (而非開啟它們的順序)，將它們加入至 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="c19a5-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="c19a5-200">下列範例會建立 <xref:System.Xml.XmlDocument> 物件及 <xref:System.Xml.XPath.XPathNavigator> 物件，然後使用由 <xref:System.Xml.XmlWriter> 方法傳回的 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> 物件，在 `books.xml` 檔案建立第一本書的結構。</span><span class="sxs-lookup"><span data-stu-id="c19a5-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="c19a5-201">之後，範例會將其儲存為 `book.xml` 檔案。</span><span class="sxs-lookup"><span data-stu-id="c19a5-201">The example then saves it as the `book.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="c19a5-202">儲存 XML 文件</span><span class="sxs-lookup"><span data-stu-id="c19a5-202">Saving an XML Document</span></span>  
 <span data-ttu-id="c19a5-203">使用 <xref:System.Xml.XmlDocument> 類別的方法，將用本主題中說明之方法對 <xref:System.Xml.XmlDocument> 物件所做的變更儲存下來。</span><span class="sxs-lookup"><span data-stu-id="c19a5-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="c19a5-204">如需有關儲存所做的變更<xref:System.Xml.XmlDocument>物件，請參閱[儲存與寫入文件](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)。</span><span class="sxs-lookup"><span data-stu-id="c19a5-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c19a5-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c19a5-205">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="c19a5-206">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="c19a5-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="c19a5-207">使用 XPathNavigator 修改 XML 資料</span><span class="sxs-lookup"><span data-stu-id="c19a5-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="c19a5-208">使用 XPathNavigator 移除 XML 資料</span><span class="sxs-lookup"><span data-stu-id="c19a5-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
