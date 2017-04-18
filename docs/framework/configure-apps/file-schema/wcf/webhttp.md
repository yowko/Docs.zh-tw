---
title: "&lt;webHttp&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;webHttp&gt;
此項目透過組態指定端點上的 <xref:System.ServiceModel.Description.WebHttpBehavior>。  這個行為會在與 [\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) 標準繫結搭配使用時，為 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務啟用 Web 程式設計模型。  
  
## 語法  
  
```  
  
<webHttp />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|automaticFormatSelectionEnabled|當此屬性設定為 `true` 時，WCF 基礎結構會判斷要使用的最佳格式。  為了提供回溯相容性，自動格式選取預設為停用。  自動格式選取可以透過程式設計方式或透過組態啟用。|  
|defaultBodyStyle|指定傳回訊息的預設本文樣式。  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.Web.WebMessageBodyStyle>和[WCF Web HTTP 格式化](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。|  
|defaultOutgoingResponseFormat|指定訊息的預設傳出回應格式。  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]如需詳細資訊，請參閱 [WCF Web HTTP 格式化](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。|  
|faultExceptionEnabled|取得或設定旗標，指定內部伺服器錯誤 \(HTTP 狀態碼：500\) 發生時，是否產生 FaultException。|  
|helpEnabled|取得或設定值，這個值會判斷是否已啟用說明頁面。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為組。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.WebHttpElement>   
 <xref:System.ServiceModel.Description.WebHttpBehavior>   
 [AJAX 整合與 JSON 支援](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)   
 [\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)