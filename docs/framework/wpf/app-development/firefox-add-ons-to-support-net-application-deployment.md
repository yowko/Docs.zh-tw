---
title: 支援 .NET 應用程式部署的 Firefox 附加元件
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 56f5f633092d8aa0bfabdb0570ec26f14221838d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124607"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>支援 .NET 應用程式部署的 Firefox 附加元件
適用于 Firefox 的 Windows Presentation Foundation （WPF）外掛程式和 Firefox 的 .NET Framework 小幫手可讓 XAML 瀏覽器應用程式（Xbap）、鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和 ClickOnce 應用程式與 Mozilla Firefox 瀏覽器搭配使用。  
  
## <a name="wpf-plug-in-for-firefox"></a>適用于 Firefox 的 WPF 外掛程式  
 適用于 Firefox 的 WPF 外掛程式可讓 Xbap 和鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案導覽至頂層，或在 Firefox 瀏覽器的 HTML IFRAME 中執行。 XBAP 是 WPF 應用程式，可以發行至 Web 服務器並在支援的瀏覽器中啟動。 鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是僅限 XAML 的檔案，可在支援的瀏覽器中導覽和顯示，與 XML 檔案非常類似。  
  
 Firefox 的 WPF 外掛程式會與 .NET Framework 3.5 一起安裝。 Window 7 包含 .NET Framework 3.5，但不包含 Firefox 的 WPF 外掛程式。 您無法在 Windows 7 上安裝 Firefox 的 WPF 外掛程式。  
  
 .NET Framework 4 不包含 Firefox 的 WPF 外掛程式。 不過，如果已安裝 .NET Framework 3.5 和 .NET Framework 4，Firefox 的 WPF 外掛程式會與 .NET Framework 3.5 一起安裝。 因此 .NET Framework 4 應用程式仍會執行，因為 WPF 主機會載入正確的架構版本。 如需詳細資訊，請參閱[WPF Host （presentationhost.exe .exe）](wpf-host-presentationhost-exe.md)。  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 Firefox 的 [.NET Framework 助理] 可讓獨立 ClickOnce 應用程式從 Firefox 瀏覽器執行。 Firefox 的 .NET Framework 助理在 Firefox 瀏覽器之前和之後安裝時，會有相同的功能。 當 Firefox 瀏覽器啟動且安裝了 .NET Framework 3.5 SP1 時，Firefox 會尋找並安裝 Firefox 的 .NET Framework 助理。 使用者可以設定 Firefox 的 [.NET Framework 助理] 來執行下列動作：  
  
- 在執行 ClickOnce 應用程式之前提示。  
  
- 報告所有已安裝的 .NET Framework 版本或僅限最新版本。  
  
 適用于 Firefox 的 [.NET Framework 助理] 隨附于 .NET Framework 3.5 SP1。 如需移除 Firefox 的 [.NET Framework 助理] 的相關資訊，請參閱[如何移除 firefox 的 .NET Framework 助理](https://support.microsoft.com/help/963707/how-to-remove-the-net-framework-assistant-for-firefox)。  
  
## <a name="see-also"></a>另請參閱

- [部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)
- [WPF XAML 瀏覽器應用程式概觀](wpf-xaml-browser-applications-overview.md)
- [偵測有無安裝 Firefox 的 WPF 外掛程式](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
