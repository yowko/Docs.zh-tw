---
title: "載入 DOM 時處理泛空白字元和顯著泛空白字元"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>載入 DOM 時處理泛空白字元和顯著泛空白字元
當載入文件，您可以設定的選項來保留泛空白字元，並且建立**XmlWhitespace**文件樹狀結構中的節點。 若要建立泛空白字元節點，設定**PreserveWhitespace**屬性設定為 true。 如果屬性設定為**false**、 預設值時，不會建立泛空白字元節點。 顯著泛空白字元節點一定會被保留，和**XmlSignificantWhitespace**節點一律會建立在記憶體中，表示這個資料，不論設定為何**PreserveWhitespace**旗標。  
  
 從讀取器載入文件，然後設定**PreserveWhitespace**旗標屬性**XmlDocument**類別會影響建立**XmlWhitespace**節點只有當**Xmldocument**屬性**XmlTextReader**未設定為**WhitespaceHandling.None**。 值是**Xmldocument**屬性優先於該旗標的設定的讀取器上**XmlDocument**。 如需有關**XmlSignificantWhitespace**，請參閱<xref:System.Xml.XmlSignificantWhitespace>。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
