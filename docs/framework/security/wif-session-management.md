---
title: "WIF 工作階段管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7703d9fb612ead13140d010b1670abb209c5acb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wif-session-management"></a>WIF 工作階段管理
當用戶端第一次嘗試存取由信賴憑證者裝載的受保護資源時，用戶端必須先向信賴憑證者所信任的安全性權杖服務 (STS) 驗證其本身。 接著，STS 會發出安全性權杖給用戶端。 用戶端將這個權杖出示給信賴憑證者後，信賴憑證者便可授與用戶端存取受保護資源的權限。 不過，您不希望用戶端針對每個要求向 STS 重新進行驗證，特別是因為它還可能與信賴憑證者不在同一部電腦或同一個網域中。 相反地，Windows Identity Foundation (WIF) 會讓用戶端和信賴憑證者建立一個工作階段，用戶端可在其中針對第一個要求之後的所有要求，使用工作階段安全性權杖向信賴憑證者驗證其本身。 信賴憑證者可以使用儲存在 Cookie 內的這個工作階段安全性權杖，用來重新建構用戶端的 <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>。  
  
 STS 會定義用戶端必須提供的驗證。 不過，用戶端可能會有多個可用來向 STS 驗證其本身的認證。 例如，它可能會有來自 Windows Live 的權杖、使用者名稱和密碼、憑證以及智慧金鑰。 在此情況下，STS 會授與用戶端數個身分識別，其中每個身分識別對應到用戶端出示的其中一個認證。 信賴憑證者決定授與用戶端的存取層級時，可以使用一或多個這些身分識別。  
  
 <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=nameWithType> 用來重新建構用戶端的 <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>，後者包含 <xref:System.Security.Claims.ClaimsPrincipal.Identities%2A> 中的所有用戶端身分識別。 集合中的每個 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> 都包含與該身分識別建立關聯的啟動程序權杖。  
  
 如果發出新的工作階段權杖時使用原始工作階段權杖的工作階段識別碼，<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=nameWithType> 不會更新權杖快取中的工作階段權杖。 將工作階段權杖具現化時，應該一律使用唯一的工作階段識別碼。  
  
> [!NOTE]
>  如果 Session.SecurityTokenHandler.ReadToken 收到無效的輸入(比方說，如果包含工作階段權杖的 Cookie 已損毀)，便會擲回 <xref:System.Xml.XmlException> 例外狀況。 建議您攔截此例外狀況，並提供特定應用程式行為。  
  
 如果受保護的網頁包含同樣也位於受保護網域的大量資源 (例如小型圖形)，用戶端必須向信賴憑證者重新驗證其本身，以便下載這些資源。 使用工作階段驗證權杖可避免需要針對每個要求向 STS 進行驗證，但這仍然意味著要傳送許多 Cookie。 您可以設定網頁，讓重要資料和資源儲存在受保護的網域中，同時將次要項目儲存在未受保護的網域，並從主要網頁加以連結。 此外，請將 Cookie 路徑設定為只參考受保護的網域。  
  
 若要在參考模式中運作，Microsoft 建議您在 **global.asax.cs** 檔案中提供 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> 事件的處理常式，並在 <xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> 屬性所傳遞的權杖上設定 **IsReferenceMode** 屬性。 這些更新可確保工作階段權杖會針對每個要求在參考模式中運作，並且只要設定工作階段驗證模組上的 <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> 屬性就能優先使用。  
  
## <a name="extensibility"></a>擴充性  
 您可以擴充工作階段管理機制。 進行此操作的其中一個原因是為了改善效能。 例如，您可以建立自訂的 Cookie 處理常式，以便在其記憶體內部狀態與 Cookie 傳入內容之間轉換或最佳化工作階段安全性權杖。 若要這樣做，您可以設定 <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=nameWithType> 的 <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=nameWithType> 屬性來使用衍生自 <xref:System.IdentityModel.Services.CookieHandler?displayProperty=nameWithType> 的自訂 Cookie 處理常式。 由於 Cookie 超過超文字傳輸通訊協定 (HTTP) 所允許的大小，因此 <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=nameWithType> 是預設的 Cookie 處理常式；如果您改為使用自訂的 Cookie 處理常式，則必須實作區塊處理。  
  
 如需詳細資訊，請參閱 [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) (http://go.microsoft.com/fwlink/?LinkID=248408) 範例。 此範例示範伺服陣列就緒的工作階段快取 (相對於 tokenreplycache)，讓您能夠透過參考使用工作階段，而非交換大型 Cookie；此範例也示範了一種更簡單的方法，用來保護伺服陣列中的 Cookie。 工作階段快取是以 WCF 為基礎。 關於工作階段保護，此範例示範了在 WIF 4.5 中根據 MachineKey 進行 Cookie 轉換的新功能，只要在 web.config 中貼上適當的程式碼片段，就能啟用此功能。此範例本身沒有「伺服陣列」，但它會示範要讓應用程式伺服陣列就緒所需執行的作業。
