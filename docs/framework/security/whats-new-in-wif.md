---
title: Windows Identity Foundation 4.5 的新功能
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
ms.openlocfilehash: 673294ccdb76e6016169a4e2b4e7713ba63fa1e7
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777470"
---
# <a name="what39s-new-in-windows-identity-foundation-45"></a>Windows Identity Foundation 4.5 的新功能
第一版的 Windows Identity Foundation (WIF) 是發行為獨立下載的版本，稱為 WIF 3.5，因為它是在 .NET 3.5 SP1 的期間內所引入的。 從 .NET 4.5 開始，WIF 就成為 .NET Framework 的一部分。 在架構中直接提供 WIF 類別可讓 .NET 中的宣告式身分識別的整合更加深入，讓您更容易使用宣告。 您需要修改為 WIF 3.5 所撰寫的應用程式，才能利用新的模型；如需詳細資訊，請參閱[將使用 WIF 3.5 建置的應用程式移轉至 WIF 4.5 的方針](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)。  
  
 您可以在下文中找到一些主要變更重點。  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>WIF 現在是 .NET Framework 的一部分  
 WIF 類別現在散佈在數個組件，主要有 `mscorlib`、`System.IdentityModel`、`System.IdentityModel.Services` 和 `System.ServiceModel`。 同樣地，WIF 類別也散佈在數個命名空間中：<xref:System.Security.Claims?displayProperty=nameWithType>、數個 [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) 命名空間以及 <xref:System.ServiceModel.Security?displayProperty=nameWithType>。 <xref:System.Security.Claims?displayProperty=nameWithType> 命名空間包含新的 <xref:System.Security.Claims.ClaimsPrincipal> 和 <xref:System.Security.Claims.ClaimsIdentity> 類別 (請參閱下文)。 .NET 中所有的主體現在是衍生自 <xref:System.Security.Claims.ClaimsPrincipal>。 如需 WIF 命名空間以及其所包含之各種類別的詳細資訊，請參閱 [WIF API 參考](../../../docs/framework/security/wif-api-reference.md)。 如需 WIF 3.5 和 WIF 4.5 之間的命名空間對應方式詳細資訊，請參閱 [WIF 3.5 和 WIF 4.5 之間的命名空間對應](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)。  
  
## <a name="new-claims-model-and-principal-object"></a>新的宣告模型和主體物件  
 宣告是位於 .NET Framework 4.5 的最核心。 基本的宣告類別 (<xref:System.Security.Claims.Claim>、<xref:System.Security.Claims.ClaimsIdentity>、<xref:System.Security.Claims.ClaimsPrincipal>、<xref:System.Security.Claims.ClaimTypes> 和 <xref:System.Security.Claims.ClaimValueTypes>) 全部都是直接位於 `mscorlib` 命名空間的 <xref:System.Security.Claims?displayProperty=nameWithType> 中。 現在已經不需要使用介面來將宣告外掛到 .NET 識別系統中：<xref:System.Security.Principal.WindowsPrincipal>、<xref:System.Security.Principal.GenericPrincipal> 和 <xref:System.Web.Security.RolePrincipal> 現在是繼承自 <xref:System.Security.Claims.ClaimsPrincipal>；而 <xref:System.Security.Principal.WindowsIdentity>、<xref:System.Security.Principal.GenericIdentity> 和 <xref:System.Web.Security.FormsIdentity> 現在則是繼承自 <xref:System.Security.Claims.ClaimsIdentity>。 簡單地說，現在每個主體類別都可提供宣告。 因此，也就移除了 WIF 3.5 整合類別和介面 (`WindowsClaimsIdentity`、`WindowsClaimsPrincipal`、`IClaimsPrincipal` 和 `IClaimsIdentity`)。 此外，<xref:System.Security.Claims.ClaimsIdentity> 類別現在會公開可以輕鬆查詢識別的宣告集合的方法。  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>對 WIF 4.5 Visual Studio 經驗的變更  
  
-   **新增 STS 參考...** Visual Studio 功能 (cmdline 公用程式 FedUtil) 已不存在；您可以改為使用新的 Visual Studio 延伸模組 **Visual Studio 2012 的身分識別與存取工具**。 這可讓您與現有的 STS 建立同盟或使用 LocalSTS 來測試方案。 安裝此延伸模組之後，您可以用滑鼠右鍵按一下專案，然後尋找操作功能表上的 [身分識別與存取]。  
  
-   ASP.NET 和 STS 範本已不再提供，因為現有的 ASP.NET、網站和 WCF 專案範本中可以直接使用宣告。  
  
-   WIF 4.5 不再延續使用 `Microsoft.IdentityModel.Web.Controls` 命名空間中的控制項 (`SignInControl`、`FederatedPassiveSignInControl` 和 `FederatedPassiveSignInStatus`)。  
  
## <a name="changes-to-the-wif-45-api"></a>WIF 4.5 應用程式開發介面的變更  
  
-   一般而言，宣告相關類別是位於 <xref:System.Security.Claims?displayProperty=nameWithType> 命名空間中；WCF 相關類別 (用於 WS-Trust 情節的服務合約、通道、通道處理站和服務主機) 是位於 <xref:System.ServiceModel.Security?displayProperty=nameWithType> 中；而所有其他 WIF 類別則是散佈在各種 [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) 命名空間中 (這些類別包括，例如，表示 WS-* 和 SAML 成品的類別、權杖處理常式和相關類別，以及用於 WS-同盟情節的類別)。 如需詳細資訊，請參閱 [WIF 3.5 和 WIF 4.5 之間的命名空間對應](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)和 [WIF API 參考](../../../docs/framework/security/wif-api-reference.md)。  
  
-   電腦金鑰已可用於 Web 伺服陣列情節中的工作階段 Cookie 中。 如需詳細資訊，請參閱 [WIF 和 Web 伺服陣列](../../../docs/framework/security/wif-and-web-farms.md)。  
  
-   您現在以宣告方式設定 [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) 和 [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 元素下的 WIF。 如需 WIF 組態的詳細資訊，請參閱 [WIF 組態參考](../../../docs/framework/security/wif-configuration-reference.md)。  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>將 WIF 整合到 .NET 中所造成的其他值得注意的 .NET 變更或功能  
  
-   執行宣告式授權 (CBAC) 的可能性現在已整合至 .NET Framework。 您可以設定 <xref:System.Security.Claims.ClaimsAuthorizationManager> 物件，然後使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 和 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別在您的程式碼中執行命令式和宣告式存取檢查。 CBAC 比傳統的角色式存取檢查 (RBAC) 提供更多的彈性和更佳的細微性。 它也可以讓授權原則更有效地從商務邏輯分離，因為商務邏輯可以根據特定宣告或宣告集進行存取檢查，而這些宣告的授權原則可以用宣告的方式設定在 [\<claimsAuthorizationManager>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) 元素下。  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>由 WIF 整合所造成的 WCF 變更：  
  
-   WIF 已取代 WCF 宣告式識別模型。 這表示應該捨棄 <xref:System.IdentityModel.Claims?displayProperty=nameWithType>、<xref:System.IdentityModel.Policy?displayProperty=nameWithType> 和 <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> 命名空間中的類別，改為使用 WIF 類別。  
  
-   WCF 服務現在可以使用 WIF，只需指定 `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>` 元素的 `useIdentityConfiguration` 屬性，如下面 XML 所示：  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     當您使用 **Visual Studio 2012 的身分識別分與存取工具** (請參閱上述的**對 Visual Studio 體驗的變更**) 時，此工具會為您在組態檔中新增設定了 `useIdentityConfiguration` 屬性的 `<serviceCredentials>` 元素。 它還會新增一個含有 WIF 組態設定的對應 [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) 元素，以及新增繫結和其他必要的設定，以便讓您將驗證外包給您選擇的 STS。  
  
## <a name="see-also"></a>另請參閱  
 [將使用 WIF 3.5 建置的應用程式移轉至 WIF 4.5 的方針](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)  
 [WIF 3.5 和 WIF 4.5 之間的命名空間對應](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [WIF API 參考](../../../docs/framework/security/wif-api-reference.md)  
 [WIF 組態參考](../../../docs/framework/security/wif-configuration-reference.md)
