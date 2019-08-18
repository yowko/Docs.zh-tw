---
title: 資料繫結概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data conversion for binding [WPF]
- binding data [WPF], about data binding
- data binding [WPF], about data binding
- conversion for data binding [WPF]
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
ms.openlocfilehash: 44a35131273c6f191ab5da5bc1639d97bd961ff1
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567524"
---
# <a name="data-binding-overview"></a>資料繫結概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結在資料的展示和互動上，提供應用程式簡單而一致的方式。 元素可以系結至各種資料來源中的資料, 其格式為 common language runtime (CLR) 物件和[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]。 <xref:System.Windows.Controls.ContentControl>之類的<xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox>和(例如和<xref:System.Windows.Controls.ListView> ) 具有內建功能, 可啟用單一資料項目或資料項目集合的彈性樣式。 <xref:System.Windows.Controls.Button> 您可以在資料上方產生排序、篩選和群組檢視。  
  
 相較於傳統模型，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的資料繫結功能具有數個優點，包括本身就支援資料繫結的相當多屬性、資料的彈性 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 表示，以及 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 個別的清楚商務邏輯。  
  
 本主題會先討論[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]資料系結的基本概念, 然後進入<xref:System.Windows.Data.Binding>類別的使用方式, 以及資料系結的其他功能。  

<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>資料繫結是什麼？  
 資料繫結是指在應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 與商務邏輯之間建立連接的程序。 如果繫結具有正確的設定而且資料提供了適當的通知，則當資料變更其值時，繫結至資料的元素就會自動反映變更。 資料繫結也代表在元素資料的外部表示變更時，基礎資料也會自動更新以反映變更。 例如, 如果使用者編輯<xref:System.Windows.Controls.TextBox>元素中的值, 則會自動更新基礎資料值以反映該變更。  
  
 一個資料繫結的常見用法是將伺服器或本機組態資料，放入表單或其他 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 控制項中。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中會擴充這個概念，以包含相當多屬性對各種資料來源的繫結。 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中, 元素的相依性屬性可以系結至 CLR 物件 (包括 ADO.NET 物件或與 web 服務和 web 屬性相關聯[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]的物件) 和資料。  
  
 如需資料繫結的範例，請參考下列來自[資料繫結示範](https://go.microsoft.com/fwlink/?LinkID=163703) 的應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]：  
  
 ![資料系結範例螢幕擷取畫面](./media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 上面的應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 會顯示拍賣項目的清單。 應用程式會示範下列資料繫結功能：  
  
- 的內容<xref:System.Windows.Controls.ListBox>會系結至*AuctionItem*物件的集合。 *AuctionItem* 物件具有 *Description*、*StartPrice*、*StartDate*、*Category* 和 *SpecialFeatures* 等屬性。  
  
- 中<xref:System.Windows.Controls.ListBox>顯示的資料 (*AuctionItem*物件) 會進行樣板化, 以顯示每個專案的描述和目前價格。 這會使用<xref:System.Windows.DataTemplate>來完成。 除此之外，每個項目的外觀取決於所顯示 *AuctionItem* 的 *SpecialFeatures* 值。 如果 *AuctionItem* 的 *SpecialFeatures* 值是 *Color*，項目就具有藍色框線。 如果值是 *Highlight*，項目就具有橘色框線和星號。 [資料範本化](#data_templating)一節會提供資料範本化的相關資訊。  
  
- 使用者可以使用提供的<xref:System.Windows.Controls.CheckBox>es 來分組、篩選或排序資料。 在上圖中, 已選取「依類別分組」和「依類別排序」和<xref:System.Windows.Controls.CheckBox>「日期」 es。 您可能已經注意到，資料的群組化是依據產品的分類，且分類名稱是以字母順序排列。 雖然在圖中很難辨識，但項目在每個分類內也有以開始日期排序。 這是藉由使用*集合檢視*而達成的。 [繫結至集合](#binding_to_collections)一節會討論集合檢視。  
  
- 當使用者選取專案時, <xref:System.Windows.Controls.ContentControl>會顯示所選取專案的詳細資料。 這稱為*一對多案例*。 [一對多案例](#master_detail_scenario)一節會提供這類型繫結案例的相關資訊。  
  
- *起始*屬性的類型是, 它<xref:System.DateTime>會傳回包含毫秒時間的日期。 這個應用程式中有使用自訂轉換器，因此顯示較短的日期字串。 [資料轉換](#data_conversion)一節會提供轉換器的相關資訊。  
  
 當使用者按一下 [Add Product (加入產品)] 按鈕時，會出現下列表單：  
  
 ![加入產品清單頁面](./media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 使用者可以編輯表單中的欄位、使用簡短預覽和更為詳盡的預覽窗格來預覽產品清單，然後再按一下 [Submit (提交)] 以加入新產品清單。 任何現有的群組、篩選和排序功能會套用到新項目上。 在這種特定情形下，輸入上圖的項目會在 [Computer (電腦)] 分類內顯示為第二個項目。  
  
 此圖中未顯示的是*開始日期* <xref:System.Windows.Controls.TextBox>中所提供的驗證邏輯。 如果使用者輸入不正確日期 (格式無效或過去的日期), 使用者就會收到通知<xref:System.Windows.Controls.ToolTip> , 並在旁邊<xref:System.Windows.Controls.TextBox>出現紅色驚嘆號。 [資料驗證](#data_validation)一節會討論如何建立驗證邏輯。  
  
 在進入上面概要說明的各種功能之前，下節中我們會先討論對於了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資料繫結很重要的基本概念。  
  
## <a name="basic-data-binding-concepts"></a>基本資料繫結概念  
  
 不管您的繫結元素是什麼，也不論資料來源的本質，每個繫結一定會遵循下圖所說明的模型：  
  
 ![顯示基本資料系結模型的圖表。](./media/data-binding-overview/basic-data-binding-diagram.png)  
  
 如上圖所說明，資料繫結基本上是繫結目標和繫結來源間的橋樑。 該圖示範下列基本 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資料繫結概念：  
  
- 一般而言，每個繫結都具有這四個元件：繫結目標物件、目標屬性、繫結來源，以及繫結來源中要使用之值的路徑。 例如, 如果您想要將的內容<xref:System.Windows.Controls.TextBox>系結至*Employee*物件的<xref:System.Windows.Controls.TextBox> *Name*屬性, 您的目標物件是、目標屬性<xref:System.Windows.Controls.TextBox.Text%2A>是屬性、要使用的值是*Name*, 以及來源物件是*Employee*物件。  
  
- 目標屬性必須是相依性屬性。 大部分<xref:System.Windows.UIElement>屬性都是相依性屬性, 而除了唯讀以外, 大部分的相依性屬性預設都支援資料系結。 (只有<xref:System.Windows.DependencyObject>類型可以定義相依性屬性, <xref:System.Windows.UIElement>而且所有衍生<xref:System.Windows.DependencyObject>自)。  
  
- 雖然未在圖中指定, 但請注意, 系結來源物件不限於自訂 CLR 物件。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]資料系結支援 CLR 物件和[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]格式的資料。 為了提供一些範例, 您的<xref:System.Windows.UIElement>系結來源可以是、任何清單物件、與 ADO.NET 資料或 Web 服務相關聯的 CLR 物件, 或是包含您[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料的 XmlNode。 如需詳細資訊，請參閱[繫結來源概觀](binding-sources-overview.md)。  
  
 當您閱讀其他 SDK 主題時, 請務必記住, 當您建立系結時, 您會將系結目標系結*至*系結來源。 例如, 如果您要使用資料系結[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] <xref:System.Windows.Controls.ListBox>來顯示中<xref:System.Windows.Controls.ListBox>的一些基礎資料, 您[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]會將系結至資料。  
  
 若要建立系結, 您可以<xref:System.Windows.Data.Binding>使用物件。 本主題的其餘部分將討論與相關的許多概念以及<xref:System.Windows.Data.Binding>物件的一些屬性和使用方式。  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>資料流程的方向  
 如先前所述, 如同上圖中的箭號所示, 系結的資料流程可以從系結目標移至系結來源 (例如, 當使用者編輯的值<xref:System.Windows.Controls.TextBox>) 和/或來自系結來源時, 來源值就會變更。如果系結來源提供適當的通知, <xref:System.Windows.Controls.TextBox>系結目標 (例如, 您的內容會更新系結來源中的變更)。  
  
 您可能會想讓使用者透過應用程式變更資料，並將變更散佈回來源物件。 或者您可能不希望使用者更新來源資料。 您可以藉由設定<xref:System.Windows.Data.Binding.Mode%2A> <xref:System.Windows.Data.Binding>物件的屬性來控制此項。 下圖說明不同類型的資料流程：  
  
 ![資料繫結資料流程](./media/databinding-dataflow.png "DataBinding_DataFlow")  
  
- <xref:System.Windows.Data.BindingMode.OneWay>系結會使 source 屬性的變更自動更新目標屬性, 但對目標屬性的變更不會傳播回來源屬性。 如果要繫結的控制項是隱含唯讀的，這種類型的繫結很適當。 例如，您可以繫結到股票行情即時看板這類的來源，或者目標屬性沒有可供進行變更的控制項介面，例如資料表的資料繫結背景色彩。 如果不需要監視目標屬性的變更，使用 <xref:System.Windows.Data.BindingMode.OneWay> 繫結模式可以避免 <xref:System.Windows.Data.BindingMode.TwoWay> 繫結模式的額外負荷。  
  
- <xref:System.Windows.Data.BindingMode.TwoWay>系結會使來源屬性或目標屬性的變更自動更新另一個。 這種類型的繫結適合可編輯表單或其他完全互動式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例。 大部分屬性預設為<xref:System.Windows.Data.BindingMode.OneWay>系結, 但部分相依性屬性 (通常是使用者可編輯控制項的屬性<xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> , 例如的屬性<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>和的<xref:System.Windows.Controls.CheckBox>屬性) 預設為<xref:System.Windows.Data.BindingMode.TwoWay> binding。 判斷相依性屬性預設是否會單向或雙向繫結的程式設計方式是，使用 <xref:System.Windows.DependencyProperty.GetMetadata%2A> 取得屬性的屬性中繼資料，然後檢查 <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> 屬性的布林值。  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource>這是系結<xref:System.Windows.Data.BindingMode.OneWay>的反向; 當目標屬性變更時, 它會更新 source 屬性。 範例案例之一是當您只需要從 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 重新評估來源值時。  
  
- 圖中未說明的是<xref:System.Windows.Data.BindingMode.OneTime>系結, 這會導致 source 屬性初始化目標屬性, 但後續的變更不會傳播。 這代表如果資料內容發生變更或資料內容中的物件有變更，則變更不會反映在目標屬性中。 如果您使用的資料適合使用目前狀態的快照集或資料是真正的靜態，則此類型的繫結很適當。 如果您想要以來源屬性的某些值初始化目標屬性，但無法預先得知資料內容，則此類型的繫結也很有用。 這是 <xref:System.Windows.Data.BindingMode.OneWay> 繫結的基本簡易形式，萬一來源值不變更，可提供較佳的效能。  
  
 請注意, 若要偵測來源變更 ( <xref:System.Windows.Data.BindingMode.OneWay>適用<xref:System.Windows.Data.BindingMode.TwoWay>于和系結), 來源必須執行適當的屬性<xref:System.ComponentModel.INotifyPropertyChanged>變更通知機制, 例如。 如需<xref:System.ComponentModel.INotifyPropertyChanged>執行的範例, 請參閱[執行屬性變更通知](how-to-implement-property-change-notification.md)。  
  
 [ <xref:System.Windows.Data.Binding.Mode%2A>屬性] 頁面會提供系結模式的詳細資訊, 以及如何指定系結方向的範例。  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>觸發來源更新的機制  
 系結, <xref:System.Windows.Data.BindingMode.TwoWay>或<xref:System.Windows.Data.BindingMode.OneWayToSource>接聽目標屬性中的變更, 並將它們傳播回來源。 這種情況稱為更新來源。 舉例來說，您可以編輯 TextBox 的文字以變更基礎來源值。 如上一節所述, 資料流程的方向是由系結的<xref:System.Windows.Data.Binding.Mode%2A>屬性值所決定。  
  
 然而，當您編輯文字時，或者是在完成文字編輯且將滑鼠指標帶離 TextBox 後，來源值是否有更新？ 系結的屬性會決定觸發來源更新的原因。 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 下圖中右箭號的點說明<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性的角色:  
  
 ![顯示 UpdateSourceTrigger 屬性角色的圖表。](./media/data-binding-overview/data-binding-updatesource-trigger.png)  
  
 如果值為, <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>則當目標屬性變更時, <xref:System.Windows.Data.BindingMode.TwoWay>或<xref:System.Windows.Data.BindingMode.OneWayToSource>系結的向右箭號所指向的值就會更新。 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 不過, 如果<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值為, <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>則只有當目標屬性失去焦點時, 才會以新的值更新該值。  
  
 與屬性類似<xref:System.Windows.Data.Binding.Mode%2A> , 不同的相依性屬性有不同<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的預設值。 大多數相依性屬性的預設值為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>，而 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性具有 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> 的預設值。 這表示當目標屬性變更時, 通常會發生來源更新, 這適用于<xref:System.Windows.Controls.CheckBox>es 和其他簡單的控制項。 然而，對於文字欄位而言，在每個按鍵動作後更新會降低效能，並且在提交新值之前拒絕使用者按退格鍵和修正輸入錯誤的一般機會。 這就是為什麼<xref:System.Windows.Controls.TextBox.Text%2A>屬性的預設<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>值為, 而不<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>是。  
  
 如需<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>如何尋找相依性屬性之預設<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值的相關資訊, 請參閱屬性頁。  
  
 下表提供每個<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值的範例案例, <xref:System.Windows.Controls.TextBox>使用做為範例:  
  
|UpdateSourceTrigger 值|來源值更新時機|TextBox 的範例案例|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (的<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>預設值)|TextBox 控制項失去焦點時|與<xref:System.Windows.Controls.TextBox>驗證邏輯相關聯的 (請參閱資料驗證一節)|  
|PropertyChanged|當您輸入<xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox>聊天室視窗中的控制項|  
|明確|當應用程式呼叫時<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox>可編輯表單中的控制項 (只有在使用者按一下 [提交] 按鈕時才會更新來源值)|  
  
 如需範例，請參閱[控制 TextBox 文字更新來源的時機](how-to-control-when-the-textbox-text-updates-the-source.md)。  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>建立繫結。  
  
 若要 recapitulate 先前幾節中所討論的一些概念, 您可以使用<xref:System.Windows.Data.Binding>物件建立系結, 而且每個系結通常會有四個元件: 系結目標、目標屬性、系結來源, 以及要使用之來源值的路徑。 本節討論如何設定繫結。  
  
 請考慮下列範例，其中的繫結來源物件是名為 *MyData* 的類別，定義於 *SDKSample* 命名空間中。 為了便於示範，*MyData* 類別的字串屬性名為 *ColorName*，其值設為 "Red"。 因此，本範例會產生具有紅色背景的按鈕。  
  
 [!code-xaml[BindNonTextProperty#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 如需繫結宣告語法的詳細資訊，以及如何在程式碼中設定繫結的範例，請參閱[繫結宣告概觀](binding-declarations-overview.md)。  
  
 如果將這個範例套用到我們的基本圖表，結果會類似下圖。 這是<xref:System.Windows.Data.BindingMode.OneWay>系結, 因為 Background 屬性預設<xref:System.Windows.Data.BindingMode.OneWay>支援系結。  
  
 ![顯示資料系結背景屬性的圖表。](./media/data-binding-overview/data-binding-button-background-example.png)  
  
 您可能會想知道當*ColorName*屬性是字串類型, 而<xref:System.Windows.Controls.Control.Background%2A>屬性的類型<xref:System.Windows.Media.Brush>為時, 這項工作的原因。 這是因為預設型別轉換的作用，在[資料轉換](#data_conversion)一節中會討論到。  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>指定繫結來源  
 請注意, 在上一個範例中, 系結來源是藉由<xref:System.Windows.FrameworkElement.DataContext%2A>在<xref:System.Windows.Controls.DockPanel>元素上設定屬性來指定。 接著會繼承的<xref:System.Windows.Controls.DockPanel>值, 也就是它的父元素。 <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.Button> 再重複聲明一次，繫結來源物件是繫結的四個必要元件之一。 因此，沒有指定繫結來源物件，就無法進行繫結。  
  
 有數種方式可以指定繫結來源物件。 當您將多個屬性系結至相同的來源時, 在父元素上使用屬性會很有用。<xref:System.Windows.FrameworkElement.DataContext%2A> 然而，有時候在個別的繫結宣告上指定繫結來源可能比較恰當。 在上一個範例中, 您可以在<xref:System.Windows.FrameworkElement.DataContext%2A>按鈕的系結宣告上直接<xref:System.Windows.Data.Binding.Source%2A>設定屬性, 而不使用屬性來指定系結來源, 如下列範例所示:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 除了直接在專案<xref:System.Windows.FrameworkElement.DataContext%2A>上設定屬性外, 也會繼承<xref:System.Windows.FrameworkElement.DataContext%2A>上階的值 (例如第一個範例中的按鈕), 並藉由設定<xref:System.Windows.Data.Binding.Source%2A>上的屬性,明確指定系結來源。<xref:System.Windows.Data.Binding>(例如最後一個範例的按鈕), 您也可以使用<xref:System.Windows.Data.Binding.ElementName%2A>屬性<xref:System.Windows.Data.Binding.RelativeSource%2A>或屬性來指定系結來源。 當您要系結至應用程式中的其他專案 (例如, 當您使用滑杆來調整按鈕的寬度) 時,屬性會很有用。<xref:System.Windows.Data.Binding.ElementName%2A> 在<xref:System.Windows.Data.Binding.RelativeSource%2A> 或<xref:System.Windows.Controls.ControlTemplate>中指定系結時, 屬性會很有用。 <xref:System.Windows.Style> 如需詳細資訊，請參閱[指定繫結來源](how-to-specify-the-binding-source.md)。  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>指定值的路徑  
 如果您的系結來源是物件, 您可以<xref:System.Windows.Data.Binding.Path%2A>使用屬性來指定要用於系結的值。 如果您要系結[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]至資料, 請<xref:System.Windows.Data.Binding.XPath%2A>使用屬性來指定值。 在某些情況下, 即使您的資料為<xref:System.Windows.Data.Binding.Path%2A> [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], 也可能適用于使用屬性。 例如, 如果您想要存取所傳回 XmlNode 的 Name 屬性 (因為 XPath 查詢的結果), 除了<xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Data.Binding.XPath%2A>屬性之外, 您還應該使用屬性。  
  
 如需語法資訊和範例, 請<xref:System.Windows.Data.Binding.Path%2A>參閱<xref:System.Windows.Data.Binding.XPath%2A>和屬性頁。  
  
 請注意, 雖然我們已強調<xref:System.Windows.Data.Binding.Path%2A>要使用的值是系結的四個必要元件之一, 但在您想要系結至整個物件的案例中, 要使用的值會與系結來源物件相同。 在這些情況下, 它適用于不指定<xref:System.Windows.Data.Binding.Path%2A>。 參考下列範例：  
  
 [!code-xaml[MasterDetail#EmptyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 上述範例使用空白繫結語法：{Binding}。 在此情況下, <xref:System.Windows.Controls.ListBox>會從父 DockPanel 元素繼承 DataCoNtext (在此範例中未顯示)。 沒有指定路徑時，預設會繫結到整個物件。 換句話說, 在此範例中, 路徑已被省略, 因為我們將<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性系結至整個物件。 (如需深入討論，請參閱[繫結至集合](#binding_to_collections)一節)。  
  
 除了繫結到集合之外，當您要繫結到整個物件而非只是物件的單一屬性時，這個案例也很好用。 舉例來說，如果來源物件的型別是字串，而您只是要繫結到字串本身時。 另一個常用案例是當您要將元素繫結到具有許多屬性的物件時。  
  
 請注意，您可能必須套用自訂邏輯，如此資料對於繫結目標屬性來說才有意義。 自訂邏輯的型式可以是自訂轉換器 (如果沒有預設型別轉換)。 如需轉換器的詳細資訊，請參閱[資料轉換](#data_conversion)。  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>繫結和 BindingExpression  
 在取得資料系結的其他功能和使用方式之前, 引進<xref:System.Windows.Data.BindingExpression>類別會很有用。 如同您在先前的章節中所見<xref:System.Windows.Data.Binding> , 類別是系結宣告的高階類別<xref:System.Windows.Data.Binding> ; 類別提供許多屬性, 可讓您指定系結的特性。 相關類別<xref:System.Windows.Data.BindingExpression>是基礎物件, 可維護來源與目標之間的連接。 繫結包含可以跨數種繫結運算式共用的所有資訊。 是無法共用的實例運算式, 而且包含的所有實例資訊<xref:System.Windows.Data.Binding>。 <xref:System.Windows.Data.BindingExpression>  
  
 例如, 請考慮下列各項, 其中*myDataObject*是*MyData*類別的實例, *myBinding*是來源<xref:System.Windows.Data.Binding>物件, 而*MyData*類別是定義的類別, 其中包含名為*的字串屬性。MyDataProperty*。 這個範例會將*mytext*(的實例<xref:System.Windows.Controls.TextBlock>) 的文字內容系結至*MyDataProperty*。  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 您可以使用相同的 *myBinding* 物件建立其他繫結。 舉例來說，您可以使用 *myBinding* 物件將核取方塊的文字內容繫結到 *MyDataProperty*。 在該案例中, 將會有兩個<xref:System.Windows.Data.BindingExpression>共用*myBinding*物件的實例。  
  
 您可以透過在資料系結物件上呼叫<xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A>的傳回值來取得物件。<xref:System.Windows.Data.BindingExpression> 下列主題將示範<xref:System.Windows.Data.BindingExpression>類別的一些使用方式:  
  
- [從繫結的目標屬性取得繫結物件](how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
- [控制 TextBox 文字更新來源的時機](how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>資料轉換  
 在上述範例中, 按鈕是紅色的, 因為<xref:System.Windows.Controls.Control.Background%2A>它的屬性系結至值為 "red" 的字串屬性。 這是因為類型轉換器會出現在<xref:System.Windows.Media.Brush>類型上, 以將字串值轉換<xref:System.Windows.Media.Brush>為。  
  
 若要將這項資訊加入到[建立繫結](#creating_a_binding)一節的圖中，則圖表看起來會像這樣：  
  
 ![顯示資料系結預設屬性的圖表。](./media/data-binding-overview/data-binding-button-default-conversion.png)  
  
 不過, 如果您的系結來源物件具有類型<xref:System.Windows.Media.Color>的*色彩*屬性, 而不是使用字串類型的屬性, 該怎麼辦？ 在這種情況下, 若要讓系結能夠正常執行, 您必須先將*Color*屬性值轉換成<xref:System.Windows.Controls.Control.Background%2A>屬性所接受的內容。 您必須藉由執行<xref:System.Windows.Data.IValueConverter>介面來建立自訂轉換器, 如下列範例所示:  
  
 [!code-csharp[ColorPicker_snip#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 [ <xref:System.Windows.Data.IValueConverter>參考] 頁面會提供詳細資訊。  
  
 現在是使用自訂轉換器來代替預設轉換，圖表如下圖所示：  
  
 ![顯示資料系結自訂轉換器的圖表。](./media/data-binding-overview/data-binding-converter-color-example.png)  
  
 再重複聲明一次，預設轉換也可以使用，因為要繫結的型別中存在型別轉換器。 這個行為會取決於目標中提供的型別轉換器。 如果有疑問，請建立自己的轉換器。  
  
 下列是適合實作資料轉換器的一些常見案例：  
  
- 依據文化特性的不同，您的資料顯示方式會有所不同。 例如，依據特定文化特性所使用的值或標準，您可能會想要實作貨幣轉換器或日曆日期/時間轉換器。  
  
- 要使用的資料不見得是要變更屬性的文字值，但有可能是改為變更某些其他值，例如影像的來源，或者是顯示文字的色彩或樣式。 在這個情況下可能的轉換器使用方式，是藉由將可能不適合的屬性繫結轉換，例如將文字欄位繫結到表格儲存格的 Background 屬性。  
  
- 一個以上的控制項或者是控制項的多個屬性，會繫結到相同資料。 在這個情況下，主要繫結可能只是顯示文字，而其他繫結會處理特定顯示問題，但仍然使用相同的繫結做為來源資訊。  
  
- 到目前為止, 我們尚未討論<xref:System.Windows.Data.MultiBinding>過, 其中的目標屬性具有系結的集合。 在案例<xref:System.Windows.Data.MultiBinding>中, 您可以使用自訂<xref:System.Windows.Data.IMultiValueConverter>的, 從系結的值產生最終的值。 舉例來說，顏色可以由紅藍綠的值計算而來，而這些值可以來自相同或不同的繫結來源物件。 如需範例和資訊, 請參閱類別頁面。<xref:System.Windows.Data.MultiBinding>  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>繫結至集合  
  
 繫結來源物件可以視為其屬性包含資料的單一物件，或是通常會群組在一起的多型物件的資料集合 (例如資料庫查詢的結果)。 目前為止，我們只討論到單一物件的繫結，然而，繫結到資料集合是常見的案例。 例如, 常見的<xref:System.Windows.Controls.ItemsControl>案例是使用<xref:System.Windows.Controls.ListBox>、 <xref:System.Windows.Controls.ListView>或<xref:System.Windows.Controls.TreeView>之類的來顯示資料收集, 例如在 [[什麼是資料系結？](#what_is_data_binding) ] 區段中所顯示的應用程式中。  
  
 所幸，我們的基本圖表仍然適用。 如果您要將系<xref:System.Windows.Controls.ItemsControl>結至集合, 圖表看起來會像這樣:  
  
 ![顯示資料系結 ItemsControl 物件的圖表。](./media/data-binding-overview/data-binding-itemscontrol.png)  
  
 如此圖所示, 若要<xref:System.Windows.Controls.ItemsControl>將系結至集合物件, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性是要使用的屬性。 您可以<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>將屬性視為的內容<xref:System.Windows.Controls.ItemsControl>。 請注意, 系結<xref:System.Windows.Data.BindingMode.OneWay>是<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>因為屬性預設<xref:System.Windows.Data.BindingMode.OneWay>支援系結。  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>如何實作集合  
 您可以列舉任何會執行<xref:System.Collections.IEnumerable>介面的集合。 不過, 若要設定動態系結, 讓集合中的插入或刪除[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]自動更新, 則集合必須<xref:System.Collections.Specialized.INotifyCollectionChanged>執行介面。 這個介面會公開每次基礎集合變更時必須引發的事件。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供類別, 這是<xref:System.Collections.Specialized.INotifyCollectionChanged>公開介面之資料集合的內建執行。 <xref:System.Collections.ObjectModel.ObservableCollection%601> 請注意, 若要完全支援將資料值從來源物件傳送至目標, 集合中支援可系結屬性的每個<xref:System.ComponentModel.INotifyPropertyChanged>物件也必須執行介面。 如需詳細資訊，請參閱[繫結來源概觀](binding-sources-overview.md)。  
  
 在執行您自己的集合之前, <xref:System.Collections.ObjectModel.ObservableCollection%601>請考慮使用或其中一個現有的集合類別<xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>例如、 <xref:System.ComponentModel.BindingList%601>和。 如果您有一個先進的案例, 而且想要執行自己的集合, <xref:System.Collections.IList>請考慮使用, 它會提供可依索引個別存取的非泛型物件集合, 進而達到最佳效能。  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>集合檢視  
 <xref:System.Windows.Controls.ItemsControl>一旦系結至資料集合之後, 您可能會想要排序、篩選或群組資料。 若要這麼做, 您可以使用「集合視圖」, 這是<xref:System.ComponentModel.ICollectionView>執行介面的類別。  

#### <a name="what-are-collection-views"></a>集合檢視是什麼  
 集合檢視是以繫結來源集合為基礎的一層，可以讓您依據排序、篩選和群組查詢來巡覽和顯示來源集合，而不需要變更基礎來源集合本身。 集合檢視也會保留集合中目前項目的指標。 如果來源集合<xref:System.Collections.Specialized.INotifyCollectionChanged>會執行介面, <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged>事件所引發的變更就會傳播至 views。  
  
 因為檢視不會變更基礎來源集合，每個來源集合可以有多個相關聯的檢視。 舉例來說，您可以有一個 *Task* 物件集合。 使用檢視時，您可以不同方式顯示相同資料。 舉例來說，在頁面左方您可以顯示依優先順序排序的工作，右方顯示依區域分組的工作。  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>如何建立檢視  
 建立和使用檢視的方法之一，是直接具現化檢視物件，然後將它做為繫結來源使用。 例如，以[資料繫結是什麼](#what_is_data_binding)一節中顯示的[資料繫結示範](https://go.microsoft.com/fwlink/?LinkID=163703)應用程式為例。 應用程式會<xref:System.Windows.Controls.ListBox>實作為, 而不是直接系結至資料集合的視圖, 而是直接系結至資料集合。 下列範例擷取自[資料繫結示範](https://go.microsoft.com/fwlink/?LinkID=163703)應用程式。 類別是繼承自之<xref:System.Windows.Data.CollectionView>類別的proxy。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Data.CollectionViewSource> 在此特定範例中, <xref:System.Windows.Data.CollectionViewSource.Source%2A>視圖的會系結至目前應用程式物件的*AuctionItems*集合 (屬於類型<xref:System.Collections.ObjectModel.ObservableCollection%601>)。  
  
 [!code-xaml[DataBindingLab#WindowResources1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 然後, 資源*listingDataView*會作為應用程式中元素的系結來源, 例如<xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 若要為相同的集合建立另一個視圖, 您可以<xref:System.Windows.Data.CollectionViewSource>建立另一個實例, 並`x:Key`指定不同的名稱。  
  
 下表顯示哪些視圖資料類型會建立為預設的集合視圖, 或<xref:System.Windows.Data.CollectionViewSource>根據來源集合類型。  
  
|來源集合型別|集合檢視型別|注意|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|以為基礎的內部類型<xref:System.Windows.Data.CollectionView>|無法群組項目。|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|最快。|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>使用預設檢視  
 指定集合檢視做為繫結來源是建立和使用集合檢視的方式之一。 WPF 也會為做為繫結來源使用的每個集合建立預設集合檢視。 如果您直接繫結至集合，WPF 會繫結至它的預設檢視。 請注意，此預設檢視是由相同集合的所有繫結所共用，因此若其中一個繫結控制項或程式碼 (例如排序或變更目前的項目指標，這會在稍後討論) 變更預設檢視，此變更會反映在相同集合的所有其他繫結中。  
  
 若要取得預設的視圖, 您可以<xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A>使用方法。 如需範例，請參閱[取得資料集合的預設檢視](how-to-get-the-default-view-of-a-data-collection.md)。  
  
##### <a name="collection-views-with-adonet-datatables"></a>包含 ADO.NET DataTables 的集合檢視  
 為了改善效能, ADO.NET <xref:System.Data.DataTable>或<xref:System.Data.DataView>物件的集合視圖會將<xref:System.Data.DataView>排序和篩選委派給。 這會使得資料來源的所有集合檢視共用排序和篩選。 若要讓每個集合視圖單獨進行排序和篩選, 請使用自己<xref:System.Data.DataView>的物件初始化每個集合視圖。  
  
#### <a name="sorting"></a>排序  
 如先前所述，檢視可以將排序順序套用到集合上。 當資料存在於基礎集合中時，資料本身可能有也可能沒有相關的順序。 對集合的檢視可以讓您依據所提供的比較準則，安排順序或變更預設順序。 因為是資料的用戶端檢視，常見的案例是使用者會想要針對資料行對應的值，而排序表格式資料的資料行。 藉由使用檢視，就可以套用這個使用者驅動的排序，同樣不需要對基礎集合進行任何變更，或甚至不需要重新查詢集合內容。 如需範例，請參閱[在按一下標頭時排序 GridView 資料行](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)。  
  
 下列範例顯示「[什麼是資料系結](#what_is_data_binding)」一節中, 應用程式<xref:System.Windows.Controls.CheckBox> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的「依類別目錄和日期排序」的排序邏輯:  
  
 [!code-csharp[DataBindingLab#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>篩選  
 檢視也可以對集合套用篩選。 這代表雖然項目是存在於集合中的，這個特別的檢視可以只顯示完整集合的部分子集。 您可以對資料篩選條件。 比方說, 在「[什麼是資料系結？](#what_is_data_binding) 」一節中, 應用程式會執行「僅顯示 bargains <xref:System.Windows.Controls.CheckBox> 」, 其中包含用來篩選掉成本 $25 或更多之專案的邏輯。 當選取時<xref:System.Windows.Controls.CheckBox> , 會執行下列程式碼, <xref:System.Windows.Data.CollectionViewSource.Filter>將*ShowOnlyBargainsFilter*設定為事件處理常式:  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* 事件處理常式實作如下：  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 如果您直接使用其中一個<xref:System.Windows.Data.CollectionView>類別<xref:System.Windows.Data.CollectionViewSource> <xref:System.Windows.Data.CollectionView.Filter%2A> , 而不是, 則會使用屬性來指定回呼。 如需範例，請參閱[篩選檢視中的資料](how-to-filter-data-in-a-view.md)。  
  
#### <a name="grouping"></a>群組  
 除了用來流覽<xref:System.Collections.IEnumerable>集合的內部類別之外, 所有集合視圖都支援群組的功能, 這可讓使用者將集合視圖中的集合分割成邏輯群組。 群組可以是明確的，由使用者提供群組清單，或者是隱含的，讓群組依據資料動態產生。  
  
 下列範例顯示「Group by category <xref:System.Windows.Controls.CheckBox>」的邏輯:  
  
 [!code-csharp[DataBindingLab#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 如需另一個群組範例，請參閱[實作 GridView 的 ListView 中的群組項目](../controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md)。  
  
#### <a name="current-item-pointers"></a>目前項目指標  
 檢視也支援目前項目的概念。 您可以在集合檢視中逐一巡覽物件。 當您巡覽時，移動項目指標可以讓您擷取集合中存在該特定位置的物件。 如需範例，請參閱[透過資料 CollectionView 中的物件巡覽](how-to-navigate-through-the-objects-in-a-data-collectionview.md)。  
  
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
  
 目前項目指標可能會受套用至集合的任何排序或篩選所影響。 排序會將目前項目指標保留在最後選取的項目上，但現在集合檢視已在其周圍重組結構。 (或許選取的項目先前是在清單的開頭，但現在選取的項目可能是在中間的某處)。如果該選取內容在篩選之後仍然在檢視範圍中，篩選就會保留選取的項目。 否則，目前項目指標會設定在篩選集合檢視的第一個項目。  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>主從式繫結案例  
 目前項目的概念不但對巡覽集合項目很有用，也能應用在主從式繫結案例。 請再回想[資料繫結是什麼](#what_is_data_binding)一節中的應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 在該應用程式中, 中<xref:System.Windows.Controls.ListBox>的選取專案會決定<xref:System.Windows.Controls.ContentControl>中所顯示的內容。 若要以另一種方式放入<xref:System.Windows.Controls.ListBox> , 當選取專案時<xref:System.Windows.Controls.ContentControl> , 會顯示所選取專案的詳細資料。  
  
 您可以實作主從式案例，只要藉由讓兩或多個控制項繫結到相同檢視即可。 下列來自資料系結[示範](https://go.microsoft.com/fwlink/?LinkID=163703)的範例會<xref:System.Windows.Controls.ListBox>顯示的標記, 以及<xref:System.Windows.Controls.ContentControl>您在「[什麼是資料系結](#what_is_data_binding)」一節中的應用程式[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]上所看到的。  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 請注意，這兩個控制項都繫結到相同來源：*listingDataView* 靜態資源 (請參閱[如何建立檢視](#how_to_create_a_view)一節中這個資源的定義)。 這是因為當單一物件 ( <xref:System.Windows.Controls.ContentControl>在此案例中為) 系結至集合視圖時, 它會自動系結<xref:System.Windows.Data.CollectionView.CurrentItem%2A>至視圖的。 請注意<xref:System.Windows.Data.CollectionViewSource> , 物件會自動同步處理貨幣和選取範圍。 如果您的清單控制項未系結至<xref:System.Windows.Data.CollectionViewSource>物件, 如下列範例所示, 則您必須將其<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>屬性設定`true`為, 才能讓此作業正常執行。  
  
 如需其他範例，請參閱[繫結至集合並根據選取項目顯示資訊](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)和[使用含階層式資料的主從式模式](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。  
  
 您可能已經注意到上述範例有使用範本。 事實上, 資料不會以<xref:System.Windows.Controls.ContentControl>我們想要的方式來顯示, 而不使用範本 (明確使用的, 和<xref:System.Windows.Controls.ListBox>由隱含使用的)。 現在，下節中要說明資料範本化。  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>資料範本化  
 沒有使用資料範本的話，[資料繫結是什麼](#what_is_data_binding)一節中的應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 看起來會類似下圖：  
  
 ![不含資料範本的資料繫結示範](./media/data-binding-overview/data-binding-demo-templates.png)  
  
 如前一節中的範例所示, <xref:System.Windows.Controls.ListBox>控制項<xref:System.Windows.Controls.ContentControl>和都系結至*AuctionItem*s 的整個集合物件 (或更明確地說, 也就是集合物件上的視圖)。 若沒有如何顯示資料收集的特定指示, <xref:System.Windows.Controls.ListBox>會顯示基礎集合中每個物件的字串表示, <xref:System.Windows.Controls.ContentControl>而且會顯示其所系結之物件的字串表示。  
  
 為了解決這個問題, 應用程式會<xref:System.Windows.DataTemplate>定義。 如前一節中的範例所示, <xref:System.Windows.Controls.ContentControl>會明確地使用*detailsProductListingTemplate* <xref:System.Windows.DataTemplate>。 控制項<xref:System.Windows.Controls.ListBox>在集合中顯示 AuctionItem <xref:System.Windows.DataTemplate>物件時,會隱含地使用下列內容:  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 使用這兩個<xref:System.Windows.DataTemplate>時, 產生的 UI 會顯示在[什麼是資料系結？](#what_is_data_binding)一節中。 您可以從該螢幕擷取畫面中看到, 除了可讓您將資料放在控制項<xref:System.Windows.DataTemplate>中之外, 還可讓您為資料定義引人注目的視覺效果。 例如, 在<xref:System.Windows.DataTrigger>上述<xref:System.Windows.DataTemplate>的中會使用, 讓*SpecialFeatures*值為*醒目*提示的*AuctionItem*會以橙色框線和星形來顯示。  
  
 如需資料範本的詳細資訊，請參閱[資料範本化概觀](data-templating-overview.md)。  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>資料驗證  
  
 接受使用者輸入的大部分應用程式都需要驗證邏輯，以確保使用者輸入的是預期的資訊。 驗證會依據類型、範圍、格式或其他應用程式特定的需求而進行檢查。 本節討論 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的資料驗證運作方式。  
  
### <a name="associating-validation-rules-with-a-binding"></a>建立驗證規則與繫結的關聯  
 資料系結模型可讓您與<xref:System.Windows.Data.Binding>物件產生關聯<xref:System.Windows.Data.Binding.ValidationRules%2A>。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 例如, 下列<xref:System.Windows.Controls.TextBox>範例會將系結至名為`StartPrice`的屬性, 並<xref:System.Windows.Controls.ExceptionValidationRule> <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType>將物件加入至屬性。  
  
 [!code-xaml[DataBindingLab#DefaultValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 <xref:System.Windows.Controls.ValidationRule>物件會檢查屬性的值是否有效。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]具有下列兩種類型的內<xref:System.Windows.Controls.ValidationRule>建物件:  
  
- 會<xref:System.Windows.Controls.ExceptionValidationRule>檢查系結來源屬性更新期間所擲回的例外狀況。 在上面的範例中，`StartPrice` 的型別為整數。 當使用者輸入的值無法轉換為整數時，就會擲回例外狀況，造成繫結標記為無效。 明確<xref:System.Windows.Controls.ExceptionValidationRule>設定的替代語法是在您<xref:System.Windows.Data.Binding>的或<xref:System.Windows.Data.MultiBinding>物件<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>上將`true`屬性設定為。  
  
- 物件會檢查<xref:System.ComponentModel.IDataErrorInfo>執行介面之物件所引發的錯誤。 <xref:System.Windows.Controls.DataErrorValidationRule> 如需使用此驗證規則的範例, 請<xref:System.Windows.Controls.DataErrorValidationRule>參閱。 明確<xref:System.Windows.Controls.DataErrorValidationRule>設定的替代語法是在您<xref:System.Windows.Data.Binding>的或<xref:System.Windows.Data.MultiBinding>物件<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>上將`true`屬性設定為。  
  
 您也可以藉由衍生自<xref:System.Windows.Controls.ValidationRule>類別並<xref:System.Windows.Controls.ValidationRule.Validate%2A>執行方法, 來建立自己的驗證規則。 下列範例顯示<xref:System.Windows.Controls.TextBox>從[什麼是資料系結？](#what_is_data_binding)一節中, 新增*產品清單*「開始日期」所使用的規則:  
  
 [!code-csharp[DataBindingLab#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 StartDateEntryForm<xref:System.Windows.Controls.TextBox>會使用此*FutureDateRule*, 如下列範例所示:  
  
 [!code-xaml[DataBindingLab#CustomValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 請注意, 由於<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值為<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, 系結引擎會更新每個擊鍵的來源值, 這表示它也會檢查每個<xref:System.Windows.Data.Binding.ValidationRules%2A>擊鍵的集合中的每個規則。 我們將在＜驗證程序＞一節進一步討論這個部分。  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>提供視覺化回應  
 如果使用者輸入無效值，您可能會想要在應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 中提供一些關於錯誤的回應。 提供這類意見反應的其中一種方式<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> , 就是將附加<xref:System.Windows.Controls.ControlTemplate>屬性設定為自訂。 如上一節所示, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox>會使用<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>稱為*validationTemplate*。 下列範例顯示 *validationTemplate* 的定義：  
  
 [!code-xaml[DataBindingLab#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder>元素會指定要裝飾之控制項的放置位置。  
  
 此外, 您也可以使用<xref:System.Windows.Controls.ToolTip>來顯示錯誤訊息。 *StartDateEntryForm*和*StartPriceEntryForm* <xref:System.Windows.Controls.TextBox>es 都會使用<xref:System.Windows.Controls.ToolTip> style *textStyleTextBox*, 它會建立顯示錯誤訊息的。 下列範例顯示 *textStyleTextBox* 的定義。 當繫結項目<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>之`true`屬性的一個或多個系結髮生錯誤時, 附加屬性為。  
  
 [!code-xaml[DataBindingLab#14](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 使用自訂<xref:System.Windows.Controls.Validation.ErrorTemplate%2A> <xref:System.Windows.Controls.ToolTip>和, 當發生驗證錯誤時, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox>看起來會像下面這樣:  
  
 ![資料繫結驗證錯誤](./media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 如果您<xref:System.Windows.Data.Binding>有相關聯的驗證規則, 但未在<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>繫結控制項上指定, 則會<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>在發生驗證錯誤時, 使用預設值來通知使用者。 預設值<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>是在裝飾項圖層中定義紅色框線的控制項範本。 使用預設值<xref:System.Windows.Controls.Validation.ErrorTemplate%2A> <xref:System.Windows.Controls.ToolTip>和時, 如果[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]發生驗證錯誤, 則*StartPriceEntryForm* <xref:System.Windows.Controls.TextBox>的會如下所示:  
  
 ![資料繫結驗證錯誤](./media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 如需如何提供邏輯以驗證對話方塊中所有控制項的範例，請參閱[對話方塊概觀](../app-development/dialog-boxes-overview.md)中的＜自訂對話方塊＞一節。  
  
### <a name="validation-process"></a>驗證程序  
 通常驗證發生的時機，是將目標的值傳輸到繫結來源屬性的時候。 這會發生<xref:System.Windows.Data.BindingMode.TwoWay>在<xref:System.Windows.Data.BindingMode.OneWayToSource>和系結上。 再次重申, 會造成來源更新相依于<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性的值, 如[觸發程式來源更新](#what_triggers_source_updates)一節中所述。  
  
 以下描述「驗證」程序。 請注意，如果在此程序執行期間發生驗證錯誤或其他型別錯誤，程序就會中止。  
  
1. 系結引擎會檢查是否有任何定義<xref:System.Windows.Controls.ValidationRule>的自訂<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>物件, 其<xref:System.Windows.Controls.ValidationStep.RawProposedValue>已設定為, 在此情況下, <xref:System.Windows.Controls.ValidationRule.Validate%2A>它會在<xref:System.Windows.Controls.ValidationRule>每個上呼叫方法, 直到其中一個發生錯誤為止。 <xref:System.Windows.Data.Binding>或直到全部通過為止。  
  
2. 接著，繫結引擎就會在有轉換器的情況下呼叫轉換器。  
  
3. 如果轉換器成功, 系結引擎會檢查是否有<xref:System.Windows.Controls.ValidationRule>任何定義<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationRule.Validate%2A>的<xref:System.Windows.Data.Binding>自訂物件, 其已<xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue>將設定為, 在此情況下, 它會在<xref:System.Windows.Controls.ValidationRule>具有下列條件的每個上呼叫方法:將設定<xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue>為, 直到其中一個錯誤發生, 或直到全部通過為止。 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>  
  
4. 繫結引擎會設定來源屬性。  
  
5. 系結引擎會檢查是否有任何定義<xref:System.Windows.Controls.ValidationRule>的自訂<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>物件<xref:System.Windows.Data.Binding>, 其<xref:System.Windows.Controls.ValidationStep.UpdatedValue>已設定為, 在此情況下, <xref:System.Windows.Controls.ValidationRule.Validate%2A>它會在<xref:System.Windows.Controls.ValidationRule>已<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>設定為的每個上呼叫方法。<xref:System.Windows.Controls.ValidationStep.UpdatedValue>直到其中一個錯誤發生, 或直到全部通過為止。 如果與系結相關聯, 而且其<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>設定為預設值, <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Controls.DataErrorValidationRule>則會在此時檢查。 <xref:System.Windows.Controls.DataErrorValidationRule> 這也是檢查已<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>設定為`true`之系結的時間點。  
  
6. 系結引擎會檢查是否有任何定義<xref:System.Windows.Controls.ValidationRule>的自訂<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>物件<xref:System.Windows.Data.Binding>, 其<xref:System.Windows.Controls.ValidationStep.CommittedValue>已設定為, 在此情況下, <xref:System.Windows.Controls.ValidationRule.Validate%2A>它會在<xref:System.Windows.Controls.ValidationRule>已<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>設定為的每個上呼叫方法。<xref:System.Windows.Controls.ValidationStep.CommittedValue>直到其中一個錯誤發生, 或直到全部通過為止。  
  
 如果在整個過程中都不<xref:System.Windows.Controls.ValidationError> <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 會傳遞,系結引擎會建立物件,並將它加入至綁定<xref:System.Windows.Controls.ValidationRule>項的集合。 在系結引擎于任何<xref:System.Windows.Controls.ValidationRule>指定的步驟執行物件之前, 它會<xref:System.Windows.Controls.ValidationError>移除在該步驟期間<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>加入繫結項目之附加屬性中的任何。 例如<xref:System.Windows.Controls.ValidationRule> , 如果將其<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>設定為<xref:System.Windows.Controls.ValidationStep.UpdatedValue>失敗, 則在下一次進行驗證程式時, 系結引擎會在<xref:System.Windows.Controls.ValidationError>呼叫任何<xref:System.Windows.Controls.ValidationRule>已<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>設定為的之前, 立即移除該進程<xref:System.Windows.Controls.ValidationStep.UpdatedValue>。  
  
 當<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>不是空的時<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> , 元素的附加屬性會設定為`true`。 此外, 如果<xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>的屬性<xref:System.Windows.Data.Binding>設定為`true`, 則系結引擎會在元素上引發<xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType>附加事件。  
  
 另請注意, 任一方向的有效值傳輸 (目標至來源或來源至目標) 都會清除<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>附加屬性。  
  
 如果系結具有與它<xref:System.Windows.Controls.ExceptionValidationRule>相關聯的, 或<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>屬性設定為`true` , 而且當系結引擎設定來源時擲回例外狀況, 則系結<xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>引擎會檢查是否有。 您可以選擇使用<xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>回呼來提供處理例外狀況的自訂處理常式。 如果未<xref:System.Windows.Controls.ValidationError> <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>在上指定<xref:System.Windows.Data.Binding>, 系結引擎會建立具有例外狀況的,並將它新增至綁定<xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>項的集合。  
  
## <a name="debugging-mechanism"></a>偵錯機制  
 您可以在系結相關<xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType>物件上設定附加屬性, 以接收特定系結狀態的相關資訊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [WPF 第 4.5 版的新功能](../getting-started/whats-new.md)
- [繫結至 LINQ 查詢的結果](how-to-bind-to-the-results-of-a-linq-query.md)
- [資料繫結](../advanced/optimizing-performance-data-binding.md)
- [資料系結示範](https://go.microsoft.com/fwlink/?LinkID=163703)
- [HOW-TO 主題](data-binding-how-to-topics.md)
- [繫結至 ADO.NET 資料來源](how-to-bind-to-an-ado-net-data-source.md)
