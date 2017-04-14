---
title: "部署 WPF 應用程式 (WPF) | Microsoft Docs"
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
  - "部署 [WPF], 應用程式"
  - "WPF 應用程式, 部署"
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# 部署 WPF 應用程式 (WPF)
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 應用程式必須於建置完成後就進行部署。  [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 和 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 包含幾種部署技術。  要使用哪項技術來部署 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式則會視應用程式的類型而異。  本主題提供每種部署技術的簡要概觀，說明這些技術如何配合每種 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式類型的部署需求運用。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Deployment_Technologies"></a>   
## 部署技術  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 和 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 內含幾種部署技術，包括：  
  
-   XCopy 部署。  
  
-   [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 部署。  
  
-   [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 部署。  
  
<a name="XCopy_Deployment"></a>   
### XCopy 部署  
 XCopy 部署是指使用 XCopy 命令列程式，將檔案從一個位置複製到另一個位置。  XCopy 部署適用於下列情況：  
  
-   應用程式是獨立的 \(Self\-Contained\)。  不需要更新用戶端即可執行。  
  
-   應用程式檔案必須從一個位置移至另一個位置，例如從建置位置 \(本機磁碟、[!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] 檔案共用等\) 移至發行位置 \(網站、[!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] 檔案共用等\)。  
  
-   應用程式不需要 Shell 整合 \(\[開始\] 功能表捷徑、桌面圖示等\)。  
  
 雖然 XCopy 適用於簡單的部署案例，但當需要更複雜的部署功能時卻會受到限制。  特別是，使用 XCopy 通常需要另外建立、執行和維護指令碼，才能穩固地管理部署。  此外，XCopy 不支援版本控制、解除安裝或復原。  
  
<a name="Windows_Installer"></a>   
### Windows Installer  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 可讓應用程式封裝成獨立的可執行檔，方便散佈到用戶端並執行。  此外，[!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 會隨 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 一起安裝，可與桌面、\[開始\] 功能表和 \[程式集\] 控制台整合。  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 可簡化應用程式的安裝和解除安裝作業，但並未提供版本控制功能，無法確保安裝的應用程式是最新的。  
  
 如需 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 的詳細資訊，請參閱 [Windows Installer Deployment](http://msdn.microsoft.com/zh-tw/121be21b-b916-43e2-8f10-8b080516d2a0)。  
  
<a name="ClickOnce_Deployment"></a>   
### ClickOnce 部署  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 可為非 Web 應用程式啟用 Web 式應用程式的部署。應用程式會先發行至 Web 或檔案伺服器，再從該處進行部署。  雖然 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 不如 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 安裝的應用程式支援完整的用戶端功能，但它還是支援其中的一部分功能，包括：  
  
-   與 \[開始\] 功能表和 \[程式集\] 控制台整合。  
  
-   版本控制、復原和解除安裝。  
  
-   線上安裝模式，這可永遠從部署位置啟動應用程式。  
  
-   在有新版本發行時自動更新。  
  
-   註冊副檔名。  
  
 如需 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 的詳細資訊，請參閱 [ClickOnce 安全性和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)。  
  
<a name="Deploying_WPF_Applications"></a>   
## 部署 WPF 應用程式  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的部署選項會根據應用程式的類型而定。  從部署觀點來看，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 有三種主要應用程式類型：  
  
-   獨立應用程式。  
  
-   全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 應用程式。  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### 部署獨立應用程式  
 獨立應用程式是使用 [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 或 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 部署。  無論使用哪種方式，獨立應用程式都需要完全信任才能執行。  完全信任會自動授與使用 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 部署的獨立應用程式。  使用 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 部署的獨立應用程式不會自動獲得授與完整信任。  相反地，[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 會顯示安全性警告對話方塊，使用者必須接受才能安裝獨立應用程式。  如果接受，會安裝獨立應用程式並授與完全信任。  如果不接受，則不會安裝獨立應用程式。  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### 部署全標記 XAML 應用程式  
 全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面通常會發行至網頁伺服器，就如同 [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] 網頁一樣，並且可以使用 [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] 進行檢視。  全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面會在部分信任的安全性沙箱中執行，其限制是由網際網路區域權限集合所定義。  這就提供了相當於 [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] Web 應用程式所使用的安全性沙箱。  
  
 如需 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式之安全性的詳細資訊，請參閱 [安全性](../../../../docs/framework/wpf/security-wpf.md)。  
  
 全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面可使用 XCopy 或 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 安裝到本機檔案系統。  這些頁面可使用 [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] 或 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 檔案總管檢視。  
  
 如需 XAML 的詳細資訊，請參閱 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### 部署 XAML 瀏覽器應用程式  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 是已編譯的應用程式，需要下列三個檔案進行部署：  
  
-   \<*應用程式名稱*\>.exe：可執行的組件應用程式檔案。  
  
-   \<*應用程式名稱*\>.xbap：部署資訊清單。  
  
-   \<*應用程式名稱*\>.exe.manifest：應用程式資訊清單。  
  
> [!NOTE]
>  如需部署和應用程式資訊清單的詳細資訊，請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)。  
  
 這些檔案會在建置 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 時產生。  如需詳細資訊，請參閱 [HOW TO：建立新的 WPF 瀏覽器應用程式專案](http://msdn.microsoft.com/zh-tw/72ef4d90-e163-42a1-8df0-ea7ccfd1901f)。  如同全標記的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面，[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 通常也會發行至網頁伺服器，並使用 [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] 檢視。  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 可使用任何部署技術來部署至用戶端。  但是，建議使用 [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]，因為它可以提供下列功能：  
  
1.  在有新版本發行時自動更新。  
  
2.  提高權限，讓 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 在受到完全信任的狀態下執行。  
  
 根據預設，ClickOnce 會發行副檔名為 .deploy 的應用程式檔案。  這可能會有問題，但可予以停用。  如需詳細資訊，請參閱 [ClickOnce 部署中的伺服器和用戶端組態問題](../Topic/Server%20and%20Client%20Configuration%20Issues%20in%20ClickOnce%20Deployments.md)。  
  
 如需部署 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 的詳細資訊，請參閱 [WPF XAML 瀏覽器應用程式概觀](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)。  
  
<a name="Installing__NET_Framework_3_0"></a>   
## 安裝 .NET Framework  
 若要執行 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式，在用戶端上必須安裝 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]。  在檢視 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 瀏覽器裝載應用程式時，[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] 會自動偵測用戶端是否已安裝 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]。  若未安裝 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]，[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] 會提示使用者加以安裝。  
  
 為偵測是否已安裝了 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]，[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] 會包含啟動載入器應用程式，此應用程式註冊為具有下列副檔名的內容檔案的後援 [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] 處理常式：.xaml、.xps、.xbap 和 .application。  如果您巡覽至這些檔案類型，而用戶端上未安裝 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]，則啟動載入器應用程式會要求取得安裝它的使用權限。  如果沒有提供使用權限，就不會安裝 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]，也不會安裝應用程式。  
  
 如果授與使用權限，[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] 會使用 [!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)] 下載並安裝 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]。  在順利安裝 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 之後，原先要求的檔案會在新瀏覽器視窗中開啟。  
  
 已安裝 [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] 或更新版本的 [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]、[!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)] 和 [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] 用戶端上都會提供 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 自動偵測功能。  
  
 如需詳細資訊，請參閱[部署 .NET Framework 和應用程式](../../../../docs/framework/deployment/net-framework-and-applications.md)。  
  
## 請參閱  
 [建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [安全性](../../../../docs/framework/wpf/security-wpf.md)