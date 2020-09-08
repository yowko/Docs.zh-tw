---
title: System.xml.linq.xelement> 和 XDocument 物件的有效內容-LINQ to XML
description: System.xml.linq.xelement> 和 XDocument 的函式會接受許多引數類型，包括從查詢傳回的集合。 還有其他的函式和函式可用於新增 XML 內容。
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: e0288dce06f8040385c9b9a30335fd039d3c45bd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552777"
---
# <a name="valid-content-of-xelement-and-xdocument-objects-linq-to-xml"></a><span data-ttu-id="88d19-104">System.xml.linq.xelement> 和 XDocument 物件的有效內容 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="88d19-104">Valid content of XElement and XDocument objects (LINQ to XML)</span></span>

<span data-ttu-id="88d19-105">本文描述可傳遞給函式的有效引數，以及您用來將內容加入至專案和檔的方法。</span><span class="sxs-lookup"><span data-stu-id="88d19-105">This article describes the valid arguments that can be passed to constructors, and methods that you use to add content to elements and documents.</span></span>

## <a name="valid-types-for-the-xelement-constructor"></a><span data-ttu-id="88d19-106">System.xml.linq.xelement> 函式的有效類型</span><span class="sxs-lookup"><span data-stu-id="88d19-106">Valid types for the XElement constructor</span></span>

<span data-ttu-id="88d19-107">查詢通常會評估成 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 或 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="88d19-107">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="88d19-108">您可以將 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件的集合傳遞給 <xref:System.Xml.Linq.XElement> 建構函式。</span><span class="sxs-lookup"><span data-stu-id="88d19-108">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="88d19-109">這就是為什麼將查詢結果當作內容傳遞至您用來填入 XML 樹狀結構的方法和函式很方便的原因。</span><span class="sxs-lookup"><span data-stu-id="88d19-109">That's why it's convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>

<span data-ttu-id="88d19-110">新增簡單的內容時，可以將各種類型傳遞給這個方法，包括：</span><span class="sxs-lookup"><span data-stu-id="88d19-110">When adding simple content, various types can be passed to this method, including::</span></span>

- <xref:System.String>
- <xref:System.Double>
- <xref:System.Single>
- <xref:System.Decimal>
- <xref:System.Boolean>
- <xref:System.DateTime>
- <xref:System.TimeSpan>
- <xref:System.DateTimeOffset>
- <span data-ttu-id="88d19-111">任何實作 `Object.ToString` 的型別。</span><span class="sxs-lookup"><span data-stu-id="88d19-111">Any type that implements `Object.ToString`.</span></span>
- <span data-ttu-id="88d19-112">任何實作 <xref:System.Collections.Generic.IEnumerable%601> 的型別。</span><span class="sxs-lookup"><span data-stu-id="88d19-112">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="88d19-113">新增複雜的內容時，可以將各種類型傳遞給這個方法，包括：</span><span class="sxs-lookup"><span data-stu-id="88d19-113">When adding complex content, various types can be passed to this method, including:</span></span>

- <xref:System.Xml.Linq.XObject>
- <xref:System.Xml.Linq.XNode>
- <xref:System.Xml.Linq.XAttribute>
- <span data-ttu-id="88d19-114">實作 <xref:System.Collections.Generic.IEnumerable%601> 的任何類型</span><span class="sxs-lookup"><span data-stu-id="88d19-114">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>

<span data-ttu-id="88d19-115">如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="88d19-115">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="88d19-116">如果集合包含 <xref:System.Xml.Linq.XNode> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="88d19-116">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="88d19-117">如果集合包含文字 (或轉換為文字的物件)，集合中的文字會遭到串連，並加入為單一文字節點。</span><span class="sxs-lookup"><span data-stu-id="88d19-117">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>

<span data-ttu-id="88d19-118">如果內容為 `null`，不會加入任何項目。</span><span class="sxs-lookup"><span data-stu-id="88d19-118">If content is `null`, nothing is added.</span></span> <span data-ttu-id="88d19-119">傳遞集合時，集合中的專案可以是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="88d19-119">When passing a collection, items in the collection can be `null`.</span></span> <span data-ttu-id="88d19-120">集合中的 `null` 項目對於樹狀結構沒有任何影響。</span><span class="sxs-lookup"><span data-stu-id="88d19-120">A `null` item in the collection has no effect on the tree.</span></span>

<span data-ttu-id="88d19-121">加入的屬性在其包含的項目中必須擁有一個唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="88d19-121">An added attribute must have a unique name within its containing element.</span></span>

<span data-ttu-id="88d19-122">加入 <xref:System.Xml.Linq.XNode> 或 <xref:System.Xml.Linq.XAttribute> 物件時，如果新內容沒有父代，則物件只會附加到 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="88d19-122">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="88d19-123">如果新內容已經成為父代，或是其他 XML 樹狀結構的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="88d19-123">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>

## <a name="valid-types-for-the-xdocument-constructor"></a><span data-ttu-id="88d19-124">XDocument 函式的有效類型</span><span class="sxs-lookup"><span data-stu-id="88d19-124">Valid types for the XDocument constructor</span></span>

<span data-ttu-id="88d19-125">屬性和簡單的內容無法加入到文件中。</span><span class="sxs-lookup"><span data-stu-id="88d19-125">Attributes and simple content can't be added to a document.</span></span>

<span data-ttu-id="88d19-126">在許多情況下，您不需要建立 <xref:System.Xml.Linq.XDocument> 。</span><span class="sxs-lookup"><span data-stu-id="88d19-126">There aren't many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="88d19-127">不過，您通常可以使用 <xref:System.Xml.Linq.XElement> 根節點來建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="88d19-127">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="88d19-128">除非您有特定需求來建立檔 (例如，因為您必須在最上層建立處理指示和批註，或您必須支援) 的檔案類型，否則使用 <xref:System.Xml.Linq.XElement> 做為根節點通常會更方便。</span><span class="sxs-lookup"><span data-stu-id="88d19-128">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it's often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>

<span data-ttu-id="88d19-129">有效的函式類型 <xref:System.Xml.Linq.XDocument.%23ctor%2A> 包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="88d19-129">Valid types for the <xref:System.Xml.Linq.XDocument.%23ctor%2A> constructor include the following:</span></span>

- <span data-ttu-id="88d19-130">零或一個 <xref:System.Xml.Linq.XDocumentType> 物件。</span><span class="sxs-lookup"><span data-stu-id="88d19-130">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="88d19-131">文件型別必須在項目之前。</span><span class="sxs-lookup"><span data-stu-id="88d19-131">The document types must come before the element.</span></span>
- <span data-ttu-id="88d19-132">零或一個項目。</span><span class="sxs-lookup"><span data-stu-id="88d19-132">Zero or one element.</span></span>
- <span data-ttu-id="88d19-133">零或多個註解。</span><span class="sxs-lookup"><span data-stu-id="88d19-133">Zero or more comments.</span></span>
- <span data-ttu-id="88d19-134">零或多個處理指示。</span><span class="sxs-lookup"><span data-stu-id="88d19-134">Zero or more processing instructions.</span></span>
- <span data-ttu-id="88d19-135">只包含一個空白字元的零或多個節點。</span><span class="sxs-lookup"><span data-stu-id="88d19-135">Zero or more text nodes that contain only white space.</span></span>

## <a name="constructors-and-functions-for-adding-content"></a><span data-ttu-id="88d19-136">用於新增內容的函式和函式</span><span class="sxs-lookup"><span data-stu-id="88d19-136">Constructors and functions for adding content</span></span>

<span data-ttu-id="88d19-137">下列方法可讓您將子內容加入到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>：</span><span class="sxs-lookup"><span data-stu-id="88d19-137">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>

|<span data-ttu-id="88d19-138">方法</span><span class="sxs-lookup"><span data-stu-id="88d19-138">Method</span></span>|<span data-ttu-id="88d19-139">描述</span><span class="sxs-lookup"><span data-stu-id="88d19-139">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="88d19-140">建構 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="88d19-140">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="88d19-141">建構 <xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="88d19-141">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="88d19-142">加入到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 之子內容的結尾。</span><span class="sxs-lookup"><span data-stu-id="88d19-142">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="88d19-143">將內容加入到 <xref:System.Xml.Linq.XNode> 之後。</span><span class="sxs-lookup"><span data-stu-id="88d19-143">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="88d19-144">將內容加入到 <xref:System.Xml.Linq.XNode> 之前。</span><span class="sxs-lookup"><span data-stu-id="88d19-144">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="88d19-145">將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的開頭。</span><span class="sxs-lookup"><span data-stu-id="88d19-145">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="88d19-146">取代 <xref:System.Xml.Linq.XElement> 的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="88d19-146">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="88d19-147">取代 <xref:System.Xml.Linq.XElement> 的屬性。</span><span class="sxs-lookup"><span data-stu-id="88d19-147">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="88d19-148">以新的內容取代子節點。</span><span class="sxs-lookup"><span data-stu-id="88d19-148">Replaces the children nodes with new content.</span></span>|
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="88d19-149">以新內容取代節點。</span><span class="sxs-lookup"><span data-stu-id="88d19-149">Replaces a node with new content.</span></span>|

## <a name="see-also"></a><span data-ttu-id="88d19-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88d19-150">See also</span></span>

- [<span data-ttu-id="88d19-151">XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="88d19-151">XML trees</span></span>](functional-construction.md)
