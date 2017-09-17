---
title: "網際網路通訊協定第 6 版"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
caps.latest.revision: 11
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7901084f38099d74f3bcde086342bd3c90b34348
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# 網際網路通訊協定第 6 版
網際網路通訊協定第 6 版 (IPv6) 是網際網路網路層級的新標準通訊協定套件。 IPv6 旨在解決網際網路通訊協定當前版本 (稱為 IPv4) 有關位址耗竭、安全性、自動組態和擴充性等等的許多問題。 IPv6 展開網際網路的功能，以啟用新種類的應用程式，包括點對點與行動應用程式。 以下是目前 IPv4 通訊協定的主要問題：  
  
-   快速消耗位址空間。  
  
     這導致使用網路位址轉譯器 (NAT) 將多個私人位址對應到單一公用 IP 位址。 這項機制引起的主要問題是處理額外負荷以及缺乏端對端連線。  
  
-   缺少階層式支援。  
  
     因為其固有的預先定義類別組織，IPv4 缺少真正的階層式支援。 不可能以真正對應網路拓撲的方式來建立 IP 位址的結構。 此一重大的設計缺陷創造了對大型路由表的需求，以將 IPv4 封包傳遞至網際網路上的任何位置。  
  
-   複雜的網路組態。  
  
     使用 IPv4，必須以靜態方式或使用 DHCP 等組態通訊協定指派位址。 理想的情況下，主機可能不必依賴 DHCP 基礎結構的管理。 相反地，它們可以根據所在的網路區段自行設定。  
  
-   缺少內建的驗證和機密性。  
  
     IPv4 不需要任何提供交換資料驗證或加密之機制的支援。 這會隨著 IPv6 變更。 網際網路通訊協定安全性 (IPSec) 是 IPv6 支援需求。  
  
 新的通訊協定套件必須滿足下列基本需求：  
  
-   低額外負荷的大規模路由和定址。  
  
-   各種連線情況的自動組態。  
  
-   內建的驗證和機密性。  
  
 如需詳細資訊，請參閱 [IPv6 定址](../../../docs/framework/network-programming/ipv6-addressing.md)、[IPv6 路由](../../../docs/framework/network-programming/ipv6-routing.md)、[IPv6 自動組態](../../../docs/framework/network-programming/ipv6-auto-configuration.md)、[啟用和停用 IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md) 以及[如何：修改電腦組態檔以啟用 IPv6 支援](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)。  
  
## 參考  
 以下是您可在網際網路工程任務推動小組網站中找到的精選 RFC 文件 ([http://www.ietf.org](http://www.ietf.org/))：  
  
-   RFC 1287，前進未來網際網路架構。  
  
-   RFC 1454，下一版 IP 的建議比較。  
  
-   RFC 2373，IP 第 6 版定址架構。  
  
-   RFC 2374，IPv6 彙總全域單點傳播位址格式。  
  
 您也可以在 [Technet 的 IPv6 區域](http://go.microsoft.com/fwlink/?LinkID=179658)找到 IPv6 的相關資訊。  
  
## 另請參閱  
 [IPv6 通訊端範例](http://go.microsoft.com/fwlink/?LinkID=179568)   
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)   
 [通訊端](../../../docs/framework/network-programming/sockets.md)

