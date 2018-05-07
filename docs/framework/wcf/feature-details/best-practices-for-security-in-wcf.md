---
title: WCF 中安全性的最佳做法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 62675bc5cca2eccfcd4f210f96e5eeec93341399
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-for-security-in-wcf"></a>WCF 中安全性的最佳做法
下列章節會列出建立安全的應用程式使用 Windows Communication Foundation (WCF) 時要考量的最佳作法。 如需有關安全性的詳細資訊，請參閱[安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)，[資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)，和[與中繼資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)。  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>利用 SPN 識別執行 Windows 驗證的服務  
 服務可以透過使用者主要名稱 (UPN) 或服務主要名稱 (SPN) 進行識別。 以如網路服務的電腦帳戶來執行的服務，都有一個對應於所執行電腦的 SPN 身分識別。 雖然 `setspn` 工具可用於指派 SPN 給使用者帳戶，但是以使用者帳戶執行的服務都有一個對應於所執行之使用者身分的 UPN 身分識別。 對服務進行設定，讓服務可以透過 SPN 識別，並且設定用戶端要連結到該服務，以使用該 SPN，才能確保服務不容易受到特定攻擊。 這個方法也適用於使用 Kerberos 或 SSPI 交涉的繫結。  在 SSPI 又改回使用 NTLM 的情況下，用戶端應該仍然能夠指定 SPN。  
  
## <a name="verify-service-identities-in-wsdl"></a>利用 WSDL 驗證服務身分識別  
 WS-SecurityPolicy 允許服務以中繼資料發佈關於本身身分識別的資訊。 透過擷取時`svcutil`或其他方法，例如<xref:System.ServiceModel.Description.WsdlImporter>，此身分識別資訊就會轉譯成 WCF 服務端點位址的識別屬性。 沒有驗證這些服務的用戶端屬於正確且有效的略過服務驗證。 但是，惡意的服務會利用這類用戶端，變更 WSDL 中聲稱的身分，執行認證轉送或其他的中間人攻擊。  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>使用 X509 憑證取代 NTLM  
 WCF 提供的對等驗證兩種機制： X509 憑證 （對等通道所使用） 和 Windows 驗證的 Kerberos SSPI 交涉降級為 NTLM 位置。  相較於 NTLM，使用 1024 位元以上的金鑰進行的憑證式驗證較為理想，因為：  
  
-   雙向驗證的可用性  
  
-   使用更強的密碼編譯演算法  
  
-   更不容易利用轉送的 X509 憑證  
  
 如需 NTLM 轉寄攻擊的概觀，請移至[ http://msdn.microsoft.com/msdnmag/issues/06/09/SecureByDesign/default.aspx ](http://go.microsoft.com/fwlink/?LinkId=109571)。  
  
## <a name="always-revert-after-impersonation"></a>在模擬完畢後一律還原  
 在使用可啟用用戶端模擬的 API 時，請務必還原成原始身分識別。 例如，當使用<xref:System.Security.Principal.WindowsIdentity>和<xref:System.Security.Principal.WindowsImpersonationContext>，使用 C#`using`陳述式或 Visual Basic`Using`陳述式，如下列程式碼所示。 <xref:System.Security.Principal.WindowsImpersonationContext> 類別會實作 <xref:System.IDisposable> 介面，因此 Common Language Runtime (CLR) 會在程式碼離開 `using` 區塊後，自動還原成原始身分識別。  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>只有必要時才模擬  
 透過 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> 類別的 <xref:System.Security.Principal.WindowsIdentity> 方法，您可以在嚴格控制的範圍內使用模擬。 這與使用 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> 的 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性剛好相反，後者允許對整個作業範圍進行模擬。 只要可能，任何時候都請您使用更精確的 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> 方法來控制模擬範圍。  
  
## <a name="obtain-metadata-from-trusted-sources"></a>取得來自信任來源的中繼資料  
 請務必信任您的中繼資料來源，並確認中繼資料未遭受任何竄改。 使用 HTTP 通訊協定擷取的中繼資料會以純文字傳送出去且可以竄改。 如果服務使用 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> 和 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> 屬性，請以服務建立者提供的 URL 來使用 HTTPS 通訊協定下載資料。  
  
## <a name="publish-metadata-using-security"></a>使用安全性發行中繼資料  
 若要預防服務的已發行中繼資料遭到竄改，請使用傳輸或訊息層級的安全性來保護中繼資料交換端點的安全。 如需詳細資訊，請參閱[發行中繼資料端點](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)和[How to： 服務使用程式碼發行中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)。  
  
## <a name="ensure-use-of-local-issuer"></a>確定本機簽發者的用途  
 如果已指定特定繫結的簽發者位址和繫結，這時使用該繫結的端點就不會使用該本機簽發者。 預期一定要使用該本機簽發者的用戶端應該要確定自己沒有使用這類繫結，否則它們就會修改繫結，進而使得簽發者位址成為 null。  
  
## <a name="saml-token-size-quotas"></a>SAML 權杖大小配額  
 當安全性判斷提示標記語言 SAML 權杖在訊息中序列化，不論這些權杖是由安全性權杖服務 (STS) 所核發，或者這些權杖由用戶端視為驗證的一部份提供至服務，最大訊息大小配額必須大到足以容納 SAML 權杖及其他訊息部份。 正常情況下，預設訊息大小配額應足夠。 然而，若 SAML 權杖因為包含數百個宣告而變很大時，您就需要增加配額以容納序列化的權杖。 如需有關配額的詳細資訊，請參閱[資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)。  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>在自訂繫結上，將 SecurityBindingElement.IncludeTimestamp 設定為 True  
 當您建立自訂繫結時，您必須將 <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> 設定為 `true`。 否則，如果 <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> 設定為 `false`，而且用戶端使用以非對稱金鑰為基礎的權杖 (如 X509 憑證)，則不會簽署訊息。  
  
## <a name="see-also"></a>另請參閱  
 [安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 [中繼資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
