---
title: 巡覽概觀
description: 瞭解在 Windows Presentation Foundation （WPF）中用於獨立應用程式和 XAML 瀏覽器應用程式的瀏覽器樣式導覽支援。
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
ms.openlocfilehash: 2aac1b3a38b6240bfba1b90983fd9cbd18b31b6f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621700"
---
# <a name="navigation-overview"></a>巡覽概觀

Windows Presentation Foundation （WPF）支援瀏覽器樣式的導覽，可用於兩種類型的應用程式：獨立應用程式和 XAML 瀏覽器應用程式（Xbap）。 為了要封裝內容以進行導覽，WPF 提供了 <xref:System.Windows.Controls.Page> 類別。 您可以藉由使用 <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> 或以程式設計方式，使用從一個流覽至另一個 <xref:System.Windows.Navigation.NavigationService> 。 WPF 會使用日誌來記住已從流覽的頁面，並流覽回它們。

<xref:System.Windows.Controls.Page>、 <xref:System.Windows.Documents.Hyperlink> 、 <xref:System.Windows.Navigation.NavigationService> 和日誌形成 WPF 所提供的導覽支援的核心。 本總覽會在涵蓋包含鬆散檔案、HTML 檔案和物件導覽的先進導覽支援之前，先深入探索這些功能 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。

> [!NOTE]
> 在本主題中，「瀏覽器」一詞只是指可以裝載 WPF 應用程式的瀏覽器，其中目前包含 Microsoft Internet Explorer 和 Firefox。 只有特定的瀏覽器支援特定的 WPF 功能時，才會參考瀏覽器版本。

## <a name="navigation-in-wpf-applications"></a>WPF 應用程式中的巡覽

本主題提供 WPF 中主要導覽功能的總覽。 這些功能都可供獨立應用程式和 Xbap 使用，雖然本主題會在 XBAP 的內容中呈現它們。

> [!NOTE]
> 本主題不會討論如何建立和部署 Xbap。 如需 Xbap 的詳細資訊，請參閱[WPF XAML 瀏覽器應用程式總覽](wpf-xaml-browser-applications-overview.md)。

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

在 WPF 中，您可以導覽至數種內容類型，其中包括 .NET Framework 物件、自訂物件、列舉值、使用者控制項、檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和 HTML 檔案。 不過，您會發現封裝內容最常見且方便的方式是使用 <xref:System.Windows.Controls.Page> 。 此外， <xref:System.Windows.Controls.Page> 也會執行導覽特有的功能，以增強其外觀並簡化開發。

使用 <xref:System.Windows.Controls.Page> ，您可以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 使用如下所示的標記，以宣告方式執行可導覽的內容頁面。

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

<xref:System.Windows.Controls.Page>在標記中實 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` 作為其根項目，而且需要 WPF XML 命名空間宣告。 專案 `Page` 包含您要流覽並顯示的內容。 您可以藉由設定屬性元素來新增內容 `Page.Content` ，如下列標記所示。

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` 只能包含一個子項目。在上例中，內容是單一字串 "Hello, Page!" 在實務上，您通常會使用版面配置控制項做為子專案（請參閱[版面](../advanced/layout.md)配置）以包含及撰寫內容。

專案的子專案 `Page` 會被視為和的內容 <xref:System.Windows.Controls.Page> ，因此，您不需要使用明確宣告 `Page.Content` 。 下列標記是前例的宣告式對等項目。

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

在此情況下， `Page.Content` 會自動使用專案的子項目進行設定 `Page` 。 如需詳細資訊，請參閱 [WPF 內容模型](../controls/wpf-content-model.md)。

僅限標記適用 <xref:System.Windows.Controls.Page> 于顯示內容。 不過， <xref:System.Windows.Controls.Page> 也可以顯示可讓使用者與頁面互動的控制項，而且它可以藉由處理事件和呼叫應用程式邏輯來回應使用者互動。 互動式 <xref:System.Windows.Controls.Page> 會使用標記和程式碼後置的組合來執行，如下列範例所示。

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

若要讓標記檔案和程式碼後置檔案一起工作，需要設定下列項目：

- 在標記中， `Page` 元素必須包含 `x:Class` 屬性。 建立應用程式時，標記檔案中的存在 `x:Class` 會導致 Microsoft build engine （MSBuild）建立 `partial` 衍生自的類別， <xref:System.Windows.Controls.Page> 並具有屬性所指定的名稱 `x:Class` 。 這需要新增架構的 XML 命名空間宣告 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] （ `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ）。 產生的 `partial` 類別 `InitializeComponent` 會執行，它會呼叫來註冊事件，並設定在標記中實作為的屬性。

- 在程式碼後置中，類別必須是 `partial` 具有與標記中的屬性所指定相同名稱的類別 `x:Class` ，而且必須衍生自 <xref:System.Windows.Controls.Page> 。 這可讓程式碼後置檔案與 `partial` 建立應用程式時為標記檔案產生的類別相關聯（請參閱[建立 WPF 應用程式](building-a-wpf-application-wpf.md)）。

- 在程式碼後置中， <xref:System.Windows.Controls.Page> 類別必須執行呼叫方法的函式 `InitializeComponent` 。 `InitializeComponent`會由標記檔案產生的 `partial` 類別來執行，以註冊事件並設定在標記中定義的屬性。

> [!NOTE]
> 當您使用 Visual Studio 將新的新增 <xref:System.Windows.Controls.Page> 至專案時， <xref:System.Windows.Controls.Page> 會使用標記和程式碼後置來實作為，並包含必要的設定來建立標記和程式碼後置檔案之間的關聯，如這裡所述。

一旦有 <xref:System.Windows.Controls.Page> ，您就可以流覽至該檔案。 若要指定 <xref:System.Windows.Controls.Page> 應用程式流覽的第一個，您必須設定 [啟動] <xref:System.Windows.Controls.Page> 。

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>設定起始頁

Xbap 需要在瀏覽器中裝載一定數量的應用程式基礎結構。 在 WPF 中， <xref:System.Windows.Application> 類別是應用程式定義的一部分，可建立必要的應用程式基礎結構（請參閱[應用程式管理總覽](application-management-overview.md)）。

應用程式定義通常會使用標記和程式碼後置來實作為，並將標記檔案設定為 MSBuild `ApplicationDefinition` 專案。 以下是 XBAP 的應用程式定義。

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

XBAP 可以使用其應用程式定義來指定 start <xref:System.Windows.Controls.Page> ，這是啟動 <xref:System.Windows.Controls.Page> XBAP 時自動載入的。 若要這麼做，您可以 <xref:System.Windows.Application.StartupUri%2A> 為所需的統一資源識別項（URI）設定屬性 <xref:System.Windows.Controls.Page> 。

> [!NOTE]
> 在大部分情況下， <xref:System.Windows.Controls.Page> 會編譯成或與應用程式一起部署。 在這些情況下，識別的 URI <xref:System.Windows.Controls.Page> 是一個 PACK uri，這是符合*套件*配置的 uri。 套件 Uri 會[在 WPF 的 Pack uri](pack-uris-in-wpf.md)中進一步討論。 您也可以巡覽至使用 http 配置的內容，後文會討論。

您可以 <xref:System.Windows.Application.StartupUri%2A> 在標記中以宣告方式設定，如下列範例所示。

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

在此範例中， `StartupUri` 屬性是以識別首頁的相對 PACK URI 來設定。 當 XBAP 啟動時，首頁. xaml 會自動流覽並顯示。 如下圖所示，它會顯示從 Web 服務器啟動的 XBAP。

![XBAP 網頁](./media/navigation-overview/xbap-launched-from-a-web-server.png "這會顯示從 Web 服務器啟動的 XBAP。")

> [!NOTE]
> 如需有關開發和部署 Xbap 的詳細資訊，請參閱[WPF XAML 瀏覽器應用程式總覽](wpf-xaml-browser-applications-overview.md)和[部署 wpf 應用程式](deploying-a-wpf-application-wpf.md)。

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>設定主機視窗的標題、寬度和高度

您在上圖中可能注意到的一件事，就是瀏覽器和索引標籤面板的標題都是 XBAP 的 URI。 除了長之外，標題既不吸引人，也不提供資訊。 基於這個理由， <xref:System.Windows.Controls.Page> 您可以藉由設定屬性來變更標題 <xref:System.Windows.Controls.Page.WindowTitle%2A> 。 此外，您可以分別設定和，藉以設定瀏覽器視窗的寬度和高度 <xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page.WindowHeight%2A> 。

<xref:System.Windows.Controls.Page.WindowTitle%2A>、 <xref:System.Windows.Controls.Page.WindowWidth%2A> 和 <xref:System.Windows.Controls.Page.WindowHeight%2A> 可以在標記中以宣告方式設定，如下列範例所示。

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

其結果如下圖所示。

![視窗標題、高度、寬度](./media/navigation-overview/window-title-width-height.png "這會顯示您可以設定的視窗標題、高度和寬度。")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>超連結巡覽

典型的 XBAP 包含數個頁面。 從一頁流覽至另一個頁面的最簡單方式是使用 <xref:System.Windows.Documents.Hyperlink> 。 您可以 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> 使用專案 `Hyperlink` （如下列標記所示），以宣告的方式將加入至。

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

`Hyperlink`元素需要下列專案：

- 要導覽之的 pack URI <xref:System.Windows.Controls.Page> ，如屬性所指定 `NavigateUri` 。

- 使用者可以按一下以起始導覽的內容，例如文字和影像（針對 `Hyperlink` 元素可以包含的內容，請參閱 <xref:System.Windows.Documents.Hyperlink> ）。

下圖顯示具有之的 XBAP <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> 。

![具有超連結的頁面](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "這會顯示具有超連結之頁面的 XBAP。")

如您所預期，按一下 <xref:System.Windows.Documents.Hyperlink> 會導致 XBAP 流覽至 <xref:System.Windows.Controls.Page> 屬性所識別的 `NavigateUri` 。 此外，XBAP 會 <xref:System.Windows.Controls.Page> 在 Internet Explorer 的 [最近使用的頁面] 清單中新增先前的專案。 如下圖所示。

![[上一頁] 和 [下一頁] 按鈕](./media/navigation-overview/back-and-forward-navigation.png "以 [上一頁] 和 [下一頁] 按鈕導覽。")

除了支援從一個導覽 <xref:System.Windows.Controls.Page> 至另一個， <xref:System.Windows.Documents.Hyperlink> 也支援片段導覽。

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>片段巡覽

*片段導覽*是導覽至目前或另一個中的內容片段 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> 。 在 WPF 中，內容片段是指已命名專案所包含的內容。 已命名的元素是已設定其屬性的元素 `Name` 。 下列標記顯示 `TextBlock` 包含內容片段的命名元素。

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

<xref:System.Windows.Documents.Hyperlink>若要讓流覽至內容片段， `NavigateUri` 屬性必須包含下列各項：

- <xref:System.Windows.Controls.Page>具有要導覽之內容片段的 URI。

- "#" 字元。

- 上包含內容片段之專案的名稱 <xref:System.Windows.Controls.Page> 。

片段 URI 具有下列格式。

*PageURI <項目名稱>* `#` **

以下顯示的範例 `Hyperlink` 是設定為流覽至內容片段。

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> 本節說明 WPF 中的預設片段導覽執行。 WPF 也可以讓您執行自己的片段導覽配置，而這種配置必須處理 <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> 事件。

> [!IMPORTANT]
> 只有在可以透過 HTTP 流覽頁面時，您才可以流覽到鬆散分頁中的片段（僅限標記的檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，以 `Page` 作為根項目）。
>
> 不過，鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 分頁可以流覽至它自己的片段。

<a name="NavigationService"></a>

### <a name="navigation-service"></a>巡覽服務

雖然 <xref:System.Windows.Documents.Hyperlink> 可讓使用者起始特定的導覽，但 <xref:System.Windows.Controls.Page> 尋找和下載頁面的工作是由 <xref:System.Windows.Navigation.NavigationService> 類別執行。 基本上， <xref:System.Windows.Navigation.NavigationService> 可讓您代表用戶端程式代碼（例如）來處理導覽要求 <xref:System.Windows.Documents.Hyperlink> 。 此外， <xref:System.Windows.Navigation.NavigationService> 也會執行更高層級的追蹤和影響導覽要求支援。

當您 <xref:System.Windows.Documents.Hyperlink> 按一下時，WPF 會呼叫 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 來尋找並下載 <xref:System.Windows.Controls.Page> 位於指定 pack URI 的。 已下載的 <xref:System.Windows.Controls.Page> 會轉換成物件的樹狀結構，其根物件是已下載的實例 <xref:System.Windows.Controls.Page> 。 根物件的參考 <xref:System.Windows.Controls.Page> 會儲存在 <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> 屬性中。 所流覽之內容的 pack URI 會儲存在 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> 屬性中，而則會 <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> 儲存流覽至的最後一頁的 pack uri。

> [!NOTE]
> WPF 應用程式可能會有一個以上的目前作用 <xref:System.Windows.Navigation.NavigationService> 中。 如需詳細資訊，請參閱本主題稍後的[導覽主機](#Navigation_Hosts)。

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>以程式設計的巡覽及巡覽服務

您不需要知道是否使用來以宣告 <xref:System.Windows.Navigation.NavigationService> 方式在標記中執行導覽 <xref:System.Windows.Documents.Hyperlink> ，因為會 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService> 代表您使用。 這表示，只要的直接或間接父系 <xref:System.Windows.Documents.Hyperlink> 是導覽主控制項（請參閱 [[導覽主機](#Navigation_Hosts)]）， <xref:System.Windows.Documents.Hyperlink> 就能夠尋找和使用導覽主機的導覽服務來處理導覽要求。

不過，在某些情況下，您需要 <xref:System.Windows.Navigation.NavigationService> 直接使用，包括下列各項：

- 當您需要 <xref:System.Windows.Controls.Page> 使用非無參數的函式來具現化時。

- 當您需要在流覽至之前設定上的屬性時 <xref:System.Windows.Controls.Page> 。

- 當 <xref:System.Windows.Controls.Page> 需要流覽至的時，只能在執行時間決定。

在這些情況下，您需要撰寫程式碼，藉由呼叫物件的方法，以程式設計方式起始導覽 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> <xref:System.Windows.Navigation.NavigationService> 。 這需要取得的參考 <xref:System.Windows.Navigation.NavigationService> 。

#### <a name="getting-a-reference-to-the-navigationservice"></a>取得 NavigationService 的參考

針對 [[導覽主機](#Navigation_Hosts)] 區段中所涵蓋的原因，WPF 應用程式可以有一個以上的 <xref:System.Windows.Navigation.NavigationService> 。 這表示您的程式碼需要一種方式來尋找 <xref:System.Windows.Navigation.NavigationService> ，這通常是 <xref:System.Windows.Navigation.NavigationService> 流覽至目前的 <xref:System.Windows.Controls.Page> 。 您可以藉 <xref:System.Windows.Navigation.NavigationService> 由呼叫方法來取得的參考 `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> 。 若要取得導覽 <xref:System.Windows.Navigation.NavigationService> 至特定的 <xref:System.Windows.Controls.Page> ，請將的參考傳遞至 <xref:System.Windows.Controls.Page> 做為方法的引數 <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> 。 下列程式碼顯示如何取得目前的 <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> 。

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

若要尋找的快捷方式 <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> ，請執行 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page.NavigationService%2A> 屬性。 下列範例會顯示這一點。

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService> 當引發事件時，只能取得其的參考 <xref:System.Windows.Controls.Page> <xref:System.Windows.FrameworkElement.Loaded> 。

#### <a name="programmatic-navigation-to-a-page-object"></a>以程式設計方式巡覽至頁面物件

下列範例示範如何使用，以程式設計 <xref:System.Windows.Navigation.NavigationService> 方式流覽至 <xref:System.Windows.Controls.Page> 。 必須以程式設計方式導覽，因為所流覽的只能 <xref:System.Windows.Controls.Page> 使用單一、非參數的函式來具現化。 <xref:System.Windows.Controls.Page>具有非無參數的函式的會顯示在下列標記和程式碼中。

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

<xref:System.Windows.Controls.Page>使用非無參數的函式來流覽至的 <xref:System.Windows.Controls.Page> 會顯示在下列標記和程式碼中。

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

當按一下 [on] 時 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> ，就會藉由具現化來起始導覽， <xref:System.Windows.Controls.Page> 以使用非無參數的函式並呼叫方法來流覽至 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 。 <xref:System.Windows.Navigation.NavigationService.Navigate%2A>接受將導覽至之物件的參考 <xref:System.Windows.Navigation.NavigationService> ，而不是 PACK URI。

#### <a name="programmatic-navigation-with-a-pack-uri"></a>以程式設計的巡覽及 Pack URI

如果您需要以程式設計方式來建立 pack URI （例如，您只能在執行時間判斷 pack URI），可以使用 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 方法。 下列範例會顯示這一點。

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>重新整理目前的頁面

<xref:System.Windows.Controls.Page>如果與儲存在屬性中的 PACK uri 具有相同的 pack uri，則不會下載。 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> 若要強制 WPF 再次下載目前的頁面，您可以呼叫 <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> 方法，如下列範例所示。

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>巡覽存留期

如您所見，有多種方式可以初始化巡覽。 當導覽已起始，而且導覽正在進行時，您可以使用下列所實的事件來追蹤和影響導覽 <xref:System.Windows.Navigation.NavigationService> ：

- <xref:System.Windows.Navigation.NavigationService.Navigating>. 要求新的巡覽時發生。 可用於取消巡覽。

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. 在下載期間定期發生以提供導覽進度資訊。

- <xref:System.Windows.Navigation.NavigationService.Navigated>. 找到並下載頁面時發生。

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. 當導覽已停止（藉由呼叫 <xref:System.Windows.Navigation.NavigationService.StopLoading%2A> ），或目前導覽正在進行中要求新的導覽時發生。

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. 在廵覽至要求的內容引發錯誤時發生。

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. 當載入並剖析巡覽到的內容，且開始轉譯時發生。

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. 當內容片段巡覽開始時發生，狀況為︰

  - 立即發生，如果所需片段位在目前的內容中。

  - 載入來源內容之後，如果所需片段位在不同的內容中。

下圖顯示巡覽事件的引發順序。

![頁面巡覽流程圖](./media/navigation-overview/order-of-navigation-events.png "頁面導覽事件流程圖表")

一般而言，不會 <xref:System.Windows.Controls.Page> 關心這些事件。 應用程式很有可能會擔心它們，因此，這些事件也會由 <xref:System.Windows.Application> 類別引發：

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

每次 <xref:System.Windows.Navigation.NavigationService> 引發事件時， <xref:System.Windows.Application> 類別都會引發對應的事件。 <xref:System.Windows.Controls.Frame>和會 <xref:System.Windows.Navigation.NavigationWindow> 提供相同的事件，以偵測其各自範圍內的導覽。

在某些情況下， <xref:System.Windows.Controls.Page> 可能會對這些事件感興趣。 例如， <xref:System.Windows.Controls.Page> 可能會處理事件， <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> 以判斷是否要取消本身的導覽。 下列範例會顯示這一點。

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

如果您從註冊具有導覽事件的處理常式 <xref:System.Windows.Controls.Page> ，如上述範例所示，您也必須取消註冊事件處理常式。 如果您沒有這麼做，可能會有關于 WPF 導覽如何使用日誌來記住導覽的副作用 <xref:System.Windows.Controls.Page> 。

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>以日誌記憶巡覽

WPF 會使用兩個堆疊來記住您所流覽的頁面：後端堆疊和向前堆疊。 當您從目前的流覽 <xref:System.Windows.Controls.Page> 至新的 <xref:System.Windows.Controls.Page> 或轉送到現有的時 <xref:System.Windows.Controls.Page> ，會將目前的 <xref:System.Windows.Controls.Page> 加入至*後端堆疊*。 當您從目前的 <xref:System.Windows.Controls.Page> 回到上一個時 <xref:System.Windows.Controls.Page> ，會將目前的 <xref:System.Windows.Controls.Page> 加入至*正向堆疊*中。 上一頁堆疊、下一頁堆疊和管理它們的功能，統稱為日誌。 後端堆疊和轉寄堆疊中的每個專案都是類別的實例 <xref:System.Windows.Navigation.JournalEntry> ，而則稱為*日誌項目*。

#### <a name="navigating-the-journal-from-internet-explorer"></a>從 Internet Explorer 巡覽日誌

就概念而言，日誌的運作方式與 Internet Explorer 中的 [**上一頁**] 和 [**下一頁**] 按鈕相同。 如下圖所示。

![[上一頁] 和 [下一頁] 按鈕](./media/navigation-overview/back-and-forward-navigation.png "以 [上一頁] 和 [下一頁] 按鈕導覽。")

若為 Internet Explorer 所裝載的 Xbap，WPF 會將日誌整合到 Internet Explorer 的導覽中 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 這可讓使用者使用 Internet Explorer 中的 [**上一頁**]、[**下一頁**] 和 [**最近使用的頁面**] 按鈕，流覽 XBAP 中的頁面。

> [!IMPORTANT]
> 在 Internet Explorer 中，當使用者離開並回到 XBAP 時，只有未保持運作之頁面的記錄項目會保留在日誌中。 如需讓頁面保持運作的討論，請參閱本主題稍後的[頁面存留期和日誌](#PageLifetime)。

根據預設， <xref:System.Windows.Controls.Page> Internet Explorer [**最近使用的頁面**] 清單中出現的每個文字，都是的 URI <xref:System.Windows.Controls.Page> 。 在許多情況下，這對使用者都不是特別有意義。 幸運的是，您可以變更使用下列選項之一的文字︰

1. 附加的 `JournalEntry.Name` 屬性值。

2. `Page.Title`屬性值。

3. `Page.WindowTitle`屬性值和目前的 URI <xref:System.Windows.Controls.Page> 。

4. 目前的 URI <xref:System.Windows.Controls.Page> 。 (預設值)

選項列示順序符合尋找文字的優先順序。 例如，如果 `JournalEntry.Name` 設定，則會忽略其他值。

下列範例 `Page.Title` 會使用屬性來變更日誌項目所顯示的文字。

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>巡覽使用 WPF 的日誌

雖然使用者可以使用 Internet Explorer 中的 [**上一頁**]、[**下一頁**] 和 [**最近] 頁面**來流覽日誌，但是您也可以使用 WPF 所提供的宣告式和程式設計機制來流覽日誌。 這麼做的其中一個原因是在您的頁面中提供自訂的導覽 Ui。

您可以使用所公開的導覽命令，以宣告方式加入日誌流覽支援 <xref:System.Windows.Input.NavigationCommands> 。 下列範例示範如何使用 `BrowseBack` 導覽命令。

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

您可以使用類別的下列其中一個成員，以程式設計方式流覽日誌 <xref:System.Windows.Navigation.NavigationService> ：

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

您也可以透過程式設計方式動作記錄，如本主題稍後的[保留內容狀態與導覽歷程記錄](#RetainingContentStateWithNavigationHistory)中所述。

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>網頁存留期和日誌

假設有多個頁面包含豐富內容的 XBAP，包括圖形、動畫和媒體。 這類頁面的磁碟使用量可能相當大，尤其是使用視訊和音訊媒體的時候。 假設筆記本「記憶」已流覽過的頁面，這樣的 XBAP 可能很快就會耗用大量且明顯的記憶體數量。

基於這個理由，日誌的預設行為是將 <xref:System.Windows.Controls.Page> 中繼資料儲存在每個日誌項目中，而不是對 <xref:System.Windows.Controls.Page> 物件的參考。 當流覽記錄項目時，其 <xref:System.Windows.Controls.Page> 中繼資料會用來建立指定的的新實例 <xref:System.Windows.Controls.Page> 。 因此，流覽的每個都 <xref:System.Windows.Controls.Page> 具有下圖所說明的存留期。

![網頁存留期](./media/navigation-overview/navigated-page-lifetime.png "這會顯示流覽頁面時的存留期。")

雖然使用預設日誌行為可以節省記憶體耗用量，但每頁轉譯的效能可能會降低;reinstantiating <xref:System.Windows.Controls.Page> 可能會耗費大量時間，特別是當它有許多內容時。 如果您需要將實例保留 <xref:System.Windows.Controls.Page> 在日誌中，您可以使用兩種技術來進行繪製。 首先，您可以藉由呼叫方法，以程式設計方式流覽至 <xref:System.Windows.Controls.Page> 物件 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 。

第二，您可以 <xref:System.Windows.Controls.Page> 將 <xref:System.Windows.Controls.Page.KeepAlive%2A> 屬性設定為 `true` （預設值為），藉以指定 WPF 在日誌中保留的實例 `false` 。 如下列範例所示，您可以 <xref:System.Windows.Controls.Page.KeepAlive%2A> 在標記中以宣告方式設定。

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

保持運作狀態的存留期與 <xref:System.Windows.Controls.Page> 不是一樣。 第一次保持運作的 <xref:System.Windows.Controls.Page> 狀態會被流覽至，它會具現化，就像 <xref:System.Windows.Controls.Page> 不會保持運作的一樣。 不過，因為的實例 <xref:System.Windows.Controls.Page> 會保留在日誌中，所以只要它保留在日誌中，就永遠不會再次具現化。 因此，如果 <xref:System.Windows.Controls.Page> 有必須在每次導覽時呼叫的初始化邏輯 <xref:System.Windows.Controls.Page> ，您就應該將它從函式移至事件的處理常式 <xref:System.Windows.FrameworkElement.Loaded> 。 如下圖所示， <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.FrameworkElement.Unloaded> 每次流覽到和時，仍會引發和事件 <xref:System.Windows.Controls.Page> 。

![引發 Loaded 和 Unloaded 事件時](./media/navigation-overview/loaded-and-unloaded-events.png "當頁面流覽至和時，會引發載入和卸載的事件。")

當未 <xref:System.Windows.Controls.Page> 保持運作時，您不應該執行下列其中一項動作：

- 儲存其參考或任何部分。

- 使用它未實作的事件來登錄事件處理常式。

執行其中一項作業會建立參考，強制將 <xref:System.Windows.Controls.Page> 其保留在記憶體中，即使已從日誌中移除亦然。

一般來說，您應該偏好不要保持運作的預設 <xref:System.Windows.Controls.Page> 行為 <xref:System.Windows.Controls.Page> 。 不過，這有下一節要討論的隱含狀態。

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>以巡覽記錄保留內容狀態

如果 <xref:System.Windows.Controls.Page> 不是保持運作狀態，而且它具有可從使用者收集資料的控制項，當使用者流覽離開並回到時，資料會發生什麼事 <xref:System.Windows.Controls.Page> ？ 從使用者體驗的觀點而言，使用者應該會希望看到他們先前所輸入的資料。 可惜的是，由於 <xref:System.Windows.Controls.Page> 會使用每個導覽來建立的新實例，因此會 reinstantiated 收集資料的控制項並遺失資料。

幸運的是，日誌提供了跨導覽來記憶資料的支援 <xref:System.Windows.Controls.Page> ，包括控制資料。 具體而言，每個專案的日誌項目都會 <xref:System.Windows.Controls.Page> 作為相關聯狀態的暫存容器 <xref:System.Windows.Controls.Page> 。 下列步驟概述當從流覽時，如何使用這項支援 <xref:System.Windows.Controls.Page> ：

1. 目前的專案 <xref:System.Windows.Controls.Page> 會新增至日誌。

2. 的狀態 <xref:System.Windows.Controls.Page> 會與該頁面的日誌項目一起儲存，這會新增至後端堆疊。

3. 新的 <xref:System.Windows.Controls.Page> 會被流覽至。

當頁面 <xref:System.Windows.Controls.Page> 流覽回時，使用日誌，會進行下列步驟：

1. <xref:System.Windows.Controls.Page>已具現化（後端堆疊上的最上層記錄項目）。

2. <xref:System.Windows.Controls.Page>會使用與的日誌項目一起儲存的狀態重新整理 <xref:System.Windows.Controls.Page> 。

3. <xref:System.Windows.Controls.Page>會流覽回。

當下列控制項用於時，WPF 會自動使用這項支援 <xref:System.Windows.Controls.Page> ：

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

如果 <xref:System.Windows.Controls.Page> 使用這些控制項，則會在所有導覽中記住輸入的資料， <xref:System.Windows.Controls.Page> 如下圖中的我的**最愛色彩**所示 <xref:System.Windows.Controls.ListBox> 。

![具有可記憶狀態之控制項的頁面](./media/navigation-overview/data-remembered-across-page-navigations.png "在頁面導覽中，會記住輸入的資料。")

當 <xref:System.Windows.Controls.Page> 具有上述清單以外的控制項，或當狀態儲存在自訂物件中時，您必須撰寫程式碼，讓日誌記住跨導覽的狀態 <xref:System.Windows.Controls.Page> 。

如果您需要記住跨導覽的小部分狀態 <xref:System.Windows.Controls.Page> ，您可以使用 <xref:System.Windows.DependencyProperty> 以中繼資料旗標設定的相依性屬性（請參閱） <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> 。

如果您 <xref:System.Windows.Controls.Page> 需要記住跨導覽的狀態包含多個資料片段，您可能會發現在單一類別中封裝您的狀態並執行介面的程式碼較少 <xref:System.Windows.Navigation.IProvideCustomContentState> 。

如果您需要流覽單一的各種狀態 <xref:System.Windows.Controls.Page> ，而不想從 <xref:System.Windows.Controls.Page> 本身導覽，則可以使用 <xref:System.Windows.Navigation.IProvideCustomContentState> 和 <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType> 。

<a name="Cookies"></a>

### <a name="cookies"></a>Cookie

WPF 應用程式可以儲存資料的另一種方式是使用和方法來建立、更新和刪除 cookie <xref:System.Windows.Application.SetCookie%2A> <xref:System.Windows.Application.GetCookie%2A> 。 您可以在 WPF 中建立的 cookie 與其他類型的 Web 應用程式所使用的 cookie 相同。cookie 是應用程式在應用程式會話期間或之間儲存的任意資料片段。 Cookie 資料通常會採用下列格式的名稱/值組形式。

*名稱* `=`*值*

將資料傳遞至時，如果要 <xref:System.Windows.Application.SetCookie%2A> <xref:System.Uri> 設定 cookie 的位置，就會在記憶體中建立 cookie，而且僅適用于目前應用程式會話的持續時間。 這種類型的 cookie 稱為*會話 cookie*。

若要在應用程式工作階段之間儲存 Cookie，到期日必須使用下列格式新增至 Cookie。

「名稱」*「值」* `=` ** `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

具有到期日的 cookie 會儲存在目前 Windows 安裝的 [Internet Files] 資料夾中，直到 cookie 到期為止。 這類 cookie 稱為*持續性 cookie* ，因為它會在應用程式會話之間持續保存。

您可以藉由呼叫方法來取得會話和持續性的 cookie <xref:System.Windows.Application.GetCookie%2A> ，傳遞 <xref:System.Uri> 使用方法設定 cookie 的位置 <xref:System.Windows.Application.SetCookie%2A> 。

以下是 WPF 支援 cookie 的一些方式：

- WPF 獨立應用程式和 Xbap 可以建立和管理 cookie。

- 您可以從瀏覽器存取 XBAP 所建立的 cookie。

- 來自相同網域的 Xbap 可以建立和共用 cookie。

- 來自相同網域的 Xbap 和 HTML 頁面可以建立和共用 cookie。

- 當 Xbap 和鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 分頁提出 Web 要求時，會分派 cookie。

- 在 IFRAME 中裝載的頂層 Xbap 和 Xbap 都可以存取 cookie。

- WPF 中的 Cookie 支援對所有支援的瀏覽器都是相同的。

- 在 Internet Explorer 中，適用于 cookie 的 P3P 原則會由 WPF 接受，特別是關於第一方和協力廠商的 Xbap。

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>結構化巡覽

如果您需要將資料從一個傳送 <xref:System.Windows.Controls.Page> 到另一個，您可以將資料當做引數傳遞至的非無參數的函式 <xref:System.Windows.Controls.Page> 。 請注意，如果您使用這項技術，就必須維持運作的 <xref:System.Windows.Controls.Page> 狀態。如果不是，則當您下次流覽至時， <xref:System.Windows.Controls.Page> WPF 會 <xref:System.Windows.Controls.Page> 使用無參數的函式來 reinstantiates。

或者，您 <xref:System.Windows.Controls.Page> 可以使用需要傳遞的資料來執行設定的屬性。 不過，當 <xref:System.Windows.Controls.Page> 需要將資料傳回給導覽到它的時，會變得 <xref:System.Windows.Controls.Page> 很棘手。 問題在於，導覽原本並不支援機制，以確保在 <xref:System.Windows.Controls.Page> 流覽之後，將會傳回。 基本上，巡覽不支援呼叫/傳回語意。 為了解決這個問題，WPF 提供了 <xref:System.Windows.Navigation.PageFunction%601> 類別，您可以用它來確保以 <xref:System.Windows.Controls.Page> 可預測且結構化的方式傳回。 如需詳細資訊，請參閱[結構化導覽總覽](structured-navigation-overview.md)。

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow 類別

至此，您已了解最可能用來建置有可巡覽內容之應用程式的巡覽服務範圍。 這些服務是在 Xbap 的內容中討論，雖然它們不限於 Xbap。 新式作業系統和 Windows 應用程式利用新式使用者的瀏覽器體驗，將瀏覽器樣式的導覽併入獨立應用程式中。 常見範例包括：

- **文字同義字**︰巡覽文字選擇。

- **檔案總管**︰巡覽檔案和資料夾。

- **精靈**︰將複雜的工作細分成可往來巡覽的多個頁面。 其中一個範例是處理新增和移除 Windows 功能的 Windows 元件 Wizard。

若要將瀏覽器樣式的導覽併入您的獨立應用程式，您可以使用 <xref:System.Windows.Navigation.NavigationWindow> 類別。 <xref:System.Windows.Navigation.NavigationWindow>衍生自 <xref:System.Windows.Window> ，並使用 xbap 所提供的相同導覽支援來加以擴充。 您可以使用 <xref:System.Windows.Navigation.NavigationWindow> 做為獨立應用程式的主視窗，或當做對話方塊之類的次要視窗。

若要執行 <xref:System.Windows.Navigation.NavigationWindow> ，如同 WPF 中的大部分最上層類別（ <xref:System.Windows.Window> 、 <xref:System.Windows.Controls.Page> 等等），您可以使用標記和程式碼後置的組合。 下列範例會顯示這一點。

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

此 <xref:System.Windows.Navigation.NavigationWindow> 程式碼會建立，它會在開啟時自動流覽至 <xref:System.Windows.Controls.Page> （首頁. xaml） <xref:System.Windows.Navigation.NavigationWindow> 。 如果 <xref:System.Windows.Navigation.NavigationWindow> 是主應用程式視窗，您可以使用 `StartupUri` 屬性來啟動它。 下列標記顯示此做法。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

下圖顯示 <xref:System.Windows.Navigation.NavigationWindow> 作為獨立應用程式的主要視窗。

![主視窗](./media/navigation-overview/navigation-window-as-main-window.png "做為主視窗的導覽視窗")

從圖中，您可以看到 <xref:System.Windows.Navigation.NavigationWindow> 有一個標題，即使它不是在上述範例的實程式碼中設定也一樣 <xref:System.Windows.Navigation.NavigationWindow> 。 而是使用屬性來設定標題 <xref:System.Windows.Controls.Page.WindowTitle%2A> ，如下列程式碼所示。

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

設定 <xref:System.Windows.Controls.Page.WindowWidth%2A> 和 <xref:System.Windows.Controls.Page.WindowHeight%2A> 屬性也會影響 <xref:System.Windows.Navigation.NavigationWindow> 。

<xref:System.Windows.Navigation.NavigationWindow>當您需要自訂其行為或其外觀時，通常會執行自己的工作。 如果兩樣都不做，您可以使用捷徑。 如果您在獨立應用程式中將的 pack URI 指定 <xref:System.Windows.Controls.Page> 為 <xref:System.Windows.Application.StartupUri%2A> ，則 <xref:System.Windows.Application> 會自動建立 <xref:System.Windows.Navigation.NavigationWindow> 來裝載 <xref:System.Windows.Controls.Page> 。 下列標記顯示如何啟用此功能。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

如果您想要讓次要應用程式視窗（例如對話方塊 <xref:System.Windows.Navigation.NavigationWindow> ）成為，您可以使用下列範例中的程式碼來開啟它。

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

其結果如下圖所示。

![對話方塊](./media/navigation-overview/navigation-window-as-dialog-box.png "作為對話方塊的導覽視窗")

如您所見，會 <xref:System.Windows.Navigation.NavigationWindow> 顯示 Internet Explorer 樣式的 [**上一頁**] 和 [**下一頁**] 按鈕，讓使用者可以流覽日誌。 這些按鈕提供相同的使用者體驗，如下圖所示。

![NavigationWindow 中的向後和向前按鈕](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "導覽視窗中的 [上一頁] 和 [下一頁] 按鈕")

如果您的頁面提供自己的日誌流覽支援和 UI，您可以將屬性的值設定為，以隱藏顯示的 [**上一頁**] 和 [**下一頁**] 按鈕 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> `false` 。

或者，您可以使用 WPF 中的自訂支援來取代 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.NavigationWindow> 本身的。

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Frame 類別

瀏覽器和 <xref:System.Windows.Navigation.NavigationWindow> 都是裝載可流覽內容的視窗。 在某些情況下，應用程式會有不需要由整個視窗裝載的內容。 這類內容反可以裝載於其他內容中。 您可以使用類別，將可流覽的內容插入至其他內容 <xref:System.Windows.Controls.Frame> 。 <xref:System.Windows.Controls.Frame>提供與和 Xbap 相同的支援 <xref:System.Windows.Navigation.NavigationWindow> 。

下列範例顯示如何使用專案，以宣告方式將加入 <xref:System.Windows.Controls.Frame> 至 <xref:System.Windows.Controls.Page> `Frame` 。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

此標記 `Source` `Frame` <xref:System.Windows.Controls.Page> 會針對應該一開始流覽至的，使用的 pack URI 來設定專案的屬性 <xref:System.Windows.Controls.Frame> 。 下圖顯示的 XBAP 具有，其已 <xref:System.Windows.Controls.Page> 在 <xref:System.Windows.Controls.Frame> 數個頁面之間流覽。

![已在多個頁面之間巡覽過的框架](./media/navigation-overview/frame-navigation-between-multiple-pages.png "這會顯示多個頁面之間的框架導覽。")

您不只需要在的 <xref:System.Windows.Controls.Frame> 內容內使用 <xref:System.Windows.Controls.Page> 。 在的內容中裝載，也是很常見的情況 <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window> 。

根據預設， <xref:System.Windows.Controls.Frame> 只有在沒有另一個日誌時，才會使用自己的日誌。 如果是裝載于 <xref:System.Windows.Controls.Frame> 或 xbap 內部之內容的一部分，則會 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame> 使用屬於 <xref:System.Windows.Navigation.NavigationWindow> 或 xbap 的日誌。 不過，有時候 <xref:System.Windows.Controls.Frame> 可能需要負責自己的日誌。 這麼做的其中一個原因是允許在所裝載的頁面內進行日誌導覽 <xref:System.Windows.Controls.Frame> 。 如下圖所示。

![框架和頁面圖表](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "這會在框架所主控的頁面中顯示日誌導覽。")

在此情況下，您可以將的 <xref:System.Windows.Controls.Frame> 屬性設為，將設定為使用自己的日誌 <xref:System.Windows.Controls.Frame.JournalOwnership%2A> <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal> 。 下列標記顯示此做法。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

下圖說明在使用自己的日誌的中流覽的效果 <xref:System.Windows.Controls.Frame> 。

![使用本身之日誌的框架](./media/navigation-overview/frame-uses-its-own-journal.png "這會顯示在使用自己的日誌的框架內流覽的效果。")

請注意，中的導覽會顯示日誌項目 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame> ，而不是 Internet Explorer。

> [!NOTE]
> 如果 <xref:System.Windows.Controls.Frame> 是裝載于中之內容的一部分，則 <xref:System.Windows.Window> 會 <xref:System.Windows.Controls.Frame> 使用自己的日誌，因此會顯示它自己的導覽 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。

如果您的使用者體驗需要 <xref:System.Windows.Controls.Frame> 提供自己的日誌，而不顯示導覽 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，您可以 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 將設定為來隱藏導覽 <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> <xref:System.Windows.Visibility.Hidden> 。 下列標記顯示此做法。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>巡覽裝載

<xref:System.Windows.Controls.Frame>和 <xref:System.Windows.Navigation.NavigationWindow> 是稱為「導覽主機」的類別。 *導覽主機*是可流覽並顯示內容的類別。 為了完成這項工作，每個導覽主機都會使用自己的 <xref:System.Windows.Navigation.NavigationService> 和日誌。 巡覽裝載的基本建構如下圖所示。

![導覽器圖表](./media/navigation-overview/navigation-host-construction.png "導覽主控制項的基本結構")

基本上，這可讓 <xref:System.Windows.Navigation.NavigationWindow> 和 <xref:System.Windows.Controls.Frame> 提供在瀏覽器中裝載時，XBAP 提供的相同導覽支援。

除了使用 <xref:System.Windows.Navigation.NavigationService> 和日誌以外，流覽主控制項還會執行相同的成員 <xref:System.Windows.Navigation.NavigationService> 。 如下圖所示。

![在框架和 NavigationWindow 中的日誌](./media/navigation-overview/navigation-window-and-frame.png "導覽視窗和框架")

這可讓您針對它們直接設計巡覽支援程式。 如果您需要為裝載于的，提供自訂導覽，可以考慮這 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame> 一點 <xref:System.Windows.Window> 。 此外，這兩種類型都會執行其他的導覽相關成員，包括 `BackStack` （ <xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType> ， <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType> ）和 `ForwardStack` （ <xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType> ， <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType> ），這可讓您分別列舉後端堆疊和轉送堆疊中的記錄項目。

如前所述，應用程式中可有多個日誌。 下圖提供這種情況的範例。

![一個應用程式中包含多個日誌](./media/navigation-overview/multiple-journals-in-one-application.png "這是應用程式中一個以上的日誌範例。")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>巡覽至 XAML 頁面以外的內容

在本主題中， <xref:System.Windows.Controls.Page> 和 Pack xbap 已用來示範 WPF 的各種導覽功能。 不過， <xref:System.Windows.Controls.Page> 編譯成應用程式的不是可流覽的唯一內容類型，而套件 xbap 則不是識別內容的唯一方法。

如本節所示，您也可以流覽至鬆散的檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 、HTML 檔案和物件。

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>巡覽至鬆散的 XAML 檔案

鬆散檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是具有下列特性的檔案：

- 僅包含 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] （也就是沒有程式碼）。

- 具有適當的命名空間宣告。

- 具有 .xaml 副檔名。

例如，請考慮將下列內容儲存為鬆散檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，Person. xaml。

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

當您按兩下檔案時，瀏覽器會開啟、巡覽至並顯示內容。 如下圖所示。

![顯示 Person.XAML 檔案中的內容](./media/navigation-overview/contents-of-person-xaml-file.png "顯示 Person. XAML 檔案的內容。")

您可以顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 下列的鬆散檔案：

- 在本機電腦、內部網路或網際網路上的網站。

- 通用命名慣例（UNC）檔案共用。

- 本機磁碟。

鬆散檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 可以新增至瀏覽器的 [我的最愛]，或作為瀏覽器的首頁。

> [!NOTE]
> 如需發佈和啟動鬆散頁面的詳細資訊 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，請參閱[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)。

鬆散的一項限制 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是，您只能裝載可安全地在部分信任中執行的內容。 例如， `Window` 不能是鬆散檔案的根項目 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>使用框架巡覽至 HTML 檔案

如您所預期，您也可以流覽至 HTML。 您只需要提供使用 HTTP 配置的 URI。 例如，以下 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 顯示 <xref:System.Windows.Controls.Frame> 流覽至 HTML 網頁的。

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

流覽至 HTML 需要特殊許可權。 例如，您無法從在網際網路區域部分信任安全性沙箱中執行的 XBAP 進行流覽。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>使用 WebBrowser 控制項巡覽至 HTML 檔案

<xref:System.Windows.Controls.WebBrowser>控制項支援 HTML 檔案裝載、導覽和腳本/managed 程式碼互通性。 如需有關控制項的詳細資訊 <xref:System.Windows.Controls.WebBrowser> ，請參閱 <xref:System.Windows.Controls.WebBrowser> 。

如同 <xref:System.Windows.Controls.Frame> ，使用流覽至 HTML <xref:System.Windows.Controls.WebBrowser> 需要特殊許可權。 例如，您可以從部分信任的應用程式，只流覽至位於來源網站的 HTML。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>巡覽至自訂物件

如果您有儲存為自訂物件的資料，顯示該資料的一種方式是建立， <xref:System.Windows.Controls.Page> 並將內容系結至這些物件（請參閱[資料](../../../desktop-wpf/data/data-binding-overview.md)系結總覽）。 如果您不需要建立整個頁面此額外負荷，而只要顯示物件，則您可以改為直接巡覽至它們。

請考慮在 `Person` 下列程式碼中執行的類別。

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

若要流覽至它，您可以呼叫 <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> 方法，如下列程式碼所示。

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

其結果如下圖所示。

![巡覽至類別的頁面](./media/navigation-overview/page-navigates-to-an-object.png "這是導覽至物件的頁面範例。")

在此圖中，您看不到任何有用的內容。 事實上，顯示的值是 Person 物件之方法的傳回值 `ToString` ; 根據預設， **Person**這是 WPF 可用來代表物件的唯一值。 您可以覆寫 `ToString` 方法以傳回更有意義的資訊，但它仍然只是字串值。 您可以使用的一種技術，利用 WPF 的呈現功能，就是使用資料範本。 您可以執行 WPF 可以與特定類型的物件產生關聯的資料範本。 下列程式碼顯示物件的資料範本 `Person` 。

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

在這裡，資料範本會 `Person` 使用 `x:Type` 屬性中的標記延伸，與類型相關聯 `DataType` 。 然後，資料範本會將 `TextBlock` 元素（請參閱）系結 <xref:System.Windows.Controls.TextBlock> 至 `Person` 類別的屬性。 下圖顯示物件的更新外觀 `Person` 。

![巡覽至具有資料範本的類別](./media/navigation-overview/navigating-to-a-class.png "流覽至具有資料範本的類別。")

這項技術的優點是可以取得一致性，因為能夠重複使用資料範本，所以應用程式任何位置都可顯示一致的物件。

如需資料範本的詳細資訊，請參閱[資料範本化總覽](../data/data-templating-overview.md)。

<a name="Security"></a>

## <a name="security"></a>安全性

WPF 導覽支援可讓您透過網際網路流覽 Xbap，並允許應用程式裝載協力廠商內容。 為了保護應用程式和使用者免于有害的行為，WPF 提供了[安全性](../security-wpf.md)和[WPF 部分信任安全性](../wpf-partial-trust-security.md)中所討論的各種安全性功能。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [應用程式管理概觀](application-management-overview.md)
- [WPF 中的 Pack URI](pack-uris-in-wpf.md)
- [結構化巡覽概觀](structured-navigation-overview.md)
- [巡覽拓撲概觀](navigation-topologies-overview.md)
- [操作說明主題](navigation-how-to-topics.md)
- [部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)
