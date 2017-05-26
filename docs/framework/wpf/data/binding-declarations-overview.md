---
title: "繫結宣告概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料繫結, 宣告"
  - "繫結宣告"
  - "資料繫結, 宣告"
  - "標記延伸"
  - "物件項目語法"
  - "語法, 物件項目"
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# 繫結宣告概觀
本主題討論可以用來宣告繫結的不同方法。  
  
   
  
<a name="Prereq"></a>   
## 必要條件  
 在閱讀本主題之前，請務必先熟悉標記延伸的概念和使用方式。  如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 這個主題並未涵蓋資料繫結 \(Data Binding\) 的概念。  如需資料繫結概念的相關討論，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
<a name="BindinginXAML"></a>   
## 在 XAML 中宣告繫結  
 本節討論如何在 XAML 中宣告繫結。  
  
<a name="MarkupExtensionSyntax"></a>   
### 標記延伸使用方式  
 <xref:System.Windows.Data.Binding> 是一種標記延伸。  使用繫結延伸宣告繫結時，該宣告是由一系列子句組成，這些子句接在 `Binding` 關鍵字後面，並以逗號 \(,\) 分隔。  繫結宣告中的子句可以是任何順序，而且有許多可能的組合。  這些子包括 *Name*\=*Value* 配對，其中 *Name* 是 <xref:System.Windows.Data.Binding> 屬性的名稱，而 *Value* 則是您為該屬性設定的值。  
  
 在標記中建立繫結宣告字串時，必須將這些字串附加至目標物件的特定[相依性屬性](GTMT)。  下列範例示範如何使用繫結延伸，藉由指定 <xref:System.Windows.Data.Binding.Source%2A> 和 <xref:System.Windows.Data.Binding.Path%2A> 屬性的方式繫結 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> 屬性。  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 您可以使用這種方法指定 <xref:System.Windows.Data.Binding> 類別的大部分屬性。  如需繫結延伸的詳細資訊，以及無法使用繫結延伸設定的 <xref:System.Windows.Data.Binding> 屬性清單，請參閱[繫結標記延伸](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)概觀。  
  
<a name="ObjectElementSyntax"></a>   
### 物件項目語法  
 物件項目語法是建立繫結宣告的另一種選擇。  在大部分的情況下，使用標記延伸或物件項目語法都沒有特別的優勢。  但是，若標記延伸無法支援您的案例，例如當屬性值屬於非字串型別，而沒有型別轉換時，則必須使用物件項目語法。  
  
 以下為使用物件項目語法和標記延伸的範例。  
  
 [!code-xml[BindConversionMarkup#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 這個範例是透過使用延伸語法宣告繫結的方式，繫結 <xref:System.Windows.Controls.TextBlock.Foreground%2A> 屬性。  <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性的繫結宣告則使用物件項目語法。  
  
 如需不同詞彙的詳細資訊，請參閱 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
<a name="MBandPB"></a>   
### MultiBinding 和 PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> 和 <xref:System.Windows.Data.PriorityBinding> 不支援 XAML 延伸語法。  因此，如果要在 XAML 中宣告 <xref:System.Windows.Data.MultiBinding> 或 <xref:System.Windows.Data.PriorityBinding>，您必須使用物件項目語法。  
  
<a name="BindinginCode"></a>   
## 在程式碼中建立繫結  
 指定繫結的另外一種方法是直接在程式碼中的 <xref:System.Windows.Data.Binding> 物件上設定屬性。  下列範例示範如何在程式碼中建立 <xref:System.Windows.Data.Binding> 物件並指定屬性。  在此範例中，`TheConverter` 是實作 <xref:System.Windows.Data.IValueConverter> 介面的物件。  
  
 [!code-csharp[BindConversion#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
[!code-csharp[BindConversion#end1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#end1)]
[!code-vb[BindConversion#end1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#end1)]  
  
 如果您要繫結的物件是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>，可以直接在物件上呼叫 `SetBinding` 方法，而不要使用 <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=fullName>。  如需範例，請參閱 [使用程式碼建立繫結](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)。  
  
<a name="Path_Syntax"></a>   
## 繫結路徑語法  
 請使用 <xref:System.Windows.Data.Binding.Path%2A> 屬性指定您要繫結的來源值：  
  
-   在最簡單的狀況中，<xref:System.Windows.Data.Binding.Path%2A> 屬性值是用於繫結之來源物件屬性的名稱，例如 `Path=PropertyName`。  
  
-   您可以使用 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 中所用的類似語法，指定屬性的子屬性。  例如，子句 `Path=ShoppingCart.Order` 會將繫結設定為物件或屬性 `ShoppingCart` 的子屬性 `Order`。  
  
-   若要繫結至[附加屬性](GTMT)，請在[附加屬性](GTMT)前後加上括號。  例如，若要繫結至[附加屬性](GTMT) <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>，則語法為 `Path=(DockPanel.Dock)`。  
  
-   屬性的索引子 \(Indexer\) 可以在方括弧內指定，接在套用索引子的屬性名稱後面。  例如，子句 `Path=ShoppingCart[0]` 會將繫結設定為索引，而該索引對應於屬性之內部索引處理常值字串 "0" 的方式。  此語法也支援巢狀索引子。  
  
-   `Path` 子句中可以混合使用索引子和子屬性；例如，`Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   您可以在索引子內加入多個以逗號 \(,\) 分隔的索引子參數。  各個參數的型別可以使用括號指定。  例如，您可以加入 `Path="[(sys:Int32)42,(sys:Int32)24]"`，其中 `sys` 對應至 `System` 命名空間 \(Namespace\)。  
  
-   當來源為集合檢視時，就可以使用斜線 \(\/\) 指定目前的項目。  例如，子句 `Path=/` 會將繫結設定為檢視中目前的項目。  如果來源為集合，這個語法就會指定預設集合檢視目前的項目。  
  
-   屬性名稱和斜線可以組合用來周遊本身為集合的屬性。  例如，`Path=/Offices/ManagerName` 會指定來源集合目前的項目，其中包含同樣為集合的 `Offices` 屬性。  其目前項目為包含 `ManagerName` 屬性的物件。  
  
-   另外，可以選擇使用句號 \(.\) 路徑來繫結至目前的來源。  例如，`Text="{Binding}"` 等於 `Text="{Binding Path=.}"`。  
  
### 逸出機制  
  
-   在索引子 \(\[ \]\) 內，插入號 \(Caret\) 字元 \(^\) 會逸出下一個子元。  
  
-   如果您在 XAML 中設定 <xref:System.Windows.Data.Binding.Path%2A>，則也必須逸出 \(使用 XML 實體\) XML 語言定義特有的某些字元：  
  
    -   使用 `&` 逸出 "&" 字元。  
  
    -   使用 `>` 逸出 "\>" 結束標記。  
  
-   此外，如果您使用標記延伸語法在屬性中描述完整的繫結，您必須逸出 \(使用反斜線 \\\) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 標記延伸剖析器特有的字元：  
  
    -   反斜線 \(\\\) 本身是逸出字元。  
  
    -   等號 \(\=\) 分隔屬性名稱和屬性值。  
  
    -   逗號 \(,\) 分隔屬性。  
  
    -   右大括號 \(}\) 是標記延伸的結尾。  
  
<a name="Default"></a>   
## 預設行為  
 如果宣告中沒有指定，預設行為便如下所述。  
  
-   建立預設轉換子 \(Converter\)，以嘗試在[繫結來源](GTMT)值和[繫結目標](GTMT)值之間執行型別轉換。  如果無法進行轉換，預設轉換子會傳回 `null`。  
  
-   如果您未設定 <xref:System.Windows.Data.Binding.ConverterCulture%2A>，繫結引擎會使用[繫結目標](GTMT)物件的 `Language` 屬性。  在 XAML 中，這個值預設為 "en\-US"，但如果已明確設定，則會繼承頁面之根項目或任何項目的值。  
  
-   只要繫結已經有資料內容 \(例如繼承的資料內容來自父項目\)，而且該內容所傳回的任何項目或集合不需要進一步修改路徑即可適用於繫結，繫結宣告可以完全沒有子句：`{Binding}`。這通常是資料樣式設定指定繫結的方式，其中繫結的作用對象是集合。  如需詳細資訊，請參閱[繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)中的＜使用整個物件做為繫結來源＞一節。  
  
-   預設 <xref:System.Windows.Data.Binding.Mode%2A> 會因所繫結之[相依性屬性](GTMT)而有單向和雙向的不同。  您永遠都可以明確宣告繫結模式，以確保繫結具有所需的行為。  一般來說，使用者可編輯的控制項屬性 \(例如 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> 和 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=fullName>\) 預設為雙向繫結，而其他屬性大多預設為單向繫結。  
  
-   預設 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值也會因為繫結的[相依性屬性](GTMT)而有 <xref:System.Windows.Data.UpdateSourceTrigger> 和 <xref:System.Windows.Data.UpdateSourceTrigger> 的不同。  大部分[相依性屬性](GTMT)的預設值是 <xref:System.Windows.Data.UpdateSourceTrigger>，而 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> 屬性的預設值為 <xref:System.Windows.Data.UpdateSourceTrigger>。  
  
## 請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [PropertyPath XAML 語法](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)