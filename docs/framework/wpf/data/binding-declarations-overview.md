---
title: 繫結宣告概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- markup extensions [WPF]
- data binding [WPF], declarations
- object element syntax [WPF]
- binding data [WPF], declarations
- syntax [WPF], object elements
- binding declarations [WPF]
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
ms.openlocfilehash: a8652648e1ac9da96a027f9aa56f0eee40cbaf09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="binding-declarations-overview"></a>繫結宣告概觀
本主題討論可以用來宣告繫結的不同方法。  
  
 
  
<a name="Prereq"></a>   
## <a name="prerequisites"></a>必要條件  
 在閱讀本主題之前，請務必先熟悉標記延伸的概念和使用方式。 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 這個主題並未涵蓋資料繫結的概念。 如需資料繫結概念的相關討論，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
<a name="BindinginXAML"></a>   
## <a name="declaring-a-binding-in-xaml"></a>在 XAML 中宣告繫結  
 本節討論如何在 XAML 中宣告繫結。  
  
<a name="MarkupExtensionSyntax"></a>   
### <a name="markup-extension-usage"></a>標記延伸使用方式  
 <xref:System.Windows.Data.Binding> 是一種標記延伸。 當您使用繫結延伸宣告繫結時，該宣告是由一系列子句組成，這些子句接在 `Binding` 關鍵字後面，並以逗號 (,) 分隔。 繫結宣告中的子句可以按照任何順序，而且有許多可能的組合。 子句是*名稱*=*值*組 where*名稱*名稱<xref:System.Windows.Data.Binding>屬性和*值*是您要設定屬性值。  
  
 在標記中建立繫結宣告字串時，必須將這些字串附加至目標物件的特定相依性屬性。 下列範例示範如何將繫結<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>屬性使用的繫結延伸模組，指定<xref:System.Windows.Data.Binding.Source%2A>和<xref:System.Windows.Data.Binding.Path%2A>屬性。  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]  
  
 您可以指定屬性的大部分<xref:System.Windows.Data.Binding>類別這種方式。 如需有關繫結延伸模組以及針對一份<xref:System.Windows.Data.Binding>屬性不能使用繫結延伸模組設定，請參閱[繫結標記延伸](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)概觀。  
  
<a name="ObjectElementSyntax"></a>   
### <a name="object-element-syntax"></a>物件元素語法  
 物件元素語法是建立繫結宣告的另一種選擇。 在大部分的情況下，使用標記延伸或物件元素語法並沒有特別的優勢。 但是，若標記延伸無法支援您的案例，例如當屬性值屬於非字串型別，而沒有型別轉換時，則必須使用物件元素語法。  
  
 以下為物件元素語法和標記延伸的使用方式範例：  
  
 [!code-xaml[BindConversionMarkup#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 此範例會將繫結<xref:System.Windows.Controls.TextBlock.Foreground%2A>藉由宣告使用延伸語法的繫結的屬性。 繫結宣告<xref:System.Windows.Controls.TextBlock.Text%2A>屬性使用物件項目語法。  
  
 如需不同詞彙的詳細資訊，請參閱 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
<a name="MBandPB"></a>   
### <a name="multibinding-and-prioritybinding"></a>MultiBinding 和 PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> 和<xref:System.Windows.Data.PriorityBinding>不支援 XAML 延伸語法。 因此，您必須使用物件項目語法如果您宣告<xref:System.Windows.Data.MultiBinding>或<xref:System.Windows.Data.PriorityBinding>在 XAML 中。  
  
<a name="BindinginCode"></a>   
## <a name="creating-a-binding-in-code"></a>在程式碼中建立繫結  
 指定的繫結的另一個方法是直接在設定屬性<xref:System.Windows.Data.Binding>程式碼中的物件。 下列範例示範如何建立<xref:System.Windows.Data.Binding>物件，並在程式碼中指定的屬性。  在此範例中，`TheConverter`是實作的物件<xref:System.Windows.Data.IValueConverter>介面。  
  
 [!code-csharp[BindConversion#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
  
 如果您要繫結的物件<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>可以呼叫`SetBinding`直接而不是使用在物件上的方法<xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>。 如需範例，請參閱[使用程式碼建立繫結](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)。  
  
<a name="Path_Syntax"></a>   
## <a name="binding-path-syntax"></a>繫結路徑語法  
 使用<xref:System.Windows.Data.Binding.Path%2A>屬性來指定您想要繫結來源值：  
  
-   在最簡單的情況下，<xref:System.Windows.Data.Binding.Path%2A>屬性值是使用繫結，例如來源物件的屬性名稱`Path=PropertyName`。  
  
-   子屬性的屬性可以指定類似的語法和在 C#。 例如，子句 `Path=ShoppingCart.Order` 會將繫結設定為物件或屬性 `ShoppingCart` 的子屬性 `Order`。  
  
-   若要繫結至附加屬性，請在附加屬性前後加上括號。 例如，若要附加的屬性繫結<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>，語法是`Path=(DockPanel.Dock)`。  
  
-   屬性的索引子可以在方括弧內指定，接在套用索引子的屬性名稱後面。 例如，子句 `Path=ShoppingCart[0]` 會將繫結設定為索引，而該索引對應於屬性之內部索引處理常值字串 "0" 的方式。 此語法也支援巢狀索引子。  
  
-   `Path` 子句中可以混合使用索引子和子屬性；例如，`Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   您可以在索引子內加入多個以逗號 (,) 分隔的索引子參數。 各個參數的型別可以使用括號指定。 例如，您可以加入 `Path="[(sys:Int32)42,(sys:Int32)24]"`，其中 `sys` 對應至 `System` 命名空間。  
  
-   當來源為集合檢視時，就可以使用斜線 (/) 指定目前的項目。 例如，子句 `Path=/` 會將繫結設定為檢視中目前的項目。 如果來源為集合，這個語法就會指定預設集合檢視目前的項目。  
  
-   屬性名稱和斜線可以組合用來周遊本身為集合的屬性。 例如，`Path=/Offices/ManagerName` 會指定來源集合目前的項目，其中包含同樣為集合的 `Offices` 屬性。 其目前項目為包含 `ManagerName` 屬性的物件。  
  
-   另外，可以使用句號 (.) 路徑來繫結至目前的來源。 例如，`Text="{Binding}"` 等於 `Text="{Binding Path=.}"`。  
  
### <a name="escaping-mechanism"></a>逸出機制  
  
-   在索引子 ([ ]) 內，插入號字元 (^) 會逸出下一個字元。  
  
-   如果您設定<xref:System.Windows.Data.Binding.Path%2A>在 XAML 中，您也需要逸出 （使用 XML 實體） 是特殊的 XML 語言定義的某些字元：  
  
    -   使用 `&` 逸出 "&" 字元。  
  
    -   使用 `>` 逸出 ">" 結束標記。  
  
-   此外，如果您使用標記延伸語法在屬性中描述完整的繫結，您必須逸出 (使用反斜線 \\) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 標記延伸剖析器特有的字元：  
  
    -   反斜線 (\\) 本身是逸出字元。  
  
    -   等號 (=) 會分隔屬性名稱和屬性值。  
  
    -   逗號 (,) 會分隔屬性。  
  
    -   右大括號 (}) 是標記延伸的結尾。  
  
<a name="Default"></a>   
## <a name="default-behaviors"></a>預設行為  
 如果宣告中未指定，則預設行為如下。  
  
-   建立預設轉換器，以嘗試在繫結來源值和繫結目標值之間執行型別轉換。 如果無法進行轉換，預設轉換器會傳回 `null`。  
  
-   如果您未設定<xref:System.Windows.Data.Binding.ConverterCulture%2A>，繫結引擎會使用`Language`繫結目標物件的屬性。 在 XAML 中，這個值預設為 "en-US"，但如果已明確設定，則會繼承頁面之根元素 (或任何元素) 的值。  
  
-   只要繫結已經有資料內容 (例如繼承的資料內容來自父元素)，而且該內容所傳回的任何項目或集合不需要進一步修改路徑即可適用於繫結，繫結宣告可以完全沒有子句：`{Binding}`。這通常是資料樣式設定指定繫結的方式，其中繫結的作用對象是集合。 如需詳細資訊，請參閱[繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)中的＜使用整個物件做為繫結來源＞一節。  
  
-   預設值<xref:System.Windows.Data.Binding.Mode%2A>單向和雙向取決於與所繫結的相依性屬性而異。 您永遠都可以明確宣告繫結模式，以確保繫結具有所需的行為。 一般而言，使用者可以編輯控制項屬性，例如<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>和<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>，預設為雙向繫結，而其他大多數屬性預設為單向繫結。  
  
-   預設值<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值而異<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>和<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>依據的繫結的相依性屬性。 大多數相依性屬性的預設值為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>，而 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 屬性具有 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> 的預設值。  
  
## <a name="see-also"></a>另請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [PropertyPath XAML 語法](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)
