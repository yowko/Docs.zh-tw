---
title: 部署應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 54d14503a0f65bb50f2dfb14d40af3b47d51589c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186317"
---
# <a name="deploy-a-wpf-application"></a>部署 WPF 應用程式

構建 Windows 演示基礎 （WPF） 應用程式後，需要部署它們。 Windows 和 .NET 框架包括多種部署技術。 用於部署 WPF 應用程式的部署技術取決於應用程式類型。 本主題簡要概述了每種部署技術，以及如何結合每種 WPF 應用程式類型的部署要求使用。

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a>部署技術  
 Windows 和 .NET 框架包括多種部署技術，包括：  
  
- XCopy 部署。  
  
- Windows 安裝程式部署。  
  
- ClickOnce 部署。  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a>XCopy 部署  
 XCopy 部署是指使用 XCopy 命令列程式，將檔案從一個位置複製到另一個位置。 XCopy 部署適用於下列情況：  
  
- 應用程式是獨立的。 不需要更新用戶端即可執行。  
  
- 應用程式檔必須從一個位置移動到另一個位置，例如從生成位置（本地磁片、UNC 檔共用等）移動到發佈位置（網站、UNC 檔共用等）。  
  
- 應用程式不需要介面整合 ([開始] 功能表捷徑、桌面圖示等)。  
  
 雖然 XCopy 適用於簡單的部署案例，但當需要更複雜的部署功能時卻會受到限制。 特別是，使用 XCopy 通常需要另外建立、執行和維護指令碼，才能穩固地管理部署。 此外，XCopy 不支援版本設定、解除安裝或復原。  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a>Windows Installer  
 Windows 安裝程式允許將應用程式打包為可獨立執行檔，以便輕鬆分發到用戶端並運行。 此外，Windows 安裝程式與 Windows 一起安裝，並啟用與桌面、"開始"功能表和程式控制面板的集成。  
  
 Windows 安裝程式簡化了應用程式的安裝和卸載，但它不提供從版本控制的角度來看確保已安裝的應用程式保持最新功能。  
  
 有關 Windows 安裝程式的詳細資訊，請參閱[Windows 安裝程式部署](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)。
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a>ClickOnce 部署  
 ClickOnce 支援針對非 Web 應用程式部署 Web 樣式的應用程式。 應用程式會先發行至網頁伺服器或檔案伺服器，再從中部署。 儘管 ClickOnce 不支援 Windows 安裝程式安裝的應用程式的全部用戶端功能，但它確實支援包含以下內容的子集：  
  
- 與 [開始] 功能表和 [程式集] 控制台整合。  
  
- 版本設定、復原和解除安裝。  
  
- 一律會從部署位置啟動應用程式的線上安裝模式。  
  
- 在發行新版本時自動更新。  
  
- 註冊副檔名。  
  
 有關按一下"一次"的詳細資訊，請參閱[按一下"一次安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)"。  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a>部署 WPF 應用程式  
 WPF 應用程式的部署選項取決於應用程式的類型。 從部署的角度來看，WPF 有三種重要的應用程式類型：  
  
- 獨立應用程式。  
  
- 全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 應用程式。  
  
- XAML 瀏覽器應用程式 （XBAP）。  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a>部署獨立應用程式  
 使用 ClickOnce 或 Windows 安裝程式部署獨立應用程式。 無論使用哪種方式，獨立應用程式都需要完全信任才能執行。 完全信任將自動授予使用 Windows 安裝程式部署的獨立應用程式。 使用 ClickOnce 部署的獨立應用程式不會自動授予完全信任。 相反，ClickOnce 會顯示使用者在安裝獨立應用程式之前必須接受的安全警告對話方塊。 如果接受，則會安裝獨立應用程式並授與完全信任。 如果不接受，則不會安裝獨立應用程式。  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a>部署全標記 XAML 應用程式  
 僅[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記頁面通常發佈到 Web 服務器（如 HTML 頁面），並且可以使用 Internet Explorer 查看。 全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面會在部分信任的安全性沙箱內執行，其限制是由網際網路區域權限集合所定義。 這為基於 HTML 的 Web 應用程式提供了等效的安全沙箱。  
  
 有關 WPF 應用程式安全性的詳細資訊，請參閱[安全](../security-wpf.md)。  
  
 通過使用 XCopy[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]或 Windows 安裝程式，只能將標記頁面安裝到本地檔案系統。 可以使用 Internet 資源管理器或 Windows 資源管理器查看這些頁面。  
  
 如需 XAML 的詳細資訊，請參閱 [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)。  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a>部署 XAML 瀏覽器應用程式  
 XBAP 是需要部署以下三個檔的編譯應用程式：  
  
- *應用程式名稱*.exe：可執行組件應用程式檔案。  
  
- *應用程式名稱*.xbap：部署資訊清單。  
  
- *應用程式名稱*.exe.manifest：應用程式資訊清單。  
  
> [!NOTE]
> 如需部署和應用程式資訊清單的詳細資訊，請參閱[建置 WPF 應用程式](building-a-wpf-application-wpf.md)。  
  
 這些檔是在生成 XBAP 時生成的。 如需詳細資訊，請參閱[如何：建立新的 WPF 瀏覽器應用程式專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))。 與僅[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記頁面一樣，XBAP 通常發佈到 Web 服務器並使用 Internet 資源管理器進行查看。  
  
 可以使用任何部署技術將 XBAP 部署到用戶端。 但是，建議按一下一次，因為它提供以下功能：  
  
1. 在發行新版本時自動更新。  
  
2. 完全信任運行的 XBAP 的提升許可權。  
  
 根據預設，ClickOnce 會發行副檔名為 .deploy 的應用程式檔案。 這可能會造成問題，但可予以停用。 如需詳細資訊，請參閱 [ClickOnce 部署中的伺服器和用戶端組態問題](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)。  
  
 有關部署 XAML 瀏覽器應用程式 （XBAPs） 的詳細資訊，請參閱[WPF XAML 瀏覽器應用程式概述](wpf-xaml-browser-applications-overview.md)。  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a>安裝.NET Framework  
 要運行 WPF 應用程式，必須在用戶端上安裝 Microsoft .NET 框架。 當查看 WPF 瀏覽器託管的應用程式時，Internet Explorer 會自動檢測用戶端是否安裝了 .NET Framework。 如果未安裝 .NET 框架，Internet Explorer 會提示使用者安裝它。  
  
 為了檢測是否安裝了 .NET 框架，Internet Explorer 包括一個引導應用程式，該應用程式註冊為具有以下副檔名的內容檔的回退多用途 Internet 郵件擴展 （MIME） 處理常式：.xaml、.xps、.xbap和 .應用程式。 如果導航到這些檔案類型，並且未在用戶端上安裝 .NET Framework，則引導程式應用程式將請求安裝它的許可權。 如果未提供許可權，則既不安裝 .NET 框架，也不會安裝應用程式。  
  
 如果授予許可權，Internet Explorer 將使用 Microsoft 後臺智慧傳輸服務 （BITS） 下載並安裝 .NET 框架。 成功安裝 .NET 框架後，在新的瀏覽器視窗中打開最初請求的檔。  
  
 如需詳細資訊，請參閱[部署 .NET Framework 和應用程式](../../deployment/index.md)。  
  
## <a name="see-also"></a>另請參閱

- [建置 WPF 應用程式](building-a-wpf-application-wpf.md)
- [安全性](../security-wpf.md)
