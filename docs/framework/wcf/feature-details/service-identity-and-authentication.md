---
title: "服務身分識別和驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19ff205fd1e76a5d2ee787522cc5d94916b0c11c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="service-identity-and-authentication"></a>服務身分識別和驗證
服務的*端點身分識別*是從服務 Web 服務描述語言 (WSDL) 產生的值。 這個值會傳播至任何用戶端上，用來驗證服務。 在用戶端初始化對某個端點的通訊，且服務也向用戶端進行自我驗證之後，用戶端就會比較端點身分識別值與端點驗證處理序傳回的實際值。 如果兩者相符，則可確定用戶端已聯繫所需的服務端點。 這項功能可以防範*網路釣魚*藉由防止用戶端重新導向至惡意服務所裝載的端點。  
  
 範例應用程式，示範身分識別設定，請參閱[服務身分識別範例](../../../../docs/framework/wcf/samples/service-identity-sample.md)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]端點和端點位址，請參閱[位址](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)。  
  
> [!NOTE]
>  當您使用 NT LanMan (NTLM) 進行驗證時，因為用戶端在 NTLM 協定下無法驗證伺服器，所以不會檢查服務身分識別。 當電腦是 Windows 工作群組的一部分，或者執行的是不支援 Kerberos 驗證的舊版 Windows 時，就會使用 NTLM。  
  
 當用戶端初始化安全通道以透過其傳送訊息至服務時，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 基礎結構會驗證服務，而且如果服務身分識別符合用戶端所使用之端點位址中指定的身分識別時，這個基礎結構只會傳送訊息。  
  
 身分識別處理包含下列階段：  
  
-   在設計階段，用戶端開發人員會從端點的中繼資料 (透過 WSDL 公開) 來決定服務的身分識別。  
  
-   在執行階段，用戶端應用程式會先檢查服務安全性認證的宣告，再將訊息傳送至服務。  
  
 用戶端上的身分識別處理與服務上的用戶端驗證很類似。 安全服務會等到用戶端認證經過驗證之後，才會執行程式碼。 同理，用戶端會等到服務認證根據事先從服務中繼資料得知的內容經過驗證之後，才會將訊息傳送至服務。  
  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A> 類別的 <xref:System.ServiceModel.EndpointAddress> 屬性代表用戶端所呼叫之服務的身分識別。 服務會在其中繼資料內發行 <xref:System.ServiceModel.EndpointAddress.Identity%2A>。 當用戶端開發人員執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)對服務端點，則產生的組態會包含值的服務的<xref:System.ServiceModel.EndpointAddress.Identity%2A>屬性。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構 (如果使用安全性來設定) 會確認服務是否具有指定的身分識別。  
  
> [!IMPORTANT]
>  中繼資料包含所需的服務身分識別，因此建議您透過安全方式來公開服務中繼資料，例如為服務建立 HTTPS 端點。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][How to： 安全中繼資料端點](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)。  
  
## <a name="identity-types"></a>身分識別類型  
 服務可以提供五種身分識別類型， 每種身分識別類型都會對應至可包含在組態 `<identity>` 項目中的某個項目。 所使用的類型會隨情況和服務的安全性需求而有所不同， 下表說明每種身分識別類型。  
  
|身分識別類型|描述|典型案例|  
|-------------------|-----------------|----------------------|  
|網域名稱系統 (DNS)|您可以使用此項目來搭配 X.509 憑證或 Windows 帳戶， 它會比較認證中指定的 DNS 名稱與此項目中指定的值。|DNS 檢查可讓您使用包含 DNS 或主體名稱的憑證。 如果重新發行的憑證包含相同的 DNS 或主體名稱，則身分識別檢查仍舊有效。 重新發行憑證時，憑證會取得新的 RSA 金鑰，但會保留相同的 DNS 或主體名稱， 表示用戶端不需要更新與服務相關的用戶端身分識別資訊。|  
|憑證。 當 `ClientCredentialType` 設為 Certificate 時的預設值。|此項目會指定 Base64 編碼格式的 X.509 憑證值，以便與用戶端進行比較。<br /><br /> 如果您使用 [!INCLUDE[infocard](../../../../includes/infocard-md.md)] 做為驗證服務的認證，也要使用此項目。|此項目會根據憑證的指紋值將驗證限制為單一憑證， 因為指紋值是唯一的，所以這麼做可以讓驗證更加嚴格， 同時也要特別注意，如果重新發行的憑證具有相同的主體名稱，也會具有新的指紋。 因此，用戶端必須先知道新的指紋，才能驗證服務。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]尋找憑證的指紋，請參閱[How to： 擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。|  
|憑證參考|與先前所述之「憑證」選項相同。 但是，這個項目可讓您指定憑證名稱與存放區位置，以便從中擷取憑證。|與先前所述之「憑證」案例相同。<br /><br /> 好處是憑證存放區位置可以變更。|  
|RSA|此項目會指定 RSA 金鑰值，以便與用戶端進行比較。 此選項與憑證選項很類似，但不是使用憑證的指紋，而是改為使用憑證的 RSA 金鑰。|RSA 檢查可讓您根據憑證的 RSA 金鑰將驗證限制為單一憑證， 雖然這個做法可以更嚴格地驗證 RSA 金鑰，但是如果 RSA 金鑰值改變，服務就再也無法與現有的用戶端一起使用。|  
|使用者主要名稱 (UPN)。 當 `ClientCredentialType` 設為 Windows，且服務處理序不是以其中一個系統帳戶執行時的預設值。|此項目會指定用來執行服務的 UPN。 請參閱 Kerberos 通訊協定和身分識別的[覆寫服務進行驗證的身分識別](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)。|這樣可確保服務在特定 Windows 使用者帳戶底下執行。 使用者帳戶可以是目前登入的使用者或是在特定使用者帳戶底下執行的服務。<br /><br /> 如果服務是在 Active Directory 環境中的網域帳戶底下執行，此設定便能充分善用 Windows Kerberos 安全性的優勢。|  
|服務主要名稱 (SPN)。 當 `ClientCredentialType` 設為 Windows，且服務處理序在 LocalService、LocalSystem 或 NetworkService 系統帳戶底下執行時的預設值。|此項目會指定與服務帳戶關聯的 SPN。 請參閱 Kerberos 通訊協定和身分識別的[覆寫服務進行驗證的身分識別](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)。|這樣可確保 SPN 及與其關聯之特定 Windows 帳戶都能識別服務。<br /><br /> 您可以使用 Setspn.exe 工具讓電腦帳戶與服務的使用者帳戶產生關聯。<br /><br /> 如果服務是在其中一個系統帳戶或具有相關 SPN 名稱的網域帳戶底下執行，而且電腦是 Active Directory 環境中的網域成員時，此設定便能充分善用 Windows Kerberos 安全性的優勢。|  
  
## <a name="specifying-identity-at-the-service"></a>指定服務端的身分識別  
 一般來說，您不需要在服務上設定身分識別，因為選擇用戶端認證類型，即表示服務中繼資料中公開的身分識別類型。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何覆寫或指定服務身分識別，請參閱[覆寫服務進行驗證的身分識別](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)。  
  
## <a name="using-the-identity-element-in-configuration"></a>使用\<識別 > 組態中的項目  
 如果您在先前對 `Certificate,` 顯示的繫結中變更用戶端認證類型，則產生的 WSDL 會包含 Base64 序列化 X.509 憑證做為身分識別值，如下列程式碼所示。 這是 Windows 以外所有用戶端認證類型的預設值。  
  
  
  
 您可以變更預設服務身分識別的值，或變更使用的身分識別類型`<identity>`組態或程式碼中設定的身分識別的項目。 下列組態程式碼會以 `contoso.com` 這個值來設定網域名稱系統 (DNS) 身分識別。  
  
  
  
## <a name="setting-identity-programmatically"></a>以程式設計方式設定身分識別  
 您的服務不需要明確指定身分識別，因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會自動決定。 不過，如果有需要，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可讓您指定端點上的身分識別。 下列程式碼會新增具有特定 DNS 身分識別的新服務端點。  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>指定用戶端的身分識別  
 在設計階段，用戶端開發人員通常會使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端設定。 產生的組態檔 (供用戶端使用) 會包含伺服器的身分識別。 例如，下列由服務產生的程式碼會指定 DNS 身分識別，如先前範例所示。 請注意，用戶端的端點身分識別值符合服務的身分識別值。 此時，如果用戶端接收服務的 Windows (Kerberos) 認證，值應該會是 `contoso.com`。  
  
  
  
 如果，服務 (而不是 Windows) 將憑證指定為用戶端認證類型，則憑證的 DNS 屬性應該會是 `contoso.com`  (或者，如果 DNS 屬性為 `null`，則憑證的主體名稱必須是 `contoso.com`)。  
  
#### <a name="using-a-specific-value-for-identity"></a>使用特定的身分識別值  
 下列用戶端組態檔說明服務的身分識別值如何成為所需的特定值。 在下列範例中，用戶端可與兩個端點進行通訊。 第一個端點是使用憑證指紋進行識別，而第二個則是使用憑證 RSA 金鑰。 也就是說，這個憑證只包含公用金鑰/私用金鑰組，不是由受信任的授權單位發行。  
  
  
  
## <a name="identity-checking-at-run-time"></a>執行階段的身分識別檢查  
 在設計階段，用戶端開發人員會透過伺服器的中繼資料來決定其身分識別。 在執行階段，系統會先執行身分識別檢查，然後再呼叫服務的任何端點。  
  
 身分識別值與中繼資料指定的驗證類型有關，換句話說，就是服務使用的認證類型。  
  
 如果通道已設為使用具有 X.509 憑證的訊息層級或傳輸層級 Secure Sockets Layer (SSL) 來進行驗證，則下列身分識別值有效：  
  
-   DNS： [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可確保在 SSL 交換期間提供的憑證包含 DNS，或者 `CommonName` (CN) 屬性，而此屬性等於在用戶端之 DNS 身分識別中指定的值。 請注意，除了判斷伺服器憑證是否有效，系統也會進行這些檢查。 根據預設，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會驗證伺服器憑證是由受信任的根授權所發行。  
  
-   憑證。 在 SSL 交換期間，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可確保遠端端點根據身分識別的指定提供正確的憑證值。  
  
-   憑證參考： 與「憑證」相同。  
  
-   RSA： 在 SSL 交換期間，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可確保遠端端點根據身分識別的指定提供正確的 RSA 金鑰。  
  
 如果服務使用具有 Windows 認證的訊息層級或傳輸層級 SSL 來進行驗證並交涉認證，則下列身分識別值有效：  
  
-   DNS： 交涉會傳遞服務的 SPN，以便檢查 DNS 名稱。 SPN 的形式為 `host/<dns name>`。  
  
-   SPN： 會傳回明確的服務 SPN，例如 `host/myservice`。  
  
-   UPN： 服務帳戶的 UPN。 UPN 的格式為`username` @ `domain`。 例如，當服務在使用者帳戶底下執行時，UPN 可能為 `username@contoso.com`。  
  
 您可以選擇以程式設計方式指定身分識別 (透過 <xref:System.ServiceModel.EndpointAddress.Identity%2A> 屬性)。 如果未指定任何身分識別，且用戶端認證類型為 Windows，則預設值為 SPN (其值設為服務端點位址的主機名稱部分，並於前面加上 "host/" 常值)。 如果未指定任何身分識別，且用戶端認證類型為憑證，則預設為 `Certificate`， 訊息層級與傳輸層級安全性都適用這個預設值。  
  
## <a name="identity-and-custom-bindings"></a>身分識別與自訂繫結  
 由於服務的身分識別取決於使用的繫結型別，所以建立自訂繫結時一定要公開適當的身分識別。 例如，在下列程式碼範例中，公開的身分識別與安全性類型不相容，因為安全對話啟動安裝繫結的身分識別與端點上的繫結身分識別不符。 安全對話繫結會設定 DNS 身分識別，而 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> 則會設定 UPN 或 SPN 身分識別。  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]堆疊繫結正確的自訂繫結項目，請參閱[Creating User-Defined 繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]建立自訂繫結與<xref:System.ServiceModel.Channels.SecurityBindingElement>，請參閱[How to： 指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [如何： 指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 [如何： 建立自訂用戶端身分識別驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [選取認證類型](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [建立使用者定義繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [如何： 擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
