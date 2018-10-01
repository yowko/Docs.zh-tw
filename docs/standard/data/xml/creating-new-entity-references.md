---
title: 建立新實體參考
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67fdbcdbff64bcd91c80fbeaec0c41982b68d98f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47203371"
---
# <a name="creating-new-entity-references"></a>建立新實體參考
**CreateEntityReference** 方法建立新 **XmlEntityReference** 節點。 XML 文件物件模型 (DOM) 會查看所要參考的實體名稱是否已進行宣告。 如果是，**XmlEntityReference** 節點的子節點會從實體宣告節點複製。 如果沒有符合的實體宣告，會將空白文字節點當成實體參考節點的唯一子代附加上去。 因為 **XmlEntityReference** 節點的子節點是其他節點的複本，因此這些子節點是唯讀的而且無法修改。  
  
 複製節點時，在實體參考的範圍可能有命名空間。 這個命名空間影響任何產生的項目或屬性節點的組態。  
  
> [!NOTE]
>  只有在您將 **EntityReference** 節點插入文件時，DOM 才會將子節點加入 **EntityReference**。 新建的 **EntityReference** 節點沒有子節點。  
  
 雖然 **XmlDataDocument** 是 **XmlDocument** 的衍生類別，但是 **XmlDataDocument** 卻不能建立實體參考。 這是因為 **EntityReference** 子系是唯讀的。 **EntityReference** 節點的子系可以擴展一個以上的區域。 因此，與包含部分 **EntityReference** 的區域相關之資料列的部分也會是唯讀的。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
