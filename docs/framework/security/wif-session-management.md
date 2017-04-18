---
title: "WIF 工作階段管理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# WIF 工作階段管理
當用戶端先嘗試存取由一個相依的一方裝載的受保護的資源時，用戶端必須先驗證加入至所依賴之部分信任的安全性權杖服務 \(STS\)。  STS 然後發出安全性語彙基元傳遞至用戶端。  用戶端所表示這個語彙基元所依賴的一方，然後將受保護之資源的用戶端存取。  不過，特別是，因為它可能也不在同一部電腦上或網域和這個相依的一方相同，所以不要讓用戶端必須重新驗證對每個要求的 STS。  相反地， Windows 識別基礎 \(WIF\) 排列此用戶端所依賴之廠商建立用戶端使用一個工作階段安全性權杖驗證加入所有需要的信任的一方，在第一個要求之後的工作階段。  這個相依的一方能使用工作階段安全性權杖，儲存在 Cookie 中，重建用戶端的 <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName>。  
  
 STS 定義哪些驗證用戶端必須提供。  不過，用戶端可能不會驗證加入 STS 的多個認證。  例如，它可能會從作用中視窗的語彙基元，表示使用者名稱和密碼、憑證和 smartkey。  在這種情況下， STS 授與用戶端數個識別，以及每一個識別與用戶端所表示的其中一個認證對應。  此信任的一方可以使用一或多個識別，並決定時授與用戶端的存取等級為何。  
  
 <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=fullName> 用來重建用戶端的 <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName>，在 <xref:System.Security.Claims.ClaimsPrincipal.Identities%2A>包含所有用戶端的識別。  集合中的每個 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> 包含與該識別的指引語彙基元。  
  
 如果新工作階段語彙基元都會以原始工作階段語彙基元的工作階段 ID， <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=fullName> 不對語彙基元更新快取工作階段語彙基元。  您應該永遠以唯一工作階段 ID. 的一個工作階段語彙基元  
  
> [!NOTE]
>  如果它收到無效的輸入， Session.SecurityTokenHandler.ReadToken <xref:System.Xml.XmlException> 擲回例外狀況;例如，則為，如果工作階段 Cookie 中的語彙基元損毀。  建議您攔截此例外狀況並提供特定應用程式的行為。  
  
 如果受保護的 Web 網頁可以包含或受保護之網域的許多資源 \(例如小圖形\)，用戶端就必須重新驗證本身加入至相依的兩方下載這些資源中。  對工作階段驗證語彙基元來避免驗證對每個要求的 STS，，但仍表示許多 Cookie 傳送。  您可能想要將網頁，如此重要資料和資源在受保護的網域中，當次要項目在未受保護的網域儲存並且與主版頁面時連接。  此外，設定 Cookie 路徑參考只受保護的網域。  
  
 若要操作參考模式， Microsoft 建議提供的處理常式會在 **global.asax.cs** 檔案的 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> 事件和設定 **IsReferenceMode** 屬性在 <xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> 屬性傳遞的語彙基元。  這些更新會確保工作階段語彙基元在每個要求上參考模式下操作和優先於僅設定在工作階段驗證模組的 <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> 屬性。  
  
## 擴充性  
 您可以擴充工作階段管理機制。  其中一個理由是以改善效能。  例如，您可以建立轉換或最佳化其記憶體狀態之間的工作階段安全性語彙基元的自訂處理常式 Cookie，以及存取 Cookie。  若要這麼做，您可以設定 <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=fullName> 的 <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=fullName> 屬性使用 <xref:System.IdentityModel.Services.CookieHandler?displayProperty=fullName>衍生自類別的自訂處理常式 Cookie。  <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=fullName> 是預設的 Cookie 處理常式，因為 Cookie 超過超文字傳輸通訊協定 \(HTTPS\) 的 \(HTTP\) 容許大小;如果您使用自訂 Cookie 處理常式，您必須實作區塊。  
  
 如需詳細資訊， [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) 請參閱 \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=248408\) 範例。  這個範例會顯示陣列準備工作階段快取 \(與 tokenreplycache\)，讓您可以參考使用工作階段而非切換大 Cookie，這個範例在伺服陣列將示範保護 Cookie 的簡單方法。  工作階段快取 WCF 架構。  如需保護的工作階段，程式碼範例示範在 Cookie 的 WIF 4.5 的新功能轉換以 MachineKey，可以透過貼在 web.config 的適當的程式碼片段啟動。  這個範例「沒有型別陣列」，不過，它會顯示您所提供讓您的應用程式需要伺服陣列就緒。