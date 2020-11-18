---
title: 保留實體參照
ms.date: 03/30/2017
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: 2cc2fcf3fdc2a89e4f72ae65e6e7385cb83f168c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823832"
---
# <a name="entity-references-are-preserved"></a>保留實體參照
當實體參照並未擴充但保留下來時，若 XML 文件物件模型 (DOM) 遇到實體參照，就會建置 **XmlEntityReference** 節點。  
  
 使用下列 XML，  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 當 DOM 遇到 `&publisher;` 參照時，就會建置 **XmlEntityReference** 節點。 **XmlEntityReference** 包含從實體宣告中的內容所複製的子節點。 先前的程式碼範例包含實體宣告中的文字，因此 **XmlText** 節點會建立為實體參照節點的子節點。  
  
 ![保留實體參考的樹狀](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
保留之實體參照的樹狀  
  
 **XmlEntityReference** 的子節點是在遇到實體宣告時，由 **XmlEntity** 節點建立的所有子節點的複本。  
  
> [!NOTE]
> 從 **XmlEntity** 複製的節點不一定就是曾置於實體參照節點下的複本。 在實體參照節點的範圍中可能有命名空間，這會影響子節點的最後組態。  
  
 根據預設，會保留 `&abc;` 之類的一般實體，且一律會建立 **XmlEntityReference** 節點。  
  
## <a name="see-also"></a>請參閱

- [XML 文件物件模型 (DOM)](xml-document-object-model-dom.md)
