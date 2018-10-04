---
title: 如何：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: 182ceb96385bdca74d1d5c20079f78fe589982cf
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779188"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>如何：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 網際網路區域集合的權限僅限於在部分信任安全性沙箱內執行。 此權限集合會限制只有 web 服務，是位在 Web 服務呼叫[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]應用程式的來源網站。 當[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]進行偵錯從 Visual Studio 2005，不過，它不是擁有相同來源網站上的 Web 服務的方法參考。 此會導致安全性例外狀況，當引發[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]嘗試呼叫 Web 服務。 不過，Visual Studio 2005[!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]專案可以設定為模擬擁有為其偵錯時所呼叫的 Web 服務相同的來源站台。 這可讓[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]來安全地呼叫 Web 服務，而不會造成安全性例外狀況。

## <a name="configuring-visual-studio"></a>設定 Visual Studio
 若要設定 Visual Studio 2005 偵錯[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]呼叫 Web 服務：

1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2.  在 [**專案設計工具**，按一下**偵錯**] 索引標籤。

3.  在 **起始動作**區段中，選取**啟動外部程式**並輸入下列命令：

     `C:\WINDOWS\System32\PresentationHost.exe`

4.  在 **啟動選項**區段中，輸入下列內容輸入**命令列引數**文字方塊：

     `-debug`  *檔案名稱*

     *檔名*值 **-偵錯**參數是.xbap 檔案名稱; 例如：

     `-debug c:\example.xbap`

> [!NOTE]
>  這是由 Visual Studio 2005 所建立之解決方案的預設組態[!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]專案範本。

1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2.  在 [**專案設計工具**，按一下**偵錯**] 索引標籤。

3.  在 **啟動選項**區段中，加入下列的命令列參數來**命令列引數**文字方塊：

     `-debugSecurityZoneURL`  *URL*

     *URL*值 **-debugSecurityZoneURL**參數是[!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)]您想要模擬為您的應用程式的來源網站上的位置。

 例如，請考慮[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]使用 Web 服務以下列[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 來源網站上的[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]為此 Web 服務是：

 `http://services.msdn.microsoft.com`

 因此，完整 **-debugSecurityZoneURL**命令列參數，而且值是：

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>另請參閱
 [WPF 主應用程式 (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
