---
title: 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML files [WPF], sandbox behavior
- browser-hosted application security [WPF]
- application security [WPF]
- navigation security [WPF]
- loose XAML files [WPF], sandbox behavior
- WPF security [WPF]
- WebBrowser control [WPF], security
- feature controls [WPF], security
- XBAP security [WPF]
- Internet Explorer security settings [WPF]
ms.assetid: ee1baea0-3611-4e36-9ad6-fcd5205376fb
ms.openlocfilehash: e0a56dcbf8d151fcb0d4f6271ecba15c0ff955a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174611"
---
# <a name="security-wpf"></a>安全性 (WPF)
<a name="introduction"></a>在開發 Windows 演示文稿基礎 （WPF） 獨立和瀏覽器託管的應用程式時，必須考慮安全模型。 WPF 獨立應用程式以不受限制的許可權（CAS**完全信任**許可權集）執行，無論是使用 Windows 安裝程式 （.msi）、XCopy 還是 ClickOnce 部署。 不支援使用 ClickOnce 部署部分信任的獨立 WPF 應用程式。 但是，完全信任的主機應用程式可以使用 .NET 框架外<xref:System.AppDomain>接程式模型創建部分信任。 有關詳細資訊，請參閱[WPF 載入項概述](./app-development/wpf-add-ins-overview.md)。  
  
 WPF瀏覽器託管的應用程式由 Windows Internet 資源管理器或 Firefox 託管，可以是 XAML 瀏覽器應用程式 （XBAPs） 或鬆散[!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)]文檔 有關詳細資訊，請參閱[WPF XAML 瀏覽器應用程式概述](./app-development/wpf-xaml-browser-applications-overview.md)。  
  
 預設情況下，WPF 瀏覽器託管的應用程式在部分信任安全沙箱中執行，該沙箱僅限於預設的 CAS**Internet**區域許可權集。 這將有效地將 WPF 瀏覽器託管的應用程式與用戶端電腦隔離，就像您希望將典型的 Web 應用程式隔離一樣。 XBAP 可以根據部署 URL 的安全性區域以及用戶端的安全性組態來提高權限，而最高為「完全信任」。 如需詳細資訊，請參閱 [WPF 部分信任安全性](wpf-partial-trust-security.md)。  
  
 本主題討論 Windows 演示文稿基礎 （WPF） 獨立和瀏覽器託管應用程式的安全模型。  
  
 本主題包含下列幾節：  
  
- [安全巡覽](#SafeTopLevelNavigation)  
  
- [Web 瀏覽軟體安全性設定](#InternetExplorerSecuritySettings)  
  
- [WebBrowser 控制項和功能控制項](#webbrowser_control_and_feature_controls)  
  
- [停用部分信任用戶端應用程式的 APTCA 組件](#APTCA)  
  
- [鬆散 XAML 檔案的沙箱行為](#LooseContentSandboxing)  
  
- [用於開發可提高安全性的 WPF 應用程式的資源](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>
## <a name="safe-navigation"></a>安全巡覽  
 對於 XBAP，WPF 區分兩種類型的導航：應用程式和瀏覽器。  
  
 「應用程式巡覽」** 是瀏覽器所裝載之應用程式的內容項目間的巡覽。 「瀏覽器巡覽」** 是變更瀏覽器本身的內容和位置 URL 的巡覽。 應用程式導航（通常為 XAML）和瀏覽器導航（通常 HTML）之間的關係如下圖所示：
  
 ![應用程式導航和瀏覽器導航之間的關係。](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 XBAP 導航到的內容類型主要取決於是否使用應用程式導航或瀏覽器導航。  
  
<a name="Application_Navigation_Security"></a>
### <a name="application-navigation-security"></a>應用程式巡覽安全性  
 如果可以使用包 URI 進行標識，則應用程式導航被視為安全，該 URI 支援四種類型的內容：  
  
|內容類型|描述|URI 範例|  
|------------------|-----------------|-----------------|  
|資源|添加到具有組建類型的**資源**的專案的檔。|`pack://application:,,,/MyResourceFile.xaml`|  
|內容|添加到具有生成**類型內容**的專案的檔。|`pack://application:,,,/MyContentFile.xaml`|  
|Site of origin|添加到組建類型的 **"無"** 的專案的檔。|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|應用程式程式碼|具有已編譯程式碼後置的 XAML 資源。<br /><br /> -或-<br /><br /> 添加到具有組建類型的**Page**的專案的 XAML 檔。|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
> 有關應用程式資料檔案和打包 URI 的詳細資訊，請參閱[WPF 應用程式資源、內容和資料檔案](./app-development/wpf-application-resource-content-and-data-files.md)。  
  
 使用者或透過程式設計方式可以巡覽到這些內容類型的檔案︰  
  
- **使用者巡覽**。 使用者通過按一下<xref:System.Windows.Documents.Hyperlink>元素進行導航。  
  
- **程式設計巡覽**。 應用程式導航時不涉及使用者，例如，通過設置<xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>屬性。  
  
<a name="Browser_Navigation_Security"></a>
### <a name="browser-navigation-security"></a>瀏覽器巡覽安全性  
 只有在下列情況下，才會將瀏覽器巡覽視為安全：  
  
- **使用者巡覽**。 使用者通過按一下<xref:System.Windows.Documents.Hyperlink>主<xref:System.Windows.Navigation.NavigationWindow>元素中的元素而不是嵌套<xref:System.Windows.Controls.Frame>中進行導航。  
  
- **區域**。 所要巡覽的內容位在網際網路或近端內部網路。  
  
- **通訊協定**。 **file**正在使用的協定是**http****HTTP、HTTPs、** 檔或**mailto**。  
  
 如果 XBAP 嘗試以不符合這些條件的方式導航到內容，則引發 。 <xref:System.Security.SecurityException>  
  
<a name="InternetExplorerSecuritySettings"></a>
## <a name="web-browsing-software-security-settings"></a>Web 瀏覽軟體安全性設定  
 電腦上的安全性設定決定授與任何 Web 瀏覽軟體的存取權。 Web 流覽套裝軟體括使用[WinINet](/windows/win32/wininet/portal)或[UrlMon](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) API 的任何應用程式或元件，包括 Internet 資源管理器和演示Host.exe。  
  
 Internet Explorer 提供了一種機制，通過該機制可以配置允許由 Internet Explorer 執行的功能，包括以下內容：  
  
- .NET 框架相依元件  
  
- ActiveX 控制項和外掛程式  
  
- 下載  
  
- 指令碼  
  
- 使用者驗證  
  
 以這種方式保護的功能集合按區域配置，用於**Internet、Intranet、****受信任的網站**和**受限網站**區域。 **Internet** 下列步驟描述如何設定安全性設定：  
  
1. 開啟 [控制台]****。  
  
2. 點擊**網路和互聯網**，然後按一下**互聯網選項**。  
  
     [網際網路選項] 對話方塊隨即出現。  
  
3. 在 **"安全"** 選項卡上，選擇要為其配置安全設置的區域。  
  
4. 按一下 **"自訂級別"** 按鈕。  
  
     將顯示 **"安全設置"** 對話方塊，您可以配置所選區域的安全設置。  
  
     ![顯示"安全設置"對話方塊的螢幕截圖。](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> 您也可以從 Internet Explorer 到達 [網際網路選項] 對話方塊。 按一下**工具**，然後按一下**互聯網選項**。  
  
 從 Windows Internet 資源管理器 7 開始，包括針對 .NET 框架的以下安全設置：  
  
- **鬆散 XAML**。 控制 Internet 資源管理器是否可以導航到和[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]鬆散的檔。 ([啟用]、[停用] 和 [提示] 選項)。  
  
- **XAML 瀏覽器應用程式**。 控制 Internet 資源管理器是否可以導航到並運行 XBAP。 ([啟用]、[停用] 和 [提示] 選項)。  
  
 預設情況下，這些設置都為**Internet、****本地 Intranet**和**受信任的網站**區域啟用，並且為**受限網站**區域禁用。  
  
<a name="Security_Settings_for_IE6_and_Below"></a>
### <a name="security-related-wpf-registry-settings"></a>安全性相關 WPF 登錄設定  
 除了透過 [網際網路選項] 取得的安全性設定之外，還提供下列登錄值可選擇性地封鎖許多有安全性顧慮的 WPF 功能。 值會定義在下列機碼下方︰  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 下表列出可設定的值。  
  
|值名稱|值類型|數值資料|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|1 表示不允許；0 表示允許。|  
|LooseXamlDisallow|REG_DWORD|1 表示不允許；0 表示允許。|  
|WebBrowserDisallow|REG_DWORD|1 表示不允許；0 表示允許。|  
|MediaAudioDisallow|REG_DWORD|1 表示不允許；0 表示允許。|  
|MediaImageDisallow|REG_DWORD|1 表示不允許；0 表示允許。|  
|MediaVideoDisallow|REG_DWORD|1 表示不允許；0 表示允許。|  
|ScriptInteropDisallow|REG_DWORD|1 表示不允許；0 表示允許。|  
  
<a name="webbrowser_control_and_feature_controls"></a>
## <a name="webbrowser-control-and-feature-controls"></a>WebBrowser 控制項和功能控制項  
 WPF<xref:System.Windows.Controls.WebBrowser>控制項可用於託管 Web 內容。 WPF<xref:System.Windows.Controls.WebBrowser>控制項包裝基礎 Web 瀏覽器 ActiveX 控制項。 當您使用 WPF<xref:System.Windows.Controls.WebBrowser>控制項託管不受信任的 Web 內容時，WPF 為保護應用程式提供了一些支援。 但是，某些安全功能必須由使用控制項<xref:System.Windows.Controls.WebBrowser>的應用程式直接應用。 有關 Web 瀏覽器 ActiveX 控制項的詳細資訊，請參閱[Web 瀏覽器控制項概述和教程](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85))。  
  
> [!NOTE]
> 本節也適用于控制項，<xref:System.Windows.Controls.Frame>因為它使用<xref:System.Windows.Controls.WebBrowser>導航到 HTML 內容。  
  
 如果 WPF<xref:System.Windows.Controls.WebBrowser>控制項用於託管不受信任的 Web 內容，則應用程式應使用部分信任<xref:System.AppDomain>來説明將應用程式代碼與潛在的惡意 HTML 腳本代碼隔離。 如果應用程式使用<xref:System.Windows.Controls.WebBrowser.InvokeScript%2A>方法和<xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A>屬性與託管腳本交互，則尤其如此。 有關詳細資訊，請參閱[WPF 載入項概述](./app-development/wpf-add-ins-overview.md)。  
  
 如果應用程式使用 WPF<xref:System.Windows.Controls.WebBrowser>控制項，則提高安全性和緩解攻擊的另一種方法是啟用 Internet Explorer 功能控制項。 功能控制項是 Internet 資源管理器的補充，允許管理員和開發人員配置 Internet Explorer 的功能以及承載 WebBrowser ActiveX 控制項的應用程式，WPF<xref:System.Windows.Controls.WebBrowser>控制項將該控制項包裝。 可以使用[CoInternetSetFeature 啟用功能](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85))或更改註冊表中的值來配置功能控制項。 有關功能控制項的詳細資訊，請參閱[功能控制和](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85)) [Internet 功能控制項](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85))簡介。  
  
 如果您正在開發使用 WPF 控制項的獨立 WPF<xref:System.Windows.Controls.WebBrowser>應用程式，WPF 會自動為應用程式啟用以下功能控制項。  
  
|功能控制項|  
|---------------------|  
|FEATURE_MIME_HANDLING|  
|FEATURE_MIME_SNIFFING|  
|FEATURE_OBJECT_CACHING|  
|FEATURE_SAFE_BINDTOOBJECT|  
|FEATURE_WINDOW_RESTRICTIONS|  
|FEATURE_ZONE_ELEVATION|  
|FEATURE_RESTRICT_FILEDOWNLOAD|  
|FEATURE_RESTRICT_ACTIVEXINSTALL|  
|FEATURE_ADDON_MANAGEMENT|  
|FEATURE_HTTP_USERNAME_PASSWORD_DISABLE|  
|FEATURE_SECURITYBAND|  
|FEATURE_UNC_SAVEDFILECHECK|  
|FEATURE_VALIDATE_NAVIGATE_URL|  
|FEATURE_DISABLE_TELNET_PROTOCOL|  
|FEATURE_WEBOC_POPUPMANAGEMENT|  
|FEATURE_DISABLE_LEGACY_COMPRESSION|  
|FEATURE_SSLUX|  
  
 因為會無條件地啟用這些功能控制項，所以它們可能會損害完全信任應用程式。 在此情況下，如果特定應用程式和其所裝載的內容沒有安全性風險，則可以停用對應的功能控制項。  
  
 功能控制項由具現化 Web 瀏覽器 ActiveX 物件的過程應用。 因此，如果您要建立的獨立應用程式會巡覽到不受信任的內容，則應該認真考慮啟用其他功能控制項。  
  
> [!NOTE]
> 這項建議根據 MSHTML 和 SHDOCVW 主機安全性的一般建議。 有關詳細資訊，請參閱[MSHTML 主機安全常見問題解答：II 部分 I](https://msrc-blog.microsoft.com/2009/04/02/the-mshtml-host-security-faq-part-i-of-ii/)和[MSHTML 主機安全常見問題解答：II 的第二部分](https://msrc-blog.microsoft.com/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii/)。  
  
 針對可執行檔，請考慮將登錄值設定為 1 來啟用下列功能控制項。  
  
|功能控制項|  
|---------------------|  
|FEATURE_ACTIVEX_REPURPOSEDETECTION|  
|FEATURE_BLOCK_LMZ_IMG|  
|FEATURE_BLOCK_LMZ_OBJECT|  
|FEATURE_BLOCK_LMZ_SCRIPT|  
|FEATURE_RESTRICT_RES_TO_LMZ|  
|FEATURE_RESTRICT_ABOUT_PROTOCOL_IE7|  
|FEATURE_SHOW_APP_PROTOCOL_WARN_DIALOG|  
|FEATURE_LOCALMACHINE_LOCKDOWN|  
|FEATURE_FORCE_ADDR_AND_STATUS|  
|FEATURE_RESTRICTED_ZONE_WHEN_FILE_NOT_FOUND|  
  
 針對可執行檔，請考慮將登錄值設定為 0 來停用下列功能控制項。  
  
|功能控制項|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 如果運行部分信任的 XAML 瀏覽器應用程式 （XBAP），該應用程式在<xref:System.Windows.Controls.WebBrowser>Windows Internet 資源管理器中包含 WPF 控制項，則 WPF 在 Internet 資源管理器進程的位址空間中託管 Web 瀏覽器 ActiveX 控制項。 由於 Web 瀏覽器 ActiveX 控制項託管在 Internet 資源管理器過程中，因此 Internet Explorer 的所有功能控制項也已為 Web 瀏覽器 ActiveX 控制項啟用。  
  
 與一般獨立應用程式相較之下，在 Internet Explorer 中執行的 XBAP 也會取得額外層級的安全性。 這種額外的安全性是因為 Internet 資源管理器（因此是 Web 瀏覽器 ActiveX 控制項）預設在 Windows Vista 和 Windows 7 上以受保護模式運行。 有關受保護模式的詳細資訊，請參閱[在受保護模式下瞭解和工作 Internet 資源管理器](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/)。  
  
> [!NOTE]
> 如果您嘗試運行一個 XBAP，該 XBAP 在 Firefox 中包含<xref:System.Windows.Controls.WebBrowser>WPF<xref:System.Security.SecurityException>控制項，而在 Internet 區域中，將引發 。 這是因為 WPF 安全性原則。  
  
<a name="APTCA"></a>
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>停用部分信任用戶端應用程式的 APTCA 組件  
 當託管程式集安裝到全域組件快取 （GAC） 中時，它們將完全受信任，因為使用者必須提供明確權限才能安裝它們。 因為它們完全受信任，所以只有完全受信任的受管理用戶端應用程式才能使用它們。 要允許部分受信任的應用程式使用它們，必須用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>（APTCA） 標記它們。 只有經過測試可在部分信任中安全執行的組件才應該標記這個屬性。  
  
 但是，APTCA 程式集在安裝到 GAC 後可能會表現出安全性漏洞。 發現安全性缺陷之後，組件發行者可以產生安全性更新來修正現有安裝上的問題，以及防止在發現問題之後可能進行的安裝。 雖然解除安裝組件可能會中斷其他使用組件的完全信任用戶端應用程式，但是更新的其中一個選項是解除安裝組件。  
  
 WPF 提供了一種機制，通過該機制，無需卸載 APTCA 程式集，即可禁用 APTCA 程式集，以用於部分受信任的 XBAPs。  
  
 若要停用 APTCA 組件，您必須建立特殊登錄機碼︰  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 下列示範範例：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 此機碼會為 APTCA 組件建立一個項目。 您也必須在這個機碼中建立啟用或停用組件的數值。 數值的詳細資料如下︰  
  
- 值名稱 **：APTCA_FLAG**。  
  
- 數值型別 **：REG_DWORD**。  
  
- 值資料 **：1**個要禁用;**0**啟用。  
  
 如果必須停用部分信任用戶端應用程式的組件，您可以撰寫可建立登錄機碼和值的更新。  
  
> [!NOTE]
> Core .NET 框架程式集不會以這種方式禁用它們，因為它們是託管應用程式運行所必需的。 停用 APTCA 組件的支援主要是針對協力廠商應用程式。  
  
<a name="LooseContentSandboxing"></a>
## <a name="sandbox-behavior-for-loose-xaml-files"></a>鬆散 XAML 檔案的沙箱行為  
 鬆散[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]檔是僅標記的 XAML 檔，不依賴于任何代碼備份、事件處理常式或特定于應用程式的程式集。 當鬆散[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]檔直接從瀏覽器導航到時，它們將基於預設 Internet 區域許可權集載入到安全沙箱中。  
  
 但是，當鬆散[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]檔從 或<xref:System.Windows.Navigation.NavigationWindow>在獨立應用程式中導航到時<xref:System.Windows.Controls.Frame>，安全行為會有所不同。  
  
 在這兩種情況下，導航以[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]繼承其主機應用程式許可權的鬆散檔。 但是，從安全形度來看，此行為可能是不可取的，尤其是在由不[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]受信任的實體或未知實體生成的鬆散檔的情況下。 這種類型的內容稱為*外部內容*，<xref:System.Windows.Controls.Frame>並且<xref:System.Windows.Navigation.NavigationWindow>可以配置為在導航到時將其隔離。 通過將**沙箱外部內容**屬性設置為 true 來實現隔離，如 以下示例<xref:System.Windows.Controls.Frame>所示， <xref:System.Windows.Navigation.NavigationWindow>  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 使用此設定，會將外部內容載入與裝載應用程式的程序不同的程序。 此程序僅限於預設網際網路區域權限集，可有效地隔離它與裝載應用程式和用戶端電腦。  
  
> [!NOTE]
> 即使基於 WPF[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]瀏覽器託管基礎結構<xref:System.Windows.Navigation.NavigationWindow>（<xref:System.Windows.Controls.Frame>涉及演示文稿主機進程）實現從 a 或獨立應用程式中對鬆散檔的導航，安全級別比直接在 Windows Vista 和 Windows 7 上的 Internet 資源管理器中載入的內容（這仍通過演示主機）時略低。 這是因為使用 Web 瀏覽器的獨立 WPF 應用程式不會提供 Internet Explorer 的額外受保護模式安全性功能。  
  
<a name="BestPractices"></a>
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>用於開發可提高安全性的 WPF 應用程式的資源  
 以下是一些其他資源，可説明開發 WPF 應用程式，以提高安全性：  
  
|區域|資源|  
|----------|--------------|  
|Managed 程式碼|[Patterns and Practices Security Guidance for Applications](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)) (應用程式的模式和實務安全性指南)|  
|CAS|[代碼訪問安全性](../misc/code-access-security.md)|  
|ClickOnce|[按一下"一次安全和部署"](/visualstudio/deployment/clickonce-security-and-deployment)|  
|WPF|[WPF 部分信任安全性](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>另請參閱

- [WPF 部分信任安全性](wpf-partial-trust-security.md)
- [WPF 安全性策略 – 平台安全性](wpf-security-strategy-platform-security.md)
- [WPF 安全性策略 – 安全性工程](wpf-security-strategy-security-engineering.md)
- [Patterns and Practices Security Guidance for Applications](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)) (應用程式的模式和實務安全性指南)
- [代碼訪問安全性](../misc/code-access-security.md)
- [按一下"一次安全和部署"](/visualstudio/deployment/clickonce-security-and-deployment)
- [XAML 概觀 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
