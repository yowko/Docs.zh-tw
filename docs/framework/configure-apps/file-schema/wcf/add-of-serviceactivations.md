---
title: '&lt;serviceActivations&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 1a25ad517e26e037c588bb14844e38147e251d96
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745821"
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a><span data-ttu-id="4c366-102">&lt;serviceActivations&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="4c366-102">&lt;add&gt; of &lt;serviceActivations&gt;</span></span>
<span data-ttu-id="4c366-103">可讓您定義虛擬服務啟用設定對應至您的 Windows Communication Foundation (WCF) 服務類型組態項目。</span><span class="sxs-lookup"><span data-stu-id="4c366-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="4c366-104">如此一來，不需 .svc 檔案也能啟動裝載於 WAS/IIS 中的服務。</span><span class="sxs-lookup"><span data-stu-id="4c366-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="4c366-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4c366-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="4c366-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="4c366-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c366-107">語法</span><span class="sxs-lookup"><span data-stu-id="4c366-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c366-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4c366-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4c366-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4c366-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c366-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4c366-110">Attributes</span></span>  
  
|<span data-ttu-id="4c366-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4c366-111">Attribute</span></span>|<span data-ttu-id="4c366-112">描述</span><span class="sxs-lookup"><span data-stu-id="4c366-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c366-113">factory</span><span class="sxs-lookup"><span data-stu-id="4c366-113">factory</span></span>|<span data-ttu-id="4c366-114">字串，指定產生服務啟動項目之處理站的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="4c366-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|  
|<span data-ttu-id="4c366-115">服務</span><span class="sxs-lookup"><span data-stu-id="4c366-115">service</span></span>|<span data-ttu-id="4c366-116">實作服務的 ServiceType 可以是完整 Typename 或簡短 Typename (置於 App_Code 資料夾時)。</span><span class="sxs-lookup"><span data-stu-id="4c366-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|  
|<span data-ttu-id="4c366-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="4c366-117">relativeAddress</span></span>|<span data-ttu-id="4c366-118">在目前 IIS 應用程式中的相對位址，例如 "Service.svc"。</span><span class="sxs-lookup"><span data-stu-id="4c366-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="4c366-119">在 WCF 4.0 中，此相對位址必須包含其中一個已知的副檔名 (.svc、.xamlx...)。relativeUrl 不一定要有實體檔案存在</span><span class="sxs-lookup"><span data-stu-id="4c366-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c366-120">子項目</span><span class="sxs-lookup"><span data-stu-id="4c366-120">Child Elements</span></span>  
 <span data-ttu-id="4c366-121">無。</span><span class="sxs-lookup"><span data-stu-id="4c366-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c366-122">父項目</span><span class="sxs-lookup"><span data-stu-id="4c366-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4c366-123">項目</span><span class="sxs-lookup"><span data-stu-id="4c366-123">Element</span></span>|<span data-ttu-id="4c366-124">描述</span><span class="sxs-lookup"><span data-stu-id="4c366-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c366-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="4c366-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="4c366-126">描述啟動設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="4c366-126">A configuration section that describes activation settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c366-127">備註</span><span class="sxs-lookup"><span data-stu-id="4c366-127">Remarks</span></span>  
 <span data-ttu-id="4c366-128">下列範例示範如何在您的 web.config 檔案中設定啟動設定。</span><span class="sxs-lookup"><span data-stu-id="4c366-128">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="4c366-129">使用這個組態時，您不需要使用 .svc 檔案也可以啟動 GreetingService。</span><span class="sxs-lookup"><span data-stu-id="4c366-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="4c366-130">請注意，`<serviceHostingEnvironment>` 是應用程式層級的組態。</span><span class="sxs-lookup"><span data-stu-id="4c366-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="4c366-131">您必須將包含該組態的 `web.config` 置於虛擬應用程式的根之下。</span><span class="sxs-lookup"><span data-stu-id="4c366-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="4c366-132">此外，`serviceHostingEnvironment` 是 machinetoApplication 可繼承的區段。</span><span class="sxs-lookup"><span data-stu-id="4c366-132">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="4c366-133">如果在電腦的根中註冊單一服務，則應用程式中的每個服務都會繼承這個服務。</span><span class="sxs-lookup"><span data-stu-id="4c366-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="4c366-134">以組態為主的啟動支援透過 HTTP 和非 HTTP 通訊協定啟動。</span><span class="sxs-lookup"><span data-stu-id="4c366-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="4c366-135">這項作業需要 relatativeAddress 中的擴充，也就是 .svc、.xoml 或 .xamlx。</span><span class="sxs-lookup"><span data-stu-id="4c366-135">It requires extensions in the relatativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="4c366-136">您可以將自己的擴充對應至已知的 buildProvider，這樣您就可以透過任何擴充啟動服務。</span><span class="sxs-lookup"><span data-stu-id="4c366-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="4c366-137">發生衝突時，`<serviceActivations>` 區段會覆寫 .svc 註冊。</span><span class="sxs-lookup"><span data-stu-id="4c366-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c366-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c366-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
