---
title: '&lt;net.pipe&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 918ee745e12a339b71f228f3f79b366335d7824d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltnetpipegt"></a><span data-ttu-id="857b0-102">&lt;net.pipe&gt;</span><span class="sxs-lookup"><span data-stu-id="857b0-102">&lt;net.pipe&gt;</span></span>
<span data-ttu-id="857b0-103">指定 Named Pipe Activation Service 的組態設定，該服務會管理具名管道連線的存留期，並且會處理透過具名管道送達的啟用要求。</span><span class="sxs-lookup"><span data-stu-id="857b0-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="857b0-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="857b0-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="857b0-105">\<net.pipe ></span><span class="sxs-lookup"><span data-stu-id="857b0-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="857b0-106">語法</span><span class="sxs-lookup"><span data-stu-id="857b0-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
          <allowAccounts>  
             // LocalSystem account  
             <add securityIdentifier="S-1-5-18"/>  
             // LocalService account  
             <add securityIdentifier="S-1-5-19"/>  
             // Administrators account  
             <add securityIdentifier="S-1-5-20"/>  
             // Network Service account  
             <add securityIdentifier="S-1-5-32-544" />  
             // IIS_IUSRS account (Vista only)  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="857b0-107">類型</span><span class="sxs-lookup"><span data-stu-id="857b0-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="857b0-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="857b0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="857b0-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="857b0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="857b0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="857b0-110">Attributes</span></span>  
  
|<span data-ttu-id="857b0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="857b0-111">Attribute</span></span>|<span data-ttu-id="857b0-112">描述</span><span class="sxs-lookup"><span data-stu-id="857b0-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="857b0-113">整數，指定共用服務之接聽端點上、未完成之並行接收執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="857b0-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="857b0-114">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="857b0-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="857b0-115">整數，指定可以等候分派之連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="857b0-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="857b0-116">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="857b0-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="857b0-117">`TimeSpan`，指定讀取框架資料以及從基礎連線執行連線分派的逾時。</span><span class="sxs-lookup"><span data-stu-id="857b0-117">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="857b0-118">預設為 "00:00:10"</span><span class="sxs-lookup"><span data-stu-id="857b0-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="857b0-119">子元素</span><span class="sxs-lookup"><span data-stu-id="857b0-119">Child Elements</span></span>  
  
|<span data-ttu-id="857b0-120">項目</span><span class="sxs-lookup"><span data-stu-id="857b0-120">Element</span></span>|<span data-ttu-id="857b0-121">說明</span><span class="sxs-lookup"><span data-stu-id="857b0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="857b0-122">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="857b0-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="857b0-123">組態項目的集合，其中包含 `securityIdentifier` 屬性，此屬性可為裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務且已授權可連線共用服務的處理序指定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="857b0-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="857b0-124">父項目</span><span class="sxs-lookup"><span data-stu-id="857b0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="857b0-125">項目</span><span class="sxs-lookup"><span data-stu-id="857b0-125">Element</span></span>|<span data-ttu-id="857b0-126">說明</span><span class="sxs-lookup"><span data-stu-id="857b0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="857b0-127">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="857b0-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="857b0-128">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="857b0-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="857b0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="857b0-129">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
