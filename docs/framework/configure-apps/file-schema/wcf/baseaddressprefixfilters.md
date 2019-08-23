---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 8a59f651318e18411b1485fc4eebeb7a550afca0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919860"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="36e5f-101">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="36e5f-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="36e5f-102">代表設定專案的集合, 這些專案會指定 [傳遞篩選準則], 以在 IIS 中裝載 Windows Communication Foundation (WCF) 應用程式時, 提供挑選適當 Internet Information Services (IIS) 系結的機制。</span><span class="sxs-lookup"><span data-stu-id="36e5f-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="36e5f-103">\<baseAddressPrefixFilters > 無法辨識 "localhost", 請改用完整的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="36e5f-103">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="36e5f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="36e5f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="36e5f-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="36e5f-105">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36e5f-106">語法</span><span class="sxs-lookup"><span data-stu-id="36e5f-106">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36e5f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="36e5f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="36e5f-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="36e5f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36e5f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="36e5f-109">Attributes</span></span>  
 <span data-ttu-id="36e5f-110">無。</span><span class="sxs-lookup"><span data-stu-id="36e5f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36e5f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="36e5f-111">Child Elements</span></span>  
  
|<span data-ttu-id="36e5f-112">項目</span><span class="sxs-lookup"><span data-stu-id="36e5f-112">Element</span></span>|<span data-ttu-id="36e5f-113">說明</span><span class="sxs-lookup"><span data-stu-id="36e5f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36e5f-114">\<add></span><span class="sxs-lookup"><span data-stu-id="36e5f-114">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="36e5f-115">新增組態項目，這個項目會指定由服務主機使用之基底位址的前置詞篩選條件。</span><span class="sxs-lookup"><span data-stu-id="36e5f-115">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36e5f-116">父項目</span><span class="sxs-lookup"><span data-stu-id="36e5f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="36e5f-117">項目</span><span class="sxs-lookup"><span data-stu-id="36e5f-117">Element</span></span>|<span data-ttu-id="36e5f-118">描述</span><span class="sxs-lookup"><span data-stu-id="36e5f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36e5f-119">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="36e5f-119">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="36e5f-120">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="36e5f-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36e5f-121">備註</span><span class="sxs-lookup"><span data-stu-id="36e5f-121">Remarks</span></span>  
 <span data-ttu-id="36e5f-122">前置詞篩選條件為共用裝載提供者提供一種方式，使其可指定服務所要使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="36e5f-122">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="36e5f-123">它可讓共用主機在同一個網站上裝載多個應用程式，而且同一個配置中可以有不同的基底位址。</span><span class="sxs-lookup"><span data-stu-id="36e5f-123">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="36e5f-124">IIS 網站是包含虛擬目錄的虛擬應用程式的容器 (Container)。</span><span class="sxs-lookup"><span data-stu-id="36e5f-124">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="36e5f-125">網站中的應用程式則可以透過一個或多個 IIS 繫結來存取。</span><span class="sxs-lookup"><span data-stu-id="36e5f-125">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="36e5f-126">IIS 繫結提供繫結通訊協定和繫結這兩項資訊。</span><span class="sxs-lookup"><span data-stu-id="36e5f-126">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="36e5f-127">繫結通訊協定 (例如 HTTP) 會定義產生通訊的配置，而繫結資訊 (例如 IPAddress、Port、Hostheader) 包含用來存取該網站的資料。</span><span class="sxs-lookup"><span data-stu-id="36e5f-127">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="36e5f-128">IIS 支援為每個網站指定多個 IIS 繫結，讓每個配置都有多個基底位址。</span><span class="sxs-lookup"><span data-stu-id="36e5f-128">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="36e5f-129">由於裝載在網站下的 WCF 服務只允許針對每個配置系結至一個基底位址, 因此您可以使用前置詞篩選功能來挑選託管服務所需的基底位址。</span><span class="sxs-lookup"><span data-stu-id="36e5f-129">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="36e5f-130">IIS 提供的傳入基底位址會依據選擇性的前置詞清單篩選條件進行篩選。</span><span class="sxs-lookup"><span data-stu-id="36e5f-130">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="36e5f-131">例如，您的網站可能包含下列基底位址。</span><span class="sxs-lookup"><span data-stu-id="36e5f-131">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="36e5f-132">您可以使用下列組態檔在 appdomain 層級指定前置詞篩選條件。</span><span class="sxs-lookup"><span data-stu-id="36e5f-132">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="36e5f-133">在此範例中，`net.tcp://test1.fabrikam.com:8000` 和 `http://test2.fabrikam.com:9000` 分別是其配置的唯一基底位址，而且已被允許通過篩選。</span><span class="sxs-lookup"><span data-stu-id="36e5f-133">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="36e5f-134">根據預設，如果沒有指定前置詞，則所有位址都會通過。</span><span class="sxs-lookup"><span data-stu-id="36e5f-134">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="36e5f-135">如果指定前置詞，則只會允許要通過之配置的相符基底位址。</span><span class="sxs-lookup"><span data-stu-id="36e5f-135">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36e5f-136">篩選條件不支援任何萬用字元。</span><span class="sxs-lookup"><span data-stu-id="36e5f-136">The filter does not support any wildcards.</span></span> <span data-ttu-id="36e5f-137">此外，IIS 提供的 baseAddress 中，可能會有位址繫結程序至不在 `baseAddressPrefixFilters` 清單中的配置，</span><span class="sxs-lookup"><span data-stu-id="36e5f-137">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="36e5f-138">而且這些位址尚未經過篩選。</span><span class="sxs-lookup"><span data-stu-id="36e5f-138">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e5f-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36e5f-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="36e5f-140">裝載</span><span class="sxs-lookup"><span data-stu-id="36e5f-140">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
