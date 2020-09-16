---
title: 不支援的案例
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: a3ee91e5232926b4ea7db80db35d9a309ca8105b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557810"
---
# <a name="unsupported-scenarios"></a>不支援的案例

基於各種原因，Windows Communication Foundation (WCF) 不支援某些特定的安全性案例。 例如，Windows XP Home Edition 不會執行 SSPI 或 Kerberos 驗證通訊協定，因此 WCF 不支援在該平臺上執行具有 Windows 驗證的服務。 在 Windows XP Home Edition 下執行 WCF 時，支援其他驗證機制，例如使用者名稱/密碼和 HTTP/HTTPS 整合式驗證。

## <a name="impersonation-scenarios"></a>模擬案例

### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>當用戶端進行非同步呼叫時，模擬的身分識別可能不會流動
 當 WCF 用戶端在模擬下使用 Windows 驗證對 WCF 服務進行非同步呼叫時，可能會驗證用戶端處理序的識別，而非模擬的識別。

### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>已啟用 Windows XP 和安全內容權杖 cookie

WCF 不支援模擬， <xref:System.InvalidOperationException> 當下列條件存在時，就會擲回。

- 作業系統是 Windows XP。

- 驗證模式變成 Windows 識別。

- <xref:System.ServiceModel.OperationBehaviorAttribute> 的 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> 屬性會設定為 <xref:System.ServiceModel.ImpersonationOption.Required>。

- 建立以狀態為基礎的安全性內容權杖 (SCT) (根據預設會停用建立作業)。

 您只能透過自訂繫結來建立以狀態為基礎的 SCT ( 如需詳細資訊，請參閱 [如何：建立安全會話的安全性內容權杖](how-to-create-a-security-context-token-for-a-secure-session.md)。 ) 在程式碼中，您可以使用或方法來建立安全性繫結項目， (<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 或 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) ， <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> 並將 `requireCancellation` 參數設為 `false` ，藉此啟用權杖。 此參數會參考 SCT 的快取。 將值設為 `false` 會啟用以狀態為基礎的 SCT 功能。

 或者，在設定中，權杖是藉由建立 <> 來啟用 `customBinding` ，然後新增 <`security`> 元素，並將屬性設定 `authenticationMode` 為 SecureConversation，並將 `requireSecurityContextCancellation` 屬性設定為 `true` 。

> [!NOTE]
> 執行作業之前有一些特定需求： 例如，<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> 將建立會變成 Windows 識別的繫結項目，但是不會建立 SCT。 因此，您可以將它與 `Required` WINDOWS XP 上的選項搭配使用。

### <a name="possible-aspnet-conflict"></a>可能的 ASP.NET 衝突

WCF 和 ASP.NET 可以啟用或停用模擬。 當 ASP.NET 裝載 WCF 應用程式時，WCF 和 ASP.NET 設定之間可能存在衝突。 如果發生衝突，除非屬性設定為，否則 WCF 設定會優先使用， <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> <xref:System.ServiceModel.ImpersonationOption.NotAllowed> 在此情況下，ASP.NET 模擬設定會優先使用。

### <a name="assembly-loads-may-fail-under-impersonation"></a>元件載入在模擬下可能會失敗

如果模擬的內容沒有載入組件的存取權，而且同時也是 Common Language Runtime (CLR) 第一次嘗試載入該 AppDomain 的組件，則 <xref:System.AppDomain> 會快取失敗結果。 即使還原模擬後，後續的組件載入嘗試一樣會失敗，而且即使還原後的內容具有載入組件的存取權也一樣。 這是因為 CLR 在使用者內容變更之後不會重新嘗試載入。 您必須重新啟動應用程式定義域，從失敗中進行還原。

> [!NOTE]
> <xref:System.ServiceModel.Security.WindowsClientCredential> 類別的 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>屬性預設值為 <xref:System.Security.Principal.TokenImpersonationLevel.Identification>。 在大多數情況下，識別層級的模擬內容沒有載入任何其他組件的權限。 這是預設值，因此您應該要瞭解這個常見的情況。 當模擬的處理序沒有 `SeImpersonate` 權限時，一樣會發生識別層級的模擬情況。 如需詳細資訊，請參閱 [委派和](delegation-and-impersonation-with-wcf.md)模擬。

### <a name="delegation-requires-credential-negotiation"></a>委派需要認證協商

若要將 Kerberos 驗證通訊協定與委派搭配使用，您必須實作具有認證交涉的 Kerberos 通訊協定 (有時也稱做「多線」(Multi-leg) 或「多步驟」(Multi-step) Kerberos)。 如果您實作不具有認證交涉的 Kerberos 驗證 (有時也稱做「單次」(One-shot) 或「單支線」(Single-leg) Kerberos)，則會擲回例外狀況。 如需如何執行認證協商的詳細資訊，請參閱 [Windows 驗證錯誤的調試](debugging-windows-authentication-errors.md)程式。

## <a name="cryptography"></a>密碼編譯

### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>只有對稱金鑰使用方式支援 SHA-256

WCF 支援您可以使用系統提供之系結中的演算法套件來指定各種加密和簽章摘要建立演算法。 為了提高安全性，WCF 支援安全雜湊演算法， (SHA) 2 演算法（尤其是 SHA-256）來建立簽章摘要雜湊。 此版本僅針對對稱金鑰用途 (例如 Kerberos 金鑰) 支援使用 SHA-256，而且並未使用 X.509 憑證來簽署訊息。 WCF 不支援在 x.509 憑證中使用的 RSA 256 簽章 (使用 SHA-1 雜湊) ，因為在 WinFX 中目前缺乏 RSA-SHA256 的支援。

### <a name="fips-compliant-sha-256-hashes-not-supported"></a>不支援符合 FIPS 規範的 SHA-256 雜湊

WCF 不支援符合 256 SHA-1 FIPS 標準的雜湊，因此在需要使用符合 FIPS 規範的演算法的系統上，WCF 不支援使用 SHA-256 的演算法套件。

### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>符合 FIPS 規範的演算法可能會在編輯登錄時失敗

您可以透過 [本機安全性設定] 之 Microsoft Management Console (MMC) 嵌入式管理單元，啟用與停用與聯邦資訊處理標準 (FIPS) 相容的演算法。 您也可以存取登錄中的設定。 不過請注意，WCF 不支援使用登錄來重設設定。 如果將值設為 1 或 0 以外的任意值，則 CLR 與作業系統之間就會產生不一致的結果。

### <a name="fips-compliant-aes-encryption-limitation"></a>符合 FIPS 規範的 AES 加密限制

符合 FIPS 規範的 AES 加密無法在識別層級模擬下的雙工回呼中運作。

### <a name="cngksp-certificates"></a>CNG/KSP 憑證

*密碼編譯 API：新一代 (CNG) * 是 CryptoAPI 的長期取代。 此 API 適用于 Windows Vista、Windows Server 2008 及更新版本 Windows 版本上的非受控碼。

 .NET Framework 4.6.1 和較早的版本不支援這些憑證，因為它們使用舊版 CryptoAPI 來處理 CNG/KSP 憑證。 使用這些憑證搭配 .NET Framework 4.6.1 和更早版本將會造成例外狀況。

 有兩種可能的方式可以判斷憑證是否使用 KSP：

- 對 `p/invoke` 執行 `CertGetCertificateContextProperty` 後，檢查所傳回 `dwProvType` 的 `CertGetCertificateContextProperty`。

- `certutil`從命令列使用命令來查詢憑證。 如需詳細資訊，請參閱 [針對憑證進行疑難排解的 Certutil](/previous-versions/orphan-topics/ws.10/cc772619(v=ws.10))工作。

## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>如果需要使用 ASP.NET 模擬和 ASP.NET 相容性，訊息安全性會失敗

WCF 不支援下列設定的組合，因為它們可以防止用戶端驗證發生：

- 已啟用 ASP.NET 模擬。 這是在 Web.config 檔案中完成，方法是將 `impersonate` <> 專案的屬性設定 `identity` 為 `true` 。

- 將的 `aspNetCompatibilityEnabled` 屬性設定 [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) 為，即可啟用 ASP.NET 相容性模式 `true` 。

- 已使用訊息模式安全性。

解決辦法是關閉 ASP.NET 相容性模式。 或者，如果需要 ASP.NET 相容性模式，請停用 ASP.NET 模擬功能，並改為使用 WCF 提供的模擬。 如需詳細資訊，請參閱 [委派和](delegation-and-impersonation-with-wcf.md)模擬。

## <a name="ipv6-literal-address-failure"></a>IPv6 常值位址失敗

安全性要求會失敗的情況為：當用戶端與服務位於同一部電腦，以及服務使用 IPv6 常值位址時。

 如果服務與用戶端位於不同的電腦上，則 IPv6 常值位址就能正常運作。

## <a name="wsdl-retrieval-failures-with-federated-trust"></a>使用同盟信任的 WSDL 抓取失敗

WCF 針對同盟信任鏈中的每個節點，都只需要一個 WSDL 檔案。 指定端點時，請小心不要設定迴圈。 一個可能發生迴圈的方式是，使用 WSDL 來下載同一份 WSDL 文件中有兩個以上連結的聯合信任鏈結。 會產生這個問題的常見案例是，Security Token Server 和聯合服務包含在相同的 ServiceHost 中。

 舉例來說，當服務具有下列三個端點位址時，就會發生這種狀況：

- `http://localhost/CalculatorService/service` (服務) 

- `http://localhost/CalculatorService/issue_ticket` (STS) 

- `http://localhost/CalculatorService/mex` (中繼資料端點) 

 這會擲回例外狀況。

 您可以藉由將 `issue_ticket` 端點放在其他位置，來解決這個狀況。

## <a name="wsdl-import-attributes-can-be-lost"></a>WSDL 匯入屬性可能會遺失

WCF 在執行 WSDL 匯入時，會遺失 `<wst:Claims>` 範本中 `RST` 項目的屬性。 如果您是在 `<Claims>` 或 `WSFederationHttpBinding.Security.Message.TokenRequestParameters` 中直接指定 `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters`，而不是直接使用宣告類型集合，在 WSDL 匯入期間就會發生這個狀況。  因為匯入作業會遺失屬性，繫結無法透過 WSDL 適當往返，也因此繫結在用戶端是不正確的。

 解決方式是匯入之後直接在用戶端修改繫結。

## <a name="see-also"></a>另請參閱

- [安全性考量](security-considerations-in-wcf.md)
- [洩露資訊](information-disclosure.md)
- [提高權限](elevation-of-privilege.md)
- [拒絕服務](denial-of-service.md)
- [竄改](tampering.md)
- [重新執行攻擊](replay-attacks.md)
