---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 8fffcd02b1c08172b184225f13a1852414cf429a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltbaseaddressprefixfiltersgt"></a><span data-ttu-id="ea224-102">&lt;baseAddressPrefixFilters&gt;</span><span class="sxs-lookup"><span data-stu-id="ea224-102">&lt;baseAddressPrefixFilters&gt;</span></span>
<span data-ttu-id="ea224-103">表示的組態項目會指定通過篩選條件，提供一個機制，裝載在 IIS 中的 Windows Communication Foundation (WCF) 應用程式時挑選適當的網際網路資訊服務 (IIS) 繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="ea224-103">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ea224-104">\<baseAddressPrefixFilters > 無法辨識"localhost"，請改用完整的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="ea224-104">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="ea224-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ea224-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ea224-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="ea224-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea224-107">語法</span><span class="sxs-lookup"><span data-stu-id="ea224-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea224-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ea224-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ea224-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ea224-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea224-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ea224-110">Attributes</span></span>  
 <span data-ttu-id="ea224-111">無。</span><span class="sxs-lookup"><span data-stu-id="ea224-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ea224-112">子項目</span><span class="sxs-lookup"><span data-stu-id="ea224-112">Child Elements</span></span>  
  
|<span data-ttu-id="ea224-113">項目</span><span class="sxs-lookup"><span data-stu-id="ea224-113">Element</span></span>|<span data-ttu-id="ea224-114">描述</span><span class="sxs-lookup"><span data-stu-id="ea224-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea224-115">\<add></span><span class="sxs-lookup"><span data-stu-id="ea224-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="ea224-116">新增組態項目，這個項目會指定由服務主機使用之基底位址的前置詞篩選條件。</span><span class="sxs-lookup"><span data-stu-id="ea224-116">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea224-117">父項目</span><span class="sxs-lookup"><span data-stu-id="ea224-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ea224-118">項目</span><span class="sxs-lookup"><span data-stu-id="ea224-118">Element</span></span>|<span data-ttu-id="ea224-119">描述</span><span class="sxs-lookup"><span data-stu-id="ea224-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea224-120">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="ea224-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="ea224-121">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="ea224-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea224-122">備註</span><span class="sxs-lookup"><span data-stu-id="ea224-122">Remarks</span></span>  
 <span data-ttu-id="ea224-123">前置詞篩選條件為共用裝載提供者提供一種方式，使其可指定服務所要使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="ea224-123">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="ea224-124">它可讓共用主機在同一個網站上裝載多個應用程式，而且同一個配置中可以有不同的基底位址。</span><span class="sxs-lookup"><span data-stu-id="ea224-124">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="ea224-125">IIS 網站是包含虛擬目錄的虛擬應用程式的容器 (Container)。</span><span class="sxs-lookup"><span data-stu-id="ea224-125">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="ea224-126">網站中的應用程式則可以透過一個或多個 IIS 繫結來存取。</span><span class="sxs-lookup"><span data-stu-id="ea224-126">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="ea224-127">IIS 繫結提供繫結通訊協定和繫結這兩項資訊。</span><span class="sxs-lookup"><span data-stu-id="ea224-127">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="ea224-128">繫結通訊協定 (例如 HTTP) 會定義產生通訊的配置，而繫結資訊 (例如 IPAddress、Port、Hostheader) 包含用來存取該網站的資料。</span><span class="sxs-lookup"><span data-stu-id="ea224-128">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="ea224-129">IIS 支援為每個網站指定多個 IIS 繫結，讓每個配置都有多個基底位址。</span><span class="sxs-lookup"><span data-stu-id="ea224-129">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="ea224-130">由於裝載在網站下的 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務僅允許每個配置繫結至一個基底位址，因此，您可以使用前置詞篩選功能挑選所裝載服務所需的基底位址。</span><span class="sxs-lookup"><span data-stu-id="ea224-130">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="ea224-131">IIS 提供的傳入基底位址會依據選擇性的前置詞清單篩選條件進行篩選。</span><span class="sxs-lookup"><span data-stu-id="ea224-131">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="ea224-132">例如，您的網站可能包含下列基底位址。</span><span class="sxs-lookup"><span data-stu-id="ea224-132">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="ea224-133">您可以使用下列組態檔在 appdomain 層級指定前置詞篩選條件。</span><span class="sxs-lookup"><span data-stu-id="ea224-133">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="ea224-134">在此範例中，`net.tcp://test1.fabrikam.com:8000` 和 `http://test2.fabrikam.com:9000` 分別是其配置的唯一基底位址，而且已被允許通過篩選。</span><span class="sxs-lookup"><span data-stu-id="ea224-134">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="ea224-135">根據預設，如果沒有指定前置詞，則所有位址都會通過。</span><span class="sxs-lookup"><span data-stu-id="ea224-135">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="ea224-136">如果指定前置詞，則只會允許要通過之配置的相符基底位址。</span><span class="sxs-lookup"><span data-stu-id="ea224-136">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea224-137">篩選條件不支援任何萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ea224-137">The filter does not support any wildcards.</span></span> <span data-ttu-id="ea224-138">此外，IIS 提供的 baseAddress 中，可能會有位址繫結至不在 `baseAddressPrefixFilters` 清單中的配置，</span><span class="sxs-lookup"><span data-stu-id="ea224-138">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="ea224-139">而且這些位址尚未經過篩選。</span><span class="sxs-lookup"><span data-stu-id="ea224-139">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea224-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea224-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="ea224-141">裝載</span><span class="sxs-lookup"><span data-stu-id="ea224-141">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
