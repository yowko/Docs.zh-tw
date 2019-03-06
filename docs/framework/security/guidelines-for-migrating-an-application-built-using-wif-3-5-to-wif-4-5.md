---
title: 將使用 WIF 3.5 建置的應用程式移轉至 WIF 4.5 的方針
ms.date: 03/30/2017
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
author: BrucePerlerMS
ms.openlocfilehash: ad8ff2b6daaaf48975b86c637435b31fa1869e1d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370016"
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>將使用 WIF 3.5 建置的應用程式移轉至 WIF 4.5 的方針

## <a name="applies-to"></a>適用於

- Microsoft® Windows® Identity Foundation (WIF) 3.5 和 4.5。

## <a name="overview"></a>總覽

Windows Identity Foundation (WIF) 一開始發行於 .NET 3.5 SP1 時間範圍內。 該版 WIF 稱為 WIF 3.5。 它已發行為個別執行階段和 SDK，表示已在其上執行具 WIF 功能之應用程式的每部電腦都必須已安裝 WIF 執行階段，而且開發人員必須下載並安裝 WIF SDK，以取得已啟用具 WIF 功能之應用程式開發的 Visual Studio 範本和工具。 從 .NET 4.5 開始，WIF 已與 .NET Framework 完全整合。 不再需要個別執行階段，而且可以使用 Visual Studio 延伸模組管理員將 WIF 工具安裝在 Visual Studio 2012 中。 這版 WIF 稱為 WIF 4.5。

將 WIF 整合至 .NET 需要 WIF API 介面中的數項變更。 WIF 4.5 包含 Visual Studio 的新命名空間、一些組態項目變更和新工具。 本主題所提供的指引可用來協助您將使用 WIF 3.5 所建置的應用程式移轉至 WIF 4.5。 在某些情況下，您需要在執行 Windows 8 或 Windows Server 2012 的電腦上執行使用 WIF 3.5 所建置的舊版應用程式。 本主題也提供如何啟用這些作業系統之 WIF 3.5 的指引。

## <a name="changes-required-for-wif-45"></a>WIF 4.5 所需的變更

本節描述將 WIF 3.5 應用程式移轉至 WIF 4.5 所需的變更。

### <a name="assembly-and-namespace-changes"></a>組件和命名空間變更

在 WIF 3.5 中，所有 WIF 類別都已包含在 `Microsoft.IdentityModel` 組件 (microsoft.identitymicrosoft.identitymodel.dll) 中。 在 WIF 4.5 中，WIF 類別已分成下列組件：`mscorlib`(mscorlib.dll)、`System.IdentityModel` (System.IdentityModel.dll)、`System.IdentityModel.Services` (System.IdentityModel.Services.dll) 和 `System.ServiceModel` (System.ServiceModel.dll)。

WIF 3.5 類別全部包含在其中一個 `Microsoft.IdentityModel` 命名空間中；例如，`Microsoft.IdentityModel`、`Microsoft.IdentityModel.Tokens`、`Microsoft.IdentityModel.Web` 等等。 在 WIF 4.5 中，WIF 類別現在會散佈到 [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) 命名空間、<xref:System.Security.Claims?displayProperty=nameWithType> 命名空間和 <xref:System.ServiceModel.Security?displayProperty=nameWithType> 命名空間。 除了這項重組之外，WIF 4.5 中已卸除一些 WIF 3.5 類別。

下表顯示一些更重要的 WIF 4.5 命名空間以及它們所含的類別類型。 如需 WIF 3.5 與 WIF 4.5 間之命名空間對應方式以及已在 WIF 4.5 中卸除之命名空間和類別的詳細資訊，請參閱 [WIF 3.5 和 WIF 4.5 之間的命名空間對應](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)。

|WIF 4.5 命名空間|描述|
|-----------------------|-----------------|
|<xref:System.IdentityModel?displayProperty=nameWithType>|包含的類別代表 Cookie 轉換、安全性權杖服務，以及特定的 XML 字典讀取器。 包含下列 WIF 3.5 命名空間中的類別：`Microsoft.IdentityModel`、`Microsoft.IdentityModel.SecurityTokenService` 和 `Microsoft.IdentityModel.Threading`。|
|<xref:System.Security.Claims?displayProperty=nameWithType>|包含的類別代表宣告、宣告式身分識別、宣告式主體，以及其他宣告式身分識別模型成品。 包含 `Microsoft.IdentityModel.Claims` 命名空間中的類別。|
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|包含的類別代表安全性權杖、安全性權杖處理常式，以及其他安全性權杖成品。 包含下列 WIF 3.5 命名空間中的類別：`Microsoft.IdentityModel.Tokens`、`Microsoft.IdentityModel.Tokens.Saml11` 和 `Microsoft.IdentityModel.Tokens.Saml2`。|
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|包含的類別用於被動 (WS-同盟) 案例。 包含 `Microsoft.IdentityModel.Web` 命名空間中的類別。|
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|類別代表 WCF 合約、通道、服務主機，以及主動 (WS-Trust) 案例中使用的其他成品，並且現在位在此命名空間中。 在 WIF 3.5 中，這些類別位在 `Microsoft.IdentityModel.Protocols.WSTrust` 命名空間中。|

> [!IMPORTANT]
> 下列 `System.IdentityModel` 命名空間包含的類別可實作 WCF 宣告式身分識別模型：<xref:System.IdentityModel.Claims?displayProperty=nameWithType>、<xref:System.IdentityModel.Policy?displayProperty=nameWithType> 和 <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>。 WIF 已取代 WCF 宣告式識別模型。 在建置以 WIF 為基礎的解決方案時，您不應該使用這三個命名空間中的類別。

### <a name="changes-due-to-net-integration"></a>.NET 整合所造成的變更

WIF 現在已整合至 .NET Framework。 大部分 .NET 身分識別和主體類別現在衍生自 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> 和 <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>。 WIF 4.5 中下列變更的結果：

- 代表宣告、身分識別和主體的 WIF 類別現在存在於 <xref:System.Security.Claims?displayProperty=nameWithType> 命名空間中。

    > [!IMPORTANT]
    > <xref:System.IdentityModel.Claims?displayProperty=nameWithType> 命名空間所含的類別代表 WCF 宣告式身分識別模型中的成品。 其中許多類別的名稱都與 WIF 類別相同；例如，`Claims`。 以 WIF 為基礎建置解決方案時，請不要使用這些類別。

- .NET 身分識別和主體類別現在直接衍生自 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> 和 <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>，其代表宣告式身分識別和主體。 基於這個原因，不再需要 WIF 3.5 介面 `IClaimsIdentity` 和 `IClaimsPrincipal`，而且 WIF 4.5 中不再提供它們。

- 因為 <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> 和 <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> 這類 .NET 身分識別和主體類別現在衍生自 <xref:System.Security.Claims.ClaimsIdentity> 和 <xref:System.Security.Claims.ClaimsPrincipal>，所以已內建宣告功能。 基於這個原因，不再需要 WIF 3.5 中的宣告特定身分識別和主體類別 (例如 `WindowsClaimsIdentity` 和 `WindowsClaimsPrincipal`)，而且 WIF 4.5 中沒有它們。

### <a name="other-changes-to-wif-functionality"></a>其他 WIF 功能變更

除了命名空間變更以及與 .NET 整合所造成的變更之外，WIF 4.5 中也會發生下列一般 WIF 功能變更。

- 已移除 `Microsoft.IdentityModel.ExceptionMapper` 類別，而此類別所提供的功能可讓您將例外狀況對應至特定 SOAP 錯誤。

- 已經大幅降低例外狀況介面。

- 已移除許多已定義通訊協定或 WS-* 特定常數的類別；例如，已定義 WS-Addressing 1.0 相關常數的 `Microsoft.IdentityModel.WSAddressing10Constants` 類別。

- 已移除 `Microsoft.IdentityModel.WindowsTokenService` 命名空間中的「對 Windows 權杖服務的宣告 (c2wts)」和其關聯的類別。

### <a name="wif-configuration-changes"></a>WIF 組態變更

在 WIF 4.5 中，命名空間更新已造成組態檔中的許多變更。 例如，請考慮在 `<httpModules>` 區段中使用下列 WIF 3.5 項目，以將 WS-同盟驗證管理員新增至應用程式：

```xml
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />
```

WIF 4.5 中已將此項目更新成包含新的命名空間和組件版本：

```xml
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>
```

下列清單列舉 WIF 4.5 組態檔的主要變更。

- `<microsoft.identityModel>` 區段現在是 [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) 區段。

- `<service>` 項目現在是 [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 項目。

- 已新增區段 [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)，指定可控制被動 (WS-同盟) 案例中行為的設定。

- [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 項目和其子項目已從 WIF 3.5 中的 `<service>` 項目移至新的 `<system.identityModel.services>` 項目。

- 可直接在 WIF 3.5 的 `<service>` 項目下的服務層級指定的數個項目，已限制為指定於 [\<securityTokenHandlerConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) 項目下方 (基於回溯相容性，它們可能仍然指定於 WIF 4.5 的 [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 項目下方)。

如需 WIF 4.5 組態項目的完整清單，請參閱 [WIF 組態結構描述](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)。

### <a name="visual-studio-tooling-changes"></a>Visual Studio 工具變更

WIF 3.5 SDK 已提供獨立同盟公用程式 FedUtil.exe (FedUtil)，可用來將具 WIF 功能之應用程式中的身分識別管理外包到安全性權杖服務 (STS)。 此工具已在應用程式組態檔中新增 WIF 設定，以讓應用程式從一或多個 STS 取得安全性權杖，並透過 [Add STS Service Reference] (新增 STS 服務參考)  按鈕呈現在 Visual Studio 中。 FedUtil 未隨附於 WIF 4.5。 相反地，WIF 4.5 支援名為「Visual Studio 2012 的身分識別和存取工具」的新 Visual Studio 延伸模組，用來使用將身分識別管理外包到 STS 所需的 WIF 設定來修改應用程式組態檔。 身分識別和存取工具也會實作稱為「本機 STS」的 STS，以用來測試具 WIF 功能的應用程式。 在許多情況下，這項功能都不需要建置自訂 STS，而這些自訂 STS 通常是 WIF 3.5 中測試開發中解決方案的必要項目。 基於這個原因，Visual Studio 2012 中不再支援 STS 範本；不過，WIF 4.5 仍然支援開發 STS 的類別。

您可以從擴充功能和更新管理員，在 Visual Studio 中安裝 Identity and Access Tool，或您可以從 Code Gallery 上的下列網頁：[Identity and Access Tool Code Gallery 上的 Visual Studio 2012](https://go.microsoft.com/fwlink/?LinkID=245849)。 下列清單摘要說明 Visual Studio 工具變更：

- 已移除 [Add STS Service Reference] (新增 STS 服務參考) 功能。 取代項目是身分識別和存取工具。

- 已移除 Visual Studio STS 範本。 您可以使用透過身分識別和存取工具取得的「本機 STS」來設定您使用 WIF 所開發的身分識別解決方案。 「本機 STS」組態可以修改成自訂它所提供的宣告。

- WIF 4.5 不再提供獨立同盟公用程式 (FedUtil)。 您可以使用身分識別和存取工具來修改組態檔，以將身分識別管理外包到 STS。

如需身分識別和存取工具的詳細資訊，請參閱 [Visual Studio 2012 的身分識別和存取工具](../../../docs/framework/security/identity-and-access-tool-for-vs.md)。

<a name="BKMK_ToolingChanges"></a>

### <a name="passive-ws-federation-scenarios"></a>被動 (WS-同盟) 案例：

- 支援被動案例的類別已移至 <xref:System.IdentityModel.Services?displayProperty=nameWithType> 命名空間。 在 WIF 3.5 中，這些類別位在 `Microsoft.IdentityModel.Web` 命名空間中。

- `Microsoft.IdentityModel.Web.Configuration` 命名空間中的類別已移至 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>。 這些類別代表被動案例中組態特有的物件。

- 不再支援 `FederatedPassiveSignInControl`；已從 WIF 4.5 中移除 `Microsoft.IdentityModel.Web.Controls` 命名空間中的所有類別。

- WS-同盟驗證模組 (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) 登出功能與 WIF 3.5 不同。 如需 WIF 4.5 中登出運作方式的詳細資訊，請參閱 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 類別主題。

### <a name="active-wcfws-trust-scenarios"></a>作用中 (WCF/WS-Trust) 案例：

- 在 WIF 4.5 中，`Microsoft.IdentityModel.Protocols.WSTrust` 命名空間主要分成兩個命名空間。 代表 WS-Trust 通訊協定特有成品的類別現在位於 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> 中。 這包含 <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> 這類類別。 類別代表 WCF 合約、通道、服務主機，以及在 WCF 應用程式中使用 WS-Trust 所含的其他成品，並且已移至 <xref:System.ServiceModel.Security?displayProperty=nameWithType>；例如，<xref:System.ServiceModel.Security.IWSTrust13AsyncContract> 介面。

- 已大幅簡化將 WCF 應用程式設定成使用 WIF。 之前，必須將 `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` 新增為行為延伸模組，並且接著指定 `<federatedServiceHostConfiguration>` 項目，以使用這項功能將 WIF 插入服務行為中。 WIF 4.5 已更緊密地與 WCF 整合。 您現在可以在 WCF 服務上啟用 WIF，只需在 `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>` 項目上指定 `useIdentityConfiguration` 屬性即可，如下列 XML 所示：

    ```xml
    <serviceCredentials useIdentityConfiguration="true">
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />
    </serviceCredentials>
    ```

- 在 WIF 4.5 中，必須於服務主機上指定作用中 (WCF) 服務所使用的服務憑證。 在組態中，做法是透過 `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>`/`<serviceCertificate>` 項目，如上述範例所示。 在 WIF 3.5 中，可以透過 WIF `<service>` 項目的 `<serviceCertificate>` 子項目指定服務憑證。 WIF 4.5 沒有這項功能；請改為在 `<serviceCredentials>` 項目下指定 `<serviceCertificate>` 項目。

- 用來將 WIF 3.5 插入 WCF 的類別不再存在。 這包含 `Microsoft.IdentityModel.Tokens` 命名空間中的下列類別：`FederatedSecurityTokenManager`、`FederatedServiceCredentials` 和 `IdentityModelServiceAuthorizationManager`，以及 `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` 類別。

## <a name="enabling-wif-35-in-windows-8"></a>在 Windows 8 中啟用 WIF 3.5

因為 WIF 4.5 是 .NET 4.5 的一部分，所以會在執行 Windows 8 和 Windows Server 2012 的電腦上自動予以啟用，而且使用 WIF 4.5 所建置的應用程式預設會在 Windows 8 或 Windows Server 2012 下執行。 不過，您可能需要在執行 Windows 8 或 Windows Server 2012 的電腦上執行使用 WIF 3.5 所建置的應用程式。 在此情況下，您需要在目標電腦上啟用 WIF 3.5。 在執行 Windows 8 的電腦上，您可以使用部署映像服務和管理 (DISM) 工具來達成這項作業。 在執行 Windows Server 2012 的電腦上，您可以使用 DISM 工具，也可以使用 Windows PowerShell `Add-WindowsFeature` Cmdlet。 在這兩種情況下，可以在命令列或從 Windows PowerShell 環境中叫用適當的命令。

下列命令示範如何從命令列或 Windows PowerShell 環境中使用 DISM 工具。 根據預設，DISM PowerShell 模組包含在 Windows 8 和 Windows Server 2012 中，因此不需要進行匯入。 如需搭配使用 DISM 與 Windows PowerShell 的詳細資訊，請參閱[在 Windows PowerShell 中使用 DISM](https://go.microsoft.com/fwlink/?LinkId=254419)。

使用 DISM 啟用 WIF 3.5：

```console
dism /online /enable-feature:windows-identity-foundation
```

使用 DISM 停用 WIF 3.5：

```console
dism /online /disable-feature:windows-identity-foundation
```

檢查使用 DISM 所啟用或停用的功能：

```console
dism /online /get-features
```

或者，在執行 Windows Server 2012 的電腦上，您可以使用 Windows PowerShell `Add-WindowsFeature` Cmdlet 來啟用 WIF 3.5。 若要從命令列這麼做，您可以輸入下列命令：

```console
powershell "add-windowsfeature windows-identity-foundation"
```

 從 Windows PowerShell 環境中，您可以直接輸入下列命令：

```powershell
Add-WindowsFeature windows-identity-foundation
```

> [!NOTE]
> 因為 WIF 3.5 和 WIF 4.5 中的許多類別都共用相同的名稱，所以同時使用 WIF 3.5 和 WIF 4.5 時，請一定要使用完整類別名稱，或使用命名空間別名來區分 WIF 3.5 和 WIF 4.5 中的類別。

## <a name="see-also"></a>另請參閱

- [WIF 組態結構描述](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)
- [WIF 3.5 和 WIF 4.5 之間的命名空間對應](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Windows Identity Foundation 4.5 的新功能](../../../docs/framework/security/whats-new-in-wif.md)
- [Visual Studio 2012 的身分識別與存取工具](../../../docs/framework/security/identity-and-access-tool-for-vs.md)
