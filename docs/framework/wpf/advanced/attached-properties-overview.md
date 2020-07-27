---
title: 附加屬性概觀
description: 瞭解 Windows Presentation Foundation 中的附加屬性，這是可在任何物件上設定的全域屬性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 993f65024fcfc4f39a408c81af43b798360e6cf6
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168382"
---
# <a name="attached-properties-overview"></a>附加屬性概觀

附加屬性是透過 XAML 所定義的概觀。 附加屬性是要用作可在任何物件上設定的全域屬性類型。 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，附加屬性一般會定義為沒有傳統屬性「包裝函式」的特殊形式相依性屬性。

## <a name="prerequisites"></a>要求<a name="prerequisites"></a>

本文假設您已從類別上現有相依性屬性的取用者觀點瞭解相依性屬性 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ，並已閱讀相依性[屬性總覽](dependency-properties-overview.md)。 若要遵循本文中的範例，您也應該瞭解 XAML 並知道如何撰寫 WPF 應用程式。

## <a name="why-use-attached-properties"></a>為何要使用附加屬性<a name="attached_properties_usage"></a>

附加屬性的其中一個用途是允許不同的子項目指定父元素中定義之屬性的唯一值。 此情節的特定應用程式可讓子項目通知父項目，有關如何在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中呈現它們。 其中一個範例是 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 屬性。 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>屬性會建立為附加屬性，因為它是設計來在包含在中，而不是本身的專案上設定 <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel> 。 <xref:System.Windows.Controls.DockPanel>類別會定義 <xref:System.Windows.DependencyProperty> 名為的靜態欄位 <xref:System.Windows.Controls.DockPanel.DockProperty> ，然後提供 <xref:System.Windows.Controls.DockPanel.GetDock%2A> 和 <xref:System.Windows.Controls.DockPanel.SetDock%2A> 方法做為附加屬性的公用存取子。

## <a name="attached-properties-in-xaml"></a>XAML 中的附加屬性<a name="attached_properties_xaml"></a>

在 XAML 中，您可以使用 *AttachedPropertyProvider*.<屬性名稱>** 語法來設定附加屬性。

以下是您可以如何 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 在 XAML 中設定的範例：

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

使用方式與靜態屬性有點類似;您一律會參考 <xref:System.Windows.Controls.DockPanel> 擁有和註冊附加屬性的類型，而不是參照任何依名稱指定的實例。

此外，因為 XAML 中的附加屬性是您在標記中設定的屬性，所以只有設定作業才會有任何相關性。 雖然有一些間接機制可比較值 (例如樣式中的觸發程序)，但是您無法在 XAML 中直接取得屬性 (如需詳細資訊，請參閱[設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md))。

### <a name="attached-property-implementation-in-wpf"></a>WPF 中的附加屬性實作

在中 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ，WPF 類型上大部分與 UI 相關的附加屬性都會實作為相依性屬性。 附加屬性是 XAML 概念，而相依性屬性則是 WPF 概念。 由於 WPF 附加屬性是相依性屬性，因此支援相依性屬性概念，例如屬性中繼資料，以及來自該屬性中繼資料的預設值。

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>擁有類型如何使用附加屬性<a name="howused"></a>

雖然可在任何物件上設定附加屬性，但是這不自動表示設定屬性就會產生明確結果，或者另一個物件將使用值。 一般而言，會使用附加屬性，讓來自各種可能類別階層或邏輯關聯性的物件都可以報告可定義附加屬性之類型的通用資訊。 可定義附加屬性的類型通常會遵循下列其中一個模型︰

- 設計可定義附加屬性的類型，因此它可以是設定附加屬性值之項目的父項目。 類型接著會透過內部邏輯針對某個物件樹狀結構逐一查看其子物件，並取得值，然後以某種方式處理這些值。

- 可定義附加屬性的類型將會用作各種可能父項目和內容模組的子項目。

- 可定義附加屬性的類型代表服務。 其他類型設定附加屬性的值。 然後，在服務內容中評估可設定屬性的項目時，會透過服務類別的內部邏輯取得附加屬性值。

### <a name="an-example-of-a-parent-defined-attached-property"></a>父代已定義的附加屬性範例

WPF 定義附加屬性的最常見案例是當父元素支援子專案集合時，也會執行行為，其中會針對每個子專案個別報告行為的細節。

<xref:System.Windows.Controls.DockPanel>定義 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 附加屬性，並 <xref:System.Windows.Controls.DockPanel> 具有類別層級程式碼作為其轉譯邏輯的一部分（尤其是 <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> 和 <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A> ）。 <xref:System.Windows.Controls.DockPanel>實例一律會檢查是否有任何直屬子專案已設定的值 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 。 如果是這樣，這些值會變成套用至該特定子項目之轉譯邏輯的輸入。 <xref:System.Windows.Controls.DockPanel>每個嵌套的實例都會處理自己的直屬子專案集合，但該行為會因 <xref:System.Windows.Controls.DockPanel> 處理值而異 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 。 理論上，可能會有附加屬性影響直屬父代以外的項目。 如果 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 附加屬性設定在沒有父元素的專案上 <xref:System.Windows.Controls.DockPanel> 進行動作，則不會引發錯誤或例外狀況。 這只是表示已設定全域屬性值，但目前沒有任何 <xref:System.Windows.Controls.DockPanel> 可能會耗用此資訊的父系。

## <a name="attached-properties-in-code"></a>程式碼中的附加屬性<a name="attached_properties_code"></a>

WPF 中附加的屬性沒有一般的 CLR 「包裝函式」方法，可輕鬆取得/設定存取。 這是因為附加屬性不一定是設定屬性之實例的 CLR 命名空間的一部分。 不過，XAML 處理器必須可以在剖析 XAML 時設定這些值。 若要支援有效的附加屬性使用方式，附加屬性的擁有者類型必須以**Get_PropertyName_** 和**Set_PropertyName_** 的形式，實作為專用存取子方法。 這些專用存取子方法也適用於取得或設定程式碼中的附加屬性。 從程式碼觀點，附加屬性類似具有方法存取子而非屬性存取子的支援欄位，而且該支援欄位可以存在於任何物件，而不需要特別進行定義。

下列範例示範如何在程式碼中設定附加屬性。 在此範例中， `myCheckBox` 是類別的實例 <xref:System.Windows.Controls.CheckBox> 。

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

類似于 XAML 案例，如果尚未 `myCheckBox` `myDockPanel` 在第四行程式碼中新增為的子項目，則第五行程式碼不會引發例外狀況，但屬性值不會與父系互動， <xref:System.Windows.Controls.DockPanel> 因此不會執行任何動作。 只有 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 在子項目上設定的值與父元素的存在結合，才 <xref:System.Windows.Controls.DockPanel> 會在轉譯的應用程式中造成有效的行為。 (在此情況下，您可以設定附加屬性，然後將其附加至樹狀結構。 或者，您可以將其附加至樹狀結構，然後設定附加屬性。 任一個動作順序都會提供相同的結果)。

## <a name="attached-property-metadata"></a>附加屬性中繼資料<a name="attached_properties_metadata"></a>

當註冊屬性時， <xref:System.Windows.FrameworkPropertyMetadata> 會設定為指定屬性的特性，例如屬性是否會影響轉譯、測量等等。 附加屬性的中繼資料一般與相依性屬性並無不同。 如果您在附加屬性中繼資料的覆寫中指定預設值，該值會變成覆寫類別執行個體上的隱含附加屬性預設值。 具體而言，如果某個處理序透過該屬性的 `Get` 方法存取子來查詢附加屬性值，並指定已指定中繼資料之類別的執行個體，則會報告預設值，否則不會設定該附加屬性的值。

如果您想要啟用屬性的屬性值繼承，則應該使用附加屬性，而不是使用非附加相依性屬性。 如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

## <a name="custom-attached-properties"></a>自訂附加屬性<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>建立附加屬性的時機<a name="create_attached_properties"></a>

非定義類別的類別需要有可用的屬性設定機制時，您可以建立附加屬性。 最常見的案例是配置。 現有版面配置屬性的範例包括 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 、 <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> 。 在這裡啟用的情節是本身為配置控制項目之子項目的項目可以個別表達其配置父項目的配置需求，且各會設定父代定義為附加屬性的屬性值。

另一個使用附加屬性的情節是類別代表一項服務，而且想要類別能夠更緊密地整合服務。

另一種情況是接收 Visual Studio WPF 設計工具支援，例如 [**屬性**] 視窗編輯。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。

如前所述，如果您想要使用屬性值繼承，則應該註冊為附加屬性。

### <a name="how-to-create-an-attached-property"></a>如何建立附加屬性<a name="how_do_i_create_attached_properties"></a>

如果您的類別是嚴格定義附加屬性以用於其他類型，則類別不需要衍生自 <xref:System.Windows.DependencyObject> 。 但是， <xref:System.Windows.DependencyObject> 如果您遵循整體 WPF 模型讓附加屬性也是相依性屬性，就必須衍生自。

藉由宣告類型的欄位，將附加屬性定義為相依性屬性 `public static readonly` <xref:System.Windows.DependencyProperty> 。 您可以使用方法的傳回值來定義此欄位 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 。 功能變數名稱必須符合附加屬性名稱（加上字串 `Property` ），以遵循已建立的 WPF 模式來命名識別欄位與它們所代表的屬性。 附加屬性提供者也必須提供靜態**Get_PropertyName_** 和**Set_PropertyName_** 方法做為附加屬性的存取子;無法執行此動作會導致屬性系統無法使用您的附加屬性。

> [!NOTE]
> 如果您省略附加屬性的 get 存取子，屬性上的資料系結將無法在設計工具中使用，例如 Visual Studio 和 Blend for Visual Studio。

#### <a name="the-get-accessor"></a>Get 存取子

**Get_PropertyName_** 存取子的簽章必須是：

`public static object GetPropertyName(object target)`

- `target` 物件可以指定為實作中的更特定類型。 例如， <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> 方法會將參數輸入為 <xref:System.Windows.UIElement> ，因為附加屬性僅適用于實例上的設定 <xref:System.Windows.UIElement> 。

- 傳回值可以指定為實作中的更特定類型。 例如， <xref:System.Windows.Controls.DockPanel.GetDock%2A> 方法會將它輸入為 <xref:System.Windows.Controls.Dock> ，因為此值只能設定為該列舉。

#### <a name="the-set-accessor"></a>Set 存取子

**Set_PropertyName_** 存取子的簽章必須是：

`public static void SetPropertyName(object target, object value)`

- `target` 物件可以指定為實作中的更特定類型。 例如，方法會將 <xref:System.Windows.Controls.DockPanel.SetDock%2A> 它輸入為 <xref:System.Windows.UIElement> ，因為附加屬性僅適用于實例上的設定 <xref:System.Windows.UIElement> 。

- `value` 物件可以指定為實作中的更特定類型。 例如， <xref:System.Windows.Controls.DockPanel.SetDock%2A> 方法會將它輸入為 <xref:System.Windows.Controls.Dock> ，因為此值只能設定為該列舉。 請記住，當這個方法在標記的附加屬性使用方式中遇到附加屬性時，其值是來自 XAML 載入器的輸入。 該輸入是指定為標記中 XAML 屬性值的值。 因此，您使用的類型必須要有類型轉換、值序列化程式或標記延伸支援，因此，可以從屬性值 (這最後就是一個字串) 建立適當的類型。

下列範例顯示相依性屬性註冊（使用 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 方法），以及**Get_PropertyName_** 和**Set_PropertyName_** 存取子。 在此範例中，附加屬性名稱為 `IsBubbleSource`。 因此，存取子必須命名為 `GetIsBubbleSource` 和 `SetIsBubbleSource`。

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>附加屬性 (property) 的屬性 (attribute)

WPF 會定義數個 .NET 屬性，其目的是要將附加屬性的相關資訊提供給反映進程，以及反映的一般使用者和屬性資訊（例如設計工具）。 因為附加屬性的類型為無限制範圍，所以設計人員需要方法來避免使用 XAML 的特定技術實作中所定義之所有附加屬性的全域清單，讓使用者無所適從。 WPF 為附加屬性定義的 .NET 屬性可用來界定給定附加屬性應該顯示在 [屬性] 視窗中的狀況範圍。 您也可以考慮針對您自己的自訂附加屬性套用這些屬性。 如需 .NET 屬性的用途和語法，請參閱適當的參考頁面：

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>深入瞭解附加屬性<a name="more"></a>

- 如需建立附加屬性的詳細資訊，請參閱[註冊附加屬性](how-to-register-an-attached-property.md)。

- 如需相依性屬性和附加屬性的更進階使用方式情節，請參閱[自訂相依性屬性](custom-dependency-properties.md)。

- 您也可以將屬性註冊為附加屬性和相依性屬性，但仍公開「包裝函式」實作。 在此情況下，可以在該項目上設定屬性，或透過 XAML 附加屬性語法的任何項目上設定屬性。 具有適用于標準和附加用法之適當案例的屬性範例為 <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType> 。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.DependencyProperty>
- [相依性屬性總覽](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [註冊附加屬性](how-to-register-an-attached-property.md)
