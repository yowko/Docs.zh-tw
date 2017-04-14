---
title: "IWpfHostSupport | Microsoft Docs"
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
  - "IWpfHostSupport 介面"
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# IWpfHostSupport
透過 PresentationHost.exe 裝載 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 內容的應用程式會實作這個介面，以提供該主應用程式和 PresentationHost.exe 之間的整合點。  
  
## 備註  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 應用程式，例如網頁瀏覽器可以裝載 [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] 內容，包括 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 和鬆散的 XAML。  為了裝載 [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] 內容，[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 應用程式會建立 [WebBrowser 控制項](http://go.microsoft.com/fwlink/?LinkId=97911) \(英文\) 的執行個體。  為了接受裝載，[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] 會建立 PresentationHost.exe 執行個體，提供裝載的 [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] 內容給主應用程式顯示在 [WebBrowser 控制項](http://go.microsoft.com/fwlink/?LinkId=97911) \(英文\)。  
  
 `IWpfHostSupport` 所啟用的整合可以讓 PresentationHost.exe：  
  
-   針對主應用程式有興趣的未經處理輸入裝置 \(人性化介面裝置，Human Interface Devices\) 進行探索和註冊。  
  
-   從註冊的未經處理輸入裝置接收輸入訊息，並轉送適當訊息給主應用程式。  
  
-   向主應用程式查詢自訂進度和錯誤使用者介面。  
  
> [!NOTE]
>  這個 API 只預定在本機用戶端電腦上使用並支援  
  
## Members  
  
|成員|描述|  
|--------|--------|  
|[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|讓 PresentationHost.exe 尋找主應用程式有興趣的未經處理輸入裝置 \(人性化介面裝置\)。|  
|[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|除非有傳回 E\_NOTIMPL，否則只要收到訊息，PresentationHost.exe 就會呼叫它。|  
|[GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)|根據預設，PresentationHost.exe 會提供自己的部署進度和部署錯誤使用者介面 \(在部署 WPF 內容時所顯示的\)。|