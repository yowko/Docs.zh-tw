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
ms.openlocfilehash: 23e40a27d04d960306f219a7e8d95a464b1e0dec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639638"
---
# <a name="navigation-overview"></a>巡覽概觀
Windows Presentation Foundation (WPF) 支援兩種類型的應用程式可以使用的瀏覽器樣式巡覽︰ 獨立應用程式和[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]。 封裝內容以供巡覽，來[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]提供<xref:System.Windows.Controls.Page>類別。 您可以從一個巡覽<xref:System.Windows.Controls.Page>到另一個以宣告方式，利用<xref:System.Windows.Documents.Hyperlink>，或以程式設計方式使用<xref:System.Windows.Navigation.NavigationService>。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用日誌記憶曾經巡覽過的頁面，以利返回巡覽。  
  
 <xref:System.Windows.Controls.Page><xref:System.Windows.Documents.Hyperlink>， <xref:System.Windows.Navigation.NavigationService>，及日誌，形成所提供的巡覽支援核心[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。 本概觀會探討這些功能的詳細資料之前先深入介紹巡覽支援，包括巡覽到鬆散[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案，[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]檔案和物件。  
  
> [!NOTE]
>  本主題中，「 瀏覽器 」 一詞是指只可以裝載的瀏覽器[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式，以及目前包含[!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)]和 Firefox。 特定[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]只能由特定的瀏覽器支援的功能，指瀏覽器版本。  

## <a name="navigation-in-wpf-applications"></a>WPF 應用程式中的巡覽  
 本主題提供的主要巡覽功能概觀[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。 這些功能可供獨立應用程式和[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，不過本主題所介紹的是它們的內容中[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]。  
  
> [!NOTE]
>  本主題不討論如何建置和部署[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]。 如需詳細資訊[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，請參閱 < [WPF XAML 瀏覽器應用程式概觀](wpf-xaml-browser-applications-overview.md)。  
  
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
 在  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，您可以瀏覽至包含.NET Framework 物件、 自訂物件，列舉值、 使用者控制項的數種內容類型[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，和[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]檔案。 不過，您會發現，最常見且方便的方式封裝內容是使用<xref:System.Windows.Controls.Page>。 此外，<xref:System.Windows.Controls.Page>實作巡覽特定的功能，以增強其外觀並簡化開發。  
  
 使用<xref:System.Windows.Controls.Page>，以宣告方式，您就可以實作可巡覽網頁[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]內容使用標記，如下所示。  
  
 [!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]  
  
 A <xref:System.Windows.Controls.Page> ，它實作於[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記有`Page`作為其根元素，而且需要[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]命名空間宣告。 `Page`項目包含您想要瀏覽至並顯示內容。 您可以將內容設定`Page.Content`屬性項目，如下列標記所示。  
  
 [!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]  
  
 `Page.Content` 只能包含一個子項目。在上例中，內容是單一字串 "Hello, Page!" 在實務上，您通常會使用的版面配置控制項作為子項目 (請參閱[版面配置](../advanced/layout.md)) 來容納及撰寫您的內容。  
  
 子項目的`Page`項目會被視為內容<xref:System.Windows.Controls.Page>，因此，您不需要使用明確`Page.Content`宣告。 下列標記是前例的宣告式對等項目。  
  
 [!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]  
  
 在此情況下，`Page.Content`的子項目會自動設定`Page`項目。 如需詳細資訊，請參閱 [WPF 內容模型](../controls/wpf-content-model.md)。  
  
 全標記<xref:System.Windows.Controls.Page>適合用來顯示內容。 不過，<xref:System.Windows.Controls.Page>也可以顯示控制項，可讓使用者與頁面互動，以及它可以回應使用者互動的處理事件和呼叫應用程式邏輯。 互動式<xref:System.Windows.Controls.Page>您的使用標記和程式碼後置的組合來實作，如下列範例所示。  
  
 [!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
 [!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]  
  
 若要讓標記檔案和程式碼後置檔案一起工作，需要設定下列項目：  
  
- 在標記中，`Page`元素必須包含`x:Class`屬性。 應用程式建置時是否存在`x:Class`標記中檔案會導致[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]來建立`partial`類別衍生自<xref:System.Windows.Controls.Page>，並具有所指定的名稱`x:Class`屬性。 這需要額外[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]命名空間宣告[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]結構描述 ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` )。 產生`partial`類別會實作`InitializeComponent`，稱為註冊事件，並設定屬性來標記中實作。  
  
- 類別必須是在程式碼後置`partial`類別所指定的同名`x:Class`屬性標記，而且必須衍生自<xref:System.Windows.Controls.Page>。 這可讓程式碼後置檔案相關聯`partial`建置應用程式時，會將標記檔案產生的類別 (請參閱 <<c2> [ 建置 WPF 應用程式](building-a-wpf-application-wpf.md))。  
  
- 在 程式碼後置<xref:System.Windows.Controls.Page>類別必須實作呼叫的建構函式`InitializeComponent`方法。 `InitializeComponent` 實作標記檔案產生的`partial`類別來註冊事件，並設定標記中定義的屬性。  
  
> [!NOTE]
>  當您將加入新<xref:System.Windows.Controls.Page>至您的專案使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，則<xref:System.Windows.Controls.Page>使用標記和程式碼後置實作並包含必要的設定，以建立為標記和程式碼後置檔案之間的關聯此處所述。  
  
 一旦您擁有<xref:System.Windows.Controls.Page>，您可以瀏覽至它。 若要指定第一個<xref:System.Windows.Controls.Page>，巡覽至的應用程式，您需要設定啟動<xref:System.Windows.Controls.Page>。  
  
<a name="Configuring_a_Start_Page"></a>   
### <a name="configuring-a-start-page"></a>設定起始頁  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 需要瀏覽器中裝載一定數量的應用程式基礎結構。 在  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，則<xref:System.Windows.Application>類別是建立必要的應用程式基礎結構的應用程式定義的一部分 (請參閱[應用程式管理概觀](application-management-overview.md))。  
  
 應用程式定義通常標記檔案設定為使用標記和程式碼後置來實作[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`ApplicationDefinition`項目。 以下是應用程式定義[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]。  
  
 [!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
 [!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]  
  
 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]可以使用其應用程式定義，指定起始<xref:System.Windows.Controls.Page>，即<xref:System.Windows.Controls.Page>時會自動載入時[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]啟動。 您可以設定<xref:System.Windows.Application.StartupUri%2A>具有屬性[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]如需<xref:System.Windows.Controls.Page>。  
  
> [!NOTE]
>  在大部分情況下，<xref:System.Windows.Controls.Page>被編譯成或部署的應用程式。 在這些情況下，[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]可識別<xref:System.Windows.Controls.Page>組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，即[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]符合*pack*配置。 組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]討論中進一步[WPF 中的 Pack Uri](pack-uris-in-wpf.md)。 您也可以巡覽至使用 http 配置的內容，後文會討論。  
  
 您可以設定<xref:System.Windows.Application.StartupUri%2A>以宣告方式在標記中，如下列範例所示。  
  
 [!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 在此範例中，`StartupUri`屬性設為相對 pack[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]可識別 HomePage.xaml。 當[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]會啟動，HomePage.xaml 自動巡覽及顯示。 下圖中，它會顯示所示[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]從 Web 伺服器啟動。  
  
 ![XBAP 網頁](./media/navigation-overview/xbap-launched-from-a-web-server.png "這會顯示從 Web 伺服器啟動 XBAP。")  
  
> [!NOTE]
>  如需開發和部署的詳細資訊[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，請參閱 < [WPF XAML 瀏覽器應用程式概觀](wpf-xaml-browser-applications-overview.md)並[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)。  
  
<a name="ConfiguringAXAMLPage"></a>   
### <a name="configuring-the-host-windows-title-width-and-height"></a>設定主機視窗的標題、寬度和高度  
 您可能已經注意到在上圖中的一件事是瀏覽器和索引標籤面板的標題[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]針對[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]。 除了長之外，標題既不吸引人，也不提供資訊。 基於這個理由，<xref:System.Windows.Controls.Page>提供的方式，讓您藉由設定變更標題<xref:System.Windows.Controls.Page.WindowTitle%2A>屬性。 此外，您可以在此處設定所設定的瀏覽器視窗的高度與寬度<xref:System.Windows.Controls.Page.WindowWidth%2A>和<xref:System.Windows.Controls.Page.WindowHeight%2A>分別。  
  
 <xref:System.Windows.Controls.Page.WindowTitle%2A><xref:System.Windows.Controls.Page.WindowWidth%2A>，和<xref:System.Windows.Controls.Page.WindowHeight%2A>可設定，以宣告方式在標記中，如下列範例所示。  
  
 [!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 其結果如下圖所示。  
  
 ![視窗標題、 高度、 寬度](./media/navigation-overview/window-title-width-height.png "這會顯示視窗標題、 高度和寬度，您可以設定。")  
  
<a name="NavigatingBetweenXAMLPages"></a>   
### <a name="hyperlink-navigation"></a>超連結巡覽  
 一般[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]是由數個網頁組成。 若要從一頁巡覽到另一個最簡單的方式是使用<xref:System.Windows.Documents.Hyperlink>。 您可以宣告方式新增<xref:System.Windows.Documents.Hyperlink>要<xref:System.Windows.Controls.Page>使用`Hyperlink`元素，其會顯示在下列標記中。  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 A`Hyperlink`元素需要下列：  
  
- 組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的<xref:System.Windows.Controls.Page>若要瀏覽至所指定`NavigateUri`屬性。  
  
- 內容的使用者可以按一下以啟始巡覽，例如文字和影像 (內容所`Hyperlink`項目可以包含，請參閱<xref:System.Windows.Documents.Hyperlink>)。  
  
 下圖顯示[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]具有<xref:System.Windows.Controls.Page>具有<xref:System.Windows.Documents.Hyperlink>。  
  
 ![具有超連結的頁面](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "這會顯示與超連結的頁面 XBAP。")  
  
 如您所預期，請按一下<xref:System.Windows.Documents.Hyperlink>會導致[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]瀏覽至<xref:System.Windows.Controls.Page>識別`NavigateUri`屬性。 此外，[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]上一個加入的項目<xref:System.Windows.Controls.Page>中的最近存取的頁面清單[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]。 如下圖所示。  
  
 ![上一頁及下一頁按鈕](./media/navigation-overview/back-and-forward-navigation.png "瀏覽使用 [上一頁] 和 [下一頁] 按鈕。")  
  
 以及支援從一個巡覽<xref:System.Windows.Controls.Page>到另一個，<xref:System.Windows.Documents.Hyperlink>也支援片段巡覽。  
  
<a name="FragmentNavigation"></a>   
### <a name="fragment-navigation"></a>片段巡覽  
 *片段巡覽*目前是在內容片段巡覽<xref:System.Windows.Controls.Page>或另一個<xref:System.Windows.Controls.Page>。 在  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，內容片段是具名的項目所包含的內容。 具名的項目是項目具有其`Name`屬性設定。 下列標記顯示具名`TextBlock`元素，其中包含內容片段。  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]  
  
 針對<xref:System.Windows.Documents.Hyperlink>瀏覽至內容片段，`NavigateUri`屬性必須包含下列：  
  
- [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的<xref:System.Windows.Controls.Page>與瀏覽至內容片段。  
  
- "#" 字元。  
  
- 上的項目名稱<xref:System.Windows.Controls.Page>，其中包含內容片段。  
  
 片段[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]具有下列格式。  
  
 *PageURI* `#` <項目名稱>  
  
 下圖顯示的範例`Hyperlink`設定為巡覽至內容片段。  
  
 [!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]  
  
> [!NOTE]
>  本章節描述中的預設片段巡覽實作[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 也可讓您實作您自己的部分需要處理的片段巡覽配置<xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType>事件。  
  
> [!IMPORTANT]
>  您可以巡覽至片段在鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面 (僅標記[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案`Page`作為根項目) 可透過瀏覽頁面時，才[!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)]。  
>   
>  不過，鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面可以巡覽至其本身的片段。  
  
<a name="NavigationService"></a>   
### <a name="navigation-service"></a>巡覽服務  
 雖然<xref:System.Windows.Documents.Hyperlink>可讓使用者初始化巡覽至特定<xref:System.Windows.Controls.Page>，尋找並下載頁面的工作由執行<xref:System.Windows.Navigation.NavigationService>類別。 基本上，<xref:System.Windows.Navigation.NavigationService>讓您能夠處理巡覽要求代替用戶端程式碼，如<xref:System.Windows.Documents.Hyperlink>。 此外，<xref:System.Windows.Navigation.NavigationService>實作高階支援的追蹤及影響巡覽要求。  
  
 當<xref:System.Windows.Documents.Hyperlink>按下時，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]呼叫<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>找出並下載<xref:System.Windows.Controls.Page>在指定的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。 已下載<xref:System.Windows.Controls.Page>轉換成其根物件是所下載的執行個體的物件的樹狀結構<xref:System.Windows.Controls.Page>。 根參考<xref:System.Windows.Controls.Page>物件會儲存在<xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType>屬性。 組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]巡覽至的內容會儲存在<xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>屬性，而<xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType>儲存組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]所巡覽的最後一頁。  
  
> [!NOTE]
>  可能[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]有多個目前作用中的應用程式<xref:System.Windows.Navigation.NavigationService>。 如需詳細資訊，請參閱 <<c0> [ 巡覽裝載](#Navigation_Hosts)本主題稍後的。  
  
<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>   
### <a name="programmatic-navigation-with-the-navigation-service"></a>以程式設計的巡覽及巡覽服務  
 您不需要知道<xref:System.Windows.Navigation.NavigationService>如果導覽以宣告方式在標記使用實作<xref:System.Windows.Documents.Hyperlink>，因為<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.Navigation.NavigationService>代替您。 這表示，只要的直接或間接父代<xref:System.Windows.Documents.Hyperlink>是巡覽裝載 (請參閱[巡覽裝載](#Navigation_Hosts))，<xref:System.Windows.Documents.Hyperlink>將能夠尋找和處理使用巡覽裝載的巡覽服務巡覽要求。  
  
 不過，有些情況需要使用<xref:System.Windows.Navigation.NavigationService>直接，包括下列：  
  
- 當您需要具現化<xref:System.Windows.Controls.Page>使用非預設建構函式。  
  
- 當您需要設定屬性<xref:System.Windows.Controls.Page>巡覽到它之前。  
  
- 當<xref:System.Windows.Controls.Page>，必須以瀏覽至只能決定在執行階段。  
  
 在這些情況下，您需要撰寫程式碼以程式設計方式初始化巡覽，藉由呼叫<xref:System.Windows.Navigation.NavigationService.Navigate%2A>方法的<xref:System.Windows.Navigation.NavigationService>物件。 這需要取得的參考<xref:System.Windows.Navigation.NavigationService>。  
  
#### <a name="getting-a-reference-to-the-navigationservice"></a>取得 NavigationService 的參考  
 如所述的理由[巡覽裝載](#Navigation_Hosts)區段中，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式可以有多個<xref:System.Windows.Navigation.NavigationService>。 這表示您的程式碼需要的方式來尋找<xref:System.Windows.Navigation.NavigationService>，而這通常是<xref:System.Windows.Navigation.NavigationService>巡覽至目前<xref:System.Windows.Controls.Page>。 您可以取得參考<xref:System.Windows.Navigation.NavigationService>藉由呼叫`static`<xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType>方法。 若要取得<xref:System.Windows.Navigation.NavigationService>巡覽至特定<xref:System.Windows.Controls.Page>，您將參考傳遞給<xref:System.Windows.Controls.Page>做為引數<xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A>方法。 下列程式碼示範如何取得<xref:System.Windows.Navigation.NavigationService>目前<xref:System.Windows.Controls.Page>。  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]  
  
 尋找快捷<xref:System.Windows.Navigation.NavigationService>for <xref:System.Windows.Controls.Page>，<xref:System.Windows.Controls.Page>實作<xref:System.Windows.Controls.Page.NavigationService%2A>屬性。 這在下列範例中顯示。  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]  
  
> [!NOTE]
>  A<xref:System.Windows.Controls.Page>只能取得的參考及其<xref:System.Windows.Navigation.NavigationService>當<xref:System.Windows.Controls.Page>引發<xref:System.Windows.FrameworkElement.Loaded>事件。  
  
#### <a name="programmatic-navigation-to-a-page-object"></a>以程式設計方式巡覽至頁面物件  
 下列範例示範如何使用<xref:System.Windows.Navigation.NavigationService>若要以程式設計的方式瀏覽至<xref:System.Windows.Controls.Page>。 以程式設計方式巡覽是必要的因為<xref:System.Windows.Controls.Page>也就是正在巡覽可以只具現化使用單一的非預設的建構函式。 <xref:System.Windows.Controls.Page>具有非預設建構函式會顯示下列標記和程式碼。  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
 [!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]  
  
 <xref:System.Windows.Controls.Page>巡覽至<xref:System.Windows.Controls.Page>使用非預設建構函式會顯示下列標記和程式碼。  
  
 [!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]  
  
 當<xref:System.Windows.Documents.Hyperlink>這<xref:System.Windows.Controls.Page>是按下，即初始化巡覽，以具現化<xref:System.Windows.Controls.Page>瀏覽至使用非預設建構函式和呼叫<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>方法。 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> 接受物件的參考，<xref:System.Windows.Navigation.NavigationService>將瀏覽至，而不是組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
#### <a name="programmatic-navigation-with-a-pack-uri"></a>以程式設計的巡覽及 Pack URI  
 如果您要建構套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]以程式設計方式 (當您只可以判斷組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]在執行階段，例如)，您可以使用<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>方法。 這在下列範例中顯示。  
  
 [!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]  
  
#### <a name="refreshing-the-current-page"></a>重新整理目前的頁面  
 A<xref:System.Windows.Controls.Page>不會有相同的組件下載[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]與組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]儲存於<xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>屬性。 若要強制[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]若要再次下載目前的頁面，您可以呼叫<xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType>方法，如下列範例所示。  
  
 [!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]  
  
<a name="Navigation_Lifetime"></a>   
### <a name="navigation-lifetime"></a>巡覽存留期  
 如您所見，有多種方式可以初始化巡覽。 當巡覽初始化，並進行瀏覽時，您可以追蹤並影響使用下列事件所實作的導覽<xref:System.Windows.Navigation.NavigationService>:  
  
- <xref:System.Windows.Navigation.NavigationService.Navigating>. 要求新的巡覽時發生。 可用於取消巡覽。  
  
- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. 在下載期間定期發生以提供導覽進度資訊。  
  
- <xref:System.Windows.Navigation.NavigationService.Navigated>. 找到並下載頁面時發生。  
  
- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. 當巡覽停止時發生 (藉由呼叫<xref:System.Windows.Navigation.NavigationService.StopLoading%2A>)，或目前的巡覽正在進行時，當要求新的瀏覽。  
  
- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. 在廵覽至要求的內容引發錯誤時發生。  
  
- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. 當載入並剖析巡覽到的內容，且開始轉譯時發生。  
  
- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. 當內容片段巡覽開始時發生，狀況為︰  
  
    - 立即發生，如果所需片段位在目前的內容中。  
  
    - 載入來源內容之後，如果所需片段位在不同的內容中。  
  
 下圖顯示巡覽事件的引發順序。  
  
 ![頁面巡覽流程圖](./media/navigation-overview/order-of-navigation-events.png "頁面巡覽事件流程圖")  
  
 一般情況下，<xref:System.Windows.Controls.Page>不擔心這些事件。 就越有可能與它們有關應用程式及基於這個理由，這些事件也會引發<xref:System.Windows.Application>類別：  
  
- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>  
  
- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>  
  
- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>  
  
- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>  
  
- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>  
  
 每次<xref:System.Windows.Navigation.NavigationService>引發事件時，<xref:System.Windows.Application>類別會引發對應的事件。 <xref:System.Windows.Controls.Frame> 和<xref:System.Windows.Navigation.NavigationWindow>提供相同的事件來偵測瀏覽其各自範圍內。  
  
 在某些情況下，<xref:System.Windows.Controls.Page>可能會想要在這些事件。 例如，<xref:System.Windows.Controls.Page>可能會處理<xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType>事件，以判斷是否要取消巡覽離開本身。 這在下列範例中顯示。  
  
 [!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]  
  
 如果您使用巡覽事件註冊處理常式<xref:System.Windows.Controls.Page>，如同上述範例中，您也必須取消登錄事件處理常式。 如果不這麼做，可能會有副作用，如何[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]瀏覽會記住<xref:System.Windows.Controls.Page>使用日誌巡覽。  
  
<a name="NavigationHistory"></a>   
### <a name="remembering-navigation-with-the-journal"></a>以日誌記憶巡覽  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用兩個堆疊記憶您曾廵覽過的頁面︰上一頁堆疊和下一頁堆疊。 當您從目前的瀏覽<xref:System.Windows.Controls.Page>至新<xref:System.Windows.Controls.Page>的現有向前或向<xref:System.Windows.Controls.Page>，目前<xref:System.Windows.Controls.Page>新增至*上一頁堆疊*。 當您從目前的瀏覽<xref:System.Windows.Controls.Page>回到先前<xref:System.Windows.Controls.Page>，目前<xref:System.Windows.Controls.Page>加入至*下一頁堆疊*。 上一頁堆疊、下一頁堆疊和管理它們的功能，統稱為日誌。 上一頁堆疊和下一頁堆疊中的每個項目是的執行個體<xref:System.Windows.Navigation.JournalEntry>類別，並稱為*日誌項目*。  
  
#### <a name="navigating-the-journal-from-internet-explorer"></a>從 Internet Explorer 巡覽日誌  
 就概念而言，日誌運作方式相同方式來**回**並**向前**按鈕[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]執行。 如下圖所示。  
  
 ![上一頁及下一頁按鈕](./media/navigation-overview/back-and-forward-navigation.png "瀏覽使用 [上一頁] 和 [下一頁] 按鈕。")  
  
 針對[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]所裝載的[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]將日誌整合到瀏覽[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]。 這可讓使用者瀏覽中的分頁[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]利用**回**，**向前**，和**最近存取的頁面**按鈕[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]。 日誌尚未整合至[!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)]相同的方式會因[!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)]或 Internet Explorer 8。 相反地，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]轉譯替代的巡覽[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]中，當使用者巡覽離開再回到[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]，只有不保持運作的頁面日誌項目會保留在日誌中。 如需讓頁面保持運作的討論，請參閱[網頁存留期和日誌](#PageLifetime)本主題稍後的。  
  
 根據預設，每個文字<xref:System.Windows.Controls.Page>出現在**最近存取的頁面**份[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]會[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如<xref:System.Windows.Controls.Page>。 在許多情況下，這對使用者都不是特別有意義。 幸運的是，您可以變更使用下列選項之一的文字︰  
  
1. 附加`JournalEntry.Name`屬性值。  
  
2. `Page.Title`屬性值。  
  
3. `Page.WindowTitle`屬性值與[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]目前<xref:System.Windows.Controls.Page>。  
  
4. 目前 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的 <xref:System.Windows.Controls.Page>。 (預設值)  
  
 選項列示順序符合尋找文字的優先順序。 例如，如果`JournalEntry.Name`時，就會忽略其他值。  
  
 下列範例會使用`Page.Title`屬性來變更日誌項目顯示的文字。  
  
 [!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]  
  
#### <a name="navigating-the-journal-using-wpf"></a>巡覽使用 WPF 的日誌  
 雖然使用者可以使用巡覽日誌**回復**，**向前**，並**最近存取的頁面**中[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]，您也可以瀏覽使用這兩個日誌所提供的宣告式和程式設計機制[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。 若要這樣做的其中一個原因是要提供自訂的瀏覽[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]在頁面中。  
  
 您可以使用所公開的巡覽命令，以宣告方式新增日誌巡覽支援<xref:System.Windows.Input.NavigationCommands>。 下列範例示範如何使用`BrowseBack`巡覽命令。  
  
 [!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]  
  
 使用其中一個的下列成員，您可以以程式設計方式巡覽日誌<xref:System.Windows.Navigation.NavigationService>類別：  
  
- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>  
  
- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>  
  
- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>  
  
- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>  
  
 日誌也可操作以程式設計的方式中所述[以巡覽記錄保留內容狀態](#RetainingContentStateWithNavigationHistory)本主題稍後的。  
  
<a name="PageLifetime"></a>   
### <a name="page-lifetime-and-the-journal"></a>網頁存留期和日誌  
 請考慮[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]包含多格式內容的數個頁面，包括圖形、 動畫和媒體。 這類頁面的磁碟使用量可能相當大，尤其是使用視訊和音訊媒體的時候。 假設日誌 「 記憶 」 頁面已巡覽至、 這類[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]會快速消耗有大型且明顯的記憶體數量。  
  
 基於這個理由，日誌的預設行為是儲存<xref:System.Windows.Controls.Page>中繼資料在各日誌項目，而不是參考<xref:System.Windows.Controls.Page>物件。 當巡覽日誌項目時，其<xref:System.Windows.Controls.Page>中繼資料用來建立的新執行個體指定的<xref:System.Windows.Controls.Page>。 如此一來，每個<xref:System.Windows.Controls.Page>，巡覽至具有如下圖所示的存留期。  
  
 ![網頁存留期](./media/navigation-overview/navigated-page-lifetime.png "這會顯示網頁被巡覽時的存留期。")  
  
 雖然使用預設的日誌行為可以節省記憶體耗用量，可能會降低每頁的轉譯效能;重新具現化<xref:System.Windows.Controls.Page>可以大量時間，特別是當它有許多內容。 如果您需要保留<xref:System.Windows.Controls.Page>執行個體在筆記本中，您可以在兩種技術，這種方式上繪製。 首先，您以程式設計方式巡覽至<xref:System.Windows.Controls.Page>藉由呼叫物件<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>方法。  
  
 第二，您可以指定[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]保留的執行個體<xref:System.Windows.Controls.Page>中設定日誌<xref:System.Windows.Controls.Page.KeepAlive%2A>屬性設`true`(預設值是`false`)。 下列範例所示，您可以設定<xref:System.Windows.Controls.Page.KeepAlive%2A>以宣告方式在標記中。  
  
 [!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]  
  
 存留期<xref:System.Windows.Controls.Page>也就是保持運作是不是由稍有不同。 第一次<xref:System.Windows.Controls.Page>保持運作巡覽至，就像具現化<xref:System.Windows.Controls.Page>，不保持運作。 不過，因為執行個體<xref:System.Windows.Controls.Page>會保留在筆記本中，它會永遠不會再次具現化的只要它會保留在日誌。 因此，如果<xref:System.Windows.Controls.Page>具有需要每次呼叫的初始化邏輯<xref:System.Windows.Controls.Page>瀏覽時，應該把它從建構函式的處理常式到<xref:System.Windows.FrameworkElement.Loaded>事件。 下圖所示<xref:System.Windows.FrameworkElement.Loaded>並<xref:System.Windows.FrameworkElement.Unloaded>事件仍會引發每次<xref:System.Windows.Controls.Page>分別巡覽到或離開。  
  
 ![引發 Loaded 和 Unloaded 事件時](./media/navigation-overview/loaded-and-unloaded-events.png "來回巡覽頁面時引發 Loaded 和 unloaded 的事件。")  
  
 當<xref:System.Windows.Controls.Page>不是保持運作，您不應該執行下列其中一項：  
  
- 儲存其參考或任何部分。  
  
- 使用它未實作的事件來登錄事件處理常式。  
  
 任一這些步驟會建立參考，強制<xref:System.Windows.Controls.Page>来保留在記憶體中，即使它已從日誌移除。  
  
 一般情況下，您應該會偏好使用預設值<xref:System.Windows.Controls.Page>行為，不讓<xref:System.Windows.Controls.Page>保持運作。 不過，這有下一節要討論的隱含狀態。  
  
<a name="RetainingContentStateWithNavigationHistory"></a>   
### <a name="retaining-content-state-with-navigation-history"></a>以巡覽記錄保留內容狀態  
 如果<xref:System.Windows.Controls.Page>不保持運作，而且它有使用者，如果使用者巡覽離開再回到，資料會發生什麼事從收集資料的控制項<xref:System.Windows.Controls.Page>嗎？ 從使用者體驗的觀點而言，使用者應該會希望看到他們先前所輸入的資料。 不幸的是，因為的新執行個體<xref:System.Windows.Controls.Page>會透過每個導覽中，該控制收集的資料會重新具現化，而且會遺失資料。  
  
 幸運的是，日誌記憶跨越的資料中提供支援<xref:System.Windows.Controls.Page>巡覽，包括控制項資料。 具體來說，每個日誌項目<xref:System.Windows.Controls.Page>做為相關聯的暫存容器<xref:System.Windows.Controls.Page>狀態。 下列步驟概述如何使用這項支援時<xref:System.Windows.Controls.Page>從巡覽至：  
  
1. 目前的項目<xref:System.Windows.Controls.Page>新增至日誌。  
  
2. 狀態<xref:System.Windows.Controls.Page>會與該頁面上，新增至上一頁堆疊的日誌項目一起儲存。  
  
3. 新<xref:System.Windows.Controls.Page>巡覽。  
  
 當頁面<xref:System.Windows.Controls.Page>是巡覽回使用筆記本中，進行下列步驟：  
  
1. <xref:System.Windows.Controls.Page>具現化 （上一頁堆疊的最上層日誌項目）。  
  
2. <xref:System.Windows.Controls.Page>就會重新整理的日誌項目一起儲存的狀態<xref:System.Windows.Controls.Page>。  
  
3. <xref:System.Windows.Controls.Page>巡覽回。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用下列控制項上時，會自動使用這項支援<xref:System.Windows.Controls.Page>:  
  
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
  
 如果<xref:System.Windows.Controls.Page>會使用這些控制項，輸入至其中的資料會記住跨<xref:System.Windows.Controls.Page>巡覽，如所示**偏愛顏色**<xref:System.Windows.Controls.ListBox>在下圖中。  
  
 ![使用記憶狀態之控制項的頁面](./media/navigation-overview/data-remembered-across-page-navigations.png "輸入資料會記住所有頁面巡覽。")  
  
 當<xref:System.Windows.Controls.Page>已在上述清單中，以外的控制項，或當狀態儲存在自訂物件，您需要撰寫程式碼，讓日誌記住之間的狀態<xref:System.Windows.Controls.Page>巡覽。  
  
 如果您需要記住小片段狀態，跨<xref:System.Windows.Controls.Page>巡覽，您可以使用相依性屬性 (請參閱 < <xref:System.Windows.DependencyProperty>) 設定為將<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType>中繼資料旗標。  
  
 如果狀態，您<xref:System.Windows.Controls.Page>需要記住所有巡覽包含多個資料片段，您可能會發現較少的程式碼封裝單一類別並實作大量<xref:System.Windows.Navigation.IProvideCustomContentState>介面。  
  
 如果您要瀏覽各種狀態的單一<xref:System.Windows.Controls.Page>，而不從巡覽<xref:System.Windows.Controls.Page>本身，您可以使用<xref:System.Windows.Navigation.IProvideCustomContentState>和<xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>。  
  
<a name="Cookies"></a>   
### <a name="cookies"></a>Cookie  
 另一個方式來[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式可以儲存資料是使用 cookie，建立、 更新和刪除利用<xref:System.Windows.Application.SetCookie%2A>和<xref:System.Windows.Application.GetCookie%2A>方法。 您可以在建立的 cookie[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]相同的 cookie 的其他類型的 Web 應用程式使用的 cookie 任意應用程式在用戶端電腦期間，或是跨應用程式工作階段儲存的資料。 Cookie 資料通常會採用下列格式的名稱/值組形式。  
  
 「名稱」`=`「值」  
  
 當將資料傳遞至<xref:System.Windows.Application.SetCookie%2A>，連同<xref:System.Uri>設定 cookie 的位置，cookie 會在記憶體中建立，，它僅供目前的應用程式工作階段的持續期間。 這種類型的 cookie 指*工作階段 cookie*。  
  
 若要在應用程式工作階段之間儲存 Cookie，到期日必須使用下列格式新增至 Cookie。  
  
 「名稱」`=`「值」`; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`  
  
 過期的 cookie 儲存在目前[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]安裝的 Temporary Internet Files 資料夾，直到 cookie 到期為止。 此類 cookie 稱為*永續性 cookie*因為它會存留在應用程式工作階段。  
  
 您藉由呼叫擷取工作階段和永續性 cookie<xref:System.Windows.Application.GetCookie%2A>方法，傳遞<xref:System.Uri>cookie 已設定使用位置的<xref:System.Windows.Application.SetCookie%2A>方法。  
  
 以下是一些支援 cookie 的方式[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:  
  
- [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 獨立應用程式和[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]都可建立及管理 cookie。  
  
- 所建立的 cookie[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]可以從瀏覽器存取。  
  
- 來自相同網域的 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 可以建立及共用 Cookie。  
  
- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 和[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]來自相同網域的頁面可建立及共用 cookie。  
  
- 會分派 cookie 時[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]和鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面提出 Web 要求。  
  
- 最上層[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]和[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]裝載於 IFRAME 可以存取 cookie。  
  
- 中的 cookie 支援[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]適用於所有支援的瀏覽器。  
  
- 在  [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]，會接受與 ccookie 的 P3P 原則[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，特別是關於第一方和第三方[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]。  
  
<a name="Structured_Navigation"></a>   
### <a name="structured-navigation"></a>結構化巡覽  
 如果您需要將資料從某個<xref:System.Windows.Controls.Page>到另一個，您可以將資料傳遞做為引數的非預設建構函式<xref:System.Windows.Controls.Page>。 請注意，是否您使用這項技術，您必須保留<xref:System.Windows.Controls.Page>作用中; 如果沒有，請在下一次您瀏覽至<xref:System.Windows.Controls.Page>，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]重複具現化<xref:System.Windows.Controls.Page>使用預設建構函式。  
  
 或者，您<xref:System.Windows.Controls.Page>可實作設定需要傳遞資料的屬性。 事情會變麻煩，不過，當<xref:System.Windows.Controls.Page>需要將資料送回<xref:System.Windows.Controls.Page>，導覽到它。 問題是巡覽不以原生方式支援機制保證，<xref:System.Windows.Controls.Page>會在從巡覽後返回。 基本上，巡覽不支援呼叫/傳回語意。 若要解決這個問題，請[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]提供<xref:System.Windows.Navigation.PageFunction%601>類別，您可以使用以確保<xref:System.Windows.Controls.Page>傳回給可預測且結構化的方式。 如需詳細資訊，請參閱 <<c0> [ 結構化巡覽概觀](structured-navigation-overview.md)。  
  
<a name="The_NavigationWindow_Class"></a>   
## <a name="the-navigationwindow-class"></a>NavigationWindow 類別  
 至此，您已了解最可能用來建置有可巡覽內容之應用程式的巡覽服務範圍。 這些服務所討論的內容[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，但不限於[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]。 現代作業系統和 Windows 應用程式利用現代瀏覽器式巡覽併入獨立的應用程式的使用者的瀏覽器體驗。 常見範例包括︰  
  
- **Word 同義字**:瀏覽的文字選項。  
  
- **檔案總管**:瀏覽檔案和資料夾。  
  
- **精靈**:細分成多個頁面可以巡覽之間複雜的工作。 例如，處理新增和移除 Windows 功能 [Windows 元件精靈]。  
  
 若要瀏覽器式巡覽併入獨立的應用程式中，您可以使用<xref:System.Windows.Navigation.NavigationWindow>類別。 <xref:System.Windows.Navigation.NavigationWindow> 衍生自<xref:System.Windows.Window>並將它擴充與相同巡覽支援，[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]提供。 您可以使用<xref:System.Windows.Navigation.NavigationWindow>作為獨立應用程式的主要視窗或次要視窗，例如對話方塊。  
  
 若要實作<xref:System.Windows.Navigation.NavigationWindow>，就像使用大部分的最上層類別，在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)](<xref:System.Windows.Window>， <xref:System.Windows.Controls.Page>，依此類推)，您使用標記和程式碼後置的組合。 這在下列範例中顯示。  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
 [!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]  
  
 此程式碼會建立<xref:System.Windows.Navigation.NavigationWindow>自動巡覽至<xref:System.Windows.Controls.Page>(HomePage.xaml) 時<xref:System.Windows.Navigation.NavigationWindow>開啟。 如果<xref:System.Windows.Navigation.NavigationWindow>是主要的應用程式 視窗中，您可以使用`StartupUri`屬性來啟動它。 下列標記顯示此做法。  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]  
  
 下圖顯示<xref:System.Windows.Navigation.NavigationWindow>作為獨立應用程式的主視窗。  
  
 ![主視窗](./media/navigation-overview/navigation-window-as-main-window.png "主要視窗的 瀏覽視窗")  
  
 從圖中，您可以看到<xref:System.Windows.Navigation.NavigationWindow>有標題，即使它不設定<xref:System.Windows.Navigation.NavigationWindow>前述範例中的實作程式碼。 相反地，使用設定標題<xref:System.Windows.Controls.Page.WindowTitle%2A>屬性，下列程式碼所示。  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]  
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]  
  
 設定<xref:System.Windows.Controls.Page.WindowWidth%2A>並<xref:System.Windows.Controls.Page.WindowHeight%2A>屬性也會影響<xref:System.Windows.Navigation.NavigationWindow>。  
  
 通常，您會實作您自己<xref:System.Windows.Navigation.NavigationWindow>當您需要自訂其行為或外觀。 如果兩樣都不做，您可以使用捷徑。 如果您指定的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的<xref:System.Windows.Controls.Page>作為<xref:System.Windows.Application.StartupUri%2A>獨立應用程式中，<xref:System.Windows.Application>會自動建立<xref:System.Windows.Navigation.NavigationWindow>主機<xref:System.Windows.Controls.Page>。 下列標記顯示如何啟用此功能。  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]  
  
 如果您想要次要應用程式視窗中的，例如對話方塊成為<xref:System.Windows.Navigation.NavigationWindow>，您可以在下列範例中使用程式碼，以開啟它。  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
 [!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]  
  
 其結果如下圖所示。  
  
 ![對話方塊](./media/navigation-overview/navigation-window-as-dialog-box.png "作為對話方塊的 瀏覽視窗")  
  
 如您所見，<xref:System.Windows.Navigation.NavigationWindow>會顯示[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]-樣式**回**並**向前**按鈕，可讓使用者巡覽日誌。 這些按鈕提供相同的使用者體驗，如下圖所示。  
  
 ![上一頁及下一頁按鈕在 NavigationWindow](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "向後和向前瀏覽視窗中的按鈕")  
  
 如果您的頁面會提供其本身日誌巡覽支援及 UI，您可以隱藏**回**並**向前**所顯示的按鈕<xref:System.Windows.Navigation.NavigationWindow>藉由設定的值<xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A>屬性`false`.  
  
 或者，您可以使用中的自訂支援[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]來取代[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的<xref:System.Windows.Navigation.NavigationWindow>本身。  
  
<a name="Frame_in_Standalone_Applications"></a>   
## <a name="the-frame-class"></a>Frame 類別  
 這兩個瀏覽器和<xref:System.Windows.Navigation.NavigationWindow>是該裝載可巡覽內容的視窗。 在某些情況下，應用程式會有不需要由整個視窗裝載的內容。 這類內容反可以裝載於其他內容中。 您可以將可巡覽內容插入其他內容使用<xref:System.Windows.Controls.Frame>類別。 <xref:System.Windows.Controls.Frame> 提供相同的支援<xref:System.Windows.Navigation.NavigationWindow>和[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]。  
  
 下列範例示範如何新增<xref:System.Windows.Controls.Frame>要<xref:System.Windows.Controls.Page>以宣告方式是藉由使用`Frame`項目。  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]  
  
 此標記會將`Source`的屬性`Frame`組件的項目[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如<xref:System.Windows.Controls.Page>，<xref:System.Windows.Controls.Frame>應該一開始瀏覽至。 下圖顯示[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]具有<xref:System.Windows.Controls.Page>具有<xref:System.Windows.Controls.Frame>已往復巡覽數個頁面。  
  
 ![具有多個頁面之間巡覽框架](./media/navigation-overview/frame-navigation-between-multiple-pages.png "這會顯示多個頁面之間的畫面格巡覽。")  
  
 您不必只使用<xref:System.Windows.Controls.Frame>的內容當中<xref:System.Windows.Controls.Page>。 它也是通用的裝載<xref:System.Windows.Controls.Frame>的內容當中<xref:System.Windows.Window>。  
  
 根據預設，<xref:System.Windows.Controls.Frame>只會使用其本身的日誌，如果沒有其他日誌。 如果<xref:System.Windows.Controls.Frame>是任何一個區塊所裝載之內容的一部分<xref:System.Windows.Navigation.NavigationWindow>或有[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]，<xref:System.Windows.Controls.Frame>會使用屬於日誌<xref:System.Windows.Navigation.NavigationWindow>或[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]。 有時候，不過，<xref:System.Windows.Controls.Frame>可能要負責使用其本身的日誌。 若要這樣做的其中一個原因是允許日誌巡覽裝載的頁面內<xref:System.Windows.Controls.Frame>。 如下圖所示。  
  
 ![框架和頁面圖表](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "這會顯示依畫面格所裝載的頁面中的日誌巡覽。")  
  
 在此情況下，您可以設定<xref:System.Windows.Controls.Frame>藉由設定使用其本身的日誌<xref:System.Windows.Controls.Frame.JournalOwnership%2A>屬性<xref:System.Windows.Controls.Frame>至<xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>。 下列標記顯示此做法。  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]  
  
 下圖說明內巡覽的效果<xref:System.Windows.Controls.Frame>使用其本身的日誌。  
  
 ![使用其本身的日誌的框架](./media/navigation-overview/frame-uses-its-own-journal.png "這會顯示使用其本身的日誌的框架內巡覽的效果。")  
  
 請注意，日誌項目會顯示經由巡覽[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]中<xref:System.Windows.Controls.Frame>，而非以[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]。  
  
> [!NOTE]
>  如果<xref:System.Windows.Controls.Frame>是裝載於內容的一部分<xref:System.Windows.Window>，<xref:System.Windows.Controls.Frame>會使用其本身的日誌，並因此顯示自己的巡覽[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 如果您的使用者體驗需要<xref:System.Windows.Controls.Frame>提供其本身的日誌，而不會顯示巡覽[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，您可以隱藏巡覽[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]藉由設定<xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A>到<xref:System.Windows.Visibility.Hidden>。 下列標記顯示此做法。  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]  
  
<a name="Navigation_Hosts"></a>   
## <a name="navigation-hosts"></a>巡覽裝載  
 <xref:System.Windows.Controls.Frame> 和<xref:System.Windows.Navigation.NavigationWindow>是稱為巡覽裝載的類別。 A*巡覽裝載*是類別，可以瀏覽至並顯示內容。 若要達成此目的，每個巡覽裝載都會使用自己<xref:System.Windows.Navigation.NavigationService>和日誌。 巡覽裝載的基本建構如下圖所示。  
  
 ![導覽器圖表](./media/navigation-overview/navigation-host-construction.png "巡覽裝載的基本建構")  
  
 基本上，這可讓<xref:System.Windows.Navigation.NavigationWindow>並<xref:System.Windows.Controls.Frame>提供相同巡覽支援，[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]提供裝載於瀏覽器時。  
  
 除了使用<xref:System.Windows.Navigation.NavigationService>和日誌，巡覽裝載實作相同的成員，<xref:System.Windows.Navigation.NavigationService>實作。 如下圖所示。  
  
 ![在框架和 NavigationWindow 中的日誌](./media/navigation-overview/navigation-window-and-frame.png "瀏覽 視窗和框架")  
  
 這可讓您針對它們直接設計巡覽支援程式。 如果您需要提供自訂的瀏覽您可以考慮這[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]for<xref:System.Windows.Controls.Frame>裝載在<xref:System.Windows.Window>。 此外，這兩種類型會實作其他的巡覽相關成員，包括`BackStack`(<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) 及`ForwardStack`(<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>)，可讓您列舉背後的日誌項目堆疊，並分別轉寄堆疊。  
  
 如前所述，應用程式中可有多個日誌。 下圖提供這種情況的範例。  
  
 ![一個應用程式中的多個日誌](./media/navigation-overview/multiple-journals-in-one-application.png "這是應用程式中的多個日誌的範例。")  
  
<a name="Navigating_to_Content_Other_than_Pages"></a>   
## <a name="navigating-to-content-other-than-xaml-pages"></a>巡覽至 XAML 頁面以外的內容  
 在本主題中，整個<xref:System.Windows.Controls.Page>與套件[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]已用來示範各種巡覽功能[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。 不過，<xref:System.Windows.Controls.Page>也就是編譯成應用程式不是唯一的就可以瀏覽的內容和套件類型[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]並非以識別內容的唯一途徑。  
  
 如本節所示，您也可以巡覽到鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]檔案和物件。  
  
<a name="Navigating_to_Loose_XAML_Files"></a>   
### <a name="navigating-to-loose-xaml-files"></a>巡覽至鬆散的 XAML 檔案  
 鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案是具有下列特性的檔案：  
  
- 僅包含[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]（也就是沒有程式碼）。  
  
- 具有適當的命名空間宣告。  
  
- 具有 .xaml 副檔名。  
  
 例如，請考慮下列內容儲存為鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案 Person.xaml。  
  
 [!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]  
  
 當您按兩下檔案時，瀏覽器會開啟、巡覽至並顯示內容。 如下圖所示。  
  
 ![顯示 Person.XAML 檔案中的內容](./media/navigation-overview/contents-of-person-xaml-file.png "顯示 Person.XAML 檔案的內容。")  
  
 您可以顯示鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]下列檔案：  
  
- 在本機電腦、內部網路或網際網路上的網站。  
  
- A[!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)]檔案共用。  
  
- 本機磁碟。  
  
 鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案可以新增至瀏覽器的我的最愛，或者是瀏覽器的首頁。  
  
> [!NOTE]
>  如需發佈和啟動鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面，請參閱[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)。  
  
 鬆散的一項限制[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是您可以只裝載能夠安全地在部分信任中執行的內容。 例如，`Window`不能鬆散的根項目[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。  
  
<a name="Navigating_to_HTML_Files_Using_Frame"></a>   
### <a name="navigating-to-html-files-by-using-frame"></a>使用框架巡覽至 HTML 檔案  
 如您所料，您也可以巡覽至[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]。 您只需要提供[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]使用 http 配置。 例如，下列[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]會顯示<xref:System.Windows.Controls.Frame>巡覽至[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]頁面。  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]  
  
 瀏覽至[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]需要特殊權限。 例如，您無法從瀏覽[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]網際網路區域部分信任安全性沙箱中執行。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。  
  
<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>   
### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>使用 WebBrowser 控制項巡覽至 HTML 檔案  
 <xref:System.Windows.Controls.WebBrowser>控制項支援[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]文件裝載、 巡覽和指令碼 /managed 程式碼互通性。 如需詳細資訊的相關<xref:System.Windows.Controls.WebBrowser>控制項，請參閱<xref:System.Windows.Controls.WebBrowser>。  
  
 像是<xref:System.Windows.Controls.Frame>，請巡覽至[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]使用<xref:System.Windows.Controls.WebBrowser>需要特殊權限。 例如，從部分信任應用程式，您可以巡覽至[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]位於來源網站上。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。  
  
<a name="Navigating_to_Objects"></a>   
### <a name="navigating-to-custom-objects"></a>巡覽至自訂物件  
 如果您有儲存為自訂物件的資料，顯示該資料的一種方法是建立<xref:System.Windows.Controls.Page>繫結至這些物件的內容 (請參閱 <<c2> [ 資料繫結概觀](../data/data-binding-overview.md))。 如果您不需要建立整個頁面此額外負荷，而只要顯示物件，則您可以改為直接巡覽至它們。  
  
 請考慮`Person`在下列程式碼中實作的類別。  
  
 [!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
 [!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]  
  
 若要瀏覽至它，請呼叫<xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType>方法，如下列程式碼所示。  
  
 [!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]  
  
 [!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
 [!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]  
  
 其結果如下圖所示。  
  
 ![巡覽至類別的頁面](./media/navigation-overview/page-navigates-to-an-object.png "這是巡覽至物件的頁面的範例。")  
  
 在此圖中，您看不到任何有用的內容。 事實上，顯示的值是傳回值`ToString`方法**人員**物件; 根據預設，這是唯一值[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]可用來代表您的物件。 您可以覆寫`ToString`方法，以傳回更有意義的資訊，雖然它仍然只是一個字串值。 您可以使用的技術會充分利用的簡報功能[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]是使用資料範本。 您可以實作資料範本，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]可以與特定類型的物件建立關聯。 下列程式碼顯示的資料範本`Person`物件。  
  
 [!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]  
  
 在這裡，與相關聯的資料範本`Person`使用的型別`x:Type`中的標記延伸`DataType`屬性。 資料範本接著會繫結`TextBlock`項目 (請參閱 < <xref:System.Windows.Controls.TextBlock>) 的屬性`Person`類別。 下圖顯示更新後的外觀`Person`物件。  
  
 ![巡覽至具有資料範本類別](./media/navigation-overview/navigating-to-a-class.png "巡覽至具有資料範本的類別。")  
  
 這項技術的優點是可以取得一致性，因為能夠重複使用資料範本，所以應用程式任何位置都可顯示一致的物件。  
  
 如需有關資料範本的詳細資訊，請參閱 <<c0> [ 資料範本化概觀](../data/data-templating-overview.md)。  
  
<a name="Security"></a>   
## <a name="security"></a>安全性  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 巡覽支援可[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]巡覽跨網際網路，而且可讓應用程式裝載協力廠商內容。 保護應用程式和使用者的有害行為，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]提供了各種中討論的安全性功能[安全性](../security-wpf.md)並[WPF 部分信任安全性](../wpf-partial-trust-security.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [應用程式管理概觀](application-management-overview.md)
- [WPF 中的 Pack URI](pack-uris-in-wpf.md)
- [結構化巡覽概觀](structured-navigation-overview.md)
- [巡覽拓撲概觀](navigation-topologies-overview.md)
- [HOW-TO 主題](navigation-how-to-topics.md)
- [部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)
