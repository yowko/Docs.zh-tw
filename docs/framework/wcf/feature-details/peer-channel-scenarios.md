---
title: "對等通道案例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 62ea53cf5a96519c864e48dc48e28ed81e3b6d8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="peer-channel-scenarios"></a>對等通道案例
對等通道 API 支援下列開發案例。  
  
## <a name="publicationsubscription-messaging"></a>發行/訂閱訊息  
 建置發行/訂閱應用程式 (例如，股票行情和新聞頭條、運動成績和氣象報告發行者) 的公司可以使用對等通道來建立無伺服器的應用程式。 例如，使用者只要加入一般網狀結構 (或用戶端群組) 即可獲知最新的運動成績，並可傳播大量最新的競賽資料而不會增加伺服器負載。 這種方法可以協助資料提供者提供更高品質的服務，而不必大幅增加對於伺服器技術的投資。  
  
## <a name="collaboration"></a>共同作業  
 獨立軟體廠商 (Independent Software Vendor，ISV) 所建立的應用程式，可讓人們建立用於參與對等活動的緊密群組。 例如，這個群組包括處理共同專案的團隊、在朋友之間共享照片、規劃派對的活動等。 傳統上，這些活動一定會涉及伺服器；不過，對等通道實現了一種無法輕易在傳統伺服器/用戶端模型下實作的離線存取案例，透過這種案例，以更節省成本的方式來提供這項服務。  
  
## <a name="distributed-processing-and-compute-clusters"></a>分散式處理和計算叢集  
 計算叢集和分散式處理一般會用在大型計算作業上，例如財務/氣象模型和進行人類 DNA 的解碼。 一般來說，伺服器會個別將工作指派給參與計算叢集的所有用戶端來完成這項作業。 但這些伺服器可能也有其他需求；例如，可能需要在特定期間內完成所有工作，因此每個工作所需的電腦就不只一台。 此外，如果執行工作的任何用戶端發生問題，其他用戶端必須能夠接手該作業，並繼續處理。 同樣地，可能需要多個用戶端一起執行相同的工作，以確保結果一致。 儘管伺服器可執行這種類型的用戶端協調作業，您還是可以建立對等解決方案，讓接收工作的用戶端可獨立判斷處理工作的伺服器需求，並使用計算網狀結構來判斷完成該工作的方式。  
  
## <a name="gaming"></a>遊戲  
 使用對等通道時，應用程式開發人員可以建立無伺服器版本的遊戲，也就是透過對等機制而非中央伺服器，傳輸遊戲進度並與其他玩家同步。 針對小型 ISV，這個機制可以省下部署、維護和保養中央伺服器的相關作業成本。 使用對等架構撰寫的遊戲可以在整個網際網路、有線或無線區域網路上進行。 您也可以使用對等網路開發輔助遊戲活動，例如大廳和在遊戲中交談。  
  
## <a name="see-also"></a>另請參閱  
 [對等通道概念](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
