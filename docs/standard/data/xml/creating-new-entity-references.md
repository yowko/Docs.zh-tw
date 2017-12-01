---
title: "建立新實體參考"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22e9b66f58275141cf9da154573ca43a0b90affc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-entity-references"></a>建立新實體參考
**CreateEntityReference**方法建立新**XmlEntityReference**節點。 XML 文件物件模型 (DOM) 會查看所要參考的實體名稱是否已進行宣告。 如果有，子節點的**XmlEntityReference**節點會從實體宣告節點複製。 如果沒有符合的實體宣告，會將空白文字節點當成實體參考節點的唯一子代附加上去。 因為子節點的**XmlEntityReference**節點是其他節點的複本，這些子節點是唯讀而且無法修改。  
  
 複製節點時，在實體參考的範圍可能有命名空間。 這個命名空間影響任何產生的項目或屬性節點的組態。  
  
> [!NOTE]
>  DOM 將子節點至**EntityReference**只有當您插入**EntityReference**文件的節點。 新建立的**EntityReference**節點有任何子節點。  
  
 即使**XmlDataDocument**衍生類別的**XmlDocument**、 **XmlDataDocument**不支援建立實體參考。 這是因為**EntityReference**子系是唯讀狀態。 子系**EntityReference**節點可以跨越多個區域。 資料列的一部分在此情況下，包含的組件的區域相關聯**EntityReference**將處於唯讀模式。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
