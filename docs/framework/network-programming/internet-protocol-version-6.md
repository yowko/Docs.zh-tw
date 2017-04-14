---
title: "網際網路通訊協定第 6 版 | Microsoft Docs"
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
helpviewer_keywords: 
  - "IPv6，增強功能"
  - "IPv4"
  - "IPv6"
  - "網際網路通訊協定第 6 版，增強功能"
  - "網際網路通訊協定第 6 版"
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 網際網路通訊協定第 6 版
網際網路通訊協定第 6 版 \(IPv6\) 是標準通訊協定新的套件網際網路的網路層。  IPv6 是設計來解決許多網際網路通訊協定套件的目前版本的問題 \(稱為 IPv4\) 有關位址範圍結尾，安全性，自動配置，擴充性，依此類推。  IPv6 展開網際網路的功能啟用新類型的應用程式，包括對等和行動應用程式。  以下是目前 IPv4 通訊協定的主題:  
  
-   位址空間的快速而造成。  
  
     這個前置字元使用的網路位址轉譯器 \(NATs\) 與對應多個私人位址單一公用 IP 位址。  這個機制建立的主要問題處理成本和缺少端對端連接。  
  
-   缺少階層架構支援。  
  
     由於其繼承的預先定義的分類來組織， IPv4 缺少真正的階層式的支援。  結構 IP 位址以真正對應網路拓撲的方法是不可能的。  這個金鑰的設計上的缺陷已建立需要大量路由表中傳送 IPv4 封包至網際網路上的任何位置。  
  
-   複雜網路組態。  
  
     使用 IPv4，必須以靜態方式指派位址或使用組態通訊協定 \(例如 DHCP。  在理想情況下，主應用程式不需要依賴、基礎結構的管理。  相反地，它們可以自行配置是根據其網路區段。  
  
-   沒有內建驗證和機密性。  
  
     IPv4 不提供已交換資料的驗證或加密的任何機制必須支援。  這會隨著 IPv6。  網際網路通訊協定安全性 \(IPSec\) 是 IPv6 支援需要。  
  
 新的通訊協定套件必須滿足下列基本需求:  
  
-   大型路由並解決與低額外負荷。  
  
-   各種連接的情況下自動配置。  
  
-   內建驗證和機密性。  
  
 如需詳細資訊，請參閱 [IPv6 定址](../../../docs/framework/network-programming/ipv6-addressing.md)、[IPv6 路由](../../../docs/framework/network-programming/ipv6-routing.md)、[IPv6 自動設定](../../../docs/framework/network-programming/ipv6-auto-configuration.md)、[啟用和停用 IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md)和[如何：修改電腦設定檔案以啟用 IPv6 支援](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)。  
  
## 參考  
 以下是您可以在網際網路工程任務推動小組 \(Internet Engineering Task Force，\(IETF\) 站台中的選項的 RFC 文件 \([http:\/\/www.ietf.org](http://www.ietf.org/)\):  
  
-   向未來網際網路架構的 RFC 1287 的定義。  
  
-   RFC 1454，提供比較對於 IP 下一個版本。  
  
-   RFC 2373， IP 第 6 版位址的結構。  
  
-   RFC 2374， Aggregatable 全域 Unicast IPv6 位址格式。  
  
 您也可以提供有關的 [如果在 Technet 的區域](http://go.microsoft.com/fwlink/?LinkID=179658)IPv6 相關的資訊。  
  
## 請參閱  
 [IPv6 Sockets 範例](http://go.microsoft.com/fwlink/?LinkID=179568)   
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)   
 [通訊端](../../../docs/framework/network-programming/sockets.md)