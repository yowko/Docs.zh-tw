---
title: "修改 XML 文件中的節點、內容和值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 72039faef3bcde4db830d110938266c63689219e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a><span data-ttu-id="631bb-102">修改 XML 文件中的節點、內容和值</span><span class="sxs-lookup"><span data-stu-id="631bb-102">Modifying Nodes, Content, and Values in an XML Document</span></span>
<span data-ttu-id="631bb-103">有許多方法可以修改文件中的節點及內容。</span><span class="sxs-lookup"><span data-stu-id="631bb-103">There are many ways you can modify the nodes and content in a document.</span></span> <span data-ttu-id="631bb-104">您可以：</span><span class="sxs-lookup"><span data-stu-id="631bb-104">You can:</span></span>  
  
-   <span data-ttu-id="631bb-105">使用 <xref:System.Xml.XmlNode.Value%2A> 屬性變更節點的值。</span><span class="sxs-lookup"><span data-stu-id="631bb-105">Change the value of nodes using the <xref:System.Xml.XmlNode.Value%2A> property.</span></span>  
  
-   <span data-ttu-id="631bb-106">藉由以新節點取代節點，修改整個節點集。</span><span class="sxs-lookup"><span data-stu-id="631bb-106">Modify an entire set of nodes by replacing the nodes with new nodes.</span></span> <span data-ttu-id="631bb-107">這可以使用 <xref:System.Xml.XmlNode.InnerXml%2A> 屬性來完成。</span><span class="sxs-lookup"><span data-stu-id="631bb-107">This is done using the <xref:System.Xml.XmlNode.InnerXml%2A> property.</span></span>  
  
-   <span data-ttu-id="631bb-108">使用 <xref:System.Xml.XmlNode.RemoveChild%2A> 方法，以新節點取代現有節點。</span><span class="sxs-lookup"><span data-stu-id="631bb-108">Replace existing nodes with new nodes using the <xref:System.Xml.XmlNode.RemoveChild%2A> method.</span></span>  
  
-   <span data-ttu-id="631bb-109">使用 <xref:System.Xml.XmlCharacterData>、<xref:System.Xml.XmlCharacterData.AppendData%2A> 或 <xref:System.Xml.XmlCharacterData.InsertData%2A> 方法，將其他字元加入繼承自 <xref:System.Xml.XmlCharacterData.ReplaceData%2A> 類別的節點。</span><span class="sxs-lookup"><span data-stu-id="631bb-109">Add additional characters to nodes that inherit from the <xref:System.Xml.XmlCharacterData> class using the <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A>, or <xref:System.Xml.XmlCharacterData.ReplaceData%2A> methods.</span></span>  
  
-   <span data-ttu-id="631bb-110">使用繼承自 <xref:System.Xml.XmlCharacterData.DeleteData%2A> 之節點型別上的 <xref:System.Xml.XmlCharacterData> 方法，藉由移除某範圍的字元來修改內容。</span><span class="sxs-lookup"><span data-stu-id="631bb-110">Modify the content by removing a range of characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method on node types that inherit from <xref:System.Xml.XmlCharacterData>.</span></span>  
  
 <span data-ttu-id="631bb-111">變更節點值的簡單技術是使用 `node.Value = "new value";`。</span><span class="sxs-lookup"><span data-stu-id="631bb-111">A simple technique for changing the value of a node is to use `node.Value = "new value";`.</span></span> <span data-ttu-id="631bb-112">下表列出此單行程式碼適用的節點型別，以及該節點型別已變更的確切資料。</span><span class="sxs-lookup"><span data-stu-id="631bb-112">The following table lists the node types that this single line of code works on and exactly what data for that node type is changed.</span></span>  
  
|<span data-ttu-id="631bb-113">節點類型</span><span class="sxs-lookup"><span data-stu-id="631bb-113">Node type</span></span>|<span data-ttu-id="631bb-114">變更的資料</span><span class="sxs-lookup"><span data-stu-id="631bb-114">Data changed</span></span>|  
|---------------|------------------|  
|<span data-ttu-id="631bb-115">屬性</span><span class="sxs-lookup"><span data-stu-id="631bb-115">Attribute</span></span>|<span data-ttu-id="631bb-116">屬性的值。</span><span class="sxs-lookup"><span data-stu-id="631bb-116">The value of the attribute.</span></span>|  
|<span data-ttu-id="631bb-117">CDATASection</span><span class="sxs-lookup"><span data-stu-id="631bb-117">CDATASection</span></span>|<span data-ttu-id="631bb-118">CDATASection 的內容。</span><span class="sxs-lookup"><span data-stu-id="631bb-118">The content of the CDATASection.</span></span>|  
|<span data-ttu-id="631bb-119">註解</span><span class="sxs-lookup"><span data-stu-id="631bb-119">Comment</span></span>|<span data-ttu-id="631bb-120">註解的內容。</span><span class="sxs-lookup"><span data-stu-id="631bb-120">The content of the comment.</span></span>|  
|<span data-ttu-id="631bb-121">ProcessingInstruction</span><span class="sxs-lookup"><span data-stu-id="631bb-121">ProcessingInstruction</span></span>|<span data-ttu-id="631bb-122">內容 (目標除外)。</span><span class="sxs-lookup"><span data-stu-id="631bb-122">The content, excluding the target.</span></span>|  
|<span data-ttu-id="631bb-123">Text</span><span class="sxs-lookup"><span data-stu-id="631bb-123">Text</span></span>|<span data-ttu-id="631bb-124">文字的內容。</span><span class="sxs-lookup"><span data-stu-id="631bb-124">The content of the text.</span></span>|  
|<span data-ttu-id="631bb-125">XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="631bb-125">XmlDeclaration</span></span>|<span data-ttu-id="631bb-126">宣告的內容 (`<?xml` 及 `?>` 標記除外)。</span><span class="sxs-lookup"><span data-stu-id="631bb-126">The content of the declaration, excluding the `<?xml` and `?>` markup.</span></span>|  
|<span data-ttu-id="631bb-127">Whitespace</span><span class="sxs-lookup"><span data-stu-id="631bb-127">Whitespace</span></span>|<span data-ttu-id="631bb-128">泛空白字元的值。</span><span class="sxs-lookup"><span data-stu-id="631bb-128">The value of the white space.</span></span> <span data-ttu-id="631bb-129">該值可以設為四個可以辨識的 XML 空白字元其中之一：空格、定位字元、CR 或 LF。</span><span class="sxs-lookup"><span data-stu-id="631bb-129">You can set the value to be one of the four recognized XML white space characters: space, tab, CR, or LF.</span></span>|  
|<span data-ttu-id="631bb-130">SignificantWhitespace</span><span class="sxs-lookup"><span data-stu-id="631bb-130">SignificantWhitespace</span></span>|<span data-ttu-id="631bb-131">顯著泛空白字元的值。</span><span class="sxs-lookup"><span data-stu-id="631bb-131">The value of the significant white space.</span></span> <span data-ttu-id="631bb-132">該值可以設為四個可以辨識的 XML 空白字元其中之一：空格、定位字元、CR 或 LF。</span><span class="sxs-lookup"><span data-stu-id="631bb-132">You can set the value to be one of the four recognized XML white space characters: space, tab, CR, or LF.</span></span>|  
  
 <span data-ttu-id="631bb-133">未列在表格中的任何節點型別都是無效節點型別，不可設定值。</span><span class="sxs-lookup"><span data-stu-id="631bb-133">Any node type not listed in the table is not a valid node type to set a value on.</span></span> <span data-ttu-id="631bb-134">在任何其他節點型別上設定值都會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="631bb-134">Setting a value on any other node type throws an <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="631bb-135"><xref:System.Xml.XmlNode.InnerXml%2A> 屬性會變更目前節點之子節點的標記。</span><span class="sxs-lookup"><span data-stu-id="631bb-135">The <xref:System.Xml.XmlNode.InnerXml%2A> property changes the markup of the child nodes for the current node.</span></span> <span data-ttu-id="631bb-136">設定此屬性，會以指定字串的已剖析內容取代子節點。</span><span class="sxs-lookup"><span data-stu-id="631bb-136">Setting this property replaces the child nodes with the parsed contents of the given string.</span></span> <span data-ttu-id="631bb-137">剖析會在目前命名空間內容中完成。</span><span class="sxs-lookup"><span data-stu-id="631bb-137">The parsing is done in the current namespace context.</span></span> <span data-ttu-id="631bb-138">此外，<xref:System.Xml.XmlNode.InnerXml%2A> 會移除多餘的命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="631bb-138">In addition, <xref:System.Xml.XmlNode.InnerXml%2A> removes redundant namespace declarations.</span></span> <span data-ttu-id="631bb-139">因此，大量的剪貼作業並不會因為有多餘的命名空間宣告，而增加文件大小。</span><span class="sxs-lookup"><span data-stu-id="631bb-139">As a result, numerous cut and paste operations do not increase the size of your document with redundant namespace declarations.</span></span> <span data-ttu-id="631bb-140">如需顯示 <xref:System.Xml.XmlNode.InnerXml%2A> 作業上命名空間效果的程式碼範例，請參閱 <xref:System.Xml.XmlDocument.InnerXml%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="631bb-140">For a code example showing the effect of namespaces on the <xref:System.Xml.XmlNode.InnerXml%2A> operation, see the <xref:System.Xml.XmlDocument.InnerXml%2A> property.</span></span>  
  
 <span data-ttu-id="631bb-141">當使用 <xref:System.Xml.XmlCharacterData.ReplaceData%2A> 及 <xref:System.Xml.XmlNode.RemoveChild%2A> 方法時，方法會傳回已取代或已移除的節點。</span><span class="sxs-lookup"><span data-stu-id="631bb-141">When using the <xref:System.Xml.XmlCharacterData.ReplaceData%2A> and <xref:System.Xml.XmlNode.RemoveChild%2A> methods, the methods return the replaced or removed node.</span></span> <span data-ttu-id="631bb-142">然後，可以將此節點重新插入至 XML 文件物件模型 (DOM) 中的任何其他位置。</span><span class="sxs-lookup"><span data-stu-id="631bb-142">This node can then be reinserted somewhere else in the XML Document Object Model (DOM).</span></span> <span data-ttu-id="631bb-143"><xref:System.Xml.XmlCharacterData.ReplaceData%2A> 方法會在插入至文件的節點上進行兩個驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="631bb-143">The <xref:System.Xml.XmlCharacterData.ReplaceData%2A> method does two validation checks on the node being inserted into the document.</span></span> <span data-ttu-id="631bb-144">第一個檢查可確保該節點已成為可以擁有其型別子節點之節點的子項。</span><span class="sxs-lookup"><span data-stu-id="631bb-144">The first check ensures that the node is becoming a child of a node that can have child nodes of its type.</span></span> <span data-ttu-id="631bb-145">第二個檢查可確保插入的節點不是其成為子項之節點的上階。</span><span class="sxs-lookup"><span data-stu-id="631bb-145">The second check ensures that the node being inserted is not an ancestor of the node it is becoming a child of.</span></span> <span data-ttu-id="631bb-146">違反任何一個條件，都會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="631bb-146">Violating either of these conditions throws an <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="631bb-147">在可編輯之節點中加入或移除唯讀子節點有效。</span><span class="sxs-lookup"><span data-stu-id="631bb-147">It is valid to add or remove a read-only child from a node that can be edited.</span></span> <span data-ttu-id="631bb-148">不過，嘗試修改唯讀節點本身會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="631bb-148">However, attempts to modify the read-only node itself throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="631bb-149">修改 <xref:System.Xml.XmlEntityReference> 節點的子節點便是一個範例。</span><span class="sxs-lookup"><span data-stu-id="631bb-149">An example of this is modifying the children of an <xref:System.Xml.XmlEntityReference> node.</span></span> <span data-ttu-id="631bb-150">子節點是唯讀的，而且無法修改。</span><span class="sxs-lookup"><span data-stu-id="631bb-150">The children are read-only and cannot be modified.</span></span> <span data-ttu-id="631bb-151">對其進行修改的任何嘗試，都會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="631bb-151">Any attempt to modify them throws an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="631bb-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="631bb-152">See Also</span></span>  
 [<span data-ttu-id="631bb-153">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="631bb-153">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
