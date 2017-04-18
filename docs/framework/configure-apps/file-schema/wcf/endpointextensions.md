---
title: "&lt;endpointExtensions&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;endpointExtensions&gt;
這個區段會在電腦或應用程式的組態檔的擴充區段中註冊新的標準端點。  您可以透過使用 `add` 關鍵字，並將項目的 `type` 屬性設定為端點型別，同時將 `name` 屬性設定為標準端點的名稱，將標準端點加入至這個集合。  
  
 下列範例使用 `add` 項目及 `name` 屬性，將標準端點加入至組態檔的 `<endpointExtensions>` 區段。  
  
```  
<system.serviceModel>  
    <extensions>  
        <endpointExtensions>  
           <add name="udpDiscoveryEndpoint"  
                type="System.Discovery.UdpEndpointCollectionElement, System.Discovery.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
        </endpointExtensions>   
    </extensions>  
</system.serviceModel>  
```  
  
 註冊標準端點後，您可以如下列範例所示使用該端點。  在 [\<endpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) 項目中，`kind` 屬性會指定已在 `<endpointExtensions>` 區段中註冊的標準端點類型。  `endpointConfiguration` 屬性會與 `<standardEndpoints>` 區段中標準端點之組態項目的 `name` 屬性完全相同。  
  
```  
  
<system.serviceModel>  
    <services>  
      <service name="Service1">  
        <endpoint kind="udpDiscoveryEndpoint"  
                  endpointConfiguration="udpConfig" />  
      </service>  
    </services>  
    <standardEndpoints>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
                  name="udpConfig"  
                  multicastAddress="soap.udp://239.255.255.250:3703"  
                  ... />  
      </udpDiscoveryEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
  
```