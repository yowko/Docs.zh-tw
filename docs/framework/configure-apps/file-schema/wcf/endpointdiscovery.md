---
title: '&lt;endpointDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6cca48cec486cfdbb9bca2eba48847c25c35abe9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="c6760-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="c6760-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="c6760-103">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="c6760-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="c6760-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c6760-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c6760-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c6760-105">\<behaviors></span></span>  
<span data-ttu-id="c6760-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c6760-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="c6760-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c6760-107">\<behavior></span></span>  
<span data-ttu-id="c6760-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="c6760-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6760-109">語法</span><span class="sxs-lookup"><span data-stu-id="c6760-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6760-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c6760-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c6760-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c6760-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6760-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c6760-112">Attributes</span></span>  
  
|<span data-ttu-id="c6760-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c6760-113">Attribute</span></span>|<span data-ttu-id="c6760-114">描述</span><span class="sxs-lookup"><span data-stu-id="c6760-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6760-115">enabled</span><span class="sxs-lookup"><span data-stu-id="c6760-115">enabled</span></span>|<span data-ttu-id="c6760-116">布林值，這個值指定這個端點是否已啟用探索能力。</span><span class="sxs-lookup"><span data-stu-id="c6760-116">A Boolean value that that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="c6760-117">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c6760-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6760-118">子元素</span><span class="sxs-lookup"><span data-stu-id="c6760-118">Child Elements</span></span>  
  
|<span data-ttu-id="c6760-119">項目</span><span class="sxs-lookup"><span data-stu-id="c6760-119">Element</span></span>|<span data-ttu-id="c6760-120">說明</span><span class="sxs-lookup"><span data-stu-id="c6760-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6760-121">\<範圍 ></span><span class="sxs-lookup"><span data-stu-id="c6760-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="c6760-122">端點之範圍 URI 的集合。</span><span class="sxs-lookup"><span data-stu-id="c6760-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="c6760-123">有一個以上的範圍 URI 與單一端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c6760-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="c6760-124">[\<延伸模組 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [的\<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="c6760-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="c6760-125">XML 項目的集合，這個集合可讓您指定端點要發行的自訂中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c6760-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="c6760-126">\<類型 ></span><span class="sxs-lookup"><span data-stu-id="c6760-126">\<types></span></span>|<span data-ttu-id="c6760-127">要搜尋之介面的集合。</span><span class="sxs-lookup"><span data-stu-id="c6760-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6760-128">父項目</span><span class="sxs-lookup"><span data-stu-id="c6760-128">Parent Elements</span></span>  
  
|<span data-ttu-id="c6760-129">項目</span><span class="sxs-lookup"><span data-stu-id="c6760-129">Element</span></span>|<span data-ttu-id="c6760-130">說明</span><span class="sxs-lookup"><span data-stu-id="c6760-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6760-131">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c6760-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c6760-132">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="c6760-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="c6760-133">備註</span><span class="sxs-lookup"><span data-stu-id="c6760-133">Remarks</span></span>  
 <span data-ttu-id="c6760-134">加入至端點的行為組態 (且 `enabled` 屬性設為 `true`) 時，這個組態項目會啟用其探索能力。</span><span class="sxs-lookup"><span data-stu-id="c6760-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="c6760-135">此外，您可以使用[\<範圍 >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)子項目加入指定的自訂範圍 Uri 可以用於在查詢期間篩選服務端點，以及[\<延伸模組 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md)子元素來指定應該與標準的可探索中繼資料 （EPR、 ContractTypeName、 BindingName、 範圍及 ListenURI） 發行的自訂中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c6760-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="c6760-136">這個組態項目是依存於[ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)提供探索能力服務層級控制項的項目。</span><span class="sxs-lookup"><span data-stu-id="c6760-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="c6760-137">這表示，如果，則會忽略這個項目設定[ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)不是出現在組態中。</span><span class="sxs-lookup"><span data-stu-id="c6760-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6760-138">範例</span><span class="sxs-lookup"><span data-stu-id="c6760-138">Example</span></span>  
 <span data-ttu-id="c6760-139">下列組態範例指定用於要針對端點發行的篩選範圍及擴充中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c6760-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6760-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6760-140">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
