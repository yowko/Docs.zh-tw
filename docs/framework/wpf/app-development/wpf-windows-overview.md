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
ms.openlocfilehash: 60ed101df691db9f1afa8e47702f131bee384495
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625318"
---
# <a name="wpf-windows-overview"></a>WPF 視窗概觀
使用者透過 windows 的 Windows Presentation Foundation (WPF) 獨立應用程式與互動。 視窗的主要用途是裝載內容，以視覺化方式檢視資料，並讓使用者可以與資料互動。 獨立[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式提供自己的視窗使用<xref:System.Windows.Window>類別。 本主題將介紹<xref:System.Windows.Window>再介紹建立和管理獨立應用程式中的 windows 的基本概念。  
  
> [!NOTE]
>  瀏覽器裝載[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式，包括[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]和鬆散[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]頁面，不會提供自己的視窗。 相反地，它們裝載於所提供的 windows [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]。 請參閱[WPF XAML 瀏覽器應用程式概觀](wpf-xaml-browser-applications-overview.md)。  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Window 類別  
 下圖說明視窗的組成部分：  
  
 ![如果螢幕擷取畫面顯示視窗項目。](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 視窗分為兩個區域︰非工作區和工作區。  
  
 *非工作區* 視窗藉由[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]並包含通用於大部分的 windows，包括下列視窗的組件：  
  
- 框線。  
  
- 標題列。  
  
- 圖示。  
  
- [最小化]、[最大化] 和 [還原] 按鈕。  
  
- [關閉] 按鈕。  
  
- [系統] 功能表，具有允許使用者最小化、最大化、還原、移動、調整大小和關閉視窗的功能表項目。  
  
 *工作區*視窗是視窗非工作區內的區域，而且由開發人員用來新增應用程式特定的內容，例如功能表列、 工具列和控制項。  
  
 在  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，視窗由封裝<xref:System.Windows.Window>類別，您用來執行下列動作：  
  
- 顯示視窗。  
  
- 設定視窗的大小、位置和外觀。  
  
- 裝載應用程式特定內容。  
  
- 管理視窗的存留期。  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>實作視窗  
 典型視窗的實作包含外觀和行為，其中*外觀*定義的使用者 視窗的外觀並*行為*定義當使用者互動，視窗運作的方式使用它。 在  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，您可以實作外觀和行為的視窗中，使用程式碼或[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記。  
  
 一般情況下，不過，視窗的外觀使用實作[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記和其行為使用實作程式碼後置，如下列範例所示。  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 若要啟用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記檔案和程式碼後置檔案能一起運作，需要下列憑證：  
  
- 在標記中，`Window`元素必須包含`x:Class`屬性。 應用程式建置時是否存在`x:Class`標記中檔案會導致[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]來建立`partial`類別衍生自<xref:System.Windows.Window>，並具有所指定的名稱`x:Class`屬性。 這需要額外[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]命名空間宣告[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]結構描述 ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` )。 產生`partial`類別會實作`InitializeComponent`方法，呼叫以註冊事件，並設定標記中實作的屬性。  
  
- 類別必須是在程式碼後置`partial`類別所指定的同名`x:Class`屬性標記，而且必須衍生自<xref:System.Windows.Window>。 這可讓程式碼後置檔案相關聯`partial`建置應用程式時，會將標記檔案產生的類別 (請參閱 <<c2> [ 建置 WPF 應用程式](building-a-wpf-application-wpf.md))。  
  
- 在 程式碼後置<xref:System.Windows.Window>類別必須實作呼叫的建構函式`InitializeComponent`方法。 `InitializeComponent` 實作標記檔案產生的`partial`類別來註冊事件，並設定標記中定義的屬性。  
  
> [!NOTE]
>  當您將加入新<xref:System.Windows.Window>至您的專案使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，則<xref:System.Windows.Window>使用標記和程式碼後置來實作，並包含必要的設定，以建立為標記和程式碼後置檔案之間的關聯此處所述。  
  
 使用此設定後，您可以專注於定義中的視窗外觀[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記和程式碼後置中實作它的行為。 下列範例顯示具有按鈕，在中實作的視窗[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記，並針對按鈕的事件處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>實作程式碼後置中的事件。  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>設定 MSBuild 的視窗定義  
 實作視窗的方式設定的方式會決定[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]。 使用這兩個定義的視窗[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記和程式碼後置：  
  
- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記檔案設定為[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目。  
  
- 程式碼後置檔案設定為[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile`項目。  
  
 這會顯示下列[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]專案檔。  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 如需建置[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式，請參閱[建置 WPF 應用程式](building-a-wpf-application-wpf.md)。  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>視窗存留期  
 如同任何類別，視窗有存留期，會在它一開始具現化時開始，在那之後它會被開啟、啟動和停用，並最終關閉。  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>開啟視窗  
 若要開啟視窗，您要先建立它的執行個體，如下列範例中示範。  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 在此範例中，`MarkupAndCodeBehindWindow`應用程式啟動時，就會出現，具現化時<xref:System.Windows.Application.Startup>就會引發事件。  
  
 具現化一個視窗時，它的參考會自動新增以一份 windows 受<xref:System.Windows.Application>物件 (請參閱<xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>)。 此外，要具現化的第一個視窗，根據預設，設定<xref:System.Windows.Application>作為主應用程式視窗 (請參閱<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>)。  
  
 藉由呼叫最後開啟的視窗<xref:System.Windows.Window.Show%2A>方法; 以下圖所示的結果。  
  
 ![藉由呼叫 window.show 而開啟的視窗](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 藉由呼叫開啟的視窗<xref:System.Windows.Window.Show%2A>會非強制回應視窗中，這表示應用程式的運作模式，可讓使用者啟用相同的應用程式中的其他視窗中。  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A> 呼叫可開啟視窗，例如對話方塊時，以強制回應方式。 請參閱[對話方塊概觀](dialog-boxes-overview.md)如需詳細資訊。  
  
 當<xref:System.Windows.Window.Show%2A>是呼叫，視窗執行初始化工作後，它會顯示建立基礎結構，讓它能夠接收使用者輸入。 當初始化視窗時，<xref:System.Windows.Window.SourceInitialized>就會引發事件，並顯示視窗。  
  
 當作捷徑使用，<xref:System.Windows.Application.StartupUri%2A>可以設定，以指定第一個應用程式啟動時自動開啟的視窗。  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 應用程式啟動時，值所指定視窗<xref:System.Windows.Application.StartupUri%2A>開啟 modelessly; 就內部而言，視窗會開啟藉由呼叫其<xref:System.Windows.Window.Show%2A>方法。  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>視窗擁有權  
 使用開啟的視窗<xref:System.Windows.Window.Show%2A>方法並沒有隱含的關聯性，與建立它的視窗，使用者可以與彼此獨立，這表示任一個視窗都可以執行下列其中一個視窗互動：  
  
- 涵蓋另 (除非其中一個視窗具有其<xref:System.Windows.Window.Topmost%2A>屬性設定為`true`)。  
  
- 最小化、最大化和還原而不會影響對方。  
  
 某些視窗需要與開啟它們的視窗有關聯性。 比方說，[!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)]應用程式可能會開啟屬性視窗和工具視窗，其一般行為是以涵蓋建立它們的視窗。 此外，這類視窗應該一律與建立它們的視窗一致地關閉、最小化、最大化和還原。 藉由一個視窗，可以建立這類關聯性*自己*另一個，之後，即可設定並<xref:System.Windows.Window.Owner%2A>屬性*擁有視窗*參考*擁有者視窗*。 這在下列範例中顯示。  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 建立擁有權之後︰  
  
- 擁有的視窗可以檢查的值來參考其主控視窗及其<xref:System.Windows.Window.Owner%2A>屬性。  
  
- 主控視窗可以探索其所檢查的值所擁有的所有 windows 其<xref:System.Windows.Window.OwnedWindows%2A>屬性。  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>避免視窗啟動  
 有些的情況，windows 應該不在顯示時啟動，例如網際網路 messenger 樣式應用程式的交談視窗或電子郵件應用程式的通知視窗。  
  
 如果您的應用程式不應該在顯示時啟動的視窗，您可以設定其<xref:System.Windows.Window.ShowActivated%2A>屬性，以`false`再呼叫<xref:System.Windows.Window.Show%2A>方法第一次。 因此：  
  
- 未啟動視窗。  
  
- 視窗的<xref:System.Windows.Window.Activated>不會引發事件。  
  
- 目前已啟動的視窗會保持已啟動。  
  
 不過，當使用者按一下工作區或非工作區來啟動它時，視窗將會啟動。 在此情況下：  
  
- 視窗已啟動。  
  
- 視窗的<xref:System.Windows.Window.Activated>就會引發事件。  
  
- 先前已啟動的視窗已停用。  
  
- 視窗的<xref:System.Windows.Window.Deactivated>和<xref:System.Windows.Window.Activated>如預期般運作，以回應使用者動作，接著引發事件。  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>視窗啟動  
 當第一次開啟視窗時，它會變成使用中視窗 (除非它會顯示<xref:System.Windows.Window.ShowActivated%2A>設定為`false`)。 *作用中視窗*是目前正在擷取使用者輸入，例如按鍵動作與滑鼠點按的視窗。 當視窗成為使用中時，會引發<xref:System.Windows.Window.Activated>事件。  
  
> [!NOTE]
>  第一次開啟視窗，<xref:System.Windows.FrameworkElement.Loaded>並<xref:System.Windows.Window.ContentRendered>之後才會引發事件<xref:System.Windows.Window.Activated>就會引發事件。 這一點，視窗可以有效地視為時開啟<xref:System.Windows.Window.ContentRendered>，就會引發。  
  
 視窗成為使用中之後，使用者可以在相同應用程式中啟動另一個視窗，或啟動另一個應用程式。 目前使用中視窗時，會變成停用，並引發<xref:System.Windows.Window.Deactivated>事件。 同樣地，當使用者選取目前失效的視窗，視窗再次變成作用中和<xref:System.Windows.Window.Activated>，就會引發。  
  
 若要處理的一個常見原因<xref:System.Windows.Window.Activated>和<xref:System.Windows.Window.Deactivated>是啟用和停用只能執行時的視窗是作用中的功能。 例如，某些視窗顯示需要使用者持續輸入和注意的互動式內容，包括遊戲和視訊播放程式。 下列範例是簡化的視訊播放程式，示範如何處理<xref:System.Windows.Window.Activated>和<xref:System.Windows.Window.Deactivated>來實作此行為。  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 當視窗已停用時，其他應用程式類型仍然可能會在背景中執行程式碼。 例如，當使用者使用其他應用程式時，郵件用戶端可能會繼續輪詢郵件伺服器。 這類應用程式在主視窗已停用時，通常會提供不同或其他行為。 對於郵件程式，這可能表示同時將新的郵件項目加入收件匣，並將通知圖示加入系統匣。 通知圖示需要只會顯示，當郵件視窗不是使用中，可以透過檢查來判斷<xref:System.Windows.Window.IsActive%2A>屬性。  
  
 如果背景工作完成時，視窗可能會想要更迫切地通知使用者，藉由呼叫<xref:System.Windows.Window.Activate%2A>方法。 如果使用者互動與另一個應用程式啟動時<xref:System.Windows.Window.Activate%2A>呼叫時，視窗的工作列按鈕會閃爍。 如果使用者正在與目前的應用程式互動，則呼叫<xref:System.Windows.Window.Activate%2A>將視窗帶到前景。  
  
> [!NOTE]
>  您可以處理應用程式範圍啟動使用<xref:System.Windows.Application.Activated?displayProperty=nameWithType>和<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>事件。  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>關閉視窗  
 視窗的存留期在使用者關閉它時開始進入尾聲。 視窗可以使用非工作區中的項目關閉，包括下列項目︰  
  
- **關閉**的項目**系統**功能表。  
  
- 按下 ALT+F4。  
  
- 按下**關閉** 按鈕。  
  
 您可以提供其他機制讓工作區關閉視窗，較常見的包括下列各項︰  
  
- **結束**中的項目**檔案**功能表中，通常是針對主要的應用程式視窗。  
  
- A**關閉**中的項目**檔案**功能表中的，通常是在次要應用程式視窗。  
  
- A**取消**按鈕，通常在強制回應對話方塊。  
  
- A**關閉**按鈕，通常在非強制回應對話方塊。  
  
 若要關閉視窗以回應這其中一種自訂機制，您必須呼叫<xref:System.Windows.Window.Close%2A>方法。 下列範例會實作能夠關閉視窗，選擇**結束**上**檔案**功能表。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 當視窗關閉時，會引發兩個事件：<xref:System.Windows.Window.Closing>和<xref:System.Windows.Window.Closed>。  
  
 <xref:System.Windows.Window.Closing> 在視窗關閉，並提供的機制，可用來防止關閉視窗之前引發。 防止視窗關閉的一個常見原因，是視窗內容包含已修改的資料。 在此情況下，<xref:System.Windows.Window.Closing>可以處理事件，以判斷是否已變更資料，如果是的話，詢問使用者是否要繼續關閉視窗而不儲存資料，或是取消視窗關閉。 下列範例示範處理的重要層面<xref:System.Windows.Window.Closing>。  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <xref:System.Windows.Window.Closing>傳遞事件處理常式<xref:System.ComponentModel.CancelEventArgs>，它會實作`Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性，您將設定為`true`來防止關閉視窗。  
  
 如果<xref:System.Windows.Window.Closing>未處理，或已處理但未取消，則會關閉視窗。 只在視窗實際關閉之前， <xref:System.Windows.Window.Closed> ，就會引發。 此時無法防止視窗關閉。  
  
> [!NOTE]
>  應用程式可以設定為關閉自動主應用程式視窗關閉時 (請參閱<xref:System.Windows.Application.MainWindow%2A>) 或最後一個視窗關閉。 如需詳細資訊，請參閱 <xref:System.Windows.Application.ShutdownMode%2A>。  
  
 雖然可以透過非用戶端和用戶端區域中提供的機制明確關閉視窗，視窗也可以隱含地關閉應用程式的其他部分中的行為的結果或[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，包括下列：  
  
- 使用者登出或關閉 Windows。  
  
- 視窗的擁有者關閉 (請參閱<xref:System.Windows.Window.Owner%2A>)。  
  
- 主應用程式視窗已關閉並<xref:System.Windows.Application.ShutdownMode%2A>是<xref:System.Windows.ShutdownMode.OnMainWindowClose>。  
  
- 呼叫 <xref:System.Windows.Application.Shutdown%2A>。  
  
> [!NOTE]
>  在關閉之後就無法重新開啟視窗。  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>視窗存留期事件  
 下圖顯示視窗的存留期的主體事件順序：  
  
 ![此圖顯示在視窗的存留期的事件。](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 下圖顯示顯示時沒有啟動視窗的存留期的主體事件順序 (<xref:System.Windows.Window.ShowActivated%2A>設為`false`視窗顯示之前):  
  
 ![此圖顯示在視窗的存留期，而不需要啟用的事件。](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>視窗位置  
 視窗開啟時，它會有相對於桌面的 x 和 y 維度位置。 這個位置可決定藉由檢查<xref:System.Windows.Window.Left%2A>和<xref:System.Windows.Window.Top%2A>屬性，分別。 您可以設定這些屬性，以變更視窗的位置。  
  
 您也可以指定的初始位置<xref:System.Windows.Window>第一次出現時藉由設定<xref:System.Windows.Window.WindowStartupLocation%2A>具有下列其中一種屬性<xref:System.Windows.WindowStartupLocation>列舉值：  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (預設)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 如果啟動位置指定為<xref:System.Windows.WindowStartupLocation.Manual>，而<xref:System.Windows.Window.Left%2A>並<xref:System.Windows.Window.Top%2A>尚未設定屬性，<xref:System.Windows.Window>會要求才會出現在位置的 Windows。  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>最上層視窗和疊置順序  
 除了有 x 和 y 位置，視窗也有 z 維度的位置，這決定了它相對於其他視窗的垂直位置。 這稱為視窗的疊置順序，並且有兩種類型︰一般疊置順序和最上層疊置順序。 在視窗的位置*一般疊置順序*取決於它是否目前作用中。 根據預設，視窗位於一般疊置順序。 在視窗的位置*最上層的疊置順序*也取決於它是否目前作用中。 此外，最上層疊置順序的視窗一定會位於一般疊置順序的視窗之上。 視窗位於最上層的疊置順序藉由設定其<xref:System.Windows.Window.Topmost%2A>屬性設`true`。  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 在每個疊置順序內，目前使用中視窗會顯示在相同疊置順序中的所有其他視窗之上。  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>視窗大小  
 除了有桌面位置，視窗會有數個屬性，包括各種寬度和高度屬性所決定的大小和<xref:System.Windows.Window.SizeToContent%2A>。  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A><xref:System.Windows.FrameworkElement.Width%2A>，和<xref:System.Windows.FrameworkElement.MaxWidth%2A>用來管理的視窗可以在其生命週期，並已在下列範例所示的寬度範圍。  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 視窗高度受<xref:System.Windows.FrameworkElement.MinHeight%2A>， <xref:System.Windows.FrameworkElement.Height%2A>，和<xref:System.Windows.FrameworkElement.MaxHeight%2A>，並已在下列範例所示。  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 因為各種寬度值和高度值都各指定一個範圍，所以可調整大小視窗的高度與寬度可能會是個別維度的指定範圍內的任何位置。 若要偵測其目前的寬度和高度，檢查<xref:System.Windows.FrameworkElement.ActualWidth%2A>和<xref:System.Windows.FrameworkElement.ActualHeight%2A>分別。  
  
 如果您想要視窗的高度與寬度，調整成視窗大小的大小的內容，您可以使用<xref:System.Windows.Window.SizeToContent%2A>屬性，它具有下列值：  
  
- <xref:System.Windows.SizeToContent.Manual>. 無效果 (預設值)。  
  
- <xref:System.Windows.SizeToContent.Width>. 調整成內容的寬度，具有相同的效果設定兩者<xref:System.Windows.FrameworkElement.MinWidth%2A>和<xref:System.Windows.FrameworkElement.MaxWidth%2A>內容的寬度。  
  
- <xref:System.Windows.SizeToContent.Height>. 調整成內容的高度，具有相同的效果設定兩者<xref:System.Windows.FrameworkElement.MinHeight%2A>和<xref:System.Windows.FrameworkElement.MaxHeight%2A>內容的高度。  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. 調整成內容的寬度和高度，設定兩者相同的效果<xref:System.Windows.FrameworkElement.MinHeight%2A>並<xref:System.Windows.FrameworkElement.MaxHeight%2A>內容，以及設定這兩個高度<xref:System.Windows.FrameworkElement.MinWidth%2A>和<xref:System.Windows.FrameworkElement.MaxWidth%2A>內容的寬度。  
  
 下列範例顯示自動調整垂直和水平大小以符合其內容的視窗，第一次顯示時的樣子。  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 下列範例示範如何設定<xref:System.Windows.Window.SizeToContent%2A>指定視窗如何調整大小以符合其內容的程式碼中的屬性。
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>調整大小屬性優先順序  
 基本上，視窗的各種大小屬性會合併起來定義可調整大小的視窗的寬度和高度範圍。 若要確保維護有效的範圍，<xref:System.Windows.Window>評估大小屬性，使用下列優先順序之訂單的值。  
  
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
  
 優先順序也可以決定視窗的大小，它最大化時，管理與<xref:System.Windows.Window.WindowState%2A>屬性。  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>視窗狀態  
 在可調整大小的視窗存留期中，它可以有三種狀態︰標準、最小化及最大化。 使用視窗*正常*狀態是視窗的預設狀態。 這種狀態的視窗可以讓使用者移動並使用調整大小底框或框線調整其大小，如果它可調整大小。  
  
 與視窗*最小化*狀態摺疊到其工作列按鈕，如果<xref:System.Windows.Window.ShowInTaskbar%2A>設為`true`; 否則它會摺疊的最小的可能大小，它可以是並且重新本身放置到桌面的左下角。 最小化視窗的類型都無法使用框線或調整大小底框來調整大小，雖然未顯示在工作列中的最小化視窗可以在桌面拖曳。  
  
 使用視窗*最大化*狀態會展開的大小上限，它可以是，才會大可達其<xref:System.Windows.FrameworkElement.MaxWidth%2A>， <xref:System.Windows.FrameworkElement.MaxHeight%2A>，和<xref:System.Windows.Window.SizeToContent%2A>; 屬性指定。 就像最小化的視窗，最大化的視窗無法使用調整大小底框或藉由拖曳框線來調整大小。  
  
> [!NOTE]
>  值<xref:System.Windows.Window.Top%2A>， <xref:System.Windows.Window.Left%2A>， <xref:System.Windows.FrameworkElement.Width%2A>，和<xref:System.Windows.FrameworkElement.Height%2A>視窗的內容一律代表正常狀態的值，即使目前最大化或最小化視窗。  
  
 視窗的狀態可以透過設定來設定其<xref:System.Windows.Window.WindowState%2A>屬性，它可以有下列其中一種<xref:System.Windows.WindowState>列舉值：  
  
- <xref:System.Windows.WindowState.Normal> (預設)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 下列範例示範如何建立在開啟時會顯示為最大化的視窗。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 一般情況下，您應該設定<xref:System.Windows.Window.WindowState%2A>設定視窗的初始狀態。 可調整大小的視窗顯示後，使用者可以按下視窗標題列上的最小化、最大化和還原按鈕，以變更視窗狀態。  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>視窗外觀  
 您可以新增視窗特定的內容，例如按鈕、標籤和文字方塊，來變更視窗工作區的外觀。 若要設定非工作區中，<xref:System.Windows.Window>提供數個屬性，其中包括<xref:System.Windows.Window.Icon%2A>來設定視窗的圖示和<xref:System.Windows.Window.Title%2A>以設定其標題。  
  
 您也可以藉由設定視窗的調整大小模式、視窗樣式，以及它是否顯示為桌面工作列上的按鈕，變更非工作區框線的外觀和行為。  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>調整大小模式  
 取決於<xref:System.Windows.Window.WindowStyle%2A>屬性，您可以控制如何 （以及是否） 使用者可以調整視窗大小。 視窗樣式的選擇會影響是否使用者可以調整視窗大小是否拖曳其框線，使用滑鼠**最小化**，**最大化**，並**調整**按鈕會出現在非工作區中，而且如果它們出現時是否已啟用。  
  
 您可以設定視窗調整大小時藉由設定其<xref:System.Windows.Window.ResizeMode%2A>屬性，它可以是下列其中一種<xref:System.Windows.ResizeMode>列舉值：  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (預設)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 如同<xref:System.Windows.Window.WindowStyle%2A>，在視窗的調整大小模式是不太可能在其生命週期，這表示您將最有可能將它從變更[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記。  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 請注意，您可以偵測是否已最大化的視窗，最小化，或藉由檢查還原<xref:System.Windows.Window.WindowState%2A>屬性。  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>視窗樣式  
 從視窗非工作區公開的框線適用於大部分的應用程式。 不過，有一些情況下需要不同型別的框線，或是完全不需要框線，視視窗的型別而定。  
  
 若要控制何種框線的視窗取得，則將其<xref:System.Windows.Window.WindowStyle%2A>屬性的下列值之一<xref:System.Windows.WindowStyle>列舉型別：  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (預設)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 在下圖說明這些視窗樣式的影響：  
  
 ![視窗的框線樣式的圖例。](./media/wpf-windows-overview/window-border-styles.png)  
  
 您可以設定<xref:System.Windows.Window.WindowStyle%2A>採用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記或程式碼，因為它是不太可能變更視窗的存留期間，您將最有可能設定使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>非矩形視窗樣式  
 也有些情況下，其中的框線樣式，<xref:System.Windows.Window.WindowStyle%2A>可讓您有不敷使用。 比方說，您可能想要建立具有非矩形框線，應用程式，例如[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]使用。  
  
 下圖所示的語音泡泡視窗為例：  
  
 ![語音泡泡視窗指出拖曳 me.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 可以建立這類視窗設定<xref:System.Windows.Window.WindowStyle%2A>屬性，以<xref:System.Windows.WindowStyle.None>，並使用特殊支援，<xref:System.Windows.Window>對透明度。  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 這些值的組合會指示視窗要轉譯為完全透明。 在此狀態下，無法使用視窗的非工作區裝飾 ([關閉] 功能表、[最小化]、[最大化] 和 [還原] 按鈕等等)。 因此，您需要自行提供。  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>工作列目前狀態  

視窗的預設外觀包含工作列按鈕時，在下圖所示：

 ![如果螢幕擷取畫面顯示具有工作列按鈕的視窗。](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 某些類型的視窗沒有工作列按鈕，例如訊息方塊和對話方塊 (請參閱[對話方塊概觀](dialog-boxes-overview.md))。 您可以控制是否要將視窗的工作列按鈕顯示藉由設定<xref:System.Windows.Window.ShowInTaskbar%2A>屬性 (`true`預設情況下)。  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>安全性考量  
 <xref:System.Windows.Window> 需要`UnmanagedCode`具現化的安全性權限。 對於本機電腦上安裝和啟動的應用程式，這落在授與給該應用程式的權限集範圍內。  
  
 不過，這不屬於授與給從網際網路或本機內部網路區域使用啟動的應用程式的權限集[!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]。 因此，使用者會收到[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]安全性警告，必須以提高的權限集合完全信任應用程式。  
  
 此外，[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]無法預設顯示視窗和對話方塊。 如需獨立應用程式的安全性考量的討論，請參閱 < [WPF 安全性策略 – 平台安全性](../wpf-security-strategy-platform-security.md)。  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>其他類型的視窗  
 <xref:System.Windows.Navigation.NavigationWindow> 是設計用來裝載可巡覽內容的視窗。 如需詳細資訊，請參閱 <<c0> [ 巡覽概觀](navigation-overview.md))。  
  
 對話方塊是經常用來從使用者收集資訊以完成一項功能的視窗。 例如，當使用者想要開啟檔案，**開啟檔案**程式的應用程式，以從使用者取得檔案名稱會顯示對話方塊。 如需詳細資訊，請參閱[對話方塊概觀](dialog-boxes-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [對話方塊概觀](dialog-boxes-overview.md)
- [建置 WPF 應用程式](building-a-wpf-application-wpf.md)
