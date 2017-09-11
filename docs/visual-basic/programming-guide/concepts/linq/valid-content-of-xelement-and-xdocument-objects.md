---
title: "有效的內容的 XElement 和 XDocument Objects2 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ecdcd4c2c0ec61cf248c9e210d42abb750e0546b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="aa377-102">XElement 和 XDocument 物件的有效內容</span><span class="sxs-lookup"><span data-stu-id="aa377-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="aa377-103">本主題說明可以傳遞給用於將內容加入至項目和文件之建構函式 (Constructor) 和方法的有效引數。</span><span class="sxs-lookup"><span data-stu-id="aa377-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="aa377-104">有效內容</span><span class="sxs-lookup"><span data-stu-id="aa377-104">Valid Content</span></span>  
 <span data-ttu-id="aa377-105">查詢通常會評估<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Xml.Linq.XElement><xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute>的</xref:System.Collections.Generic.IEnumerable%601></xref:System.Xml.Linq.XElement></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="aa377-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="aa377-106">您可以將集合的<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>物件加入至<xref:System.Xml.Linq.XElement>建構函式。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="aa377-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="aa377-107">因此，將查詢的結果當做內容傳入您用來填入 XML 樹狀結構的方法和建構函式會相當方便。</span><span class="sxs-lookup"><span data-stu-id="aa377-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="aa377-108">加入簡單內容時，可以將各種型別傳遞到這個方法。</span><span class="sxs-lookup"><span data-stu-id="aa377-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="aa377-109">有效的型別包括：</span><span class="sxs-lookup"><span data-stu-id="aa377-109">Valid types include the following:</span></span>  
  
-   <span data-ttu-id="aa377-110"><xref:System.String></xref:System.String></span><span class="sxs-lookup"><span data-stu-id="aa377-110"><xref:System.String></span></span>  
  
-   <span data-ttu-id="aa377-111"><xref:System.Double></xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="aa377-111"><xref:System.Double></span></span>  
  
-   <span data-ttu-id="aa377-112"><xref:System.Single></xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="aa377-112"><xref:System.Single></span></span>  
  
-   <span data-ttu-id="aa377-113"><xref:System.Decimal></xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="aa377-113"><xref:System.Decimal></span></span>  
  
-   <span data-ttu-id="aa377-114"><xref:System.Boolean></xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="aa377-114"><xref:System.Boolean></span></span>  
  
-   <span data-ttu-id="aa377-115"><xref:System.DateTime></xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="aa377-115"><xref:System.DateTime></span></span>  
  
-   <span data-ttu-id="aa377-116"><xref:System.TimeSpan></xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="aa377-116"><xref:System.TimeSpan></span></span>  
  
-   <span data-ttu-id="aa377-117"><xref:System.DateTimeOffset></xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="aa377-117"><xref:System.DateTimeOffset></span></span>  
  
-   <span data-ttu-id="aa377-118">任何實作 `Object.ToString` 的型別。</span><span class="sxs-lookup"><span data-stu-id="aa377-118">Any type that implements `Object.ToString`.</span></span>  
  
-   <span data-ttu-id="aa377-119">可實作<xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>任何型別</span><span class="sxs-lookup"><span data-stu-id="aa377-119">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="aa377-120">加入複雜內容時，可以將各種型別傳遞到這個方法：</span><span class="sxs-lookup"><span data-stu-id="aa377-120">When adding complex content, various types can be passed to this method:</span></span>  
  
-   <span data-ttu-id="aa377-121"><xref:System.Xml.Linq.XObject></xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="aa377-121"><xref:System.Xml.Linq.XObject></span></span>  
  
-   <span data-ttu-id="aa377-122"><xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="aa377-122"><xref:System.Xml.Linq.XNode></span></span>  
  
-   <span data-ttu-id="aa377-123"><xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="aa377-123"><xref:System.Xml.Linq.XAttribute></span></span>  
  
-   <span data-ttu-id="aa377-124">可實作任何型別<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="aa377-124">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="aa377-125">如果物件實作<xref:System.Collections.Generic.IEnumerable%601>會列舉中物件的集合，集合中的所有項目加入。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="aa377-125">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="aa377-126">如果集合包含<xref:System.Xml.Linq.XNode>或<xref:System.Xml.Linq.XAttribute>物件，會個別加入集合中的每個項目。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="aa377-126">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="aa377-127">如果集合包含文字 (或轉換為文字的物件)，集合中的文字會遭到串連，並加入為單一文字節點。</span><span class="sxs-lookup"><span data-stu-id="aa377-127">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="aa377-128">如果內容為 `null`，不會加入任何項目。</span><span class="sxs-lookup"><span data-stu-id="aa377-128">If content is `null`, nothing is added.</span></span> <span data-ttu-id="aa377-129">傳遞集合時，集合中的項目可以為 `null`。</span><span class="sxs-lookup"><span data-stu-id="aa377-129">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="aa377-130">集合中的 `null` 項目對於樹狀結構沒有任何影響。</span><span class="sxs-lookup"><span data-stu-id="aa377-130">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="aa377-131">加入的屬性在其包含的項目中必須擁有一個唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="aa377-131">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="aa377-132">當加入<xref:System.Xml.Linq.XNode>或<xref:System.Xml.Linq.XAttribute>物件，如果新內容沒有父代，則物件只會附加到 XML 樹狀結構。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="aa377-132">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="aa377-133">如果新內容已經成為父代，或是其他 XML 樹狀結構的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="aa377-133">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="aa377-134">有效的文件內容</span><span class="sxs-lookup"><span data-stu-id="aa377-134">Valid Content for Documents</span></span>  
 <span data-ttu-id="aa377-135">屬性和簡單的內容無法加入到文件中。</span><span class="sxs-lookup"><span data-stu-id="aa377-135">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="aa377-136">不需要您建立<xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument>的許多案例</span><span class="sxs-lookup"><span data-stu-id="aa377-136">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="aa377-137">相反地，您通常可以建立 XML 樹狀結構與<xref:System.Xml.Linq.XElement>根節點。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="aa377-137">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="aa377-138">除非您有建立文件 （例如，因為您必須在最上層建立處理指示與註解，或者您必須支援文件類型） 的特定需求，更方便使用<xref:System.Xml.Linq.XElement>做為根節點。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="aa377-138">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="aa377-139">有效的文件內容包括：</span><span class="sxs-lookup"><span data-stu-id="aa377-139">Valid content for a document includes the following:</span></span>  
  
-   <span data-ttu-id="aa377-140">零個或一個<xref:System.Xml.Linq.XDocumentType>物件。</xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="aa377-140">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="aa377-141">文件型別必須在項目之前。</span><span class="sxs-lookup"><span data-stu-id="aa377-141">The document types must come before the element.</span></span>  
  
-   <span data-ttu-id="aa377-142">零或一個項目。</span><span class="sxs-lookup"><span data-stu-id="aa377-142">Zero or one element.</span></span>  
  
-   <span data-ttu-id="aa377-143">零或多個註解。</span><span class="sxs-lookup"><span data-stu-id="aa377-143">Zero or more comments.</span></span>  
  
-   <span data-ttu-id="aa377-144">零或多個處理指示。</span><span class="sxs-lookup"><span data-stu-id="aa377-144">Zero or more processing instructions.</span></span>  
  
-   <span data-ttu-id="aa377-145">只包含一個空白字元的零或多個節點。</span><span class="sxs-lookup"><span data-stu-id="aa377-145">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="aa377-146">允許加入內容的建構函式與函式</span><span class="sxs-lookup"><span data-stu-id="aa377-146">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="aa377-147">下列方法可讓您將子內容加入至<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>::</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="aa377-147">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="aa377-148">方法</span><span class="sxs-lookup"><span data-stu-id="aa377-148">Method</span></span>|<span data-ttu-id="aa377-149">描述</span><span class="sxs-lookup"><span data-stu-id="aa377-149">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="aa377-150"><xref:System.Xml.Linq.XElement.%23ctor%2A></xref:System.Xml.Linq.XElement.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="aa377-150"><xref:System.Xml.Linq.XElement.%23ctor%2A></span></span>|<span data-ttu-id="aa377-151">建構<xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="aa377-151">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="aa377-152"><xref:System.Xml.Linq.XDocument.%23ctor%2A></xref:System.Xml.Linq.XDocument.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="aa377-152"><xref:System.Xml.Linq.XDocument.%23ctor%2A></span></span>|<span data-ttu-id="aa377-153">建構<xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="aa377-153">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<span data-ttu-id="aa377-154"><xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XContainer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="aa377-154"><xref:System.Xml.Linq.XContainer.Add%2A></span></span>|<span data-ttu-id="aa377-155">將子內容的<xref:System.Xml.Linq.XElement><xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument>或</xref:System.Xml.Linq.XElement>結尾</span><span class="sxs-lookup"><span data-stu-id="aa377-155">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<span data-ttu-id="aa377-156"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span><span class="sxs-lookup"><span data-stu-id="aa377-156"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span></span>|<span data-ttu-id="aa377-157">將內容加入在<xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="aa377-157">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<span data-ttu-id="aa377-158"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span><span class="sxs-lookup"><span data-stu-id="aa377-158"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span></span>|<span data-ttu-id="aa377-159">新增<xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode>之前的內容</span><span class="sxs-lookup"><span data-stu-id="aa377-159">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<span data-ttu-id="aa377-160"><xref:System.Xml.Linq.XContainer.AddFirst%2A></xref:System.Xml.Linq.XContainer.AddFirst%2A></span><span class="sxs-lookup"><span data-stu-id="aa377-160"><xref:System.Xml.Linq.XContainer.AddFirst%2A></span></span>|<span data-ttu-id="aa377-161">將內容加入<xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer>目的子內容的開頭</span><span class="sxs-lookup"><span data-stu-id="aa377-161">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="aa377-162"><xref:System.Xml.Linq.XElement.ReplaceAll%2A></xref:System.Xml.Linq.XElement.ReplaceAll%2A></span><span class="sxs-lookup"><span data-stu-id="aa377-162"><xref:System.Xml.Linq.XElement.ReplaceAll%2A></span></span>|<span data-ttu-id="aa377-163">取代<xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>所有內容 （子節點和屬性）</span><span class="sxs-lookup"><span data-stu-id="aa377-163">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="aa377-164"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></span><span class="sxs-lookup"><span data-stu-id="aa377-164"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></span></span>|<span data-ttu-id="aa377-165">取代<xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>屬性</span><span class="sxs-lookup"><span data-stu-id="aa377-165">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="aa377-166"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></span><span class="sxs-lookup"><span data-stu-id="aa377-166"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></span></span>|<span data-ttu-id="aa377-167">以新的內容取代子節點。</span><span class="sxs-lookup"><span data-stu-id="aa377-167">Replaces the children nodes with new content.</span></span>|  
|<span data-ttu-id="aa377-168"><xref:System.Xml.Linq.XNode.ReplaceWith%2A></xref:System.Xml.Linq.XNode.ReplaceWith%2A></span><span class="sxs-lookup"><span data-stu-id="aa377-168"><xref:System.Xml.Linq.XNode.ReplaceWith%2A></span></span>|<span data-ttu-id="aa377-169">以新內容取代節點。</span><span class="sxs-lookup"><span data-stu-id="aa377-169">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa377-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa377-170">See Also</span></span>  
 [<span data-ttu-id="aa377-171">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa377-171">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
