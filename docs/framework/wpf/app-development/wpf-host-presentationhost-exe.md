---
title: "WPF 主應用程式 (PresentationHost.exe) | Microsoft Docs"
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
  - "PresentationHost.exe"
  - "WPF 主應用程式"
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# WPF 主應用程式 (PresentationHost.exe)
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host \(PresentationHost.exe\) 是應用程式，可讓 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式裝載於相容的瀏覽器中 \(包含 [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] \(含\) 以後版本\)。  根據預設，[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host 會註冊為 Shell 和 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 處理常式，適用於瀏覽器裝載的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 內容，其中包含：  
  
-   鬆散 \(未壓縮的\) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案 \(.xaml\)  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] \(.xbap\)  
  
 對於這些檔案類型，[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host 會：  
  
-   啟動已註冊的 [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] 處理常式，以裝載 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 內容。  
  
-   載入正確版本的必要 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 和 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 組件。  
  
-   確定已備妥部署區域的適當使用權限等級。  
  
 本主題說明可用於 PresentationHost.exe 的命令列參數。  
  
## 使用方式  
 `PresentationHost.exe [parameters] uri|filename`  
  
## 參數  
  
|參數|描述|  
|--------|--------|  
|filename|要啟動之檔案的路徑。  也可以是 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。|  
|\-debug|啟動應用程式時，不從存放區進行認可或執行。  啟動本機檔案時，此參數才有作用。|  
|\-debugSecurityZoneURL \<url\>|與 [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 值搭配使用，以指示 PresentationHost.exe 有個應用程式應予以偵錯，就猶如從指定的 [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 進行部署一般。  此參數可同時決定部署區域與來源網站。|  
|\-embedding|OLE 的必要參數。  如果已指定 `-event` 或 `-debug` 參數，則不需指定 `-embedding` 參數，因為該參數已在內部設定。|  
|\-event \<eventname\>|開啟具有此名稱的事件，並在 PresentationHost.exe 已初始化且準備裝載 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 內容時發出信號。  如果在開啟此事件時發生錯誤 \(例如，此事件尚未建立\)，PresentationHost.exe 就會結束。|  
|\-launchApplication \<url\>|透過指定的 URL 啟動獨立的 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式。  會套用與 .NET 應用程式有關的 [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] 和 WinINet 安全性原則。|  
  
## 案例  
  
### Shell 處理常式  
 `PresentationHost.exe example.xbap`  
  
### MIME 處理常式  
 `PresentationHost.exe -embedding example.xbap`  
  
### Visual Studio 偵錯  
 `PresentationHost.exe -debug example.xbap`  
  
### Visual Studio 區域偵錯  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## 請參閱  
 [安全性](../../../../docs/framework/wpf/security-wpf.md)