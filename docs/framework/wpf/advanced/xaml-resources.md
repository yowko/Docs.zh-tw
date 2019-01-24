---
title: XAML 資源
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 5898d3236f58cd40c5e1ccd446b756b94e3fb113
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718659"
---
# <a name="xaml-resources"></a>XAML 資源
資源是可在應用程式中不同位置重複使用的物件。 資源的範例包括筆刷和樣式。 本概觀說明如何使用中的資源[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 您也可以建立及存取資源，使用程式碼，或是交換使用程式碼之間和[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 資源和程式碼](../../../../docs/framework/wpf/advanced/resources-and-code.md)。  
  
> [!NOTE]
>  本主題中所述的資源檔案為不同的資源檔中所述[WPF 應用程式資源、 內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)也不同於中所述的內嵌或連結資源[管理應用程式資源 (.NET)](https://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e)。  
  
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>在 XAML 中使用資源  
 下列範例會定義<xref:System.Windows.Media.SolidColorBrush>頁面的根項目上的資源。 此範例會參考資源，並使用它來設定屬性的數個子項目，包括<xref:System.Windows.Shapes.Ellipse>，則<xref:System.Windows.Controls.TextBlock>，和<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[FEResourceSH_snip#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 每個架構層級項目 (<xref:System.Windows.FrameworkElement>或是<xref:System.Windows.FrameworkContentElement>) 已<xref:System.Windows.FrameworkElement.Resources%2A>屬性，這是包含資源的屬性 (作為<xref:System.Windows.ResourceDictionary>) 資源定義。 您可以在任何項目上定義資源。 不過，資源最常定義於根項目，也就是<xref:System.Windows.Controls.Page>在範例中。  
  
 資源字典中的每個資源都必須有唯一索引鍵。 當您在標記中定義的資源時，您將指派到唯一的索引鍵[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)。 索引鍵通常是字串；不過，您也可以使用適當的標記延伸，將它設定為其他物件類型。 特定的功能區中所使用資源非字串索引鍵[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，特別是代表樣式、 元件資源和資料樣式。  
  
 定義資源之後，您可以使用指定索引鍵名稱的資源標記延伸語法，參考要用於屬性值的資源，例如：  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 在上述範例中，當[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入器處理值`{StaticResource MyBrush}`for<xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Controls.Button>，資源查閱邏輯會先檢查資源字典中的<xref:System.Windows.Controls.Button>項目。 如果<xref:System.Windows.Controls.Button>沒有定義資源索引鍵`MyBrush`（它沒有; 其資源集合是空的），查閱會接著檢查的父項目<xref:System.Windows.Controls.Button>，也就是<xref:System.Windows.Controls.Page>。 因此，當您定義的資源上<xref:System.Windows.Controls.Page>根項目，邏輯樹狀結構中的所有項目<xref:System.Windows.Controls.Page>可以存取它，並設定任何屬性的值可接受的您可以重複使用相同的資源<xref:System.Type>的資源表示。 在上述範例中，相同`MyBrush`資源設定兩個不同的屬性：<xref:System.Windows.Controls.Control.Background%2A>的<xref:System.Windows.Controls.Button>，而<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>靜態和動態資源  
 資源可以當做靜態資源或動態資源參考。 這是藉由使用[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)或[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。 標記延伸是一項功能[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以讓標記延伸處理屬性字串，並傳回物件，以指定的物件參考[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入器。 如需標記延伸行為的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 當您使用標記延伸時，您通常會提供一或多個字串形式的參數，以供該特定標記延伸處理，而不是在所設定的屬性內容中進行評估。 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)處理按鍵，藉由查閱在所有可用的資源字典中該索引鍵的值。 這會在載入期間發生，也就是載入程序需要指派接受靜態資源參考的屬性值時。 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)改為處理程序藉由建立運算式和該運算式的索引鍵會保持未評估直到實際執行應用程式時，此時運算式會評估並提供值。  
  
 當您參考資源時，下列考量可能會影響您使用靜態資源參考或動態資源參考：  
  
-   如何為您的應用程式來建立資源的整體設計 (每頁、 在應用程式，在鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，在資源專用組件中)。  
  
-   應用程式功能︰應用程式是否需要即時更新資源？  
  
-   該資源參考型別的相關查閱行為。  
  
-   特定屬性或資源類型，以及這些類型的原生行為。  
  
### <a name="static-resources"></a>靜態資源  
 靜態資源參考最適用於下列情況：  
  
-   應用程式設計將其大部分資源集中到頁面或應用程式層級資源字典中。 由於靜態資源參考不會根據執行階段行為 (例如重新載入頁面) 重新評估，因此當根據資源和應用程式設計不需要動態資源參考時，可避免使用大量動態資源參考，藉此提升一些效能。  
  
-   您要設定不在屬性的值<xref:System.Windows.DependencyObject>或<xref:System.Windows.Freezable>。  
  
-   您要建立編譯成 DLL 並封裝成應用程式一部分或在應用程式之間共用的資源字典。  
  
-   您要建立自訂控制項的佈景主題，然後定義用於佈景主題的資源。 在此情況下，您通常不需要動態資源參考查閱行為，而需要靜態資源參考行為，以便佈景主題可預測並內封查閱。 使用動態資源參考時，甚至是佈景主題內的參考也會在執行階段之前保持未評估，在套用佈景主題時，有些區域項目可能會重新定義佈景主題嘗試參考的索引鍵，而且區域項目將會落在查閱中的佈景主題本身之前。 如果發生此情況，您的佈景主題將不會如預期般運作。  
  
-   您要使用資源來設定大量相依性屬性。 相依性屬性具有屬性系統已啟用的有效值快取，因此如果您將值提供給可在載入時評估的相依性屬性，相依性屬性不必檢查是否有重新評估的運算式，而且可能傳回最後一個有效值。 這項技術可能會提升效能。  
  
-   您想要變更的基礎資源的所有取用者，或您想要使用不同的可寫入執行個體維護每個取用者[x： 共用屬性](../../../../docs/framework/xaml-services/x-shared-attribute.md)。  
  
#### <a name="static-resource-lookup-behavior"></a>靜態資源查閱行為  
  
1.  查閱程序會檢查設定屬性之項目所定義的資源字典內，是否有要求的索引鍵。  
  
2.  查閱程序接著會在邏輯樹狀結構中，向上周游到父項目及其資源字典。 這會繼續直到到達根項目。  
  
3.  接下來，會檢查應用程式資源。 應用程式資源則由定義資源字典內<xref:System.Windows.Application>物件您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  
  
 資源字典內的靜態資源參考必須參考資源參考之前已在語彙上定義的資源。 靜態資源參考無法解析向前參考。 因此，如果您使用靜態資源參考，您必須設計資源字典結構，讓預期要供某個資源使用的所有資源都在每個相關資源字典開頭或附近定義。  
  
 靜態資源查閱可以延伸到佈景主題或系統資源，但這只是因為[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入器會延遲要求。 為了將頁面載入時的執行階段佈景主題正確套用至應用程式，必須有此延遲。 不過，不建議已知只存在於佈景主題中或作為系統資源的索引鍵有靜態資源參考。 這是因為如果使用者即時變更佈景主題，不會重新評估這類參考。 當您要求佈景主題或系統資源時，動態資源參考會更可靠。 但佈景主題項目本身要求另一個資源時則例外。 這些參考應該是靜態資源參考，原因如前所述。  
  
 找不到靜態資源參考時的例外狀況行為會有所不同。 如果已延遲資源，則會在執行階段發生例外狀況。 如果未延遲資源，則會在載入時發生例外狀況。  
  
### <a name="dynamic-resources"></a>動態資源  
 動態資源最適用於下列情況：  
  
-   資源的值取決於執行階段之後才知道的狀況。 這包括系統資源或使用者可設定的資源。 例如，您可以建立參考系統屬性的 setter 值所公開之<xref:System.Windows.SystemColors>， <xref:System.Windows.SystemFonts>，或<xref:System.Windows.SystemParameters>。 由於這些值最終是來自使用者和作業系統的執行階段環境，因此是真正動態的。 您也可能有會變更的應用程式層級佈景主題，其中的頁面層級資源存取也必須擷取該變更。  
  
-   您要建立或參考自訂控制項的佈景主題樣式。  
  
-   您想要調整的內容<xref:System.Windows.ResourceDictionary>應用程式存留期間。  
  
-   您有內含相互依存性的複雜資源結構，可能需要向前參考。 靜態資源參考不支援向前參考，但動態資源參考則支援，因為資源不需要執行階段之前評估，因此向前參考並不相關的概念。  
  
-   您所參考的資源從編譯或工作集的觀點來看特別大，因此當頁面載入時，可能無法立即使用資源。 靜態資源參考一律從載入[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]當頁面載入; 不過，動態資源參考不會載入直到實際使用。  
  
-   您要建立樣式，其中的 setter 值可能來自受到佈景主題或其他使用者設定影響的其他值。  
  
-   您要將資源套用至可能在應用程式存留期間於邏輯樹狀結構中重設父代的項目。 變更父代也可能會變更資源查閱範圍，因此如果您想要根據新範圍重新評估重設父代項目的資源，請一律使用動態資源參考。  
  
#### <a name="dynamic-resource-lookup-behavior"></a>動態資源查閱行為  
 動態資源參考的資源查閱行為平行程式碼中的查閱行為，如果您呼叫<xref:System.Windows.FrameworkElement.FindResource%2A>或<xref:System.Windows.FrameworkElement.SetResourceReference%2A>。  
  
1.  查閱程序會檢查設定屬性之項目所定義的資源字典內，是否有要求的索引鍵。  
  
    -   如果項目定義<xref:System.Windows.FrameworkElement.Style%2A>屬性，<xref:System.Windows.Style.Resources%2A>字典內<xref:System.Windows.Style>已核取。  
  
    -   如果項目定義<xref:System.Windows.Controls.Control.Template%2A>屬性，<xref:System.Windows.FrameworkTemplate.Resources%2A>字典內<xref:System.Windows.FrameworkTemplate>已核取。  
  
2.  查閱程序接著會在邏輯樹狀結構中，向上周游到父項目及其資源字典。 這會繼續直到到達根項目。  
  
3.  接下來，會檢查應用程式資源。 應用程式資源則由定義資源字典內<xref:System.Windows.Application>物件您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  
  
4.  檢查目前使用中佈景主題的佈景主題資源字典。 如果佈景主題在執行階段變更，則會重新評估其值。  
  
5.  檢查系統資源。  
  
 例外狀況行為 (如果有的話) 則有所不同：  
  
-   如果所要求資源<xref:System.Windows.FrameworkElement.FindResource%2A>呼叫，並找不到，會引發例外狀況。  
  
-   如果所要求資源<xref:System.Windows.FrameworkElement.TryFindResource%2A>呼叫，並找不到，會引發任何例外狀況，但傳回的值是`null`。 如果要設定的屬性不接受`null`，則仍有可能，會引發更深入的例外狀況 （這取決於所設定的個別屬性）。  
  
-   如果中的動態資源參考要求資源[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，並找不到，則其行為取決於一般屬性系統中，但一般行為會如同資源所在的層級發生任何屬性設定作業。 例如，如果您嘗試使用無法評估的資源來設定個別按鈕項目的背景，則沒有值會設定結果，但有效值仍然可能來自屬性系統和值優先順序中的其他參與值。 例如，背景值仍然可能來自本機定義的按鈕樣式，或來自佈景主題樣式。 針對不是由佈景主題樣式定義的屬性，資源評估失敗後的有效值可能來自屬性中繼資料內的預設值。  
  
#### <a name="restrictions"></a>限制  
 動態資源參考有一些值得注意的限制。 至少必須符合下列其中一個情況：  
  
-   要設定的屬性必須是屬性上<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。 屬性都必須受<xref:System.Windows.DependencyProperty>。  
  
-   參考中的值是<xref:System.Windows.Style> <xref:System.Windows.Setter>。  
  
-   所設定的屬性必須是屬性上<xref:System.Windows.Freezable>提供的值為<xref:System.Windows.FrameworkElement>或是<xref:System.Windows.FrameworkContentElement>屬性，或<xref:System.Windows.Setter>值。  
  
 由於所設定的屬性必須是<xref:System.Windows.DependencyProperty>或<xref:System.Windows.Freezable>屬性，大部分的屬性變更可以傳播至 UI，因為屬性變更 （變更的動態資源值） 由屬性系統認可。 大多數控制項所包含邏輯，會強制另一個控制項的配置，如果<xref:System.Windows.DependencyProperty>變更和屬性可能會影響版面配置。 然而，並非所有的屬性具有[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)做為其值會保證提供的方式，更新在 UI 中的即時值。 該功能仍然可能會依屬性、擁有屬性的類型，甚至是應用程式的邏輯結構而有所不同。  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>樣式、DataTemplate 和隱含索引鍵  
 更早版本，說明所有項目中<xref:System.Windows.ResourceDictionary>必須有索引鍵。 不過，這不表示所有資源都必須都有明確`x:Key`。 有幾種物件類型會在定義為資源時支援隱含索引鍵，其中索引鍵值會繫結至另一個屬性的值。 這就所謂的隱含索引鍵，而`x:Key`屬性是明確的索引鍵。 您可以藉由指定明確索引鍵，來覆寫任何隱含索引鍵。  
  
 資源的其中一個非常重要的案例是當您定義<xref:System.Windows.Style>。 事實上，<xref:System.Windows.Style>幾乎都定義為資源字典中的項目因為樣式原本就是僅供重複使用。 如需有關樣式的詳細資訊，請參閱 <<c0> [ 設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
 控制項的樣式可以透過隱含索引鍵來建立及參考。 定義預設控制項外觀的佈景主題樣式會依賴此隱含索引鍵。 從要求它的觀點來看，隱含索引鍵是<xref:System.Type>控制項本身。 從定義資源的觀點來看，隱含索引鍵是<xref:System.Windows.Style.TargetType%2A>的樣式。 因此，如果您要建立自訂控制項的佈景主題，建立互動的樣式與現有佈景主題樣式，您不需要指定[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)該<xref:System.Windows.Style>。 此外，如果您想要使用佈景主題樣式，則完全不需要指定任何樣式。 比方說，下列樣式定義的運作方式，即使<xref:System.Windows.Style>有索引鍵，似乎不到資源：  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 該樣式其實有索引鍵： 隱含索引鍵`typeof(` <xref:System.Windows.Controls.Button> `)`。 在標記中，您可以指定<xref:System.Windows.Style.TargetType%2A>直接做為類型名稱 (或您可以選擇性地使用[{x: Type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md) 要傳回<xref:System.Type>。  
  
 透過所使用的預設佈景主題樣式機制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，樣式會套用作為執行階段樣式<xref:System.Windows.Controls.Button>在頁面上，即使<xref:System.Windows.Controls.Button>本身不會嘗試指定其<xref:System.Windows.FrameworkElement.Style%2A>屬性或特定的資源參考的樣式。 稍早在比使用佈景主題字典樣式所具有的相同金鑰的佈景主題字典樣式的查閱序列中找到您頁面中定義的樣式。 您可以指定`<Button>Hello</Button>`頁面，並以您定義的樣式中的任何地方<xref:System.Windows.Style.TargetType%2A>的`Button`會套用至該按鈕。 如果您想，您可以仍然明確樣式的索引鍵具有相同的型別值<xref:System.Windows.Style.TargetType%2A>、 清楚的標記，但為選用。  
  
 樣式的隱含索引鍵不會套用在控制項上如果<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>已`true`(另請注意，<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>可能設定為 control 類別，而不是明確的控制項執行個體上的原生行為的一部分)。 此外，為了支援衍生的類別情節的隱含索引鍵，控制項必須覆寫<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>(提供做為一部分的所有現有控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]這麼做)。 如需樣式、 佈景主題和控制設計的詳細資訊，請參閱[設計可設定樣式控制項的方針](../../../../docs/framework/wpf/controls/guidelines-for-designing-stylable-controls.md)。  
  
 <xref:System.Windows.DataTemplate> 也有隱含索引鍵。 隱含索引鍵<xref:System.Windows.DataTemplate>是<xref:System.Windows.DataTemplate.DataType%2A>屬性值。 <xref:System.Windows.DataTemplate.DataType%2A> 也可以指定為型別名稱，而不是使用明確[{x: Type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md). 如需詳細資訊，請參閱 <<c0> [ 資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.ResourceDictionary>
- [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)
- [資源和程式碼](../../../../docs/framework/wpf/advanced/resources-and-code.md)
- [定義和參考資源](../../../../docs/framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)
- [x:Type 標記延伸模組](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
- [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
- [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
