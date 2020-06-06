---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398024"
---
# \<endpointDiscovery>
<span data-ttu-id="bb3ab-101">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-101">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="bb3ab-102">語法</span><span class="sxs-lookup"><span data-stu-id="bb3ab-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb3ab-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bb3ab-103">Attributes and Elements</span></span>  
 <span data-ttu-id="bb3ab-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb3ab-105">屬性</span><span class="sxs-lookup"><span data-stu-id="bb3ab-105">Attributes</span></span>  
  
|<span data-ttu-id="bb3ab-106">屬性</span><span class="sxs-lookup"><span data-stu-id="bb3ab-106">Attribute</span></span>|<span data-ttu-id="bb3ab-107">描述</span><span class="sxs-lookup"><span data-stu-id="bb3ab-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bb3ab-108">已啟用</span><span class="sxs-lookup"><span data-stu-id="bb3ab-108">enabled</span></span>|<span data-ttu-id="bb3ab-109">布林值，指定是否在這個端點上啟用探索功能。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-109">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="bb3ab-110">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-110">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb3ab-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bb3ab-111">Child Elements</span></span>  
  
|<span data-ttu-id="bb3ab-112">元素</span><span class="sxs-lookup"><span data-stu-id="bb3ab-112">Element</span></span>|<span data-ttu-id="bb3ab-113">描述</span><span class="sxs-lookup"><span data-stu-id="bb3ab-113">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="bb3ab-114">端點之範圍 URI 的集合。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-114">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="bb3ab-115">有一個以上的範圍 URI 與單一端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-115">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="bb3ab-116">[\<extensions>](extensions.md)[/ \<endpointDiscovery> ]</span><span class="sxs-lookup"><span data-stu-id="bb3ab-116">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="bb3ab-117">XML 項目的集合，這個集合可讓您指定端點要發行的自訂中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-117">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|\<types>|<span data-ttu-id="bb3ab-118">要搜尋之介面的集合。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-118">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb3ab-119">父項目</span><span class="sxs-lookup"><span data-stu-id="bb3ab-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bb3ab-120">元素</span><span class="sxs-lookup"><span data-stu-id="bb3ab-120">Element</span></span>|<span data-ttu-id="bb3ab-121">描述</span><span class="sxs-lookup"><span data-stu-id="bb3ab-121">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bb3ab-122">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-122">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="bb3ab-123">備註</span><span class="sxs-lookup"><span data-stu-id="bb3ab-123">Remarks</span></span>  
 <span data-ttu-id="bb3ab-124">加入至端點的行為組態 (且 `enabled` 屬性設為 `true`) 時，這個組態項目會啟用其探索能力。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-124">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="bb3ab-125">此外，您可以使用子專案 [\<scopes>](scopes.md) 來指定自訂範圍 uri，以便在查詢期間用來篩選服務端點，以及 [\<extensions>](extensions.md) 指定應與標準可探索的中繼資料（EPR、ContractTypeName、BindingName、Scope 及 ListenURI）一起發行的自訂中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-125">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="bb3ab-126">這個設定元素相依于 [\<serviceDiscovery>](servicediscovery.md) 提供可搜尋性之服務層級控制項的元素。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-126">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="bb3ab-127">這表示，如果不存在於設定中，則會忽略此元素的設定 [\<serviceDiscovery>](servicediscovery.md) 。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-127">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb3ab-128">範例</span><span class="sxs-lookup"><span data-stu-id="bb3ab-128">Example</span></span>  
 <span data-ttu-id="bb3ab-129">下列組態範例指定用於要針對端點發行的篩選範圍及擴充中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bb3ab-129">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb3ab-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb3ab-130">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
