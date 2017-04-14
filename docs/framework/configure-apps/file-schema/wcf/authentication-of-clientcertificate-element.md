---
title: "&lt;clientCertificate&gt; 的 &lt;authentication&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# &lt;clientCertificate&gt; 的 &lt;authentication&gt; 項目
指定服務所使用之用戶端憑證的驗證行為。  
  
## 語法  
  
```  
  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|customCertificateValidatorType|選擇性字串。  用來驗證自訂型別的型別和組件。  當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。|  
|certificateValidationMode|選擇性列舉。  指定用來驗證認證的其中一個模式。  此屬性的型別為 [System.Servicemodel.Security.X509CertificateValidationMode](assetId:///System.Servicemodel.Security.X509CertificateValidationMode?qualifyHint=False&amp;autoUpgrade=True)。  如果設定為 `Custom`，也必須提供 `customCertificateValidator`。  預設為 `ChainTrust`。|  
|includeWindowsGroups|選擇性布林值。  指定 Windows 群組是否包含在安全性內容中。  將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。  如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。|  
|mapClientCertificateToWindowsAcccount|布林值。  指定是否能夠使用憑證將用戶端對應至 Windows 身分識別。  必須啟用 Active Directory 才能這麼做。|  
|revocationMode|選擇性列舉。  用於檢查撤銷憑證清單 \(RCL\) 的模式之一。  預設為 `Online`。  使用 HTTP 傳輸安全性時，將忽略此值。|  
|trustedStoreLocation|選擇性列舉。  兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。  當與用戶端交涉服務憑證時，會使用這個值。  會針對指定之存放位置內的 \[**受信任的人**\] 存放區來執行驗證。  預設為 `CurrentUser`。|  
  
## customCertificateValidatorType 屬性  
  
|值|描述|  
|-------|--------|  
|String|指定型別名稱和組件以及用來尋找此型別的其他資料。|  
  
## certificateValidationMode 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|下列其中一個值：None、PeerTrust、ChainTrust、PeerOrChainTrust、Custom。<br /><br /> 如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。|  
  
## revocationMode 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|下列其中一個值：NoCheck、Online、Offline。  如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。|  
  
## trustedStoreLocation 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|下列其中一個值：`LocalMachine` 或 `CurrentUser`。  預設為 `CurrentUser`。  如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。  如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<clientCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|定義用於向服務驗證的 X.509 憑證。|  
  
## 備註  
 `<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 類別。  它可讓您自訂驗證用戶端的方法。  您可以將 `certificateValidationMode` 屬性 \(Attribute\) 設定為 `None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust` 或 `Custom`。  根據預設，層級會設為 `ChainTrust`，指定每一個憑證必須出現在鏈結頂端以「*根授權*」\(Root Authority\) 為結尾的憑證階層中。  這是最安全的模式。  您也可以將值設定為 `PeerOrChainTrust`，指定可接受自行發出的憑證 \(對等信任\)，以及信任鏈結內的憑證。  這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。  部署用戶端時，請改用 `ChainTrust` 值。  
  
 您也可以將值設定為 `Custom`。  設定為 `Custom` 值時，您還必須將 `customCertificateValidatorType` 屬性設定為可用來驗證憑證的組件與型別。  若要建立自己的自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。  如需詳細資訊，請參閱[HOW TO：建立使用自訂憑證驗證程式的服務](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。  
  
## 範例  
 下列程式碼會在 `<authentication>` 項目中指定 X.509 憑證和自訂驗證類型。  
  
```  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>   
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>   
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>   
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [HOW TO：建立使用自訂憑證驗證程式的服務](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)