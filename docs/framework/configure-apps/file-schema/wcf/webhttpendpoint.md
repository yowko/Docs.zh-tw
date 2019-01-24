---
title: '&lt;webHttpEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: b69ace451e90c824cdf8b911d596fdd158eb3f73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491715"
---
# <a name="ltwebhttpendpointgt"></a>&lt;webHttpEndpoint&gt;
此組態元素定義具有固定的標準端點[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)繫結，會自動加入[ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)行為。 撰寫 REST 服務時，請使用這個端點。  
  
\<system.ServiceModel>  
\<standardEndpoints>  
  
## <a name="syntax"></a>語法  
  
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
 下列各節描述屬性、子項目和父項目。  
  
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
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
