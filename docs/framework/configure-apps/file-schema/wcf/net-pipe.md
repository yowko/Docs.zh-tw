---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: d070b822cefeef3c281d5b0e47411f4c624dd83f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204602"
---
# \<net.pipe>

<span data-ttu-id="b8d13-102">指定 Named Pipe Activation Service 的組態設定，該服務會管理具名管道連線的存留期，並且會處理透過具名管道送達的啟用要求。</span><span class="sxs-lookup"><span data-stu-id="b8d13-102">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="b8d13-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="b8d13-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="b8d13-104">類型</span><span class="sxs-lookup"><span data-stu-id="b8d13-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8d13-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8d13-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b8d13-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b8d13-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8d13-107">屬性</span><span class="sxs-lookup"><span data-stu-id="b8d13-107">Attributes</span></span>  
  
|<span data-ttu-id="b8d13-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b8d13-108">Attribute</span></span>|<span data-ttu-id="b8d13-109">描述</span><span class="sxs-lookup"><span data-stu-id="b8d13-109">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="b8d13-110">整數，指定共用服務之接聽端點上、未完成之並行接收執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="b8d13-110">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="b8d13-111">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="b8d13-111">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="b8d13-112">整數，指定可以等候分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="b8d13-112">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="b8d13-113">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="b8d13-113">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b8d13-114"><xref:System.TimeSpan>，指定讀取框架資料以及從基礎連線執行連線分派的逾時。</span><span class="sxs-lookup"><span data-stu-id="b8d13-114">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="b8d13-115">預設為 "00:00:10"</span><span class="sxs-lookup"><span data-stu-id="b8d13-115">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8d13-116">子元素</span><span class="sxs-lookup"><span data-stu-id="b8d13-116">Child Elements</span></span>  
  
|<span data-ttu-id="b8d13-117">項目</span><span class="sxs-lookup"><span data-stu-id="b8d13-117">Element</span></span>|<span data-ttu-id="b8d13-118">描述</span><span class="sxs-lookup"><span data-stu-id="b8d13-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="b8d13-119">設定專案的集合，其中包含 `securityIdentifier` 屬性，可指定裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="b8d13-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8d13-120">父項目</span><span class="sxs-lookup"><span data-stu-id="b8d13-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b8d13-121">項目</span><span class="sxs-lookup"><span data-stu-id="b8d13-121">Element</span></span>|<span data-ttu-id="b8d13-122">描述</span><span class="sxs-lookup"><span data-stu-id="b8d13-122">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="b8d13-123">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="b8d13-123">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8d13-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8d13-124">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
