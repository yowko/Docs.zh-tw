---
title: 以 .NET Framework 進行網路程式設計
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f4ed8fa218e97f4a6b06bd1c8a06d9b300b16119
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646966"
---
# <a name="network-programming-in-the-net-framework"></a><span data-ttu-id="1d3bb-102">以 .NET Framework 進行網路程式設計</span><span class="sxs-lookup"><span data-stu-id="1d3bb-102">Network Programming in the .NET Framework</span></span>
<span data-ttu-id="1d3bb-103">Microsoft .NET Framework 提供有層次、可擴充和網際網路服務的 Managed 實作，可以迅速而簡易地整合到您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-103">The Microsoft .NET Framework provides a layered, extensible, and managed implementation of Internet services that can be quickly and easily integrated into your applications.</span></span> <span data-ttu-id="1d3bb-104">您的網路應用程式可以建置在可外掛式通訊協定上，以便自動利用新的網際網路通訊協定，或者也可以使用 Windows Socket 介面的 Managed 實作，以便搭配使用通訊端層級上的網路。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-104">Your network applications can build on pluggable protocols to automatically take advantage of new Internet protocols, or they can use a managed implementation of the Windows socket interface to work with the network on the socket level.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d3bb-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="1d3bb-105">In This Section</span></span>  

 [<span data-ttu-id="1d3bb-106">可插式通訊協定簡介</span><span class="sxs-lookup"><span data-stu-id="1d3bb-106">Introducing Pluggable Protocols</span></span>](../../../docs/framework/network-programming/introducing-pluggable-protocols.md)  
 <span data-ttu-id="1d3bb-107">說明如何存取網際網路資源而不用考慮需要的存取通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-107">Describes how to access an Internet resource without regard to the access protocol that it requires.</span></span>  
  
 [<span data-ttu-id="1d3bb-108">要求資料</span><span class="sxs-lookup"><span data-stu-id="1d3bb-108">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 <span data-ttu-id="1d3bb-109">說明如何使用可外掛式通訊協定從網際網路資源上傳和下載資料。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-109">Explains how to use pluggable protocols to upload and download data from Internet resources.</span></span>  
  
 [<span data-ttu-id="1d3bb-110">可插式通訊協定程式設計</span><span class="sxs-lookup"><span data-stu-id="1d3bb-110">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 <span data-ttu-id="1d3bb-111">說明如何衍生通訊協定特定類別以實作可外掛式通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-111">Explains how to derive protocol-specific classes to implement pluggable protocols.</span></span>  
  
 [<span data-ttu-id="1d3bb-112">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="1d3bb-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 <span data-ttu-id="1d3bb-113">說明如何設計使用網路通訊協定 (例如 TCP、UDP 和 HTTP) 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-113">Describes programming applications that take advantage of network protocols such as TCP, UDP, and HTTP.</span></span>  
  
 [<span data-ttu-id="1d3bb-114">網際網路通訊協定第 6 版</span><span class="sxs-lookup"><span data-stu-id="1d3bb-114">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 <span data-ttu-id="1d3bb-115">說明在目前版本的網際網路通訊協定組合 (IPv4) 之上網際網路通訊協定第 6 版 (IPv6) 的優點，描述 IPv6 位址、路由和自動設定，以及如何啟用和停用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-115">Describes the advantages of Internet Protocol version 6 (IPv6) over the current version of the Internet Protocol suite (IPv4), describes IPv6 addressing, routing and auto-configuration, and how to enable and disable IPv6.</span></span>  
  
 [<span data-ttu-id="1d3bb-116">設定網際網路應用程式</span><span class="sxs-lookup"><span data-stu-id="1d3bb-116">Configuring Internet Applications</span></span>](../../../docs/framework/network-programming/configuring-internet-applications.md)  
 <span data-ttu-id="1d3bb-117">說明如何使用 .NET Framework 組態檔以設定網際網路應用程式。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-117">Explains how to use the .NET Framework configuration files to configure Internet applications.</span></span>  
  
 [<span data-ttu-id="1d3bb-118">以 .NET Framework 進行網路追蹤</span><span class="sxs-lookup"><span data-stu-id="1d3bb-118">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)  
 <span data-ttu-id="1d3bb-119">說明如何使用網路追蹤以取得有關方法叫用及 Managed 應用程式所產生的網路流量的資訊。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-119">Explains how to use network tracing to get information about method invocations and network traffic generated by a managed application.</span></span>  
  
 [<span data-ttu-id="1d3bb-120">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="1d3bb-120">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 <span data-ttu-id="1d3bb-121">說明如何針對使用 <xref:System.Net.WebClient?displayProperty=nameWithType>、<xref:System.Net.WebRequest?displayProperty=nameWithType> 和 <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> 類別的應用程式來使用快取。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-121">Describes how to use caching for applications that use the <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>, and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 [<span data-ttu-id="1d3bb-122">網路程式設計的安全性</span><span class="sxs-lookup"><span data-stu-id="1d3bb-122">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)  
 <span data-ttu-id="1d3bb-123">描述如何使用標準網際網路安全性和驗證技術。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-123">Describes how to use standard Internet security and authentication techniques.</span></span>  
  
 [<span data-ttu-id="1d3bb-124">System.Net 類別的最佳做法</span><span class="sxs-lookup"><span data-stu-id="1d3bb-124">Best Practices for System.Net Classes</span></span>](../../../docs/framework/network-programming/best-practices-for-system-net-classes.md)  
 <span data-ttu-id="1d3bb-125">提供可讓您善用網際網路應用程式的祕訣和訣竅。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-125">Provides tips and tricks for getting the most out of your Internet applications.</span></span>  
  
 [<span data-ttu-id="1d3bb-126">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="1d3bb-126">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 <span data-ttu-id="1d3bb-127">描述如何設定 Proxy。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-127">Describes how to configure proxies.</span></span>  
  
 [<span data-ttu-id="1d3bb-128">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="1d3bb-128">NetworkInformation</span></span>](../../../docs/framework/network-programming/networkinformation.md)  
 <span data-ttu-id="1d3bb-129">描述如何蒐集網路事件、變更、統計資料和屬性的相關資訊，以及說明如何判斷遠端主機是否可以使用 <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> 類別取得聯繫。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-129">Describes how to gather information about network events, changes, statistics, and properties and also explains how to determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
 [<span data-ttu-id="1d3bb-130">2.0 版中 System.Uri 命名空間的變更</span><span class="sxs-lookup"><span data-stu-id="1d3bb-130">Changes to the System.Uri namespace in Version 2.0</span></span>](../../../docs/framework/network-programming/changes-to-the-system-uri-namespace-in-version-2-0.md)  
 <span data-ttu-id="1d3bb-131">說明在版本 2.0 中對 <xref:System.Uri?displayProperty=nameWithType> 類別所做的幾個變更，以修正不正確的行為、提高可用性，以及增強安全性。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-131">Describes several changes made to the <xref:System.Uri?displayProperty=nameWithType> class in Version 2.0 to fixed incorrect behavior, enhance usability, and enhance security.</span></span>  
  
 [<span data-ttu-id="1d3bb-132">System.Uri 的國際資源識別項支援</span><span class="sxs-lookup"><span data-stu-id="1d3bb-132">International Resource Identifier Support in System.Uri</span></span>](../../../docs/framework/network-programming/international-resource-identifier-support-in-system-uri.md)  
 <span data-ttu-id="1d3bb-133">說明在版本 3.5、3.0 SP1 和 2.0 SP1 中的 <xref:System.Uri?displayProperty=nameWithType> 類別增強功能，以支援國際資源識別項 (IRI) 和國際化網域名稱 (IDN)。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-133">Describes enhancements to the <xref:System.Uri?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 for International Resource Identifier (IRI) and Internationalized Domain Name (IDN) support.</span></span>  
  
 [<span data-ttu-id="1d3bb-134">3.5 版中的通訊端效能增強功能</span><span class="sxs-lookup"><span data-stu-id="1d3bb-134">Socket Performance Enhancements in Version 3.5</span></span>](../../../docs/framework/network-programming/socket-performance-enhancements-in-version-3-5.md)  
 <span data-ttu-id="1d3bb-135">說明在版本 3.5、3.0 SP1 和 2.0 SP1 中 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> 類別的一組增強功能，其提供另一種非同步模式，可供專業化的高效能通訊端應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-135">Describes a set of enhancements to the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.</span></span>  
  
 [<span data-ttu-id="1d3bb-136">對等名稱解析通訊協定</span><span class="sxs-lookup"><span data-stu-id="1d3bb-136">Peer Name Resolution Protocol</span></span>](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)  
 <span data-ttu-id="1d3bb-137">說明在版本 3.5 中所新增的支援，以支援對等名稱解析通訊協定 (PNRP)、無伺服器和動態名稱登錄以及名稱解析通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-137">Describes support added in Version 3.5 to support the Peer Name Resolution Protocol (PNRP), a serverless and dynamic name registration and name resolution protocol.</span></span> <span data-ttu-id="1d3bb-138">這些新功能是由 <xref:System.Net.PeerToPeer?displayProperty=nameWithType> 命名空間所支援。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-138">These new features are supported by the <xref:System.Net.PeerToPeer?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="1d3bb-139">對等共同作業</span><span class="sxs-lookup"><span data-stu-id="1d3bb-139">Peer-to-Peer Collaboration</span></span>](../../../docs/framework/network-programming/peer-to-peer-collaboration.md)  
 <span data-ttu-id="1d3bb-140">說明在版本 3.5 中所新增的支援，以支援建置在 PNRP 上的對等協同作業。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-140">Describes support added in Version 3.5 to support the Peer-to-Peer Collaboration that builds on PNRP.</span></span> <span data-ttu-id="1d3bb-141">這些新功能是由 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> 命名空間所支援。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-141">These new features are supported by the <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="1d3bb-142">3.5 SP1 版中 HttpWebRequest 之 NTLM 驗證的變更</span><span class="sxs-lookup"><span data-stu-id="1d3bb-142">Changes to NTLM authentication for HttpWebRequest in Version 3.5 SP1</span></span>](../../../docs/framework/network-programming/changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 <span data-ttu-id="1d3bb-143">說明在版本 3.5 SP1 中所做的安全性變更，這些變更會影響 <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>、<xref:System.Net.HttpListener?displayProperty=nameWithType>、<xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType> 以及 System.Net 命名空間中的相關類別處理整合式 Windows 驗證的方式。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-143">Describes security changes made in Version 3.5 SP1 that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the System.Net namespace.</span></span>  
  
 [<span data-ttu-id="1d3bb-144">具有延伸保護的整合式 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="1d3bb-144">Integrated Windows Authentication with Extended Protection</span></span>](../../../docs/framework/network-programming/integrated-windows-authentication-with-extended-protection.md)  
 <span data-ttu-id="1d3bb-145">說明延伸保護的增強功能，這些增強功能會影響 <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>、<xref:System.Net.HttpListener?displayProperty=nameWithType>、<xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>、<xref:System.Net.Security.SslStream?displayProperty=nameWithType>、<xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType> 以及 <xref:System.Net?displayProperty=nameWithType> 和相關命名空間中的相關類別處理整合式 Windows 驗證的方式。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-145">Describes enhancements for extended protection that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the <xref:System.Net?displayProperty=nameWithType> and related namespaces.</span></span>  
  
 [<span data-ttu-id="1d3bb-146">使用 IPv6 和 Teredo 的 NAT 周遊</span><span class="sxs-lookup"><span data-stu-id="1d3bb-146">NAT Traversal using IPv6 and Teredo</span></span>](../../../docs/framework/network-programming/nat-traversal-using-ipv6-and-teredo.md)  
 <span data-ttu-id="1d3bb-147">說明 <xref:System.Net?displayProperty=nameWithType>、<xref:System.Net.NetworkInformation?displayProperty=nameWithType> 和 <xref:System.Net.Sockets?displayProperty=nameWithType> 命名空間所新增的增強功能，以支援使用 IPv6 和 Teredo 進行 NAT 周遊。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-147">Describes enhancements added to the <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, and <xref:System.Net.Sockets?displayProperty=nameWithType> namespaces to support NAT traversal using IPv6 and Teredo.</span></span>  
  
 [<span data-ttu-id="1d3bb-148">Windows 市集應用程式的網路隔離</span><span class="sxs-lookup"><span data-stu-id="1d3bb-148">Network Isolation for Windows Store Apps</span></span>](../../../docs/framework/network-programming/network-isolation-for-windows-store-apps.md)  
 <span data-ttu-id="1d3bb-149">說明當 <xref:System.Net>、 <xref:System.Net.Http>和 <xref:System.Net.Http.Headers> 命名空間中的類別用於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式時，網路隔離的影響。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-149">Describes the impact of network isolation when classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces are used in [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="1d3bb-150">網路程式設計範例</span><span class="sxs-lookup"><span data-stu-id="1d3bb-150">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 <span data-ttu-id="1d3bb-151">可供下載的網路程式設計範例的連結，這些範例會使用 <xref:System.Net>、 <xref:System.Net.Cache>、 <xref:System.Net.Configuration>、 <xref:System.Net.Mail>、 <xref:System.Net.Mime>、 <xref:System.Net.NetworkInformation>、 <xref:System.Net.PeerToPeer>、 <xref:System.Net.Security>以及 <xref:System.Net.Sockets> 命名空間中的類別。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-151">Links to downloadable network programming samples that use classes in the <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> namespaces.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1d3bb-152">參考資料</span><span class="sxs-lookup"><span data-stu-id="1d3bb-152">Reference</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-153">提供一個簡單的程式設計介面，讓現今網路所用的許多通訊協定使用。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-153">Provides a simple programming interface for many of the protocols used on networks today.</span></span> <span data-ttu-id="1d3bb-154">此命名空間中的 <xref:System.Net.WebRequest?displayProperty=nameWithType> 和 <xref:System.Net.WebResponse?displayProperty=nameWithType> 類別是可外掛式通訊協定的基礎。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-154">The <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.WebResponse?displayProperty=nameWithType> classes in this namespace are the basis for pluggable protocols.</span></span>  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-155">可定義類型和列舉，這些類型和列舉是用來定義使用 <xref:System.Net.WebRequest?displayProperty=nameWithType> 和 <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> 類別所取得之資源的快取原則。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-155">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-156">應用程式用來以程式設計方式存取及更新 System.Net 命名空間組態設定的類別。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-156">Classes that applications use to programmatically access and update configuration settings for the System.Net namespaces.</span></span>  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-157">可為現代 HTTP 應用程式提供程式設計介面的類別。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-157">Classes that provides a programming interface for modern HTTP applications.</span></span>  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-158">為 <xref:System.Net.Http?displayProperty=nameWithType> 命名空間所使用的 HTTP 標頭集合提供支援</span><span class="sxs-lookup"><span data-stu-id="1d3bb-158">Provides support for collections of HTTP headers used by the <xref:System.Net.Http?displayProperty=nameWithType> namespace</span></span>  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-159">用於使用 SMTP 通訊協定撰寫及傳送郵件的類別。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-159">Classes to compose and send mail using the SMTP protocol.</span></span>  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-160">可定義類型，這些類型是用於表示 <xref:System.Net.Mail?displayProperty=nameWithType> 命名空間中的類別所使用的多用途網際網路郵件交換 (MIME) 標頭。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-160">Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=nameWithType> namespace.</span></span>  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-161">以程式設計方式收集網路事件、變更、統計資料和屬性的相關資訊的類別。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-161">Classes to programmatically gather information about network events, changes, statistics, and properties.</span></span>  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-162">為開發人員提供對等名稱解析通訊協定 (PNRP) 的 Managed 實作。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-162">Provides a managed implementation of the Peer Name Resolution Protocol (PNRP) for developers.</span></span>  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-163">為開發人員提供對等協同作業介面的 Managed 實作。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-163">Provides a managed implementation of the Peer-to-Peer Collaboration interface for developers.</span></span>  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-164">用於提供主機之間安全通訊的網路資料流的類別。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-164">Classes to provide network streams for secure communications between hosts.</span></span>  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-165">提供 Windows Sockets (Winsock) 介面的 Managed 實作，讓需要協助控制網路存取的開發人員使用。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-165">Provides a managed implementation of the Windows Sockets (Winsock) interface for developers who need to help control access to the network.</span></span>  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-166">為開發人員提供 WebSocket 介面的 Managed 實作。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-166">Provides a managed implementation of the WebSocket interface for developers.</span></span>  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-167">提供統一資源識別元 (URI) 的物件表示，以及對 URI 各部分的簡易存取。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-167">Provides an object representation of a uniform resource identifier (URI) and easy access to the parts of the URI.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-168">為應用程式提供使用延伸保護進行驗證的支援。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-168">Provides support for authentication using extended protection for applications.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="1d3bb-169">為應用程式提供使用延伸保護設定驗證組態的支援。</span><span class="sxs-lookup"><span data-stu-id="1d3bb-169">Provides support for configuration of authentication using extended protection for applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d3bb-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d3bb-170">See Also</span></span>  

 [<span data-ttu-id="1d3bb-171">.NET Framework 的傳輸層安全性 (TLS) 最佳做法</span><span class="sxs-lookup"><span data-stu-id="1d3bb-171">Transport Layer Security (TLS) best practices with .NET Framework</span></span>](../../../docs/framework/network-programming/tls.md)  
 [<span data-ttu-id="1d3bb-172">網路程式設計「如何」主題</span><span class="sxs-lookup"><span data-stu-id="1d3bb-172">Network Programming How-to Topics</span></span>](../../../docs/framework/network-programming/network-programming-how-to-topics.md)  
 [<span data-ttu-id="1d3bb-173">網路程式設計範例</span><span class="sxs-lookup"><span data-stu-id="1d3bb-173">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="1d3bb-174">MSDN Code Gallery 上的 .NET 網路範例</span><span class="sxs-lookup"><span data-stu-id="1d3bb-174">Networking Samples for .NET on MSDN Code Gallery</span></span>](https://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)  
 [<span data-ttu-id="1d3bb-175">HttpClient 範例</span><span class="sxs-lookup"><span data-stu-id="1d3bb-175">HttpClient Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=242550)
