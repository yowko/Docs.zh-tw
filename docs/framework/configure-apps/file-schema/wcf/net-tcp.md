---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 589bae5d1f91e0424eb19cee62fe758aa7846191
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166513"
---
# <a name="nettcp"></a><span data-ttu-id="78f58-102">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="78f58-102">\<net.tcp></span></span>
<span data-ttu-id="78f58-103">指定 NET.TCP Port Sharing Service 的組態設定，此服務允許多個處理序共用相同的 TCP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="78f58-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="78f58-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="78f58-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="78f58-105">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="78f58-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f58-106">語法</span><span class="sxs-lookup"><span data-stu-id="78f58-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="78f58-107">類型</span><span class="sxs-lookup"><span data-stu-id="78f58-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78f58-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="78f58-108">Attributes and Elements</span></span>  
 <span data-ttu-id="78f58-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="78f58-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78f58-110">屬性</span><span class="sxs-lookup"><span data-stu-id="78f58-110">Attributes</span></span>  
  
|<span data-ttu-id="78f58-111">屬性</span><span class="sxs-lookup"><span data-stu-id="78f58-111">Attribute</span></span>|<span data-ttu-id="78f58-112">描述</span><span class="sxs-lookup"><span data-stu-id="78f58-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="78f58-113">整數，指定由共用連線所接受但是尚未分派到 Windows Communication Foundation (WCF) 服務的最大未完成連線。</span><span class="sxs-lookup"><span data-stu-id="78f58-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="78f58-114">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="78f58-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="78f58-115">整數，指定共用服務之接聽端點上、未完成之並行接收執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="78f58-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="78f58-116">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="78f58-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="78f58-117">接聽項上等待應用程式接受連線的最大數目。</span><span class="sxs-lookup"><span data-stu-id="78f58-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="78f58-118">當超過這個配額值時，新的傳入連線會被捨棄，而不是等待被接受。</span><span class="sxs-lookup"><span data-stu-id="78f58-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="78f58-119">如訊息安全性等連線功能，可能會導致用戶端開啟一個以上的連線。</span><span class="sxs-lookup"><span data-stu-id="78f58-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="78f58-120">在設定這個配額值時，服務系統管理員應該考量到其他連線。</span><span class="sxs-lookup"><span data-stu-id="78f58-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="78f58-121">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="78f58-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="78f58-122"><xref:System.TimeSpan>，指定讀取框架資料以及從基礎連線執行連線分派的逾時。</span><span class="sxs-lookup"><span data-stu-id="78f58-122">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="78f58-123">預設為 "00:00:10"。</span><span class="sxs-lookup"><span data-stu-id="78f58-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="78f58-124">布林值，指出是否連接埠共用服務會使用 Microsoft Teredo 服務代表 WCF 服務的 TCP 連接埠上接聽。</span><span class="sxs-lookup"><span data-stu-id="78f58-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="78f58-125">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="78f58-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78f58-126">子元素</span><span class="sxs-lookup"><span data-stu-id="78f58-126">Child Elements</span></span>  
  
|<span data-ttu-id="78f58-127">項目</span><span class="sxs-lookup"><span data-stu-id="78f58-127">Element</span></span>|<span data-ttu-id="78f58-128">描述</span><span class="sxs-lookup"><span data-stu-id="78f58-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78f58-129">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="78f58-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="78f58-130">包含的組態項目的集合`securityIdentifier`屬性來指定裝載 WCF 服務，且已授權可連線共用服務的存取權的處理程序的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="78f58-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78f58-131">父項目</span><span class="sxs-lookup"><span data-stu-id="78f58-131">Parent Elements</span></span>  
  
|<span data-ttu-id="78f58-132">項目</span><span class="sxs-lookup"><span data-stu-id="78f58-132">Element</span></span>|<span data-ttu-id="78f58-133">描述</span><span class="sxs-lookup"><span data-stu-id="78f58-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78f58-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="78f58-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="78f58-135">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="78f58-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78f58-136">備註</span><span class="sxs-lookup"><span data-stu-id="78f58-136">Remarks</span></span>  
 <span data-ttu-id="78f58-137">如需有關連接埠共用的詳細資訊，請參閱[Net.TCP 連接埠共用](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)。</span><span class="sxs-lookup"><span data-stu-id="78f58-137">For more information on port sharing, see [Net.TCP Port Sharing](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="78f58-138">若要了解如何設定連接埠共用服務，請參閱[設定 Net.TCP Port Sharing Service](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)。</span><span class="sxs-lookup"><span data-stu-id="78f58-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f58-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78f58-139">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="78f58-140">Net.TCP 連接埠共用</span><span class="sxs-lookup"><span data-stu-id="78f58-140">Net.TCP Port Sharing</span></span>](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="78f58-141">設定 Net.TCP 連接埠共用服務</span><span class="sxs-lookup"><span data-stu-id="78f58-141">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
