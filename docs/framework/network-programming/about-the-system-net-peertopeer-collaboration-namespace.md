---
title: "關於 System.Net.PeerToPeer.Collaboration 命名空間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 24571209673d7706955bdb9ffbe21ad6da98e18a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>關於 System.Net.PeerToPeer.Collaboration 命名空間
<xref:System.Net.PeerToPeer.Collaboration> 命名空間提供使用對等共同作業基礎結構，可用來實作對等共同作業活動的類別和 API。  
  
## <a name="classes"></a>類別  
 用於對等共同作業活動之實作的主要類別如下：  
  
-   <xref:System.Net.PeerToPeer.Collaboration.ContactManager>，可用來儲存對等連絡人。  
  
-   要在其中進行共同作業的 <xref:System.Net.PeerToPeer.Collaboration.PeerApplication>，例如遊戲、交談用戶端或會議解決方案。  
  
-   將在活動中共同作業的同儕節點。  這些同儕節點可以 <xref:System.Net.PeerToPeer.Collaboration.PeerContact>、<xref:System.Net.PeerToPeer.Collaboration.PeerNearMe> 或 <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> 物件表示。  
  
-   靜態 <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> 類別本身，其指定哪些應用程式可用以及哪些同儕節點會參與它們。  
  
 <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> 方法可用來邀請同儕節點加入共同作業工作階段。  呼叫端同儕節點可以訂閱另一個同儕節點的事件，以指出附屬於共同作業工作階段的應用程式、物件或目前狀態資訊的更新。 目前狀態類別指定 <xref:System.Net.PeerToPeer.Collaboration.Peer> 是否可用於共同作業，而 <xref:System.Net.PeerToPeer.Collaboration.PeerScope> 類別用來指定同儕節點允許的參與數目：<xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (全域)、<xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe> (子網路) 或 <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>。  
  
 共同作業工作階段包含四個步驟：  
  
-   探索。 探索或發佈應用程式、同儕節點和目前狀態資訊。  例如，找出本機子網路上已安裝相同遊戲的其他人。  
  
-   邀請。 傳送和接受遠端同儕節點的安全邀請，以啟動或加入 <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> 工作階段。  
  
-   管理連絡人。 將探索到的同儕節點作為連絡人加入 <xref:System.Net.PeerToPeer.Collaboration.ContactManager>。  
  
-   通訊。 建立通訊時，請使用 <xref:System.Net> API、<xref:System.Net.PeerToPeer> API 或 Windows Communication Foundation 對等通道類別來進行多方通訊。  
  
 例如，主機同儕節點會啟動共同作業工作階段，並利用 <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> 方法，將遠端同儕節點和其中一個本機同儕節點加入主機同儕節點的連絡人管理員。  接著，這三個使用者將參與自己的私用共同作業工作階段。  
  
 P2P 應用程式通常是：共同作業筆記記錄或白板的電話會議、無伺服器交談應用程式、互動式廣告以及線上遊戲工作階段。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Net.PeerToPeer.Collaboration>
