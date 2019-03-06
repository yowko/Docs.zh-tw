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
ms.openlocfilehash: 12843c74a7519d29e869be0342b18a1137f2dc5a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372213"
---
# <a name="custom-dependency-properties"></a>自訂相依性屬性

本主題會說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式開發人員和元件作者可能想要建立自訂相依性屬性的原因，並說明實作步驟以及某些可以改善屬性的效能、可用性或多功能的實作選項。

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件

本主題假設您已從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)主題。 為遵循本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。

<a name="whatis"></a>
## <a name="what-is-a-dependency-property"></a>什麼是相依性屬性？

您可將原可能成為 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性的項目實作為相依性屬性，以支援樣式、資料繫結、繼承、動畫和預設值。 相依性屬性是屬性，已向[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]藉由呼叫屬性系統<xref:System.Windows.DependencyProperty.Register%2A>方法 (或<xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>)，並由<xref:System.Windows.DependencyProperty>識別碼欄位。 相依性屬性可以僅供<xref:System.Windows.DependencyObject>類型，但<xref:System.Windows.DependencyObject>在相當高[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類別階層架構，因此大部分的類別中可用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可支援相依性屬性。 如需相依性屬性的詳細資訊，以及此 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 中描述它們所使用的一些術語和慣例，請參閱[相依性屬性概觀](dependency-properties-overview.md)。

<a name="example_dp"></a>
## <a name="examples-of-dependency-properties"></a>相依性屬性範例

相依性屬性上實作的範例[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類別包括<xref:System.Windows.Controls.Control.Background%2A>屬性，<xref:System.Windows.FrameworkElement.Width%2A>屬性，而<xref:System.Windows.Controls.TextBox.Text%2A>; 屬性，還有許多其他項目。 類別公開的每個相依性屬性都已型別的對應的公用靜態欄位<xref:System.Windows.DependencyProperty>該相同的類別上公開。 這是相依性屬性的識別碼。 識別碼依慣例命名︰相依性屬性的名稱後綴字串 `Property`。 例如，對應<xref:System.Windows.DependencyProperty>識別碼欄位<xref:System.Windows.Controls.Control.Background%2A>屬性是<xref:System.Windows.Controls.Control.BackgroundProperty>。 識別碼會儲存相依性屬性的相關資訊，其註冊，以及識別項稍後再用於牽涉到的相依性屬性，例如呼叫其他作業<xref:System.Windows.DependencyObject.SetValue%2A>。

如[相依性屬性概觀](dependency-properties-overview.md)所述，因為實作 "wrapper"，所以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的所有相依性屬性也都是 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性 (最緊密的屬性除外)。 因此，在程式碼中，您可以像使用其他 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性一樣呼叫定義包裝函式的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 存取子，來取得或設定相依性屬性。 為已建立的相依性屬性消費者，通常不用<xref:System.Windows.DependencyObject>方法<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>，這是基礎屬性系統的連接點。 相反地，現有的實作[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]屬性將會已呼叫<xref:System.Windows.DependencyObject.GetValue%2A>並<xref:System.Windows.DependencyObject.SetValue%2A>內`get`和`set`包裝函式實作的屬性，適當地使用的識別項欄位. 如果您要自行實作自訂的相依性屬性，則會以類似的方式定義包裝函式。

<a name="backing_with_dp"></a>
## <a name="when-should-you-implement-a-dependency-property"></a>您應於何時實作相依性屬性？

當您實作的屬性在類別上，只要您的類別衍生自<xref:System.Windows.DependencyObject>，您可以選擇將您的屬性與<xref:System.Windows.DependencyProperty>識別碼，因此若要讓相依性屬性。 讓您的屬性成為相依性屬性並非絕對必要或合適，視案例需求而定。 有時候，支援有私用欄位的屬性，一般的技巧即已足夠。 但只要您希望屬性支援下列一或多項 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能，就應該將屬性實作為相依性屬性：

-   您希望屬性在樣式中是可設定的。 如需詳細資訊，請參閱 [設定樣式和範本](../controls/styling-and-templating.md)。

-   您希望屬性支援資料繫結。 如需資料繫結相依性屬性的詳細資訊，請參閱[繫結兩個控制項的屬性](../data/how-to-bind-the-properties-of-two-controls.md)。

-   您希望屬性可使用動態資源參考來設定。 如需詳細資訊，請參閱 [XAML 資源](xaml-resources.md)。

-   您想要自動繼承項目樹狀結構父項目的屬性值。 在此情況下，向<xref:System.Windows.DependencyProperty.RegisterAttached%2A>方法，即使您也建立了屬性包裝函式[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]存取。 如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

-   您希望屬性可製成動畫。 如需詳細資訊，請參閱 [動畫概觀](../graphics-multimedia/animation-overview.md)。

-   當屬性系統、環境或使用者所採取的動作，或讀取和使用樣式變更了先前的屬性值時，您希望屬性系統能夠回報。 使用屬性中繼資料，您的屬性可以指定每次屬性系統判定屬性值變更時都會叫用回呼方法。 相關的概念是屬性值強制型轉。 如需詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)。

-   您想要使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程序也使用的已建立中繼資料慣例，例如報告變更屬性值是否應該需要配置系統重新撰寫項目的視覺效果。 或者您想要能夠使用中繼資料覆寫，以便衍生類別可以變更中繼資料型的特性，例如預設值。

-   您想要接收 Visual Studio WPF 設計工具的自訂控制項的屬性支援，例如**屬性**視窗編輯。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。

當您檢查這些案例時，您也應該考慮是否能夠以覆寫現有相依性屬性中繼資料的方式完成您的案例，而不是實作全新的屬性。 中繼資料覆寫是否實際可行，取決於您的案例，以及該案例與現有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 相依性屬性和類別實作的類似程度。 如需覆寫現有屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。

<a name="checklist"></a>
## <a name="checklist-for-defining-a-dependency-property"></a>定義相依性屬性所使用的檢查清單

定義相依性屬性包含四個不同的概念。 這些概念不一定得是嚴苛的程序步驟，因為其中有些最後會結合為實作中的單一段程式碼︰

-   (選擇性) 建立相依性屬性的屬性中繼資料。

-   向屬性系統登錄屬性名稱，指定擁有者類型和屬性值類型。 如經使用，也指定屬性中繼資料。

-   定義<xref:System.Windows.DependencyProperty>識別碼作為`public` `static` `readonly`擁有者型別的欄位。

-   定義名稱與相依性屬性名稱符合的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]"wrapper" 屬性。 實作 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "wrapper" 屬性的 `get` 和 `set` 存取子，以連接支援它的相依性屬性。

<a name="registering"></a>
### <a name="registering-the-property-with-the-property-system"></a>向屬性系統登錄屬性

為使屬性成為相依性屬性，您必須將該屬性登錄到屬性系統維護的資料表中，並給它唯一識別碼用為後續屬性系統作業的限定詞。 這些作業可能是內部作業，或您自己程式碼呼叫的屬性系統 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。 若要註冊的屬性，請呼叫<xref:System.Windows.DependencyProperty.Register%2A>類別 （類別，但任何成員定義之外） 的主體內的方法。 [識別碼] 欄位也會提供由<xref:System.Windows.DependencyProperty.Register%2A>方法呼叫，傳回的值。 原因，<xref:System.Windows.DependencyProperty.Register%2A>呼叫完成之外其他成員定義是因為您可以使用此傳回值指派，並建立`public` `static` `readonly`型別的欄位<xref:System.Windows.DependencyProperty>為您類別的一部分。 此欄位會變成您相依性屬性的識別碼。

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>
### <a name="dependency-property-name-conventions"></a>相依性屬性命名慣例

相依性屬性有已建立的命名慣例，除非例外情況，否則必須遵循。

相依性屬性本身有基本的名稱，"AquariumGraphic"這個範例中，會指定的第一個參數為<xref:System.Windows.DependencyProperty.Register%2A>。 該名稱在每個登錄類型中都必須是唯一的。 透過基底類型繼承的相依性屬性視為登錄類型的一部分，已繼承屬性的名稱無法再次登錄。 不過，即使不能繼承該相依性屬性，還有一種技巧可將類別新增為相依性屬性的擁有者；如需詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。

當您建立識別碼欄位時，請以登錄屬性時所用名稱命名此欄位，再加上尾碼 `Property`。 這個欄位是您相依性屬性識別碼，而且它將在稍後用做為輸入<xref:System.Windows.DependencyObject.SetValue%2A>和<xref:System.Windows.DependencyObject.GetValue%2A>允許您將會在包裝函式的任何其他程式碼存取您自己的程式碼中，屬性的任何外部程式碼存取您的呼叫屬性系統，也可能是[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器。

> [!NOTE]
> 在類別主體中定義相依性屬性是一般的實作，但也可能在類別靜態建構函式中定義相依性屬性。 如果您需要多行程式碼來初始化相依性屬性，這個方式可能有意義。

<a name="wrapper1"></a>
### <a name="implementing-the-wrapper"></a>實作 "wrapper"

您的包裝函式實作應該呼叫<xref:System.Windows.DependencyObject.GetValue%2A>中`get`實作，並<xref:System.Windows.DependencyObject.SetValue%2A>中`set`（原始的登錄呼叫和欄位會顯示以下太為了清楚起見） 的實作。

在以外的所有例外的情況下，包裝函式實作應該只執行<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>動作，分別。 相關原因討論請參閱 [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)主題。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別中提供的所有現有公用相依性屬性都使用這個簡單的包裝函式實作模型，相依性屬性運作方式最複雜的部分或為固有的屬性系統行為，或為透過其他概念予以實行，例如透過屬性中繼資料的強制型轉或屬性變更回呼。

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

同樣地，依照慣例，包裝函式屬性的名稱必須與所選擇和指定的第一個參數的名稱相同<xref:System.Windows.DependencyProperty.Register%2A>註冊屬性的呼叫。 如果您的屬性不遵循慣例，不一定會停用所有可能的用途，但您會遇到幾個值得注意的問題︰

-   樣式和範本的某些方面不起作用。

-   大部分的工具和設計工具必須依賴命名慣例，才能正確序列化 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，或依屬性層級提供設計工具環境協助。

-   目前的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 載入器實作會略過整個包裝函式，且在處理屬性值時依賴命名慣例。 如需詳細資訊，請參閱 [XAML 相依性屬性](xaml-loading-and-dependency-properties.md)。

<a name="metadata"></a>
### <a name="property-metadata-for-a-new-dependency-property"></a>新相依性屬性的屬性中繼資料

當您登錄相依性屬性時，登錄會透過屬性系統建立儲存屬性特性的中繼資料物件。 許多這些特性都有預設值，如果使用簡單的簽章的已註冊的屬性會設定<xref:System.Windows.DependencyProperty.Register%2A>。 其他的簽章的<xref:System.Windows.DependencyProperty.Register%2A>可讓您指定您想要為您在登錄屬性的中繼資料。 相依性屬性最常指定的中繼資料，是套用在新執行個體的預設值，而新執行個體使用該屬性。

如果您要建立存在的相依性屬性的衍生類別上<xref:System.Windows.FrameworkElement>，您可以使用更具特製化的中繼資料類別<xref:System.Windows.FrameworkPropertyMetadata>而不是基底<xref:System.Windows.PropertyMetadata>類別。 建構函式<xref:System.Windows.FrameworkPropertyMetadata>類別具有幾項特徵標記，您可以在其中組合中指定各種中繼資料特性。 如果您想要指定預設值，使用採用單一參數型別的簽章<xref:System.Object>。 將該物件參數傳遞為屬性的特定型別的預設值 (提供的預設值必須是您提供做為型別`propertyType`中的參數<xref:System.Windows.DependencyProperty.Register%2A>呼叫)。

針對<xref:System.Windows.FrameworkPropertyMetadata>，您也可以為您的屬性指定中繼資料選項旗標。 這些旗標在登錄後會轉換成屬性中繼資料中的個別屬性，用以與版面配置引擎等其他處理序溝通特定條件。

#### <a name="setting-appropriate-metadata-flags"></a>設定適當的中繼資料旗標

-   屬性 （或其值的變更） 會影響[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，並特別會影響版面配置系統應該調整大小，或呈現您的項目在頁面中，如何設定一或多個下列旗標： <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>， <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>， <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>。

    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> 指出此屬性的變更需要變更[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]轉譯，其中包含的物件可能需要增加或減少父代的空間。 例如，"Width" 屬性應該設定此旗標。

    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> 指出此屬性的變更需要變更[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]呈現，通常不需要變更專用的空間，不過，不表示空間中的定位已變更。 例如，"Alignment" 屬性應該設定此旗標。

    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> 指出一些其他的變更發生，不會影響版面配置和測量，但確實需要另一種轉譯。 例如可變更現有項目色彩的 "Background" 等屬性。

    -   這些旗標在您自己的屬性系統或配置回呼覆寫實作中，通常用為中繼資料的通訊協定。 比方說，您可能會有<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>會呼叫的回呼<xref:System.Windows.UIElement.InvalidateArrange%2A>如果執行個體的任何屬性回報值變更，而且擁有<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>做為`true`其中繼資料中。

-   某些屬性會影響包含父項目的轉譯特性，超過前文所述之所需大小的變更。 例如，<xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A>模型中使用非固定格式文件，該屬性的變更可以在其中變更包含段落之非固定格式文件的整體轉譯的屬性。 使用<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange>或<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure>來識別類似的情況下，在您自己的屬性。

-   相依性屬性預設支援資料繫結。 對於沒有任何實際案例可進行資料繫結的情況，或者大型物件的資料繫結效能認定有問題的情況，您可以故意停用資料繫結。

-   根據預設，資料繫結<xref:System.Windows.Data.Binding.Mode%2A>相依性屬性的預設值為<xref:System.Windows.Data.BindingMode.OneWay>。 您可以隨時變更繫結還是<xref:System.Windows.Data.BindingMode.TwoWay>每個繫結執行個體; 如需詳細資訊，請參閱[指定的繫結方向](../data/how-to-specify-the-direction-of-the-binding.md)。 相依性屬性的作者，您可以選擇要使用的屬性，但<xref:System.Windows.Data.BindingMode.TwoWay>預設的繫結模式。 現有的相依性屬性的範例<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; 這個屬性的情況是，<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>設定邏輯和撰寫<xref:System.Windows.Controls.MenuItem>與預設佈景主題樣式互動。 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>屬性邏輯會使用資料繫結原生方式來維護其他狀態屬性和方法呼叫以根據屬性的狀態。 另一個繫結的範例屬性<xref:System.Windows.Data.BindingMode.TwoWay>預設是<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>。

-   您也可以藉由設定來啟用自訂的相依性屬性中的屬性繼承<xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits>旗標。 屬性繼承對父項目和子項目有共同屬性的案例很有用，而且對子項目將特定屬性值設定為和父項目設定的值一樣，才有意義。 繼承屬性的範例是<xref:System.Windows.FrameworkElement.DataContext%2A>，後者用來繫結以啟用重要的主從式案例以呈現資料的作業。 藉由<xref:System.Windows.FrameworkElement.DataContext%2A>可繼承的任何子項目會繼承該資料內容也。 因為屬性值繼承的緣故，您可以指定位在網頁或應用程式根目錄中的資料內容，不需要重新指定即可繫結所有可能的子項目。 <xref:System.Windows.FrameworkElement.DataContext%2A> 也是不錯的範例，說明繼承覆寫預設值，但它可以永遠在本機上設定任何特定的子元素如需詳細資訊，請參閱 <<c0> [ 使用含階層式資料的主從式模式](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。 屬性值繼承確實有可能的效能成本，因此應謹慎使用。如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

-   設定<xref:System.Windows.FrameworkPropertyMetadataOptions.Journal>旗標，指出是否應該偵測到或瀏覽日誌服務所使用的相依性屬性。 例如，<xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>屬性; 在選取項目中選取任何項目巡覽日誌記錄時，就應該保存控制項。

<a name="RODP"></a>
## <a name="read-only-dependency-properties"></a>唯讀相依性屬性

您可以定義唯讀的相依性屬性。 但您為何可能將屬性定義為唯讀的案例有點不同，和向屬性系統登錄它們並公開識別碼的程序一樣。 如需詳細資訊，請參閱[唯讀相依性屬性](read-only-dependency-properties.md)。

<a name="CTDP"></a>
## <a name="collection-type-dependency-properties"></a>集合類型相依性屬性

集合類型相依性屬性要考慮一些其他的實作問題。 如需詳細資訊，請參閱[集合類型相依性屬性](collection-type-dependency-properties.md)。

<a name="SecurityC"></a>
## <a name="dependency-property-security-considerations"></a>相依性屬性安全性考量

相依性屬性應該宣告為公用屬性。 相依性屬性識別碼欄位應該宣告為公用靜態欄位。 即使您嘗試宣告其他存取層級 (例如受保護的)，仍一律可以透過與屬性系統 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 結合的識別項存取相依性屬性。 即使受保護的識別項欄位是可能為可存取，因為中繼資料的報表或值判斷[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]屬於屬性系統，例如<xref:System.Windows.LocalValueEnumerator>。 如需詳細資訊，請參閱[相依性屬性的安全性](dependency-property-security.md)。

<a name="DPCtor"></a>
## <a name="dependency-properties-and-class-constructors"></a>相依性屬性和類別建構函式

Managed 程式碼程式設計中有項一般原則 (通常由 FxCop 等程式碼分析工具強制執行)，類別建構函式不應該呼叫虛擬方法。 這是因為建構函式可以呼叫為衍生類別建構函式的基底初始化，而透過建構函式進入虛擬方法，可能會發生在建構中的物件執行個體尚未完全初始化的狀態。 當您衍生自任何衍生自的類別<xref:System.Windows.DependencyObject>，您應該要知道屬性系統本身呼叫，並在內部公開虛擬方法。 這些虛擬方法都屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統服務。 覆寫方法可讓衍生的類別參與值判斷。 若要避免執行階段初始化可能發生的問題，您不應該在類別的建構函式中設定相依性屬性值，除非您遵循非常明確的建構函式模式。 如需詳細資訊，請參閱 [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)。

## <a name="see-also"></a>另請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [相依性屬性中繼資料](dependency-property-metadata.md)
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [集合類型的相依性屬性](collection-type-dependency-properties.md)
- [相依性屬性的安全性](dependency-property-security.md)
- [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)
- [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)