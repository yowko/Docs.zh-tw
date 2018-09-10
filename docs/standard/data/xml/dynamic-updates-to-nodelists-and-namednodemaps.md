---
title: 動態更新 NodeList 和 NamedNodeMap
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f56ba8711988f2f7d743dc4ff7b69272e2642a2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44207404"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="3c2a4-102">動態更新 NodeList 和 NamedNodeMap</span><span class="sxs-lookup"><span data-stu-id="3c2a4-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="3c2a4-103">由於 **XmlNodeList** 和 **XmlNamedNodeMap** 都包含一組節點，但 XML 文件會載入記憶體並且被修改，因此全球資訊網協會 (W3C) 指出這些包含節點集的物件都必須為動態。</span><span class="sxs-lookup"><span data-stu-id="3c2a4-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="3c2a4-104">也就是，如果基礎文件變更，那麼這兩個物件中的資料也應該變更。</span><span class="sxs-lookup"><span data-stu-id="3c2a4-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="3c2a4-105">因此，若您所擁有的 **XmlNodeList** 含有特定項目 (例如項目 X) 的所有項目子系，就必須在項目 X 下的文件中加入其他項目 (項目 Q)。**XmlNodeList** 也應在其集合中加入這個新項目 Q。</span><span class="sxs-lookup"><span data-stu-id="3c2a4-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="3c2a4-106">反之亦然。</span><span class="sxs-lookup"><span data-stu-id="3c2a4-106">The same is true in reverse.</span></span> <span data-ttu-id="3c2a4-107">如果節點加入 **XmlNodeList**，基礎文件也會更新。</span><span class="sxs-lookup"><span data-stu-id="3c2a4-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c2a4-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c2a4-108">See also</span></span>

- [<span data-ttu-id="3c2a4-109">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="3c2a4-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
