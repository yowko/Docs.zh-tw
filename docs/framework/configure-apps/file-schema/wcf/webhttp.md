---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 716d960e2d5f896976c22a60d419d9b165b36178
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202457"
---
# \<webHttp>

此項目透過組態指定端點上的 <xref:System.ServiceModel.Description.WebHttpBehavior>。 這種行為與標準系結搭配使用時 [\<webHttpBinding>](webhttpbinding.md) ，會啟用 Windows Communication Foundation (WCF) 服務的 Web 程式設計模型。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|當此屬性設定為 `true` 時，WCF 基礎結構會判斷要使用的最佳格式。 為了提供回溯相容性，自動格式選取預設為停用。 自動格式選取可以透過程式設計方式或透過組態啟用。|  
|defaultBodyStyle|指定傳回訊息的預設本文樣式。 如需詳細資訊，請參閱 <xref:System.ServiceModel.Web.WebMessageBodyStyle> 和 [WCF Web HTTP 格式](../../../wcf/feature-details/wcf-web-http-formatting.md)。|  
|defaultOutgoingResponseFormat|指定訊息的預設傳出回應格式。 如需詳細資訊，請參閱 [WCF WEB HTTP 格式](../../../wcf/feature-details/wcf-web-http-formatting.md)。|  
|faultExceptionEnabled|取得或設定旗標，指定內部伺服器錯誤 (HTTP 狀態碼：500) 發生時，是否產生 FaultException。|  
|helpEnabled|取得或設定值，這個值會判斷是否已啟用說明頁面。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定端點行為組。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [AJAX 整合與 JSON 支援](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
