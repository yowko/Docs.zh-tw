---
title: '&lt;endpointExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 6c80b9edb2da9368c0f53be7068d638b045ac19c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752347"
---
# <a name="ltendpointextensionsgt"></a>&lt;endpointExtensions&gt;
這個區段會在電腦或應用程式的組態檔的擴充區段中註冊新的標準端點。 您可以透過使用 `add` 關鍵字，並將項目的 `type` 屬性設定為端點型別，同時將 `name` 屬性設定為標準端點的名稱，將標準端點加入至這個集合。  
  
 下列範例使用 `add` 項目及 `name` 屬性，將標準端點加入至組態檔的 `<endpointExtensions>` 區段。  
  
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
  
 註冊標準端點後，您可以如下列範例所示使用該端點。 在[\<端點 >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目，`kind`屬性會指定已經在中註冊標準端點類型`<endpointExtensions>`> 一節。 `endpointConfiguration`屬性將會等於`name`屬性中的標準端點之組態項目的`<standardEndpoints>`> 一節。  
  
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
