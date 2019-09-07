---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399447"
---
# <a name="systemservicemodel"></a>\<system.serviceModel>
此設定區段包含所有的 Windows Communication Foundation （WCF） System.servicemodel configuration 元素。  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp; **\<System.servicemodel >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>
  <behaviors>
  </behaviors>
  <bindings>
  </bindings>
  <client>
  </client>
  <comContracts>
  </comContracts>
  <commonBehaviors>
  </commonBehaviors>
  <diagnostics>
  </diagnostics>
  <extensions>
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>
  <serviceHostingEnvironment>
  </serviceHostingEnvironment>
  <services>
  </services>
  <standardEndpoints>
  </standardEndpoints>
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|這個區段會定義兩個名稱為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。  每個集合會定義分別由端點和服務使用的行為項目。 每個行為項目都由其唯一的 `name` 屬性所識別。|  
|[\<bindings>](bindings.md)|這個區段保存標準和自訂繫結的集合。 每一個項目都是由它的唯一 `name` 所識別。 服務會使用 `name` 來連結繫結，以便利用繫結。|  
|[\<client>](client.md)|這個區段包含用戶端用於連接服務之端點的清單。|  
|[\<comContracts>](comcontracts.md)|這個區段會定義為 WCF 與 COM interop 啟用的 COM 合約。|  
|[\<commonBehaviors>](commonbehaviors.md)|這個區段只能定義在 machine.config 檔中。 它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。  每個集合會分別定義機器上所有 WCF 端點和服務所使用的行為專案。  如果在`<commonBehaviors>`和`<behaviors>`區段中都定義了行為，則 [ \<行為 >] 區段中的行為會獲得喜好設定。|  
|[\<diagnostics>](diagnostics.md)|這個區段包含 WCF 之診斷功能的設定。 使用者可以啟用/停用追蹤、效能計數器和 WMI 提供者，並且可以新增自訂訊息篩選條件。|  
|[\<延伸模組 >](extensions-section.md)|這個區段包含延伸的集合，可讓使用者建立使用者定義的繫結程序、行為和其他方面的延伸。|  
|[\<protocolMapping>](protocolmapping.md)|這個區段會定義傳輸通訊協定配置（例如 HTTP、net.tcp、net.pipe 等）和 WCF 系結之間的一組預設通訊協定對應。|  
|[\<routing>](routing.md)|這個區段會定義一組路由篩選準則，以決定在評估傳入訊息時所<xref:System.ServiceModel.Dispatcher.MessageFilter>使用的 Windows Communication Foundation （WCF）類型，以及定義在下列情況下要傳送訊息的目標端點的路由表：篩選符合專案。|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|這個區段會定義服務裝載環境為特定傳輸具現化的型別。 如果這個區段是空白的，便會使用預設的型別。|  
|[\<services>](services.md)|這個區段包含服務的集合。 對於在組件中定義的各個服務，此項目包含指定服務設定的 `service` 項目。|  
|[\<standardEndpoints>](standardendpoints.md)|這個區段會定義標準端點的集合，這些端點是可重複使用的預先設定端點。 標準端點會有一個或多個位址、繫結，以及設為固定值的合約屬性。 例如，探索端點中的合約是固定的。 您也可以使用標準端點，以類似定義自訂繫結的新屬性擴充服務端點。|
|[\<tracking>](tracking-of-wcf.md)|這個區段會定義工作流程服務的追蹤設定。|

### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|\<configuration>|.NET 組態檔中所有組態項目的根項目。|  
  
## <a name="remarks"></a>備註  
 WCF 不會將元素新增至其他產品的設定區段。  
  
 WCF 服務是在設定檔`services`的區段中定義。 組件可包含任何數目的服務。 各服務都有自己的 `service` 組態區段。 這個區段及其內容會定義特定服務的服務合約、行為和端點。  
  
 只有服務的 `name` 屬性才需要用到。  根據預設，服務名稱會說明用來實作服務的基礎 CLR 型別，但您可變更 <xref:System.ServiceModel.ServiceContractAttribute> 上的 ConfigurationName 屬性來覆寫 CLR 型別需求。  
  
 `behaviorConfiguration` 屬性是選擇性的。 它會識別服務使用的服務行為。 此屬性指定的行為必須連結到相同組態檔範圍中 (如同一支檔案或父檔案) 定義的服務行為。  
  
 每個服務會公開一個或多個 `endpoint` 項目中定義的端點。 每個端點都有自己的位址和繫結。 在組態檔中使用的所有繫結都必須定義在檔案的範圍內。  
  
 繫結會透過 `name` 和 `bindingConfiguration` 屬性的組合連結至端點。 `binding` 屬性會定義在哪一個區段定義繫結， `bindingConfiguration` 屬性則會定義使用繫節區段中哪一個已設定的繫結。 繫結區段可定義數個已設定的繫結。  
  
## <a name="example"></a>範例  
 下列是 WCF 組態檔的範例。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <!-- List of Behaviors -->
    </behaviors>
    <client>
      <!-- List of Endpoints -->
    </client>
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
    </diagnostics>
    <serviceHostingEnvironment>
      <!-- List of entries -->
    </serviceHostingEnvironment>
    <comContracts>
      <!-- List of COM+ Contracts -->
    </comContracts>
    <services>
      <!-- List of Services -->
    </services>
    <bindings>
      <!-- List of Bindings -->
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
