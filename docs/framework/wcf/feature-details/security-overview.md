---
title: 安全性概觀
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
ms.openlocfilehash: e7dd73b755c7aed91a1fd59baaf9d5e090a36768
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541457"
---
# <a name="windows-communication-foundation-security-overview"></a>Windows Communication Foundation 安全性概觀
Windows Communication Foundation (WCF) 是以 SOAP 訊息為基礎的分散式程式設計平臺，而且用戶端與服務之間的訊息安全對於保護資料而言是不可或缺的。 WCF 提供了一個靈活且互通的平臺，可根據現有的安全性基礎結構和 SOAP 訊息的可辨識安全性標準來交換安全訊息。  
  
> [!NOTE]
> 如需 WCF 安全性的完整指南，請參閱 [Wcf 安全性指引](https://archive.codeplex.com/?p=WCFSecurity)。  
  
 如果您建立了具有現有技術（例如 HTTPS、Windows 整合式安全性或使用者名稱和密碼）的安全、分散式應用程式來驗證使用者，則 WCF 會使用熟悉的概念。 WCF 不僅能與現有的安全性基礎結構整合，還可以使用安全的 SOAP 訊息，將分散式安全性延伸至僅限 Windows 的網域。 除了現有的通訊協定之外，請將 WCF 視為採用 SOAP 做為通訊協定的主要優點，來實行現有的安全性機制。 例如，識別用戶端或服務的認證 (如使用者名稱和密碼，或 X.509 憑證) 有互通的 XML 架構 SOAP 設定檔。 使用這些設定檔，訊息可以利用像 XML 數位簽章和 XML 加密的開放規格，來安全交換。 如需規格的清單，請參閱 [由系統提供的互通性系結所支援的 Web 服務通訊協定](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)。  
  
 這和 Windows 平台上的元件物件模型 (Component Object Model，COM) 很相似，後者會啟用安全、分散式應用程式。 COM 有功能齊全的安全性機制，藉此安全性內容可以在元件間流動，這個機制會強制完整性、機密性和驗證。 不過，COM 不會啟用跨平臺的安全訊息，例如 WCF。 您可以使用 WCF 來建立跨網際網路的 Windows 網域的服務和用戶端。 WCF 可互通的訊息是建立動態商務導向服務的必要條件，可協助您安心瞭解資訊的安全性。  
  
## <a name="windows-communication-foundation-security-benefits"></a>Windows Communication Foundation 安全性優點  
 WCF 是以 SOAP 訊息為基礎的分散式程式設計平臺。 您可以使用 WCF 來建立可同時作為服務和服務用戶端的應用程式，以及從不限數目的其他服務和用戶端建立和處理訊息。 在這類的分散式應用程式中，訊息可以在節點間流動、通過防火牆、在網際網路上流動，以及通過多個 SOAP 媒介。 這會引入各種訊息安全性威脅。 下列範例說明 WCF 安全性在實體之間交換訊息時，可協助減輕的一些常見威脅：  
  
- 觀察網路流量以取得敏感資訊。 例如，在線上銀行的案例中，用戶端會要求從某個帳戶轉帳至另一個帳戶。 惡意使用者會攔截訊息，在取得帳戶號碼和密碼後，從入侵的帳戶轉帳。  
  
- 駭客實體作用為服務，但用戶端並不知情。 在這個案例中，惡意使用者 (駭客) 會作用為線上服務，從用戶端攔截訊息，以取得敏感資訊。 然後，駭客會使用竊取的資料，從破解入侵的帳戶轉帳。 這項攻擊也稱為 *網路釣魚攻擊*。  
  
- 修改訊息，以取得不同於呼叫者預期的結果。 例如，修改帳戶號碼，讓存款存入 rogue 帳戶。  
  
- 駭客重新執行，駭客會重新執行相同採購單來進行騷擾。 例如，線上書店接收數以百計的訂單，並將書籍傳送至未訂購的客戶。  
  
- 服務無法驗證用戶端。 在這種情況下，服務無法確定適當人員執行異動。  
  
 摘要說明，傳輸安全性提供了下列保證：  
  
- 服務端點 (應答者) 驗證。  
  
- 用戶端主體 (啟動器) 驗證。  
  
- 訊息完整性。  
  
- 訊息機密性。  
  
- 重新執行偵測。  
  
### <a name="integration-with-existing-security-infrastructures"></a>與現有安全性基礎結構整合  
 通常 Web 服務部署會就地使用現有安全性方案，例如，Secure Sockets Layer (SSL) 或 Kerberos 通訊協定。 有些會利用已部署的安全性基礎結構，例如使用 Active Directory 的 Windows 網域。 通常必須與這些現有技術整合，同時評估及採用新技術。  
  
 WCF 安全性與現有的傳輸安全性模型整合，並且可以根據 SOAP 訊息安全性，運用現有的基礎結構來進行較新的傳輸安全性模型。  
  
### <a name="integration-with-existing-authentication-models"></a>與現有驗證模型整合  
 任何通訊安全性模型的重要部分是識別及驗證通訊中實體的能力。 這些通訊中實體會使用「數位身分識別」(或認證)，向通訊對等驗證自身。 隨著分散式通訊平台發展，已實作各種認證驗證和相關的安全性模型。 例如，在網際網路上，用來識別使用者的使用者名稱和密碼很普及。 在內部網路上，用來支援使用者和服務驗證的 Kerberos 網域控制站也逐漸普及。 在某些情況下，例如在兩個商業夥伴之間，憑證可以用來相互驗證夥伴。  
  
 因此，在 Web 服務的世界中，相同服務可能同時對內部公司客戶、外部夥伴或網際網路客戶公開，基礎結構必須與現有安全性驗證模型整合，變得很重要。 WCF 安全性可支援各種不同的認證類型 (驗證模型) 包括：  
  
- 匿名呼叫者。  
  
- 使用者名稱用戶端認證。  
  
- 憑證用戶端認證。  
  
- Windows (Kerberos 通訊協定和 NT LanMan [NTLM] 兩者)。  
  
### <a name="standards-and-interoperability"></a>標準和互通性  
 在大型現有部署的世界中，同質性很少見。 分散式運算/通訊平台必須與來自不同廠商的技術交互操作。 同樣的，安全性也必須是互通的。  
  
 為了啟用互通的安全性系統，Web 服務業界中積極參與的公司已經設計各種標準。 特別關於安全性，已提出一些知名的標準：Web 服務安全性：SOAP 訊息安全性 (已由 OASIS 標準組織接受，以前稱為 Web 服務安全性)、WS-Trust、WS-SecureConversation 和 WS-SecurityPolicy。  
  
 WCF 支援各種互通性案例。 <xref:System.ServiceModel.BasicHttpBinding> 類別的目標為 Basic Security Profile (BSP)，而 <xref:System.ServiceModel.WSHttpBinding> 類別的目標則是最新的安全性標準，例如 WS-Security 1.1 和 WS-SecureConversation。 藉由遵守這些標準，WCF 安全性可相交互操作並與裝載于 Microsoft Windows 以外的作業系統和平臺上的 Web 服務整合。  
  
## <a name="wcf-security-functional-areas"></a>WCF 安全性功能區域  
 WCF 安全性分為三個功能區域：傳輸安全性、存取控制和審核。 下列各節會簡要討論這些區域，並提供詳細資訊的連結。  
  
### <a name="transfer-security"></a>傳輸安全性  
 傳輸安全性涵蓋三個主要的安全性功能：完整性、機密性和驗證。 *完整性* 是指偵測訊息是否已遭篡改的能力。 *機密性* 是讓非預期的收件者無法讀取訊息的能力;這是透過密碼編譯來達成。 *驗證* 是驗證宣告身分識別的能力。 這三個功能合起來有助於確保訊息從某一點安全送達另一點。  
  
#### <a name="transport-and-message-security-modes"></a>傳輸和訊息安全性模式  
 您可以使用兩種主要機制，在 WCF 中執行傳輸安全性： *傳輸* 安全性模式和 *訊息* 安全性模式。  
  
- *傳輸安全性模式* 會使用傳輸層級的通訊協定（例如 HTTPS）來達到傳輸安全性。 傳輸模式的優點是已廣為採用、可使用於許多平台，且運算較不複雜。 但缺點是只確保訊息點對點安全性。  
  
- 相反地，*訊息安全性模式*會使用 WS-security (和其他規格) 來執行傳輸安全性。 因為訊息安全性是直接套用至 SOAP 訊息，並且會與應用程式資料包含在 SOAP 封套中，所以它的優點是與傳輸通訊協定無關、更具擴充性和確保端對端安全性 (相對於點對點)。因為必須處理 SOAP 訊息的 XML 特性，它的缺點是比傳輸安全性慢上好幾倍。  
  
 如需有關這些差異的詳細資訊，請參閱 [保護服務與用戶端](securing-services-and-clients.md)。  
  
 第三個安全性模式同時使用前兩個模式，且結合兩者的優點。 這個模式稱為 `TransportWithMessageCredential`。 在這個模式中，訊息安全性會用來驗證用戶端，而傳輸安全性則會用來驗證伺服器及提供訊息機密性和完整性。 `TransportWithMessageCredential` 安全性模式因此受惠，幾乎與傳輸安全性模式一樣快速，並且以訊息安全性的相同方式提供用戶端驗證擴充性。 不過，不像訊息安全性模式，它不會提供完整的端對端安全性。  
  
### <a name="access-control"></a>存取控制  
 *存取控制* 也稱為授權。 *授權* 可讓不同的使用者具有不同的許可權來查看資料。 例如，因為公司的人力資源檔案包含敏感的員工資料，所以只有經理才能檢視員工資料。 而且，經理只能檢視其直屬員工的資料。 在這種情況下，存取控制是根據角色 (「經理」) 和經理的特定身分識別 (以防止某個經理查看另一個經理的員工記錄)。  
  
 在 WCF 中，存取控制功能是透過整合 common language runtime (CLR) <xref:System.Security.Permissions.PrincipalPermissionAttribute> ，以及透過一組稱為「身分 *識別模型*」的 api 來提供。 如需存取控制和以宣告為基礎的授權詳細資訊，請參閱 [擴充安全性](../extending/extending-security.md)。  
  
### <a name="auditing"></a>稽核  
 *審核* 是將安全性事件記錄至 Windows 事件記錄檔。 您可以記錄安全性相關的事件，例如驗證失敗 (或成功)。 如需詳細資訊，請參閱「 [審核](auditing-security-events.md)」。 如需程式設計詳細資料，請參閱 [如何：審核安全性事件](how-to-audit-wcf-security-events.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [保護服務的安全](../securing-services.md)
- [常見的安全性案例](common-security-scenarios.md)
- [繫結和安全性](bindings-and-security.md)
- [確保服務與用戶端的安全](securing-services-and-clients.md)
- [驗證](authentication-in-wcf.md)
- [授權](authorization-in-wcf.md)
- [聯合與發行的權杖](federation-and-issued-tokens.md)
- [稽核](auditing-security-events.md)
- [安全性指引與最佳做法](security-guidance-and-best-practices.md)
- [使用組態檔設定服務](../configuring-services-using-configuration-files.md)
- [系統提供的繫結](../system-provided-bindings.md)
- [端點建立概觀](../endpoint-creation-overview.md)
- [擴充安全性](../extending/extending-security.md)
- [Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))
