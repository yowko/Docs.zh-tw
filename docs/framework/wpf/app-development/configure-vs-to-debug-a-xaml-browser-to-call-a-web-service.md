---
title: "如何：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務 | Microsoft Docs"
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
  - "設定 Visual Studio 偵錯 XAML 瀏覽器應用程式 [WPF]"
  - "設定 Visual Studio 偵錯 XBAP [WPF]"
  - "偵錯 XBAP 的安全性例外狀況 [WPF]"
  - "偵錯呼叫 Web 服務的 XBAP [WPF]"
  - "XBAP 的安全性例外狀況 [WPF], 偵錯"
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 會在限於網際網路區域權限集合的部分信任安全性沙箱中執行。  此權限集合限制 Web 服務呼叫只能是位於 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 應用程式來源網站的 Web 服務。  不過，當 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 從 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] 偵錯時，不會將它的來源網站視為與它所參考的 Web 服務相同。  這會在 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 嘗試呼叫 Web 服務時，導致引發安全性例外狀況。  不過，[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] 專案可設成在偵錯時模擬其來源網站與所呼叫的 Web 服務相同。  這可讓 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 安全地呼叫 Web 服務，而不會導致安全性例外狀況。  
  
## 設定 Visual Studio  
 若要設定 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] 來偵錯呼叫 Web 服務的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]：  
  
1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  在 \[**專案設計工具**\] 中，按一下 \[**偵錯**\] 索引標籤。  
  
3.  在 \[**起始動作**\] 區段中選取 \[**起始外部程式**\]，然後輸入下面這一行：  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  在 \[**起始選項**\] 區段中，在 \[**命令列的引數**\] 文字方塊中輸入：  
  
     `-debug`  *filename*  
  
     **\-debug** 參數的 *filename* 值是 .xbap 檔名，例如：  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  這是使用 [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] 專案範本所建立方案的預設組態。  
  
1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  在 \[**專案設計工具**\] 中，按一下 \[**偵錯**\] 索引標籤。  
  
3.  在 \[**起始選項**\] 區段中，將下列命令列參數加入到 \[**命令列的引數**\] 文字方塊中：  
  
     `-debugSecurityZoneURL`  *URL*  
  
     **\-debugSecurityZoneURL** 參數的 *URL* 值是要模擬為應用程式來源網站之位置的 [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)]。  
  
 例如，假設有個 [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] 使用下列 [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 的 Web 服務：  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 這個 Web 服務的來源網站 [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 就是：  
  
 `http://services.msdn.microsoft.com`  
  
 因此，完整的 **\-debugSecurityZoneURL** 命令列參數和值就是：  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## 請參閱  
 [WPF 主應用程式 \(PresentationHost.exe\)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)