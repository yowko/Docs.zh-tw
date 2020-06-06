---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855143"
---
# \<serviceActivations>

<span data-ttu-id="85fb6-101">一種 configuration 專案，可讓您新增設定，以定義對應至您的 Windows Communication Foundation （WCF）服務類型的虛擬服務啟用設定。</span><span class="sxs-lookup"><span data-stu-id="85fb6-101">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="85fb6-102">如此一來，不需 .svc 檔案也能啟動裝載於 WAS/IIS 中的服務。</span><span class="sxs-lookup"><span data-stu-id="85fb6-102">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

## <a name="syntax"></a><span data-ttu-id="85fb6-103">語法</span><span class="sxs-lookup"><span data-stu-id="85fb6-103">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="85fb6-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="85fb6-104">Attributes and Elements</span></span>

<span data-ttu-id="85fb6-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="85fb6-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="85fb6-106">屬性</span><span class="sxs-lookup"><span data-stu-id="85fb6-106">Attributes</span></span>

<span data-ttu-id="85fb6-107">無。</span><span class="sxs-lookup"><span data-stu-id="85fb6-107">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="85fb6-108">子元素</span><span class="sxs-lookup"><span data-stu-id="85fb6-108">Child Elements</span></span>

|<span data-ttu-id="85fb6-109">元素</span><span class="sxs-lookup"><span data-stu-id="85fb6-109">Element</span></span>|<span data-ttu-id="85fb6-110">描述</span><span class="sxs-lookup"><span data-stu-id="85fb6-110">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|<span data-ttu-id="85fb6-111">加入組態項目，此項目指定服務應用程式的啟動。</span><span class="sxs-lookup"><span data-stu-id="85fb6-111">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="85fb6-112">父項目</span><span class="sxs-lookup"><span data-stu-id="85fb6-112">Parent Elements</span></span>

|<span data-ttu-id="85fb6-113">元素</span><span class="sxs-lookup"><span data-stu-id="85fb6-113">Element</span></span>|<span data-ttu-id="85fb6-114">描述</span><span class="sxs-lookup"><span data-stu-id="85fb6-114">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="85fb6-115">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="85fb6-115">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="85fb6-116">備註</span><span class="sxs-lookup"><span data-stu-id="85fb6-116">Remarks</span></span>

<span data-ttu-id="85fb6-117">下列範例示範如何在您的 web.config 檔案中設定啟動設定。</span><span class="sxs-lookup"><span data-stu-id="85fb6-117">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="85fb6-118">使用這個組態時，您不需要使用 .svc 檔案也可以啟動 GreetingService。</span><span class="sxs-lookup"><span data-stu-id="85fb6-118">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="85fb6-119">請注意，`<serviceHostingEnvironment>` 是應用程式層級的組態。</span><span class="sxs-lookup"><span data-stu-id="85fb6-119">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="85fb6-120">您必須將包含該組態的 `web.config` 置於虛擬應用程式的根之下。</span><span class="sxs-lookup"><span data-stu-id="85fb6-120">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="85fb6-121">此外， `serviceHostingEnvironment` 是可繼承的 machineToApplication 區段。</span><span class="sxs-lookup"><span data-stu-id="85fb6-121">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="85fb6-122">如果在電腦的根中註冊單一服務，則應用程式中的每個服務都會繼承這個服務。</span><span class="sxs-lookup"><span data-stu-id="85fb6-122">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="85fb6-123">以組態為主的啟動支援透過 HTTP 和非 HTTP 通訊協定啟動。</span><span class="sxs-lookup"><span data-stu-id="85fb6-123">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="85fb6-124">它需要 relativeAddress 中的延伸模組，例如 .svc、. xoml 或. service1.xamlx。</span><span class="sxs-lookup"><span data-stu-id="85fb6-124">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="85fb6-125">您可以將自己的擴充對應至已知的 buildProvider，這樣您就可以透過任何擴充啟動服務。</span><span class="sxs-lookup"><span data-stu-id="85fb6-125">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="85fb6-126">發生衝突時，`<serviceActivations>` 區段會覆寫 .svc 註冊。</span><span class="sxs-lookup"><span data-stu-id="85fb6-126">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="85fb6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85fb6-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
