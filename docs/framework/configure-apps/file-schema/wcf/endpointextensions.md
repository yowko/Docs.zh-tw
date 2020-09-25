---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: d0587ae942d1b0c7eb72bee830ca3ced76e4270c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190029"
---
# \<endpointExtensions>

<span data-ttu-id="af86f-101">這個區段會在電腦或應用程式的組態檔的擴充區段中註冊新的標準端點。</span><span class="sxs-lookup"><span data-stu-id="af86f-101">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="af86f-102">您可以透過使用 `add` 關鍵字，並將項目的 `type` 屬性設定為端點型別，同時將 `name` 屬性設定為標準端點的名稱，將標準端點加入至這個集合。</span><span class="sxs-lookup"><span data-stu-id="af86f-102">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="af86f-103">下列範例使用 `add` 項目及 `name` 屬性，將標準端點加入至組態檔的 `<endpointExtensions>` 區段。</span><span class="sxs-lookup"><span data-stu-id="af86f-103">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <endpointExtensions>
      <add name="udpDiscoveryEndpoint"
           type="System.Discovery.UdpEndpointCollectionElement, System.Discovery.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="af86f-104">註冊標準端點後，您可以如下列範例所示使用該端點。</span><span class="sxs-lookup"><span data-stu-id="af86f-104">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="af86f-105">在 [\<endpoint>](endpoint-element.md) 元素中， `kind` 屬性會指定已在區段中註冊的標準端點類型 `<endpointExtensions>` 。</span><span class="sxs-lookup"><span data-stu-id="af86f-105">In the [\<endpoint>](endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="af86f-106">`endpointConfiguration`屬性將與 `name` 區段中標準端點的 configuration 元素屬性相同 `<standardEndpoints>` 。</span><span class="sxs-lookup"><span data-stu-id="af86f-106">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Service1">
      <endpoint kind="udpDiscoveryEndpoint"
                endpointConfiguration="udpConfig" />
    </service>
  </services>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="udpConfig"
                        multicastAddress="soap.udp://239.255.255.250:3703"
                        ... />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
