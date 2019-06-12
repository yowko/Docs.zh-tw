---
title: 應用程式啟動時間
ms.date: 03/30/2017
helpviewer_keywords:
- splash screen [WPF], startup time
- WPF [WPF], startup time
- startup time [WPF]
- application startup [WPF]
- performance [WPF], startup time
ms.assetid: f0ec58d8-626f-4d8a-9873-c20f95e08b96
ms.openlocfilehash: 321aad14d17d6ef6fe0b7c112f8f694dd1c767d6
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832693"
---
# <a name="application-startup-time"></a>應用程式啟動時間
WPF 應用程式啟動所需的時間可能有很大的差異。 本主題說明各種技術來縮短 Windows Presentation Foundation (WPF) 應用程式的認知和實際啟動時間。  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>了解冷啟動和暖啟動  
 冷啟動發生於系統重新開機後第一次啟動應用程式，或您啟動應用程式，關閉它，然後經過很長一段時間後重新啟動。 應用程式啟動時，如果 Windows 記憶體管理員的待命清單中沒有必要的分頁 (程式碼、靜態資料、登錄等)，就會發生分頁錯誤。 將頁面放入記憶體需要存取磁碟。  
  
 暖啟動發生於主要通用語言執行平台 (CLR) 元件的大部分頁面已經載入記憶體中，可節省寶貴的磁碟存取時間。 這就是為什麼 Managed 應用程式第二次執行時較快啟動。  
  
## <a name="implement-a-splash-screen"></a>實作啟動顯示畫面  
 如果從啟動應用程式到顯示第一個 UI 之間，有很明顯、無可避免的延遲時間，請使用「啟動顯示畫面」  最佳化感知的啟動時間。 這種方法會在使用者啟動應用程式時，幾乎立即顯示影像。 當應用程式準備好顯示第一個 UI 時，啟動顯示畫面會消失。 從.NET Framework 3.5 SP1 中，您可以使用<xref:System.Windows.SplashScreen>類別來實作啟動顯示畫面。 如需詳細資訊，請參閱[將啟動顯示畫面新增至 WPF 應用程式](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)。  
  
 您也可以使用原生 Win32 圖形，以實作您自己的啟動顯示畫面。 顯示您之前的實作<xref:System.Windows.Application.Run%2A>呼叫方法。  
  
## <a name="analyze-the-startup-code"></a>分析啟始程式碼  
 判斷冷啟動緩慢的原因。 磁碟 I/O 可能是原因，但不一定如此。 一般情況下，您應該盡可能不要使用外部資源，例如網路、Web 服務或磁碟。  
  
 在測試之前，請確認沒有其他正在執行的應用程式或服務使用 Managed 程式碼或 WPF 程式碼。  
  
 重新開機之後立即啟動 WPF 應用程式，判斷它花多少時間才出現。 如果後續啟動您的應用程式 (暖啟動) 都非常快速，則冷啟動問題極可能是 I/O 引起。  
  
 如果應用程式的冷啟動問題與 I/O 無關，很可能是您的應用程式執行一些冗長的初始化或計算、等待某個事件完成，或在啟動時需要大量 JIT 編譯。 下列章節詳述其中一些狀況。  
  
## <a name="optimize-module-loading"></a>最佳化模組載入  
 使用處理序總管 (Procexp.exe) 和 Tlist.exe 之類的工具，判斷您的應用程式載入哪些模組。 `Tlist <pid>` 命令會顯示處理序載入的所有模組。  
  
 例如，如果您未連線至網路，但看到載入 System.Web.dll，表示您的應用程式中有模組參考這個組件。 請確定該參考是必要。  
  
 如果應用程式有多個模組，請將它們合併成單一模組。 這個方法需要的 CLR 組件載入負荷較少。 較少的組件也表示 CLR 維護較少的狀態。  
  
## <a name="defer-initialization-operations"></a>延後初始化作業  
 請考慮將初始化程式碼延後到主要應用程式視窗出現之後。  
  
 請注意，初始化可能在類別建構函式內執行，如果初始化程式碼參考其他類別，可能會造成連鎖效應而執行許多類別建構函式。  
  
## <a name="avoid-application-configuration"></a>避免應用程式組態  
 請考慮避免應用程式組態。 例如，如果應用程式有簡單的組態需求及嚴格的啟動時間目標，則登錄項目或簡單的 INI 檔案可能是較快的啟動替代方法。  
  
## <a name="utilize-the-gac"></a>利用 GAC  
 如果組件未安裝在全域組件快取 (GAC) 中，則強式命名組件的雜湊驗證和 Ngen 映像驗證 (如果電腦上有該組件的原生映像) 會造成延遲。 安裝在 GAC 中的所有組件會跳過強式名稱驗證。 如需詳細資訊，請參閱 [Gacutil.exe (全域組件快取工具)](../../tools/gacutil-exe-gac-tool.md)。  
  
## <a name="use-ngenexe"></a>使用 Ngen.exe  
 請考慮在您的應用程式上使用原生映像產生器 (Ngen.exe)。 使用 Ngen.exe 表示以 CPU 消耗換取更多磁碟存取，因為由 Ngen.exe 產生的原生映像可能大於 MSIL 映像。  
  
 若要改善暖啟動時間，您在應用程式上應該一律使用 Ngen.exe，因為這可避免應用程式程式碼 JIT 編譯的 CPU 成本。  
  
 在某些冷啟動情節中，使用 Ngen.exe 也很有用。 這是因為不需要載入 JIT 編譯器 (mscorjit.dll)。  
  
 同時有 Ngen 和 JIT 模組可能得到最差效果。 這是因為必須載入 mscorjit.dll，而且當 JIT 編譯器處理您的程式碼時，JIT 編譯器在讀取組件的中繼資料時必須存取 Ngen 映像中的許多分頁。  
  
### <a name="ngen-and-clickonce"></a>Ngen 和 ClickOnce  
 您打算部署應用程式的方式也會造成載入時間不同。 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式部署不支援 Ngen。 如果您決定對應用程式使用 Ngen.exe，您必須使用其他部署機制，例如 Windows Installer。  
  
 如需詳細資訊，請參閱 [Ngen.exe (原生映像產生器)](../../tools/ngen-exe-native-image-generator.md)。  
  
### <a name="rebasing-and-dll-address-collisions"></a>重設基底和 DLL 位址衝突  
 如果您使用 Ngen.exe，請注意，當原生映像載入記憶體中時，可能會發生重定基底。 如果因為位址範圍已配置而未於慣用基底位址載入 DLL，Windows 載入器會將其載入其他位址，作業會很耗時。  
  
 您可以使用虛擬位址傾印 (Vadump.exe) 工具，檢查是否有所有頁面都是私用的模組。 如果是這樣，模組可能已重定基底到不同的位址。 因此，無法共用其頁面。  
  
 如需有關如何設定基底位址的詳細資訊，請參閱 [Ngen.exe (原生映像產生器)](../../tools/ngen-exe-native-image-generator.md)。  
  
## <a name="optimize-authenticode"></a>最佳化 Authenticode  
 Authenticode 驗證會增加啟動時間。 Authenticode 簽署的組件必須經過憑證授權單位 (CA) 驗證。 這項驗證可能耗費時間，因為需要連線至網路許多次來下載目前的憑證撤銷清單。 這也可確保受信任根的路徑上存在完整的有效憑證鏈結。 這意味著載入組件時會延遲幾秒鐘。  
  
 請考慮在用戶端電腦上安裝 CA 憑證，或盡可能避免使用 Authenticode。 如果您知道您的應用程式不需要發行者辨識項，則不需要付出簽章驗證的成本。  
  
 從.NET Framework 3.5 開始，沒有略過 Authenticode 驗證的組態選項。 若要這樣做，請在 app.exe.config 檔案中新增下列設定︰  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 如需詳細資訊，請參閱 [\<generatePublisherEvidence> 元素](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md)。  
  
## <a name="compare-performance-on-windows-vista"></a>在 Windows Vista 上比較效能  
 Windows Vista 的記憶體管理員有一項稱為 SuperFetch 的技術。 SuperFetch 會分析一段時間的使用模式，以判斷特定使用者的最佳記憶體內容。 它會持續運作來隨時維護該內容。  
  
 這種方式不同於 Windows XP 中所使用的預先提取技術，此技術會預先將資料載入記憶體中，但不分析使用模式。 經過一段時間，如果使用者經常在 Windows Vista 上使用您的 WPF 應用程式，應用程式的冷啟動時間會改善。  
  
## <a name="use-appdomains-efficiently"></a>有效率地使用 AppDomain  
 可能的話，請將組件載入定義域中性程式碼區域中，以確保應用程式的所有 AppDomains 中使用原生映像 (如果有的話)。  
  
 為了達到最佳效能，請減少跨網域呼叫，以強制達成有效率的跨網域通訊。 可能的話，請使用不含引數或有基本型別引數的呼叫。  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>使用 NeutralResourcesLanguage 屬性  
 使用<xref:System.Resources.NeutralResourcesLanguageAttribute>指定中性文化特性<xref:System.Resources.ResourceManager>。 這個方法可避免組件查閱失敗。  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>使用 BinaryFormatter 類別進行序列化  
 如果您必須使用序列化，請使用<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>類別而不是<xref:System.Xml.Serialization.XmlSerializer>類別。 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>類別實作在基底類別庫 (BCL) mscorlib.dll 組件中。 <xref:System.Xml.Serialization.XmlSerializer> System.Xml.dll 組件，這可能是載入其他 DLL 中實作。  
  
 如果您必須使用<xref:System.Xml.Serialization.XmlSerializer>類別，您可以達到更佳的效能，如果您預先產生序列化組件。  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>將 ClickOnce 設定為啟動之後檢查更新  
 如果您的應用程式使用 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]，請將 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 設定成在應用程式啟動之後檢查部署網站是否有更新，以避免在啟動時存取網路。  
  
 如果您使用 XAML 瀏覽器應用程式 (XBAP) 模型，請記住，即使 XBAP 已在 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 快取中，[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 仍會檢查部署網站是否有更新。 如需詳細資訊，請參閱 [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment)。  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>將 PresentationFontCache 服務設定為自動啟動  
 重新開機後第一個執行的 WPF 應用程式是 PresentationFontCache 服務。 此服務會快取系統字型、改善字型存取，並改善整體效能。 啟動服務時會產生額外負荷，在一些受控制的環境中，請考慮將服務設定成在系統重新開機時自動啟動。  
  
## <a name="set-data-binding-programmatically"></a>以程式設計的方式設定資料繫結  
 而不是使用 XAML 來設定<xref:System.Windows.FrameworkElement.DataContext%2A>宣告的主視窗中，請考慮設定它以程式設計方式在<xref:System.Windows.Application.OnActivated%2A>方法。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.SplashScreen>
- <xref:System.AppDomain>
- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- <xref:System.Resources.ResourceManager>
- [在 WPF 應用程式中加入啟動顯示畫面](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)
- [Ngen.exe (原生映像產生器)](../../tools/ngen-exe-native-image-generator.md)
- [\<generatePublisherEvidence> 元素](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
