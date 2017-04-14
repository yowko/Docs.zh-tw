---
title: "WCF 中的安全性行為 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
caps.latest.revision: 23
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 23
---
# WCF 中的安全性行為
在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中，行為會修改服務層級或端點層級的執行階段行為 \([!INCLUDE[crabout](../../../../includes/crabout-md.md)]行為的一般詳細資訊，請參閱[指定服務執行階段行為](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)\)。「*安全性行為*」\(Security Behavior\) 可控制認證、驗證、授權和稽核記錄。您可以藉由程式設計的方式或透過組態的方式使用這些行為。本主題將著重於設定下列與安全性功能相關的行為：  
  
-   [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
-   [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
-   [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
-   [\<serviceSecurityAudit\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
-   [\<serviceMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)，此項目也可讓您指定讓用戶端存取中繼資料的安全端點。  
  
## 設定認證與行為  
 使用 [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) 和 [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) 為服務或用戶端設定認證值。基礎繫結組態會判斷是否必須設定認證。例如，若安全性模式設定為 `None`，則用戶端和服務不需互相驗證彼此，也不需要任何類型的認證。  
  
 另一方面，服務繫結可以要求用戶端認證類型。在這種情況下，您必須使用行為設定認證值\([!INCLUDE[crabout](../../../../includes/crabout-md.md)]可能之認證類型的詳細資訊，請參閱[選取認證類型](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)\)。在某些情況下 \(如：使用 Windows 認證進行驗證時\)，環境會自動建立實際的認證值，您不需要明確地設定認證值 \(除非您想要指定不同的認證集合\)。  
  
 所有的服務認證會以 [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) 之子項目的形式出現。下列範例示範當成服務認證使用的憑證。  
  
```  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"   
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## 服務認證  
 [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)包含四個子項目。下列各章節將討論這些項目及其使用方法。  
  
### \<serviceCertificate\> 項目  
 使用此項目指定 X.509 憑證，而該憑證將用以驗證使用訊息安全性模式的用戶端服務。如果您是使用會定期更新的憑證，則其指紋將會變更。在這種情況下，請使用主體名稱當成 `X509FindType`，因為憑證可以使用相同的主體名稱重新發出。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用項目的詳細資訊，請參閱 [HOW TO：指定用戶端認證值](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)。  
  
### \<clientCertificate\> 的 \<certificate\> 項目  
 當服務必須具有用戶端的憑證，以便與用戶端安全地進行通訊，請使用 [\<certificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) 項目。這種情況發生在使用雙工通訊模式時。在較為典型的要求\-回覆模式下，用戶端會在要求中納入其憑證，以便讓服務使用此憑證安全地將回覆傳回用戶端。不過，雙工通訊模式便沒有要求和回覆。由於服務無法從通訊中推斷用戶端的憑證，服務即需要用戶端的憑證，以便與用戶端安全地傳遞訊息。您必須以超出範圍的方式取得用戶端的憑證，並使用此項目指定憑證。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]雙工服務的詳細資訊，請參閱 [HOW TO：建立雙工合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。  
  
### \<clientCertificate\> 項目的 \<authentication\>  
 [\<authentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) 項目可讓您自訂驗證用戶端的方法。您可以將 `CertificateValidationMode` 屬性 \(Attribute\) 設定為 `None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust` 或 `Custom`。根據預設，層級會設為 `ChainTrust`，指定每一個憑證必須出現在鏈結頂端以「*根授權*」\(Root Authority\) 為結尾的憑證階層中。這是最安全的模式。您也可以將值設定為 `PeerOrChainTrust`，指定可接受自行發出的憑證 \(對等信任\)，以及信任鏈結內的憑證。這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。部署用戶端時，請改用 `ChainTrust` 值。您也可以將值設定為 `Custom`。設定為 `Custom` 值時，您還必須將 `CustomCertificateValidatorType` 屬性設定為可用來驗證憑證的組件與型別。若要建立自己的自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。  
  
### \<issuedTokenAuthentication\> 項目  
 發行之權杖的情況有三個階段。在第一個階段中，用戶端會嘗試存取稱為「*安全權杖服務*」\(Secure Token Service，STS\) 的服務。此 STS 接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 \(SAML\) 權杖。用戶端接著會以權杖傳回服務。此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。[\<issuedTokenAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) 項目是任何此類安全權杖服務憑證的存放庫。若要加入憑證，請使用 [\<knownCertificates\>](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)。為每個憑證插入 [\<add\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)，如下列範例所示。  
  
```  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 根據預設，必須從安全權杖服務取得憑證。這些「已知的」憑證可確保只有合法的用戶端可以存取服務。  
  
 您應該在使用會發行 `SamlSecurityToken` 安全性權杖之*「安全權杖服務」* \(Secure Token Service，STS\) 的聯合應用程式中使用 [\<allowedAudienceUris\>](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) 集合。當 STS 發出安全性權杖時，它可以將 `SamlAudienceRestrictionCondition` 加入至安全性權杖中，以便指定此安全性權杖適用之 Web 服務的 URI。如此便可讓接收端 Web 服務的 `SamlSecurityTokenAuthenticator` 驗證發出的安全性權杖是否適用於此 Web 服務，而驗證的方法則是指定這項檢查應該透過執行下列動作來進行：  
  
-   將 [\<issuedTokenAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) 的 `audienceUriMode` 屬性設定為 `Always` 或 `BearerKeyOnly`。  
  
-   將 URI 加入此集合，以指定有效的 URI 集合。若要執行這個步驟，可在每一個 URI 中插入 [\<add\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用這個組態項目的詳細資訊，請參閱 [HOW TO：設定聯合服務的認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。  
  
#### 允許匿名的 CardSpace 使用者  
 將 `<IssuedTokenAuthentication>` 項目的 `AllowUntrustedRsaIssuers` 屬性設定為 `true`，以明確地允許任何用戶端提出以任一 RSA 金鑰組所簽署之自行發行的權杖。簽發者是「*不受信任的*」\(Untrusted\)，因為沒有與金鑰關聯的簽發者資料。[!INCLUDE[infocard](../../../../includes/infocard-md.md)] 使用者可以建立自動發行資訊卡，其中包含自行提供的身分識別宣告。使用這個功能時必須要很小心。若要使用此功能，請考慮使用 RSA 公開金鑰做為更安全的密碼，這個金鑰應該與使用者名稱一起儲存在資料庫中。允許用戶端存取服務之前，請確認用戶端所提出的 RSA 公開金鑰，此動作可透過將用戶端所提出的 RSA 公開金鑰與所呈現之使用者名稱對應的儲存公開金鑰進行比較來達成。這個情況是假設您已建立註冊程式，以便讓使用者註冊其使用者名稱，並將其與自行發行的 RSA 公開金鑰產生關聯。  
  
## 用戶端認證  
 在需要雙向驗證的情況下，用戶端認證可用於驗證服務的用戶端。在用戶端必須以服務的憑證保護傳遞給服務的訊息時，您可以使用此章節的說明指定服務憑證。  
  
 您也可以將用戶端設定為同盟情節的一部分，以便從安全權杖服務或權杖的本機簽發者使用發行的權杖。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]同盟情節的詳細資訊，請參閱 [聯合與發行的權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。所有用戶端認證都可以在 [\<endpointBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)下找到，如下列程式碼所示。  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"     
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"   
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
#### \<clientCertifictate\> 項目  
 使用此項目來設定用以驗證用戶端的憑證。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][HOW TO：指定用戶端認證值](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### \<httpDigest\>  
 此功能必須與 Windows 和 Internet Information Services \(IIS\) 上的 Active Directory 一起啟用。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][IIS 6.0 中的摘要式驗證](http://go.microsoft.com/fwlink/?LinkId=88443)。  
  
#### \<issuedToken\> 項目  
 [\<issuedToken\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)包含用以設定權杖之本機簽發者的項目，或搭配安全性權杖服務使用的行為。如需將用戶端設定為使用本機簽發者的指示，請參閱 [HOW TO：設定本機簽發者](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。  
  
#### \<localIssuerAddress\>  
 指定預設的安全性權杖服務位址。這會在 <xref:System.ServiceModel.WSFederationHttpBinding> 未提供安全性權杖服務的 URL 時使用，或者在聯合繫結的簽發者位址為 http:\/\/schemas.microsoft.com\/2005\/12\/ServiceModel\/Addressing\/Anonymous 或 `null` 時使用。在這種情形下，<xref:System.ServiceModel.Description.ClientCredentials> 必須設定本機簽發者的位址，以及用於與該簽發者進行通訊的繫結。  
  
#### \<issuerChannelBehaviors\>  
 使用 [\<issuerChannelBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)加入 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端行為，以便在與安全性權杖服務通訊時使用。在 [\<endpointBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) 區段內定義用戶端行為。若要使用已定義的行為，請將 \<`add`\> 項目加入至具有兩個屬性的 `<issuerChannelBehaviors>` 項目中。將 `issuerAddress` 設定為安全性權杖服務的 URL，並將 `behaviorConfiguration` 屬性設定為已定義之端點行為的名稱，如下列範例所示。  
  
```  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### \<serviceCertificate\> 項目  
 使用此項目控制服務憑證的驗證。  
  
 [\<defaultCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) 項目可以儲存單一憑證，這個憑證會在服務未指定憑證時使用。  
  
 使用 [\<scopedCertificates\>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) 和 [\<add\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)設定與特定服務相關聯的服務憑證。`<add>` 項目包含 `targetUri` 屬性，此屬性是用於將憑證與服務產生關聯。  
  
 [\<驗證\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) 項目會指定信任的層級，而用以驗證憑證。根據預設，層級會設為 "ChainTrust"，指定每一個憑證必須出現在鏈結頂端以受信任的憑證授權單位為結尾的憑證階層中。這是最安全的模式。您也可以將其值設定為 "PeerOrChainTrust"，指定可接受自行簽發的憑證 \(對等信任\)，以及信任鏈結內的憑證。這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。部署用戶端時，請改用 "ChainTrust" 值。您也可以將值設定為 "Custom" 或 "None"。若要使用 "Custom" 值，您必須同時將 `CustomCertificateValidatorType` 屬性設為可用來驗證憑證的組件與型別。若要建立自己的自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][HOW TO：建立使用自訂憑證驗證程式的服務](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [\<驗證\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) `RevocationMode 項目包含`  屬性，用以指定檢查憑證是否已被撤銷的方法。預設為 "online"，指出會自動檢查該憑證是否已被撤銷。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## ServiceAuthorization  
 [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) 項目所包含的項目會影響授權、自訂的角色提供者，以及模擬。  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 類別會套用至服務方法。屬性會指定使用者群組，以便在對保護的方法進行授權使用時使用。預設值為 "UseWindowsGroups"，指定在 Windows 群組 \(例如 "Administrators" 或 "Users"\) 中搜尋嘗試存取資源的身分識別。您也可指定 "UseAspNetRoles" 以使用自訂的角色提供者 \(在 \<`system.web` \> 項目之下設定\)，如下列程式碼所示。  
  
```  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 下列程式碼示範搭配 `principalPermissionMode` 屬性使用 `roleProviderName`。  
  
```  
<behaviors>  
 <behavior name="ServiceBehaviour">          
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                        roleProviderName ="SqlProvider" />  
</behavior>   
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## 設定安全性稽核  
 使用 [\<serviceSecurityAudit\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)指定要寫入的記錄，以及所要記錄的事件類型。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][稽核](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
```  
<system.serviceModel>  
<serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## 安全的中繼資料交換  
 將中繼資料匯出至用戶端對於服務和用戶端的開發人員來說是很方便的，因為如此一來便可以下載設定和用戶端程式碼。若要降低將服務暴露給惡意使用者的機會，可以使用 SSL over HTTP \(HTTPS\) 機制來進行安全的傳輸。若要這麼做，您必須先將適當的 X.509 憑證，繫結至裝載服務之電腦上的特定連接埠 \([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).\)其次，將 [\<serviceMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)`HttpsGetEnabled`加入至服務組態，並將 `true` 屬性設定為 。最後，將 `HttpsGetUrl` 屬性設定為服務中繼資料端點的 URL，如下列範例所示。  
  
```  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"   
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## 請參閱  
 [稽核](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)   
 [Windows Server AppFabric 的資訊安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)