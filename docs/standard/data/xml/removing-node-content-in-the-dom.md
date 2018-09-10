---
title: 移除 DOM 中的節點內容
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 737766586ee920a87c25dd42896bdfb14ae69d98
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44205214"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="231ad-102">移除 DOM 中的節點內容</span><span class="sxs-lookup"><span data-stu-id="231ad-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="231ad-103">針對繼承自 <xref:System.Xml.XmlCharacterData> 的 <xref:System.Xml.XmlComment>、<xref:System.Xml.XmlText>、<xref:System.Xml.XmlCDataSection>、<xref:System.Xml.XmlWhitespace> 及 <xref:System.Xml.XmlSignificantWhitespace> 節點型別，您可使用 <xref:System.Xml.XmlCharacterData.DeleteData%2A> 方法移除字元，該方法會移除節點中的字元範圍。</span><span class="sxs-lookup"><span data-stu-id="231ad-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="231ad-104">若要完全移除內容，可以移除包含內容的節點。</span><span class="sxs-lookup"><span data-stu-id="231ad-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="231ad-105">若要保留內容不正確的節點，應修改該節點的內容。</span><span class="sxs-lookup"><span data-stu-id="231ad-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="231ad-106">如需修改節點內容的詳細資訊，請參閱[修改 XML 文件中的節點、內容和值](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)。</span><span class="sxs-lookup"><span data-stu-id="231ad-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="231ad-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="231ad-107">See also</span></span>

- [<span data-ttu-id="231ad-108">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="231ad-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
