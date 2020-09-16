---
title: 定義 XAML 資源
description: 瞭解 WPF 中適用于 .NET Core 的 XAML 資源。 瞭解 XAML 資源的類型，並瞭解如何定義 XAML 資源。
author: adegeo
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: 2393b3b2fabd0e900a99bf950d30e1744c754da5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541821"
---
# <a name="overview-of-xaml-resources"></a>XAML 資源總覽

資源是可在應用程式中的不同位置重複使用的物件。 資源的範例包括筆刷和樣式。 本總覽說明如何使用 Extensible Application Markup Language (XAML) 中的資源。 您也可以使用程式碼來建立及存取資源。

> [!NOTE]
> 本文所述的 XAML 資源不同于通常會新增至應用程式之檔案的 *應用程式資源* ，例如內容、資料或內嵌檔案。

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>使用 XAML 中的資源

下列範例會將定義 <xref:System.Windows.Media.SolidColorBrush> 為頁面根項目的資源。 然後，此範例會參考資源，並使用它來設定數個子專案的屬性，包括 <xref:System.Windows.Shapes.Ellipse> 、 <xref:System.Windows.Controls.TextBlock> 和 <xref:System.Windows.Controls.Button> 。

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

 (或) 的每個架構層級專案 <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> 都有一個 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性，也就是 <xref:System.Windows.ResourceDictionary> 包含已定義資源的型別。 您可以在任何元素上定義資源，例如 <xref:System.Windows.Controls.Button> 。 不過，資源最常定義于根項目， <xref:System.Windows.Controls.Page> 例如範例中。

資源字典中的每個資源都必須有唯一索引鍵。 當您在標記中定義資源時，您可以透過 [x：Key](../xaml-services/xkey-directive.md)指示詞指派唯一索引鍵。 索引鍵通常是字串；不過，您也可以使用適當的標記延伸，將它設定為其他物件類型。 WPF 中的某些功能區域會使用資源的非字串索引鍵，特別是針對樣式、元件資源和資料樣式。

您可以使用已定義的資源搭配資源標記延伸語法，以指定資源的索引鍵名稱。 例如，使用資源做為另一個元素上的屬性值。

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

在上述範例中，當 XAML 載入器處理 `{StaticResource MyBrush}` 上的屬性值時， <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> 資源查閱邏輯會先檢查元素的資源字典 <xref:System.Windows.Controls.Button> 。 如果 <xref:System.Windows.Controls.Button> 沒有資源金鑰的定義 `MyBrush` (在該範例中，其資源集合為空白) ，則查閱會接著檢查的父元素 <xref:System.Windows.Controls.Button> ，也就是 <xref:System.Windows.Controls.Page> 。 如果您在根項目上定義資源，則的 <xref:System.Windows.Controls.Page> 邏輯樹狀結構中的所有元素都 <xref:System.Windows.Controls.Page> 可以存取它。 而且，您可以重複使用相同的資源，來設定接受資源所代表之相同類型的任何屬性值。 在上述範例中，相同的 `MyBrush` 資源會設定兩個不同的屬性：的 <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> 、和的 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> 。

## <a name="static-and-dynamic-resources"></a>靜態和動態資源

資源可以參考為靜態或動態。 您可以使用 [StaticResource 標記延伸](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) 或 [DynamicResource 標記延伸](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension)來建立參考。 標記延伸是一種 XAML 功能，可讓您藉由讓標記延伸處理屬性字串並將物件傳回至 XAML 載入器，來指定物件參考。 如需標記延伸行為的詳細資訊，請參閱 [標記延伸和 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)。

當您使用標記延伸時，通常會提供一或多個由該特定標記延伸所處理之字串格式的參數。 [StaticResource 標記延伸](/dotnet/desktop/wpf/advanced/staticresource-markup-extension)會藉由在所有可用的資源字典中查閱該索引鍵的值來處理索引鍵。 處理會在載入期間進行，也就是載入進程需要指派屬性值時。 [DynamicResource 標記延伸](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension)會藉由建立運算式來處理索引鍵，而且在執行應用程式之前，該運算式會保持未評估狀態，此時會評估運算式並提供值。

當您參考資源時，下列考量可能會影響您使用靜態資源參考或動態資源參考：

- 當您決定如何為應用程式建立資源的整體設計 (每個頁面、應用程式中的鬆散 XAML 或僅限資源的元件) ，請考慮下列事項：

- 應用程式的功能。 是否正在更新應用程式需求的即時資源？
- 該資源參考型別的相關查閱行為。
- 特定屬性或資源類型，以及這些類型的原生行為。

## <a name="static-resources"></a>靜態資源

靜態資源參考最適用於下列情況：

- 您的應用程式設計會將其大部分的資源集中在頁面或應用層級的資源字典中。 靜態資源參考不會根據執行時間行為重新評估，例如重載頁面。 因此，在不需要以資源和應用程式設計為基礎時，避免大量動態資源參考時，可能會有一些效能優勢。

- 您正在設定不在或上的屬性值 <xref:System.Windows.DependencyObject> <xref:System.Windows.Freezable> 。

- 您要建立的資源字典將會編譯成 DLL，並封裝成應用程式的一部分，或在應用程式之間共用。

- 您要建立自訂控制項的主題，並定義在主題中使用的資源。 在此情況下，您通常不想要動態資源參考查閱行為;相反地，您會想要靜態資源參考行為，使查閱可預測且可在主題中自行包含。 使用動態資源參考時，即使在執行時間之前，仍會將主題中的參考保持未評估。 有可能在套用主題時，某些區域元素會重新定義您的主題嘗試參考的索引鍵，而本機元素則會在查詢中的主題本身之前。 如果發生這種情況，您的主題將不會如預期般運作。

- 您要使用資源來設定大量相依性屬性。 相依性屬性具有屬性系統啟用的有效值快取，因此，如果您提供可在載入時評估之相依性屬性的值，則相依性屬性不需要檢查重新評估的運算式，而且可以傳回最後一個有效值。 這項技術可能會提升效能。

- 您想要變更所有取用者的基礎資源，或想要使用 [X:Shared 屬性](../xaml-services/xshared-attribute.md)為每個取用者維護個別的可寫入實例。

### <a name="static-resource-lookup-behavior"></a>靜態資源查閱行為

以下描述當屬性或元素參考靜態資源時，會自動發生的查詢程式：

01. 查閱程序會檢查設定屬性之項目所定義的資源字典內，是否有要求的索引鍵。

01. 查閱進程接著會將邏輯樹狀結構向上移至父項目及其資源字典。 此程式會繼續進行，直到到達根項目為止。

01. 系統會檢查應用程式資源。 應用程式資源是資源字典中的資源，這些資源是由 <xref:System.Windows.Application> 您 WPF 應用程式的物件所定義。

資源字典內的靜態資源參考必須參考資源參考之前已在語彙上定義的資源。 靜態資源參考無法解析向前參考。 基於這個理由，請設計您的資源字典結構，讓資源在每個個別資源字典的開頭或附近定義。

靜態資源查閱可延伸至主題或系統資源，但僅支援此查閱，因為 XAML 載入器會延遲要求。 延遲是必要的，因此頁面載入時的執行時間主題會正確套用至應用程式。 不過，對於已知只存在於主題或作為系統資源的索引鍵，其靜態資源參考不是建議的作法，因為如果使用者即時變更該主題，則不會重新評估這類參考。 當您要求佈景主題或系統資源時，動態資源參考會更可靠。 但佈景主題項目本身要求另一個資源時則例外。 這些參考應該是靜態資源參考，原因如前所述。

如果找不到靜態資源參考，則為例外狀況行為。 如果已延遲資源，則會在執行階段發生例外狀況。 如果未延遲資源，則會在載入時發生例外狀況。

## <a name="dynamic-resources"></a>動態資源

動態資源的運作效果最好：

- 資源的值（包括系統資源）或其他使用者可設定的資源，取決於在執行時間之前不知道的狀況。 例如，您可以建立 setter 值來參考、或所公開的系統屬性 <xref:System.Windows.SystemColors> <xref:System.Windows.SystemFonts> <xref:System.Windows.SystemParameters> 。 由於這些值最終是來自使用者和作業系統的執行階段環境，因此是真正動態的。 您也可能有會變更的應用程式層級佈景主題，其中的頁面層級資源存取也必須擷取該變更。

- 您正在建立或參考自訂控制項的主題樣式。

- 您想要在 <xref:System.Windows.ResourceDictionary> 應用程式存留期間調整的內容。

- 您有內含相互依存性的複雜資源結構，可能需要向前參考。 靜態資源參考不支援向前參考，但動態資源參考支援它們，因為在執行時間之前不需要評估資源，而向前參考則不是相關的概念。

- 您所參考的資源很大，從編譯或工作集的角度來看，當頁面載入時，可能無法立即使用資源。 當頁面載入時，靜態資源參考一律會從 XAML 載入。 不過，動態資源參考在使用之前都不會載入。

- 您正在建立一個樣式，其中 setter 值可能來自其他受主題或其他使用者設定影響的值。

- 您要將資源套用至應用程式存留期間可能在邏輯樹狀結構中重設父元素的專案。 變更父代也可能會變更資源查閱範圍，因此如果您想要根據新範圍重新評估重設父代項目的資源，請一律使用動態資源參考。

### <a name="dynamic-resource-lookup-behavior"></a>動態資源查閱行為

如果您呼叫或，動態資源參考的資源查閱行為會使程式碼中的查閱行為更平行 <xref:System.Windows.FrameworkElement.FindResource%2A> <xref:System.Windows.FrameworkElement.SetResourceReference%2A> ：

01. 查閱會在設定屬性的專案所定義的資源字典中，檢查所要求的索引鍵：

    - 如果元素定義了屬性，則專案的會 <xref:System.Windows.FrameworkElement.Style%2A> <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> 核取其 <xref:System.Windows.Style.Resources> 字典。

    - 如果元素定義了 <xref:System.Windows.Controls.Control.Template%2A> 屬性，則 <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> 會檢查元素的字典。

01. 查閱會將邏輯樹狀結構向上移至父元素及其資源字典。 此程式會繼續進行，直到到達根項目為止。

01. 系統會檢查應用程式資源。 應用程式資源是資源字典中的資源，這些資源是由 <xref:System.Windows.Application> WPF 應用程式的物件所定義。

01. 主題資源字典會檢查目前作用中的主題。 如果佈景主題在執行階段變更，則會重新評估其值。

01. 檢查系統資源。

例外狀況行為 (如果有的話) 則有所不同：

- 如果呼叫要求資源，且找不到資源，則會擲回 <xref:System.Windows.FrameworkElement.FindResource%2A> 例外狀況。

- 如果呼叫要求資源但找不到資源 <xref:System.Windows.FrameworkElement.TryFindResource%2A> ，則不會擲回例外狀況，且傳回的值為 `null` 。 如果設定的屬性不接受 `null` ，則根據設定的個別屬性，仍可能會擲回更深層的例外狀況。

- 如果 XAML 中的動態資源參考要求了資源，而且找不到資源，則行為會視一般屬性系統而定。 一般行為就像資源所在層級沒有發生屬性設定作業一樣。 比方說，如果您嘗試使用無法評估的資源來設定個別按鈕元素的背景，則沒有值設定結果，但有效值仍可來自屬性系統中的其他參與者和值優先順序。 例如，背景值可能仍來自本機定義的按鈕樣式或主題樣式。 針對不是由主題樣式定義的屬性，失敗資源評估之後的有效值可能來自屬性中繼資料中的預設值。

### <a name="restrictions"></a>限制

動態資源參考有一些值得注意的限制。 至少必須符合下列其中一個條件：

- 要設定的屬性必須是或上的屬性 <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> 。 該屬性必須由支援 <xref:System.Windows.DependencyProperty> 。

- 參考是針對中的值 `StyleSetter` 。

- 要設定的屬性必須是的屬性，其 <xref:System.Windows.Freezable> 提供為 <xref:System.Windows.FrameworkElement> 或屬性的值 <xref:System.Windows.FrameworkContentElement> ，或是 <xref:System.Windows.Setter> 值。

因為所設定的屬性必須是 <xref:System.Windows.DependencyProperty> 或 <xref:System.Windows.Freezable> 屬性，所以大部分的屬性變更都可以傳播至 UI，因為屬性系統會 (變更的動態資源值) 屬性變更。 大部分的控制項都包含邏輯，會在變更時強制控制項的另一個配置 <xref:System.Windows.DependencyProperty> ，且該屬性可能會影響版面配置。 不過，並非所有具有 [DynamicResource 標記延伸](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension) 的屬性作為其值，因此保證可在 UI 中提供即時更新。 這項功能仍然可能會根據屬性而有所不同，也會根據擁有屬性的類型，或甚至是應用程式的邏輯結構而有所不同。

## <a name="styles-datatemplates-and-implicit-keys"></a>樣式、DataTemplates 和隱含索引鍵

雖然 a 中的所有專案都 <xref:System.Windows.ResourceDictionary> 必須有索引鍵，但這並不表示所有資源都必須有明確的 `x:Key` 。 有幾種物件類型會在定義為資源時支援隱含索引鍵，其中索引鍵值會繫結至另一個屬性的值。 這種類型的索引鍵稱為隱含索引鍵，而 `x:Key` 屬性則是明確的索引鍵。 您可以藉由指定明確索引鍵，來覆寫任何隱含索引鍵。

資源的其中一個重要案例是當您定義時 <xref:System.Windows.Style> 。 事實上， <xref:System.Windows.Style> 幾乎一律會在資源字典中定義為專案，因為樣式本質上是為了重複使用而設計。 如需樣式的詳細資訊，請參閱設定樣式 [和範本](styles-templates-overview.md)。

控制項的樣式可以透過隱含索引鍵來建立及參考。 定義預設控制項外觀的佈景主題樣式會依賴此隱含索引鍵。 從要求的觀點來看，隱含索引鍵是 <xref:System.Type> 控制項本身的。 從定義資源的觀點來看，隱含索引鍵是 <xref:System.Windows.Style.TargetType%2A> 樣式的。 因此，如果您要建立自訂控制項的主題，或建立與現有主題樣式互動的樣式，則不需要為該控制項指定 [x：Key](../xaml-services/xkey-directive.md) 指示詞 <xref:System.Windows.Style> 。 此外，如果您想要使用佈景主題樣式，則完全不需要指定任何樣式。 比方說，下列樣式定義可以運作，即使 <xref:System.Windows.Style> 資源看起來沒有索引鍵也一樣：

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

該樣式的確有一個索引鍵：隱含索引鍵 `typeof(System.Windows.Controls.Button)` 。 在標記中，您可以 <xref:System.Windows.Style.TargetType%2A> 直接指定 (類型名稱，也可以選擇性地使用 [{x:Type...}](../xaml-services/xtype-markup-extension.md) 傳回 <xref:System.Type> 。

透過 WPF 所使用的預設主題樣式機制，該樣式會套用為 <xref:System.Windows.Controls.Button> 頁面上的執行時間樣式，即使 <xref:System.Windows.Controls.Button> 本身不會嘗試指定其 <xref:System.Windows.FrameworkElement.Style%2A> 屬性或樣式的特定資源參考也一樣。 您在頁面中所定義的樣式，在查閱序列中會比主題字典樣式所擁有的相同索引鍵，在查閱序列中找到。 您可以只指定 `<Button>Hello</Button>` 頁面中的任何位置，而您使用定義的 <xref:System.Windows.Style.TargetType%2A> 樣式 `Button` 會套用至該按鈕。 如果您想要的話，仍然可以使用與標記中的相同類型值來明確地標示樣式 <xref:System.Windows.Style.TargetType%2A> ，但這是選擇性的。

若為，則不會在控制項上套用樣式的隱含索引鍵 <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> `true` 。  (也請注意， <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> 可能會在控制項類別的原生行為中設定，而不是在控制項的實例上明確地設定。 ) 此外，為了支援衍生類別情節的隱含索引鍵，控制項必須覆寫 <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (WPF 中提供的所有現有控制項包含此覆寫) 。 如需樣式、主題和控制項設計的詳細資訊，請參閱 [設計可設定樣式控制項的指導方針](/dotnet/desktop/wpf/controls/guidelines-for-designing-stylable-controls)。

<xref:System.Windows.DataTemplate> 也有隱含的索引鍵。 的隱含索引鍵 <xref:System.Windows.DataTemplate> 是 <xref:System.Windows.DataTemplate.DataType%2A> 屬性值。 <xref:System.Windows.DataTemplate.DataType%2A> 也可以指定為類型的名稱，而非明確地使用 [{x:Type...}](../xaml-services/xtype-markup-extension.md)。 如需詳細資訊，請參閱 [資料範本化總覽](/dotnet/desktop/wpf/data/data-templating-overview)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.ResourceDictionary>
- [應用程式資源](/dotnet/desktop/wpf/advanced/optimizing-performance-application-resources)
- [資源和程式碼](/dotnet/desktop/wpf/advanced/resources-and-code)
- [定義和參考資源](/dotnet/desktop/wpf/advanced/how-to-define-and-reference-a-resource)
- [應用程式管理總覽](/dotnet/desktop/wpf/app-development/application-management-overview)
- [x:Type 標記延伸](../xaml-services/xtype-markup-extension.md)
- [StaticResource 標記延伸](/dotnet/desktop/wpf/advanced/staticresource-markup-extension)
- [DynamicResource 標記延伸](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension)
