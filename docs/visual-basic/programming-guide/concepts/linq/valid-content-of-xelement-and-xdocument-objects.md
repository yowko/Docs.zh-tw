---
title: XElement 和 XDocument Objects2 的有效內容
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: bb5dda6bee0863a2ef951975e92c55184df9d516
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907578"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="9e62f-102">XElement 和 XDocument 物件的有效內容</span><span class="sxs-lookup"><span data-stu-id="9e62f-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="9e62f-103">本主題說明可以傳遞給用於將內容加入至項目和文件之建構函式 (Constructor) 和方法的有效引數。</span><span class="sxs-lookup"><span data-stu-id="9e62f-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="9e62f-104">有效內容</span><span class="sxs-lookup"><span data-stu-id="9e62f-104">Valid Content</span></span>  
 <span data-ttu-id="9e62f-105">查詢通常會評估成 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 或 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="9e62f-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="9e62f-106">您可以將 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件的集合傳遞給 <xref:System.Xml.Linq.XElement> 建構函式。</span><span class="sxs-lookup"><span data-stu-id="9e62f-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="9e62f-107">因此，將查詢的結果當做內容傳入您用來填入 XML 樹狀結構的方法和建構函式會相當方便。</span><span class="sxs-lookup"><span data-stu-id="9e62f-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="9e62f-108">加入簡單內容時，可以將各種型別傳遞到這個方法。</span><span class="sxs-lookup"><span data-stu-id="9e62f-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="9e62f-109">有效的型別包括：</span><span class="sxs-lookup"><span data-stu-id="9e62f-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="9e62f-110">任何實作 `Object.ToString` 的型別。</span><span class="sxs-lookup"><span data-stu-id="9e62f-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="9e62f-111">任何實作 <xref:System.Collections.Generic.IEnumerable%601> 的型別。</span><span class="sxs-lookup"><span data-stu-id="9e62f-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="9e62f-112">加入複雜內容時，可以將各種型別傳遞到這個方法：</span><span class="sxs-lookup"><span data-stu-id="9e62f-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="9e62f-113">任何實作 <xref:System.Collections.Generic.IEnumerable%601> 的型別</span><span class="sxs-lookup"><span data-stu-id="9e62f-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="9e62f-114">如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="9e62f-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="9e62f-115">如果集合包含 <xref:System.Xml.Linq.XNode> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="9e62f-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="9e62f-116">如果集合包含文字 (或轉換為文字的物件)，集合中的文字會遭到串連，並加入為單一文字節點。</span><span class="sxs-lookup"><span data-stu-id="9e62f-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="9e62f-117">如果內容為 `null`，不會加入任何項目。</span><span class="sxs-lookup"><span data-stu-id="9e62f-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="9e62f-118">傳遞集合時，集合中的項目可以為 `null`。</span><span class="sxs-lookup"><span data-stu-id="9e62f-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="9e62f-119">集合中的 `null` 項目對於樹狀結構沒有任何影響。</span><span class="sxs-lookup"><span data-stu-id="9e62f-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="9e62f-120">加入的屬性在其包含的項目中必須擁有一個唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e62f-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="9e62f-121">加入 <xref:System.Xml.Linq.XNode> 或 <xref:System.Xml.Linq.XAttribute> 物件時，如果新內容沒有父代，則物件只會附加到 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="9e62f-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="9e62f-122">如果新內容已經成為父代，或是其他 XML 樹狀結構的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="9e62f-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="9e62f-123">有效的文件內容</span><span class="sxs-lookup"><span data-stu-id="9e62f-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="9e62f-124">屬性和簡單的內容無法加入到文件中。</span><span class="sxs-lookup"><span data-stu-id="9e62f-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="9e62f-125">需要您建立 <xref:System.Xml.Linq.XDocument> 的案例並不多。</span><span class="sxs-lookup"><span data-stu-id="9e62f-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="9e62f-126">不過，您通常可以使用 <xref:System.Xml.Linq.XElement> 根節點來建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="9e62f-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="9e62f-127">除非您有建立文件的特定需求 (例如，因為您必須在頂層建立處理指示與註解，或者您必須支援文件型別)，否則使用 <xref:System.Xml.Linq.XElement> 做為您的根節點通常更方便。</span><span class="sxs-lookup"><span data-stu-id="9e62f-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="9e62f-128">有效的文件內容包括：</span><span class="sxs-lookup"><span data-stu-id="9e62f-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="9e62f-129">零或一個 <xref:System.Xml.Linq.XDocumentType> 物件。</span><span class="sxs-lookup"><span data-stu-id="9e62f-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="9e62f-130">文件型別必須在項目之前。</span><span class="sxs-lookup"><span data-stu-id="9e62f-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="9e62f-131">零或一個項目。</span><span class="sxs-lookup"><span data-stu-id="9e62f-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="9e62f-132">零或多個註解。</span><span class="sxs-lookup"><span data-stu-id="9e62f-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="9e62f-133">零或多個處理指示。</span><span class="sxs-lookup"><span data-stu-id="9e62f-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="9e62f-134">只包含一個空白字元的零或多個節點。</span><span class="sxs-lookup"><span data-stu-id="9e62f-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="9e62f-135">允許加入內容的建構函式與函式</span><span class="sxs-lookup"><span data-stu-id="9e62f-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="9e62f-136">下列方法可讓您將子內容加入到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>：</span><span class="sxs-lookup"><span data-stu-id="9e62f-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="9e62f-137">方法</span><span class="sxs-lookup"><span data-stu-id="9e62f-137">Method</span></span>|<span data-ttu-id="9e62f-138">描述</span><span class="sxs-lookup"><span data-stu-id="9e62f-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="9e62f-139">建構 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="9e62f-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="9e62f-140">建構 <xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="9e62f-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="9e62f-141">加入到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 之子內容的結尾。</span><span class="sxs-lookup"><span data-stu-id="9e62f-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="9e62f-142">將內容加入到 <xref:System.Xml.Linq.XNode> 之後。</span><span class="sxs-lookup"><span data-stu-id="9e62f-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="9e62f-143">將內容加入到 <xref:System.Xml.Linq.XNode> 之前。</span><span class="sxs-lookup"><span data-stu-id="9e62f-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="9e62f-144">將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的開頭。</span><span class="sxs-lookup"><span data-stu-id="9e62f-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="9e62f-145">取代 <xref:System.Xml.Linq.XElement> 的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="9e62f-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="9e62f-146">取代 <xref:System.Xml.Linq.XElement> 的屬性。</span><span class="sxs-lookup"><span data-stu-id="9e62f-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="9e62f-147">以新的內容取代子節點。</span><span class="sxs-lookup"><span data-stu-id="9e62f-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="9e62f-148">以新內容取代節點。</span><span class="sxs-lookup"><span data-stu-id="9e62f-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e62f-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e62f-149">See also</span></span>

- [<span data-ttu-id="9e62f-150">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e62f-150">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
