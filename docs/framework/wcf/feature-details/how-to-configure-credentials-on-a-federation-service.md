---
title: HOW TO：設定聯合服務的認證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
ms.openlocfilehash: 5bfea40a500dc1355b439ae7d949b0d96d3ab08c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495605"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>HOW TO：設定聯合服務的認證
在 Windows Communication Foundation (WCF)，建立聯合的服務包含下列主要程序：  
  
1.  設定 <xref:System.ServiceModel.WSFederationHttpBinding> 或類似的自訂繫結。 如需有關建立適當的繫結的詳細資訊，請參閱[How to： 建立 WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)。  
  
2.  設定 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>，此認證可控制如何驗證提供給服務的已發行權杖。  
  
 本主題會提供第二個步驟的詳細資訊。 如需同盟的服務的運作方式的詳細資訊，請參閱[同盟](../../../../docs/framework/wcf/feature-details/federation.md)。  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>使用程式碼來設定 IssuedTokenServiceCredential 的屬性  
  
1.  使用 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> 類別的 <xref:System.ServiceModel.Description.ServiceCredentials> 屬性，傳回 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> 執行個體 (Instance) 的參照。 此屬性可從 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 類別的 <xref:System.ServiceModel.ServiceHostBase> 屬性存取。  
  
2.  如果是要驗證類似 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> 卡的自行發行權杖，則將 `true` 屬性設定為 [!INCLUDE[infocard](../../../../includes/infocard-md.md)]。 預設值為 `false`。  
  
3.  將 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> 屬性所傳回的集合填入 (Populate) <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 類別的執行個體。 每個執行個體都代表服務將會從該處驗證權杖的簽發者。  
  
    > [!NOTE]
    >  不同於 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> 屬性所傳回的用戶端集合，已知憑證集合並不是有索引鍵的集合。 無論傳送包含已發行權杖之訊息的用戶端位址為何，服務都會接受已指定憑證所發行的權杖 (仍有其他條件限制，將於本主題稍後內容中說明)。  
  
4.  將 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> 屬性設定為其中一個 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 列舉值。 只有透過程式碼才能做到這點。 預設值為 <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>。  
  
5.  如果 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> 屬性是設定為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>，則會將自訂 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別的執行個體指派給 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> 屬性。  
  
6.  如果 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> 是設定為 `ChainTrust` 或 `PeerOrChainTrust`，則會將 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> 屬性設定為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 列舉中的適當值。 請注意，在 `PeerTrust` 或 `Custom` 驗證模式中沒有使用撤銷模式。  
  
7.  如有需要，將自訂 <xref:System.IdentityModel.Tokens.SamlSerializer> 類別的執行個體指派給 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> 屬性。 例如，需要使用自訂的安全性判斷提示標記語言 (Security Assertions Markup Language，SAML) 序列化程式來剖析自訂 SAML 時。  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>使用組態來設定 IssuedTokenServiceCredential 的屬性  
  
1.  建立`<issuedTokenAuthentication>`做為子元素 <`serviceCredentials`> 項目。  
  
2.  如果是要驗證類似 `allowUntrustedRsaIssuers` 卡的自行發行權杖，則將 `<issuedTokenAuthentication>` 項目的 `true` 屬性設定為 [!INCLUDE[infocard](../../../../includes/infocard-md.md)]。  
  
3.  建立 `<knownCertificates>` 項目做為 `<issuedTokenAuthentication>` 項目的子項。  
  
4.  建立零個或多個 `<add>` 項目做為 `<knownCertificates>` 項目的子項目，並使用 `storeLocation`, `storeName`、`x509FindType` 及 `findValue` 屬性來指定如何找到該憑證。  
  
5.  如有必要，設定`samlSerializer`屬性 <`issuedTokenAuthentication`> 項目類型名稱的自訂<xref:System.IdentityModel.Tokens.SamlSerializer>類別。  
  
## <a name="example"></a>範例  
 下列範例會示範使用程式碼來設定 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> 的屬性。  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 為了讓聯合服務驗證用戶端，下列有關已發行權杖的各項條件必須成立：  
  
-   當已發行權杖的數位簽章使用 RSA 安全性金鑰識別碼時，<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> 屬性必須是 `true`。  
  
-   當已發行權杖的簽章使用 X.509 簽發者序號、X.509 主體金鑰識別碼或 X.509 指紋安全性識別碼時，已發行權杖必須由 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> 類別之 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> 屬性所傳回集合中的憑證完成簽署。  
  
-   當已發行權杖使用 X.509 憑證完成簽署時，該憑證都必須根據 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> 屬性值所指定的語意進行驗證，無論該憑證是否當做 <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> 傳送到信賴憑證者或者是從 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> 屬性取得。 如需 X.509 憑證驗證的詳細資訊，請參閱[使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
 例如，將 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> 設定為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust>，便會對任何簽署憑證是位於 `TrustedPeople` 憑證存放區中的憑證進行驗證。 在此情況下，請將 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> 屬性設定為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> 或 <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>。 您可以選擇包括 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> 的其他模式。 若是選擇 `Custom`，您就必須將 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別的執行個體指派給 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> 屬性。 自訂驗證器可以使用其所偏好的任何準則來驗證憑證。 如需詳細資訊，請參閱[How to： 建立採用自訂憑證驗證程式服務](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。  
  
## <a name="see-also"></a>另請參閱  
 [同盟](../../../../docs/framework/wcf/feature-details/federation.md)  
 [同盟和信任](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 [同盟範例](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [如何：在 WSFederationHttpBinding 上停用安全工作階段](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [如何：建立 WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [如何：建立同盟用戶端](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [SecurityBindingElement 驗證模式](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
