---
title: "&lt;endpointDiscovery&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;endpointDiscovery&gt;
指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。  
  
## 語法  
  
```  
  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="String">  
      <endpointDiscovery enabled="Boolean">  
        <scopes>  
          <add scope="URI"/>  
        </scopes>  
        <extensions>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|enabled|布林值，這個值指定這個端點是否已啟用探索能力。  預設為 `false`。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<scopes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|端點之範圍 URI 的集合。  有一個以上的範圍 URI 與單一端點產生關聯。|  
|[\<擴充功能\>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) \[的 \<endpointDiscovery\>\]|XML 項目的集合，這個集合可讓您指定端點要發行的自訂中繼資料。|  
|\<類型\>|要搜尋之介面的集合。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定行為項目。|  
|||  
  
## 備註  
 加入至端點的行為組態 \(且 `enabled` 屬性設為 `true`\) 時，這個組態項目會啟用其探索能力。  此外，除了使用 [\<scopes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)[\<擴充功能\>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) 子項目指定應與標準可探索的中繼資料 \(EPR、ContractTypeName、BindingName、Scope 及 ListenURI\) 一起發行的自訂中繼資料。  
  
 這個組態項目相依於提供服務層級探索能力控制項的 [\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) 項目。  也就是說，如果 [\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) 不存在於組態中，則會忽略這個項目的設定。  
  
## 範例  
 下列組態範例指定用於要針對端點發行的篩選範圍及擴充中繼資料。  
  
```  
  
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
  
## 請參閱  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>