---
title: "保留實體參照"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 770c714e8f5942ea733c417ae9b06f69e4acf1a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-preserved"></a>保留實體參照
當實體參照並未擴充，但保留時，XML 文件物件模型 (DOM) 建置**XmlEntityReference**時遇到實體參照節點。  
  
 使用下列 XML，  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 DOM 建置**XmlEntityReference**節點時遇到`&publisher;`參考。 **XmlEntityReference**包含從實體宣告中的內容複製的子節點。 上述程式碼範例包含實體宣告中，因此**XmlText**節點會建立為實體參照節點的子節點。  
  
 ![保留的實體參考的樹狀](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
保留之實體參照的樹狀  
  
 子節點**XmlEntityReference**是複本的所有子節點建立從**XmlEntity**節點時遇到實體宣告。  
  
> [!NOTE]
>  從複製的節點**XmlEntity**不一定是曾置於實體參照節點下的完整複本。 在實體參照節點的範圍中可能有命名空間，這會影響子節點的最後組態。  
  
 根據預設，之類的一般實體`&abc;`會保留和**XmlEntityReference**一律所建立的節點。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
