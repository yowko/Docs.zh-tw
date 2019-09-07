---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397720"
---
# <a name="netpipe"></a><span data-ttu-id="f39fd-102">\<net.pipe></span><span class="sxs-lookup"><span data-stu-id="f39fd-102">\<net.pipe></span></span>
<span data-ttu-id="f39fd-103">指定 Named Pipe Activation Service 的組態設定，該服務會管理具名管道連線的存留期，並且會處理透過具名管道送達的啟用要求。</span><span class="sxs-lookup"><span data-stu-id="f39fd-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
<span data-ttu-id="f39fd-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f39fd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f39fd-105">&nbsp;&nbsp;[ **\<System.servicemodel. 啟用 >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="f39fd-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="f39fd-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<net.pipe >**</span><span class="sxs-lookup"><span data-stu-id="f39fd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f39fd-107">語法</span><span class="sxs-lookup"><span data-stu-id="f39fd-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="f39fd-108">類型</span><span class="sxs-lookup"><span data-stu-id="f39fd-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f39fd-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f39fd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f39fd-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f39fd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f39fd-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f39fd-111">Attributes</span></span>  
  
|<span data-ttu-id="f39fd-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f39fd-112">Attribute</span></span>|<span data-ttu-id="f39fd-113">說明</span><span class="sxs-lookup"><span data-stu-id="f39fd-113">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="f39fd-114">整數，指定共用服務之接聽端點上、未完成之並行接收執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="f39fd-114">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="f39fd-115">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="f39fd-115">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="f39fd-116">整數，指定可以等候分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="f39fd-116">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="f39fd-117">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="f39fd-117">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f39fd-118"><xref:System.TimeSpan>，指定讀取框架資料以及從基礎連線執行連線分派的逾時。</span><span class="sxs-lookup"><span data-stu-id="f39fd-118">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="f39fd-119">預設為 "00:00:10"</span><span class="sxs-lookup"><span data-stu-id="f39fd-119">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f39fd-120">子元素</span><span class="sxs-lookup"><span data-stu-id="f39fd-120">Child Elements</span></span>  
  
|<span data-ttu-id="f39fd-121">項目</span><span class="sxs-lookup"><span data-stu-id="f39fd-121">Element</span></span>|<span data-ttu-id="f39fd-122">描述</span><span class="sxs-lookup"><span data-stu-id="f39fd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f39fd-123">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="f39fd-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="f39fd-124">Configuration 專案的集合，其中包含`securityIdentifier`屬性，以指定裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="f39fd-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f39fd-125">父項目</span><span class="sxs-lookup"><span data-stu-id="f39fd-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f39fd-126">項目</span><span class="sxs-lookup"><span data-stu-id="f39fd-126">Element</span></span>|<span data-ttu-id="f39fd-127">描述</span><span class="sxs-lookup"><span data-stu-id="f39fd-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f39fd-128">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="f39fd-128">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="f39fd-129">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="f39fd-129">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f39fd-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f39fd-130">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
