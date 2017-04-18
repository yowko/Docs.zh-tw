---
title: "&lt;exposedMethod&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;exposedMethod&gt;
表示 COM\+ 方法，這個方法會在 COM\+ 元件上的介面公開為 Web 服務時公開。  
  
## 語法  
  
```  
  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|包含 COM\+ 方法的字串，這個方法會在 COM\+ 元件上的介面公開為 Web 服務時公開。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<exposedMethods\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|[\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) 項目的集合。|  
  
## 備註  
 COM\+ 整合設定工具 \(ComSvcConfig.exe\) 可用來從 COM 介面加入特定的方法，使這些方法可以出現在所產生的服務合約上。  
  
 例如，您可以使用下列命令，從 `ItemOrders`.Financial 元件上的 `IFinances` COM 介面將三個具名方法加入至所產生的服務合約中。  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 當您也執行 ComSvcConfig.exe 時，它會產生下列將上述方法列為 [\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) 項目的服務合約。  
  
```  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 在服務初始化階段，執行階段會藉由反映並只加入包含在 [\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) 項目清單中的方法，嘗試產生服務合約。  這時會針對每個未包含在服務合約中的介面方法加以追蹤。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>   
 <xref:System.ServiceModel.Configuration.ComMethodElement>   
 [\<comContracts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)   
 [整合 COM\+ 應用程式](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)   
 [HOW TO：設定 COM\+ 服務設定](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)