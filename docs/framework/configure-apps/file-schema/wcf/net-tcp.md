---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 12709d58d9192825598b15a50baa10a54450226e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178069"
---
# \<net.tcp>

<span data-ttu-id="ca575-102">指定 NET.TCP Port Sharing Service 的組態設定，此服務允許多個處理序共用相同的 TCP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="ca575-102">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a><span data-ttu-id="ca575-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca575-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="ca575-104">類型</span><span class="sxs-lookup"><span data-stu-id="ca575-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca575-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ca575-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ca575-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ca575-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca575-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ca575-107">Attributes</span></span>  
  
|<span data-ttu-id="ca575-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ca575-108">Attribute</span></span>|<span data-ttu-id="ca575-109">描述</span><span class="sxs-lookup"><span data-stu-id="ca575-109">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="ca575-110">整數，指定從共用連接接受但尚未分派至 Windows Communication Foundation (WCF) 服務的最大未處理連接。</span><span class="sxs-lookup"><span data-stu-id="ca575-110">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="ca575-111">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="ca575-111">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="ca575-112">整數，指定共用服務之接聽端點上、未完成之並行接收執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="ca575-112">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="ca575-113">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="ca575-113">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="ca575-114">接聽項上等待應用程式接受連線的最大數目。</span><span class="sxs-lookup"><span data-stu-id="ca575-114">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="ca575-115">當超過這個配額值時，新的傳入連線會被捨棄，而不是等待被接受。</span><span class="sxs-lookup"><span data-stu-id="ca575-115">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="ca575-116">如訊息安全性等連線功能，可能會導致用戶端開啟一個以上的連線。</span><span class="sxs-lookup"><span data-stu-id="ca575-116">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="ca575-117">在設定這個配額值時，服務系統管理員應該考量到其他連線。</span><span class="sxs-lookup"><span data-stu-id="ca575-117">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="ca575-118">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="ca575-118">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ca575-119"><xref:System.TimeSpan>，指定讀取框架資料以及從基礎連線執行連線分派的逾時。</span><span class="sxs-lookup"><span data-stu-id="ca575-119">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="ca575-120">預設為 "00:00:10"。</span><span class="sxs-lookup"><span data-stu-id="ca575-120">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="ca575-121">布林值，指出埠共用服務是否使用 Microsoft Teredo 服務代表 WCF 服務接聽 TCP 埠。</span><span class="sxs-lookup"><span data-stu-id="ca575-121">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="ca575-122">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="ca575-122">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca575-123">子元素</span><span class="sxs-lookup"><span data-stu-id="ca575-123">Child Elements</span></span>  
  
|<span data-ttu-id="ca575-124">項目</span><span class="sxs-lookup"><span data-stu-id="ca575-124">Element</span></span>|<span data-ttu-id="ca575-125">描述</span><span class="sxs-lookup"><span data-stu-id="ca575-125">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="ca575-126">設定專案的集合，其中包含 `securityIdentifier` 屬性，可指定裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="ca575-126">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca575-127">父項目</span><span class="sxs-lookup"><span data-stu-id="ca575-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ca575-128">項目</span><span class="sxs-lookup"><span data-stu-id="ca575-128">Element</span></span>|<span data-ttu-id="ca575-129">描述</span><span class="sxs-lookup"><span data-stu-id="ca575-129">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="ca575-130">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="ca575-130">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca575-131">備註</span><span class="sxs-lookup"><span data-stu-id="ca575-131">Remarks</span></span>  

 <span data-ttu-id="ca575-132">如需埠共用的詳細資訊，請參閱 [Net.tcp 埠共用](../../../wcf/feature-details/net-tcp-port-sharing.md)。</span><span class="sxs-lookup"><span data-stu-id="ca575-132">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="ca575-133">若要瞭解如何設定埠共用服務，請參閱設定 [Net.tcp 埠共用服務](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)。</span><span class="sxs-lookup"><span data-stu-id="ca575-133">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca575-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca575-134">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="ca575-135">Net.TCP Port Sharing</span><span class="sxs-lookup"><span data-stu-id="ca575-135">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="ca575-136">設定 Net.TCP Port Sharing Service</span><span class="sxs-lookup"><span data-stu-id="ca575-136">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
