---
title: '&lt;endpointExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 6c80b9edb2da9368c0f53be7068d638b045ac19c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltendpointextensionsgt"></a><span data-ttu-id="c5e56-102">&lt;endpointExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="c5e56-102">&lt;endpointExtensions&gt;</span></span>
<span data-ttu-id="c5e56-103">這個區段會在電腦或應用程式的組態檔的擴充區段中註冊新的標準端點。</span><span class="sxs-lookup"><span data-stu-id="c5e56-103">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="c5e56-104">您可以透過使用 `add` 關鍵字，並將項目的 `type` 屬性設定為端點型別，同時將 `name` 屬性設定為標準端點的名稱，將標準端點加入至這個集合。</span><span class="sxs-lookup"><span data-stu-id="c5e56-104">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="c5e56-105">下列範例使用 `add` 項目及 `name` 屬性，將標準端點加入至組態檔的 `<endpointExtensions>` 區段。</span><span class="sxs-lookup"><span data-stu-id="c5e56-105">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c5e56-106">註冊標準端點後，您可以如下列範例所示使用該端點。</span><span class="sxs-lookup"><span data-stu-id="c5e56-106">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="c5e56-107">在[\<端點 >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目，`kind`屬性會指定已經在中註冊標準端點類型`<endpointExtensions>`> 一節。</span><span class="sxs-lookup"><span data-stu-id="c5e56-107">In the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="c5e56-108">`endpointConfiguration`屬性將會等於`name`屬性中的標準端點之組態項目的`<standardEndpoints>`> 一節。</span><span class="sxs-lookup"><span data-stu-id="c5e56-108">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
        <standardEndpoint  
                  name="udpConfig"  
                  multicastAddress="soap.udp://239.255.255.250:3703"  
                  ... />  
      </udpDiscoveryEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```
