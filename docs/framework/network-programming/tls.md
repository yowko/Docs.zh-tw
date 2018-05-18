---
title: .NET Framework 的傳輸層安全性 (TLS) 最佳做法
description: 描述搭配 .NET Framework 使用傳輸層安全性 (TLS) 的最佳做法
ms.date: 03/15/2018
helpviewer_keywords:
- sending data, Internet security
- protocols, Internet security
- Network security
- network resources, Internet security
- receiving data, Internet security
- authentication [.NET Framework], Internet security
- Internet, security
- security [.NET Framework], Internet
- permissions [.NET Framework], Internet
author: blowdart
ms.openlocfilehash: 41814129d038f8cb1ab98db0c7a4e0cbd7e7cd54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>.NET Framework 的傳輸層安全性 (TLS) 最佳做法

傳輸層安全性 (TLS) 通訊協定為一項業界標準，其設計目的是用來協助保護透過網際網路所通訊之資訊的隱私權。 [TLS 1.2](https://tools.ietf.org/html/rfc5246) \(英文\) 為最新發行的標準，並能提供優於先前版本的安全性。 TLS 1.2 於未來將會由 [TLS 1.3](https://tools.ietf.org/html/draft-ietf-tls-tls13-22) \(英文\) 取代。 本文提供保護使用 TLS 通訊協定之 .NET Framework 應用程式的建議。

為了確保能維持 .NET Framework 應用程式的安全性，TLS 版本**不應**為硬式編碼。 .NET Framework 應用程式應使用作業系統 (OS) 所支援的 TLS 版本。

本文件適用於下列開發人員：

- 直接使用 <xref:System.Net> API (例如，<xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 和 <xref:System.Net.Security.SslStream?displayProperty=nameWithType>) 的開發人員。
- 直接使用運用 <xref:System.ServiceModel?displayProperty=nameWithType> 命名空間之 WCF 用戶端和服務的開發人員。
- 使用 [Azure 雲端服務](https://azure.microsoft.com/services/cloud-services/) Web 角色及背景工作角色來主控及執行您應用程式的開發人員。 請參閱 [Azure 雲端服務](#azure-cloud-services)一節。

建議您：

- 在應用程式上以 .NET Framework 4.7 或更新版本作為目標。 在 WCF 應用程式上以 .NET Framework 4.7.1 或更新版本作為目標。
- 不要指定 TLS 版本。 設定程式碼以由 OS 決定 TLS 版本。
- 執行完整的程式碼稽核，以確認您沒有指定 TLS 或 SSL 版本。

當應用程式讓 OS 選擇 TLS 版本時：

- 它會自動運用於未來新增的新通訊協定，例如 TLS 1.3。
- OS 會封鎖被發現不安全的通訊協定。

[對程式碼進行稽核並做出程式碼變更](#audit-your-code-and-make-code-changes)一節會涵蓋對程式碼進行稽核及更新的相關內容。

本文說明如何針對應用程式所執行的.NET Framework 版本，啟用可供使用的最強安全性。 當應用程式明確設定安全性通訊協定及版本時，它將會退出所有其他替代方案，並退出 .NET Framework 及 OS 預設行為。 如果您想讓應用程式能夠交涉 TLS 1.2 連線，明確設定至較低的 TLS 版本將會防止 TLS 1.2 連線。

如果您無法避免採取通訊協定版本的硬式編碼，我們強烈建議您指定 TLS 1.2。 如需識別及移除 TLS 1.0 相依性的指引，請下載[解決 TLS 1.0 問題](https://www.microsoft.com/download/details.aspx?id=55266) \(英文\) 白皮書。

在 .NET Framework 4.7 中，WCF 預設支援 TLS1.0、1.1 及 1.2。 從 .NET Framework 4.7.1 開始，WCF 預設會使用作業系統所設定的版本。 如果有應用程式是搭配 `SslProtocols.None` 進行明確設定，WCF 在使用 NetTcp 傳輸時，便會使用作業系統的預設設定。

您可以在 GitHub 問題 [.NET Framework 的傳輸層安全性 (TLS) 最佳做法](https://github.com/dotnet/docs/issues/4675) \(英文\) 中，詢問與本文件相關的問題。

## <a name="audit-your-code-and-make-code-changes"></a>對程式碼進行稽核並做出程式碼變更

針對 ASP.NET 應用程式，請檢查 _web.config_ 的 `<system.web><httpRuntime targetFramework>` 元素，以確認您是使用正確的 .NET Framework 版本。

針對 Windows Forms 及其他應用程式，請參閱[如何：將 .NET Framework 的某個版本設定為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。

使用下列小節來確認您沒有使用特定的 TLS 或 SSL 版本。

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>若應用程式是以 .NET Framework 4.7 或更新版本作為目標

下列小節會示範如何確認您沒有使用特定的 TLS 或 SSL 版本。

### <a name="for-http-networking"></a>針對 HTTP 網路功能

<xref:System.Net.ServicePointManager>，在使用 .NET Framework 4.7 及更新版本的情況下，預設會讓 OS 選擇最佳的安全性通訊協定和版本。 若要在可能的情況下取得最佳的預設 OS 選擇，請不要為 <xref:System.Net.ServicePointManager.SecurityProtocol> 屬性設定值。 否則請將其設定為 <xref:System.Net.SecurityProtocolType.SystemDefault>。

本文剩下的內容，與針對 HTTP 網路功能將 .NET Framework 4.7 或更新版本設為目標無關。

### <a name="for-tcp-sockets-networking"></a>針對 TCP 通訊端網路功能

<xref:System.Net.Security.SslStream>，在使用 .NET Framework 4.7 及更新版本的情況下，預設會讓 OS 選擇最佳的安全性通訊協定和版本。 若要在可能的情況下取得最佳的預設 OS 選擇，請不要使用會採用明確 <xref:System.Security.Authentication.SslProtocols> 參數之 <xref:System.Net.Security.SslStream> 的方法多載。 否則，請傳遞 <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>。 建議您不要使用 <xref:System.Security.Authentication.SslProtocols.Default>；設定 `SslProtocols.Default` 會強制使用 SSL 3.0/TLS 1.0 並防止 TLS 1.2。

不要為 <xref:System.Net.ServicePointManager.SecurityProtocol> 屬性 (針對 HTTP 網路功能) 設定值。

不要使用會採用明確 <xref:System.Security.Authentication.SslProtocols> 參數 (針對 TCP 通訊端網路功能) 之 <xref:System.Net.Security.SslStream> 的方法多載。 當您將應用程式目標重新設為 .NET Framework 4.7 或更新版本時，即是遵循最佳做法建議。

本主題剩下的內容，與針對 TCP 通訊端網路功能將 .NET Framework 4.7 或更新版本設為目標無關。

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>針對搭配憑證認證使用傳輸安全性的 WCF TCP 傳輸

WCF 會使用和其他 .NET Framework 相同的網路堆疊。

若您是以 4.7.1 為目標，WCF 預設便已設定為允許 OS 選擇最佳的安全性通訊協定，除非另外透過下列方式明確設定：

- 在您的應用程式組態檔中。
- **或**在您應用程式的原始程式碼中。

根據預設，.NET Framework 4.7 及更新版本已設定為使用 TLS 1.2，並允許使用 TLS 1.1 或 TLS 1.0 的連線。 特過設定繫結以使用 <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>，來設定 WCF 以允許 OS 選擇最佳的安全性通訊協定。 這可以在 <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols> 上設定。 `SslProtocols.None` 可以從 <xref:System.ServiceModel.NetTcpSecurity.Transport> 存取。 `NetTcpSecurity.Transport` 可以從 <xref:System.ServiceModel.NetTcpBinding.Security> 存取。

若您是使用自訂繫結：

- 特過設定 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> 以使用 <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>，來設定 WCF 以允許 OS 選擇最佳的安全性通訊協定。
- **或**透過設定路徑 `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols` 來設定所使用的通訊協定。

若您**沒有** 使用自訂繫結，**且**您是使用設定來設定 WCF 繫結，請透過設定路徑 `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols` 來設定所使用的通訊協定。

### <a name="for-wcf-message-security-with-certificate-credentials"></a>針對具有憑證認證的 WCF 訊息安全性

.NET Framework 4.7 及更新版本預設會使用於 <xref:System.Net.ServicePointManager.SecurityProtocol> 屬性中指定的通訊協定。 當 [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` 設定為 `true` 時，WCF 會選擇最佳的通訊協定 (最高版本為 TLS 1.0)。

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>若應用程式是以 .NET Framework 4.7 之前的版本為目標

使用下列小節來對程式碼進行稽核，以確認您沒有使用特定的 TLS 或 SSL 版本：

### <a name="for-net-framework-46---462-and-not-wcf"></a>針對 .NET Framework 4.6 - 4.6.2 且非 WCF

將 `DontEnableSystemDefaultTlsVersions` `AppContext` 參數設定為 `false`。 請參閱[透過 AppContext 參數設定安全性](#configuring-security-via-appcontext-switches)。

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>針對使用搭配憑證認證使用 TCP 傳輸安全性之 .NET Framework 4.6 至 4.6.2 的 WCF

您必須安裝最新的 OS 修補程式。 請參閱[安全性更新](#security-updates)。

WCF 架構會自動選擇可用的最高版本通訊協定 (最高版本為 TLS 1.2)，除非您明確設定通訊協定版本。 如需詳細資訊，請參閱先前的[針對搭配憑證認證使用傳輸安全性的 WCF TCP 傳輸](#wcf-tcp-cert)一節。

### <a name="for-net-framework-35---451-and-not-wcf"></a>針對 .NET Framework 3.5 至 4.5.1 且非 WCF

我們建議您將應用程式升級至 .NET Framework 4.7 或更新版本。 如果您無法升級，請採取下列步驟。 在未來的某個時間點，若不將您的應用程式升級至 .NET Framework 4.7 或更新版本，該應用程式可能會失敗。

將 [SchUseStrongCrypto](#schusestrongcrypto) 和 [SystemDefaultTlsVersions](#systemdefaulttlsversions) 登錄機碼設定為 1。 請參閱[透過 Windows 登錄來設定安全性](#configuring-security-via-the-windows-registry)。 .NET Framework 3.5 版只有在傳遞明確 TLS 值時，才會支援 `SchUseStrongCrypto` 旗標。

若您是執行 .NET Framework 3.5，便需要安裝修補程式，使您的程式可以指定 TLS 1.2：

| [KB3154518](https://support.microsoft.com/kb/3154518) | 可靠性彙總套件 HR-1605 - 針對 TLS 系統預設版本的支援已包含在 Windows 7 SP1 和 Server 2008 R2 SP1 上的 .NET Framework 3.5.1 中 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | 可靠性彙總套件 HR-1605 - 針對 TLS 系統預設版本的支援已包含在 Windows Server 2012 上的 .NET Framework 3.5 中 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | 可靠性彙總套件 HR-1605 - 針對 TLS 系統預設版本的支援已包含在 Windows 8.1 和 Windows Server 2012 R2 的 .NET Framework 3.5 中 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | 適用於 Windows 上的 .NET Framework 4.5.2 和 4.5.1 的 1605 Hotfix 彙總套件 3154521 |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>針對使用搭配憑證認證使用 TCP 傳輸安全性之 .NET Framework 3.5 至 4.5.2 的 WCF

這些版本的 WCF 架構具有使用 SSL 3.0 和 TLS 1.0 值的硬式編碼。 這些值不能變更。 您必須更新並將目標重新設定為 NET Framework 4.6 或更新版本，以使用 TLS 1.1 和 1.2。

## <a name="if-your-app-targets-net-framework-35"></a>若應用程式是以 .NET Framework 3.5 作為目標

若您必須明確設定安全性通訊協定，而不是讓 .NET framework 或 OS 選擇安全性通訊協定，請將 `SecurityProtocolTypeExtensions` 和 `SslProtocolsExtension` 列舉新增至您的程式碼。 `SecurityProtocolTypeExtensions` 和 `SslProtocolsExtension` 包含適用於 `Tls12`、`Tls11` 的值，以及 `SystemDefault` 值。 請參閱[針對 TLS 系統預設版本的支援已包含在 Windows 8.1 和 Windows Server 2012 R2 的 .NET Framework 3.5 中](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) \(機器翻譯\)。

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>透過 AppContext 參數設定安全性 (適用於 .NET Framework 4.6 或更新版本)

只有在您的應用程式是以 .NET Framework 4.6 或更新版本為目標 (或是在其上執行) 的情況下，才會與描述於本節的 [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數具關連性。 無論是根據預設設定，或是透過明確設定這些參數，它們在可能的情況下都應為 `false`。 若您想要透過其中一個或同時透過這兩個參數來設定安全性，請不要在程式碼中指定安全性通訊協定，因為這麼做將會覆寫這些參數。

無論您是執行 HTTP 網路功能 (<xref:System.Net.ServicePointManager>) 或 TCP 通訊端網路功能 (<xref:System.Net.Security.SslStream>)，這些參數都具有相同的效果。

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

將 `Switch.System.Net.DontEnableSchUseStrongCrypto` 設定為 `false` 值，會導致您的應用程式使用強式加密。 將 `DontEnableSchUseStrongCrypto` 設定為 `false` 值，會使用更安全的網路通訊協定 (TLS 1.2、TLS 1.1 及 TLS 1.0)，並封鎖不安全的通訊協定。 如需詳細資訊，請參閱 [SCH_USE_STRONG_CRYPTO 旗標](#the-schusestrongcrypto-flag)。 設定為 `true` 值會停用應用程式的強式加密。

若應用程式是以 .NET Framework 4.6 或更新版本作為目標，此參數預設會設定為 `false`。 那是安全的預設值，也是我們建議的選項。 若您的應用程式是在 .NET Framework 4.6 上執行，但是以較舊的版本為目標，此參數預設會設定為 `true`。 在此情況下，您應該明確地將它設定為 `false`。

若您需要連線至不支援強式加密且無法升級的舊版服務，則 `DontEnableSchUseStrongCrypto` 應該僅設定為 `true` 值。

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

將 `Switch.System.Net.DontEnableSystemDefaultTlsVersions` 設為 `false` 值，會導致您的應用程式允許作業系統選擇通訊協定。 設定為 `true` 值會導致您的應用程式使用由 .NET Framework 所選取的通訊協定。

若應用程式是以 .NET Framework 4.7 或更新版本作為目標，此參數預設會設定為 `false`。 這是建議的安全預設值。 若您的應用程式是在 .NET Framework 4.7 或更新版本上執行，但是以較舊的版本為目標，此參數預設會設定為 `true`。 在此情況下，您應該明確地將它設定為 `false`。

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

將 `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` 設定為 `false` 值，會導致您的應用程式針對使用憑證認證的訊息安全性，使用定義於 `ServicePointManager.SecurityProtocols` 中的值。 設定為 `true` 值會使用可用的最高版本通訊協定 (最高版本為 TLS1.0)

針對以 .NET Framework 4.7 及更新版本為目標的應用程式，此值預設會設定為 `false`。 針對以 .NET Framework 4.6.2 及較舊版本為目標的應用程式，此值預設會設定為 `true`。

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

將 `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` 設為 `false` 值，會設定預設設定以允許作業系統選擇通訊協定。 設定為 `true` 值會將預設值設定為可用的最高版本通訊協定 (最高版本為 TLS1.2)。

針對以 .NET Framework 4.7.1 及更新版本為目標的應用程式，此值預設會設定為 `false`。 針對以 .NET Framework 4.7 及較舊版本為目標的應用程式，此值預設會設定為 `true`。

如需 TLS 通訊協定的詳細資訊，請參閱[風險降低：TLS 通訊協定](../migration-guide/mitigation-tls-protocols.md)。 如需 `AppContext` 參數的詳細資訊，請參閱 [`<AppContextSwitchOverrides> Element`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

## <a name="configuring-security-via-the-windows-registry"></a>透過 Windows 登錄來設定安全性

如果您無法設定其中一個 `AppContext` 參數 (或是兩個都無法設定)，則可以透過本節中描述的 Windows 登錄機碼來控制應用程式所使用的安全性通訊協定。 如果您的應用程式是以 .NET Framework 4.6 版之前的版本為目標，或是無法編輯設定檔，便可能無法使用其中一個 `AppContext` 參數，或是兩個都無法使用。 若您想要透過登錄來設定安全性，請不要在程式碼中指定安全性通訊協定，因為這麼做將會覆寫這些登錄。

登錄機碼的名稱與相對應的 `AppContext` 參數類似，但名稱前方不會有 `DontEnable`。 例如，`AppContext` 參數 `DontEnableSchUseStrongCrypto` 就是稱為 [SchUseStrongCrypto](#schusestrongcrypto) 的登錄機碼。

這些機碼已透過近日的安全性修補程式，於所有 .NET Framework 版本中提供。 請參閱[安全性更新](#security-updates)。

無論您是執行 HTTP 網路功能 (<xref:System.Net.ServicePointManager>) 或 TCP 通訊端網路功能 (<xref:System.Net.Security.SslStream>)，下列所描述的登錄機碼都具有相同的效果。

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` 登錄機碼具有 DWORD 類型的值。 將值設為 1 會導致您的應用程式使用強式加密。 強式加密會使用更安全的網路通訊協定 (TLS 1.2、TLS 1.1 及 TLS 1.0)，並封鎖不安全的通訊協定。 將值設為 0 會停用強式加密。 如需詳細資訊，請參閱 [SCH_USE_STRONG_CRYPTO 旗標](#the-schusestrongcrypto-flag)。

若應用程式是以 .NET Framework 4.6 或更新版本作為目標，此機碼預設會設定為 1。 這是建議的安全預設值。 若您的應用程式是在 .NET Framework 4.6 上執行，但是以較舊的版本為目標，此機碼預設會設定為 0。 在此情況下，您應該明確地將它的值設定為 1。

若您需要連線至不支援強式加密且無法升級的舊版服務，則此機碼的值應該僅設定為 0。

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` 登錄機碼具有 DWORD 類型的值。 將值設為 1 會導致您的應用程式允許作業系統選擇通訊協定。 將值設為 0 會導致您的應用程式使用由 .NET Framework 所選取的通訊協定。

`<VERSION>` 必須是 v4.0.30319 (針對 .NET Framework 4 及更新版本) 或 v2.0.50727 (針對 .NET Framework 3.5)。

若應用程式是以 .NET Framework 4.7 或更新版本作為目標，此機碼預設會設定為 1。 這是建議的安全預設值。 若您的應用程式是在 .NET Framework 4.7 或更新版本上執行，但是以較舊的版本為目標，此機碼預設會設定為 0。 在此情況下，您應該明確地將它的值設定為 1。

如需詳細資訊，請參閱 [Windows 10 1511 版和 Windows Server 2016 Technical Preview 4 的累積更新：2016 年 5 月 10 日](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016)。

如需 .NET Framework 3.5.1 的詳細資訊，請參閱[針對 TLS 系統預設版本的支援已包含在 Windows 7 SP1 和 Server 2008 R2 SP1 上的 .NET Framework 3.5.1 中](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) \(機器翻譯\)。

下列 _.REG_ 檔案會將登錄機碼及其變體設定為最安全的值：

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001
```

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>在 Windows 登錄中設定安全通道通訊協定

您可以使用登錄以對您用戶端和/或伺服器應用程式交涉的通訊協定進行細微的控制。 您應用程式的網路功能會透過[安全通道](https://msdn.microsoft.com/library/windows/desktop/aa380123) \(英文\) 進行。 透過設定 `Schannel`，您便可以設定應用程式的行為。

請從 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` 登錄機碼開始。 在該機碼底下，您可以在 `SSL 2.0`、`SSL 3.0`、`TLS 1.0`、`TLS 1.1` 及 `TLS 1.2` 集合中建立任何子機碼。 在那些子機碼底下，您可以建立子機碼 `Client` 和/或 `Server`。 在 `Client` 和 `Server` 底下，您可以建立 DWORD 值 `DisabledByDefault` (0 或 1) 和 `Enabled` (0 或 0xFFFFFFFF)。

## <a name="the-schusestrongcrypto-flag"></a>SCH_USE_STRONG_CRYPTO 旗標

啟用 `SCH_USE_STRONG_CRYPTO` 旗標時 (預設會由 `AppContext` 參數或 Windows 登錄啟用)，.NET Framework 會在您的應用程式要求 TLS 安全性通訊協定時使用此旗標。 `SCH_USE_STRONG_CRYPTO` 旗標可以依預設啟用、搭配 `AppContext` 參數啟用，或是搭配登錄啟用。 OS 會將旗標傳遞至 `Schannel`，以指示它停用已知的弱式加密演算法、加密套件，以及 TLS/SSL 通訊協定版本；若不這樣做，系統可能會為了取得更佳的互通性而啟用這些項目。 如需詳細資訊，請參閱:

- [安全通道](https://msdn.microsoft.com/library/windows/desktop/aa380123) \(英文\)
- [SCHANNEL_CRED 結構](https://msdn.microsoft.com/library/windows/desktop/aa379810) \(英文\)

當您明確使用 <xref:System.Net.SecurityProtocolType> 或 <xref:System.Security.Authentication.SslProtocols> 的 `Tls` (TLS 1.0)、`Tls11` 或 `Tls12` 列舉值時，`SCH_USE_STRONG_CRYPTO` 旗標也會傳遞至 `Schannel`。

## <a name="security-updates"></a>安全性更新

本文中的最佳做法取決於所安裝的最新安全性更新。 這些更新包括使用進階 .NET Framework 4.7 和更新版本功能的能力。 如果您的應用程式是在 .NET Framework 4.7 和更新版本上執行，則最新的安全性更新十分重要 (即使應用程式是以舊版為目標)。

若要更新 .NET Framework 以允許作業系統選擇要使用的最佳 TLS 版本，您至少必須安裝：

- [.NET Framework 2017 年 8 月品質彙總套件預覽](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup) \(英文\)。
- **或者** [.NET Framework 2017 年 9 月安全性與品質彙總套件](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup) \(英文\)。

另請參閱：

- [.NET Framework 版本和相依性](../migration-guide/versions-and-dependencies.md)
- [如何：判斷所安裝的 .NET Framework 版本](../migration-guide/how-to-determine-which-versions-are-installed.md)。

## <a name="support-for-tls-12"></a>支援 TLS 1.2

若要讓您的應用程式交涉 TLS 1.2，作業系統和 .NET Framework 版本都需要支援 TLS 1.2。

**支援 TLS 1.2 的作業系統要求**

若要在支援 TLS 1.2 和/或 TLS 1.1 的系統上啟用或重新啟用它們，請參閱[傳輸層安全性 (TLS) 登錄設定](/windows-server/security/tls/tls-registry-settings)。

| **作業系統** | **TLS 1.2 支援** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | 支援且預設會啟用。 |
| Windows 8.1</br>Windows Server 2012 R2 | 支援且預設會啟用。 |
| Windows 8.0</br>Windows Server 2012 | 支援且預設會啟用。 |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | 支援但預設不會啟用。 如需如何啟用 TLS 1.2 的詳細資訊，請參閱[傳輸層安全性 (TLS) 登錄設定](/windows-server/security/tls/tls-registry-settings)網頁。 |
| Windows Server 2008 | 支援 TLS 1.2 和 TLS 1.1 需要更新。 請參閱[在 Windows Server 2008 SP2 中加入 TLS 1.1 和 TLS 1.2 支援的更新](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s)。 |
| Windows Vista | 不支援。 |

如需每個 Windows 版本上所預設啟用 TLS/SSL 通訊協定的相關資訊，請參閱 [TLS/SSL (Schannel SSP) 中的通訊協定](https://msdn.microsoft.com/library/windows/desktop/mt808159) \(英文\)。

**使用 .NET Framework 3.5 支援 TLS 1.2 的要求**

此表格顯示使用 .NET Framework 3.5 支援 TLS 1.2 所需的作業系統更新。 建議您套用所有的作業系統更新。

| **作業系統** | **使用 .NET Framework 3.5 支援 TLS 1.2 所需的最低更新** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | [適用於 Windows 10 1511 版和 Windows Server 2016 Technical Preview 4 的累積更新：2016 年 5 月 10 日](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1</br>Windows Server 2012 R2 | [支援 Windows 8.1 和 Windows Server 2012 R2 上 .NET Framework 3.5 所包含的 TLS 系統預設版本](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) \(機器翻譯\) |
| Windows 8.0</br>Windows Server 2012 | [支援 Windows Server 2012 上 .NET Framework 3.5 所包含的 TLS 系統預設版本](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) \(機器翻譯\) |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | [支援 Windows 7 SP1 和 Server 2008 R2 SP1 上 .NET Framework 3.5.1 所包含的 TLS 系統預設版本](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) \(機器翻譯\) |
| Windows Server 2008 | [支援 Windows Vista SP2 和 Server 2008 SP2 上 .NET Framework 2.0 SP2 所包含的 TLS 系統預設版本](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) \(機器翻譯\) |
| Windows Vista | 不支援 |

## <a name="azure-cloud-services"></a>Azure 雲端服務

如果您是使用 [Azure 雲端服務](https://azure.microsoft.com/services/cloud-services/) Web 和 背景工作角色來裝載和執行應用程式，則支援 TLS 1.2 時會有一些額外考量。

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>根據預設，Azure 客體作業系統上未安裝 .NET Framework 4.7

最新的 Azure 客體作業系統 5 系列版本 (Windows Server 2016) 中安裝的最新版本是 4.6.2。 若要查看每個 Azure 客體作業系統上所安裝的 .NET Framework 版本，請參閱 [Azure 客體作業系統版本和 SDK 相容性矩陣](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix)。

如果應用程式以 Azure 客體作業系統版本上未提供的 .NET Framework 版本為目標，則您需要自行安裝。 請參閱[在 Azure 雲端服務角色上安裝 .NET](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet)。 如果 Framework 安裝需要重新啟動，則在進入就緒狀態之前，服務角色可能也會重新啟動。

### <a name="azure-guest-os-registry-settings"></a>Azure 客體作業系統登錄設定

[Azure 雲端服務](https://azure.microsoft.com/services/cloud-services/)的 Azure 客體作業系統映像已將 `SchUseStrongCrypto` 登錄機碼值設定為 1。 如需詳細資訊，請參閱 [SchUseStrongCrypto](#schusestrongcrypto)。

將 [SystemDefaultTlsVersions](#systemdefaulttlsversions) 登錄機碼設定為 1。 請參閱[透過 Windows 登錄來設定安全性](#configuring-security-via-the-windows-registry)。
