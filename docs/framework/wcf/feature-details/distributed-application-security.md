---
title: "分散式應用程式安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "分散式應用程式安全性 [WCF]"
  - "安全性 [WCF], 傳輸"
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
caps.latest.revision: 32
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 32
---
# 分散式應用程式安全性
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 安全性分為三個主要的功能區域：傳輸安全性、存取控制和稽核。傳輸安全性提供完整性、機密性與驗證。傳輸安全性是由下列其中一項提供：傳輸安全性、訊息安全性或 `TransportWithMessageCredential`。  
  
 如需 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 訊息安全性的概觀，請參閱[安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)。[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 其他兩項 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性的詳細資訊，請參閱[授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)和[稽核](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)。  
  
## 傳輸安全性案例  
 採用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 傳輸安全性的常見案例包括下列各項：  
  
-   使用 Windows 保護傳輸。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端和服務會部署在 Windows 網域中 \(或 Windows 樹系\)。由於訊息包含個人資料，因此要求會包括用戶端和服務的雙向驗證、訊息完整性及訊息機密性。此外，特殊交易發生時需要證明，例如訊息接收者應記錄簽章資訊。  
  
-   使用 `UserName` 和 HTTPS 保護傳輸。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端和服務需要經過開發才能跨網際網路運作。用戶端認證會根據使用者名稱\/密碼組的資料庫進行驗證。服務會使用受信任的安全通訊端層 \(SSL\) 憑證部署在 HTTPS 位址。由於訊息會透過網際網路傳輸，因此用戶端和服務需要經過雙向驗證，而且必須維持傳輸期間訊息的機密性與完整性。  
  
-   使用憑證保護傳輸。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端和服務需要經過開發才能透過公用網際網路運作。用戶端和服務都有憑證，可以用來保護訊息的安全。用戶端和服務會使用網際網路彼此通訊，以及執行要求有訊息完整性、機密性與雙向驗證的高價值交易。  
  
## 完整性、機密性與驗證  
 完整性、機密性及驗證這三項功能合稱為傳輸安全性。傳輸安全性所提供的各種功能，會協助減少分散式應用程式的威脅。下表簡要說明構成傳輸安全性的這三項功能。  
  
|功能|描述|  
|--------|--------|  
|完整性|*完整性*是指保證資料完整且正確，尤其是在資料從某個端點傳送到另一個端點，而且可能已有許多參與者讀取過之後。完整性必須維持，才能避免資料竄改，而且通常是藉由訊息數位簽署達成這個目的。|  
|機密性|*機密性*是指保證訊息未被原本指定的讀者以外的人讀取。例如，信用卡號在透過網際網路傳送時必須保持其機密。機密性通常是藉由使用公開金鑰\/私密金鑰配置加密資料的方式提供。|  
|驗證|*驗證*是指對宣告識別的驗證例如，使用銀行帳戶時，必須只允許實際的帳戶擁有人提款。驗證可藉由各種方法提供。其中一種常見的方法是使用者帳號\/密碼系統。另一種方式則是使用由協力廠商提供的 X.509 憑證。|  
  
## 安全性模式  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 有數種傳輸安全性模式，將在下表中加以說明。  
  
|模式|描述|  
|--------|--------|  
|無|未在傳輸層或訊息層提供任何安全性。除了 [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 項目或使用程式碼時的 <xref:System.ServiceModel.BasicHttpBinding> 類別之外，沒有任何預先定義的繫結預設為使用此模式。|  
|傳輸|使用安全傳輸 \(例如 HTTPS\) 以獲得完整性、機密性和雙向驗證。|  
|訊息|使用 SOAP 訊息安全性，以獲得完整性、機密性和雙向驗證。SOAP 訊息是根據 WS\-Security 標準加以保護。|  
|混合模式|使用傳輸安全性，以獲得完整性、機密性和伺服器驗證。使用訊息安全性 \(WS\-Security 和其他標準\) 以獲得用戶端驗證。<br /><br /> \(此模式的列舉型別為 `TransportWithMessageCredential`\)|  
|兩種模式|在兩個層級執行保護和驗證。此模式只適用於 [\<netMsmqBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) 項目。|  
  
## 認證和傳輸安全性  
 *認證*是指代表用來建立所宣告之識別或功能的資料。出示認證同時包含出示資料和資料的所有權證明。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援傳輸和訊息安全層級的各種認證類型。您可以針對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結指定認證類型。  
  
 在許多國家或地區，駕駛執照就是認證的一個範例。執照包含代表一個人身分識別和能力的資料。其中包含以持有人的照片做為所有權的證明。執照是由受信任的授權單位發出，通常是政府的發照部門。執照會經過密封，而且可能內含雷射防偽，表示沒有遭到竄改或偽造。  
  
 例如，請試想 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中支援的兩種認證類型：使用者名稱和 \(X.509\) 憑證認證。  
  
 對於使用者名稱認證，使用者名稱代表宣告的身分識別，而密碼代表所有權的證明。在此案例中，受信任的授權單位是驗證使用者名稱和密碼的系統。  
  
 在憑證認證中，主體名稱、主體別名或憑證內的特定欄位可用來代表所宣告的身分識別和 \(或\) 能力。認證中資料所有權的證明，是使用相關的私密金鑰產生簽章的方式建立。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 程式設計傳輸安全性和指定認證的詳細資訊，請參閱[繫結和安全性](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)和[安全性行為](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)。  
  
### 傳輸用戶端認證類型  
 下表說明建立使用傳輸安全性的應用程式時，可能使用的值。您可以在程式碼或繫結設定中使用這些值。  
  
|設定|描述|  
|--------|--------|  
|無|指定用戶端不需要提出任何認證。這會轉譯成匿名用戶端。|  
|Basic|指定基本驗證。如需其他資訊，請參閱 RFC2617「[HTTP 驗證：基本與摘要式驗證](http://go.microsoft.com/fwlink/?LinkId=88313)」\(本頁面可能為英文\)。|  
|摘要式|指定摘要式驗證。如需其他資訊，請參閱 RFC2617「[HTTP 驗證：基本與摘要式驗證](http://go.microsoft.com/fwlink/?LinkId=88313)」\(本頁面可能為英文\)。|  
|Ntlm|指定在 Windows 網域上使用 SSPI 交涉的 Windows 驗證。<br /><br /> SSPI 交涉的結果會是使用 Kerberos 通訊協定或 NT LanMan \(NTLM\)。|  
|Windows|指定在 Windows 網域上使用 SSPI 的 Windows 驗證。SSPI 會挑選 Kerberos 通訊協定或 NTLM 做為驗證服務。<br /><br /> SSPI 會先嘗試 Kerberos 通訊協定，如果失敗的話，才會使用 NTLM。|  
|憑證|使用憑證 \(通常是 X.509\) 執行用戶端驗證。|  
  
### 訊息用戶端認證類型  
 下表說明建立使用訊息安全性的應用程式時，可能使用的值。您可以在程式碼或繫結設定中使用這些值。  
  
|設定|描述|  
|--------|--------|  
|無|允許服務與匿名用戶端互動。|  
|Windows|允許在 Windows 認證的已驗證內容中發生 SOAP 訊息交換。使用 SSPI 交涉機制挑選 Kerberos 通訊協定或 NTLM 做為驗證服務。|  
|使用者名稱|允許服務要求用戶端必須使用使用者名稱認證進行驗證。請注意，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不允許任何利用使用者名稱的密碼編譯作業，例如產生簽章或加密資料。基於這個理由，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會在利用使用者名稱認證時，強制保護傳輸安全。|  
|憑證|允許服務要求用戶端使用憑證進行驗證。|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|允許服務要求用戶端以 [!INCLUDE[infocard](../../../../includes/infocard-md.md)] 進行驗證。|  
  
### 程式設計認證  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 程式設計模型允許您使用服務行為和通道行為，針對每一種用戶端認證類型指定認證值和認證驗證程式。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性有兩種類型的認證：服務認證行為和通道認證行為。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的認證行為會指定實際資料，也就是用來符合透過繫結表示的安全性需求的認證。在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，用戶端類別是執行階段元件，會在作業引動和訊息之間進行轉換。所有用戶端都是繼承自 <xref:System.ServiceModel.ClientBase%601> 類別。基底類別上的 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 屬性可讓您指定各種用戶端認證的值。  
  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，服務行為是套用至類別的屬性 \(Attribute\)，此類別實作了服務合約 \(介面\)，以程式設計的方式控制服務。<xref:System.ServiceModel.Description.ServiceCredentials> 類別可讓您指定服務認證的憑證，以及各種用戶端認證類型的用戶端驗證設定。  
  
### 訊息安全性的交涉模型  
 訊息安全性模式可讓您執行傳輸安全性，如此服務認證就會在用戶端超出範圍時設定。例如，如果您使用儲存在 Windows 憑證存放區中的憑證，就必須使用 Microsoft Management Console \(MMC\) 嵌入式管理單元這類的工具。  
  
 訊息安全性模式還可讓您執行傳輸安全性，如此服務認證就會在初始交涉的過程中與用戶端交換。若要啟用交涉，請將 <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> 屬性設為 `true`。  
  
## 請參閱  
 [端點建立概觀](../../../../docs/framework/wcf/endpoint-creation-overview.md)   
 [系統提供的繫結](../../../../docs/framework/wcf/system-provided-bindings.md)   
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Windows Server AppFabric 的資訊安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)