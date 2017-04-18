---
title: "將使用 WIF 3.5 建置的應用程式移轉至 WIF 4.5 的方針 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
caps.latest.revision: 12
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 12
---
# 將使用 WIF 3.5 建置的應用程式移轉至 WIF 4.5 的方針
## 適用於  
  
-   Microsoft® Windows® Windows Identity Foundation \(WIF\) 3.5 和 4.5。  
  
## 概觀  
 Windows Identity Foundation \(WIF\) 在 .NET 3.5 SP1 一詞最初放開。  WIF 該版本指 WIF 3.5。  它會釋放為不同的執行階段和 SDK，表示 WIF 允許應用程式必須安排 WIF 安裝執行階段的每部電腦，開發人員必須下載和安裝 WIF SDK 取得 Visual Studio 範本和指定之裝飾 WIF 允許應用程式的可讓開發。  從 .NET 4.5 開始， WIF 完全整合了 .NET Framework。  不同的執行階段不再需要使用 Visual Studio 增益集管理員，然後， WIF \< 出的裝飾可以在 Visual Studio 2012 安裝。  WIF 所指 WIF 4.5。  
  
 WIF 整合到 .NET 中需要在 WIF 應用程式開發介面上的幾項變更。  WIF 4.5 包含新的命名空間、一些變更組態項目和新的值會的裝飾 Visual Studio 的。  本主題提供使用 WIF 3.5 到 WIF 可以用來協助移轉應用程式中 Visual Basic 4.5 的指引。可能有使用電腦上的 WIF 需要執行舊版應用程式的 Visual Basic 3.5 執行 Windows 8 或 Windows Server 2012 的案例。  本主題也提供如何的指引啟用這些作業系統的 WIF 3.5。  
  
## 對於 WIF 需要變更 4.5  
 本節說明要求移轉 WIF 3.5 應用程式到 WIF 4.5 的變更。  
  
### 組件和命名空間變更  
 在 WIF 3.5，所有的 WIF 類別是包含在 `Microsoft.IdentityModel` 組件 \(microsoft.identitymicrosoft.identitymodel.dll\) 包含了。  在 WIF 4.5， WIF 類別跨下列組件中分割: `mscorlib` \(mscorlib.dll\)， `System.IdentityModel` \(System.IdentityModel.dll\)， System.IdentityModel.Services.dll \( `System.IdentityModel.Services` \) 和 `System.ServiceModel` \(System.ServiceModel.dll\)。  
  
 WIF 3.5 類別全部包含在其中一個 `Microsoft.IdentityModel` 命名空間中;例如， `Microsoft.IdentityModel`， `Microsoft.IdentityModel.Tokens`， `Microsoft.IdentityModel.Web`，依此類推。  在 WIF 4.5， WIF 類別跨命名空間、 [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004)<xref:System.Security.Claims?displayProperty=fullName> 命名空間和 <xref:System.ServiceModel.Security?displayProperty=fullName> 命名空間中傳用。  除了這個重新組織外，某些 WIF 3.5 類別在 WIF 4.5 拖曳的項目。  
  
 下表顯示其所包含的幾項重要的 WIF 4.5 命名空間和這種類別。  如需命名空間運作方式的詳細資訊將 WIF WIF 3.5 和 4.5 之間以及 WIF 4.5 置放之命名空間和類別，請參閱 [WIF 3.5 和 WIF 4.5 之間的命名空間對應](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)。  
  
|WIF 4.5 命名空間|Description|  
|------------------|-----------------|  
|<xref:System.IdentityModel?displayProperty=fullName>|包含表示 Cookie 轉換，安全性權杖服務和特定 XML 字典讀取器的類別。  包含從下列 WIF 3.5 命名空間的類別: `Microsoft.IdentityModel`、 `Microsoft.IdentityModel.SecurityTokenService`和 `Microsoft.IdentityModel.Threading`。|  
|<xref:System.Security.Claims?displayProperty=fullName>|包含表示宣告、宣告式識別、宣告以主體和其他宣告架構的識別模型成品的類別。  從 `Microsoft.IdentityModel.Claims` 命名空間中的類別。|  
|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|包含代表安全性權杖、安全性權杖處理常式和其他安全性權杖成品的類別。  包含從下列 WIF 3.5 命名空間的類別: `Microsoft.IdentityModel.Tokens`、 `Microsoft.IdentityModel.Tokens.Saml11`和 `Microsoft.IdentityModel.Tokens.Saml2`。|  
|<xref:System.IdentityModel.Services?displayProperty=fullName>|包含用來被動的類別 \(WS\-Federation\) 案例。  從 `Microsoft.IdentityModel.Web` 命名空間中的類別。|  
|<xref:System.ServiceModel.Security?displayProperty=fullName>|表示 WCF 合約、通道、服務主機和其他成品用於使用中的類別 \(WS\-Trust\) 案例出現在這個命名空間。  在 WIF 3.5，這些類別是在 `Microsoft.IdentityModel.Protocols.WSTrust` 命名空間。|  
  
> [!IMPORTANT]
>  下列 `System.IdentityModel` 命名空間包含實作 WCF 宣告式識別模型的類別: <xref:System.IdentityModel.Claims?displayProperty=fullName>、 <xref:System.IdentityModel.Policy?displayProperty=fullName>和 <xref:System.IdentityModel.Selectors?displayProperty=fullName>。  WCF 宣告式識別模型由 WIF 所取代。  表示建立根據 WIF 時，的方案在這三個命名空間不應該使用類別。  
  
### 變更因為 .NET 整合  
 WIF 現在 .NET Framework。  大部分 .NET 識別和主體類別從 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> 和 <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName>現在衍生。  在下列變更的結果在 WIF 4.5 上:  
  
-   表示宣告的 WIF 類別，識別和主體現在位於 <xref:System.Security.Claims?displayProperty=fullName> 命名空間。  
  
    > [!IMPORTANT]
    >  <xref:System.IdentityModel.Claims?displayProperty=fullName> 命名空間包含表示 WCF 宣告式識別模型成品的類別。  許多這些類別具有相同 WIF 類別的名稱;例如， `Claims`。  表示建立根據 WIF 時，的方案不要使用這些類別。  
  
-   .NET 識別和主體類別直接從 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> 和 <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName>現在衍生，表示宣告架構的識別和主體。  因此， WIF 3.5 介面 `IClaimsIdentity` 和 `IClaimsPrincipal` 不再需要而是 WIF 4.5 中無法使用。  
  
-   Because.NET 識別和主體類別 \(例如 <xref:System.Security.Principal.WindowsIdentity?displayProperty=fullName> 和 <xref:System.Security.Principal.WindowsPrincipal?displayProperty=fullName> 從 <xref:System.Security.Claims.ClaimsIdentity> 中取得，而且 <xref:System.Security.Claims.ClaimsPrincipal>，它們會宣告功能內建。  因此，在 WIF 3.5 的宣告特定識別和主體類別 \(例如 `WindowsClaimsIdentity` 和 `WindowsClaimsPrincipal` 不再需要和不存在於 WIF 4.5。  
  
### 其他變更 WIF 功能  
 除了命名空間變更和之外因為 .NET 整合，對 WIF 功能的下列一般變更在 WIF 4.5 時發生。  
  
-   提供功能可讓您將例外狀況加入至特定的 SOAP 錯誤，移除 `Microsoft.IdentityModel.ExceptionMapper` 類別。  
  
-   大幅減少了例外狀況介面。  
  
-   定義通訊協定或 WS\-\* 特定常數取消的許多類別;例如， `Microsoft.IdentityModel.WSAddressing10Constants` 類別，定義常數與 WS\-Addressing 1.0 相關。  
  
-   在 `Microsoft.IdentityModel.WindowsTokenService` 命名空間中移除 Windows 語彙基元服務 \(c2wts\) 及其相關類別的宣告。  
  
### WIF 配置變更  
 可以在組態檔中的變更是由命名空間更新所造成的在 WIF 4.5。例如，請考慮在套用 `<httpModules>` 區段中的下列 WIF 3.5 輸入將 WS\-Federation 驗證管理員加入至應用程式:  
  
```  
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />  
```  
  
 這個項目在 WIF 4.5 更新包括新的命名空間和組件版本:  
  
```  
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>  
```  
  
 下表列出列舉型別對組態檔的主要變更 WIF 的 4.5。  
  
-   `<microsoft.identityModel>` 區段現在是 [\<system.identityModel\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) 一節。  
  
-   `<service>` 項目現在是 [\<identityConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 項目。  
  
-   新的區段， [\<system.identityModel.services\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)，在被動 \(WS\-Federation 案例\) 將指定設定該控制項行為。  
  
-   [\<federationConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 項目及其子項目在 WIF 3.5 的 `<service>` 項目已移至新的 `<system.identityModel.services>` 項目。  
  
-   可以指定在服務層級直接在 `<service>` 項目底下在 WIF 3.5 的幾個項目會指定在 [\<securityTokenHandlerConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) 項目中。\(它們仍然能夠指定在 [\<identityConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 項目下的 WIF 4.5 為回溯相容性 \(Backward Compatibility\)。  
  
 如需 WIF 4.5 組態項目的完整清單，請參閱 [WIF 組態結構描述](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)。  
  
### 工具變更的 Visual Studio  
 WIF 3.5 SDK 提供了獨立的聯合公用程式， FedUtil.exe \(FedUtil\)，您可以使用外包在 WIF 允許應用程式的識別管理到 Security Token Service \(STS\)。  這個工具在 Visual Studio 將 WIF 設定加入至應用程式組態檔中啟用應用程式從一個或多個取得安全性權杖 STSs 和公開了 \(透過 \[**加入包含服務參考**\] 按鈕。  FedUtil 不隨附 WIF 4.5。相反地， WIF 4.5 支援新的 Visual Studio 擴充功能命名為可用來修改以要求的 WIF 設定應用程式的組態檔外包識別管理至 STS 的 Visual Studio 2012 的識別和存取工具。  識別和存取工具也會實作可用來測試您的 WIF 允許應用程式的 STS 呼叫的 Local STS。  在大部分情況下，這項功能不需要建置通常需要在 WIF 3.5 開發中測試方案的自訂 STSs。  因此， STS 範本在 Visual Studio 2012 不再支援;不過，支援 STSs 開發的類別可在 WIF 4.5。  
  
 您可以安裝識別和從擴充存取工具並更新 Visual Studio 的管理員或可以從在程式碼繪製廊的下列頁面: [為 Visual Studio 2012 的識別和存取工具程式碼繪製廊的](http://go.microsoft.com/fwlink/?LinkID=245849).  工具變更的 Visual Studio 在下列清單將摘要說明:  
  
-   取消加入包含服務參考功能。  取代為識別和存取工具。  
  
-   移除 Visual Studio STS 範本。  您可以用來識別和存取工具可供測試識別方案您開發與 WIF 區域的 STS。  可以修改區域的 STS 組態自訂服務其宣告。  
  
-   獨立聯合公用程式 \(FedUtil\) 是 WIF 4.5 中無法使用。您可以使用識別和存取工具修改您的組態檔外包識別管理至 STS。  
  
 如需識別和存取工具的詳細資訊，請參閱 [Visual Studio 2012 的識別和存取工具](../../../docs/framework/security/identity-and-access-tool-for-vs.md)  
  
<a name="BKMK_ToolingChanges"></a>   
### 被動 \(WS\-Federation\) 案例:  
  
-   支援被動案例的類別已移至 <xref:System.IdentityModel.Services?displayProperty=fullName> 命名空間。  在 WIF 3.5 這些類別在 `Microsoft.IdentityModel.Web` 命名空間。  
  
-   在 `Microsoft.IdentityModel.Web.Configuration` 命名空間中的類別已移至 <xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>。  這些類別代表特定的物件至被動案例的組態。  
  
-   `FederatedPasssiveSignInControl` 不再受支援;在 `Microsoft.IdentityModel.Web.Controls` 命名空間中所有類別從 WIF 4.5 已取消。  
  
-   WS\-Federation 驗證模組 \(<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>\) 標記功能對於 WIF 3.5 不同。  如需詳細資訊與標記如何在 WIF 4.5 運作，請參閱 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 類別主題。  
  
### 使用中 \(\) WCF\/WS 信任案例:  
  
-   `Microsoft.IdentityModel.Protocols.WSTrust` 命名空間會分割成主要在 WIF 4.5 的兩個命名空間。代表成品專屬於 WS\-Trust 通訊協定的類別出現在 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName>。  這包括如 <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>的類別。  代表服務合約、通道、服務主機和其他成品在使用包含 WS\-Trust WCF 應用程式的類別已移至 <xref:System.ServiceModel.Security?displayProperty=fullName>;例如， <xref:System.ServiceModel.Security.IWSTrust13AsyncContract> 介面。  
  
-   設定 WCF 應用程式使用 WIF 大幅簡化了。  先前 `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` 必須加入做為行為延伸，並指定 `<federatedServiceHostConfiguration>` 項目接著會使用這項功能楔住 WIF 入服務行為。  WIF 4.5 緊密整合與 WCF。  現在您可以指定 `useIdentityConfiguration` 屬性啟用 WCF 服務的 WIF 在 `<system.serviceModel>`\/`<behaviors>`\/`<serviceBehaviors>`\/`<serviceCredentials>` 項目在下列 XML:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
-   在 WIF 4.5 在服務主機必須指定現用 \(WCF\) 服務的服務憑證。  如前述範例所示，在組態中，您可以透過 `<system.serviceModel>`\/`<behaviors>`\/`<serviceBehaviors>`\/`<serviceCredentials>`\/`<serviceCertificate>` 項目\)。  在 WIF 3.5 服務憑證可以 WIF `<service>` 項目的 `<serviceCertificate>` 子項目指定。  這項功能不存在於 WIF 4.5;指定 `<serviceCertificate>` 項目在 `<serviceCredentials>` 項目底下。  
  
-   用於類別楔住 WIF 3.5 到 WCF 不存在。  這包含 `Microsoft.IdentityModel.Tokens` 命名空間包含下列類別: `FederatedSecurityTokenManager`、 `FederatedServiceCredentials`和 `IdentityModelServiceAuthorizationManager`，以及 `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` 類別。  
  
## 若要在 Windows 8 的 WIF 3.5  
 由於 WIF 4.5 是 .NET 4.5 的一部分，它在執行 Windows 8 的電腦上自動啟用，而且預設會建立使用 WIF 4.5 的 Windows Server 2012 和應用程式將會在 Windows 8 或 Windows Server 2012 下。  不過，您可能需要執行建置使用電腦上的 WIF 3.5 執行 Windows 8 或 Windows Server 2012 的應用程式。  在這種情況下，您必須在目標電腦上的 WIF 3.5。  使用部署映像服務與管理 \(DISM\) 工具，在執行 Windows 8 的電腦上，您可以這麼做。  在電腦上執行 Windows Server 2012 上，您可以使用該胎工具或使用 Windows PowerShell Cmdlet `Add-WindowsFeature` 。  在這兩種情況下，適當的命令可以叫用命令列或從 Windows PowerShell 環境內部。  
  
 下列命令會顯示如何使用輪胎工具從命令列或從 Windows PowerShell 環境內部。  根據預設， DISM PowerShell 模組在 Windows 8 和 Windows Server 2012 中，而且不需要匯入。  如需使用 Windows PowerShell 的 DISM 的詳細資訊，請 [如何使用 DISM 在 Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=254419)參閱。  
  
 使用 DISM，啟用 WIF 3.5:  
  
```  
dism /online /enable-feature:windows-identity-foundation  
```  
  
 使用 DISM，停用 WIF 3.5:  
  
```  
dism /online /disable-feature:windows-identity-foundation  
```  
  
 檢查 DISM，哪些功能啟用或停用:  
  
```  
dism /online /get-features  
```  
  
 或者，您可以使用 Windows PowerShell Cmdlet `Add-WindowsFeature` ，在執行 Windows Server 2012 的電腦上，您可以啟用 WIF 3.5。  從命令列來執行，您可以輸入下列命令:  
  
```  
powershell "add-windowsfeature windows-identity-foundation"  
```  
  
 從 Windows PowerShell 環境內部，您可以直接輸入命令:  
  
```  
add-windowsfeature windows-identity-foundation  
```  
  
> [!NOTE]
>  由於許多在 WIF 3.5 和 4.5 WIF 共用的類別名稱相同，也就是說，當您使用 WIF WIF 3.5 和 4.5，就一定要用來完整類別名稱或使用命名空間別名區別在 WIF 3.5 和 4.5 的 WIF 類別之間。  
  
## 請參閱  
 [WIF 組態結構描述](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)   
 [WIF 3.5 和 WIF 4.5 之間的命名空間對應](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)   
 [Windows Identity Foundation 4.5 的新功能](../../../docs/framework/security/whats-new-in-wif.md)   
 [Visual Studio 2012 的識別和存取工具](../../../docs/framework/security/identity-and-access-tool-for-vs.md)