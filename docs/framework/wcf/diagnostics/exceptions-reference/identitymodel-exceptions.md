---
title: "IdentityModel 例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f38d09ef9b1ee2e620b42082a05c6832eec7c746
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="identitymodel-exceptions"></a>IdentityModel 例外狀況
本主題會列出由 IdentityModel 產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|目前的字串|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|此引數的值必須是這兩種類型的其中一種。|  
|SAMLSubjectNameIdentifierRequiresNameValue|為 SamlNameIdentifier 指定的 'Name' 不可以是 Null 或是長度為 0。|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|IssuanceTokenProvider 已經完成安全性交涉。|  
|TraceCodeSecurityNewServerSessionKeyIssued|伺服器已發出新的安全性工作階段金鑰。|  
|SAMLAttributeMissingNameAttributeOnRead|為 SamlAttribute 所讀取的 'Name' 遺失或是長度為 0。|  
|UnknownICryptoType|不支援 ICrypto 實作。|  
|TraceCodeSecurityTokenProviderClosed|安全性權杖提供者已關閉。|  
|SAMLUnableToLoadAdvice|無法載入\<saml:advice > 項目。|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|為 SamlAuthenticationStatement 所讀取的 'AuthenticationMethod' 屬性遺失或是長度為 0。|  
|UnsupportedTransformAlgorithm|不支援的轉換或標準化演算法。|  
|SAMLAudienceRestrictionShouldHaveOneAudience|SamlAudienceRestrictionCondition 至少必須包含一個 Audience (URI)。|  
|SAMLEvidenceShouldHaveOneAssertion|SamlEvidence 至少必須參照一個 SamlAssertion (根據識別碼或參考)。|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|所讀取的 SamlAudienceRestrictionCondition 缺少 'Audience' 項目的值。|  
|X509ChainBuildFail|指定的 X.509 憑證鏈結建立失敗。 使用的憑證擁有無法驗證的信賴鏈結。 請取代憑證或變更 certificateValidationMode。|  
|XDCannotFindValueInDictionaryString|在字典字串中找不到指定的值識別碼。|  
|TraceCodeImportSecurityChannelBindingEntry|啟動安全性 ImportChannelBinding。|  
|PrivateKeyExchangeNotSupported|私密金鑰不支援交換 KeySpec。|  
|TokenProviderUnableToGetToken|指定的權杖提供者無法提供安全性權杖。|  
|SAMLEntityCannotBeNullOrEmpty|指定的 SamlAssertion 實體不可以是 Null 或空白。|  
|SAMLAssertionRequireOneStatement|SamlAssertion 至少需要一個陳述式。 請確定已經在您建立的 SamlAssertion 中至少新增了一個 SamlStatement。|  
|AESInvalidInputBlockSize|輸入大小必須是特定位元組的倍數。|  
|AESCryptAcquireContextFailed|無法取得 CSP 內容。|  
|SAMLAssertionRequireOneStatementOnRead|所讀取的 SamlAssertion 未包含任何 SamlStatement。 SamlAssertion 至少必須包含一個 SamlStatement。|  
|TraceCodeSecuritySessionClosedFaultReceived|用戶端安全性工作階段已從伺服器接收工作階段已關閉的錯誤。|  
|TraceCodeIssuanceTokenProviderRedirectApplied|IssuanceTokenProvider 已套用重新導向標頭。|  
|TraceCodeSecuritySessionClosedFaultSendFailure|將安全性工作階段已關閉的錯誤傳送到用戶端時失敗。|  
|ValueMustBeZero|這個引數的值必須是 0。|  
|SAMLUnableToResolveSignatureKey|無法解析在 SamlAssertion 簽章中找到的 SecurityKeyIdentifier。 無法驗證特定簽發者的 SamlAssertion 簽章。|  
|X509IsNotInTrustedStore|特定的 X.509 憑證不是位於受信任人的存放區。|  
|SAMLElementNotRecognized|不支援特定的項目。|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|所讀取的 SamlAuthorizationDecisionStatement 之 'Resource' 屬性遺失或是長度為 0。|  
|SamlTokenMissingSignature|未簽署 SamlAssertion。 設定 SigningCredentials 即可簽署 SamlAssertions。|  
|ExpectedElementMissing|遺失具有特定命名空間的必要項目。|  
|NoKeyIdentifierClauseFound|在 SecurityKeyIdentifier 中找不到特定類型的子句。|  
|MissingPrivateKey|X.509 憑證中沒有私密金鑰。|  
|UnexpectedEOFFromReader|來自 XML 讀取器的意外 EOF。|  
|UnsupportedKeyDerivationAlgorithm|不支援特定的金鑰衍生演算法。|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|特定權杖不支援建立特定的金鑰識別碼子句。|  
|LastMessageNumberExceeded|已偵測到序號通訊協定違規。|  
|SymmetricKeyLengthTooShort|所指定的對稱金鑰長度太短。|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|遺漏所讀取之 SamlAuthorityBinding 包含的 'AuthorityKind' 或是長度為 0。  這是不允許的。|  
|XmlTokenBufferIsEmpty|XmlTokenBuffer 是空的。|  
|InvalidXmlQualifiedName|需要 Xml 限定名稱，但找到無效的名稱。|  
|SAMLAuthorityKindMissingName|在 SamlAuthorityBinding 中，代表 'AuthorityKind' 的 XmlQualifiedName 不可以是 Null 或是長度為 0。|  
|AESCryptEncryptFailed|無法加密特定的資料。|  
|AuthorizationContextCreated|已建立具有特定識別碼的授權內容。|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|SamlSerializer 不包含能夠讀取 SecurityKeyIdentifier 的 SecurityTokenSerializer。 如果您使用自訂的 SecurityKeyIdentifier，則必須提供自訂的 SecurityTokenSerializer。|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|IssuanceTokenProvider 已減少服務權杖快取。|  
|TraceCodeSecurityTokenProviderOpened|安全性權杖提供者已開啟。|  
|PublicKeyNotRSA|公開金鑰不是 RSA 金鑰。|  
|InvalidReaderState|所提供之輸入讀取器的特定狀態無效。|  
|UnableToResolveReferenceUriForSignature|無法解析簽章中特定的 URI 來計算摘要。|  
|EmptyBase64Attribute|在必要的 Base64 屬性名稱和命名空間找到空值。|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|指定了 Confirmation Data 或 KeyInfo 時，SAML SubjectConfirmation 就需要 Confirmation 方法。|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|所讀取的 SamlAudienceRestrictionCondition 至少必須包含一個 'Audience' 值。 找不到任何值。|  
|TokenProviderUnableToRenewToken|特定的權杖提供者無法更新安全性權杖。|  
|AESIVLengthNotSupported|不支援特定的 bits IV。 只支援 128 bits IV。|  
|SAMLAuthorityBindingMissingAuthorityKind|SamlAuthorityBinding 必須包含不是 Null 的 'AuthorityKind'。|  
|TraceCodeSecuritySessionDemuxFailure|傳入訊息不是現有安全性工作階段的一部分。|  
|TokenRenewalNotSupported|特定的權杖提供者不支援更新權杖。|  
|AtLeastOneReferenceRequired|簽章中至少需要一個參考。|  
|SAMLSignatureAlreadyRead|已經在 SAML 判斷提示中讀取簽章。|  
|AlgorithmAndPrivateKeyMisMatch|指定的演算法與私密金鑰不相符。|  
|EmptyTransformChainNotSupported|不支援空白轉換鏈結。|  
|SspiWrapperEncryptDecryptAssert1|Sspiwrapper:: Encryptdecrypthelper &#124;'offset' 超出範圍。|  
|SspiWrapperEncryptDecryptAssert2|Sspiwrapper:: Encryptdecrypthelper &#124;'大小 ' 超出範圍。 SecurityTokenManagerCannotCreateAuthenticatorForRequirement=安全性權杖管理員無法針對特定需求建立權杖驗證器。|  
|UnableToCreateKeyedHashAlgorithm|無法從特定的值針對特定的簽章演算法建立 KeyedHashAlgorithm。|  
|SAMLUnableToLoadAssertion|\<Saml:assertion > 無法載入項目。|  
|X509FindValueMismatchMulti|特定的 X509FindType 要求 findValue 引數型別必須是兩個值的其中一個值。 引數 findValue 是另一個類型。|  
|TraceCodeSecurityIdentityDeterminationSuccess|已確定 EndpointAddress 的身分識別。|  
|UndefinedUseOfPrefixAtElement|在項目使用的特定前置詞尚未定義命名空間。|  
|TraceCodeSecuritySessionResponderOperationFailure|伺服器的安全性工作階段作業失敗。|  
|CannotFindCert|使用下列特定的搜尋條件找不到 X.509 憑證：StoreName、StoreLocation、FindType、FindValue。|  
|X509InvalidUsageTime|特定的 X.509 憑證使用時間無效。 使用時間不是介於必要的 NotBefore 時間與 NotAfter 時間之間。|  
|TraceCodeSecurityIdentityDeterminationFailure|無法判斷 EndpointAddress 的身分識別。|  
|AsyncObjectAlreadyEnded|已對這個非同步結果物件呼叫 End 方法。|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|外部字典未包含所有必要字串的定義。 遠端字典沒有提供特定的字串。|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|用戶端安全性工作階段從伺服器收到金鑰更新錯誤。|  
|SAMLActionNameRequired|代表 SamlAction 的字串不可以是 Null 或是長度為 0。|  
|SignatureVerificationFailed|簽章驗證失敗。|  
|TraceCodeSecurityContextTokenCacheFull|SecurityContextSecurityToken 快取已滿。|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|所讀取的 SamlAssertion 遺失 MajorVersion 或其長度為 0。|  
|SamlAttributeClaimRightShouldBePossessProperty|這個 SamlAttribute 建構函式要求宣告權利的值必須是 System.IdentityModel.Claims.Rights.PossessProperty。|  
|AuthorizationPolicyEvaluated|已評估具有特定識別碼的原則。|  
|SAMLUnableToLoadCondtions|\<Saml:conditions > 無法載入項目。|  
|AESKeyLengthNotSupported|不支援指定的 bits Key。 只支援 128、192 和 256 bits Key。|  
|UserNameCannotBeEmpty|使用者名稱不可以空白。|  
|AlgorithmAndPublicKeyMisMatch|指定的演算法與公開金鑰不相符。|  
|SAMLUnableToLoadCondtion|\<Saml:conditions > 無法載入項目。|  
|SamlAssertionMissingSigningCredentials|尚未對 SamlAssertion 設定 SigningCredentials。 SamlAssertions 必須簽署，請對 SamlAssertion 設定有效的 SigningCredentials，才能繼續進行。|  
|SspiPayloadNotEncrypted|二進位資料未以 SSPI 安全性內容加密。|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|所讀取的 SamlAuthorizationDecisionStatement 未包含任何 SamlAction。|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|安全性通訊協定無法確保傳出訊息的安全。|  
|UndefinedUseOfPrefixAtAttribute|使用於特定屬性的特定前置詞尚未定義命名空間。|  
|NoInputIsSetForCanonicalization|未設定輸入，無法撰寫標準化輸出。|  
|TraceCodeSecurityPendingServerSessionAdded|擱置中的安全性工作階段已新增至伺服器。|  
|AsyncCallbackException|AsyncCallback 擲回例外狀況。|  
|PrivateKeyNotRSA|私密金鑰不是 RSA 金鑰。|  
|TraceCodeSecurityClientSessionKeyRenewed|用戶端安全性工作階段已更新工作階段金鑰。|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|所讀取的 SamlAuthorizationDecisionStatement 之 'Decision' 遺失或是長度為 0。|  
|SAMLAttributeNameAttributeRequired|為 SamlAttribute 指定的 'Name' 不可以是 Null 或是長度為 0。|  
|SamlSerializerRequiresExternalSerializers|SamlSerializer 要求 SecurityTokenSerializer 將權杖中現有的 SecurityKeyIdentifier 序列化。|  
|UnableToResolveKeyReference|權杖解析程式無法解析特定的安全性金鑰參考。|  
|UnsupportedKeyWrapAlgorithm|不支援特定的金鑰包裝演算法。|  
|SAMLAssertionMissingIssuerAttributeOnRead|所讀取的 SamlAssertion 遺失 'Issuer' 或其長度為 0。|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|IssuanceTokenProvider 已使用快取的服務權杖。|  
|AESCryptGetKeyParamFailed|無法取得特定的金鑰參數。|  
|InvalidNamespaceForEmptyPrefix|空白前置詞的命名空間無效。|  
|AESCipherModeNotSupported|不支援特定的加密模式。 只支援 CBC。|  
|ArgumentCannotBeEmptyString|引數必須是非空字串。|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|所讀取的 SamlAssertion 遺失 MinorVersion 或其長度為 0。|  
|SpecifiedStringNotAvailableInDictionary|指定的字串不是目前字典內的項目。|  
|KerberosApReqInvalidOrOutOfMemory|AP-REQ 無效，或系統記憶體不足。|  
|FailLogonUser|指定之使用者的 LogonUser 失敗。 請確定使用者的 Windows 帳戶是正確的。|  
|ValueMustBeNonNegative|此引數值必須是非負數。|  
|X509ValidationFail|指定的 X.509 憑證驗證失敗。|  
|TraceCodeSecuritySessionRequestorOperationSuccess|用戶端的安全性工作階段作業順利完成。|  
|SAMLActionNameRequiredOnRead|為 SamlAction 讀取的字串遺失或是長度為 0。|  
|KerberosMultilegsNotSupported|身分識別已指定為 UPN。 不支援對需要多支線 (Multi-leg) Kerberos 的使用者帳戶下的服務進行驗證。|  
|SAMLAssertionIdRequired|SamlAssertion 的 ' assertionId' 不可以是 Null 或空白。|  
|InvalidOperationForWriterState|指定的作業在指定的 XmlWriter 狀態時無效。|  
|CannotValidateSecurityTokenType|指定的安全性權杖驗證器無法驗證指定之類型的權杖。|  
|X509FindValueMismatch|指定的 X509FindType 要求引數 findValue 的類型必須是指定的值。 引數 findValue 是另一個類型。|  
|TraceCodeSecurityClientSessionCloseSent|用戶端安全性工作階段已傳送「關閉」訊息。|  
|SuiteDoesNotAcceptAlgorithm|指定的演算法套件所進行的指定之作業不接受指定的演算法|  
|TraceCodeSecuritySessionRequestorOperationFailure|用戶端安全性工作階段作業失敗。|  
|SAMLUnableToLoadStatement|無法載入 SamlStatement。|  
|InnerReaderMustBeAtElement|內部讀取器必須在項目的位置。|  
|UnableToCreateTokenReference|無法建立安全性權杖參照。|  
|TraceCodeSecurityBindingIncomingMessageVerified|安全性通訊協定已驗證傳入訊息。|  
|ObjectIsReadOnly|物件是唯讀的。|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|用戶端安全性工作階段已捨棄先前的工作階段金鑰。|  
|SAMLTokenTimeInvalid|SamlToken 的時間無效。 目前的時間位於權杖的有效時間及到期時間之外。|  
|TraceCodeSecurityIdentityVerificationSuccess|身分識別驗證成功。|  
|SigningTokenHasNoKeys|指定的簽署權杖不包含金鑰。|  
|TraceCodeSecurityIdentityVerificationFailure|身分識別驗證失敗。|  
|AESCryptImportKeyFailed|無法匯入金鑰內容。|  
|FailInitializeSecurityContext|InitializeSecurityContent 失敗。 請確定服務主要名稱是正確的。|  
|TraceCodeStreamSecurityUpgradeAccepted|已成功接受資料流安全性升級。|  
|SAMLAuthorityBindingRequiresLocation|對 SamlAuthorityBinding 指定的 'Location' 屬性不可以是 Null 或是長度為 0。|  
|PublicKeyNotDSA|公開金鑰不是 DSA 金鑰。|  
|ImpersonationLevelNotSupported|使用 Kerberos 的驗證模式不支援指定的模擬等級。 請指定有效的識別或模擬等級。|  
|RequiredTargetNotSigned|必須簽署具有指定識別碼的項目，但尚未簽署。|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|為 SamlAuthenticationStatement 所讀取的 'AuthenticationInstant' 屬性遺失或是長度為 0。|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|所讀取的 SamlEvidence 未包含對 SamlAssertion 的參考或是內嵌的 SamlAssertion。|  
|LengthOfArrayToConvertMustGreaterThanZero|要轉換成整數的陣列長度必須大於 0。|  
|InvalidAsyncResult|AsyncResult 無效。|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|IssuanceTokenProvider 已移除過期的服務權杖。|  
|IncorrectUserNameFormat|使用者名稱的格式無效。 使用者名稱格式必須是格式 「 使用者名稱 '或' 網域\\\username'。|  
|TraceCodeExportSecurityChannelBindingEntry|啟動安全性 ExportChannelBinding。|  
|UnsupportedInputTypeForTransform|轉換不支援指定的輸入類型。|  
|CannotFindDocumentRoot|找不到文件的根。|  
|XmlBufferQuotaExceeded|用來緩衝 XML 內容的所需大小已超過緩衝區配額。|  
|TraceCodeSecuritySessionClosedResponseSendFailure|將安全性工作階段「關閉」回應傳送到用戶端時發生失敗。|  
|UnableToResolveReferenceInSamlSignature|無法以 AssertionID 來解析 SAML 簽章中指定的參考。|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|SamlSubject 需要指定 'NameIdentifier' 或 'ConfirmationMethod'。 兩者均已遺失。|  
|SAMLAttributeMissingNamespaceAttributeOnRead|所讀取的 SamlAttribute 之 'Namespace' 遺失或是長度為 0。|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|在所讀取的 SamlSubjectConfirmation 中，找不到 'ConfirmationMethod'。|  
|SecurityTokenRequirementHasInvalidTypeForProperty|權杖需求的指定之屬性出現不正確的類型。 需要的屬性型別為其他值。|  
|TraceCodeNegotiationTokenProviderAttached|已附加 NegotiationTokenProvider。|  
|TraceCodeSpnegoClientNegotiationCompleted|SpnegoTokenProvider 已完成 SSPI 交涉。|  
|SAMLUnableToLoadUnknownElement|所選取的 SamlSerializer 無法將此項目還原序列化。 請註冊自訂的 SamlSerializer，以將自訂項目還原序列化。|  
|CreateSequenceRefused|RM 目的地已拒絕建立順序要求。|  
|TraceCodeSecuritySessionRedirectApplied|用戶端安全性工作階段已重新導向。|  
|SecurityTokenRequirementDoesNotContainProperty|權杖需求不包含指定的屬性。|  
|SAMLAttributeValueCannotBeNull|在 SamlAttribute 找到的某個 attributeValues 是 Null 值。 請確定建立 SamlAttribute 時，清單不是 Null。|  
|ValueMustBeGreaterThanZero|此引數的值必須大於 0。|  
|TraceCodeNegotiationAuthenticatorAttached|已附加 NegotiationTokenAuthenticator。|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|SamlAuthorizationDecisionStatement 必須至少有一個 SamlAction。|  
|TraceCodeSecurityTokenAuthenticatorClosed|安全性權杖驗證器已關閉。|  
|TraceCodeSecurityAuditWrittenSuccess|順利寫入安全性稽核記錄。|  
|PrivateKeyNotDSA|私密金鑰不是 DSA 金鑰。|  
|MessageNumberRollover|已超過此順序的序號上限。|  
|AESPaddingModeNotSupported|不支援指定的填補模式。 只支援 PKCS7 和 ISO10126。|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|在所讀取的 SamlSubject 中，找不到必要的 'NameIdentifier' 及 'ConfirmationMethod' 項目。|  
|TraceCodeSecurityAuditWrittenFailure|寫入安全性稽核記錄時發生失敗。|  
|UnsupportedCryptoAlgorithm|此內容不支援指定的加密演算法。|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|簽署權杖沒有支援指定之演算法套件的金鑰。|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|所讀取的 SamlNameIdentifier 之 'Identifier' 字串已遺失。|  
|SAMLSubjectStatementRequiresSubject|SAML 主體陳述式需要指定 SAML 主體。|  
|TraceCodeSslClientCertMissing|遠端 SSL 用戶端無法提供必要的憑證。|  
|SAMLTokenVersionNotSupported|不支援指定的主要版本和次要版本。|  
|TraceCodeConfigurationIsReadOnly|此組態是唯讀的。|  
|TraceCodeSecuritySessionRenewFaultSendFailure|將安全性工作階段金鑰更新的錯誤傳送到用戶端時發生失敗。|  
|TraceCodeSecurityInactiveSessionFaulted|非作用中的安全性工作階段因伺服器發生錯誤。|  
|SAMLUnableToLoadAttribute|無法載入 SamlAttribute。|  
|Psha1KeyLengthInvalid|指定的 PSHA1 金鑰長度無效。|  
|KeyIdentifierCannotCreateKey|這個 SecurityKeyIdentifier 沒有任何子句可用來建立金鑰。|  
|X509IsInUntrustedStore|指定的 X.509 憑證位於不受信任的憑證存放區。|  
|UnexpectedXmlChildNode|指定的項目不應該有所指定類型之指定的 XML 子節點。|  
|TokenDoesNotMeetKeySizeRequirements|指定之權杖的金鑰大小不符合指定之演算法套件的金鑰大小需求。|  
|TraceCodeSecuritySessionRequestorStartOperation|已在用戶端啟動安全性工作階段作業。|  
|InvalidHexString|十六進位字串格式無效。|  
|SamlAttributeClaimResourceShouldBeAString|這個 SamlAttribute 建構函式要求宣告資源的類型必須是 'string'。|  
|SamlSigningTokenNotFound|SamlAssertion 已簽署，但是找不到用來簽署 SamlAssertion 的權杖。 請確定 SecurityTokenResolver 含有用來簽署 SamlAssertion 的權杖。|  
|TraceCodeSecuritySpnToSidMappingFailure|ServicePrincipalName 無法對應到 SecurityIdentifier。|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|無法從指定的非對稱式加密針對指定的演算法建立簽章格式器。|  
|TraceCodeSecurityServerSessionClosedFaultSent|伺服器安全性工作階段已將工作階段已關閉的錯誤傳送給用戶端。|  
|UnableToFindPrefix|在指定的項目找不到指定的常用前置詞。|  
|TraceCodeSecurityTokenAuthenticatorOpened|安全性權杖驗證器已開啟。|  
|RequiredAttributeMissing|指定的項目上需要指定的屬性。|  
|LocalIdCannotBeEmpty|localId 不可以空白。 請指定有效的 'localId'。|  
|ValueMustBeInRange|此引數值必須在指定的範圍之間。|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|IssuanceTokenProvider 已經啟動新的安全性交涉。|  
|InvalidNtMapping|指定的 X.509 憑證無法對應到 Windows 帳戶。 需要 UPN 主體交替名稱。|  
|AESCryptSetKeyParamFailed|無法設定指定的金鑰參數。|  
|TraceCodeSecuritySessionClosedResponseReceived|用戶端安全性工作階段收到來自伺服器的已關閉回應。|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|無法從指定的非對稱式加密針對指定的演算法建立簽章變形項。|  
|TraceCodeIdentityModelAsyncCallbackThrewException|非同步回呼擲回例外狀況。|  
|LengthMustBeGreaterThanZero|此引數的長度必須大於 0。|  
|FoundMultipleCerts|使用指定的搜尋條件 StoreName、StoreLocation、FindType、FindValue 時，找到多個 X.509 憑證。 請提供更精確的尋找值。|  
|AtLeastOneTransformRequired|Transforms 項目必須至少包含一個轉換。|  
|SAMLTokenNotSerialized|SamlAssertion 無法序列化到 XML。 如需詳細資訊，請參閱內部例外狀況。|  
|TraceCodeSecurityBindingOutgoingMessageSecured|安全性通訊協定已驗證傳出訊息。|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|這個 SecurityKeyIdentifierClause 不支援建立金鑰。|  
|UnableToResolveTokenReference|權杖解析程式無法解析指定的權杖參考。|  
|UnsupportedEncryptionAlgorithm|不支援指定的加密演算法。|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|SamlSerializer 不包含能夠序列化特定 SecurityKeyIdentifier 的 SecurityTokenSerializer。 如果您使用自訂的 SecurityKeyIdentifier，則必須提供自訂的 SecurityTokenSerializer。|  
|SAMLAttributeShouldHaveOneValue|找不到屬性值。 SamlAttribute 屬性必須至少有一個屬性值。|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|安全性通訊協定無法檢查傳入訊息。|  
|SamlSigningTokenMissing|傳送到 SamlSecurityTokenAuthenticator 的 SamlAssertion 不包含簽署權杖。|  
|NoPrivateKeyAvailable|沒有私密金鑰可用。|  
|ValueMustBeOne|此引數的值必須是 1。|  
|TraceCodeSecurityPendingServerSessionRemoved|伺服器已啟用擱置中的安全性工作階段。|  
|TraceCodeImportSecurityChannelBindingExit|完成安全性 ImportChannelBinding。|  
|X509CertStoreLocationNotValid|StoreLocation 必須是 LocalMachine 或 CurrentUser。|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|只有在寫入器處於「開始」狀態時，才能修改寫入器設定。|  
|ArgumentInvalidCertificate|憑證無效。|  
|DigestVerificationFailedForReference|指定之參考的摘要驗證失敗。|  
|SAMLAuthorityBindingRequiresBinding|對 SamlAuthorityBinding 指定的 'Binding' 屬性不可以是 Null 或是長度為 0。|  
|AESInsufficientOutputBuffer|輸出緩衝區必須大於指定的位元組。|  
|SAMLAuthorityBindingMissingBindingOnRead|所讀取的 SamlAuthorityBinding 之 'Binding' 屬性遺失或是長度為 0。|  
|SAMLAuthorityBindingInvalidAuthorityKind|所讀取的 SamlAuthorityBinding 之 AuthorityKind 無效。 AuthorityKind 的格式必須是 QName。|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|為 Kerberos 權杖提供的 NetworkCredentials 沒有有效的 UserName。|  
|SSPIPackageNotSupported|不支援指定的 SSPI 封裝。|  
|TokenCancellationNotSupported|指定的權杖提供者不支援取消權杖。|  
|UnboundPrefixInQName|指定的限定名稱中使用了未繫結的前置詞。|  
|SAMLAuthorizationDecisionResourceRequired|為 SamlAuthorizationDecisionStatement 指定的 'resource' 不可以是 Null 或是長度為 0。|  
|TraceCodeSecurityNegotiationProcessingFailure|服務安全性交涉處理失敗。|  
|SAMLAssertionIssuerRequired|為 SamlAssertion 指定的 'Issuer' 不可以是 Null 或空白。|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|無法從指定的非對稱式加密針對指定的演算法建立 HashAlgorithm。|  
|SamlUnableToExtractSubjectKey|在 SamlSubject 中找到的 SecurityKeyIdentifier 無法解析為 SecurityToken。 SecurityTokenResolver 必須包含 SecurityKeyIdentifier 所解析成的 SecurityToken。|  
|ChildNodeTypeMissing|指定的 XML 項目不具有指定之類型的子系。|  
|TraceCodeSecurityPendingServerSessionClosed|伺服器已關閉擱置中的安全性工作階段。|  
|TraceCodeSecuritySessionCloseResponseSent|伺服器安全性工作階段已將關閉回應傳送給用戶端。|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|端點位址的 HostName 部分無法正規化。|  
|FailAcceptSecurityContext|AcceptSecurityContext 失敗。|  
|EmptyXmlElementError|指定的項目不可以空白。|  
|PrefixNotDefinedForNamespace|此內容未定義指定之命名空間的前置詞，且無法宣告。|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|所讀取的 SamlAuthorizationDecisionStatement 包含多個 Evidence。 這是不允許的。|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|SamlSecurityTokenAuthenticator 只能處理 SamlSecurityTokens。 已接收到指定的 SecurityTokenType。|  
|SAMLAttributeStatementMissingAttributeOnRead|所讀取的 SamlAttributeStatement 未包含任何 'SamlAttribute' 項目。 這是不允許的。|  
|CouldNotFindNamespaceForPrefix|無法查詢指定之前置詞的命名空間。|  
|TraceCodeExportSecurityChannelBindingExit|完成安全性 ExportChannelBinding。|  
|AESCryptDecryptFailed|無法解密指定的資料。|  
|SAMLAttributeNamespaceAttributeRequired|為 SamlAttribute 指定的 'Namespace' 不可以是 Null 或是長度為 0。|  
|TraceCodeSpnegoServiceNegotiationCompleted|SpnegoTokenAuthenticator 已完成 SSPI 交涉。|  
|TraceCodeSecurityServerSessionRenewalFaultSent|伺服器安全性工作階段已將金鑰更新錯誤傳送至用戶端。|  
|AlgorithmMismatchForTransform|轉換時，演算法發生不一致的情形。|  
|UserNameAuthenticationFailed|使用指定的機制驗證使用者名稱/密碼失敗。 未驗證使用者。|  
|SamlInvalidSigningToken|用來簽署 SamlAssertion 的權杖尚未根據通訊協定進行驗證。 如果您使用的是 X.509 憑證，請檢查驗證語法。|  
|TraceCodeSecurityServerSessionKeyUpdated|伺服器已更新安全性工作階段金鑰。|  
|TraceCodeSecurityServerSessionCloseReceived|伺服器安全性工作階段已從用戶端收到關閉訊息。|  
|SAMLAuthenticationStatementMissingSubject|SamlAuthenticationStatement 遺失了必要的 SamlSubjectStatement。|  
|UnexpectedEndOfFile|檔案意外結束。|  
|UnsupportedAlgorithmForCryptoOperation|指定的作業不支援指定的演算法。|  
|XmlLangAttributeMissing|必要的 xml:lang 屬性已遺失。|  
|TraceCodeSecurityImpersonationSuccess|伺服器的安全性模擬成功。|  
|SAMLAuthorityBindingMissingLocationOnRead|所讀取的 SamlAuthorityBinding 之 'Location' 屬性遺失或是長度為 0。|  
|SAMLAttributeStatementMissingSubjectOnRead|缺少 SamlAttributeStatement 的 'SamlSubject' 項目。|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|所讀取的 SamlAuthorizationDecisionStatement 缺少 'SamlSubject' 項目。|  
|SAMLBadSchema|讀取 SamlAssertion 時，發現此指定的項目與結構描述不符。|  
|SAMLAssertionIDIsInvalid|SamlAssertion 之指定的 'assertionId' 必須以字母或 '_' 開頭。|  
|TraceCodeSecurityActiveServerSessionRemoved|伺服器已移除作用中的安全性工作階段。|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|無法從指定的對稱式加密針對指定的演算法建立 keyedHashAlgorithm。|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|為 SamlAuthenticationStatement 指定的 'AuthenticationMethod' 不可以是 Null 或是長度為 0。|  
|TraceCodeSecurityImpersonationFailure|伺服器的安全性模擬失敗。|  
|預設|(預設值)|  
|UnsupportedNodeTypeInReader|不支援具有指定名稱的指定之節點類型。|
