---
title: WCF 中的安全性行為
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: b25d476e9c9b4a70834274c6970dad1b056cecb9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595202"
---
# <a name="security-behaviors-in-wcf"></a>WCF 中的安全性行為
在 Windows Communication Foundation （WCF）中，行為會在服務層級或端點層級修改執行時間行為。 （如需一般行為的詳細資訊，請參閱[指定服務執行時間行為](../specifying-service-run-time-behavior.md)。）*安全性行為*可讓您控制認證、驗證、授權和審核記錄。 您可以藉由程式設計的方式或透過組態的方式使用這些行為。 本主題將著重於設定下列與安全性功能相關的行為：  
  
- [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).  
  
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).  
  
- [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
- [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
- [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md)，這也可讓您指定用戶端可以存取中繼資料的安全端點。  
  
## <a name="setting-credentials-with-behaviors"></a>設定認證與行為  
 使用 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 和 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) 來設定服務或用戶端的認證值。 基礎繫結組態會判斷是否必須設定認證。 例如，若安全性模式設定為 `None`，則用戶端和服務不需互相驗證彼此，也不需要任何類型的認證。  
  
 另一方面，服務繫結程序可以要求用戶端認證類型。 在這種情況下，您必須使用行為設定認證值 （如需可能認證類型的詳細資訊，請參閱[選取認證類型](selecting-a-credential-type.md)）。在某些情況下（例如使用 Windows 認證進行驗證時），環境會自動建立實際的認證值，您不需要明確設定認證值（除非您想要指定一組不同的認證）。  
  
 所有服務認證都是以的子項目的形式存在 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 。 下列範例示範當成服務認證使用的憑證。  
  
```xml  
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
  
## <a name="service-credentials"></a>服務認證  
 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md)包含四個子項目。 下列各章節將討論這些項目及其使用方法。  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate> 項目  
 使用此項目指定 X.509 憑證，而該憑證將用以驗證使用訊息安全性模式的用戶端服務。 如果您是使用會定期更新的憑證，則其指紋將會變更。 在這種情況下，請使用主體名稱當成 `X509FindType`，因為憑證可以使用相同的主體名稱重新發出。  
  
 如需使用元素的詳細資訊，請參閱[如何：指定用戶端認證值](../how-to-specify-client-credential-values.md)。  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certificate> 項目的 \<clientCertificate>  
 [\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)當服務必須具有用戶端的憑證，以便與用戶端安全地進行通訊時，請使用元素。 這種情況發生在使用雙工通訊模式時。 在較為典型的要求-回覆模式下，用戶端會在要求中納入其憑證，以便讓服務使用此憑證安全地將回覆傳回用戶端。 不過，雙工通訊模式便沒有要求和回覆。 由於服務無法從通訊中推斷用戶端的憑證，服務即需要用戶端的憑證，以便與用戶端安全地傳遞訊息。 您必須以頻外的方式來取得用戶端的憑證，並使用此元素來指定憑證。 如需雙工服務的詳細資訊，請參閱[如何：建立雙工合約](how-to-create-a-duplex-contract.md)。  
  
### <a name="authentication-of-clientcertificate-element"></a>\<authentication> 項目的 \<clientCertificate>  
 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)元素可讓您自訂用戶端的驗證方式。 您可以將 `CertificateValidationMode` 屬性 (Attribute) 設定為 `None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust` 或 `Custom`。 根據預設，層級會設定為 `ChainTrust` ，這會指定每個憑證都必須在鏈頂端以*根授權*單位結尾的憑證階層中找到。 這是最安全的模式。 您也可以將值設定為 `PeerOrChainTrust`，指定可接受自行發出的憑證 (對等信任)，以及信任鏈結內的憑證。 這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。 部署用戶端時，請改用 `ChainTrust` 值。 您也可以將值設定為 `Custom`。 設定為 `Custom` 值時，您還必須將 `CustomCertificateValidatorType` 屬性設定為可用來驗證憑證的組件與型別。 若要建立自己的自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication> 項目  
 發行之權杖的情況有三個階段。 在第一個階段中，嘗試存取服務的用戶端稱為「*安全權杖服務*（STS）」。 此 STS 接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。 用戶端接著會以權杖傳回服務。 此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。 若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。 [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)元素是任何此類安全權杖服務憑證的存放庫。 若要新增憑證，請使用 [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md) 。 為 [\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md) 每個憑證插入，如下列範例所示。  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"
           storeLocation="LocalMachine" storeName="My"
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 根據預設，必須從安全權杖服務取得憑證。 這些「已知的」憑證可確保只有合法的用戶端可以存取服務。  
  
 您應該在使用會 [\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md) 發出安全性權杖之*安全權杖服務*（STS）的同盟應用程式中使用集合 `SamlSecurityToken` 。 當 STS 發出安全性權杖時，它可以將 `SamlAudienceRestrictionCondition` 加入至安全性權杖中，以便指定此安全性權杖適用之 Web 服務的 URI。 如此便可讓接收端 Web 服務的 `SamlSecurityTokenAuthenticator` 驗證發出的安全性權杖是否適用於此 Web 服務，而驗證的方法則是指定這項檢查應該透過執行下列動作來進行：  
  
- 將的 `audienceUriMode` 屬性設定 [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) 為 `Always` 或 `BearerKeyOnly` 。  
  
- 將 URI 加入此集合，以指定有效的 URI 集合。 若要這麼做，請 [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) 為每個 URI 插入  
  
 如需詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 。  
  
 如需使用此設定元素的詳細資訊，請參閱[如何：在同盟服務上設定認證](how-to-configure-credentials-on-a-federation-service.md)。  
  
#### <a name="allowing-anonymous-cardspace-users"></a>允許匿名的 CardSpace 使用者  
 將 `AllowUntrustedRsaIssuers` 項目的 `<IssuedTokenAuthentication>` 屬性設定為 `true`，以明確地允許任何用戶端提出以任一 RSA 金鑰組所簽署之自行發行的權杖。 簽發者未*受信任*，因為該金鑰沒有相關聯的簽發者資料。 CardSpace 使用者可以建立自我發行的卡片，其中包含自我提供的身分識別宣告。 使用這個功能時必須要很小心。 若要使用此功能，請考慮使用 RSA 公開金鑰做為更安全的密碼，這個金鑰應該與使用者名稱一起儲存在資料庫中。 允許用戶端存取服務之前，請確認用戶端所提出的 RSA 公開金鑰，此動作可透過將用戶端所提出的 RSA 公開金鑰與所呈現之使用者名稱對應的儲存公開金鑰進行比較來達成。 這個情況是假設您已建立註冊程式，以便讓使用者註冊其使用者名稱，並將其與自行發行的 RSA 公開金鑰產生關聯。  
  
## <a name="client-credentials"></a>用戶端認證  
 在需要雙向驗證的情況下，用戶端認證可用於驗證服務的用戶端。 在用戶端必須以服務的憑證保護傳遞給服務的訊息時，您可以使用此章節的說明指定服務憑證。  
  
 您也可以將用戶端設定為同盟案例的一部分，以便從安全權杖服務或權杖的本機簽發者使用發行的權杖。 如需聯合案例的詳細資訊，請參閱[同盟和發行的權杖](federation-and-issued-tokens.md)。 所有的用戶端認證都可以在底下找到 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) ，如下列程式碼所示。  
  
```xml  
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
</behaviors>  
```  
  
#### <a name="clientcertificate-element"></a>\<clientCertificate> 項目  
 使用此項目來設定用以驗證用戶端的憑證。 如需詳細資訊，請參閱[如何：指定用戶端認證值](../how-to-specify-client-credential-values.md)。  
  
#### \<httpDigest>  
 此功能必須與 Windows 和 Internet Information Services (IIS) 上的 Active Directory 一起啟用。 如需詳細資訊，請參閱[IIS 6.0 中的摘要式驗證](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))。  
  
#### <a name="issuedtoken-element"></a>\<issuedToken> 項目  
 [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md)包含用來設定權杖之本機簽發者的元素，或與 Security Token Service 搭配使用的行為。 如需將用戶端設定為使用本機簽發者的指示，請參閱[如何：設定本機簽發者](how-to-configure-a-local-issuer.md)。  
  
#### \<localIssuerAddress>  
 指定預設的安全性權杖服務位址。 當未 <xref:System.ServiceModel.WSFederationHttpBinding> 提供 Security Token Service 的 URL，或同盟系結的簽發者位址是或時，就會使用這個 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` 。 在這種情形下，<xref:System.ServiceModel.Description.ClientCredentials> 必須設定本機簽發者的位址，以及用於與該簽發者進行通訊的繫結。  
  
#### \<issuerChannelBehaviors>  
 使用 [\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) 新增與 Security Token Service 通訊時所使用的 WCF 用戶端行為。 定義一節中的用戶端行為 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) 。 若要使用已定義的行為，請將 <`add`> 元素新增至 `<issuerChannelBehaviors>` 具有兩個屬性的專案。 將 `issuerAddress` 設定為安全性權杖服務的 URL，並將 `behaviorConfiguration` 屬性設定為已定義之端點行為的名稱，如下列範例所示。  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
      </issuerChannelBehaviors>  
   </issuedToken>  
</clientCredentials>
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate> 項目  
 使用此項目控制服務憑證的驗證。  
  
 [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md)元素可以儲存當服務未指定憑證時所使用的單一憑證。  
  
 使用 [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) 和 [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) 設定與特定服務相關聯的服務憑證。 `<add>` 項目包含 `targetUri` 屬性，此屬性是用於將憑證與服務產生關聯。  
  
 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)元素會指定用來驗證憑證的信任層級。 根據預設，層級會設為 "ChainTrust"，指定每一個憑證必須出現在鏈結頂端以受信任的憑證授權單位為結尾的憑證階層中。 這是最安全的模式。 您也可以將其值設定為 "PeerOrChainTrust"，指定可接受自行簽發的憑證 (對等信任)，以及信任鏈結內的憑證。 這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。 部署用戶端時，請改用 "ChainTrust" 值。 您也可以將值設定為 "Custom" 或 "None"。 若要使用 "Custom" 值，您必須同時將 `CustomCertificateValidatorType` 屬性設為可用來驗證憑證的組件與型別。 若要建立自己的自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。 如需詳細資訊，請參閱[如何：建立採用自訂憑證驗證程式的服務](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。  
  
 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)元素包含 `RevocationMode` 屬性，指定如何檢查憑證的撤銷。 預設為 "online"，指出會自動檢查該憑證是否已被撤銷。 如需詳細資訊，請參閱[使用憑證](working-with-certificates.md)。  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)元素包含會影響授權、自訂角色提供者和模擬的元素。  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 類別會套用至服務方法。 屬性會指定使用者群組，以便在對保護的方法進行授權使用時使用。 預設值為 "UseWindowsGroups"，指定在 Windows 群組 (例如 "Administrators" 或 "Users") 中搜尋嘗試存取資源的身分識別。 您也可以指定 "UseAspNetRoles"，以使用在 <> 元素下設定的自訂角色提供者 `system.web` ，如下列程式碼所示。  
  
```xml  
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
  
 下列程式碼示範搭配 `roleProviderName` 屬性使用的 `principalPermissionMode`。  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                        roleProviderName ="SqlProvider" />  
</behavior>
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>設定安全性稽核  
 使用 [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) 指定寫入的記錄檔，以及要記錄的事件種類。 如需詳細資訊，請參閱「[審核](auditing-security-events.md)」。  
  
```xml  
<behaviors>
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
  
## <a name="secure-metadata-exchange"></a>安全的中繼資料交換  
 將中繼資料匯出至用戶端對於服務和用戶端的開發人員來說是很方便的，因為如此一來便可以下載設定和用戶端程式碼。 若要降低將服務暴露給惡意使用者的機會，可以使用 SSL over HTTP (HTTPS) 機制來進行安全的傳輸。 若要這麼做，您必須先將適當的 X.509 憑證，繫結至裝載服務之電腦上的特定連接埠  （如需詳細資訊，請參閱[使用憑證](working-with-certificates.md)）。第二，將新增 [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) 至服務設定，並將 `HttpsGetEnabled` 屬性設為 `true` 。 最後，將 `HttpsGetUrl` 屬性設定為服務中繼資料端點的 URL，如下列範例所示。  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>另請參閱

- [稽核](auditing-security-events.md)
- [Windows Server AppFabric 的資訊安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
