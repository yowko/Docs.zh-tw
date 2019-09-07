---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398024"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="649d3-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="649d3-101">\<endpointDiscovery></span></span>
<span data-ttu-id="649d3-102">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="649d3-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="649d3-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="649d3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="649d3-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="649d3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="649d3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="649d3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="649d3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="649d3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="649d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="649d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="649d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endpointDiscovery >**</span><span class="sxs-lookup"><span data-stu-id="649d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="649d3-109">語法</span><span class="sxs-lookup"><span data-stu-id="649d3-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="649d3-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="649d3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="649d3-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="649d3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="649d3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="649d3-112">Attributes</span></span>  
  
|<span data-ttu-id="649d3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="649d3-113">Attribute</span></span>|<span data-ttu-id="649d3-114">描述</span><span class="sxs-lookup"><span data-stu-id="649d3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="649d3-115">enabled</span><span class="sxs-lookup"><span data-stu-id="649d3-115">enabled</span></span>|<span data-ttu-id="649d3-116">布林值，指定是否在這個端點上啟用探索功能。</span><span class="sxs-lookup"><span data-stu-id="649d3-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="649d3-117">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="649d3-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="649d3-118">子元素</span><span class="sxs-lookup"><span data-stu-id="649d3-118">Child Elements</span></span>  
  
|<span data-ttu-id="649d3-119">項目</span><span class="sxs-lookup"><span data-stu-id="649d3-119">Element</span></span>|<span data-ttu-id="649d3-120">描述</span><span class="sxs-lookup"><span data-stu-id="649d3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="649d3-121">\<scopes></span><span class="sxs-lookup"><span data-stu-id="649d3-121">\<scopes></span></span>](scopes.md)|<span data-ttu-id="649d3-122">端點之範圍 URI 的集合。</span><span class="sxs-lookup"><span data-stu-id="649d3-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="649d3-123">有一個以上的範圍 URI 與單一端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="649d3-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="649d3-124">延伸模組 > [of endpointDiscovery>]\< [ \< ](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="649d3-124">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="649d3-125">XML 項目的集合，這個集合可讓您指定端點要發行的自訂中繼資料。</span><span class="sxs-lookup"><span data-stu-id="649d3-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="649d3-126">\<types></span><span class="sxs-lookup"><span data-stu-id="649d3-126">\<types></span></span>|<span data-ttu-id="649d3-127">要搜尋之介面的集合。</span><span class="sxs-lookup"><span data-stu-id="649d3-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="649d3-128">父項目</span><span class="sxs-lookup"><span data-stu-id="649d3-128">Parent Elements</span></span>  
  
|<span data-ttu-id="649d3-129">項目</span><span class="sxs-lookup"><span data-stu-id="649d3-129">Element</span></span>|<span data-ttu-id="649d3-130">說明</span><span class="sxs-lookup"><span data-stu-id="649d3-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="649d3-131">\<behavior></span><span class="sxs-lookup"><span data-stu-id="649d3-131">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="649d3-132">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="649d3-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="649d3-133">備註</span><span class="sxs-lookup"><span data-stu-id="649d3-133">Remarks</span></span>  
 <span data-ttu-id="649d3-134">加入至端點的行為組態 (且 `enabled` 屬性設為 `true`) 時，這個組態項目會啟用其探索能力。</span><span class="sxs-lookup"><span data-stu-id="649d3-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="649d3-135">此外，您可以使用 [ [ \<範圍] >](scopes.md)子項目來指定自訂範圍 uri，以便在查詢期間用來篩選服務端點，以及 > 子項目的[ \<擴充](extensions.md)功能來指定自訂應該與標準可探索的中繼資料（EPR、ContractTypeName、BindingName、Scope 及 ListenURI）一起發行的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="649d3-135">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="649d3-136">此設定元素相依[ \<](servicediscovery.md)于提供可搜尋性之服務等級控制項的 serviceDiscovery > 元素。</span><span class="sxs-lookup"><span data-stu-id="649d3-136">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="649d3-137">這表示如果[ \<serviceDiscovery >](servicediscovery.md)不存在於設定中，就會忽略此元素的設定。</span><span class="sxs-lookup"><span data-stu-id="649d3-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="649d3-138">範例</span><span class="sxs-lookup"><span data-stu-id="649d3-138">Example</span></span>  
 <span data-ttu-id="649d3-139">下列組態範例指定用於要針對端點發行的篩選範圍及擴充中繼資料。</span><span class="sxs-lookup"><span data-stu-id="649d3-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="649d3-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="649d3-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
