---
title: 資料繫結概觀
description: 瞭解可在 .NET Core 的 Windows 演示文稿基礎中添加到專案中的不同數據源。 數據源可以綁定到 XAML 元素以創建動態應用。
author: thraka
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7f17ff094a35c04ba880c87c6966d7d249817516
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "82072008"
---
# <a name="data-binding-overview-in-wpf"></a>WPF 中的數據繫結概述

Windows 示範基礎 (WPF) 中的數據繫結為應用提供一種簡單且一致的方式來呈現資料並與之互動。 元素可以綁定到來自各種資料源的數據,其形式是 .NET 物件和 XML。 任何<xref:System.Windows.Controls.ContentControl><xref:System.Windows.Controls.Button>(<xref:System.Windows.Controls.ItemsControl>如<xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.ListView>和 ) 的任何 ,如和 , 都有內建功能,可靈活設置單個數據項或數據項集合的樣式。 您可以在資料上方產生排序、篩選和群組檢視。

WPF 中的數據綁定功能與傳統模型相比具有幾個優勢,包括通過多種屬性對數據綁定的固有支援、數據靈活的 UI 表示形式以及業務邏輯與 UI 的完全分離。

本文首先討論 WPF 數據綁定的基本概念,然後介紹數據<xref:System.Windows.Data.Binding>綁定的 類和其他功能的用法。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>資料繫結是什麼？

數據綁定是在應用 UI 及其顯示的數據之間建立連接的過程。 如果繫結具有正確的設定而且資料提供了適當的通知，當資料變更其值時，繫結至資料的項目就會自動反映變更。 資料繫結也代表在元素資料的外部表示變更時，基礎資料也會自動更新以反映變更。 例如,如果使用者編輯`TextBox`元素中的值,則基礎數據值將自動更新以反映該更改。

數據綁定的典型用途是將伺服器或本地配置數據放入窗體或其他 UI 控件中。 在 WPF 中,這一概念被擴展為包括將各種屬性綁定到各種數據源。 在 WPF 中,元素的依賴項屬性可以綁定到 .NET 物件(包括與 Web 服務和 Web 屬性關聯的 ADO.NET 物件或物件)和 XML 數據。

有關資料綁定的範例,請查看[資料綁定演示][data-binding-demo]中的以下應用 UI,該演示顯示拍賣專案的清單。

![資料繫結圖樣螢幕擷取](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

該應用程式展示資料線線的以下功能:

- ListBox 的內容綁定到*拍賣項目物件*的集合。 *拍賣項目物件*具有*描述*、*啟動價格*、*開始日期*、*類別*、*特殊功能*等屬性。

- 中顯示的數據(*拍賣項目*`ListBox`物件) 是範本化的,以便顯示每個項目的說明和當前價格。 樣本是使用 建立的<xref:System.Windows.DataTemplate>。 除此之外，每個項目的外觀取決於所顯示 *AuctionItem* 的 *SpecialFeatures* 值。 如果 *AuctionItem* 的 *SpecialFeatures* 值是 *Color*，項目就具有藍色框線。 如果值是 *Highlight*，項目就具有橘色框線和星號。 [資料範本化](#data-templating)一節會提供資料範本化的相關資訊。

- 用戶可以使用`CheckBoxes`提供的對數據進行分組、篩選或排序。 在上面的圖中,按**類別**分組和**按類別和日期**`CheckBoxes`排序。 您可能已經注意到，資料的群組化是依據產品的分類，且分類名稱是以字母順序排列。 雖然在圖中很難辨識，但項目在每個分類內也有以開始日期排序。 排序是使用*集合視圖*完成的。 [綁定到集合](#binding-to-collections)部分討論集合檢視。

- 當使用者選擇項目時,<xref:System.Windows.Controls.ContentControl>將顯示所選項目的詳細資訊。 此體驗為*主詳細資訊機制*。 [主詳細資訊方案](#master-detail-binding-scenario)部分提供有關此類型的綁定的資訊。

- *StartDate*屬性的類型<xref:System.DateTime>為 ,它返回包含時間到毫秒的日期。 在此應用中,已使用自訂轉換器,以便顯示較短的日期字串。 「[資料轉換](#data-conversion)」部分提供有關轉換器的資訊。

當使用者選擇「*添加產品*」按鈕時,將出現以下窗體。

![加入產品清單頁面](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

用戶可以編輯表單中的欄位,使用簡短或詳細的預覽窗格預覽產品清單,然後選擇`Submit`添加新產品清單。 任何現有的分組、篩選和排序設置都將應用於新條目。 在這種特定情形下，輸入上圖的項目會在 [Computer (電腦)]** 分類內顯示為第二個項目。

此圖像中未顯示的驗證邏輯是*開始日期*<xref:System.Windows.Controls.TextBox>中提供的驗證邏輯。 如果使用者輸入無效日期(格式無效或過去日期),則會在旁邊使用和<xref:System.Windows.Controls.ToolTip>紅色感嘆號通知使用者<xref:System.Windows.Controls.TextBox>。 [資料驗證](#data-validation)一節會討論如何建立驗證邏輯。

在討論上述數據綁定的不同功能之前,我們將首先討論對理解 WPF 數據綁定至關重要的基本概念。

## <a name="basic-data-binding-concepts"></a>基本資料繫結概念

無論您綁定的是哪個元素,以及數據源的性質如何,每個綁定始終遵循下圖所示的模型。

![顯示基本數據綁定模型的圖表。](./media/data-binding-overview/basic-data-binding-diagram.png)

如圖所示,數據綁定實質上是綁定目標和綁定源之間的橋樑。 該圖演示了以下基本 WPF 資料繫結概念:

- 通常,每個繫結有四個元件:

  - 綁定目標物件。
  - 目標屬性。
  - 繫結來源。
  - 要使用的綁定源中值的路徑。
  
  > 例如,如果要`TextBox`將的內容綁定到`Employee.Name`屬性,則目標物件是`TextBox`,目標屬性<xref:System.Windows.Controls.TextBox.Text%2A>是 屬性,要使用的值是*Name,* 源物件是*Employ*物件。

- 目標屬性必須是相依性屬性。 大多數<xref:System.Windows.UIElement>屬性都是依賴項屬性,大多數依賴項屬性(只讀屬性除外)預設支援數據綁定。 (只有派生自<xref:System.Windows.DependencyObject>的類型才能定義相依項屬性<xref:System.Windows.UIElement>;並且所有`DependencyObject`類型都派生自 。

- 雖然圖中未顯示,但需要注意的是,綁定源對象不僅限於自定義 .NET 物件。 WPF 資料繫結支援以 .NET 物件和 XML 形式的資料。 為了提供一些範例,綁定源可以是<xref:System.Windows.UIElement>任何清單物件、ADO.NET或 Web 服務物件或包含 XML 資料的 XmlNode。 有關詳細資訊,請參閱[綁定源概述](../../framework/wpf/data/binding-sources-overview.md)。

請務必記住,在建立綁定時,您將綁定目標綁定*到*綁定源。 例如,如果要在<xref:System.Windows.Controls.ListBox>使用數據綁定中顯示某些基礎 XML 數據,則對`ListBox`XML 數據進行綁定。

要建立繫結,請使用<xref:System.Windows.Data.Binding>物件 。 本文的其餘部分討論了與`Binding`對象相關的許多概念以及物件的一些屬性和用法。

### <a name="direction-of-the-data-flow"></a>資料流程的方向

如上圖中的箭頭所示,如果綁定源提供正確的通知,綁定的數據流可以從綁定目標轉到綁定源(例如,當使用者編輯`TextBox`值 時,源值會更改) 和/或綁定源到綁定目標(例如`TextBox`,您的內容會隨著綁定源中的更改而更新)。

您可能希望你的應用允許使用者更改數據並將其傳播回源物件。 或者您可能不希望使用者更新來源資料。 您可以通過設置<xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>來控制 資料流。

底線表表示不同類型的資料串流:

![資料繫結資料流程](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>綁定會導致對源屬性的更改自動更新目標屬性,但對目標屬性的更改不會傳播回源屬性。 如果要繫結的控制項是隱含唯讀的，這種類型的繫結很適當。 例如,您可以綁定到源(如股票代碼,或者目標屬性沒有為進行更改(如表的數據綁定背景顏色)提供控制介面。 如果不需要監視目標屬性的變更，使用 <xref:System.Windows.Data.BindingMode.OneWay> 繫結模式可以避免 <xref:System.Windows.Data.BindingMode.TwoWay> 繫結模式的額外負荷。

- <xref:System.Windows.Data.BindingMode.TwoWay>綁定會導致對源屬性或目標屬性的更改,以自動更新另一個屬性。 這種類型的綁定適用於可編輯的窗體或其他完全互動式 UI 方案。 大多數屬性預設為<xref:System.Windows.Data.BindingMode.OneWay>綁定,但某些依賴項屬性(通常是使用者可編輯控件的屬性,<xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>如和[CheckBox.IsCheck](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked)默認<xref:System.Windows.Data.BindingMode.TwoWay>綁定。 確定依賴項屬性在預設情況下是單向綁定還是雙向綁定的程式設計方法是獲取屬性元數據<xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType>,然後檢查屬性<xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType>的 布爾值。

- <xref:System.Windows.Data.BindingMode.OneWayToSource>是綁定的<xref:System.Windows.Data.BindingMode.OneWay>反面;當目標屬性發生更改時,它將更新源屬性。 一個範例方案是,如果您只需要從 UI 重新評估源值。

- 圖中未說明的是<xref:System.Windows.Data.BindingMode.OneTime>綁定,這將導致源屬性初始化目標屬性,但不會傳播後續更改。 如果數據上下文發生更改或數據上下文中的物件發生更改,則更改*不會*反映在目標屬性中。 如果當前狀態的快照是適當的,或者數據是真正的靜態的,則這種類型的綁定是合適的。 如果您想要以來源屬性的某些值初始化目標屬性，但無法預先得知資料內容，則此類型的繫結也很有用。 此模式本質上是一種更簡單的<xref:System.Windows.Data.BindingMode.OneWay>綁定形式,在源值不變的情況下提供更好的性能。

要偵測來源變更(<xref:System.Windows.Data.BindingMode.OneWay>適用於<xref:System.Windows.Data.BindingMode.TwoWay>與繫結),源必須實現適當的屬性更改通知機制,<xref:System.ComponentModel.INotifyPropertyChanged>如 。 [請參閱如何:實現屬性更改通知](../../framework/wpf/data/how-to-implement-property-change-notification.md),<xref:System.ComponentModel.INotifyPropertyChanged>了解 實現的示例。

該<xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>屬性提供了有關綁定模式的詳細資訊以及如何指定綁定的方向的範例。

### <a name="what-triggers-source-updates"></a>觸發源更新的內容

正在<xref:System.Windows.Data.BindingMode.TwoWay>或<xref:System.Windows.Data.BindingMode.OneWayToSource>偵聽目標屬性中的更改並將其傳播回源(稱為更新源)的綁定。 舉例來說，您可以編輯 TextBox 的文字以變更基礎來源值。

但是,在編輯文本或完成文本編輯后是否更新了源值,控件會失去焦點? 屬性<xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType>確定觸發源更新的原因。 下圖中右箭頭的點說明瞭<xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType>屬性的作用。

![顯示 UpdateSourceTrigger 屬性角色的圖表。](./media/data-binding-overview/data-binding-updatesource-trigger.png)

如果`UpdateSourceTrigger`值<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType>為 ,則當目標屬性發生更改時,<xref:System.Windows.Data.BindingMode.TwoWay>將更新<xref:System.Windows.Data.BindingMode.OneWayToSource>右箭頭指向的值或綁定。 但是,如果`UpdateSourceTrigger`值為<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>,則僅當目標屬性失去焦點時,該值僅會使用新值更新。

與屬性<xref:System.Windows.Data.Binding.Mode%2A>類似,不同的依賴項屬性具有<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>不同的 預設值。 大多數相依性屬性的預設值為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>，而 `TextBox.Text` 屬性具有 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> 的預設值。 `PropertyChanged`表示源更新通常在目標屬性更改時發生。 對於複選框和其他簡單控件,即時更改是可以的。 但是,對於文本欄位,每次擊鍵後更新都會降低性能,並剝奪使用者在提交到新值之前回空間和修復鍵入錯誤的通常機會。

有關如何查找<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>依賴項屬性的預設值的資訊,請參閱屬性頁。

下表提供每個<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值的範例方案,<xref:System.Windows.Controls.TextBox>該範例用作範例。

| UpdateSourceTrigger 值 | 更新來源值時 | 文字框的範例方案 |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`( 預設<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>為 ) | 當 TextBox 控件失去焦點時。 | 與驗證邏輯關聯的文本框(請參閱下面的[數據驗證](#data-validation))。 |
| `PropertyChanged` | 當您鍵入<xref:System.Windows.Controls.TextBox>中 時。 | 聊天室視窗中的 TextBox 控制件。 |
| `Explicit` | 當應用程式調用<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>時。 | TextBox 控制件為可編輯窗體(僅在用戶按一下提交按鈕時更新源值)。 |

例如,請參考[如何:控制文字盒文字何時更新來源](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)。

## <a name="creating-a-binding"></a>建立繫結

為了重構前面各節中討論的某些概念,可以使用<xref:System.Windows.Data.Binding>物件建立綁定,並且每個綁定通常有四個元件:綁定目標、目標屬性、綁定源和要使用的源值的路徑。 本節討論如何設定繫結。

請考慮下列範例，其中的繫結來源物件是名為 *MyData* 的類別，定義於 *SDKSample* 命名空間中。 出於展示目的 *,MyData*具有名為*ColorName*的字串屬性,其值設置為"紅色"。 因此，本範例會產生具有紅色背景的按鈕。

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

有關繫結聲明語法的詳細資訊以及如何在代碼中設定綁定的範例,請參閱[連結概述](../../framework/wpf/data/binding-declarations-overview.md)。

如果將這個範例套用到我們的基本圖表，結果會類似下圖。 此圖描述綁定<xref:System.Windows.Data.BindingMode.OneWay>,因為預設情況下,背景<xref:System.Windows.Data.BindingMode.OneWay>屬性 支援綁定。

![顯示數據繫結背景屬性的圖表。](./media/data-binding-overview/data-binding-button-background-example.png)

您可能想知道為什麼此繫結有效,即使*ColorName*屬性是型態字<xref:System.Windows.Controls.Control.Background%2A>串, 而<xref:System.Windows.Media.Brush>屬性是類型 。 此繫結出預設類型轉換,在[「資料轉換](#data-conversion)」部分中討論。

### <a name="specifying-the-binding-source"></a>指定繫結源

請注意,在前面的示例中,綁定源是通過設置[DockPanel.DataContext](xref:System.Windows.FrameworkElement.DataContext)屬性來指定的。 <xref:System.Windows.Controls.Button>然後從<xref:System.Windows.FrameworkElement.DataContext%2A>繼承的值<xref:System.Windows.Controls.DockPanel>從 ,這是其父元素。 再重複聲明一次，繫結來源物件是繫結的四個必要元件之一。 因此，沒有指定繫結來源物件，就無法進行繫結。

有數種方式可以指定繫結來源物件。 將多個<xref:System.Windows.FrameworkElement.DataContext%2A>屬性綁定到同一源時,在父元素上使用 該屬性非常有用。 然而，有時候在個別的繫結宣告上指定繫結來源可能比較恰當。 對於前面的範例,<xref:System.Windows.FrameworkElement.DataContext%2A>可以通過直接在按鈕的綁定聲明<xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>中設置 屬性來指定綁定源,如下例所示。

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

除了直接在元素<xref:System.Windows.FrameworkElement.DataContext%2A>上設置屬性外<xref:System.Windows.FrameworkElement.DataContext%2A>, 從祖先繼承值(如第一個示例中的按鈕),並通過在綁定<xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>上設置 屬性(如最後一個示例的按鈕)顯式指定綁定源<xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType>,還可以<xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType>使用 屬性或 屬性指定綁定源。 當您<xref:System.Windows.Data.Binding.ElementName%2A>綁定到應用中的其他元素時,該屬性很有用,例如,當您使用滑塊調整按鈕的寬度時。 在<xref:System.Windows.Data.Binding.RelativeSource%2A><xref:System.Windows.Controls.ControlTemplate>或 指定的結合時,該屬性很有<xref:System.Windows.Style>用 。 有關詳細資訊,請參閱[操作:指定繫結源](../../framework/wpf/data/how-to-specify-the-binding-source.md)。

### <a name="specifying-the-path-to-the-value"></a>指定值的路徑

如果綁定源是物件,則可以使用<xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType>屬性 指定用於綁定的值。 如果要綁定到 XML 資料,請<xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType>使用 屬性指定值。 在某些情況下,即使數據為 XML,<xref:System.Windows.Data.Binding.Path%2A>也可以使用該屬性。 例如,如果要訪問返回的 XmlNode 的 Name 屬性(作為 XPath 查詢<xref:System.Windows.Data.Binding.Path%2A><xref:System.Windows.Data.Binding.XPath%2A>的結果),則應除該屬性之外使用 該屬性。

有關詳細資訊,請參閱和<xref:System.Windows.Data.Binding.Path%2A><xref:System.Windows.Data.Binding.XPath%2A>屬性。

儘管我們強調<xref:System.Windows.Data.Binding.Path%2A>要使用的值是綁定的四個必要元件之一,但在要綁定到整個物件的方案中,要使用的值將與綁定源物件相同。 在這些情況下,它適用於不指定<xref:System.Windows.Data.Binding.Path%2A>。 請思考一下下列範例。

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

上述範例使用空白繫結語法：{Binding}。 在這種情況下,從<xref:System.Windows.Controls.ListBox>父 DockPanel 元素繼承 DataContext(此示例中未顯示)。 沒有指定路徑時，預設會繫結到整個物件。 換句話說,在此示例中,路徑被遺漏了,因為我們將<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性綁定到整個物件。 (有關深入討論[,請參閱綁定到集合](#binding-to-collections)部分。

除了繫結到集合之外，當您要繫結到整個物件而非只是物件的單一屬性時，這個案例也很好用。 例如,如果源物件的類型<xref:System.String>,您可能只想綁定到字串本身。 另一個常用案例是當您要將元素繫結到具有許多屬性的物件時。

您可能需要應用自定義邏輯,以便數據對綁定的目標屬性有意義。 如果不存在預設類型轉換,自定義邏輯可能採用自定義轉換器的形式。 有關轉換器的資訊,請參考[資料轉換](#data-conversion)。

### <a name="binding-and-bindingexpression"></a>繫結和 BindingExpression

在介紹數據綁定的其他功能和用法之前,引入類<xref:System.Windows.Data.BindingExpression>非常有用。 如前一節所示,<xref:System.Windows.Data.Binding>類是聲明綁定的高級類;它提供了許多屬性,允許您指定綁定的特徵。 相關類<xref:System.Windows.Data.BindingExpression>是維護源和目標之間連接的基礎物件。 繫結包含可以跨數種繫結運算式共用的所有資訊。 a<xref:System.Windows.Data.BindingExpression>是不能共用的實例表達式,它包含<xref:System.Windows.Data.Binding>的所有 實例資訊。

請考慮`myDataObject`以下範例,其中是類`MyData`的實體,`myBinding`是<xref:System.Windows.Data.Binding>源`MyData`物件, 是`MyDataProperty`包含名為的字串屬性的已定義類。 此範例將`myText`的文字內容繫結為<xref:System.Windows.Controls.TextBlock>`MyDataProperty`。

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

您可以使用相同的 *myBinding* 物件建立其他繫結。 例如,可以使用*myBinding*物件將選取框的文字內容繫結到*MyDataProperty*。 在這種情況下,將有兩個共用*myBinding*<xref:System.Windows.Data.BindingExpression>物件的 實例。

通過<xref:System.Windows.Data.BindingExpression>調用<xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A>數據綁定物件來返回物件。 以下文章演示了<xref:System.Windows.Data.BindingExpression>類的一些用法:

- [從繫結的目標屬性取得繫結物件](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [控制項文字文字何時更新來源](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>資料轉換

在「[創建綁定](#creating-a-binding)」部分中,按鈕為紅色,因為<xref:System.Windows.Controls.Control.Background%2A>它的屬性綁定到值為「紅色」的字串屬性。 這個字串值之所以有效,是因為類型轉換器存在於類型上<xref:System.Windows.Media.Brush>,用於將字串值轉換為 。 <xref:System.Windows.Media.Brush>

將此資訊添加到圖"[創建綁定](#creating-a-binding)「部分如下所示。

![顯示數據繫結式Default 屬性的圖表。](./media/data-binding-overview/data-binding-button-default-conversion.png)

但是,如果綁定源物件沒有類型字串的屬性,而是具有<xref:System.Windows.Media.Color>*類型的顏色*屬性,該怎麼辦? 在這種情況下,為了使綁定正常工作,您需要首先將*Color*屬性值<xref:System.Windows.Controls.Control.Background%2A>轉換為 屬性接受的內容。 您需要透過連接<xref:System.Windows.Data.IValueConverter>介面來建立自訂轉換器,如以下範例所示。

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

如需相關資訊，請參閱 <xref:System.Windows.Data.IValueConverter>。

現在使用自定義轉換器而不是預設轉換,我們的圖表如下所示。

![顯示數據繫結定自訂轉換器的圖表。](./media/data-binding-overview/data-binding-converter-color-example.png)

再重複聲明一次，預設轉換也可以使用，因為要繫結的型別中存在型別轉換器。 這個行為會取決於目標中提供的型別轉換器。 如果有疑問，請建立自己的轉換器。

以下是一些典型方案,其中實現數據轉換器是有意義的:

- 依據文化特性的不同，您的資料顯示方式會有所不同。 例如,您可能希望基於特定區域性中使用的約定實現貨幣轉換器或日曆日期/時間轉換器。

- 要使用的資料不見得是要變更屬性的文字值，但有可能是改為變更某些其他值，例如影像的來源，或者是顯示文字的色彩或樣式。 在這個情況下可能的轉換器使用方式，是藉由將可能不適合的屬性繫結轉換，例如將文字欄位繫結到表格儲存格的 Background 屬性。

- 控制項多個控制件或多個屬性綁定到同一數據。 在這個情況下，主要繫結可能只是顯示文字，而其他繫結會處理特定顯示問題，但仍然使用相同的繫結做為來源資訊。

- 目標屬性具有繫結定的集合,<xref:System.Windows.Data.MultiBinding>稱為 。 對於<xref:System.Windows.Data.MultiBinding>,使用自<xref:System.Windows.Data.IMultiValueConverter>定義 從綁定的值生成最終值。 舉例來說，顏色可以由紅藍綠的值計算而來，而這些值可以來自相同或不同的繫結來源物件。 有關<xref:System.Windows.Data.MultiBinding>範例和資訊,請參閱。

## <a name="binding-to-collections"></a>繫結到集合

綁定源物件可以被視為屬性包含數據的單個物件,也可以被視為通常分組在一起的多態物件的數據收集(例如對資料庫的查詢結果)。 到目前為止,我們只討論了綁定到單個物件。 但是,綁定到數據收集是常見方案。 例如,常見方案是使用<xref:System.Windows.Controls.ItemsControl>等<xref:System.Windows.Controls.ListBox>,<xref:System.Windows.Controls.ListView><xref:System.Windows.Controls.TreeView>或顯示資料收集,例如在[「什麼是數據綁定」](#what-is-data-binding)部分中顯示的應用中。

所幸，我們的基本圖表仍然適用。 如果要將 綁<xref:System.Windows.Controls.ItemsControl>定 到集合,則關係圖如下所示。

![顯示數據綁定項控制對象的關係圖。](./media/data-binding-overview/data-binding-itemscontrol.png)

如此關係圖所示,要將<xref:System.Windows.Controls.ItemsControl>綁定 到集合<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType>物件 ,屬性是要使用的屬性。 您可以將`ItemsSource`這個視為<xref:System.Windows.Controls.ItemsControl>的內容 。 綁定的原因是<xref:System.Windows.Data.BindingMode.OneWay>默認情況下`ItemsSource`屬性`OneWay`支援 綁定。

### <a name="how-to-implement-collections"></a>如何實現集合

可以枚舉實現<xref:System.Collections.IEnumerable>介面的任何集合。 但是,要設置動態綁定,以便集合中的插入或刪除自動更新 UI,集合必須<xref:System.Collections.Specialized.INotifyCollectionChanged>實現介面。 這個介面會公開每次基礎集合變更時必須引發的事件。

WPF<xref:System.Collections.ObjectModel.ObservableCollection%601>提供 類,<xref:System.Collections.Specialized.INotifyCollectionChanged>它是公開 介面的數據收集的內置實現。 要完全支援將資料值從源物件傳輸到目標,集合中支援可綁定屬性的每個物件還必須實現<xref:System.ComponentModel.INotifyPropertyChanged>介面。 有關詳細資訊,請參閱[綁定源概述](../../framework/wpf/data/binding-sources-overview.md)。

在實現自己的<xref:System.Collections.ObjectModel.ObservableCollection%601>集合之前,請考慮使用或現有集合類之一,<xref:System.Collections.Generic.List%601>例如<xref:System.Collections.ObjectModel.Collection%601>,<xref:System.ComponentModel.BindingList%601>和等。 如果您有高級方案並希望實現自己的集合,請考慮使用<xref:System.Collections.IList>,它提供一個非泛型的物件集合,該集合可以由索引單獨訪問,從而提供最佳性能。

### <a name="collection-views"></a>集合檢視

<xref:System.Windows.Controls.ItemsControl>綁定到數據收集后,可能需要對數據進行排序、篩選或分組。 為此,可以使用集合視圖,集合視圖是實現介面的<xref:System.ComponentModel.ICollectionView>類。

#### <a name="what-are-collection-views"></a>什麼是集合視圖?

集合檢視是以繫結來源集合為基礎的一層，可以讓您依據排序、篩選和群組查詢來巡覽和顯示來源集合，而不需要變更基礎來源集合本身。 集合檢視也會保留集合中目前項目的指標。 如果源集合實現<xref:System.Collections.Specialized.INotifyCollectionChanged>介面<xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged>, 則事件引發的更改將傳播到檢視。

因為檢視不會變更基礎來源集合，每個來源集合可以有多個相關聯的檢視。 舉例來說，您可以有一個 *Task* 物件集合。 使用檢視時，您可以不同方式顯示相同資料。 舉例來說，在頁面左方您可以顯示依優先順序排序的工作，右方顯示依區域分組的工作。

#### <a name="how-to-create-a-view"></a>如何建立檢視

建立和使用檢視的方法之一，是直接具現化檢視物件，然後將它做為繫結來源使用。 例如,請考慮[「什麼是數據綁定」](#what-is-data-binding)部分中顯示的[數據綁定演示][data-binding-demo]應用。 應用的實現使<xref:System.Windows.Controls.ListBox>綁定到數據集上的視圖,而不是直接綁定到數據收集。 以下示例從[數據綁定演示][data-binding-demo]應用中提取。 類別<xref:System.Windows.Data.CollectionViewSource>是從繼承的類別的 XAML<xref:System.Windows.Data.CollectionView>代理程式 。 在此特定範例中,<xref:System.Windows.Data.CollectionViewSource.Source%2A>檢視的綁定到當前應用物件的*拍賣專案*集合(類型<xref:System.Collections.ObjectModel.ObservableCollection%601>)。

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

然後,資源*清單 DataView*充當應用中的元素(如<xref:System.Windows.Controls.ListBox>中的綁定源)。

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

要為同一集合創建另一個檢視,可以創建<xref:System.Windows.Data.CollectionViewSource>另一個實例併為其`x:Key`指定其他名稱。

下表顯示了哪些檢視數據類型創建為預設集合檢視或<xref:System.Windows.Data.CollectionViewSource>基於源集合類型創建。

| 來源集合型別                    | 集合檢視型別 | 注意 |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | 基於內部類型<xref:System.Windows.Data.CollectionView> | 無法群組項目。 |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | 最快。 |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>使用預設檢視

指定集合檢視做為繫結來源是建立和使用集合檢視的方式之一。 WPF 也會為做為繫結來源使用的每個集合建立預設集合檢視。 如果您直接繫結至集合，WPF 會繫結至它的預設檢視。 此預設檢視由同一集合的所有綁定共用,因此由一個綁定控件或代碼對預設檢視所做的更改(如排序或對當前項指標的更改,稍後討論)將反映在對同一集合的所有其他綁定中。

要取得預設檢視,請使用方法<xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A>。 例如,請參閱[獲取資料收集的預設檢視](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)。

#### <a name="collection-views-with-adonet-datatables"></a>具有ADO.NET資料表的集合檢視

為了提高性能,ADO.NET<xref:System.Data.DataTable><xref:System.Data.DataView>或 物件的集合檢視將排序和篩選委託給<xref:System.Data.DataView>, 這將導致在數據源的所有集合視圖中共用排序和篩選。 要使每個集合檢視能夠獨立排序和篩選,使用自己的<xref:System.Data.DataView>物件初始化每個集合視圖。

#### <a name="sorting"></a>排序

如先前所述，檢視可以將排序順序套用到集合上。 當資料存在於基礎集合中時，資料本身可能有也可能沒有相關的順序。 對集合的檢視可以讓您依據所提供的比較準則，安排順序或變更預設順序。 因為是資料的用戶端檢視，常見的案例是使用者會想要針對資料行對應的值，而排序表格式資料的資料行。 藉由使用檢視，就可以套用這個使用者驅動的排序，同樣不需要對基礎集合進行任何變更，或甚至不需要重新查詢集合內容。 例如,請參閱[單擊標題時對 GridView 列進行排序](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)。

下面的範例顯示了應用 UI 在「[什麼是資料綁定」](#what-is-data-binding)部分中的「<xref:System.Windows.Controls.CheckBox>按類別和日期排序」 的排序邏輯。

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtering

視圖還可以將篩選器應用於集合,以便檢視僅顯示完整集合的特定子集。 您可以對資料篩選條件。 例如,正如應用在「[什麼是數據綁定」](#what-is-data-binding)部分所做的那樣,「僅顯示便宜貨<xref:System.Windows.Controls.CheckBox>」 包含篩選出成本為 25 美元或更多的項目的邏輯。 執行以下代碼以在選擇時會*將 「只顯示只討價還價」* 設定<xref:System.Windows.Data.CollectionViewSource.Filter>為 事件<xref:System.Windows.Controls.CheckBox>處理程式 。

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

*"只顯示討價還價"* 事件處理程式具有以下實現。

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

如果直接使用其中一個<xref:System.Windows.Data.CollectionView>類<xref:System.Windows.Data.CollectionViewSource>而不是 ,則可以<xref:System.Windows.Data.CollectionView.Filter%2A>使用 屬性 指定回調。 如需範例，請參閱[篩選檢視中的資料](../../framework/wpf/data/how-to-filter-data-in-a-view.md)。

#### <a name="grouping"></a>分組

除了查看<xref:System.Collections.IEnumerable>集合的內部類外,所有集合視圖都支援*分組*,這允許使用者將集合視圖中的集合分區為邏輯組。 群組可以是明確的，由使用者提供群組清單，或者是隱含的，讓群組依據資料動態產生。

下面的範例顯示了"按類別分組"<xref:System.Windows.Controls.CheckBox>的邏輯。

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

如需另一個群組範例，請參閱[實作 GridView 的 ListView 中的群組項目](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md)。

#### <a name="current-item-pointers"></a>目前項目針

檢視也支援目前項目的概念。 您可以在集合檢視中逐一巡覽物件。 當您巡覽時，移動項目指標可以讓您擷取集合中存在該特定位置的物件。 例如,請參閱[瀏覽資料收集檢視中的物件](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md)。

由於 WPF 只使用檢視 (可能是您指定的檢視或集合的預設檢視) 繫結至集合，因此集合的所有繫結都有目前項目指標。 當繫結至檢視時，`Path` 值中的斜線 ("/") 字元會指定檢視的目前項目。 在下列範例中，資料內容是集合檢視。 第一行繫結至集合。 第二行繫結至集合中的目前項目。 第三行繫結至集合中目前項目的 `Description` 屬性。

```xaml
<Button Content="{Binding }" />
<Button Content="{Binding Path=/}" />
<Button Content="{Binding Path=/Description}" />
```

斜線和屬性語法也可以堆疊來周遊集合的階層架構。 下列範例繫結至名為 `Offices` 之集合的目前項目，此集合是來源集合目前項目的屬性。

```xaml
<Button Content="{Binding /Offices/}" />
```

目前項目指標可能會受套用至集合的任何排序或篩選所影響。 排序會將目前項目指標保留在最後選取的項目上，但現在集合檢視已在其周圍重組結構。 (可能所選專案以前位於清單的開頭,但現在所選項可能位於中間的某個位置。如果篩選后該選擇仍保留在檢視中,則篩選將保留所選項。 否則，目前項目指標會設定在篩選集合檢視的第一個項目。

#### <a name="master-detail-binding-scenario"></a>主詳細資訊繫結方案

目前項目的概念不但對巡覽集合項目很有用，也能應用在主從式繫結案例。 再次考慮[「什麼是數據綁定」](#what-is-data-binding)部分中的應用 UI。 在該應用程式中,中的選擇<xref:System.Windows.Controls.ListBox>確定 中顯示的內容<xref:System.Windows.Controls.ContentControl>。 要以另一種方式放置它,在<xref:System.Windows.Controls.ListBox>選擇專案時<xref:System.Windows.Controls.ContentControl>, 將顯示所選項的詳細資訊。

您可以實作主從式案例，只要藉由讓兩或多個控制項繫結到相同檢視即可。 [數據繫結示範][data-binding-demo]的以下範例在「[什麼是資料綁定」](#what-is-data-binding)部分<xref:System.Windows.Controls.ListBox>中<xref:System.Windows.Controls.ContentControl>顯示 應用 UI 上的標記和中看到的。

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

請注意,兩個控制項都綁定到同一源,*即清單 DataView*靜態資源(請參閱["如何創建視圖"部分](#how-to-create-a-view)中此資源的定義)。 此繫結有效,因為當單例物件(本<xref:System.Windows.Controls.ContentControl>例中)綁定到集合檢視時,它會自動綁定到檢視<xref:System.Windows.Data.CollectionView.CurrentItem%2A>。 對<xref:System.Windows.Data.CollectionViewSource>象 會自動同步貨幣和選擇。 如果清單控制項未綁定到<xref:System.Windows.Data.CollectionViewSource>物件,例如本示例中所示,則需要<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>將其 屬性`true`設置為以正常工作。

有關其他範例,請參閱[連結到集合並根據選擇顯示資訊](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md),並使用[具有階層資料的主詳細資訊模式](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。

您可能已經注意到上述範例有使用範本。 事實上,如果不使用範本(由和<xref:System.Windows.Controls.ContentControl>隱式使用範本)來顯示數據,數據就不會按我們希望的方式顯示。 <xref:System.Windows.Controls.ListBox> 現在，下節中要說明資料範本化。

## <a name="data-templating"></a>製作資料範本

如果不使用數據範本,我們在["什麼是數據綁定"](#what-is-data-binding)部分中的應用 UI 如下所示。

![不含資料範本的資料繫結示範](./media/data-binding-overview/demo-no-template.png)

如上一節中的示例所示,<xref:System.Windows.Controls.ListBox>控件<xref:System.Windows.Controls.ContentControl>和 綁定都綁定到*拍賣專案*的整個集合物件(或更具體地說,對集合物件的視圖)。 如果沒有有關如何顯示資料收集的特定說明,則<xref:System.Windows.Controls.ListBox>顯示基礎集合中每個物件的字串表示形式,<xref:System.Windows.Controls.ContentControl>並顯示綁定到的物件的字串表示形式。

要解決此問題,應用程式定義<xref:System.Windows.DataTemplate?text=DataTemplates>。 如前一個樣本的範例的範<xref:System.Windows.Controls.ContentControl>例, 顯示式使用*詳細資訊產品清單樣本*。 當<xref:System.Windows.Controls.ListBox>集合中顯示*拍賣項目*物件時,控件隱式使用以下數據範本。

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

使用這兩個 DataTemplate 時,生成的 UI 就是[「什麼是數據綁定」](#what-is-data-binding)部分中顯示的 UI。 正如您從該螢幕截圖中看到的,除了允許您將數據放置在控制項中之外,DataTemplate 還允許您為數據定義引人注目的視覺物件。 <xref:System.Windows.DataTrigger>例如,上面<xref:System.Windows.DataTemplate>使用 s,以便具有*高光**特殊功能*值的*拍賣專案*將顯示橙色邊框和星形。

關於資料樣本的詳細資訊,請參考[資料樣本概述](../../framework/wpf/data/data-templating-overview.md)。

## <a name="data-validation"></a>資料驗證

大多數採用使用者輸入的應用都需要具有驗證邏輯,以確保使用者已輸入預期資訊。 驗證檢查可以基於類型、範圍、格式或其他特定於應用的要求。 本節討論數據驗證在 WPF 中的工作原理。

### <a name="associating-validation-rules-with-a-binding"></a>將驗證規則與繫結

WPF 資料繫結模型允許您<xref:System.Windows.Data.Binding.ValidationRules%2A><xref:System.Windows.Data.Binding>與 物件關聯。 例如,下面的示例<xref:System.Windows.Controls.TextBox>將綁定`StartPrice`到名為的屬性<xref:System.Windows.Controls.ExceptionValidationRule>,並將物件添加<xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType>到該 屬性。

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

<xref:System.Windows.Controls.ValidationRule>物件檢查屬性的值是否有效。 WPF 有兩種類型的內<xref:System.Windows.Controls.ValidationRule>建 物件:

- <xref:System.Windows.Controls.ExceptionValidationRule>檢查在更新綁定源屬性期間引發的異常。 在上面的範例中，`StartPrice` 的型別為整數。 當使用者輸入的值無法轉換為整數時，就會擲回例外狀況，造成繫結標記為無效。 <xref:System.Windows.Controls.ExceptionValidationRule>顯式設定的替代語法是<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>將 屬性`true`設置<xref:System.Windows.Data.Binding><xref:System.Windows.Data.MultiBinding>為 或 物件。

- <xref:System.Windows.Controls.DataErrorValidationRule>對象檢查由<xref:System.ComponentModel.IDataErrorInfo>實現介面的物件引發的錯誤。 有關使用此驗證規則的範例,請參閱<xref:System.Windows.Controls.DataErrorValidationRule>。 <xref:System.Windows.Controls.DataErrorValidationRule>顯式設定的替代語法是<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>將 屬性`true`設置<xref:System.Windows.Data.Binding><xref:System.Windows.Data.MultiBinding>為 或 物件。

還可以通過派生<xref:System.Windows.Controls.ValidationRule>類和<xref:System.Windows.Controls.ValidationRule.Validate%2A>實現 方法創建自己的驗證規則。 下面的範例顯示了 *「添加產品清單*」開始日期<xref:System.Windows.Controls.TextBox>"在[「什麼是數據綁定](#what-is-data-binding)」部分使用的規則。

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*StartDateEntryForm*<xref:System.Windows.Controls.TextBox>使用此*未來日期規則*,如以下示例所示。

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

由於<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>為 ,綁定引擎會更新每個擊鍵的源值,這意味著它還會檢查<xref:System.Windows.Data.Binding.ValidationRules%2A>集合中 每個擊鍵中的每個規則。 我們將在＜驗證程序＞一節進一步討論這個部分。

### <a name="providing-visual-feedback"></a>提供視覺回饋

如果使用者輸入無效值,您可能需要提供有關應用 UI 上的錯誤的一些反饋。 提供此類回饋的一種方法是附加<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>屬性設定為自訂<xref:System.Windows.Controls.ControlTemplate>。 如上一節所示 *,StartDateEntryForm*<xref:System.Windows.Controls.TextBox>使用<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>稱為*驗證範本*。 下面的示例顯示了*驗證範本*的定義。

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

該<xref:System.Windows.Controls.AdornedElementPlaceholder>元素指定應放置要修飾的控制項的位置。

此外,您還可以使用顯示<xref:System.Windows.Controls.ToolTip>錯誤訊息。 *StartDateEntryForm*和*StartPriceentryForm*<xref:System.Windows.Controls.TextBox>都使用樣式*文字樣式文字Box*,它建立顯示<xref:System.Windows.Controls.ToolTip>錯誤訊息的 樣式文字文字Box 。 下列範例顯示 *textStyleTextBox* 的定義。 附加屬性<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>`true`是在綁定元素的屬性上的一個或多個綁定出錯時。

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

當出現驗證<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>錯誤<xref:System.Windows.Controls.ToolTip>時 ,使用 自訂和啟動*日期輸入窗體*<xref:System.Windows.Controls.TextBox>如下所示。

![資料繫結驗證錯誤](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

<xref:System.Windows.Data.Binding>如果具有關聯的驗證規則,但未在綁定控制項上<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>指定, 則<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>當存在 驗證錯誤時,將使用預設值通知使用者。 默認值<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>是定義裝飾層中的紅色邊框的控制範本。 當出現驗證<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>錯誤<xref:System.Windows.Controls.ToolTip>時 ,使用預設值和 的 UI 時 *,StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>的 UI 如下所示。

![資料繫結驗證錯誤](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

有關如何提供邏輯以驗證對話方塊中的所有控制項的範例,請參閱[對話方塊概述](../../framework/wpf/app-development/dialog-boxes-overview.md)中的「自定義對話框」 部分。

### <a name="validation-process"></a>驗證過程

通常驗證發生的時機，是將目標的值傳輸到繫結來源屬性的時候。 此傳輸發生在<xref:System.Windows.Data.BindingMode.TwoWay>和<xref:System.Windows.Data.BindingMode.OneWayToSource>綁定上。 要重申,源更新的原因取決於<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性的值,如[「什麼觸發源更新](#what-triggers-source-updates)」部分所述。

以下項描述*驗證*過程。 如果在此過程中的任何時間發生驗證錯誤或其他類型的錯誤,則行程將停止:

1. 綁定引擎檢查<xref:System.Windows.Controls.ValidationRule>是否有任何自定義物件定義<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>其<xref:System.Windows.Controls.ValidationStep.RawProposedValue>設置<xref:System.Windows.Data.Binding>為 該 ,在這種情況下,<xref:System.Windows.Controls.ValidationRule.Validate%2A><xref:System.Windows.Controls.ValidationRule>它調用每個 物件上的方法,直到其中一個運行錯誤或直到所有物件都通過。

2. 接著，繫結引擎就會在有轉換器的情況下呼叫轉換器。

3. 如果轉換器成功,綁定引擎將檢查是否有任何自定義<xref:System.Windows.Controls.ValidationRule>物件定義<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>其<xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue>設置<xref:System.Windows.Data.Binding>為 該 物件,在這種情況下,它<xref:System.Windows.Controls.ValidationRule.Validate%2A><xref:System.Windows.Controls.ValidationRule><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>會調用<xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue>每個 已設置為 的方法,直到其中一個物件遇到錯誤或直到所有對象都通過。

4. 繫結引擎會設定來源屬性。

5. 綁定引擎<xref:System.Windows.Controls.ValidationRule>檢查是否有任何自定義物件定義<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>其<xref:System.Windows.Controls.ValidationStep.UpdatedValue>設置<xref:System.Windows.Data.Binding>為 該 物件,在這種情況下,它<xref:System.Windows.Controls.ValidationRule.Validate%2A><xref:System.Windows.Controls.ValidationRule><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>會調用<xref:System.Windows.Controls.ValidationStep.UpdatedValue>每個 已設置為 的方法,直到其中一個物件遇到錯誤或直到所有物件都通過。 如果<xref:System.Windows.Controls.DataErrorValidationRule>與繫結的關聯,並且<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>設定為預設值<xref:System.Windows.Controls.ValidationStep.UpdatedValue>, 此時會<xref:System.Windows.Controls.DataErrorValidationRule>檢查 。 此時,<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>`true`將檢查具有集的任何綁定。

6. 綁定引擎<xref:System.Windows.Controls.ValidationRule>檢查是否有任何自定義物件定義<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>其<xref:System.Windows.Controls.ValidationStep.CommittedValue>設置<xref:System.Windows.Data.Binding>為 該 物件,在這種情況下,它<xref:System.Windows.Controls.ValidationRule.Validate%2A><xref:System.Windows.Controls.ValidationRule><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>會調用<xref:System.Windows.Controls.ValidationStep.CommittedValue>每個 已設置為 的方法,直到其中一個物件遇到錯誤或直到所有物件都通過。

如果<xref:System.Windows.Controls.ValidationRule>在整個過程中任何時候都未傳遞 ,綁定引擎將創建<xref:System.Windows.Controls.ValidationError>一個 物件並將其添加到<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>綁定元素 的集合中。 在綁定引擎在任何給定步驟<xref:System.Windows.Controls.ValidationRule>上運行物件之前,它會刪除該步驟<xref:System.Windows.Controls.ValidationError>期間 添加到綁<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>定元素的附加屬性的任何內容。 例如,如果設置為<xref:System.Windows.Controls.ValidationRule><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A><xref:System.Windows.Controls.ValidationStep.UpdatedValue>失敗<xref:System.Windows.Controls.ValidationError>的 ,則下次發生驗證過程時,綁定引擎將刪除它調<xref:System.Windows.Controls.ValidationRule>用<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>任何<xref:System.Windows.Controls.ValidationStep.UpdatedValue>已設置為之前。

當<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>不為空時,<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>元素的附加屬性設定為`true`。 此外,如果<xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>的屬性<xref:System.Windows.Data.Binding>設置為`true`,則綁定引擎<xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType>將附加事件引發元素。

另請注意,向任一方向(目標到源或源到目標)的有效值轉移將清除<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>附加屬性。

如果繫結具與其關聯的綁定<xref:System.Windows.Controls.ExceptionValidationRule>,或者<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>將 屬性`true`設定為 ,並在綁定引擎設定來源時引發異常,則綁定引擎將<xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>檢查是否有 。 您可以選擇使用<xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>回調來提供用於處理異常的自定義處理程式。 如果在<xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A><xref:System.Windows.Data.Binding>上 未指定 , 繫<xref:System.Windows.Controls.ValidationError>結引擎將建立 具有異常的<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>, 並將其新增到 綁定元素的集合中。

## <a name="debugging-mechanism"></a>除錯機制

您可以在綁定相關物件上設置<xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType>附加屬性以接收有關特定綁定狀態的資訊。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [繫結到 LINQ 查詢的結果](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [資料繫結](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [資料繫結示範][data-binding-demo]
- [如何使用的文章](../../framework/wpf/data/data-binding-how-to-topics.md)
- [繫結至 ADO.NET 資料來源](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "資料繫結示範應用程式"
