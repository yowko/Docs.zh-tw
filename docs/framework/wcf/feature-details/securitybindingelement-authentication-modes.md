---
title: SecurityBindingElement 驗證模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 715c813015fdb4b52444efca0bdcfc99acc92c21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507752"
---
# <a name="securitybindingelement-authentication-modes"></a>SecurityBindingElement 驗證模式
Windows Communication Foundation (WCF) 提供數個用戶端和服務驗證彼此的模式。 您可以在 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別上使用靜態方法或透過組態，建立這些驗證模式的安全性繫結項目。 本主題會簡短說明這 18 種驗證模式。  
  
 使用的驗證模式的其中一個元素的範例，請參閱[How to： 指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)。  
  
## <a name="basic-configuration-programming"></a>基本組態程式設計  
 下列程序會說明如何使用組態檔來設定驗證模式。  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>使用組態來設定驗證模式  
  
1.  若要[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)項目，加入[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。  
  
2.  做為子項目，加入[\<繫結 >](../../../../docs/framework/misc/binding.md)元素`<customBinding>`項目。  
  
3.  將 `<security>` 項目加入至 `<binding>` 項目。  
  
4.  將 `authenticationMode` 屬性設定為下列其中一個描述值。 例如，下列程式碼會將此模式設定為 `AnonymousForCertificate`。  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>以程式設計方式來設定模式  
  
1.  判斷傳回型別，該型別可能是下列其中一種型別：<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>、<xref:System.ServiceModel.Channels.TransportSecurityBindingElement>、<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 或 <xref:System.ServiceModel.Channels.SecurityBindingElement>。  
  
2.  呼叫 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別的適當靜態方法。 例如，下列程式碼會呼叫 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> 方法。  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3.  使用繫結項目來建立自訂繫結。 如需詳細資訊，請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## <a name="mode-descriptions"></a>模式描述  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 在此驗證模式中，用戶端為匿名，而服務會使用 X.509 憑證來進行驗證。 安全性繫結項目是由 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A>。 或者，設定`authenticationMode`屬性 <`security`> 項目`AnonymousForCertificate`。  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 在此驗證模式中，用戶端為匿名，而服務會使用在執行階段交涉的 X.509 憑證來進行驗證。 如果為第一個參數傳遞的值是 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 時，安全性繫結項目就是由 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> 方法傳回的 `false`。 或者，可以將 `authenticationMode` 屬性設定為 `AnonymousForSslNegotiated`。  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 在此驗證模式中，用戶端會使用出現在 SOAP 層中當做簽署支援權杖 (也就是簽署訊息簽章的權杖) 的 X.509 憑證來進行驗證。 服務會在傳輸層上使用 X.509 憑證來進行驗證。 安全性繫結項目是由 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `CertificateOverTransport`。  
  
### <a name="issuedtoken"></a>IssuedToken  
 在此驗證模式中，用戶端本身不會向服務驗證，而是向安全性權杖服務驗證並接收 SAML 權杖，接著將該權杖呈現給伺服器，證明自己知道共用金鑰。 服務本身不會向用戶端驗證，但安全性權杖服務會將共用金鑰加密做為所發出權杖的一部分，這樣就只有服務才能解密該金鑰。 安全性繫結項目是由 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `IssuedToken`。  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 在此驗證模式中，用戶端本身不會向服務驗證，而是向安全性權杖服務驗證並接收 SAML 權杖，接著將該權杖呈現給伺服器，證明自己知道共用金鑰。 發出的權杖會當做簽署支援權杖或持有人權杖 (也就是簽署訊息簽章的權杖) 出現在 SOAP 層中。 服務會使用 X.509 憑證對用戶端進行驗證。 安全性繫結項目是由 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `IssuedTokenForCertificate`。  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 在此驗證模式中，用戶端本身不會向服務驗證，而是向安全性權杖服務驗證並接收 SAML 權杖，接著將該權杖呈現給伺服器，證明自己知道共用金鑰。 發出的權杖會當做簽署支援權杖或持有人權杖 (也就是簽署訊息簽章的權杖) 出現在 SOAP 層中。 服務會使用 X.509 憑證來進行驗證。 安全性繫結項目是由 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `IssuedTokenForSslnegotiated`。  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 在此驗證模式中，用戶端本身不會向服務驗證，而是向安全性權杖服務驗證並接收 SAML 權杖，接著將該權杖呈現給伺服器，證明自己知道共用金鑰。 發出的權杖會當做簽署支援權杖或持有人權杖 (也就是簽署訊息簽章的權杖) 出現在 SOAP 層中。 服務會在傳輸層上使用 X.509 憑證來進行驗證。 安全性繫結項目是由 `TransportSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `IssuedTokenOverTransport`。  
  
### <a name="kerberos"></a>Kerberos  
 在此驗證模式中，用戶端會使用 Kerberos 票證向服務進行驗證。 相同的票證也會提供伺服器驗證。 安全性繫結項目是由 `SymmetricSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `Kerberos`。  
  
> [!NOTE]
>  為了使用此驗證模式，服務帳戶必須與某個服務主要名稱 (SPN) 相關聯。 如果要這樣做，請以 NETWORK SERVICE 帳戶或 LOCAL SYSTEM 帳戶執行此服務。 或者，使用 SetSpn.exe 工具來建立服務帳戶的 SPN。 在任一情況下，用戶端必須使用正確的 SPN 中[ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md)項目，或使用<xref:System.ServiceModel.EndpointAddress>建構函式。 如需詳細資訊，請參閱[服務識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
> [!NOTE]
>  當使用 `Kerberos` 驗證模式時，就不會支援 <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> 與 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> 模擬等級。  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 在此驗證模式中，用戶端會使用 Kerberos 票證向服務進行驗證。 Kerberos 權杖會當做簽署支援權杖 (也就是簽署訊息簽章的權杖) 出現在 SOAP 層中。 服務會在傳輸層上使用 X.509 憑證來進行驗證。 安全性繫結項目是由 `TransportSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `KerberosOverTransport`。  
  
> [!NOTE]
>  為了使用此驗證模式，服務帳戶必須與某個 SPN 相關聯。 如果要這樣做，請以 NETWORK SERVICE 帳戶或 LOCAL SYSTEM 帳戶執行此服務。 或者，使用 SetSpn.exe 工具來建立服務帳戶的 SPN。 在任一情況下，用戶端必須使用正確的 SPN 中[ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md)項目，或使用<xref:System.ServiceModel.EndpointAddress>建構函式。 如需詳細資訊，請參閱[服務識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 在此驗證模式中，用戶端會使用出現在 SOAP 層中當做簽署支援權杖 (也就是簽署訊息簽章的權杖) 的 X.509 憑證來進行驗證。 服務也會使用 X.509 憑證來進行驗證。 安全性繫結項目是由 `SymmetricSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `MutualCertificate`。  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 在此驗證模式中，用戶端會使用出現在 SOAP 層中當做簽署支援權杖 (也就是簽署訊息簽章的權杖) 的 X.509 憑證來進行驗證。 服務也會使用 X.509 憑證來進行驗證。 繫結是由 `AsymmetricSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `MutualCertificateDuplex`。  
  
### <a name="mutalsslnegotiation"></a>MutalSslNegotiation  
 在此驗證模式中，用戶端和服務會使用 X.509 憑證來進行驗證。 如果為第一個參數傳遞的值是 `SymmetricSecurityBindingElement` 時，安全性繫結項目就是由 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> 方法傳回的 `true`。 或者，可以將 `authenticationMode` 屬性設定為 `MutualSslNegotiated`。  
  
### <a name="secureconversation"></a>SecureConversation  
 安全性繫結項目是由 `SymmetricSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>。 這個方法會將 <xref:System.ServiceModel.Channels.SecurityBindingElement> 當做參數接受，而該項目會在初始化期間用來建立安全工作階段。 或者，可以將 `authenticationMode` 屬性設定為 `SecureConversation`。  
  
 如果沒有指定啟動安裝繫結，便會為啟動安裝使用 `SspiNegotiated` 驗證模式。  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 在此驗證模式中，將使用交涉通訊協定來執行用戶端和伺服器驗證。 如果可能，便會使用 Kerberos，否則會使用 NT LanMan (NTLM)。 安全性繫結項目是由 `SymmetricSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `SspiNegotiated`。  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 在此驗證模式中，將使用交涉通訊協定來執行用戶端和伺服器驗證。 如果可能，便會使用 Kerberos 通訊協定，否則會使用 NTLM。 產生的權杖會當做簽署支援權杖 (也就是簽署訊息簽章的權杖) 出現在 SOAP 層中。 此外，服務也會在傳輸層上使用 X.509 憑證來進行驗證。 安全性繫結項目是由 `TransportSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `SspiNegotiatedOverTransport`。  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 在此驗證模式中，用戶端會使用當做簽署支援權杖 (也就是由訊息簽章簽署的權杖) 出現在 SOAP 層中的「使用者名稱權杖」向服務進行驗證。 服務會使用 X.509 憑證對用戶端進行驗證。 安全性繫結項目是由 `SymmetricSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `UserNameForCertificate`。  
  
 在 `UserNameForCertificate` 驗證模式中，用戶端與服務都必須使用 WS-Security 1.1。  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 在此驗證模式中，用戶端會使用當做簽署支援權杖 (也就是由訊息簽章簽署的權杖) 出現在 SOAP 層中的「使用者名稱權杖」進行驗證。 服務會使用 X.509 憑證來進行驗證。 安全性繫結項目是由 `SymmetricSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `UserNameForSslNegotiated`。  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 在此驗證模式中，用戶端會使用當做簽署支援權杖 (也就是由訊息簽章簽署的權杖) 出現在 SOAP 層中的「使用者名稱權杖」進行驗證。 服務會在傳輸層上使用 X.509 憑證來進行驗證。 安全性繫結項目是由 `TransportSecurityBindingElement` 方法傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A>。 或者，可以將 `authenticationMode` 屬性設定為 `UserNameOverTransport`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 [如何：為指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
