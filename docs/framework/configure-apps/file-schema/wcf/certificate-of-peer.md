---
title: "&lt;peer&gt; 的 &lt;certificate&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;peer&gt; 的 &lt;certificate&gt;
指定對等所使用的憑證。  
  
## 語法  
  
```  
  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`findValue`|字串，其中包含要在 X.509 憑證存放區內搜尋的值。  屬性所包含的型別必須滿足指定之 `x509FindType` 的需求。  預設為空字串。|  
|`storeLocation`|指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區針對這個位置驗證對等的憑證。  有效值包括以下的值：<br /><br /> -   LocalMachine：指派給本機電腦的憑證存放區。<br />-   CurrentUser：指派給目前使用者的憑證存放區。<br /><br /> 預設為 LocalMachine。|  
|`storeName`|指定要開啟之 X.509 憑證存放區的名稱。  有效值包括以下的值：<br /><br /> -   AddressBook：其他使用者的憑證存放區。<br />-   AuthRoot：協力廠商憑證授權單位 \(CA\) 的憑證存放區。<br />-   CertificateAuthority：中繼憑證授權單位 \(CA\) 的憑證存放區。<br />-   Disallowed：已撤銷之憑證的憑證存放區。<br />-   My：個人憑證的憑證存放區。<br />-   Root：信任之根憑證授權單位 \(CA\) 的憑證存放區。<br />-   TrustedPeople：直接信任之人員和資源的憑證存放區。<br />-   TrustedPublisher：直接信任之發行者的憑證存放區。<br /><br /> 預設為 My。|  
|`X509FindType`|定義要執行之 X.509 搜尋的類型。  有效值包括以下的值：<br /><br /> -   FindByThumbPrint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 屬性所包含的型別必須滿足指定之 `X509FindType` 的需求。<br /><br /> 預設值為 FindBySubjectDistinguishedName。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|指定對等節點的目前認證。|  
  
## 備註  
 這個組態項目包含在驗證對等網狀結構中鄰接項目時所使用的 `X509Certificate2` 執行個體。  
  
 如需對等程式設計的詳細資訊，請參閱[對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>   
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>   
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>   
 <xref:System.ServiceModel.Security.PeerCredential>   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/zh-tw/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/zh-tw/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [確保對等通道應用程式安全](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)