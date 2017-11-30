---
title: "動態更新 NodeList 和 NamedNodeMap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 459d746ff278ac4affa0318c1fad0aeb6a73e560
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="caec4-102">動態更新 NodeList 和 NamedNodeMap</span><span class="sxs-lookup"><span data-stu-id="caec4-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="caec4-103">因為**XmlNodeList**和**XmlNamedNodeMap**包含一組節點，但 XML 文件載入記憶體並且被修改，World Wide Web Consortium (W3C) 指出這些物件包含節點必須是動態的集合。</span><span class="sxs-lookup"><span data-stu-id="caec4-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="caec4-104">也就是，如果基礎文件變更，那麼這兩個物件中的資料也應該變更。</span><span class="sxs-lookup"><span data-stu-id="caec4-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="caec4-105">因此，如果您有**XmlNodeList** ，其中包含所有子項目的特定項目 （例如，項目 X），接著您將新增其他項目，項目 Q 項目 X 下的文件。**XmlNodeList**也應該有該新的項目加入至其集合 Q。</span><span class="sxs-lookup"><span data-stu-id="caec4-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="caec4-106">反之亦然。</span><span class="sxs-lookup"><span data-stu-id="caec4-106">The same is true in reverse.</span></span> <span data-ttu-id="caec4-107">如果節點加入至**XmlNodeList**，也會更新基礎的文件。</span><span class="sxs-lookup"><span data-stu-id="caec4-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caec4-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caec4-108">See Also</span></span>  
 [<span data-ttu-id="caec4-109">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="caec4-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
