---
title: "實體參考是可擴充且沒有保留"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 069d3b94a0269917400e75fdbe975ec39dcfdb71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>實體參考是可擴充且沒有保留
當實體參考擴充並且由它所表示的文字取代**XmlEntityReference**就不會建立節點。 相反地，實體宣告會剖析，並從宣告中的內容建立的節點複製中取代的**XmlEntityReference**。 因此，在`&publisher;`範例中，`&publisher;`未儲存，而是， **XmlText**會建立節點。  
  
 ![展開樹狀結構](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
擴充之實體參考的樹狀結構  
  
 字元實體 (例如 `B` 或 `<`) 不會予以保留。 相反的，它們一定會擴充且以文字節點表示。  
  
 若要保留**XmlEntityReference**節點，以及實體參考子節點附加，將**EntityHandling**旗標設為**ExpandCharEntities**。 否則，保留**EntityHandling**旗標為預設值，也就是**ExpandEntities**。 在這個範例中，您不會看到 DOM 中的實體參考節點。 節點會被實體宣告的子節點複本的節點取代。  
  
 沒有保留實體參考的其中一項副作用是當文件儲存並且傳入另一個應用程式時，接收的應用程式不知道節點是由實體參考產生。 但當實體參考保留時，接收應用程式將可看見實體參考，並可讀取子節點。 顯然子節點會呈現先前位於實體宣告中的資訊。 例如，如果實體參考是保留的，DOM 理論上會有下列結構。  
  
 XmlElement: publisher  
  
 XmlEntityReference: `&publisher;`  
  
 XmlText: Microsoft Press  
  
 如果實體參考在 DOM 中擴充 (這是預設方法)，此結構擁有這種樹狀結構類型：  
  
 XmlElement: publisher  
  
 XmlText: Microsoft Press  
  
 請注意，實體參考節點已經消失，並接收應用程式無法分辨**XmlText**節點包含"Microsoft Press"已建立從實體宣告。  
  
 如果您使用的讀取器無法解析實體，**負載**方法在遇到實體參考時，會擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
