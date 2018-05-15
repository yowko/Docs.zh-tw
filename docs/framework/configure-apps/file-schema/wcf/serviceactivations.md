---
title: '&lt;v&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: c62f2bd1a34aca31ea9f9d5de17840f2967b269c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="28f3c-102">&lt;v&gt;</span><span class="sxs-lookup"><span data-stu-id="28f3c-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="28f3c-103">組態項目，可讓您新增設定，以定義虛擬服務啟用設定對應至您的 Windows Communication Foundation (WCF) 服務類型。</span><span class="sxs-lookup"><span data-stu-id="28f3c-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="28f3c-104">如此一來，不需 .svc 檔案也能啟動裝載於 WAS/IIS 中的服務。</span><span class="sxs-lookup"><span data-stu-id="28f3c-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="28f3c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="28f3c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="28f3c-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="28f3c-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="28f3c-107">\<v ></span><span class="sxs-lookup"><span data-stu-id="28f3c-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28f3c-108">語法</span><span class="sxs-lookup"><span data-stu-id="28f3c-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28f3c-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="28f3c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="28f3c-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="28f3c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28f3c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="28f3c-111">Attributes</span></span>  
 <span data-ttu-id="28f3c-112">無。</span><span class="sxs-lookup"><span data-stu-id="28f3c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="28f3c-113">子項目</span><span class="sxs-lookup"><span data-stu-id="28f3c-113">Child Elements</span></span>  
  
|<span data-ttu-id="28f3c-114">項目</span><span class="sxs-lookup"><span data-stu-id="28f3c-114">Element</span></span>|<span data-ttu-id="28f3c-115">描述</span><span class="sxs-lookup"><span data-stu-id="28f3c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28f3c-116">\<add></span><span class="sxs-lookup"><span data-stu-id="28f3c-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="28f3c-117">加入組態項目，此項目指定服務應用程式的啟動。</span><span class="sxs-lookup"><span data-stu-id="28f3c-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28f3c-118">父項目</span><span class="sxs-lookup"><span data-stu-id="28f3c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="28f3c-119">項目</span><span class="sxs-lookup"><span data-stu-id="28f3c-119">Element</span></span>|<span data-ttu-id="28f3c-120">描述</span><span class="sxs-lookup"><span data-stu-id="28f3c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28f3c-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="28f3c-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="28f3c-122">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="28f3c-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28f3c-123">備註</span><span class="sxs-lookup"><span data-stu-id="28f3c-123">Remarks</span></span>  
 <span data-ttu-id="28f3c-124">下列範例示範如何在您的 web.config 檔案中設定啟動設定。</span><span class="sxs-lookup"><span data-stu-id="28f3c-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="28f3c-125">使用這個組態時，您不需要使用 .svc 檔案也可以啟動 GreetingService。</span><span class="sxs-lookup"><span data-stu-id="28f3c-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="28f3c-126">請注意，`<serviceHostingEnvironment>` 是應用程式層級的組態。</span><span class="sxs-lookup"><span data-stu-id="28f3c-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="28f3c-127">您必須將包含該組態的 `web.config` 置於虛擬應用程式的根之下。</span><span class="sxs-lookup"><span data-stu-id="28f3c-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="28f3c-128">此外，`serviceHostingEnvironment` 是 machinetoApplication 可繼承的區段。</span><span class="sxs-lookup"><span data-stu-id="28f3c-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="28f3c-129">如果在電腦的根中註冊單一服務，則應用程式中的每個服務都會繼承這個服務。</span><span class="sxs-lookup"><span data-stu-id="28f3c-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="28f3c-130">以組態為主的啟動支援透過 HTTP 和非 HTTP 通訊協定啟動。</span><span class="sxs-lookup"><span data-stu-id="28f3c-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="28f3c-131">這項作業需要 relatativeAddress 中的擴充，也就是 .svc、.xoml 或 .xamlx。</span><span class="sxs-lookup"><span data-stu-id="28f3c-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="28f3c-132">您可以將自己的擴充對應至已知的 buildProvider，這樣您就可以透過任何擴充啟動服務。</span><span class="sxs-lookup"><span data-stu-id="28f3c-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="28f3c-133">發生衝突時，`<serviceActivations>` 區段會覆寫 .svc 註冊。</span><span class="sxs-lookup"><span data-stu-id="28f3c-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f3c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28f3c-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
