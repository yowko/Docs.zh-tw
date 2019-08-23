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
ms.openlocfilehash: 574449f95ee9632d37f277d61806802457494df0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964594"
---
# <a name="navigation-overview"></a>巡覽概觀

Windows Presentation Foundation (WPF) 支援瀏覽器樣式的導覽, 可用於兩種類型的應用程式: 獨立應用[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]程式和。 若要封裝內容以供[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]導覽, <xref:System.Windows.Controls.Page>請提供類別。 您可以藉由使用<xref:System.Windows.Controls.Page>或<xref:System.Windows.Navigation.NavigationService>以程式設計方式, 使用<xref:System.Windows.Documents.Hyperlink>從一個流覽至另一個。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用日誌記憶曾經巡覽過的頁面，以利返回巡覽。

<xref:System.Windows.Controls.Page>、 <xref:System.Windows.Documents.Hyperlink> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、 <xref:System.Windows.Navigation.NavigationService>和日誌形成所提供的導覽支援的核心。 本總覽會在涵蓋包含鬆散[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案、HTML 檔案和物件導覽的先進導覽支援之前, 先深入探索這些功能。

> [!NOTE]
> 在本主題中, 「瀏覽器」一詞只是指可以裝載[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式的瀏覽器, 其中目前包含 Microsoft Internet Explorer 和 Firefox。 只有特定[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]的瀏覽器才支援特定功能, 瀏覽器版本則稱為。

## <a name="navigation-in-wpf-applications"></a>WPF 應用程式中的巡覽

本主題提供中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]的主要導覽功能總覽。 這些功能可供獨立應用程式和[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]使用, 雖然本主題會在的內容[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]中呈現它們。

> [!NOTE]
> 本主題不會討論如何建立和部署[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]。 如需的詳細[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]資訊, 請參閱[WPF XAML 瀏覽器應用程式總覽](wpf-xaml-browser-applications-overview.md)。

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

在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中, 您可以流覽至數種內容類型, 其中包括 .NET Framework 物件、自訂物件、列舉值[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 、使用者控制項、檔案和 HTML 檔案。 不過, 您會發現封裝內容最常見且方便的方式是使用<xref:System.Windows.Controls.Page>。 此外, <xref:System.Windows.Controls.Page>也會執行導覽特有的功能, 以增強其外觀並簡化開發。

使用<xref:System.Windows.Controls.Page>, 您可以使用如下所示的標記[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , 以宣告方式執行可導覽的內容頁面。

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在標記`Page`中實作為其根項目, 而且需要[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]命名空間宣告。 <xref:System.Windows.Controls.Page> `Page`專案包含您要流覽並顯示的內容。 您可以藉由設定`Page.Content`屬性元素來新增內容, 如下列標記所示。

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` 只能包含一個子項目。在上例中，內容是單一字串 "Hello, Page!" 在實務上, 您通常會使用版面配置控制項做為子專案 (請參閱[版面](../advanced/layout.md)配置) 以包含及撰寫內容。

專案的子`Page`專案會被視為<xref:System.Windows.Controls.Page>和的內容, 因此, 您不需要使用明確`Page.Content`宣告。 下列標記是前例的宣告式對等項目。

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

在此情況下`Page.Content` , 會自動使用專案的子項目`Page`進行設定。 如需詳細資訊，請參閱 [WPF 內容模型](../controls/wpf-content-model.md)。

僅限<xref:System.Windows.Controls.Page>標記適用于顯示內容。 不過, <xref:System.Windows.Controls.Page>也可以顯示可讓使用者與頁面互動的控制項, 而且它可以藉由處理事件和呼叫應用程式邏輯來回應使用者互動。 互動式<xref:System.Windows.Controls.Page>會使用標記和程式碼後置的組合來執行, 如下列範例所示。

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

若要讓標記檔案和程式碼後置檔案一起工作，需要設定下列項目：

- 在標記中, `Page`元素必須`x:Class`包含屬性。 建立應用程式時`x:Class` , 標記檔案中的存在會導致 Microsoft build engine (MSBuild) `partial`建立衍生自<xref:System.Windows.Controls.Page>的類別, 並`x:Class`具有屬性所指定的名稱。 這需要新增[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]架構的命名空間宣告 ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` )。 產生`partial` 的`InitializeComponent`類別會執行, 它會呼叫來註冊事件, 並設定在標記中實作為的屬性。

- 在程式碼後置中, 類別必須是`partial`具有與標記中的`x:Class`屬性所指定相同名稱的類別, 而且必須衍生自<xref:System.Windows.Controls.Page>。 這可讓程式碼後置檔案與`partial`建立應用程式時為標記檔案產生的類別相關聯 (請參閱[建立 WPF 應用程式](building-a-wpf-application-wpf.md))。

- 在程式碼後置中<xref:System.Windows.Controls.Page> , 類別必須執行`InitializeComponent`呼叫方法的函式。 `InitializeComponent`會由標記檔案產生`partial`的類別來執行, 以註冊事件並設定在標記中定義的屬性。

> [!NOTE]
> 當您使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]將新<xref:System.Windows.Controls.Page>的新增至專案時, <xref:System.Windows.Controls.Page>會使用標記和程式碼後置來實作為, 並包含必要的設定來建立標記和程式碼後置檔案之間的關聯, 如下所示:此處所述。

一旦有<xref:System.Windows.Controls.Page>, 您就可以流覽至該檔案。 若要指定應用<xref:System.Windows.Controls.Page>程式流覽的第一個, 您必須設定 [啟動<xref:System.Windows.Controls.Page>]。

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>設定起始頁

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 需要瀏覽器中裝載一定數量的應用程式基礎結構。 在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中<xref:System.Windows.Application> , 類別是應用程式定義的一部分, 可建立必要的應用程式基礎結構 (請參閱[應用程式管理總覽](application-management-overview.md))。

應用程式定義通常會使用標記和程式碼後置來實作為, 並將標記檔案設定為`ApplicationDefinition` MSBuild 專案。 以下是的應用程式定義[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]。

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

可以使用其應用程式定義來指定 start <xref:System.Windows.Controls.Page>, 這是<xref:System.Windows.Controls.Page>啟動時[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]自動載入的。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 若要這麼做, 您<xref:System.Windows.Application.StartupUri%2A>可以[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]為所需<xref:System.Windows.Controls.Page>的設定具有的屬性。

> [!NOTE]
> 在大部分情況下, <xref:System.Windows.Controls.Page>會編譯成或與應用程式一起部署。 在這些情況下, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] <xref:System.Windows.Controls.Page>識別的會是一個[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], 這是符合*套件*配置的。 套件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]會在 WPF 的[套件 uri](pack-uris-in-wpf.md)中進一步討論。 您也可以巡覽至使用 http 配置的內容，後文會討論。

您可以在<xref:System.Windows.Application.StartupUri%2A>標記中以宣告方式設定, 如下列範例所示。

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

在此範例中, `StartupUri`屬性是以識別首頁的相對[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]套件來設定。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]當啟動時, 首頁. xaml 會自動流覽並顯示。 如下圖所示, 它會顯示[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]從 Web 服務器啟動的。

![XBAP 頁面](./media/navigation-overview/xbap-launched-from-a-web-server.png "這會顯示從 Web 服務器啟動的 XBAP。")

> [!NOTE]
> 如需有關開發和部署[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]的詳細資訊, 請參閱[wpf XAML 瀏覽器應用程式總覽](wpf-xaml-browser-applications-overview.md)和[部署 wpf 應用程式](deploying-a-wpf-application-wpf.md)。

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>設定主機視窗的標題、寬度和高度

您在上圖中可能注意到的一件事, 就是瀏覽器和 [索引標籤] 面板[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的標題[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]都是的。 除了長之外，標題既不吸引人，也不提供資訊。 基於這個理由, <xref:System.Windows.Controls.Page>您可以藉由<xref:System.Windows.Controls.Page.WindowTitle%2A>設定屬性來變更標題。 此外, 您可以分別設定和<xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page.WindowHeight%2A>, 藉以設定瀏覽器視窗的寬度和高度。

<xref:System.Windows.Controls.Page.WindowTitle%2A>、 <xref:System.Windows.Controls.Page.WindowWidth%2A>和<xref:System.Windows.Controls.Page.WindowHeight%2A>可以在標記中以宣告方式設定, 如下列範例所示。

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

其結果如下圖所示。

![視窗標題、高度、寬度](./media/navigation-overview/window-title-width-height.png "這會顯示您可以設定的視窗標題、高度和寬度。")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>超連結巡覽

一般[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]會包含數個頁面。 從一頁流覽至另一個頁面的最簡單方式是使用<xref:System.Windows.Documents.Hyperlink>。 您可以使用<xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> 專案(如下列標記所示),以宣告的方式`Hyperlink`將加入至。

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

`Hyperlink`元素需要下列專案:

- 要導覽[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]至的套件`NavigateUri` , 如屬性所指定。 <xref:System.Windows.Controls.Page>

- 使用者可以按一下以起始導覽的內容, 例如文字和影像 (針對`Hyperlink`元素可以包含的內容, 請參閱<xref:System.Windows.Documents.Hyperlink>)。

下圖顯示[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Controls.Page>具有<xref:System.Windows.Documents.Hyperlink>之的。

![具有超連結的頁面](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "這會顯示具有超連結之頁面的 XBAP。")

如您<xref:System.Windows.Documents.Hyperlink>所預期, 按一下[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]會導致流覽至`NavigateUri`屬性所識別<xref:System.Windows.Controls.Page>的。 此外, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]會在 Internet Explorer 的 [最近<xref:System.Windows.Controls.Page>使用的頁面] 清單中新增先前的專案。 如下圖所示。

[![上一頁] 和 [下一頁] 按鈕](./media/navigation-overview/back-and-forward-navigation.png "以 [上一頁] 和 [下一頁] 按鈕導覽。")

除了支援從一個<xref:System.Windows.Controls.Page>導覽至另一個, <xref:System.Windows.Documents.Hyperlink>也支援片段導覽。

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>片段巡覽

*片段導覽*是導覽至目前<xref:System.Windows.Controls.Page>或另一個<xref:System.Windows.Controls.Page>中的內容片段。 在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中, 內容片段是指已命名專案所包含的內容。 已命名的元素是已設定其`Name`屬性的元素。 下列標記顯示包含內容片段`TextBlock`的命名元素。

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

若要讓流覽至內容片段`NavigateUri` , 屬性必須包含下列各項: <xref:System.Windows.Documents.Hyperlink>

- <xref:System.Windows.Controls.Page>具有要導覽之[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]內容片段的。

- "#" 字元。

- 上<xref:System.Windows.Controls.Page>包含內容片段之專案的名稱。

片段[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]具有下列格式。

*PageURI* `#` <項目名稱>

以下顯示的範例`Hyperlink`是設定為流覽至內容片段。

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> 本節描述中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]的預設片段導覽執行。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]也可讓您執行自己的片段導覽配置, 而這部分需要處理<xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType>事件。

> [!IMPORTANT]
> 只有在可以透過 HTTP 流覽頁面[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]時, 您才可以[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]流覽到`Page`鬆散分頁中的片段 (僅限標記的檔案, 以作為根項目)。
>
> 不過, 鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]分頁可以流覽至它自己的片段。

<a name="NavigationService"></a>

### <a name="navigation-service"></a>巡覽服務

雖然<xref:System.Windows.Documents.Hyperlink>可讓使用者起始特定<xref:System.Windows.Controls.Page>的導覽, 但尋找和下載<xref:System.Windows.Navigation.NavigationService>頁面的工作是由類別執行。 基本上, <xref:System.Windows.Navigation.NavigationService>可讓您代表用戶端程式代碼 (例如<xref:System.Windows.Documents.Hyperlink>) 來處理導覽要求。 此外, <xref:System.Windows.Navigation.NavigationService>也會執行更高層級的追蹤和影響導覽要求支援。

<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] <xref:System.Windows.Controls.Page>當您按一下時, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]會呼叫來尋找並下載位於指定之套件的。 <xref:System.Windows.Documents.Hyperlink> 已下載<xref:System.Windows.Controls.Page>的會轉換成物件的樹狀結構, 其根物件是已下載<xref:System.Windows.Controls.Page>的實例。 根<xref:System.Windows.Controls.Page>物件的參考會儲存<xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType>在屬性中。 流覽至[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]之內容的套件會儲存<xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>在屬性中, 而則<xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType>會儲存流覽至之最後[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]一頁的套件。

> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式可能會有一個以上的<xref:System.Windows.Navigation.NavigationService>目前作用中。 如需詳細資訊, 請參閱本主題稍後的[導覽主機](#Navigation_Hosts)。

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>以程式設計的巡覽及巡覽服務

您<xref:System.Windows.Navigation.NavigationService>不需要知道是否使用<xref:System.Windows.Documents.Hyperlink>來以宣告方式在標記中執行導覽, <xref:System.Windows.Documents.Hyperlink>因為會<xref:System.Windows.Navigation.NavigationService>代表您使用。 這表示, 只要的直接或間接父系<xref:System.Windows.Documents.Hyperlink>是導覽主控制項 (請參閱 [[導覽主機](#Navigation_Hosts)]), <xref:System.Windows.Documents.Hyperlink>就能夠尋找和使用導覽主機的導覽服務來處理導覽要求。

不過, 在某些情況下, 您需要直接<xref:System.Windows.Navigation.NavigationService>使用, 包括下列各項:

- 當您需要<xref:System.Windows.Controls.Page>使用非無參數的函式來具現化時。

- 當您需要在流覽至之前設定<xref:System.Windows.Controls.Page>上的屬性時。

- 當需要流覽至的時,只能在執行時間決定。<xref:System.Windows.Controls.Page>

在這些情況下, 您需要撰寫程式碼, 藉由呼叫<xref:System.Windows.Navigation.NavigationService.Navigate%2A> <xref:System.Windows.Navigation.NavigationService>物件的方法, 以程式設計方式起始導覽。 這需要取得的參考<xref:System.Windows.Navigation.NavigationService>。

#### <a name="getting-a-reference-to-the-navigationservice"></a>取得 NavigationService 的參考

針對 [[導覽主機](#Navigation_Hosts)] 區段中涵蓋的原因, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式可以有一個<xref:System.Windows.Navigation.NavigationService>以上的。 這表示您的程式碼需要一種方式來<xref:System.Windows.Navigation.NavigationService>尋找, 這<xref:System.Windows.Navigation.NavigationService>通常是流覽至目前<xref:System.Windows.Controls.Page>的。 您可以藉由<xref:System.Windows.Navigation.NavigationService> `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType>呼叫方法來取得的參考。 若要取得<xref:System.Windows.Navigation.NavigationService>導覽至特定<xref:System.Windows.Controls.Page>的, 請將的<xref:System.Windows.Controls.Page>參考傳遞至做為<xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A>方法的引數。 下列程式碼顯示如何取得<xref:System.Windows.Navigation.NavigationService>目前<xref:System.Windows.Controls.Page>的。

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

若<xref:System.Windows.Navigation.NavigationService>要尋找<xref:System.Windows.Controls.Page>的快捷方式, 請<xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page.NavigationService%2A>執行屬性。 這在下列範例中顯示。

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> 當引發<xref:System.Windows.Navigation.NavigationService> 事件時<xref:System.Windows.Controls.Page> , 只能取得其的參考。 <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.Controls.Page>

#### <a name="programmatic-navigation-to-a-page-object"></a>以程式設計方式巡覽至頁面物件

下列範例示範如何使用<xref:System.Windows.Navigation.NavigationService> , 以程式設計方式流覽<xref:System.Windows.Controls.Page>至。 必須以程式設計方式導覽<xref:System.Windows.Controls.Page> , 因為所流覽的只能使用單一、非參數的函式來具現化。 具有<xref:System.Windows.Controls.Page>非無參數的函式的會顯示在下列標記和程式碼中。

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

使用非無參數的函式<xref:System.Windows.Controls.Page>來流覽至的會顯示在下列標記和程式<xref:System.Windows.Controls.Page>代碼中。

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

當按一下<xref:System.Windows.Documents.Hyperlink> [ <xref:System.Windows.Controls.Page> on] 時, 就會藉由具現<xref:System.Windows.Controls.Page>化來起始導覽, 以使用非無參數的函<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>式並呼叫方法來流覽至。 <xref:System.Windows.Navigation.NavigationService.Navigate%2A>接受<xref:System.Windows.Navigation.NavigationService>將導覽至之物件的參考, 而不是套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。

#### <a name="programmatic-navigation-with-a-pack-uri"></a>以程式設計的巡覽及 Pack URI

如果您需要以程式設計方式[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]來建立套件 (例如, 當您只能[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]在執行時間判斷套件) <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> , 可以使用方法。 這在下列範例中顯示。

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>重新整理目前的頁面

如果與儲存在[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 屬性<xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>中的套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]具有相同的套件,則不會下載。<xref:System.Windows.Controls.Page> 若要[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]強制再次下載目前的頁面, 您可以<xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType>呼叫方法, 如下列範例所示。

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>巡覽存留期

如您所見，有多種方式可以初始化巡覽。 當導覽已起始, 而且導覽正在進行時, 您可以使用下列所實的事件<xref:System.Windows.Navigation.NavigationService>來追蹤和影響導覽:

- <xref:System.Windows.Navigation.NavigationService.Navigating>. 要求新的巡覽時發生。 可用於取消巡覽。

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. 在下載期間定期發生以提供導覽進度資訊。

- <xref:System.Windows.Navigation.NavigationService.Navigated>. 找到並下載頁面時發生。

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. 當導覽已停止 (藉由呼叫<xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), 或目前導覽正在進行中要求新的導覽時發生。

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. 在廵覽至要求的內容引發錯誤時發生。

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. 當載入並剖析巡覽到的內容，且開始轉譯時發生。

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. 當內容片段巡覽開始時發生，狀況為︰

  - 立即發生，如果所需片段位在目前的內容中。

  - 載入來源內容之後，如果所需片段位在不同的內容中。

下圖顯示巡覽事件的引發順序。

![頁面導覽流程圖](./media/navigation-overview/order-of-navigation-events.png "頁面導覽事件流程圖表")

一般而言, <xref:System.Windows.Controls.Page>不會關心這些事件。 應用程式很有可能會擔心它們, 因此, 這些事件也會由<xref:System.Windows.Application>類別引發:

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

每次<xref:System.Windows.Navigation.NavigationService>引發事件時<xref:System.Windows.Application> , 類別都會引發對應的事件。 <xref:System.Windows.Controls.Frame>和<xref:System.Windows.Navigation.NavigationWindow>會提供相同的事件, 以偵測其各自範圍內的導覽。

在某些情況下, <xref:System.Windows.Controls.Page>可能會對這些事件感興趣。 例如, <xref:System.Windows.Controls.Page>可能會<xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType>處理事件, 以判斷是否要取消本身的導覽。 這在下列範例中顯示。

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

如果您從<xref:System.Windows.Controls.Page>註冊具有導覽事件的處理常式, 如上述範例所示, 您也必須取消註冊事件處理常式。 如果您沒有這麼做, 則可能會有關于導覽如何[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]使用日誌<xref:System.Windows.Controls.Page>來記住導覽的副作用。

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>以日誌記憶巡覽

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用兩個堆疊記憶您曾廵覽過的頁面︰上一頁堆疊和下一頁堆疊。 當<xref:System.Windows.Controls.Page>您從目前的流覽至新<xref:System.Windows.Controls.Page>的或轉送到現有<xref:System.Windows.Controls.Page>的時, 會<xref:System.Windows.Controls.Page>將目前的加入至*後端堆疊*。 當您從<xref:System.Windows.Controls.Page>目前的回到上一個<xref:System.Windows.Controls.Page>時, 會將目前<xref:System.Windows.Controls.Page>的加入至*正向堆疊*中。 上一頁堆疊、下一頁堆疊和管理它們的功能，統稱為日誌。 後端堆疊和轉寄堆疊中的每個專案都是<xref:System.Windows.Navigation.JournalEntry>類別的實例, 而則稱為*日誌項目*。

#### <a name="navigating-the-journal-from-internet-explorer"></a>從 Internet Explorer 巡覽日誌

就概念而言, 日誌的運作方式與 Internet Explorer 中的 [**上一頁**] 和 [**下一頁**] 按鈕相同。 如下圖所示。

[![上一頁] 和 [下一頁] 按鈕](./media/navigation-overview/back-and-forward-navigation.png "以 [上一頁] 和 [下一頁] 按鈕導覽。")

若[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]為 internet explorer 所裝載的, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]則會將日誌整合到[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] internet explorer 的導覽中。 這可讓使用者使用 Internet Explorer 中[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]的 [**上一頁**]、[**下一頁**] 和 [**最近的頁面**] 按鈕, 在中流覽頁面。

> [!IMPORTANT]
> 在 Internet Explorer 中, 當使用者流覽離開並返回[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]時, 只有未保持運作的頁面記錄項目會保留在日誌中。 如需讓頁面保持運作的討論, 請參閱本主題稍後的[頁面存留期和日誌](#PageLifetime)。

<xref:System.Windows.Controls.Page>根據預設, <xref:System.Windows.Controls.Page>Internet Explorer [**最近使用的頁面**] 清單中出現的每個文字, 都是的。[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 在許多情況下，這對使用者都不是特別有意義。 幸運的是，您可以變更使用下列選項之一的文字︰

1. 附加`JournalEntry.Name`的屬性值。

2. `Page.Title`屬性值。

3. 屬性值[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]和目前<xref:System.Windows.Controls.Page>的。 `Page.WindowTitle`

4. 目前 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的 <xref:System.Windows.Controls.Page>。 (預設值)

選項列示順序符合尋找文字的優先順序。 例如, 如果`JournalEntry.Name`設定, 則會忽略其他值。

下列範例會使用`Page.Title`屬性來變更日誌項目所顯示的文字。

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>巡覽使用 WPF 的日誌

雖然使用者可以使用 Internet Explorer 中的 [**上一頁**]、[**下一頁**] 和 [**最近] 頁面**來流覽日誌, 但您也可以使用所提供的宣告式和[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]程式設計機制來流覽日誌。 這麼做的其中一個原因是在您的[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]頁面中提供自訂導覽。

您可以使用所公開<xref:System.Windows.Input.NavigationCommands>的導覽命令, 以宣告方式加入日誌流覽支援。 下列範例示範如何使用`BrowseBack`導覽命令。

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

您可以使用<xref:System.Windows.Navigation.NavigationService>類別的下列其中一個成員, 以程式設計方式流覽日誌:

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

您也可以透過程式設計方式動作記錄, 如本主題稍後的[保留內容狀態與導覽歷程記錄](#RetainingContentStateWithNavigationHistory)中所述。

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>網頁存留期和日誌

[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]假設有數個頁面包含豐富內容, 包括圖形、動畫和媒體。 這類頁面的磁碟使用量可能相當大，尤其是使用視訊和音訊媒體的時候。 假設日誌「記憶」已流覽過的頁面, 這類[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]的可能很快就會耗用大量且明顯的記憶體數量。

基於這個理由, 日誌的預設行為是將中繼資料儲存<xref:System.Windows.Controls.Page>在每個日誌項目中, 而不是對<xref:System.Windows.Controls.Page>物件的參考。 當流覽記錄項目時, 其<xref:System.Windows.Controls.Page>中繼資料會用來建立指定<xref:System.Windows.Controls.Page>的的新實例。 因此, 流覽的每<xref:System.Windows.Controls.Page>個都具有下圖所說明的存留期。

![頁面存留期](./media/navigation-overview/navigated-page-lifetime.png "這會顯示流覽頁面時的存留期。")

雖然使用預設日誌行為可以節省記憶體耗用量, 但每頁轉譯的效能可能會降低;<xref:System.Windows.Controls.Page> reinstantiating 可能會耗費大量時間, 特別是當它有許多內容時。 如果您需要將<xref:System.Windows.Controls.Page>實例保留在日誌中, 您可以使用兩種技術來進行繪製。 首先, 您可以藉由<xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>呼叫方法, 以程式設計方式流覽至物件。

第二, 您可以將[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <xref:System.Windows.Controls.Page.KeepAlive%2A>屬性設為`true` (預設<xref:System.Windows.Controls.Page>值為`false`), 藉以指定保留日誌中的實例。 如下列範例所示, 您可以在標記<xref:System.Windows.Controls.Page.KeepAlive%2A>中以宣告方式設定。

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

保持運作狀態的<xref:System.Windows.Controls.Page>存留期與不是一樣。 第一次<xref:System.Windows.Controls.Page>保持運作的狀態會被流覽至, 它會具現化, <xref:System.Windows.Controls.Page>就像不會保持運作的一樣。 不過, 因為的實例<xref:System.Windows.Controls.Page>會保留在日誌中, 所以只要它保留在日誌中, 就永遠不會再次具現化。 因此, 如果<xref:System.Windows.Controls.Page>有必須在每<xref:System.Windows.Controls.Page>次導覽時呼叫的初始化邏輯, 您就應該將它從函式移至<xref:System.Windows.FrameworkElement.Loaded>事件的處理常式。 如下圖所示, <xref:System.Windows.FrameworkElement.Loaded>每次<xref:System.Windows.Controls.Page>流覽到<xref:System.Windows.FrameworkElement.Unloaded>和時, 仍會引發和事件。

![當已載入和卸載的事件引發時](./media/navigation-overview/loaded-and-unloaded-events.png "當頁面流覽至和時, 會引發載入和卸載的事件。")

<xref:System.Windows.Controls.Page>當未保持運作時, 您不應該執行下列其中一項動作:

- 儲存其參考或任何部分。

- 使用它未實作的事件來登錄事件處理常式。

執行其中一項作業會建立參考, 強制<xref:System.Windows.Controls.Page>將其保留在記憶體中, 即使已從日誌中移除亦然。

一般來說, 您應該偏好不要<xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page>保持運作的預設行為。 不過，這有下一節要討論的隱含狀態。

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>以巡覽記錄保留內容狀態

如果不<xref:System.Windows.Controls.Page>是保持運作狀態, 而且它具有可從使用者收集資料的控制項, 當使用者流覽離開並回到時, 資料會發生什麼事？ <xref:System.Windows.Controls.Page> 從使用者體驗的觀點而言，使用者應該會希望看到他們先前所輸入的資料。 可惜的<xref:System.Windows.Controls.Page>是, 由於會使用每個導覽來建立的新實例, 因此會 reinstantiated 收集資料的控制項並遺失資料。

幸運的是, 日誌提供了跨<xref:System.Windows.Controls.Page>導覽來記憶資料的支援, 包括控制資料。 具體而言, 每個<xref:System.Windows.Controls.Page>專案的日誌項目都會作為相關聯<xref:System.Windows.Controls.Page>狀態的暫存容器。 下列步驟概述當從流覽時<xref:System.Windows.Controls.Page> , 如何使用這項支援:

1. 目前<xref:System.Windows.Controls.Page>的專案會新增至日誌。

2. 的狀態<xref:System.Windows.Controls.Page>會與該頁面的日誌項目一起儲存, 這會新增至後端堆疊。

3. 新<xref:System.Windows.Controls.Page>的會被流覽至。

當頁面<xref:System.Windows.Controls.Page>流覽回時, 使用日誌, 會進行下列步驟:

1. 已具現化(後端堆疊上的最上層記錄項目)。<xref:System.Windows.Controls.Page>

2. 會使用與的日誌項目<xref:System.Windows.Controls.Page>一起儲存的狀態重新整理。 <xref:System.Windows.Controls.Page>

3. <xref:System.Windows.Controls.Page>會流覽回。

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]當下列控制項用於時, 會自動使用這項<xref:System.Windows.Controls.Page>支援:

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

如果使用這些控制項, 則會在所有<xref:System.Windows.Controls.Page>導覽中記住輸入的資料, 如下圖中的我的**最愛色彩**<xref:System.Windows.Controls.ListBox>所示。 <xref:System.Windows.Controls.Page>

![具有記憶狀態之控制項的頁面](./media/navigation-overview/data-remembered-across-page-navigations.png "在頁面導覽中, 會記住輸入的資料。")

當具有上述清單以外的控制項, 或當狀態儲存在自訂物件中時, 您必須撰寫程式碼, 讓日誌記住跨<xref:System.Windows.Controls.Page>導覽的狀態。 <xref:System.Windows.Controls.Page>

如果您需要記住跨<xref:System.Windows.Controls.Page>導覽的小部分狀態, 您可以使用以<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType>中繼資料旗標<xref:System.Windows.DependencyProperty>設定的相依性屬性 (請參閱)。

如果您<xref:System.Windows.Controls.Page>需要記住跨導覽的狀態包含多個資料片段, 您可能會發現在單一類別中封裝您的狀態並<xref:System.Windows.Navigation.IProvideCustomContentState>執行介面的程式碼較少。

如果您需要流覽<xref:System.Windows.Controls.Page>單一的各種狀態, 而不想<xref:System.Windows.Controls.Page>從本身導覽, 則可以使用<xref:System.Windows.Navigation.IProvideCustomContentState>和<xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>。

<a name="Cookies"></a>

### <a name="cookies"></a>Cookie

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式可以儲存資料的另一種方式是使用<xref:System.Windows.Application.SetCookie%2A>和<xref:System.Windows.Application.GetCookie%2A>方法來建立、更新和刪除 cookie。 您可以在中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]建立的 cookie 與其他類型的 Web 應用程式所使用的 cookie 相同; cookie 是應用程式在應用程式會話期間或之間儲存的任意資料片段。 Cookie 資料通常會採用下列格式的名稱/值組形式。

「名稱」`=`「值」

將資料傳遞至時, <xref:System.Windows.Application.SetCookie%2A>如果要<xref:System.Uri>設定 cookie 的位置, 就會在記憶體中建立 cookie, 而且僅適用于目前應用程式會話的持續時間。 這種類型的 cookie 稱為*會話 cookie*。

若要在應用程式工作階段之間儲存 Cookie，到期日必須使用下列格式新增至 Cookie。

「名稱」`=`「值」`; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

具有到期日的 cookie 會儲存在目前 Windows 安裝的 [Internet Files] 資料夾中, 直到 cookie 到期為止。 這類 cookie 稱為*持續性 cookie* , 因為它會在應用程式會話之間持續保存。

您可以藉由呼叫<xref:System.Windows.Application.GetCookie%2A>方法來取得會話和持續性的 cookie, <xref:System.Uri>傳遞使用<xref:System.Windows.Application.SetCookie%2A>方法設定 cookie 的位置。

以下是中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]支援 cookie 的一些方式:

- [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]獨立應用程式[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]和可以建立和管理 cookie。

- 您[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]可以從瀏覽器存取所建立的 cookie。

- 來自相同網域的 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 可以建立及共用 Cookie。

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]相同網域中的和 HTML 網頁可以建立和共用 cookie。

- 當和鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]提出 Web 要求時, 會分派 cookie。

- 最上層[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]和[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]裝載于 iframe 中的都可以存取 cookie。

- 中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]的 Cookie 支援對所有支援的瀏覽器都是相同的。

- 在 Internet Explorer 中, 會接受[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]與 cookie 相關的 P3P 原則, 特別是關於第一方和協力廠商。 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>結構化巡覽

如果您需要將資料從一個<xref:System.Windows.Controls.Page>傳送到另一個, 您可以將資料當做引數傳遞至的非無參數<xref:System.Windows.Controls.Page>的函式。 請注意, 如果您使用這項技術, 就必須<xref:System.Windows.Controls.Page>維持運作的狀態。如果不是, 則在下次<xref:System.Windows.Controls.Page>流覽[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]至時<xref:System.Windows.Controls.Page> , 會使用無參數的函式來 reinstantiates。

或者, 您<xref:System.Windows.Controls.Page>可以使用需要傳遞的資料來執行設定的屬性。 不過, 當<xref:System.Windows.Controls.Page>需要將資料傳回給導覽到它的<xref:System.Windows.Controls.Page>時, 會變得很棘手。 問題在於, 導覽原本並不支援機制, 以確保在<xref:System.Windows.Controls.Page>流覽之後, 將會傳回。 基本上，巡覽不支援呼叫/傳回語意。 若要解決這個問題[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , 會<xref:System.Windows.Navigation.PageFunction%601>提供類別, 讓您<xref:System.Windows.Controls.Page>用來確保以可預測且結構化的方式傳回至。 如需詳細資訊, 請參閱[結構化導覽總覽](structured-navigation-overview.md)。

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow 類別

至此，您已了解最可能用來建置有可巡覽內容之應用程式的巡覽服務範圍。 這些服務已在的內容[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]中討論, 但它們並不[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]限於。 新式作業系統和 Windows 應用程式利用新式使用者的瀏覽器體驗, 將瀏覽器樣式的導覽併入獨立應用程式中。 常見範例包括︰

- **Word**同義字:流覽 word 選擇。

- 檔案**瀏覽器**:流覽檔案和資料夾。

- **嚮導**:將複雜的工作分解成可以在之間流覽的多個頁面。 其中一個範例是處理新增和移除 Windows 功能的 Windows 元件 Wizard。

若要將瀏覽器樣式的導覽併入您的<xref:System.Windows.Navigation.NavigationWindow>獨立應用程式, 您可以使用類別。 <xref:System.Windows.Navigation.NavigationWindow>衍生自<xref:System.Windows.Window> , 並以提供的相同支援導覽來[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]加以擴充。 您可以使用<xref:System.Windows.Navigation.NavigationWindow>做為獨立應用程式的主視窗, 或當做對話方塊之類的次要視窗。

若要執行<xref:System.Windows.Navigation.NavigationWindow>, 如同中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]的大部分最上層類別 (<xref:System.Windows.Window>、 <xref:System.Windows.Controls.Page>等等), 您可以使用標記和程式碼後置的組合。 這在下列範例中顯示。

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

此<xref:System.Windows.Navigation.NavigationWindow>程式碼會建立, 它會在<xref:System.Windows.Controls.Page>開啟時<xref:System.Windows.Navigation.NavigationWindow>自動流覽至 (首頁. xaml)。 如果是主應用程式視窗, 您可以`StartupUri`使用屬性來啟動它。 <xref:System.Windows.Navigation.NavigationWindow> 下列標記顯示此做法。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

下圖顯示<xref:System.Windows.Navigation.NavigationWindow>作為獨立應用程式的主要視窗。

![主視窗](./media/navigation-overview/navigation-window-as-main-window.png "做為主視窗的導覽視窗")

從圖中, 您可以看到<xref:System.Windows.Navigation.NavigationWindow>有一個標題, 即使它不是在上述範例的<xref:System.Windows.Navigation.NavigationWindow>實程式碼中設定也一樣。 而是使用<xref:System.Windows.Controls.Page.WindowTitle%2A>屬性來設定標題, 如下列程式碼所示。

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

<xref:System.Windows.Controls.Page.WindowWidth%2A>設定和<xref:System.Windows.Controls.Page.WindowHeight%2A>屬性也會影響<xref:System.Windows.Navigation.NavigationWindow>。

當您需要自訂其<xref:System.Windows.Navigation.NavigationWindow>行為或其外觀時, 通常會執行自己的工作。 如果兩樣都不做，您可以使用捷徑。 如果您在獨立[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] <xref:System.Windows.Application.StartupUri%2A> <xref:System.Windows.Controls.Page> <xref:System.Windows.Application> 應用程式<xref:System.Windows.Navigation.NavigationWindow>中將的套件指定為, 則會自動建立來裝載。 <xref:System.Windows.Controls.Page> 下列標記顯示如何啟用此功能。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

如果您想要讓次要應用程式視窗 (例如對話方塊<xref:System.Windows.Navigation.NavigationWindow>) 成為, 您可以使用下列範例中的程式碼來開啟它。

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

其結果如下圖所示。

![對話方塊](./media/navigation-overview/navigation-window-as-dialog-box.png "作為對話方塊的導覽視窗")

如您所見, <xref:System.Windows.Navigation.NavigationWindow>會顯示 Internet Explorer 樣式的 [**上一頁**] 和 [**下一頁**] 按鈕, 讓使用者可以流覽日誌。 這些按鈕提供相同的使用者體驗，如下圖所示。

![NavigationWindow 中的 [上一頁] 和 [下一頁] 按鈕](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "導覽視窗中的 [上一頁] 和 [下一頁] 按鈕")

如果您的頁面提供自己的日誌流覽支援和 UI, 您可以將<xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A>屬性的值設定為, <xref:System.Windows.Navigation.NavigationWindow>以`false`隱藏顯示的 [**上一頁**] 和 [下一頁] 按鈕。

或者, 您可以使用中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]的自訂支援來[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]取代<xref:System.Windows.Navigation.NavigationWindow>本身的。

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Frame 類別

瀏覽器和<xref:System.Windows.Navigation.NavigationWindow>都是裝載可流覽內容的視窗。 在某些情況下，應用程式會有不需要由整個視窗裝載的內容。 這類內容反可以裝載於其他內容中。 您可以使用<xref:System.Windows.Controls.Frame>類別, 將可流覽的內容插入至其他內容。 <xref:System.Windows.Controls.Frame>提供與<xref:System.Windows.Navigation.NavigationWindow>和[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]相同的支援。

下列範例顯示如何使用<xref:System.Windows.Controls.Frame> `Frame`專案, 以宣告方式<xref:System.Windows.Controls.Page>將加入至。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

此`Source`標記<xref:System.Windows.Controls.Frame>會將專案的屬性`Frame`設定為<xref:System.Windows.Controls.Page> , 其[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]一開始應流覽至的套件。 下圖顯示[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Controls.Page>具有的, 其已在<xref:System.Windows.Controls.Frame>數個頁面之間流覽。

![在多個頁面之間流覽的框架](./media/navigation-overview/frame-navigation-between-multiple-pages.png "這會顯示多個頁面之間的框架導覽。")

您不只需要在的<xref:System.Windows.Controls.Frame>內容<xref:System.Windows.Controls.Page>內使用。 在的內容<xref:System.Windows.Controls.Frame> <xref:System.Windows.Window>中裝載, 也是很常見的情況。

根據預設, <xref:System.Windows.Controls.Frame>只有在沒有另一個日誌時, 才會使用自己的日誌。 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame> [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Navigation.NavigationWindow>如果是在或[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]內裝載之內容的一部分, 則會使用屬於或的日誌。 <xref:System.Windows.Controls.Frame> 不過, 有時候<xref:System.Windows.Controls.Frame>可能需要負責自己的日誌。 這麼做的其中一個原因是允許在所裝載的頁面<xref:System.Windows.Controls.Frame>內進行日誌導覽。 如下圖所示。

![框架和頁面圖表](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "這會在框架所主控的頁面中顯示日誌導覽。")

在此情況下<xref:System.Windows.Controls.Frame> , 您可以將的<xref:System.Windows.Controls.Frame.JournalOwnership%2A>屬性<xref:System.Windows.Controls.Frame>設為<xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>, 將設定為使用自己的日誌。 下列標記顯示此做法。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

下圖說明在使用自己的日誌的中<xref:System.Windows.Controls.Frame>流覽的效果。

![使用自己的日誌的框架](./media/navigation-overview/frame-uses-its-own-journal.png "這會顯示在使用自己的日誌的框架內流覽的效果。")

請注意[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame>, 中的導覽會顯示日誌項目, 而不是 Internet Explorer。

> [!NOTE]
> 如果是裝載<xref:System.Windows.Window>于中之內容的一部分, <xref:System.Windows.Controls.Frame>則會使用自己的日誌, 因此會顯示它自己的導覽[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 <xref:System.Windows.Controls.Frame>

如果您的<xref:System.Windows.Controls.Frame>使用者體驗需要提供自己的日誌, 而不顯示導覽[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], 您可以將設定<xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A>為[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]來<xref:System.Windows.Visibility.Hidden>隱藏導覽。 下列標記顯示此做法。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>巡覽裝載

<xref:System.Windows.Controls.Frame>和<xref:System.Windows.Navigation.NavigationWindow>是稱為「導覽主機」的類別。 *導覽主機*是可流覽並顯示內容的類別。 為了完成這項工作, 每個導覽主機<xref:System.Windows.Navigation.NavigationService>都會使用自己的和日誌。 巡覽裝載的基本建構如下圖所示。

導覽![器圖表](./media/navigation-overview/navigation-host-construction.png "導覽主控制項的基本結構")

基本上, 這可<xref:System.Windows.Navigation.NavigationWindow>讓<xref:System.Windows.Controls.Frame>和提供在瀏覽器中裝載時[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]提供的相同導覽支援。

除了使用<xref:System.Windows.Navigation.NavigationService>和日誌以外, 流覽主控制項還會<xref:System.Windows.Navigation.NavigationService>執行相同的成員。 如下圖所示。

![畫面格和 NavigationWindow 中的日誌](./media/navigation-overview/navigation-window-and-frame.png "導覽視窗和框架")

這可讓您針對它們直接設計巡覽支援程式。 如果您需要為裝載于的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window>, 提供自訂導覽, 可以考慮這一點。 此外, 這兩種類型都會執行其他的導覽相關成員`BackStack` ,<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>包括<xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>(, `ForwardStack` )<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>和<xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>(,), 可讓您列舉後端中的記錄項目堆疊和轉送堆疊的對應。

如前所述，應用程式中可有多個日誌。 下圖提供這種情況的範例。

![一個應用程式內的多個日誌](./media/navigation-overview/multiple-journals-in-one-application.png "這是應用程式中一個以上的日誌範例。")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>巡覽至 XAML 頁面以外的內容

在本主題中<xref:System.Windows.Controls.Page> , 和[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] pack 已用來示範的各種導覽功能[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。 不過, <xref:System.Windows.Controls.Page>編譯成應用程式的不是唯一可以流覽的內容類型, 套件[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]則不是識別內容的唯一方法。

如本節所示, 您也可以流覽至鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的檔案、HTML 檔案和物件。

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>巡覽至鬆散的 XAML 檔案

鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案是具有下列特性的檔案:

- 僅[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]包含 (也就是沒有程式碼)。

- 具有適當的命名空間宣告。

- 具有 .xaml 副檔名。

例如, 請考慮將下列內容儲存為鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案, Person. xaml。

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

當您按兩下檔案時，瀏覽器會開啟、巡覽至並顯示內容。 如下圖所示。

![顯示 app.xaml 檔案中的內容](./media/navigation-overview/contents-of-person-xaml-file.png "顯示 Person. XAML 檔案的內容。")

您可以顯示下列的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]鬆散檔案:

- 在本機電腦、內部網路或網際網路上的網站。

- [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)]檔案共用。

- 本機磁碟。

鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案可以新增至瀏覽器的 [我的最愛], 或作為瀏覽器的首頁。

> [!NOTE]
> 如需發佈和啟動鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面的詳細資訊, 請參閱[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)。

鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的一項限制是, 您只能裝載可安全地在部分信任中執行的內容。 例如, `Window`不能是鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案的根項目。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>使用框架巡覽至 HTML 檔案

如您所預期, 您也可以流覽至 HTML。 您只需要提供[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]使用 HTTP 配置的。 例如, 以下[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Frame>顯示流覽至 HTML 網頁的。

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

流覽至 HTML 需要特殊許可權。 例如, 您無法從在網際網路區域[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]部分信任安全性沙箱中執行的進行流覽。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>使用 WebBrowser 控制項巡覽至 HTML 檔案

<xref:System.Windows.Controls.WebBrowser>控制項支援 HTML 檔案裝載、導覽和腳本/managed 程式碼互通性。 如需有關控制項的<xref:System.Windows.Controls.WebBrowser>詳細資訊, <xref:System.Windows.Controls.WebBrowser>請參閱。

如同<xref:System.Windows.Controls.Frame>, 使用<xref:System.Windows.Controls.WebBrowser>流覽至 HTML 需要特殊許可權。 例如, 您可以從部分信任的應用程式, 只流覽至位於來源網站的 HTML。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>巡覽至自訂物件

如果您有儲存為自訂物件的資料, 顯示該資料的一種方式是建立<xref:System.Windows.Controls.Page> , 並將內容系結至這些物件 (請參閱資料系結[總覽](../data/data-binding-overview.md))。 如果您不需要建立整個頁面此額外負荷，而只要顯示物件，則您可以改為直接巡覽至它們。

請考慮`Person`在下列程式碼中執行的類別。

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

若要流覽至它, 您可以<xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType>呼叫方法, 如下列程式碼所示。

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

其結果如下圖所示。

![流覽至類別的頁面](./media/navigation-overview/page-navigates-to-an-object.png "這是導覽至物件的頁面範例。")

在此圖中，您看不到任何有用的內容。 事實上, 顯示的值是`ToString` **Person**物件之方法的傳回值; 根據預設, 這是唯一[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]可用來表示物件的值。 您可以覆寫`ToString`方法以傳回更有意義的資訊, 但它仍然只是字串值。 您可以使用的一項技術, 利用的呈現功能[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]是使用資料範本。 您可以執行[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]可與特定類型的物件產生關聯的資料範本。 下列程式碼顯示`Person`物件的資料範本。

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

在這裡, 資料範本會使用`Person` `DataType`屬性中的`x:Type`標記延伸, 與類型相關聯。 然後`TextBlock` , 資料範本會將元素 ( <xref:System.Windows.Controls.TextBlock>請參閱) 系結`Person`至類別的屬性。 下圖顯示`Person`物件的更新外觀。

![流覽至具有資料範本的類別](./media/navigation-overview/navigating-to-a-class.png "流覽至具有資料範本的類別。")

這項技術的優點是可以取得一致性，因為能夠重複使用資料範本，所以應用程式任何位置都可顯示一致的物件。

如需資料範本的詳細資訊, 請參閱[資料範本化總覽](../data/data-templating-overview.md)。

<a name="Security"></a>

## <a name="security"></a>安全性

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]流覽支援可[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]讓您跨網際網路流覽, 並可讓應用程式裝載協力廠商內容。 為了保護應用程式和使用者免于有害的行為[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , 提供[安全性](../security-wpf.md)和[WPF 部分信任安全性](../wpf-partial-trust-security.md)中所討論的各種安全性功能。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [應用程式管理概觀](application-management-overview.md)
- [WPF 中的 Pack URI](pack-uris-in-wpf.md)
- [結構化巡覽概觀](structured-navigation-overview.md)
- [巡覽拓撲概觀](navigation-topologies-overview.md)
- [HOW-TO 主題](navigation-how-to-topics.md)
- [部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)
