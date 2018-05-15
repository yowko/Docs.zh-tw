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
ms.openlocfilehash: ad7d5225dbaaae544ab463a8f4f16bc43bdf4098
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="75357-102">WPF 視窗概觀</span><span class="sxs-lookup"><span data-stu-id="75357-102">WPF Windows Overview</span></span>
<span data-ttu-id="75357-103">使用者透過 windows 的 Windows Presentation Foundation (WPF) 獨立應用程式與互動。</span><span class="sxs-lookup"><span data-stu-id="75357-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="75357-104">視窗的主要用途是裝載內容，以視覺化方式檢視資料，並讓使用者可以與資料互動。</span><span class="sxs-lookup"><span data-stu-id="75357-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="75357-105">獨立[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式使用，提供它們自己的視窗<xref:System.Windows.Window>類別。</span><span class="sxs-lookup"><span data-stu-id="75357-105">Standalone [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="75357-106">本主題將介紹<xref:System.Windows.Window>之前涵蓋建立和管理 windows 獨立應用程式中的基本概念。</span><span class="sxs-lookup"><span data-stu-id="75357-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75357-107">瀏覽器裝載[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式，包括[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]和鬆散[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]頁面，不會提供自己的視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-107">Browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="75357-108">相反地，它們會裝載在 windows 所提供[!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="75357-108">Instead, they are hosted in windows provided by [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)].</span></span> <span data-ttu-id="75357-109">請參閱[WPF XAML 瀏覽器應用程式概觀](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="75357-109">See [WPF XAML Browser Applications Overview](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).</span></span>  
  
  
<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a><span data-ttu-id="75357-110">Window 類別</span><span class="sxs-lookup"><span data-stu-id="75357-110">The Window Class</span></span>  
 <span data-ttu-id="75357-111">下圖說明視窗的組成部分。</span><span class="sxs-lookup"><span data-stu-id="75357-111">The following figure illustrates the constituent parts of a window.</span></span>  
  
 <span data-ttu-id="75357-112">![視窗項目](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")</span><span class="sxs-lookup"><span data-stu-id="75357-112">![Window elements](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")</span></span>  
  
 <span data-ttu-id="75357-113">視窗分為兩個區域︰非工作區和工作區。</span><span class="sxs-lookup"><span data-stu-id="75357-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="75357-114">*非工作區*的視窗由實作[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]並包含通用於大多數的視窗，其中包括下列視窗的組件：</span><span class="sxs-lookup"><span data-stu-id="75357-114">The *non-client area* of a window is implemented by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
-   <span data-ttu-id="75357-115">框線。</span><span class="sxs-lookup"><span data-stu-id="75357-115">A border.</span></span>  
  
-   <span data-ttu-id="75357-116">標題列。</span><span class="sxs-lookup"><span data-stu-id="75357-116">A title bar.</span></span>  
  
-   <span data-ttu-id="75357-117">圖示。</span><span class="sxs-lookup"><span data-stu-id="75357-117">An icon.</span></span>  
  
-   <span data-ttu-id="75357-118">[最小化]、[最大化] 和 [還原] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="75357-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
-   <span data-ttu-id="75357-119">[關閉] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="75357-119">A Close button.</span></span>  
  
-   <span data-ttu-id="75357-120">[系統] 功能表，具有允許使用者最小化、最大化、還原、移動、調整大小和關閉視窗的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="75357-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="75357-121">*用戶端區域*視窗的視窗之非工作區內的區域，且可由開發人員來新增應用程式特定的內容，例如功能表列、 工具列和控制項。</span><span class="sxs-lookup"><span data-stu-id="75357-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="75357-122">在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，視窗由封裝<xref:System.Windows.Window>類別用來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="75357-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
-   <span data-ttu-id="75357-123">顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-123">Display a window.</span></span>  
  
-   <span data-ttu-id="75357-124">設定視窗的大小、位置和外觀。</span><span class="sxs-lookup"><span data-stu-id="75357-124">Configure the size, position, and appearance of a window.</span></span>  
  
-   <span data-ttu-id="75357-125">裝載應用程式特定內容。</span><span class="sxs-lookup"><span data-stu-id="75357-125">Host application-specific content.</span></span>  
  
-   <span data-ttu-id="75357-126">管理視窗的存留期。</span><span class="sxs-lookup"><span data-stu-id="75357-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a><span data-ttu-id="75357-127">實作視窗</span><span class="sxs-lookup"><span data-stu-id="75357-127">Implementing a Window</span></span>  
 <span data-ttu-id="75357-128">典型視窗的實作包含外觀和行為，其中*外觀*定義使用者在視窗的外觀和*行為*定義視窗的功能與使用者互動的方式使用它。</span><span class="sxs-lookup"><span data-stu-id="75357-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="75357-129">在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、 您可以實作的外觀和行為視窗使用的是程式碼或[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記。</span><span class="sxs-lookup"><span data-stu-id="75357-129">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="75357-130">一般情況下，不過，視窗的外觀使用實作[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記和其行為使用實作程式碼後置，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="75357-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="75357-131">若要啟用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記檔案和程式碼後置檔案，以搭配使用，需要下列憑證：</span><span class="sxs-lookup"><span data-stu-id="75357-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
-   <span data-ttu-id="75357-132">在標記中，`Window`元素必須包含`x:Class`屬性。</span><span class="sxs-lookup"><span data-stu-id="75357-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="75357-133">應用程式建置的時，是否存在`x:Class`標記中的檔案會導致[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]建立`partial`類別衍生自<xref:System.Windows.Window>且具有所指定名稱`x:Class`屬性。</span><span class="sxs-lookup"><span data-stu-id="75357-133">When the application is built, the existence of `x:Class` in the markup file causes [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="75357-134">這需要加入[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]的命名空間宣告[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]結構描述 ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` )。</span><span class="sxs-lookup"><span data-stu-id="75357-134">This requires the addition of an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="75357-135">產生`partial`類別會實作`InitializeComponent`方法，呼叫以註冊事件，並設定會在標記中實作的屬性。</span><span class="sxs-lookup"><span data-stu-id="75357-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
-   <span data-ttu-id="75357-136">在程式碼後置類別必須是`partial`類別具有相同名稱的指定`x:Class`屬性標記，並必須衍生自<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="75357-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="75357-137">這可讓相關聯的程式碼後置檔案`partial`建置應用程式時，所產生的標記檔案類別 (請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md))。</span><span class="sxs-lookup"><span data-stu-id="75357-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).</span></span>  
  
-   <span data-ttu-id="75357-138">在程式碼後置<xref:System.Windows.Window>類別必須實作的建構函式呼叫`InitializeComponent`方法。</span><span class="sxs-lookup"><span data-stu-id="75357-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="75357-139">`InitializeComponent` 實作標記所產生檔案的`partial`類別，以註冊事件，並設定標記中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="75357-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75357-140">當您新增新<xref:System.Windows.Window>至您的專案使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、<xref:System.Windows.Window>使用標記和程式碼後置實作，並包含必要的設定，以建立做為標記和程式碼後置檔案之間的關聯此處所述。</span><span class="sxs-lookup"><span data-stu-id="75357-140">When you add a new <xref:System.Windows.Window> to your project by using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="75357-141">這項設定的位置，您可以專注於定義中的視窗外觀[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記和程式碼後置中實作其行為。</span><span class="sxs-lookup"><span data-stu-id="75357-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="75357-142">下列範例顯示一個按鈕，在中實作包含視窗[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記和按鈕的事件處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>實作程式碼後置中的事件。</span><span class="sxs-lookup"><span data-stu-id="75357-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="75357-143">設定 MSBuild 的視窗定義</span><span class="sxs-lookup"><span data-stu-id="75357-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="75357-144">實作您的視窗的方式設定的方式會決定[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="75357-144">How you implement your window determines how it is configured for [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].</span></span> <span data-ttu-id="75357-145">使用這兩個定義的視窗[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記和程式碼後置：</span><span class="sxs-lookup"><span data-stu-id="75357-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="75357-146"> 標記檔案會設定為[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目。</span><span class="sxs-lookup"><span data-stu-id="75357-146"> markup files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items.</span></span>  
  
-   <span data-ttu-id="75357-147">程式碼後置檔案會設定為[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile`項目。</span><span class="sxs-lookup"><span data-stu-id="75357-147">Code-behind files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile` items.</span></span>  
  
 <span data-ttu-id="75357-148">這會顯示下列[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]專案檔。</span><span class="sxs-lookup"><span data-stu-id="75357-148">This is shown in the following [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="75357-149">如需建置[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式，請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="75357-149">For information about building [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, see [Building a WPF Application](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a><span data-ttu-id="75357-150">視窗存留期</span><span class="sxs-lookup"><span data-stu-id="75357-150">Window Lifetime</span></span>  
 <span data-ttu-id="75357-151">如同任何類別，視窗有存留期，會在它一開始具現化時開始，在那之後它會被開啟、啟動和停用，並最終關閉。</span><span class="sxs-lookup"><span data-stu-id="75357-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  
  
  
<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a><span data-ttu-id="75357-152">開啟視窗</span><span class="sxs-lookup"><span data-stu-id="75357-152">Opening a Window</span></span>  
 <span data-ttu-id="75357-153">若要開啟視窗，您要先建立它的執行個體，如下列範例中示範。</span><span class="sxs-lookup"><span data-stu-id="75357-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="75357-154">在此範例中，`MarkupAndCodeBehindWindow`具現化應用程式啟動時，發生於當<xref:System.Windows.Application.Startup>就會引發事件。</span><span class="sxs-lookup"><span data-stu-id="75357-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="75357-155">具現化一個視窗時，它的參考會自動加入至受 windows 清單<xref:System.Windows.Application>物件 (請參閱<xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="75357-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="75357-156">此外，第一個視窗来具現化，根據預設，設定<xref:System.Windows.Application>做為主要應用程式視窗 (請參閱<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="75357-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="75357-157">藉由呼叫最後開啟的視窗<xref:System.Windows.Window.Show%2A>方法; 在下圖中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="75357-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 <span data-ttu-id="75357-158">![呼叫 Window.Show 而開啟的視窗](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")</span><span class="sxs-lookup"><span data-stu-id="75357-158">![A Window Opened by Calling Window.Show](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")</span></span>  
  
 <span data-ttu-id="75357-159">開啟的視窗，藉由呼叫<xref:System.Windows.Window.Show%2A>是強制回應視窗，這表示該應用程式會在允許使用者啟用 其他視窗相同的應用程式中的模式。</span><span class="sxs-lookup"><span data-stu-id="75357-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75357-160"><xref:System.Windows.Window.ShowDialog%2A> 呼叫以強制回應方式開啟例如對話方塊視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="75357-161">請參閱[對話方塊概觀](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="75357-161">See [Dialog Boxes Overview](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="75357-162">當<xref:System.Windows.Window.Show%2A>是呼叫，視窗執行初始化工作後，它會顯示建立基礎結構，讓它能夠接收使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="75357-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="75357-163">當初始化視窗時，<xref:System.Windows.Window.SourceInitialized>就會引發事件，並顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="75357-164">快捷<xref:System.Windows.Application.StartupUri%2A>可以設定以指定應用程式啟動時自動開啟的第一個視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="75357-165">應用程式啟動時，值所指定視窗<xref:System.Windows.Application.StartupUri%2A>開啟 modelessly; 就內部而言，開啟視窗的方式呼叫其<xref:System.Windows.Window.Show%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="75357-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a><span data-ttu-id="75357-166">視窗擁有權</span><span class="sxs-lookup"><span data-stu-id="75357-166">Window Ownership</span></span>  
 <span data-ttu-id="75357-167">開啟的視窗，使用<xref:System.Windows.Window.Show%2A>方法並沒有隱含關聯性與建立它的視窗，使用者可以彼此獨立，這表示其中一個視窗可以執行下列其中一個視窗與互動：</span><span class="sxs-lookup"><span data-stu-id="75357-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
-   <span data-ttu-id="75357-168">涵蓋的其他 (除非其中一個視窗有其<xref:System.Windows.Window.Topmost%2A>屬性設定為`true`)。</span><span class="sxs-lookup"><span data-stu-id="75357-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
-   <span data-ttu-id="75357-169">最小化、最大化和還原而不會影響對方。</span><span class="sxs-lookup"><span data-stu-id="75357-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="75357-170">某些視窗需要與開啟它們的視窗有關聯性。</span><span class="sxs-lookup"><span data-stu-id="75357-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="75357-171">例如，[!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)]應用程式可能會開啟屬性視窗和工具視窗的典型的行為是要彌補建立它們的視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-171">For example, an [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="75357-172">此外，這類視窗應該一律與建立它們的視窗一致地關閉、最小化、最大化和還原。</span><span class="sxs-lookup"><span data-stu-id="75357-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="75357-173">藉由一個視窗，可以建立這類關聯性*自己*另一個，並達成設定<xref:System.Windows.Window.Owner%2A>屬性*擁有視窗*參考*擁有者視窗*。</span><span class="sxs-lookup"><span data-stu-id="75357-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="75357-174">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="75357-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="75357-175">建立擁有權之後︰</span><span class="sxs-lookup"><span data-stu-id="75357-175">After ownership is established:</span></span>  
  
-   <span data-ttu-id="75357-176">擁有的視窗可以藉由檢查的值參考其擁有者視窗其<xref:System.Windows.Window.Owner%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="75357-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
-   <span data-ttu-id="75357-177">主控視窗可以探索其擁有藉由檢查的值的所有 windows 其<xref:System.Windows.Window.OwnedWindows%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="75357-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a><span data-ttu-id="75357-178">避免視窗啟動</span><span class="sxs-lookup"><span data-stu-id="75357-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="75357-179">有其中 windows 不應該啟動時顯示，例如網際網路 messenger 樣式應用程式對話視窗或通知電子郵件應用程式視窗的案例。</span><span class="sxs-lookup"><span data-stu-id="75357-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="75357-180">如果您的應用程式不應該在顯示時啟動的視窗，您可以設定其<xref:System.Windows.Window.ShowActivated%2A>屬性`false`之前先呼叫<xref:System.Windows.Window.Show%2A>第一次的方法。</span><span class="sxs-lookup"><span data-stu-id="75357-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="75357-181">因此：</span><span class="sxs-lookup"><span data-stu-id="75357-181">As a consequence:</span></span>  
  
-   <span data-ttu-id="75357-182">未啟動視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-182">The window is not activated.</span></span>  
  
-   <span data-ttu-id="75357-183">視窗的<xref:System.Windows.Window.Activated>不會引發事件。</span><span class="sxs-lookup"><span data-stu-id="75357-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
-   <span data-ttu-id="75357-184">目前已啟動的視窗會保持已啟動。</span><span class="sxs-lookup"><span data-stu-id="75357-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="75357-185">不過，當使用者按一下工作區或非工作區來啟動它時，視窗將會啟動。</span><span class="sxs-lookup"><span data-stu-id="75357-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="75357-186">在此情況下：</span><span class="sxs-lookup"><span data-stu-id="75357-186">In this case:</span></span>  
  
-   <span data-ttu-id="75357-187">視窗已啟動。</span><span class="sxs-lookup"><span data-stu-id="75357-187">The window is activated.</span></span>  
  
-   <span data-ttu-id="75357-188">視窗的<xref:System.Windows.Window.Activated>就會引發事件。</span><span class="sxs-lookup"><span data-stu-id="75357-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
-   <span data-ttu-id="75357-189">先前已啟動的視窗已停用。</span><span class="sxs-lookup"><span data-stu-id="75357-189">The previously activated window is deactivated.</span></span>  
  
-   <span data-ttu-id="75357-190">視窗的<xref:System.Windows.Window.Deactivated>和<xref:System.Windows.Window.Activated>如預期般回應使用者動作，後續引發事件。</span><span class="sxs-lookup"><span data-stu-id="75357-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a><span data-ttu-id="75357-191">視窗啟動</span><span class="sxs-lookup"><span data-stu-id="75357-191">Window Activation</span></span>  
 <span data-ttu-id="75357-192">當第一次開啟一個視窗時，它會變成作用中視窗 (除非它顯示<xref:System.Windows.Window.ShowActivated%2A>設`false`)。</span><span class="sxs-lookup"><span data-stu-id="75357-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="75357-193">*作用中視窗*是目前是否擷取使用者輸入，例如按鍵及滑鼠的視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="75357-194">當視窗成為使用中時，會引發<xref:System.Windows.Window.Activated>事件。</span><span class="sxs-lookup"><span data-stu-id="75357-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75357-195">當第一次開啟一個視窗時，<xref:System.Windows.FrameworkElement.Loaded>和<xref:System.Windows.Window.ContentRendered>之後才會引發事件<xref:System.Windows.Window.Activated>就會引發事件。</span><span class="sxs-lookup"><span data-stu-id="75357-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="75357-196">這一點，視窗也可以有效地被視為時開啟<xref:System.Windows.Window.ContentRendered>，就會引發。</span><span class="sxs-lookup"><span data-stu-id="75357-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="75357-197">視窗成為使用中之後，使用者可以在相同應用程式中啟動另一個視窗，或啟動另一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="75357-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="75357-198">當發生這種情況時，目前作用中視窗會變成停用，並引發<xref:System.Windows.Window.Deactivated>事件。</span><span class="sxs-lookup"><span data-stu-id="75357-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="75357-199">同樣地，當使用者選取目前已停用的視窗、 視窗再次變成作用中和<xref:System.Windows.Window.Activated>，就會引發。</span><span class="sxs-lookup"><span data-stu-id="75357-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="75357-200">若要處理的一個常見原因<xref:System.Windows.Window.Activated>和<xref:System.Windows.Window.Deactivated>是啟用和停用只能執行時視窗是作用中的功能。</span><span class="sxs-lookup"><span data-stu-id="75357-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="75357-201">例如，某些視窗顯示需要使用者持續輸入和注意的互動式內容，包括遊戲和視訊播放程式。</span><span class="sxs-lookup"><span data-stu-id="75357-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="75357-202">下列範例是簡化的視訊播放器，示範如何處理<xref:System.Windows.Window.Activated>和<xref:System.Windows.Window.Deactivated>來實作此行為。</span><span class="sxs-lookup"><span data-stu-id="75357-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="75357-203">當視窗已停用時，其他應用程式類型仍然可能會在背景中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="75357-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="75357-204">例如，當使用者使用其他應用程式時，郵件用戶端可能會繼續輪詢郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="75357-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="75357-205">這類應用程式在主視窗已停用時，通常會提供不同或其他行為。</span><span class="sxs-lookup"><span data-stu-id="75357-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="75357-206">對於郵件程式，這可能表示同時將新的郵件項目加入收件匣，並將通知圖示加入系統匣。</span><span class="sxs-lookup"><span data-stu-id="75357-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="75357-207">當郵件視窗不是作用中，您可以判斷藉由檢查時，需要只會顯示通知圖示<xref:System.Windows.Window.IsActive%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="75357-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="75357-208">如果背景工作完成時，視窗可能會想要更緊急通知使用者，藉由呼叫<xref:System.Windows.Window.Activate%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="75357-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="75357-209">如果在使用者互動與另一個應用程式啟動時<xref:System.Windows.Window.Activate%2A>呼叫時，視窗的工作列按鈕會閃爍。</span><span class="sxs-lookup"><span data-stu-id="75357-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="75357-210">如果使用者在目前的應用程式互動，則呼叫<xref:System.Windows.Window.Activate%2A>會將視窗帶到前景。</span><span class="sxs-lookup"><span data-stu-id="75357-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75357-211">您可以處理應用程式範圍啟用使用<xref:System.Windows.Application.Activated?displayProperty=nameWithType>和<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="75357-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a><span data-ttu-id="75357-212">關閉視窗</span><span class="sxs-lookup"><span data-stu-id="75357-212">Closing a Window</span></span>  
 <span data-ttu-id="75357-213">視窗的存留期在使用者關閉它時開始進入尾聲。</span><span class="sxs-lookup"><span data-stu-id="75357-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="75357-214">視窗可以使用非工作區中的項目關閉，包括下列項目︰</span><span class="sxs-lookup"><span data-stu-id="75357-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
-   <span data-ttu-id="75357-215">**關閉**的項目**系統**功能表。</span><span class="sxs-lookup"><span data-stu-id="75357-215">The **Close** item of the **System** menu.</span></span>  
  
-   <span data-ttu-id="75357-216">按下 ALT+F4。</span><span class="sxs-lookup"><span data-stu-id="75357-216">Pressing ALT+F4.</span></span>  
  
-   <span data-ttu-id="75357-217">按下**關閉** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="75357-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="75357-218">您可以提供其他機制讓工作區關閉視窗，較常見的包括下列各項︰</span><span class="sxs-lookup"><span data-stu-id="75357-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
-   <span data-ttu-id="75357-219">**結束**中的項目**檔案**功能表上，通常是針對主應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
-   <span data-ttu-id="75357-220">A**關閉**中的項目**檔案**功能表上，通常位於次要應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
-   <span data-ttu-id="75357-221">A**取消**按鈕，通常強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="75357-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
-   <span data-ttu-id="75357-222">A**關閉**按鈕，通常非強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="75357-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="75357-223">若要關閉視窗，以回應其中一種自訂的機制，您必須呼叫<xref:System.Windows.Window.Close%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="75357-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="75357-224">下列範例會實作能夠藉由選擇關閉視窗**結束**上**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="75357-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="75357-225">當視窗關閉時，會引發兩個事件：<xref:System.Windows.Window.Closing>和<xref:System.Windows.Window.Closed>。</span><span class="sxs-lookup"><span data-stu-id="75357-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="75357-226"><xref:System.Windows.Window.Closing> 關閉視窗，並提供的機制，可以避免關閉由哪一個視窗之前引發。</span><span class="sxs-lookup"><span data-stu-id="75357-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="75357-227">防止視窗關閉的一個常見原因，是視窗內容包含已修改的資料。</span><span class="sxs-lookup"><span data-stu-id="75357-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="75357-228">在此情況下，<xref:System.Windows.Window.Closing>可以處理事件，以判斷是否資料已變更，而且如果是，要詢問使用者是否要繼續關閉視窗而不儲存資料，或取消關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="75357-229">下列範例示範處理的關鍵層面<xref:System.Windows.Window.Closing>。</span><span class="sxs-lookup"><span data-stu-id="75357-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  
 
  
 <span data-ttu-id="75357-230"><xref:System.Windows.Window.Closing>傳遞事件處理常式<xref:System.ComponentModel.CancelEventArgs>，它會實作`Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性設為`true`防止關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="75357-231">如果<xref:System.Windows.Window.Closing>未處理，或處理，但不是會取消，將會關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="75357-232">只要視窗實際關閉之前， <xref:System.Windows.Window.Closed> ，就會引發。</span><span class="sxs-lookup"><span data-stu-id="75357-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="75357-233">此時無法防止視窗關閉。</span><span class="sxs-lookup"><span data-stu-id="75357-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75357-234">若要關閉自動在主要應用程式視窗關閉時可以設定應用程式 (請參閱<xref:System.Windows.Application.MainWindow%2A>) 或最後一個視窗關閉。</span><span class="sxs-lookup"><span data-stu-id="75357-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="75357-235">如需詳細資訊，請參閱 <xref:System.Windows.Application.ShutdownMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="75357-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="75357-236">雖然可以明確關閉視窗，透過用戶端和用戶端區域中提供的機制，視窗也可以隱含地關閉結果中的應用程式其他部分的行為或[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，包括下列：</span><span class="sxs-lookup"><span data-stu-id="75357-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], including the following:</span></span>  
  
-   <span data-ttu-id="75357-237">使用者登出或關閉 Windows。</span><span class="sxs-lookup"><span data-stu-id="75357-237">A user logs off or shuts down Windows.</span></span>  
  
-   <span data-ttu-id="75357-238">關閉視窗的擁有者 (請參閱<xref:System.Windows.Window.Owner%2A>)。</span><span class="sxs-lookup"><span data-stu-id="75357-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
-   <span data-ttu-id="75357-239">主應用程式視窗已關閉和<xref:System.Windows.Application.ShutdownMode%2A>是<xref:System.Windows.ShutdownMode.OnMainWindowClose>。</span><span class="sxs-lookup"><span data-stu-id="75357-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
-   <span data-ttu-id="75357-240">呼叫 <xref:System.Windows.Application.Shutdown%2A>。</span><span class="sxs-lookup"><span data-stu-id="75357-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75357-241">在關閉之後就無法重新開啟視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a><span data-ttu-id="75357-242">視窗存留期事件</span><span class="sxs-lookup"><span data-stu-id="75357-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="75357-243">下圖顯示在視窗存留期的主體事件順序。</span><span class="sxs-lookup"><span data-stu-id="75357-243">The following illustration shows the sequence of the principal events in the lifetime of a window.</span></span>  
  
 <span data-ttu-id="75357-244">![視窗存留期](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")</span><span class="sxs-lookup"><span data-stu-id="75357-244">![Window Lifetime](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")</span></span>  
  
 <span data-ttu-id="75357-245">下圖顯示的主體的事件順序的視窗會顯示為沒有啟用的存留期間 (<xref:System.Windows.Window.ShowActivated%2A>設`false`顯示視窗之前)。</span><span class="sxs-lookup"><span data-stu-id="75357-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown).</span></span>  
  
 <span data-ttu-id="75357-246">![視窗存留期 &#40;Window.ShowActivated &#61; False&#41;](../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")</span><span class="sxs-lookup"><span data-stu-id="75357-246">![Window Lifetime &#40;Window.ShowActivated &#61; False&#41;](../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")</span></span>  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a><span data-ttu-id="75357-247">視窗位置</span><span class="sxs-lookup"><span data-stu-id="75357-247">Window Location</span></span>  
 <span data-ttu-id="75357-248">視窗開啟時，它會有相對於桌面的 x 和 y 維度位置。</span><span class="sxs-lookup"><span data-stu-id="75357-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="75357-249">此位置可以決定藉由檢查<xref:System.Windows.Window.Left%2A>和<xref:System.Windows.Window.Top%2A>屬性，分別。</span><span class="sxs-lookup"><span data-stu-id="75357-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="75357-250">您可以設定這些屬性，以變更視窗的位置。</span><span class="sxs-lookup"><span data-stu-id="75357-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="75357-251">您也可以指定的初始位置<xref:System.Windows.Window>第一次出現時藉由設定<xref:System.Windows.Window.WindowStartupLocation%2A>具有下列其中一種屬性<xref:System.Windows.WindowStartupLocation>列舉值：</span><span class="sxs-lookup"><span data-stu-id="75357-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
-   <span data-ttu-id="75357-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (預設值)</span><span class="sxs-lookup"><span data-stu-id="75357-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="75357-253">如果啟動位置指定為<xref:System.Windows.WindowStartupLocation.Manual>，而<xref:System.Windows.Window.Left%2A>和<xref:System.Windows.Window.Top%2A>沒有設定屬性，<xref:System.Windows.Window>會要求才會出現在位置的 Windows。</span><span class="sxs-lookup"><span data-stu-id="75357-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="75357-254">最上層視窗和疊置順序</span><span class="sxs-lookup"><span data-stu-id="75357-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="75357-255">除了有 x 和 y 位置，視窗也有 z 維度的位置，這決定了它相對於其他視窗的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="75357-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="75357-256">這稱為視窗的疊置順序，並且有兩種類型︰一般疊置順序和最上層疊置順序。</span><span class="sxs-lookup"><span data-stu-id="75357-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="75357-257">在視窗的位置*一般疊置順序*取決於它是否目前作用中。</span><span class="sxs-lookup"><span data-stu-id="75357-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="75357-258">根據預設，視窗位於一般疊置順序。</span><span class="sxs-lookup"><span data-stu-id="75357-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="75357-259">在 視窗位置*最上層的疊置順序*也取決於它是否目前作用中。</span><span class="sxs-lookup"><span data-stu-id="75357-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="75357-260">此外，最上層疊置順序的視窗一定會位於一般疊置順序的視窗之上。</span><span class="sxs-lookup"><span data-stu-id="75357-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="75357-261">視窗位於最上層的疊置順序藉由設定其<xref:System.Windows.Window.Topmost%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="75357-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="75357-262">在每個疊置順序內，目前使用中視窗會顯示在相同疊置順序中的所有其他視窗之上。</span><span class="sxs-lookup"><span data-stu-id="75357-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a><span data-ttu-id="75357-263">視窗大小</span><span class="sxs-lookup"><span data-stu-id="75357-263">Window Size</span></span>  
 <span data-ttu-id="75357-264">除了桌面的位置，視窗有數個屬性，包括各種 width 和 height 屬性所決定的大小和<xref:System.Windows.Window.SizeToContent%2A>。</span><span class="sxs-lookup"><span data-stu-id="75357-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="75357-265"><xref:System.Windows.FrameworkElement.MinWidth%2A><xref:System.Windows.FrameworkElement.Width%2A>，和<xref:System.Windows.FrameworkElement.MaxWidth%2A>用來管理視窗可能會在其生命週期，而且都已設定為下列範例所示的寬度的範圍。</span><span class="sxs-lookup"><span data-stu-id="75357-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="75357-266">視窗高度受<xref:System.Windows.FrameworkElement.MinHeight%2A>， <xref:System.Windows.FrameworkElement.Height%2A>，和<xref:System.Windows.FrameworkElement.MaxHeight%2A>，且已設定，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="75357-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="75357-267">因為各種寬度值和高度值都各指定一個範圍，所以可調整大小視窗的高度與寬度可能會是個別維度的指定範圍內的任何位置。</span><span class="sxs-lookup"><span data-stu-id="75357-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="75357-268">若要偵測其目前的寬度和高度，檢查<xref:System.Windows.FrameworkElement.ActualWidth%2A>和<xref:System.Windows.FrameworkElement.ActualHeight%2A>分別。</span><span class="sxs-lookup"><span data-stu-id="75357-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="75357-269">如果您想要您的視窗的高度與寬度調整成視窗大小的大小的內容，您可以使用<xref:System.Windows.Window.SizeToContent%2A>屬性，具有下列值：</span><span class="sxs-lookup"><span data-stu-id="75357-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
-   <span data-ttu-id="75357-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="75357-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="75357-271">無效果 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="75357-271">No effect (default).</span></span>  
  
-   <span data-ttu-id="75357-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="75357-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="75357-273">調整成視窗具有相同的效果與將兩者設定中的內容寬度<xref:System.Windows.FrameworkElement.MinWidth%2A>和<xref:System.Windows.FrameworkElement.MaxWidth%2A>內容的寬度。</span><span class="sxs-lookup"><span data-stu-id="75357-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
-   <span data-ttu-id="75357-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="75357-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="75357-275">調整成內容的高度，具有相同的效果與將兩者設定<xref:System.Windows.FrameworkElement.MinHeight%2A>和<xref:System.Windows.FrameworkElement.MaxHeight%2A>內容的高度。</span><span class="sxs-lookup"><span data-stu-id="75357-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
-   <span data-ttu-id="75357-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="75357-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="75357-277">調整成內容的寬度和高度，具有相同的效果與將兩者設定<xref:System.Windows.FrameworkElement.MinHeight%2A>和<xref:System.Windows.FrameworkElement.MaxHeight%2A>內容，以及設定高度<xref:System.Windows.FrameworkElement.MinWidth%2A>和<xref:System.Windows.FrameworkElement.MaxWidth%2A>內容的寬度。</span><span class="sxs-lookup"><span data-stu-id="75357-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="75357-278">下列範例顯示自動調整垂直和水平大小以符合其內容的視窗，第一次顯示時的樣子。</span><span class="sxs-lookup"><span data-stu-id="75357-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="75357-279">下列範例示範如何設定<xref:System.Windows.Window.SizeToContent%2A>指定視窗會調整大小以符合其內容的程式碼中的屬性。</span><span class="sxs-lookup"><span data-stu-id="75357-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="75357-280">調整大小屬性優先順序</span><span class="sxs-lookup"><span data-stu-id="75357-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="75357-281">基本上，視窗的各種大小屬性會合併起來定義可調整大小的視窗的寬度和高度範圍。</span><span class="sxs-lookup"><span data-stu-id="75357-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="75357-282">若要確保能維持有效的範圍，<xref:System.Windows.Window>評估使用下列優先順序之訂單的大小屬性的值。</span><span class="sxs-lookup"><span data-stu-id="75357-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="75357-283">**針對高度屬性：**</span><span class="sxs-lookup"><span data-stu-id="75357-283">**For Height Properties:**</span></span>  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="75357-284">**針對寬度屬性：**</span><span class="sxs-lookup"><span data-stu-id="75357-284">**For Width Properties:**</span></span>  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="75357-285">優先順序也可以判斷視窗的大小，它最大化時，管理與<xref:System.Windows.Window.WindowState%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="75357-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>   
## <a name="window-state"></a><span data-ttu-id="75357-286">視窗狀態</span><span class="sxs-lookup"><span data-stu-id="75357-286">Window State</span></span>  
 <span data-ttu-id="75357-287">在可調整大小的視窗存留期中，它可以有三種狀態︰標準、最小化及最大化。</span><span class="sxs-lookup"><span data-stu-id="75357-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="75357-288">與視窗*正常*狀態是在視窗的預設狀態。</span><span class="sxs-lookup"><span data-stu-id="75357-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="75357-289">這種狀態的視窗可以讓使用者移動並使用調整大小底框或框線調整其大小，如果它可調整大小。</span><span class="sxs-lookup"><span data-stu-id="75357-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="75357-290">與視窗*最小化*其工作列按鈕來摺疊狀態，如果<xref:System.Windows.Window.ShowInTaskbar%2A>設為`true`; 否則它摺疊的最小的可能大小，它可以是和本身基底位址至桌面的左下角。</span><span class="sxs-lookup"><span data-stu-id="75357-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="75357-291">最小化視窗的類型都無法使用框線或調整大小底框來調整大小，雖然未顯示在工作列中的最小化視窗可以在桌面拖曳。</span><span class="sxs-lookup"><span data-stu-id="75357-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="75357-292">與視窗*最大化*狀態會展開，以最大大小可能造成，才會大可達其<xref:System.Windows.FrameworkElement.MaxWidth%2A>， <xref:System.Windows.FrameworkElement.MaxHeight%2A>，和<xref:System.Windows.Window.SizeToContent%2A>屬性指定。</span><span class="sxs-lookup"><span data-stu-id="75357-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="75357-293">就像最小化的視窗，最大化的視窗無法使用調整大小底框或藉由拖曳框線來調整大小。</span><span class="sxs-lookup"><span data-stu-id="75357-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75357-294">值<xref:System.Windows.Window.Top%2A>， <xref:System.Windows.Window.Left%2A>， <xref:System.Windows.FrameworkElement.Width%2A>，和<xref:System.Windows.FrameworkElement.Height%2A>視窗的內容一律代表的值的一般狀態，即使目前最大化或最小化視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="75357-295">您可以設定視窗的狀態設定其<xref:System.Windows.Window.WindowState%2A>屬性，可以有下列其中一種<xref:System.Windows.WindowState>列舉值：</span><span class="sxs-lookup"><span data-stu-id="75357-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
-   <span data-ttu-id="75357-296"><xref:System.Windows.WindowState.Normal> (預設值)</span><span class="sxs-lookup"><span data-stu-id="75357-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="75357-297">下列範例示範如何建立在開啟時會顯示為最大化的視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="75357-298">一般情況下，您應該設定<xref:System.Windows.Window.WindowState%2A>設定視窗的初始狀態。</span><span class="sxs-lookup"><span data-stu-id="75357-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="75357-299">可調整大小的視窗顯示後，使用者可以按下視窗標題列上的最小化、最大化和還原按鈕，以變更視窗狀態。</span><span class="sxs-lookup"><span data-stu-id="75357-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a><span data-ttu-id="75357-300">視窗外觀</span><span class="sxs-lookup"><span data-stu-id="75357-300">Window Appearance</span></span>  
 <span data-ttu-id="75357-301">您可以新增視窗特定的內容，例如按鈕、標籤和文字方塊，來變更視窗工作區的外觀。</span><span class="sxs-lookup"><span data-stu-id="75357-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="75357-302">若要設定的非工作區，<xref:System.Windows.Window>提供數個屬性，其中包括<xref:System.Windows.Window.Icon%2A>設定視窗的圖示和<xref:System.Windows.Window.Title%2A>若要設定其標題。</span><span class="sxs-lookup"><span data-stu-id="75357-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="75357-303">您也可以藉由設定視窗的調整大小模式、視窗樣式，以及它是否顯示為桌面工作列上的按鈕，變更非工作區框線的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="75357-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  
  
  
<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a><span data-ttu-id="75357-304">調整大小模式</span><span class="sxs-lookup"><span data-stu-id="75357-304">Resize Mode</span></span>  
 <span data-ttu-id="75357-305">取決於<xref:System.Windows.Window.WindowStyle%2A>屬性，您可以控制如何 （和 if） 的使用者可以調整視窗大小。</span><span class="sxs-lookup"><span data-stu-id="75357-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="75357-306">視窗樣式的選擇會影響是否使用者可以拖曳調整大小視窗框線的滑鼠是否**最小化**，**最大化**，和**調整**按鈕會出現在非工作區中，而且如果它們沒有出現，請他們是否已啟用。</span><span class="sxs-lookup"><span data-stu-id="75357-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="75357-307">您可以設定視窗調整大小時藉由設定其<xref:System.Windows.Window.ResizeMode%2A>屬性，它可以是下列其中一種<xref:System.Windows.ResizeMode>列舉值：</span><span class="sxs-lookup"><span data-stu-id="75357-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <span data-ttu-id="75357-308"><xref:System.Windows.ResizeMode.CanResize> (預設值)</span><span class="sxs-lookup"><span data-stu-id="75357-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="75357-309">如同<xref:System.Windows.Window.WindowStyle%2A>，視窗的調整大小模式不太可能變更在其生命週期，這表示，您很可能是設定它從[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記。</span><span class="sxs-lookup"><span data-stu-id="75357-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="75357-310">請注意，您可以偵測是否視窗最大化，最小化，或藉由檢查還原<xref:System.Windows.Window.WindowState%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="75357-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a><span data-ttu-id="75357-311">視窗樣式</span><span class="sxs-lookup"><span data-stu-id="75357-311">Window Style</span></span>  
 <span data-ttu-id="75357-312">從視窗非工作區公開的框線適用於大部分的應用程式。</span><span class="sxs-lookup"><span data-stu-id="75357-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="75357-313">不過，有一些情況下需要不同型別的框線，或是完全不需要框線，視視窗的型別而定。</span><span class="sxs-lookup"><span data-stu-id="75357-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="75357-314">若要控制何種框線視窗取得時，設定其<xref:System.Windows.Window.WindowStyle%2A>具有下列值的其中一個屬性<xref:System.Windows.WindowStyle>列舉型別：</span><span class="sxs-lookup"><span data-stu-id="75357-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <span data-ttu-id="75357-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (預設值)</span><span class="sxs-lookup"><span data-stu-id="75357-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="75357-316">下圖說明這些視窗樣式的效果。</span><span class="sxs-lookup"><span data-stu-id="75357-316">The effect of these window styles are illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="75357-317">![視窗樣式](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.PNG "WindowOverviewFigure6")</span><span class="sxs-lookup"><span data-stu-id="75357-317">![Window styles](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.PNG "WindowOverviewFigure6")</span></span>  
  
 <span data-ttu-id="75357-318">您可以設定<xref:System.Windows.Window.WindowStyle%2A>使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記或程式碼，因為它是不太可能變更視窗的存留期間，您將很可能是設定它使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記。</span><span class="sxs-lookup"><span data-stu-id="75357-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="75357-319">非矩形視窗樣式</span><span class="sxs-lookup"><span data-stu-id="75357-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="75357-320">也有一些情況下，其中的框線樣式，<xref:System.Windows.Window.WindowStyle%2A>可讓您有不足夠。</span><span class="sxs-lookup"><span data-stu-id="75357-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="75357-321">比方說，您可以建立非矩形的框線，應用程式，像是[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="75357-321">For example, you may want to create an application with a non-rectangular border, like [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] uses.</span></span>  
  
 <span data-ttu-id="75357-322">例如，以下圖顯示的語音泡泡視窗為例。</span><span class="sxs-lookup"><span data-stu-id="75357-322">For example, consider the speech bubble window shown in the following figure.</span></span>  
  
 <span data-ttu-id="75357-323">![非矩形視窗](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")</span><span class="sxs-lookup"><span data-stu-id="75357-323">![Nonrectangular window](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")</span></span>  
  
 <span data-ttu-id="75357-324">可以建立這類視窗設定<xref:System.Windows.Window.WindowStyle%2A>屬性<xref:System.Windows.WindowStyle.None>，並使用特殊支援<xref:System.Windows.Window>具有的透明度。</span><span class="sxs-lookup"><span data-stu-id="75357-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="75357-325">這些值的組合會指示視窗要轉譯為完全透明。</span><span class="sxs-lookup"><span data-stu-id="75357-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="75357-326">在此狀態下，無法使用視窗的非工作區裝飾 ([關閉] 功能表、[最小化]、[最大化] 和 [還原] 按鈕等等)。</span><span class="sxs-lookup"><span data-stu-id="75357-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="75357-327">因此，您需要自行提供。</span><span class="sxs-lookup"><span data-stu-id="75357-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a><span data-ttu-id="75357-328">工作列目前狀態</span><span class="sxs-lookup"><span data-stu-id="75357-328">Task Bar Presence</span></span>  
 <span data-ttu-id="75357-329">視窗的預設外觀包含工作列按鈕，像下圖所示。</span><span class="sxs-lookup"><span data-stu-id="75357-329">The default appearance of a window includes a task bar button, like the one shown in the following figure.</span></span>  
  
 <span data-ttu-id="75357-330">![具有工作列按鈕的視窗](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.PNG "WindowOverviewFigure7")</span><span class="sxs-lookup"><span data-stu-id="75357-330">![Window with a task bar button](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.PNG "WindowOverviewFigure7")</span></span>  
  
 <span data-ttu-id="75357-331">某些類型的視窗沒有工作列按鈕，例如訊息方塊和對話方塊 (請參閱[對話方塊概觀](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="75357-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)).</span></span> <span data-ttu-id="75357-332">您可以控制在視窗的工作列按鈕是否顯示藉由設定<xref:System.Windows.Window.ShowInTaskbar%2A>屬性 (`true`依預設)。</span><span class="sxs-lookup"><span data-stu-id="75357-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a><span data-ttu-id="75357-333">安全性考量</span><span class="sxs-lookup"><span data-stu-id="75357-333">Security Considerations</span></span>  
 <span data-ttu-id="75357-334"><xref:System.Windows.Window> 需要`UnmanagedCode`具現化的安全性權限。</span><span class="sxs-lookup"><span data-stu-id="75357-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="75357-335">對於本機電腦上安裝和啟動的應用程式，這落在授與給該應用程式的權限集範圍內。</span><span class="sxs-lookup"><span data-stu-id="75357-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="75357-336">不過，這超出的權限授與給從網際網路或本機內部網路區域使用啟動的應用程式集[!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="75357-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].</span></span> <span data-ttu-id="75357-337">因此，使用者會收到[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]安全性警告，而且必須提升為完全信任應用程式設定的權限。</span><span class="sxs-lookup"><span data-stu-id="75357-337">Consequently, users will receive a [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="75357-338">此外，[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]無法顯示預設視窗和對話方塊。</span><span class="sxs-lookup"><span data-stu-id="75357-338">Additionally, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="75357-339">獨立應用程式的安全性考量的討論，請參閱[WPF 安全性策略-平台安全性](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)。</span><span class="sxs-lookup"><span data-stu-id="75357-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a><span data-ttu-id="75357-340">其他類型的視窗</span><span class="sxs-lookup"><span data-stu-id="75357-340">Other Types of Windows</span></span>  
 <span data-ttu-id="75357-341"><xref:System.Windows.Navigation.NavigationWindow> 是設計來裝載可瀏覽內容的視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="75357-342">如需詳細資訊，請參閱[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="75357-342">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="75357-343">對話方塊是經常用來從使用者收集資訊以完成一項功能的視窗。</span><span class="sxs-lookup"><span data-stu-id="75357-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="75357-344">例如，當使用者想要開啟檔案，**開啟檔案**從使用者取得檔案名稱的應用程式通常會顯示對話方塊。</span><span class="sxs-lookup"><span data-stu-id="75357-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="75357-345">如需詳細資訊，請參閱[對話方塊概觀](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="75357-345">For more information, see [Dialog Boxes Overview](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75357-346">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75357-346">See Also</span></span>  
 <xref:System.Windows.Window>  
 <xref:System.Windows.MessageBox>  
 <xref:System.Windows.Navigation.NavigationWindow>  
 <xref:System.Windows.Application>  
 [<span data-ttu-id="75357-347">對話方塊概觀</span><span class="sxs-lookup"><span data-stu-id="75357-347">Dialog Boxes Overview</span></span>](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)  
 [<span data-ttu-id="75357-348">建置 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="75357-348">Building a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
