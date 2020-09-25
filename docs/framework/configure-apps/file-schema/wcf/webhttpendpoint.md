---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 3282871bf8dbd25726ada7003d3066b9a42e2366
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177978"
---
# \<webHttpEndpoint>

這個設定元素會定義具有固定系結的標準端點，此系結 [\<webHttpBinding>](webhttpbinding.md) 會自動加入 [\<webHttp>](webhttp.md) 行為。 撰寫 REST 服務時，請使用這個端點。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|布林值，指出是否啟用自動格式化選取範圍。<br /><br /> 啟用自動格式化選取範圍時，基礎結構會剖析要求訊息的 `Accept` 標頭，並且判斷最適合的回應格式。 如果 `Accept` 標頭未指定適合的回應格式，基礎結構會使用要求訊息的 `Content-Type` 或作業的預設回應格式。|  
|defaultOutgoingResponseFormat|屬性，用來指定預設的傳出回應格式。 此屬性的型別為 <xref:System.ServiceModel.Web.WebMessageFormat>。|  
|helpEnabled|布林值，指出是否啟用端點的 HTTP 說明頁。|  
|webEndpointType|字串，指定端點的型別。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
