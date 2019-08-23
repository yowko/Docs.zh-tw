---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 366def5d0f4cc82b0ff0a5127701b0b5a6adb6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940496"
---
# <a name="webhttp"></a>\<webHttp>
此項目透過組態指定端點上的 <xref:System.ServiceModel.Description.WebHttpBehavior>。 這個行為與[ \<webHttpBinding >](webhttpbinding.md)標準系結搭配使用時, 會啟用 Windows Communication Foundation (WCF) 服務的 Web 程式設計模型。  
  
 \<system.ServiceModel>  
\<行為 >  
\<endpointBehaviors>  
\<行為 >  
\<webHttp>  
  
## <a name="syntax"></a>語法  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|當此屬性設定為 `true` 時，WCF 基礎結構會判斷要使用的最佳格式。 為了提供回溯相容性，自動格式選取預設為停用。 自動格式選取可以透過程式設計方式或透過組態啟用。|  
|defaultBodyStyle|指定傳回訊息的預設本文樣式。 如需詳細資訊, <xref:System.ServiceModel.Web.WebMessageBodyStyle>請參閱和[WCF Web HTTP 格式](../../../wcf/feature-details/wcf-web-http-formatting.md)。|  
|defaultOutgoingResponseFormat|指定訊息的預設傳出回應格式。 如需詳細資訊, 請參閱[WCF WEB HTTP 格式](../../../wcf/feature-details/wcf-web-http-formatting.md)。|  
|faultExceptionEnabled|取得或設定旗標，指定是否要在內部伺服器錯誤 (HTTP 狀態碼：500) 發生時產生 FaultException。|  
|helpEnabled|取得或設定值，這個值會判斷是否已啟用說明頁面。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定端點行為組。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [AJAX 整合與 JSON 支援](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
