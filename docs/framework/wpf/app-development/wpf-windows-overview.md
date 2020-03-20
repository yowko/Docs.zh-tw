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
# <a name="wpf-windows-overview"></a><span data-ttu-id="f6a6d-102">WPF 視窗概觀</span><span class="sxs-lookup"><span data-stu-id="f6a6d-102">WPF Windows Overview</span></span>
<span data-ttu-id="f6a6d-103">使用者通過視窗與 Windows 演示基礎 （WPF） 獨立應用程式進行交互。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="f6a6d-104">視窗的主要用途是裝載內容，以視覺化方式檢視資料，並讓使用者可以與資料互動。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="f6a6d-105">獨立 WPF 應用程式通過使用<xref:System.Windows.Window>類提供自己的視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-105">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="f6a6d-106">本主題在<xref:System.Windows.Window>介紹在獨立應用程式中創建和管理視窗的基礎知識之前介紹。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6a6d-107">瀏覽器託管的 WPF 應用程式（包括 XAML 瀏覽器應用程式 （XBAP） 和鬆散[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]頁面）不提供自己的視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-107">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="f6a6d-108">相反，它們託管在 Windows Internet 資源管理器提供的視窗中。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-108">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="f6a6d-109">請參閱[WPF XAML 瀏覽器應用程式概述](wpf-xaml-browser-applications-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a><span data-ttu-id="f6a6d-110">Window 類別</span><span class="sxs-lookup"><span data-stu-id="f6a6d-110">The Window Class</span></span>  
 <span data-ttu-id="f6a6d-111">下圖說明瞭視窗的組成部分：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![顯示視窗元素的螢幕截圖。](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="f6a6d-113">視窗分為兩個區域︰非工作區和工作區。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="f6a6d-114">視窗*的非工作區*由 WPF 實現，包括大多數視窗共有的視窗部分，包括以下內容：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-114">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="f6a6d-115">框線。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-115">A border.</span></span>  
  
- <span data-ttu-id="f6a6d-116">標題列。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-116">A title bar.</span></span>  
  
- <span data-ttu-id="f6a6d-117">圖示。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-117">An icon.</span></span>  
  
- <span data-ttu-id="f6a6d-118">[最小化]、[最大化] 和 [還原] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="f6a6d-119">[關閉] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-119">A Close button.</span></span>  
  
- <span data-ttu-id="f6a6d-120">[系統] 功能表，具有允許使用者最小化、最大化、還原、移動、調整大小和關閉視窗的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="f6a6d-121">視窗的*工作區*是視窗非工作區中的區域，開發人員使用 它添加特定于應用程式的內容，如功能表列、工具列和控制項。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="f6a6d-122">在 WPF 中，視窗由用於執行<xref:System.Windows.Window>以下操作的類封裝：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-122">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="f6a6d-123">顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-123">Display a window.</span></span>  
  
- <span data-ttu-id="f6a6d-124">設定視窗的大小、位置和外觀。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="f6a6d-125">裝載應用程式特定內容。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="f6a6d-126">管理視窗的存留期。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a><span data-ttu-id="f6a6d-127">實作視窗</span><span class="sxs-lookup"><span data-stu-id="f6a6d-127">Implementing a Window</span></span>  
 <span data-ttu-id="f6a6d-128">典型視窗的實現包括外觀和行為，其中*外觀*定義視窗對使用者的外觀，*行為*定義視窗在使用者與其交互時的工作方式。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="f6a6d-129">在 WPF 中，可以使用代碼或[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記實現視窗的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-129">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="f6a6d-130">但是，通常情況下，視窗的外觀使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記實現，並且其行為使用代碼後面實現，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="f6a6d-131">要使[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記檔和代碼後面檔協同工作，需要：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="f6a6d-132">在標記中，`Window`元素必須包括屬性。 `x:Class`</span><span class="sxs-lookup"><span data-stu-id="f6a6d-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="f6a6d-133">生成應用程式`x:Class`時，標記檔中的存在會導致 Microsoft 生成引擎 （MSBuild） 創建派生`partial`自<xref:System.Windows.Window>並具有`x:Class`屬性指定的名稱的類。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-133">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="f6a6d-134">這需要為[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]架構添加 XML 命名空間聲明 （ `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` 。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-134">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="f6a6d-135">生成的`partial`類實現方法`InitializeComponent`，該方法被調用以註冊事件並設置在標記中實現的屬性。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="f6a6d-136">在代碼後面，類必須是具有標記中屬性`partial`指定的相同名稱的`x:Class`類，並且必須派生自<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="f6a6d-137">這允許代碼背後的檔與生成應用程式時為標記檔生成的`partial`類相關聯（請參閱[構建 WPF 應用程式](building-a-wpf-application-wpf.md)）。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="f6a6d-138">在代碼後面，<xref:System.Windows.Window>類必須實現調用方法的`InitializeComponent`建構函式。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="f6a6d-139">`InitializeComponent`由標記檔的生成`partial`類實現，以註冊事件並設置在標記中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6a6d-140">使用 Visual Studio<xref:System.Windows.Window>向專案添加新專案時，<xref:System.Windows.Window>將使用標記和代碼後面實現 ，並包括創建標記和代碼後面檔之間的關聯的必要配置，如此處所述。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-140">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="f6a6d-141">有了此配置，您可以專注于在標記中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義視窗的外觀，並在代碼後面實現其行為。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="f6a6d-142">下面的示例顯示了一個視窗，其中帶有一個按鈕[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，在標記中實現，並且在代碼後面實現該<xref:System.Windows.Controls.Primitives.ButtonBase.Click>按鈕事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="f6a6d-143">設定 MSBuild 的視窗定義</span><span class="sxs-lookup"><span data-stu-id="f6a6d-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="f6a6d-144">如何實現視窗決定了如何為 MSBuild 配置視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-144">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="f6a6d-145">對於使用標記[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和代碼後面定義的視窗：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="f6a6d-146">XAML 標記檔配置為 MSBuild`Page`項。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-146">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="f6a6d-147">代碼背後的檔配置為 MSBuild`Compile`項。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-147">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="f6a6d-148">這顯示在以下 MSBuild 專案檔案中。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-148">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="f6a6d-149">有關構建 WPF 應用程式的資訊，請參閱[構建 WPF 應用程式](building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-149">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a><span data-ttu-id="f6a6d-150">視窗存留期</span><span class="sxs-lookup"><span data-stu-id="f6a6d-150">Window Lifetime</span></span>  
 <span data-ttu-id="f6a6d-151">如同任何類別，視窗有存留期，會在它一開始具現化時開始，在那之後它會被開啟、啟動和停用，並最終關閉。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a><span data-ttu-id="f6a6d-152">開啟視窗</span><span class="sxs-lookup"><span data-stu-id="f6a6d-152">Opening a Window</span></span>  
 <span data-ttu-id="f6a6d-153">若要開啟視窗，您要先建立它的執行個體，如下列範例中示範。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="f6a6d-154">在此示例中，應用程式啟動時`MarkupAndCodeBehindWindow`具現化，在引發<xref:System.Windows.Application.Startup>事件時發生具現化。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="f6a6d-155">具現化視窗時，對視窗的引用將自動添加到由<xref:System.Windows.Application>物件管理的視窗清單中（請參閱<xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>）。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="f6a6d-156">此外，預設情況下，要具現化的第一個視窗<xref:System.Windows.Application>設置為主應用程式視窗（請參閱<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>）。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="f6a6d-157">最後通過調用<xref:System.Windows.Window.Show%2A>方法打開視窗;結果如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![通過調用視窗打開的視窗。](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="f6a6d-159">通過調用<xref:System.Windows.Window.Show%2A>打開的視窗是一個無強制回應視窗，這意味著應用程式以允許使用者在同一應用程式中啟動其他視窗的模式運行。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6a6d-160"><xref:System.Windows.Window.ShowDialog%2A>調用 以以模式方式打開視窗，如對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="f6a6d-161">有關詳細資訊，請參閱[對話方塊概述](dialog-boxes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="f6a6d-162">調用<xref:System.Windows.Window.Show%2A>時，視窗在顯示建立基礎結構以允許其接收使用者輸入之前執行初始化工作。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="f6a6d-163">初始化視窗時，<xref:System.Windows.Window.SourceInitialized>將引發事件並顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="f6a6d-164">作為快捷方式，<xref:System.Windows.Application.StartupUri%2A>可以設置為指定應用程式啟動時自動打開的第一個視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="f6a6d-165">應用程式啟動時，由 的值<xref:System.Windows.Application.StartupUri%2A>指定的視窗將無模式打開;在內部，視窗通過調用其<xref:System.Windows.Window.Show%2A>方法打開。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a><span data-ttu-id="f6a6d-166">視窗擁有權</span><span class="sxs-lookup"><span data-stu-id="f6a6d-166">Window Ownership</span></span>  
 <span data-ttu-id="f6a6d-167">使用<xref:System.Windows.Window.Show%2A>方法打開的視窗與創建它的視窗沒有隱式關係;因此，使用 方法打開的視窗與創建它的視窗沒有隱式關係。使用者可以獨立于另一個視窗與任一視窗進行交互，這意味著任一視窗都可以執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="f6a6d-168">蓋住另一個視窗（除非其中一個視窗<xref:System.Windows.Window.Topmost%2A>的屬性設置為`true`）。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="f6a6d-169">最小化、最大化和還原而不會影響對方。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="f6a6d-170">某些視窗需要與開啟它們的視窗有關聯性。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="f6a6d-171">例如，整合式開發環境 （IDE） 應用程式可能會打開屬性視窗和工具視窗，其典型行為是覆蓋創建它們的視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-171">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="f6a6d-172">此外，這類視窗應該一律與建立它們的視窗一致地關閉、最小化、最大化和還原。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="f6a6d-173">這種關係可以通過使一個視窗*擁有*另一個視窗來建立，並且通過使用擁有者<xref:System.Windows.Window.Owner%2A>*視窗*來設置*擁有的視窗*的屬性來實現。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="f6a6d-174">下列範例會顯示這一點。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="f6a6d-175">建立擁有權之後︰</span><span class="sxs-lookup"><span data-stu-id="f6a6d-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="f6a6d-176">擁有的視窗可以通過檢查其屬性的值來引用其<xref:System.Windows.Window.Owner%2A>擁有者視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="f6a6d-177">擁有者視窗可以通過檢查其<xref:System.Windows.Window.OwnedWindows%2A>屬性的值來發現它擁有的所有視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a><span data-ttu-id="f6a6d-178">避免視窗啟動</span><span class="sxs-lookup"><span data-stu-id="f6a6d-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="f6a6d-179">在某些情況下，在顯示時不應啟動視窗，例如 Internet 信使式應用程式的交談視窗或電子郵件應用程式的通知視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="f6a6d-180">如果應用程式的視窗在顯示時不應啟動，則可以在首次調用<xref:System.Windows.Window.ShowActivated%2A>`false`<xref:System.Windows.Window.Show%2A>該方法之前將其屬性設置為 。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="f6a6d-181">因此：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-181">As a consequence:</span></span>  
  
- <span data-ttu-id="f6a6d-182">未啟動視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="f6a6d-183">不會引發視窗的事件<xref:System.Windows.Window.Activated>。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="f6a6d-184">目前已啟動的視窗會保持已啟動。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="f6a6d-185">不過，當使用者按一下工作區或非工作區來啟動它時，視窗將會啟動。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="f6a6d-186">在此案例中：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-186">In this case:</span></span>  
  
- <span data-ttu-id="f6a6d-187">視窗已啟動。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-187">The window is activated.</span></span>  
  
- <span data-ttu-id="f6a6d-188">引發視窗的事件<xref:System.Windows.Window.Activated>。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="f6a6d-189">先前已啟動的視窗已停用。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="f6a6d-190">視窗<xref:System.Windows.Window.Deactivated>和<xref:System.Windows.Window.Activated>事件隨後按預期引發，以回應使用者操作。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a><span data-ttu-id="f6a6d-191">視窗啟動</span><span class="sxs-lookup"><span data-stu-id="f6a6d-191">Window Activation</span></span>  
 <span data-ttu-id="f6a6d-192">首次打開視窗時，它將成為使用中視窗（除非將其顯示為<xref:System.Windows.Window.ShowActivated%2A>）。 `false`</span><span class="sxs-lookup"><span data-stu-id="f6a6d-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="f6a6d-193">*使用中視窗*是當前捕獲使用者輸入的視窗，例如擊鍵和滑鼠按一下。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="f6a6d-194">當視窗變為活動狀態時，它會引發<xref:System.Windows.Window.Activated>事件。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6a6d-195">首次打開視窗時，僅在引發<xref:System.Windows.FrameworkElement.Loaded><xref:System.Windows.Window.ContentRendered><xref:System.Windows.Window.Activated>事件後引發 和 事件。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="f6a6d-196">考慮到這一點，在提出時<xref:System.Windows.Window.ContentRendered>，可以有效地考慮打開一個視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="f6a6d-197">視窗成為使用中之後，使用者可以在相同應用程式中啟動另一個視窗，或啟動另一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="f6a6d-198">發生這種情況時，當前使用中視窗將停用並引發事件<xref:System.Windows.Window.Deactivated>。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="f6a6d-199">同樣，當使用者選擇當前停用的視窗時，該視窗將再次變為活動狀態並<xref:System.Windows.Window.Activated>引發。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="f6a6d-200">處理<xref:System.Windows.Window.Activated><xref:System.Windows.Window.Deactivated>的一個常見原因是啟用和禁用只能在視窗處於活動狀態時運行的功能。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="f6a6d-201">例如，某些視窗顯示需要使用者持續輸入和注意的互動式內容，包括遊戲和視訊播放程式。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="f6a6d-202">下面的示例是一個簡化的視頻播放機，演示如何處理<xref:System.Windows.Window.Activated>和<xref:System.Windows.Window.Deactivated>實現此行為。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="f6a6d-203">當視窗已停用時，其他應用程式類型仍然可能會在背景中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="f6a6d-204">例如，當使用者使用其他應用程式時，郵件用戶端可能會繼續輪詢郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="f6a6d-205">這類應用程式在主視窗已停用時，通常會提供不同或其他行為。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="f6a6d-206">對於郵件程式，這可能表示同時將新的郵件項目加入收件匣，並將通知圖示加入系統匣。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="f6a6d-207">僅當郵件視窗不處於活動狀態時，才需要顯示通知圖示，可以通過檢查<xref:System.Windows.Window.IsActive%2A>屬性來確定該圖示。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="f6a6d-208">如果背景工作完成，視窗可能需要通過調用<xref:System.Windows.Window.Activate%2A>方法更緊急地通知使用者。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="f6a6d-209">如果使用者正在與調用時<xref:System.Windows.Window.Activate%2A>啟動的另一個應用程式交互，則視窗的工作列按鈕將閃爍。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="f6a6d-210">如果使用者正在與當前應用程式交互，則調用<xref:System.Windows.Window.Activate%2A>會將視窗帶到前臺。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6a6d-211">您可以使用 和<xref:System.Windows.Application.Activated?displayProperty=nameWithType><xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>事件處理應用程式範圍啟動。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a><span data-ttu-id="f6a6d-212">關閉視窗</span><span class="sxs-lookup"><span data-stu-id="f6a6d-212">Closing a Window</span></span>  
 <span data-ttu-id="f6a6d-213">視窗的存留期在使用者關閉它時開始進入尾聲。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="f6a6d-214">視窗可以使用非工作區中的項目關閉，包括下列項目︰</span><span class="sxs-lookup"><span data-stu-id="f6a6d-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="f6a6d-215">**"關閉"功能表**的 **"關閉**"項。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="f6a6d-216">按下 ALT+F4。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="f6a6d-217">按 **"關閉"** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="f6a6d-218">您可以提供其他機制讓工作區關閉視窗，較常見的包括下列各項︰</span><span class="sxs-lookup"><span data-stu-id="f6a6d-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="f6a6d-219">**"檔**"功能表中的**退出**項，通常用於主應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="f6a6d-220">**"檔**"功能表中的**Close**項，通常在輔助應用程式視窗中。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="f6a6d-221">**取消**按鈕，通常在強制回應對話方塊上。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="f6a6d-222">**關閉**按鈕，通常在無強制回應對話方塊上。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="f6a6d-223">要關閉視窗以回應這些自訂機制之一，您需要調用 方法<xref:System.Windows.Window.Close%2A>。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="f6a6d-224">以下示例通過選擇 **"檔**"功能表上的 **"退出**"來實現關閉視窗的能力。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="f6a6d-225">當視窗關閉時，它將引發兩個事件： <xref:System.Windows.Window.Closing> <xref:System.Windows.Window.Closed>和 。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="f6a6d-226"><xref:System.Windows.Window.Closing>在視窗關閉之前引發，它提供了一種機制，可以阻止視窗關閉。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="f6a6d-227">防止視窗關閉的一個常見原因，是視窗內容包含已修改的資料。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="f6a6d-228">在此情況下，<xref:System.Windows.Window.Closing>可以處理事件以確定資料是否髒，如果是，則詢問使用者是繼續關閉視窗而不保存資料，還是取消視窗關閉。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="f6a6d-229">下面的示例顯示了處理<xref:System.Windows.Window.Closing>的關鍵方面。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="f6a6d-230">事件<xref:System.Windows.Window.Closing>處理常式傳遞 一個<xref:System.ComponentModel.CancelEventArgs>，它實現`Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>設置為`true`防止視窗關閉的屬性。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="f6a6d-231">如果未<xref:System.Windows.Window.Closing>處理，或者處理但未取消，視窗將關閉。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="f6a6d-232">就在視窗實際關閉之前，<xref:System.Windows.Window.Closed>正在引發。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="f6a6d-233">此時無法防止視窗關閉。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6a6d-234">可以將應用程式佈建為在主應用程式視窗關閉（請參閱<xref:System.Windows.Application.MainWindow%2A>）或最後一個視窗關閉時自動關閉。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="f6a6d-235">如需詳細資訊，請參閱<xref:System.Windows.Application.ShutdownMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="f6a6d-236">雖然可以通過非用戶端和工作區中提供的機制顯式關閉視窗，但視窗也可以由於應用程式或 Windows 的其他部分的行為而隱式關閉，包括：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="f6a6d-237">使用者登出或關閉 Windows。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="f6a6d-238">視窗的擁有者關閉（請參閱<xref:System.Windows.Window.Owner%2A>）。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="f6a6d-239">主應用程式視窗已關閉，並且<xref:System.Windows.Application.ShutdownMode%2A>為<xref:System.Windows.ShutdownMode.OnMainWindowClose>。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="f6a6d-240">呼叫 <xref:System.Windows.Application.Shutdown%2A>。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6a6d-241">在關閉之後就無法重新開啟視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a><span data-ttu-id="f6a6d-242">視窗存留期事件</span><span class="sxs-lookup"><span data-stu-id="f6a6d-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="f6a6d-243">下圖顯示了視窗存留期內主體事件的順序：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![顯示視窗存留期內的事件的圖表。](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="f6a6d-245">下圖顯示了不啟動的情況下顯示的視窗存留期內主體事件的順序（<xref:System.Windows.Window.ShowActivated%2A>設置為`false`在顯示視窗之前）：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![顯示視窗存留期內的事件而不啟動的圖表。](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a><span data-ttu-id="f6a6d-247">視窗位置</span><span class="sxs-lookup"><span data-stu-id="f6a6d-247">Window Location</span></span>  
 <span data-ttu-id="f6a6d-248">視窗開啟時，它會有相對於桌面的 x 和 y 維度位置。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="f6a6d-249">此位置可以通過分別檢查 和<xref:System.Windows.Window.Left%2A><xref:System.Windows.Window.Top%2A>屬性來確定。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="f6a6d-250">您可以設定這些屬性，以變更視窗的位置。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="f6a6d-251">還可以通過使用以下<xref:System.Windows.Window><xref:System.Windows.Window.WindowStartupLocation%2A><xref:System.Windows.WindowStartupLocation>枚舉值之一設置屬性來指定首次出現 時的初始位置：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="f6a6d-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (預設值)</span><span class="sxs-lookup"><span data-stu-id="f6a6d-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="f6a6d-253">如果啟動位置<xref:System.Windows.WindowStartupLocation.Manual>指定為 ，並且 尚未<xref:System.Windows.Window.Left%2A>設置<xref:System.Windows.Window.Top%2A>和 屬性，<xref:System.Windows.Window>則請求 Windows 顯示位置。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="f6a6d-254">最上層視窗和疊置順序</span><span class="sxs-lookup"><span data-stu-id="f6a6d-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="f6a6d-255">除了有 x 和 y 位置，視窗也有 z 維度的位置，這決定了它相對於其他視窗的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="f6a6d-256">這稱為視窗的疊置順序，並且有兩種類型︰一般疊置順序和最上層疊置順序。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="f6a6d-257">視窗在正常*z 順序*中的位置由視窗當前是否處於活動狀態決定。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="f6a6d-258">根據預設，視窗位於一般疊置順序。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="f6a6d-259">視窗在*最頂層 z 順序*中的位置也取決於視窗當前是否處於活動狀態。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="f6a6d-260">此外，最上層疊置順序的視窗一定會位於一般疊置順序的視窗之上。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="f6a6d-261">視窗通過將屬性<xref:System.Windows.Window.Topmost%2A>設置為`true`位於最上面的 z 順序中。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="f6a6d-262">在每個疊置順序內，目前使用中視窗會顯示在相同疊置順序中的所有其他視窗之上。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>
## <a name="window-size"></a><span data-ttu-id="f6a6d-263">視窗大小</span><span class="sxs-lookup"><span data-stu-id="f6a6d-263">Window Size</span></span>  
 <span data-ttu-id="f6a6d-264">除了具有桌面位置外，視窗的大小由多個屬性確定，包括各種寬度和高度屬性和<xref:System.Windows.Window.SizeToContent%2A>。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="f6a6d-265"><xref:System.Windows.FrameworkElement.MinWidth%2A><xref:System.Windows.FrameworkElement.Width%2A>，<xref:System.Windows.FrameworkElement.MaxWidth%2A>用於管理視窗在其存留期內可以具有的寬度範圍，並配置如下示例所示。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="f6a6d-266">視窗高度由<xref:System.Windows.FrameworkElement.MinHeight%2A><xref:System.Windows.FrameworkElement.Height%2A>和 和<xref:System.Windows.FrameworkElement.MaxHeight%2A>進行管理，並配置如下示例所示。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="f6a6d-267">因為各種寬度值和高度值都各指定一個範圍，所以可調整大小視窗的高度與寬度可能會是個別維度的指定範圍內的任何位置。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="f6a6d-268">要檢測其當前寬度和高度，分別<xref:System.Windows.FrameworkElement.ActualWidth%2A>檢查<xref:System.Windows.FrameworkElement.ActualHeight%2A>和 。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="f6a6d-269">如果希望視窗的寬度和高度具有適合視窗內容大小的大小，則可以使用 具有以下值<xref:System.Windows.Window.SizeToContent%2A>的屬性：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="f6a6d-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="f6a6d-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="f6a6d-271">無效果 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-271">No effect (default).</span></span>  
  
- <span data-ttu-id="f6a6d-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="f6a6d-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="f6a6d-273">適合內容寬度，其效果與設置內容<xref:System.Windows.FrameworkElement.MinWidth%2A>和<xref:System.Windows.FrameworkElement.MaxWidth%2A>內容寬度的效果相同。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="f6a6d-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="f6a6d-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="f6a6d-275">適合內容高度，這與設置內容<xref:System.Windows.FrameworkElement.MinHeight%2A>的高度和<xref:System.Windows.FrameworkElement.MaxHeight%2A>內容的高度具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="f6a6d-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="f6a6d-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="f6a6d-277">適合內容<xref:System.Windows.FrameworkElement.MinHeight%2A>寬度和高度，其效果與設置內容的高度以及<xref:System.Windows.FrameworkElement.MaxHeight%2A>設置內容<xref:System.Windows.FrameworkElement.MinWidth%2A>的寬度和<xref:System.Windows.FrameworkElement.MaxWidth%2A>寬度的效果相同。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="f6a6d-278">下列範例顯示自動調整垂直和水平大小以符合其內容的視窗，第一次顯示時的樣子。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="f6a6d-279">下面的示例演示如何在代碼中設置<xref:System.Windows.Window.SizeToContent%2A>屬性以指定視窗如何調整大小以適合其內容。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="f6a6d-280">調整大小屬性優先順序</span><span class="sxs-lookup"><span data-stu-id="f6a6d-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="f6a6d-281">基本上，視窗的各種大小屬性會合併起來定義可調整大小的視窗的寬度和高度範圍。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="f6a6d-282">為確保保持有效範圍，<xref:System.Windows.Window>請使用以下優先順序順序計算大小屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="f6a6d-283">**針對高度屬性：**</span><span class="sxs-lookup"><span data-stu-id="f6a6d-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="f6a6d-284">**針對寬度屬性：**</span><span class="sxs-lookup"><span data-stu-id="f6a6d-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="f6a6d-285">優先順序順序還可以確定視窗在最大化時的大小，該視窗使用<xref:System.Windows.Window.WindowState%2A>屬性進行管理。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>
## <a name="window-state"></a><span data-ttu-id="f6a6d-286">視窗狀態</span><span class="sxs-lookup"><span data-stu-id="f6a6d-286">Window State</span></span>  
 <span data-ttu-id="f6a6d-287">在可調整大小的視窗存留期中，它可以有三種狀態︰標準、最小化及最大化。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="f6a6d-288">具有*正常*狀態的視窗是視窗的預設狀態。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="f6a6d-289">這種狀態的視窗可以讓使用者移動並使用調整大小底框或框線調整其大小，如果它可調整大小。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="f6a6d-290">具有*最小化*狀態的視窗將折疊到其工作列按鈕（如果<xref:System.Windows.Window.ShowInTaskbar%2A>設置為`true`;否則，它會折疊到盡可能小的大小，並重新置放到桌面的左下角。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="f6a6d-291">最小化視窗的類型都無法使用框線或調整大小底框來調整大小，雖然未顯示在工作列中的最小化視窗可以在桌面拖曳。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="f6a6d-292">具有*最大化*狀態的視窗將擴展到其可以的最大大小，該大小將僅與其<xref:System.Windows.FrameworkElement.MaxWidth%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>和<xref:System.Windows.Window.SizeToContent%2A>屬性規定的大小一樣大。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="f6a6d-293">就像最小化的視窗，最大化的視窗無法使用調整大小底框或藉由拖曳框線來調整大小。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6a6d-294"><xref:System.Windows.Window.Top%2A>視窗的值<xref:System.Windows.Window.Left%2A><xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性始終表示正常狀態的值，即使視窗當前正在最大化或最小化也是如此。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="f6a6d-295">可以通過設置其<xref:System.Windows.Window.WindowState%2A>屬性來配置視窗的狀態，該屬性可以具有以下<xref:System.Windows.WindowState>枚舉值之一：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="f6a6d-296"><xref:System.Windows.WindowState.Normal> (預設值)</span><span class="sxs-lookup"><span data-stu-id="f6a6d-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="f6a6d-297">下列範例示範如何建立在開啟時會顯示為最大化的視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="f6a6d-298">通常，應設置為<xref:System.Windows.Window.WindowState%2A>配置視窗的初始狀態。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="f6a6d-299">可調整大小的視窗顯示後，使用者可以按下視窗標題列上的最小化、最大化和還原按鈕，以變更視窗狀態。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a><span data-ttu-id="f6a6d-300">視窗外觀</span><span class="sxs-lookup"><span data-stu-id="f6a6d-300">Window Appearance</span></span>  
 <span data-ttu-id="f6a6d-301">您可以新增視窗特定的內容，例如按鈕、標籤和文字方塊，來變更視窗工作區的外觀。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="f6a6d-302">要配置非工作區，<xref:System.Windows.Window>請提供多個屬性，其中包括<xref:System.Windows.Window.Icon%2A>設置視窗的圖示並<xref:System.Windows.Window.Title%2A>設置其標題。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="f6a6d-303">您也可以藉由設定視窗的調整大小模式、視窗樣式，以及它是否顯示為桌面工作列上的按鈕，變更非工作區框線的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a><span data-ttu-id="f6a6d-304">調整大小模式</span><span class="sxs-lookup"><span data-stu-id="f6a6d-304">Resize Mode</span></span>  
 <span data-ttu-id="f6a6d-305">根據屬性，<xref:System.Windows.Window.WindowStyle%2A>您可以控制使用者調整視窗大小的方式（以及是否）大小。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="f6a6d-306">視窗樣式的選擇會影響使用者是否可以通過拖動視窗與滑鼠的邊框來調整視窗的大小，是否在非工作區上顯示 **"最小化**"、**最大化**和**調整大小**按鈕，如果確實出現，則是否啟用了這些按鈕。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="f6a6d-307">您可以通過設置視窗<xref:System.Windows.Window.ResizeMode%2A>的屬性（可以是以下<xref:System.Windows.ResizeMode>枚舉值之一）來配置視窗的大小大小：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="f6a6d-308"><xref:System.Windows.ResizeMode.CanResize> (預設值)</span><span class="sxs-lookup"><span data-stu-id="f6a6d-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="f6a6d-309">與<xref:System.Windows.Window.WindowStyle%2A>，視窗的調整大小模式在其存留期內不太可能更改，這意味著您很可能從[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記中設置它。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="f6a6d-310">請注意，您可以通過檢查<xref:System.Windows.Window.WindowState%2A>屬性來檢測視窗是最大化、最小化還是還原。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>
### <a name="window-style"></a><span data-ttu-id="f6a6d-311">視窗樣式</span><span class="sxs-lookup"><span data-stu-id="f6a6d-311">Window Style</span></span>  
 <span data-ttu-id="f6a6d-312">從視窗非工作區公開的框線適用於大部分的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="f6a6d-313">不過，有一些情況下需要不同型別的框線，或是完全不需要框線，視視窗的型別而定。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="f6a6d-314">要控制視窗獲取的邊框類型，您需要使用枚<xref:System.Windows.Window.WindowStyle%2A><xref:System.Windows.WindowStyle>舉的以下值之一設置其屬性：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="f6a6d-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (預設值)</span><span class="sxs-lookup"><span data-stu-id="f6a6d-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="f6a6d-316">下圖說明瞭這些視窗樣式的效果：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![視窗邊框樣式的插圖。](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="f6a6d-318">您可以使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記或<xref:System.Windows.Window.WindowStyle%2A>代碼進行設置;因為它不太可能在視窗的存留期內更改，因此您很可能使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記來配置它。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="f6a6d-319">非矩形視窗樣式</span><span class="sxs-lookup"><span data-stu-id="f6a6d-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="f6a6d-320">還在某些情況下，<xref:System.Windows.Window.WindowStyle%2A>允許您擁有的邊界樣式是不夠的。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="f6a6d-321">例如，您可能希望創建具有非矩形邊框的應用程式，如 Microsoft Windows 媒體播放機使用。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-321">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="f6a6d-322">例如，請考慮下圖中顯示的語音氣泡視窗：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![一個語音氣泡視窗，上面寫著"拖動我"。](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="f6a6d-324">可以通過將<xref:System.Windows.Window.WindowStyle%2A>屬性設置為<xref:System.Windows.WindowStyle.None>和 使用<xref:System.Windows.Window>具有透明度的特殊支援來創建這種類型的視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="f6a6d-325">這些值的組合會指示視窗要轉譯為完全透明。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="f6a6d-326">在此狀態下，無法使用視窗的非工作區裝飾 ([關閉] 功能表、[最小化]、[最大化] 和 [還原] 按鈕等等)。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="f6a6d-327">因此，您需要自行提供。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a><span data-ttu-id="f6a6d-328">工作列目前狀態</span><span class="sxs-lookup"><span data-stu-id="f6a6d-328">Task Bar Presence</span></span>  

<span data-ttu-id="f6a6d-329">視窗的預設面板包括工作列按鈕，如圖所示：</span><span class="sxs-lookup"><span data-stu-id="f6a6d-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![顯示帶有工作列按鈕的視窗的螢幕截圖。](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="f6a6d-331">某些類型的視窗沒有工作列按鈕，如訊息方塊和對話方塊（請參閱[對話方塊概述](dialog-boxes-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="f6a6d-332">您可以通過設置<xref:System.Windows.Window.ShowInTaskbar%2A>屬性（預設情況下）`true`來控制視窗的工作列按鈕是否顯示。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a><span data-ttu-id="f6a6d-333">安全性考量</span><span class="sxs-lookup"><span data-stu-id="f6a6d-333">Security Considerations</span></span>  
 <span data-ttu-id="f6a6d-334"><xref:System.Windows.Window>需要`UnmanagedCode`具現化安全許可權。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="f6a6d-335">對於本機電腦上安裝和啟動的應用程式，這落在授與給該應用程式的權限集範圍內。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="f6a6d-336">但是，這不屬於使用 ClickOnce 從 Internet 或本地 Intranet 區域啟動的應用程式授予的許可權集。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="f6a6d-337">因此，使用者將收到 ClickOnce 安全警告，並且需要將應用程式的許可權集提升為完全信任。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-337">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="f6a6d-338">此外，預設情況下，XBAP 不能顯示視窗或對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-338">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="f6a6d-339">有關獨立應用程式安全注意事項的討論，請參閱[WPF 安全性原則 - 平臺安全](../wpf-security-strategy-platform-security.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a><span data-ttu-id="f6a6d-340">其他類型的視窗</span><span class="sxs-lookup"><span data-stu-id="f6a6d-340">Other Types of Windows</span></span>  
 <span data-ttu-id="f6a6d-341"><xref:System.Windows.Navigation.NavigationWindow>是一個視窗，旨在承載可導航內容。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="f6a6d-342">有關詳細資訊，請參閱[導航概述](navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="f6a6d-343">對話方塊是經常用來從使用者收集資訊以完成一項功能的視窗。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="f6a6d-344">例如，當使用者想要打開檔時，"**打開檔"** 對話方塊通常由應用程式顯示，以便從使用者獲取檔案名。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="f6a6d-345">如需詳細資訊，請參閱[對話方塊概觀](dialog-boxes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a6d-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6a6d-346">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6a6d-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="f6a6d-347">對話方塊概觀</span><span class="sxs-lookup"><span data-stu-id="f6a6d-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="f6a6d-348">建置 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="f6a6d-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
