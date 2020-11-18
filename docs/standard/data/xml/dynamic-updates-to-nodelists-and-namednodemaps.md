---
title: 動態更新 NodeList 和 NamedNodeMap
ms.date: 03/30/2017
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 2e23507000a780246c129d470b525f19b8b3b9c9
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827655"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>動態更新 NodeList 和 NamedNodeMap
由於 **XmlNodeList** 和 **XmlNamedNodeMap** 都包含一組節點，但 XML 文件會載入記憶體並且被修改，因此全球資訊網協會 (W3C) 指出這些包含節點集的物件都必須為動態。 也就是，如果基礎文件變更，那麼這兩個物件中的資料也應該變更。 因此，若您所擁有的 **XmlNodeList** 含有特定項目 (例如項目 X) 的所有項目子系，就必須在項目 X 下的文件中加入其他項目 (項目 Q)。**XmlNodeList** 也應在其集合中加入這個新項目 Q。 反之亦然。 如果節點加入 **XmlNodeList**，基礎文件也會更新。  
  
## <a name="see-also"></a>請參閱

- [XML 文件物件模型 (DOM)](xml-document-object-model-dom.md)
