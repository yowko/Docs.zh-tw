---
title: WPF 視窗概觀
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
ms.openlocfilehash: 16f4155cefea20868185febb3d2a566dc1524cc4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956277"
---
# <a name="wpf-windows-overview"></a>WPF 視窗概觀
使用者透過 Windows 與 Windows Presentation Foundation (WPF) 獨立應用程式互動。 視窗的主要用途是裝載內容，以視覺化方式檢視資料，並讓使用者可以與資料互動。 獨立[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式會<xref:System.Windows.Window>使用類別來提供自己的視窗。 本主題將<xref:System.Windows.Window>介紹在獨立應用程式中建立和管理 windows 的基本概念。  
  
> [!NOTE]
> 瀏覽器裝載[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]的應用程式[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] (包括[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]和鬆散頁面) 不會提供自己的視窗。 相反地, 它們是裝載于 Windows Internet Explorer 所提供的 windows 中。 請參閱[WPF XAML 瀏覽器應用程式總覽](wpf-xaml-browser-applications-overview.md)。  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Window 類別  
 下圖說明視窗的構成部分:  
  
 ![顯示視窗元素的螢幕擷取畫面。](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 視窗分為兩個區域︰非工作區和工作區。  
  
 視窗的*非工作區*是由[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]所執行, 並包含大部分視窗通用的視窗部分, 包括下列各項:  
  
- 框線。  
  
- 標題列。  
  
- 圖示。  
  
- [最小化]、[最大化] 和 [還原] 按鈕。  
  
- [關閉] 按鈕。  
  
- [系統] 功能表，具有允許使用者最小化、最大化、還原、移動、調整大小和關閉視窗的功能表項目。  
  
 視窗的*工作區*是在視窗的非工作區中的區域, 開發人員會使用它來新增應用程式特定的內容, 例如功能表列、工具列和控制項。  
  
 在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中, 視窗是<xref:System.Windows.Window>由您用來執行下列動作的類別所封裝:  
  
- 顯示視窗。  
  
- 設定視窗的大小、位置和外觀。  
  
- 裝載應用程式特定內容。  
  
- 管理視窗的存留期。  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>實作視窗  
 一般視窗的執行包含外觀和行為, 其中的*外觀*會定義視窗外觀給使用者的方式, 而*行為*會定義視窗功能與使用者互動的方式。 在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中, 您可以使用程式碼或[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記來執行視窗的外觀和行為。  
  
 不過, 一般情況下, 視窗的外觀會使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記來執行, 而且其行為會使用程式碼後置來執行, 如下列範例所示。  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 若要讓[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記檔和程式碼後置檔案一起工作, 需要下列各項:  
  
- 在標記中, `Window`元素必須`x:Class`包含屬性。 建立應用程式時`x:Class` , 標記檔案中的存在會導致 Microsoft build engine (MSBuild) `partial`建立衍生自<xref:System.Windows.Window>的類別, 並`x:Class`具有屬性所指定的名稱。 這需要新增[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]架構的命名空間宣告 ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` )。 產生`partial`的類別`InitializeComponent`會執行方法, 其會呼叫來註冊事件並設定在標記中執行的屬性。  
  
- 在程式碼後置中, 類別必須是`partial`具有與標記中的`x:Class`屬性所指定相同名稱的類別, 而且必須衍生自<xref:System.Windows.Window>。 這可讓程式碼後置檔案與`partial`建立應用程式時為標記檔案產生的類別相關聯 (請參閱[建立 WPF 應用程式](building-a-wpf-application-wpf.md))。  
  
- 在程式碼後置中<xref:System.Windows.Window> , 類別必須執行`InitializeComponent`呼叫方法的函式。 `InitializeComponent`會由標記檔案產生`partial`的類別來執行, 以註冊事件並設定在標記中定義的屬性。  
  
> [!NOTE]
> 當您使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]將新<xref:System.Windows.Window>的新增至專案時, <xref:System.Windows.Window>會使用標記和程式碼後置來實作為, 並包含必要的設定來建立標記和程式碼後置檔案之間的關聯, 如下所示:此處所述。  
  
 設定好此設定之後, 您可以專注于在標記中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義視窗的外觀, 並在程式碼後置中執行其行為。 下列範例會顯示一個視窗, 其中包含按鈕、在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記中實作為, 以及<xref:System.Windows.Controls.Primitives.ButtonBase.Click>按鈕事件的事件處理常式 (在程式碼後置中執行)。  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>設定 MSBuild 的視窗定義  
 您在視窗中的執行方式會決定如何設定 MSBuild。 針對使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記和程式碼後置定義的視窗:  
  
- XAML 標記檔案會設定為 MSBuild `Page`專案。  
  
- 程式碼後置檔案會設定為`Compile` MSBuild 專案。  
  
 這會顯示在下列 MSBuild 專案檔中。  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 如需建立[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式的相關資訊, 請參閱[建立 WPF 應用程式](building-a-wpf-application-wpf.md)。  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>視窗存留期  
 如同任何類別，視窗有存留期，會在它一開始具現化時開始，在那之後它會被開啟、啟動和停用，並最終關閉。  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>開啟視窗  
 若要開啟視窗，您要先建立它的執行個體，如下列範例中示範。  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 在此範例中, `MarkupAndCodeBehindWindow`會在應用程式啟動時具現化, 這<xref:System.Windows.Application.Startup>會發生在引發事件時。  
  
 當視窗具現化時, 它的參考會自動加入至由<xref:System.Windows.Application>物件管理的視窗清單 (請參閱<xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>)。 此外, 根據預設, 第一個要具現化的視窗會設定<xref:System.Windows.Application>為主應用程式視窗 (請<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>參閱)。  
  
 視窗最後會藉由呼叫<xref:System.Windows.Window.Show%2A>方法來開啟, 而結果如下圖所示。  
  
 ![藉由呼叫 Window 開啟的視窗。顯示](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 藉由呼叫<xref:System.Windows.Window.Show%2A>開啟的視窗為非強制回應視窗, 這表示應用程式會以可讓使用者在相同應用程式中啟用其他視窗的模式運作。  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>呼叫來以模式開啟視窗, 例如對話方塊。 如需詳細資訊, 請參閱[對話方塊總覽](dialog-boxes-overview.md)。  
  
 當<xref:System.Windows.Window.Show%2A>呼叫時, 視窗會先執行初始化工作, 然後才會顯示它, 以建立可讓它接收使用者輸入的基礎結構。 初始化視窗時, <xref:System.Windows.Window.SourceInitialized>會引發事件並顯示視窗。  
  
 做為快捷方式<xref:System.Windows.Application.StartupUri%2A> , 可以設定為指定在應用程式啟動時自動開啟的第一個視窗。  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 當應用程式啟動時, 值<xref:System.Windows.Application.StartupUri%2A>所指定的視窗會在方式中開啟; 在內部, 會藉由呼叫其<xref:System.Windows.Window.Show%2A>方法來開啟視窗。  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>視窗擁有權  
 使用<xref:System.Windows.Window.Show%2A>方法開啟的視窗與建立它的視窗沒有隱含關聯性; 使用者可以與任一視窗獨立互動, 這表示任一視窗都可以執行下列動作:  
  
- 涵蓋另一個 (除非其中一個視窗<xref:System.Windows.Window.Topmost%2A>的屬性設定為`true`)。  
  
- 最小化、最大化和還原而不會影響對方。  
  
 某些視窗需要與開啟它們的視窗有關聯性。 例如, 整合式開發環境 (IDE) 應用程式可能會開啟屬性視窗和工具視窗, 其一般行為是涵蓋建立它們的視窗。 此外，這類視窗應該一律與建立它們的視窗一致地關閉、最小化、最大化和還原。 這種關聯性可以藉由將一個視窗設為另一個來建立, 並藉<xref:System.Windows.Window.Owner%2A>由使用擁有者*視窗*的參考來設定*擁有視窗*的屬性來達成。 這在下列範例中顯示。  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 建立擁有權之後︰  
  
- 擁有的視窗可以藉由檢查其<xref:System.Windows.Window.Owner%2A>屬性的值來參考其擁有者視窗。  
  
- [擁有者] 視窗可以藉由檢查其<xref:System.Windows.Window.OwnedWindows%2A>屬性的值, 來探索所有 windows it 擁有的內容。  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>避免視窗啟動  
 在某些情況下, windows 不應在顯示時啟動, 例如網際網路 messenger 樣式應用程式的交談視窗或電子郵件應用程式的通知視窗。  
  
 如果您的應用程式具有不應在顯示時啟動的視窗, 您可以<xref:System.Windows.Window.ShowActivated%2A>在第`false`一次呼叫<xref:System.Windows.Window.Show%2A>方法之前, 將其屬性設定為。 因此：  
  
- 未啟動視窗。  
  
- 視窗的<xref:System.Windows.Window.Activated>事件不會引發。  
  
- 目前已啟動的視窗會保持已啟動。  
  
 不過，當使用者按一下工作區或非工作區來啟動它時，視窗將會啟動。 在此情況下：  
  
- 視窗已啟動。  
  
- 會引發視窗<xref:System.Windows.Window.Activated>的事件。  
  
- 先前已啟動的視窗已停用。  
  
- 接著, 視窗<xref:System.Windows.Window.Deactivated>的<xref:System.Windows.Window.Activated>和事件會如預期般引發, 以回應使用者動作。  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>視窗啟動  
 當視窗第一次開啟時, 它會變成作用中的視窗 (除非它<xref:System.Windows.Window.ShowActivated%2A>是以`false`設定為的顯示)。 *使用中視窗*是目前正在捕捉使用者輸入的視窗, 例如按鍵筆劃和滑鼠點擊。 當視窗變成作用中狀態時, 它<xref:System.Windows.Window.Activated>會引發事件。  
  
> [!NOTE]
> 當第一次開啟視窗時, <xref:System.Windows.FrameworkElement.Loaded>只有<xref:System.Windows.Window.ContentRendered>在引發<xref:System.Windows.Window.Activated>事件之後, 才會引發和事件。 記住這一點之後, 當引發時<xref:System.Windows.Window.ContentRendered> , 可以有效地將視窗視為已開啟。  
  
 視窗成為使用中之後，使用者可以在相同應用程式中啟動另一個視窗，或啟動另一個應用程式。 發生這種情況時, 目前作用中的視窗會變成<xref:System.Windows.Window.Deactivated>停用狀態, 並引發事件。 同樣地, 當使用者選取目前已停用的視窗時, 視窗會再次<xref:System.Windows.Window.Activated>變成使用中狀態, 並引發。  
  
 處理<xref:System.Windows.Window.Activated> 和<xref:System.Windows.Window.Deactivated>的其中一個常見原因是啟用和停用只有在視窗作用中時才可執行檔功能。 例如，某些視窗顯示需要使用者持續輸入和注意的互動式內容，包括遊戲和視訊播放程式。 下列範例是簡化的影片播放程式, 示範如何處理<xref:System.Windows.Window.Activated>及<xref:System.Windows.Window.Deactivated>執行此行為。  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 當視窗已停用時，其他應用程式類型仍然可能會在背景中執行程式碼。 例如，當使用者使用其他應用程式時，郵件用戶端可能會繼續輪詢郵件伺服器。 這類應用程式在主視窗已停用時，通常會提供不同或其他行為。 對於郵件程式，這可能表示同時將新的郵件項目加入收件匣，並將通知圖示加入系統匣。 只有當 [郵件] 視窗不在使用中時, 才需要顯示通知圖示, 這可以藉<xref:System.Windows.Window.IsActive%2A>由檢查屬性來判斷。  
  
 如果背景工作完成, 視窗可能會想要藉由呼叫<xref:System.Windows.Window.Activate%2A>方法, 更迫切地通知使用者。 如果使用者與呼叫時<xref:System.Windows.Window.Activate%2A>啟動的另一個應用程式互動, 視窗的工作列按鈕會閃爍。 如果使用者與目前的應用程式互動, 則呼叫<xref:System.Windows.Window.Activate%2A>會將視窗帶到前景。  
  
> [!NOTE]
> 您可以使用<xref:System.Windows.Application.Activated?displayProperty=nameWithType>和<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>事件來處理應用程式範圍啟用。  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>關閉視窗  
 視窗的存留期在使用者關閉它時開始進入尾聲。 視窗可以使用非工作區中的項目關閉，包括下列項目︰  
  
- [**系統**] 功能表的**關閉**專案。  
  
- 按下 ALT+F4。  
  
- 按下 [**關閉**] 按鈕。  
  
 您可以提供其他機制讓工作區關閉視窗，較常見的包括下列各項︰  
  
- [檔案] 功能表中的 [結束] 專案, 通常是針對主應用程式視窗。  
  
- [檔案] 功能表中的 [**關閉**] 專案, 通常是在次要應用程式視窗上。  
  
- [**取消**] 按鈕, 通常是在強制回應對話方塊上。  
  
- [**關閉**] 按鈕, 通常是在非強制回應對話方塊上。  
  
 若要關閉視窗以回應其中一個自訂機制, 您必須呼叫<xref:System.Windows.Window.Close%2A>方法。 下列範例會藉由選擇 [檔案] 功能表上的 [結束],來執行關閉視窗的功能。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 當視窗關閉時, 它會引發兩個<xref:System.Windows.Window.Closing>事件<xref:System.Windows.Window.Closed>: 和。  
  
 <xref:System.Windows.Window.Closing>會在視窗關閉之前引發, 而且它會提供一種機制, 讓您可以防止視窗關閉。 防止視窗關閉的一個常見原因，是視窗內容包含已修改的資料。 在此情況下, <xref:System.Windows.Window.Closing>可以處理事件以判斷資料是否已變更, 如果是, 則要求使用者是否要繼續關閉視窗而不儲存資料, 或取消視窗關閉。 下列範例顯示處理<xref:System.Windows.Window.Closing>的重要層面。  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 `Boolean` <xref:System.ComponentModel.CancelEventArgs> `true`事件處理常式會傳遞, 它<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>會執行您設定為的屬性, 以防止關閉視窗。 <xref:System.Windows.Window.Closing>  
  
 如果<xref:System.Windows.Window.Closing>未處理, 或已處理但未取消, 視窗將會關閉。 在視窗實際關閉之前, <xref:System.Windows.Window.Closed>會引發。 此時無法防止視窗關閉。  
  
> [!NOTE]
> 應用程式可以設定為在主應用程式視窗關閉時自動關閉 (請參閱<xref:System.Windows.Application.MainWindow%2A>), 或最後一個視窗關閉。 如需詳細資訊，請參閱 <xref:System.Windows.Application.ShutdownMode%2A>。  
  
 雖然可以透過非用戶端和用戶端區域中提供的機制明確地關閉視窗, 但也可以在應用程式或視窗的其他部分中, 以隱含方式關閉視窗, 包括下列各項:  
  
- 使用者登出或關閉 Windows。  
  
- 視窗的擁有者會關閉 ( <xref:System.Windows.Window.Owner%2A>請參閱)。  
  
- 主應用程式視窗已關閉, <xref:System.Windows.Application.ShutdownMode%2A>且<xref:System.Windows.ShutdownMode.OnMainWindowClose>為。  
  
- 呼叫 <xref:System.Windows.Application.Shutdown%2A>。  
  
> [!NOTE]
> 在關閉之後就無法重新開啟視窗。  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>視窗存留期事件  
 下圖顯示主事件在視窗存留期間的順序:  
  
 ![在視窗的存留期內顯示事件的圖表。](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 下圖顯示在未啟用的視窗存留期間內, 主體事件的順序 (<xref:System.Windows.Window.ShowActivated%2A>在顯示視窗之前設定為`false` ):  
  
 ![在不啟用的情況下, 于視窗存留期間顯示事件的圖表。](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>視窗位置  
 視窗開啟時，它會有相對於桌面的 x 和 y 維度位置。 您可以分別檢查<xref:System.Windows.Window.Left%2A>和<xref:System.Windows.Window.Top%2A>屬性來判斷這個位置。 您可以設定這些屬性，以變更視窗的位置。  
  
 您也可以使用下列<xref:System.Windows.Window> <xref:System.Windows.WindowStartupLocation>其中一個列舉值來<xref:System.Windows.Window.WindowStartupLocation%2A>設定屬性, 以指定第一次出現時的初始位置:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (預設)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 如果將啟動位置指定<xref:System.Windows.WindowStartupLocation.Manual>為, <xref:System.Windows.Window.Left%2A>而且尚未設定和<xref:System.Windows.Window.Top%2A>屬性, <xref:System.Windows.Window>將會要求 Windows 位置出現在中。  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>最上層視窗和疊置順序  
 除了有 x 和 y 位置，視窗也有 z 維度的位置，這決定了它相對於其他視窗的垂直位置。 這稱為視窗的疊置順序，並且有兩種類型︰一般疊置順序和最上層疊置順序。 視窗在一般迭置*順序*中的位置取決於它目前是否在作用中。 根據預設，視窗位於一般疊置順序。 視窗在*最上層*的迭置順序中的位置也取決於目前是否為使用中狀態。 此外，最上層疊置順序的視窗一定會位於一般疊置順序的視窗之上。 視窗是以最上層的迭置順序, 將其<xref:System.Windows.Window.Topmost%2A>屬性設定為。 `true`  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 在每個疊置順序內，目前使用中視窗會顯示在相同疊置順序中的所有其他視窗之上。  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>視窗大小  
 除了擁有桌面位置, 視窗的大小是由數個屬性所決定, 包括各種寬度和高度屬性和<xref:System.Windows.Window.SizeToContent%2A>。  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.MaxWidth%2A>是用來管理視窗在其存留期內可以有的寬度範圍, 如下列範例所示設定。  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 視窗高度是由<xref:System.Windows.FrameworkElement.MinHeight%2A>、 <xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.MaxHeight%2A>所管理, 而且會設定為, 如下列範例所示。  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 因為各種寬度值和高度值都各指定一個範圍，所以可調整大小視窗的高度與寬度可能會是個別維度的指定範圍內的任何位置。 若要偵測其目前的寬度和高度<xref:System.Windows.FrameworkElement.ActualWidth%2A> , <xref:System.Windows.FrameworkElement.ActualHeight%2A>請分別檢查和。  
  
 如果您想要讓視窗的寬度和高度符合視窗內容的大小, 您可以使用<xref:System.Windows.Window.SizeToContent%2A>屬性, 其具有下列值:  
  
- <xref:System.Windows.SizeToContent.Manual>. 無效果 (預設值)。  
  
- <xref:System.Windows.SizeToContent.Width>. 符合內容寬度, 其效果與將<xref:System.Windows.FrameworkElement.MinWidth%2A>和<xref:System.Windows.FrameworkElement.MaxWidth%2A>設定為內容的寬度相同。  
  
- <xref:System.Windows.SizeToContent.Height>. 符合內容高度, 其效果等同于將<xref:System.Windows.FrameworkElement.MinHeight%2A>和<xref:System.Windows.FrameworkElement.MaxHeight%2A>設定為內容的高度。  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. 符合內容寬度和<xref:System.Windows.FrameworkElement.MinHeight%2A>高度, 其效果與將和<xref:System.Windows.FrameworkElement.MaxHeight%2A>設定為內容的高度相同, 並同時<xref:System.Windows.FrameworkElement.MinWidth%2A>將和<xref:System.Windows.FrameworkElement.MaxWidth%2A>設定為內容的寬度。  
  
 下列範例顯示自動調整垂直和水平大小以符合其內容的視窗，第一次顯示時的樣子。  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 下列範例示範如何在程式碼中<xref:System.Windows.Window.SizeToContent%2A>設定屬性, 以指定視窗的調整大小以符合其內容。
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>調整大小屬性優先順序  
 基本上，視窗的各種大小屬性會合併起來定義可調整大小的視窗的寬度和高度範圍。 為確保維持有效的範圍, <xref:System.Windows.Window>會使用下列優先順序來評估大小屬性的值。  
  
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
  
 優先順序也可以決定視窗最大化時的大小, 而這是使用<xref:System.Windows.Window.WindowState%2A>屬性來管理。  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>視窗狀態  
 在可調整大小的視窗存留期中，它可以有三種狀態︰標準、最小化及最大化。 具有*正常*狀態的視窗是視窗的預設狀態。 這種狀態的視窗可以讓使用者移動並使用調整大小底框或框線調整其大小，如果它可調整大小。  
  
 如果<xref:System.Windows.Window.ShowInTaskbar%2A>設定為`true`, 則具有*最小化*狀態的視窗會折迭至其工作列按鈕, 否則會折迭為最小的可能大小, 並將其本身重新放置到桌面的左下角。 最小化視窗的類型都無法使用框線或調整大小底框來調整大小，雖然未顯示在工作列中的最小化視窗可以在桌面拖曳。  
  
 具有*最大化*狀態的視窗會展開為它可以達到的最大大小, 而這只會與其<xref:System.Windows.FrameworkElement.MaxWidth%2A>、 <xref:System.Windows.FrameworkElement.MaxHeight%2A>和<xref:System.Windows.Window.SizeToContent%2A>屬性所指定的大小一樣大。 就像最小化的視窗，最大化的視窗無法使用調整大小底框或藉由拖曳框線來調整大小。  
  
> [!NOTE]
> 視窗的<xref:System.Windows.Window.Top%2A>、 <xref:System.Windows.Window.Left%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>和屬性值一律代表正常狀態的值,即使視窗目前已最大化或最小化。<xref:System.Windows.FrameworkElement.Height%2A>  
  
 視窗的狀態可以藉由設定其<xref:System.Windows.Window.WindowState%2A>屬性來設定, 它可以有下列<xref:System.Windows.WindowState>其中一個列舉值:  
  
- <xref:System.Windows.WindowState.Normal> (預設)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 下列範例示範如何建立在開啟時會顯示為最大化的視窗。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 一般來說, 您應該設定以<xref:System.Windows.Window.WindowState%2A>設定視窗的初始狀態。 可調整大小的視窗顯示後，使用者可以按下視窗標題列上的最小化、最大化和還原按鈕，以變更視窗狀態。  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>視窗外觀  
 您可以新增視窗特定的內容，例如按鈕、標籤和文字方塊，來變更視窗工作區的外觀。 若要設定非工作區, <xref:System.Windows.Window>會提供數個屬性, 包括<xref:System.Windows.Window.Icon%2A>設定視窗的圖示以及<xref:System.Windows.Window.Title%2A>設定其標題。  
  
 您也可以藉由設定視窗的調整大小模式、視窗樣式，以及它是否顯示為桌面工作列上的按鈕，變更非工作區框線的外觀和行為。  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>調整大小模式  
 <xref:System.Windows.Window.WindowStyle%2A>視屬性而定, 您可以控制使用者可以如何調整視窗大小。 視窗樣式的選擇會影響使用者是否可以使用滑鼠拖曳框線來調整視窗大小, 而非工作區上是否顯示 [**最小化**]、[**最大化**] 和 [重**設大小**] 按鈕, 以及是否出現後.  
  
 您可以設定視窗的屬性來調整其<xref:System.Windows.Window.ResizeMode%2A>大小, 它可以是下列<xref:System.Windows.ResizeMode>其中一個列舉值:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (預設)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 如同, 視窗的調整大小模式不太可能會在其存留期內變更, 這表示您很有可能會從[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記進行設定。 <xref:System.Windows.Window.WindowStyle%2A>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 請注意, 您可以藉由檢查<xref:System.Windows.Window.WindowState%2A>屬性, 偵測視窗是最大化、最小化或還原。  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>視窗樣式  
 從視窗非工作區公開的框線適用於大部分的應用程式。 不過，有一些情況下需要不同型別的框線，或是完全不需要框線，視視窗的型別而定。  
  
 若要控制視窗所取得的框線類型, 您可以使用<xref:System.Windows.Window.WindowStyle%2A>下列其中一個<xref:System.Windows.WindowStyle>列舉值來設定其屬性:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (預設)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 這些視窗樣式的效果如下圖所示:  
  
 ![視窗框線樣式的說明。](./media/wpf-windows-overview/window-border-styles.png)  
  
 您可以<xref:System.Windows.Window.WindowStyle%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]使用標記或程式碼來設定; 因為在視窗存留期間不太可能變更, 所以您很可能會使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記來設定它。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>非矩形視窗樣式  
 在某些情況下, 可<xref:System.Windows.Window.WindowStyle%2A>讓您擁有的框線樣式還不夠。 例如, 您可能會想要建立具有非矩形框線的應用程式, [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]例如使用。  
  
 例如, 請考慮下圖所示的語音反升視窗:  
  
 ![顯示 [拖曳我] 的語音反升視窗。](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 藉由將<xref:System.Windows.Window.WindowStyle%2A>屬性設為<xref:System.Windows.WindowStyle.None>, 以及使用<xref:System.Windows.Window>具有透明度的特殊支援, 即可建立這種類型的視窗。  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 這些值的組合會指示視窗要轉譯為完全透明。 在此狀態下，無法使用視窗的非工作區裝飾 ([關閉] 功能表、[最小化]、[最大化] 和 [還原] 按鈕等等)。 因此，您需要自行提供。  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>工作列目前狀態  

視窗的預設面板包括工作列按鈕, 如下圖所示:

 ![顯示具有工作列按鈕之視窗的螢幕擷取畫面。](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 有些類型的 windows 沒有工作列按鈕, 例如訊息方塊和對話方塊 (請參閱[對話方塊總覽](dialog-boxes-overview.md))。 您可以藉由設定<xref:System.Windows.Window.ShowInTaskbar%2A>屬性來控制視窗的工作列按鈕是否顯示 (`true`預設為)。  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>安全性考量  
 <xref:System.Windows.Window>需要`UnmanagedCode`具現化安全性許可權。 對於本機電腦上安裝和啟動的應用程式，這落在授與給該應用程式的權限集範圍內。  
  
 不過, 這不在授與使用 ClickOnce 從網際網路或近端內部網路區域啟動之應用程式的許可權集之外。 因此, 使用者會收到 ClickOnce 安全性警告, 而且必須將應用程式的許可權集合提升為完全信任。  
  
 此外, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]根據預設, 無法顯示視窗或對話方塊。 如需獨立應用程式安全性考慮的討論, 請參閱[WPF 安全性策略-平臺安全性](../wpf-security-strategy-platform-security.md)。  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>其他類型的視窗  
 <xref:System.Windows.Navigation.NavigationWindow>是設計用來裝載可導覽內容的視窗。 如需詳細資訊, 請參閱[導覽總覽](navigation-overview.md))。  
  
 對話方塊是經常用來從使用者收集資訊以完成一項功能的視窗。 例如, 當使用者想要開啟檔案時, 應用程式通常會顯示 [**開啟**檔案] 對話方塊, 以取得使用者的檔案名。 如需詳細資訊，請參閱[對話方塊概觀](dialog-boxes-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [對話方塊概觀](dialog-boxes-overview.md)
- [建置 WPF 應用程式](building-a-wpf-application-wpf.md)
