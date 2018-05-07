---
title: 附加屬性概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 626cc0a5ddb1ba51be14eb045bcedcf7574cfb11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="attached-properties-overview"></a>附加屬性概觀
附加屬性是透過 XAML 所定義的概觀。 附加屬性是要用作可在任何物件上設定的全域屬性類型。 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，附加屬性一般會定義為沒有傳統屬性「包裝函式」的特殊形式相依性屬性。  
  
   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。 若要遵循本主題中的範例，您也應該了解 XAML 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="attached_properties_usage"></a>   
## <a name="why-use-attached-properties"></a>為何使用附加屬性  
 附加屬性的其中一個用途是允許不同的子項目指定父項目中實際定義的屬性的唯一值。 此情節的特定應用程式可讓子項目通知父項目，有關如何在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中呈現它們。 其中一個範例是<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>屬性。 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>因為其設計目的是要在設定內所包含的項目，將會建立為附加屬性的屬性<xref:System.Windows.Controls.DockPanel>，而非在<xref:System.Windows.Controls.DockPanel>本身。 <xref:System.Windows.Controls.DockPanel>類別會定義靜態<xref:System.Windows.DependencyProperty>名為欄位<xref:System.Windows.Controls.DockPanel.DockProperty>，然後提供<xref:System.Windows.Controls.DockPanel.GetDock%2A>和<xref:System.Windows.Controls.DockPanel.SetDock%2A>附加屬性的公用存取子方法。  
  
<a name="attached_properties_xaml"></a>   
## <a name="attached-properties-in-xaml"></a>XAML 中的附加屬性  
 在 XAML 中，您可以使用 *AttachedPropertyProvider*.<屬性名稱> 語法來設定附加屬性。  
  
 以下是您可以設定的範例<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>在 XAML 中：  
  
 [!code-xaml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]  
  
 請注意，使用類似的靜態屬性;您一律參考型別<xref:System.Windows.Controls.DockPanel>所擁有，且註冊附加的屬性，而不是參考到依名稱指定任何執行個體。  
  
 此外，因為 XAML 中的附加屬性是您在標記中設定的屬性，所以只有設定作業才會有任何相關性。 雖然有一些間接機制可比較值 (例如樣式中的觸發程序)，但是您無法在 XAML 中直接取得屬性 (如需詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md))。  
  
### <a name="attached-property-implementation-in-wpf"></a>WPF 中的附加屬性實作  
 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，存在於 UI 呈現相關 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類型的大部分附加屬性都會實作為相依性屬性。 附加屬性是 XAML 概念，而相依性屬性是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 概念。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加屬性是相依性屬性，因此支援屬性中繼資料這類相依性屬性概念，以及從該屬性中繼資料中的預設值。  
  
<a name="howused"></a>   
## <a name="how-attached-properties-are-used-by-the-owning-type"></a>擁有者類型如何使用附加屬性  
 雖然可在任何物件上設定附加屬性，但是這不自動表示設定屬性就會產生明確結果，或者另一個物件將使用值。 一般而言，會使用附加屬性，讓來自各種可能類別階層或邏輯關聯性的物件都可以報告可定義附加屬性之類型的通用資訊。 可定義附加屬性的類型通常會遵循下列其中一個模型︰  
  
-   設計可定義附加屬性的類型，因此它可以是設定附加屬性值之項目的父項目。 類型接著會透過內部邏輯針對某個物件樹狀結構逐一查看其子物件，並取得值，然後以某種方式處理這些值。  
  
-   可定義附加屬性的類型將會用作各種可能父項目和內容模組的子項目。  
  
-   可定義附加屬性的類型代表服務。 其他類型設定附加屬性的值。 然後，在服務內容中評估可設定屬性的項目時，會透過服務類別的內部邏輯取得附加屬性值。  
  
### <a name="an-example-of-a-parent-defined-attached-property"></a>父代已定義的附加屬性範例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義附加屬性的最常見情節是父項目支援子項目集合，同時實作會個別報告每個子項目之行為細節的行為。  
  
 <xref:System.Windows.Controls.DockPanel> 定義<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>附加屬性，以及<xref:System.Windows.Controls.DockPanel>具有類別層級程式碼做為其呈現邏輯的一部分 (具體而言，<xref:System.Windows.Controls.DockPanel.MeasureOverride%2A>和<xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>)。 A<xref:System.Windows.Controls.DockPanel>執行個體一律會檢查以查看是否任一其直屬子系項目已設定的值<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>。 如果是這樣，這些值會變成套用至該特定子項目之轉譯邏輯的輸入。 巢狀<xref:System.Windows.Controls.DockPanel>每一個執行個體都將視為自己的當前子系項目集合，但該行為是依實作方式<xref:System.Windows.Controls.DockPanel>處理程序<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>值。 理論上，可能會有附加屬性影響直屬父代以外的項目。 如果<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>之中未包含任何項目上設定附加的屬性<xref:System.Windows.Controls.DockPanel>採取它、 任何錯誤或例外狀況的父項目，就會引發。 這只是表示已設定全域屬性值，但它有沒有目前<xref:System.Windows.Controls.DockPanel>無法使用該資訊的父代。  
  
<a name="attached_properties_code"></a>   
## <a name="attached-properties-in-code"></a>程式碼中的附加屬性  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的附加屬性沒有一般 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]「包裝函式」方法可輕鬆進行 get/set 存取。 這是因為附加屬性不一定屬於已設定屬性之執行個體的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 命名空間。 不過，XAML 處理器必須可以在剖析 XAML 時設定這些值。 若要支援有效的附加屬性使用方式，附加屬性的擁有者類型必須在表單 <屬性名稱>`Get` 和 <屬性名稱>`Set` 中實作專用存取子方法。 這些專用存取子方法也適用於取得或設定程式碼中的附加屬性。 從程式碼觀點，附加屬性類似具有方法存取子而非屬性存取子的支援欄位，而且該支援欄位可以存在於任何物件，而不需要特別進行定義。  
  
 下列範例示範如何在程式碼中設定附加屬性。 在此範例中，`myCheckBox`的執行個體<xref:System.Windows.Controls.CheckBox>類別。  
  
 [!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
 [!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]  
  
 XAML 類似情況下，如果`myCheckBox`不已經加入為的子元素`myDockPanel`由程式碼的第三行，第四個一行程式碼不會引發例外狀況，但屬性值都不會互動<xref:System.Windows.Controls.DockPanel>父代，因此會執行任何動作。 只有<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>值的設定結合的子項目<xref:System.Windows.Controls.DockPanel>父項目會使得轉譯的應用程式中的有效的行為。 (在此情況下，您可以設定附加屬性，然後將其附加至樹狀結構。 或者，您可以將其附加至樹狀結構，然後設定附加屬性。 任一個動作順序都會提供相同的結果)。  
  
<a name="attached_properties_metadata"></a>   
## <a name="attached-property-metadata"></a>附加屬性中繼資料  
 註冊屬性時<xref:System.Windows.FrameworkPropertyMetadata>設為指定的屬性，例如的屬性是否會影響轉譯、 度量，以及其他特性。 附加屬性的中繼資料一般與相依性屬性並無不同。 如果您在附加屬性中繼資料的覆寫中指定預設值，該值會變成覆寫類別執行個體上的隱含附加屬性預設值。 具體而言，如果某個處理序透過該屬性的 `Get` 方法存取子來查詢附加屬性值，並指定已指定中繼資料之類別的執行個體，則會報告預設值，否則不會設定該附加屬性的值。  
  
 如果您想要啟用屬性的屬性值繼承，則應該使用附加屬性，而不是使用非附加相依性屬性。 如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
<a name="custom"></a>   
## <a name="custom-attached-properties"></a>自訂附加屬性  
  
<a name="create_attached_properties"></a>   
### <a name="when-to-create-an-attached-property"></a>何時建立附加屬性  
 非定義類別的類別需要有可用的屬性設定機制時，您可以建立附加屬性。 最常見的案例是配置。 現有的版面配置屬性的範例包括<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>，和<xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>。 在這裡啟用的情節是本身為配置控制項目之子項目的項目可以個別表達其配置父項目的配置需求，且各會設定父代定義為附加屬性的屬性值。  
  
 另一個使用附加屬性的情節是類別代表一項服務，而且想要類別能夠更緊密地整合服務。  
  
 但另一個情節是獲得 [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] 支援，例如 [屬性] 視窗編輯。 如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
 如前所述，如果您想要使用屬性值繼承，則應該註冊為附加屬性。  
  
<a name="how_do_i_create_attached_properties"></a>   
### <a name="how-to-create-an-attached-property"></a>如何建立附加屬性  
 如果您的類別會定義使用嚴格的附加的屬性上其他類型，則不需要是衍生自類別<xref:System.Windows.DependencyObject>。 但您需要以衍生自<xref:System.Windows.DependencyObject>如果遵循整體[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]讓您附加的屬性的模型也是相依性屬性。  
  
 您附加的屬性定義為相依性屬性，藉由宣告`public` `static` `readonly`欄位型別的<xref:System.Windows.DependencyProperty>。 您使用的傳回值來定義此欄位<xref:System.Windows.DependencyProperty.RegisterAttached%2A>方法。 欄位名稱必須符合附加 `Property` 字串的附加屬性名稱，以遵循命名識別欄位與其所代表屬性的已建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 模式。 附加屬性提供者也必須提供靜態 `Get`<屬性名稱> 和 `Set`<屬性名稱> 方法作為附加屬性的存取子；無法這麼做會導致屬性系統無法使用您的附加屬性。  
  
> [!NOTE]
>  如果您省略附加的屬性 get 存取子，屬性的資料繫結將不適用於設計工具，例如 Visual Studio 和 Expression Blend。  
  
#### <a name="the-get-accessor"></a>Get 存取子  
 `Get`<屬性名稱> 存取子的簽章必須是︰  
  
 `public static object Get` <屬性名稱> `(object`  `target` `)`  
  
-   `target` 物件可以指定為實作中的更特定類型。 例如，<xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType>方法類型參數做為<xref:System.Windows.UIElement>，因為附加的屬性只是要在設定<xref:System.Windows.UIElement>執行個體。  
  
-   傳回值可以指定為實作中的更特定類型。 例如，<xref:System.Windows.Controls.DockPanel.GetDock%2A>方法類型，做為<xref:System.Windows.Controls.Dock>，因為值只可以將該列舉型別。  
  
#### <a name="the-set-accessor"></a>Set 存取子  
 `Set`<屬性名稱> 存取子的簽章必須是︰  
  
 `public static void Set` <屬性名稱> `(object`  `target` `, object`  `value` `)`  
  
-   `target` 物件可以指定為實作中的更特定類型。 例如，<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法類型，做為<xref:System.Windows.UIElement>，因為附加的屬性只是要在設定<xref:System.Windows.UIElement>執行個體。  
  
-   `value` 物件可以指定為實作中的更特定類型。 例如，<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法類型，做為<xref:System.Windows.Controls.Dock>，因為值只可以將該列舉型別。 請記住，當這個方法在標記的附加屬性使用方式中遇到附加屬性時，其值是來自 XAML 載入器的輸入。 該輸入是指定為標記中 XAML 屬性值的值。 因此，您使用的類型必須要有類型轉換、值序列化程式或標記延伸支援，因此，可以從屬性值 (這最後就是一個字串) 建立適當的類型。  
  
 下列範例示範相依性屬性註冊 (使用<xref:System.Windows.DependencyProperty.RegisterAttached%2A>方法)，並將`Get` *PropertyName*和`Set` *PropertyName*存取子. 在此範例中，附加屬性名稱為 `IsBubbleSource`。 因此，存取子必須命名為 `GetIsBubbleSource` 和 `SetIsBubbleSource`。  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
#### <a name="attached-property-attributes"></a>附加屬性 (property) 的屬性 (attribute)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義數個 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)]，以將附加屬性相關資訊提供給反映程序以及一般反映和屬性資訊使用者，例如設計工具。 因為附加屬性的類型為無限制範圍，所以設計人員需要方法來避免使用 XAML 的特定技術實作中所定義之所有附加屬性的全域清單，讓使用者無所適從。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 針對附加屬性所定義的 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] 可以用來限定所指定附加屬性應該顯示在屬性視窗中的情況。 您也可以考慮針對您自己的自訂附加屬性套用這些屬性。 適當的參考頁面會描述 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] 的用途和語法：  
  
-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>  
  
<a name="more"></a>   
## <a name="learning-more-about-attached-properties"></a>深入了解附加屬性  
  
-   如需建立附加屬性的詳細資訊，請參閱[註冊附加屬性](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)。  
  
-   如需相依性屬性和附加屬性的更進階使用方式情節，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  
  
-   您也可以將屬性註冊為附加屬性和相依性屬性，但仍公開「包裝函式」實作。 在此情況下，可以在該項目上設定屬性，或透過 XAML 附加屬性語法的任何項目上設定屬性。 舉例來說，具有適當的案例來設定標準和附加使用方式的屬性是<xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.DependencyProperty>  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [註冊附加屬性](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)
