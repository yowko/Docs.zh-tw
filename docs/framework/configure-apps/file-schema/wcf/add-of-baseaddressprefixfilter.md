---
title: <add> 的 <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: a58a29e44fff3d653d04da271e3b240f2969611f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673734"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="8cbb2-102">\<add> of \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="8cbb2-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="8cbb2-103">表示指定通過篩選條件，提供一個機制，Windows Communication Foundation (WCF) 應用程式裝載在 IIS 時挑選適當的 Internet Information Services (IIS) 繫結的組態項目。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="8cbb2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8cbb2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8cbb2-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="8cbb2-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="8cbb2-106">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="8cbb2-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="8cbb2-107">\<add></span><span class="sxs-lookup"><span data-stu-id="8cbb2-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cbb2-108">語法</span><span class="sxs-lookup"><span data-stu-id="8cbb2-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cbb2-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8cbb2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8cbb2-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cbb2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8cbb2-111">Attributes</span></span>  
  
|<span data-ttu-id="8cbb2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8cbb2-112">Attribute</span></span>|<span data-ttu-id="8cbb2-113">描述</span><span class="sxs-lookup"><span data-stu-id="8cbb2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8cbb2-114">prefix</span><span class="sxs-lookup"><span data-stu-id="8cbb2-114">prefix</span></span>|<span data-ttu-id="8cbb2-115">URI，這個 URI 可用來比對基底位址的一部分。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cbb2-116">子元素</span><span class="sxs-lookup"><span data-stu-id="8cbb2-116">Child Elements</span></span>  
 <span data-ttu-id="8cbb2-117">無。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cbb2-118">父項目</span><span class="sxs-lookup"><span data-stu-id="8cbb2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8cbb2-119">項目</span><span class="sxs-lookup"><span data-stu-id="8cbb2-119">Element</span></span>|<span data-ttu-id="8cbb2-120">描述</span><span class="sxs-lookup"><span data-stu-id="8cbb2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cbb2-121">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="8cbb2-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="8cbb2-122">指定通過篩選條件，提供一個機制來裝載在 IIS 中的 Windows Communication Foundation (WCF) 應用程式時挑選適當 IIS 繫結的組態項目的集合。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cbb2-123">備註</span><span class="sxs-lookup"><span data-stu-id="8cbb2-123">Remarks</span></span>  
 <span data-ttu-id="8cbb2-124">前置詞篩選條件為共用裝載提供者提供一種方式，使其可指定服務所要使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="8cbb2-125">它可讓共用主機在同一個網站上裝載多個應用程式，而且同一個配置中可以有不同的基底位址。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="8cbb2-126">IIS 網站是包含虛擬目錄的虛擬應用程式的容器 (Container)。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="8cbb2-127">網站中的應用程式則可以透過一個或多個 IIS 繫結來存取。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="8cbb2-128">IIS 繫結提供繫結通訊協定和繫結這兩項資訊。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="8cbb2-129">繫結通訊協定 (例如 HTTP) 會定義產生通訊的配置，而繫結資訊 (例如 IPAddress、Port、Hostheader) 包含用來存取該網站的資料。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="8cbb2-130">IIS 支援為每個網站指定多個 IIS 繫結，讓每個配置都有多個基底位址。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="8cbb2-131">因為在網站下裝載的 WCF 服務可讓每個配置的繫結至一個基底位址，您可以使用前置詞篩選功能挑選裝載服務所需的基底位址。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="8cbb2-132">IIS 提供的傳入基底位址會依據選擇性的前置詞清單篩選條件進行篩選。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="8cbb2-133">例如，您的網站可能包含下列基底位址。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="8cbb2-134">您可以使用下列組態檔在 appdomain 層級指定前置詞篩選條件。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="8cbb2-135">在此範例中，`net.tcp://test1.fabrikam.com:8000` 和 `http://test2.fabrikam.com:9000` 分別是其配置的唯一基底位址，而且已被允許通過篩選。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="8cbb2-136">根據預設，如果沒有指定前置詞，則所有位址都會通過。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="8cbb2-137">如果指定前置詞，則只會允許要通過之配置的相符基底位址。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8cbb2-138">篩選條件不支援任何萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="8cbb2-139">此外，IIS 提供的 baseAddress 中，可能會有位址繫結程序至不在 `baseAddressPrefixFilters` 清單中的配置，</span><span class="sxs-lookup"><span data-stu-id="8cbb2-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="8cbb2-140">而且這些位址尚未經過篩選。</span><span class="sxs-lookup"><span data-stu-id="8cbb2-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbb2-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cbb2-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="8cbb2-142">裝載</span><span class="sxs-lookup"><span data-stu-id="8cbb2-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
