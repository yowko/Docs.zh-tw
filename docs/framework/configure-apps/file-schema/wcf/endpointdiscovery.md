---
title: '&lt;endpointDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: c5971ce79ac2f03fbdc91653d5d282804e98cf8a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="ba42c-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="ba42c-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="ba42c-103">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ba42c-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="ba42c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ba42c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ba42c-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ba42c-105">\<behaviors></span></span>  
<span data-ttu-id="ba42c-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ba42c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ba42c-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ba42c-107">\<behavior></span></span>  
<span data-ttu-id="ba42c-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="ba42c-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba42c-109">語法</span><span class="sxs-lookup"><span data-stu-id="ba42c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba42c-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ba42c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ba42c-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ba42c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba42c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ba42c-112">Attributes</span></span>  
  
|<span data-ttu-id="ba42c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ba42c-113">Attribute</span></span>|<span data-ttu-id="ba42c-114">描述</span><span class="sxs-lookup"><span data-stu-id="ba42c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba42c-115">enabled</span><span class="sxs-lookup"><span data-stu-id="ba42c-115">enabled</span></span>|<span data-ttu-id="ba42c-116">布林值，這個值指定這個端點是否已啟用探索能力。</span><span class="sxs-lookup"><span data-stu-id="ba42c-116">A Boolean value that that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="ba42c-117">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="ba42c-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba42c-118">子項目</span><span class="sxs-lookup"><span data-stu-id="ba42c-118">Child Elements</span></span>  
  
|<span data-ttu-id="ba42c-119">項目</span><span class="sxs-lookup"><span data-stu-id="ba42c-119">Element</span></span>|<span data-ttu-id="ba42c-120">描述</span><span class="sxs-lookup"><span data-stu-id="ba42c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba42c-121">\<範圍 ></span><span class="sxs-lookup"><span data-stu-id="ba42c-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="ba42c-122">端點之範圍 URI 的集合。</span><span class="sxs-lookup"><span data-stu-id="ba42c-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="ba42c-123">有一個以上的範圍 URI 與單一端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="ba42c-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="ba42c-124">[\<延伸模組 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [的\<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="ba42c-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="ba42c-125">XML 項目的集合，這個集合可讓您指定端點要發行的自訂中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ba42c-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="ba42c-126">\<類型 ></span><span class="sxs-lookup"><span data-stu-id="ba42c-126">\<types></span></span>|<span data-ttu-id="ba42c-127">要搜尋之介面的集合。</span><span class="sxs-lookup"><span data-stu-id="ba42c-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba42c-128">父項目</span><span class="sxs-lookup"><span data-stu-id="ba42c-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ba42c-129">項目</span><span class="sxs-lookup"><span data-stu-id="ba42c-129">Element</span></span>|<span data-ttu-id="ba42c-130">描述</span><span class="sxs-lookup"><span data-stu-id="ba42c-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba42c-131">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ba42c-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ba42c-132">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="ba42c-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="ba42c-133">備註</span><span class="sxs-lookup"><span data-stu-id="ba42c-133">Remarks</span></span>  
 <span data-ttu-id="ba42c-134">加入至端點的行為組態 (且 `enabled` 屬性設為 `true`) 時，這個組態項目會啟用其探索能力。</span><span class="sxs-lookup"><span data-stu-id="ba42c-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="ba42c-135">此外，您可以使用[\<範圍 >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)子項目加入指定的自訂範圍 Uri 可以用於在查詢期間篩選服務端點，以及[\<延伸模組 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md)子元素來指定應該與標準的可探索中繼資料 （EPR、 ContractTypeName、 BindingName、 範圍及 ListenURI） 發行的自訂中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ba42c-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="ba42c-136">這個組態項目是依存於[ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)提供探索能力服務層級控制項的項目。</span><span class="sxs-lookup"><span data-stu-id="ba42c-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="ba42c-137">這表示，如果，則會忽略這個項目設定[ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)不是出現在組態中。</span><span class="sxs-lookup"><span data-stu-id="ba42c-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba42c-138">範例</span><span class="sxs-lookup"><span data-stu-id="ba42c-138">Example</span></span>  
 <span data-ttu-id="ba42c-139">下列組態範例指定用於要針對端點發行的篩選範圍及擴充中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ba42c-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="ba42c-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba42c-140">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
