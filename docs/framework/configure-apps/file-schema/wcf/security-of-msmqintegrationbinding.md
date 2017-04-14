---
title: "&lt;msmqIntegrationBinding&gt; 的 &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# &lt;msmqIntegrationBinding&gt; 的 &lt;security&gt;
定義訊息佇列 \(MSMQ\) 整合通道的傳輸安全性設定。  
  
## 語法  
  
```  
  
<msmqIntegrationBinding>  
   <binding>   
       <security mode="None/Transport">  
         <transport msmqAuthenticationMode="None/Windows/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          <message  algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"  
                        clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
            defaultProtectionLevel="None/Sign/EncryptAndSign" />  
       </security>  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|模式|指定控制訊息佇列整合通道之完整性、機密性和驗證的安全性類型。  有效值包括以下的值：<br /><br /> -   None：這會停用安全性。<br />-   Transport：由傳輸提供保護和驗證。  這會套用在兩個佇列管理員之間的訊息安全性。  應用程式和佇列管理員之間沒有提供安全性。  現有 Msmq 應用程式在功能上相當於這個安全性模式類型。<br /><br /> 預設值是 `Transport`。  此屬性的型別為 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|定義訊息佇列整合傳輸的安全性設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|[\<msmqIntegrationBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)的繫結項目。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>   
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>   
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>   
 [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)   
 [\<msmqIntegrationBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)