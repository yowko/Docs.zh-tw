---
title: 從 DOM 移除節點
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be592466627e6ee7b23c608e0defe786548907ad
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46576557"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="55620-102">從 DOM 移除節點</span><span class="sxs-lookup"><span data-stu-id="55620-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="55620-103">若要從 XML 文件物件模型 (DOM) 移除節點，請使用 <xref:System.Xml.XmlNode.RemoveChild%2A> 方法移除特定的節點。</span><span class="sxs-lookup"><span data-stu-id="55620-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="55620-104">換言之，如果節點不是分葉節點，則在移除節點時，該方法會移除屬於要移除之節點的子樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="55620-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="55620-105">從 DOM 移除多個節點時，可視需要使用 <xref:System.Xml.XmlNode.RemoveAll%2A> 方法，移除目前節點的所有子節點及屬性。</span><span class="sxs-lookup"><span data-stu-id="55620-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="55620-106">如果您正使用 <xref:System.Xml.XmlNamedNodeMap>，則可使用 <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> 方法移除節點。</span><span class="sxs-lookup"><span data-stu-id="55620-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="55620-107">若要移除屬性，請參閱[移除 DOM 中項目節點的屬性](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="55620-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55620-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55620-108">See also</span></span>

- [<span data-ttu-id="55620-109">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="55620-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
