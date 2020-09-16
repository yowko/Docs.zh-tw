---
title: 資料繫結概觀
description: 瞭解您可以在適用于 .NET Core 的 Windows Presentation Foundation 中加入專案的不同資料來源。 資料來源可系結至 XAML 元素，以建立動態應用程式。
author: adegeo
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: b187b8a274ab770c28d2c2bc2a9be621b501e842
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555766"
---
# <a name="data-binding-overview-in-wpf"></a>WPF 中的資料系結總覽

Windows Presentation Foundation 中的資料系結 (WPF) 提供簡單且一致的方式，讓應用程式呈現資料並與之互動。 專案可以從各種資料來源中的資料，以 .NET 物件和 XML 的形式系結。 任何（例如和 <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView> ）都有內建功能，可啟用單一資料項目或資料項目集合的彈性樣式。 您可以在資料上方產生排序、篩選和群組檢視。

WPF 中的資料系結功能有幾項優點，而不是傳統的模型，包括資料系結的固有支援，由廣泛的屬性、彈性的 UI 標記法，以及將商務邏輯從 UI 中清楚分隔。

本文先討論 WPF 資料系結的基本概念，然後涵蓋類別的使用方式 <xref:System.Windows.Data.Binding> ，以及資料系結的其他功能。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>資料繫結是什麼？

資料系結是在應用程式 UI 與其顯示的資料之間建立連接的程式。 如果繫結具有正確的設定而且資料提供了適當的通知，當資料變更其值時，繫結至資料的項目就會自動反映變更。 資料繫結也代表在元素資料的外部表示變更時，基礎資料也會自動更新以反映變更。 例如，如果使用者編輯元素中的值 `TextBox` ，則會自動更新基礎資料值以反映該變更。

資料系結的一般用法是將伺服器或本機設定資料放入表單或其他 UI 控制項。 在 WPF 中，此概念已擴充，以包含將廣泛的屬性系結至各種不同的資料來源。 在 WPF 中，元素的相依性屬性可以系結至 .NET 物件 (包括與 Web 服務和 Web 屬性相關聯的 ADO.NET 物件或物件) 和 XML 資料。

如需資料系結的範例，請從資料系結 [示範][data-binding-demo]中查看下列應用程式 UI，以顯示拍賣專案清單。

![資料系結範例螢幕擷取畫面](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

應用程式會示範下列資料系結功能：

- ListBox 的內容會系結至 *>auctionitem* 物件的集合。 *>auctionitem*物件具有諸如*Description*、 *StartPrice*、開始*日期*、*類別目錄*、 *>auctionitem*等的屬性。

- ) 中所顯示的資料 (*>auctionitem* 物件 `ListBox` 會樣板化，以便顯示每個專案的描述和目前價格。 使用建立範本 <xref:System.Windows.DataTemplate> 。 除此之外，每個項目的外觀取決於所顯示 *AuctionItem* 的 *SpecialFeatures* 值。 如果 *AuctionItem* 的 *SpecialFeatures* 值是 *Color*，項目就具有藍色框線。 如果值是 *Highlight*，項目就具有橘色框線和星號。 [資料範本化](#data-templating)一節會提供資料範本化的相關資訊。

- 使用者可以使用提供的來群組、篩選或排序資料 `CheckBoxes` 。 在上圖中，已選取 [ **依類別分組** ] 和 [ **依類別目錄排序] 和 [日期**] `CheckBoxes` 。 您可能已經注意到，資料的群組化是依據產品的分類，且分類名稱是以字母順序排列。 雖然在圖中很難辨識，但項目在每個分類內也有以開始日期排序。 排序是使用「 *收集視圖*」來完成。 [系結 [至集合](#binding-to-collections) ] 區段討論集合視圖。

- 當使用者選取專案時，會 <xref:System.Windows.Controls.ContentControl> 顯示所選取專案的詳細資料。 這項體驗稱為 *主要詳細資料案例*。 [主從階層案例](#master-detail-binding-scenario)一節提供有關此系結類型的資訊。

- *起始*屬性的類型是 <xref:System.DateTime> ，它會傳回包含毫秒時間的日期。 在此應用程式中，已使用自訂轉換器，以便顯示較短的日期字串。 [ [資料轉換](#data-conversion) ] 區段提供轉換器的相關資訊。

當使用者選取 [ *新增產品* ] 按鈕時，會出現下列表單。

![加入產品清單頁面](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

使用者可以編輯表單中的欄位、使用簡短或詳細的預覽窗格來預覽產品清單，然後選取 `Submit` 加入新的產品清單。 任何現有的群組、篩選和排序設定都會套用到新專案。 在這種特定情形下，輸入上圖的項目會在 [Computer (電腦)]** 分類內顯示為第二個項目。

此映射中未顯示的是 *開始日期*中所提供的驗證邏輯 <xref:System.Windows.Controls.TextBox> 。 如果使用者輸入不正確日期 (格式無效或過去的日期) ，使用者將會收到一則通知，其旁邊會有 <xref:System.Windows.Controls.ToolTip> 紅色驚嘆號 <xref:System.Windows.Controls.TextBox> 。 [資料驗證](#data-validation)一節會討論如何建立驗證邏輯。

在進入上述資料系結的不同功能之前，我們會先討論瞭解 WPF 資料系結的重要基本概念。

## <a name="basic-data-binding-concepts"></a>基本資料系結概念

無論您系結的專案和資料來源的本質為何，每個系結一律遵循下圖所示的模型。

![顯示基本資料系結模型的圖表。](./media/data-binding-overview/basic-data-binding-diagram.png)

如圖所示，資料系結基本上是您的系結目標與系結來源之間的橋樑。 下圖將示範下列基本的 WPF 資料系結概念：

- 一般而言，每個系結都有四個元件：

  - 系結目標物件。
  - 目標屬性。
  - 繫結來源。
  - 要使用之系結來源中的值路徑。
  
  > 例如，如果您想要將的內容系結 `TextBox` 至 `Employee.Name` 屬性，您的目標物件是 `TextBox` 、目標屬性為 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性、要使用的值為 *Name*，而且來源物件是 *Employee* 物件。

- 目標屬性必須是相依性屬性。 大部分的 <xref:System.Windows.UIElement> 屬性是相依性屬性，而大部分的相依性屬性（唯讀除外）預設都支援資料系結。  (衍生自的型別只能定義相依性 <xref:System.Windows.DependencyObject> 屬性，而且所有型別都是 <xref:System.Windows.UIElement> 衍生自 `DependencyObject` 。 ) 

- 雖然圖中未顯示，但請注意，系結來源物件不會限制為自訂的 .NET 物件。 WPF 資料系結支援 .NET 物件和 XML 格式的資料。 為了提供一些範例，您的系結來源可能是 <xref:System.Windows.UIElement> 、任何清單物件、ADO.NET 或 Web 服務物件，或是包含 XML 資料的 XmlNode。 如需詳細資訊，請參閱系結 [來源總覽](/dotnet/desktop/wpf/data/binding-sources-overview)。

請務必記住，當您建立系結時，會將系結目標系結 *至* 系結來源。 例如，如果您使用資料系結在中顯示一些基礎 XML 資料 <xref:System.Windows.Controls.ListBox> ，則會將系結 `ListBox` 至 XML 資料。

若要建立系結，請使用 <xref:System.Windows.Data.Binding> 物件。 本文的其餘部分將討論許多相關概念，以及物件的一些屬性和使用方式 `Binding` 。

### <a name="direction-of-the-data-flow"></a>資料流程的方向

如上圖中的箭號所示，系結的資料流程可以從系結目標移至系結來源 (例如，當使用者編輯) 的值和/或從系結來源到系結目標時，來源值 `TextBox` 會變更 (例如，如果系結 `TextBox` 來源提供適當的通知，您的內容就會以系結來源) 的變更進行更新。

您可能想要讓您的應用程式能夠讓使用者變更資料，並將資料傳播回來源物件。 或者您可能不希望使用者更新來源資料。 您可以藉由設定來控制資料的流程 <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> 。

下圖說明不同類型的資料流程：

![資料繫結資料流程](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay> 系結會導致來源屬性的變更自動更新目標屬性，但對目標屬性的變更不會傳播回來源屬性。 如果要繫結的控制項是隱含唯讀的，這種類型的繫結很適當。 例如，您可以系結至來源（例如股票行情），或您的目標屬性沒有提供任何控制項介面來進行變更，例如資料表的資料系結背景色彩。 如果沒有需要監視目標屬性的變更，則使用 <xref:System.Windows.Data.BindingMode.OneWay> 繫結模式可以避免 <xref:System.Windows.Data.BindingMode.TwoWay> 繫結模式所帶來的負荷。

- <xref:System.Windows.Data.BindingMode.TwoWay> 系結會導致來源屬性或目標屬性的變更自動更新另一個屬性。 這種類型的系結適用于可編輯的表單或其他完全互動的 UI 案例。 大部分的屬性預設為系結 <xref:System.Windows.Data.BindingMode.OneWay> ，但某些相依性屬性 (一般使用者可編輯控制項的屬性，例如 <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> 和  [核取方塊。 IsChecked](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) 預設為系結 <xref:System.Windows.Data.BindingMode.TwoWay> 。 以程式設計方式判斷相依性屬性是否預設系結單向或雙向，是要取得屬性中繼資料 <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> ，然後檢查屬性的布林值 <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> 。

- <xref:System.Windows.Data.BindingMode.OneWayToSource> 是系結的反向 <xref:System.Windows.Data.BindingMode.OneWay> ; 當目標屬性變更時，它會更新來源屬性。 其中一個範例案例是您只需要重新評估來自 UI 的來源值。

- 圖中未說明的是系結 <xref:System.Windows.Data.BindingMode.OneTime> ，這會導致來源屬性初始化目標屬性，但不會傳播後續的變更。 如果資料內容變更或資料內容中的物件有所變更，則 *不* 會在目標屬性中反映變更。 如果目前狀態的快照集是適當的，或是資料是真正靜態的，則這種類型的系結是適當的。 如果您想要以來源屬性的某些值初始化目標屬性，但無法預先得知資料內容，則此類型的繫結也很有用。 這種模式基本上是較簡單的系結形式 <xref:System.Windows.Data.BindingMode.OneWay> ，可在來源值未變更的情況下提供較佳的效能。

若要偵測來源變更 (適用于和系結 <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay>) ，來源必須執行適當的屬性變更通知機制，例如 <xref:System.ComponentModel.INotifyPropertyChanged> 。 請參閱如何：實作為執行範例的 [屬性變更通知](/dotnet/desktop/wpf/data/how-to-implement-property-change-notification) <xref:System.ComponentModel.INotifyPropertyChanged> 。

<xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>屬性提供有關系結模式的詳細資訊，以及如何指定系結方向的範例。

### <a name="what-triggers-source-updates"></a>觸發程式來源更新

在 <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> 目標屬性中或接聽變更的系結，並將其傳播回來源（稱為更新來源）。 舉例來說，您可以編輯 TextBox 的文字以變更基礎來源值。

但是，當您編輯文字時，或是在編輯完文字且控制項失去焦點之後，您的來源值會更新？ <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType>屬性會決定觸發來源更新的原因。 下圖中的右箭號點說明屬性的角色 <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> 。

![顯示 System.windows.data.binding.updatesourcetrigger 屬性角色的圖表。](./media/data-binding-overview/data-binding-updatesource-trigger.png)

如果 `UpdateSourceTrigger` 值為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType> ，則當目標屬性變更時，或系結的向右箭號所指向的值 <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> 就會立即更新。 但是，如果 `UpdateSourceTrigger` 值為 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> ，則只有當目標屬性失去焦點時，該值才會以新的值更新。

與屬性類似 <xref:System.Windows.Data.Binding.Mode%2A> ，不同的相依性屬性有不同的預設 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值。 大多數相依性屬性的預設值為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>，而 `TextBox.Text` 屬性具有 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> 的預設值。 `PropertyChanged` 這表示當目標屬性變更時，通常會發生來源更新。 立即變更適用于核取方塊和其他簡單控制項。 不過，對於文字欄位，在每次按鍵後進行更新可能會降低效能，並拒絕使用者在認可新值之前，倒退鍵和修正輸入錯誤的一般機會。

如需 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 如何尋找相依性屬性之預設值的相關資訊，請參閱屬性頁。

下錶針對 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 使用作為範例的每個值提供範例案例 <xref:System.Windows.Controls.TextBox> 。

| UpdateSourceTrigger 值 | 當來源值更新時 | TextBox 的範例案例 |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`)  (預設值 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> | TextBox 控制項失去焦點時。 | 與驗證邏輯相關聯的文字方塊 (請參閱以下) 的 [資料驗證](#data-validation) 。 |
| `PropertyChanged` | 當您在中輸入時 <xref:System.Windows.Controls.TextBox> 。 | 聊天室視窗中的 TextBox 控制項。 |
| `Explicit` | 當應用程式呼叫時 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> 。 | 編輯表單中的 TextBox 控制項 (只有當使用者按一下 [提交] 按鈕時，才會更新來源值) 。 |

如需範例，請參閱 how [to：控制 TextBox 文字更新來源](/dotnet/desktop/wpf/data/how-to-control-when-the-textbox-text-updates-the-source)的時機。

## <a name="creating-a-binding"></a>建立系結

若要重新聲明先前章節中討論的一些概念，您可以使用物件建立系結 <xref:System.Windows.Data.Binding> ，而且每個系結通常有四個元件：系結目標、目標屬性、系結來源，以及要使用之來源值的路徑。 本節討論如何設定繫結。

請考慮下列範例，其中的繫結來源物件是名為 *MyData* 的類別，定義於 *SDKSample* 命名空間中。 基於示範目的， *MyData* 具有名為 *ColorName* 的字串屬性，其值會設定為 "Red"。 因此，本範例會產生具有紅色背景的按鈕。

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

如需系結宣告語法的詳細資訊，以及如何在程式碼中設定系結的範例，請參閱系結宣告 [總覽](/dotnet/desktop/wpf/data/binding-declarations-overview)。

如果將這個範例套用到我們的基本圖表，結果會類似下圖。 此圖描述系結， <xref:System.Windows.Data.BindingMode.OneWay> 因為 Background 屬性預設支援系結 <xref:System.Windows.Data.BindingMode.OneWay> 。

![顯示資料系結背景屬性的圖表。](./media/data-binding-overview/data-binding-button-background-example.png)

您可能會想知道此系結的運作原因，即使 *ColorName* 屬性是字串類型，而屬性的型別為 <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Media.Brush> 。 這個系結會使用「 [資料轉換](#data-conversion) 」一節中討論的預設型別轉換。

### <a name="specifying-the-binding-source"></a>指定系結來源

請注意，在上述範例中，系結來源是藉由設定 [DockPanel](xref:System.Windows.FrameworkElement.DataContext) 屬性來指定。 <xref:System.Windows.Controls.Button>然後繼承的 <xref:System.Windows.FrameworkElement.DataContext%2A> 值 <xref:System.Windows.Controls.DockPanel> ，也就是其父元素。 再重複聲明一次，繫結來源物件是繫結的四個必要元件之一。 因此，沒有指定繫結來源物件，就無法進行繫結。

有數種方式可以指定繫結來源物件。 <xref:System.Windows.FrameworkElement.DataContext%2A>當您將多個屬性系結至相同的來源時，在父元素上使用屬性會很有用。 然而，有時候在個別的繫結宣告上指定繫結來源可能比較恰當。 在上述範例中， <xref:System.Windows.FrameworkElement.DataContext%2A> 您可以直接在按鈕的系結宣告上設定屬性，以指定系結來源（如下列範例所示），而不是使用屬性 <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> 。

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

除了 <xref:System.Windows.FrameworkElement.DataContext%2A> 直接在專案上設定屬性之外， <xref:System.Windows.FrameworkElement.DataContext%2A> 也會繼承上階 (的值（例如第一個範例) 中的按鈕），並藉由設定系結的 <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> 屬性（例如最後一個範例) 的按鈕）來明確指定系結來源 (例如，您也可以使用 <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> 屬性或 <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> 屬性來指定系結來源。 當您要系 <xref:System.Windows.Data.Binding.ElementName%2A> 結至應用程式中的其他專案（例如，當您使用滑杆來調整按鈕的寬度）時，屬性會很有用。 <xref:System.Windows.Data.Binding.RelativeSource%2A>當在或中指定系結時，屬性會很有用 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Style> 。 如需詳細資訊，請參閱 [如何：指定](/dotnet/desktop/wpf/data/how-to-specify-the-binding-source)系結來源。

### <a name="specifying-the-path-to-the-value"></a>指定值的路徑

如果您的系結來源是物件，您可以使用 <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> 屬性來指定要用於系結的值。 如果您要系結至 XML 資料，請使用 <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> 屬性來指定值。 在某些情況下，即使您的資料是 XML，也可能適用于使用 <xref:System.Windows.Data.Binding.Path%2A> 屬性。 例如，如果您想要存取傳回的 XmlNode (的 Name 屬性（因為 XPath 查詢) 的結果），除了屬性之外，您還應該使用 <xref:System.Windows.Data.Binding.Path%2A> 屬性 <xref:System.Windows.Data.Binding.XPath%2A> 。

如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.Path%2A> 和 <xref:System.Windows.Data.Binding.XPath%2A> 屬性。

雖然我們已強調 <xref:System.Windows.Data.Binding.Path%2A> 要使用的值是系結的四個必要元件之一，但是在您想要系結至整個物件的案例中，要使用的值會與系結來源物件相同。 在這些情況下，它適用于不指定 <xref:System.Windows.Data.Binding.Path%2A> 。 請思考一下下列範例。

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

上述範例使用空白繫結語法：{Binding}。 在此情況下， <xref:System.Windows.Controls.ListBox> 會從父 DockPanel 元素繼承 DataCoNtext， (不會在此範例) 中顯示。 沒有指定路徑時，預設會繫結到整個物件。 換句話說，在此範例中，因為我們要將屬性系結至整個物件，所以已省略路徑 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 。  (請參閱「系結 [至集合](#binding-to-collections) 」一節，以取得深入討論。 ) 

除了繫結到集合之外，當您要繫結到整個物件而非只是物件的單一屬性時，這個案例也很好用。 例如，如果您的來源物件是型別 <xref:System.String> ，您可能只想要系結至字串本身。 另一個常用案例是當您要將元素繫結到具有許多屬性的物件時。

您可能需要套用自訂邏輯，讓資料對您的系結目標屬性有意義。 如果預設類型轉換不存在，自訂邏輯可能會以自訂轉換器的形式呈現。 如需轉換器的詳細資訊，請參閱 [資料轉換](#data-conversion) 。

### <a name="binding-and-bindingexpression"></a>繫結和 BindingExpression

在進入資料系結的其他功能和使用方式之前，請先介紹 <xref:System.Windows.Data.BindingExpression> 類別。 如上一節所示，類別是系結宣告的 <xref:System.Windows.Data.Binding> 高階類別，它提供了許多屬性，可讓您指定系結的特性。 相關的類別 <xref:System.Windows.Data.BindingExpression> 是基礎物件，可維護來源與目標之間的連接。 繫結包含可以跨數種繫結運算式共用的所有資訊。 <xref:System.Windows.Data.BindingExpression>是無法共用的實例運算式，而且包含的所有實例資訊 <xref:System.Windows.Data.Binding> 。

請考慮下列範例，其中 `myDataObject` 是類別的實例 `MyData` 、 `myBinding` 是來源 <xref:System.Windows.Data.Binding> 物件，而且 `MyData` 是包含名為之字串屬性的定義類別 `ColorName` 。 此範例會將實例的文字內容系結 `myText` <xref:System.Windows.Controls.TextBlock> 至 `ColorName` 。

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

您可以使用相同的 *myBinding* 物件建立其他繫結。 例如，您可以使用 *>mybinding* 物件，將核取方塊的文字內容系結至 *ColorName*。 在該案例中，會有兩個 <xref:System.Windows.Data.BindingExpression> 共用 *>mybinding* 物件的實例。

藉 <xref:System.Windows.Data.BindingExpression> 由 <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> 在資料繫結物件上呼叫來傳回物件。 下列文章示範類別的一些使用方式 <xref:System.Windows.Data.BindingExpression> ：

- [從繫結的目標屬性取得繫結物件](/dotnet/desktop/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property)

- [控制 TextBox 文字更新來源的時機](/dotnet/desktop/wpf/data/how-to-control-when-the-textbox-text-updates-the-source)

## <a name="data-conversion"></a>資料轉換

在 [ [建立](#creating-a-binding) 系結] 區段中，按鈕是紅色的，因為它的屬性系結 <xref:System.Windows.Controls.Control.Background%2A> 至值為 "red" 的字串屬性。 這個字串值有效，因為類型轉換器存在於類型上 <xref:System.Windows.Media.Brush> ，以將字串值轉換成 <xref:System.Windows.Media.Brush> 。

在 [ [建立](#creating-a-binding) 系結] 區段中，將這項資訊新增至圖表看起來會像這樣。

![顯示資料系結預設屬性的圖表。](./media/data-binding-overview/data-binding-button-default-conversion.png)

但是，如果您的系結來源物件具有類型的 *色彩* 屬性，那麼您的系結來源物件是什麼 <xref:System.Windows.Media.Color> ？ 在這種情況下，為了讓系結正常運作，您必須先將 *Color* 屬性值轉換成屬性所接受的內容 <xref:System.Windows.Controls.Control.Background%2A> 。 您必須藉由執行介面來建立自訂轉換器 <xref:System.Windows.Data.IValueConverter> ，如下列範例所示。

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

如需相關資訊，請參閱 <xref:System.Windows.Data.IValueConverter> 。

現在會使用自訂轉換器來取代預設轉換，而我們的圖表看起來會像這樣。

![顯示資料系結自訂轉換器的圖表。](./media/data-binding-overview/data-binding-converter-color-example.png)

再重複聲明一次，預設轉換也可以使用，因為要繫結的型別中存在型別轉換器。 這個行為會取決於目標中提供的型別轉換器。 如果有疑問，請建立自己的轉換器。

以下是執行資料轉換器的一些典型案例：

- 依據文化特性的不同，您的資料顯示方式會有所不同。 例如，您可能會想要根據特定文化特性所使用的慣例，來執行貨幣轉換器或行事曆日期/時間轉換器。

- 要使用的資料不見得是要變更屬性的文字值，但有可能是改為變更某些其他值，例如影像的來源，或者是顯示文字的色彩或樣式。 在這個情況下可能的轉換器使用方式，是藉由將可能不適合的屬性繫結轉換，例如將文字欄位繫結到表格儲存格的 Background 屬性。

- 控制項有一個以上的控制項或多個屬性系結至相同的資料。 在這個情況下，主要繫結可能只是顯示文字，而其他繫結會處理特定顯示問題，但仍然使用相同的繫結做為來源資訊。

- 目標屬性具有系結的集合，也稱為 <xref:System.Windows.Data.MultiBinding> 。 針對 <xref:System.Windows.Data.MultiBinding> ，您可以使用自訂，從系結的 <xref:System.Windows.Data.IMultiValueConverter> 值產生最後的值。 舉例來說，顏色可以由紅藍綠的值計算而來，而這些值可以來自相同或不同的繫結來源物件。 <xref:System.Windows.Data.MultiBinding>如需範例和資訊，請參閱。

## <a name="binding-to-collections"></a>系結至集合

系結來源物件可視為單一物件，該物件的屬性包含資料，或做為多型物件的資料集合，這些物件通常會群組在一起 (例如查詢到資料庫) 的結果。 到目前為止，我們只討論過單一物件的系結。 不過，系結至資料集合是常見的情況。 例如，常見的案例是使用 <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox> 、或之類的 <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.TreeView> 來顯示資料集合，例如「 [什麼是資料](#what-is-data-binding) 系結」一節中所示的應用程式。

所幸，我們的基本圖表仍然適用。 如果您要將系結 <xref:System.Windows.Controls.ItemsControl> 至集合，此圖表看起來會像這樣。

![顯示資料系結 ItemsControl 物件的圖表。](./media/data-binding-overview/data-binding-itemscontrol.png)

如下圖所示，若要將系結 <xref:System.Windows.Controls.ItemsControl> 至集合物件， <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> 屬性是要使用的屬性。 您可以把 `ItemsSource` 視為的內容 <xref:System.Windows.Controls.ItemsControl> 。 系結是 <xref:System.Windows.Data.BindingMode.OneWay> 因為 `ItemsSource` 屬性預設支援系結 `OneWay` 。

### <a name="how-to-implement-collections"></a>如何執行集合

您可以列舉任何實作為介面的集合 <xref:System.Collections.IEnumerable> 。 不過，若要設定動態系結，讓集合中的插入或刪除自動更新 UI，則集合必須執行 <xref:System.Collections.Specialized.INotifyCollectionChanged> 介面。 這個介面會公開每次基礎集合變更時必須引發的事件。

WPF 提供 <xref:System.Collections.ObjectModel.ObservableCollection%601> 類別，這是公開介面之資料集合的內建實作為 <xref:System.Collections.Specialized.INotifyCollectionChanged> 。 若要完全支援將資料值從源物件傳送到目標，您集合中支援可系結屬性的每個物件也必須執行 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。 如需詳細資訊，請參閱系結 [來源總覽](/dotnet/desktop/wpf/data/binding-sources-overview)。

在執行您自己的集合之前，請考慮使用 <xref:System.Collections.ObjectModel.ObservableCollection%601> 或其中一個現有的集合類別，例如 <xref:System.Collections.Generic.List%601> 、 <xref:System.Collections.ObjectModel.Collection%601> 和等等 <xref:System.ComponentModel.BindingList%601> 。 如果您有 advanced 案例，而且想要執行自己的集合，請考慮使用 <xref:System.Collections.IList> ，它會提供可由索引個別存取的非泛型物件集合，進而提供最佳效能。

### <a name="collection-views"></a>集合檢視

一旦系結 <xref:System.Windows.Controls.ItemsControl> 至資料集合之後，您可能會想要排序、篩選或分組資料。 若要這樣做，您可以使用集合視圖，也就是實作為介面的類別 <xref:System.ComponentModel.ICollectionView> 。

#### <a name="what-are-collection-views"></a>什麼是集合查看？

集合檢視是以繫結來源集合為基礎的一層，可以讓您依據排序、篩選和群組查詢來巡覽和顯示來源集合，而不需要變更基礎來源集合本身。 集合檢視也會保留集合中目前項目的指標。 如果來源集合實作為 <xref:System.Collections.Specialized.INotifyCollectionChanged> 介面，事件所引發的變更 <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> 就會傳播到 views。

因為檢視不會變更基礎來源集合，每個來源集合可以有多個相關聯的檢視。 舉例來說，您可以有一個 *Task* 物件集合。 使用檢視時，您可以不同方式顯示相同資料。 舉例來說，在頁面左方您可以顯示依優先順序排序的工作，右方顯示依區域分組的工作。

#### <a name="how-to-create-a-view"></a>如何建立檢視

建立和使用檢視的方法之一，是直接具現化檢視物件，然後將它做為繫結來源使用。 例如，請考慮「[何謂資料](#what-is-data-binding)系結」一節中所示的資料系結[示範][data-binding-demo]應用程式。 應用程式會實作為系結 <xref:System.Windows.Controls.ListBox> 至資料集合的觀點，而不是直接系結至資料收集。 下列範例會從資料系結 [示範][data-binding-demo] 應用程式中解壓縮。 <xref:System.Windows.Data.CollectionViewSource>類別是繼承自之類別的 XAML proxy <xref:System.Windows.Data.CollectionView> 。 在此特定範例中， <xref:System.Windows.Data.CollectionViewSource.Source%2A> 視圖的會系結至*AuctionItems* <xref:System.Collections.ObjectModel.ObservableCollection%601> 目前應用程式物件) 類型 (的 AuctionItems 集合。

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

然後，資源 *>listingdataview* 會作為應用程式元素的系結來源，例如 <xref:System.Windows.Controls.ListBox> 。

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

若要為相同的集合建立另一個視圖，您可以建立另一個 <xref:System.Windows.Data.CollectionViewSource> 實例，並為它指定不同的 `x:Key` 名稱。

下表顯示建立為預設收集視圖的視圖資料類型，或 <xref:System.Windows.Data.CollectionViewSource> 根據來源集合類型而建立的視圖資料類型。

| 來源集合型別                    | 集合檢視型別 | 注意 |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | 內部型別依據 <xref:System.Windows.Data.CollectionView> | 無法群組項目。 |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | 最快。 |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>使用預設視圖

指定集合檢視做為繫結來源是建立和使用集合檢視的方式之一。 WPF 也會為做為繫結來源使用的每個集合建立預設集合檢視。 如果您直接繫結至集合，WPF 會繫結至它的預設檢視。 此預設視圖是由相同集合的所有系結所共用，因此，) 稍後所討論的預設視圖會變更為一個繫結控制項或程式碼 (例如排序或變更目前的專案指標，並反映在相同集合的所有其他系結中。

若要取得預設視圖，請使用 <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> 方法。 如需範例，請參閱 [取得資料集合的預設視圖](/dotnet/desktop/wpf/data/how-to-get-the-default-view-of-a-data-collection)。

#### <a name="collection-views-with-adonet-datatables"></a>使用 ADO.NET Datatable 的集合視圖

為了改善效能，ADO.NET 或物件的集合視圖 <xref:System.Data.DataTable> <xref:System.Data.DataView> 會將排序和篩選委派給，以在 <xref:System.Data.DataView> 資料來源的所有集合視圖之間共用排序和篩選。 若要讓每個收集視圖各自進行排序和篩選，請使用它自己的物件來初始化每個集合視圖 <xref:System.Data.DataView> 。

#### <a name="sorting"></a>排序

如先前所述，檢視可以將排序順序套用到集合上。 當資料存在於基礎集合中時，資料本身可能有也可能沒有相關的順序。 對集合的檢視可以讓您依據所提供的比較準則，安排順序或變更預設順序。 因為是資料的用戶端檢視，常見的案例是使用者會想要針對資料行對應的值，而排序表格式資料的資料行。 藉由使用檢視，就可以套用這個使用者驅動的排序，同樣不需要對基礎集合進行任何變更，或甚至不需要重新查詢集合內容。 如需範例，請參閱 [在按一下標頭時排序 GridView 資料行](/dotnet/desktop/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked)。

下列範例顯示「 <xref:System.Windows.Controls.CheckBox> [何謂資料](#what-is-data-binding) 系結」一節中應用程式 UI 的「依分類和日期排序」的排序邏輯。

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>篩選

Views 也可以將篩選套用至集合，讓視圖只顯示完整集合的特定子集。 您可以對資料篩選條件。 例如，當應用程式在 [ [什麼是資料](#what-is-data-binding) 系結] 區段中執行時，[僅顯示 bargains] 會 <xref:System.Windows.Controls.CheckBox> 包含用來篩選掉成本 $25 或更多之專案的邏輯。 當選取 ShowOnlyBargainsFilter 時，會執行下列程式碼，將*ShowOnlyBargainsFilter*設定為 <xref:System.Windows.Data.CollectionViewSource.Filter> 事件處理常式 <xref:System.Windows.Controls.CheckBox> 。

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

*ShowOnlyBargainsFilter*事件處理常式具有下列執行。

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

如果您直接使用其中一個 <xref:System.Windows.Data.CollectionView> 類別，而不是 <xref:System.Windows.Data.CollectionViewSource> ，則會使用 <xref:System.Windows.Data.CollectionView.Filter%2A> 屬性來指定回呼。 如需範例，請參閱[篩選檢視中的資料](/dotnet/desktop/wpf/data/how-to-filter-data-in-a-view)。

#### <a name="grouping"></a>群組

除了用來查看集合的內部類別以外 <xref:System.Collections.IEnumerable> ，所有的集合視圖都支援 *群組*，這可讓使用者將集合視圖中的集合分割成邏輯群組。 群組可以是明確的，由使用者提供群組清單，或者是隱含的，讓群組依據資料動態產生。

下列範例顯示「依類別分組」的邏輯 <xref:System.Windows.Controls.CheckBox> 。

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

如需另一個群組範例，請參閱[實作 GridView 的 ListView 中的群組項目](/dotnet/desktop/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview)。

#### <a name="current-item-pointers"></a>目前專案指標

檢視也支援目前項目的概念。 您可以在集合檢視中逐一巡覽物件。 當您巡覽時，移動項目指標可以讓您擷取集合中存在該特定位置的物件。 如需範例，請參閱 [流覽資料 CollectionView 中的物件](/dotnet/desktop/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview)。

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

目前項目指標可能會受套用至集合的任何排序或篩選所影響。 排序會將目前項目指標保留在最後選取的項目上，但現在集合檢視已在其周圍重組結構。  (可能是選取的專案之前位於清單的開頭，但現在選取的專案可能在中間的某處。如果在篩選之後，選取的專案仍維持為 [已選取]，則 ) 篩選會保留選取的專案。 否則，目前項目指標會設定在篩選集合檢視的第一個項目。

#### <a name="master-detail-binding-scenario"></a>主從階層系結案例

目前項目的概念不但對巡覽集合項目很有用，也能應用在主從式繫結案例。 請考慮 [ [什麼是資料](#what-is-data-binding) 系結] 區段中的應用程式 UI。 在該應用程式中，中的選取專案會 <xref:System.Windows.Controls.ListBox> 決定所顯示的內容 <xref:System.Windows.Controls.ContentControl> 。 若要以另一種方式加以放置，當 <xref:System.Windows.Controls.ListBox> 選取專案時，會 <xref:System.Windows.Controls.ContentControl> 顯示所選取專案的詳細資料。

您可以實作主從式案例，只要藉由讓兩或多個控制項繫結到相同檢視即可。 下列來自資料系結 [示範][data-binding-demo] 的範例會顯示的標記 <xref:System.Windows.Controls.ListBox> ，以及 <xref:System.Windows.Controls.ContentControl> 您在應用程式 UI 的 [ [什麼是資料](#what-is-data-binding) 系結] 區段中看到的標記。

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

請注意，這兩個控制項都系結至相同的來源， *>listingdataview* 靜態資源 (在 [ [如何建立視圖] 區段](#how-to-create-a-view) 中看到此資源的定義) 。 這個系結的運作方式是因為在此案例中 (的 singleton 物件) 系結 <xref:System.Windows.Controls.ContentControl> 至集合視圖時，它會自動系結至 <xref:System.Windows.Data.CollectionView.CurrentItem%2A> 視圖的。 <xref:System.Windows.Data.CollectionViewSource>物件會自動同步處理貨幣和選取專案。 如果您的清單控制項未 <xref:System.Windows.Data.CollectionViewSource> 如這個範例所示系結至物件，則您必須將其屬性設定為，才能 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> `true` 讓它運作。

如需其他範例，請參閱系結 [至集合並根據選取專案顯示資訊](/dotnet/desktop/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection) ，並 [以階層式資料使用主版詳細資料模式](/dotnet/desktop/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data)。

您可能已經注意到上述範例有使用範本。 事實上，資料不會以我們想要的方式顯示，而不使用範本 (明確使用的範本 <xref:System.Windows.Controls.ContentControl> ，以及) 隱含使用的範本 <xref:System.Windows.Controls.ListBox> 。 現在，下節中要說明資料範本化。

## <a name="data-templating"></a>製作資料範本

如果沒有使用資料範本，則 [ [資料](#what-is-data-binding) 系結] 區段中的應用程式 UI 看起來會如下所示。

![不含資料範本的資料繫結示範](./media/data-binding-overview/demo-no-template.png)

如同上一節中的範例所示， <xref:System.Windows.Controls.ListBox> 控制項和都系結 <xref:System.Windows.Controls.ContentControl> 至整個集合物件 (更明確地說，是 *>auctionitem*s) 的集合物件。 若沒有如何顯示資料集合的特定指示，會 <xref:System.Windows.Controls.ListBox> 顯示基礎集合中每個物件的字串標記法，並 <xref:System.Windows.Controls.ContentControl> 顯示其所系結之物件的字串表示。

為了解決這個問題，應用程式會定義 <xref:System.Windows.DataTemplate?text=DataTemplates> 。 如上一節中的範例所示， <xref:System.Windows.Controls.ContentControl> 明確地使用 *detailsProductListingTemplate* 資料範本。 <xref:System.Windows.Controls.ListBox>控制項在集合中顯示 *>auctionitem*物件時，會隱含地使用下列資料範本。

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

使用這兩個 DataTemplates 時，產生的 UI 就是 [ [什麼是資料](#what-is-data-binding) 系結] 區段中所顯示的 UI。 您可以從該螢幕擷取畫面看到，除了讓您將資料放在控制項中之外，DataTemplates 還可讓您為資料定義引人注目的視覺效果。 例如， <xref:System.Windows.DataTrigger> 在上述範例中，會 <xref:System.Windows.DataTemplate> 顯示具有*反白顯示* *>auctionitem*值的 *>auctionitem*，並顯示橙色框線和星號。

如需資料範本的詳細資訊，請參閱 [資料範本化總覽](/dotnet/desktop/wpf/data/data-templating-overview)。

## <a name="data-validation"></a>資料驗證

大部分採用使用者輸入的應用程式都必須有驗證邏輯，以確保使用者輸入了預期的資訊。 驗證檢查可根據類型、範圍、格式或其他應用程式特定需求。 本節討論資料驗證在 WPF 中的運作方式。

### <a name="associating-validation-rules-with-a-binding"></a>建立驗證規則與系結的關聯

WPF 資料系結模型可讓您 <xref:System.Windows.Data.Binding.ValidationRules%2A> 與物件建立關聯 <xref:System.Windows.Data.Binding> 。 例如，下列範例會將系結 <xref:System.Windows.Controls.TextBox> 至名為的屬性 `StartPrice` ，並將 <xref:System.Windows.Controls.ExceptionValidationRule> 物件加入至 <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> 屬性。

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

<xref:System.Windows.Controls.ValidationRule>物件會檢查屬性的值是否有效。 WPF 有兩種類型的內建 <xref:System.Windows.Controls.ValidationRule> 物件：

- 檢查系結 <xref:System.Windows.Controls.ExceptionValidationRule> 來源屬性更新期間所擲回的例外狀況。 在上面的範例中，`StartPrice` 的型別為整數。 當使用者輸入的值無法轉換為整數時，就會擲回例外狀況，造成繫結標記為無效。 明確設定的替代語法 <xref:System.Windows.Controls.ExceptionValidationRule> 是 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> `true` 在或物件上將屬性設為 <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.MultiBinding> 。

- <xref:System.Windows.Controls.DataErrorValidationRule>物件會檢查執行介面之物件所引發的錯誤 <xref:System.ComponentModel.IDataErrorInfo> 。 如需使用此驗證規則的範例，請參閱 <xref:System.Windows.Controls.DataErrorValidationRule> 。 明確設定的替代語法 <xref:System.Windows.Controls.DataErrorValidationRule> 是 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> `true` 在或物件上將屬性設為 <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.MultiBinding> 。

您也可以從 <xref:System.Windows.Controls.ValidationRule> 類別衍生並執行方法，以建立自己的驗證規則 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 。 下列範例會顯示 [什麼是資料系結] 區段中，[新增產品]*清單*的 [開始日期] 所使用的規則 <xref:System.Windows.Controls.TextBox> 。 [What is data binding](#what-is-data-binding)

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*StartDateEntryForm*會 <xref:System.Windows.Controls.TextBox> 使用此*FutureDateRule*，如下列範例所示。

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

因為 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值為，系結 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> 引擎會在每次擊鍵時更新來源值，這表示它也會 <xref:System.Windows.Data.Binding.ValidationRules%2A> 在每次擊鍵時檢查集合中的每個規則。 我們將在＜驗證程序＞一節進一步討論這個部分。

### <a name="providing-visual-feedback"></a>提供視覺效果意見反應

如果使用者輸入不正確值，您可能會想要在應用程式 UI 上提供關於錯誤的一些意見反應。 提供這類意見反應的其中一種方式是將 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> 附加屬性設定為自訂 <xref:System.Windows.Controls.ControlTemplate> 。 如上一節所示，StartDateEntryForm 會*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> 使用呼叫的 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> *>validationtemplate*。 下列範例顯示 *>validationtemplate*的定義。

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

<xref:System.Windows.Controls.AdornedElementPlaceholder>元素會指定要將裝飾的控制項放置在何處。

此外，您也可以使用 <xref:System.Windows.Controls.ToolTip> 來顯示錯誤訊息。 *StartDateEntryForm*和 *>startpriceentryform* <xref:System.Windows.Controls.TextBox> es 都使用 style *>textstyletextbox*，它會建立 <xref:System.Windows.Controls.ToolTip> 顯示錯誤訊息的。 下列範例顯示 *textStyleTextBox* 的定義。 附加屬性 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 是 `true` 當繫結項目的屬性上有一或多個系結髮生錯誤時。

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

使用自訂 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 和 <xref:System.Windows.Controls.ToolTip> ， *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> 當發生驗證錯誤時，StartDateEntryForm 看起來會如下所示。

![資料繫結驗證錯誤](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

如果您 <xref:System.Windows.Data.Binding> 有相關聯的驗證規則，但是未 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 在繫結控制項上指定，則會 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 使用預設值來通知使用者發生驗證錯誤。 預設值 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 是在裝飾項圖層中定義紅色框線的控制項範本。 使用預設值 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 和 <xref:System.Windows.Controls.ToolTip> *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> 時，當發生驗證錯誤時，>startpriceentryform 的 UI 看起來會如下所示。

![資料繫結驗證錯誤](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

如需如何提供邏輯來驗證對話方塊中所有控制項的範例，請參閱 [對話方塊](/dotnet/desktop/wpf/app-development/dialog-boxes-overview)中的自訂對話方塊一節。

### <a name="validation-process"></a>驗證程序

通常驗證發生的時機，是將目標的值傳輸到繫結來源屬性的時候。 此傳輸會在和系結上進行 <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> 。 再次重申，造成來源更新的原因取決於屬性的值 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> ，如「 [觸發程式來源更新](#what-triggers-source-updates) 」一節中所述。

下列專案描述 *驗證* 流程。 如果在此程式期間任何時候發生驗證錯誤或其他類型的錯誤，則會停止進程：

1. 系結引擎會檢查是否有任何定義為的自訂 <xref:System.Windows.Controls.ValidationRule> 物件 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.RawProposedValue> <xref:System.Windows.Data.Binding> ，在這種情況下，它會 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 在每個物件上呼叫方法， <xref:System.Windows.Controls.ValidationRule> 直到其中一個發生錯誤或全部都通過為止。

2. 接著，繫結引擎就會在有轉換器的情況下呼叫轉換器。

3. 如果轉換器成功，系結引擎會檢查是否有任何定義為的自訂 <xref:System.Windows.Controls.ValidationRule> 物件 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> <xref:System.Windows.Data.Binding> ，在這種情況下，它會 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 在每一個已設定為的物件上呼叫方法，直到其中 <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 一個發生 <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> 錯誤或全部通過為止。

4. 繫結引擎會設定來源屬性。

5. 系結引擎會檢查是否有任何定義為的自訂 <xref:System.Windows.Controls.ValidationRule> 物件 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Data.Binding> ，在這種情況下，它會 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 在每一個已設定為的方法上呼叫方法， <xref:System.Windows.Controls.ValidationRule> 直到其中 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 一個發生 <xref:System.Windows.Controls.ValidationStep.UpdatedValue> 錯誤或全部通過為止。 如果與系結 <xref:System.Windows.Controls.DataErrorValidationRule> 相關聯，而且其 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 設定為預設值，則 <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Controls.DataErrorValidationRule> 會在此時檢查。 此時 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> 會檢查任何設定為的系結 `true` 。

6. 系結引擎會檢查是否有任何定義為的自訂 <xref:System.Windows.Controls.ValidationRule> 物件 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.CommittedValue> <xref:System.Windows.Data.Binding> ，在這種情況下，它會 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 在每一個已設定為的方法上呼叫方法， <xref:System.Windows.Controls.ValidationRule> 直到其中 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 一個發生 <xref:System.Windows.Controls.ValidationStep.CommittedValue> 錯誤或全部通過為止。

如果 <xref:System.Windows.Controls.ValidationRule> 未在此程式中的任何時間通過，系結引擎會建立 <xref:System.Windows.Controls.ValidationError> 物件，並將它加入至 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 繫結項目的集合。 在系結引擎執行 <xref:System.Windows.Controls.ValidationRule> 任何指定步驟的物件之前，它會在 <xref:System.Windows.Controls.ValidationError> 該步驟中移除任何已加入至 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 繫結項目之附加屬性的專案。 例如，如果將 <xref:System.Windows.Controls.ValidationRule> 其 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 設為 <xref:System.Windows.Controls.ValidationStep.UpdatedValue> failed，則在下次驗證程式發生時，系結引擎會在 <xref:System.Windows.Controls.ValidationError> 呼叫任何 <xref:System.Windows.Controls.ValidationRule> 已設定為的之前，立即移除 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> 。

當不 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 是空的時， <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 元素的附加屬性會設定為 `true` 。 此外，如果的 <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> 屬性 <xref:System.Windows.Data.Binding> 設定為，則系結 `true` 引擎會 <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> 在元素上引發附加事件。

另請注意，任何方向的有效值傳輸 (目標設為目標的來源或來源) 會清除 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 附加屬性。

如果系結具有與其 <xref:System.Windows.Controls.ExceptionValidationRule> 相關聯的，或 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> 屬性設定為， `true` 而且當系結引擎設定來源時，會擲回例外狀況，系結引擎會檢查是否有 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> 。 您可以選擇使用 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> 回呼來提供處理例外狀況的自訂處理常式。 如果 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> 未在上指定，系結 <xref:System.Windows.Data.Binding> 引擎會建立具有例外狀況的， <xref:System.Windows.Controls.ValidationError> 並將它加入至 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 繫結項目的集合。

## <a name="debugging-mechanism"></a>調試機制

您可以在系結 <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> 相關物件上設定附加屬性，以接收特定系結狀態的相關資訊。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [系結至 LINQ 查詢的結果](/dotnet/desktop/wpf/data/how-to-bind-to-the-results-of-a-linq-query)
- [資料繫結](/dotnet/desktop/wpf/advanced/optimizing-performance-data-binding)
- [資料系結示範][data-binding-demo]
- [操作說明文章](/dotnet/desktop/wpf/data/data-binding-how-to-topics)
- [繫結至 ADO.NET 資料來源](/dotnet/desktop/wpf/data/how-to-bind-to-an-ado-net-data-source)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "資料系結示範應用程式"
