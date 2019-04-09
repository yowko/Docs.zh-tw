---
title: HOW TO：建立同盟用戶端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
ms.openlocfilehash: 457c09ec381db97bc757b9288c9d6ebc0890a305
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104321"
---
# <a name="how-to-create-a-federated-client"></a>HOW TO：建立同盟用戶端
在 Windows Communication Foundation (WCF) 中，建立適用於用戶端*同盟服務*包含三個主要步驟：  
  
1.  設定[ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)或類似的自訂繫結。 如需建立適當的繫結的詳細資訊，請參閱[How to:建立 WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)。 或者，執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)針對聯合服務來產生聯合的服務和一或多個與通訊的組態檔的中繼資料端點安全性權杖服務。  
  
2.  針對可控制用戶端與安全性權杖服務之間各種互動方式的 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 設定其屬性。  
  
3.  設定 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> 的屬性，以提供與特定端點 (例如，安全性權杖服務) 安全通訊所需的憑證。  
  
> [!NOTE]
>  當用戶端使用模擬認證、<xref:System.Security.Cryptography.CryptographicException> 繫結或自訂發行權杖，以及非對稱金鑰時，可能會擲回 <xref:System.ServiceModel.WSFederationHttpBinding>。 當 <xref:System.ServiceModel.WSFederationHttpBinding> 和 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> 屬性分別設為 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> 時，非對稱金鑰便能與 <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey> 繫結或自訂發行權杖一起使用。 當用戶端嘗試傳送訊息，而用戶端想要模擬的身分識別並沒有使用者設定檔時，就會擲回 <xref:System.Security.Cryptography.CryptographicException>。 若要減少發生這個問題，請在傳送訊息之前登入用戶端電腦，或是呼叫 `LoadUserProfile`。  
  
 本主題提供這些程序的詳細資訊。 如需建立適當的繫結的詳細資訊，請參閱[How to:建立 WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)。 如需聯合的服務的運作方式的詳細資訊，請參閱[同盟](../../../../docs/framework/wcf/feature-details/federation.md)。  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>若要產生並檢查聯合服務的組態  
  
1.  執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)中繼資料服務的 URL 做為命令列參數的位址。  
  
2.  透過適當的編輯器開啟產生的組態檔。  
  
3.  檢查屬性和任何產生的內容[\<簽發者 >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)並[ \<issuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)項目。 這些都是位於[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)項目[ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)或自訂繫結項目。 請確定位址包含預期的網域名稱或其他位址資訊。 請務必檢查這項資訊，因為用戶端會對這些位址進行驗證，而且可能揭露使用者名稱/密碼組這類的資訊。 如果位址不是預期的位址，可能會導致向不適當的收件者揭露資訊。  
  
4.  檢查任何額外[ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)加上註解的項目出 <`alternativeIssuedTokenParameters`> 項目。 使用 Svcutil.exe 工具來產生聯合服務的組態時，如果聯合服務或任何中繼安全性權杖服務未指定發行者位址，而是指定了會公開多個端點之安全性權杖服務的中繼資料位址，則結果組態檔會參照到第一個端點。 標記為註解為組態檔中的其他端點則是 <`alternativeIssuedTokenParameters`> 項目。  
  
     判斷這些 <`issuedTokenParameters`> 最好是在組態中已存在。 例如，用戶端可能會偏好使用 Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] 權杖 (而不是使用者名稱/密碼組) 向安全性權杖服務進行驗證。  
  
    > [!NOTE]
    >  如果與服務進行通訊之前，必須周遊多個安全性權杖服務時，中繼安全性權杖服務可能會將用戶端導向不正確的安全性權杖服務。 因此，請確定在安全性權杖服務的端點[ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)是預期的安全性權杖服務而不未知的安全性權杖服務。  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>若要透過程式碼設定 IssuedTokenClientCredential  
  
1.  如下列範例程式碼所示，透過 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 類別的 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> 屬性，存取 <xref:System.ServiceModel.Description.ClientCredentials> (由 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 類別的 <xref:System.ServiceModel.ClientBase%601> 屬性傳回，或是透過 <xref:System.ServiceModel.ChannelFactory> 類別)。  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2.  如果不需要權杖快取，請將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> 屬性設為 `false`。 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> 屬性控制是否快取來自安全性權杖服務的這類權杖。 如果此屬性設為 `false`，每當用戶端必須向聯合服務重新驗證自己時，不管前一個權杖是否仍舊有效，都會向安全性權杖服務要求新的權杖。 如果此屬性設為 `true`，每當用戶端必須向聯合服務重新驗證自己時，只要權杖尚未到期，用戶端都會重複使用現有的權杖。 預設為 `true`。  
  
3.  如果必須在快取的權杖上設定時間限制，請將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> 屬性設為 <xref:System.TimeSpan> 值。 此屬性會指定多久快取權杖一次。 一旦經過了指定的時間範圍，就會從用戶端快取中移除權杖。 根據預設，權杖無快取時間限制。 下列範例會將時間範圍設為 10 分鐘。  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4.  選擇性。 將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> 設為百分比。 預設為 60%。 此屬性會指定權杖的有效期間百分比。 例如，如果發行權杖有效時間是 10 小時，而 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> 設為 80，則權杖會在 8 小時後更新。 下例範例會將值設為 80%。  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     當快取時間比更新閾值時間還短時，由權杖有效期間與 `IssuedTokenRenewalThresholdPercentage` 值決定的更新間隔會被 `MaxIssuedTokenCachingTime` 值覆寫。 例如，如果 `IssuedTokenRenewalThresholdPercentage` 和權杖有效期間的乘積是 8 小時，而 `MaxIssuedTokenCachingTime` 值為 10 分鐘，則用戶端會每 10 分鐘連絡一次安全性權杖服務以取得更新的權杖。  
  
5.  如果不使用訊息安全性或傳輸安全性來搭配訊息認證的繫結，需要 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> 以外的金鑰 Entropy 模式 (例如， 繫結不包含 <xref:System.ServiceModel.Channels.SecurityBindingElement>)，請將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> 屬性設為適當值。 *Entropy*模式會決定是否可以使用來控制對稱金鑰<xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A>屬性。 預設是 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>，其中用戶端與權杖發行者所提供的資料將合併用來產生真正的金鑰。 其他值則是 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> 和 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>，這兩個值表示整個金鑰將分別由用戶端或伺服器全權決定。 下列範例設定的屬性將會只使用伺服器資料來產生金鑰。  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    >  如果安全性權杖服務或服務繫結中存在 <xref:System.ServiceModel.Channels.SecurityBindingElement>，則 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> 上所設定的 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 會被 <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> 的 `SecurityBindingElement` 屬性覆寫。  
  
6.  設定任何特定發行者的端點行為時，請將它們新增至 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> 屬性所傳回的集合中。  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>若要透過組態設定 IssuedTokenClientCredential  
  
1.  建立[ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)的子系的項目[ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)是端點行為中的項目。  
  
2.  如果權杖快取並非必要，設定`cacheIssuedTokens`屬性 (的 <`issuedToken`> 項目) 來`false`。  
  
3.  如果快取的權杖需要時間限制時，請設定`maxIssuedTokenCachingTime`屬性上 <`issuedToken`> 設為適當值的項目。 例如:   
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4.  如果慣用預設值以外的值，設定`issuedTokenRenewalThresholdPercentage`屬性上 <`issuedToken`> 項目設為適當的值，例如：  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5.  如果不使用訊息安全性或傳輸安全性來搭配訊息認證的繫結程序需要的是 `CombinedEntropy` 以外的金鑰 Entropy 模式 (例如，繫結程序不包含 `SecurityBindingElement`)，請視需要將 `defaultKeyEntropyMode` 項目上的 `<issuedToken>` 屬性設為 `ServerEntropy` 或 `ClientEntropy`。  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6.  選擇性。 藉由設定任何特定發行者的自訂端點行為 <`issuerChannelBehaviors`> 元素的子系 <`issuedToken`> 項目。 每個行為，建立 <`add`> 元素的子系 <`issuerChannelBehaviors`> 項目。 設定以指定行為的簽發者位址`issuerAddress`屬性上 <`add`> 項目。 設定以指定行為本身`behaviorConfiguration`屬性上 <`add`> 項目。  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>若要透過程式碼設定 X509CertificateRecipientClientCredential  
  
1.  透過屬於 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> 類別或 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> 屬性的 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 屬性之 <xref:System.ServiceModel.ClientBase%601> 屬性，存取 <xref:System.ServiceModel.ChannelFactory>。  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2.  如果特定端點憑證可使用 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 執行個體，請使用 <xref:System.Collections.Generic.ICollection%601.Add%2A> 屬性所傳回之集合的 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> 方法。  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3.  如下列範例所示，如果無法使用 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 執行個體，請使用 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> 方法。  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>若要透過組態設定 X509CertificateRecipientClientCredential  
  
1.  建立[ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)的子系的項目[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)是本身的子系的項目[ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)是端點行為中的項目。  
  
2.  建立 `<add>` 項目以做為 `<scopedCertificates>` 項目的子項。 指定 `storeLocation`、`storeName`、`x509FindType` 和 `findValue` 的屬性值以參照到適當的憑證。 將 `targetUri` 的屬性值設為將使用該憑證之端點的位址，如下列範例所示。  
  
    ```xml  
    <scopedCertificates>  
     <add targetUri="http://fabrikam.com/sts"   
          storeLocation="CurrentUser"  
          storeName="TrustedPeople"  
          x509FindType="FindBySubjectName"  
          findValue="FabrikamSTS" />  
    </scopedCertificates>  
    ```  
  
## <a name="example"></a>範例  
 下列程式碼範例會透過程式碼設定 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 類別的執行個體。  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 為了避免發生資訊洩露，執行 Svcutil.exe 工具以處理來自聯合端點之中繼資料的用戶端需要確定結果的安全性權杖服務位址是所需要的。 當安全性權杖服務公開多個端點時，這點特別重要，因為 Svcutil.exe 工具會產生結果組態檔以運用第一個此類端點，但是這可能不是用戶端應該使用的端點。  
  
## <a name="localissuer-required"></a>需要 LocalIssuer  
 如果用戶端預期一律使用本機發行者，請注意下列事項：如果鏈結中倒數第二個安全性權杖服務指定了發行者位址或發行者中繼資料位址，則預設的 Svcutil.exe 輸出將會導致無法使用本機發行者。  
  
 如需設定的詳細資訊<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>， <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>，並<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A>的屬性<xref:System.ServiceModel.Security.IssuedTokenClientCredential>類別，請參閱[How to:設定本機簽發者](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。  
  
## <a name="scoped-certificates"></a>範圍憑證  
 一般來說，如果因為沒有使用憑證交涉而必須指定服務憑證才能與任何一項安全性權杖服務通訊的話，您可以透過 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> 屬性來指定服務憑證。 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> 方法會採用 <xref:System.Uri> 和 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 做為參數。 在指定的 URI 上與端點通訊時，會使用指定的憑證。 或者，您可以使用 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> 方法，將憑證新增至 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> 屬性所傳回的集合中。  
  
> [!NOTE]
>  用戶端對於規範到特定 URI 範圍的憑證概念，只會套用到對服務 (可在這些 URI 上公開端點) 執行傳出呼叫的應用程式上。 它不會套用到用來簽署已發行的權杖，例如所傳回的集合中的伺服器上設定的憑證<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>的<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>類別。 如需詳細資訊，請參閱[如何：Federation Service 上設定認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。  
  
## <a name="see-also"></a>另請參閱

- [聯合範例](../../../../docs/framework/wcf/samples/federation-sample.md)
- [HOW TO：在 WSFederationHttpBinding 上停用安全工作階段](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [HOW TO：建立 WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [HOW TO：設定同盟服務的認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [HOW TO：設定本機簽發者](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [中繼資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [HOW TO：保護中繼資料端點的安全](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
