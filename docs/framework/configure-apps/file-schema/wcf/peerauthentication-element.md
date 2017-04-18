---
title: "&lt;peerAuthentication&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;peerAuthentication&gt; 項目
指定對等用戶端的驗證選項。  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]對等程式設計的詳細資訊，請參閱[對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。  
  
## 語法  
  
```  
  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`customCertificateValidatorType`|選擇性字串。  用來驗證自訂型別的型別和組件。  當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。|  
|`certifcateValidationMode`|選擇性列舉。  指定用來驗證認證之三個模式的其中一個。  如果設定為 `Custom`，也必須提供 `customCertificateValidator`。  預設為 `ChainTrust`。|  
|`revocationMode`|選擇性列舉。  用於檢查撤銷憑證清單 \(CRL\) 的模式之一。  預設為 `Online`。|  
|`trustedStoreLocation`|選擇性列舉。  兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。  當與用戶端交涉服務憑證時，會使用這個值。  會針對指定之存放位置內的 \[**受信任的人**\] 存放區來執行驗證。  預設為 `CurrentUser`。|  
  
## customCertificateValidatorType 屬性  
  
|值|描述|  
|-------|--------|  
|String|指定型別名稱和組件以及用來尋找此型別的其他資料。  至少需要命名空間和型別名稱。  選擇性的資訊包括：組件名稱、版本號碼、文化特性和公開金鑰權杖。|  
  
## certificateValidationMode 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|下列其中一個值：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom`。  預設為 `ChainTrust`。<br /><br /> 如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。|  
  
## revocationMode 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|下列其中一個值：`NoCheck`、`Online`、`Offline`。  預設為 `Online`。<br /><br /> 如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。|  
  
## trustedStoreLocation 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|下列其中一個值：`LocalMachine` 或 `CurrentUser`。  預設為 `CurrentUser`。  如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。  如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|指定向對等服務驗證用戶端時所使用的認證。|  
  
## 備註  
 `<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> 類別。  這個項目會指定驗證程式，當網狀結構中進行鄰居對鄰居驗證時，就會叫用此驗證程式。  當新對等嘗試建立鄰居連線時，它會將自己的認證傳遞至對應的對等。  會叫用回應程式的驗證器來驗證遠端方的認證。  每次在網狀結構中建立對等連線時，對等的兩方會互相驗證，亦即會叫用兩端的驗證程式。  
  
## 範例  
 下列程式碼會將憑證驗證模式設定為 `PeerOrChainTrust`。  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>   
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>   
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/zh-tw/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/zh-tw/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [確保對等通道應用程式安全](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)