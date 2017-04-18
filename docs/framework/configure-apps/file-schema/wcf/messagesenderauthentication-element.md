---
title: "&lt;messageSenderAuthentication&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;messageSenderAuthentication&gt; 項目
指定對等訊息寄件者的驗證選項。  
  
 如需對等程式設計的詳細資訊，請參閱[對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。  
  
## 語法  
  
```  
  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
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
|customCertificateValidatorType|用來驗證自訂型別的型別和組件。  當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。|  
|certifcateValidationMode|指定用來驗證認證之三個模式的其中一個。  如果設定為 `Custom`，也必須提供 `customCertificateValidator`。|  
|revocationMode|用於檢查撤銷憑證清單 \(CRL\) 的模式之一。|  
|trustedStoreLocation|兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。  當與用戶端交涉服務憑證時，會使用這個值。  會針對指定之存放位置內的 \[**受信任的人**\] 存放區來執行驗證。|  
  
## customCertificateValidatorType 屬性  
  
|值|描述|  
|-------|--------|  
|String|選擇項。  指定型別名稱和組件以及用來尋找此型別的其他資料。  至少需要命名空間和型別名稱。  選擇性的資訊包括：組件名稱、版本號碼、文化特性和公開金鑰權杖。|  
  
## certificateValidationMode 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|選擇項。  下列其中一個值：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom`。  預設為 `ChainTrust`。  預設為 `ChainTrust`。<br /><br /> 如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。|  
  
## revocationMode 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|下列其中一個值：`NoCheck`、`Online`、`Offline`。  預設為 `Online`。<br /><br /> 如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。|  
  
## trustedStoreLocation 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|下列其中一個值：`LocalMachine` 或 `CurrentUser`。  預設為 `CurrentUser`。  如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。  如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。  預設為 `CurrentUser`。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|指定向對等服務驗證用戶端時所使用的認證。|  
  
## 備註  
 如果已選取訊息驗證，則必須設定這個項目。  針對輸出通道，每個訊息都會以 [\<certificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md) 提供的憑證進行簽署。  所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。  驗證器可接受或拒絕認證。  
  
## 範例  
 下列程式碼會將訊息寄件者驗證模式設定為 `PeerOrChainTrust`。  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>   
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/zh-tw/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/zh-tw/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [確保對等通道應用程式安全](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)