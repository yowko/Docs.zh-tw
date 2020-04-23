---
title: 定義 XAML 資源
description: 瞭解 WPF 中用於 .NET 核心的 XAML 資源。 瞭解 XAML 資源的類型,並瞭解如何定義 XAML 資源。
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
# <a name="overview-of-xaml-resources"></a>XAML 資源概述

資源是可在應用中不同位置重複使用的物件。 資源的範例包括筆刷和樣式。 本概述介紹如何在可擴展應用程式標記語言 (XAML) 中使用資源。 您還可以使用代碼創建和訪問資源。

> [!NOTE]
> 本文中描述的 XAML 資源與通常添加到*應用的應用資源*(如內容、資料或嵌入檔)不同。

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>使用 XAML 資源

下面的範例將<xref:System.Windows.Media.SolidColorBrush>a 定義為頁面根元素上的資源。 然後,該範例引用資源,並用它來設置多個子元素的屬性,包括<xref:System.Windows.Shapes.Ellipse>.<xref:System.Windows.Controls.TextBlock>a<xref:System.Windows.Controls.Button>和 。

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

每個框架級元素(<xref:System.Windows.FrameworkElement><xref:System.Windows.FrameworkContentElement>或<xref:System.Windows.FrameworkElement.Resources%2A>) 都有<xref:System.Windows.ResourceDictionary>一個屬性 ,該屬性是包含已定義資源的類型。 可以定義任何元素(如<xref:System.Windows.Controls.Button>) 上的資源。 但是,資源最常在根元素上定義,該元素在<xref:System.Windows.Controls.Page>示例中。

資源字典中的每個資源都必須有唯一索引鍵。 在標記中定義資源時,可以通過[x:Key 指令](../xaml-services/xkey-directive.md)分配唯一鍵。 索引鍵通常是字串；不過，您也可以使用適當的標記延伸，將它設定為其他物件類型。 WPF 中的某些要素區域(尤其是樣式、元件資源和數據樣式)使用資源的非字串鍵。

可以將定義的資源與指定資源鍵名稱的資源標記擴展語法一起使用。 例如,將資源用作另一個元素上屬性的值。

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

在前面的範例中,當 XAML 載入`{StaticResource MyBrush}`程式處理<xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Controls.Button>的值 時,資源查<xref:System.Windows.Controls.Button>找邏輯首先檢查 元素的資源字典。 如果沒有<xref:System.Windows.Controls.Button>資源`MyBrush`鍵的定義(在此範例中沒有;其資源集合為空),則下一個尋找將檢查的<xref:System.Windows.Controls.Button>父元素, 該元素<xref:System.Windows.Controls.Page>為 。 如果在<xref:System.Windows.Controls.Page>根元素上定義資源,則的邏輯<xref:System.Windows.Controls.Page>樹中的所有元素都可以訪問它。 您可以重用同一資源來設置接受資源表示的相同類型的任何屬性的值。 在前面`MyBrush`的範例中,同一<xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Button><xref:System.Windows.Shapes.Shape.Fill%2A>資源設定兩個不同的屬性:的和<xref:System.Windows.Shapes.Rectangle>。

## <a name="static-and-dynamic-resources"></a>靜態和動態資源

可以將資源引用為靜態或動態。 引用是透過使用[靜態資源標記擴展](../../framework/wpf/advanced/staticresource-markup-extension.md)或[動態資源標記擴展](../../framework/wpf/advanced/dynamicresource-markup-extension.md)創建的。 標記延伸是一種 XAML 功能,允許您透過讓標記擴展處理屬性字串並將物件返回到 XAML 載入程式來指定物件引用。 有關標記延伸行為的詳細資訊,請參閱[標籤擴展和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。

使用標記延伸時,通常以字串形式提供由該特定標記擴展處理的一個或多個參數。 [靜態資源標記擴展](../../framework/wpf/advanced/staticresource-markup-extension.md)通過查找所有可用資源字典中該鍵的值來處理密鑰。 處理發生在載入期間,即載入過程需要分配屬性值時。 [動態資源標記擴展](../../framework/wpf/advanced/dynamicresource-markup-extension.md)通過創建表達式處理鍵,該運算式在應用運行之前保持未計算狀態,此時將計算運算式並提供值。

當您參考資源時，下列考量可能會影響您使用靜態資源參考或動態資源參考：

- 在確定如何為應用建立資源的總體設計時(每頁、應用中、鬆散 XAML 或僅資源程式集中),請考慮以下事項:

- 應用的功能。 更新資源是應用需求的即時部分嗎?
- 該資源參考型別的相關查閱行為。
- 特定屬性或資源類型，以及這些類型的原生行為。

## <a name="static-resources"></a>靜態資源

靜態資源參考最適用於下列情況：

- 應用設計將其大部分資源集中到頁面或應用程式級資源字典中。 靜態資源引用不會根據運行時行為(如重新載入頁面)重新評估。 因此,在不需要基於您的資源和應用設計時,避免大量動態資源引用,可能會帶來一些性能優勢。

- 正在設置不在<xref:System.Windows.DependencyObject>或上的屬性的值。 <xref:System.Windows.Freezable>

- 您正在創建一個資源字典,該字典將編譯到 DLL 中,並打包為應用的一部分或在應用之間共用。

- 您正在為自訂控制件建立主題,並定義主題中使用的資源。 在這種情況下,您通常不希望動態資源引用查找行為;因此,您不希望出現動態資源引用查找行為。相反,您希望靜態資源引用行為,以便查找是可預測和自包含的主題。 使用動態資源引用時,即使主題中的引用在運行時之前都處於未計算。 應用主題時,一些局部元素可能會重新定義主題嘗試引用的鍵,並且本地元素將落在查找中的主題本身之前。 如果發生這種情況,您的主題將不按預期進行。

- 您正在使用資源來設置大量依賴項屬性。 依賴項屬性具有屬性系統啟用的有效值緩存,因此,如果為可在載入時計算的依賴項屬性提供值,則依賴項屬性不必檢查重新評估的表達式,並可以返回最後一個有效值。 這項技術可能會提升效能。

- 您希望更改所有使用者的基礎資源,或者希望使用[x:共用屬性](../xaml-services/xshared-attribute.md)為每個使用者維護單獨的可寫實例。

### <a name="static-resource-lookup-behavior"></a>靜態資源查閱行為

下面描述了當屬性或元素引用靜態資源時自動發生的查找過程:

01. 查閱程序會檢查設定屬性之項目所定義的資源字典內，是否有要求的索引鍵。

01. 然後,查找過程向上遍歷邏輯樹到父元素及其資源字典。 此過程將繼續,直到到達根元素。

01. 檢查應用資源。 應用資源是資源字典中由 WPF<xref:System.Windows.Application>應用 的物件定義的資源資源。

資源字典內的靜態資源參考必須參考資源參考之前已在語彙上定義的資源。 靜態資源參考無法解析向前參考。 因此,請設計資源字典結構,以便在每個資源字典的開頭或附近定義資源。

靜態資源查找可以擴展到主題或系統資源,但僅支援此查找,因為 XAML 載入程式延遲請求。 延遲是必需的,以便頁面載入時執行時主題正確應用於應用。 但是,不建議對已知僅存在於主題或系統資源中的鍵進行靜態資源引用,因為如果使用者即時更改主題,則不會重新評估此類引用。 當您要求佈景主題或系統資源時，動態資源參考會更可靠。 但佈景主題項目本身要求另一個資源時則例外。 這些參考應該是靜態資源參考，原因如前所述。

如果未找到靜態資源引用,則異常行為會有所不同。 如果已延遲資源，則會在執行階段發生例外狀況。 如果未延遲資源，則會在載入時發生例外狀況。

## <a name="dynamic-resources"></a>動態資源

動態資源在:

- 資源的值(包括系統資源或其他使用者可設置的資源)取決於在運行時之前不知道的條件。 例如,您可以建立 setter 值,這些值引用由<xref:System.Windows.SystemColors><xref:System.Windows.SystemFonts>或公開的<xref:System.Windows.SystemParameters>系統屬性 。 由於這些值最終是來自使用者和作業系統的執行階段環境，因此是真正動態的。 您也可能有會變更的應用程式層級佈景主題，其中的頁面層級資源存取也必須擷取該變更。

- 您正在為自訂控制件建立或引用主題樣式。

- 您打算在應用生存期內調整<xref:System.Windows.ResourceDictionary>的內容。

- 您有內含相互依存性的複雜資源結構，可能需要向前參考。 靜態資源引用不支援轉發引用,但動態資源引用確實支援它們,因為在運行時之前不需要計算資源,因此轉發引用不是相關概念。

- 從編譯或工作集的角度來看,您引用的是較大的資源,並且在頁面載入時可能不會立即使用該資源。 當頁面載入時,靜態資源引用始終從 XAML 載入。 但是,動態資源引用在使用之前不會載入。

- 您正在創建一種樣式,其中 setter 值可能來自受主題或其他使用者設置影響的其他值。

- 正在將資源應用於在應用生存期內可能重新父化邏輯樹中的元素。 變更父代也可能會變更資源查閱範圍，因此如果您想要根據新範圍重新評估重設父代項目的資源，請一律使用動態資源參考。

### <a name="dynamic-resource-lookup-behavior"></a>動態資源查閱行為

動態資源參考的資源尋找行為與程式碼中的尋找行為平行,如果呼叫<xref:System.Windows.FrameworkElement.FindResource%2A>或呼<xref:System.Windows.FrameworkElement.SetResourceReference%2A>叫 :

01. 尋找查詢設定屬性的元素定義的資源字典中請求的金鑰:

    - 如果元素定義屬性<xref:System.Windows.FrameworkElement.Style%2A>,則元素<xref:System.Windows.FrameworkElement.Style?displayProperty=fullName>的 字<xref:System.Windows.Style.Resources>典已 選中。

    - 如果元素定義屬性<xref:System.Windows.Controls.Control.Template%2A><xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName>, 則檢查元素的字典。

01. 查找將邏輯樹向上遍歷父元素及其資源字典。 此過程將繼續,直到到達根元素。

01. 檢查應用資源。 應用資源是資源字典中由 WPF<xref:System.Windows.Application>應用 的物件定義的資源資源。

01. 檢查主題資源字典以檢查當前活動的主題。 如果佈景主題在執行階段變更，則會重新評估其值。

01. 檢查系統資源。

例外狀況行為 (如果有的話) 則有所不同：

- 如果<xref:System.Windows.FrameworkElement.FindResource%2A>調用請求了資源,但未找到資源,則引發異常。

- 如果<xref:System.Windows.FrameworkElement.TryFindResource%2A>呼叫請求了資源,但未找到資源,則不會引發異常,傳回的`null`值為 。 如果正在設置的屬性不接受`null`,則仍可能引發更深的異常,具體取決於要設置的單個屬性。

- 如果 XAML 中的動態資源引用請求了資源,但未找到資源,則該行為取決於常規屬性系統。 一般行為就好像在資源所在的級別上沒有發生屬性設置操作一樣。 例如,如果您嘗試使用無法計算的資源在單個按鈕元素上設置背景,則沒有值設置結果,但有效值仍可能來自屬性系統和值優先順序中的其他參與者。 例如,背景值可能仍來自本地定義的按鈕樣式或主題樣式。 對於主題樣式未定義的屬性,失敗的資源計算后的有效值可能來自屬性元數據中的預設值。

### <a name="restrictions"></a>限制

動態資源參考有一些值得注意的限制。 以下條件之一必須至少為 true:

- 正在設置的屬性必須是<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>上的屬性。 該屬性必須由的支援<xref:System.Windows.DependencyProperty>。

- 引用是針對中的值。 `StyleSetter`

- 正在<xref:System.Windows.Freezable>設定的屬性必須是作為<xref:System.Windows.FrameworkElement><xref:System.Windows.FrameworkContentElement>或 屬性的值提供的<xref:System.Windows.Setter>屬性或值。

由於正在設置的屬性必須是<xref:System.Windows.DependencyProperty><xref:System.Windows.Freezable>或 屬性,因此大多數屬性更改可以傳播到 UI,因為屬性系統確認屬性更改(更改的動態資源值)。 大多數控件都包含邏輯,如果更改和該屬性可能會影響佈局,<xref:System.Windows.DependencyProperty>則該邏輯將強制控件的另一個佈局。 但是,並非所有具有[動態資源標記擴展](../../framework/wpf/advanced/dynamicresource-markup-extension.md)的屬性(其值)都保證在 UI 中提供即時更新。 該功能可能仍因屬性而異,具體取決於擁有屬性的類型,甚至應用的邏輯結構。

## <a name="styles-datatemplates-and-implicit-keys"></a>樣式、資料範本和隱式鍵

儘管 中<xref:System.Windows.ResourceDictionary>的所有 項都必須具有鍵,但這並不意味著所有資源都必須`x:Key`具有顯式 。 有幾種物件類型會在定義為資源時支援隱含索引鍵，其中索引鍵值會繫結至另一個屬性的值。 這種類型的鍵稱為隱式鍵,而`x:Key`屬性是顯式鍵。 您可以藉由指定明確索引鍵，來覆寫任何隱含索引鍵。

資源的一個重要機制是定義<xref:System.Windows.Style>時 。 事實上,在資源<xref:System.Windows.Style>字典中,幾乎總是定義為條目,因為樣式本質上是要重用的。 有關樣式的詳細資訊,請參閱[樣式和範本](styles-templates-overview.md)化。

控制項的樣式可以透過隱含索引鍵來建立及參考。 定義預設控制項外觀的佈景主題樣式會依賴此隱含索引鍵。 從請求的角度來看,隱式鍵是<xref:System.Type>控件本身。 從定義資源的角度來看,隱式鍵是<xref:System.Windows.Style.TargetType%2A>樣式的。 因此,如果要為自訂控制件建立主題或建立與現有主題樣式互動的樣式,則無需為此<xref:System.Windows.Style>指定[x:Key 指令](../xaml-services/xkey-directive.md)。 此外，如果您想要使用佈景主題樣式，則完全不需要指定任何樣式。 例如,以下樣式定義有效,即使<xref:System.Windows.Style>資源似乎沒有密鑰:

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

這種風格確實有一個鍵:隱式鍵`typeof(System.Windows.Controls.Button)`。 在標記中,可以直接指定類型<xref:System.Windows.Style.TargetType%2A>名稱(也可以選擇使用[{x:Type...]](../xaml-services/xtype-markup-extension.md) 返回<xref:System.Type>。

通過 WPF 使用的預設主題樣式機制,該樣式將應用於頁面上的<xref:System.Windows.Controls.Button>運行時<xref:System.Windows.Controls.Button>樣式,即使<xref:System.Windows.FrameworkElement.Style%2A>本身不嘗試指定其 屬性或對該樣式的特定資源引用。 在頁面中定義的樣式在查找序列中早於主題字典樣式中找到,使用主題詞典樣式具有的相同鍵。 您可以指定`<Button>Hello</Button>`頁面中的任意位置,並且您<xref:System.Windows.Style.TargetType%2A>定義的樣式`Button`將應用於該按鈕。 如果需要,您仍然可以顯式鍵入樣式,其類型值與<xref:System.Windows.Style.TargetType%2A>標記中的明確性相同,但這是可選的。

如果<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>`true`是 ,則樣式的隱式鍵不適用於控件。 (另請注意,<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>可能設置為控制項類別的本機行為的一部分,而不是在控制項的實例上顯式設置。此外,為了支援派生類方案的隱式鍵,控件必須重寫<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>(作為 WPF 的一部分提供的所有現有控制項都包括此覆蓋)。 有關樣式、主題和控制設計的詳細資訊,請參閱[設計可手寫控制件的指南](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md)。

<xref:System.Windows.DataTemplate>也有一個隱式鍵。 的隱式鍵<xref:System.Windows.DataTemplate><xref:System.Windows.DataTemplate.DataType%2A>是 屬性值。 <xref:System.Windows.DataTemplate.DataType%2A>也可以指定為類型的名稱,而不是顯式使用[[x:Type...]](../xaml-services/xtype-markup-extension.md)。 有關詳細資訊,請參閱[資料樣本概述](../../framework/wpf/data/data-templating-overview.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.ResourceDictionary>
- [應用程式資源](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [資源與代碼](../../framework/wpf/advanced/resources-and-code.md)
- [定義及參考資源](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [應用程式管理概述](../../framework/wpf/app-development/application-management-overview.md)
- [x:鍵入標記延伸](../xaml-services/xtype-markup-extension.md)
- [靜態資源標記延伸](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [動態資源標記延伸](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
