---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: fe57cb84cfa70b1f6b92abf1dbac89ddad9d4dc8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925703"
---
# <a name="endpointextensions"></a><span data-ttu-id="cf59b-101">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="cf59b-101">\<endpointExtensions></span></span>
<span data-ttu-id="cf59b-102">這個區段會在電腦或應用程式的組態檔的擴充區段中註冊新的標準端點。</span><span class="sxs-lookup"><span data-stu-id="cf59b-102">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="cf59b-103">您可以透過使用 `add` 關鍵字，並將項目的 `type` 屬性設定為端點型別，同時將 `name` 屬性設定為標準端點的名稱，將標準端點加入至這個集合。</span><span class="sxs-lookup"><span data-stu-id="cf59b-103">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="cf59b-104">下列範例使用 `add` 項目及 `name` 屬性，將標準端點加入至組態檔的 `<endpointExtensions>` 區段。</span><span class="sxs-lookup"><span data-stu-id="cf59b-104">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="cf59b-105">註冊標準端點後，您可以如下列範例所示使用該端點。</span><span class="sxs-lookup"><span data-stu-id="cf59b-105">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="cf59b-106">在端點 > 元素中, `kind`屬性會指定已在`<endpointExtensions>`區段中註冊的標準端點類型。 [ \< ](endpoint-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf59b-106">In the [\<endpoint>](endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="cf59b-107">屬性會與`<standardEndpoints>`一節中標準`name`端點之 configuration 元素的屬性相同。 `endpointConfiguration`</span><span class="sxs-lookup"><span data-stu-id="cf59b-107">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
