---
title: 定義 XAML 資源
description: 瞭解適用于 .NET Core 的 WPF 中的 XAML 資源。 瞭解 XAML 資源的類型，並瞭解如何定義 XAML 資源。
author: thraka
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: b278bb92afc308578d60e347871e0150b26a95db
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "82071280"
---
# <a name="overview-of-xaml-resources"></a>XAML 資源的總覽

資源是可以在應用程式中的不同位置重複使用的物件。 資源的範例包括筆刷和樣式。 本總覽說明如何使用 Extensible Application Markup Language （XAML）中的資源。 您也可以使用程式碼來建立和存取資源。

> [!NOTE]
> 本文所述的 XAML 資源與應用程式*資源*不同，通常是新增至應用程式的檔案，例如內容、資料或內嵌檔案。

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>在 XAML 中使用資源

下列範例會將定義<xref:System.Windows.Media.SolidColorBrush>為頁面根項目上的資源。 然後，此範例會參考資源，並使用它來設定數個子項目的屬性， <xref:System.Windows.Shapes.Ellipse>包括、 <xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Controls.Button>。

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

每個架構層級專案<xref:System.Windows.FrameworkElement> （ <xref:System.Windows.FrameworkContentElement>或）都<xref:System.Windows.FrameworkElement.Resources%2A>有一個屬性，其<xref:System.Windows.ResourceDictionary>為包含已定義資源的類型。 您可以在任何元素上定義資源，例如<xref:System.Windows.Controls.Button>。 不過，資源最常定義在根項目上，在此範例<xref:System.Windows.Controls.Page>中為。

資源字典中的每個資源都必須有唯一索引鍵。 當您在標記中定義資源時，您可以透過[x：Key](../xaml-services/xkey-directive.md)指示詞指派唯一索引鍵。 索引鍵通常是字串；不過，您也可以使用適當的標記延伸，將它設定為其他物件類型。 WPF 中的特定功能區域會使用資源的非字串索引鍵，特別是針對樣式、元件資源和資料樣式。

您可以使用定義的資源搭配資源標記延伸語法，以指定資源的索引鍵名稱。 例如，使用資源作為另一個元素上的屬性值。

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

在上述範例中，當 XAML 載入`{StaticResource MyBrush}`器處理上<xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>屬性的值時，資源查閱邏輯會先檢查<xref:System.Windows.Controls.Button>元素的資源字典。 如果<xref:System.Windows.Controls.Button>沒有資源索引鍵`MyBrush`的定義（在此範例中，它不是，它的資源集合是空的），則查閱接下來會<xref:System.Windows.Controls.Button>檢查的父<xref:System.Windows.Controls.Page>元素，也就是。 如果您在<xref:System.Windows.Controls.Page>根項目上定義資源，則的邏輯樹狀結構中的所有元素都<xref:System.Windows.Controls.Page>可以存取它。 而且，您可以重複使用相同的資源來設定接受資源所代表之相同類型的任何屬性值。 在`MyBrush`上述範例中，相同的資源會設定兩個不同的<xref:System.Windows.Controls.Control.Background%2A>屬性： <xref:System.Windows.Controls.Button>的、和<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。

## <a name="static-and-dynamic-resources"></a>靜態和動態資源

可以將資源當做靜態或動態來參考。 您可以使用[StaticResource 標記延伸](../../framework/wpf/advanced/staticresource-markup-extension.md)或[DynamicResource 標記延伸](../../framework/wpf/advanced/dynamicresource-markup-extension.md)來建立參考。 標記延伸是一種 XAML 功能，可讓標記延伸處理屬性字串，並將物件傳回至 XAML 載入器，藉此指定物件參考。 如需標記延伸行為的詳細資訊，請參閱[標記延伸和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。

當您使用標記延伸時，通常會以特定標記延伸所處理的字串格式提供一或多個參數。 [StaticResource 標記延伸](../../framework/wpf/advanced/staticresource-markup-extension.md)會在所有可用的資源字典中查閱該索引鍵的值，藉此處理索引鍵。 處理會在載入期間進行，這是載入進程需要指派屬性值的時候。 [DynamicResource 標記延伸](../../framework/wpf/advanced/dynamicresource-markup-extension.md)會改為藉由建立運算式來處理索引鍵，而且該運算式會在應用程式執行之前維持未評估狀態，此時運算式會進行評估並提供值。

當您參考資源時，下列考量可能會影響您使用靜態資源參考或動態資源參考：

- 當您決定如何為應用程式建立資源的整體設計（每頁、在應用程式中、在鬆散 XAML 中，或在僅限資源的元件中）時，請考慮下列事項：

- 應用程式的功能。 您的應用程式需求即時更新資源嗎？
- 該資源參考型別的相關查閱行為。
- 特定屬性或資源類型，以及這些類型的原生行為。

## <a name="static-resources"></a>靜態資源

靜態資源參考最適用於下列情況：

- 您的應用程式設計將大部分的資源集中在頁面或應用層級的資源字典中。 靜態資源參考不會根據執行時間行為重新評估，例如重載頁面。 因此，根據您的資源和應用程式設計，避免大量動態資源參考時，可能會有一些效能上的好處。

- 您要設定的屬性值不在<xref:System.Windows.DependencyObject>或上。 <xref:System.Windows.Freezable>

- 您所建立的資源字典將會編譯成 DLL，並封裝為應用程式的一部分，或在應用程式之間共用。

- 您正在建立自訂控制項的主題，並定義在主題中使用的資源。 在此情況下，您通常不想要動態資源參考查閱行為;您會想要有靜態資源參考行為，讓查閱可預測，並獨立于主題中。 使用動態資源參考，即使在執行時間之前，還是會將主題內的參考保持為未評估狀態。 而且有可能會在套用主題時，部分本機專案會重新定義您的主題嘗試參考的索引鍵，而本機元素會在查詢中的主題本身之前繼續進行。 如果發生這種情況，您的主題將無法如預期般運作。

- 您要使用資源來設定大量相依性屬性。 相依性屬性具有由屬性系統啟用的有效值快取，因此，如果您提供可在載入時評估之相依性屬性的值，則相依性屬性不需要檢查重新評估的運算式，而且可以傳回最後一個有效值。 這項技術可能會提升效能。

- 您想要變更所有取用者的基礎資源，或您想要使用[X:Shared 屬性](../xaml-services/xshared-attribute.md)為每個取用者維護不同的可寫入實例。

### <a name="static-resource-lookup-behavior"></a>靜態資源查閱行為

以下描述當屬性或專案參考靜態資源時，會自動發生的查閱程式：

01. 查閱程序會檢查設定屬性之項目所定義的資源字典內，是否有要求的索引鍵。

01. 查閱程式接著會將邏輯樹狀結構向上移至父元素和其資源字典。 此程式會繼續進行，直到達到根項目為止。

01. 已檢查應用程式資源。 應用程式資源是資源字典中的資源，由 WPF 應用程式<xref:System.Windows.Application>的物件所定義。

資源字典內的靜態資源參考必須參考資源參考之前已在語彙上定義的資源。 靜態資源參考無法解析向前參考。 基於這個理由，請設計您的資源字典結構，以便在每個個別資源字典的開頭或附近定義資源。

靜態資源查閱可以延伸到主題或系統資源，但只有在 XAML 載入器延遲要求時，才支援此查詢。 延遲是必要的，如此一來，當頁面載入時，執行時間主題才會適當地套用至應用程式。 不過，不建議只存在於主題中或做為系統資源的索引鍵的靜態資源參考，因為使用者會即時變更該主題，因此不會重新評估這類參考。 當您要求佈景主題或系統資源時，動態資源參考會更可靠。 但佈景主題項目本身要求另一個資源時則例外。 這些參考應該是靜態資源參考，原因如前所述。

如果找不到靜態資源參考，就會發生例外狀況的情況。 如果已延遲資源，則會在執行階段發生例外狀況。 如果未延遲資源，則會在載入時發生例外狀況。

## <a name="dynamic-resources"></a>動態資源

動態資源的最佳使用時機：

- 資源的值（包括系統資源）或其他可供使用者設定的資源，取決於執行時間之前不知道的條件。 例如，您可以建立 setter 值，參考、 <xref:System.Windows.SystemColors> <xref:System.Windows.SystemFonts>或<xref:System.Windows.SystemParameters>公開的系統屬性。 由於這些值最終是來自使用者和作業系統的執行階段環境，因此是真正動態的。 您也可能有會變更的應用程式層級佈景主題，其中的頁面層級資源存取也必須擷取該變更。

- 您正在建立或參考自訂控制項的主題樣式。

- 您想要<xref:System.Windows.ResourceDictionary>在應用程式存留期間調整的內容。

- 您有內含相互依存性的複雜資源結構，可能需要向前參考。 靜態資源參考不支援向前參考，但動態資源參考會支援它們，因為在執行時間之前，不需要評估資源，而向前參考則不是相關的概念。

- 您從編譯或工作集的觀點來參考的資源很大，而且當頁面載入時，資源可能不會立即使用。 靜態資源參考一律會在頁面載入時從 XAML 載入。 不過，動態資源參考在使用之前不會載入。

- 您正在建立一個樣式，其中 setter 值可能來自其他會受到主題或其他使用者設定影響的值。

- 您要將資源套用至在應用程式存留期間可能會在邏輯樹狀結構中重設父代的元素。 變更父代也可能會變更資源查閱範圍，因此如果您想要根據新範圍重新評估重設父代項目的資源，請一律使用動態資源參考。

### <a name="dynamic-resource-lookup-behavior"></a>動態資源查閱行為

如果您呼叫<xref:System.Windows.FrameworkElement.FindResource%2A>或<xref:System.Windows.FrameworkElement.SetResourceReference%2A>，動態資源參考的資源查閱行為會與您程式碼中的查閱行為類似：

01. Lookup 會在設定屬性的元素所定義的資源字典中，檢查所要求的索引鍵：

    - 如果元素定義<xref:System.Windows.FrameworkElement.Style%2A>屬性， <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName>則專案的會核取其<xref:System.Windows.Style.Resources>字典。

    - 如果元素定義<xref:System.Windows.Controls.Control.Template%2A>屬性，則會檢查<xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName>專案的字典。

01. 查閱會將邏輯樹狀結構向上移至父元素和其資源字典。 此程式會繼續進行，直到達到根項目為止。

01. 已檢查應用程式資源。 應用程式資源是資源字典中的資源，由 WPF 應用程式<xref:System.Windows.Application>的物件所定義。

01. 針對目前作用中的主題，會檢查主題資源字典。 如果佈景主題在執行階段變更，則會重新評估其值。

01. 檢查系統資源。

例外狀況行為 (如果有的話) 則有所不同：

- 如果資源是由<xref:System.Windows.FrameworkElement.FindResource%2A>呼叫所要求，而且找不到，則會擲回例外狀況。

- 如果資源是由<xref:System.Windows.FrameworkElement.TryFindResource%2A>呼叫所要求，而且找不到，則不會擲回任何例外狀況，且`null`傳回的值為。 如果要設定的屬性不接受`null`，則根據所設定的個別屬性，仍然可能會擲回更深入的例外狀況。

- 如果資源是由 XAML 中的動態資源參考所要求，而且找不到，則行為取決於一般屬性系統。 一般行為就如同資源所在的層級上沒有發生屬性設定作業一樣。 比方說，如果您嘗試使用無法評估的資源來設定個別按鈕元素的背景，則沒有任何值設定結果，但有效值仍然可以來自屬性系統和值優先順序的其他參與者。 例如，背景值仍然可能來自本機定義的按鈕樣式或主題樣式。 對於未由主題樣式定義的屬性，失敗資源評估之後的有效值可能來自屬性中繼資料中的預設值。

### <a name="restrictions"></a>限制

動態資源參考有一些值得注意的限制。 至少必須有下列其中一項條件成立：

- 要設定的屬性必須是<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>上的屬性。 該屬性必須由所支援<xref:System.Windows.DependencyProperty>。

- 參考適用于中的值`StyleSetter`。

- 要設定的屬性必須是上的屬性， <xref:System.Windows.Freezable>它是以<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>屬性的值或<xref:System.Windows.Setter>值的形式提供。

因為所設定的屬性必須是<xref:System.Windows.DependencyProperty>或<xref:System.Windows.Freezable>屬性，所以大部分的屬性變更都可以傳播至 UI，因為屬性系統會通知屬性變更（變更的動態資源值）。 大部分的控制項都包含邏輯，會在<xref:System.Windows.DependencyProperty>變更時強制控制項的另一個版面配置，而該屬性可能會影響版面配置。 不過，並非所有具有[DynamicResource 標記延伸](../../framework/wpf/advanced/dynamicresource-markup-extension.md)作為其值的屬性，都保證會在 UI 中提供即時更新。 該功能仍然可能因屬性而異，並取決於擁有屬性的類型，或甚至是應用程式的邏輯結構。

## <a name="styles-datatemplates-and-implicit-keys"></a>樣式、DataTemplates 和隱含索引鍵

雖然中的<xref:System.Windows.ResourceDictionary>所有專案都必須有索引鍵，但這並不表示所有資源都必須`x:Key`具有明確的。 有幾種物件類型會在定義為資源時支援隱含索引鍵，其中索引鍵值會繫結至另一個屬性的值。 這種類型的索引鍵稱為隱含索引鍵，而`x:Key`屬性則是明確的索引鍵。 您可以藉由指定明確索引鍵，來覆寫任何隱含索引鍵。

當您定義時，資源的其中一個重要<xref:System.Windows.Style>案例是。 事實上，幾乎一律<xref:System.Windows.Style>會定義為資源字典中的專案，因為樣式原本就是要重複使用。 如需樣式的詳細資訊，請參閱設定樣式[和範本](styles-templates-overview.md)。

控制項的樣式可以透過隱含索引鍵來建立及參考。 定義預設控制項外觀的佈景主題樣式會依賴此隱含索引鍵。 從要求它的觀點來看，隱含索引鍵是<xref:System.Type>控制項本身的。 從定義資源的觀點來看，隱含索引鍵是<xref:System.Windows.Style.TargetType%2A>樣式的。 因此，如果您要建立自訂控制項的主題，或建立與現有主題樣式互動的樣式，就不需要為該指定[x：Key](../xaml-services/xkey-directive.md)指示<xref:System.Windows.Style>詞。 此外，如果您想要使用佈景主題樣式，則完全不需要指定任何樣式。 例如，下列樣式定義的運作方式，雖然<xref:System.Windows.Style>資源似乎沒有索引鍵：

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

該樣式的確有一個索引鍵：隱含索引鍵`typeof(System.Windows.Controls.Button)`。 在標記中，您可以將<xref:System.Windows.Style.TargetType%2A>直接指定為類型名稱（或者，您可以選擇性地使用[{x:Type...}](../xaml-services/xtype-markup-extension.md) 傳回<xref:System.Type>。

透過 WPF 使用的預設主題樣式機制，該樣式會套用為頁面<xref:System.Windows.Controls.Button>上的執行時間樣式，即使<xref:System.Windows.Controls.Button>本身不會嘗試指定其<xref:System.Windows.FrameworkElement.Style%2A>屬性或樣式的特定資源參考也一樣。 您在頁面中所定義的樣式，會與主題字典樣式所擁有的相同索引鍵，在查閱序列中找到。 您可以只指定`<Button>Hello</Button>`頁面中的任何位置，而您使用<xref:System.Windows.Style.TargetType%2A>定義的樣式`Button`會套用至該按鈕。 如果您想要的話，仍然可以使用與標記相同的型別值<xref:System.Windows.Style.TargetType%2A>來明確地為樣式索引鍵，但這是選擇性的。

如果<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>為，則`true`樣式的隱含索引鍵不適用於控制項。 （也請注意<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> ，可能會設定為控制項類別的原生行為的一部分，而不是明確地在控制項的實例上）。此外，為了支援衍生類別案例的隱含索引鍵，控制項必須覆寫<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> （WPF 中提供的所有現有控制項都包含此覆寫）。 如需樣式、主題和控制項設計的詳細資訊，請參閱[設計可設定樣式控制項的方針](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md)。

<xref:System.Windows.DataTemplate>也有隱含的索引鍵。 的隱含索引鍵<xref:System.Windows.DataTemplate>是<xref:System.Windows.DataTemplate.DataType%2A>屬性值。 <xref:System.Windows.DataTemplate.DataType%2A>也可以指定為類型的名稱，而不是明確地使用[{x:Type...}](../xaml-services/xtype-markup-extension.md)。 如需詳細資訊，請參閱[資料範本化總覽](../../framework/wpf/data/data-templating-overview.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.ResourceDictionary>
- [應用程式資源](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [資源和程式碼](../../framework/wpf/advanced/resources-and-code.md)
- [定義和參考資源](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [應用程式管理總覽](../../framework/wpf/app-development/application-management-overview.md)
- [x:Type 標記延伸](../xaml-services/xtype-markup-extension.md)
- [StaticResource 標記延伸](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [DynamicResource 標記延伸](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
