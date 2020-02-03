---
title: WPF 主應用程式 (PresentationHost.exe)
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: bda7efbb1b7a4760199215bdb58c12b3063e290c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743395"
---
# <a name="wpf-host-presentationhostexe"></a>WPF 主應用程式 (PresentationHost.exe)
Windows Presentation Foundation （WPF）主機（Presentationhost.exe）是應用程式，可讓 WPF 應用程式裝載在相容的瀏覽器中（包括 Microsoft Internet Explorer 6 和更新版本）。 根據預設，Windows Presentation Foundation （WPF）主機會註冊為瀏覽器裝載 WPF 內容的 shell 和 MIME 處理常式，其中包括：  
  
- 鬆散 (未編譯) 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案 (.xaml)。  
  
- XAML 瀏覽器應用程式（XBAP）（xbap）。  
  
 對於這些類型的檔案，請 Windows Presentation Foundation （WPF）主機：  
  
- 啟動已註冊的 HTML 處理常式，以裝載 Windows Presentation Foundation （WPF）內容。  
  
- 載入所需 common language runtime （CLR）和 Windows Presentation Foundation （WPF）元件的正確版本。  
  
- 確保部署區域的適當權限等級都已就緒。  
  
 本主題說明可以搭配使用 PresentationHost.exe 的命令列參數。  
  
## <a name="usage"></a>使用方式  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|filename|要啟動的檔案路徑。 也可以是 URI。|  
|-debug|當啟動應用程式時，不會從存放區認可或執行應用程式。 這只有在已啟動本機檔案時才有用。|  
|-debugSecurityZoneURL \<url>|與 URL 值搭配使用，以指示 Presentationhost.exe 應用程式應該進行調試，如同從指定的 URL 部署一樣。 這會決定部署區域與原始站台。|  
|-embedding|為 OLE 的必要項。 如果已指定 `-event` 或 `-debug` 參數，就不需要指定 `-embedding` 參數，因為該參數已在內部設定。|  
|-event \<eventname>|開啟具有這個名稱的事件，並在 Presentationhost.exe 初始化並準備好裝載 WPF 內容時發出通知。 如果開啟事件時發生錯誤 (例如事件尚未建立)，則會終止 PresentationHost.exe。|  
|-launchApplication \<url>|從指定的 URL 啟動獨立 ClickOnce 應用程式。 適用于 .NET 應用程式的 Internet Explorer 和 WinINet 安全性原則會套用。|  
  
## <a name="scenarios"></a>案例  
  
### <a name="shell-handler"></a>殼層處理常式  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>MIME 處理常式  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Visual Studio 偵錯  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Visual Studio 區域中偵錯  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>另請參閱

- [安全性](../security-wpf.md)
