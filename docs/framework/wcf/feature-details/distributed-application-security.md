---
title: 分散式應用程式安全性
ms.date: 03/30/2017
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
ms.openlocfilehash: 70718b5dfbd54693d2734a58c3da17806137ad2f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557537"
---
# <a name="distributed-application-security"></a>分散式應用程式安全性
Windows Communication Foundation (WCF) 安全性分為三個主要功能領域：傳輸安全性、存取控制和審核。 傳輸安全性提供完整性、機密性與驗證。 傳輸安全性是由下列其中一項提供：傳輸安全性、訊息安全性或 `TransportWithMessageCredential`。  
  
 如需 WCF 訊息安全性的總覽，請參閱 [安全性概觀](security-overview.md)。 如需 WCF 安全性的其他兩個部分的詳細資訊，請參閱 [授權](authorization-in-wcf.md) 和 [審核](auditing-security-events.md)。  
  
## <a name="transfer-security-scenarios"></a>傳輸安全性案例  
 使用 WCF 傳輸安全性的常見案例包括下列各項：  
  
- 使用 Windows 保護傳輸。 WCF 用戶端和服務會部署在 Windows 網域 (或 Windows 樹系) 中。 由於訊息包含個人資料，因此要求會包括用戶端和服務的雙向驗證、訊息完整性及訊息機密性。 此外，特殊交易發生時需要證明，例如訊息接收者應記錄簽章資訊。  
  
- 使用 `UserName` 和 HTTPS 保護傳輸。 必須開發 WCF 用戶端和服務，才能在網際網路上運作。 用戶端認證會根據使用者名稱/密碼組的資料庫進行驗證。 服務會使用受信任的安全通訊端層 (SSL) 憑證部署在 HTTPS 位址。 由於訊息會透過網際網路傳輸，因此用戶端和服務需要經過雙向驗證，而且必須維持傳輸期間訊息的機密性與完整性。  
  
- 使用憑證保護傳輸。 必須開發 WCF 用戶端和服務，才能透過公用網際網路運作。 用戶端和服務都有憑證，可以用來保護訊息的安全。 用戶端和服務會使用網際網路彼此通訊，以及執行要求有訊息完整性、機密性與雙向驗證的高價值交易。  
  
## <a name="integrity-confidentiality-and-authentication"></a>完整性、機密性與驗證  
 完整性、機密性及驗證這三項功能合稱為傳輸安全性。 傳輸安全性所提供的各種功能，會協助減少分散式應用程式的威脅。 下表簡要說明構成傳輸安全性的這三項功能。  
  
|函式|描述|  
|--------------|-----------------|  
|完整性|*完整性* 可保證資料是完整且精確的，尤其是在從某個點到另一個點，而且可能被許多動作專案讀取之後。 完整性必須維持，才能避免資料竄改，而且通常是藉由訊息數位簽署達成這個目的。|  
|機密性|*機密性* 可保證除了預期的讀者之外，還不會讀取訊息。 例如，信用卡號在透過網際網路傳送時必須保持其機密。 機密性通常是藉由使用公開金鑰/私密金鑰配置加密資料的方式提供。|  
|驗證|*驗證* 是宣告身分識別的驗證。 例如，使用銀行帳戶時，必須只允許實際的帳戶擁有人提款。 驗證可藉由各種方法提供。 其中一種常見的方法是使用者帳號/密碼系統。 另一種方式則是使用由協力廠商提供的 X.509 憑證。|  
  
## <a name="security-modes"></a>安全性模式  
 WCF 有數種傳輸安全性模式，如下表所述。  
  
|[模式]|描述|  
|----------|-----------------|  
|None|未在傳輸層或訊息層提供任何安全性。 除了專案或使用程式碼時，任何預先定義的系結預設都不會使用此模式 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) <xref:System.ServiceModel.BasicHttpBinding> 。|  
|傳輸|使用安全傳輸 (例如 HTTPS) 以獲得完整性、機密性和雙向驗證。|  
|訊息|使用 SOAP 訊息安全性，以獲得完整性、機密性和雙向驗證。 SOAP 訊息是根據 WS-Security 標準加以保護。|  
|混合模式|使用傳輸安全性，以獲得完整性、機密性和伺服器驗證。 使用訊息安全性 (WS-Security 和其他標準) 以獲得用戶端驗證。<br /><br /> (此模式的列舉型別為 `TransportWithMessageCredential`)|  
|兩者|在兩個層級執行保護和驗證。 此模式只適用于 [\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md) 元素。|  
  
## <a name="credentials-and-transfer-security"></a>認證和傳輸安全性  
 認證是為了建立宣告的 *身分* 識別或功能所呈現的資料。 出示認證包括出示資料以及資料的所有權證明。 WCF 支援傳輸和訊息安全性層級的各種認證類型。 您可以指定 WCF 系結的認證類型。  
  
 在許多國家或地區，駕駛執照就是認證的一個範例。 執照包含代表一個人身分識別和能力的資料。 其中包含以持有人的照片做為所有權的證明。 執照是由受信任的授權單位發出，通常是政府的發照部門。 執照會經過密封，而且可能內含雷射防偽，表示沒有遭到竄改或偽造。  
  
 例如，請考慮在 WCF 中支援兩種類型的認證：使用者名稱和 (x.509) 憑證認證。  
  
 對於使用者名稱認證，使用者名稱代表宣告的身分識別，而密碼代表所有權的證明。 在此案例中，受信任的授權單位是驗證使用者名稱和密碼的系統。  
  
 在憑證認證中，主體名稱、主體別名或憑證內的特定欄位可用來代表所宣告的身分識別和 (或) 能力。 認證中資料所有權的證明，是使用相關的私密金鑰產生簽章的方式建立。  
  
 如需程式設計傳輸安全性和指定認證的詳細資訊，請參閱系結 [和安全性](bindings-and-security.md) 和 [安全性行為](security-behaviors-in-wcf.md)。  
  
### <a name="transport-client-credential-types"></a>傳輸用戶端認證類型  
 下表說明建立使用傳輸安全性的應用程式時，可能使用的值。 您可以在程式碼或繫結設定中使用這些值。  
  
|設定|描述|  
|-------------|-----------------|  
|None|指定用戶端不需要提出任何認證。 這會轉譯成匿名用戶端。|  
|基本|指定基本驗證。 如需詳細資訊，請參閱 RFC2617、[HTTP 驗證：基本與摘要式驗證](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)。|  
|Digest|指定摘要式驗證。 如需詳細資訊，請參閱 RFC2617、[HTTP 驗證：基本與摘要式驗證](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)。|  
|Ntlm|指定在 Windows 網域上使用 SSPI 交涉的 Windows 驗證。<br /><br /> SSPI 交涉的結果會是使用 Kerberos 通訊協定或 NT LanMan (NTLM)。|  
|Windows|指定在 Windows 網域上使用 SSPI 的 Windows 驗證。 SSPI 會挑選 Kerberos 通訊協定或 NTLM 做為驗證服務。<br /><br /> SSPI 會先嘗試 Kerberos 通訊協定，如果失敗的話，才會使用 NTLM。|  
|憑證|使用憑證 (通常是 X.509) 執行用戶端驗證。|  
  
### <a name="message-client-credential-types"></a>訊息用戶端認證類型  
 下表說明建立使用訊息安全性的應用程式時，可能使用的值。 您可以在程式碼或繫結設定中使用這些值。  
  
|設定|描述|  
|-------------|-----------------|  
|None|允許服務與匿名用戶端互動。|  
|Windows|允許在 Windows 認證的已驗證內容中發生 SOAP 訊息交換。 使用 SSPI 交涉機制挑選 Kerberos 通訊協定或 NTLM 做為驗證服務。|  
|使用者名稱|允許服務要求用戶端必須使用使用者名稱認證進行驗證。 請注意，WCF 不允許任何使用使用者名稱的密碼編譯作業，例如產生簽章或加密資料。 因此，WCF 會在使用使用者名稱認證時強制保護傳輸。|  
|憑證|允許服務要求用戶端使用憑證進行驗證。|  
|CardSpace|允許服務要求用戶端使用 CardSpace 進行驗證。|  
  
### <a name="programming-credentials"></a>程式設計認證  
 針對每個用戶端認證類型，WCF 程式設計模型可讓您使用服務行為和通道行為來指定認證值和認證驗證程式。  
  
 WCF 安全性有兩種類型的認證：服務認證行為和通道認證行為。 WCF 中的認證行為會指定實際資料，也就是用來符合透過系結表示之安全性需求的認證。 在 WCF 中，用戶端類別是執行時間元件，可在作業調用和訊息之間進行轉換。 所有用戶端都是繼承自 <xref:System.ServiceModel.ClientBase%601> 類別。 基底類別上的 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 屬性可讓您指定各種用戶端認證的值。  
  
 在 WCF 中，服務行為是套用至類別的屬性，這些屬性是用來執行服務合約 (介面) ，以程式設計方式控制服務。 <xref:System.ServiceModel.Description.ServiceCredentials> 類別可讓您指定服務認證的憑證，以及各種用戶端認證類型的用戶端驗證設定。  
  
### <a name="negotiation-model-for-message-security"></a>訊息安全性的交涉模型  
 訊息安全性模式可讓您執行傳輸安全性，如此服務認證就會在用戶端超出範圍時設定。 例如，如果您使用儲存在 Windows 憑證存放區中的憑證，就必須使用 Microsoft Management Console (MMC) 嵌入式管理單元這類的工具。  
  
 訊息安全性模式還可讓您執行傳輸安全性，如此服務認證就會在初始交涉的過程中與用戶端交換。 若要啟用交涉，請將 <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> 屬性設為 `true`。  
  
## <a name="see-also"></a>另請參閱

- [端點建立概觀](../endpoint-creation-overview.md)
- [系統提供的繫結](../system-provided-bindings.md)
- [安全性概觀](security-overview.md)
- [Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))
