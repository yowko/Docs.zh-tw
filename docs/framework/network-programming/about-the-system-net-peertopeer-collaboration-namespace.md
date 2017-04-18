---
title: "關於 System.Net.PeerToPeer.Collaboration 命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
caps.latest.revision: 4
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 4
---
# 關於 System.Net.PeerToPeer.Collaboration 命名空間
<xref:System.Net.PeerToPeer.Collaboration> 命名空間提供使用對等共同作業基礎結構，可用來實作對等共同作業活動的類別和 API。  
  
## 類別  
 用於對等共同作業活動之實作的主要類別為:  
  
-   <xref:System.Net.PeerToPeer.Collaboration.ContactManager>，可用來儲存對等連絡人。  
  
-   的 <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> 共同作業，例如遊戲、交談用戶端或工作階段方案。  
  
-   在 活動共同作業的對等電腦。  這些對等個體可以表示為 <xref:System.Net.PeerToPeer.Collaboration.PeerContact>、 <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>或 <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> 物件。  
  
-   靜態 <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> 類別，指定應用程式是否可用，以及哪些對等電腦參與它們。  
  
 <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> 方法用於邀請對等電腦共同作業工作階段。  指定呼叫的對等電腦可以訂閱通知更新至應用程式、物件或狀態資訊參與共同作業工作階段之事件的其他對等電腦。  類別存在指定 <xref:System.Net.PeerToPeer.Collaboration.Peer> 是否為共同作業，就可以使用，並 <xref:System.Net.PeerToPeer.Collaboration.PeerScope> 類別是用來指定要參與允許對等電腦: <xref:System.Net.PeerToPeer.Collaboration.PeerScope> \(全域\)， <xref:System.Net.PeerToPeer.Collaboration.PeerScope>子網路，或 <xref:System.Net.PeerToPeer.Collaboration.PeerScope>。  
  
 共同作業工作階段包含四個步驟:  
  
-   要尋找的。  尋找或發行應用程式、對等物件和顯示狀態資訊。  例如，找出具有相同的結果安裝區域子網路的其他人員。  
  
-   邀請。  尋找並接受遠端對等電腦的安全性邀請啟動或已 <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> 工作階段。  
  
-   與管理連接。  將找到的對等電腦做為連絡人的 <xref:System.Net.PeerToPeer.Collaboration.ContactManager>。  
  
-   通訊。  當建立通訊時，請使用 <xref:System.Net> API， <xref:System.Net.PeerToPeer> API，或 Windows Communication Foundation 對等通道的多方通訊分類。  
  
 例如，主機對等電腦啟動共同作業工作階段，並套用 <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> 方法加入遠端對等電腦和一個本機對等電腦加入至主機對等電腦的連絡人管理員。  三個使用者會參與它自己的私用共同作業工作階段。  
  
 典型的 P2P 應用程式為:為共同作業注意接受或 whiteboarding 的呼叫工作階段，無伺服器交談應用程式、互動式廣告與連接移動對於工作階段。  
  
## 請參閱  
 <xref:System.Net.PeerToPeer.Collaboration>