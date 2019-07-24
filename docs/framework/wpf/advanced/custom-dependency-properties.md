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
ms.openlocfilehash: 1352876b79e103d20d08382ab088f7777c6fe2ae
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401575"
---
# <a name="custom-dependency-properties"></a>自訂相依性屬性

本主題會說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式開發人員和元件作者可能想要建立自訂相依性屬性的原因，並說明實作步驟以及某些可以改善屬性的效能、可用性或多功能的實作選項。

<a name="prerequisites"></a>

## <a name="prerequisites"></a>必要條件

本主題假設您已從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)主題。 為遵循本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>什麼是相依性屬性？

您可以啟用通用語言執行平臺 (CLR) 屬性, 以支援樣式、資料系結、繼承、動畫和預設值, 方法是將其實作為相依性屬性。 相依性[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性是藉由<xref:System.Windows.DependencyProperty.Register%2A>呼叫方法 (或<xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> <xref:System.Windows.DependencyProperty> ), 並由識別碼欄位支援的屬性, 向屬性系統註冊。 相依性<xref:System.Windows.DependencyObject>屬性只能由型別使用, 但是<xref:System.Windows.DependencyObject>在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類別階層中相當高, 因此在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供的大部分類別都可以支援相依性屬性。 如需相依性屬性的詳細資訊，以及此 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 中描述它們所使用的一些術語和慣例，請參閱[相依性屬性概觀](dependency-properties-overview.md)。

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>相依性屬性範例

在類別上[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實作為相依性屬性的範例<xref:System.Windows.Controls.Control.Background%2A>包括屬性、 <xref:System.Windows.FrameworkElement.Width%2A>屬性和<xref:System.Windows.Controls.TextBox.Text%2A>屬性, 還有其他許多專案。 類別所公開的每個相依性屬性都有一個對應的公用<xref:System.Windows.DependencyProperty>靜態欄位, 類型會公開在該相同的類別上。 這是相依性屬性的識別碼。 識別碼依慣例命名︰相依性屬性的名稱後綴字串 `Property`。 例如, <xref:System.Windows.Controls.Control.Background%2A>屬性的對應<xref:System.Windows.DependencyProperty>識別碼欄位是<xref:System.Windows.Controls.Control.BackgroundProperty>。 識別碼會儲存已註冊之相依性屬性的相關資訊, 稍後會使用此識別碼進行相依性屬性的其他作業, 例如呼叫<xref:System.Windows.DependencyObject.SetValue%2A>。

如相依性[屬性總覽](dependency-properties-overview.md)中所述, 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的所有相依性屬性 (除了大部分的附加屬性以外) 也都是 CLR 屬性, 因為「包裝函式」的執行。 因此, 在程式碼中, 您可以藉由呼叫 CLR 存取子來取得或設定相依性屬性, 方法是以您使用其他 CLR 屬性的相同方式來定義包裝函式。 身為已建立相依性屬性的取用者, 您通常不<xref:System.Windows.DependencyObject>會<xref:System.Windows.DependencyObject.GetValue%2A>使用<xref:System.Windows.DependencyObject.SetValue%2A>方法和, 這是基礎屬性系統的連接點。 相反地, 現有的 CLR 屬性<xref:System.Windows.DependencyObject.GetValue%2A>執行已經呼叫, 而且<xref:System.Windows.DependencyObject.SetValue%2A>在屬性的`get`和`set`包裝函式中, 會適當使用 [識別碼] 欄位。 如果您要自行實作自訂的相依性屬性，則會以類似的方式定義包裝函式。

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>您應於何時實作相依性屬性？

當您在類別上執行屬性時, 只要您的類別衍生自<xref:System.Windows.DependencyObject>, 您就可以選擇<xref:System.Windows.DependencyProperty>使用識別碼來備份您的屬性, 進而使其成為相依性屬性。 讓您的屬性成為相依性屬性並非絕對必要或合適，視案例需求而定。 有時候，支援有私用欄位的屬性，一般的技巧即已足夠。 但只要您希望屬性支援下列一或多項 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能，就應該將屬性實作為相依性屬性：

- 您希望屬性在樣式中是可設定的。 如需詳細資訊，請參閱 [設定樣式和範本](../controls/styling-and-templating.md)。

- 您希望屬性支援資料繫結。 如需資料繫結相依性屬性的詳細資訊，請參閱[繫結兩個控制項的屬性](../data/how-to-bind-the-properties-of-two-controls.md)。

- 您希望屬性可使用動態資源參考來設定。 如需詳細資訊，請參閱 [XAML 資源](xaml-resources.md)。

- 您想要自動繼承項目樹狀結構父項目的屬性值。 在此情況下, 即使您<xref:System.Windows.DependencyProperty.RegisterAttached%2A>也建立了 CLR 存取的屬性包裝函式, 也會使用方法進行註冊。 如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

- 您希望屬性可製成動畫。 如需詳細資訊，請參閱 [動畫概觀](../graphics-multimedia/animation-overview.md)。

- 當屬性系統、環境或使用者所採取的動作，或讀取和使用樣式變更了先前的屬性值時，您希望屬性系統能夠回報。 使用屬性中繼資料，您的屬性可以指定每次屬性系統判定屬性值變更時都會叫用回呼方法。 相關的概念是屬性值強制型轉。 如需詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)。

- 您想要使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程序也使用的已建立中繼資料慣例，例如報告變更屬性值是否應該需要配置系統重新撰寫項目的視覺效果。 或者您想要能夠使用中繼資料覆寫，以便衍生類別可以變更中繼資料型的特性，例如預設值。

- 您想要自訂控制項的屬性, 以接收 Visual Studio WPF 設計工具支援, 例如 [**屬性**] 視窗編輯。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。

當您檢查這些案例時，您也應該考慮是否能夠以覆寫現有相依性屬性中繼資料的方式完成您的案例，而不是實作全新的屬性。 中繼資料覆寫是否實際可行，取決於您的案例，以及該案例與現有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 相依性屬性和類別實作的類似程度。 如需覆寫現有屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>定義相依性屬性所使用的檢查清單

定義相依性屬性包含四個不同的概念。 這些概念不一定得是嚴苛的程序步驟，因為其中有些最後會結合為實作中的單一段程式碼︰

- (選擇性) 建立相依性屬性的屬性中繼資料。

- 向屬性系統登錄屬性名稱，指定擁有者類型和屬性值類型。 如經使用，也指定屬性中繼資料。

- `public`將識別碼定義`static`為擁有者類型上的欄位。`readonly` <xref:System.Windows.DependencyProperty>

- 定義 CLR "包裝函式" 屬性, 其名稱符合相依性屬性的名稱。 執行 CLR 「包裝函式」屬性`get`的`set`和存取子, 以使用其支援的相依性屬性來連接。

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>向屬性系統登錄屬性

為使屬性成為相依性屬性，您必須將該屬性登錄到屬性系統維護的資料表中，並給它唯一識別碼用為後續屬性系統作業的限定詞。 這些作業可能是內部作業, 或您自己的程式碼呼叫屬性系統 Api。 若要註冊屬性, 您可以呼叫<xref:System.Windows.DependencyProperty.Register%2A>類別主體中的方法 (在類別中, 但在任何成員定義外)。 [識別碼] 欄位也是由<xref:System.Windows.DependencyProperty.Register%2A>方法呼叫所提供, 做為傳回值。 <xref:System.Windows.DependencyProperty.Register%2A>呼叫是在其他成員定義以外完成的原因, 是因為您使用此傳回值來指派類型<xref:System.Windows.DependencyProperty>的`readonly`欄位, `public`並將其`static`建立為類別的一部分。 此欄位會變成您相依性屬性的識別碼。

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>相依性屬性命名慣例

相依性屬性有已建立的命名慣例，除非例外情況，否則必須遵循。

相依性屬性本身會有基本名稱 "AquariumGraphic", 如下列範例所示, 它會指定為的第一個參數<xref:System.Windows.DependencyProperty.Register%2A>。 該名稱在每個登錄類型中都必須是唯一的。 透過基底類型繼承的相依性屬性視為登錄類型的一部分，已繼承屬性的名稱無法再次登錄。 不過，即使不能繼承該相依性屬性，還有一種技巧可將類別新增為相依性屬性的擁有者；如需詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。

當您建立識別碼欄位時，請以登錄屬性時所用名稱命名此欄位，再加上尾碼 `Property`。 此欄位是相依性屬性的識別碼, 稍後將用來做為的輸入, 以及<xref:System.Windows.DependencyObject.SetValue%2A> <xref:System.Windows.DependencyObject.GetValue%2A>您將在包裝函式中進行的任何其他程式碼存取, 由您自己的程式碼對屬性所做的任何其他程式碼存取, 由您允許的任何外部程式碼存取、由屬性系統, 而且可能是[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器。

> [!NOTE]
> 在類別主體中定義相依性屬性是一般的實作，但也可能在類別靜態建構函式中定義相依性屬性。 如果您需要多行程式碼來初始化相依性屬性，這個方式可能有意義。

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>實作 "wrapper"

您的包裝函式<xref:System.Windows.DependencyObject.GetValue%2A>的`get`執行應該會在<xref:System.Windows.DependencyObject.SetValue%2A> `set`執行中呼叫, 而在執行中 (原始註冊呼叫和欄位也會顯示為清楚明瞭)。

在所有例外狀況的情況下, 您的包裝函式<xref:System.Windows.DependencyObject.GetValue%2A>會<xref:System.Windows.DependencyObject.SetValue%2A>分別執行和動作。 相關原因討論請參閱 [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)主題。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別中提供的所有現有公用相依性屬性都使用這個簡單的包裝函式實作模型，相依性屬性運作方式最複雜的部分或為固有的屬性系統行為，或為透過其他概念予以實行，例如透過屬性中繼資料的強制型轉或屬性變更回呼。

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

同樣地, 依照慣例, 包裝函式屬性的名稱必須與所選擇的名稱相同, 並指定為註冊屬性之<xref:System.Windows.DependencyProperty.Register%2A>呼叫的第一個參數。 如果您的屬性不遵循慣例，不一定會停用所有可能的用途，但您會遇到幾個值得注意的問題︰

- 樣式和範本的某些方面不起作用。

- 大部分的工具和設計工具必須依賴命名慣例，才能正確序列化 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，或依屬性層級提供設計工具環境協助。

- 目前的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 載入器實作會略過整個包裝函式，且在處理屬性值時依賴命名慣例。 如需詳細資訊，請參閱 [XAML 相依性屬性](xaml-loading-and-dependency-properties.md)。

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>新相依性屬性的屬性中繼資料

當您登錄相依性屬性時，登錄會透過屬性系統建立儲存屬性特性的中繼資料物件。 如果屬性是以的簡單<xref:System.Windows.DependencyProperty.Register%2A>簽章註冊, 則其中許多特性都會有設定的預設值。 的<xref:System.Windows.DependencyProperty.Register%2A>其他簽章可讓您在註冊屬性時指定您想要的中繼資料。 相依性屬性最常指定的中繼資料，是套用在新執行個體的預設值，而新執行個體使用該屬性。

如果您要建立的相依性屬性存在於的衍生類別<xref:System.Windows.FrameworkElement>上, 您可以使用更特製化的中繼資料類別<xref:System.Windows.FrameworkPropertyMetadata> , 而<xref:System.Windows.PropertyMetadata>不是基底類別。 <xref:System.Windows.FrameworkPropertyMetadata>類別的函式有數個簽章, 您可以在其中指定各種中繼資料特性組合。 如果您只想要指定預設值, 請使用採用類型<xref:System.Object>之單一參數的簽章。 傳遞該物件參數作為屬性的類型特定預設值 (提供的預設值必須是您在`propertyType` <xref:System.Windows.DependencyProperty.Register%2A>呼叫中提供作為參數的類型)。

針對<xref:System.Windows.FrameworkPropertyMetadata>, 您也可以指定屬性的中繼資料選項旗標。 這些旗標在登錄後會轉換成屬性中繼資料中的個別屬性，用以與版面配置引擎等其他處理序溝通特定條件。

#### <a name="setting-appropriate-metadata-flags"></a>設定適當的中繼資料旗標

- 如果您的屬性 (或其值的變更) 會[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]影響, 尤其會影響版面配置系統應如何在頁面中調整或轉譯元素的大小, 並設定下列一個或多個旗<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>標<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>、、。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>指出此屬性的變更需要變更[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]轉譯, 其中包含的物件在父系中可能需要更多或較少的空間。 例如，"Width" 屬性應該設定此旗標。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>指出此屬性的變更需要變更[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]轉譯, 這通常不需要變更專用空間, 而是表示空間中的位置已變更。 例如，"Alignment" 屬性應該設定此旗標。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>表示發生一些其他變更, 這不會影響配置和量值, 但需要另一個呈現。 例如可變更現有項目色彩的 "Background" 等屬性。

  - 這些旗標在您自己的屬性系統或配置回呼覆寫實作中，通常用為中繼資料的通訊協定。 比方說, <xref:System.Windows.UIElement.InvalidateArrange%2A>如果實例的任何<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>屬性報告`true`值變更, 而且在其中繼資料中有<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> , 則您可能會有回呼。

- 某些屬性會影響包含父項目的轉譯特性，超過前文所述之所需大小的變更。 其中一個範例是<xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A>在非固定格式檔模型中使用的屬性, 而該屬性的變更會變更包含該段落之流程檔的整體呈現。 使用<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> 或<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure>來識別您自己屬性中的類似案例。

- 相依性屬性預設支援資料繫結。 對於沒有任何實際案例可進行資料繫結的情況，或者大型物件的資料繫結效能認定有問題的情況，您可以故意停用資料繫結。

- 依預設, 相依性<xref:System.Windows.Data.Binding.Mode%2A>屬性的資料系結<xref:System.Windows.Data.BindingMode.OneWay>會預設為。 您隨時都可以將系結變更<xref:System.Windows.Data.BindingMode.TwoWay>為每個系結實例。如需詳細資訊, 請參閱指定系結的[方向](../data/how-to-specify-the-direction-of-the-binding.md)。 但身為相依性屬性作者, 您可以選擇讓屬性依預設<xref:System.Windows.Data.BindingMode.TwoWay>使用系結模式。 現有相依性屬性<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>的範例為; 這個屬性的案例是<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>設定<xref:System.Windows.Controls.MenuItem>邏輯和與預設主題樣式互動的組合。 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>屬性邏輯會以原生方式使用資料系結, 以根據其他狀態屬性和方法呼叫來維護屬性的狀態。 預設系結的另<xref:System.Windows.Data.BindingMode.TwoWay>一個範例屬性<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>是。

- 您也可以藉由設定<xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits>旗標, 在自訂相依性屬性中啟用屬性繼承。 屬性繼承對父項目和子項目有共同屬性的案例很有用，而且對子項目將特定屬性值設定為和父項目設定的值一樣，才有意義。 可繼承的屬性範例<xref:System.Windows.FrameworkElement.DataContext%2A>是, 用來系結作業, 以啟用資料呈現的重要主要詳細案例。 藉由<xref:System.Windows.FrameworkElement.DataContext%2A>建立可繼承的, 任何子專案也會繼承該資料內容。 因為屬性值繼承的緣故，您可以指定位在網頁或應用程式根目錄中的資料內容，不需要重新指定即可繫結所有可能的子項目。 <xref:System.Windows.FrameworkElement.DataContext%2A>也是一個很好的範例, 說明繼承會覆寫預設值, 但一律可在任何特定的子專案上進行本機設定。如需詳細資訊, 請參閱搭配[階層式資料使用主版-詳細模式](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。 屬性值繼承確實有可能的效能成本，因此應謹慎使用。如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

- <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal>設定旗標, 以指示導覽日誌服務是否應該偵測或使用相依性屬性。 其中一個範例就<xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>是屬性; 流覽記錄歷程記錄時, 應該保存選取控制項中選取的任何專案。

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>唯讀相依性屬性

您可以定義唯讀的相依性屬性。 但您為何可能將屬性定義為唯讀的案例有點不同，和向屬性系統登錄它們並公開識別碼的程序一樣。 如需詳細資訊，請參閱[唯讀相依性屬性](read-only-dependency-properties.md)。

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>集合類型相依性屬性

集合類型相依性屬性要考慮一些其他的實作問題。 如需詳細資訊，請參閱[集合類型相依性屬性](collection-type-dependency-properties.md)。

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>相依性屬性安全性考量

相依性屬性應該宣告為公用屬性。 相依性屬性識別碼欄位應該宣告為公用靜態欄位。 即使您嘗試宣告其他存取層級 (例如受保護), 還是可以透過識別碼搭配屬性系統 Api 來存取相依性屬性。 即使是「受保護的識別碼」欄位, 也可能因為元資料包告或屬於屬性系統一部分的值判斷 Api ( <xref:System.Windows.LocalValueEnumerator>例如) 而可存取。 如需詳細資訊，請參閱[相依性屬性的安全性](dependency-property-security.md)。

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>相依性屬性和類別建構函式

Managed 程式碼程式設計中有項一般原則 (通常由 FxCop 等程式碼分析工具強制執行)，類別建構函式不應該呼叫虛擬方法。 這是因為建構函式可以呼叫為衍生類別建構函式的基底初始化，而透過建構函式進入虛擬方法，可能會發生在建構中的物件執行個體尚未完全初始化的狀態。 當您從已衍生<xref:System.Windows.DependencyObject>自的任何類別衍生時, 您應該注意屬性系統本身會呼叫並公開內部的虛擬方法。 這些虛擬方法都屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統服務。 覆寫方法可讓衍生的類別參與值判斷。 若要避免執行階段初始化可能發生的問題，您不應該在類別的建構函式中設定相依性屬性值，除非您遵循非常明確的建構函式模式。 如需詳細資訊，請參閱 [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)。

## <a name="see-also"></a>另請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [相依性屬性中繼資料](dependency-property-metadata.md)
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [集合類型的相依性屬性](collection-type-dependency-properties.md)
- [相依性屬性的安全性](dependency-property-security.md)
- [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)
- [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)
