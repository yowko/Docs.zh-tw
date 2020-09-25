---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 621c742e3bb06ce91fa5a6b8951351295f73df9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185804"
---
# \<endpointDiscovery>

指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|已啟用|布林值，指定是否在此端點上啟用可探索性。 預設值為 `false`。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|端點之範圍 URI 的集合。 有一個以上的範圍 URI 與單一端點產生關聯。|  
|[\<extensions>](extensions.md) [/ \<endpointDiscovery> ]|XML 項目的集合，這個集合可讓您指定端點要發行的自訂中繼資料。|  
|\<types>|要搜尋之介面的集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定行為項目。|  
|||  
  
## <a name="remarks"></a>備註  

 加入至端點的行為組態 (且 `enabled` 屬性設為 `true`) 時，這個組態項目會啟用其探索能力。 此外，您可以使用子專案 [\<scopes>](scopes.md) 來指定自訂範圍 uri，這些 uri 可用於在查詢期間篩選服務端點，也可以使用 [\<extensions>](extensions.md) 子專案來指定自訂的中繼資料，該中繼資料應隨標準可探索中繼資料一起發行 (EPR、ContractTypeName、BindingName、Scope 和 ListenURI) 。  
  
 這個設定元素相依于 [\<serviceDiscovery>](servicediscovery.md) 提供可搜尋性之服務層級控制的元素。 這表示如果設定中沒有，則會忽略此元素的設定 [\<serviceDiscovery>](servicediscovery.md) 。  
  
## <a name="example"></a>範例  

 下列組態範例指定用於要針對端點發行的篩選範圍及擴充中繼資料。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
