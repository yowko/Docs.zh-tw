---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: fb7c699612ef12aae39aaeadaf170d0e8f2553cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936438"
---
# <a name="serviceactivations"></a><span data-ttu-id="2fe60-101">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="2fe60-101">\<serviceActivations></span></span>

<span data-ttu-id="2fe60-102">一種 configuration 專案, 可讓您新增設定, 以定義對應至您的 Windows Communication Foundation (WCF) 服務類型的虛擬服務啟用設定。</span><span class="sxs-lookup"><span data-stu-id="2fe60-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="2fe60-103">如此一來，不需 .svc 檔案也能啟動裝載於 WAS/IIS 中的服務。</span><span class="sxs-lookup"><span data-stu-id="2fe60-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="2fe60-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2fe60-104">\<system.ServiceModel></span></span>\
<span data-ttu-id="2fe60-105">\<serviceHostingEnvironment > </span><span class="sxs-lookup"><span data-stu-id="2fe60-105">\<serviceHostingEnvironment></span></span>\
<span data-ttu-id="2fe60-106">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="2fe60-106">\<serviceActivations></span></span>

## <a name="syntax"></a><span data-ttu-id="2fe60-107">語法</span><span class="sxs-lookup"><span data-stu-id="2fe60-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2fe60-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2fe60-108">Attributes and Elements</span></span>

<span data-ttu-id="2fe60-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2fe60-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2fe60-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2fe60-110">Attributes</span></span>

<span data-ttu-id="2fe60-111">無。</span><span class="sxs-lookup"><span data-stu-id="2fe60-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2fe60-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2fe60-112">Child Elements</span></span>

|<span data-ttu-id="2fe60-113">項目</span><span class="sxs-lookup"><span data-stu-id="2fe60-113">Element</span></span>|<span data-ttu-id="2fe60-114">說明</span><span class="sxs-lookup"><span data-stu-id="2fe60-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fe60-115">\<add></span><span class="sxs-lookup"><span data-stu-id="2fe60-115">\<add></span></span>](add-of-serviceactivations.md)|<span data-ttu-id="2fe60-116">加入組態項目，此項目指定服務應用程式的啟動。</span><span class="sxs-lookup"><span data-stu-id="2fe60-116">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2fe60-117">父項目</span><span class="sxs-lookup"><span data-stu-id="2fe60-117">Parent Elements</span></span>

|<span data-ttu-id="2fe60-118">項目</span><span class="sxs-lookup"><span data-stu-id="2fe60-118">Element</span></span>|<span data-ttu-id="2fe60-119">說明</span><span class="sxs-lookup"><span data-stu-id="2fe60-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fe60-120">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="2fe60-120">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="2fe60-121">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="2fe60-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2fe60-122">備註</span><span class="sxs-lookup"><span data-stu-id="2fe60-122">Remarks</span></span>

<span data-ttu-id="2fe60-123">下列範例示範如何在您的 web.config 檔案中設定啟動設定。</span><span class="sxs-lookup"><span data-stu-id="2fe60-123">The following example shows how to configure activation settings within your web.config file.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="2fe60-124">使用這個組態時，您不需要使用 .svc 檔案也可以啟動 GreetingService。</span><span class="sxs-lookup"><span data-stu-id="2fe60-124">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="2fe60-125">請注意，`<serviceHostingEnvironment>` 是應用程式層級的組態。</span><span class="sxs-lookup"><span data-stu-id="2fe60-125">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="2fe60-126">您必須將包含該組態的 `web.config` 置於虛擬應用程式的根之下。</span><span class="sxs-lookup"><span data-stu-id="2fe60-126">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="2fe60-127">此外, `serviceHostingEnvironment`是可繼承的 machineToApplication 區段。</span><span class="sxs-lookup"><span data-stu-id="2fe60-127">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="2fe60-128">如果在電腦的根中註冊單一服務，則應用程式中的每個服務都會繼承這個服務。</span><span class="sxs-lookup"><span data-stu-id="2fe60-128">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="2fe60-129">以組態為主的啟動支援透過 HTTP 和非 HTTP 通訊協定啟動。</span><span class="sxs-lookup"><span data-stu-id="2fe60-129">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="2fe60-130">它需要 relativeAddress 中的延伸模組, 例如 .svc、. xoml 或. service1.xamlx。</span><span class="sxs-lookup"><span data-stu-id="2fe60-130">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="2fe60-131">您可以將自己的擴充對應至已知的 buildProvider，這樣您就可以透過任何擴充啟動服務。</span><span class="sxs-lookup"><span data-stu-id="2fe60-131">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="2fe60-132">發生衝突時，`<serviceActivations>` 區段會覆寫 .svc 註冊。</span><span class="sxs-lookup"><span data-stu-id="2fe60-132">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fe60-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fe60-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
