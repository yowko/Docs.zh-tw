---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 885cfad7be42f7c48b4c061f3293d667eb5d4ad8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103388"
---
# <a name="netpipe"></a><span data-ttu-id="fb39d-102">\<net.pipe></span><span class="sxs-lookup"><span data-stu-id="fb39d-102">\<net.pipe></span></span>
<span data-ttu-id="fb39d-103">指定 Named Pipe Activation Service 的組態設定，該服務會管理具名管道連線的存留期，並且會處理透過具名管道送達的啟用要求。</span><span class="sxs-lookup"><span data-stu-id="fb39d-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="fb39d-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="fb39d-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="fb39d-105">\<net.pipe></span><span class="sxs-lookup"><span data-stu-id="fb39d-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb39d-106">語法</span><span class="sxs-lookup"><span data-stu-id="fb39d-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="fb39d-107">類型</span><span class="sxs-lookup"><span data-stu-id="fb39d-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb39d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fb39d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fb39d-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fb39d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb39d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="fb39d-110">Attributes</span></span>  
  
|<span data-ttu-id="fb39d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="fb39d-111">Attribute</span></span>|<span data-ttu-id="fb39d-112">描述</span><span class="sxs-lookup"><span data-stu-id="fb39d-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="fb39d-113">整數，指定共用服務之接聽端點上、未完成之並行接收執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="fb39d-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="fb39d-114">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="fb39d-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="fb39d-115">整數，指定可以等候分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="fb39d-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="fb39d-116">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="fb39d-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="fb39d-117"><xref:System.TimeSpan>，指定讀取框架資料以及從基礎連線執行連線分派的逾時。</span><span class="sxs-lookup"><span data-stu-id="fb39d-117">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="fb39d-118">預設為 "00:00:10"</span><span class="sxs-lookup"><span data-stu-id="fb39d-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb39d-119">子元素</span><span class="sxs-lookup"><span data-stu-id="fb39d-119">Child Elements</span></span>  
  
|<span data-ttu-id="fb39d-120">項目</span><span class="sxs-lookup"><span data-stu-id="fb39d-120">Element</span></span>|<span data-ttu-id="fb39d-121">描述</span><span class="sxs-lookup"><span data-stu-id="fb39d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb39d-122">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="fb39d-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="fb39d-123">包含的組態項目的集合`securityIdentifier`屬性來指定裝載 WCF 服務，且已授權可連線共用服務的存取權的處理程序的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb39d-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb39d-124">父項目</span><span class="sxs-lookup"><span data-stu-id="fb39d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fb39d-125">項目</span><span class="sxs-lookup"><span data-stu-id="fb39d-125">Element</span></span>|<span data-ttu-id="fb39d-126">描述</span><span class="sxs-lookup"><span data-stu-id="fb39d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb39d-127">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="fb39d-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="fb39d-128">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="fb39d-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb39d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb39d-129">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
