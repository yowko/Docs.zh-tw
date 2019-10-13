---
title: 巡覽概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loose XAML files [WPF]
- windows [WPF]
- Start page [WPF]
- HTML files [WPF]
- structured navigation [WPF]
- fragment navigation [WPF]
- URIs (Uniform Resource Identifiers)
- custom objects [WPF]
- Uniform Resource Identifiers (URIs)
- pages [WPF]
- frames [WPF]
- navigation hosts [WPF]
- journals [WPF]
- lifetimes [WPF]
- retaining content state [WPF]
- content state [WPF]
- programmatic navigation [WPF]
- hyperlinks [WPF]
ms.assetid: 86ad2143-606a-4e34-bf7e-51a2594248b8
ms.openlocfilehash: 874bc0b1b0ac38210569632dc3d21ed727ae26e4
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291640"
---
# <a name="navigation-overview"></a>巡覽概觀

Windows Presentation Foundation （WPF）支援瀏覽器樣式的導覽，可用於兩種類型的應用程式：獨立應用程式和 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]。 若要封裝內容以進行導覽，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供 <xref:System.Windows.Controls.Page> 類別。 您可以使用 <xref:System.Windows.Navigation.NavigationService>，以宣告方式從一個 <xref:System.Windows.Controls.Page> 流覽至另一個，方法是使用 <xref:System.Windows.Documents.Hyperlink> 或以程式設計方式。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用日誌記憶曾經巡覽過的頁面，以利返回巡覽。

<xref:System.Windows.Controls.Page>，<xref:System.Windows.Documents.Hyperlink>，<xref:System.Windows.Navigation.NavigationService>，而日誌會形成 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 所提供的導覽支援的核心。 本總覽會在涵蓋先進的導覽支援（包含鬆散的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案、HTML 檔案和物件）之前，先深入探索這些功能。

> [!NOTE]
> 在本主題中，「瀏覽器」一詞只是指可以裝載 @no__t 0 應用程式的瀏覽器，其中目前包含 Microsoft Internet Explorer 和 Firefox。 只有特定的瀏覽器才支援特定的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 功能時，會參考瀏覽器版本。

## <a name="navigation-in-wpf-applications"></a>WPF 應用程式中的巡覽

本主題提供 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的主要導覽功能的總覽。 這些功能可供獨立應用程式和 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 使用，雖然本主題會在 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的內容中呈現它們。

> [!NOTE]
> 本主題不會討論如何建立和部署 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]。 如需 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 的詳細資訊，請參閱[WPF XAML 瀏覽器應用程式總覽](wpf-xaml-browser-applications-overview.md)。

本節說明並示範下列巡覽的各個面向︰

- [實作頁面](#CreatingAXAMLPage)

- [設定起始頁](#Configuring_a_Start_Page)

- [設定主機視窗的標題、寬度和高度](#ConfiguringAXAMLPage)

- [超連結巡覽](#NavigatingBetweenXAMLPages)

- [片段巡覽](#FragmentNavigation)

- [巡覽服務](#NavigationService)

- [以程式設計的巡覽及巡覽服務](#Programmatic_Navigation_with_the_Navigation_Service)

- [巡覽存留期](#Navigation_Lifetime)

- [以日誌記憶巡覽](#NavigationHistory)

- [網頁存留期和日誌](#PageLifetime)

- [以巡覽記錄保留內容狀態](#RetainingContentStateWithNavigationHistory)

- [Cookie](#Cookies)

- [結構化巡覽](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a>實作頁面

在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，您可以流覽至數種內容類型，包括 .NET Framework 物件、自訂物件、列舉值、使用者控制項、@no__t 1 檔案和 HTML 檔案。 不過，您會發現封裝內容最常見且方便的方式，就是使用 <xref:System.Windows.Controls.Page>。 此外，<xref:System.Windows.Controls.Page> 會執行導覽特有的功能，以增強其外觀並簡化開發。

使用 <xref:System.Windows.Controls.Page>，您可以使用如下所示的標記，以宣告方式執行 @no__t 1 內容的可流覽頁面。

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記中執行的 <xref:System.Windows.Controls.Page> 會以 `Page` 作為其根項目，而且需要 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] @ no__t-4 命名空間宣告。 @No__t-0 元素包含您要流覽和顯示的內容。 您可以藉由設定 `Page.Content` 屬性元素來新增內容，如下列標記所示。

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` 只能包含一個子項目。在上例中，內容是單一字串 "Hello, Page!" 在實務上，您通常會使用版面配置控制項做為子專案（請參閱[版面](../advanced/layout.md)配置）以包含及撰寫內容。

@No__t 0 元素的子項目會被視為 <xref:System.Windows.Controls.Page> 的內容，因此，您不需要使用明確的 `Page.Content` 宣告。 下列標記是前例的宣告式對等項目。

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

在此情況下，`Page.Content` 會自動設定為 `Page` 元素的子項目。 如需詳細資訊，請參閱 [WPF 內容模型](../controls/wpf-content-model.md)。

僅限標記的 <xref:System.Windows.Controls.Page> 適用于顯示內容。 不過，@no__t 0 也可以顯示允許使用者與頁面互動的控制項，而且它可以藉由處理事件和呼叫應用程式邏輯來回應使用者互動。 互動式 <xref:System.Windows.Controls.Page> 是使用標記和程式碼後置的組合來執行，如下列範例所示。

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

若要讓標記檔案和程式碼後置檔案一起工作，需要設定下列項目：

- 在標記中，`Page` 元素必須包含 `x:Class` 屬性。 建立應用程式時，標記檔案中的 `x:Class` 存在會導致 Microsoft build engine （MSBuild）建立衍生自 <xref:System.Windows.Controls.Page> 的 @no__t 1 類別，且其名稱是由 `x:Class` 屬性所指定。 這需要為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 架構（`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`）新增 @no__t 0 的命名空間宣告。 產生的 `partial` 類別會執行 `InitializeComponent`，這會呼叫來註冊事件並設定在標記中執行的屬性。

- 在程式碼後置中，類別必須是與標記中的 `x:Class` 屬性所指定相同名稱的 @no__t 0 類別，而且必須衍生自 <xref:System.Windows.Controls.Page>。 這可讓程式碼後置檔案與建立應用程式時為標記檔案產生的 `partial` 類別相關聯（請參閱[建立 WPF 應用程式](building-a-wpf-application-wpf.md)）。

- 在程式碼後置中，@no__t 0 類別必須執行呼叫 `InitializeComponent` 方法的函式。 `InitializeComponent` 是由標記檔案產生的 @no__t 1 類別所執行，以註冊事件並設定在標記中定義的屬性。

> [!NOTE]
> 當您使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 將新的 <xref:System.Windows.Controls.Page> 加入至專案時，會同時使用標記和程式碼後置來執行 <xref:System.Windows.Controls.Page>，並包含必要的設定來建立標記和程式碼後置檔案之間的關聯，如這裡所述。

一旦您有 <xref:System.Windows.Controls.Page>，就可以流覽至它。 若要指定應用程式流覽的第一個 <xref:System.Windows.Controls.Page>，您必須設定 start <xref:System.Windows.Controls.Page>。

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>設定起始頁

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 需要瀏覽器中裝載一定數量的應用程式基礎結構。 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，<xref:System.Windows.Application> 類別是應用程式定義的一部分，可建立必要的應用程式基礎結構（請參閱[應用程式管理總覽](application-management-overview.md)）。

應用程式定義通常會使用標記和程式碼後置來實作為，並將標記檔案設定為 MSBuild @ no__t-0 專案。 以下是 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的應用程式定義。

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

@No__t-0 可以使用其應用程式定義來指定開始 <xref:System.Windows.Controls.Page>，也就是啟動 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 時，會自動載入的 <xref:System.Windows.Controls.Page>。 若要這麼做，您可以為所需的 <xref:System.Windows.Controls.Page>，將 <xref:System.Windows.Application.StartupUri%2A> 屬性設定為 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]。

> [!NOTE]
> 在大部分情況下，<xref:System.Windows.Controls.Page> 會編譯成或與應用程式一起部署。 在這些情況下，可識別 <xref:System.Windows.Controls.Page> 的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 是套件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，這是符合*套件*配置的 @no__t 3。 套件 [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 會在 WPF 的[Pack uri](pack-uris-in-wpf.md)中進一步討論。 您也可以巡覽至使用 http 配置的內容，後文會討論。

您可以在標記中以宣告方式設定 <xref:System.Windows.Application.StartupUri%2A>，如下列範例所示。

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

在此範例中，`StartupUri` 屬性是以識別首頁的相對套件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 來設定。 當 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 啟動時，首頁. xaml 會自動流覽並顯示。 如下圖所示，這會顯示從 Web 服務器啟動的 @no__t 0。

![Xbap 頁面](./media/navigation-overview/xbap-launched-from-a-web-server.png "：這會顯示從 Web 服務器啟動的 XBAP。")

> [!NOTE]
> 如需有關 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 的開發和部署的詳細資訊，請參閱[WPF XAML 瀏覽器應用程式總覽](wpf-xaml-browser-applications-overview.md)和[部署 wpf 應用程式](deploying-a-wpf-application-wpf.md)。

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>設定主機視窗的標題、寬度和高度

您在上圖中可能注意到的一件事，就是瀏覽器和索引標籤面板的標題都是 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。 除了長之外，標題既不吸引人，也不提供資訊。 基於這個理由，<xref:System.Windows.Controls.Page> 提供了一種方式，可讓您藉由設定 <xref:System.Windows.Controls.Page.WindowTitle%2A> 屬性來變更標題。 此外，您可以分別設定 <xref:System.Windows.Controls.Page.WindowWidth%2A> 和 <xref:System.Windows.Controls.Page.WindowHeight%2A>，來設定瀏覽器視窗的寬度和高度。

<xref:System.Windows.Controls.Page.WindowTitle%2A>、<xref:System.Windows.Controls.Page.WindowWidth%2A> 和 <xref:System.Windows.Controls.Page.WindowHeight%2A> 可以在標記中以宣告方式設定，如下列範例所示。

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

其結果如下圖所示。

![視窗標題、高度、寬度：](./media/navigation-overview/window-title-width-height.png "這會顯示您可以設定的視窗標題、高度和寬度。")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>超連結巡覽

典型的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 包含數個頁面。 從一頁流覽至另一個頁面的最簡單方式是使用 <xref:System.Windows.Documents.Hyperlink>。 您可以使用 `Hyperlink` 元素（如下列標記所示），以宣告方式將 <xref:System.Windows.Documents.Hyperlink> 加入至 <xref:System.Windows.Controls.Page>。

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

@No__t-0 元素需要下列專案：

- 要導覽至之 <xref:System.Windows.Controls.Page> 的套件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，如 `NavigateUri` 屬性所指定。

- 使用者可以按一下以起始導覽的內容，例如文字和影像（針對 @no__t 0 元素可以包含的內容，請參閱 <xref:System.Windows.Documents.Hyperlink>）。

下圖顯示具有 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> 的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]。

![具有超連結的頁面](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "：顯示具有超連結頁面的 XBAP。")

如您所預期，按一下 <xref:System.Windows.Documents.Hyperlink> 會導致 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 流覽至 `NavigateUri` 屬性所識別的 <xref:System.Windows.Controls.Page>。 此外，[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 會將先前 <xref:System.Windows.Controls.Page> 的專案新增到 Internet Explorer 的 [最近使用的頁面] 清單中。 如下圖所示。

[![上一頁] 和 [下一頁] 按鈕]會(./media/navigation-overview/back-and-forward-navigation.png "以 [上一頁] 和 [下一頁] 按鈕導覽。")

此外，支援從一個 <xref:System.Windows.Controls.Page> 到另一個的導覽，<xref:System.Windows.Documents.Hyperlink> 也支援片段導覽。

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>片段巡覽

*片段導覽*是目前 <xref:System.Windows.Controls.Page> 或另一個 <xref:System.Windows.Controls.Page> 的內容片段導覽。 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，內容片段是已命名專案所包含的內容。 已命名的元素是已設定其 @no__t 0 屬性的元素。 下列標記顯示名為的 @no__t 0 元素，其中包含內容片段。

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

若要讓 <xref:System.Windows.Documents.Hyperlink> 流覽至內容片段，@no__t 1 屬性必須包括下列各項：

- @No__t-1 的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，其中包含要流覽的內容片段。

- "#" 字元。

- @No__t 0 上包含內容片段之元素的名稱。

@No__t-0 的片段具有下列格式。

*PageURI* `#` <項目名稱>

以下顯示的範例是設定為流覽至內容片段的 @no__t 0。

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> 本節說明 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的預設片段導覽執行。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 也可以讓您執行自己的片段導覽配置，而這部分必須處理 <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> 事件。

> [!IMPORTANT]
> 只有在可以透過 HTTP 流覽頁面時，您才可以流覽至鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面中的片段（僅限標記的 @no__t 1 個檔案，其中只有 `Page` 做為根項目）。
>
> 不過，鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面可以流覽至它自己的片段。

<a name="NavigationService"></a>

### <a name="navigation-service"></a>巡覽服務

雖然 <xref:System.Windows.Documents.Hyperlink> 允許使用者起始特定 <xref:System.Windows.Controls.Page> 的導覽，但尋找和下載頁面的工作是由 @no__t 2 類別執行。 基本上，<xref:System.Windows.Navigation.NavigationService> 提供代表用戶端程式代碼（例如 <xref:System.Windows.Documents.Hyperlink>）處理導覽要求的功能。 此外，<xref:System.Windows.Navigation.NavigationService> 會執行追蹤和影響導覽要求的更高層級支援。

當按下 <xref:System.Windows.Documents.Hyperlink> 時，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會呼叫 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 來尋找並下載 <xref:System.Windows.Controls.Page> （在指定的套件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]）。 下載的 <xref:System.Windows.Controls.Page> 會轉換成物件的樹狀結構，其根物件是已下載 <xref:System.Windows.Controls.Page> 的實例。 根 <xref:System.Windows.Controls.Page> 物件的參考會儲存在 <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> 屬性中。 所流覽之內容的套件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 會儲存在 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> 屬性中，而 <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> 則會針對流覽至的最後一頁，儲存套件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。

> [!NOTE]
> @No__t 0 應用程式可能會有一個以上的目前作用中 <xref:System.Windows.Navigation.NavigationService>。 如需詳細資訊，請參閱本主題稍後的[導覽主機](#Navigation_Hosts)。

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>以程式設計的巡覽及巡覽服務

如果使用 <xref:System.Windows.Documents.Hyperlink> 在標記中以宣告方式實作為導覽，您就不需要知道 <xref:System.Windows.Navigation.NavigationService>，因為 <xref:System.Windows.Documents.Hyperlink> 會代表您使用 <xref:System.Windows.Navigation.NavigationService>。 這表示，只要 <xref:System.Windows.Documents.Hyperlink> 的直接或間接父系是導覽主機（請參閱 [[導覽主機](#Navigation_Hosts)]），<xref:System.Windows.Documents.Hyperlink> 就能夠尋找和使用導覽主機的導覽服務來處理導覽要求。

不過，在某些情況下，您必須直接使用 <xref:System.Windows.Navigation.NavigationService>，包括下列各項：

- 當您需要使用非無參數的函式來具現化 <xref:System.Windows.Controls.Page> 時。

- 當您需要先設定 <xref:System.Windows.Controls.Page> 的屬性，然後再流覽至它。

- 當需要流覽的 <xref:System.Windows.Controls.Page> 時，只能在執行時間決定。

在這些情況下，您需要撰寫程式碼，藉由呼叫 <xref:System.Windows.Navigation.NavigationService> 物件的 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> 方法來以程式設計方式起始導覽。 這需要取得 <xref:System.Windows.Navigation.NavigationService> 的參考。

#### <a name="getting-a-reference-to-the-navigationservice"></a>取得 NavigationService 的參考

基於 [[導覽主機](#Navigation_Hosts)] 區段中所述的原因，@no__t 1 應用程式可以有一個以上的 <xref:System.Windows.Navigation.NavigationService>。 這表示您的程式碼需要一種方式來尋找 <xref:System.Windows.Navigation.NavigationService>，這通常是流覽至目前 <xref:System.Windows.Controls.Page> 的 <xref:System.Windows.Navigation.NavigationService>。 您可以藉由呼叫 `static` @ no__t-2 方法來取得 <xref:System.Windows.Navigation.NavigationService> 的參考。 若要取得流覽至特定 <xref:System.Windows.Controls.Page> 的 <xref:System.Windows.Navigation.NavigationService>，請將 <xref:System.Windows.Controls.Page> 的參考傳遞至 <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> 方法的引數。 下列程式碼顯示如何取得目前 <xref:System.Windows.Controls.Page> 的 <xref:System.Windows.Navigation.NavigationService>。

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

若要尋找 <xref:System.Windows.Controls.Page> 之 <xref:System.Windows.Navigation.NavigationService> 的快捷方式，<xref:System.Windows.Controls.Page> 會執行 <xref:System.Windows.Controls.Page.NavigationService%2A> 屬性。 這在下列範例中顯示。

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> 當 <xref:System.Windows.Controls.Page> 引發 <xref:System.Windows.FrameworkElement.Loaded> 事件時，<xref:System.Windows.Controls.Page> 只能取得其 <xref:System.Windows.Navigation.NavigationService> 的參考。

#### <a name="programmatic-navigation-to-a-page-object"></a>以程式設計方式巡覽至頁面物件

下列範例顯示如何使用 <xref:System.Windows.Navigation.NavigationService>，以程式設計方式流覽至 <xref:System.Windows.Controls.Page>。 必須以程式設計方式導覽，因為所流覽至的 <xref:System.Windows.Controls.Page> 只能使用單一、非參數的函式來具現化。 具有非無參數的函式的 <xref:System.Windows.Controls.Page> 會顯示在下列標記和程式碼中。

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

使用非無參數的函式來流覽至 <xref:System.Windows.Controls.Page> 的 <xref:System.Windows.Controls.Page> 會顯示在下列標記和程式碼中。

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

當此 @no__t 上的 <xref:System.Windows.Documents.Hyperlink> 按下時，就會藉由具現化 <xref:System.Windows.Controls.Page> 來起始導覽，以使用非無參數的函式來流覽至，並呼叫 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 方法。 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> 會接受 <xref:System.Windows.Navigation.NavigationService> 將導覽至之物件的參考，而不是 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的套件。

#### <a name="programmatic-navigation-with-a-pack-uri"></a>以程式設計的巡覽及 Pack URI

如果您需要以程式設計方式建立套件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] （例如，當您只能在執行時間判斷套件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]）時，您可以使用 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 方法。 這在下列範例中顯示。

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>重新整理目前的頁面

如果 <xref:System.Windows.Controls.Page> 的套件與儲存在 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> 屬性中的 pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，則不會下載。 若要強制 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 再次下載目前的頁面，您可以呼叫 <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> 方法，如下列範例所示。

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>巡覽存留期

如您所見，有多種方式可以初始化巡覽。 當導覽已起始，而且導覽正在進行時，您可以使用下列 @no__t 所實的事件來追蹤和影響導覽：

- <xref:System.Windows.Navigation.NavigationService.Navigating>. 要求新的巡覽時發生。 可用於取消巡覽。

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. 在下載期間定期發生以提供導覽進度資訊。

- <xref:System.Windows.Navigation.NavigationService.Navigated>. 找到並下載頁面時發生。

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. 當導覽停止（藉由呼叫 <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>）時發生，或在目前的導覽正在進行中要求新的流覽時，就會發生。

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. 在廵覽至要求的內容引發錯誤時發生。

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. 當載入並剖析巡覽到的內容，且開始轉譯時發生。

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. 當內容片段巡覽開始時發生，狀況為︰

  - 立即發生，如果所需片段位在目前的內容中。

  - 載入來源內容之後，如果所需片段位在不同的內容中。

下圖顯示巡覽事件的引發順序。

![頁面導覽流程圖](./media/navigation-overview/order-of-navigation-events.png "頁面導覽事件流程圖表")

一般來說，<xref:System.Windows.Controls.Page> 並不在意這些事件。 應用程式很有可能會擔心它們，因此，這些事件也會由 <xref:System.Windows.Application> 類別引發：

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

每次 <xref:System.Windows.Navigation.NavigationService> 引發事件時，@no__t 1 類別就會引發對應的事件。 <xref:System.Windows.Controls.Frame> 和 <xref:System.Windows.Navigation.NavigationWindow> 提供相同的事件，以偵測其各自範圍內的導覽。

在某些情況下，<xref:System.Windows.Controls.Page> 可能會對這些事件感興趣。 例如，@no__t 0 可能會處理 <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> 事件，以判斷是否要取消本身的導覽。 這在下列範例中顯示。

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

如果您使用來自 <xref:System.Windows.Controls.Page> 的導覽事件來註冊處理常式，如上述範例所示，您也必須取消註冊事件處理常式。 如果您不想這麼做，則可能會有關于 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 導覽如何記住使用日誌 <xref:System.Windows.Controls.Page> 導覽的副作用。

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>以日誌記憶巡覽

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用兩個堆疊記憶您曾廵覽過的頁面︰上一頁堆疊和下一頁堆疊。 當您從目前的 <xref:System.Windows.Controls.Page> 流覽至新的 <xref:System.Windows.Controls.Page> 或轉送到現有的 <xref:System.Windows.Controls.Page> 時，會將目前的 <xref:System.Windows.Controls.Page> 新增至*後端堆疊*。 當您從目前的 <xref:System.Windows.Controls.Page> 流覽回到先前的 <xref:System.Windows.Controls.Page> 時，會將目前的 <xref:System.Windows.Controls.Page> 新增至*正向堆疊*中。 上一頁堆疊、下一頁堆疊和管理它們的功能，統稱為日誌。 後端堆疊和轉寄堆疊中的每個專案都是 <xref:System.Windows.Navigation.JournalEntry> 類別的實例，而則稱為*日誌項目*。

#### <a name="navigating-the-journal-from-internet-explorer"></a>從 Internet Explorer 巡覽日誌

就概念而言，日誌的運作方式與 Internet Explorer 中的 [**上一頁**] 和 [**下一頁**] 按鈕相同。 如下圖所示。

[![上一頁] 和 [下一頁] 按鈕]會(./media/navigation-overview/back-and-forward-navigation.png "以 [上一頁] 和 [下一頁] 按鈕導覽。")

若為 Internet Explorer 所裝載的 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會將日誌整合到 Internet Explorer 的導覽 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 這可讓使用者使用 Internet Explorer 中的 [**上一頁**]、[**下一頁**] 和 [**最近的頁面**] 按鈕，在 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 中流覽頁面。

> [!IMPORTANT]
> 在 Internet Explorer 中，當使用者流覽離開並返回 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 時，只有未保持運作的頁面記錄項目會保留在日誌中。 如需讓頁面保持運作的討論，請參閱本主題稍後的[頁面存留期和日誌](#PageLifetime)。

根據預設，Internet Explorer [**最近使用的頁面**] 清單中出現的每個 <xref:System.Windows.Controls.Page> 的文字，都是 <xref:System.Windows.Controls.Page> 的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。 在許多情況下，這對使用者都不是特別有意義。 幸運的是，您可以變更使用下列選項之一的文字︰

1. 附加的 `JournalEntry.Name` 屬性值。

2. @No__t-0 屬性值。

3. @No__t-0 屬性值和目前 <xref:System.Windows.Controls.Page> 的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。

4. 目前 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的 <xref:System.Windows.Controls.Page>。 (預設值)

選項列示順序符合尋找文字的優先順序。 例如，如果已設定 `JournalEntry.Name`，則會忽略其他值。

下列範例會使用 `Page.Title` 屬性來變更日誌項目所顯示的文字。

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>巡覽使用 WPF 的日誌

雖然使用者可以使用 Internet Explorer 中的 [**上一頁**]、[**下一頁**] 和 [**最近] 頁面**來流覽日誌，但是您也可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 所提供的宣告式和程式設計機制來流覽日誌。 這麼做的其中一個原因是在您的頁面中提供自訂的導覽 Ui。

您可以使用 <xref:System.Windows.Input.NavigationCommands> 所公開的導覽命令，以宣告方式新增日誌導覽支援。 下列範例示範如何使用 `BrowseBack` 導覽命令。

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

您可以使用 <xref:System.Windows.Navigation.NavigationService> 類別的下列其中一個成員，以程式設計方式流覽日誌：

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

您也可以透過程式設計方式動作記錄，如本主題稍後的[保留內容狀態與導覽歷程記錄](#RetainingContentStateWithNavigationHistory)中所述。

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>網頁存留期和日誌

假設有數個頁面包含豐富內容的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]，包括圖形、動畫和媒體。 這類頁面的磁碟使用量可能相當大，尤其是使用視訊和音訊媒體的時候。 假設筆記本「記憶」已流覽過的頁面，這類 @no__t 0 可能很快就會耗用大量且顯著的記憶體數量。

基於這個理由，日誌的預設行為是將 <xref:System.Windows.Controls.Page> 中繼資料儲存在每個日誌項目中，而不是對 @no__t 1 物件的參考。 當流覽到日誌項目時，會使用其 <xref:System.Windows.Controls.Page> 中繼資料來建立指定 <xref:System.Windows.Controls.Page> 的新實例。 因此，流覽的每個 <xref:System.Windows.Controls.Page> 都具有下圖所說明的存留期。

![頁面存留期](./media/navigation-overview/navigated-page-lifetime.png "：這會顯示流覽頁面時的存留期。")

雖然使用預設日誌行為可以節省記憶體耗用量，但每頁轉譯的效能可能會降低;reinstantiating <xref:System.Windows.Controls.Page> 可能會耗費大量時間，特別是當它有許多內容時。 如果您需要將 <xref:System.Windows.Controls.Page> 實例保留在日誌中，您可以使用兩種技術來進行繪製。 首先，您可以藉由呼叫 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 方法，以程式設計方式流覽至 @no__t 0 物件。

第二，您可以將 [<xref:System.Windows.Controls.Page.KeepAlive%2A>] 屬性設為 [`true`] （預設值為 `false`），指定 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 將 <xref:System.Windows.Controls.Page> 的實例保留在日誌中。 如下列範例所示，您可以在標記中以宣告方式設定 <xref:System.Windows.Controls.Page.KeepAlive%2A>。

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

保持運作之 <xref:System.Windows.Controls.Page> 的存留期間，與不會有任何差異。 第一次會流覽至保持運作的 <xref:System.Windows.Controls.Page> 時，它會具現化，就像未保持運作的 <xref:System.Windows.Controls.Page> 一樣。 不過，因為 <xref:System.Windows.Controls.Page> 的實例會保留在日誌中，所以只要它保留在日誌中，就不會再次具現化。 因此，如果 <xref:System.Windows.Controls.Page> 具有必須在每次流覽 <xref:System.Windows.Controls.Page> 時呼叫的初始化邏輯，您應該將它從函式移至 @no__t 2 事件的處理常式。 如下圖所示，每次從流覽到和 @no__t 時，<xref:System.Windows.FrameworkElement.Loaded> 和 @no__t 1 事件仍會引發。

![當載入和卸載的事件已](./media/navigation-overview/loaded-and-unloaded-events.png "載入，而且當頁面導覽至和時，會引發卸載的事件。")

當 <xref:System.Windows.Controls.Page> 未保持運作時，您不應該執行下列其中一項動作：

- 儲存其參考或任何部分。

- 使用它未實作的事件來登錄事件處理常式。

執行其中一項作業會建立參考，強制將 <xref:System.Windows.Controls.Page> 保留在記憶體中，即使已從日誌中移除也一樣。

一般來說，您應該偏好預設的 <xref:System.Windows.Controls.Page> 的行為，而不讓 <xref:System.Windows.Controls.Page> 保持運作。 不過，這有下一節要討論的隱含狀態。

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>以巡覽記錄保留內容狀態

如果 <xref:System.Windows.Controls.Page> 未保持運作，而且它具有可從使用者收集資料的控制項，則當使用者流覽離開並回到 <xref:System.Windows.Controls.Page> 時，資料會發生什麼事？ 從使用者體驗的觀點而言，使用者應該會希望看到他們先前所輸入的資料。 可惜的是，因為每個導覽都會建立 <xref:System.Windows.Controls.Page> 的新實例，所以會 reinstantiated 收集資料的控制項並遺失資料。

幸運的是，日誌提供了在 @no__t 0 的導覽（包括控制資料）上記住資料的支援。 具體而言，每個 <xref:System.Windows.Controls.Page> 的日誌項目會作為相關聯之 <xref:System.Windows.Controls.Page> 狀態的暫存容器。 下列步驟概述從流覽 <xref:System.Windows.Controls.Page> 時，如何使用這項支援：

1. 目前 <xref:System.Windows.Controls.Page> 的專案會新增至日誌。

2. @No__t-0 的狀態會與該頁面的日誌項目一起儲存，這會新增至後端堆疊。

3. 新的 <xref:System.Windows.Controls.Page> 會被流覽至。

當頁面 <xref:System.Windows.Controls.Page> 流覽回時，使用日誌，會進行下列步驟：

1. @No__t-0 （後端堆疊上的前幾個日誌項目）已具現化。

2. @No__t-0 會使用與 <xref:System.Windows.Controls.Page> 的日誌項目一起儲存的狀態重新整理。

3. @No__t-0 會被流覽回。

當下列控制項用於 <xref:System.Windows.Controls.Page> 時，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會自動使用這項支援：

- <xref:System.Windows.Controls.CheckBox>

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.Expander>

- <xref:System.Windows.Controls.Frame>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListBoxItem>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.ProgressBar>

- <xref:System.Windows.Controls.RadioButton>

- <xref:System.Windows.Controls.Slider>

- <xref:System.Windows.Controls.TabControl>

- <xref:System.Windows.Controls.TabItem>

- <xref:System.Windows.Controls.TextBox>

如果 <xref:System.Windows.Controls.Page> 使用這些控制項，則會在 @no__t 1 的導覽中記憶輸入的資料，如下圖中的**最愛色彩**<xref:System.Windows.Controls.ListBox> 所示。

包含所輸入狀態資料之![控制項的頁面]，(./media/navigation-overview/data-remembered-across-page-navigations.png "會在頁面導覽中記住。")

當 <xref:System.Windows.Controls.Page> 除了上述清單中的控制項以外，或當狀態儲存在自訂物件中時，您必須撰寫程式碼，讓日誌在 @no__t 1 的導覽中記住狀態。

如果您需要在 <xref:System.Windows.Controls.Page> 的導覽之間記住較小的狀態片段，您可以使用以 @no__t 2 中繼資料旗標設定的相依性屬性（請參閱 <xref:System.Windows.DependencyProperty>）。

如果您的 <xref:System.Windows.Controls.Page> 在跨導覽時必須記住的狀態包含多個資料片段，您可能會發現在單一類別中封裝您的狀態並執行 @no__t 1 介面的程式碼較少。

如果您需要流覽單一 <xref:System.Windows.Controls.Page> 的各種狀態，而不是從 <xref:System.Windows.Controls.Page> 開始流覽，您可以使用 <xref:System.Windows.Navigation.IProvideCustomContentState> 和 <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>。

<a name="Cookies"></a>

### <a name="cookies"></a>Cookie

@No__t-0 應用程式可以儲存資料的另一種方式，是使用 <xref:System.Windows.Application.SetCookie%2A> 和 @no__t 2 方法來建立、更新和刪除 cookie。 您可以在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中建立的 cookie 與其他類型的 Web 應用程式所使用的 cookie 相同。cookie 是應用程式在應用程式會話期間或之間儲存的任意資料片段。 Cookie 資料通常會採用下列格式的名稱/值組形式。

「名稱」`=`「值」

將資料傳遞給 <xref:System.Windows.Application.SetCookie%2A> 時，以及應設定 cookie 的位置 <xref:System.Uri>，就會在記憶體中建立 cookie，而且僅適用于目前應用程式會話的持續時間。 這種類型的 cookie 稱為*會話 cookie*。

若要在應用程式工作階段之間儲存 Cookie，到期日必須使用下列格式新增至 Cookie。

「名稱」`=`「值」`; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

具有到期日的 cookie 會儲存在目前 Windows 安裝的 [Internet Files] 資料夾中，直到 cookie 到期為止。 這類 cookie 稱為*持續性 cookie* ，因為它會在應用程式會話之間持續保存。

您可以藉由呼叫 <xref:System.Windows.Application.GetCookie%2A> 方法，傳遞 cookie 的 <xref:System.Uri> 和 @no__t 2 方法，來抓取會話和持續性 cookie。

以下是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中支援 cookie 的一些方式：

- @no__t 0 獨立應用程式和 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 都可以建立和管理 cookie。

- @No__t-0 所建立的 cookie 可從瀏覽器存取。

- 來自相同網域的 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 可以建立及共用 Cookie。

- 來自相同網域的 @no__t 0 和 HTML 網頁可以建立和共用 cookie。

- 當 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，而鬆散的 @no__t 1 頁提出 Web 要求時，會分派 cookie。

- 在 IFRAME 中裝載的頂層 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 和 @no__t 1 都可以存取 cookie。

- @No__t 中的 Cookie 支援-0 對所有支援的瀏覽器都是相同的。

- 在 Internet Explorer 中，與 cookie 相關的 P3P 原則會由 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 接受，特別是第一方和協力廠商 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]。

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>結構化巡覽

如果您需要將資料從 <xref:System.Windows.Controls.Page> 傳遞至另一個，您可以將資料當做引數傳遞給 <xref:System.Windows.Controls.Page> 的非參數函式。 請注意，如果您使用這項技術，您必須保持 <xref:System.Windows.Controls.Page> 的運作狀態;如果不是，則下一次流覽至 <xref:System.Windows.Controls.Page> 時，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會使用無參數的函式來 reinstantiates <xref:System.Windows.Controls.Page>。

或者，您的 <xref:System.Windows.Controls.Page> 可以執行使用需要傳遞的資料所設定的屬性。 不過，當 @no__t 0 必須將資料傳回給導覽到它的 <xref:System.Windows.Controls.Page> 時，就會變得很棘手。 問題在於，導覽並不是原本就支援機制，以確保在流覽之後，<xref:System.Windows.Controls.Page> 會傳回給。 基本上，巡覽不支援呼叫/傳回語意。 若要解決這個問題，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供 @no__t 1 類別，您可以使用此類別來確保以可預測且結構化的方式傳回 @no__t 2。 如需詳細資訊，請參閱[結構化導覽總覽](structured-navigation-overview.md)。

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow 類別

至此，您已了解最可能用來建置有可巡覽內容之應用程式的巡覽服務範圍。 這些服務是在 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 的內容中討論，但它們並不限於 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]。 新式作業系統和 Windows 應用程式利用新式使用者的瀏覽器體驗，將瀏覽器樣式的導覽併入獨立應用程式中。 常見範例包括︰

- **Word**同義字：流覽 word 選擇。

- 檔案**瀏覽器**：流覽檔案和資料夾。

- **嚮導**：將複雜的工作分解成可以在之間流覽的多個頁面。 其中一個範例是處理新增和移除 Windows 功能的 Windows 元件 Wizard。

若要將瀏覽器樣式的導覽併入您的獨立應用程式，您可以使用 <xref:System.Windows.Navigation.NavigationWindow> 類別。 <xref:System.Windows.Navigation.NavigationWindow> 衍生自 <xref:System.Windows.Window>，並以 @no__t 2 提供的相同導覽支援來加以擴充。 您可以使用 <xref:System.Windows.Navigation.NavigationWindow> 做為獨立應用程式的主視窗，或當做對話方塊之類的次要視窗。

若要執行 <xref:System.Windows.Navigation.NavigationWindow>，如同 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] （<xref:System.Windows.Window>、<xref:System.Windows.Controls.Page> 等的大部分最上層類別），您可以使用標記和程式碼後置的組合。 這在下列範例中顯示。

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

這段程式碼會建立 <xref:System.Windows.Navigation.NavigationWindow>，在開啟 <xref:System.Windows.Navigation.NavigationWindow> 時，自動流覽至 <xref:System.Windows.Controls.Page> （首頁. xaml）。 如果 <xref:System.Windows.Navigation.NavigationWindow> 是主應用程式視窗，您可以使用 `StartupUri` 屬性來啟動它。 下列標記顯示此做法。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

下圖顯示 <xref:System.Windows.Navigation.NavigationWindow>，做為獨立應用程式的主視窗。

![主]視窗(./media/navigation-overview/navigation-window-as-main-window.png "流覽視窗做為主視窗")

從圖中，您可以看到 <xref:System.Windows.Navigation.NavigationWindow> 有一個標題，即使它並未設定在上述範例的 @no__t 1 實程式碼中也一樣。 而是使用 <xref:System.Windows.Controls.Page.WindowTitle%2A> 屬性來設定標題，如下列程式碼所示。

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

設定 <xref:System.Windows.Controls.Page.WindowWidth%2A> 和 @no__t 1 屬性也會影響 <xref:System.Windows.Navigation.NavigationWindow>。

當您需要自訂其行為或其外觀時，通常會執行自己的 <xref:System.Windows.Navigation.NavigationWindow>。 如果兩樣都不做，您可以使用捷徑。 如果您在獨立應用程式中指定 <xref:System.Windows.Controls.Page> 的套件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 做為 <xref:System.Windows.Application.StartupUri%2A>，<xref:System.Windows.Application> 會自動建立 <xref:System.Windows.Navigation.NavigationWindow> 來裝載 <xref:System.Windows.Controls.Page>。 下列標記顯示如何啟用此功能。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

如果您想要讓對話方塊之類的次要應用程式視窗成為 <xref:System.Windows.Navigation.NavigationWindow>，您可以使用下列範例中的程式碼來開啟它。

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

其結果如下圖所示。

![對話方塊](./media/navigation-overview/navigation-window-as-dialog-box.png "導覽視窗做為對話方塊")

如您所見，<xref:System.Windows.Navigation.NavigationWindow> 會顯示 Internet Explorer 樣式的 [**上一頁**] 和 [**下一頁**] 按鈕，讓使用者可以流覽日誌。 這些按鈕提供相同的使用者體驗，如下圖所示。

![](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "導覽視窗中 NavigationWindow 上一頁和下一頁按鈕")的 [上一頁] 和 [下一頁] 按鈕

如果您的頁面提供自己的日誌流覽支援和 UI，您可以將 <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> 屬性的值設定為 `false`，以隱藏 <xref:System.Windows.Navigation.NavigationWindow> 顯示的 [**上一頁**] 和 [**下一頁**] 按鈕。

或者，您可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的自訂支援來取代 <xref:System.Windows.Navigation.NavigationWindow> 本身的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Frame 類別

瀏覽器和 <xref:System.Windows.Navigation.NavigationWindow> 都是裝載可流覽內容的視窗。 在某些情況下，應用程式會有不需要由整個視窗裝載的內容。 這類內容反可以裝載於其他內容中。 您可以使用 <xref:System.Windows.Controls.Frame> 類別，將可流覽的內容插入至其他內容。 <xref:System.Windows.Controls.Frame> 提供與 <xref:System.Windows.Navigation.NavigationWindow> 和 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 相同的支援。

下列範例示範如何使用 `Frame` 元素，以宣告方式將 <xref:System.Windows.Controls.Frame> 加入至 <xref:System.Windows.Controls.Page>。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

此標記會針對 <xref:System.Windows.Controls.Frame> @no__t 一開始流覽至的 <xref:System.Windows.Controls.Page>，設定 `Frame` 元素的 `Source` 屬性。 下圖顯示 <xref:System.Windows.Controls.Page> 的 @no__t，其具有在數個頁面之間流覽的 <xref:System.Windows.Controls.Frame>。

![在多個頁面之間流覽的框架，這會](./media/navigation-overview/frame-navigation-between-multiple-pages.png "顯示多個頁面之間的框架導覽。")

您不只需要在 <xref:System.Windows.Controls.Page> 的內容內使用 <xref:System.Windows.Controls.Frame>。 在 <xref:System.Windows.Window> 的內容中裝載 <xref:System.Windows.Controls.Frame> 也是很常見的情況。

根據預設，只有在沒有另一個日誌時，<xref:System.Windows.Controls.Frame> 才會使用自己的日誌。 如果 <xref:System.Windows.Controls.Frame> 屬於裝載于 <xref:System.Windows.Navigation.NavigationWindow> 或 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 內的內容，<xref:System.Windows.Controls.Frame> 會使用屬於 <xref:System.Windows.Navigation.NavigationWindow> 或 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的日誌。 不過，有時候 @no__t 0 可能需要負責自己的日誌。 若要這麼做，其中一個原因是允許在 <xref:System.Windows.Controls.Frame> 所裝載的頁面內進行日誌導覽。 如下圖所示。

![框架和頁面圖表](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "：這會在框架所裝載的頁面中顯示日誌導覽。")

在此情況下，您可以將 <xref:System.Windows.Controls.Frame> 的 <xref:System.Windows.Controls.Frame.JournalOwnership%2A> 屬性設定為 <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>，以設定 <xref:System.Windows.Controls.Frame> 來使用自己的日誌。 下列標記顯示此做法。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

下圖說明在使用自己的日誌的 <xref:System.Windows.Controls.Frame> 內流覽的效果。

![使用自己的日誌的框架，](./media/navigation-overview/frame-uses-its-own-journal.png "這會顯示在使用自己的日誌的框架內流覽的效果。")

請注意，日誌項目會顯示在 <xref:System.Windows.Controls.Frame> 中的導覽 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，而不是 Internet Explorer。

> [!NOTE]
> 如果 <xref:System.Windows.Controls.Frame> 是裝載于 <xref:System.Windows.Window> 之內容的一部分，<xref:System.Windows.Controls.Frame> 會使用自己的日誌，因此會顯示自己的導覽 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。

如果您的使用者體驗需要 <xref:System.Windows.Controls.Frame> 才能提供自己的日誌，而不顯示導覽 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，您可以將 <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> 設定為 <xref:System.Windows.Visibility.Hidden>，以隱藏導覽 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 下列標記顯示此做法。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>巡覽裝載

<xref:System.Windows.Controls.Frame> 和 <xref:System.Windows.Navigation.NavigationWindow> 是稱為「導覽主機」的類別。 *導覽主機*是可流覽並顯示內容的類別。 為了完成這項工作，每個導覽主機都會使用自己的 @no__t 0 和日誌。 巡覽裝載的基本建構如下圖所示。

導覽主控制項的流覽![器圖表](./media/navigation-overview/navigation-host-construction.png "基本結構")

基本上，這可讓 <xref:System.Windows.Navigation.NavigationWindow> 和 <xref:System.Windows.Controls.Frame> 提供在瀏覽器中裝載時，@no__t 2 提供的相同導覽支援。

除了使用 <xref:System.Windows.Navigation.NavigationService> 和日誌以外，導覽主機還會實作為 <xref:System.Windows.Navigation.NavigationService> 所執行的相同成員。 如下圖所示。

![畫面格和 NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "導覽視窗和框架")中的日誌

這可讓您針對它們直接設計巡覽支援程式。 如果您需要為裝載于 <xref:System.Windows.Window> 的 <xref:System.Windows.Controls.Frame> 提供自訂導覽 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，可以考慮這一點。 此外，這兩種類型都會執行其他的導覽相關成員，包括 `BackStack` （<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>，<xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>）和 `ForwardStack` （<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>，<xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>），這可讓您分別列舉後端堆疊和轉送堆疊中的記錄項目。

如前所述，應用程式中可有多個日誌。 下圖提供這種情況的範例。

![一個應用程式內有多個日誌](./media/navigation-overview/multiple-journals-in-one-application.png "，這就是一個應用程式中多個日誌的範例。")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>巡覽至 XAML 頁面以外的內容

在本主題中，<xref:System.Windows.Controls.Page> 和 pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 已用來示範 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的各種導覽功能。 不過，編譯成應用程式的 <xref:System.Windows.Controls.Page> 並不是唯一可以流覽的內容類型，而套件 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 則不是識別內容的唯一方法。

如本節所示，您也可以流覽到鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案、HTML 檔案和物件。

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>巡覽至鬆散的 XAML 檔案

鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案是具有下列特性的檔案：

- 僅包含 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] （也就是沒有程式碼）。

- 具有適當的命名空間宣告。

- 具有 .xaml 副檔名。

例如，請考慮將下列內容儲存為鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案、Person. xaml。

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

當您按兩下檔案時，瀏覽器會開啟、巡覽至並顯示內容。 如下圖所示。

![顯示 person. xaml 檔案中的內容]會(./media/navigation-overview/contents-of-person-xaml-file.png "顯示 person. xaml 檔案的內容。")

您可以顯示鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案，如下所示：

- 在本機電腦、內部網路或網際網路上的網站。

- 通用命名慣例（UNC）檔案共用。

- 本機磁碟。

鬆散的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案可以新增至瀏覽器的 [我的最愛]，或是瀏覽器的首頁。

> [!NOTE]
> 如需發佈和啟動鬆散 @no__t （0）頁面的詳細資訊，請參閱[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)。

鬆散 @no__t 的一項限制是，您只能裝載安全的內容，以部分信任的方式執行。 例如，`Window` 不可以是鬆散 @no__t 1 檔案的根項目。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>使用框架巡覽至 HTML 檔案

如您所預期，您也可以流覽至 HTML。 您只需要提供使用 HTTP 配置的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。 例如，下列 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 會顯示流覽至 HTML 網頁的 <xref:System.Windows.Controls.Frame>。

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

流覽至 HTML 需要特殊許可權。 例如，您無法從在網際網路區域部分信任安全性沙箱中執行的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 進行流覽。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>使用 WebBrowser 控制項巡覽至 HTML 檔案

@No__t-0 控制項支援 HTML 檔案裝載、導覽和腳本/managed 程式碼互通性。 如需有關 @no__t 0 控制項的詳細資訊，請參閱 <xref:System.Windows.Controls.WebBrowser>。

如同 <xref:System.Windows.Controls.Frame>，使用 <xref:System.Windows.Controls.WebBrowser> 流覽至 HTML 需要特殊許可權。 例如，您可以從部分信任的應用程式，只流覽至位於來源網站的 HTML。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>巡覽至自訂物件

如果您有儲存為自訂物件的資料，顯示該資料的一種方式是使用系結至這些物件的內容來建立 <xref:System.Windows.Controls.Page> （請參閱資料系結[總覽](../data/data-binding-overview.md)）。 如果您不需要建立整個頁面此額外負荷，而只要顯示物件，則您可以改為直接巡覽至它們。

請考慮在下列程式碼中實作為 @no__t 0 的類別。

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

若要流覽至它，您可以呼叫 <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> 方法，如下列程式碼所示。

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

其結果如下圖所示。

![流覽至類別的頁面]：(./media/navigation-overview/page-navigates-to-an-object.png "這是導覽至物件的頁面範例。")

在此圖中，您看不到任何有用的內容。 事實上，顯示的值是**Person**物件的 `ToString` 方法的傳回值;根據預設，這是唯一的值，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可以用來代表您的物件。 您可以覆寫 `ToString` 方法以傳回更有意義的資訊，但它仍然只是字串值。 您可以使用的一項技術，利用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的呈現功能，就是使用資料範本。 您可以執行資料範本，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可以與特定類型的物件產生關聯。 下列程式碼顯示 `Person` 物件的資料範本。

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

在這裡，資料範本會使用 `DataType` 屬性中的 `x:Type` 標記延伸，與 `Person` 類型相關聯。 然後，資料範本會將 @no__t 0 元素（請參閱 <xref:System.Windows.Controls.TextBlock>）系結至 @no__t 2 類別的屬性。 下圖顯示 `Person` 物件的更新外觀。

![導覽至具有資料範本的類別，該類別]會(./media/navigation-overview/navigating-to-a-class.png "流覽至具有資料範本的類別。")

這項技術的優點是可以取得一致性，因為能夠重複使用資料範本，所以應用程式任何位置都可顯示一致的物件。

如需資料範本的詳細資訊，請參閱[資料範本化總覽](../data/data-templating-overview.md)。

<a name="Security"></a>

## <a name="security"></a>安全性

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 導覽支援可讓您透過網際網路流覽至 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，並允許應用程式裝載協力廠商內容。 為了保護應用程式和使用者免于有害的行為，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供了[安全性](../security-wpf.md)和[WPF 部分信任安全性](../wpf-partial-trust-security.md)中所討論的各種安全性功能。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [應用程式管理概觀](application-management-overview.md)
- [WPF 中的 Pack URI](pack-uris-in-wpf.md)
- [結構化巡覽概觀](structured-navigation-overview.md)
- [巡覽拓撲概觀](navigation-topologies-overview.md)
- [HOW-TO 主題](navigation-how-to-topics.md)
- [部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)
