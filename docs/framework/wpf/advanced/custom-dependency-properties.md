---
title: 自訂相依性屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- implementing [WPF], wrappers
- registering properties [WPF]
- properties [WPF], metadata
- metadata [WPF], for properties
- custom dependency properties [WPF]
- properties [WPF], registering
- wrappers [WPF], implementing
- dependency properties [WPF], custom
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
ms.openlocfilehash: 00596911cf603ae9615eb64d0aedefe90c2520bc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458998"
---
# <a name="custom-dependency-properties"></a>自訂相依性屬性

本主題會說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式開發人員和元件作者可能想要建立自訂相依性屬性的原因，並說明實作步驟以及某些可以改善屬性的效能、可用性或多功能的實作選項。

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prerequisites

本主題假設您已從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)主題。 為了解本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>什麼是相依性屬性？

您可以啟用通用語言執行平臺（CLR）屬性，以支援樣式、資料系結、繼承、動畫和預設值，方法是將其實作為相依性屬性。 相依性屬性是藉由呼叫 <xref:System.Windows.DependencyProperty.Register%2A> 方法（或 <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>），並由 <xref:System.Windows.DependencyProperty> 識別碼欄位支援的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統註冊的屬性。 相依性屬性只能由 <xref:System.Windows.DependencyObject> 類型使用，但 <xref:System.Windows.DependencyObject> 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別階層中相當高，因此 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中提供的大部分類別都可以支援相依性屬性。 如需相依性屬性的詳細資訊，以及此 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 中描述它們所使用的一些術語和慣例，請參閱[相依性屬性概觀](dependency-properties-overview.md)。

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>相依性屬性範例

在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別上實作為相依性屬性的範例包括 <xref:System.Windows.Controls.Control.Background%2A> 屬性、<xref:System.Windows.FrameworkElement.Width%2A> 屬性和 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性等許多其他專案。 類別所公開的每個相依性屬性都有一個類型的對應公用靜態欄位，<xref:System.Windows.DependencyProperty> 公開于相同的類別上。 這是相依性屬性的識別碼。 識別碼依慣例命名︰相依性屬性的名稱後綴字串 `Property`。 例如，<xref:System.Windows.Controls.Control.Background%2A> 屬性的對應 <xref:System.Windows.DependencyProperty> 識別碼欄位是 <xref:System.Windows.Controls.Control.BackgroundProperty>。 識別碼會儲存已註冊之相依性屬性的相關資訊，稍後會使用此識別碼進行相依性屬性的其他作業，例如呼叫 <xref:System.Windows.DependencyObject.SetValue%2A>。

如相依性[屬性總覽](dependency-properties-overview.md)中所述，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的所有相依性屬性（大部分的附加屬性除外）也是 CLR 屬性，因為「包裝函式」的執行。 因此，在程式碼中，您可以藉由呼叫 CLR 存取子來取得或設定相依性屬性，方法是以您使用其他 CLR 屬性的相同方式來定義包裝函式。 做為已建立相依性屬性的取用者，您通常不會使用 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A>的 <xref:System.Windows.DependencyObject> 方法，這是基礎屬性系統的連接點。 相反地，現有的 CLR 屬性的執行已經被呼叫 <xref:System.Windows.DependencyObject.GetValue%2A>，而且在屬性的 `get` 和 `set` 的包裝函式內，會適當使用 identifier 欄位來 <xref:System.Windows.DependencyObject.SetValue%2A>。 如果您要自行實作自訂的相依性屬性，則會以類似的方式定義包裝函式。

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>您應於何時實作相依性屬性？

當您在類別上執行屬性時，只要您的類別衍生自 <xref:System.Windows.DependencyObject>，就可以選擇使用 <xref:System.Windows.DependencyProperty> 識別碼來備份您的屬性，進而使其成為相依性屬性。 讓您的屬性成為相依性屬性並非絕對必要或合適，視案例需求而定。 有時候，支援有私用欄位的屬性，一般的技巧即已足夠。 但只要您希望屬性支援下列一或多項 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能，就應該將屬性實作為相依性屬性：

- 您希望屬性在樣式中是可設定的。 如需詳細資訊，請參閱 [設定樣式和範本](../controls/styling-and-templating.md)。

- 您希望屬性支援資料繫結。 如需資料繫結相依性屬性的詳細資訊，請參閱[繫結兩個控制項的屬性](../data/how-to-bind-the-properties-of-two-controls.md)。

- 您希望屬性可使用動態資源參考來設定。 如需詳細資訊，請參閱 [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。

- 您想要自動繼承項目樹狀結構父項目的屬性值。 在此情況下，請使用 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 方法進行註冊，即使您也建立了 CLR 存取的屬性包裝函式也一樣。 如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

- 您希望屬性可製成動畫。 如需詳細資訊，請參閱 [動畫概觀](../graphics-multimedia/animation-overview.md)。

- 當屬性系統、環境或使用者所採取的動作，或讀取和使用樣式變更了先前的屬性值時，您希望屬性系統能夠回報。 使用屬性中繼資料，您的屬性可以指定每次屬性系統判定屬性值變更時都會叫用回呼方法。 相關的概念是屬性值強制型轉。 如需詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)。

- 您想要使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程序也使用的已建立中繼資料慣例，例如報告變更屬性值是否應該需要配置系統重新撰寫項目的視覺效果。 或者您想要能夠使用中繼資料覆寫，以便衍生類別可以變更中繼資料型的特性，例如預設值。

- 您想要自訂控制項的屬性，以接收 Visual Studio WPF 設計工具支援，例如 [**屬性**] 視窗編輯。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。

當您檢查這些案例時，您也應該考慮是否能夠以覆寫現有相依性屬性中繼資料的方式完成您的案例，而不是實作全新的屬性。 中繼資料覆寫是否實際可行，取決於您的案例，以及該案例與現有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 相依性屬性和類別實作的類似程度。 如需覆寫現有屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>定義相依性屬性所使用的檢查清單

定義相依性屬性包含四個不同的概念。 這些概念不一定得是嚴苛的程序步驟，因為其中有些最後會結合為實作中的單一段程式碼︰

- (選擇性) 建立相依性屬性的屬性中繼資料。

- 向屬性系統登錄屬性名稱，指定擁有者類型和屬性值類型。 如經使用，也指定屬性中繼資料。

- 在擁有者類型上，將 <xref:System.Windows.DependencyProperty> 識別碼定義為 `public` `static` `readonly` 欄位。

- 定義 CLR "包裝函式" 屬性，其名稱符合相依性屬性的名稱。 執行 CLR 「包裝函式」屬性的 `get`，並 `set` 存取子來與支援它的相依性屬性連接。

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>向屬性系統登錄屬性

為使屬性成為相依性屬性，您必須將該屬性登錄到屬性系統維護的資料表中，並給它唯一識別碼用為後續屬性系統作業的限定詞。 這些作業可能是內部作業，或您自己的程式碼呼叫屬性系統 Api。 若要註冊屬性，請在類別主體中呼叫 <xref:System.Windows.DependencyProperty.Register%2A> 方法（在類別中，但在任何成員定義之外）。 [識別碼] 欄位也是由 <xref:System.Windows.DependencyProperty.Register%2A> 方法呼叫所提供，做為傳回值。 <xref:System.Windows.DependencyProperty.Register%2A> 呼叫是在其他成員定義以外完成的原因，是因為您使用此傳回值來指派和建立 `public` `static` `readonly` 欄位，做為類別的一部分 <xref:System.Windows.DependencyProperty> 類型。 此欄位會變成您相依性屬性的識別碼。

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>相依性屬性命名慣例

相依性屬性有已建立的命名慣例，除非例外情況，否則必須遵循。

相依性屬性本身會有基本名稱 "AquariumGraphic"，如下列範例所示，它會指定為 <xref:System.Windows.DependencyProperty.Register%2A>的第一個參數。 該名稱在每個登錄類型中都必須是唯一的。 透過基底類型繼承的相依性屬性視為登錄類型的一部分，已繼承屬性的名稱無法再次登錄。 不過，即使不能繼承該相依性屬性，還有一種技巧可將類別新增為相依性屬性的擁有者；如需詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。

當您建立識別碼欄位時，請以登錄屬性時所用名稱命名此欄位，再加上尾碼 `Property`。 此欄位是相依性屬性的識別碼，稍後將用來做為 <xref:System.Windows.DependencyObject.SetValue%2A> 的輸入，以及您將在包裝函式中進行的 <xref:System.Windows.DependencyObject.GetValue%2A> 呼叫，由您自己的程式碼對屬性的任何其他程式碼存取，由屬性系統所允許的任何外部程式碼存取，而且可能會 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器。

> [!NOTE]
> 在類別主體中定義相依性屬性是一般的實作，但也可能在類別靜態建構函式中定義相依性屬性。 如果您需要多行程式碼來初始化相依性屬性，這個方式可能有意義。

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>實作 "wrapper"

您的包裝函式執行應該會在 `get` 執行中呼叫 <xref:System.Windows.DependencyObject.GetValue%2A>，並在 `set` 的執行中 <xref:System.Windows.DependencyObject.SetValue%2A> （原始註冊呼叫和欄位也會顯示為清楚明瞭）。

除了例外狀況以外，您的包裝函式會分別執行 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 動作。 相關原因討論請參閱 [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)主題。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別中提供的所有現有公用相依性屬性都使用這個簡單的包裝函式實作模型，相依性屬性運作方式最複雜的部分或為固有的屬性系統行為，或為透過其他概念予以實行，例如透過屬性中繼資料的強制型轉或屬性變更回呼。

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

同樣地，依照慣例，包裝函式屬性的名稱必須與所選擇的名稱相同，並指定為註冊屬性之 <xref:System.Windows.DependencyProperty.Register%2A> 呼叫的第一個參數。 如果您的屬性不遵循慣例，不一定會停用所有可能的用途，但您會遇到幾個值得注意的問題︰

- 樣式和範本的某些方面不起作用。

- 大部分的工具和設計工具必須依賴命名慣例，才能正確序列化 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，或依屬性層級提供設計工具環境協助。

- 目前的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 載入器實作會略過整個包裝函式，且在處理屬性值時依賴命名慣例。 如需詳細資訊，請參閱 [XAML 相依性屬性](xaml-loading-and-dependency-properties.md)。

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>新相依性屬性的屬性中繼資料

當您登錄相依性屬性時，登錄會透過屬性系統建立儲存屬性特性的中繼資料物件。 如果屬性是以 <xref:System.Windows.DependencyProperty.Register%2A>的簡單簽章註冊，則這些特性中有許多都有設定的預設值。 <xref:System.Windows.DependencyProperty.Register%2A> 的其他簽章可讓您在註冊屬性時指定您想要的中繼資料。 相依性屬性最常指定的中繼資料，是套用在新執行個體的預設值，而新執行個體使用該屬性。

如果您要建立存在於 <xref:System.Windows.FrameworkElement>的衍生類別上的相依性屬性，您可以使用更特殊化的中繼資料類別，<xref:System.Windows.FrameworkPropertyMetadata> 而不是基底 <xref:System.Windows.PropertyMetadata> 類別。 <xref:System.Windows.FrameworkPropertyMetadata> 類別的構造函式有數個簽章，您可以在其中指定各種中繼資料特性組合。 如果您只想要指定預設值，請使用接受 <xref:System.Object>類型之單一參數的簽章。 傳遞該物件參數作為屬性的類型特定預設值（提供的預設值必須是您在 <xref:System.Windows.DependencyProperty.Register%2A> 呼叫中提供作為 `propertyType` 參數的類型）。

針對 <xref:System.Windows.FrameworkPropertyMetadata>，您也可以指定屬性的中繼資料選項旗標。 這些旗標在登錄後會轉換成屬性中繼資料中的個別屬性，用以與版面配置引擎等其他處理序溝通特定條件。

#### <a name="setting-appropriate-metadata-flags"></a>設定適當的中繼資料旗標

- 如果您的屬性（或其值的變更）會影響 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，尤其會影響版面配置系統應如何在頁面中調整或轉譯元素的大小，請設定下列一個或多個旗標： <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>、<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>、<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> 指出此屬性的變更需要變更 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 轉譯，其中包含的物件在父系中可能需要更多或較少的空間。 例如，"Width" 屬性應該設定此旗標。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> 指出此屬性的變更需要變更 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 轉譯，這通常不需要變更專用空間，而是表示空間中的位置已變更。 例如，"Alignment" 屬性應該設定此旗標。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> 表示發生一些其他變更，這不會影響配置和量值，但需要另一個呈現。 例如可變更現有項目色彩的 "Background" 等屬性。

  - 這些旗標在您自己的屬性系統或配置回呼覆寫實作中，通常用為中繼資料的通訊協定。 例如，如果實例的任何屬性報告值變更，並在其中繼資料中 <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> 做為 `true`，您可能會有 <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> 回呼會呼叫 <xref:System.Windows.UIElement.InvalidateArrange%2A>。

- 某些屬性會影響包含父項目的轉譯特性，超過前文所述之所需大小的變更。 例如，用於非固定格式檔模型中的 <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> 屬性，其中該屬性的變更可以變更包含該段落之流程檔的整體呈現。 使用 <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> 或 <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure>，在您自己的屬性中識別類似的案例。

- 相依性屬性預設支援資料繫結。 對於沒有任何實際案例可進行資料繫結的情況，或者大型物件的資料繫結效能認定有問題的情況，您可以故意停用資料繫結。

- 依預設，相依性屬性 <xref:System.Windows.Data.Binding.Mode%2A> 的資料系結預設為 <xref:System.Windows.Data.BindingMode.OneWay>。 您隨時都可以將系結變更為每個系結實例 <xref:System.Windows.Data.BindingMode.TwoWay>;如需詳細資訊，請參閱指定系結的[方向](../data/how-to-specify-the-direction-of-the-binding.md)。 但是做為相依性屬性作者，您可以選擇讓屬性預設使用 <xref:System.Windows.Data.BindingMode.TwoWay> 系結模式。 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>現有相依性屬性的範例;這個屬性的案例是 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> 設定邏輯和 <xref:System.Windows.Controls.MenuItem> 的組合會與預設主題樣式互動。 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> 屬性邏輯會根據其他狀態屬性和方法呼叫，以原生方式使用資料系結來維護屬性的狀態。 預設會系結 <xref:System.Windows.Data.BindingMode.TwoWay> 的另一個範例屬性是 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>。

- 您也可以藉由設定 <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> 旗標，在自訂相依性屬性中啟用屬性繼承。 屬性繼承對父項目和子項目有共同屬性的案例很有用，而且對子項目將特定屬性值設定為和父項目設定的值一樣，才有意義。 範例可繼承屬性為 <xref:System.Windows.FrameworkElement.DataContext%2A>，可用於系結作業，以啟用資料呈現的重要主要詳細案例。 藉由讓 <xref:System.Windows.FrameworkElement.DataContext%2A> 可繼承，任何子專案也會繼承該資料內容。 因為屬性值繼承的緣故，您可以指定位在網頁或應用程式根目錄中的資料內容，不需要重新指定即可繫結所有可能的子項目。 <xref:System.Windows.FrameworkElement.DataContext%2A> 也是一個很好的範例，可說明繼承會覆寫預設值，但一律可在任何特定子專案的本機上設定;如需詳細資訊，請參閱搭配[階層式資料使用主版-詳細模式](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。 屬性值繼承確實有可能的效能成本，因此應謹慎使用。如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

- 設定 <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> 旗標，以指示導覽日誌服務是否應該偵測或使用相依性屬性。 其中一個範例是 <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> 屬性;當流覽日誌記錄時，應該保存選取範圍控制項中選取的任何專案。

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>唯讀相依性屬性

您可以定義唯讀的相依性屬性。 但您為何可能將屬性定義為唯讀的案例有點不同，和向屬性系統登錄它們並公開識別碼的程序一樣。 如需詳細資訊，請參閱[唯讀相依性屬性](read-only-dependency-properties.md)。

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>集合類型相依性屬性

集合類型相依性屬性要考慮一些其他的實作問題。 如需詳細資訊，請參閱[集合類型相依性屬性](collection-type-dependency-properties.md)。

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>相依性屬性安全性考量

相依性屬性應該宣告為公用屬性。 相依性屬性識別碼欄位應該宣告為公用靜態欄位。 即使您嘗試宣告其他存取層級（例如受保護），還是可以透過識別碼搭配屬性系統 Api 來存取相依性屬性。 即使是「受保護的識別碼」欄位，也可能因為元資料包告或屬於屬性系統一部分的值判斷 Api （如 <xref:System.Windows.LocalValueEnumerator>）而存取。 如需詳細資訊，請參閱[相依性屬性的安全性](dependency-property-security.md)。

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>相依性屬性和類別建構函式

Managed 程式碼程式設計中有項一般原則 (通常由 FxCop 等程式碼分析工具強制執行)，類別建構函式不應該呼叫虛擬方法。 這是因為建構函式可以呼叫為衍生類別建構函式的基底初始化，而透過建構函式進入虛擬方法，可能會發生在建構中的物件執行個體尚未完全初始化的狀態。 當您從已衍生自 <xref:System.Windows.DependencyObject>的任何類別衍生時，您應該注意屬性系統本身會呼叫並公開內部的虛擬方法。 這些虛擬方法都屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統服務。 覆寫方法可讓衍生的類別參與值判斷。 若要避免執行階段初始化可能發生的問題，您不應該在類別的建構函式中設定相依性屬性值，除非您遵循非常明確的建構函式模式。 如需詳細資訊，請參閱 [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)。

## <a name="see-also"></a>請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [相依性屬性中繼資料](dependency-property-metadata.md)
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [集合類型的相依性屬性](collection-type-dependency-properties.md)
- [相依性屬性的安全性](dependency-property-security.md)
- [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)
- [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)
