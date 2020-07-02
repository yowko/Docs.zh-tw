---
title: 繫結宣告概觀
description: 瞭解如何在 XAML 中宣告系結，以在 Windows Presentation Foundation （WPF）中開發應用程式。
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
ms.openlocfilehash: 8d4943de0cacb5fe0b5a0c37a5a68f15243ad528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619633"
---
# <a name="binding-declarations-overview"></a>繫結宣告概觀

本主題討論可以用來宣告繫結的不同方法。

<a name="Prereq"></a>

## <a name="prerequisites"></a>必要條件

在閱讀本主題之前，請務必先熟悉標記延伸的概念和使用方式。 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md)。

這個主題並未涵蓋資料繫結的概念。 如需資料繫結概念的相關討論，請參閱[資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)。

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a>在 XAML 中宣告繫結

本節討論如何在 XAML 中宣告繫結。

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a>標記延伸使用方式

<xref:System.Windows.Data.Binding> 是一種標記延伸。 當您使用繫結延伸宣告繫結時，該宣告是由一系列子句組成，這些子句接在 `Binding` 關鍵字後面，並以逗號 (,) 分隔。 繫結宣告中的子句可以按照任何順序，而且有許多可能的組合。 子句是*名稱* = *值*組，其中*name*是屬性的名稱 <xref:System.Windows.Data.Binding> ，而*值*則是您要為屬性設定的值。

在標記中建立繫結宣告字串時，必須將這些字串附加至目標物件的特定相依性屬性。 下列範例顯示如何使用系結延伸模組來系結 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 屬性，並指定 <xref:System.Windows.Data.Binding.Source%2A> 和 <xref:System.Windows.Data.Binding.Path%2A> 屬性。

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

您可以用 <xref:System.Windows.Data.Binding> 這種方式指定類別的大部分屬性。 如需系結延伸模組以及無法使用系結延伸模組設定之屬性清單的詳細資訊 <xref:System.Windows.Data.Binding> ，請參閱系結[標記延伸](../advanced/binding-markup-extension.md)的總覽。

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a>物件元素語法

物件元素語法是建立繫結宣告的另一種選擇。 在大部分的情況下，使用標記延伸或物件元素語法並沒有特別的優勢。 但是，若標記延伸無法支援您的案例，例如當屬性值屬於非字串型別，而沒有型別轉換時，則必須使用物件元素語法。

以下為物件元素語法和標記延伸的使用方式範例：

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

此範例會使用延伸模組語法宣告系結來系結 <xref:System.Windows.Controls.TextBlock.Foreground%2A> 屬性。 屬性的系結宣告會 <xref:System.Windows.Controls.TextBlock.Text%2A> 使用物件元素語法。

如需不同詞彙的詳細資訊，請參閱 [XAML 語法詳細資料](../advanced/xaml-syntax-in-detail.md)。

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a>MultiBinding 和 PriorityBinding

<xref:System.Windows.Data.MultiBinding>和不 <xref:System.Windows.Data.PriorityBinding> 支援 XAML 延伸模組語法。 因此，如果您要 <xref:System.Windows.Data.MultiBinding> 在 XAML 中宣告或，則必須使用物件元素語法 <xref:System.Windows.Data.PriorityBinding> 。

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a>在程式碼中建立繫結

另一個指定系結的方式是直接在程式碼中的物件上設定屬性 <xref:System.Windows.Data.Binding> 。 下列範例顯示如何建立 <xref:System.Windows.Data.Binding> 物件，並在程式碼中指定屬性。  在此範例中， `TheConverter` 是用來執行介面的物件 <xref:System.Windows.Data.IValueConverter> 。

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

如果您要系結的物件是 <xref:System.Windows.FrameworkElement> 或， <xref:System.Windows.FrameworkContentElement> 您可以 `SetBinding` 直接在物件上呼叫方法，而不是使用 <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> 。 如需範例，請參閱[使用程式碼建立繫結](how-to-create-a-binding-in-code.md)。

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a>繫結路徑語法

使用 <xref:System.Windows.Data.Binding.Path%2A> 屬性來指定您想要系結的來源值：

- 在最簡單的情況下， <xref:System.Windows.Data.Binding.Path%2A> 屬性值就是要用於系結之來源物件的屬性名稱，例如 `Path=PropertyName` 。

- 屬性的子屬性可以透過與 c # 中類似的語法來指定。 例如，子句 `Path=ShoppingCart.Order` 會將繫結設定為物件或屬性 `ShoppingCart` 的子屬性 `Order`。

- 若要繫結至附加屬性，請在附加屬性前後加上括號。 例如，若要系結至附加屬性 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ，語法為 `Path=(DockPanel.Dock)` 。

- 屬性的索引子可以在方括弧內指定，接在套用索引子的屬性名稱後面。 例如，子句 `Path=ShoppingCart[0]` 會將繫結設定為索引，而該索引對應於屬性之內部索引處理常值字串 "0" 的方式。 此語法也支援巢狀索引子。

- `Path` 子句中可以混合使用索引子和子屬性；例如，`Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`

- 您可以在索引子內加入多個以逗號 (,) 分隔的索引子參數。 各個參數的型別可以使用括號指定。 例如，您可以加入 `Path="[(sys:Int32)42,(sys:Int32)24]"`，其中 `sys` 對應至 `System` 命名空間。

- 當來源為集合檢視時，就可以使用斜線 (/) 指定目前的項目。 例如，子句 `Path=/` 會將繫結設定為檢視中目前的項目。 如果來源為集合，這個語法就會指定預設集合檢視目前的項目。

- 屬性名稱和斜線可以組合用來周遊本身為集合的屬性。 例如，`Path=/Offices/ManagerName` 會指定來源集合目前的項目，其中包含同樣為集合的 `Offices` 屬性。 其目前項目為包含 `ManagerName` 屬性的物件。

- 另外，可以使用句號 (.) 路徑來繫結至目前的來源。 例如，`Text="{Binding}"` 等於 `Text="{Binding Path=.}"`。

### <a name="escaping-mechanism"></a>逸出機制

- 在索引子 ([ ]) 內，插入號字元 (^) 會逸出下一個字元。

- 如果您 <xref:System.Windows.Data.Binding.Path%2A> 在 XAML 中設定，您也需要對 xml 語言定義的特殊字元進行 escape （使用 xml 實體）：

  - 使用 `&amp;` 逸出 "&" 字元。

  - 使用 `&gt;` 逸出 ">" 結束標記。

- 此外，如果您使用標記延伸語法在屬性中描述完整的繫結，您必須逸出 (使用反斜線 \\) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 標記延伸剖析器特有的字元：

  - 反斜線 (\\) 本身是逸出字元。

  - 等號 (=) 會分隔屬性名稱和屬性值。

  - 逗號 (,) 會分隔屬性。

  - 右大括號 (}) 是標記延伸的結尾。

<a name="Default"></a>

## <a name="default-behaviors"></a>預設行為

如果宣告中未指定，則預設行為如下。

- 建立預設轉換器，以嘗試在繫結來源值和繫結目標值之間執行型別轉換。 如果無法進行轉換，預設轉換器會傳回 `null`。

- 如果未設定，系結 <xref:System.Windows.Data.Binding.ConverterCulture%2A> 引擎會使用系結 `Language` 目標物件的屬性。 在 XAML 中，這個值預設為 "en-US"，但如果已明確設定，則會繼承頁面之根元素 (或任何元素) 的值。

- 只要繫結已經有資料內容 (例如繼承的資料內容來自父元素)，而且該內容所傳回的任何項目或集合不需要進一步修改路徑即可適用於繫結，繫結宣告可以完全沒有子句：`{Binding}`。這通常是資料樣式設定指定繫結的方式，其中繫結的作用對象是集合。 如需詳細資訊，請參閱[繫結來源概觀](binding-sources-overview.md)中的＜使用整個物件做為繫結來源＞一節。

- 預設會根據所系結的相依性屬性，在 <xref:System.Windows.Data.Binding.Mode%2A> 單向和雙向之間有所不同。 您永遠都可以明確宣告繫結模式，以確保繫結具有所需的行為。 一般而言，使用者可編輯的控制項屬性（例如 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType> ）預設為雙向系結，而其他大多數屬性則預設為單向系結。

- 根據系結的相依性 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性，預設值會在和之間有所不同 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> 。 大多數相依性屬性的預設值為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>，而 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 屬性具有 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> 的預設值。

## <a name="see-also"></a>另請參閱

- [資料系結總覽](../../../desktop-wpf/data/data-binding-overview.md)
- [操作說明主題](data-binding-how-to-topics.md)
- [資料繫結](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath XAML 語法](../advanced/propertypath-xaml-syntax.md)
