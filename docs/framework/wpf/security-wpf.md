---
title: 安全性 (WPF)
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
ms.openlocfilehash: ec026fd9273e99c88ec2e30cf46c3147419ace94
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629806"
---
# <a name="security-wpf"></a>安全性 (WPF)
<a name="introduction"></a>開發 Windows Presentation Foundation (WPF) 獨立和瀏覽器裝載的應用程式時, 您必須考慮安全性模型。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]獨立應用程式會以不受限制的許可權 (CAS**FullTrust**許可權集合) 執行, 不論是使用 Windows Installer (.msi)、XCopy 或 ClickOnce 部署。 不支援使用 ClickOnce 部署部分信任的獨立 WPF 應用程式。 不過, 完全信任的主應用程式可以使用 .NET Framework 增益集模型<xref:System.AppDomain>來建立部分信任。 如需詳細資訊, 請參閱[WPF 增益集總覽](./app-development/wpf-add-ins-overview.md)。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]瀏覽器裝載的應用程式是[!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)]由或 Firefox 主控, 而且可以[!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)]是或[!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)]鬆散檔以取得詳細資訊, 請參閱[WPF XAML 瀏覽器應用程式總覽](./app-development/wpf-xaml-browser-applications-overview.md)。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]瀏覽器裝載的應用程式預設會在部分信任安全性沙箱中執行, 其限制為預設的 CAS**網際網路**區域許可權集合。 這可有效[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]地將瀏覽器裝載的應用程式與用戶端電腦隔離, 使其與一般 Web 應用程式隔離的方式相同。 XBAP 可以根據部署 URL 的安全性區域以及用戶端的安全性組態來提高權限，而最高為「完全信任」。 如需詳細資訊，請參閱 [WPF 部分信任安全性](wpf-partial-trust-security.md)。  
  
 本主題討論 Windows Presentation Foundation (WPF) 獨立和瀏覽器裝載應用程式的安全性模型。  
  
 本主題包含下列幾節：  
  
- [安全巡覽](#SafeTopLevelNavigation)  
  
- [Web 瀏覽軟體安全性設定](#InternetExplorerSecuritySettings)  
  
- [WebBrowser 控制項和功能控制項](#webbrowser_control_and_feature_controls)  
  
- [停用部分信任用戶端應用程式的 APTCA 組件](#APTCA)  
  
- [鬆散 XAML 檔案的沙箱行為](#LooseContentSandboxing)  
  
- [用於開發可提高安全性的 WPF 應用程式的資源](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>安全巡覽  
 針對[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] ,[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]區分兩種類型的流覽: 應用程式和瀏覽器。  
  
 「應用程式巡覽」  是瀏覽器所裝載之應用程式的內容項目間的巡覽。 「瀏覽器巡覽」  是變更瀏覽器本身的內容和位置 URL 的巡覽。 下圖顯示應用程式導覽 (通常是 XAML) 和瀏覽器導覽 (通常是 HTML) 之間的關聯性:
  
 ![應用程式導覽與瀏覽器導覽之間的關聯性。](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 視為[!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)]要流覽至安全的內容類型主要取決於是否使用應用程式導覽或瀏覽器導覽。  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>應用程式巡覽安全性  
 如果可以使用支援四種內容類型的套件[!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)]識別應用程式, 則會將它視為安全:  
  
|內容類型|描述|URI 範例|  
|------------------|-----------------|-----------------|  
|資源|新增至組建類型為**資源**之專案的檔案。|`pack://application:,,,/MyResourceFile.xaml`|  
|內容|新增至專案的檔案, 其組建類型為**Content**。|`pack://application:,,,/MyContentFile.xaml`|  
|Site of origin|新增至組建類型為**None**之專案的檔案。|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|應用程式程式碼|具有已編譯程式碼後置的 XAML 資源。<br /><br /> -或-<br /><br /> 加入至組建類型為**Page**之專案的 XAML 檔案。|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
>  如需有關應用程式資料檔案和套件[!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)]的詳細資訊, 請參閱[WPF 應用程式資源、內容和資料檔案](./app-development/wpf-application-resource-content-and-data-files.md)。  
  
 使用者或透過程式設計方式可以巡覽到這些內容類型的檔案︰  
  
- **使用者巡覽**。 使用者可以按一下<xref:System.Windows.Documents.Hyperlink>專案來流覽。  
  
- **程式設計巡覽**。 應用程式流覽時不會涉及使用者, 例如, 藉由設定<xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>屬性。  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>瀏覽器巡覽安全性  
 只有在下列情況下，才會將瀏覽器巡覽視為安全：  
  
- **使用者巡覽**。 使用者藉由按一下<xref:System.Windows.Documents.Hyperlink>主要<xref:System.Windows.Navigation.NavigationWindow>內的專案, 而不是在嵌套<xref:System.Windows.Controls.Frame>的中, 來進行流覽。  
  
- **區域**。 所要巡覽的內容位在網際網路或近端內部網路。  
  
- **通訊協定**. 所使用的通訊協定為**HTTP**、 **HTTPs**、 **file**或**mailto**。  
  
 如果嘗試以不符合這些條件的方式流覽至內容<xref:System.Security.SecurityException> , 就會擲回。 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)]  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Web 瀏覽軟體安全性設定  
 電腦上的安全性設定決定授與任何 Web 瀏覽軟體的存取權。 Web 流覽套裝軟體含任何使用[WinINet](https://go.microsoft.com/fwlink/?LinkId=179379)或[urlmon.dll](https://go.microsoft.com/fwlink/?LinkId=179383) Api (包括 Internet Explorer 和 presentationhost.exe) 的應用程式或元件。  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)]提供一種機制, 讓您可以設定允許或從[!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)]執行的功能, 包括下列各項:  
  
- .NET Framework 相依元件  
  
- ActiveX 控制項和外掛程式  
  
- 下載  
  
- 正在處理指令碼  
  
- 使用者驗證  
  
 以這種方式受到保護的功能集合, 是針對網際網路、**內部** **網路**、**信任的網站**和**受限制的網站**區域, 以每個區域為基礎進行設定。 下列步驟描述如何設定安全性設定：  
  
1. 開啟 [**控制台**]。  
  
2. 按一下 [**網路和網際網路**], 然後按一下 [**網際網路選項**]。  
  
     [網際網路選項] 對話方塊隨即出現。  
  
3. 在 [**安全性**] 索引標籤上, 選取要設定安全性設定的區域。  
  
4. 按一下 [**自訂層級**] 按鈕。  
  
     [**安全性設定**] 對話方塊隨即出現, 您可以設定所選區域的安全性設定。  
  
     ![顯示 [安全性設定] 對話方塊的螢幕擷取畫面。](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
>  您也可以從 Internet Explorer 到達 [網際網路選項] 對話方塊。 按一下 [**工具**], 然後按一下 [**網際網路選項**]。  
  
 從開始[!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], 會包含專門用於 .NET Framework 的下列安全性設定:  
  
- **鬆散 XAML**。 控制是否[!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)]可以導覽至檔案或[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]鬆散檔案。 ([啟用]、[停用] 和 [提示] 選項)。  
  
- **XAML 瀏覽器應用程式**。 控制是否[!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)]可以導覽和執行[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]。 ([啟用]、[停用] 和 [提示] 選項)。  
  
 根據預設, 這些設定都會針對 [**網際網路**]、[近端**內部**網路] 和 [**信任**的網站] 區域啟用, 並針對 [**限制的網站**] 區域停用。  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>安全性相關 WPF 登錄設定  
 除了透過 [網際網路選項] 取得的安全性設定之外，還提供下列登錄值可選擇性地封鎖許多有安全性顧慮的 WPF 功能。 值會定義在下列機碼下方︰  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 下表列出可設定的值。  
  
|數值名稱|實值類型|數值資料|  
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
 WPF <xref:System.Windows.Controls.WebBrowser>控制項可以用來裝載 Web 內容。 WPF <xref:System.Windows.Controls.WebBrowser>控制項會包裝基礎 WebBrowser ActiveX 控制項。 當您使用 wpf <xref:System.Windows.Controls.WebBrowser>控制項來裝載不受信任的 Web 內容時, wpf 會提供一些保護應用程式的支援。 不過, 某些安全性功能必須由使用<xref:System.Windows.Controls.WebBrowser>控制項的應用程式直接套用。 如需 WebBrowser ActiveX 控制項的詳細資訊, 請參閱[Webbrowser 控制項總覽和教學](https://go.microsoft.com/fwlink/?LinkId=179388)課程。  
  
> [!NOTE]
>  本節也適用<xref:System.Windows.Controls.Frame>于控制項, 因為它會<xref:System.Windows.Controls.WebBrowser>使用來流覽至 HTML 內容。  
  
 如果 WPF <xref:System.Windows.Controls.WebBrowser>控制項是用來裝載不受信任的 Web 內容, 您的應用程式應該使用<xref:System.AppDomain>部分信任, 協助將您的應用程式程式碼與可能惡意的 HTML 腳本隔離。 特別是當您的應用程式使用<xref:System.Windows.Controls.WebBrowser.InvokeScript%2A>方法<xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A>和屬性與裝載的腳本互動時, 更是如此。 如需詳細資訊, 請參閱[WPF 增益集總覽](./app-development/wpf-add-ins-overview.md)。  
  
 如果您的應用程式使用<xref:System.Windows.Controls.WebBrowser> WPF 控制項, 另一個增加安全性和緩和攻擊的方法, 就是啟用 Internet Explorer 功能控制項。 功能控制是 internet explorer 的新增專案, 可讓系統管理員和開發人員設定 internet explorer 的功能, 以及裝載 WebBrowser ActiveX 控制項的應用程式<xref:System.Windows.Controls.WebBrowser> (WPF 控制項會包裝此控制項)。 您可以使用[CoInternetSetFeatureEnabled](https://go.microsoft.com/fwlink/?LinkId=179394)函數或變更登錄中的值, 來設定功能控制項。 如需功能控制項的詳細資訊, 請參閱[功能控制項簡介](https://go.microsoft.com/fwlink/?LinkId=179390)和[網際網路功能控制項](https://go.microsoft.com/fwlink/?LinkId=179392)。  
  
 如果您要開發使用 wpf <xref:System.Windows.Controls.WebBrowser>控制項的獨立 WPF 應用程式, WPF 會自動為您的應用程式啟用下列功能控制項。  
  
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
  
 功能控制項是由具現化 WebBrowser ActiveX 物件的進程所套用。 因此，如果您要建立的獨立應用程式會巡覽到不受信任的內容，則應該認真考慮啟用其他功能控制項。  
  
> [!NOTE]
>  這項建議根據 MSHTML 和 SHDOCVW 主機安全性的一般建議。 如需詳細資訊, [請參閱 MSHTML 主機安全性常見問題:第 I](https://go.microsoft.com/fwlink/?LinkId=179396)部分和[MSHTML 主機安全性常見問題:II](https://go.microsoft.com/fwlink/?LinkId=179415)的第二部分。  
  
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
  
 如果您在中[!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)]執行包含 WPF <xref:System.Windows.Controls.WebBrowser>控制項的部分信任, WPF 會在 Internet Explorer 進程的位址空間中裝載 WebBrowser ActiveX 控制項。 由於 webbrowser activex 控制項裝載于[!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)]進程中, 因此 Internet Explorer 的所有功能控制項也會針對 WebBrowser ActiveX 控制項啟用。  
  
 與一般獨立應用程式相較之下，在 Internet Explorer 中執行的 XBAP 也會取得額外層級的安全性。 這項額外的安全性是因為 Internet Explorer (因此 WebBrowser ActiveX 控制項) 預設會在和[!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] [!INCLUDE[win7](../../../includes/win7-md.md)]上以受保護模式執行。 如需受保護模式的詳細資訊, 請參閱[瞭解及使用受保護模式的 Internet Explorer](https://go.microsoft.com/fwlink/?LinkId=179393)。  
  
> [!NOTE]
>  如果您嘗試在 Firefox 中執行包含 WPF <xref:System.Windows.Controls.WebBrowser>控制項的 XBAP, 而在網際網路區域中<xref:System.Security.SecurityException> , 則會擲回。 這是因為 WPF 安全性原則。  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>停用部分信任用戶端應用程式的 APTCA 組件  
 當 managed 元件安裝到全域組件快取 (GAC) 時, 它們會變成完全信任, 因為使用者必須提供明確的許可權才能進行安裝。 因為它們完全受信任，所以只有完全受信任的受管理用戶端應用程式才能使用它們。 若要允許部分信任的應用程式使用它們, 則必須以<xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 標記。 只有經過測試可在部分信任中安全執行的組件才應該標記這個屬性。  
  
 不過, APTCA 元件可能會在安裝到 GAC 後出現安全性缺陷。 發現安全性缺陷之後，組件發行者可以產生安全性更新來修正現有安裝上的問題，以及防止在發現問題之後可能進行的安裝。 雖然解除安裝組件可能會中斷其他使用組件的完全信任用戶端應用程式，但是更新的其中一個選項是解除安裝組件。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]提供一種機制, 可讓 aptca 元件停用部分信任[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] , 而不需要卸載 aptca 元件。  
  
 若要停用 APTCA 組件，您必須建立特殊登錄機碼︰  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 下列示範範例：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 此機碼會為 APTCA 組件建立一個項目。 您也必須在這個機碼中建立啟用或停用組件的數值。 數值的詳細資料如下︰  
  
- 值名稱:**APTCA_FLAG**。  
  
- 數值型別:**REG_DWORD**。  
  
- 數值資料:**1**表示停用;**0**表示啟用。  
  
 如果必須停用部分信任用戶端應用程式的組件，您可以撰寫可建立登錄機碼和值的更新。  
  
> [!NOTE]
>  核心 .NET Framework 元件不會受到以這種方式停用的影響, 因為受控應用程式必須執行它們。 停用 APTCA 組件的支援主要是針對協力廠商應用程式。  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>鬆散 XAML 檔案的沙箱行為  
 鬆散[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]檔案是僅限標記的 XAML 檔案, 不相依于任何程式碼後置、事件處理常式或應用程式特定的元件。 直接從[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]瀏覽器導覽到鬆散檔案時, 會根據預設的網際網路區域許可權集合, 將它們載入至安全性沙箱。  
  
 不過, 當從或[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Frame>獨立應用程式中的<xref:System.Windows.Navigation.NavigationWindow>鬆散檔案流覽至時, 安全性行為會有所不同。  
  
 在這兩種情況下[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] , 流覽至的鬆散檔案會繼承其主應用程式的許可權。 不過, 此行為可能會因為安全性的觀點而不需要, 特別是[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]如果鬆散檔案是由不受信任或未知的實體所產生。 這種類型的內容稱為*外部內容*, 而且和<xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow>都可以設定為在流覽至時加以隔離。 藉由將**SandboxExternalContent**屬性設為 true 來達成隔離, 如下列<xref:System.Windows.Controls.Frame>和<xref:System.Windows.Navigation.NavigationWindow>的範例所示:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 使用此設定，會將外部內容載入與裝載應用程式的程序不同的程序。 此程序僅限於預設網際網路區域權限集，可有效地隔離它與裝載應用程式和用戶端電腦。  
  
> [!NOTE]
>  即使從[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Navigation.NavigationWindow>或在獨立應用程式中流覽到鬆散檔案,也是根據WPF瀏覽器裝載基礎結構(涉及presentationhost.exe程式)來執行,安全性層級是<xref:System.Windows.Controls.Frame>將內容直接載入到 Internet Explorer 的[!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)]和[!INCLUDE[win7](../../../includes/win7-md.md)] (仍然是透過 presentationhost.exe) 時稍微小於。 這是因為使用 Web 瀏覽器的獨立 WPF 應用程式不會提供 Internet Explorer 的額外受保護模式安全性功能。  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>用於開發可提高安全性的 WPF 應用程式的資源  
 以下是一些額外的資源, 可協助[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]開發提升安全性的應用程式:  
  
|區域|資源|  
|----------|--------------|  
|Managed 程式碼|[Patterns and Practices Security Guidance for Applications](https://go.microsoft.com/fwlink/?LinkId=117426) (應用程式的模式和實務安全性指南)|  
|CAS|[程式碼存取安全性](../misc/code-access-security.md)|  
|ClickOnce|[ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[WPF 部分信任安全性](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>另請參閱

- [WPF 部分信任安全性](wpf-partial-trust-security.md)
- [WPF 安全性策略 – 平台安全性](wpf-security-strategy-platform-security.md)
- [WPF 安全性策略 – 安全性工程](wpf-security-strategy-security-engineering.md)
- [Patterns and Practices Security Guidance for Applications](https://go.microsoft.com/fwlink/?LinkId=117426) (應用程式的模式和實務安全性指南)
- [程式碼存取安全性](../misc/code-access-security.md)
- [ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)
- [XAML 概觀 (WPF)](./advanced/xaml-overview-wpf.md)
