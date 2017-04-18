---
title: "安全性 (WPF) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式安全性 [WPF]"
  - "瀏覽器裝載應用程式安全性 [WPF]"
  - "功能控制項 [WPF], 安全性"
  - "Internet Explorer 安全性設定 [WPF]"
  - "鬆散的 XAML 檔案 [WPF], 沙箱行為"
  - "巡覽安全性 [WPF]"
  - "WebBrowser 控制項 [WPF], 安全性"
  - "WPF 安全性"
  - "XAML 檔案 [WPF], 沙箱行為"
  - "XBAP 安全性 [WPF]"
ms.assetid: ee1baea0-3611-4e36-9ad6-fcd5205376fb
caps.latest.revision: 38
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# 安全性 (WPF)
<a name="introduction"></a> 開發 [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] 獨立應用程式與瀏覽器裝載的應用程式時，您必須考慮安全性模型。[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 獨立應用程式會以不受限的權限 \([!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **FullTrust** 權限集合\) 執行，不論部署方法是使用 Windows Installer \(.msi\)、XCopy 或 [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]。  不支援以 ClickOnce 部署部分信任的獨立 WPF 應用程式。  不過，完全信任的應用程式可以使用 .NET Framework 增益集模型，建立部分信任的 <xref:System.AppDomain>。  如需詳細資訊，請參閱 [WPF 增益集概觀](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 瀏覽器裝載的應用程式是由 [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)] 或 Firefox 裝載，而且可以是 [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] 或鬆散的[!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] 文件。如需詳細資訊，請參閱 [WPF XAML 瀏覽器應用程式概觀](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 瀏覽器裝載的應用程式會在部分信任安全性沙箱內執行，根據預設，會限制為預設 [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **Internet** 區域權限集合。  這樣會將 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 瀏覽器裝載的應用程式有效地與用戶端電腦隔離，方法就像隔離平常的 Web 應用程式一樣。  XBAP 可以提高使用權限，最高可提高至完全信任，視部署 URL 的安全性區域以及用戶端的安全性組態而定。  如需詳細資訊，請參閱 [WPF 部分信任安全性](../../../docs/framework/wpf/wpf-partial-trust-security.md)。  
  
 本主題會討論 [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] 獨立和瀏覽器裝載的應用程式的安全性模型。  
  
 此主題包括下列章節：  
  
-   [安全巡覽](#SafeTopLevelNavigation)  
  
-   [Web 瀏覽軟體安全性設定](#InternetExplorerSecuritySettings)  
  
-   [WebBrowser 控制項和功能控制項](#webbrowser_control_and_feature_controls)  
  
-   [針對部分信任的用戶端應用程式停用 APTCA 組件](#APTCA)  
  
-   [鬆散 XAML 檔案的沙箱行為](#LooseContentSandboxing)  
  
-   [開發具更佳安全性之 WPF 應用程式的相關資源](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## 安全巡覽  
 對於 [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]，[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 會區分兩種類型的巡覽：應用程式和瀏覽器。  
  
 「*應用程式巡覽*」是指在瀏覽器所裝載之應用程式中的內容項目之間進行的巡覽。  「*瀏覽器巡覽*」是指會變更瀏覽器本身之內容和位置 URL 的巡覽。  下圖顯示應用程式巡覽 \(通常為 XAML\) 和瀏覽器巡覽 \(通常為 HTML\) 之間的關係：  
  
 ![巡覽圖表](../../../docs/framework/wpf/media/safetoplevelnavigationfigure.png "SafeTopLevelNavigationFigure")  
  
 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] 可以安全巡覽的內容類型，主要取決於使用的是應用程式巡覽還是瀏覽器巡覽。  
  
<a name="Application_Navigation_Security"></a>   
### 應用程式巡覽安全性  
 應用程式巡覽如果可以用封包 [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)] 來識別，即視為安全的，可以支援四種類型的內容：  
  
|內容類型|描述|URI 範例|  
|----------|--------|------------|  
|資源|以組建類型 \[**資源**\] 加入至專案的檔案。|`pack://application:,,,/MyResourceFile.xaml`|  
|內容|以組建類型 \[**內容**\] 加入至專案的檔案。|`pack://application:,,,/MyContentFile.xaml`|  
|來源網站|以組建類型 \[**無**\] 加入至專案的檔案。|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|應用程式程式碼|具有已編譯之後置程式碼的 XAML 資源。<br /><br /> \-或\-<br /><br /> 以組建類型 \[**頁面**\] 加入至專案的 XAML 檔案。|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
>  如需應用程式資料檔案和封包 [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)] 的詳細資訊，請參閱 [WPF 應用程式資源、內容和資料檔案](../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)。  
  
 這些內容類型的檔案可以由使用者巡覽或以程式設計的方式來巡覽：  
  
-   **使用者巡覽**：  使用者藉由按一下 <xref:System.Windows.Documents.Hyperlink> 項目進行巡覽。  
  
-   **程式設計巡覽**：  與使用者無關的應用程式巡覽，例如藉由設定 <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=fullName> 屬性。  
  
<a name="Browser_Navigation_Security"></a>   
### 瀏覽器巡覽安全性  
 只有在下列情況下，瀏覽器巡覽才會視為安全的：  
  
-   **使用者巡覽**：  使用者藉由按一下主要 <xref:System.Windows.Navigation.NavigationWindow> 內 \(而不是巢狀 <xref:System.Windows.Controls.Frame> 中\) 的 <xref:System.Windows.Documents.Hyperlink> 項目進行巡覽。  
  
-   **區域**：  要巡覽的內容位於網際網路或近端內部網路。  
  
-   **通訊協定**：  使用的通訊協定是 **http**、**https**、**file** 或 **mailto**。  
  
 如果 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] 以不符合上述情況的方式來巡覽內容，就會擲回 <xref:System.Security.SecurityException>。  
  
<a name="InternetExplorerSecuritySettings"></a>   
## Web 瀏覽軟體安全性設定  
 您電腦上的安全性設定會決定所有 Web 瀏覽軟體具有的存取權。  Web 瀏覽軟體包含任何使用 [WinINet](http://go.microsoft.com/fwlink/?LinkId=179379) 或 [UrlMon](http://go.microsoft.com/fwlink/?LinkId=179383) API 的應用程式或元件 \(包括 Internet Explorer 和 PresentationHost.exe 在內\)。  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] 提供一個機制，可供您設定 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] 可以執行的功能，包括：  
  
-   依賴 [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] 的元件  
  
-   ActiveX 控制項和外掛程式  
  
-   下載  
  
-   指令碼  
  
-   使用者驗證  
  
 可以用這樣的方式保護的功能集合是以個別區域 \(例如 \[**網際網路**\]、\[**內部網路**\]、\[**信任的網站**\] 及 \[**限制的網站**\] 區域\) 為單位來設定。  下列步驟將說明如何設定您的安全性設定：  
  
1.  開啟 \[**控制台**\]。  
  
2.  按一下 \[**網路和網際網路**\]，再按一下 \[**網際網路選項**\]。  
  
     \[網際網路選項\] 對話方塊隨即出現。  
  
3.  在 \[**安全性**\] 索引標籤上，選取要設定安全性設定的區域。  
  
4.  按一下 \[**自訂層級**\] 按鈕。  
  
     \[**安全性設定**\] 對話方塊隨即出現，您可以設定選取之區域的安全性設定。  
  
     ![安全性設定對話方塊](../../../docs/framework/wpf/media/wpfsecurityfigure1.PNG "WPFSecurityFigure1")  
  
> [!NOTE]
>  您也可以從 Internet Explorer 開啟 \[網際網路選項\] 對話方塊。  按一下 \[**工具**\]，再按一下 \[**網際網路選項**\]。  
  
 從 [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)] 開始，會包含下列特別針對 [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] 的安全性設定：  
  
-   **鬆散的 XAML**：  控制 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] 是否可以巡覽至鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 檔案並且加以使用   \(\[啟用\]、\[停用\] 和 \[提示\] 選項\)。  
  
-   **XAML 瀏覽器應用程式**：  控制 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] 是否可以巡覽至 [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] 檔案並且執行   \(\[啟用\]、\[停用\] 和 \[提示\] 選項\)。  
  
 根據預設，這些設定在 \[**網際網路**\]、\[**近端區域網路**\] 及 \[**信任的網站**\] 區域中都是啟用的，在 \[**限制的網站**\] 區域中則是停用的。  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### 安全性相關 WPF 登錄設定  
 除了可透過 \[網際網路選項\] 設定的安全性設定以外，下列登錄值可用於選擇性封鎖一些可能有安全疑慮的 WPF 功能。  這些值會定義於下列機碼之下：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 下表列出可以設定的值。  
  
|數值名稱|實值型別|數值資料|  
|----------|----------|----------|  
|XBAPDisallow|REG\_DWORD|1 表示不允許，0 表示允許。|  
|LooseXamlDisallow|REG\_DWORD|1 表示不允許，0 表示允許。|  
|WebBrowserDisallow|REG\_DWORD|1 表示不允許，0 表示允許。|  
|MediaAudioDisallow|REG\_DWORD|1 表示不允許，0 表示允許。|  
|MediaImageDisallow|REG\_DWORD|1 表示不允許，0 表示允許。|  
|MediaVideoDisallow|REG\_DWORD|1 表示不允許，0 表示允許。|  
|ScriptInteropDisallow|REG\_DWORD|1 表示不允許，0 表示允許。|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## WebBrowser 控制項和功能控制項  
 WPF <xref:System.Windows.Controls.WebBrowser> 控制項可用於裝載 Web 內容。  WPF <xref:System.Windows.Controls.WebBrowser> 控制項會包裝基礎的 WebBrowser ActiveX 控制項。  當您使用 WPF <xref:System.Windows.Controls.WebBrowser> 控制項來裝載未受信任的 Web 內容時，WPF 會提供一些有助於保護應用程式安全的支援。  不過，有些安全性功能必須由應用程式使用 <xref:System.Windows.Controls.WebBrowser> 控制項直接套用。  如需 WebBrowser ActiveX 控制項的詳細資訊，請參閱 [WebBrowser 控制項概觀和教學課程](http://go.microsoft.com/fwlink/?LinkId=179388) \(英文\)。  
  
> [!NOTE]
>  本節也適用於 <xref:System.Windows.Controls.Frame> 控制項，因為該控制項使用 <xref:System.Windows.Controls.WebBrowser> 來巡覽 HTML 內容。  
  
 如果會使用 WPF <xref:System.Windows.Controls.WebBrowser> 控制項來裝載未受信任的 Web 內容，則您的應用程式應該使用部分信任的 <xref:System.AppDomain> 來協助將您的應用程式程式碼與潛在的惡意 HTML 指令碼隔離。  如果應用程式會使用 <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> 方法和 <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> 屬性來與裝載的指令碼互動，就更需要這麼做。  如需詳細資訊，請參閱 [WPF 增益集概觀](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)。  
  
 如果應用程式會使用 WPF <xref:System.Windows.Controls.WebBrowser> 控制項，另一個可提高安全性並緩和攻擊影響的方法，就是啟用 Internet Explorer 功能控制項。  功能控制項是 Internet Explorer 的附加項目，可供系統管理員與開發人員設定 Internet Explorer 以及裝載 WebBrowser ActiveX 控制項 \(由 WPF <xref:System.Windows.Controls.WebBrowser> 控制項所包裝\) 之應用程式的功能。  設定功能控制項的方式有使用 [CoInternetSetFeatureEnabled](http://go.microsoft.com/fwlink/?LinkId=179394) 函式或是變更登錄中的值。  如需功能控制項的詳細資訊，請參閱[功能控制項簡介](http://go.microsoft.com/fwlink/?LinkId=179390) \(英文\) 和[網際網路功能控制項](http://go.microsoft.com/fwlink/?LinkId=179392) \(英文\)。  
  
 如果您所開發的獨立 WPF 應用程式會使用 WPF <xref:System.Windows.Controls.WebBrowser> 控制項，則 WPF 會替您的應用程式自動啟用下列功能控制項。  
  
|功能控制項|  
|-----------|  
|FEATURE\_MIME\_HANDLING|  
|FEATURE\_MIME\_SNIFFING|  
|FEATURE\_OBJECT\_CACHING|  
|FEATURE\_SAFE\_BINDTOOBJECT|  
|FEATURE\_WINDOW\_RESTRICTIONS|  
|FEATURE\_ZONE\_ELEVATION|  
|FEATURE\_RESTRICT\_FILEDOWNLOAD|  
|FEATURE\_RESTRICT\_ACTIVEXINSTALL|  
|FEATURE\_ADDON\_MANAGEMENT|  
|FEATURE\_HTTP\_USERNAME\_PASSWORD\_DISABLE|  
|FEATURE\_SECURITYBAND|  
|FEATURE\_UNC\_SAVEDFILECHECK|  
|FEATURE\_VALIDATE\_NAVIGATE\_URL|  
|FEATURE\_DISABLE\_TELNET\_PROTOCOL|  
|FEATURE\_WEBOC\_POPUPMANAGEMENT|  
|FEATURE\_DISABLE\_LEGACY\_COMPRESSION|  
|FEATURE\_SSLUX|  
  
 因為這些功能控制項會無條件啟用，所以完全信任的應用程式可能會因此受到損害。  在這種情況下，如果停用對應的功能控制項對於該特定應用程式和其裝載的內容並不會有安全性風險，則可放心停用。  
  
 功能控制項是在執行個體化 WebBrowser ActiveX 物件的過程中受到套用。  因此，如果您要建立可以巡覽未受信任內容的獨立應用程式，則應該認真考慮啟用其他功能控制項。  
  
> [!NOTE]
>  這項建議是以針對 MSHTML 和 SHDOCVW 主機安全性的一般建議事項為根據。  如需詳細資訊，請參閱 [MSHTML 主機安全性常見問題集：上篇](http://go.microsoft.com/fwlink/?LinkId=179396) \(英文\) 和 [MSHTML 主機安全性常見問題集：下篇](http://go.microsoft.com/fwlink/?LinkId=179415) \(英文\)。  
  
 對於您的可執行檔，請考慮將下列功能控制項的登錄值設為 1 加以啟用。  
  
|功能控制項|  
|-----------|  
|FEATURE\_ACTIVEX\_REPURPOSEDETECTION|  
|FEATURE\_BLOCK\_LMZ\_IMG|  
|FEATURE\_BLOCK\_LMZ\_OBJECT|  
|FEATURE\_BLOCK\_LMZ\_SCRIPT|  
|FEATURE\_RESTRICT\_RES\_TO\_LMZ|  
|FEATURE\_RESTRICT\_ABOUT\_PROTOCOL\_IE7|  
|FEATURE\_SHOW\_APP\_PROTOCOL\_WARN\_DIALOG|  
|FEATURE\_LOCALMACHINE\_LOCKDOWN|  
|FEATURE\_FORCE\_ADDR\_AND\_STATUS|  
|FEATURE\_RESTRICTED\_ZONE\_WHEN\_FILE\_NOT\_FOUND|  
  
 對於您的可執行檔，請考慮將下列功能控制項的登錄值設為 0 加以停用。  
  
|功能控制項|  
|-----------|  
|FEATURE\_ENABLE\_SCRIPT\_PASTE\_URLACTION\_IF\_PROMPT|  
  
 如果您執行的部分信任 [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] 會在 [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)] 中加上 WPF <xref:System.Windows.Controls.WebBrowser> 控制項，則 WPF 會在 Internet Explorer 處理序的位址空間中裝載 WebBrowser ActiveX 控制項。  因為 WebBrowser ActiveX 控制項是裝載於 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] 處理序中，所以 Internet Explorer 的所有功能控制項也都會對 WebBrowser ActiveX 控制項啟用。  
  
 相較於一般獨立應用程式，在 Internet Explorer 中執行的 XBAP 可獲得額外一層安全性。  其之所以能夠有此額外的安全性，是因為在 [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] 和 [!INCLUDE[win7](../../../includes/win7-md.md)] 上，預設會以受保護模式執行 Internet Explorer \(因此及於 WebBrowser ActiveX 控制項\)。  如需受保護模式的詳細資訊，請參閱[了解及在受保護模式 Internet Explorer 中作業](http://go.microsoft.com/fwlink/?LinkId=179393) \(英文\)。  
  
> [!NOTE]
>  如果您嘗試執行的 XBAP 會在 Firefox 中加上 WPF <xref:System.Windows.Controls.WebBrowser> 控制項，則在位於 \[網際網路\] 區域時會擲回 <xref:System.Security.SecurityException>。  這是由於 WPF 安全性原則的緣故。  
  
<a name="APTCA"></a>   
## 針對部分信任的用戶端應用程式停用 APTCA 組件  
 當 Managed 組件安裝至[!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)] 時，會變成完全受信任的，因為使用者必須明確提供安裝它們的權限。  因為它們是完全受信任的，所以只有完全受信任的 Managed 用戶端應用程式可以使用它們。  若要讓部分信任的應用程式可以使用它們，它們必須有 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) 標示。  但是只有在部分信任中經過測試可以安全執行的組件，才應標示這個屬性 \(Attribute\)。  
  
 不過，APTCA 組件可能會在安裝至 [!INCLUDE[TLA2#tla_gac](../../../includes/tla2sharptla-gac-md.md)] 之後才呈現出安全性缺陷。  一旦發現安全性缺陷，組件發行者可以產生安全性更新以修正現有安裝上的問題，並且在發現問題後防範可能造成缺陷的安裝。  更新的解決方法之一是解除安裝組件，不過這樣可能會使得使用該組件的其他完全受信任的用戶端應用程式中斷。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 提供一個機制，可針對部分信任的 [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] 停用 APTCA 組件，而不需解除安裝 APTCA 組件。  
  
 若要停用 APTCA 組件，您必須建立特殊的登錄機碼：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 以下顯示範例：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 這個機碼會建立 APTCA 組件的項目。  您還必須在這個機碼中建立啟用或停用該組件的值。  以下是此值的詳細資料：  
  
-   數值名稱：**APTCA\_FLAG**。  
  
-   數值型別：**REG\_DWORD**。  
  
-   數值資料：**1** 表示停用，**0** 表示啟用。  
  
 如果需要針對部分信任的用戶端應用程式停用某個組件，您可以撰寫更新來建立登錄機碼和值。  
  
> [!NOTE]
>  核心 [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] 組件不受這種停用方式的影響，因為它們是 Managed 應用程式執行所需的項目。  這項停用 APTCA 組件的支援，主要是以協力廠商應用程式為目標。  
  
<a name="LooseContentSandboxing"></a>   
## 鬆散 XAML 檔案的沙箱行為  
 鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 檔案是全標記的 XAML 檔案，這些檔案並不相依於任何後置程式碼、事件處理常式或應用程式專用組件。  直接從瀏覽器巡覽至鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 檔案時，這些檔案會根據預設的 \[網際網路\] 區域權限集合載入至安全性沙箱中。  
  
 不過，當從獨立應用程式中的 <xref:System.Windows.Navigation.NavigationWindow> 或 <xref:System.Windows.Controls.Frame> 直接巡覽至鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 檔案時，展現的安全性行為則會不同。  
  
 在這兩種情況下，巡覽到的鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 檔案會繼承其主應用程式的權限。  但是，從安全性角度來看這可能不是好現象，特別是當鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 檔案是由不信任或未知的實體產生時。  這種內容稱為「外部內容」，<xref:System.Windows.Controls.Frame> 和 <xref:System.Windows.Navigation.NavigationWindow> 都可以設為在巡覽至這種內容時加以隔離。  隔離可以藉由將 **SandboxExternalContent** 屬性 \(Property\) 設為 true 來達成，如同下列 <xref:System.Windows.Controls.Frame> 和 <xref:System.Windows.Navigation.NavigationWindow> 的範例所示：  
  
 [!code-xml[SecurityOverviewSnippets#FrameMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xml[SecurityOverviewSnippets#NavigationWindowMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 使用這項設定，外部內容載入至的處理序，會與裝載應用程式的處理序不同。  這個處理序只能使用預設的 \[網際網路\] 區域權限集合，而能有效地與主應用程式和用戶端電腦隔離。  
  
> [!NOTE]
>  雖然在獨立應用程式中從 <xref:System.Windows.Navigation.NavigationWindow> 或 <xref:System.Windows.Controls.Frame> 巡覽至鬆散 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 檔案的功能，是以 WPF 瀏覽器裝載基礎結構 \(牽涉到 PresentationHost 處理序\) 為基礎來實作，但是其安全性層級還是會比直接在 [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] 和 [!INCLUDE[win7](../../../includes/win7-md.md)] 的 Internet Explorer 中載入內容 \(仍會透過 PresentationHost\) 稍弱一些。這是因為使用 Web 瀏覽器的獨立 WPF 應用程式並不提供 Internet Explorer 所額外提供的 \[受保護模式\] 安全性功能。  
  
<a name="BestPractices"></a>   
## 開發具更佳安全性之 WPF 應用程式的相關資源  
 以下是一些有助於開發具更佳安全性之 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 應用程式的其他資源：  
  
|區域|資源|  
|--------|--------|  
|Managed 程式碼|[應用程式的模式和做法安全性指引](http://go.microsoft.com/fwlink/?LinkId=117426)|  
|[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]|[程式碼存取安全性](../../../docs/framework/misc/code-access-security.md)|  
|[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]|[ClickOnce 安全性和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[WPF 部分信任安全性](../../../docs/framework/wpf/wpf-partial-trust-security.md)|  
  
## 請參閱  
 [WPF 部分信任安全性](../../../docs/framework/wpf/wpf-partial-trust-security.md)   
 [WPF 安全性策略 – 平台安全性](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)   
 [WPF 安全性策略 – 安全性工程](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)   
 [應用程式的模式和做法安全性指引](http://go.microsoft.com/fwlink/?LinkId=117426)   
 [程式碼存取安全性](../../../docs/framework/misc/code-access-security.md)   
 [ClickOnce 安全性和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)   
 [XAML 概觀 \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)