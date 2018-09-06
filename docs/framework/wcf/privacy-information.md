---
title: Windows Communication Foundation 隱私權資訊
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 9c2a8d89fc62f8e3e0ce17f13604a6ba05df1a6f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799196"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="43b3d-102">Windows Communication Foundation 隱私權資訊</span><span class="sxs-lookup"><span data-stu-id="43b3d-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="43b3d-103">Microsoft 一向致力於保護終端使用者的隱私權。</span><span class="sxs-lookup"><span data-stu-id="43b3d-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="43b3d-104">當您建置的應用程式使用 Windows Communication Foundation (WCF) 3.0 版，您的應用程式可能會影響到使用者的隱私權。</span><span class="sxs-lookup"><span data-stu-id="43b3d-104">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="43b3d-105">例如，應用程式可能會明確收集使用者的連絡資訊，或者透過網際網路向您的網站要求資訊或傳送資訊至網站。</span><span class="sxs-lookup"><span data-stu-id="43b3d-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="43b3d-106">如果您在應用程式中內嵌 Microsoft 技術，則該技術可能帶有會影響隱私權的行為。</span><span class="sxs-lookup"><span data-stu-id="43b3d-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="43b3d-107">WCF 不會傳送任何資訊給 Microsoft 從您的應用程式除非您本人或使用者選擇要傳送給我們。</span><span class="sxs-lookup"><span data-stu-id="43b3d-107">WCF does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="43b3d-108">WCF 簡介</span><span class="sxs-lookup"><span data-stu-id="43b3d-108">WCF in Brief</span></span>  
 <span data-ttu-id="43b3d-109">WCF 是使用 Microsoft.NET Framework 可讓開發人員建置分散式應用程式的分散式訊息架構。</span><span class="sxs-lookup"><span data-stu-id="43b3d-109">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="43b3d-110">而在兩個應用程式之間通訊的訊息則包含標頭和本文資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="43b3d-111">根據應用程式使用的服務而定，標頭可能包含訊息路由、安全性資訊、交易及其他項目。</span><span class="sxs-lookup"><span data-stu-id="43b3d-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="43b3d-112">根據預設，訊息通常會經過加密。</span><span class="sxs-lookup"><span data-stu-id="43b3d-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="43b3d-113">唯一的例外為使用 `BasicHttpBinding` 時，此項原本就設計用於不受安全保護的舊式 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="43b3d-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="43b3d-114">身為應用程式設計師，您要負責做好最後的設計。</span><span class="sxs-lookup"><span data-stu-id="43b3d-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="43b3d-115">在 SOAP 主體中的訊息包含應用程式專屬資料;不過，這項資料，例如應用程式定義的個人資訊，您可以保護使用 WCF 加密或機密性功能。</span><span class="sxs-lookup"><span data-stu-id="43b3d-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="43b3d-116">下列章節將描述可能影響隱私權的功能。</span><span class="sxs-lookup"><span data-stu-id="43b3d-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="43b3d-117">訊息</span><span class="sxs-lookup"><span data-stu-id="43b3d-117">Messaging</span></span>  
 <span data-ttu-id="43b3d-118">每個 WCF 訊息具有指定的訊息目的地的位址標頭和回覆去處。</span><span class="sxs-lookup"><span data-stu-id="43b3d-118">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="43b3d-119">端點位址的位址元件則是可識別端點的統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="43b3d-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="43b3d-120">此位址可以是網路位址或邏輯位址。</span><span class="sxs-lookup"><span data-stu-id="43b3d-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="43b3d-121">位址也可能包含電腦名稱 (主機名稱，完整網域名稱) 和 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="43b3d-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="43b3d-122">端點位址也可能包含全域唯一識別元 (GUID)，或者包含可用於分辨每個位址之暫存定址的 GUID 集合。</span><span class="sxs-lookup"><span data-stu-id="43b3d-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="43b3d-123">每則訊息中都包含屬於 GUID 的訊息識別碼。</span><span class="sxs-lookup"><span data-stu-id="43b3d-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="43b3d-124">另外，此功能會遵循 WS-Addressing 參照標準。</span><span class="sxs-lookup"><span data-stu-id="43b3d-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="43b3d-125">WCF 傳訊層不會寫入到本機電腦的任何個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-125">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="43b3d-126">不過，如果服務開發人員建立了會公開這類資訊的服務 (例如，在端點名稱中使用某個人的名稱，或者在端點的 Web 服務描述語言中加入個人資訊，可是沒有要求用戶端使用 https 來存取 WSDL)，則該訊息層可能在網路層級中傳播個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="43b3d-127">此外，如果開發人員執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具針對端點公開個人資訊，此工具的輸出可能包含該資訊，並寫入輸出檔案本機硬碟。</span><span class="sxs-lookup"><span data-stu-id="43b3d-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="43b3d-128">裝載</span><span class="sxs-lookup"><span data-stu-id="43b3d-128">Hosting</span></span>  
 <span data-ttu-id="43b3d-129">WCF 中的裝載功能可讓應用程式可視需要啟動或啟用多個應用程式之間的連接埠共用。</span><span class="sxs-lookup"><span data-stu-id="43b3d-129">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="43b3d-130">WCF 應用程式可以裝載在網際網路資訊服務 (IIS)，類似於[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="43b3d-130">An WCF application can be hosted in Internet Information Services (IIS), similar to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="43b3d-131">裝載時並不會在網路上公開任何特定資訊，而且也不會保存電腦上的資料。</span><span class="sxs-lookup"><span data-stu-id="43b3d-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="43b3d-132">訊息安全性</span><span class="sxs-lookup"><span data-stu-id="43b3d-132">Message Security</span></span>  
 <span data-ttu-id="43b3d-133">WCF 安全性會提供訊息應用程式的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="43b3d-133">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="43b3d-134">所提供的安全性功能包含驗證和授權。</span><span class="sxs-lookup"><span data-stu-id="43b3d-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="43b3d-135">驗證的作法是在用戶端和服務之間傳遞認證。</span><span class="sxs-lookup"><span data-stu-id="43b3d-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="43b3d-136">您可以透過傳輸層級安全性或 SOAP 訊息層級安全性來進行驗證，如下所示：</span><span class="sxs-lookup"><span data-stu-id="43b3d-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
-   <span data-ttu-id="43b3d-137">在 SOAP 訊息安全性中，可以透過使用者名稱/密碼、X.509 憑證、Kerberos 票證和 SAML 語彙基元這類認證來執行驗證，而視簽發者而定，這些認證中可能含有個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
-   <span data-ttu-id="43b3d-138">使用傳輸安全性時，則可藉由 HTTP 驗證配置 (Basic、Digest、Negotiate、Integrated Windows Authorization、NTLM、None 和 Anonymous) 這種傳統傳輸驗證機制和表單驗證，來處理驗證動作。</span><span class="sxs-lookup"><span data-stu-id="43b3d-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="43b3d-139">執行驗證之後，會在進行通訊的端點之間建立安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="43b3d-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="43b3d-140">這個工作階段是由會在安全性工作階段的存留期間持續活動的 GUID 所識別。</span><span class="sxs-lookup"><span data-stu-id="43b3d-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="43b3d-141">下表會顯示所保留的項目的位置。</span><span class="sxs-lookup"><span data-stu-id="43b3d-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="43b3d-142">資料</span><span class="sxs-lookup"><span data-stu-id="43b3d-142">Data</span></span>|<span data-ttu-id="43b3d-143">儲存區</span><span class="sxs-lookup"><span data-stu-id="43b3d-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="43b3d-144">展示認證，例如使用者名稱、X.509 憑證、Kerberos 語彙基元和認證的各種參照。</span><span class="sxs-lookup"><span data-stu-id="43b3d-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="43b3d-145">標準 Windows 認證管理機制，例如 Windows 憑證存放庫。</span><span class="sxs-lookup"><span data-stu-id="43b3d-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="43b3d-146">使用者成員資格資訊，例如使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="43b3d-146">User membership information, such as usernames and passwords.</span></span>|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]<span data-ttu-id="43b3d-147"> 成員資格提供者。</span><span class="sxs-lookup"><span data-stu-id="43b3d-147"> membership providers.</span></span>|  
|<span data-ttu-id="43b3d-148">身分識別服務的相關資訊，此服務是用來驗證用戶端的服務。</span><span class="sxs-lookup"><span data-stu-id="43b3d-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="43b3d-149">服務的端點位址。</span><span class="sxs-lookup"><span data-stu-id="43b3d-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="43b3d-150">呼叫端資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-150">Caller information.</span></span>|<span data-ttu-id="43b3d-151">稽核記錄。</span><span class="sxs-lookup"><span data-stu-id="43b3d-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="43b3d-152">稽核</span><span class="sxs-lookup"><span data-stu-id="43b3d-152">Auditing</span></span>  
 <span data-ttu-id="43b3d-153">稽核會記錄驗證和授權事件的成功與失敗。</span><span class="sxs-lookup"><span data-stu-id="43b3d-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="43b3d-154">稽核記錄中則包含下列資料：服務 URI、動作 URI 和呼叫端的識別。</span><span class="sxs-lookup"><span data-stu-id="43b3d-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="43b3d-155">稽核也會記錄系統管理員修改訊息記錄組態 (開啟或關閉) 的時間，這是因為訊息記錄可能會在標頭和本文中記錄應用程式特定的資料。</span><span class="sxs-lookup"><span data-stu-id="43b3d-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="43b3d-156">若為 [!INCLUDE[wxp](../../../includes/wxp-md.md)]，則會在應用程式事件日誌中記載一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="43b3d-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="43b3d-157">若為 [!INCLUDE[wv](../../../includes/wv-md.md)] 和 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]，則會在安全性事件日誌中記載一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="43b3d-157">For [!INCLUDE[wv](../../../includes/wv-md.md)] and [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="43b3d-158">異動</span><span class="sxs-lookup"><span data-stu-id="43b3d-158">Transactions</span></span>  
 <span data-ttu-id="43b3d-159">交易功能提供交易服務的 WCF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="43b3d-159">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="43b3d-160">異動傳播中使用的異動標頭可能包含屬於 GUID 的異動識別碼或登記識別碼。</span><span class="sxs-lookup"><span data-stu-id="43b3d-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="43b3d-161">交易功能會使用 Microsoft Distributed Transaction Coordinator (MSDTC) 的交易管理員 (一種 Windows 元件) 來管理交易狀態。</span><span class="sxs-lookup"><span data-stu-id="43b3d-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="43b3d-162">根據預設，系統會加密交易管理員之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="43b3d-163">交易管理員可能會記錄端點參照、交易識別碼和登記識別碼，作為其長期狀態的一部分。</span><span class="sxs-lookup"><span data-stu-id="43b3d-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="43b3d-164">這個狀態的存留期則是由交易管理員的記錄檔存留期所決定。</span><span class="sxs-lookup"><span data-stu-id="43b3d-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="43b3d-165">MSDTC 服務則擁有並維護此記錄。</span><span class="sxs-lookup"><span data-stu-id="43b3d-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="43b3d-166">交易功能會實作 WS-Coordination 和 WS-Atomic 交易標準。</span><span class="sxs-lookup"><span data-stu-id="43b3d-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="43b3d-167">可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="43b3d-167">Reliable Sessions</span></span>  
 <span data-ttu-id="43b3d-168">在 WCF 中的可靠工作階段提供訊息的傳輸，傳輸或中繼失敗發生時。</span><span class="sxs-lookup"><span data-stu-id="43b3d-168">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="43b3d-169">即使中斷基礎傳輸 (例如，無線網路上的 TCP 連線) 或遺失訊息 (HTTP Proxy 捨棄了傳出或傳入的訊息)，這些可靠的工作階段仍可確實傳送一次訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="43b3d-170">可靠的工作階段也會復原重新排列順序後的訊息 (在多路徑路由時可能會發生)，保留訊息傳送的順序。</span><span class="sxs-lookup"><span data-stu-id="43b3d-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="43b3d-171">您可以使用 WS-ReliableMessaging (WS-RM) 通訊協定來實作可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="43b3d-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="43b3d-172">這些工作階段會新增其中包含工作階段資訊的 WS-RM 標頭，而您可以使用此資訊來識別與特定可靠的工作階段相關聯的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="43b3d-173">每個 WS-RM 工作階段都有識別碼，也就是 GUID。</span><span class="sxs-lookup"><span data-stu-id="43b3d-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="43b3d-174">使用者電腦上不會保留任何個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="43b3d-175">佇列通道</span><span class="sxs-lookup"><span data-stu-id="43b3d-175">Queued Channels</span></span>  
 <span data-ttu-id="43b3d-176">佇列可代表接收應用程式，存放來自傳送應用程式的訊息，並在稍後將這些訊息轉寄至接收應用程式。</span><span class="sxs-lookup"><span data-stu-id="43b3d-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="43b3d-177">例如，接收應用程式為暫時性時，使用佇列將協助確保訊息的傳輸，從傳送應用程式至接收應用程式。</span><span class="sxs-lookup"><span data-stu-id="43b3d-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="43b3d-178">WCF 會提供使用 Microsoft Message Queuing (MSMQ) 做為傳輸佇列的支援。</span><span class="sxs-lookup"><span data-stu-id="43b3d-178">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="43b3d-179">佇列通道功能不會將標頭新增至訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="43b3d-180">該功能會以適當的 [訊息佇列] 訊息屬性設定，來建立 [訊息佇列] 的訊息，並叫用 [訊息佇列] 方法以將訊息放置在 [訊息佇列] 的佇列中。</span><span class="sxs-lookup"><span data-stu-id="43b3d-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="43b3d-181">[訊息佇列] 是隨附於 Windows 的選用元件。</span><span class="sxs-lookup"><span data-stu-id="43b3d-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="43b3d-182">佇列通道功能並不會在使用者電腦上保留任何資訊，而這都歸功於使用 [訊息佇列] 做為佇列基礎結構。</span><span class="sxs-lookup"><span data-stu-id="43b3d-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="43b3d-183">COM+ 整合</span><span class="sxs-lookup"><span data-stu-id="43b3d-183">COM+ Integration</span></span>  
 <span data-ttu-id="43b3d-184">這項功能會包裝現有的 COM 和 COM + 功能以建立與 WCF 服務相容的服務。</span><span class="sxs-lookup"><span data-stu-id="43b3d-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="43b3d-185">這項功能不會使用特定標頭，也不會在終端使用者的電腦上保留任何資料。</span><span class="sxs-lookup"><span data-stu-id="43b3d-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="43b3d-186">COM 服務 Moniker</span><span class="sxs-lookup"><span data-stu-id="43b3d-186">COM Service Moniker</span></span>  
 <span data-ttu-id="43b3d-187">這是標準的 WCF 用戶端提供 unmanaged 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="43b3d-187">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="43b3d-188">這項功能在網路上沒有特定的標頭，也不會在電腦上保留任何資料。</span><span class="sxs-lookup"><span data-stu-id="43b3d-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="43b3d-189">對等通道</span><span class="sxs-lookup"><span data-stu-id="43b3d-189">Peer Channel</span></span>  
 <span data-ttu-id="43b3d-190">對等通道可讓使用 WCF 的多方應用程式的開發。</span><span class="sxs-lookup"><span data-stu-id="43b3d-190">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="43b3d-191">多方通訊會以網狀結構的脈絡發生。</span><span class="sxs-lookup"><span data-stu-id="43b3d-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="43b3d-192">[網狀結構] 是依照各節點可加入的名稱所識別。</span><span class="sxs-lookup"><span data-stu-id="43b3d-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="43b3d-193">對等通道中的每個節點都會在使用者指定的連接埠上建立 TCP 接聽項，並與網狀結構中的其他節點建立連線以確保擁有回復性。</span><span class="sxs-lookup"><span data-stu-id="43b3d-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="43b3d-194">若要連線至網狀結構中的其他節點，節點也必須與網狀結構中的其他節點交換資料，包括接聽項位址和電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="43b3d-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="43b3d-195">在網狀結構中來回傳送的訊息會包含專屬於傳送者的安全性資訊，因此可防止發生訊息詐騙和竄改。</span><span class="sxs-lookup"><span data-stu-id="43b3d-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="43b3d-196">使用者電腦上不會存放任何個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="43b3d-197">IT 專業人員的體驗</span><span class="sxs-lookup"><span data-stu-id="43b3d-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="43b3d-198">追蹤</span><span class="sxs-lookup"><span data-stu-id="43b3d-198">Tracing</span></span>  
 <span data-ttu-id="43b3d-199">WCF 基礎結構的診斷功能會記錄透過傳輸和服務模型層，和活動以及這些訊息相關聯的事件傳遞的訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-199">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="43b3d-200">根據預設，這個功能是關閉的。</span><span class="sxs-lookup"><span data-stu-id="43b3d-200">This feature is turned off by default.</span></span> <span data-ttu-id="43b3d-201">啟用使用應用程式的組態檔，且可能在執行階段使用的 WCF WMI 提供者修改追蹤行為。</span><span class="sxs-lookup"><span data-stu-id="43b3d-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="43b3d-202">啟用此功能時，追蹤基礎結構會將包含訊息、活動和處理事件的診斷追蹤，發送至已設定的接聽項。</span><span class="sxs-lookup"><span data-stu-id="43b3d-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="43b3d-203">輸出的格式和位置是由系統管理員的接聽程式組態選項來決定，不過通常會是 XML 格式的檔案。</span><span class="sxs-lookup"><span data-stu-id="43b3d-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="43b3d-204">系統管理員要負責設定追蹤檔上的存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="43b3d-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="43b3d-205">由 Windows Activation System (WAS) 裝載時，系統管理員更應該確定在非必須的情況下，不是從公開的虛擬根目錄使用檔案。</span><span class="sxs-lookup"><span data-stu-id="43b3d-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="43b3d-206">追蹤的類型有兩種：訊息記錄和服務模型診斷追蹤，分別會在下節中描述。</span><span class="sxs-lookup"><span data-stu-id="43b3d-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="43b3d-207">這兩個類型的追蹤也可透過本身的追蹤來源進行設定：<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> 和 <xref:System.ServiceModel>。</span><span class="sxs-lookup"><span data-stu-id="43b3d-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="43b3d-208">這些記錄追蹤來源都會擷取對應用程式而言為本機的資料。</span><span class="sxs-lookup"><span data-stu-id="43b3d-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="43b3d-209">訊息記錄</span><span class="sxs-lookup"><span data-stu-id="43b3d-209">Message Logging</span></span>  
 <span data-ttu-id="43b3d-210">訊息記錄追蹤來源 (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) 可讓系統管理員記錄在系統來回傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="43b3d-211">透過組態，使用者可以決定要記錄整個訊息或僅記錄訊息標頭、是否要在傳輸層及 (或) 服務模型層記錄，以及是否包含格式不正確的訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="43b3d-212">此外，使用者也可以設定篩選以限制要記錄的訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="43b3d-213">根據預設，訊息記錄呈停用狀態。</span><span class="sxs-lookup"><span data-stu-id="43b3d-213">By default, message logging is disabled.</span></span> <span data-ttu-id="43b3d-214">而本機電腦的系統管理員可以防止應用程式層級的管理員開啟訊息記錄功能。</span><span class="sxs-lookup"><span data-stu-id="43b3d-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="43b3d-215">加密和解密的訊息記錄</span><span class="sxs-lookup"><span data-stu-id="43b3d-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="43b3d-216">系統會對訊息進行記錄、加密或解密，如下列詞彙所述。</span><span class="sxs-lookup"><span data-stu-id="43b3d-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="43b3d-217">傳輸記錄</span><span class="sxs-lookup"><span data-stu-id="43b3d-217">Transport Logging</span></span>  
 <span data-ttu-id="43b3d-218">記錄在傳輸層級接收和傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="43b3d-219">這些訊息包含所有標頭，而且可能會在網路上傳送前和收到訊息時加密。</span><span class="sxs-lookup"><span data-stu-id="43b3d-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="43b3d-220">如果訊息是在網路上傳送之前以及收到時進行加密，那麼這些訊息也會以加密記錄。</span><span class="sxs-lookup"><span data-stu-id="43b3d-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="43b3d-221">使用安全性通訊協定 (https) 則為例外：即使在網路上加密這些訊息，仍會在傳送之前和接收之後，以解密記錄。</span><span class="sxs-lookup"><span data-stu-id="43b3d-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="43b3d-222">服務記錄</span><span class="sxs-lookup"><span data-stu-id="43b3d-222">Service Logging</span></span>  
 <span data-ttu-id="43b3d-223">記錄在服務模型層級、發生通道標頭處理之後以及輸入使用者程式碼之前與之後所接收或傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="43b3d-224">在此層級記錄的訊息即使已安全保護並且在網路上加密，仍會進行解密。</span><span class="sxs-lookup"><span data-stu-id="43b3d-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="43b3d-225">格式不正確的訊息記錄</span><span class="sxs-lookup"><span data-stu-id="43b3d-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="43b3d-226">WCF 基礎結構無法理解或處理的記錄檔訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-226">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="43b3d-227">會以現狀記錄訊息，也就是加密或未加密的狀態。</span><span class="sxs-lookup"><span data-stu-id="43b3d-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="43b3d-228">當訊息記錄在解密或未加密的形式，根據預設 WCF 移除安全性金鑰和可能的個人資訊訊息之前記錄。</span><span class="sxs-lookup"><span data-stu-id="43b3d-228">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="43b3d-229">下面章節會描述要移除的資訊以及移除的時機。</span><span class="sxs-lookup"><span data-stu-id="43b3d-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="43b3d-230">電腦的系統管理員和應用程式開發人員都必須採取特定的組態動作，才能變更行為以記錄金鑰和可能的個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="43b3d-231">記錄解密/未加密訊息時，從訊息標頭中移除的資訊</span><span class="sxs-lookup"><span data-stu-id="43b3d-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="43b3d-232">以解密/未加密形式記錄訊息時，在記錄訊息之前，預設會從訊息標頭和訊息本文中移除安全性金鑰和可能會有的個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="43b3d-233">下列清單顯示什麼 WCF 視為金鑰和可能的個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-233">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="43b3d-234">移除的金鑰：</span><span class="sxs-lookup"><span data-stu-id="43b3d-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="43b3d-235">\- Xmlns:wst ="http://schemas.xmlsoap.org/ws/2004/04/trust"和 xmlns:wst ="http://schemas.xmlsoap.org/ws/2005/02/trust」</span><span class="sxs-lookup"><span data-stu-id="43b3d-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="43b3d-236">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="43b3d-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="43b3d-237">wst:Entropy</span><span class="sxs-lookup"><span data-stu-id="43b3d-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="43b3d-238">\- Xmlns:wsse ="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd"和 xmlns:wsse ="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd」</span><span class="sxs-lookup"><span data-stu-id="43b3d-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="43b3d-239">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="43b3d-239">wsse:Password</span></span>  
  
 <span data-ttu-id="43b3d-240">wsse:Nonce</span><span class="sxs-lookup"><span data-stu-id="43b3d-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="43b3d-241">移除的可能個人資訊：</span><span class="sxs-lookup"><span data-stu-id="43b3d-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="43b3d-242">\- Xmlns:wsse ="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd"和 xmlns:wsse ="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd」</span><span class="sxs-lookup"><span data-stu-id="43b3d-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="43b3d-243">wsse:Username</span><span class="sxs-lookup"><span data-stu-id="43b3d-243">wsse:Username</span></span>  
  
 <span data-ttu-id="43b3d-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="43b3d-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="43b3d-245">\- 為 xmlns: saml ="urn: oasis： 名稱： tc: SAML:1.0:assertion 「 移除的項目以粗體顯示 （如下所示）：</span><span class="sxs-lookup"><span data-stu-id="43b3d-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="43b3d-246">\<判斷提示</span><span class="sxs-lookup"><span data-stu-id="43b3d-246">\<Assertion</span></span>  
  
 <span data-ttu-id="43b3d-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="43b3d-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="43b3d-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="43b3d-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="43b3d-249">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="43b3d-250">Issuer="[string]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="43b3d-251">IssueInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="43b3d-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span><span class="sxs-lookup"><span data-stu-id="43b3d-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="43b3d-253">\<AudienceRestrictionCondition></span><span class="sxs-lookup"><span data-stu-id="43b3d-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="43b3d-254">\<對象 > [uri]\</Audience > +</span><span class="sxs-lookup"><span data-stu-id="43b3d-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="43b3d-255">\</AudienceRestrictionCondition>\*</span><span class="sxs-lookup"><span data-stu-id="43b3d-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="43b3d-256">\<DoNotCacheCondition / > \*</span><span class="sxs-lookup"><span data-stu-id="43b3d-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="43b3d-257"><\!-抽象基底型別</span><span class="sxs-lookup"><span data-stu-id="43b3d-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="43b3d-258">\<條件 / > \*</span><span class="sxs-lookup"><span data-stu-id="43b3d-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="43b3d-259">\</ 條件 > 嗎？</span><span class="sxs-lookup"><span data-stu-id="43b3d-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="43b3d-260">\<建議 ></span><span class="sxs-lookup"><span data-stu-id="43b3d-260">\<Advice></span></span>  
  
 <span data-ttu-id="43b3d-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span><span class="sxs-lookup"><span data-stu-id="43b3d-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="43b3d-262">\<判斷提示 > [判斷提示]\</Assertion > \*</span><span class="sxs-lookup"><span data-stu-id="43b3d-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="43b3d-263">[any]\*</span><span class="sxs-lookup"><span data-stu-id="43b3d-263">[any]\*</span></span>  
  
 <span data-ttu-id="43b3d-264">\</ 建議 > 嗎？</span><span class="sxs-lookup"><span data-stu-id="43b3d-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="43b3d-265"><\!-抽象基底類型</span><span class="sxs-lookup"><span data-stu-id="43b3d-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="43b3d-266">\<陳述式 / > \*</span><span class="sxs-lookup"><span data-stu-id="43b3d-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="43b3d-267">\<SubjectStatement ></span><span class="sxs-lookup"><span data-stu-id="43b3d-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="43b3d-268">\<主旨 ></span><span class="sxs-lookup"><span data-stu-id="43b3d-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="43b3d-269">\<SubjectConfirmation></span><span class="sxs-lookup"><span data-stu-id="43b3d-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="43b3d-270">\<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="43b3d-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="43b3d-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span><span class="sxs-lookup"><span data-stu-id="43b3d-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="43b3d-272">\<ds: keyinfo >...\</ds:KeyInfo > 嗎？</span><span class="sxs-lookup"><span data-stu-id="43b3d-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="43b3d-273">\</ SubjectConfirmation > 嗎？</span><span class="sxs-lookup"><span data-stu-id="43b3d-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="43b3d-274">\</Subject></span><span class="sxs-lookup"><span data-stu-id="43b3d-274">\</Subject></span></span>  
  
 <span data-ttu-id="43b3d-275">\</ SubjectStatement > \*</span><span class="sxs-lookup"><span data-stu-id="43b3d-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="43b3d-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="43b3d-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="43b3d-277">AuthenticationMethod="[uri]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="43b3d-278">AuthenticationInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="43b3d-279">[主旨]</span><span class="sxs-lookup"><span data-stu-id="43b3d-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="43b3d-280"><AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="43b3d-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="43b3d-281">AuthorityKind="[QName]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="43b3d-282">Location="[uri]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="43b3d-283">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="43b3d-284">\</ AuthenticationStatement > \*</span><span class="sxs-lookup"><span data-stu-id="43b3d-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="43b3d-285">\<AttributeStatement ></span><span class="sxs-lookup"><span data-stu-id="43b3d-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="43b3d-286">[主旨]</span><span class="sxs-lookup"><span data-stu-id="43b3d-286">[Subject]</span></span>  
  
 <span data-ttu-id="43b3d-287">\<屬性</span><span class="sxs-lookup"><span data-stu-id="43b3d-287">\<Attribute</span></span>  
  
 <span data-ttu-id="43b3d-288">AttributeName="[string]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="43b3d-289">AttributeNamespace="[uri]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="43b3d-290">\</ 屬性 > +</span><span class="sxs-lookup"><span data-stu-id="43b3d-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="43b3d-291">\</ AttributeStatement > \*</span><span class="sxs-lookup"><span data-stu-id="43b3d-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="43b3d-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="43b3d-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="43b3d-293">Resource="[uri]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="43b3d-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span><span class="sxs-lookup"><span data-stu-id="43b3d-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="43b3d-295">[主旨]</span><span class="sxs-lookup"><span data-stu-id="43b3d-295">[Subject]</span></span>  
  
 <span data-ttu-id="43b3d-296">\<動作命名空間 ="[uri]"> [string]\</Action > +</span><span class="sxs-lookup"><span data-stu-id="43b3d-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="43b3d-297">\<辨識項 ></span><span class="sxs-lookup"><span data-stu-id="43b3d-297">\<Evidence></span></span>  
  
 <span data-ttu-id="43b3d-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span><span class="sxs-lookup"><span data-stu-id="43b3d-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="43b3d-299">\<判斷提示 > [判斷提示]\</Assertion > +</span><span class="sxs-lookup"><span data-stu-id="43b3d-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="43b3d-300">\</ 辨識項 > 嗎？</span><span class="sxs-lookup"><span data-stu-id="43b3d-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="43b3d-301">\</AuthorizationDecisionStatement>\*</span><span class="sxs-lookup"><span data-stu-id="43b3d-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="43b3d-302">\</Assertion></span><span class="sxs-lookup"><span data-stu-id="43b3d-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="43b3d-303">記錄解密/未加密訊息時，從訊息本文中移除的資訊</span><span class="sxs-lookup"><span data-stu-id="43b3d-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="43b3d-304">如先前所述，WCF 移除金鑰和已知的可能個人資訊，從訊息標頭的記錄解密/未加密的訊息。</span><span class="sxs-lookup"><span data-stu-id="43b3d-304">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="43b3d-305">此外，WCF 會移除金鑰和已知的可能個人資訊的內文項目與下列清單中，會描述參與金鑰交換的安全性訊息的動作的訊息內文。</span><span class="sxs-lookup"><span data-stu-id="43b3d-305">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="43b3d-306">若為下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="43b3d-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="43b3d-307">xmlns:wst ="http://schemas.xmlsoap.org/ws/2004/04/trust"和 xmlns:wst ="http://schemas.xmlsoap.org/ws/2005/02/trust」 （例如，如果沒有可用的動作）</span><span class="sxs-lookup"><span data-stu-id="43b3d-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="43b3d-308">將移除這些本文項目的資訊，而這些本文項目牽涉到金鑰交換：</span><span class="sxs-lookup"><span data-stu-id="43b3d-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="43b3d-309">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="43b3d-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="43b3d-310">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="43b3d-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="43b3d-311">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="43b3d-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="43b3d-312">也會移除下列每個動作的資訊：</span><span class="sxs-lookup"><span data-stu-id="43b3d-312">Information is also removed for each of the following Actions:</span></span>  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend  
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="43b3d-313">不會從應用程式特定標頭和本文資料中移除資訊</span><span class="sxs-lookup"><span data-stu-id="43b3d-313">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 <span data-ttu-id="43b3d-314">WCF 不會追蹤應用程式特定標頭 （例如，查詢字串） 或本文資料 （例如信用卡號碼） 中的個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-314">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="43b3d-315">訊息記錄啟用時，也許可以在記錄中看見應用程式特定標頭和本文資訊中的個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-315">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="43b3d-316">因此，應用程式部署者應負責設定組態和記錄檔的 ACL。</span><span class="sxs-lookup"><span data-stu-id="43b3d-316">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="43b3d-317">如果不希望可以看見此資訊，則部署者也可以關閉記錄功能，或者可以在記錄之後從記錄檔中篩選掉此資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-317">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="43b3d-318">服務模型追蹤</span><span class="sxs-lookup"><span data-stu-id="43b3d-318">Service Model Tracing</span></span>  
 <span data-ttu-id="43b3d-319">服務模型追蹤來源 (<xref:System.ServiceModel>) 會啟用與訊息處理相關的活動和事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="43b3d-319">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="43b3d-320">這個功能會從 <xref:System.Diagnostics> 使用 .NET Framework 的診斷功能。</span><span class="sxs-lookup"><span data-stu-id="43b3d-320">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="43b3d-321">在搭配 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> 屬性時，使用者可以使用 .NET Framework 應用程式組態檔來設定位置和 ACL。</span><span class="sxs-lookup"><span data-stu-id="43b3d-321">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="43b3d-322">使用訊息記錄時，只要系統管理員啟用追蹤就一定會設定檔案位置，這表示系統管理員控制了 ACL。</span><span class="sxs-lookup"><span data-stu-id="43b3d-322">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="43b3d-323">當訊息在範圍內時，追蹤就包含訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="43b3d-323">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="43b3d-324">有關上一節所提及之隱藏訊息標頭中的潛在個人資訊，其對應的相同規則也適用：預設會從追蹤中的標頭移除先前所識別的個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-324">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="43b3d-325">電腦系統管理員和應用程式部署者都必須修改組態，才能記錄可能的個人資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-325">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="43b3d-326">不過，應用程式特定標頭所含的個人資訊則會記錄在追蹤中。</span><span class="sxs-lookup"><span data-stu-id="43b3d-326">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="43b3d-327">應用程式部署者應負責設定組態和追蹤檔的 ACL。</span><span class="sxs-lookup"><span data-stu-id="43b3d-327">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="43b3d-328">如果不希望可以看見此資訊，則部署者也可以關閉追蹤功能，或者可以在記錄之後從追蹤檔中篩選掉此資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-328">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="43b3d-329">在進行 ServiceModel 追蹤時，當訊息在基礎結構的不同部分傳遞時，唯一識別碼 (又稱為活動識別碼，而且通常為 GUID) 就會將不同的活動連結起來。</span><span class="sxs-lookup"><span data-stu-id="43b3d-329">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="43b3d-330">自訂追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="43b3d-330">Custom Trace Listeners</span></span>  
 <span data-ttu-id="43b3d-331">您可以對訊息記錄和追蹤設定自訂追蹤接聽項，這樣就可在網路上傳送追蹤和訊息 (例如，傳送至遠端資料庫)。</span><span class="sxs-lookup"><span data-stu-id="43b3d-331">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="43b3d-332">應用程式部署者負責設定自訂接聽項或讓使用者進行自訂。</span><span class="sxs-lookup"><span data-stu-id="43b3d-332">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="43b3d-333">部署者也負責遠端位置公開的個人資訊，以及適當套用 ACL 至此位置。</span><span class="sxs-lookup"><span data-stu-id="43b3d-333">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="43b3d-334">IT 專業人員可用的其他功能</span><span class="sxs-lookup"><span data-stu-id="43b3d-334">Other features for IT Professionals</span></span>  
 <span data-ttu-id="43b3d-335">WCF 有 WMI 提供者會公開透過 WMI （隨附於 Windows） 的 WCF 基礎結構組態資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-335">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="43b3d-336">根據預設，系統管理員將可使用 WMI 介面。</span><span class="sxs-lookup"><span data-stu-id="43b3d-336">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="43b3d-337">WCF 組態會使用.NET Framework 的組態機制。</span><span class="sxs-lookup"><span data-stu-id="43b3d-337">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="43b3d-338">而這些組態檔會存放在電腦上。</span><span class="sxs-lookup"><span data-stu-id="43b3d-338">The configuration files are stored on the machine.</span></span> <span data-ttu-id="43b3d-339">應用程式開發人員和系統管理員會針對每項應用程式需求而建立組態檔和 ACL。</span><span class="sxs-lookup"><span data-stu-id="43b3d-339">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="43b3d-340">組態檔中包含了一些端點位址和連結，可連接到憑證存放區的憑證。</span><span class="sxs-lookup"><span data-stu-id="43b3d-340">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="43b3d-341">您可以使用憑證來提供應用程式資料，進而可設定應用程式所使用的各種功能屬性。</span><span class="sxs-lookup"><span data-stu-id="43b3d-341">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="43b3d-342">WCF 也會使用.NET Framework 處理序傾印功能藉由呼叫<xref:System.Environment.FailFast%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="43b3d-342">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="43b3d-343">IT 專業人員工具</span><span class="sxs-lookup"><span data-stu-id="43b3d-343">IT Pro Tools</span></span>  
 <span data-ttu-id="43b3d-344">WCF 也提供下列 IT 專業人員工具所附 Windows SDK 中。</span><span class="sxs-lookup"><span data-stu-id="43b3d-344">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="43b3d-345">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="43b3d-345">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="43b3d-346">檢視器會顯示 WCF 追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="43b3d-346">The viewer displays WCF trace files.</span></span> <span data-ttu-id="43b3d-347">也會顯示追蹤內所含的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-347">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="43b3d-348">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="43b3d-348">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="43b3d-349">編輯器可讓使用者建立和編輯 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="43b3d-349">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="43b3d-350">這個編輯器還會顯示組態檔中所含的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-350">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="43b3d-351">使用文字編輯器也可完成同樣的工作。</span><span class="sxs-lookup"><span data-stu-id="43b3d-351">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodelreg"></a><span data-ttu-id="43b3d-352">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="43b3d-352">ServiceModel_Reg</span></span>  
 <span data-ttu-id="43b3d-353">這個工具可讓使用者管理電腦上的 ServiceModel 安裝。</span><span class="sxs-lookup"><span data-stu-id="43b3d-353">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="43b3d-354">此工具主控台視窗中顯示狀態訊息，當它執行，並在過程中，可能會顯示的 WCF 安裝組態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-354">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="43b3d-355">WSATConfig.exe 和 WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="43b3d-355">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="43b3d-356">這些工具可讓 IT 專業人員在 WCF 中設定可互通的 WS-AtomicTransaction 網路支援。</span><span class="sxs-lookup"><span data-stu-id="43b3d-356">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="43b3d-357">這些工具會顯示存放在登錄的最常用 WS-AtomicTransaction 設定值，也可讓使用者變更這些值。</span><span class="sxs-lookup"><span data-stu-id="43b3d-357">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="43b3d-358">跨領域功能</span><span class="sxs-lookup"><span data-stu-id="43b3d-358">Cross-cutting Features</span></span>  
 <span data-ttu-id="43b3d-359">下列功能為跨領域功能。</span><span class="sxs-lookup"><span data-stu-id="43b3d-359">The following features are cross-cutting.</span></span> <span data-ttu-id="43b3d-360">也就是說，可以使用前面提及的任何功能來組成不同的功能。</span><span class="sxs-lookup"><span data-stu-id="43b3d-360">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="43b3d-361">服務架構</span><span class="sxs-lookup"><span data-stu-id="43b3d-361">Service Framework</span></span>  
 <span data-ttu-id="43b3d-362">標頭中可含執行個體識別碼，這是會使訊息與 CLR 類別的執行個體產生關聯的 GUID。</span><span class="sxs-lookup"><span data-stu-id="43b3d-362">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="43b3d-363">Web 服務描述語言 (WSDL) 中包含了連接埠定義。</span><span class="sxs-lookup"><span data-stu-id="43b3d-363">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="43b3d-364">每個連接埠都有端點位址，以及表示應用程式所使用服務的繫結。</span><span class="sxs-lookup"><span data-stu-id="43b3d-364">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="43b3d-365">您可以透過組態決定是否公開 WSDL。</span><span class="sxs-lookup"><span data-stu-id="43b3d-365">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="43b3d-366">在電腦上不會保留任何資訊。</span><span class="sxs-lookup"><span data-stu-id="43b3d-366">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b3d-367">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43b3d-367">See Also</span></span>  
 [<span data-ttu-id="43b3d-368">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="43b3d-368">Windows Communication Foundation</span></span>](https://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [<span data-ttu-id="43b3d-369">安全性</span><span class="sxs-lookup"><span data-stu-id="43b3d-369">Security</span></span>](../../../docs/framework/wcf/feature-details/security.md)
