---
title: HOW TO：建立聯合用戶端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
ms.openlocfilehash: a9213d8cbbafaaa1fffa3a1db0d6936c2fc6544f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185047"
---
# <a name="how-to-create-a-federated-client"></a>HOW TO：建立聯合用戶端
在 Windows 通信基礎 （WCF） 中，為*聯合服務*創建用戶端包括三個主要步驟：  
  
1. 配置[\<ws-IaiHTTP 綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)或類似的自訂綁定。 有關創建適當綁定的詳細資訊，請參閱[：創建 WS聯邦Http綁定](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)。 或者，根據聯合服務的中繼資料終結點運行[ServiceModel 中繼資料實用程式工具 （Svcutil.exe），](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)以生成用於與聯合服務和一個或多個安全權杖服務通信的設定檔。  
  
2. 針對可控制用戶端與安全性權杖服務之間各種互動方式的 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 設定其屬性。  
  
3. 設定 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> 的屬性，以提供與特定端點 (例如，安全性權杖服務) 安全通訊所需的憑證。  
  
> [!NOTE]
> 當用戶端使用模擬認證、<xref:System.Security.Cryptography.CryptographicException> 繫結或自訂發行權杖，以及非對稱金鑰時，可能會擲回 <xref:System.ServiceModel.WSFederationHttpBinding>。 當 <xref:System.ServiceModel.WSFederationHttpBinding> 和 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> 屬性分別設為 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> 時，非對稱金鑰便能與 <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey> 繫結或自訂發行權杖一起使用。 當用戶端嘗試傳送訊息，而用戶端想要模擬的身分識別並沒有使用者設定檔時，就會擲回 <xref:System.Security.Cryptography.CryptographicException>。 若要減少發生這個問題，請在傳送訊息之前登入用戶端電腦，或是呼叫 `LoadUserProfile`。  
  
 本主題提供這些程序的詳細資訊。 有關創建適當綁定的詳細資訊，請參閱[：創建 WS聯邦Http綁定](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)。 有關聯合服務的工作原理的詳細資訊，請參閱[聯合服務](../../../../docs/framework/wcf/feature-details/federation.md)。  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>若要產生並檢查聯合服務的組態  
  
1. 運行[服務模型中繼資料實用程式工具 （Svcutil.exe），](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)將服務的中繼資料 URL 的位址作為命令列參數運行。  
  
2. 透過適當的編輯器開啟產生的組態檔。  
  
3. 檢查任何生成的[\<頒發者>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)和[\<頒發者中繼資料>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)元素的屬性和內容。 它們位於[\<ws-IaBHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)或自訂繫結元素[\<的安全>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)元素中。 請確定位址包含預期的網域名稱或其他位址資訊。 請務必檢查這項資訊，因為用戶端會對這些位址進行驗證，而且可能揭露使用者名稱/密碼組這類的資訊。 如果位址不是預期的位址，可能會導致向不適當的收件者揭露資訊。  
  
4. 檢查注釋`alternativeIssuedTokenParameters`<>元素中的任何其他[\<頒發的Token參數>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)元素。 使用 Svcutil.exe 工具來產生聯合服務的組態時，如果聯合服務或任何中繼安全性權杖服務未指定發行者位址，而是指定了會公開多個端點之安全性權杖服務的中繼資料位址，則結果組態檔會參照到第一個端點。 其他終結點在設定檔中作為注釋`alternativeIssuedTokenParameters`<>元素。  
  
     確定這些<>`issuedTokenParameters`之一是否比配置中已有的>更可取。 例如，用戶端可能更願意使用 Windows CardSpace 權杖而不是使用者名和密碼對對安全權杖服務進行身份驗證。  
  
    > [!NOTE]
    > 如果與服務進行通訊之前，必須周遊多個安全性權杖服務時，中繼安全性權杖服務可能會將用戶端導向不正確的安全性權杖服務。 因此，請確保[\<已頒發 Token 參數](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)中的安全權杖服務的終結點>是預期的安全權杖服務，而不是未知的安全權杖服務。  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>若要透過程式碼設定 IssuedTokenClientCredential  
  
1. 如下列範例程式碼所示，透過 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 類別的 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> 屬性，存取 <xref:System.ServiceModel.Description.ClientCredentials> (由 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 類別的 <xref:System.ServiceModel.ClientBase%601> 屬性傳回，或是透過 <xref:System.ServiceModel.ChannelFactory> 類別)。  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. 如果不需要權杖快取，請將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> 屬性設為 `false`。 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> 屬性控制是否快取來自安全性權杖服務的這類權杖。 如果此屬性設為 `false`，每當用戶端必須向聯合服務重新驗證自己時，不管前一個權杖是否仍舊有效，都會向安全性權杖服務要求新的權杖。 如果此屬性設為 `true`，每當用戶端必須向聯合服務重新驗證自己時，只要權杖尚未到期，用戶端都會重複使用現有的權杖。 預設值為 `true`。  
  
3. 如果必須在快取的權杖上設定時間限制，請將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> 屬性設為 <xref:System.TimeSpan> 值。 此屬性會指定多久快取權杖一次。 一旦經過了指定的時間範圍，就會從用戶端快取中移除權杖。 根據預設，權杖無快取時間限制。 下列範例會將時間範圍設為 10 分鐘。  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. 選擇性。 將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> 設為百分比。 預設為 60%。 此屬性會指定權杖的有效期間百分比。 例如，如果發行權杖有效時間是 10 小時，而 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> 設為 80，則權杖會在 8 小時後更新。 下例範例會將值設為 80%。  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     當快取時間比更新閾值時間還短時，由權杖有效期間與 `IssuedTokenRenewalThresholdPercentage` 值決定的更新間隔會被 `MaxIssuedTokenCachingTime` 值覆寫。 例如，如果 `IssuedTokenRenewalThresholdPercentage` 和權杖有效期間的乘積是 8 小時，而 `MaxIssuedTokenCachingTime` 值為 10 分鐘，則用戶端會每 10 分鐘連絡一次安全性權杖服務以取得更新的權杖。  
  
5. 如果不使用訊息安全性或傳輸安全性來搭配訊息認證的繫結，需要 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> 以外的金鑰 Entropy 模式 (例如， 繫結不包含 <xref:System.ServiceModel.Channels.SecurityBindingElement>)，請將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> 屬性設為適當值。 *熵*模式確定是否可以使用 屬性<xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A>控制對稱鍵。 預設是 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>，其中用戶端與權杖發行者所提供的資料將合併用來產生真正的金鑰。 其他值則是 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> 和 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>，這兩個值表示整個金鑰將分別由用戶端或伺服器全權決定。 下列範例設定的屬性將會只使用伺服器資料來產生金鑰。  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    > 如果安全性權杖服務或服務繫結中存在 <xref:System.ServiceModel.Channels.SecurityBindingElement>，則 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> 上所設定的 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 會被 <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> 的 `SecurityBindingElement` 屬性覆寫。  
  
6. 設定任何特定發行者的端點行為時，請將它們新增至 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> 屬性所傳回的集合中。  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>若要透過組態設定 IssuedTokenClientCredential  
  
1. 在[\<終結點行為中創建已頒發的Token>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)元素作為[\<已頒發Token>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)元素的子項目。  
  
2. 如果不需要權杖緩存，則將`cacheIssuedTokens`屬性（<>`issuedToken`元素）設置為`false`。  
  
3. 如果緩存權杖需要時間限制，則`maxIssuedTokenCachingTime``issuedToken`<>元素的屬性設置為適當的值。 例如：  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. 如果首選預設值以外的值，則將`issuedTokenRenewalThresholdPercentage`<>`issuedToken`元素的屬性設置為適當的值，例如：  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. 如果不使用訊息安全性或傳輸安全性來搭配訊息認證的繫結程序需要的是 `CombinedEntropy` 以外的金鑰 Entropy 模式 (例如，繫結程序不包含 `SecurityBindingElement`)，請視需要將 `defaultKeyEntropyMode` 項目上的 `<issuedToken>` 屬性設為 `ServerEntropy` 或 `ClientEntropy`。  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. 選擇性。 通過將<>`issuerChannelBehaviors`元素作為<>`issuedToken`元素的子項目來配置任何特定于頒發器的自訂終結點行為。 對於每個行為，創建一個`add`<>元素作為<>`issuerChannelBehaviors`元素的子項目。 通過在<>`issuerAddress``add`元素上設置屬性來指定行為的頒發者位址。 通過在<>`add`元素上設置屬性`behaviorConfiguration`來指定行為本身。  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>若要透過程式碼設定 X509CertificateRecipientClientCredential  
  
1. 透過屬於 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> 類別或 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> 屬性的 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 屬性之 <xref:System.ServiceModel.ClientBase%601> 屬性，存取 <xref:System.ServiceModel.ChannelFactory>。  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. 如果特定端點憑證可使用 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 執行個體，請使用 <xref:System.Collections.Generic.ICollection%601.Add%2A> 屬性所傳回之集合的 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> 方法。  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. 如下列範例所示，如果無法使用 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 執行個體，請使用 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> 方法。  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>若要透過組態設定 X509CertificateRecipientClientCredential  
  
1. 將[\<作用域證書>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)元素作為[\<服務證書>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)元素的子項目創建，該元素本身是終結點行為中[\<用戶端憑據>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)元素的子項目。  
  
2. 建立 `<add>` 項目以做為 `<scopedCertificates>` 項目的子項。 指定 `storeLocation`、`storeName`、`x509FindType` 和 `findValue` 的屬性值以參照到適當的憑證。 將 `targetUri` 的屬性值設為將使用該憑證之端點的位址，如下列範例所示。  
  
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
  
 有關設置<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A><xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A><xref:System.ServiceModel.Security.IssuedTokenClientCredential>類 的 和<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A>屬性的詳細資訊，請參閱[如何：配置本地頒發者](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。  
  
## <a name="scoped-certificates"></a>範圍憑證  
 一般來說，如果因為沒有使用憑證交涉而必須指定服務憑證才能與任何一項安全性權杖服務通訊的話，您可以透過 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> 屬性來指定服務憑證。 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> 方法會採用 <xref:System.Uri> 和 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 做為參數。 在指定的 URI 上與端點通訊時，會使用指定的憑證。 或者，您可以使用 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> 方法，將憑證新增至 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> 屬性所傳回的集合中。  
  
> [!NOTE]
> 用戶端對於規範到特定 URI 範圍的憑證概念，只會套用到對服務 (可在這些 URI 上公開端點) 執行傳出呼叫的應用程式上。 它不適用於用於對已頒發的權杖進行簽名的證書，例如<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A><xref:System.ServiceModel.Security.IssuedTokenServiceCredential>類返回的集合中伺服器上配置的權杖。 有關詳細資訊，請參閱[：在識別身分同盟服務上配置憑據](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。  
  
## <a name="see-also"></a>另請參閱

- [同盟範例](../../../../docs/framework/wcf/samples/federation-sample.md)
- [HOW TO：在 WSFederationHttpBinding 上停用安全工作階段](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [如何：建立 WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [HOW TO：設定聯合服務的認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [HOW TO：設定本機簽發者](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [中繼資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [HOW TO：安全中繼資料端點](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
