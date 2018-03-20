---
title: "傳輸層安全性 (TLS) 以.NET Framework 的最佳作法"
description: "說明使用.NET Framework 中的傳輸層安全性 (TLS) 的最佳作法"
ms.date: 03/15/2018
ms.prod: .net-framework
ms.topic: article
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
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64829eee5b21a44acb18cbec9b901d77d49cab90
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2018
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>傳輸層安全性 (TLS) 以.NET Framework 的最佳作法

傳輸層安全性 (TLS) 通訊協定是資訊的一項工業標準，其設計目的是資訊的協助保護在網際網路上通訊的隱私權。 [TLS 1.2](https://tools.ietf.org/html/rfc5246)是最新發行的標準，並提供舊版所沒有的安全性增強功能。 TLS 1.2 最終會取代[TLS 1.3](https://tools.ietf.org/html/draft-ietf-tls-tls13-22)。 本文件提供建議，可安全使用 TLS 通訊協定的.NET Framework 應用程式。

若要確定.NET Framework 應用程式仍然安全，TLS 版本應該**不**硬式編碼。 .NET framework 應用程式應該使用 TLS 版本支援的作業系統 (OS)。

這份文件為目標的開發人員：

- 直接使用<xref:System.Net>應用程式開發介面 (例如，<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>和<xref:System.Net.Security.SslStream?displayProperty=nameWithType>)。
- 直接使用 WCF 用戶端和服務使用<xref:System.ServiceModel?displayProperty=nameWithType>命名空間。
- 使用[Azure 雲端服務](https://azure.microsoft.com/services/cloud-services/)Web 和背景工作角色，以主控和執行您的應用程式。 請參閱[Azure 雲端服務](#azure-cloud-services)> 一節。

我們建議您：

- .NET Framework 4.7 或在您的應用程式的更新版本為目標。 目標.NET Framework 4.7.1 或更新版本建立的 WCF 應用程式。
- 請勿指定 TLS 版本。 設定您的程式碼，以便決定 TLS 版本的作業系統。
- 執行完整的程式碼稽核以確認您不會指定 TLS 或 SSL 的版本。

當您的應用程式可讓選擇 TLS 版本的作業系統：

- 它會自動利用新的通訊協定，例如 TLS 1.3 未來，加入。
- 作業系統會封鎖，會發現不安全的通訊協定。

區段[稽核您的程式碼並進行程式碼變更](#audit-your-code-and-make-code-changes)涵蓋稽核及更新您的程式碼。

本文說明如何啟用適用於您的應用程式為目標，且會執行的.NET framework 版本的最強安全性。 當應用程式會明確設定安全性通訊協定和版本時，它選擇不任何其他替代方案，並選擇.NET Framework 和作業系統的預設行為不。 如果您想要能夠交涉的 TLS 1.2 連接您的應用程式時，明確地將設定為較低的 TLS 版本可防止 TLS 1.2 的連接。

如果您無法避免硬式編碼通訊協定版本，我們強烈建議您指定 TLS 1.2。 如需識別和移除 TLS 1.0 的相依性指引，下載[解決 TLS 1.0 問題](https://www.microsoft.com/download/details.aspx?id=55266)白皮書。

WCF 支援 TLS1.0、 1.1 和 1.2 為.NET Framework 4.7 中的預設值。 從.NET Framework 4.7.1 開始，WCF 會預設為系統設定版本。 如果應用程式已明確設定`SslProtocols.None`，WCF 會使用 NetTcp 傳輸時，會使用作業系統的預設設定。

您可以詢問問題相關的文件中 GitHub 問題[傳輸層安全性 (TLS) 的最佳作法，以.NET Framework](https://github.com/dotnet/docs/issues/4675)。

## <a name="audit-your-code-and-make-code-changes"></a>稽核您的程式碼並進行程式碼變更

ASP.NET 應用程式，檢查`<system.web><httpRuntime targetFramework>`元素_web.config_以確認您使用.NET Framework 目標的版本。

Windows Form 和其他應用程式，請參閱[How to： 以.NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。

使用下列各節以確認您未使用特定的 TLS 或 SSL 版本。

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>如果您的應用程式的目標.NET Framework 4.7 或更新版本

下列章節將示範如何以確認您未使用特定的 TLS 或 SSL 版本。

### <a name="for-http-networking"></a>HTTP 網路功能

<xref:System.Net.ServicePointManager>使用.NET Framework 4.7 和更新版本中，預設值為選擇最佳的安全性通訊協定和版本的作業系統。 若要取得預設 OS 最好的選擇，可能的話，不需要設定的值<xref:System.Net.ServicePointManager.SecurityProtocol>屬性。 否則請將其設定為 <xref:System.Net.SecurityProtocolType.SystemDefault>。

當目標為.NET Framework 4.7 或更新版本的 HTTP 網路時，這篇文章的其餘部分不相關。

### <a name="for-tcp-sockets-networking"></a>網路功能的 TCP 通訊端

<xref:System.Net.Security.SslStream>使用.NET Framework 4.7 和更新版本中，預設值為選擇最佳的安全性通訊協定和版本的作業系統。 若要取得預設 OS 最好的選擇，可能的話，不使用的方法多載<xref:System.Net.Security.SslStream>可接受明確<xref:System.Security.Authentication.SslProtocols>參數。 否則，請傳遞<xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>。 我們建議您不要使用<xref:System.Security.Authentication.SslProtocols.Default>; 將`SslProtocols.Default`強制 SSL 3.0 /TLS 1.0 的使用，並防止 TLS 1.2。

不需要設定的值<xref:System.Net.ServicePointManager.SecurityProtocol>屬性 （適用於 HTTP 網路功能）。

請勿使用方法多載的<xref:System.Net.Security.SslStream>可接受明確<xref:System.Security.Authentication.SslProtocols>（適用於 TCP 網路通訊端） 的參數。 當您重新設定目標應用程式的.NET Framework 4.7 或更新版本時，您將遵循的最佳作法建議。

以.NET Framework 4.7 或更新版本為目標的 TCP 通訊端的網路時，本主題的其餘部分不相關。

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>WCF tcp 傳輸使用的憑證認證的傳輸安全性

WCF 的.NET framework 的其他部分使用相同的網路堆疊。

如果您的目標 4.7.1，WCF 已設定為允許選擇最佳的安全性通訊協定，根據預設，除非明確設定的作業系統：

- 應用程式組態檔中。
- **或**，應用程式的原始程式碼中。

根據預設，.NET Framework 4.7 和更新版本已設定為使用 TLS 1.2，並允許使用 TLS 1.1 或 TLS 1.0 的連線。 設定以允許藉由設定您要使用的繫結選擇最佳的安全性通訊協定 OS WCF <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>。 這可以設定上<xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>。 `SslProtocols.None` 您可以從存取<xref:System.ServiceModel.NetTcpSecurity.Transport>。 `NetTcpSecurity.Transport` 您可以從存取<xref:System.ServiceModel.NetTcpBinding.Security>。

如果您使用自訂繫結：

- 設定以允許藉由設定選擇最佳的安全性通訊協定 OS WCF<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols>使用<xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>。
- **或者**設定以組態路徑使用的通訊協定`system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`。

如果您是**不**使用自訂繫結**和**您正在設定 WCF 繫結使用的組態，設定與組態路徑使用的通訊協定`system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`。

### <a name="for-wcf-message-security-with-certificate-credentials"></a>WCF 訊息安全性使用憑證認證

.NET framework 4.7 和更新的版本，預設會使用指定的通訊協定<xref:System.Net.ServicePointManager.SecurityProtocol>屬性。 當[AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols`設`true`，WCF 會選擇最多 TLS 1.0 的最佳通訊協定。

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>如果您的應用程式的目標.NET Framework 版本早於 4.7

稽核您的程式碼，以確認您未設定特定 TLS 或 SSL 版本使用以下各節：

### <a name="for-net-framework-46---462-and-not-wfc"></a>適用於.NET Framework 4.6-4.6.2 和不 WFC

設定`DontEnableSystemDefaultTlsVersions``AppContext`切換至`false`。 請參閱[設定安全性 AppContext 參數透過](#configuring-security-via-appcontext-switches)。

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>使用.NET Framework 4.6 4.6.2 憑證認證搭配使用 TCP 傳輸安全性的 WCF

您必須安裝最新的 OS 修補程式。 請參閱[安全性更新](#security-updates)。

WCF 架構會自動選擇的最高可用直到 TLS 1.2 通訊協定，除非您明確設定通訊協定版本。 如需詳細資訊，請參閱上一節中[為 WCF TCP 傳輸，傳輸安全性使用憑證認證](#wcf-tcp-cert)。

### <a name="for-net-framework-35---451-and-not-wcf"></a>適用於.NET Framework 3.5-4.5.1 和不 WCF

我們建議您升級至.NET Framework 4.7 或更新版本的應用程式。 如果您無法升級，採取下列步驟。 在某個時間點以後，您的應用程式可能會失敗之前升級至.NET Framework 4.7 或更新版本。

設定[SchUseStrongCrypto](#schusestrongcrypto)和[SystemDefaultTlsVersions](#systemdefaulttlsversions)登錄機碼設為 1。 請參閱[設定在 Windows 登錄的安全性](#configuring-security-via-the-windows-registry)。 .NET Framework 3.5 版支援`SchUseStrongCrypto`僅傳遞明確的 TLS 值會加上旗標。

如果您在.NET Framework 3.5 上執行，您需要安裝，讓您的程式可以指定 TLS 1.2 的熱修補程式：

| [KB3154518](https://support.microsoft.com/kb/3154518) | 在 Windows 7 SP1 和 Server 2008 R2 SP1 上.NET Framework 3.5.1 中包含的可靠性彙總套件 HR-1605-TLS 系統預設版本的支援 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | 可靠性彙總套件 HR-1605-TLS 系統預設版本包含在 Windows Server 2012 上為.NET Framework 3.5 的支援 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | 可靠性彙總套件 HR 1605-TLS 系統預設版本的支援包含在 Windows 8.1 和 Windows Server 2012 R2 上為.NET Framework 3.5 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | .NET Framework 4.5.2 和 4.5.1 Windows 上的 1605 Hotfix 彙總 3154521 |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>使用.NET Framework 3.5 4.5.2 憑證認證搭配使用 TCP 傳輸安全性的 WCF

這些版本的 WCF framework 是硬式編碼為使用 SSL 3.0 和 TLS 1.0 的值。 無法變更這些值。 您必須更新，並將目標重定為.NET Framework 4.6 或更新版本使用 TLS 1.1 和 1.2。

## <a name="if-your-app-targets-net-framework-35"></a>如果您的應用程式的目標.NET Framework 3.5

如果您必須明確設定安全性通訊協定，而非讓.NET framework 或 OS 挑選的安全性通訊協定，將`SecurityProtocolTypeExtensions`和`SslProtocolsExtension`列舉您的程式碼。 `SecurityProtocolTypeExtensions` 和`SslProtocolsExtension`臨界值包括`Tls12`， `Tls11`，而`SystemDefault`值。 請參閱[TLS 系統預設版本包含在 Windows 8.1 和 Windows Server 2012 R2 上的.NET Framework 3.5 的支援](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework)。

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>設定安全性透過 AppContext 參數 （適用於.NET Framework 4.6 或更新版本）

[AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)本節中所述的參數，能夠如果您的應用程式的目標或在.NET Framework 4.6 或更新版本上的執行。 根據預設，或藉由明確地設定它們，參數應`false`的話。 如果您想要設定安全性透過一或兩個參數，然後不指定安全性通訊協定值在您的程式碼;因此，這樣做就會覆寫，搭配參數。

參數在您進行 HTTP 網路是否有相同的效果 (<xref:System.Net.ServicePointManager>) 或 TCP 通訊端的網路功能 (<xref:System.Net.Security.SslStream>)。

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

值為`false`如`Switch.System.Net.DontEnableSchUseStrongCrypto`會導致應用程式以使用強式密碼編譯。 值為`false`如`DontEnableSchUseStrongCrypto`使用更安全的網路通訊協定 （TLS 1.2、 TLS 1.1 和 TLS 1.0），並封鎖不安全的通訊協定。 如需詳細資訊，請參閱[SCH_USE_STRONG_CRYPTO 旗標](#the-schusestrongcrypto-flag)。 值為`true`停用強式密碼編譯應用程式。

如果您的應用程式的目標.NET Framework 4.6 或更新版本，這個參數預設值為`false`。 這是安全的預設值，我們建議。 如果您的應用程式會在.NET Framework 4.6 上執行，但目標為舊版，交換器會預設為`true`。 在此情況下，您應該明確地將它設定為`false`。

`DontEnableSchUseStrongCrypto` 應該只有值為`true`如果您要連接到舊版的服務不支援強式密碼編譯，因此無法升級。

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

值為`false`如`Switch.System.Net.DontEnableSystemDefaultTlsVersions`會導致您的應用程式讓作業系統選擇的通訊協定。 值為`true`會導致您的應用程式使用.NET Framework 所挑選的通訊協定。

如果您的應用程式的目標.NET Framework 4.7 或更新版本，這個參數預設值為`false`。 這是建議的安全預設值。 如果您的應用程式在.NET Framework 4.7 或更新版本中上, 執行，但目標為舊版，交換器會預設為`true`。 在此情況下，您應該明確地將它設定為`false`。

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

值為`false`如`Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols`會導致應用程式使用中定義之值`ServicePointManager.SecurityProtocols`對訊息安全性使用憑證認證。 值為`true`使用可用的直到 TLS1.0 最高的通訊協定

針對以.NET Framework 4.7 和更新版本為目標的應用程式，這個值預設為`false`。 對於目標為.NET Framework 4.6.2 應用程式和更早版本，這個值預設為`true`。

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

值為`false`如`Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions`設定要允許作業系統選擇的通訊協定的預設組態。 值為`true`最高可用的直到 TLS1.2 的通訊協定設定預設值。

對於目標為.NET Framework 4.7.1 及更新版本的應用程式，這個值預設為`false`。 對於目標為 4.7 及更早版本的.NET Framework 應用程式，這個值預設為`true`。

如需 TLS 通訊協定的詳細資訊，請參閱[風險降低： TLS 通訊協定](../migration-guide/mitigation-tls-protocols.md)。 如需有關`AppContext`參數，請參閱[ `<AppContextSwitchOverrides> Element` ](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

## <a name="configuring-security-via-the-windows-registry"></a>設定 Windows 登錄的安全性

如果要設定一個或兩個`AppContext`參數都不是選項，您可以控制您的應用程式會使用這一節所述的 Windows 登錄機碼的安全性通訊協定。 您可能無法使用一或兩`AppContext`切換，如果您的應用程式為目標的.NET Framework 版本早於 4.6，或您無法編輯組態檔。 如果您想要設定登錄安全性，然後不指定安全性通訊協定值在您的程式碼;因此，這樣做就會覆寫登錄。

登錄機碼名稱如下的對應名稱`AppContext`但不含切換`DontEnable`加在名稱前面。 例如，`AppContext`切換`DontEnableSchUseStrongCrypto`稱為登錄機碼[SchUseStrongCrypto](#schusestrongcrypto)。

這些金鑰為適用於所有.NET Framework 版本，它沒有最新的安全性修補程式。 請參閱[安全性更新](#security-updates)。

所有登錄機碼如下所述的在您進行 HTTP 網路是否有相同的效果 (<xref:System.Net.ServicePointManager>) 或 TCP 通訊端的網路功能 (<xref:System.Net.Security.SslStream>)。

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto`登錄機碼的類型為 DWORD 值。 值為 1 會使應用程式以使用強式密碼編譯。 強式密碼編譯使用更安全的網路通訊協定 （TLS 1.2、 TLS 1.1 和 TLS 1.0），並封鎖不安全的通訊協定。 值為 0 會停用強式密碼編譯。 如需詳細資訊，請參閱[SCH_USE_STRONG_CRYPTO 旗標](#the-schusestrongcrypto-flag)。

如果您的應用程式的目標.NET Framework 4.6 或更新版本，這個索引鍵會預設為 1 的值。 這是建議的安全預設值。 如果您的應用程式會在.NET Framework 4.6 上執行，但目標為舊版，索引鍵預設值為 0。 在此情況下，您應該明確設定其值為 1 中。

此機碼應該只能有值為 0，如果您要連接到舊版的服務不支援強式密碼編譯，因此無法升級。

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions`登錄機碼的類型為 DWORD 值。 值為 1 會使您的應用程式讓作業系統選擇的通訊協定。 值為 0 會導致您的應用程式使用.NET Framework 所挑選的通訊協定。

`<VERSION>` 必須是 v4.0.30319 （適用於.NET Framework 4 和更新版本） 或 v2.0.50727 （適用於.NET Framework 3.5)。

如果您的應用程式的目標.NET Framework 4.7 或更新版本，這個索引鍵會預設為 1 的值。 這是建議的安全預設值。 如果您的應用程式在.NET Framework 4.7 或更新版本中上, 執行，但目標為舊版，索引鍵會預設為 0。 在此情況下，您應該明確設定其值為 1 中。

如需詳細資訊，請參閱[更新 Windows 10 版本 1511 的累積和 Windows Server 2016 Technical Preview 4: 2016 年 10，](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016)。

以.NET framework 3.5.1 的詳細資訊，請參閱[支援 TLS 系統預設版本包含在 Windows 7 SP1 和 Server 2008 R2 SP1 上的.NET Framework 3.5.1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework)。

下列_。REG_檔案的登錄機碼和與其變數設定為其最安全的值：

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

您可以使用登錄的用戶端和/或伺服器應用程式會交涉的通訊協定更細微的控制。 您的應用程式的網路功能會透過安全通道 (這是另一個名稱為[安全通道](https://msdn.microsoft.com/library/windows/desktop/aa380123)。 藉由設定`Schannel`，您可以設定您的應用程式行為。

開頭`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols`登錄機碼。 該機碼下您可以建立子機碼集中`SSL 2.0`， `SSL 3.0`， `TLS 1.0`， `TLS 1.1`，和`TLS 1.2`。 在每個這些子機碼中，您可以建立子機碼`Client`及/或`Server`。 在下`Client`和`Server`，您可以建立 DWORD 值`DisabledByDefault`（0 或 1） 和`Enabled`（0 或 0xFFFFFFFF）。

## <a name="the-schusestrongcrypto-flag"></a>SCH_USE_STRONG_CRYPTO 旗標

啟用時 (根據預設，由`AppContext`切換，或 Windows 登錄)，.NET Framework 會使用`SCH_USE_STRONG_CRYPTO`旗標，當您的應用程式要求 TLS 安全性通訊協定。 `SCH_USE_STRONG_CRYPTO`旗標可以根據預設，啟用與`AppContext`切換，或登錄。 作業系統會傳遞至旗標`Schannel`以指示它停用已知的弱式密碼編譯演算法，加密套件和可能否則啟用更佳的互通性的 TLS/SSL 通訊協定版本。 如需詳細資訊，請參閱:

- [安全通道](https://msdn.microsoft.com/library/windows/desktop/aa380123)
- [SCHANNEL_CRED 結構](https://msdn.microsoft.com/library/windows/desktop/aa379810)

`SCH_USE_STRONG_CRYPTO`旗標也會傳遞至`Schannel`當您明確地使用`Tls`(TLS 1.0) `Tls11`，或`Tls12`列舉值的<xref:System.Net.SecurityProtocolType>或<xref:System.Security.Authentication.SslProtocols>。

## <a name="security-updates"></a>安全性更新

這篇文章中的最佳作法取決於正在安裝新的安全性更新。 這些更新包括能夠使用進階的.NET Framework 4.7 和更新版本的功能。 新的安全性更新是很重要，如果您的應用程式是.NET Framework 4.7 和更新版本上執行 （即使其目標為舊版）。

若要更新以便選擇的最佳 TLS，才能使用新版作業系統的.NET Framework，您必須至少安裝：

- [品質彙總套件的.NET Framework 2017 年 8 月 Preview](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup)。
- **或者** [.NET Framework 2017 年 9 月安全性和品質彙總套件](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup)。

另請參閱：

- [.NET framework 版本和相依性](../migration-guide/versions-and-dependencies.md)
- [如何： 判斷已安裝哪些.NET Framework 版本](../migration-guide/how-to-determine-which-versions-are-installed.md)。

## <a name="support-for-tls-12"></a>TLS 1.2 支援

交涉的 TLS 1.2、 作業系統和.NET Framework 版本的應用程式兩者需要支援 TLS 1.2。

**若要支援 TLS 1.2 的作業系統需求**

若要啟用或重新啟用支援它們的系統上的 TLS 1.2 和/或 TLS 1.1，請參閱[傳輸層安全性 (TLS) 登錄設定](/windows-server/security/tls/tls-registry-settings)。

| **OS** | **TLS 1.2 支援** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | 支援，而且預設已啟用。 |
| Windows 8.1</br>Windows Server 2012 R2 | 支援，而且預設已啟用。 |
| Windows 8.0</br>Windows Server 2012 | 支援，而且預設已啟用。 |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | 支援，但預設不啟用。 請參閱[傳輸層安全性 (TLS) 登錄設定](/windows-server/security/tls/tls-registry-settings)網頁，如需有關如何啟用 TLS 1.2 的詳細資訊。 |
| Windows Server 2008 | TLS 1.2 和 TLS 1.1 版的支援要求更新。 請參閱[在 Windows Server 2008 SP2 中加入支援 TLS 1.1 和 TLS 1.2 Update](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s)。 |
| Windows Vista | 不支援。 |

如需 TLS/SSL 預設會在每個 Windows 版本上啟用通訊協定的詳細資訊，請參閱[中 TLS/SSL (安全通道 SSP) 的通訊協定](https://msdn.microsoft.com/library/windows/desktop/mt808159)。

**若要支援 TLS 1.2 使用.NET Framework 3.5 的需求**

下表顯示作業系統更新，您需要支援 TLS 1.2 使用.NET Framework 3.5。 我們建議您套用所有的作業系統更新。

| **OS** | **最小支援 TLS 1.2 使用.NET Framework 3.5 所需的更新** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | [如需 Windows 10 版本 1511年的累積更新和 Windows Server 2016 Technical Preview 4: 2016 年 10，](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1</br>Windows Server 2012 R2 | [TLS 系統預設版本包含在 Windows 8.1 和 Windows Server 2012 R2 上為.NET Framework 3.5 的支援](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0</br>Windows Server 2012 | [TLS 系統預設版本包含在 Windows Server 2012 上為.NET Framework 3.5 的支援](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | [對 TLS 系統預設版本包含在.NET Framework 3.5.1，在 Windows 7 SP1 和 Server 2008 R2 SP1 上支援](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [TLS 系統預設版本包含在.NET Framework 2.0 SP2，Windows Vista SP2 和 Server 2008 SP2 的支援](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | 不支援 |

## <a name="azure-cloud-services"></a>Azure 雲端服務

如果您使用[Azure 雲端服務](https://azure.microsoft.com/services/cloud-services/)Web 和背景工作角色，以主控和執行您的應用程式，您需要支援 TLS 1.2 列入考量的一些考量。

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>.NET framework 4.7 不預設會安裝在 Azure 客體作業系統

安裝最新的 Azure 客體 OS 系列 5 版本 (Windows Server 2016) 的最新版本是 4.6.2。 若要查看每個 Azure 客體作業系統上安裝.NET framework 的版本，請參閱[Azure 客體作業系統版本與 SDK 相容性比較表](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix)。

如果您的應用程式為目標並不適用於 Azure 客體作業系統版本的.NET Framework 版本，您需要自行安裝。 請參閱[對 Azure 雲端服務角色安裝.NET](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet)。 Framework 安裝需要重新啟動，如果服務角色可能會也重新啟動之前進入就緒狀態。

### <a name="azure-guest-os-registry-settings"></a>Azure 客體 OS 登錄設定

Azure 客體作業系統的映像[Azure 雲端服務](https://azure.microsoft.com/services/cloud-services/)已經有`SchUseStrongCrypto`登錄機碼設為 1 的值。 如需詳細資訊，請參閱[SchUseStrongCrypto](#schusestrongcrypto)。

設定[SystemDefaultTlsVersions](#systemdefaulttlsversions)登錄機碼設為 1。 請參閱[設定在 Windows 登錄的安全性](#configuring-security-via-the-windows-registry)。
