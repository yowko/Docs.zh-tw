---
title: 安全性例外狀況
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 057d01ba918a41df0bdf2acc30c9bb35777ebc27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="security-exceptions"></a>安全性例外狀況
本主題會列出所有安全性例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|AnonymousLogonsAreNotAllowed|服務不允許您匿名登入。|  
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|要求訊息必須加以保護。 這是指定之合約作業的要求。 保護必須由指定的繫結提供。|  
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|回應訊息必須加以保護。 這是指定之合約作業的要求。 保護必須由指定的繫結提供。|  
|AtMostOnePrimarySignatureInReceiveSecurityHeader|安全性標頭只允許一個主要簽章。|  
|BadContextTokenFaultReason|安全性內容權杖已過期或無效。 訊息尚未處理。|  
|BadEncryptionState|此作業的 EncryptedData 或 EncryptedKey 處於無效狀態。|  
|BasicHttpMessageSecurityRequiresCertificate|BasicHttp 繫結要求安全訊息的 BasicHttpBinding.Security.Message.ClientCredentialType 與 BasicHttpMessageCredentialType.Certificate 認證類型必須相等。 請為 UserName 認證選取 Transport 或 TransportWithMessageCredential 安全性。|  
|BasicTokenCannotBeWrittenWithoutEncryption|寫入基礎權杖時必須加密。|  
|BindingDoesNotSupportProtectionForRst|指定之合約的指定繫結已設為 SecureConversation，但是驗證模式尚無法提供交涉時所需的要求/回覆式的完整性與機密性。|  
|BindingDoesNotSupportWindowsIdenityForImpersonation|指定的合約作業需要 Windows 身分識別來進行自動模擬。 指定之合約的指定繫結不會提供代表呼叫者的 Windows 身分識別。|  
|CachedNegotiationStateQuotaReached|由於已達到指定的容量，因此服務無法快取交涉狀態。 請重試要求。|  
|CacheQuotaReached|無法新增此項目。 已指定最大快取大小。|  
|CannotDetermineSPNBasedOnAddress|用戶端無法根據指定之目標位址中的身分識別判斷服務主要名稱，以用於 SspiNegotiation/Kerberos。 目標位址身分識別必須是 UPN 身分識別 (像是 acmedomain\\\alice) 或 SPN 身分識別 （像是主機/bobs-machine)。|  
|CannotFindCert|使用指定的搜尋條件 StoreName、StoreLocation、FindType、FindValue 時，找不到 X.509 憑證。|  
|CannotFindCertForTarget|針對指定的目標使用指定的搜尋條件 StoreName、StoreLocation、FindType、FindValue 時，找不到 X.509 憑證。|  
|CannotFindCorrelationStateForApplyingSecurity|找不到將安全性套用至回應程式之回覆的交互關聯狀態。|  
|CannotFindNegotiationState|找不到指定之內容的交涉狀態。|  
|CannotFindSecuritySession|找不到指定之 ID 的安全性工作階段。|  
|CannotImportProtectionLevelForContract|用來匯入處理序的原則無法為指定的合約匯入繫結。 繫結的保護需求與已為合約匯入的繫結不相容。 您必須重新設定繫結。|  
|CannotImportSupportingTokensForOperationWithoutRequestAction|安全性原則匯入失敗。 安全性原則包含作業範圍內的支援權杖需求。 合約描述未指定與此作業關聯之要求訊息的動作。|  
|CannotIssueRstTokenType|無法發行權杖或指定的類型。|  
|CannotObtainIssuedTokenKeySize|無法判斷已發行之權杖的金鑰大小。|  
|CannotPerformImpersonationOnUsernameToken|無法使用用戶端權杖進行模擬。 指定之合約的指定繫結會以使用者名稱安全性權杖，向登錄的成員資格提供者進行用戶端驗證。 請在用戶端使用不同類型的安全性權杖。|  
|CannotPerformS4UImpersonationOnPlatform|指定之合約的指定繫結僅支援在 [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] 與較新版的 Windows 上進行模擬。 請在啟用取消的安全交談中，使用 SspiNegotiated 驗證與繫結。|  
|CannotReadKeyIdentifier|無法從具有指定之命名空間的指定項目中讀取 KeyIdentifier。|  
|CannotReadToken|無法從具有指定之 BinarySecretSecurityToken 命名空間與指定之 ValueType 的指定項目中讀取權杖。 若此項目應該要有效，請確認將安全性設定為使用具有該指定名稱、命名空間及值類型的權杖。|  
|CertificateUnsupportedForHttpTransportCredentialOnly|TransportCredentialOnly 安全性模式不支援以憑證為基礎的用戶端驗證。 請選取 Transport 安全性模式。|  
|ClaimTypeCannotBeEmpty|claimType 不能是空字串。|  
|ClientCertificateNotProvided|尚未提供用戶端憑證。 憑證可以在 ClientCredentials 或 ServiceCredentials 上設定。|  
|ClientCredentialTypeMustBeSpecifiedForMixedMode|ClientCredentialType.None 對於 TransportWithMessageCredential 安全性模式無效。 請指定認證類型或使用不同的安全性模式。|  
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|組態結構描述不足，無法描述下列安全性繫結項目的非標準組態：|  
|DerivedKeyTokenGenerationAndLengthTooHigh|衍生金鑰的指定層代與長度所導致的金鑰衍生偏差，大於允許的偏差上限。|  
|DnsIdentityCheckFailedForIncomingMessage|傳入訊息的身分識別檢查失敗。 已指定預期的遠端端點網域名稱系統 (DNS) 身分識別。 遠端端點已提供指定的網域名稱系統 (DNS) 宣告。 如果這是合法的遠端端點，只要在建立通道 Proxy 時，明確指定網域名稱系統身分識別做為 EndpointAddress 的身分識別屬性，即可解決此問題。|  
|DnsIdentityCheckFailedForOutgoingMessage|傳出訊息的身分識別檢查失敗。遠端端點應該具備指定的網域名稱系統身分識別。 遠端端點已提供網域名稱系統 (DNS) 宣告。 如果這是合法的遠端端點，只要在建立通道 Proxy 時，明確指定 DNS 身分識別做為 EndpointAddress 的 Identity 屬性，即可解決此問題。|  
|DuplicateIdInMessageToBeVerified|提供用於驗證的訊息中出現兩次指定的識別碼。|  
|EmptyBase64Attribute|在必要的 Base-64 屬性名稱與命名空間中找到空值。|  
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|安全性原則匯出失敗。 繫結包含 AsymmetricSecurityBindingElement 與安全傳輸繫結項目。 不支援此類繫結的原則匯出。|  
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|安全性原則匯出失敗。 繫結包含 SymmetricSecurityBindingElement 與安全傳輸繫結項目。 不支援此類繫結的原則匯出。|  
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|安全性原則匯出失敗。 繫結包含 TransportSecurityBindingElement，但是不包含可實作 ITransportTokenAssertionProvider 的傳輸繫結項目。 不支援此類繫結的原則匯出。 請確定繫結中的傳輸繫結項目可實作 ITransportTokenAssertionProvider 介面。|  
|FoundMultipleCerts|使用指定的搜尋條件 StoreName、StoreLocation、FindType、FindValue 時，找到多個 X.509 憑證。 請提供更精確的尋找值。|  
|FoundMultipleCertsForTarget|針對指定的目標使用指定的搜尋條件 StoreName、StoreLocation、FindType、FindValue 時，找到多個 X.509 憑證。 請提供更精確的尋找值。|  
|HeaderDecryptionNotSupportedInWsSecurityJan2004|SecurityVersion.WSSecurityJan2004 不支援標頭解密。 請使用 SecurityVersion.WsSecurityXXX2005 與更新版本或使用傳輸安全性來加密完整訊息。|  
|IdentityCheckFailedForIncomingMessage|傳入訊息的身分識別檢查失敗。 已指定目標端點的預期身分識別。|  
|IdentityCheckFailedForOutgoingMessage|傳出訊息的身分識別檢查失敗。 已指定目標端點的預期身分識別。|  
|IncorrectSpnOrUpnSpecified|安全性支援提供者介面 (SSPI) 驗證失敗。 伺服器可能無法以指定之身分識別的帳戶來執行。 若伺服器是以服務帳戶 (例如網路服務) 執行，請指定帳戶的 ServicePrincipalName 做為 EndpointAddress 中伺服器的身分識別。 若伺服器是以使用者帳戶執行，請指定帳戶的 UserPrincipalName 做為 EndpointAddress 中伺服器的身分識別。|  
|InvalidAttributeInSignedHeader|指定的簽署標頭包含指定的屬性。 已指定預期的屬性。|  
|InvalidCloseResponseAction|收到含有指定之無效動作的安全性工作階段關閉回應。|  
|InvalidQName|QName 無效。|  
|InvalidRenewResponseAction|收到含有指定之無效動作的安全性工作階段更新回應。|  
|InvalidSspiNegotiation|安全性支援提供者介面交涉失敗。|  
|IssuerBindingNotPresentInTokenRequirement|安全性權杖管理員要求在描述安全對話的權杖需求中，指定啟動安裝安全性繫結項目。 下列為指定的權杖需求。|  
|KeyLengthMustBeMultipleOfEight|對稱式金鑰的指定金鑰長度不是 8 的倍數。|  
|LsaAuthorityNotContacted|內部 SSL 錯誤 (如需詳細資訊，請參閱 Win32 狀態碼)。 請檢查伺服器憑證，判斷是否能進行金鑰交換。|  
|MaximumPolicyRedirectionsExceeded|已達遞迴原則擷取限制。 請檢查聯合服務鏈中是否有迴圈。|  
|MessagePartSpecificationMustBeImmutable|訊息部分規格在設定前必須保持不變。|  
|MissingCustomCertificateValidator|X509CertificateValidationMode.Custom 需要 CustomCertificateValidator。 請指定 CustomCertificateValidator 屬性。|  
|MissingCustomUserNamePasswordValidator|UserNamePasswordValidationMode.Custom 需要 CustomUserNamePasswordValidator。 請指定 CustomUserNamePasswordValidator 屬性。|  
|MissingMembershipProvider|UserNamePasswordValidationMode.MembershipProvider 需要 MembershipProvider。 請指定 MembershipProvider 屬性。|  
|NoBinaryNegoToSend|未傳送二進位交涉給另一方。|  
|NoEncryptionPartsSpecified|具有指定之動作的訊息未指定加密訊息部分。|  
|NoKeyInfoInEncryptedItemToFindDecryptingToken|加密項目中找不到 KeyInfo 值，因此找不到解密權杖。|  
|NonceLengthTooShort|指定的 Nonce 太短。 所需的最短 Nonce 長度是 4 個位元組。|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|沒有可用的傳出 EndpointAddress，無法檢查要傳送之訊息的身分識別。|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|沒有可用的傳出 EndpointAddress，無法檢查收到之回覆的身分識別。|  
|NoPartsOfMessageMatchedPartsToSign|未建立簽章，因為訊息中沒有任何部分符合所提供的訊息部分規格。|  
|NoPrincipalSpecifiedInAuthorizationContext|授權內容中未指定自訂原則。|  
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|安全性標頭中沒有可用的簽章，無法提供重新執行偵測的 Nonce。|  
|NoSignaturePartsSpecified|具有指定之動作的訊息未指定簽章訊息部分。|  
|NoSigningTokenAvailableToDoIncomingIdentityCheck|沒有可用的簽章權杖，無法執行傳入身分識別檢查。|  
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|安全性標頭中沒有可用的時間戳記，無法進行重新執行偵測。|  
|NoTransportTokenAssertionProvided|安全性原則專家失敗。 提供的指定類型傳輸權杖判斷提示未建立要包含 sp:TransportBinding 安全性原則判斷提示的傳輸權杖判斷提示。|  
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|設定對稱式安全性通訊協定時，可設定對稱式權杖提供者和對稱式權杖驗證者，或非對稱式權杖提供者。 但是不可同時設定兩者。|  
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|無法在接收者安全性標頭上執行此作業。|  
|OperationDoesNotAllowImpersonation|屬於包含指定之名稱與命名空間的合約之指定服務作業不允許模擬。|  
|PolicyRequiresConfidentialityWithoutIntegrity|指定之動作的訊息安全性原則要求不具完整性的機密性。 不支援不具完整性的機密性。|  
|PrimarySignatureIsRequiredToBeEncrypted|主要簽章必須加密。|  
|PropertySettingErrorOnProtocolFactory|指定的安全性通訊協定處理站上的必要屬性未設定，或是具有無效值。|  
|ProtocolFactoryCouldNotCreateProtocol|通訊協定處理站無法建立通訊協定。|  
|PublicKeyNotRSA|公開金鑰不是 RSA 金鑰。|  
|RequiredMessagePartNotEncrypted|指定的必要訊息部分尚未加密。|  
|RequiredMessagePartNotEncryptedNs|指定的必要訊息部分尚未加密。|  
|RequiredMessagePartNotSigned|指定的必要訊息部分尚未簽署。|  
|RequiredMessagePartNotSignedNs|指定的必要訊息部分尚未簽署。|  
|RequiredSecurityHeaderElementNotSigned|包含指定之識別碼的指定安全性標頭項目必須經過簽署。|  
|RequiredSecurityTokenNotEncrypted|包含指定之附件模式的指定安全性權杖必須加密。|  
|RequiredSecurityTokenNotSigned|包含指定之附件模式的指定安全性權杖必須簽署。|  
|RequiredSignatureMissing|簽章必須位於安全性標頭中。|  
|RequireNonCookieMode|已設定具有指定之命名空間的指定繫結來發行 Cookie 安全性內容權杖。 COM+ Integration 服務不支援 Cookie 安全性內容權杖。|  
|RevertingPrivilegeFailed|還原作業失敗，發生指定的例外狀況。|  
|RSTRAuthenticatorIncorrect|RequestSecurityTokenResponse CombinedHash 不正確。|  
|SecureConversationCancelNotAllowedFaultReason|繫結不允許安全對話取消。|  
|SecureConversationDriverVersionDoesNotSupportSession|設定的 SecureConversation 版本不支援工作階段。 請使用 WSSecureConversationFeb2005 或更新的版本。|  
|SecureConversationRequiredByReliableSession|無法建立不包含安全對話的可靠工作階段。 啟用安全對話。|  
|SecurityAuditFailToLoadDll|指定的動態連結程式庫 (dll) 無法載入。|  
|SecurityAuditNotSupportedOnChannelFactory|通道處理站不支援 SecurityAuditBehavior。|  
|SecurityAuditPlatformNotSupported|目前的平台不支援將稽核訊息寫入安全性記錄檔。 您必須將稽核訊息寫入應用程式記錄檔。|  
|SecurityBindingElementCannotBeExpressedInConfig|已為端點匯入安全性原則。 安全性原則包含無法在 Windows Communication Foundation 組態中表示的需求。 請查看產生的組態檔中所需之 SecurityBindingElement 參數的註解。 請使用程式碼建立正確的繫結項目。 組態檔中的繫結組態不安全。|  
|SecurityBindingSupportsOneWayOnly|所指定合約之指定繫結的 SecurityBinding 僅支援 OneWay 作業。|  
|SecurityContextDoesNotAllowImpersonation|由於來自具有所指定動作之要求訊息的 UltimateReceiver 角色的 SecurityContext 無法對應 Windows 身分識別，因此無法啟動模擬。|  
|SecurityListenerClosing|接聽項正在關閉，無法接受新安全對話。|  
|SecurityListenerClosingFaultReason|伺服器正在關閉，目前無法接受新安全對話。 請稍後再試。|  
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|必須先設定安全性通訊協定處理站，才能執行此作業。|  
|SecuritySessionAbortedFaultReason|安全性工作階段已終止。 可能是因為工作階段很久未收到訊息。|  
|SecuritySessionKeyIsStale|必須更新工作階段金鑰，才能保護應用程式訊息。|  
|SecuritySessionLimitReached|無法建立安全性工作階段。 請稍後再試。|  
|SecuritySessionNotPending|沒有任何具有指定之識別碼的安全性工作階段處於擱置中狀態。|  
|SecurityTokenParametersHasIncompatibleInclusionMode|指定之繫結中設定的安全性權杖參數具有指定之不相容的安全性權杖內含模式。 請指定替代的安全性權杖內含模式。|  
|SecurityVersionDoesNotSupportEncryptedKeyBinding|指定之合約的指定繫結中設定了不相容的安全性版本，該版本不支援未附加的 EncryptedKeys 參照。 請使用指定值或更新的值做為繫結的安全性版本。|  
|SecurityVersionDoesNotSupportSignatureConfirmation|指定的 SecurityVersion 不支援簽章確認。 請使用更新的 SecurityVersion。|  
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|指定之合約的指定繫結中設定了安全性版本，該版本不支援使用憑證指紋值的 X.509 權杖外部參照。 請使用指定值或更新的值做為繫結的安全性版本。|  
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|每一訊息均必須設定安全性權杖參數及支援權杖。|  
|ServerCertificateNotProvided|收件者未提供憑證。 TLS 通訊協定需要此憑證。 雙方必須能夠存取自己的憑證。|  
|SignatureConfirmationNotSupported|設定的 SecurityVersion 不支援簽章確認。 請使用 WSSecurityXXX2005 或更新版本。|  
|SignatureConfirmationRequiresRequestReply|通訊協定處理站必須支援要求/回覆安全性，才能提供簽章確認。|  
|SignatureNotExpected|此訊息不應該有簽章。|  
|SigningTokenHasNoKeys|指定的簽署權杖不包含金鑰。 安全性權杖使用時需要執行密碼編譯作業，但是權杖未包含密碼編譯金鑰。 可能是權杖類型未支援加密作業，或是特定權杖例項未包含加密金鑰。 請檢查組態，確認在需要密碼編譯作業時 (例如，簽署支援權杖)，未指定停用密碼編譯的權杖類型 (例如，UserNameSecurityToken)。|  
|SpnegoImpersonationLevelCannotBeSetToNone|安全性支援提供者介面不支援模擬層級「無」。 請指定「身分識別」、「模擬」或「委派」層級。|  
|SslClientCertMustHavePrivateKey|指定的憑證必須包含私密金鑰。 處理序必須擁有私密金鑰的存取權限。|  
|SslServerCertMustDoKeyExchange|指定的憑證必須有能夠進行金鑰交換的私密金鑰。 處理序必須擁有私密金鑰的存取權限。|  
|StandardsManagerCannotWriteObject|權杖序列化程式無法序列化指定的物件。  如果這是自訂類型，您就必須提供自訂序列化程式。|  
|TimeStampHasCreationAheadOfExpiry|因為安全性時間戳記的建立時間大於或等於到期時間，所以安全性時間戳記無效。|  
|TimeStampHasCreationTimeInFuture|因為安全性時間戳記的建立時間在未來，所以安全性時間戳記無效。 已指定目前時間，且指定了允許的時鐘誤差。|  
|TimeStampHasExpiryTimeInPast|因為安全性時間戳記的過期時間在過去，所以安全性時間戳記已過時。 已指定目前時間，且指定了允許的時鐘誤差。|  
|TimeStampWasCreatedTooLongAgo|因為安全性時間戳記的建立時間過時甚久，所以安全性時間戳記已過時。 已指定目前時間、時間戳記存留期上限，以及允許的時鐘誤差。|  
|TokenProviderCannotGetTokensForTarget|權杖提供者無法為指定目標取得權杖。|  
|TooManyIssuedSecurityTokenParameters|聯合安全性鏈結階段包含多個 IssuedSecurityTokenParameters。 InfoCard 系統每個階段只支援一個 IssuedSecurityTokenParameters。|  
|TransportDoesNotProtectMessage|用來設定指定合約之指定繫結的驗證模式，需要傳輸層級的完整性及機密性。 不過傳輸無法提供完整性及機密性。|  
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 不支援發行 X.509 憑證或 EncryptedKeys。 請使用 WsTrustFeb2005 或更新版本。|  
|TrustDriverVersionDoesNotSupportSession|設定的 Trust 版本不支援工作階段。 請使用 WSTrustFeb2005 或更新版本。|  
|UnableToCreateICryptoFromTokenForSignatureVerification|無法從指定權杖建立用於簽章驗證的 ICrypto 介面。|  
|UnableToCreateSymmetricAlgorithmFromToken|無法從權杖建立指定的對稱式演算法。|  
|UnableToDeriveKeyFromKeyInfoClause|指定的 KeyInfo 子句已解析至指定的權杖，但不包含可用於衍生的對稱式金鑰。|  
|UnableToFindTokenAuthenticator|找不到指定之權杖類型的權杖驗證器。 根據目前的安全性設定，無法接受該類型的權杖。|  
|UnableToLoadCertificateIdentity|無法載入組態中指定的 X.509 憑證身分識別。|  
|UnexpectedEmptyElementExpectingClaim|指定之命名空間的指定項目是空的，且未指定有效的身分識別宣告。|  
|UnknownEncodingInBinarySecurityToken|讀取二進位安全性權杖時發生無法辨識的編碼。|  
|UnsecuredMessageFaultReceived|從另一方接收了不安全的錯誤。 如需錯誤碼及詳細資料，請參閱內部 FaultException。|  
|UnsupportedPasswordType|指定的使用者名稱權杖具有不支援的密碼類型。|  
|UnsupportedSecureConversationBootstrapProtectionRequirements|無法匯入安全性原則。 不支援安全交談啟動載入器繫結程序的保護需求。 安全交談啟動載入器繫結程序的保護需求強調要求及回應都必須簽署並加密。|  
|UnsupportedSecurityPolicyAssertion|指定的安全性原則匯入期間，偵測到不支援的安全性原則判斷提示。|
