---
title: "設定 Net.TCP Port Sharing Service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 942b48ff6887e079beb7c0c24c6542a774eafe33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="1cda9-102">設定 Net.TCP Port Sharing Service</span><span class="sxs-lookup"><span data-stu-id="1cda9-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="1cda9-103">使用 Net.TCP 傳輸的自我裝載服務可以控制好幾項進階設定，例如 `ListenBacklog` 和 `MaxPendingAccepts`，這些設定掌管網路通訊時使用的基礎 TCP 通訊端行為。</span><span class="sxs-lookup"><span data-stu-id="1cda9-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="1cda9-104">但是，如果傳輸繫結已經停用連接埠共用 (預設為啟用)，則每個通訊端的這些設定只能套用在繫結層級中。</span><span class="sxs-lookup"><span data-stu-id="1cda9-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="1cda9-105">當 net.tcp 繫結啟用了連接埠共用 (在傳輸繫結項目上設定 `portSharingEnabled =true`)，就會隱含地允許外部處理序 (亦即 SMSvcHost.exe，可裝載 Net.TCP Port Sharing Service) 為自己管理 TCP 通訊端。</span><span class="sxs-lookup"><span data-stu-id="1cda9-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="1cda9-106">例如，使用 TCP 時請指定：</span><span class="sxs-lookup"><span data-stu-id="1cda9-106">For example, when using TCP, specify:</span></span>  
  
```xml  
    <tcpTransport   
        portSharingEnabled="true"  
/>  
```  
  
 <span data-ttu-id="1cda9-107">以這種方式進行設定時，任何在服務的傳輸繫結項目上指定的通訊端設定都會被忽略，且會優先使用 SMSvcHost.exe 所指定的通訊端設定。</span><span class="sxs-lookup"><span data-stu-id="1cda9-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="1cda9-108">若要設定 SMSvcHost.exe，請建立名為 SmSvcHost.exe.config 的 XML 組態檔並將其置放在與 SMSvcHost.exe 可執行檔相同的實體目錄中 (例如，C:\Windows\Microsoft.NET\Framework\v4.5)。</span><span class="sxs-lookup"><span data-stu-id="1cda9-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="1cda9-109">下列範例示範針對所有明確陳述之可設定值使用預設值的 SMSvcHost.exe.config 範例。</span><span class="sxs-lookup"><span data-stu-id="1cda9-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!—16 * # of processors -->  
          maxPendingAccepts="4"<!— 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!—30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="1cda9-110">需要修改 SMSvcHost.exe.config 時</span><span class="sxs-lookup"><span data-stu-id="1cda9-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="1cda9-111">一般來說，修改 SMSvcHost.exe.config 檔時需要特別小心，因為此檔中指定的任何組態設定都會影響電腦上使用 Net.TCP Port Sharing Service 的所有服務。</span><span class="sxs-lookup"><span data-stu-id="1cda9-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="1cda9-112">這當中包含了 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上使用 Windows Process Activation Service (WAS) 之 TCP 啟用功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1cda9-112">This includes applications on [!INCLUDE[wv](../../../../includes/wv-md.md)] that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="1cda9-113">但是，有時候您可能需要變更 Net.TCP Port Sharing Service 的預設組態。</span><span class="sxs-lookup"><span data-stu-id="1cda9-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="1cda9-114">例如，`maxPendingAccepts` 的預設值為 4 * 處理器數量。</span><span class="sxs-lookup"><span data-stu-id="1cda9-114">For example, the default value for `maxPendingAccepts` is 4 * number of processors.</span></span> <span data-ttu-id="1cda9-115">裝載大量使用連接埠共用服務的伺服器，可以增加此值來達到最大的輸送量。</span><span class="sxs-lookup"><span data-stu-id="1cda9-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="1cda9-116">`maxPendingConnections` 的預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="1cda9-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="1cda9-117">如果有多個並行用戶端都在呼叫服務，而服務正在卸除用戶端連接時，您也應該考慮增加這個值。</span><span class="sxs-lookup"><span data-stu-id="1cda9-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="1cda9-118">SMSvcHost.exe.config 同時包含一些可能會用到連接埠共用服務的處理序身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="1cda9-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="1cda9-119">當處理序連接至連接埠共用服務以運用共用的 TCP 連接埠時，會將正在連接的處理序之處理序身分識別與允許使用連接埠共用服務的身分識別清單進行比對。</span><span class="sxs-lookup"><span data-stu-id="1cda9-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="1cda9-120">這些身分識別中指定的安全性識別碼 (Sid) 為\<allowAccounts > SMSvcHost.exe.config 檔案的區段。</span><span class="sxs-lookup"><span data-stu-id="1cda9-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="1cda9-121">根據預設，系統帳戶 (LocalService、LocalSystem 和 NetworkService) 以及 Administrators 群組的成員會被授予使用連接埠共用服務的權限。</span><span class="sxs-lookup"><span data-stu-id="1cda9-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="1cda9-122">允許處理序以其他身分識別 (例如，使用者身分識別) 來執行以連接至連接埠共用服務的應用程式，必須明確地將適當的 SID 新增至 SMSvcHost.exe.config (這些變更會等到重新啟動 SMSvc.exe 處理序之後才套用)。</span><span class="sxs-lookup"><span data-stu-id="1cda9-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cda9-123">在啟用了使用者帳戶控制 (UAC) 的 [!INCLUDE[wv](../../../../includes/wv-md.md)] 系統上，即使本機使用者屬於 Administrators 群組的成員之一，還是需要較高的權限。</span><span class="sxs-lookup"><span data-stu-id="1cda9-123">On [!INCLUDE[wv](../../../../includes/wv-md.md)] systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="1cda9-124">若要允許這些使用者使用的連接埠共用服務不提高權限，使用者的 SID （或使用者成員群組的 SID） 必須明確加入至\<allowAccounts > SMSvcHost.exe.config 的區段。</span><span class="sxs-lookup"><span data-stu-id="1cda9-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="1cda9-125">預設的 SMSvcHost.exe.config 檔案會指定自訂 `etwProviderId` 來防止 SMSvcHost.exe 追蹤干擾服務追蹤。</span><span class="sxs-lookup"><span data-stu-id="1cda9-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cda9-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="1cda9-126">See Also</span></span>  
 [<span data-ttu-id="1cda9-127">\<net.tcp ></span><span class="sxs-lookup"><span data-stu-id="1cda9-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
