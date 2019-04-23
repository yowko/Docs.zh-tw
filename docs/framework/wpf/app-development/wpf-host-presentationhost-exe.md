---
title: WPF 主應用程式 (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 586d306d0f375241c9382e1e24cf1af75b990ba9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122859"
---
# <a name="wpf-host-presentationhostexe"></a>WPF 主應用程式 (PresentationHost.exe)
Windows Presentation Foundation (WPF) 主應用程式 (PresentationHost.exe) 是可讓應用程式[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]相容的瀏覽器中裝載應用程式 (包括[!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)]和更新版本)。 根據預設，Windows Presentation Foundation (WPF) 的主機已登錄的殼層並[!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)]處理常式，如瀏覽器裝載[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]內容，包括：  
  
-   鬆散 (未編譯) 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案 (.xaml)。  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap)。  
  
 針對這些類型的檔案，Windows Presentation Foundation (WPF) 主機：  
  
-   啟動已登錄[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]來裝載 Windows Presentation Foundation (WPF) 內容的處理常式。  
  
-   載入所需的正確版本[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]和 Windows Presentation Foundation (WPF) 組件。  
  
-   確保部署區域的適當權限等級都已就緒。  
  
 本主題說明可以搭配使用 PresentationHost.exe 的命令列參數。  
  
## <a name="usage"></a>使用方式  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|filename|要啟動的檔案路徑。 也可以是 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。|  
|-debug|當啟動應用程式時，不會從存放區認可或執行應用程式。 這只有在已啟動本機檔案時才有用。|  
|-debugSecurityZoneURL \<url>|可搭配 [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 值使用，表示 PresentationHost.exe 應將應用程式視為已從指定 [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 進行部署，並加以偵錯。 這會決定部署區域與原始站台。|  
|-embedding|為 OLE 的必要項。 如果已指定 `-event` 或 `-debug` 參數，就不需要指定 `-embedding` 參數，因為該參數已在內部設定。|  
|-event \<eventname>|當 PresentationHost.exe 已初始化並準備好裝載 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 內容時，請開啟含此名稱的事件並對其發出通知。 如果開啟事件時發生錯誤 (例如事件尚未建立)，則會終止 PresentationHost.exe。|  
|-launchApplication \<url>|從指定的 URL，啟動獨立 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式。 系統會套用與 .NET 應用程式相關的 [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] 和 WinINet 安全性原則。|  
  
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
