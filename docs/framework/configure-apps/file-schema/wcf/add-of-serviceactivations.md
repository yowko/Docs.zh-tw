---
title: <add> 的 <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850325"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="724e1-102">\<add> 的 \<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="724e1-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="724e1-103">一種 configuration 專案，可讓您定義虛擬服務啟用設定，以對應至您的 Windows Communication Foundation （WCF）服務類型。</span><span class="sxs-lookup"><span data-stu-id="724e1-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="724e1-104">如此一來，不需 .svc 檔案也能啟動裝載於 WAS/IIS 中的服務。</span><span class="sxs-lookup"><span data-stu-id="724e1-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="724e1-105">語法</span><span class="sxs-lookup"><span data-stu-id="724e1-105">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="724e1-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="724e1-106">Attributes and Elements</span></span>

<span data-ttu-id="724e1-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="724e1-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="724e1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="724e1-108">Attributes</span></span>

|<span data-ttu-id="724e1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="724e1-109">Attribute</span></span>|<span data-ttu-id="724e1-110">描述</span><span class="sxs-lookup"><span data-stu-id="724e1-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="724e1-111">工廠</span><span class="sxs-lookup"><span data-stu-id="724e1-111">factory</span></span>|<span data-ttu-id="724e1-112">字串，指定產生服務啟動項目之處理站的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="724e1-112">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="724e1-113">服務</span><span class="sxs-lookup"><span data-stu-id="724e1-113">service</span></span>|<span data-ttu-id="724e1-114">實作服務的 ServiceType 可以是完整 Typename 或簡短 Typename (置於 App_Code 資料夾時)。</span><span class="sxs-lookup"><span data-stu-id="724e1-114">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="724e1-115">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="724e1-115">relativeAddress</span></span>|<span data-ttu-id="724e1-116">在目前 IIS 應用程式中的相對位址，例如 "Service.svc"。</span><span class="sxs-lookup"><span data-stu-id="724e1-116">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="724e1-117">在 WCF 4.0 中，此相對位址必須包含其中一個已知副檔名（.svc、. service1.xamlx、...）。RelativeUrl 不存在任何實體檔案</span><span class="sxs-lookup"><span data-stu-id="724e1-117">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="724e1-118">子元素</span><span class="sxs-lookup"><span data-stu-id="724e1-118">Child Elements</span></span>

<span data-ttu-id="724e1-119">無。</span><span class="sxs-lookup"><span data-stu-id="724e1-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="724e1-120">父項目</span><span class="sxs-lookup"><span data-stu-id="724e1-120">Parent Elements</span></span>

|<span data-ttu-id="724e1-121">元素</span><span class="sxs-lookup"><span data-stu-id="724e1-121">Element</span></span>|<span data-ttu-id="724e1-122">描述</span><span class="sxs-lookup"><span data-stu-id="724e1-122">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="724e1-123">描述啟動設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="724e1-123">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="724e1-124">備註</span><span class="sxs-lookup"><span data-stu-id="724e1-124">Remarks</span></span>

<span data-ttu-id="724e1-125">下列範例示範如何在您的 web.config 檔案中設定啟動設定。</span><span class="sxs-lookup"><span data-stu-id="724e1-125">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="724e1-126">使用這個組態時，您不需要使用 .svc 檔案也可以啟動 GreetingService。</span><span class="sxs-lookup"><span data-stu-id="724e1-126">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="724e1-127">請注意，`<serviceHostingEnvironment>` 是應用程式層級的組態。</span><span class="sxs-lookup"><span data-stu-id="724e1-127">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="724e1-128">您必須將包含該組態的 `web.config` 置於虛擬應用程式的根之下。</span><span class="sxs-lookup"><span data-stu-id="724e1-128">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="724e1-129">此外， `serviceHostingEnvironment` 是可繼承的 machineToApplication 區段。</span><span class="sxs-lookup"><span data-stu-id="724e1-129">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="724e1-130">如果在電腦的根中註冊單一服務，則應用程式中的每個服務都會繼承這個服務。</span><span class="sxs-lookup"><span data-stu-id="724e1-130">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="724e1-131">以組態為主的啟動支援透過 HTTP 和非 HTTP 通訊協定啟動。</span><span class="sxs-lookup"><span data-stu-id="724e1-131">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="724e1-132">它需要 relativeAddress 中的延伸模組，也就是 .svc、. xoml 或. service1.xamlx。</span><span class="sxs-lookup"><span data-stu-id="724e1-132">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="724e1-133">您可以將自己的擴充對應至已知的 buildProvider，這樣您就可以透過任何擴充啟動服務。</span><span class="sxs-lookup"><span data-stu-id="724e1-133">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="724e1-134">發生衝突時，`<serviceActivations>` 區段會覆寫 .svc 註冊。</span><span class="sxs-lookup"><span data-stu-id="724e1-134">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="724e1-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="724e1-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
