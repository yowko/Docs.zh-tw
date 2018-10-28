---
title: 以 .NET Framework 進行網路程式設計
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
ms.openlocfilehash: 1d35951aef3692d82bdfa648df48eb8c1bca88ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188075"
---
# <a name="network-programming-in-the-net-framework"></a>以 .NET Framework 進行網路程式設計
Microsoft .NET Framework 提供有層次、可擴充和網際網路服務的 Managed 實作，可以迅速而簡易地整合到您的應用程式。 您的網路應用程式可以建置在可外掛式通訊協定上，以便自動利用新的網際網路通訊協定，或者也可以使用 Windows Socket 介面的 Managed 實作，以便搭配使用通訊端層級上的網路。  
  
## <a name="in-this-section"></a>本節內容  

 [可插式通訊協定簡介](../../../docs/framework/network-programming/introducing-pluggable-protocols.md)  
 說明如何存取網際網路資源而不用考慮需要的存取通訊協定。  
  
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)  
 說明如何使用可外掛式通訊協定從網際網路資源上傳和下載資料。  
  
 [可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 說明如何衍生通訊協定特定類別以實作可外掛式通訊協定。  
  
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)  
 說明如何設計使用網路通訊協定 (例如 TCP、UDP 和 HTTP) 的應用程式。  
  
 [網際網路通訊協定第 6 版](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 說明在目前版本的網際網路通訊協定組合 (IPv4) 之上網際網路通訊協定第 6 版 (IPv6) 的優點，描述 IPv6 位址、路由和自動設定，以及如何啟用和停用 IPv6。  
  
 [設定網際網路應用程式](../../../docs/framework/network-programming/configuring-internet-applications.md)  
 說明如何使用 .NET Framework 組態檔以設定網際網路應用程式。  
  
 [以 .NET Framework 進行網路追蹤](../../../docs/framework/network-programming/network-tracing.md)  
 說明如何使用網路追蹤以取得有關方法叫用及 Managed 應用程式所產生的網路流量的資訊。  
  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 說明如何針對使用 <xref:System.Net.WebClient?displayProperty=nameWithType>、 <xref:System.Net.WebRequest?displayProperty=nameWithType>和 <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> 類別的應用程式來使用快取。  
  
 [網路程式設計的安全性](../../../docs/framework/network-programming/security-in-network-programming.md)  
 描述如何使用標準網際網路安全性和驗證技術。  
  
 [System.Net 類別的最佳做法](../../../docs/framework/network-programming/best-practices-for-system-net-classes.md)  
 提供可讓您善用網際網路應用程式的祕訣和訣竅。  
  
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 描述如何設定 Proxy。  
  
 [NetworkInformation](../../../docs/framework/network-programming/networkinformation.md)  
 描述如何蒐集網路事件、變更、統計資料和屬性的相關資訊，以及說明如何判斷遠端主機是否可以使用 <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> 類別取得聯繫。  
  
 [2.0 版中 System.Uri 命名空間的變更](../../../docs/framework/network-programming/changes-to-the-system-uri-namespace-in-version-2-0.md)  
 說明在版本 2.0 中對 <xref:System.Uri?displayProperty=nameWithType> 類別所做的幾個變更，以修正不正確的行為、提高可用性，以及增強安全性。  
  
 [System.Uri 的國際資源識別項支援](../../../docs/framework/network-programming/international-resource-identifier-support-in-system-uri.md)  
 說明在版本 3.5、3.0 SP1 和 2.0 SP1 中的 <xref:System.Uri?displayProperty=nameWithType> 類別增強功能，以支援國際資源識別項 (IRI) 和國際化網域名稱 (IDN)。  
  
 [3.5 版中的通訊端效能增強功能](../../../docs/framework/network-programming/socket-performance-enhancements-in-version-3-5.md)  
 說明在版本 3.5、3.0 SP1 和 2.0 SP1 中 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> 類別的一組增強功能，其提供另一種非同步模式，可供專業化的高效能通訊端應用程式使用。  
  
 [對等名稱解析通訊協定](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)  
 說明在版本 3.5 中所新增的支援，以支援對等名稱解析通訊協定 (PNRP)、無伺服器和動態名稱登錄以及名稱解析通訊協定。 這些新功能是由 <xref:System.Net.PeerToPeer?displayProperty=nameWithType> 命名空間所支援。  
  
 [對等共同作業](../../../docs/framework/network-programming/peer-to-peer-collaboration.md)  
 說明在版本 3.5 中所新增的支援，以支援建置在 PNRP 上的對等協同作業。 這些新功能是由 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> 命名空間所支援。  
  
 [3.5 SP1 版中 HttpWebRequest 之 NTLM 驗證的變更](../../../docs/framework/network-programming/changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 說明在版本 3.5 SP1 中所做的安全性變更，這些變更會影響 <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>、 <xref:System.Net.HttpListener?displayProperty=nameWithType>、 <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>以及 System.Net 命名空間中的相關類別處理整合式 Windows 驗證的方式。  
  
 [具有延伸保護的整合式 Windows 驗證](../../../docs/framework/network-programming/integrated-windows-authentication-with-extended-protection.md)  
 說明延伸保護的增強功能，這些增強功能會影響 <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>、 <xref:System.Net.HttpListener?displayProperty=nameWithType>、 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>、 <xref:System.Net.Security.SslStream?displayProperty=nameWithType>、 <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>以及 <xref:System.Net?displayProperty=nameWithType> 和相關命名空間中的相關類別處理整合式 Windows 驗證的方式。  
  
 [使用 IPv6 和 Teredo 的 NAT 周遊](../../../docs/framework/network-programming/nat-traversal-using-ipv6-and-teredo.md)  
 說明 <xref:System.Net?displayProperty=nameWithType>、 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>和 <xref:System.Net.Sockets?displayProperty=nameWithType> 命名空間所新增的增強功能，以支援使用 IPv6 和 Teredo 進行 NAT 周遊。  
  
 [Windows 市集應用程式的網路隔離](../../../docs/framework/network-programming/network-isolation-for-windows-store-apps.md)  
 說明當 <xref:System.Net>、 <xref:System.Net.Http>和 <xref:System.Net.Http.Headers> 命名空間中的類別用於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式時，網路隔離的影響。  
  
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)  
 可供下載的網路程式設計範例的連結，這些範例會使用 <xref:System.Net>、 <xref:System.Net.Cache>、 <xref:System.Net.Configuration>、 <xref:System.Net.Mail>、 <xref:System.Net.Mime>、 <xref:System.Net.NetworkInformation>、 <xref:System.Net.PeerToPeer>、 <xref:System.Net.Security>以及 <xref:System.Net.Sockets> 命名空間中的類別。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Net?displayProperty=nameWithType>  
 提供一個簡單的程式設計介面，讓現今網路所用的許多通訊協定使用。 此命名空間中的 <xref:System.Net.WebRequest?displayProperty=nameWithType> 和 <xref:System.Net.WebResponse?displayProperty=nameWithType> 類別是可外掛式通訊協定的基礎。  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 可定義類型和列舉，這些類型和列舉是用來定義使用 <xref:System.Net.WebRequest?displayProperty=nameWithType> 和 <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> 類別所取得之資源的快取原則。  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 應用程式用來以程式設計方式存取及更新 System.Net 命名空間組態設定的類別。  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 可為現代 HTTP 應用程式提供程式設計介面的類別。  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 為 <xref:System.Net.Http?displayProperty=nameWithType> 命名空間所使用的 HTTP 標頭集合提供支援  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 用於使用 SMTP 通訊協定撰寫及傳送郵件的類別。  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 可定義類型，這些類型是用於表示 <xref:System.Net.Mail?displayProperty=nameWithType> 命名空間中的類別所使用的多用途網際網路郵件交換 (MIME) 標頭。  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 以程式設計方式收集網路事件、變更、統計資料和屬性的相關資訊的類別。  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 為開發人員提供對等名稱解析通訊協定 (PNRP) 的 Managed 實作。  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 為開發人員提供對等協同作業介面的 Managed 實作。  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 用於提供主機之間安全通訊的網路資料流的類別。  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 提供 Windows Sockets (Winsock) 介面的 Managed 實作，讓需要協助控制網路存取的開發人員使用。  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 為開發人員提供 WebSocket 介面的 Managed 實作。  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 提供統一資源識別元 (URI) 的物件表示，以及對 URI 各部分的簡易存取。  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 為應用程式提供使用延伸保護進行驗證的支援。  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 為應用程式提供使用延伸保護設定驗證組態的支援。  
  
## <a name="see-also"></a>請參閱  

 [.NET Framework 的傳輸層安全性 (TLS) 最佳做法](../../../docs/framework/network-programming/tls.md)  
 [網路程式設計「如何」主題](../../../docs/framework/network-programming/network-programming-how-to-topics.md)  
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)  
 [MSDN Code Gallery 上的 .NET 網路範例](https://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)  
 [HttpClient 範例](https://go.microsoft.com/fwlink/?LinkId=242550)
