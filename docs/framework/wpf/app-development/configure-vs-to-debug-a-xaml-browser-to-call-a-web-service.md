---
title: "如何：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 330ee213e147cfef709c919c95cb0e58159bc37b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>如何：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]在部分信任安全性沙箱，限制為網際網路 區域集合的權限內執行。 此權限集合會限制 Web 服務呼叫 Web 服務位於[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]來源應用程式的網站。 當[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]進行偵錯從[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]，但是其會被視為具有相同來源網站的 Web 服務的方法參考。 這個原因安全性例外狀況時引發[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]嘗試呼叫 Web 服務。 不過， [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]專案可以設定為模擬擁有其偵錯時所呼叫的 Web 服務位於相同的來源站台。 這可讓[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]安全地呼叫 Web 服務，而不會造成安全性例外狀況。  
  
## <a name="configuring-visual-studio"></a>設定 Visual Studio  
 若要設定[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]偵錯[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]呼叫 Web 服務：  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  在**專案設計工具**，按一下 [**偵錯**] 索引標籤。  
  
3.  在**起始動作**區段中，選取**啟動外部程式**並輸入下列命令：  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  在**起始選項**區段中，輸入下列內容**命令列引數**文字方塊：  
  
     `-debug`  *檔名*  
  
     *Filename*值**-偵錯**參數為.xbap 的檔案名稱; 例如：  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  這是預設組態，以建立方案的[!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)][!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]專案範本。  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  在**專案設計工具**，按一下 [**偵錯**] 索引標籤。  
  
3.  在**起始選項**區段中，加入下列的命令列參數，以**命令列引數**文字方塊：  
  
     `-debugSecurityZoneURL`  *URL*  
  
     *URL*值**-debugSecurityZoneURL**參數是[!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)]您要模擬為應用程式的來源網站的位置。  
  
 例如，請考慮[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]使用 Web 服務以下列[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 來源網站[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]為此 Web 服務是：  
  
 `http://services.msdn.microsoft.com`  
  
 因此，完成**-debugSecurityZoneURL**命令列參數，而且值為：  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a>請參閱  
 [WPF 主應用程式 (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
