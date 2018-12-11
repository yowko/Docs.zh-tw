---
title: 附加屬性概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: bcf218efeb7bff5f7457164411efed796314ba82
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129476"
---
# <a name="attached-properties-overview"></a>附加屬性概觀

附加屬性是透過 XAML 所定義的概觀。 附加屬性是要用作可在任何物件上設定的全域屬性類型。 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，附加屬性一般會定義為沒有傳統屬性「包裝函式」的特殊形式相依性屬性。

## 必要條件 <a name="prerequisites"></a>

本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。 若要遵循本主題中的範例，您也應該了解 XAML 並知道如何撰寫 WPF 應用程式。

## 為何使用附加的屬性 <a name="attached_properties_usage"></a>

附加屬性的其中一個用途是允許不同的子項目指定父項目中實際定義的屬性的唯一值。 此情節的特定應用程式可讓子項目通知父項目，有關如何在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中呈現它們。 其中一個範例是<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>屬性。 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>屬性會建立為附加屬性，因為它設計成內所包含的項目上設定<xref:System.Windows.Controls.DockPanel>，而非在<xref:System.Windows.Controls.DockPanel>本身。 <xref:System.Windows.Controls.DockPanel>類別會定義靜態<xref:System.Windows.DependencyProperty>名為欄位<xref:System.Windows.Controls.DockPanel.DockProperty>，然後提供<xref:System.Windows.Controls.DockPanel.GetDock%2A>和<xref:System.Windows.Controls.DockPanel.SetDock%2A>附加屬性的公用存取子方法。

## XAML 中的附加的屬性 <a name="attached_properties_xaml"></a>

在 XAML 中，您可以使用 *AttachedPropertyProvider*.<屬性名稱> 語法來設定附加屬性。

以下是如何您也可以設定的範例<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>在 XAML 中：

[!code-xaml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

請注意，使用方式有點類似靜態屬性;您永遠參考型別<xref:System.Windows.Controls.DockPanel>所擁有且註冊附加的屬性，而不是參考依名稱指定任何執行個體。

此外，因為 XAML 中的附加屬性是您在標記中設定的屬性，所以只有設定作業才會有任何相關性。 雖然有一些間接機制可比較值 (例如樣式中的觸發程序)，但是您無法在 XAML 中直接取得屬性 (如需詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md))。

### <a name="attached-property-implementation-in-wpf"></a>WPF 中的附加屬性實作

在  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]，大部分的存在於 UI 呈現相關的 WPF 類型的附加屬性都會實作為相依性屬性。 附加的屬性是 XAML 概念，而相依性屬性是 WPF 的概念。 WPF 附加屬性是相依性屬性，因為它們支援相依性屬性概念，例如屬性中繼資料，並從該屬性中繼資料的預設值。

## 如何使用附加的屬性的擁有者類型 <a name="howused"></a>

雖然可在任何物件上設定附加屬性，但是這不自動表示設定屬性就會產生明確結果，或者另一個物件將使用值。 一般而言，會使用附加屬性，讓來自各種可能類別階層或邏輯關聯性的物件都可以報告可定義附加屬性之類型的通用資訊。 可定義附加屬性的類型通常會遵循下列其中一個模型︰

-   設計可定義附加屬性的類型，因此它可以是設定附加屬性值之項目的父項目。 類型接著會透過內部邏輯針對某個物件樹狀結構逐一查看其子物件，並取得值，然後以某種方式處理這些值。

-   可定義附加屬性的類型將會用作各種可能父項目和內容模組的子項目。

-   可定義附加屬性的類型代表服務。 其他類型設定附加屬性的值。 然後，在服務內容中評估可設定屬性的項目時，會透過服務類別的內部邏輯取得附加屬性值。

### <a name="an-example-of-a-parent-defined-attached-property"></a>父代已定義的附加屬性範例

WPF 定義附加的屬性的地方的最常見案例是當父項目支援子項目集合，而且也會實作行為，其中的細節的行為會個別報告每個子項目。

<xref:System.Windows.Controls.DockPanel> 定義<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>附加屬性，並<xref:System.Windows.Controls.DockPanel>具有類別層級程式碼作為其轉譯邏輯的一部分 (具體而言，<xref:System.Windows.Controls.DockPanel.MeasureOverride%2A>和<xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>)。 A<xref:System.Windows.Controls.DockPanel>執行個體一律會檢查以確認是否立即其子元素的任何已設定的值<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>。 如果是這樣，這些值會變成套用至該特定子項目之轉譯邏輯的輸入。 巢狀<xref:System.Windows.Controls.DockPanel>執行個體都會處理它們自己的直屬子項目集合，但該行為是實作特定如何<xref:System.Windows.Controls.DockPanel>處理程序<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>值。 理論上，可能會有附加屬性影響直屬父代以外的項目。 如果<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>沒有任何項目上設定附加的屬性<xref:System.Windows.Controls.DockPanel>父項目，可處理在它、 任何錯誤或例外狀況時，就會引發。 這只是表示已設定全域屬性值，但它有沒有目前<xref:System.Windows.Controls.DockPanel>使用這項資訊的父代。

## 在程式碼中的附加的屬性 <a name="attached_properties_code"></a>

在 WPF 中的附加的屬性沒有一般[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]簡單的 get/set 存取的 「 包裝函式 」 方法。 這是因為附加屬性不一定屬於已設定屬性之執行個體的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 命名空間。 不過，XAML 處理器必須可以在剖析 XAML 時設定這些值。 若要支援有效的附加的屬性使用方式，該附加屬性的擁有者類型必須在表單中實作專用存取子方法**Get_PropertyName_** 並**Set_PropertyName_**。 這些專用存取子方法也適用於取得或設定程式碼中的附加屬性。 從程式碼觀點，附加屬性類似具有方法存取子而非屬性存取子的支援欄位，而且該支援欄位可以存在於任何物件，而不需要特別進行定義。

下列範例示範如何在程式碼中設定附加屬性。 在此範例中，`myCheckBox`的執行個體<xref:System.Windows.Controls.CheckBox>類別。

[!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

類似於 XAML 情況下，如果`myCheckBox`有尚未新增為子元素`myDockPanel`由第三行程式碼，程式碼的第四行不會引發例外狀況，但屬性值不會與互動<xref:System.Windows.Controls.DockPanel>父代，因此會執行任何動作。 只有<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>值的結合出現與否的子項目設定<xref:System.Windows.Controls.DockPanel>父項目會造成轉譯應用程式的有效的行為。 (在此情況下，您可以設定附加屬性，然後將其附加至樹狀結構。 或者，您可以將其附加至樹狀結構，然後設定附加屬性。 任一個動作順序都會提供相同的結果)。

## 附加的屬性中繼資料 <a name="attached_properties_metadata"></a>

註冊屬性時<xref:System.Windows.FrameworkPropertyMetadata>設為指定的屬性，例如屬性是否影響轉譯、 測量和等等的特性。 附加屬性的中繼資料一般與相依性屬性並無不同。 如果您在附加屬性中繼資料的覆寫中指定預設值，該值會變成覆寫類別執行個體上的隱含附加屬性預設值。 具體而言，如果某個處理序透過該屬性的 `Get` 方法存取子來查詢附加屬性值，並指定已指定中繼資料之類別的執行個體，則會報告預設值，否則不會設定該附加屬性的值。

如果您想要啟用屬性的屬性值繼承，則應該使用附加屬性，而不是使用非附加相依性屬性。 如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。

## 自訂附加屬性 <a name="custom"></a>

### 何時建立附加的屬性 <a name="create_attached_properties"></a>

非定義類別的類別需要有可用的屬性設定機制時，您可以建立附加屬性。 最常見的案例是配置。 現有配置屬性的範例包括<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>，和<xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>。 在這裡啟用的情節是本身為配置控制項目之子項目的項目可以個別表達其配置父項目的配置需求，且各會設定父代定義為附加屬性的屬性值。

另一個使用附加屬性的情節是類別代表一項服務，而且想要類別能夠更緊密地整合服務。

但另一個案例是收到 Visual Studio WPF 設計工具支援，例如**屬性**視窗編輯。 如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。

如前所述，如果您想要使用屬性值繼承，則應該註冊為附加屬性。

### 如何建立附加的屬性 <a name="how_do_i_create_attached_properties"></a>

如果您的類別會定義使用嚴格的附加的屬性上其他類型，則不需要衍生自類別<xref:System.Windows.DependencyObject>。 但您必須衍生自<xref:System.Windows.DependencyObject>如果您遵循將附加的屬性，也相依性屬性的整體 WPF 模型。

將附加的屬性定義為相依性屬性，藉由宣告`public static readonly`型別的欄位<xref:System.Windows.DependencyProperty>。 您使用的傳回值來定義此欄位<xref:System.Windows.DependencyProperty.RegisterAttached%2A>方法。 欄位名稱必須符合的附加的屬性名稱，加上字串`Property`，以遵循命名識別欄位，與它們所代表的屬性建立的 WPF 模式。 附加的屬性提供者也必須提供靜態**Get_PropertyName_** 並**Set_PropertyName_** 附加的屬性; 當做存取子方法失敗，若要這樣做會導致屬性系統無法使用您的附加的屬性。

> [!NOTE]
> 如果您省略附加的屬性的 get 存取子，在屬性上的資料繫結無法在設計工具，例如 Visual Studio 和 Expression Blend。

#### <a name="the-get-accessor"></a>Get 存取子

簽章**Get_PropertyName_** 存取子必須是：

`public static object GetPropertyName(object target)`

-   `target` 物件可以指定為實作中的更特定類型。 例如，<xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType>方法類型參數做為<xref:System.Windows.UIElement>，因為附加的屬性只是要在設定<xref:System.Windows.UIElement>執行個體。

-   傳回值可以指定為實作中的更特定類型。 例如，<xref:System.Windows.Controls.DockPanel.GetDock%2A>方法型別為<xref:System.Windows.Controls.Dock>，因為值只能設定為該列舉。

#### <a name="the-set-accessor"></a>Set 存取子

簽章**Set_PropertyName_** 存取子必須是：

`public static void SetPropertyName(object target, object value)`

-   `target` 物件可以指定為實作中的更特定類型。 例如，<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法型別為<xref:System.Windows.UIElement>，因為附加的屬性只是要在設定<xref:System.Windows.UIElement>執行個體。

-   `value` 物件可以指定為實作中的更特定類型。 例如，<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法型別為<xref:System.Windows.Controls.Dock>，因為值只能設定為該列舉。 請記住，當這個方法在標記的附加屬性使用方式中遇到附加屬性時，其值是來自 XAML 載入器的輸入。 該輸入是指定為標記中 XAML 屬性值的值。 因此，您使用的類型必須要有類型轉換、值序列化程式或標記延伸支援，因此，可以從屬性值 (這最後就是一個字串) 建立適當的類型。

下列範例示範相依性屬性註冊 (使用<xref:System.Windows.DependencyProperty.RegisterAttached%2A>方法)，以及**Get_PropertyName_** 並**Set_PropertyName_** 存取子。 在此範例中，附加屬性名稱為 `IsBubbleSource`。 因此，存取子必須命名為 `GetIsBubbleSource` 和 `SetIsBubbleSource`。

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>附加屬性 (property) 的屬性 (attribute)

WPF 定義數個[!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)]，要提供給反映程序，並反映和屬性的資訊，例如設計工具的一般使用者的附加屬性的相關資訊。 因為附加屬性的類型為無限制範圍，所以設計人員需要方法來避免使用 XAML 的特定技術實作中所定義之所有附加屬性的全域清單，讓使用者無所適從。 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)]該 WPF 定義附加的屬性可以用來限定範圍的情況，其中指定的附加的屬性應該會顯示在 [屬性] 視窗。 您也可以考慮針對您自己的自訂附加屬性套用這些屬性。 適當的參考頁面會描述 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] 的用途和語法：

-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## 深入了解附加屬性 <a name="more"></a>

-   如需建立附加屬性的詳細資訊，請參閱[註冊附加屬性](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)。

-   如需相依性屬性和附加屬性的更進階使用方式情節，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。

-   您也可以將屬性註冊為附加屬性和相依性屬性，但仍公開「包裝函式」實作。 在此情況下，可以在該項目上設定屬性，或透過 XAML 附加屬性語法的任何項目上設定屬性。 舉例來說，標準和附加使用方式之適當情節的屬性是<xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.DependencyProperty>
- [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [註冊附加屬性](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)