---
title: "支援 .NET 應用程式部署的 Firefox 附加元件 | Microsoft Docs"
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
  - ".NET 應用程式部署, 使用 Firefox 附加元件部署"
  - ".NET Framework Assistant for Firefox"
  - "適用於 .NET 應用程式部署的 Firefox 附加元件"
  - "適用於 Firefox 的 WPF 外掛程式"
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 支援 .NET 應用程式部署的 Firefox 附加元件
Firefox 的 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 外掛程式和 .NET Framework Assistant for Firefox 可讓 [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]、鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和 ClickOnce 應用程式搭配 Mozilla Firefox 瀏覽器運作。  
  
## Firefox 的 WPF 外掛程式  
 Firefox 的 WPF 外掛程式可讓您在 Firefox 瀏覽器的最上層或 HTML IFRAME 中巡覽和執行 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 和鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案。  [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 是一種可以發行至 Web 伺服器並在支援的瀏覽器內啟動的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式。  鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 則是可以在支援的瀏覽器中巡覽至和顯示的純 XAML 檔案，與 XML 檔很類似。  
  
 Firefox 的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 外掛程式會隨 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] 一起安裝。  Window 7 包含 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]，但不含 Firefox 的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 外掛程式。您無法在 Windows 7 安裝 Firefox 的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 外掛程式。  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 不含 Firefox 的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 外掛程式。不過，如果同時安裝 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]，則 Firefox 的 WPF 外掛程式會隨 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] 一起安裝。  因此，[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 應用程式仍然會執行，因為 WPF 主應用程式會載入正確版本的架構。  如需詳細資訊，請參閱 [WPF 主應用程式 \(PresentationHost.exe\)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)。  
  
## .NET Framework Assistant for Firefox  
 .NET Framework Assistant for Firefox 可讓您從 Firefox 瀏覽器執行獨立的 ClickOnce 應用程式。  .NET Framework Assistant for Firefox 不論是在 Firefox 瀏覽器之前還是之後安裝，運作方式都相同。  如果啟動 Firefox 瀏覽器時已安裝 [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]，Firefox 會尋找並安裝 .NET Framework Assistant for Firefox。  使用者可以設定 .NET Framework Assistant for Firefox 執行下列動作：  
  
-   在執行 ClickOnce 應用程式之前顯示提示  
  
-   報告所有已安裝的 .NET Framework 版本或只報告最新版本。  
  
 .NET Framework Assistant for Firefox 包含在 [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] 中。  如需移除 .NET Framework Assistant for Firefox 的詳細資訊，請參閱[如何移除 .NET Framework Assistant for Firefox](http://go.microsoft.com/fwlink/?LinkId=177944) \(機器譯文\)。  
  
## 請參閱  
 [部署 WPF 應用程式](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)   
 [WPF XAML 瀏覽器應用程式概觀](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)   
 [偵測有無安裝 Firefox 的 WPF 外掛程式](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)