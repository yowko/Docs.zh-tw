---
title: "資料繫結概觀 | Microsoft Docs"
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
  - "資料繫結, 關於資料繫結"
  - "資料繫結的轉換"
  - "資料繫結, 關於資料繫結"
  - "繫結的資料轉換"
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
caps.latest.revision: 78
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 75
---
# 資料繫結概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結在資料的展示和互動上，提供應用程式簡單而一致的方式。  項目可以與來自各種資料來源的資料進行繫結，資料的型式可以是 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 物件和 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]。  <xref:System.Windows.Controls.ContentControl> \(例如 <xref:System.Windows.Controls.Button>\) 以及 <xref:System.Windows.Controls.ItemsControl> \(例如 <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.ListView>\) 具有內建的功能，可以讓單一資料項目或資料項目集合擁有彈性的樣式。  您可以依據資料產生排序、篩選和群組檢視。  
  
 相較於傳統模型，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的資料繫結功能具有數個優點，包括本身就支援資料繫結的相當多屬性、資料的彈性 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 表示，以及 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 個別的清楚商務邏輯。  
  
 本主題會先討論 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資料繫結的基本概念，然後再說明 <xref:System.Windows.Data.Binding> 類別的使用方式和資料繫結的其他功能。  
  
   
  
<a name="what_is_data_binding"></a>   
## 資料繫結是什麼  
 資料繫結是在應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 和商務邏輯間建立連接的過程。  如果繫結具有正確的設定，且資料有提供適當的告知，那麼，在資料值變更時，繫結到該資料的項目就會自動反映變更。  資料繫結也代表在項目資料的外部表示變更時，那麼基礎資料也會自動更新以反映變更。  舉例來說，當使用者編輯 <xref:System.Windows.Controls.TextBox> 項目中的值時，基礎資料值也會自動更新以反映該變更。  
  
 一個資料繫結的常見用法是將伺服器或本機組態資料，放入表單或其他 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 控制項中。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中會擴充這個概念，以包含相當多屬性對各種資料來源的繫結。  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，項目的[相依性屬性](GTMT)可以繫結到 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件 \(包括 [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] 物件或與 Web 服務和 Web 屬性關聯的物件\) 和 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料。  
  
 如需資料繫結的範例，請參考下列來自[資料繫結示範](http://go.microsoft.com/fwlink/?LinkID=163703) \(英文\) 的應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]：  
  
 ![資料繫結範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/databinding-databindingdemo.png "DataBinding\_DataBindingDemo")  
  
 上面的應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 會顯示拍賣項目的清單。  應用程式會示範下列資料繫結功能：  
  
-   <xref:System.Windows.Controls.ListBox> 的內容會繫結到 *AuctionItem* 物件的集合。  *AuctionItem* 物件具有這些屬性：*Description*、*StartPrice*、*StartDate*、*Category* 和 *SpecialFeatures* 等等。  
  
-   <xref:System.Windows.Controls.ListBox> 中顯示的資料 \(*AuctionItem* 物件\) 已套用樣板，所以會針對每個項目顯示描述和目前價格。  這是藉由使用 <xref:System.Windows.DataTemplate> 而達成的。  除此之外，每個項目的外觀取決於所顯示 *AuctionItem* 的 *SpecialFeatures* 值。  如果 *AuctionItem* 的 *SpecialFeatures* 值是 *Color*，項目就具有藍色框線。  如果值是 *Highlight*，項目就具有橘色框線和星號。  [資料樣板化](#data_templating)一節會提供資料樣板化的相關資訊。  
  
-   使用者可以使用所提供的 <xref:System.Windows.Controls.CheckBox> 來群組、篩選或排序資料。  在上圖中的 "Group by category" 和 "Sort by category and date" <xref:System.Windows.Controls.CheckBox> 是選取的。  您可能已經注意到，資料的群組化是依據產品的分類，且分類名稱是以字母順序排列。  雖然在圖中很難辨識，但項目在每個分類內也有以開始日期排序。  這是藉由使用*集合檢視*而達成的。  [繫結至集合](#binding_to_collections)一節會討論集合檢視。  
  
-   當使用者選取項目時，<xref:System.Windows.Controls.ContentControl> 會顯示選取項目的詳細資料。  這稱為*主從式案例*。  [主從式繫結案例](#master_detail_scenario)一節會提供這類型繫結案例的相關資訊。  
  
-   *StartDate* 屬性的型別是 <xref:System.DateTime>，所傳回的日期包含以毫秒顯示的時間。  這個應用程式中有使用自訂轉換子，好顯示較短的日期字串。  [資料轉換](#data_conversion)一節會提供轉換子的相關資訊。  
  
 當使用者按一下 \[*Add Product*\] 按鈕時，會出現下列表單：  
  
 ![加入產品清單頁面](../../../../docs/framework/wpf/data/media/databinding-demo-addproductlisting.png "DataBinding\_Demo\_AddProductListing")  
  
 使用者可以編輯表單中的欄位、使用簡短預覽和更為詳盡的預覽窗格來預覽產品清單，然後再按一下 \[*Submit*\] 以加入新產品清單。  任何現有的群組、篩選和排序功能會套用到新項目上。  在這種特定情形下，輸入上圖的項目會在 \[*Computer*\] 分類內顯示為第二個項目。  
  
 這個圖中沒有顯示出 *Start Date* <xref:System.Windows.Controls.TextBox> 所提供的驗證邏輯。  如果使用者輸入無效的日期 \(無效的格式或過去的日期\)，就會以 <xref:System.Windows.Controls.ToolTip> 告知使用者，且 <xref:System.Windows.Controls.TextBox> 旁邊會有紅色驚嘆號。  [資料驗證](#data_validation)一節會討論如何建立驗證邏輯。  
  
 在進入上面概要說明的各種功能之前，下節中我們會先討論對於了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資料繫結很重要的基本概念。  
  
<a name="basic_data_binding_concepts"></a>   
## 基本資料繫結概念  
   
  
 不管您的繫結項目是什麼，也不論資料來源的本質，每個繫結一定會遵循下圖所說明的模型：  
  
 ![基本資料繫結圖表](../../../../docs/framework/wpf/data/media/databindingmostbasic.png "DataBindingMostBasic")  
  
 如上圖所說明，資料繫結基本上是[繫結目標](GTMT)和[繫結來源](GTMT)間的橋樑。  該圖示範下列基本 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資料繫結概念：  
  
-   一般而言，每個繫結都具有這四個元件：[繫結目標](GTMT)物件、目標屬性、[繫結來源](GTMT)，以及要使用[繫結來源](GTMT)值的路徑。  舉例來說，如果要將 <xref:System.Windows.Controls.TextBox> 的內容繫結到 *Employee* 物件的 *Name* 屬性，則目標物件是 <xref:System.Windows.Controls.TextBox>、目標屬性是 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性，要使用的值是 *Name*，而來源物件是 *Employee* 物件。  
  
-   目標屬性必須是[相依性屬性](GTMT)。  大部分的 <xref:System.Windows.UIElement> 屬性是[相依性屬性](GTMT)，而大部分的[相依性屬性](GTMT)預設都支援資料繫結，除了唯讀的屬性外   \(只有 <xref:System.Windows.DependencyObject> 型別可以定義[相依性屬性](GTMT)，且所有的 <xref:System.Windows.UIElement> 衍生自 <xref:System.Windows.DependencyObject>\)。  
  
-   雖然圖中未指出，但應該注意的是，[繫結來源](GTMT)物件不限於自訂的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資料繫結支援 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件和 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 格式的資料。  若需要一些範例，您的繫結來源可以是 <xref:System.Windows.UIElement>、任何清單物件、與 [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] 資料或 Web 服務關聯的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件，或者是包含 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料的 XmlNode。  如需詳細資訊，請參閱 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)。  
  
 當您閱讀其他[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] 主題時有一點很重要，請記住在建立繫結時，是將[繫結目標](GTMT)*繫結到*[繫結來源](GTMT)。  舉例來說，如果您使用資料繫結在 <xref:System.Windows.Controls.ListBox> 中顯示一些基本 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料，則是將 <xref:System.Windows.Controls.ListBox> 繫結到 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料。  
  
 若要建立繫結，您要使用 <xref:System.Windows.Data.Binding> 物件。  本主題的其餘部分會討論與 <xref:System.Windows.Data.Binding> 物件關聯的許多概念，並討論一些該物件的屬性和使用方式。  
  
<a name="direction_of_data_flow"></a>   
### 資料流程的方向  
 如先前所述，並如上圖中箭頭所指出，繫結的資料流程是從[繫結目標](GTMT)走向[繫結來源](GTMT) \(舉例來說，在使用者編輯 <xref:System.Windows.Controls.TextBox> 的值時來源值會變更\)，以及\/或者在繫結來源有提供適當告知時，是從[繫結來源](GTMT)走向[繫結目標](GTMT) \(舉例來說，<xref:System.Windows.Controls.TextBox> 內容會隨著[繫結來源](GTMT)變更而更新\)。  
  
 您可能會想讓應用程式使用者變更資料，並將變更散佈回來源物件。  或者您可能不希望使用者更新來源資料。  藉由設定 <xref:System.Windows.Data.Binding> 物件的 <xref:System.Windows.Data.Binding.Mode%2A> 屬性，即可以控制這個情況。  下圖說明不同類型的資料流程：  
  
 ![資料繫結資料流程](../../../../docs/framework/wpf/data/media/databinding-dataflow.png "DataBinding\_DataFlow")  
  
-   <xref:System.Windows.Data.BindingMode> 繫結會讓來源屬性的變更自動更新到目標屬性，但目標屬性的變更不會散佈回來源屬性。  這類型的繫結適用於所繫結控制項是隱含唯讀的。  例如，您可能繫結到股票行情即時看板這類的來源，或者沒有提供目標屬性可以進行變更的控制項介面，例如資料表的資料繫結背景色彩。  如果沒有需要監視目標屬性的變更，則使用 <xref:System.Windows.Data.BindingMode> 繫結模式可以避免 <xref:System.Windows.Data.BindingMode> 繫結模式所帶來的負荷。  
  
-   <xref:System.Windows.Data.BindingMode> 繫結會讓來源屬性或目標屬性的變更，自動更新另外一個。  這類型的繫結適用於可編輯表單或其他完全互動式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例。  大部分的屬性預設是 <xref:System.Windows.Data.BindingMode> 繫結，但有些[相依性屬性](GTMT) \(通常是使用者可編輯的控制項屬性，例如 <xref:System.Windows.Controls.TextBox> 的 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性和 <xref:System.Windows.Controls.CheckBox> 的 <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 屬性\) 則預設為 <xref:System.Windows.Data.BindingMode> 繫結。  一種用來判斷[相依性屬性](GTMT)預設為單向或雙向繫結的程式設計方式是使用 <xref:System.Windows.DependencyProperty.GetMetadata%2A> 取得屬性的屬性中繼資料，然後再檢查 <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> 屬性的 Boolean 值。  
  
-   <xref:System.Windows.Data.BindingMode> 是 <xref:System.Windows.Data.BindingMode> 繫結的反向，會在目標屬性變更時更新來源屬性。  有一個範例案例是當您只需要從 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 重新評估來源值時。  
  
-   圖中沒有說明的 <xref:System.Windows.Data.BindingMode> 繫結，會讓來源屬性初始化目標屬性，但後續的變更並不會散佈。  這代表如果資料內容發生變更或資料內容中的物件有變更，則變更不會反映在目標屬性中。  這類型的繫結適用於在您所使用的資料，其目前狀態的快照適合使用，或者是資料是非常靜態的。  當您想要使用來源屬性的某個值初始化目標屬性時，而事前不知道到資料內容時，這類型的繫結也非常有用。  基本上這是 <xref:System.Windows.Data.BindingMode> 繫結的簡單形式，而這在來源值沒有變更的情況下可以提供更好的效能。  
  
 請注意，若要偵測來源變更 \(適用於 <xref:System.Windows.Data.BindingMode> 和 <xref:System.Windows.Data.BindingMode> 繫結\)，來源必須實作適當的屬性變更告知機制，例如 <xref:System.ComponentModel.INotifyPropertyChanged>。  請參閱 [實作屬性變更通知](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)，以取得 <xref:System.ComponentModel.INotifyPropertyChanged> 實作的範例。  
  
 <xref:System.Windows.Data.Binding.Mode%2A> 屬性頁提供您繫結模式的詳細資訊，以及如何指定繫結方向的範例。  
  
<a name="what_triggers_source_updates"></a>   
### 觸發來源更新的機制  
 <xref:System.Windows.Data.BindingMode> 或 <xref:System.Windows.Data.BindingMode> 繫結會接聽目標屬性的變更，並散佈回來源。  這種情況稱為更新來源。  舉例來說，您可以編輯 TextBox 的文字以變更基礎來源值。  如前一節所述，資料流程的方向是由繫結的 <xref:System.Windows.Data.Binding.Mode%2A> 屬性值所決定的。  
  
 然而，當您編輯文字時，或者是在完成文字編輯且將滑鼠指標帶離 TextBox 後，來源值是否有更新？  繫結的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性會決定觸發來源更新的機制。  下圖中右箭頭的點說明 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性的角色：  
  
 ![UpdateSourceTrigger 圖表](../../../../docs/framework/wpf/data/media/databindingupdatesourcetrigger.png "DataBindingUpdateSourceTrigger")  
  
 如果 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值是 <xref:System.Windows.Data.UpdateSourceTrigger>，則 <xref:System.Windows.Data.BindingMode> 或 <xref:System.Windows.Data.BindingMode> 繫結的右箭頭所指向的值，就會在目標屬性變更時立即更新。  然而，如果 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值是 <xref:System.Windows.Data.UpdateSourceTrigger>，則該值只會在目標屬性失去焦點時更新成新值。  
  
 跟 <xref:System.Windows.Data.Binding.Mode%2A> 屬性類似，不同的[相依性屬性](GTMT)具有不同的預設 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值。  大部分[相依性屬性](GTMT)的預設值是 <xref:System.Windows.Data.UpdateSourceTrigger>，而 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性的預設值為 <xref:System.Windows.Data.UpdateSourceTrigger>。  這代表在目標屬性變更時通常會發生來源更新，這對 <xref:System.Windows.Controls.CheckBox> 和其他簡單控制項而言是可以的。  然而，對於文字欄位而言，在每個按鍵動作後進行更新會降低效能，並且會拒絕給使用者慣有的機會，在交付新值前按退格鍵和修正輸入錯誤。  這就是 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性預設值為 <xref:System.Windows.Data.UpdateSourceTrigger> 而非 <xref:System.Windows.Data.UpdateSourceTrigger> 的原因。  
  
 如需如何找出[相依性屬性](GTMT)的預設 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值的詳細資訊，請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性頁。  
  
 下表使用 <xref:System.Windows.Controls.TextBox> 為範例，提供對於每個 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值的範例案例：  
  
|UpdateSourceTrigger 值|來源值更新時機|TextBox 的範例案例|  
|---------------------------|-------------|-------------------|  
|LostFocus \(<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> 的預設設定\)|TextBox 控制項失去焦點時|與驗證邏輯關聯的 <xref:System.Windows.Controls.TextBox> \(請參閱＜資料驗證＞一節\)|  
|PropertyChanged|當您在 <xref:System.Windows.Controls.TextBox> 中輸入時|聊天室視窗中的 <xref:System.Windows.Controls.TextBox> 控制項|  
|Explicit|應用程式呼叫 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> 時|可編輯表單中的 <xref:System.Windows.Controls.TextBox> 控制項 \(只有在使用者按一下送出按鈕時才會更新來源值\)|  
  
 如需範例，請參閱 [TextBox 文字更新來源時控制](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)。  
  
<a name="creating_a_binding"></a>   
## 建立繫結  
   
  
 若要重現上面幾節所討論的一些概念，您可以使用 <xref:System.Windows.Data.Binding> 物件建立繫結，且每個繫結通常要有四個元件：繫結目標、目標屬性、繫結來源，以及要使用的來源值路徑。  本節討論如何設定繫結。  
  
 請考慮下列範例，其中的繫結來源物件是名為 *MyData* 的類別，定義於 *SDKSample* 命名空間中。  為了便於示範，*MyData* 類別的字串屬性名為 *ColorName*，其值設為 "Red"。  因此，本範例會產生具有紅色背景的按鈕。  
  
 [!code-xml[BindNonTextProperty#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 如需繫結宣告語法的詳細資訊，以及如何在程式碼中設定繫結的範例，請參閱[繫結宣告概觀](../../../../docs/framework/wpf/data/binding-declarations-overview.md)。  
  
 如果將這個範例套用到我們的基本圖表，結果會類似下圖。  這是 <xref:System.Windows.Data.BindingMode> 繫結，因為 Background 屬性預設支援 <xref:System.Windows.Data.BindingMode> 繫結。  
  
 ![資料繫結圖表](../../../../docs/framework/wpf/data/media/databindingbuttonbackgroundexample.png "DataBindingButtonBackgroundExample")  
  
 您可能會覺得很奇怪，為什麼即使 *ColorName* 屬性的型別是字串，而 <xref:System.Windows.Controls.Control.Background%2A> 屬性型別是 <xref:System.Windows.Media.Brush>，卻仍可以運作。  這是因為預設型別轉換的作用，在[資料轉換](#data_conversion)一節中會討論到。  
  
<a name="specifying_the_binding_source"></a>   
### 指定繫結來源  
 請注意，前述範例中的繫結來源指定，是藉由設定 <xref:System.Windows.Controls.DockPanel> 項目的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性。  <xref:System.Windows.Controls.Button> 會接著繼承其父項目 <xref:System.Windows.Controls.DockPanel> 的 <xref:System.Windows.FrameworkElement.DataContext%2A> 值。  再重複聲明一次，繫結來源物件是繫結的四個必要元件之一。  因此，沒有指定繫結來源物件，就無法進行繫結。  
  
 有數種方式可以指定繫結來源物件。  當您要將多個屬性繫結到相同來源時，在父項目上使用 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性就很好用。  然而，有時候在個別的繫結宣告上指定繫結來源可能比較恰當。  針對前述範例，您可以不要使用 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性，而改為在按鈕的繫結宣告上直接設定 <xref:System.Windows.Data.Binding.Source%2A> 屬性來指定繫結來源，如下列範例所示：  
  
 [!code-xml[BindNonTextProperty#BackgroundBindingCompact](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 除了直接在項目上設定 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性、從祖系繼承 <xref:System.Windows.FrameworkElement.DataContext%2A> 值 \(例如第一個範例的按鈕\)，以及藉由在 <xref:System.Windows.Data.Binding> 上設定 <xref:System.Windows.Data.Binding.Source%2A> 屬性來明確指定繫結來源 \(例如前一範例的按鈕\) 外，您也可以使用 <xref:System.Windows.Data.Binding.ElementName%2A> 屬性或 <xref:System.Windows.Data.Binding.RelativeSource%2A> 屬性以指定繫結來源。  當您要繫結到應用程式中的其他項目時，例如使用滑桿調整按鈕寬度時，<xref:System.Windows.Data.Binding.ElementName%2A> 屬性是很好用的。  當在 <xref:System.Windows.Controls.ControlTemplate> 或 <xref:System.Windows.Style> 中指定繫結時，<xref:System.Windows.Data.Binding.RelativeSource%2A> 屬性就很好用。  如需詳細資訊，請參閱 [指定繫結來源](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)。  
  
<a name="specifying_the_path_to_the_value"></a>   
### 指定值的路徑  
 如果繫結來源是物件，則要使用 <xref:System.Windows.Data.Binding.Path%2A> 屬性指定繫結要使用的值。  如果是要繫結到 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料，則要使用 <xref:System.Windows.Data.Binding.XPath%2A> 屬性指定值。  在某些情況下，即使資料是 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]，可能也適合使用 <xref:System.Windows.Data.Binding.Path%2A> 屬性。  舉例來說，在您想要存取所傳回 XmlNode \(為 XPath 查詢的結果\) 的 Name 屬性時，則除了 <xref:System.Windows.Data.Binding.XPath%2A> 屬性之外，還應該使用 <xref:System.Windows.Data.Binding.Path%2A> 屬性。  
  
 如需相關語法資訊和範例，請參閱 <xref:System.Windows.Data.Binding.Path%2A> 和 <xref:System.Windows.Data.Binding.XPath%2A> 屬性頁。  
  
 請注意，雖然這裡強調要使用值的 <xref:System.Windows.Data.Binding.Path%2A> 是繫結的四個必要元件之一，但在要繫結整個物件的案例中，要使用的值應該與[繫結來源](GTMT)物件相同。  在這些情況下，最好不要指定 <xref:System.Windows.Data.Binding.Path%2A>。  參考下列範例：  
  
 [!code-xml[MasterDetail#EmptyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 上述範例使用空白繫結語法 {Binding}。  在這個情況下，<xref:System.Windows.Controls.ListBox> 會從父 DockPanel 項目繼承 DataContext \(未在此範例中顯示\)。  沒有指定路徑時，預設會繫結到整個物件。  換句話說，本範例中的路徑保留空白，是因為要將 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性繫結到整個物件   \(如需深入討論，請參閱[繫結至集合](#binding_to_collections)一節\)。  
  
 除了繫結到集合之外，當您要繫結到整個物件而非只是物件的單一屬性時，這個案例也很好用。  舉例來說，如果來源物件的型別是字串，而您只是要繫結到字串本身時。  另一個常用案例是當您要將項目繫結到具有許多屬性的物件時。  
  
 請注意，您可能必須套用自訂邏輯，如此資料對於繫結目標屬性來說才有意義。  自訂邏輯的型式可以是自訂轉換子 \(如果沒有預設型別轉換的話\)。  如需轉換子的詳細資訊，請參閱[資料轉換](#data_conversion)一節。  
  
<a name="binding_bindingexpression"></a>   
### 繫結和 BindingExpression  
 進入資料繫結的其他功能和使用方式之前，先介紹 <xref:System.Windows.Data.BindingExpression> 類別會很有用。  如您在前述小節所見，<xref:System.Windows.Data.Binding> 類別是繫結宣告的高階類別。<xref:System.Windows.Data.Binding> 類別提供許多屬性，可以讓您指定繫結的特性。  而相關的類別 <xref:System.Windows.Data.BindingExpression>，是用於維持來源和目標間連接的基礎物件。  繫結包含可以跨數種繫結運算式共用的所有資訊。  <xref:System.Windows.Data.BindingExpression> 是無法共用的執行個體運算式，並包含 <xref:System.Windows.Data.Binding> 的所有執行個體資訊。  
  
 舉例來說，請考慮這個情形，當 *myDataObject* 是 *MyData* 類別的執行個體，*myBinding* 是來源 <xref:System.Windows.Data.Binding> 物件，而 *MyData* 類別是包含名為 *MyDataProperty* 的字串屬性的定義類別。  本範例會將 <xref:System.Windows.Controls.TextBlock> 的執行個體 *mytext* 的文字內容繫結到 *MyDataProperty*。  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 您可以使用相同的 *myBinding* 物件建立其他繫結。  舉例來說，您可以使用 *myBinding* 物件將核取方塊的文字內容繫結到 *MyDataProperty*。  在這樣的案例中，會有兩個 <xref:System.Windows.Data.BindingExpression> 執行個體共用 *myBinding* 物件。  
  
 <xref:System.Windows.Data.BindingExpression> 物件可以透過在資料繫結物件上呼叫 <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> 的傳回值而取得。  下列主題示範 <xref:System.Windows.Data.BindingExpression> 類別的部分使用方式：  
  
-   [從繫結的目標屬性取得繫結物件](../../../../docs/framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
-   [TextBox 文字更新來源時控制](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## 資料轉換  
 在前述範例中的按鈕是紅色的，這是因為其 <xref:System.Windows.Controls.Control.Background%2A> 屬性是繫結到具有值 "Red" 的字串屬性。  因為在 <xref:System.Windows.Media.Brush> 型別上有型別轉換子存在，可以將字串值轉換為 <xref:System.Windows.Media.Brush>，所以才能這樣運作。  
  
 若要將這項資訊加入到[建立繫結](#creating_a_binding)一節的圖中，則圖表看起來如下：  
  
 ![資料繫結圖表](../../../../docs/framework/wpf/data/media/databindingbuttondefaultconversion.png "DataBindingButtonDefaultConversion")  
  
 然而，如果繫結來源物件具有的不是型別字串屬性，而是型別 <xref:System.Windows.Media.Color> 的 *Color* 屬性，那會如何？  在該情況下，為了讓繫結有作用，您需要先將 *Color* 屬性值改為 <xref:System.Windows.Controls.Control.Background%2A> 屬性能夠接受的某個值。  您會需要藉由實作 <xref:System.Windows.Data.IValueConverter> 介面來建立自訂轉換子，如下列範例所示：  
  
 [!code-csharp[ColorPicker_snip#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 <xref:System.Windows.Data.IValueConverter> 參考頁會提供詳細資訊。  
  
 現在是使用自訂轉換子來代替預設轉換，且圖表看起來如下：  
  
 ![資料繫結圖表](../../../../docs/framework/wpf/data/media/databindingconvertercolorexample.png "DataBindingConverterColorExample")  
  
 再重複聲明一次，預設轉換也可以使用，因為要繫結的型別中存在有型別轉換子。  這個行為會取決於目標中提供的型別轉換子。  如果有疑問，請建立自己的轉換子。  
  
 下列是部分適合實作資料轉換子的常見案例：  
  
-   依據文化特性的不同，您的資料顯示方式會有所不同。  例如，依據特定文化特性所使用的值或標準，您可能會想要實作貨幣轉換子或日曆日期\/時間轉換子。  
  
-   要使用的資料不見得是要變更屬性的文字值，但有可能是改為變更某些其他值，例如影像的來源，或者是顯示文字的色彩或樣式。  在這個情況下可能的轉換子使用方式，是藉由將看起來不太適合的屬性繫結加以轉換，例如將文字欄位繫結到表格儲存格的 Background 屬性。  
  
-   一個以上的控制項或者是控制項的多個屬性，會繫結到相同資料。  在這個情況下，主要繫結可能只是顯示文字，而其他繫結會處理特定顯示問題，但仍然使用相同的繫結做為來源資訊。  
  
-   目前我們尚未討論到 <xref:System.Windows.Data.MultiBinding>，其中的目標屬性具有繫結集合。  在 <xref:System.Windows.Data.MultiBinding> 的情況中，您使用自訂 <xref:System.Windows.Data.IMultiValueConverter> 從繫結值產生最後的值。  舉例來說，顏色可以由紅藍綠的值計算而來，而這些值可以來自相同或不同的繫結來源物件。  如需範例和詳細資訊，請參閱 <xref:System.Windows.Data.MultiBinding> 類別頁。  
  
<a name="binding_to_collections"></a>   
## 繫結至集合  
   
  
 繫結來源物件可以視為其屬性包含資料的單一物件，或是通常會群組在一起的多型物件的資料集合 \(例如資料庫查詢的結果\)。  目前為止，我們只討論到單一物件的繫結，然而，繫結到資料集合是常見的案例。  舉例來說，有個常見案例是使用 <xref:System.Windows.Controls.ItemsControl> \(例如 <xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.ListView> 或 <xref:System.Windows.Controls.TreeView>\) 顯示資料集合，例如[資料繫結是什麼](#what_is_data_binding)一節中的應用程式。  
  
 所幸，我們的基本圖表仍然適用。  如果是將 <xref:System.Windows.Controls.ItemsControl> 繫結到集合，圖表看起來如下：  
  
 ![資料繫結 ItemsControl 圖表](../../../../docs/framework/wpf/data/media/databindingitemscontrol.png "DataBindingItemsControl")  
  
 如圖表所示，為了將 <xref:System.Windows.Controls.ItemsControl> 繫結到集合物件，則要使用 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性。  您可以將 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性想像成 <xref:System.Windows.Controls.ItemsControl> 的內容。  請注意，繫結是 <xref:System.Windows.Data.BindingMode>，因為 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性預設支援 <xref:System.Windows.Data.BindingMode> 繫結。  
  
<a name="how_to_implement_collections"></a>   
### 如何實作集合  
 您可以列舉實作 <xref:System.Collections.IEnumerable> 介面的任何物件。  不過，若要設定動態繫結，讓集合中的插入或刪除作業自動更新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，則集合必須實作 <xref:System.Collections.Specialized.INotifyCollectionChanged> 介面。  這個介面所公開的事件，應該在基礎集合變更時引發。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了 <xref:System.Collections.ObjectModel.ObservableCollection%601> 類別，這個類別是公開 <xref:System.Collections.Specialized.INotifyCollectionChanged> 介面之資料集合的內建實作。  請注意，對於從來源物件到目標的傳輸資料值的完全支援，集合中支援可繫結屬性的每個物件，也都必須實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。  如需詳細資訊，請參閱 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)。  
  
 實作您自己的集合之前，請考慮使用 <xref:System.Collections.ObjectModel.ObservableCollection%601> 或其中一個現有的集合類別，例如 <xref:System.Collections.Generic.List%601>、<xref:System.Collections.ObjectModel.Collection%601>、<xref:System.ComponentModel.BindingList%601> 等等。  如果您擁有進階案例，而想實作自己的集合，請考慮使用 <xref:System.Collections.IList>，提供可依索引個別存取，也因而產生最佳效能之物件的非泛型集合。  
  
<a name="collection_views"></a>   
### 集合檢視  
 一旦 <xref:System.Windows.Controls.ItemsControl> 繫結到資料集合，您可能會想要排序、篩選或群組資料。  若要這樣做，您可以使用集合檢視，這是實作 <xref:System.ComponentModel.ICollectionView> 介面的類別。  
  
   
  
<a name="what_are_collection_views"></a>   
#### 集合檢視是什麼  
 集合檢視是以繫結來源集合為基礎的一層，可以讓您依據排序、篩選和群組查詢來巡覽和顯示來源集合，而不需要變更基礎來源集合本身。  集合檢視也會保留集合中目前項目的指標。  如果來源集合實作 <xref:System.Collections.Specialized.INotifyCollectionChanged> 介面，則由 <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> 事件所引發的變更會散佈到檢視中。  
  
 因為檢視不會變更基礎來源集合，每個來源集合可以有多個相關聯的檢視。  舉例來說，您可以有一個 *Task* 物件集合。  隨著檢視的使用，您可以不同方式顯示相同資料。  舉例來說，在頁面左方您可以顯示以優先順序排序的工作，而在右方則以區域群組方式列出。  
  
<a name="how_to_create_a_view"></a>   
#### 如何建立檢視  
 一個建立和使用檢視的方式，是直接具現化檢視物件，然後再用來做為繫結來源。  例如，請參閱[資料繫結示範](http://go.microsoft.com/fwlink/?LinkID=163703) \(英文\) 應用程式，如[資料繫結是什麼](#what_is_data_binding)一節中所示。  該應用程式的實作讓 <xref:System.Windows.Controls.ListBox> 繫結至資料集合的檢視，而非直接繫結到資料集合。  下列範例擷取自[資料繫結示範](http://go.microsoft.com/fwlink/?LinkID=163703) \(英文\) 應用程式。  <xref:System.Windows.Data.CollectionViewSource> 類別是繼承自 <xref:System.Windows.Data.CollectionView> 之類別的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Proxy。  在這個特別的範例中，檢視的 <xref:System.Windows.Data.CollectionViewSource.Source%2A> 是繫結到目前應用程式物件的 *AuctionItems* 集合 \(型別 <xref:System.Collections.ObjectModel.ObservableCollection%601>\)。  
  
 [!code-xml[DataBindingLab#WindowResources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xml[DataBindingLab#CollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xml[DataBindingLab#WindowResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 資源 *listingDataView* 接著會做為應用程式中項目的繫結來源，例如 <xref:System.Windows.Controls.ListBox>：  
  
 [!code-xml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 若要建立相同集合的另一個檢視，您可以建立另一個 <xref:System.Windows.Data.CollectionViewSource> 執行個體，並給它不同的 `x:Key` 名稱。  
  
 下表顯示哪些檢視資料型別會建立為預設集合檢視，或是由 <xref:System.Windows.Data.CollectionViewSource> 根據來源集合型別建立。  
  
|來源集合型別|集合檢視型別|備註|  
|------------|------------|--------|  
|<xref:System.Collections.IEnumerable>|以 <xref:System.Windows.Data.CollectionView> 為基礎的內部型別|無法群組項目。|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|最快。|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### 使用預設檢視  
 指定集合檢視做為繫結來源是建立和使用集合檢視的方式之一。  WPF 也會為做為繫結來源使用的每個集合建立預設集合檢視。  如果您直接繫結至集合，WPF 會繫結至它的預設檢視。  請注意，此預設檢視是由相同集合的所有繫結所共用，因此若其中一個繫結控制項或程式碼 \(例如排序或變更目前的項目指標，這會在稍後討論\) 變更預設檢視，此變更會反映在相同集合的所有其他繫結中。  
  
 若要取得預設檢視，您可以使用 <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> 方法。  如需範例，請參閱 [取得資料集合的預設檢視](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)。  
  
##### 包含 ADO.NET DataTables 的集合檢視  
 為了改善效能，ADO.NET <xref:System.Data.DataTable> 或 <xref:System.Data.DataView> 物件的集合檢視會將排序和篩選委派給 <xref:System.Data.DataView>。  這會使得資料來源的所有集合檢視共用排序和篩選。  若要讓每個集合檢視能夠獨立排序和篩選，請用它自己的 <xref:System.Data.DataView> 物件初始化每個集合檢視。  
  
<a name="sorting"></a>   
#### 排序  
 如先前所述，檢視可以將排序順序套用到集合上。  當資料存在於基礎集合中時，資料本身可能有也可能沒有相關的順序。  對集合的檢視可以讓您依據所提供的比較準則，安排順序或變更預設順序。  因為是資料的用戶端檢視，常見的案例是使用者會想要針對資料行對應的值，而排序表格式資料的資料行。  藉由使用檢視，就可以套用這個使用者驅動的排序，同樣不需要對基礎集合進行任何變更，或甚至不需要重新查詢集合內容。  如需範例，請參閱 [在按一下行首時排序 GridView 資料行](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)。  
  
 下列範例顯示[資料繫結是什麼](#what_is_data_binding)一節中應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 "Sort by category and date" <xref:System.Windows.Controls.CheckBox> 的排序邏輯：  
  
 [!code-csharp[DataBindingLab#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
<a name="filtering"></a>   
#### 篩選  
 檢視也可以對集合套用篩選。  這代表雖然項目是存在於集合中的，這個特別的檢視可以只顯示完整集合的部分子集。  您可以對資料篩選條件。  舉例來說，就像[資料繫結是什麼](#what_is_data_binding)一節中的應用程式所進行的，"Show only bargains" <xref:System.Windows.Controls.CheckBox> 包含的邏輯會篩選出成本為 $25 以上的項目。  下列程式碼的執行會在選取該 <xref:System.Windows.Controls.CheckBox> 時，將 *ShowOnlyBargainsFilter* 設定為 <xref:System.Windows.Data.CollectionViewSource.Filter> 事件處理常式：  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* 事件處理常式實作如下：  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 如果是直接使用其中一個 <xref:System.Windows.Data.CollectionView> 類別，而非 <xref:System.Windows.Data.CollectionViewSource>，則應該使用 <xref:System.Windows.Data.CollectionView.Filter%2A> 屬性指定回呼。  如需範例，請參閱 [篩選檢視中的資料](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)。  
  
<a name="grouping"></a>   
#### 群組  
 除了檢視 <xref:System.Collections.IEnumerable> 集合的內部類別外，所有集合檢視都支援群組的功能，讓使用者可以將集合檢視中的集合分割成數個邏輯群組。  群組可以是明確的，由使用者提供群組清單，或者是隱含的，讓群組依據資料動態產生。  
  
 下列範例顯示 "Group by category" <xref:System.Windows.Controls.CheckBox> 的邏輯：  
  
 [!code-csharp[DataBindingLab#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 如需另一個群組範例，請參閱 [實作 GridView 之 ListView 中的群組項目](../../../../docs/framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md)。  
  
<a name="current_record_pointers"></a>   
#### 目前項目指標  
 檢視也支援目前項目的概念。  您可以在集合檢視中逐一巡覽物件。  當您巡覽時，移動項目指標可以讓您擷取集合中存在該特定位置上的物件。  如需範例，請參閱 [透過資料 CollectionView 中的物件巡覽](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md)。  
  
 由於 WPF 只使用檢視 \(可能是您指定的檢視或集合的預設檢視\) 繫結至集合，因此集合的所有繫結都有目前項目指標。  當繫結至檢視時，`Path` 值中的斜線 \("\/"\) 字元會指定檢視的目前項目。  在下列範例中，資料內容是集合檢視。  第一行繫結至集合。  第二行繫結至集合中的目前項目。  第三行繫結至集合中目前項目的 `Description` 屬性。  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 斜線和屬性語法也可以堆疊來周遊集合的階層架構。  下列範例繫結至名為 `Offices` 之集合的目前項目，此集合是來源集合目前項目的屬性。  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 目前項目指標可能會受套用至集合的任何排序或篩選所影響。  排序會將目前項目指標保留在最後選取的項目上，但現在集合檢視已在其周圍重組結構   \(或許選取的項目先前是在清單的開頭，但現在選取的項目可能是在中間的某處\)。 如果該選取內容在篩選之後仍然在檢視範圍中，篩選就會保留選取的項目。  否則，目前項目指標會設定在篩選集合檢視的第一個項目。  
  
<a name="master_detail_scenario"></a>   
#### 主從式繫結案例  
 目前項目的概念不但對巡覽集合項目很有用，對於主從式繫結案例也很好用。  請再回想[資料繫結是什麼](#what_is_data_binding)一節中的應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  在該應用程式中，<xref:System.Windows.Controls.ListBox> 內的選取項目會決定 <xref:System.Windows.Controls.ContentControl> 中顯示的內容。  若要以其他方式放置，在 <xref:System.Windows.Controls.ListBox> 項目選取時，<xref:System.Windows.Controls.ContentControl> 會顯示選取項目的詳細資料。  
  
 您可以實作主從式案例，只要藉由讓兩或多個控制項繫結到相同檢視即可。  下列範例來自[資料繫結示範](http://go.microsoft.com/fwlink/?LinkID=163703) \(英文\)，其中顯示您在[資料繫結是什麼](#what_is_data_binding)一節中的應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 上看見的 <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.ContentControl> 的標記：  
  
 [!code-xml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xml[DataBindingLab#Detail](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 請注意，這兩個控制項都繫結到相同來源：*listingDataView* 靜態資源 \(請參閱[如何建立檢視](#how_to_create_a_view)一節中這個資源的定義\)。  因為在單一物件 \(這個情況中的 <xref:System.Windows.Controls.ContentControl>\) 繫結到集合檢視時，會自動繫結到檢視的 <xref:System.Windows.Data.CollectionView.CurrentItem%2A>，所以才能這樣運作。  請注意，<xref:System.Windows.Data.CollectionViewSource> 物件會自動同步化貨幣和選取項目。  如果您的清單控制項不是如本範例一樣繫結到 <xref:System.Windows.Data.CollectionViewSource> 物件，那麼應該要將其 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> 屬性設定為 `true`，這樣才能運作。  
  
 如需其他範例，請參閱 [繫結至集合並根據選取項目顯示資訊](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)和 [使用含階層式資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。  
  
 您可能已經注意到上述範例有使用樣板。  事實上，如果沒有使用樣板，資料的顯示不會如我們所預期 \(<xref:System.Windows.Controls.ContentControl> 所明確使用的樣板，以及 <xref:System.Windows.Controls.ListBox> 所隱含使用的樣板\)。  現在，下節中要說明資料樣板化。  
  
<a name="data_templating"></a>   
## 資料樣板化  
 沒有使用資料樣板的話，[資料繫結是什麼](#what_is_data_binding)一節中的應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 看起來會類似下圖：  
  
 ![不含資料範本的資料繫結示範](../../../../docs/framework/wpf/data/media/databindingdemotemplates.png "DataBindingDemoTemplates")  
  
 如上一節中的範例所示，<xref:System.Windows.Controls.ListBox> 控制項和 <xref:System.Windows.Controls.ContentControl> 都繫結至 *AuctionItem* 的整個集合物件 \(更具體來說，是集合物件的整體檢視\)。  如果沒有如何顯示資料集合的特定指示，<xref:System.Windows.Controls.ListBox> 會顯示基礎集合中每一個物件的字串表示，而 <xref:System.Windows.Controls.ContentControl> 會顯示所繫結之物件的字串表示。  
  
 為了解決該問題，應用程式會定義 <xref:System.Windows.DataTemplate>。  如上一節中的範例所示，<xref:System.Windows.Controls.ContentControl> 會明確使用 *detailsProductListingTemplate* <xref:System.Windows.DataTemplate>。  在顯示集合中 *AuctionItem* 物件時，<xref:System.Windows.Controls.ListBox> 控制項會隱含使用下列 <xref:System.Windows.DataTemplate>：  
  
 [!code-xml[DataBindingLab#AuctionItemDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 在有使用這兩個 <xref:System.Windows.DataTemplate> 的情況下，結果 UI 就是[資料繫結是什麼](#what_is_data_binding)一節中所顯示的 UI。  如同您在快照中所見，除了讓您將資料放置在控制項中外，<xref:System.Windows.DataTemplate> 也可以讓您為資料定義引人注目的視覺效果。  舉例來說，上述 <xref:System.Windows.DataTemplate> 中使用的 <xref:System.Windows.DataTrigger>，讓具有 *HighLight* 為 *SpecialFeatures* 值的 *AuctionItem* 會使用橘色框線和星號來顯示。  
  
 如需資料樣板的詳細資訊，請參閱[資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)。  
  
<a name="data_validation"></a>   
## 資料驗證  
   
  
 大部分會採用使用者輸入的應用程式都需要驗證邏輯，以確保使用者輸入的是預期的資訊。  驗證會依據類型、範圍、格式或其他應用程式特定的需求而進行檢查。  本節討論 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的資料驗證運作方式。  
  
<a name="validation_rules"></a>   
### 建立驗證規則與繫結的關聯  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資料繫結模型可以讓您建立 <xref:System.Windows.Data.Binding.ValidationRules%2A> 與 <xref:System.Windows.Data.Binding> 物件的關聯。  例如，下列範例會將 <xref:System.Windows.Controls.TextBox> 繫結至名為 `StartPrice` 的屬性，並且將 <xref:System.Windows.Controls.ExceptionValidationRule> 物件加入至 <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=fullName> 屬性。  
  
 [!code-xml[DataBindingLab#DefaultValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 <xref:System.Windows.Controls.ValidationRule> 物件會檢查屬性的值是否有效。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 有下列兩種類型的內建 <xref:System.Windows.Controls.ValidationRule> 物件：  
  
-   <xref:System.Windows.Controls.ExceptionValidationRule> 會檢查繫結來源屬性更新期間所擲回的例外狀況。  在上面的範例中，`StartPrice` 的類型為整數。  當使用者輸入的值無法轉換為整數時，就會擲回例外狀況，造成繫結會標記為無效。  明確設定 <xref:System.Windows.Controls.ExceptionValidationRule> 的替代語法是，在 <xref:System.Windows.Data.Binding> 或 <xref:System.Windows.Data.MultiBinding> 物件上將 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> 屬性設定為 `true`。  
  
-   <xref:System.Windows.Controls.DataErrorValidationRule> 物件會檢查實作 <xref:System.ComponentModel.IDataErrorInfo> 介面之物件所引發的錯誤。  如需使用此驗證規則的範例，請參閱 <xref:System.Windows.Controls.DataErrorValidationRule>。  明確設定 <xref:System.Windows.Controls.DataErrorValidationRule> 的替代語法是，在 <xref:System.Windows.Data.Binding> 或 <xref:System.Windows.Data.MultiBinding> 物件上將 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> 屬性設定為 `true`。  
  
 您也可以藉由衍生自 <xref:System.Windows.Controls.ValidationRule> 類別和實作 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法，以建立自己的驗證規則。  下列範例顯示[資料繫結是什麼](#what_is_data_binding)一節中 *Add Product Listing* "Start Date" <xref:System.Windows.Controls.TextBox> 所使用的規則：  
  
 [!code-csharp[DataBindingLab#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> 會使用這個 *FutureDateRule*，如下列範例所示：  
  
 [!code-xml[DataBindingLab#CustomValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 請注意，因為 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值是 <xref:System.Windows.Data.UpdateSourceTrigger>，繫結引擎會依每個按鍵動作來更新來源值，這代表也會依每個按鍵動作來檢查 <xref:System.Windows.Data.Binding.ValidationRules%2A> 集合中的每個規則。  我們將在＜驗證過程＞一節中進一步討論這個部分。  
  
<a name="invalidation_feedback"></a>   
### 提供視覺化回應  
 如果使用者輸入無效值，您可能會想要在應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 中提供一些關於錯誤的回應。  提供這類回應的一個方式是將 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=fullName> 附加屬性設定為自訂 <xref:System.Windows.Controls.ControlTemplate>。  如先前小節所示，*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> 使用稱為 *validationTemplate* 的 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A>。  下列範例顯示 *validationTemplate* 的定義：  
  
 [!code-xml[DataBindingLab#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> 項目指定要裝飾的控制項要放於何處。  
  
 除此之外，您也可以使用 <xref:System.Windows.Controls.ToolTip> 顯示錯誤訊息。  *StartDateEntryForm* 和 *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> 都使用樣式 *textStyleTextBox*，會建立顯示錯誤訊息的 <xref:System.Windows.Controls.ToolTip>。  下列範例顯示 *textStyleTextBox* 的定義。  當繫結項目的屬性有一個或多個繫結發生錯誤時，[附加屬性](GTMT) <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 是 `true`。  
  
 [!code-xml[DataBindingLab#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 搭配自訂 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 和 <xref:System.Windows.Controls.ToolTip>，*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> 在有驗證錯誤時看起來類似下圖：  
  
 ![資料繫結驗證錯誤](../../../../docs/framework/wpf/data/media/databindingdemo-validation.png "DataBindingDemo\_Validation")  
  
 如果 <xref:System.Windows.Data.Binding> 具有關聯的驗證規則，但您沒有指定繫結控制項的 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A>，就會使用預設 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 在有驗證錯誤時告知使用者。  預設 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 是控制項樣板，會定義裝飾項層的紅色框線。  搭配預設 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 和 <xref:System.Windows.Controls.ToolTip>，*StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> 的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 在有驗證錯誤時看起來類似下圖：  
  
 ![資料繫結驗證錯誤](../../../../docs/framework/wpf/data/media/databindingdemo-validationdefault.png "DataBindingDemo\_ValidationDefault")  
  
 如需如何提供邏輯以驗證對話方塊中的所有控制項的範例，請參閱[對話方塊概觀](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)中的＜自訂對話方塊＞一節。  
  
<a name="validation_process"></a>   
### 驗證過程  
 通常驗證發生的時機，是將目標的值傳輸到繫結來源屬性的時候。  這種情形會發生在 <xref:System.Windows.Data.BindingMode> 和 <xref:System.Windows.Data.BindingMode> 繫結上。  再重複聲明一次，造成來源更新的原因取決於 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性的值，如[觸發來源更新的機制](#what_triggers_source_updates)一節所討論。  
  
 以下將描述「*驗證*」\(Validation\) 程序。  請注意，如果在此程序執行期間發生驗證錯誤或其他型別錯誤，處理序 \(Process\) 會中止。  
  
1.  繫結引擎會檢查是否有為該 <xref:System.Windows.Data.Binding> 定義 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 的任何自訂 <xref:System.Windows.Controls.ValidationRule> 物件設定為 <xref:System.Windows.Controls.ValidationStep>，如果有的話，就針對每個 <xref:System.Windows.Controls.ValidationRule> 呼叫 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法，直到其中一個規則發生錯誤或是所有規則都通過為止。  
  
2.  接著，繫結引擎就會在有轉換子的情況下呼叫轉換子。  
  
3.  如果轉換子成功，繫結引擎會檢查是否有為該 <xref:System.Windows.Data.Binding> 定義 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 的任何自訂 <xref:System.Windows.Controls.ValidationRule> 物件設定為 <xref:System.Windows.Controls.ValidationStep> ，如果有的話，就針對每個已將 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 設定為 <xref:System.Windows.Controls.ValidationStep> 的 <xref:System.Windows.Controls.ValidationRule> 呼叫 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法，直到其中一個規則發生錯誤或是所有規則都通過為止。  
  
4.  繫結引擎會設定來源屬性。  
  
5.  繫結引擎會檢查是否有為該 <xref:System.Windows.Data.Binding> 定義 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 的任何自訂 <xref:System.Windows.Controls.ValidationRule> 物件設定為 <xref:System.Windows.Controls.ValidationStep>，如果有的話，就針對每個將 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 設定為 <xref:System.Windows.Controls.ValidationStep> 的 <xref:System.Windows.Controls.ValidationRule> 呼叫 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法，直到其中一個規則發生錯誤或是所有規則都通過為止。  如果 <xref:System.Windows.Controls.DataErrorValidationRule> 和繫結相關聯，且已將其 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 設為預設值 \(<xref:System.Windows.Controls.ValidationStep>\)，則會在此時檢查 <xref:System.Windows.Controls.DataErrorValidationRule>。  這也是已將 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> 設為 `true` 之繫結的時間點。  
  
6.  繫結引擎會檢查是否有為該 <xref:System.Windows.Data.Binding> 定義 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 的任何自訂 <xref:System.Windows.Controls.ValidationRule> 物件設定為 <xref:System.Windows.Controls.ValidationStep>，如果有的話，就針對每個將 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 設定為 <xref:System.Windows.Controls.ValidationStep> 的 <xref:System.Windows.Controls.ValidationRule> 呼叫 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法，直到其中一個規則發生錯誤或是所有規則都通過為止。  
  
 在整個程序期間如果有一個 <xref:System.Windows.Controls.ValidationRule> 沒有通過，繫結引擎就會建立 <xref:System.Windows.Controls.ValidationError> 物件，並將其加入至該繫結項目的 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=fullName> 集合。  在繫結引擎於任何指定步驟中執行 <xref:System.Windows.Controls.ValidationRule> 物件之前，它會移除任何已在該步驟期間加入至繫結項目之 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=fullName> [附加屬性](GTMT)的 <xref:System.Windows.Controls.ValidationError>。  例如，如果 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 設定為 <xref:System.Windows.Controls.ValidationStep> 的 <xref:System.Windows.Controls.ValidationRule> 失敗，則在下一次執行驗證時，繫結引擎會在呼叫任何已將 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 設定為 <xref:System.Windows.Controls.ValidationStep> 的 <xref:System.Windows.Controls.ValidationRule> 之前，立即移除該 <xref:System.Windows.Controls.ValidationError>。  
  
 當 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=fullName> 不是空白時，該項目的 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> [附加屬性](GTMT)會設定為 `true`。  此外，如果 <xref:System.Windows.Data.Binding> 的 <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> 屬性設定為 `true`，則繫結引擎會針對項目引發 <xref:System.Windows.Controls.Validation.Error?displayProperty=fullName> [附加事件](GTMT)。  
  
 請注意，以任何一個方向 \(目標至來源或來源至目標\) 傳輸有效值時，都會清除 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=fullName> [附加屬性](GTMT)。  
  
 如果繫結具有關聯的 <xref:System.Windows.Controls.ExceptionValidationRule> 或已將 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> 屬性設為 `true`，並且在將繫結引擎設為來源時會擲回例外狀況，則繫結引擎會檢查 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> 是否存在。  您可以選擇使用 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> 回呼，以提供處理例外狀況的自訂處理常式。  如果未在 <xref:System.Windows.Data.Binding> 上指定 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>，則繫結引擎會建立具有例外狀況的 <xref:System.Windows.Controls.ValidationError>，並將其加入繫結項目的 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=fullName> 集合。  
  
<a name="debugging_mechanism"></a>   
## 偵錯機制  
 您可以對繫結相關的物件設定附加屬性 <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=fullName>，以接收特定繫結的狀態資訊。  
  
## 請參閱  
 <xref:System.Windows.Controls.DataErrorValidationRule>   
 [WPF 4.5 版的新功能](../../../../docs/framework/wpf/getting-started/whats-new.md)   
 [繫結至 LINQ 查詢結果](../../../../docs/framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [資料繫結示範](http://go.microsoft.com/fwlink/?LinkID=163703)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [繫結至 ADO.NET 資料來源](../../../../docs/framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)