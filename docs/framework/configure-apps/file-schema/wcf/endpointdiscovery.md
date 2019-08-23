---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 5cb64c54067ba695f67d86c0026db77ebbe7d5ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919055"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="4cdf6-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="4cdf6-101">\<endpointDiscovery></span></span>
<span data-ttu-id="4cdf6-102">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="4cdf6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4cdf6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4cdf6-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4cdf6-104">\<behaviors></span></span>  
<span data-ttu-id="4cdf6-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4cdf6-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="4cdf6-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4cdf6-106">\<behavior></span></span>  
<span data-ttu-id="4cdf6-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="4cdf6-107">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cdf6-108">語法</span><span class="sxs-lookup"><span data-stu-id="4cdf6-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cdf6-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4cdf6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4cdf6-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cdf6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4cdf6-111">Attributes</span></span>  
  
|<span data-ttu-id="4cdf6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4cdf6-112">Attribute</span></span>|<span data-ttu-id="4cdf6-113">描述</span><span class="sxs-lookup"><span data-stu-id="4cdf6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4cdf6-114">enabled</span><span class="sxs-lookup"><span data-stu-id="4cdf6-114">enabled</span></span>|<span data-ttu-id="4cdf6-115">布林值, 指定是否在這個端點上啟用探索功能。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-115">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="4cdf6-116">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-116">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cdf6-117">子元素</span><span class="sxs-lookup"><span data-stu-id="4cdf6-117">Child Elements</span></span>  
  
|<span data-ttu-id="4cdf6-118">項目</span><span class="sxs-lookup"><span data-stu-id="4cdf6-118">Element</span></span>|<span data-ttu-id="4cdf6-119">描述</span><span class="sxs-lookup"><span data-stu-id="4cdf6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4cdf6-120">\<scopes></span><span class="sxs-lookup"><span data-stu-id="4cdf6-120">\<scopes></span></span>](scopes.md)|<span data-ttu-id="4cdf6-121">端點之範圍 URI 的集合。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-121">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="4cdf6-122">有一個以上的範圍 URI 與單一端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-122">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="4cdf6-123">延伸模組 > [of endpointDiscovery>]\< [ \< ](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="4cdf6-123">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="4cdf6-124">XML 項目的集合，這個集合可讓您指定端點要發行的自訂中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-124">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="4cdf6-125">\<types></span><span class="sxs-lookup"><span data-stu-id="4cdf6-125">\<types></span></span>|<span data-ttu-id="4cdf6-126">要搜尋之介面的集合。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-126">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4cdf6-127">父項目</span><span class="sxs-lookup"><span data-stu-id="4cdf6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4cdf6-128">項目</span><span class="sxs-lookup"><span data-stu-id="4cdf6-128">Element</span></span>|<span data-ttu-id="4cdf6-129">描述</span><span class="sxs-lookup"><span data-stu-id="4cdf6-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4cdf6-130">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4cdf6-130">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="4cdf6-131">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-131">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="4cdf6-132">備註</span><span class="sxs-lookup"><span data-stu-id="4cdf6-132">Remarks</span></span>  
 <span data-ttu-id="4cdf6-133">加入至端點的行為組態 (且 `enabled` 屬性設為 `true`) 時，這個組態項目會啟用其探索能力。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-133">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="4cdf6-134">此外, 您可以使用 [ [ \<範圍] >](scopes.md)子項目來指定自訂範圍 uri, 以便在查詢期間用來篩選服務端點, 以及 > 子項目的[ \<擴充](extensions.md)功能來指定自訂應該與標準可探索的中繼資料 (EPR、ContractTypeName、BindingName、Scope 及 ListenURI) 一起發行的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-134">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="4cdf6-135">此設定元素相依[ \<](servicediscovery.md)于提供可搜尋性之服務等級控制項的 serviceDiscovery > 元素。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-135">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="4cdf6-136">這表示如果[ \<serviceDiscovery >](servicediscovery.md)不存在於設定中, 就會忽略此元素的設定。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-136">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cdf6-137">範例</span><span class="sxs-lookup"><span data-stu-id="4cdf6-137">Example</span></span>  
 <span data-ttu-id="4cdf6-138">下列組態範例指定用於要針對端點發行的篩選範圍及擴充中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4cdf6-138">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="4cdf6-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cdf6-139">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
