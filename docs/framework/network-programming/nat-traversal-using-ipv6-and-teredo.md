---
title: "使用 IPv6 和 Teredo 的 NAT 周遊"
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
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
caps.latest.revision: 6
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d1730e5af0ee3f837f46071992c80e81b118af1e
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>使用 IPv6 和 Teredo 的 NAT 周遊
已進行支援網路位址轉譯 (NAT) 周遊的增強功能。 這些變更設計成與 IPv6 和 Teredo 搭配使用，但也適用於其他 IP 通道技術。 這些增強功能會影響 <xref:System.Net> 和相關命名空間中的類別。  
  
 這些變更可能會影響計劃使用 IP 通道技術的用戶端和伺服器應用程式。  
  
 支援 NAT 周遊的變更只適用於使用 .NET Framework 第 4 版的應用程式。 舊版 .NET Framework 無法使用這些功能。  
  
## <a name="overview"></a>概觀  
 網際網路通訊協定第 4 版 (IPv4) 已將 IPv4 位址的長度定義為 32 位元。 因此，IPv4 大約支援 40 億個唯一 IP 位址 (2^32)。 因為網際網路上的電腦和網路裝置數目已在 1990 年代擴充，所以 IPv4 位址空間限制變得明顯。  
  
 數個用來擴充 IPv4 存留期的其中一個技術是部署 NAT，以允許單一唯一公用 IP 位址代表大量私人 IP 位址 (私人內部網路)。 受 NAT 裝置保護的私人 IP 位址會共用單一公用 IPv4 位址。 NAT 裝置可能是專用硬體裝置 (例如，便宜的無線存取點和路由器) 或執行服務來提供 NAT 的電腦。 此公用 IP 位址的裝置或服務會在公用網際網路與私人內部網路之間轉譯 IP 位址封包。  
  
 此配置適用於在私人內部網路上執行的用戶端應用程式，而這些用戶端應用程式會將要求傳送給網際網路上的其他 IP 位址 (通常是伺服器)。 NAT 裝置或伺服器可以保留用戶端要求的對應；因此，它在傳回回應時會知道傳送回應的位置。 但針對在受 NAT 裝置保護且想要提供服務、接聽封包以及回應之私人內部網路中執行的應用程式，此配置會造成問題。 這是專用於對等應用程式的情況。  
  
 IPv6 通訊協定已將 IPv4 位址的長度定義為 128 位元。 因此，IPv6 支援 3.2 x 10^38 唯一位址 (2^128) 的大型 IP 位址空間。 有了此大小的位址空間之後，每個連線至網際網路的裝置就可能獲指定唯一位址。 但會發生問題。 全世界大部分仍然都只使用 IPv4。 特別的是，小型公司、組織和住家所使用的許多現有路由器和無線存取點都不支援 IPv6。 而且，有些服務這些客戶的網際網路服務提供者不支援或尚未設定 IPv6 支援。  
  
 已開發數個 IPv6 轉換技術，對 IPv4 封包中的 IPv6 位址進行通道處理。 這些技術所包含的 6to4、ISATAP 和 Teredo 通道在 IPv6 主機必須周遊 IP4 網路以連線至其他 IPv6 網路時，提供單點傳播 IPv6 流量的位址指派以及主機對主機自動通道。 IPv6 封包是以通道方式傳送為 IPv4 封包。 將會使用數個通道技術來允許透過 NAT 裝置進行 IPv6 位址的 NAT 周遊。  
  
 Teredo 是其中一種 IPv6 轉換技術，具有與 IPv4 網路的 IPv6 連線。 網際網路工程任務推動小組 (IETF) 發行的 RFC 4380 中已記載 Teredo。 Windows XP SP2 和更新版本所支援的虛擬 Teredo 配接器可以提供 2001:0::/32 範圍中的公用 IPv6 位址。 這個 IPv6 位址可以用來接聽來自網際網路的連入連線，並且可以提供給具 IPv6 功能且想要連線至接聽端服務的用戶端。 這讓應用程式不用擔心如何處理受 NAT 裝置保護的電腦，因為應用程式只能使用其 IPv6 Teredo 位址與之連線。  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>支援 NAT 周遊和 Teredo 的增強功能  
 在 <xref:System.Net>、<xref:System.Net.NetworkInformation> 和 <xref:System.Net.Sockets> 命名空間中新增增強功能，以支援使用 IPv6 和 Teredo 進行 NAT 周遊。  
  
 <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=fullName> 類別中已新增數個方法，來取得主機上的單點傳播 IP 位址清單。 <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> 方法會開始非同步要求，以擷取本機電腦上的穩定單點傳播 IP 位址表格。 <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> 方法會結束暫止非同步要求，以擷取本機電腦上的穩定單點傳播 IP 位址表格。 <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> 方法是同步要求，以擷取本機電腦上的穩定單點傳播 IP 位址表格，並視需要等到位址表格穩定為止。  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=fullName> 屬性可以用來判斷 <xref:System.Net.IPAddress> 是否為 IPv6 Teredo 位址。  
  
 搭配使用這些新 <xref:System.Net.NetworkInformation.IPGlobalProperties> 類別方法與 <xref:System.Net.IPAddress.IsIPv6Teredo%2A> 屬性，可讓應用程式輕鬆地找到 Teredo 位址。 如果應用程式將這項資訊與遠端應用程式進行通訊，則通常只需要知道本機 Teredo 位址。 例如，對等應用程式可能會將其所有 IPv6 位址傳送給配對伺服器，而配對伺服器接著可以將它們轉送給其他對等來啟用直接通訊。  
  
 應用程式通常應該設定其接聽服務接聽 <xref:System.Net.IPAddress.IPv6Any?displayProperty=fullName>，而不是本機 Teredo 位址。 因此，如果遠端用戶端或對等具有接聽服務主機的直接 IPv6 路由，則用戶端或對等可以使用 IPv6 直接連線，而不需要使用 Teredo 對封包進行通道處理。  
  
 針對 TCP 應用程式，<xref:System.Net.Sockets.TcpListener?displayProperty=fullName> 類別具有 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> 方法來啟用 NAT 周遊。 針對 UDP 應用程式，<xref:System.Net.Sockets.UdpClient?displayProperty=fullName> 類別具有 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> 方法來啟用 NAT 周遊。  
  
 針對使用 <xref:System.Net.Sockets.Socket?displayProperty=fullName> 和相關類別的應用程式，可以搭配使用 <xref:System.Net.Sockets.Socket.GetSocketOption%2A> 和 <xref:System.Net.Sockets.Socket.SetSocketOption%2A> 方法與 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=fullName> 通訊端選項來查詢、啟用或停用 NAT 周遊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName>   
 <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=fullName>

