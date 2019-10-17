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
ms.openlocfilehash: 7730ab452e227b11e5a9dd69cdabec51f333ce4f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321204"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>如何：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 在僅限網際網路區域許可權集的部分信任安全性沙箱中執行。 這個許可權集合會將 Web 服務通話限制為位於 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 應用程式的來源網站上的 Web 服務。 不過，從 Visual Studio 2005 中調試 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 時，不會將其所參考之 Web 服務的來源網站視為相同。 這會導致 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 嘗試呼叫 Web 服務時，引發安全性例外狀況。 不過，Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] 專案可以設定為模擬與在進行調試時所呼叫的 Web 服務相同的來源網站。 這可讓 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 安全地呼叫 Web 服務，而不會導致安全性例外狀況。

## <a name="configuring-visual-studio"></a>設定 Visual Studio
 若要將 Visual Studio 2005 設定為可偵測呼叫 Web 服務的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]：

1. 在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。

2. 在 [**專案設計**工具] 中，按一下 [**調試**] 索引標籤。

3. 在 [**起始動作**] 區段中，選取 [**啟動外部程式**]，並輸入下列內容：

     `C:\WINDOWS\System32\PresentationHost.exe`

4. 在 [**開始選項**] 區段的 [**命令列引數**] 文字方塊中，輸入下列內容：

     `-debug`  *檔案名*

     **-Debug**參數的*檔案名*值是 xbap filename;例如：

     `-debug c:\example.xbap`

> [!NOTE]
> 這是使用 Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] 專案範本所建立之解決方案的預設設定。

1. 在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。

2. 在 [**專案設計**工具] 中，按一下 [**調試**] 索引標籤。

3. 在 [**啟動選項**] 區段中，將下列命令列參數新增至 [**命令列引數**] 文字方塊：

     `-debugSecurityZoneURL`  *URL*

     **-DebugSecurityZoneURL**參數的*url*值是您想要模擬為應用程式來源網站之位置的 url。

 例如，假設有一個使用具有下列 URL 之 Web 服務的 [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]：

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 此 Web 服務的來源網站 URL 為：

 `http://services.msdn.microsoft.com`

 因此，完整的**debugSecurityZoneURL**命令列參數和值為：

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>請參閱

- [WPF 主應用程式 (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
