---
title: 支援 .NET 應用程式部署的 Firefox 附加元件
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: e8f6947a0fe39998d9dc229ad7b95bfd2d426f6c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391403"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>支援 .NET 應用程式部署的 Firefox 附加元件
啟用 Windows Presentation Foundation (WPF) 外掛程式 Firefox 和.NET Framework Assistant for Firefox [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]、 鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，與 ClickOnce 應用程式，才能使用 Mozilla Firefox 瀏覽器。  
  
## <a name="wpf-plug-in-for-firefox"></a>外掛程式適用於 Firefox 的 WPF  
 外掛程式適用於 Firefox 的 WPF 可讓[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]和鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]瀏覽至並執行最上層或在 HTML IFRAME Firefox 瀏覽器中的檔案。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]是[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]可以發行至 Web 伺服器和中啟動應用程式支援的瀏覽器。 鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是僅限 XAML 的檔案，可以瀏覽至並顯示在支援的瀏覽器，如同 XML 檔案。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]外掛程式的 Firefox 會隨[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]。 Window 7 包含[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]，但不包含[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Firefox 的外掛程式。 您無法安裝[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]在 Windows 7 上的 Firefox 的外掛程式。  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]不包含[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Firefox 的外掛程式。 不過，如果兩個[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]並[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]是安裝，安裝的 WPF 外掛程式適用於 Firefox 與[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]。 因此[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]應用程式仍會執行，因為 WPF 主應用程式會載入正確的 framework 版本。 如需詳細資訊，請參閱 < [WPF 主應用程式 (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)。  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 若要從 Firefox 瀏覽器執行的獨立 ClickOnce 應用程式可讓.NET Framework Assistant for Firefox。 .NET Framework Assistant for Firefox 函式只有在安裝之前和之後的 Firefox 瀏覽器時相同。 Firefox 瀏覽器啟動時，[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]是安裝，Firefox 會尋找並會安裝.NET Framework Assistant for Firefox。 使用者可以設定.NET Framework Assistant for Firefox 來執行下列作業：  
  
-   執行 ClickOnce 應用程式之前提示。  
  
-   報告所有已安裝的新版.NET Framework 或只是最新版本。  
  
 .NET Framework Assistant for Firefox 隨附[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]。 移除適用於 Firefox 的.NET Framework Assistant 的詳細資訊，請參閱[如何移除適用於 Firefox 的.NET Framework Assistant](https://go.microsoft.com/fwlink/?LinkId=177944)。  
  
## <a name="see-also"></a>另請參閱  
 [部署 WPF 應用程式](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [WPF XAML 瀏覽器應用程式概觀](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)  
 [偵測有無安裝 Firefox 的 WPF 外掛程式](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
