---
title: 阻斷服務
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: f67a8b2977e84e24654b4b65c0cdd03bcbcb1b20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968827"
---
# <a name="denial-of-service"></a>阻斷服務
當系統由於無法處理訊息，或者處理訊息的速度極為緩慢而爆滿時，就會發生阻絕服務。  
  
## <a name="excess-memory-consumption"></a>過多記憶體耗用  
 讀取具有大量唯一本機名稱、命名空間或前置詞的 XML 文件時，會發生問題。 如果您正在使用衍生自 <xref:System.Xml.XmlReader> 的類別，且您為每個項目呼叫 <xref:System.Xml.XmlReader.LocalName%2A>、<xref:System.Xml.XmlReader.Prefix%2A> 或 <xref:System.Xml.XmlReader.NamespaceURI%2A> 屬性，則傳回的字串會新增至 <xref:System.Xml.NameTable>。 <xref:System.Xml.NameTable> 所持有的集合大小一定不會減小，它會建立字串控制代碼的虛擬「記憶體遺漏」(Memory Leak)。  
  
 風險降低的方式包括：  
  
- 衍生自 <xref:System.Xml.NameTable> 類別並強制執行最大的大小配額 (當配額已滿時，您無法避免使用 <xref:System.Xml.NameTable> 或切換 <xref:System.Xml.NameTable>)。  
  
- 避免使用提到的屬性，並盡量搭配使用 <xref:System.Xml.XmlReader.MoveToAttribute%2A> 方法和 <xref:System.Xml.XmlReader.IsStartElement%2A> 方法，這些方法不會傳回字串，這樣就可避免 <xref:System.Xml.NameTable> 集合太滿的問題。  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>惡意用戶端將大量授權要求傳送至服務  
 如果惡意用戶端透過大量授權要求炸滿服務，就可能導致伺服器使用過多的記憶體。  
  
 風險降低：使用<xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>類別的下列屬性:  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>：控制時間界限之 `SecurityContextToken` 的上限，而這是伺服器在 `SPNego` 或 `SSL` 交涉之後快取的上限。  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>：控制 `SecurityContextTokens` 的存留時間，而這是伺服器在 `SPNego` 或 `SSL` 交涉之後發出的存留時間。 伺服器在這段時間內會快取 `SecurityContextToken`。  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>：控制在伺服器中建立的安全對話上限，但是不會針對這些對話處理應用程式訊息。 這個配額會防止用戶端在服務中建立安全對話，由此服務會針對每個用戶端保留對話狀態，但不會使用這些對話。  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>：控制服務將安全對話保留在作用中，而不會從用戶端中接收該對話之應用程式訊息的時間上限。 這個配額會防止用戶端在服務中建立安全對話，由此服務會針對每個用戶端保留對話狀態，但不會使用這些對話。  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding 或雙重自訂繫結需要用戶端驗證  
 根據預設，<xref:System.ServiceModel.WSDualHttpBinding> 已啟用安全性。 不過，如果透過將 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> 屬性設定為 <xref:System.ServiceModel.MessageCredentialType.None> 而停用用戶端驗證，則惡意使用者可能在第三個服務上導致阻絕服務攻擊。 可能是因為惡意用戶端可以導向至服務，並將訊息資料流傳送至第三個服務。  
  
 若要避免這個情況，請不要將屬性設定為 `None`。 建立具有雙重訊息模式的自訂繫結程序時，也請留意這個可能性。  
  
## <a name="auditing-event-log-can-be-filled"></a>稽核事件記錄檔已滿  
 如果惡意使用者發現已啟用稽核，攻擊者就可以傳送無效的訊息，而造成寫入稽核項目。 如果是因為這個方法而填滿稽核記錄檔，稽核系統就會失敗。  
  
 若要減輕這個威脅，請將 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> 屬性設定為 `true`，並使用 [事件檢視器] 的屬性來控制稽核行為。 如需使用事件檢視器來查看和管理事件記錄檔的詳細資訊, 請參閱[事件檢視器](https://go.microsoft.com/fwlink/?LinkId=186123)。 如需詳細資訊, 請參閱「[審核](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)」。  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-to-become-unresponsive"></a>不正確 IAuthorizationPolicy 的執行可能導致服務變成沒有回應  
 在發生錯誤的<xref:System.IdentityModel.Policy.IAuthorizationPolicy>介面執行上呼叫方法,可能會導致服務沒有回應。<xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A>  
  
 風險降低：僅使用信任的程式碼。 也就是說，僅使用您所撰寫並測試過的程式碼，或使用來自可信任提供者的程式碼。 在沒有謹慎的考慮之前，請勿將不受信任的 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 延伸項目外掛至您的程式碼。 這個做法適用於服務實作中使用的所有延伸項目。 WCF 不會區分使用擴充點插入的應用程式代碼和外部程式碼。  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>可能需要調整 Kerberos 權杖的大小上限  
 如果用戶端是許多群組的成員 (大約 900 個群組，不過實際數目會因群組而有所不同)，當訊息標頭的區塊超過 64 KB 時，可能會發生問題。 在這種情況下, 您可以增加最大的 Kerberos 權杖大小, 如 Microsoft 支援服務文章: 「[Internet Explorer Kerberos 驗證因為連接到 IIS 的緩衝區不足而無法運作](https://go.microsoft.com/fwlink/?LinkId=89176)」中所述。 您也可能需要增加 WCF 訊息大小上限, 以容納較大的 Kerberos 權杖。  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>自動註冊將使電腦中的多個憑證具有相同的主體名稱  
 自動*註冊*是一項[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]功能, 可自動為憑證註冊使用者和電腦。 當電腦在需要啟用功能的需求上開啟時，就會自動建立具有預期用戶端驗證用途的 X.509 憑證，而每當新電腦加入網路時，也會將此憑證插入本機電腦的「個人」憑證存放區。 不過，自動註冊會對在快取中建立的所有憑證，都使用同樣的主體名稱。  
  
 影響是 WCF 服務可能無法在具有自動註冊的網域上開啟。 這是因為預設服務 X.509 認證搜尋準則可能不明確，起因則為存在多個具有電腦完整網域名稱系統 (DNS) 名稱的憑證。 某個憑證可能源自自動註冊，而其他憑證可能為自行發行的憑證。  
  
 若要減輕此問題, 請使用[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)上更精確的搜尋準則, 來參考要使用的確切憑證。 例如，請使用 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> 選項，並依照其唯一指紋 (雜湊) 指定憑證。  
  
 如需自動註冊功能的詳細資訊, 請參閱[Windows Server 2003 中的憑證自動註冊](https://go.microsoft.com/fwlink/?LinkId=95166)。  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>最後幾個用於授權的多個替代主體名稱  
 在少數情況下，當 X.509 憑證包含多個替代主體名稱，而且您使用替代主體名稱進行授權時，授權可能會失敗。  
  
## <a name="protect-configuration-files-with-acls"></a>使用 ACL 保護組態檔  
 您可以針對 CardSpace 發行的權杖, 指定程式碼和設定檔案中的必要和選擇性宣告。 這樣會造成在傳送至安全性權杖服務的 `RequestSecurityToken` 訊息中發出相對應的項目。 攻擊者可以修改程式碼或組態以移除必要或選用的宣告，這樣便有可能取得安全性權杖服務，而發出不允許存取目標服務的權杖。  
  
 若要減輕下列問題:需要電腦的存取權才能修改設定檔。 使用檔案存取控制清單 (ACL) 以保護組態檔。 WCF 需要在應用程式目錄或全域組件快取中, 才會允許從設定載入這類程式碼。 使用目錄 ACL 以保護目錄。  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>達到服務之安全工作階段數上限  
 當服務順利驗證用戶端而且是藉由服務建立安全工作階段時，服務會持續追蹤工作階段，直到用戶端取消服務或工作階段到期為止。 每個建立的工作階段都不利於服務之同時作用中工作階段的數量上限。 達到這個限制時，將會拒絕嘗試以該服務建立新工作階段的用戶端，直到一或多個作用中工作階段到期或由用戶端所取消為止。 用戶端在服務中可以擁有多個工作階段，而且會對該限制計數每個工作階段。  
  
> [!NOTE]
> 當您使用具狀態的工作階段時，之前的段落就沒有作用。 如需可設定狀態會話的詳細[資訊, 請參閱如何:為安全會話](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)建立安全性內容權杖。  
  
 若要避免這個情況，請設定 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 屬性，以設定作用中工作階段數的上限和工作階段的最長存留時間。  
  
## <a name="see-also"></a>另請參閱

- [安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [資訊洩漏](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [權限提高](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [阻絕服務](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [重新執行攻擊](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [竄改](../../../../docs/framework/wcf/feature-details/tampering.md)
- [不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
