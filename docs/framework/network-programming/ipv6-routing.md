---
title: "IPv6 路由 | Microsoft Docs"
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
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
caps.latest.revision: 4
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 4
---
# IPv6 路由
具有彈性的路由機制是 IPv6 的優點。  由於 IPv4 網路 ID 和配置的方式，大路由表中需要由是在網際網路骨 Clerk 的路由器維護。  這些路由器必須知道所有路徑來轉送可能會導向至網際網路之所有節點的封包。  使用它可以彙總 IPv6 位址，允許彈性處理及大幅減少路由表中的大小。  在這個新的定址的架構下，中繼路由器必須只保留追蹤他們的網路的本機部分才能正確地轉寄訊息。  
  
## 尋找附近。  
 附近尋找提供的部分功能:  
  
-   路由器會出現。  這可讓主機識別區域路由器。  
  
-   位址轉換。  這可讓節點名稱解析成對應的躍點下的位址 \(位址轉換通訊協定的 ARP 取代的連結層位址\)。  
  
-   位址自動配置。  如此可讓主應用程式自動設定網站區域和全域位址。  
  
 附近尋找為 IPv6 版 \(ICMPv6\) 訊息使用中的網際網路控制訊息通訊協定:  
  
-   "路由器通告。  傳送由路由器根據空定期基礎或是回應"路由器請求"。  IPv6 路由器使用它們的可用性、位址首碼和其他參數通告的"路由器通告。  
  
-   "路由器請求"。  傳送由主應用程式需要此連結的路由器立即傳送路由器通告。  
  
-   "近鄰請求"。  送出位址轉換的節點，重複的位址偵測，或是確認相鄰面某部電腦。  
  
-   周圍的廣告。  送出的回應"近鄰請求"或通知內變更的鄰近的連結層位址上。  
  
-   重新導向。  傳送路由器表示較佳下躍點位址至傳送的節點的特殊目的。  
  
## 請參閱  
 [網際網路通訊協定第 6 版](../../../docs/framework/network-programming/internet-protocol-version-6.md)   
 [通訊端](../../../docs/framework/network-programming/sockets.md)