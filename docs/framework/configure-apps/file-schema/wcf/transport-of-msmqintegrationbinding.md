---
title: "&lt;msmqIntegrationBinding&gt; 的 &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# &lt;msmqIntegrationBinding&gt; 的 &lt;transport&gt;
定義訊息佇列整合傳輸的安全性設定。  
  
## 語法  
  
```  
  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`msmqAuthenticationMode`|指定 MSMQ 傳輸必須如何驗證訊息。  如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。<br /><br /> 有效值包括以下的值：<br /><br /> -   None：無驗證。<br />-   WindowsDomain：驗證機制使用 Active Directory 為與訊息相關聯的 SID 取得 X.509 憑證。  接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。<br />-   Certificate：通道會從憑證存放區取得憑證。<br /><br /> 預設值為 WindowsDomain。  此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。|  
|`msmqEncryptionAlgorithm`|指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。  有效值包括以下的值：<br /><br /> -   RC4Stream<br />-   AES<br /><br /> 預設值為 RC4Stream。  此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。|  
|`msmqProtectionLevel`|指定在 MSMQ 傳輸層級上保護訊息的方式。  加密可確保訊息完整性，而 EncryptAndSign 可確保訊息完整性和不可否認性，也就是訊息確實來自寄件者，且寄件者就是他本人。<br /><br /> -   有效值包括以下的值：<br />-   None：沒有任何保護。<br />-   Sign：簽署訊息。<br />-   EncryptAndSign：加密和簽署訊息。<br /><br /> 預設值為 Sign。  此屬性的型別為 ProtectionLevel。|  
|`msmqSecureHashAlgorithm`|-   指定計算摘要做為部分簽章時使用的演算法。  有效值包括以下的值：<br />-   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> 預設值為 SHA1。  此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|定義 MSMQ 繫結的安全性設定。|  
  
## 備註  
 這個項目會封裝訊息佇列整合傳輸的安全性設定。  這些設定同時適用於訊息佇列整合和已佇列之傳輸。  它還可讓您設定驗證模式、加密演算法、安全雜湊演算法和保護層級。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>   
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>   
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.MsmqTransportSecurity>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)