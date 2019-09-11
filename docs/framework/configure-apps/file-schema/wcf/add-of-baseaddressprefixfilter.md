---
title: <add> 的 <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: dee2cd482efc841b7320ed2114a05000255466f3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850528"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="a6782-102">\<add> of \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="a6782-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="a6782-103">表示指定傳遞篩選準則的 configuration 專案，這會提供在 IIS 中裝載 Windows Communication Foundation （WCF）應用程式時，挑選適當的 Internet Information Services （IIS）系結的機制。</span><span class="sxs-lookup"><span data-stu-id="a6782-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
<span data-ttu-id="a6782-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6782-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a6782-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a6782-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a6782-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="a6782-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="a6782-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<baseAddressPrefixFilters >** ](baseaddressprefixfilters.md)</span><span class="sxs-lookup"><span data-stu-id="a6782-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)</span></span>\
<span data-ttu-id="a6782-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="a6782-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6782-109">語法</span><span class="sxs-lookup"><span data-stu-id="a6782-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6782-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a6782-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a6782-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a6782-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6782-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a6782-112">Attributes</span></span>  
  
|<span data-ttu-id="a6782-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a6782-113">Attribute</span></span>|<span data-ttu-id="a6782-114">描述</span><span class="sxs-lookup"><span data-stu-id="a6782-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6782-115">prefix</span><span class="sxs-lookup"><span data-stu-id="a6782-115">prefix</span></span>|<span data-ttu-id="a6782-116">URI，這個 URI 可用來比對基底位址的一部分。</span><span class="sxs-lookup"><span data-stu-id="a6782-116">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6782-117">子元素</span><span class="sxs-lookup"><span data-stu-id="a6782-117">Child Elements</span></span>  
 <span data-ttu-id="a6782-118">無。</span><span class="sxs-lookup"><span data-stu-id="a6782-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6782-119">父項目</span><span class="sxs-lookup"><span data-stu-id="a6782-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a6782-120">項目</span><span class="sxs-lookup"><span data-stu-id="a6782-120">Element</span></span>|<span data-ttu-id="a6782-121">描述</span><span class="sxs-lookup"><span data-stu-id="a6782-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6782-122">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="a6782-122">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="a6782-123">設定專案的集合，這些專案會指定傳遞篩選準則，在 IIS 中裝載 Windows Communication Foundation （WCF）應用程式時，提供一種機制來挑選適當的 IIS 系結。</span><span class="sxs-lookup"><span data-stu-id="a6782-123">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6782-124">備註</span><span class="sxs-lookup"><span data-stu-id="a6782-124">Remarks</span></span>  
 <span data-ttu-id="a6782-125">前置詞篩選條件為共用裝載提供者提供一種方式，使其可指定服務所要使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="a6782-125">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="a6782-126">它可讓共用主機在同一個網站上裝載多個應用程式，而且同一個配置中可以有不同的基底位址。</span><span class="sxs-lookup"><span data-stu-id="a6782-126">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="a6782-127">IIS 網站是包含虛擬目錄的虛擬應用程式的容器 (Container)。</span><span class="sxs-lookup"><span data-stu-id="a6782-127">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="a6782-128">網站中的應用程式則可以透過一個或多個 IIS 繫結來存取。</span><span class="sxs-lookup"><span data-stu-id="a6782-128">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="a6782-129">IIS 繫結提供繫結通訊協定和繫結這兩項資訊。</span><span class="sxs-lookup"><span data-stu-id="a6782-129">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="a6782-130">繫結通訊協定 (例如 HTTP) 會定義產生通訊的配置，而繫結資訊 (例如 IPAddress、Port、Hostheader) 包含用來存取該網站的資料。</span><span class="sxs-lookup"><span data-stu-id="a6782-130">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="a6782-131">IIS 支援為每個網站指定多個 IIS 繫結，讓每個配置都有多個基底位址。</span><span class="sxs-lookup"><span data-stu-id="a6782-131">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="a6782-132">由於裝載在網站下的 WCF 服務只允許針對每個配置系結至一個基底位址，因此您可以使用前置詞篩選功能來挑選託管服務所需的基底位址。</span><span class="sxs-lookup"><span data-stu-id="a6782-132">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="a6782-133">IIS 提供的傳入基底位址會依據選擇性的前置詞清單篩選條件進行篩選。</span><span class="sxs-lookup"><span data-stu-id="a6782-133">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="a6782-134">例如，您的網站可能包含下列基底位址。</span><span class="sxs-lookup"><span data-stu-id="a6782-134">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="a6782-135">您可以使用下列組態檔在 appdomain 層級指定前置詞篩選條件。</span><span class="sxs-lookup"><span data-stu-id="a6782-135">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="a6782-136">在此範例中，`net.tcp://test1.fabrikam.com:8000` 和 `http://test2.fabrikam.com:9000` 分別是其配置的唯一基底位址，而且已被允許通過篩選。</span><span class="sxs-lookup"><span data-stu-id="a6782-136">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="a6782-137">根據預設，如果沒有指定前置詞，則所有位址都會通過。</span><span class="sxs-lookup"><span data-stu-id="a6782-137">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="a6782-138">如果指定前置詞，則只會允許要通過之配置的相符基底位址。</span><span class="sxs-lookup"><span data-stu-id="a6782-138">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6782-139">篩選條件不支援任何萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a6782-139">The filter does not support any wildcards.</span></span> <span data-ttu-id="a6782-140">此外，IIS 提供的 baseAddress 中，可能會有位址繫結程序至不在 `baseAddressPrefixFilters` 清單中的配置，</span><span class="sxs-lookup"><span data-stu-id="a6782-140">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="a6782-141">而且這些位址尚未經過篩選。</span><span class="sxs-lookup"><span data-stu-id="a6782-141">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6782-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6782-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="a6782-143">裝載</span><span class="sxs-lookup"><span data-stu-id="a6782-143">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
