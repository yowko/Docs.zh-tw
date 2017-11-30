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
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>動態更新 NodeList 和 NamedNodeMap
因為**XmlNodeList**和**XmlNamedNodeMap**包含一組節點，但 XML 文件載入記憶體並且被修改，World Wide Web Consortium (W3C) 指出這些物件包含節點必須是動態的集合。 也就是，如果基礎文件變更，那麼這兩個物件中的資料也應該變更。 因此，如果您有**XmlNodeList** ，其中包含所有子項目的特定項目 （例如，項目 X），接著您將新增其他項目，項目 Q 項目 X 下的文件。**XmlNodeList**也應該有該新的項目加入至其集合 Q。 反之亦然。 如果節點加入至**XmlNodeList**，也會更新基礎的文件。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
