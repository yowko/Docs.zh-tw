---
title: "WPF 視窗概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式, 裝載"
  - "內容, 顯示"
  - "內容, 透過程序性程式碼顯示"
  - "內容, 透過 XAML 顯示"
  - "建立, 視窗"
  - "對話方塊"
  - "顯示內容"
  - "透過程序性程式碼顯示內容"
  - "顯示 XAML 頁面"
  - "事件"
  - "裝載, 應用程式"
  - "管理視窗"
  - "強制回應對話方塊"
  - "強制回應視窗"
  - "NavigationWindow 物件"
  - "Page 物件"
  - "程序性程式碼, 顯示內容"
  - "視窗事件"
  - "視窗管理"
  - "視窗物件"
  - "視窗"
  - "XAML 頁面, 顯示"
  - "XAML, 顯示內容"
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
caps.latest.revision: 65
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 60
---
# WPF 視窗概觀
使用者是透過視窗與 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 獨立應用程式進行互動的。  視窗的主要目的在於裝載內容，以視覺化表示資料並讓使用者與資料互動。獨立 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式藉由使用 <xref:System.Windows.Window> 類別而提供自己的視窗。  本主題先介紹 <xref:System.Windows.Window>，然後才涵蓋在獨立應用程式中建立和管理視窗的基本說明。  
  
> [!NOTE]
>  由瀏覽器裝載的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式 \(包含 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 和鬆散[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 頁面\) 不提供自己的視窗。  而是會裝載於 [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] 所提供的視窗中。  請參閱 [WPF XAML 瀏覽器應用程式概觀](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="TheWindowClass"></a>   
## Window 類別  
 下圖說明視窗的組成部分。  
  
 ![視窗項目](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")  
  
 視窗劃分為兩個區域：工作區和非工作區。  
  
 視窗的「*非工作區*」\(Non\-Client Area\) 是由 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 實作的，並包含大部分視窗常見的視窗部分，包括下列項目：  
  
-   框線。  
  
-   標題列。  
  
-   圖示。  
  
-   \[最小化\]、\[最大化\] 和 \[還原\] 按鈕。  
  
-   \[關閉\] 按鈕。  
  
-   \[系統\] 功能表，具有可以讓使用者最小化、最大化、還原、移動、調整大小和關閉視窗的功能表項目。  
  
 視窗的「*工作區*」\(Client Area\) 則是視窗非工作區內的區域，是由開發人員用來加入應用程式專用的內容，例如功能表列、工具列和控制項。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的視窗是由 <xref:System.Windows.Window> 類別封裝的，該類別是用來進行下列作業：  
  
-   顯示視窗。  
  
-   設定視窗大小、位置和外觀。  
  
-   裝載應用程式特定的內容。  
  
-   管理視窗的存留期。  
  
<a name="DefiningAWindow"></a>   
## 實作視窗  
 一般視窗的實作包含外觀和行為兩部分：「*外觀*」\(Appearance\) 定義使用者看到視窗的方式，而「*行為*」\(Behavior\) 則定義使用者與視窗互動時視窗的運作方式。  在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，您可以使用程式碼或 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記來實作視窗的外觀和行為。  
  
 然而，一般而言，視窗的外觀是使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記實作的，而行為則是使用程式碼後置實作的，如下列範例所示。  
  
 [!code-xml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 若要讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記檔案和程式碼後置的檔案一起運作，需要下列條件：  
  
-   標記中的 `Window` 項目必須包含 `x:Class` 屬性。  建置應用程式時，標記檔案中若存在 `x:Class` 會造成 [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] 建立衍生自 <xref:System.Windows.Window> 的 `partial` 類別，並具有 `x:Class` 屬性所指定的名稱。  這需要加入 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 結構描述的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間宣告 \(`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`\)。  產生的 `partial` 類別所實作的 `InitializeComponent` 方法，是在註冊事件和設定標記所實作的屬性時呼叫的。  
  
-   程式碼後置中的類別必須是 `partial` 類別，並具有標記中 `x:Class` 屬性所指定的相同名稱，且必須衍生自 <xref:System.Windows.Window>。  允許程式碼後置的檔案與 `partial` 類別產生關聯，這個類別是在建置應用程式時根據標記產生的 \(請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)\)。  
  
-   在程式碼後置的情況下，<xref:System.Windows.Window> 類別必須實作呼叫 `InitializeComponent` 方法的建構函式。  `InitializeComponent` 是由標記檔產生的 `partial` 類別實作，用來註冊事件以及設定標記中定義的屬性。  
  
> [!NOTE]
>  當您使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 在專案中加入新的 <xref:System.Windows.Window> 時，<xref:System.Windows.Window> 是同時使用標記和程式碼後置實作的，且包含必要的組態以建立標記和程式碼後置的檔案間的關聯 \(如此處所述\)。  
  
 隨著這個組態就定位後，您可以專注於在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記中定義視窗的外觀，並在程式碼後置中實作視窗的行為。  下列範例所顯示視窗的按鈕是在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記中實作的，而按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的事件處理常式則是在程式碼後置中實作的。  
  
 [!code-xml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## 設定 MSBuild 的視窗定義  
 您實作視窗的方式會決定視窗針對 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 的設定方式。  對於同時使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記和程式碼後置定義的視窗：  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記檔案會設定為 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` 項目。  
  
-   程式碼後置的檔案會設定為 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` 項目。  
  
 下列 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 專案檔顯示這項說明。  
  
```  
<Project ... xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 如需建置 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的詳細資訊，請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)。  
  
<a name="WindowLifetime"></a>   
## 視窗存留期  
 如同任何的類別，視窗的存留期是在第一次具現化開始、接著歷經視窗的開啟、啟動和停用，最終會關閉。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Opening_a_Window"></a>   
### 開啟視窗  
 若要開啟視窗，您要先建立其執行個體，如下列範例所示範。  
  
 [!code-xml[WindowsOverviewStartupEventSnippets#AppMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 本範例中，`MarkupAndCodeBehindWindow` 是在應用程式啟動時具現化的，也就是在引發 <xref:System.Windows.Application.Startup> 事件的時間發生。  
  
 具現化視窗時，視窗的參考會自動加入到由 <xref:System.Windows.Application> 物件所管理的視窗清單 \(請參閱 <xref:System.Windows.Application.Windows%2A?displayProperty=fullName>\)。  除此之外，根據預設，第一個具現化的視窗是由 <xref:System.Windows.Application> 設定為主應用程式視窗 \(請參閱 <xref:System.Windows.Application.MainWindow%2A?displayProperty=fullName>\)。  
  
 最後會藉由呼叫 <xref:System.Windows.Window.Show%2A> 方法開啟視窗，結果顯示如下圖。  
  
 ![呼叫 Window.Show 而開啟的視窗](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")  
  
 藉由呼叫 <xref:System.Windows.Window.Show%2A> 所開啟的視窗是非強制回應 \(Modeless\) 視窗，這代表應用程式運作的模式可以讓使用者在相同應用程式中啟動其他視窗。  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A> 的呼叫是用來以強制回應的方式開啟對話方塊這類的視窗。  如需詳細資訊，請參閱[對話方塊概觀](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)。  
  
 呼叫 <xref:System.Windows.Window.Show%2A> 時，視窗會在顯示前先執行初始化工作，以建立可以讓視窗接收使用者輸入的基礎結構。  初始化視窗時，會引發 <xref:System.Windows.Window.SourceInitialized> 事件並顯示視窗。  
  
 您可以設定 <xref:System.Windows.Application.StartupUri%2A> 做為捷徑，以指定啟動應用程式時要自動開啟的第一個視窗。  
  
 [!code-xml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 啟動應用程式時，由 <xref:System.Windows.Application.StartupUri%2A> 值所指定的視窗是以非強制回應方式開啟的，而在內部，視窗是藉由呼叫 <xref:System.Windows.Window.Show%2A> 方法開啟的。  
  
<a name="Ownership"></a>   
#### 視窗擁有權  
 藉由使用 <xref:System.Windows.Window.Show%2A> 方法開啟的視窗，與建立該視窗的視窗不會有隱含的關聯性，使用者與任一個視窗的互動都與另一個視窗無關，這代表每個視窗都可以進行下列作業：  
  
-   遮蓋另一個視窗 \(除非其中一個視窗的 <xref:System.Windows.Window.Topmost%2A> 屬性設為 `true`\)。  
  
-   在不影響另一個視窗的情況下最小化、最大化和還原。  
  
 有些視窗與開啟的來源視窗需要具有關聯性。  舉例來說，[!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] 應用程式可能會開啟的屬性視窗和工具視窗，其一般行為是遮蓋建立這些視窗的視窗。  再者，這類視窗總是會與建立它們的視窗協同作業而關閉、最小化、最大化和還原。  這樣的關聯性，可以藉由讓一個視窗「*擁有*」\(Own\) 另一個視窗來建立，且可以藉由設定「*附屬視窗*」\(Owned Window\) 的 <xref:System.Windows.Window.Owner%2A> 屬性搭配「*主控視窗*」\(Owner Window\) 的參考來達成。  這在下列範例中顯示。  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 擁有權建立後：  
  
-   附屬視窗可以藉由偵測其 <xref:System.Windows.Window.Owner%2A> 屬性值，來參考主控視窗。  
  
-   主控視窗可以藉由偵測其 <xref:System.Windows.Window.OwnedWindows%2A> 屬性值，來探索它擁有的所有視窗。  
  
<a name="Preventing"></a>   
#### 避免視窗啟動  
 在某些情況中，視窗在顯示時不應該啟動，例如網際網路 Messenger 類型應用程式的交談視窗，或電子郵件應用程式的通知視窗。  
  
 如果您的應用程式有視窗在顯示時不應該啟動，您可以在首次呼叫 <xref:System.Windows.Window.Show%2A> 方法前，將應用程式的 <xref:System.Windows.Window.ShowActivated%2A> 屬性設定為 `false`。  結果如下：  
  
-   視窗不會啟動。  
  
-   不會引發視窗的 <xref:System.Windows.Window.Activated> 事件。  
  
-   目前已啟動的視窗還是維持已啟動的狀態。  
  
 不過只要使用者按一下用戶端或非用戶端區域，這個視窗還是會啟動。  在此情況下：  
  
-   視窗會啟動。  
  
-   會引發視窗的 <xref:System.Windows.Window.Activated> 事件。  
  
-   先前已啟動的視窗會停用。  
  
-   接下來會如預期般根據使用者的動作做出回應，引發視窗的 <xref:System.Windows.Window.Deactivated> 和 <xref:System.Windows.Window.Activated> 事件。  
  
<a name="Window_Activation"></a>   
### 視窗啟動  
 第一次開啟視窗時，視窗會成為使用中視窗 \(除非其 <xref:System.Windows.Window.ShowActivated%2A> 設定為 `false` 而顯示\)。  「*使用中視窗*」\(Active Window\) 是目前會捕捉使用者輸入的視窗，例如按鍵和滑鼠點按這類輸入。  當視窗成為使用中時，會引發 <xref:System.Windows.Window.Activated> 事件。  
  
> [!NOTE]
>  第一次開啟視窗時，<xref:System.Windows.FrameworkElement.Loaded> 和 <xref:System.Windows.Window.ContentRendered> 事件只會在引發 <xref:System.Windows.Window.Activated> 事件後引發。  記住這一點，視窗實際上可以視為是在引發 <xref:System.Windows.Window.ContentRendered> 時開啟的。  
  
 視窗成為使用中後，使用者可以在相同應用程式中啟動其他視窗，或是啟動其他應用程式。  發生這個情況時，目前使用中視窗會成為停用狀態，並引發 <xref:System.Windows.Window.Deactivated> 事件。  同樣地，當使用者選取目前停用的視窗，視窗會再度成為使用中並引發 <xref:System.Windows.Window.Activated>。  
  
 處理 <xref:System.Windows.Window.Activated> 和 <xref:System.Windows.Window.Deactivated> 的一個原因，在於啟用或停用只能夠在視窗使用中執行的功能。  舉例來說，有些視窗會顯示需要使用者持續輸入和注意的互動式內容，包括遊戲和視訊播放程式。  下列範例中簡化的視訊播放程式，會示範如何處理 <xref:System.Windows.Window.Activated> 和 <xref:System.Windows.Window.Deactivated> 以實作這個行為。  
  
 [!code-xml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 當視窗停用時，其他類型的應用程式可能仍會在背景執行程式碼。  舉例來說，當使用者使用其他應用程式時，郵件用戶端可能會繼續輪詢郵件伺服器。  這類的應用程式在主視窗停用時，常會提供不同的或其他的行為。  對於郵件程式而言，這可能代表會將新郵件項目加入到收件匣中，同時在系統匣中加入告知圖示。  只有在郵件視窗不在使用中時，才需要顯示告知圖示，這是藉由偵測 <xref:System.Windows.Window.IsActive%2A> 屬性而決定的。  
  
 當背景工作完成時，視窗可能會想要藉由呼叫 <xref:System.Windows.Window.Activate%2A> 方法，以更為緊急的方式告知使用者。  在呼叫 <xref:System.Windows.Window.Activate%2A> 時，如果使用者正在與其他使用中應用程式互動，視窗的工作列按鈕就會閃爍。  如果使用者正在與目前應用程式互動，呼叫 <xref:System.Windows.Window.Activate%2A> 會將視窗帶到前景中。  
  
> [!NOTE]
>  您可以使用 <xref:System.Windows.Application.Activated?displayProperty=fullName> 和 <xref:System.Windows.Application.Deactivated?displayProperty=fullName> 事件，處理應用程式範圍的啟動。  
  
<a name="Closing_a_Window"></a>   
### 關閉視窗  
 視窗的存留是從啟動開始，持續到使用者關閉它為止。  視窗的關閉可以藉由使用非工作區的項目，包括下列項目：  
  
-   \[**系統**\] 功能表的 \[**關閉**\] 項目。  
  
-   按 ALT\+F4。  
  
-   按 \[**關閉**\] 按鈕。  
  
 您可以提供其他的機制供工作區關閉視窗，較為常用的機制包括下列項目：  
  
-   \[**檔案**\] 功能表中的 \[**結束**\] 項目，通常用於主應用程式視窗。  
  
-   \[**檔案**\] 功能表中的 \[**關閉**\] 項目，通常用於次要應用程式視窗。  
  
-   \[**取消**\] 按鈕，通常用於強制回應對話方塊。  
  
-   \[**關閉**\] 按鈕，通常用於非強制回應對話方塊。  
  
 若要關閉視窗以回應其中一個自訂機制，需要呼叫 <xref:System.Windows.Window.Close%2A> 方法。  下列範例實作的能力，可以藉由選擇 \[**檔案**\] 功能表中的 \[**結束**\] 關閉視窗。  
  
 [!code-xml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 視窗關閉時會引發兩個事件：<xref:System.Windows.Window.Closing> 和 <xref:System.Windows.Window.Closed>。  
  
 <xref:System.Windows.Window.Closing> 是在視窗關閉前引發的，所提供的機制可以防止視窗關閉。  防止視窗關閉的一個原因，是針對視窗內容包含修改過的資料時。  在這種情況下，<xref:System.Windows.Window.Closing> 事件的處理可以判斷資料是否經過變更，如果是的話，將詢問使用者是否要繼續關閉視窗而不儲存資料，或者是取消視窗關閉。  下列範例顯示處理 <xref:System.Windows.Window.Closing> 的主要方向。  
  
 [!code-csharp[WindowClosingSnippets#WindowClosingCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs#windowclosingcodebehind1)]
 [!code-vb[WindowClosingSnippets#WindowClosingCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb#windowclosingcodebehind1)]  
[!code-csharp[WindowClosingSnippets#WindowClosingCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs#windowclosingcodebehind2)]
[!code-vb[WindowClosingSnippets#WindowClosingCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb#windowclosingcodebehind2)]  
  
 <xref:System.Windows.Window.Closing> 事件處理常式傳遞的 <xref:System.ComponentModel.CancelEventArgs>，會實作您設定為 `true` 的 `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 屬性，以防止視窗關閉。  
  
 如果沒有處理 <xref:System.Windows.Window.Closing>，或是處理作業遭到取消，就會關閉視窗。  就在視窗要確實關閉前一刻，會引發 <xref:System.Windows.Window.Closed>。  此時就無法防止視窗關閉。  
  
> [!NOTE]
>  您可以設定應用程式在主應用程式視窗關閉時 \(請參閱 <xref:System.Windows.Application.MainWindow%2A>\) 或者是最後一個視窗關閉時自動關閉。  如需詳細資訊，請參閱<xref:System.Windows.Application.ShutdownMode%2A>。  
  
 雖然視窗可以透過非工作區和工作區所提供的機制明確關閉，但視窗也可以因為應用程式其他部分或 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 的行為而隱含關閉，包括下列行為：  
  
-   使用者登出或關閉 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)]。  
  
-   視窗的主控視窗關閉 \(請參閱 <xref:System.Windows.Window.Owner%2A>\)。  
  
-   主應用程式視窗關閉，且 <xref:System.Windows.Application.ShutdownMode%2A> 為 <xref:System.Windows.ShutdownMode>。  
  
-   呼叫 <xref:System.Windows.Application.Shutdown%2A>。  
  
> [!NOTE]
>  視窗關閉後無法重新開啟。  
  
<a name="Window_Lifetime_Events"></a>   
### 視窗存留期事件  
 下圖顯示視窗存留期中的主體事件序列。  
  
 ![視窗存留期](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")  
  
 下圖顯示在顯示時未啟動的視窗在存留期中的主體事件序列 \(<xref:System.Windows.Window.ShowActivated%2A> 在視窗顯示前設定為 `false`\)。  
  
 ![視窗存留期 &#40;Window.ShowActivated &#61; False&#41;](../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")  
  
<a name="WindowLocation"></a>   
## 視窗位置  
 視窗開啟時，會有相對於桌面的 x 和 y 維度位置。  這個位置的判斷可以藉由偵測相對的 <xref:System.Windows.Window.Left%2A> 和 <xref:System.Windows.Window.Top%2A> 屬性。  您可以設定這些屬性以變更視窗的位置。  
  
 您也可以指定 <xref:System.Windows.Window> 第一次出現時的初始位置，方法是以下列其中一個 <xref:System.Windows.WindowStartupLocation> 列舉值設定 <xref:System.Windows.Window.WindowStartupLocation%2A> 屬性：  
  
-   <xref:System.Windows.WindowStartupLocation> \(預設值\)  
  
-   <xref:System.Windows.WindowStartupLocation>  
  
-   <xref:System.Windows.WindowStartupLocation>  
  
 如果啟動位置是指定為 <xref:System.Windows.WindowStartupLocation>，而且沒有設定 <xref:System.Windows.Window.Left%2A> 和 <xref:System.Windows.Window.Top%2A> 屬性，<xref:System.Windows.Window> 將會詢問 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 要在什麼位置出現視窗。  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### 最上層顯示視窗和疊置順序  
 除了具有 x 和 y 位置之外，視窗在 z 維度也是有位置的，這是用來決定相對於其他視窗的垂直位置。  這就是所謂的疊置順序，包含兩種類型：一般疊置順序和最上層疊置順序。  「*一般疊置順序*」\(Normal Z\-order\) 中的視窗位置，是由視窗目前是否為使用中決定。  根據預設，視窗會位於一般疊置順序中。  「*最上層疊置順序*」\(Topmost Z\-order\) 中的視窗位置，也是由視窗目前是否為使用中決定。  此外，最上層疊置順序的視窗永遠會位在一般疊置順序的視窗上方。  藉由將視窗的 <xref:System.Windows.Window.Topmost%2A> 屬性設定為 `true`，視窗就會位於最上層疊置順序。  
  
 [!code-xml[WindowsOverviewSnippets#TopmostWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#TopmostWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup2)]  
  
 在每個疊置順序內，目前使用中視窗會出現在相同疊置順序中的所有其他視窗上方。  
  
<a name="WindowSize"></a>   
## 視窗大小  
 除了具有桌面位置外，視窗的大小是由數種屬性決定的，包括各種的寬度和高度屬性，以及 <xref:System.Windows.Window.SizeToContent%2A>。  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>、<xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 是用於管理視窗在存留期中可以有的寬度範圍，設定方式如下列範例所示。  
  
 [!code-xml[WindowsOverviewSnippets#WidthWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#WidthWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup2)]  
  
 視窗高度是由 <xref:System.Windows.FrameworkElement.MinHeight%2A>、<xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 所管理的，設定方式如下列範例所示。  
  
 [!code-xml[WindowsOverviewSnippets#HeightWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#HeightWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup2)]  
  
 因為各種寬度值和高度值每種都會指定範圍，所以可調整大小視窗的寬度和高度，有可能在各自維度所指定範圍內的任何地方。  若要偵測目前寬度和高度，請分別偵測 <xref:System.Windows.FrameworkElement.ActualWidth%2A> 和 <xref:System.Windows.FrameworkElement.ActualHeight%2A>。  
  
 如果您希望視窗的寬度和高度，能夠依據視窗內容調整大小，您可以使用具有下列值的 <xref:System.Windows.Window.SizeToContent%2A> 屬性：  
  
-   <xref:System.Windows.SizeToContent>.  沒有作用 \(預設值\)。  
  
-   <xref:System.Windows.SizeToContent>.  調整成內容寬度的大小，效果跟將 <xref:System.Windows.FrameworkElement.MinWidth%2A> 和 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 設定為內容寬度一樣。  
  
-   <xref:System.Windows.SizeToContent>.  調整成內容高度的大小，效果跟將 <xref:System.Windows.FrameworkElement.MinHeight%2A> 和 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 設定為內容高度一樣。  
  
-   <xref:System.Windows.SizeToContent>.  調整成內容寬度和高度的大小，效果跟將 <xref:System.Windows.FrameworkElement.MinHeight%2A> 和 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 設定為內容高度，並將 <xref:System.Windows.FrameworkElement.MinWidth%2A> 和 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 設定為內容寬度一樣。  
  
 下列範例示範，能自動地大小以符合其內容，垂直和水平\-第一次顯示一個視窗。  
  
 [!code-xml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#SizeToContentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup2)]  
  
 下列範例會示範如何設定<xref:System.Windows.Window.SizeToContent%2A>屬性來指定視窗會調整大小以配合其內容的程式碼中。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## 調整大小屬性的優先順序  
 基本上，視窗的各種大小屬性結合，可以定義可調整大小視窗的寬度和高度範圍。  為了確保維持有效的範圍，<xref:System.Windows.Window> 會使用下列優先順序評估大小屬性的值。  
  
 **針對高度屬性：**  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=fullName> \>  
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=fullName> \>  
  
3.  <xref:System.Windows.SizeToContent?displayProperty=fullName>\/<xref:System.Windows.SizeToContent?displayProperty=fullName> \>  
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=fullName>  
  
 **針對寬度屬性：**  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=fullName> \>  
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=fullName> \>  
  
3.  <xref:System.Windows.SizeToContent?displayProperty=fullName>\/<xref:System.Windows.SizeToContent?displayProperty=fullName> \>  
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=fullName>  
  
 優先順序也可以決定視窗最大化時的大小，這是使用 <xref:System.Windows.Window.WindowState%2A> 屬性決定的。  
  
<a name="WindowState"></a>   
## 視窗狀態  
 可調整大小視窗在存留期中可以有三種狀態：標準、最小化和最大化。  具有「*標準*」\(Normal\) 狀態的視窗是視窗的預設狀態。  這種狀態的視窗如果是可調整大小的話，則可以讓使用者藉由使用調整大小底框或框線來移動或調整大小。  
  
 具有「*最小化*」\(Minimized\) 狀態的視窗，如果其 <xref:System.Windows.Window.ShowInTaskbar%2A> 設定為 `true` 時，會將視窗摺疊至工作列按鈕，否則會盡可能摺疊到最小並將視窗本身的位置重新調整到桌面左下角。  這兩種類型的最小化視窗都不能使用框線或調整大小底框來調整大小，雖然沒有顯示在工作列的最小化視窗是可以在桌面上拖曳的。  
  
 具有「*最大化*」\(Maximized\) 狀態的視窗，會盡可能擴展到最大化大小，最大只能到其 <xref:System.Windows.FrameworkElement.MaxWidth%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A> 和 <xref:System.Windows.Window.SizeToContent%2A> 屬性所支配的大小。  如同最小化視窗一樣，最大化視窗不能使用調整大小底框或拖曳框線來調整大小。  
  
> [!NOTE]
>  視窗的 <xref:System.Windows.Window.Top%2A>、<xref:System.Windows.Window.Left%2A>、<xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性值永遠表示正常狀態下的值，即使視窗目前已最大化或最小化也一樣。  
  
 視窗狀態的設定可以藉由設定其 <xref:System.Windows.Window.WindowState%2A> 屬性來達成，該屬性可以有下列其中一個 <xref:System.Windows.WindowState> 列舉值：  
  
-   <xref:System.Windows.WindowState> \(預設值\)  
  
-   <xref:System.Windows.WindowState>  
  
-   <xref:System.Windows.WindowState>  
  
 下列範例顯示如何建立在開啟視窗時顯示為最大化的視窗。  
  
 [!code-xml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#WindowStateWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup2)]  
  
 一般而言，您應該設定 <xref:System.Windows.Window.WindowState%2A> 以設定視窗的初始狀態。  在可調整大小視窗顯示後，使用者就可以按視窗標題列的最小化、最大化和還原按鈕，變更視窗狀態。  
  
<a name="WindowAppearance"></a>   
## 視窗外觀  
 藉由加入視窗特定的內容，例如按鈕、標籤和文字方塊，您可以變更視窗工作區的外觀。  為了設定非工作區，<xref:System.Windows.Window> 提供數種屬性，包括用於設定視窗圖示的 <xref:System.Windows.Window.Icon%2A> 以及用於設定標題的 <xref:System.Windows.Window.Title%2A>。  
  
 您也可以變更非工作區框線的外觀和行為，方法是藉由設定視窗的調整大小模式、視窗樣式，以及是否要在桌面工作列顯示為按鈕。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Resize_Mode"></a>   
### 調整大小模式  
 依據 <xref:System.Windows.Window.WindowStyle%2A> 屬性，您可以控制使用者調整視窗大小的方式 \(以及使用者是否能調整視窗大小\)。  視窗樣式的選擇會影響到下列項目：使用者是否可以藉由滑鼠拖曳框線來調整大小、非工作區是否要顯示 \[**最小化**\]、\[**最大化**\] 和 \[**調整大小**\] 按鈕，以及在顯示這些按鈕的情況下是否要啟用這些按鈕。  
  
 視窗調整大小的方式可以藉由設定其 <xref:System.Windows.Window.ResizeMode%2A> 屬性來設定，該屬性可以是下列其中一個 <xref:System.Windows.ResizeMode> 列舉值：  
  
-   <xref:System.Windows.ResizeMode>  
  
-   <xref:System.Windows.ResizeMode>  
  
-   <xref:System.Windows.ResizeMode> \(預設值\)  
  
-   <xref:System.Windows.ResizeMode>  
  
 跟 <xref:System.Windows.Window.WindowStyle%2A> 一樣，視窗的調整大小模式在存留期間不太會變更，這代表您最可能會在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記設定這個屬性。  
  
 [!code-xml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#ResizeModeWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup2)]  
  
 請注意，藉由偵測 <xref:System.Windows.Window.WindowState%2A> 屬性，您可以偵測視窗是否最大化、最小化或還原。  
  
<a name="Window_Style"></a>   
### 視窗樣式  
 視窗非工作區所公開的框線適用於大部分應用程式。  然而，有些情況下，依據視窗的類型，會需要不同類型的框線，或是根本不需要框線。  
  
 若要控制視窗要取得什麼類型的框線，您可以設定 <xref:System.Windows.Window.WindowStyle%2A> 屬性，搭配下列其中一個 <xref:System.Windows.WindowStyle> 列舉值：  
  
-   <xref:System.Windows.WindowStyle>  
  
-   <xref:System.Windows.WindowStyle> \(預設值\)  
  
-   <xref:System.Windows.WindowStyle>  
  
-   <xref:System.Windows.WindowStyle>  
  
 下圖說明這些視窗樣式的效果。  
  
 ![視窗樣式](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.png "WindowOverviewFigure6")  
  
 您可以使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記或程式碼設定 <xref:System.Windows.Window.WindowStyle%2A>，因為這個屬性在視窗存留期間不太會變更，而您最可能會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記進行設定。  
  
 [!code-xml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#WindowStyleWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup2)]  
  
#### 非矩形視窗樣式  
 有的時候，<xref:System.Windows.Window.WindowStyle%2A> 所允許您使用的框線樣式並不足夠。  舉例來說，您可能會想建立非矩形框線的應用程式，就像 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 所使用的。  
  
 例如，您可以考慮下圖顯示的文字泡泡視窗。  
  
 ![非矩形視窗](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")  
  
 這類型視窗的建立方式可以藉由將 <xref:System.Windows.Window.WindowStyle%2A> 屬性設定為 <xref:System.Windows.WindowStyle>，並使用 <xref:System.Windows.Window> 針對透明度的特殊支援。  
  
 [!code-xml[WindowsOverviewSnippets#TransparentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#TransparentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup2)]  
  
 這項值的組合所建構的視窗會呈現完全透明狀。  在這種情況下，視窗的非工作區裝飾項目 \(\[關閉\] 功能表、\[最小化\]、\[最大化\] 和 \[還原\] 按鈕等等\) 就無法使用。  因此，就需要提供您自己的裝飾項目。  
  
<a name="Task_Bar_Presence"></a>   
### 工作列的存在  
 視窗的預設外觀包含工作列按鈕，就像下圖所顯示的。  
  
 ![具有工作列按鈕的視窗](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.png "WindowOverviewFigure7")  
  
 有些類型的視窗沒有工作列按鈕，例如訊息方塊和對話方塊 \(請參閱[對話方塊概觀](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)\)。  您可以控制是否要顯示視窗的工作列按鈕，方法是藉由設定 <xref:System.Windows.Window.ShowInTaskbar%2A> 屬性 \(預設為 `true`\)。  
  
 [!code-xml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup2)]  
  
<a name="SecurityConsiderations"></a>   
## 安全性考量  
 <xref:System.Windows.Window> 需要 `UnmanagedCode` 安全性權限才能具現化。  對於在本機電腦上安裝和啟動的應用程式，這屬於授予應用程式的權限集合內。  
  
 然而，對於使用 [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 從網際網路或近端內部網路區域啟動的應用程式而言，這並不在授與該應用程式的權限集合範圍內。  因此，使用者會收到 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 安全性警告，並需要將應用程式的權限集合提高為完全信任。  
  
 此外，根據預設，[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 無法顯示視窗或對話方塊。  如需獨立應用程式安全性考量的討論，請參閱 [WPF 安全性策略 – 平台安全性](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)。  
  
<a name="Other_Types_of_Windows"></a>   
## 其他類型的視窗  
 <xref:System.Windows.Navigation.NavigationWindow> 是設計用來裝載可巡覽內容的視窗。  如需詳細資訊，請參閱[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
 對話方塊則是通常用來向使用者收集資訊以完成運作的視窗。  舉例來說，當使用者要開啟檔案時，應用程式通常會顯示 \[**開啟檔案**\] 對話方塊，以向使用者取得檔名。  如需詳細資訊，請參閱[對話方塊概觀](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Window>   
 <xref:System.Windows.MessageBox>   
 <xref:System.Windows.Navigation.NavigationWindow>   
 <xref:System.Windows.Application>   
 [對話方塊概觀](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)   
 [建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)