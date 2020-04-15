---
title: 附加屬性概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 5086401f4616074d364c1d387b751116120d5969
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389005"
---
# <a name="attached-properties-overview"></a>附加屬性概觀

附加屬性是透過 XAML 所定義的概觀。 附加屬性是要用作可在任何物件上設定的全域屬性類型。 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，附加屬性一般會定義為沒有傳統屬性「包裝函式」的特殊形式相依性屬性。

## <a name="prerequisites"></a>先決條件<a name="prerequisites"></a>

本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)。 要遵循本主題中的範例,您還應瞭解 XAML 並瞭解如何編寫 WPF 應用程式。

## <a name="why-use-attached-properties"></a>為什麼使用額外屬性<a name="attached_properties_usage"></a>

附加屬性的其中一個用途是允許不同的子項目指定父項目中實際定義的屬性的唯一值。 此情節的特定應用程式可讓子項目通知父項目，有關如何在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中呈現它們。 屬性就是一<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>個示例。 該<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>屬性創建為附加屬性,因為它被設計為設置為在中包含<xref:System.Windows.Controls.DockPanel>的 元素上,而不是<xref:System.Windows.Controls.DockPanel>本身。 類<xref:System.Windows.Controls.DockPanel><xref:System.Windows.DependencyProperty>定義<xref:System.Windows.Controls.DockPanel.DockProperty>名為 的靜態欄位,然後作為附加屬性<xref:System.Windows.Controls.DockPanel.GetDock%2A>的<xref:System.Windows.Controls.DockPanel.SetDock%2A>公共 訪問 器提供 和 方法。

## <a name="attached-properties-in-xaml"></a>XAML 中的額外屬性<a name="attached_properties_xaml"></a>

在 XAML 中，您可以使用 *AttachedPropertyProvider*.<屬性名稱>** 語法來設定附加屬性。

以下是如何在 XAML<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>中設定 的範例:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

請注意,使用法與靜態屬性有些類似;您始終引用擁有並<xref:System.Windows.Controls.DockPanel>註冊附加屬性的類型,而不是引用名稱指定的任何實例。

此外，因為 XAML 中的附加屬性是您在標記中設定的屬性，所以只有設定作業才會有任何相關性。 雖然有一些間接機制可比較值 (例如樣式中的觸發程序)，但是您無法在 XAML 中直接取得屬性 (如需詳細資訊，請參閱[設定樣式和範本](../controls/styling-and-templating.md))。

### <a name="attached-property-implementation-in-wpf"></a>WPF 中的附加屬性實作

在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]中,WPF 類型中存在的大多數與UI表示相關的附加屬性都作為依賴項屬性實現。 附加屬性是 XAML 概念,而依賴項屬性是 WPF 概念。 由於 WPF 附加屬性是依賴項屬性,因此它們支援依賴項屬性概念,如屬性元數據和來自該屬性元數據的預設值。

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>擁有類型如何使用額外屬性<a name="howused"></a>

雖然可在任何物件上設定附加屬性，但是這不自動表示設定屬性就會產生明確結果，或者另一個物件將使用值。 一般而言，會使用附加屬性，讓來自各種可能類別階層或邏輯關聯性的物件都可以報告可定義附加屬性之類型的通用資訊。 可定義附加屬性的類型通常會遵循下列其中一個模型︰

- 設計可定義附加屬性的類型，因此它可以是設定附加屬性值之項目的父項目。 類型接著會透過內部邏輯針對某個物件樹狀結構逐一查看其子物件，並取得值，然後以某種方式處理這些值。

- 可定義附加屬性的類型將會用作各種可能父項目和內容模組的子項目。

- 可定義附加屬性的類型代表服務。 其他類型設定附加屬性的值。 然後，在服務內容中評估可設定屬性的項目時，會透過服務類別的內部邏輯取得附加屬性值。

### <a name="an-example-of-a-parent-defined-attached-property"></a>父代已定義的附加屬性範例

WPF 定義附加屬性的最典型方案是父元素支援子元素集合,並實現一種行為,其中為每個子元素單獨報告行為的特定部分。

<xref:System.Windows.Controls.DockPanel>定義<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>附加的屬性,<xref:System.Windows.Controls.DockPanel>並將 類級代碼作為其呈現邏輯的一部分(<xref:System.Windows.Controls.DockPanel.MeasureOverride%2A><xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>特別是和)。 實例<xref:System.Windows.Controls.DockPanel>將始終檢查其任何直接子元素是否已<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>為 設置值。 如果是這樣，這些值會變成套用至該特定子項目之轉譯邏輯的輸入。 嵌套<xref:System.Windows.Controls.DockPanel>實例每個實例都處理其自己的直接子元素集合,但該行為特定於<xref:System.Windows.Controls.DockPanel><xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>流程 值的方式。 理論上，可能會有附加屬性影響直屬父代以外的項目。 如果<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>附加屬性設置在<xref:System.Windows.Controls.DockPanel>沒有 父元素的元素上,則不引發任何錯誤或異常。 這僅僅意味著設置了全域屬性值,但它沒有可以使用資訊的當前<xref:System.Windows.Controls.DockPanel>父級。

## <a name="attached-properties-in-code"></a>程式碼中的額外屬性<a name="attached_properties_code"></a>

WPF 中的附加屬性沒有典型的 CLR"包裝器"方法,便於獲取/設置訪問。 這是因為附加屬性不一定是設置該屬性的實例的 CLR 命名空間的一部分。 不過，XAML 處理器必須可以在剖析 XAML 時設定這些值。 為了支援有效的附加屬性使用,附加屬性的擁有者類型必須在**Get_PropertyName_** 和**Set_PropertyName_** 的形式實現專用訪問器方法。 這些專用存取子方法也適用於取得或設定程式碼中的附加屬性。 從程式碼觀點，附加屬性類似具有方法存取子而非屬性存取子的支援欄位，而且該支援欄位可以存在於任何物件，而不需要特別進行定義。

下列範例示範如何在程式碼中設定附加屬性。 在此範例中,`myCheckBox`是類<xref:System.Windows.Controls.CheckBox>的 實體。

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

與 XAML 案例`myCheckBox`類似, 如果第四行代碼尚未`myDockPanel`添加為子 元素,則第五行代碼不會引發異常,但<xref:System.Windows.Controls.DockPanel>屬性值不會與 父級交互,因此將不執行任何操作。 只有子<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>元素上設置的值<xref:System.Windows.Controls.DockPanel>與 父元素的存在相結合,才會在呈現的應用程式中產生有效的行為。 (在此情況下，您可以設定附加屬性，然後將其附加至樹狀結構。 或者，您可以將其附加至樹狀結構，然後設定附加屬性。 任一個動作順序都會提供相同的結果)。

## <a name="attached-property-metadata"></a>附加屬性中繼資料<a name="attached_properties_metadata"></a>

註冊屬性時,<xref:System.Windows.FrameworkPropertyMetadata>將設置為指定屬性的特徵,例如屬性是否影響渲染、測量等。 附加屬性的中繼資料一般與相依性屬性並無不同。 如果您在附加屬性中繼資料的覆寫中指定預設值，該值會變成覆寫類別執行個體上的隱含附加屬性預設值。 具體而言，如果某個處理序透過該屬性的 `Get` 方法存取子來查詢附加屬性值，並指定已指定中繼資料之類別的執行個體，則會報告預設值，否則不會設定該附加屬性的值。

如果您想要啟用屬性的屬性值繼承，則應該使用附加屬性，而不是使用非附加相依性屬性。 如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

## <a name="custom-attached-properties"></a>自訂附加屬性<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>何時建立額外屬性<a name="create_attached_properties"></a>

非定義類別的類別需要有可用的屬性設定機制時，您可以建立附加屬性。 最常見的案例是配置。 現有佈局屬性的範例包括<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> 。 在這裡啟用的情節是本身為配置控制項目之子項目的項目可以個別表達其配置父項目的配置需求，且各會設定父代定義為附加屬性的屬性值。

另一個使用附加屬性的情節是類別代表一項服務，而且想要類別能夠更緊密地整合服務。

另一種方案是接收可視化工作室 WPF 設計器支援,如**屬性**視窗編輯。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。

如前所述，如果您想要使用屬性值繼承，則應該註冊為附加屬性。

### <a name="how-to-create-an-attached-property"></a>如何建立額外屬性<a name="how_do_i_create_attached_properties"></a>

如果類嚴格定義附加屬性以用於其他類型,則類不必派生自<xref:System.Windows.DependencyObject>。 但是,如果遵循具有附加屬性<xref:System.Windows.DependencyObject>也是依賴項屬性的整體 WPF 模型,則需要派生。

通過聲明類型`public static readonly`<xref:System.Windows.DependencyProperty>欄位,將附加屬性定義為依賴項屬性。 使用<xref:System.Windows.DependencyProperty.RegisterAttached%2A>方法的返回值定義此欄位。 欄位名稱必須與附加的屬性名稱(隨字串`Property`一起追加)匹配,才能遵循已建立的 WPF 模式來命名標識欄位和它們表示的屬性。 附加屬性提供程式還必須提供靜態**Get_PropertyName_** 和**Set_PropertyName_** 方法作為附加屬性的訪問器;如果不這樣做,將導致屬性系統無法使用附加屬性。

> [!NOTE]
> 如果省略附加屬性的 get 訪問器,則屬性上的數據綁定在設計工具中不起作用,例如 Visual Studio 和 Visual Studio 的 Blend。

#### <a name="the-get-accessor"></a>Get 存取子

**Get_PropertyName_** 存取器的簽名必須:

`public static object GetPropertyName(object target)`

- `target` 物件可以指定為實作中的更特定類型。 例如,<xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType>該方法將參數類型<xref:System.Windows.UIElement>為 ,因為附加的屬性僅用於在實<xref:System.Windows.UIElement>例上 設置。

- 傳回值可以指定為實作中的更特定類型。 例如,<xref:System.Windows.Controls.DockPanel.GetDock%2A>方法將其類型<xref:System.Windows.Controls.Dock>為 ,因為該值只能設置為該枚舉。

#### <a name="the-set-accessor"></a>Set 存取子

**Set_PropertyName_** 存取器的簽章必須:

`public static void SetPropertyName(object target, object value)`

- `target` 物件可以指定為實作中的更特定類型。 例如,<xref:System.Windows.Controls.DockPanel.SetDock%2A>該方法將其鍵入<xref:System.Windows.UIElement>為 ,因為附加的屬性僅用於在實<xref:System.Windows.UIElement>例上 設置。

- `value` 物件可以指定為實作中的更特定類型。 例如,<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法將其類型<xref:System.Windows.Controls.Dock>為 ,因為該值只能設置為該枚舉。 請記住，當這個方法在標記的附加屬性使用方式中遇到附加屬性時，其值是來自 XAML 載入器的輸入。 該輸入是指定為標記中 XAML 屬性值的值。 因此，您使用的類型必須要有類型轉換、值序列化程式或標記延伸支援，因此，可以從屬性值 (這最後就是一個字串) 建立適當的類型。

下面的範例顯示依賴項屬性註冊(使用方法<xref:System.Windows.DependencyProperty.RegisterAttached%2A>),以及**Get_PropertyName_** 和**訪問者Set_PropertyName_。** 在此範例中，附加屬性名稱為 `IsBubbleSource`。 因此，存取子必須命名為 `GetIsBubbleSource` 和 `SetIsBubbleSource`。

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>附加屬性 (property) 的屬性 (attribute)

WPF 定義多個 .NET 屬性,用於提供有關反射進程附加屬性的資訊,以及反射和屬性資訊的典型使用者(如設計器)。 因為附加屬性的類型為無限制範圍，所以設計人員需要方法來避免使用 XAML 的特定技術實作中所定義之所有附加屬性的全域清單，讓使用者無所適從。 WPF 為附加屬性定義的 .NET 屬性可用於限定給定附加屬性應在屬性視窗中顯示的情況。 您也可以考慮針對您自己的自訂附加屬性套用這些屬性。 .NET 屬性的用途和語法在相應的參考頁上描述:

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>瞭解有關額外屬性的更多<a name="more"></a>

- 如需建立附加屬性的詳細資訊，請參閱[註冊附加屬性](how-to-register-an-attached-property.md)。

- 如需相依性屬性和附加屬性的更進階使用方式情節，請參閱[自訂相依性屬性](custom-dependency-properties.md)。

- 您也可以將屬性註冊為附加屬性和相依性屬性，但仍公開「包裝函式」實作。 在此情況下，可以在該項目上設定屬性，或透過 XAML 附加屬性語法的任何項目上設定屬性。 具有適用於標準和附加用法的相應機制的屬性的範例是<xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.DependencyProperty>
- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [註冊附加屬性](how-to-register-an-attached-property.md)
