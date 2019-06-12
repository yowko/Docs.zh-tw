---
title: WPF XAML 瀏覽器應用程式概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
ms.openlocfilehash: 286ec3c67e296eb49776e0f2882954c75c53eed8
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833980"
---
# <a name="wpf-xaml-browser-applications-overview"></a>WPF XAML 瀏覽器應用程式概觀
<a name="introduction"></a>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 結合的 Web 應用程式和豐富型用戶端應用程式的功能。 如同 Web 應用程式，XBAP 可以部署至 Web 伺服器，並且從 Internet Explorer 或 Firefox 啟動。 如同豐富型用戶端應用程式，Xbap 可以利用 WPF 的功能。 開發 XBAP 也類似於豐富型用戶端開發。 本主題提供 XBAP 開發的簡單、高階介紹，並且描述 XBAP 開發與標準豐富型用戶端開發的不同之處。  
  
 此主題包括下列章節：  
  
- [建立新的 XAML 瀏覽器應用程式 (XBAP)](#creating_a_new_xaml_browser_application_xbap)  
  
- [部署 XBAP](#deploying_a_xbap)  
  
- [與主機網頁通訊](#communicating_with_the_host_web_page)  
  
- [XBAP 安全性考量](#xbap_security_considerations)  
  
- [XBAP 開始時間效能考量](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a>建立新的 XAML 瀏覽器應用程式 (XBAP)  
 若要建立新的 XBAP 專案最簡單的方式是使用 Microsoft Visual Studio。 建立新專案時，從範本清單選取 [WPF 瀏覽器應用程式]  。 如需詳細資訊，請參閱[如何：建立新的 WPF 瀏覽器應用程式專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))。  
  
 當您執行 XBAP 專案時，它會在瀏覽器視窗中開啟，而不是在獨立視窗中開啟。 當您偵錯 XBAP 從 Visual Studio 時，應用程式會使用網際網路區域權限執行，並因此如果會擲回安全性例外狀況會在超過這些權限。 如需詳細資訊，請參閱[安全性](../security-wpf.md)和 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。  
  
> [!NOTE]
>  如果您使用 Visual Studio 或您想来深入了解專案檔不進行開發，請參閱[建置 WPF 應用程式](building-a-wpf-application-wpf.md)。  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a>部署 XBAP  
 當您建置 XBAP 時，輸出會包含下列三個檔案︰  
  
|檔案|描述|  
|----------|-----------------|  
|可執行檔 (.exe)|它包含已編譯的程式碼，副檔名為 .exe。|  
|應用程式資訊清單 (.manifest)|它包含與應用程式相關聯的中繼資料，副檔名為 .manifest。|  
|部署資訊清單 (.xbap)|此檔案包含 ClickOnce 部署應用程式會使用與副檔名為.xbap 的資訊。|  
  
 您將 XBAP 部署至 Web 伺服器，例如，[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或更新版本。 您不必安裝.NET Framework 的 Web 伺服器上，但您必須註冊[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)]類型和副檔名。 如需詳細資訊，請參閱[設定 IIS 5.0 和 IIS 6.0 以部署 WPF 應用程式](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md)。  
  
 若要準備您的 XBAP 以進行部署，將 .exe 和相關聯的資訊清單複製到 Web 伺服器。 建立 HTML 網頁，其中包含可開啟部署資訊清單 (它是副檔名為 .xbap 的檔案) 的超連結。 當使用者按一下.xbap 檔案的連結時，ClickOnce 會自動處理下載和啟動應用程式的機制。 下列範例程式碼顯示包含指向 XBAP 之超連結的 HTML 網頁。  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 您也可以在網頁的框架中裝載 XBAP。 建立具有一或多個框架的網頁。 將框架的來源屬性設為部署資訊清單檔。 如果您想要使用內建的機制，在裝載的網頁和 XBAP 之間進行通訊，您必須在框架中裝載應用程式。 下列程式碼範例顯示具有兩個框架的 HTML 網頁，第二個框架的來源設定為 XBAP。  
  
```html
<html>   
    <head>
        <title>A page with frames</title>
    </head>  
    <frameset cols="50%,50%">   
        <frame src="introduction.htm">   
        <frame src="XbapEx.xbap">   
    </frameset>   
</html>  
```  
  
### <a name="clearing-cached-xbaps"></a>清除快取 XBAP  
 在某些情況下，重新建置並啟動您的 XBAP 之後，您可能會發現舊版 XBAP 開啟。 例如，當 XBAP 組件版本號碼是靜態的，且您從命令列啟動 XBAP 時，可能會發生這種行為。 在此情況下，因為快取版本 (先前已啟動的版本) 與新版本之間的版本號碼維持不變，所以不會下載新版本的 XBAP。 相反地，會載入快取版本。  
  
 在這些情況下，您可以藉由移除快取的版本**Mage**命令 （與 Visual Studio 或 Windows SDK 一起安裝），在命令提示字元。 下列命令會清除應用程式快取。  
  
 ```console
 Mage.exe -cc
 ```
  
 此命令可確保啟動最新版本的 XBAP。 當您偵錯您的應用程式，在 Visual Studio 中時，應該會啟動最新版本的 XBAP。 一般而言，您應該以每個組建更新您的部署版本號碼。 如需 Mage 的詳細資訊，請參閱 [Mage.exe (資訊清單產生和編輯工具)](../../tools/mage-exe-manifest-generation-and-editing-tool.md)。  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a>與主機網頁通訊  
 當應用程式裝載在 HTML 框架中時，您可以與包含 XBAP 的網頁進行通訊。 您可以擷取<xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A>屬性<xref:System.Windows.Interop.BrowserInteropHelper>。 這個屬性會傳回代表 HTML 視窗的指令碼物件。 您接著可以使用一般 dot 語法，在[視窗物件](https://go.microsoft.com/fwlink/?LinkId=160274)上存取屬性、方法和事件。 您也可以存取指令碼方法和全域變數。 下列範例示範如何擷取指令碼物件，並且關閉瀏覽器。  
  
 [!code-csharp[XbapBrowserInterop#10](~/samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a>針對使用 HostScript 的 XBAP 進行偵錯  
 如果您的 XBAP 使用<xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A>通訊 [HTML] 視窗中，有兩個設定，您必須指定執行和偵錯 Visual Studio 中的應用程式的物件。 應用程式必須能夠存取它的來源網站，而且您必須使用包含 XBAP 的 HTML 網頁來啟動應用程式。 下列步驟說明如何檢查這兩項設定︰  
  
1. 在 Visual Studio 中，開啟專案屬性。  
  
2. 在 [安全性]  索引標籤上，按一下 [進階]  。  
  
     [進階安全性設定] 對話方塊隨即出現。  
  
3. 請確定 [允許應用程式存取它的來源網站]  核取方塊已勾選，然後按一下 [確定]  。  
  
4. 在 [偵錯]  索引標籤上，選取 [瀏覽器起始 URL]  選項，並且指定包含 XBAP 之 HTML 網頁的 URL。  
  
5. 在 Internet Explorer 中，按一下 [工具]  按鈕，然後選取 [網際網路選項]  。  
  
     [網際網路選項] 對話方塊隨即出現。  
  
6. 按一下 [進階]  按鈕。  
  
7. 在 [安全性]  底下的 [設定]  清單中，勾選 [允許檔案中的主動式內容在我的電腦上執行]  核取方塊。  
  
8. 按一下 [確定]  。  
  
     變更在重新啟動 Internet Explorer 之後才會生效。  
  
> [!CAUTION]
>  在 Internet Explorer 中啟用主動式內容可能會讓電腦面臨風險。 如果您不要變更 Internet Explorer 安全性設定，您可以啟動從伺服器 HTML 網頁，並將 Visual Studio 偵錯工具附加至處理程序。  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a>XBAP 安全性考量  
 XBAP 通常會在部分信任安全性沙箱中執行，它限制為網際網路區域權限集合。 因此，您的實作必須支援的支援在網際網路區域中的 WPF 項目子集，或您必須提高您的應用程式的權限。 如需詳細資訊，請參閱[安全性](../security-wpf.md)。  
  
 當您使用<xref:System.Windows.Controls.WebBrowser>應用程式中，WPF 控制項在內部具現化原生 WebBrowser ActiveX 控制項。 當您的應用程式是在 Internet Explorer 中執行的部分信任 XBAP 時，ActiveX 控制項會在 Internet Explorer 流程的專用執行緒中執行。 因此，會套用下列限制：  
  
- <xref:System.Windows.Controls.WebBrowser>控制項應該提供類似主機瀏覽器，包括安全性限制的行為。 其中一些安全性限制可以透過 Internet Explorer 安全性設定來控制。 如需詳細資訊，請參閱[安全性](../security-wpf.md)。  
  
- 當 XBAP 在 HTML 網頁跨網域載入時，則會擲回例外狀況。  
  
- 輸入是來自 WPF 的另一個執行緒上<xref:System.Windows.Controls.WebBrowser>，因此無法攔截鍵盤輸入，並不會共用 IME 狀態。  
  
- 因為在另一個執行緒上執行的 ActiveX 控制項，瀏覽的時間或順序可能不同。 例如，瀏覽至頁面不一定會因為啟動另一個瀏覽要求而取消。  
  
- 自訂 ActiveX 控制項可能會遇到通訊問題，因為 WPF 應用程式是在個別執行緒中執行。  
  
- <xref:System.Windows.Interop.HwndHost.MessageHook> 不會引發，因為<xref:System.Windows.Interop.HwndHost>無法在另一個執行緒或處理序中執行的視窗的子類別。  
  
### <a name="creating-a-full-trust-xbap"></a>建立完全信任 XBAP  
 如果您的 XBAP 需要完全信任，您可以變更專案以啟用此權限。 下列步驟描述如何啟用完全信任︰  
  
1. 在 Visual Studio 中，開啟專案屬性。  
  
2. 在 [安全性]  索引標籤上，選取 [這是完全信任的應用程式]  選項。  
  
 這項設定會進行下列變更︰  
  
- 在專案檔中，`<TargetZone>` 元素值變更為 `Custom`。  
  
- 在 應用程式資訊清單 (app.manifest) 中，`Unrestricted="true"`屬性新增至 '<xref:System.Security.PermissionSet>項目。  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a>部署完全信任 XBAP  
 當您部署未遵循 ClickOnce 受信任部署模型的完全信任 XBAP 時，使用者執行應用程式時的行為將取決於安全性區域。 在某些情況下，使用者會在嘗試安裝它時收到一則警告。 使用者可以選擇繼續或取消安裝。 下表描述每個安全性區域的應用程式行為，以及您必須針對應用程式執行什麼動作才能得到完全信任。  
  
|安全性區域|行為|取得完全信任|  
|-------------------|--------------|------------------------|  
|本機電腦|自動的完全信任|不需要採取任何動作。|  
|內部網路和信任的網站|完全信任的提示|使用憑證簽署 XBAP，讓使用者在提示中看到來源。|  
|網際網路|因為「未授與信任」而失敗|使用憑證簽署 XBAP。|  
  
> [!NOTE]
>  上表中描述的行為是針對未遵循 ClickOnce 受信任部署模型的完全信任 XBAP。  
  
 建議您使用 ClickOnce 受信任部署模型來部署完全信任 XBAP。 此模型可讓您的 XBAP 自動授與完全信任，無論安全性區域為何，因此系統不會提示使用者。 做為此模型的一部分，您必須使用受信任發行者的憑證來簽署應用程式。 如需詳細資訊，請參閱[受信任應用程式部署概觀](/visualstudio/deployment/trusted-application-deployment-overview)和[程式碼簽署簡介](https://go.microsoft.com/fwlink/?LinkId=166327)。  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a>XBAP 開始時間效能考量  
 XBAP 效能很重要的層面是其開始時間。 如果 XBAP 是載入的第一個 WPF 應用程式，「冷啟動」  時間可以是 10 秒或以上。 這是因為進度頁面是由 WPF 轉譯，且 CLR 和 WPF 必須冷啟動來顯示應用程式。  
  
 從.NET Framework 3.5 SP1 開始，您可以在部署週期早期顯示 unmanaged 的進度頁面降低 XBAP 冷啟動時間。 進度頁面幾乎是在應用程式啟動之後立即出現，因為它是由原生裝載程式碼顯示，並且以 HTML 轉譯。  
  
 此外，ClickOnce 下載順序的改善的並行會改善最多 10%的開始時間。 ClickOnce 下載和驗證之後資訊清單、 應用程式的下載會啟動，而進度列開始更新。  
  
## <a name="see-also"></a>另請參閱

- [設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務](configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)
- [部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)
