---
title: 支援 .NET 應用程式部署的 Firefox 附加元件
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: f05f5afa0c0a7ef858442bd98233865834b8b89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547439"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>支援 .NET 應用程式部署的 Firefox 附加元件
Windows Presentation Foundation (WPF) 外掛程式 Firefox 和.NET Framework Assistant firefox 啟用[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]、 鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，和 ClickOnce 應用程式 Mozilla Firefox 瀏覽器所使用。  
  
## <a name="wpf-plug-in-for-firefox"></a>WPF Firefox 外掛程式  
 WPF Firefox 外掛程式可讓[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]和鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，以瀏覽至並在最上層，或在 HTML 中的 IFRAME Firefox 瀏覽器中執行。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]是[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]可以發行到 Web 伺服器和內啟動應用程式支援的瀏覽器。 鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是僅限 XAML 的檔案，可以瀏覽至並顯示在支援的瀏覽器，非常類似的 XML 檔案。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]外掛程式與安裝 Firefox [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]。 視窗 7 包含[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]，但不包含[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Firefox 外掛程式。 您無法安裝[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]外掛程式，以用於在 Windows 7 上 Firefox。  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]不包含[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Firefox 外掛程式。 不過，如果兩個[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]和[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]會安裝，WPF Firefox 外掛程式會隨[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]。 因此[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]應用程式仍會執行，因為 WPF 主機會載入正確的 framework 版本。 如需詳細資訊，請參閱[WPF 主機 (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)。  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 .NET Framework 助理 firefox 讓獨立的 ClickOnce 應用程式從 Firefox 瀏覽器執行。 .NET Framework 助理 Firefox 函式只有在安裝之前和之後 Firefox 瀏覽器時，即會相同。 Firefox 瀏覽器啟動時，[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]已安裝，Firefox 找到並安裝.NET Framework 助理 firefox。 使用者可以設定 .NET Framework 助理 firefox，執行下列操作：  
  
-   執行 ClickOnce 應用程式之前提示。  
  
-   報告所有安裝的.NET Framework 版本或最新的版本。  
  
 .NET Framework 助理 firefox 隨附於[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]。 Firefox 移除.NET Framework 助理的詳細資訊，請參閱[如何移除.NET Framework 助理 firefox](http://go.microsoft.com/fwlink/?LinkId=177944)。  
  
## <a name="see-also"></a>另請參閱  
 [部署 WPF 應用程式](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [WPF XAML 瀏覽器應用程式概觀](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)  
 [偵測有無安裝 Firefox 的 WPF 外掛程式](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
