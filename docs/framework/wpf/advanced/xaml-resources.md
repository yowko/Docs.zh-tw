---
title: XAML 資源
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 738a4f397b1677b867126c7bb439b027f951baa0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958811"
---
# <a name="xaml-resources"></a>XAML 資源
資源是可在應用程式中不同位置重複使用的物件。 資源的範例包括筆刷和樣式。 本總覽說明如何使用中的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]資源。 您也可以使用程式碼來建立及存取資源, 或交替在程式[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]代碼與之間。 如需詳細資訊, 請參閱[資源和程式碼](resources-and-code.md)。  
  
> [!NOTE]
> 本主題所述的資源檔不同于[WPF 應用程式資源、內容和資料檔案](../app-development/wpf-application-resource-content-and-data-files.md)中所述的資源檔, 而且不同于[管理應用程式資源 (.net) 中所述的內嵌或連結的資源](/visualstudio/ide/managing-application-resources-dotnet)。  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>在 XAML 中使用資源  
 下列範例會將定義<xref:System.Windows.Media.SolidColorBrush>為頁面根項目上的資源。 然後, 此範例會參考資源, 並使用它來設定數個子項目的屬性, <xref:System.Windows.Shapes.Ellipse>包括<xref:System.Windows.Controls.TextBlock>、和<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 每個架構層級專案<xref:System.Windows.FrameworkElement> ( <xref:System.Windows.FrameworkContentElement>或) 都<xref:System.Windows.FrameworkElement.Resources%2A>有屬性, 這是包含資源所定義之資源 (如<xref:System.Windows.ResourceDictionary>) 的屬性。 您可以在任何項目上定義資源。 不過, 資源最常定義在根項目上, 在此範例<xref:System.Windows.Controls.Page>中為。  
  
 資源字典中的每個資源都必須有唯一索引鍵。 當您在標記中定義資源時, 您可以透過[x:Key](../../xaml-services/x-key-directive.md)指示詞指派唯一索引鍵。 索引鍵通常是字串；不過，您也可以使用適當的標記延伸，將它設定為其他物件類型。 資源的非字串索引鍵是由中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的某些功能區域所使用, 特別是針對樣式、元件資源和資料樣式。  
  
 定義資源之後，您可以使用指定索引鍵名稱的資源標記延伸語法，參考要用於屬性值的資源，例如：  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 在上述範例中, 當[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入器處理上`{StaticResource MyBrush}` <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>屬性的值時, 資源查閱邏輯會先檢查<xref:System.Windows.Controls.Button>元素的資源字典。 如果<xref:System.Windows.Controls.Button>沒有資源索引鍵`MyBrush`的定義 (不是, 它的資源集合是空的), 則查閱會接著<xref:System.Windows.Controls.Button>檢查的父元素, 也就是<xref:System.Windows.Controls.Page>。 因此, 當您在<xref:System.Windows.Controls.Page>根項目上定義資源時, 的邏輯樹狀結構<xref:System.Windows.Controls.Page>中的所有專案都可以存取它, 而且您可以重複使用相同的資源來設定接受<xref:System.Type>該資源的任何屬性值。該值. 在上述範例中, `MyBrush`相同的資源會設定兩個不同的屬性<xref:System.Windows.Controls.Control.Background%2A> : <xref:System.Windows.Controls.Button>的、和<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>靜態和動態資源  
 資源可以當做靜態資源或動態資源參考。 這可以使用[StaticResource 標記延伸](staticresource-markup-extension.md)或[DynamicResource 標記延伸](dynamicresource-markup-extension.md)來完成。 標記延伸是的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]一項功能, 讓您可以藉由標記延伸處理屬性字串, 並將物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]傳回載入器, 來指定物件參考。 如需標記延伸行為的詳細資訊, 請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
 當您使用標記延伸時，您通常會提供一或多個字串形式的參數，以供該特定標記延伸處理，而不是在所設定的屬性內容中進行評估。 [StaticResource 標記延伸](staticresource-markup-extension.md)會在所有可用的資源字典中查閱該索引鍵的值, 藉此處理索引鍵。 這會在載入期間發生，也就是載入程序需要指派接受靜態資源參考的屬性值時。 [DynamicResource 標記延伸](dynamicresource-markup-extension.md)會藉由建立運算式來處理索引鍵, 而且該運算式會保持未評估狀態, 直到應用程式實際執行為止, 此時會評估運算式並提供值。  
  
 當您參考資源時，下列考量可能會影響您使用靜態資源參考或動態資源參考：  
  
- 如何建立應用程式資源的整體設計 (每頁在應用程式中, 在鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的情況下, 在僅限資源的元件中)。  
  
- 應用程式功能︰應用程式是否需要即時更新資源？  
  
- 該資源參考型別的相關查閱行為。  
  
- 特定屬性或資源類型，以及這些類型的原生行為。  
  
### <a name="static-resources"></a>靜態資源  
 靜態資源參考最適用於下列情況：  
  
- 應用程式設計將其大部分資源集中到頁面或應用程式層級資源字典中。 由於靜態資源參考不會根據執行階段行為 (例如重新載入頁面) 重新評估，因此當根據資源和應用程式設計不需要動態資源參考時，可避免使用大量動態資源參考，藉此提升一些效能。  
  
- 您正在設定不在<xref:System.Windows.DependencyObject> <xref:System.Windows.Freezable>或上的屬性值。  
  
- 您要建立編譯成 DLL 並封裝成應用程式一部分或在應用程式之間共用的資源字典。  
  
- 您要建立自訂控制項的佈景主題，然後定義用於佈景主題的資源。 在此情況下，您通常不需要動態資源參考查閱行為，而需要靜態資源參考行為，以便佈景主題可預測並內封查閱。 使用動態資源參考時，甚至是佈景主題內的參考也會在執行階段之前保持未評估，在套用佈景主題時，有些區域項目可能會重新定義佈景主題嘗試參考的索引鍵，而且區域項目將會落在查閱中的佈景主題本身之前。 如果發生此情況，您的佈景主題將不會如預期般運作。  
  
- 您要使用資源來設定大量相依性屬性。 相依性屬性具有屬性系統已啟用的有效值快取，因此如果您將值提供給可在載入時評估的相依性屬性，相依性屬性不必檢查是否有重新評估的運算式，而且可能傳回最後一個有效值。 這項技術可能會提升效能。  
  
- 您想要變更所有取用者的基礎資源, 或您想要使用[X:Shared 屬性](../../xaml-services/x-shared-attribute.md)為每個取用者維護不同的可寫入實例。  
  
#### <a name="static-resource-lookup-behavior"></a>靜態資源查閱行為  
  
1. 查閱程序會檢查設定屬性之項目所定義的資源字典內，是否有要求的索引鍵。  
  
2. 查閱程序接著會在邏輯樹狀結構中，向上周游到父項目及其資源字典。 這會繼續直到到達根項目。  
  
3. 接下來，會檢查應用程式資源。 應用程式資源是資源字典中的資源, 由<xref:System.Windows.Application> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式的物件所定義。  
  
 資源字典內的靜態資源參考必須參考資源參考之前已在語彙上定義的資源。 靜態資源參考無法解析向前參考。 因此，如果您使用靜態資源參考，您必須設計資源字典結構，讓預期要供某個資源使用的所有資源都在每個相關資源字典開頭或附近定義。  
  
 靜態資源查閱可以延伸到主題或系統資源, 但只有在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入器延遲要求時才支援。 為了將頁面載入時的執行階段佈景主題正確套用至應用程式，必須有此延遲。 不過，不建議已知只存在於佈景主題中或作為系統資源的索引鍵有靜態資源參考。 這是因為如果使用者即時變更佈景主題，不會重新評估這類參考。 當您要求佈景主題或系統資源時，動態資源參考會更可靠。 但佈景主題項目本身要求另一個資源時則例外。 這些參考應該是靜態資源參考，原因如前所述。  
  
 找不到靜態資源參考時的例外狀況行為會有所不同。 如果已延遲資源，則會在執行階段發生例外狀況。 如果未延遲資源，則會在載入時發生例外狀況。  
  
### <a name="dynamic-resources"></a>動態資源  
 動態資源最適用於下列情況：  
  
- 資源的值取決於執行階段之後才知道的狀況。 這包括系統資源或使用者可設定的資源。 例如, 您可以建立參考系統屬性的 setter 值, 如<xref:System.Windows.SystemColors>、 <xref:System.Windows.SystemFonts>或<xref:System.Windows.SystemParameters>所公開。 由於這些值最終是來自使用者和作業系統的執行階段環境，因此是真正動態的。 您也可能有會變更的應用程式層級佈景主題，其中的頁面層級資源存取也必須擷取該變更。  
  
- 您要建立或參考自訂控制項的佈景主題樣式。  
  
- 您想要<xref:System.Windows.ResourceDictionary>在應用程式存留期間調整的內容。  
  
- 您有內含相互依存性的複雜資源結構，可能需要向前參考。 靜態資源參考不支援向前參考, 但動態資源參考會支援它們, 因為在執行時間之前, 不需要評估資源, 而向前參考則不是相關的概念。  
  
- 您所參考的資源從編譯或工作集的觀點來看特別大，因此當頁面載入時，可能無法立即使用資源。 靜態資源參考一律會在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面載入時載入, 但是動態資源參考在實際使用之前不會載入。  
  
- 您要建立樣式，其中的 setter 值可能來自受到佈景主題或其他使用者設定影響的其他值。  
  
- 您要將資源套用至可能在應用程式存留期間於邏輯樹狀結構中重設父代的項目。 變更父代也可能會變更資源查閱範圍，因此如果您想要根據新範圍重新評估重設父代項目的資源，請一律使用動態資源參考。  
  
#### <a name="dynamic-resource-lookup-behavior"></a>動態資源查閱行為  
 如果您呼叫<xref:System.Windows.FrameworkElement.FindResource%2A>或<xref:System.Windows.FrameworkElement.SetResourceReference%2A>, 動態資源參考的資源查閱行為會與程式碼中的查閱行為類似。  
  
1. 查閱程序會檢查設定屬性之項目所定義的資源字典內，是否有要求的索引鍵。  
  
    - 如果元素定義<xref:System.Windows.FrameworkElement.Style%2A>屬性, 則<xref:System.Windows.Style>會檢查<xref:System.Windows.Style.Resources%2A>內的字典。  
  
    - 如果元素定義<xref:System.Windows.Controls.Control.Template%2A>屬性, 則<xref:System.Windows.FrameworkTemplate>會檢查<xref:System.Windows.FrameworkTemplate.Resources%2A>內的字典。  
  
2. 查閱程序接著會在邏輯樹狀結構中，向上周游到父項目及其資源字典。 這會繼續直到到達根項目。  
  
3. 接下來，會檢查應用程式資源。 應用程式資源是資源字典中的資源, 由<xref:System.Windows.Application> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式的物件所定義。  
  
4. 檢查目前使用中佈景主題的佈景主題資源字典。 如果佈景主題在執行階段變更，則會重新評估其值。  
  
5. 檢查系統資源。  
  
 例外狀況行為 (如果有的話) 則有所不同：  
  
- 如果資源是由<xref:System.Windows.FrameworkElement.FindResource%2A>呼叫所要求, 而且找不到, 則會引發例外狀況。  
  
- 如果資源是由<xref:System.Windows.FrameworkElement.TryFindResource%2A>呼叫所要求, 而且找不到, 則不會引發任何例外狀況, 但傳回的值是。 `null` 如果所設定的屬性不接受`null`, 仍然可能會引發更深入的例外狀況 (這取決於所設定的個別屬性)。  
  
- 如果資源是由中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的動態資源參考所要求, 而且找不到, 則行為會根據一般屬性系統而定, 但一般行為會如同資源所在的層級上沒有發生屬性設定作業一樣。 例如，如果您嘗試使用無法評估的資源來設定個別按鈕項目的背景，則沒有值會設定結果，但有效值仍然可能來自屬性系統和值優先順序中的其他參與值。 例如，背景值仍然可能來自本機定義的按鈕樣式，或來自佈景主題樣式。 針對不是由佈景主題樣式定義的屬性，資源評估失敗後的有效值可能來自屬性中繼資料內的預設值。  
  
#### <a name="restrictions"></a>限制  
 動態資源參考有一些值得注意的限制。 至少必須符合下列其中一個情況：  
  
- 要設定的屬性必須是<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>上的屬性。 該屬性必須由<xref:System.Windows.DependencyProperty>所支援。  
  
- 參考適用于中<xref:System.Windows.Style> <xref:System.Windows.Setter>的值。  
  
- 要設定的<xref:System.Windows.Freezable>屬性必須是上的屬性, 它是以<xref:System.Windows.FrameworkElement> <xref:System.Windows.Setter>或<xref:System.Windows.FrameworkContentElement>屬性的值或值的形式提供。  
  
 因為所設定的屬性必須是<xref:System.Windows.DependencyProperty>或<xref:System.Windows.Freezable>屬性, 大部分的屬性變更都可以傳播至 UI, 因為屬性系統會認可屬性變更 (變更的動態資源值)。 大部分的控制項都包含邏輯, 會在<xref:System.Windows.DependencyProperty>變更時強制控制項的另一個版面配置, 而該屬性可能會影響版面配置。 不過, 並非所有具有[DynamicResource 標記延伸](dynamicresource-markup-extension.md)作為其值的屬性, 都保證會以在 UI 中即時更新的方式提供值。 該功能仍然可能會依屬性、擁有屬性的類型，甚至是應用程式的邏輯結構而有所不同。  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>樣式、DataTemplate 和隱含索引鍵  
 稍早, 已指出中<xref:System.Windows.ResourceDictionary>的所有專案都必須有索引鍵。 不過, 這並不表示所有資源都必須具有明確`x:Key`的。 有幾種物件類型會在定義為資源時支援隱含索引鍵，其中索引鍵值會繫結至另一個屬性的值。 這就是所謂的隱含索引鍵, 而`x:Key`屬性則是明確的索引鍵。 您可以藉由指定明確索引鍵，來覆寫任何隱含索引鍵。  
  
 資源的一個非常重要的案例是當您定義<xref:System.Windows.Style>時。 事實上, <xref:System.Windows.Style>幾乎一律會定義為資源字典中的專案, 因為樣式原本就是要重複使用。 如需樣式的詳細資訊, 請參閱設定樣式[和範本](../controls/styling-and-templating.md)。  
  
 控制項的樣式可以透過隱含索引鍵來建立及參考。 定義預設控制項外觀的佈景主題樣式會依賴此隱含索引鍵。 從要求它的觀點來看, 隱含的索引<xref:System.Type>鍵是控制項本身的。 從定義資源的觀點來看, 隱含索引鍵是<xref:System.Windows.Style.TargetType%2A>樣式的。 因此, 如果您要建立自訂控制項的主題、建立與現有主題樣式互動的樣式, 則不需要為該指定[x:Key](../../xaml-services/x-key-directive.md)指示<xref:System.Windows.Style>詞。 此外，如果您想要使用佈景主題樣式，則完全不需要指定任何樣式。 例如, 下列樣式定義的運作方式, <xref:System.Windows.Style>雖然資源似乎沒有索引鍵:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 該樣式的確有一個索引鍵: 隱含索引鍵`typeof(`。 <xref:System.Windows.Controls.Button> `)` 在標記中, 您可以將<xref:System.Windows.Style.TargetType%2A>直接指定為類型名稱 (或者, 您可以選擇性地使用[{x:Type...}](../../xaml-services/x-type-markup-extension.md) <xref:System.Type>傳回。  
  
 透過使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的預設主題樣式機制, 該樣式會套用為<xref:System.Windows.Controls.Button>頁面<xref:System.Windows.Controls.Button>上的執行時間樣式, 即使本身不會嘗試指定其<xref:System.Windows.FrameworkElement.Style%2A>屬性或特定資源樣式的參考。 您在頁面中所定義的樣式, 會與主題字典樣式所擁有的相同索引鍵, 在查閱序列中找到。 您可以只指定`<Button>Hello</Button>`頁面中的任何位置, 而您`Button`使用<xref:System.Windows.Style.TargetType%2A>定義的樣式會套用至該按鈕。 如果您想要的話, 您仍然可以使用與相同的型別值<xref:System.Windows.Style.TargetType%2A>來明確地為樣式加上索引鍵, 以便在標記中更清楚, 但這是選擇性的。  
  
 如果<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>為, 則`true`樣式的隱含索引鍵不會套用在控制項上 ( <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>也請注意, 可能會設定為控制項類別的原生行為的一部分, 而不是明確地在控制項的實例上)。 此外, 為了支援衍生類別案例的隱含索引鍵, 控制項必須覆寫<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (在中提供的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]所有現有控制項都會執行此動作)。 如需樣式、主題和控制項設計的詳細資訊, 請參閱[設計可設定樣式控制項的方針](../controls/guidelines-for-designing-stylable-controls.md)。  
  
 <xref:System.Windows.DataTemplate>也有隱含的索引鍵。 的隱含索引鍵<xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate.DataType%2A>是屬性值。 <xref:System.Windows.DataTemplate.DataType%2A>也可以指定為類型的名稱, 而不是明確地使用[{x:Type...}](../../xaml-services/x-type-markup-extension.md)。 如需詳細資訊, 請參閱[資料範本化總覽](../data/data-templating-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.ResourceDictionary>
- [應用程式資源](optimizing-performance-application-resources.md)
- [資源和程式碼](resources-and-code.md)
- [定義和參考資源](how-to-define-and-reference-a-resource.md)
- [應用程式管理概觀](../app-development/application-management-overview.md)
- [x:Type 標記延伸模組](../../xaml-services/x-type-markup-extension.md)
- [StaticResource 標記延伸](staticresource-markup-extension.md)
- [DynamicResource 標記延伸](dynamicresource-markup-extension.md)
