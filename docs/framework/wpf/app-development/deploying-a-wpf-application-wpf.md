---
title: 部署 WPF 應用程式 (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 2d3a72dad6a4e139288bf3c1fa9f4cde5124586f
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796760"
---
# <a name="deploying-a-wpf-application-wpf"></a>部署 WPF 應用程式 (WPF)
建立 Windows Presentation Foundation (WPF) 應用程式之後, 就必須部署它們。 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]而 .NET Framework 則包括數種部署技術。 用來部署 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的部署技術會視應用程式類型而定。 本主題提供每項部署技術的簡短概觀，並說明這些技術如何配合每種 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式類型的部署需求來使用。  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>部署技術  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]而 .NET Framework 包括數種部署技術, 包括:  
  
- XCopy 部署。  
  
- [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 部署。  
  
- ClickOnce 佈署。  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>XCopy 部署  
 XCopy 部署是指使用 XCopy 命令列程式，將檔案從一個位置複製到另一個位置。 XCopy 部署適用於下列情況：  
  
- 應用程式是獨立的。 不需要更新用戶端即可執行。  
  
- 應用程式檔案必須從一個位置移至另一個位置，例如從組建位置 (本機磁碟、[!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] 檔案共用等) 移至發行位置 (網站、[!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] 檔案共用等)。  
  
- 應用程式不需要介面整合 ([開始] 功能表捷徑、桌面圖示等)。  
  
 雖然 XCopy 適用於簡單的部署案例，但當需要更複雜的部署功能時卻會受到限制。 特別是，使用 XCopy 通常需要另外建立、執行和維護指令碼，才能穩固地管理部署。 此外，XCopy 不支援版本設定、解除安裝或復原。  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Windows Installer  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 可讓應用程式封裝成獨立的可執行檔，以便輕鬆地散發到用戶端並執行。 此外，[!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 會隨 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 一起安裝，並可與桌面、[開始] 功能表和 [程式集] 控制台整合。  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 可簡化應用程式的安裝和解除安裝作業，但未提供相關功能，無法透過版本設定來確保安裝的應用程式是最新的。  
  
 如需 Windows Installer 的詳細資訊, 請參閱[Windows Installer 部署](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)。
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce 部署  
 ClickOnce 為非 Web 應用程式啟用 Web 樣式應用程式部署。 應用程式會先發行至網頁伺服器或檔案伺服器，再從中部署。 雖然 ClickOnce 不支援已安裝應用程式的完整用戶端[!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]功能範圍, 但它支援包含下列的子集:  
  
- 與 [開始] 功能表和 [程式集] 控制台整合。  
  
- 版本設定、復原和解除安裝。  
  
- 一律會從部署位置啟動應用程式的線上安裝模式。  
  
- 在發行新版本時自動更新。  
  
- 註冊副檔名。  
  
 如需 ClickOnce 的詳細資訊, 請參閱[Clickonce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)。  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>部署 WPF 應用程式  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的部署選項會視應用程式類型而定。 從部署觀點來看，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 有三個重要的應用程式類型：  
  
- 獨立應用程式。  
  
- 全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 應用程式。  
  
- [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>部署獨立應用程式  
 使用 ClickOnce 或[!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]部署獨立應用程式。 無論使用哪種方式，獨立應用程式都需要完全信任才能執行。 對於使用 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 部署的獨立應用程式，會自動授與完全信任。 使用 ClickOnce 部署的獨立應用程式不會自動授與完全信任。 相反地, ClickOnce 會在安裝獨立應用程式之前, 顯示使用者必須接受的安全性警告對話方塊。 如果接受，則會安裝獨立應用程式並授與完全信任。 如果不接受，則不會安裝獨立應用程式。  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>部署全標記 XAML 應用程式  
 僅限[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記的頁面通常會發行至網頁伺服器 (例如 HTML 網頁), 並可使用[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]加以查看。 全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面會在部分信任的安全性沙箱內執行，其限制是由網際網路區域權限集合所定義。 這會提供對等的安全性沙箱給 HTML Web 應用程式。  
  
 如需 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式之安全性的詳細資訊，請參閱[安全性](../security-wpf.md)。  
  
 全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面可以使用 XCopy 或 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 安裝到本機檔案系統。 您可以使用[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]或 Windows Explorer 來查看這些頁面。  
  
 如需 XAML 的詳細資訊，請參閱 [XAML 概觀 (WPF)](../advanced/xaml-overview-wpf.md)。  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>部署 XAML 瀏覽器應用程式  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 是必須部署下列三個檔案的已編譯應用程式：  
  
- *ApplicationName*:可執行檔元件應用程式檔。  
  
- *ApplicationName*xbap:部署資訊清單。  
  
- *ApplicationName*. 資訊清單:應用程式資訊清單。  
  
> [!NOTE]
>  如需部署和應用程式資訊清單的詳細資訊，請參閱[建置 WPF 應用程式](building-a-wpf-application-wpf.md)。  
  
 這些檔案會在建置 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 時產生。 如需詳細資訊，請參閱[如何：建立新的 WPF 瀏覽器應用](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))程式專案。 如同全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面，[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 通常也會發行至網頁伺服器，並使用 [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] 進行檢視。  
  
 您可以使用任何部署技術將 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 部署到用戶端。 不過, 建議使用 ClickOnce, 因為它提供下列功能:  
  
1. 在發行新版本時自動更新。  
  
2. 提高權限，讓 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 可在完全信任的情況下執行。  
  
 根據預設，ClickOnce 會發行副檔名為 .deploy 的應用程式檔案。 這可能會造成問題，但可予以停用。 如需詳細資訊，請參閱 [ClickOnce 部署中的伺服器和用戶端組態問題](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)。  
  
 如需部署 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 的詳細資訊，請參閱 [WPF XAML 瀏覽器應用程式概觀](wpf-xaml-browser-applications-overview.md)。  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>安裝.NET Framework  
 若要執行[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式, 必須在用戶端上安裝 Microsoft .NET Framework。 [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]當瀏覽器裝載的應用程式被查看[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]時, 會自動偵測用戶端是否以 .NET Framework 安裝。 如果未安裝 .NET Framework, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]會提示使用者安裝它。  
  
 若要偵測是否已安裝 .NET Framework, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]包含一個啟動載入器應用程式, 它會[!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)]註冊為具有下列副檔名之內容檔案的回溯處理常式: .xaml、.xps、xbap 和應用程式。 如果您流覽至這些檔案類型, 而且用戶端上未安裝 .NET Framework, 啟動載入器應用程式會要求安裝它的許可權。 如果未提供許可權, 就不會安裝 .NET Framework 或應用程式。  
  
 如果授與許可權, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]會使用 Microsoft 背景智慧型傳送服務 (BITS) 下載並安裝 .NET Framework。 成功安裝 .NET Framework 之後, 原先要求的檔案會在新的瀏覽器視窗中開啟。  
  
 已[!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)] [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)]安裝或更新版本的、和用戶端上會提供 .NET Framework 自動偵測功能。 [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)]  
  
 如需詳細資訊，請參閱[部署 .NET Framework 和應用程式](../../deployment/index.md)。  
  
## <a name="see-also"></a>另請參閱

- [建置 WPF 應用程式](building-a-wpf-application-wpf.md)
- [Security](../security-wpf.md)
