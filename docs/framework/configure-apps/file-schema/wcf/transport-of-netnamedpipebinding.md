---
title: "&lt;netNamedPipeBinding&gt; 的 &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;netNamedPipeBinding&gt; 的 &lt;transport&gt;
定義具名管道的傳輸安全性設定。  
  
## 語法  
  
```  
  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|protectionLevel|定義具名管道的保護層級。  簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。  加密會提供傳輸期間的資料層級隱私權。  有效值包括以下的值：<br /><br /> -   None：沒有任何保護。<br />-   Sign：簽署訊息。<br />-   EncryptAndSign：加密和簽署訊息。<br /><br /> 預設值為 EncryptAndSign。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|定義繫結的安全性設定。|  
  
## 請參閱  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>   
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>   
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)