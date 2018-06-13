---
title: 實體參考是可擴充且沒有保留
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa03532200a89aa164648c1278c9dbafc2aee214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569527"
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>實體參考是可擴充且沒有保留
當實體參考擴充並且由它所表示的文字所取代時，就不會建立 **XmlEntityReference** 節點。 相反的，實體宣告會剖析，而從宣告中之內容建立的節點會複製到 **XmlEntityReference** 的位置。 因此，在 `&publisher;` 範例中，不會儲存 `&publisher;`，但會建立 **XmlText** 節點。  
  
 ![擴充樹狀結構](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
擴充之實體參考的樹狀  
  
 字元實體 (例如 `B` 或 `<`) 不會予以保留。 相反的，它們一定會擴充且以文字節點表示。  
  
 若要保留 **XmlEntityReference** 節點，以及附加的實體參考子節點，請將 **EntityHandling** 旗標設為 **ExpandCharEntities**。 否則，保留 **EntityHandling** 旗標為預設值，就是 **ExpandEntities**。 在這個範例中，您不會看到 DOM 中的實體參考節點。 節點會被實體宣告的子節點複本的節點取代。  
  
 沒有保留實體參考的其中一項副作用是當文件儲存並且傳入另一個應用程式時，接收的應用程式不知道節點是由實體參考產生。 但當實體參考保留時，接收應用程式將可看見實體參考，並可讀取子節點。 顯然子節點會呈現先前位於實體宣告中的資訊。 例如，如果實體參考是保留的，DOM 理論上會有下列結構。  
  
 XmlElement: publisher  
  
 XmlEntityReference: `&publisher;`  
  
 XmlText: Microsoft Press  
  
 如果實體參考在 DOM 中擴充 (這是預設方法)，此結構擁有這種樹狀結構類型：  
  
 XmlElement: publisher  
  
 XmlText: Microsoft Press  
  
 請注意，當實體參考節點消失時，接收的應用程式無法分辨包含 "Microsoft Press" 的 **XmlText** 節點是從實體宣告建立。  
  
 如果您使用無法解析實體的讀取器，當 **Load** 方法遇到實體參考時，會擲回例外狀況。  
  
## <a name="see-also"></a>請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
