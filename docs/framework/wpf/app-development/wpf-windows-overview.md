---
title: 視窗概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145536"
---
# <a name="wpf-windows-overview"></a>WPF 視窗概觀
使用者通過視窗與 Windows 演示基礎 （WPF） 獨立應用程式進行交互。 視窗的主要用途是裝載內容，以視覺化方式檢視資料，並讓使用者可以與資料互動。 獨立 WPF 應用程式通過使用<xref:System.Windows.Window>類提供自己的視窗。 本主題在<xref:System.Windows.Window>介紹在獨立應用程式中創建和管理視窗的基礎知識之前介紹。  
  
> [!NOTE]
> 瀏覽器託管的 WPF 應用程式（包括 XAML 瀏覽器應用程式 （XBAP） 和鬆散[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]頁面）不提供自己的視窗。 相反，它們託管在 Windows Internet 資源管理器提供的視窗中。 請參閱[WPF XAML 瀏覽器應用程式概述](wpf-xaml-browser-applications-overview.md)。  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>Window 類別  
 下圖說明瞭視窗的組成部分：  
  
 ![顯示視窗元素的螢幕截圖。](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 視窗分為兩個區域︰非工作區和工作區。  
  
 視窗*的非工作區*由 WPF 實現，包括大多數視窗共有的視窗部分，包括以下內容：  
  
- 框線。  
  
- 標題列。  
  
- 圖示。  
  
- [最小化]、[最大化] 和 [還原] 按鈕。  
  
- [關閉] 按鈕。  
  
- [系統] 功能表，具有允許使用者最小化、最大化、還原、移動、調整大小和關閉視窗的功能表項目。  
  
 視窗的*工作區*是視窗非工作區中的區域，開發人員使用 它添加特定于應用程式的內容，如功能表列、工具列和控制項。  
  
 在 WPF 中，視窗由用於執行<xref:System.Windows.Window>以下操作的類封裝：  
  
- 顯示視窗。  
  
- 設定視窗的大小、位置和外觀。  
  
- 裝載應用程式特定內容。  
  
- 管理視窗的存留期。  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>實作視窗  
 典型視窗的實現包括外觀和行為，其中*外觀*定義視窗對使用者的外觀，*行為*定義視窗在使用者與其交互時的工作方式。 在 WPF 中，可以使用代碼或[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記實現視窗的外觀和行為。  
  
 但是，通常情況下，視窗的外觀使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記實現，並且其行為使用代碼後面實現，如下例所示。  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 要使[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記檔和代碼後面檔協同工作，需要：  
  
- 在標記中，`Window`元素必須包括屬性。 `x:Class` 生成應用程式`x:Class`時，標記檔中的存在會導致 Microsoft 生成引擎 （MSBuild） 創建派生`partial`自<xref:System.Windows.Window>並具有`x:Class`屬性指定的名稱的類。 這需要為[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]架構添加 XML 命名空間聲明 （ `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` 。 生成的`partial`類實現方法`InitializeComponent`，該方法被調用以註冊事件並設置在標記中實現的屬性。  
  
- 在代碼後面，類必須是具有標記中屬性`partial`指定的相同名稱的`x:Class`類，並且必須派生自<xref:System.Windows.Window>。 這允許代碼背後的檔與生成應用程式時為標記檔生成的`partial`類相關聯（請參閱[構建 WPF 應用程式](building-a-wpf-application-wpf.md)）。  
  
- 在代碼後面，<xref:System.Windows.Window>類必須實現調用方法的`InitializeComponent`建構函式。 `InitializeComponent`由標記檔的生成`partial`類實現，以註冊事件並設置在標記中定義的屬性。  
  
> [!NOTE]
> 使用 Visual Studio<xref:System.Windows.Window>向專案添加新專案時，<xref:System.Windows.Window>將使用標記和代碼後面實現 ，並包括創建標記和代碼後面檔之間的關聯的必要配置，如此處所述。  
  
 有了此配置，您可以專注于在標記中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義視窗的外觀，並在代碼後面實現其行為。 下面的示例顯示了一個視窗，其中帶有一個按鈕[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，在標記中實現，並且在代碼後面實現該<xref:System.Windows.Controls.Primitives.ButtonBase.Click>按鈕事件的事件處理常式。  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>設定 MSBuild 的視窗定義  
 如何實現視窗決定了如何為 MSBuild 配置視窗。 對於使用標記[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和代碼後面定義的視窗：  
  
- XAML 標記檔配置為 MSBuild`Page`項。  
  
- 代碼背後的檔配置為 MSBuild`Compile`項。  
  
 這顯示在以下 MSBuild 專案檔案中。  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 有關構建 WPF 應用程式的資訊，請參閱[構建 WPF 應用程式](building-a-wpf-application-wpf.md)。  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>視窗存留期  
 如同任何類別，視窗有存留期，會在它一開始具現化時開始，在那之後它會被開啟、啟動和停用，並最終關閉。  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>開啟視窗  
 若要開啟視窗，您要先建立它的執行個體，如下列範例中示範。  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 在此示例中，應用程式啟動時`MarkupAndCodeBehindWindow`具現化，在引發<xref:System.Windows.Application.Startup>事件時發生具現化。  
  
 具現化視窗時，對視窗的引用將自動添加到由<xref:System.Windows.Application>物件管理的視窗清單中（請參閱<xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>）。 此外，預設情況下，要具現化的第一個視窗<xref:System.Windows.Application>設置為主應用程式視窗（請參閱<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>）。  
  
 最後通過調用<xref:System.Windows.Window.Show%2A>方法打開視窗;結果如下圖所示。  
  
 ![通過調用視窗打開的視窗。](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 通過調用<xref:System.Windows.Window.Show%2A>打開的視窗是一個無強制回應視窗，這意味著應用程式以允許使用者在同一應用程式中啟動其他視窗的模式運行。  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>調用 以以模式方式打開視窗，如對話方塊。 有關詳細資訊，請參閱[對話方塊概述](dialog-boxes-overview.md)。  
  
 調用<xref:System.Windows.Window.Show%2A>時，視窗在顯示建立基礎結構以允許其接收使用者輸入之前執行初始化工作。 初始化視窗時，<xref:System.Windows.Window.SourceInitialized>將引發事件並顯示視窗。  
  
 作為快捷方式，<xref:System.Windows.Application.StartupUri%2A>可以設置為指定應用程式啟動時自動打開的第一個視窗。  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 應用程式啟動時，由 的值<xref:System.Windows.Application.StartupUri%2A>指定的視窗將無模式打開;在內部，視窗通過調用其<xref:System.Windows.Window.Show%2A>方法打開。  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>視窗擁有權  
 使用<xref:System.Windows.Window.Show%2A>方法打開的視窗與創建它的視窗沒有隱式關係;因此，使用 方法打開的視窗與創建它的視窗沒有隱式關係。使用者可以獨立于另一個視窗與任一視窗進行交互，這意味著任一視窗都可以執行以下操作：  
  
- 蓋住另一個視窗（除非其中一個視窗<xref:System.Windows.Window.Topmost%2A>的屬性設置為`true`）。  
  
- 最小化、最大化和還原而不會影響對方。  
  
 某些視窗需要與開啟它們的視窗有關聯性。 例如，整合式開發環境 （IDE） 應用程式可能會打開屬性視窗和工具視窗，其典型行為是覆蓋創建它們的視窗。 此外，這類視窗應該一律與建立它們的視窗一致地關閉、最小化、最大化和還原。 這種關係可以通過使一個視窗*擁有*另一個視窗來建立，並且通過使用擁有者<xref:System.Windows.Window.Owner%2A>*視窗*來設置*擁有的視窗*的屬性來實現。 下列範例會顯示這一點。  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 建立擁有權之後︰  
  
- 擁有的視窗可以通過檢查其屬性的值來引用其<xref:System.Windows.Window.Owner%2A>擁有者視窗。  
  
- 擁有者視窗可以通過檢查其<xref:System.Windows.Window.OwnedWindows%2A>屬性的值來發現它擁有的所有視窗。  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>避免視窗啟動  
 在某些情況下，在顯示時不應啟動視窗，例如 Internet 信使式應用程式的交談視窗或電子郵件應用程式的通知視窗。  
  
 如果應用程式的視窗在顯示時不應啟動，則可以在首次調用<xref:System.Windows.Window.ShowActivated%2A>`false`<xref:System.Windows.Window.Show%2A>該方法之前將其屬性設置為 。 因此：  
  
- 未啟動視窗。  
  
- 不會引發視窗的事件<xref:System.Windows.Window.Activated>。  
  
- 目前已啟動的視窗會保持已啟動。  
  
 不過，當使用者按一下工作區或非工作區來啟動它時，視窗將會啟動。 在此案例中：  
  
- 視窗已啟動。  
  
- 引發視窗的事件<xref:System.Windows.Window.Activated>。  
  
- 先前已啟動的視窗已停用。  
  
- 視窗<xref:System.Windows.Window.Deactivated>和<xref:System.Windows.Window.Activated>事件隨後按預期引發，以回應使用者操作。  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>視窗啟動  
 首次打開視窗時，它將成為使用中視窗（除非將其顯示為<xref:System.Windows.Window.ShowActivated%2A>）。 `false` *使用中視窗*是當前捕獲使用者輸入的視窗，例如擊鍵和滑鼠按一下。 當視窗變為活動狀態時，它會引發<xref:System.Windows.Window.Activated>事件。  
  
> [!NOTE]
> 首次打開視窗時，僅在引發<xref:System.Windows.FrameworkElement.Loaded><xref:System.Windows.Window.ContentRendered><xref:System.Windows.Window.Activated>事件後引發 和 事件。 考慮到這一點，在提出時<xref:System.Windows.Window.ContentRendered>，可以有效地考慮打開一個視窗。  
  
 視窗成為使用中之後，使用者可以在相同應用程式中啟動另一個視窗，或啟動另一個應用程式。 發生這種情況時，當前使用中視窗將停用並引發事件<xref:System.Windows.Window.Deactivated>。 同樣，當使用者選擇當前停用的視窗時，該視窗將再次變為活動狀態並<xref:System.Windows.Window.Activated>引發。  
  
 處理<xref:System.Windows.Window.Activated><xref:System.Windows.Window.Deactivated>的一個常見原因是啟用和禁用只能在視窗處於活動狀態時運行的功能。 例如，某些視窗顯示需要使用者持續輸入和注意的互動式內容，包括遊戲和視訊播放程式。 下面的示例是一個簡化的視頻播放機，演示如何處理<xref:System.Windows.Window.Activated>和<xref:System.Windows.Window.Deactivated>實現此行為。  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 當視窗已停用時，其他應用程式類型仍然可能會在背景中執行程式碼。 例如，當使用者使用其他應用程式時，郵件用戶端可能會繼續輪詢郵件伺服器。 這類應用程式在主視窗已停用時，通常會提供不同或其他行為。 對於郵件程式，這可能表示同時將新的郵件項目加入收件匣，並將通知圖示加入系統匣。 僅當郵件視窗不處於活動狀態時，才需要顯示通知圖示，可以通過檢查<xref:System.Windows.Window.IsActive%2A>屬性來確定該圖示。  
  
 如果背景工作完成，視窗可能需要通過調用<xref:System.Windows.Window.Activate%2A>方法更緊急地通知使用者。 如果使用者正在與調用時<xref:System.Windows.Window.Activate%2A>啟動的另一個應用程式交互，則視窗的工作列按鈕將閃爍。 如果使用者正在與當前應用程式交互，則調用<xref:System.Windows.Window.Activate%2A>會將視窗帶到前臺。  
  
> [!NOTE]
> 您可以使用 和<xref:System.Windows.Application.Activated?displayProperty=nameWithType><xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>事件處理應用程式範圍啟動。  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a>關閉視窗  
 視窗的存留期在使用者關閉它時開始進入尾聲。 視窗可以使用非工作區中的項目關閉，包括下列項目︰  
  
- **"關閉"功能表**的 **"關閉**"項。  
  
- 按下 ALT+F4。  
  
- 按 **"關閉"** 按鈕。  
  
 您可以提供其他機制讓工作區關閉視窗，較常見的包括下列各項︰  
  
- **"檔**"功能表中的**退出**項，通常用於主應用程式視窗。  
  
- **"檔**"功能表中的**Close**項，通常在輔助應用程式視窗中。  
  
- **取消**按鈕，通常在強制回應對話方塊上。  
  
- **關閉**按鈕，通常在無強制回應對話方塊上。  
  
 要關閉視窗以回應這些自訂機制之一，您需要調用 方法<xref:System.Windows.Window.Close%2A>。 以下示例通過選擇 **"檔**"功能表上的 **"退出**"來實現關閉視窗的能力。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 當視窗關閉時，它將引發兩個事件： <xref:System.Windows.Window.Closing> <xref:System.Windows.Window.Closed>和 。  
  
 <xref:System.Windows.Window.Closing>在視窗關閉之前引發，它提供了一種機制，可以阻止視窗關閉。 防止視窗關閉的一個常見原因，是視窗內容包含已修改的資料。 在此情況下，<xref:System.Windows.Window.Closing>可以處理事件以確定資料是否髒，如果是，則詢問使用者是繼續關閉視窗而不保存資料，還是取消視窗關閉。 下面的示例顯示了處理<xref:System.Windows.Window.Closing>的關鍵方面。  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 事件<xref:System.Windows.Window.Closing>處理常式傳遞 一個<xref:System.ComponentModel.CancelEventArgs>，它實現`Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>設置為`true`防止視窗關閉的屬性。  
  
 如果未<xref:System.Windows.Window.Closing>處理，或者處理但未取消，視窗將關閉。 就在視窗實際關閉之前，<xref:System.Windows.Window.Closed>正在引發。 此時無法防止視窗關閉。  
  
> [!NOTE]
> 可以將應用程式佈建為在主應用程式視窗關閉（請參閱<xref:System.Windows.Application.MainWindow%2A>）或最後一個視窗關閉時自動關閉。 如需詳細資訊，請參閱<xref:System.Windows.Application.ShutdownMode%2A>。  
  
 雖然可以通過非用戶端和工作區中提供的機制顯式關閉視窗，但視窗也可以由於應用程式或 Windows 的其他部分的行為而隱式關閉，包括：  
  
- 使用者登出或關閉 Windows。  
  
- 視窗的擁有者關閉（請參閱<xref:System.Windows.Window.Owner%2A>）。  
  
- 主應用程式視窗已關閉，並且<xref:System.Windows.Application.ShutdownMode%2A>為<xref:System.Windows.ShutdownMode.OnMainWindowClose>。  
  
- 呼叫 <xref:System.Windows.Application.Shutdown%2A>。  
  
> [!NOTE]
> 在關閉之後就無法重新開啟視窗。  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>視窗存留期事件  
 下圖顯示了視窗存留期內主體事件的順序：  
  
 ![顯示視窗存留期內的事件的圖表。](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 下圖顯示了不啟動的情況下顯示的視窗存留期內主體事件的順序（<xref:System.Windows.Window.ShowActivated%2A>設置為`false`在顯示視窗之前）：  
  
 ![顯示視窗存留期內的事件而不啟動的圖表。](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>視窗位置  
 視窗開啟時，它會有相對於桌面的 x 和 y 維度位置。 此位置可以通過分別檢查 和<xref:System.Windows.Window.Left%2A><xref:System.Windows.Window.Top%2A>屬性來確定。 您可以設定這些屬性，以變更視窗的位置。  
  
 還可以通過使用以下<xref:System.Windows.Window><xref:System.Windows.Window.WindowStartupLocation%2A><xref:System.Windows.WindowStartupLocation>枚舉值之一設置屬性來指定首次出現 時的初始位置：  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (預設值)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 如果啟動位置<xref:System.Windows.WindowStartupLocation.Manual>指定為 ，並且 尚未<xref:System.Windows.Window.Left%2A>設置<xref:System.Windows.Window.Top%2A>和 屬性，<xref:System.Windows.Window>則請求 Windows 顯示位置。  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>最上層視窗和疊置順序  
 除了有 x 和 y 位置，視窗也有 z 維度的位置，這決定了它相對於其他視窗的垂直位置。 這稱為視窗的疊置順序，並且有兩種類型︰一般疊置順序和最上層疊置順序。 視窗在正常*z 順序*中的位置由視窗當前是否處於活動狀態決定。 根據預設，視窗位於一般疊置順序。 視窗在*最頂層 z 順序*中的位置也取決於視窗當前是否處於活動狀態。 此外，最上層疊置順序的視窗一定會位於一般疊置順序的視窗之上。 視窗通過將屬性<xref:System.Windows.Window.Topmost%2A>設置為`true`位於最上面的 z 順序中。  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 在每個疊置順序內，目前使用中視窗會顯示在相同疊置順序中的所有其他視窗之上。  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>視窗大小  
 除了具有桌面位置外，視窗的大小由多個屬性確定，包括各種寬度和高度屬性和<xref:System.Windows.Window.SizeToContent%2A>。  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A><xref:System.Windows.FrameworkElement.Width%2A>，<xref:System.Windows.FrameworkElement.MaxWidth%2A>用於管理視窗在其存留期內可以具有的寬度範圍，並配置如下示例所示。  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 視窗高度由<xref:System.Windows.FrameworkElement.MinHeight%2A><xref:System.Windows.FrameworkElement.Height%2A>和 和<xref:System.Windows.FrameworkElement.MaxHeight%2A>進行管理，並配置如下示例所示。  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 因為各種寬度值和高度值都各指定一個範圍，所以可調整大小視窗的高度與寬度可能會是個別維度的指定範圍內的任何位置。 要檢測其當前寬度和高度，分別<xref:System.Windows.FrameworkElement.ActualWidth%2A>檢查<xref:System.Windows.FrameworkElement.ActualHeight%2A>和 。  
  
 如果希望視窗的寬度和高度具有適合視窗內容大小的大小，則可以使用 具有以下值<xref:System.Windows.Window.SizeToContent%2A>的屬性：  
  
- <xref:System.Windows.SizeToContent.Manual>. 無效果 (預設值)。  
  
- <xref:System.Windows.SizeToContent.Width>. 適合內容寬度，其效果與設置內容<xref:System.Windows.FrameworkElement.MinWidth%2A>和<xref:System.Windows.FrameworkElement.MaxWidth%2A>內容寬度的效果相同。  
  
- <xref:System.Windows.SizeToContent.Height>. 適合內容高度，這與設置內容<xref:System.Windows.FrameworkElement.MinHeight%2A>的高度和<xref:System.Windows.FrameworkElement.MaxHeight%2A>內容的高度具有相同的效果。  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. 適合內容<xref:System.Windows.FrameworkElement.MinHeight%2A>寬度和高度，其效果與設置內容的高度以及<xref:System.Windows.FrameworkElement.MaxHeight%2A>設置內容<xref:System.Windows.FrameworkElement.MinWidth%2A>的寬度和<xref:System.Windows.FrameworkElement.MaxWidth%2A>寬度的效果相同。  
  
 下列範例顯示自動調整垂直和水平大小以符合其內容的視窗，第一次顯示時的樣子。  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 下面的示例演示如何在代碼中設置<xref:System.Windows.Window.SizeToContent%2A>屬性以指定視窗如何調整大小以適合其內容。
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>調整大小屬性優先順序  
 基本上，視窗的各種大小屬性會合併起來定義可調整大小的視窗的寬度和高度範圍。 為確保保持有效範圍，<xref:System.Windows.Window>請使用以下優先順序順序計算大小屬性的值。  
  
 **針對高度屬性：**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **針對寬度屬性：**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 優先順序順序還可以確定視窗在最大化時的大小，該視窗使用<xref:System.Windows.Window.WindowState%2A>屬性進行管理。  
  
<a name="WindowState"></a>
## <a name="window-state"></a>視窗狀態  
 在可調整大小的視窗存留期中，它可以有三種狀態︰標準、最小化及最大化。 具有*正常*狀態的視窗是視窗的預設狀態。 這種狀態的視窗可以讓使用者移動並使用調整大小底框或框線調整其大小，如果它可調整大小。  
  
 具有*最小化*狀態的視窗將折疊到其工作列按鈕（如果<xref:System.Windows.Window.ShowInTaskbar%2A>設置為`true`;否則，它會折疊到盡可能小的大小，並重新置放到桌面的左下角。 最小化視窗的類型都無法使用框線或調整大小底框來調整大小，雖然未顯示在工作列中的最小化視窗可以在桌面拖曳。  
  
 具有*最大化*狀態的視窗將擴展到其可以的最大大小，該大小將僅與其<xref:System.Windows.FrameworkElement.MaxWidth%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>和<xref:System.Windows.Window.SizeToContent%2A>屬性規定的大小一樣大。 就像最小化的視窗，最大化的視窗無法使用調整大小底框或藉由拖曳框線來調整大小。  
  
> [!NOTE]
> <xref:System.Windows.Window.Top%2A>視窗的值<xref:System.Windows.Window.Left%2A><xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性始終表示正常狀態的值，即使視窗當前正在最大化或最小化也是如此。  
  
 可以通過設置其<xref:System.Windows.Window.WindowState%2A>屬性來配置視窗的狀態，該屬性可以具有以下<xref:System.Windows.WindowState>枚舉值之一：  
  
- <xref:System.Windows.WindowState.Normal> (預設值)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 下列範例示範如何建立在開啟時會顯示為最大化的視窗。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 通常，應設置為<xref:System.Windows.Window.WindowState%2A>配置視窗的初始狀態。 可調整大小的視窗顯示後，使用者可以按下視窗標題列上的最小化、最大化和還原按鈕，以變更視窗狀態。  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>視窗外觀  
 您可以新增視窗特定的內容，例如按鈕、標籤和文字方塊，來變更視窗工作區的外觀。 要配置非工作區，<xref:System.Windows.Window>請提供多個屬性，其中包括<xref:System.Windows.Window.Icon%2A>設置視窗的圖示並<xref:System.Windows.Window.Title%2A>設置其標題。  
  
 您也可以藉由設定視窗的調整大小模式、視窗樣式，以及它是否顯示為桌面工作列上的按鈕，變更非工作區框線的外觀和行為。  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>調整大小模式  
 根據屬性，<xref:System.Windows.Window.WindowStyle%2A>您可以控制使用者調整視窗大小的方式（以及是否）大小。 視窗樣式的選擇會影響使用者是否可以通過拖動視窗與滑鼠的邊框來調整視窗的大小，是否在非工作區上顯示 **"最小化**"、**最大化**和**調整大小**按鈕，如果確實出現，則是否啟用了這些按鈕。  
  
 您可以通過設置視窗<xref:System.Windows.Window.ResizeMode%2A>的屬性（可以是以下<xref:System.Windows.ResizeMode>枚舉值之一）來配置視窗的大小大小：  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (預設值)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 與<xref:System.Windows.Window.WindowStyle%2A>，視窗的調整大小模式在其存留期內不太可能更改，這意味著您很可能從[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記中設置它。  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 請注意，您可以通過檢查<xref:System.Windows.Window.WindowState%2A>屬性來檢測視窗是最大化、最小化還是還原。  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>視窗樣式  
 從視窗非工作區公開的框線適用於大部分的應用程式。 不過，有一些情況下需要不同型別的框線，或是完全不需要框線，視視窗的型別而定。  
  
 要控制視窗獲取的邊框類型，您需要使用枚<xref:System.Windows.Window.WindowStyle%2A><xref:System.Windows.WindowStyle>舉的以下值之一設置其屬性：  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (預設值)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 下圖說明瞭這些視窗樣式的效果：  
  
 ![視窗邊框樣式的插圖。](./media/wpf-windows-overview/window-border-styles.png)  
  
 您可以使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記或<xref:System.Windows.Window.WindowStyle%2A>代碼進行設置;因為它不太可能在視窗的存留期內更改，因此您很可能使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記來配置它。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>非矩形視窗樣式  
 還在某些情況下，<xref:System.Windows.Window.WindowStyle%2A>允許您擁有的邊界樣式是不夠的。 例如，您可能希望創建具有非矩形邊框的應用程式，如 Microsoft Windows 媒體播放機使用。  
  
 例如，請考慮下圖中顯示的語音氣泡視窗：  
  
 ![一個語音氣泡視窗，上面寫著"拖動我"。](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 可以通過將<xref:System.Windows.Window.WindowStyle%2A>屬性設置為<xref:System.Windows.WindowStyle.None>和 使用<xref:System.Windows.Window>具有透明度的特殊支援來創建這種類型的視窗。  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 這些值的組合會指示視窗要轉譯為完全透明。 在此狀態下，無法使用視窗的非工作區裝飾 ([關閉] 功能表、[最小化]、[最大化] 和 [還原] 按鈕等等)。 因此，您需要自行提供。  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>工作列目前狀態  

視窗的預設面板包括工作列按鈕，如圖所示：

 ![顯示帶有工作列按鈕的視窗的螢幕截圖。](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 某些類型的視窗沒有工作列按鈕，如訊息方塊和對話方塊（請參閱[對話方塊概述](dialog-boxes-overview.md)）。 您可以通過設置<xref:System.Windows.Window.ShowInTaskbar%2A>屬性（預設情況下）`true`來控制視窗的工作列按鈕是否顯示。  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>安全性考量  
 <xref:System.Windows.Window>需要`UnmanagedCode`具現化安全許可權。 對於本機電腦上安裝和啟動的應用程式，這落在授與給該應用程式的權限集範圍內。  
  
 但是，這不屬於使用 ClickOnce 從 Internet 或本地 Intranet 區域啟動的應用程式授予的許可權集。 因此，使用者將收到 ClickOnce 安全警告，並且需要將應用程式的許可權集提升為完全信任。  
  
 此外，預設情況下，XBAP 不能顯示視窗或對話方塊。 有關獨立應用程式安全注意事項的討論，請參閱[WPF 安全性原則 - 平臺安全](../wpf-security-strategy-platform-security.md)。  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>其他類型的視窗  
 <xref:System.Windows.Navigation.NavigationWindow>是一個視窗，旨在承載可導航內容。 有關詳細資訊，請參閱[導航概述](navigation-overview.md)。  
  
 對話方塊是經常用來從使用者收集資訊以完成一項功能的視窗。 例如，當使用者想要打開檔時，"**打開檔"** 對話方塊通常由應用程式顯示，以便從使用者獲取檔案名。 如需詳細資訊，請參閱[對話方塊概觀](dialog-boxes-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [對話方塊概觀](dialog-boxes-overview.md)
- [建置 WPF 應用程式](building-a-wpf-application-wpf.md)
