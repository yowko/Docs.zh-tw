---
title: "NamedNodeMap 和 NodeList 中的節點集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 025954b8-7aa8-47c5-a1c1-f81064fb4d65
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ff327c1a450e9ce712d496bdca2cd2ebbff6adda
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="node-collections-in-namednodemaps-and-nodelists"></a>NamedNodeMap 和 NodeList 中的節點集合
您可以擷取一組節點，並且將它放入已排序或未排序的集合。 全球資訊網協會 (W3C) 將一組置於未排序之集合的節點稱為 NamedNodeMap；您可以根據這種集合型別的名稱或索引來擷取資料。 而 W3C 將一組置於已排序之集合的節點稱為 NodeList，可以使用從零開始的索引擷取資料。 NamedNodeMaps 和 NodeLists 是由 W3C 說明。 在 Microsoft .NET Framework 中，NamedNodeMap 的實作是 **XmlNamedNodeMap**，而 NodeList 則由 **XmlNodeList** 實作。  
  
 如需未排序之集合的詳細資訊，請參閱[根據名稱或索引擷取的未排序節點](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md)。 如需已排序之集合的詳細資訊，請參閱[根據索引擷取的已排序節點](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md)。  
  
## <a name="see-also"></a>請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
