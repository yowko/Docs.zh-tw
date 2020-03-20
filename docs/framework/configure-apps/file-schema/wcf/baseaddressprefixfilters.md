---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 0673507b72690c3a5c7dcc35442c05e378dba43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153031"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="cdfc2-101">\<基本位址首碼篩選器></span><span class="sxs-lookup"><span data-stu-id="cdfc2-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="cdfc2-102">表示指定傳遞篩選器的配置元素的集合，這些元素提供了在 IIS 中託管 Windows 通信基礎 （WCF） 應用程式時選擇適當 Internet 資訊服務 （IIS） 綁定的機制。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="cdfc2-103">\<基底位址首碼篩選器>無法識別"本地主機";改用完全限定的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-103">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
<span data-ttu-id="cdfc2-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cdfc2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cdfc2-105">&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cdfc2-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cdfc2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務託管環境>**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="cdfc2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="cdfc2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<基本位址首碼篩選器>**</span><span class="sxs-lookup"><span data-stu-id="cdfc2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdfc2-108">語法</span><span class="sxs-lookup"><span data-stu-id="cdfc2-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdfc2-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cdfc2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cdfc2-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdfc2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="cdfc2-111">Attributes</span></span>  
 <span data-ttu-id="cdfc2-112">無。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cdfc2-113">子元素</span><span class="sxs-lookup"><span data-stu-id="cdfc2-113">Child Elements</span></span>  
  
|<span data-ttu-id="cdfc2-114">元素</span><span class="sxs-lookup"><span data-stu-id="cdfc2-114">Element</span></span>|<span data-ttu-id="cdfc2-115">描述</span><span class="sxs-lookup"><span data-stu-id="cdfc2-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdfc2-116">\<添加></span><span class="sxs-lookup"><span data-stu-id="cdfc2-116">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="cdfc2-117">新增組態項目，這個項目會指定由服務主機使用之基底位址的前置詞篩選條件。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-117">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdfc2-118">父項目</span><span class="sxs-lookup"><span data-stu-id="cdfc2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cdfc2-119">元素</span><span class="sxs-lookup"><span data-stu-id="cdfc2-119">Element</span></span>|<span data-ttu-id="cdfc2-120">描述</span><span class="sxs-lookup"><span data-stu-id="cdfc2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdfc2-121">\<服務託管環境></span><span class="sxs-lookup"><span data-stu-id="cdfc2-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="cdfc2-122">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdfc2-123">備註</span><span class="sxs-lookup"><span data-stu-id="cdfc2-123">Remarks</span></span>  
 <span data-ttu-id="cdfc2-124">前置詞篩選條件為共用裝載提供者提供一種方式，使其可指定服務所要使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="cdfc2-125">它可讓共用主機在同一個網站上裝載多個應用程式，而且同一個配置中可以有不同的基底位址。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="cdfc2-126">IIS 網站是包含虛擬目錄的虛擬應用程式的容器 (Container)。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="cdfc2-127">網站中的應用程式則可以透過一個或多個 IIS 繫結來存取。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-127">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="cdfc2-128">IIS 繫結提供繫結通訊協定和繫結這兩項資訊。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="cdfc2-129">繫結通訊協定 (例如 HTTP) 會定義產生通訊的配置，而繫結資訊 (例如 IPAddress、Port、Hostheader) 包含用來存取該網站的資料。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="cdfc2-130">IIS 支援為每個網站指定多個 IIS 繫結，讓每個配置都有多個基底位址。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="cdfc2-131">由於網站下託管的 WCF 服務允許為每個方案僅綁定到一個基本位址，因此可以使用首碼篩選器功能來選擇託管服務所需的基本位址。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="cdfc2-132">IIS 提供的傳入基底位址會依據選擇性的前置詞清單篩選條件進行篩選。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="cdfc2-133">例如，您的網站可以包含以下基本位址：</span><span class="sxs-lookup"><span data-stu-id="cdfc2-133">For example, your site can contain the following base addresses:</span></span>
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="cdfc2-134">您可以使用下列組態檔在 appdomain 層級指定前置詞篩選條件。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="cdfc2-135">在此範例中，`net.tcp://test1.fabrikam.com:8000` 和 `http://test2.fabrikam.com:9000` 分別是其配置的唯一基底位址，而且已被允許通過篩選。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="cdfc2-136">根據預設，如果沒有指定前置詞，則所有位址都會通過。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="cdfc2-137">如果指定前置詞，則只會允許要通過之配置的相符基底位址。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdfc2-138">篩選條件不支援任何萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="cdfc2-139">此外，IIS 提供的 baseAddress 中，可能會有位址繫結程序至不在 `baseAddressPrefixFilters` 清單中的配置，</span><span class="sxs-lookup"><span data-stu-id="cdfc2-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="cdfc2-140">而且這些位址尚未經過篩選。</span><span class="sxs-lookup"><span data-stu-id="cdfc2-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdfc2-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdfc2-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="cdfc2-142">裝載</span><span class="sxs-lookup"><span data-stu-id="cdfc2-142">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
