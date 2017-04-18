---
title: "使用 IPv6 和 Teredo 的 NAT 周遊 | Microsoft Docs"
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
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# 使用 IPv6 和 Teredo 的 NAT 周遊
在網路位址轉譯 \(NAT\) 周遊 \(NAT\) 支援的改良了。  這些變更是專為與 IPv6 和 Teredo 的使用，但是，也適用於其他 IP 通道技術。  這些增強功能會影響 <xref:System.Net> 和相關的命名空間中的類別。  
  
 這些變更可能會影響計劃使用 IP 通道技術的用戶端和伺服器應用程式。  
  
 為支援 NAT 走訪的變更為應用程式只能使用 .NET Framework 4 版。  這些功能無法在舊版 .NET Framework。  
  
## 概觀  
 網際網路通訊協定第 4 版 \(IPv4\) 長度定義了 IPv4 位址為 32 位元。  因此，支援 IPv4 大約 40 億個唯一的 IP 位址 \(2^32\)。  為電腦和網路裝置數 20 年世紀展開的網際網路， IPv4 位址空間的限制變得明顯。  
  
 用於的幾種方法來擴充存留期 IPv4 是部署 NAT 允許單一唯一公用 IP 位址表示大量私人 IP 位址 \(私用內部網路\)。  在 NAT 裝置之後的私人 IP 位址共用單一公用 IPv4 位址。  NAT 裝置可能是專屬的硬體裝置 \(例如不耗費無線存取點和路由器\)，或是執行服務的電腦提供 NAT。  一個裝置或服務公開這個 IP 位址的轉譯 IP 網路封包在公用網際網路和私用內部網路之間。  
  
 這項配置是用於將要求傳送至其他 IP 位址在私用內部網路上的用戶端應用程式運作正常 \(通常是伺服器\) 在網際網路上。  以回應在何處傳回它知道傳送回應時， NAT 裝置或伺服器以這種方式保留用戶端要求對應。  但是，此配置會想要提供服務，接聽封包，並回應在私用內部網路的應用程式時出現問題 NAT 裝置之後。  這是對等應用程式的特定行為。  
  
 IPv6 通訊協定長度定義了 IPv4 位址為 128 位元。  因此，不支援 IPv6 非常大 IP 位址空間 3.2 x 10^38 唯一的位址 \(2^128\)。  這個大小位址空間中，為每個裝置可以是連接到要重新命名的網際網路有唯一的位址。  但是，有問題。  許多世界仍然只使用 IPv4。  請特別注意，許多現有的路由器和小型公司、組織、Home 使用的無線存取點不支援 IPv6。  也提供這些客戶服務的某些網際網路服務提供者不支援或尚未設定支援 IPv6。  
  
 數個 IPv6 轉換技術所開發的通道 IPv6 在 IPv4 封包的位址。  這些技術包括 6to4、ISATAP 和 IPv6 流量提供對單點傳送位址配置和主應用程式會裝載自動 Teredo 通道的通道，當 IPv6 主應用程式必須執行設計 IP4 網路到達其他 IPv6 網路時。  IPv6 封包傳送通道做為 IPv4 封包。  數個通道技術將 NAT 裝置允許的 IPv6 位址 NAT 走訪使用。  
  
 Teredo 為 IPv4 Web 帶 IPv6 連接的其中一個 IPv6 轉換技術。  Teredo 在網際網路工程任務推動小組 \(Internet Engineering Task Force，\(IETF\) 4380 文件發行的 RFC \(IETF\)。  Windows XP SP2 和才有可能提供在範圍 2001:0::\/32 公開 IPv6 位址的虛擬 Teredo 配接器之後的支援。  這個 IPv6 位址用來接聽來自網際網路的連入連線，並且可以提供給 IPv6 要連接到接聽的服務啟用用戶端。  使用其 Teredo IPv6 位址，，，因為應用程式可以連接到這項資訊是從擔心釋放一個應用程式如何處理在一 NAT 裝置之後的電腦。  
  
## 支援 NAT 走訪和 Teredo 的加強功能  
 使用 IPv6 和 Teredo，增強功能加入至 <xref:System.Net>、 <xref:System.Net.NetworkInformation>和 <xref:System.Net.Sockets> 命名空間支援的 NAT 走訪。  
  
 有幾個方法加入至 <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=fullName> 類別取得主機的單點傳送 IP 位址清單。  <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> 方法會啟動非同步要求擷取本機電腦上的穩定單點傳送 IP 位址資料表。  <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> 方法結束暫止非同步要求擷取本機電腦上的穩定單點傳送 IP 位址資料表。  <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> 方法是同步要求擷取本機電腦上的穩定單點傳送 IP 位址表，等候，直到 Address 資料表 \(如果需要的話，穩定運作。  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=fullName> 屬性可以用來判斷是否為 <xref:System.Net.IPAddress> Teredo IPv6 位址。  
  
 使用 <xref:System.Net.IPAddress.IsIPv6Teredo%2A> 屬性組合這些新 <xref:System.Net.NetworkInformation.IPGlobalProperties> 類別的方法允許應用程式輕鬆地尋找 Teredo 位址。  如果傳遞這項資訊至遠端應用程式，應用程式通常只需要知道區域 Teredo 位址。  例如，對等應用程式可能會傳送其所有 IPv6 位址加入至可轉送給其他對等電腦啟用直接通訊的做媒伺服器。  
  
 應用程式在 <xref:System.Net.IPAddress.IPv6Any?displayProperty=fullName> 通常應該將它設定為接聽的服務接聽而不是在區域 Teredo 位址。  因此，如果遠端用戶端或對等電腦有一條直接 IPv6 路由至接聽的服務主機，用戶端或對等電腦可以直接連接使用 IPv6 和不需要使用 Teredo 通道封包。  
  
 若是 TCP 應用程式， <xref:System.Net.Sockets.TcpListener?displayProperty=fullName> 類別具有可讓某個 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> 的方法 NAT 走訪。  如需建立應用程式， <xref:System.Net.Sockets.UdpClient?displayProperty=fullName> 類別具有可讓某個 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> 的方法 NAT 走訪。  
  
 使用 <xref:System.Net.Sockets.Socket?displayProperty=fullName> ，和相關類別、 <xref:System.Net.Sockets.Socket.GetSocketOption%2A> 和 <xref:System.Net.Sockets.Socket.SetSocketOption%2A> 方法可以配合 <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName> 通訊端選項查詢的應用程式中，啟用或停用 NAT 走訪。  
  
## 請參閱  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName>   
 <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=fullName>