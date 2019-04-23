---
title: 偵錯 Windows 驗證錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: 28c70ca860083808c93fa58b498e22ea4e4ca6cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299445"
---
# <a name="debugging-windows-authentication-errors"></a>偵錯 Windows 驗證錯誤
當使用 Windows 驗證做為安全性機制時，安全性支援提供者介面 (SSPI) 便會處理安全性程序。 當安全性錯誤發生在 SSPI 層時，它們會顯示由 Windows Communication Foundation (WCF)。 本主題會提供可協助診斷這些錯誤的架構與問題集。  
  
 如需 Kerberos 通訊協定的概觀，請參閱 < [Kerberos 說明 >](https://go.microsoft.com/fwlink/?LinkID=86946); 如需 SSPI 的概觀，請參閱[SSPI](https://go.microsoft.com/fwlink/?LinkId=88941)。  
  
 對於 Windows 驗證，WCF 通常會使用*交涉*安全性支援提供者 (SSP)，它會執行用戶端與服務之間的 Kerberos 相互驗證。 如果無法使用，WCF 會回復到 NT LAN Manager (NTLM) 的預設 Kerberos 通訊協定。 不過，您可以設定 WCF 只使用 Kerberos 通訊協定 （並擲回例外狀況，如果 Kerberos 無法使用）。 您也可以設定成使用限制的型態的 Kerberos 通訊協定的 WCF。  
  
## <a name="debugging-methodology"></a>偵錯方法  
 下面列出基本的方法：  
  
1. 判斷您是否在使用 Windows 驗證。 如果您是使用其他任何配置，這個主題就不適用。  
  
2. 如果您不確定您使用 Windows 驗證，判斷您的 WCF 組態是否使用 Kerberos direct 或 Negotiate。  
  
3. 判斷出您的組態是使用 Kerberos 通訊協定或 NTLM 之後，您就能夠了解在正確環境中的錯誤訊息。  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Kerberos 通訊協定與 NTLM 的可用性  
 Kerberos SSP 需要網域控制站擔任 Kerberos 金鑰發佈中心 (KDC)。 唯有當用戶端與服務都使用網域識別時，才可以使用 Kerberos 通訊協定。 在其他帳戶組合中則是使用 NTLM，如下表摘要所示。  
  
 表格標頭會顯示伺服器可能使用的帳戶類型。 左欄則顯示用戶端可能使用的帳戶類型。  
  
||本機使用者|本機系統|網域使用者|網域電腦|  
|-|----------------|------------------|-----------------|--------------------|  
|本機使用者|NTLM|NTLM|NTLM|NTLM|  
|本機系統|匿名 NTLM|匿名 NTLM|匿名 NTLM|匿名 NTLM|  
|網域使用者|NTLM|NTLM|Kerberos|Kerberos|  
|網域電腦|NTLM|NTLM|Kerberos|Kerberos|  
  
 具體而言，這四種帳戶類型包括：  
  
-   本機使用者：僅限電腦的使用者設定檔。 例如：`MachineName\Administrator` 或 `MachineName\ProfileName`。  
  
-   本機系統：內建帳戶 SYSTEM 未加入網域的電腦上。  
  
-   網域使用者：在 Windows 網域使用者帳戶。 例如：`DomainName\ProfileName`。  
  
-   網域電腦：加入 Windows 網域的機器上執行的機器身分識別與處理程序。 例如：`MachineName\Network Service`。  
  
> [!NOTE]
>  當呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 類別的 <xref:System.ServiceModel.ServiceHost> 方法時，便會擷取服務認證。 每當用戶端傳送訊息時就會讀取此用戶端認證。  
  
## <a name="common-windows-authentication-problems"></a>常見 Windows 驗證問題  
 本節會討論一些常見的 Windows 驗證問題以及可能的補救方法。  
  
### <a name="kerberos-protocol"></a>Kerberos 通訊協定  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Kerberos 通訊協定的 SPN/UPN 問題  
 當使用 Windows 驗證，而且 SSPI 有使用或交涉 Kerberos 通訊協定時，用戶端端點所使用的 URL 就必須包含在服務 URL 內之服務主機的完整網域名稱。 這是假設服務執行所在的帳戶具有將電腦加入 Active Directory 網域，其作法是最常執行服務時，會建立電腦 （預設） 服務主體名稱 (SPN) 金鑰的存取權網路服務帳戶。 如果服務無法存取電腦 SPN 金鑰，您就必須在用戶端端點身分識別中，提供用來執行服務之帳戶的正確 SPN 或使用者主要名稱 (UPN)。 如需 WCF 搭配 SPN 與 UPN 的運作方式的詳細資訊，請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
 在負載平衡的使用案例 (例如 Web 伺服陣列與 Web 處理序區) 中，常見的作法是為每一個應用程式定義一個唯一的帳戶、指派一個 SPN 給該帳戶，並且確保應用程式的所有服務都以該帳戶執行。  
  
 如果您要取得服務帳戶的 SPN，您必須是 Active Directory 網域的管理員。 如需詳細資訊，請參閱 < [Kerberos 技術補充的 Windows](https://go.microsoft.com/fwlink/?LinkID=88330)。  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Kerberos 通訊協定 Direct 要求使用網域電腦帳戶來執行服務。  
 當 `ClientCredentialType` 屬性設定為 `Windows`，而且 <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> 屬性設定為 `false` 時，便會發生這種情況，如下列程式碼所示。  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 若要修正此問題，請使用網域電腦帳戶來執行服務，例如，在加入網域之電腦上的 Network Service 帳戶。  
  
### <a name="delegation-requires-credential-negotiation"></a>委派需要認證交涉  
 若要將 Kerberos 驗證通訊協定與委派搭配使用，您必須實作具有認證交涉的 Kerberos 通訊協定 (有時也稱做「多支線」(Multi-leg) 或「多步驟」(Multi-step) Kerberos)。 如果您實作不具有認證交涉的 Kerberos 驗證 (有時也稱做「單次」(One-shot) 或「單支線」(Single-leg) Kerberos)，則會擲回例外狀況。  
  
 若要實作具有認證交涉的 Kerberos，請執行下列步驟：  
  
1. 將 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 設定為 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> 以實作委派。  
  
2. 要求 SSPI 交涉：  
  
    1.  如果您是使用標準繫結，請將 `NegotiateServiceCredential` 屬性 (Property) 設定為 `true`。  
  
    2.  如果您是使用自訂繫結，請將 `AuthenticationMode` 項目的 `Security` 屬性 (Attribute) 設定為 `SspiNegotiated`。  
  
3. 透過拒絕使用 NTLM 來要求 SSPI 交涉使用 Kerberos：  
  
    1.  在程式碼中使用下列陳述式來做到這點：`ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2.  或者，您可以將組態檔中的 `allowNtlm` 屬性設定為 `false` 來做到這點。 此屬性包含在[ \<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)。  
  
### <a name="ntlm-protocol"></a>NTLM 通訊協定  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>交涉 SSP 退而使用 NTLM，但是 NTLM 已停用  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A>屬性設定為`false`，這樣會使 Windows Communication Foundation (WCF) 讓最大努力擲回例外狀況，如果使用 NTLM。 請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。  
  
 下列程式碼示範如何停用退回使用 NTLM。  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>NTLM 登入失敗  
 用戶端認證在服務上屬於無效。 請檢查使用者名稱與密碼是否有正確設定，以及是否有對應到服務執行所在電腦所認得的帳戶。 NTLM 會使用指定的認證來登入該服務的電腦。 儘管在用戶端執行所在電腦上的認證可能是有效的，如果該認證在服務的電腦上屬於無效，這項登入仍然會失敗。  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>發生匿名 NTLM 登入，不過匿名登入已依預設地停用。  
 當建立用戶端時，<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 屬性已設定為 <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>，但是伺服器卻已依預設地拒絕匿名登入，如下列範例所示。 這種情況的發生原因在於 <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> 類別之 <xref:System.ServiceModel.Security.WindowsServiceCredential> 屬性的預設值為 `false`。  
  
 下列用戶端程式碼會嘗試啟用匿名登入 (請注意，預設屬性是 `Identification`)。  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 下列服務程式碼會變更預設值，讓伺服器允許匿名登入。  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 如需有關模擬的詳細資訊，請參閱 <<c0> [ 委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)。  
  
 或者，用戶端會使用內建帳戶 SYSTEM 來執行為 Windows 服務。  
  
### <a name="other-problems"></a>其他問題  
  
#### <a name="client-credentials-are-not-set-correctly"></a>用戶端認證沒有正確設定  
 Windows 驗證使用由 <xref:System.ServiceModel.Security.WindowsClientCredential> 類別之 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 屬性傳回的 <xref:System.ServiceModel.ClientBase%601> 執行個體，而不是使用 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>。 下面舉出不正確的範例。  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 下面舉出正確的範例。  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>無法使用 SSPI  
 在下列作業系統不支援 Windows 驗證時用來作為伺服器：[!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition， [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition 和[!INCLUDE[wv](../../../../includes/wv-md.md)]Home edition。  
  
#### <a name="developing-and-deploying-with-different-identities"></a>以不同的身分進行開發及部署  
 如果您在某一台電腦上開發應用程式，然後又在另一台電腦上進行部署，而且在每一台電腦上都使用不同的帳戶類型進行驗證，您可能會產生不同的行為。 例如，假設您是使用 `SSPI Negotiated`驗證模式，在 Windows XP Pro 機器上開發應用程式。 您又使用本機使用者帳戶進行身分驗證，然後又使用了 NTLM 通訊協定。 應用程式開發完成後，您以網域帳戶先在 Windows Server 2003 機器上部署服務而後執行。 此時，用戶端將無法驗證該服務，因為用戶端使用的是 Kerberos 及網域控制站。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
