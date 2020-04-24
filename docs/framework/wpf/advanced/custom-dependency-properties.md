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
ms.openlocfilehash: e4117d7add2a34d6d989d9222e7688361cf6b379
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646360"
---
# <a name="custom-dependency-properties"></a>自訂相依性屬性

本主題會說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式開發人員和元件作者可能想要建立自訂相依性屬性的原因，並說明實作步驟以及某些可以改善屬性的效能、可用性或多功能的實作選項。

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prerequisites

本主題假設您已從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)主題。 為遵循本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>什麼是相依性屬性？

您可以啟用本來是通用語言運行時 (CLR) 屬性,透過將其作為依賴項屬性實現來支援樣式設置、數據繫結、繼承、動畫和預設值。 依賴項屬性[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是通過調<xref:System.Windows.DependencyProperty.Register%2A>用 方法<xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>(<xref:System.Windows.DependencyProperty>或) 並在識別字段中備份的屬性在屬性系統中註冊的屬性。 依賴項屬性只能<xref:System.Windows.DependencyObject>由類型使用,<xref:System.Windows.DependencyObject>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]但在類層次結構中相當高,因此[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中大多數可用的類可以支援依賴項屬性。 有關相依屬性及用於在此 SDK 描述的一些術語和約定的詳細資訊,請參閱[相依項屬性概述](dependency-properties-overview.md)。

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>相依性屬性範例

在類[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]上實現的依賴項屬性的範<xref:System.Windows.Controls.Control.Background%2A>例 包括<xref:System.Windows.FrameworkElement.Width%2A>屬性、<xref:System.Windows.Controls.TextBox.Text%2A>屬性和屬性等。 類公開的每個依賴項屬性都有在同一類上公開的相應的公共靜態<xref:System.Windows.DependencyProperty>類型欄位。 這是相依性屬性的識別碼。 識別碼依慣例命名︰相依性屬性的名稱後綴字串 `Property`。 例如,屬性的<xref:System.Windows.DependencyProperty><xref:System.Windows.Controls.Control.Background%2A>識別碼字位為<xref:System.Windows.Controls.Control.BackgroundProperty>。 識別碼在註冊時儲存有關相依性屬性的資訊,然後識別碼稍後用於涉及相依項屬性的其他操作,<xref:System.Windows.DependencyObject.SetValue%2A>如呼叫 。

如[依賴項屬性概述](dependency-properties-overview.md)中所述,由於實現"[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]包裝 ",中的所有依賴項屬性(大多數附加屬性除外)也是 CLR 屬性。 因此,通過代碼,可以通過調用 CLR 訪問器來獲取或設置依賴項屬性,這些訪問器以與其他 CLR 屬性相同的方式定義包裝器。 作為已建立的相依性屬性的使用者,您通常不<xref:System.Windows.DependencyObject>使用與基礎屬性<xref:System.Windows.DependencyObject.GetValue%2A>系統的<xref:System.Windows.DependencyObject.SetValue%2A>連接點的方法和 。 <xref:System.Windows.DependencyObject.GetValue%2A>相反,CLR 屬性的現有實現已經調用,<xref:System.Windows.DependencyObject.SetValue%2A>並在`get`屬性`set`的和包裝器實現中,適當地使用標識符欄位。 如果您要自行實作自訂的相依性屬性，則會以類似的方式定義包裝函式。

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>您應於何時實作相依性屬性？

在類上實現屬性時,只要類派生自<xref:System.Windows.DependencyObject>,可以選擇<xref:System.Windows.DependencyProperty>使用 標識符支援屬性,從而使該屬性成為依賴項屬性。 讓您的屬性成為相依性屬性並非絕對必要或合適，視案例需求而定。 有時候，支援有私用欄位的屬性，一般的技巧即已足夠。 但只要您希望屬性支援下列一或多項 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能，就應該將屬性實作為相依性屬性：

- 您希望屬性在樣式中是可設定的。 有關詳細資訊,請參閱[樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)化。

- 您希望屬性支援資料繫結。 如需資料繫結相依性屬性的詳細資訊，請參閱[繫結兩個控制項的屬性](../data/how-to-bind-the-properties-of-two-controls.md)。

- 您希望屬性可使用動態資源參考來設定。 如需詳細資訊，請參閱 [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。

- 您想要自動繼承項目樹狀結構父項目的屬性值。 在這種情況下,請向方法<xref:System.Windows.DependencyProperty.RegisterAttached%2A>註冊,即使您也為 CLR 訪問創建了屬性包裝器。 如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

- 您希望屬性可製成動畫。 有關詳細資訊,請參閱[動畫概述](../graphics-multimedia/animation-overview.md)。

- 當屬性系統、環境或使用者所採取的動作，或讀取和使用樣式變更了先前的屬性值時，您希望屬性系統能夠回報。 使用屬性中繼資料，您的屬性可以指定每次屬性系統判定屬性值變更時都會叫用回呼方法。 相關的概念是屬性值強制型轉。 如需詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)。

- 您想要使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程序也使用的已建立中繼資料慣例，例如報告變更屬性值是否應該需要配置系統重新撰寫項目的視覺效果。 或者您想要能夠使用中繼資料覆寫，以便衍生類別可以變更中繼資料型的特性，例如預設值。

- 您希望自定義控制的屬性接收 Visual Studio WPF 設計器支援,例如**屬性**視窗編輯。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。

當您檢查這些案例時，您也應該考慮是否能夠以覆寫現有相依性屬性中繼資料的方式完成您的案例，而不是實作全新的屬性。 中繼資料覆寫是否實際可行，取決於您的案例，以及該案例與現有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 相依性屬性和類別實作的類似程度。 如需覆寫現有屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>定義相依性屬性所使用的檢查清單

定義相依性屬性包含四個不同的概念。 這些概念不一定得是嚴苛的程序步驟，因為其中有些最後會結合為實作中的單一段程式碼︰

- (選擇性) 建立相依性屬性的屬性中繼資料。

- 向屬性系統登錄屬性名稱，指定擁有者類型和屬性值類型。 如經使用，也指定屬性中繼資料。

- 將<xref:System.Windows.DependencyProperty>識別碼定義為`public``static``readonly`所有者類型的欄位。

- 定義 CLR"包裝器"屬性,其名稱與依賴項屬性的名稱匹配。 實現 CLR"包裝器"`get`屬性`set`和存取器,以便與支援它的依賴項屬性連接。

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>向屬性系統登錄屬性

為使屬性成為相依性屬性，您必須將該屬性登錄到屬性系統維護的資料表中，並給它唯一識別碼用為後續屬性系統作業的限定詞。 這些操作可能是內部操作,或者您自己的代碼調用屬性系統 API。 要註冊該屬性,請在類正文<xref:System.Windows.DependencyProperty.Register%2A>中調用 方法(類內部,但超出任何成員定義)。 標識符欄位也由<xref:System.Windows.DependencyProperty.Register%2A>方法調用作為返回值提供。 <xref:System.Windows.DependencyProperty.Register%2A>呼叫是在其他成員定義之外完成的,因為您使用此返回值作為類的一`public``static``readonly`部分分配和創建類型<xref:System.Windows.DependencyProperty>欄位。 此欄位會變成您相依性屬性的識別碼。

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>相依性屬性命名慣例

相依性屬性有已建立的命名慣例，除非例外情況，否則必須遵循。

依賴項屬性本身將具有基本名稱"水族館圖",如本示例中所示,該名稱作為<xref:System.Windows.DependencyProperty.Register%2A>的第一個參數給出。 該名稱在每個登錄類型中都必須是唯一的。 透過基底類型繼承的相依性屬性視為登錄類型的一部分，已繼承屬性的名稱無法再次登錄。 不過，即使不能繼承該相依性屬性，還有一種技巧可將類別新增為相依性屬性的擁有者；如需詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。

當您建立識別碼欄位時，請以登錄屬性時所用名稱命名此欄位，再加上尾碼 `Property`。 此欄位是依賴項屬性的標識碼,稍後將用作包裝器中要進行的<xref:System.Windows.DependencyObject.SetValue%2A>和<xref:System.Windows.DependencyObject.GetValue%2A>呼叫的輸入、您自己的代碼對該屬性的任何其他代碼存取、您允許的任何外部代碼存取、屬性系統以及[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]可能由處理器存取。

> [!NOTE]
> 在類別主體中定義相依性屬性是一般的實作，但也可能在類別靜態建構函式中定義相依性屬性。 如果您需要多行程式碼來初始化相依性屬性，這個方式可能有意義。

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>實作 "wrapper"

包裝<xref:System.Windows.DependencyObject.GetValue%2A>器實現應在`get`實現<xref:System.Windows.DependencyObject.SetValue%2A>`set`和 實現中調用(此處也顯示原始註冊調用和欄位,以便清楚)。

在除了特殊情況外,包裝器實現應分別執行和<xref:System.Windows.DependencyObject.GetValue%2A><xref:System.Windows.DependencyObject.SetValue%2A>操作。 相關原因討論請參閱 [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)主題。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別中提供的所有現有公用相依性屬性都使用這個簡單的包裝函式實作模型，相依性屬性運作方式最複雜的部分或為固有的屬性系統行為，或為透過其他概念予以實行，例如透過屬性中繼資料的強制型轉或屬性變更回呼。

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

同樣,按照慣例,包裝器屬性的名稱必須與選擇的名稱相同,並作為註冊該屬性的<xref:System.Windows.DependencyProperty.Register%2A>調用的第一個參數給出。 如果您的屬性不遵循慣例，不一定會停用所有可能的用途，但您會遇到幾個值得注意的問題︰

- 樣式和範本的某些方面不起作用。

- 大部分的工具和設計工具必須依賴命名慣例，才能正確序列化 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，或依屬性層級提供設計工具環境協助。

- 載入程式的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]當前實現完全繞過包裝器,在處理屬性值時依賴於命名約定。 如需詳細資訊，請參閱 [XAML 相依性屬性](xaml-loading-and-dependency-properties.md)。

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>新相依性屬性的屬性中繼資料

當您登錄相依性屬性時，登錄會透過屬性系統建立儲存屬性特性的中繼資料物件。 如果屬性註冊了<xref:System.Windows.DependencyProperty.Register%2A>的簡單簽名,則這些特徵中有許多具有預設設置。 的其他簽名<xref:System.Windows.DependencyProperty.Register%2A>允許您在註冊屬性時指定所需的元數據。 相依性屬性最常指定的中繼資料，是套用在新執行個體的預設值，而新執行個體使用該屬性。

如果要創建存在於 派生類的依賴項屬性,則可以使用更專用<xref:System.Windows.FrameworkElement>的 元<xref:System.Windows.FrameworkPropertyMetadata>數據類<xref:System.Windows.PropertyMetadata>而不是基 類。 類別建<xref:System.Windows.FrameworkPropertyMetadata>構函數具有多個簽名,您可以在其中組合指定各種元資料特徵。 如果只想指定預設值,請使用採用類型<xref:System.Object>為的單個參數的簽名。 將該物件參數作為屬性的特定於類型的預設值傳遞(提供的預設值必須是您在`propertyType`<xref:System.Windows.DependencyProperty.Register%2A>調用中作為參數提供的類型)。

對於<xref:System.Windows.FrameworkPropertyMetadata>,還可以為屬性指定元數據選項標誌。 這些旗標在登錄後會轉換成屬性中繼資料中的個別屬性，用以與版面配置引擎等其他處理序溝通特定條件。

#### <a name="setting-appropriate-metadata-flags"></a>設定適當的中繼資料旗標

- 如果屬性(或其值的變更)影響[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)],並且特別影響佈局系統在頁面中的大小或呈現元素的方式,請設定以下一個或多個標誌: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>指示對此屬性的更改需要更改為[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]呈現,其中包含物件可能需要父物件中或多或少的空間。 例如，"Width" 屬性應該設定此旗標。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>指示對此屬性的更改需要更改[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]渲染,這通常不需要在專用空間中進行更改,但確實表示空間中的定位已更改。 例如，"Alignment" 屬性應該設定此旗標。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>指示發生了一些其他更改,這些更改不會影響佈局和度量值,但確實需要另一個渲染。 例如可變更現有項目色彩的 "Background" 等屬性。

  - 這些旗標在您自己的屬性系統或配置回呼覆寫實作中，通常用為中繼資料的通訊協定。 例如,如果實例的任何屬性報告<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>值更改且其元<xref:System.Windows.UIElement.InvalidateArrange%2A>數據<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>中`true`具有 , 則可能具有回調。

- 某些屬性會影響包含父項目的轉譯特性，超過前文所述之所需大小的變更。 例如,流文<xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A>檔模型中使用的屬性,其中對該屬性的更改可以更改包含段落的流文檔的總體呈現。 使用<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange><xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure>或在您自己的屬性中識別類似情況。

- 相依性屬性預設支援資料繫結。 對於沒有任何實際案例可進行資料繫結的情況，或者大型物件的資料繫結效能認定有問題的情況，您可以故意停用資料繫結。

- 預設情況下,依賴項目屬性<xref:System.Windows.Data.Binding.Mode%2A>的資料繫結預設<xref:System.Windows.Data.BindingMode.OneWay>為 。 您可以隨時將綁定更改為<xref:System.Windows.Data.BindingMode.TwoWay>每個綁定實例;因此,您可以將綁定更改為每個綁定實例。有關詳細資訊,請參閱[指定綁定的方向](../data/how-to-specify-the-direction-of-the-binding.md)。 但是,作為依賴項屬性作者,您可以選擇使屬性預設使用<xref:System.Windows.Data.BindingMode.TwoWay>綁定模式。 現有相依項屬性的範例<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>是 。此屬性的方案是<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>設置邏輯和組合<xref:System.Windows.Controls.MenuItem>與 預設主題樣式交互。 屬性<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>邏輯使用本機綁定的數據來根據其他狀態屬性和方法調用維護屬性的狀態。 預設情況下繫結<xref:System.Windows.Data.BindingMode.TwoWay>的另一個範例屬性是<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>。

- 還可以通過設置<xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits>標誌在自定義依賴項屬性中啟用屬性繼承。 屬性繼承對父項目和子項目有共同屬性的案例很有用，而且對子項目將特定屬性值設定為和父項目設定的值一樣，才有意義。 可繼承屬性的範例為<xref:System.Windows.FrameworkElement.DataContext%2A>,用於綁定操作,以啟用資料表示的重要主詳細資訊方案。 通過使<xref:System.Windows.FrameworkElement.DataContext%2A>可繼承,任何子元素也繼承該數據上下文。 因為屬性值繼承的緣故，您可以指定位在網頁或應用程式根目錄中的資料內容，不需要重新指定即可繫結所有可能的子項目。 <xref:System.Windows.FrameworkElement.DataContext%2A>也是一個很好的例子,說明繼承重寫預設值,但它始終可以在本地設置在任何特定的子元素上;關於詳細資訊,請參考[使用具有分層資料的主詳細資訊模式](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。 屬性值繼承確實有可能的效能成本，因此應謹慎使用。如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

- 設置標誌<xref:System.Windows.FrameworkPropertyMetadataOptions.Journal>以指示是否應檢測到依賴項屬性或由導航日記服務使用。 屬性就是一<xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>個示例;導航日記歷史記錄時,應保留選擇控件中選擇的任何項。

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>唯讀相依性屬性

您可以定義唯讀的相依性屬性。 但您為何可能將屬性定義為唯讀的案例有點不同，和向屬性系統登錄它們並公開識別碼的程序一樣。 如需詳細資訊，請參閱[唯讀相依性屬性](read-only-dependency-properties.md)。

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>集合類型相依性屬性

集合類型相依性屬性要考慮一些其他的實作問題。 如需詳細資訊，請參閱[集合類型相依性屬性](collection-type-dependency-properties.md)。

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>相依性屬性安全性考量

相依性屬性應該宣告為公用屬性。 相依性屬性識別碼欄位應該宣告為公用靜態欄位。 即使您嘗試聲明其他訪問級別(如受保護),也始終可以通過標識符與屬性系統 API 一起訪問依賴項屬性。 由於中繼報告或作為屬性系統的一部分的值確定 API(<xref:System.Windows.LocalValueEnumerator>如 ),即使受保護的標識符欄位也可能存取。 如需詳細資訊，請參閱[相依性屬性的安全性](dependency-property-security.md)。

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>相依性屬性和類別建構函式

Managed 程式碼程式設計中有項一般原則 (通常由 FxCop 等程式碼分析工具強制執行)，類別建構函式不應該呼叫虛擬方法。 這是因為建構函式可以呼叫為衍生類別建構函式的基底初始化，而透過建構函式進入虛擬方法，可能會發生在建構中的物件執行個體尚未完全初始化的狀態。 當您從已經派生的任何<xref:System.Windows.DependencyObject>類派生時,應注意屬性系統本身在內部調用並公開虛擬方法。 這些虛擬方法都屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統服務。 覆寫方法可讓衍生的類別參與值判斷。 若要避免執行階段初始化可能發生的問題，您不應該在類別的建構函式中設定相依性屬性值，除非您遵循非常明確的建構函式模式。 如需詳細資訊，請參閱 [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)。

## <a name="see-also"></a>另請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [相依性屬性中繼資料](dependency-property-metadata.md)
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [集合類型相依性屬性](collection-type-dependency-properties.md)
- [相依性屬性的安全性](dependency-property-security.md)
- [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)
- [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)
