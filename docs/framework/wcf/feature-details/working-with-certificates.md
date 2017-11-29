---
title: "使用憑證"
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
helpviewer_keywords: certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c38a697cc5f4693977e11ff71142322533e9ded
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-certificates"></a>使用憑證
在針對 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 安全性設計程式時，通常會採用 X.509 數位憑證來驗證用戶端與伺服器、加密，以及數位簽署訊息。 本主題將扼要說明 X.509 數位憑證功能及如何在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中使用這些憑證，同時針對這些概念的進一步說明以及如何運用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 與憑證來完成一般工作的方法說明提供連結。  
  
 簡單地說，數位憑證是屬於*公開金鑰基礎結構*(PKI)，這是數位憑證、 憑證授權單位，與其他註冊授權單位，並驗證有效性的系統每個參與電子異動使用公開金鑰加密的合作對象。 憑證授權單位發出憑證，而每個憑證具有一組欄位，其中包含資料，例如*主旨*（發行憑證的實體），有效日期 （當憑證是有效的），(的簽發者實體發出憑證），與公開金鑰。 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，每一個屬性都會被當成 <xref:System.IdentityModel.Claims.Claim> 處理，而且每個宣告還會進一步分成兩種型別：身分識別與權限。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]X.509 憑證，請參閱[X.509 公用金鑰憑證](http://go.microsoft.com/fwlink/?LinkId=209952)[!INCLUDE[crabout](../../../../includes/crabout-md.md)]宣告和授權，在 WCF 中的看到[管理宣告和授權的方式識別模型](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]實作 PKI，請參閱[Windows Server 2008 R2 憑證服務](http://go.microsoft.com/fwlink/?LinkId=209949)。  
  
 憑證的主要功能就是向其他人驗證憑證擁有者的身分識別。 憑證包含*公開金鑰*的擁有者，而擁有者本身則保留私密金鑰。 公開金鑰可以用來加密傳送給憑證擁有者的訊息。 只有擁有者才能存取私密金鑰，因此只有擁有者可以解密這些訊息。  
  
 憑證必須由憑證授權單位發行，此單位通常是憑證的協力廠商簽發者。 在 Windows 網域中，會包含憑證授權單位以便用來對網域中的電腦發行憑證。  
  
## <a name="viewing-certificates"></a>檢視憑證  
 使用憑證時，通常需要檢視並檢查其內容。 您可以透過 Microsoft Management Console (MMC) 嵌入式管理單元工具輕鬆達到這個目的。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][如何： 檢視憑證 MMC 嵌入式管理單元](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。  
  
## <a name="certificate-stores"></a>憑證存放區  
 您可以在存放區中找到憑證。 兩個主要的存放區位置還可進一步細分為子存放區。 如果您是電腦的系統管理員，就可以使用 MMC 嵌入式管理單元工具來同時檢視兩個主要的存放區。 非系統管理員只能檢視目前使用者的存放區。  
  
-   **本機電腦存放區**。 裡面包含了電腦處理序所存取的憑證，例如 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]。 請使用此位置來存放可對用戶端驗證伺服器的憑證。  
  
-   **目前使用者存放區**。 一般來說，互動性應用程式會將電腦目前使用者的憑證放在此處。 如果您正在建立用戶端應用程式，通常會將用來向服務驗證使用者的憑證放在此處。  
  
 這兩個存放區還可進一步細分為子存放區。 使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 來設計程式時，其中最重要的存放區為：  
  
-   **受信任的根憑證授權單位**。 您可以使用此存放區中的憑證來建立憑證鏈結，並藉由這些憑證回溯追蹤到此存放區中某個憑證授權單位的憑證。  
  
    > [!IMPORTANT]
    >  本機電腦會隱含地信任放在此存放區中的任何憑證，就算此憑證並未來自受信任的協力廠商憑證授權單位也是一樣。 因此，除非您充分信任簽發者並了解其相關影響，否則請勿將任何憑證放在此存放區。  
  
-   **個人**。 此存放區可用來存放與電腦使用者相關聯的憑證。 一般來說，此存放區是用來存放 [受信任的根憑證授權單位] 存放區中所找到的其中一個憑證授權單位所發行的憑證。 另外，此處找到的憑證可能是自動發行並由某個應用程式所信任。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]憑證存放區，請參閱[憑證存放區](http://go.microsoft.com/fwlink/?LinkId=88912)。  
  
### <a name="selecting-a-store"></a>選取存放區  
 選取存放憑證的位置時，必須考量服務或用戶端執行的方式與時機， 並套用下列一般規則：  
  
-   如果 WCF 服務裝載在 Windows 服務使用**本機**儲存。 請注意，您需要系統管理員權限將憑證安裝到本機電腦存放區。  
  
-   如果服務或用戶端是使用者帳戶下執行的應用程式，然後使用**目前使用者**儲存。  
  
### <a name="accessing-stores"></a>存取存放區  
 存放區會受到存取控制清單 (ACL) 的保護，就像電腦上的資料夾一樣。 當您建立由網際網路資訊服務 (IIS) 所裝載的服務時，[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 處理序會透過 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 帳戶來執行。 該帳戶必須能夠存取包含服務所使用之憑證的存放區。 每一個主要存放區都會以預設的存取清單加以保護，但是您可以修改此清單。 如果您建立個別的角色來存取存放區，則必須授予該角色存取權限。 若要了解如何修改使用 WinHttpCertConfig.exe 工具的存取清單，請參閱[How to： 建立開發期間使用的暫存憑證](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用用戶端憑證與 IIS，請參閱[如何呼叫 Web 服務所使用的 ASP.NET Web 應用程式中驗證用戶端憑證](http://go.microsoft.com/fwlink/?LinkId=88914)。  
  
## <a name="chain-trust-and-certificate-authorities"></a>鏈結信任與憑證授權單位  
 憑證是在階層中建立的，其中每個個別憑證都會連結到核發憑證的 CA。 此連結連至 CA 的憑證。 接著，CA 的憑證會連結至核發 CA 原始憑證的 CA。 在找到根 CA 的憑證之前，會一直重複這個程序。 根 CA 的憑證在本質上會受到信任。  
  
 數位簽章可用來驗證實體，藉此階層中，也稱為*信任鏈結*。 您可以檢視任何憑證的鏈結，只要按兩下任何憑證，然後按一下使用 MMC 嵌入式管理單元**憑證路徑** 索引標籤[!INCLUDE[crabout](../../../../includes/crabout-md.md)]匯入的憑證授權單位憑證鏈結，請參閱[How to： 指定用來驗證簽章的憑證授權單位憑證鏈結](../../../../docs/framework/wcf/feature-details/specify-the-certificate-authority-chain-verify-signatures-wcf.md)。  
  
> [!NOTE]
>  您可以藉由將簽發者的憑證放在信任的根授權憑證存放區，為任何簽發者都指定一個信任的根授權。  
  
### <a name="disabling-chain-trust"></a>停用鏈結信任  
 在建立新服務時，您可能使用並非由信任的根憑證所發行的憑證，或者發行的憑證本身並非位於 [受信任的根憑證授權單位] 存放區中。 如果只是做為開發用途，您可以暫時停用檢查憑證之信任鏈結的機制。 若要這麼做，請將 `CertificateValidationMode` 屬性 (Property) 設為 `PeerTrust` 或 `PeerOrChainTrust`。 每種模式都會將憑證指定為自動發行 (對等信任) 或是信任鏈結的一部分。 您可以在下列任何一個類別中設定屬性。  
  
|類別|屬性|  
|-----------|--------------|  
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|  
  
 您也可以使用組態來設定屬性。 下列項目可用來指定驗證模式：  
  
-   [\<驗證 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
-   [\<peerAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)  
  
-   [\<messageSenderAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)  
  
## <a name="custom-authentication"></a>自訂驗證  
 `CertificateValidationMode` 屬性同時可讓您自訂憑證的驗證方式。 根據預設，層級會設為 `ChainTrust`。 若要使用 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> 值，您必須同時將 `CustomCertificateValidatorType` 屬性 (Attribute) 設為可用來驗證憑證的組件與型別。 若要建立自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。  
  
 在建立自訂的驗證器時，要覆寫之最重要的方法是 <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> 方法。 如需自訂驗證的範例，請參閱[X.509 憑證驗證程式](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md)範例。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][自訂認證與認證驗證](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)。  
  
## <a name="using-makecertexe-to-build-a-certificate-chain"></a>使用 Makecert.exe 來建置憑證鏈結  
 憑證建立工具 (Makecert.exe) 可建立 X.509 憑證與私密金鑰/公開金鑰組。 您可以將私密金鑰儲存到磁碟，然後用它來發行並簽署新的憑證，藉此模擬鏈結憑證的階層架構。 此工具主要當作開發服務時的輔助工具用途，請勿用來建立實際部署所需的憑證。 在開發 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務時，請透過下列步驟並使用 Makecert.exe 來建置信任鏈結。  
  
#### <a name="to-build-a-chain-of-trust-with-makecertexe"></a>若要使用 Makecert.exe 來建置信任鏈結  
  
1.  使用 MakeCert.exe 工具來建立暫時的根授權 (自動簽署) 憑證。 將私密金鑰儲存到磁碟。  
  
2.  使用新的憑證來發行另一個包含公開金鑰的憑證。  
  
3.  將根授權憑證匯入 [受信任的根憑證授權單位] 存放區。  
  
4.  如需逐步指示，請參閱[How to： 建立開發期間使用的暫存憑證](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)。  
  
## <a name="which-certificate-to-use"></a>該使用哪個憑證？  
 關於憑證常見的問題包括該使用哪些憑證以及為何使用這些憑證。 答案需視您是要針對用戶端或服務設計程式而定。 下列資訊將提供您一般性的指示，可能無法完全解答這些問題。  
  
### <a name="service-certificates"></a>服務憑證  
 服務憑證的主要工作就是對用戶端驗證伺服器。 檢查用戶端驗證伺服器時的其中一個要比較的值是**主旨**欄位統一資源識別元 (URI) 用來連絡服務： 兩者的 DNS 必須相符。 例如，如果服務的 URI 是"http://www.contoso.com/endpoint/ 」 則**主旨**欄位也必須包含值"www.contoso.com"。  
  
 請注意，該欄位可以包含數個值，每個值都可加上代表該值的初始化前置詞。 最常見的初始化前置詞就是用 "CN" 代表一般名稱，例如，"CN = www.contoso.com"。 也可能會**主旨** 欄位為空白，在此情況下**主體替代名稱**欄位只能包含**DNS 名稱**值。  
  
 也請注意值**用途**憑證欄位應包含適當的值，例如 「 伺服器驗證 」 或 「 用戶端驗證 」。  
  
### <a name="client-certificates"></a>用戶端憑證  
 用戶端憑證通常不是由協力廠商憑證授權單位所發行。 反之，目前使用者位置上的 [個人] 存放區通常包含了由根授權所放置、帶有 [用戶端驗證] 使用目的之憑證。 需要雙向驗證時，用戶端可以使用此類憑證。  
  
## <a name="online-revocation-and-offline-revocation"></a>線上撤銷與離線撤銷  
  
### <a name="certificate-validity"></a>憑證有效性  
 每個憑證是否有效，只會針對給定的一段時間，稱為*有效期*。 有效期間由定義**有效期自**和**有效期到**X.509 憑證的欄位。 在驗證期間，會檢查憑證以判斷憑證日期是否仍在有效期間內。  
  
### <a name="certificate-revocation-list"></a>憑證撤銷清單  
 在有效期間內，憑證授權單位隨時可撤銷憑證。 有許多原因會導致發生這種情況，例如憑證的私密金鑰遭到破壞。  
  
 一旦發生這種情況，任何來自已撤銷憑證的鏈結會同時失效，而且在驗證程序期間將不會受到信任。 若要找出已撤銷的憑證，每個簽發者發行時間和日期-戳記*憑證撤銷清單*(CRL)。 您也可以透過將下列類別的 `RevocationMode` 或 `DefaultRevocationMode` 屬性設為其中一個 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 列舉值的方式，使用線上撤銷或離線撤銷來檢查此清單：<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>、<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>、<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> 與 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> 類別。 所有屬性的預設值為 `Online`。  
  
 您也可以使用組態中設定模式`revocationMode`屬性兩者的[\<驗證 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (的[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) 和[\<驗證 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (的[ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md))。  
  
## <a name="the-setcertificate-method"></a>SetCertificate 方法  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，您必須經常指定服務或用戶端用來驗證、加密或數位簽署訊息的憑證或憑證集。 您也可以使用代表 X.509 憑證之各種類別的 `SetCertificate` 方法，以程式設計方式來執行這項工作。 下列類別會使用 `SetCertificate` 方法來指定憑證。  
  
|類別|方法|  
|-----------|------------|  
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|  
  
 `SetCertificate` 方法會藉由指定下列項目來進行運作：指定存放區位置與存放區、用來指定憑證欄位的 [尋找] 型別 (`x509FindType` 參數)，以及指定要在欄位中尋找的值。 例如，下列程式碼會建立<xref:System.ServiceModel.ServiceHost>執行個體，並設定用來驗證用戶端與服務的服務憑證`SetCertificate`方法。  
  
 [!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
 [!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]  
  
### <a name="multiple-certificates-with-the-same-value"></a>使用相同值的多個憑證  
 存放區可能包含使用相同主體名稱的多個憑證。 這表示，如果您指定`x509FindType`是<xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName>或<xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>，和一個以上的憑證具有相同的值、 becausethereisno 區別的方法都需要哪些憑證擲回例外狀況。 您可以將 `x509FindType` 設為 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> 來降低此行為的影響。 指紋欄位包含可用來尋找存放區中特定憑證的唯一值。 然而，此欄位也有缺點：如果憑證遭到撤銷或更新，則 `SetCertificate` 方法會因為指紋一併消失而失敗。 或者，當憑證失效時，驗證也會失敗。 降低這項風險的做法就是，將 `x590FindType` 參數設為 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> 並指定簽發者名稱。 如果不需要特定的簽發者，則您也可以設定其他任何一個 <xref:System.Security.Cryptography.X509Certificates.X509FindType> 列舉值，例如 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>。  
  
## <a name="certificates-in-configuration"></a>組態中的憑證  
 您也可以使用組態來設定憑證。 如果您要建立服務，在底下指定認證，包括憑證、 [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)。 當您進行程式設計的用戶端時，憑證會指定下[ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)。  
  
## <a name="mapping-a-certificate-to-a-user-account"></a>將憑證對應至使用者帳戶  
 IIS 與 Active Directory 的其中一項功能，就是能夠將憑證對應至 Windows 使用者帳戶。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]此功能，請參閱[將憑證對應至使用者帳戶](http://go.microsoft.com/fwlink/?LinkId=88917)。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用 Active Directory 對應，請參閱[用戶端憑證對應與目錄服務對應](http://go.microsoft.com/fwlink/?LinkId=88918)。  
  
 一旦您啟用這項功能，就可以將 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> 類別的 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 屬性設為 `true`。 在組態中，您可以設定`mapClientCertificateToWindowsAccount`屬性[\<驗證 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)元素`true`，如下列程式碼所示。  
  
```xml  
<serviceBehaviors>  
 <behavior name="MappingBehavior">  
  <serviceCredentials>  
   <clientCertificate>  
    <authentication certificateValidationMode="None" mapClientCertificateToWindowsAccount="true" />  
   </clientCertificate>  
  </serviceCredentials>  
 </behavior>  
</serviceBehaviors>  
```  
  
 將 X.509 憑證對應至代表 Windows 使用者帳戶的權杖可視為權限的提升，因為一旦對應之後，就可以使用 Windows 權杖針對受保護的資源取得其存取權限。 因此，網域原則要求 X.509 憑證在執行對應之前必須先符合此原則規定。 *SChannel*安全性封裝會強制執行這項需求。  
  
 當使用 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (含) 以後版本時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會確保憑證符合網域原則，然後才將憑證對應至 Windows 帳戶。  
  
 在第一版的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，您不需要諮詢網域原則便可進行對應。 因此，當啟用對應功能且 X.509 憑證無法滿足網域原則要求時，以往在第一版中能夠順利執行的舊版應用程式可能會無法執行。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels>  
 <xref:System.ServiceModel.Security>  
 <xref:System.ServiceModel>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType>  
 [保護服務和用戶端](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
