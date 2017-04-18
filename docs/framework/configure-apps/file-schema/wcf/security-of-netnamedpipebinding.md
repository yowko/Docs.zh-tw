---
title: "&lt;netNamedPipeBinding&gt; 的 &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# &lt;netNamedPipeBinding&gt; 的 &lt;security&gt;
定義繫結的安全性設定。  
  
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
|模式|指定套用至這個繫結的安全性類型。  有效值包括以下的值：<br /><br /> -   None：這會停用安全性。<br />-   Transport：使用基礎傳輸型安裝性提供安全性。  可使用這個模式控制保護層級。<br />-   預設值為 Transport。  此屬性的型別為 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|transport|定義傳輸的安全性設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|繫結|[\<netNamedPipeBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)的繫結項目。|  
  
## 請參閱  
 <xref:System.ServiceModel.NetNamedPipeSecurity>   
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [選取認證類型](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)