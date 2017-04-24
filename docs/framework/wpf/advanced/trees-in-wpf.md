---
title: "WPF 中的樹狀結構 | Microsoft Docs"
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
  - "項目樹狀結構"
  - "邏輯樹狀結構"
  - "視覺化樹狀結構"
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# WPF 中的樹狀結構
在許多技術中，項目和元件都會組織成樹狀結構，開發人員可直接操作樹狀結構中的物件節點來影響應用程式的轉譯或行為。  此外，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 還會使用數個樹狀結構比喻來定義程式項目之間的關係。  在大部分情形下，WPF 開發人員在概念上思考物件樹狀結構比喻時，可以使用程式碼建立應用程式或使用 XAML 定義應用程式的部分，但在進行這些作業時將會呼叫特定 API 或使用特定標記，而不是進行某些一般的物件樹狀結構管理 API，就像您在 XML DOM 中可能會使用的方式。  WPF 有公開 \(Expose\) 兩種用於提供樹狀結構比喻檢視的協助程式類別：<xref:System.Windows.LogicalTreeHelper> 和 <xref:System.Windows.Media.VisualTreeHelper>。  在 WPF 說明文件中也會使用視覺化樹狀結構和邏輯樹狀結構這兩個用語，因為這些樹狀結構在了解某些 WPF 的主要功能時是非常好用的。  本主題會定義視覺化樹狀結構和邏輯樹狀結構的代表意義、討論樹狀結構與整體物件樹狀結構概念的關聯性，並介紹 <xref:System.Windows.LogicalTreeHelper> 和 <xref:System.Windows.Media.VisualTreeHelper>。  
  
   
  
<a name="element_tree"></a>   
## WPF 中的樹狀結構  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中最完整的樹狀結構就是物件樹狀結構。  如果您以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 定義應用程式頁面，然後再載入該 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，則會依據標記中項目的巢狀關係來建立樹狀結構。  如果您是以程式碼建立應用程式或應用程式的一部分，則會依據您針對用於實作指定物件之內容模型的屬性之屬性值指派方式來建立樹狀結構。  在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，完整物件樹狀結構的概念化以及報告給其公用 API 的方式有兩種：做為邏輯樹狀結構以及做為視覺化樹狀結構。  邏輯樹狀結構與視覺化樹狀結構的差異並不一定都很重要，但有時可能會導致 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 某些子系統發生問題，並影響您對於使用標記或程式碼編寫程式的選擇。  
  
 即使您不一定會直接管理邏輯樹狀結構或視覺化樹狀結構，了解這些樹狀結構的互動方式，將有助於對 WPF 這種技術的認識。  將 WPF 比喻為某種樹狀結構，能有助於了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中屬性繼承和事件路由的運作方式。  
  
> [!NOTE]
>  因為物件樹狀結構比較接近是個概念而非實際的 API，所以另一個想像這個概念的方式是物件圖形 \(Object Graph\)。  實際上，物件間的關聯性在執行階段時，可能會讓樹狀結構比喻失效。  然而，特別是對以 XAML 定義的 UI 而言，樹狀結構比喻仍算是恰當，因此絕大部分的 WPF 說明文件在提及這個一般概念時，都會採用物件樹狀結構一詞來描述。  
  
<a name="logical_tree"></a>   
## 邏輯樹狀結構  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，您可以為 UI 項目 \(Element\) 加入內容，方法是藉由為支援這些項目 \(Element\) 的物件設定屬性。  例如，您可以操作 <xref:System.Windows.Controls.ItemsControl.Items%2A> 屬性，將項目 \(Item\) 加入到 <xref:System.Windows.Controls.ListBox> 控制項。  這麼做是將項目 \(Item\) 置於做為 <xref:System.Windows.Controls.ItemsControl.Items%2A> 屬性值的 <xref:System.Windows.Controls.ItemCollection> 中。  同樣地，若要將物件加入到 <xref:System.Windows.Controls.DockPanel> 中，您要操作其 <xref:System.Windows.Controls.Panel.Children%2A> 屬性值。  在這裡，您是將物件加入到 <xref:System.Windows.Controls.UIElementCollection> 中。  如需程式碼範例，請參閱[Add an Element Dynamically](http://msdn.microsoft.com/zh-tw/d00f258a-7973-4de7-bc54-a3fc1f638419)。  
  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，當您將清單項目 \(Item\) 置於 <xref:System.Windows.Controls.ListBox>，或者是將控制項或其他項目 \(Element\) 置於 <xref:System.Windows.Controls.DockPanel> 時，您也會明確或隱含使用 <xref:System.Windows.Controls.ItemsControl.Items%2A> 和 <xref:System.Windows.Controls.Panel.Children%2A> 屬性，如下列範例所示。  
  
 [!code-xml[TreeOvwsSupport#AllCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 如果您原本是要處理這個 XAML 做為文件物件模型下的 XML，而且您已經包含註解為隱含的標記 \(Tag\)\(這應該已合法\)，則產生的 XML DOM 樹狀結構應該已包含 `<ListBox.Items>` 的項目 \(Element\) 以及其他隱含項目 \(Item\)。  但是當您讀取標記 \(Markup\) 和寫入物件時，XAML 不會以這種方式處理，所產生的物件圖形不會逐字包含 `ListBox.Items`。  然而，它確實會具有名為 `Items` 的 <xref:System.Windows.Controls.ListBox> 屬性，其中包含 <xref:System.Windows.Controls.ItemCollection>，並且在處理 <xref:System.Windows.Controls.ListBox> XAML 時會初始化 <xref:System.Windows.Controls.ItemCollection> 但其為空白。  然後，剖析器會呼叫 `ItemCollection.Add`，將每個做為 <xref:System.Windows.Controls.ListBox> 內容的子物件項目 \(Element\) 加入到 <xref:System.Windows.Controls.ItemCollection>。  目前為止，這個將 XAML 處理到物件樹狀結構中的範例，看起來很像所建立物件樹狀結構基本上是邏輯樹狀結構的範例。  
  
 然而，即使將 XAML 隱含語法項目 \(Item\) 的因子拿掉，邏輯樹狀結構並不是您執行階段應用程式 UI 在的完整物件圖形。  主要的原因是這是視覺化項目 \(Visuals\) 和範本。  例如，請考慮 <xref:System.Windows.Controls.Button>。  邏輯樹狀結構中會報告 <xref:System.Windows.Controls.Button> 物件還有其字串 `Content`。  但是在執行階段物件樹狀結構中，這個按鈕還有更多的資訊。  特別是，按鈕只會以其特定的方式出現在畫面上，這是因為有套用特定的 <xref:System.Windows.Controls.Button> 控制項範本。  來自於套用範本的視覺化項目 \(例如由範本定義的 <xref:System.Windows.Controls.Border>，即視覺化按鈕周圍的深灰色框線\) 就不會在邏輯樹狀結構中報告出來，即使您是在執行階段查看邏輯樹狀結構 \(例如處理視覺化 UI 的輸入事件，然後再讀取邏輯樹狀結構時\)。  為了要找出範本視覺化項目，您應該改為檢視視覺化樹狀結構。  
  
 如需 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法與所建立物件圖形的對應方式以及 XAML 隱含語法的詳細資訊，請參閱 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)或 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
<a name="tree_property_inheritance_event_routing"></a>   
### 邏輯樹狀結構的用途  
 邏輯樹狀結構的存在，是要讓內容模型可立即逐一查看其可能的子物件，並使內容模型得以延伸。  再者，邏輯樹狀結構也可提供進行某些通知的架構，例如當邏輯樹狀結構中的所有物件都載入完畢時。  基本上，邏輯樹狀結構近似於架構層級的執行階段物件圖形，其中會排除視覺化項目，但足以對您自己的執行階段應用程式組合進行許多查詢作業。  
  
 除此之外，藉由針對初始要求物件向上查看 <xref:System.Windows.FrameworkElement.Resources%2A> 集合的邏輯樹狀結構，然後再沿著邏輯樹狀結構繼續往上檢查每個 <xref:System.Windows.FrameworkElement> \(或 <xref:System.Windows.FrameworkContentElement>\) 尋找包含 <xref:System.Windows.ResourceDictionary> 並可能包含該索引鍵的另一個 `Resources` 值，即可以同時解析靜態和動態資源參考。  當邏輯樹狀結構和視覺化樹狀結構同時存在時，資源查閱作業會使用邏輯樹狀結構。  如需資源字典和查閱的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
<a name="composition"></a>   
### 邏輯樹狀結構的組合  
 邏輯樹狀結構是在 [WPF 架構層級](GTMT)定義的，這表示與邏輯樹狀結構作業最為相關的 WPF 基底項目不是 <xref:System.Windows.FrameworkElement> 就是 <xref:System.Windows.FrameworkContentElement>。  然而，如您所見，如果您實際使用 <xref:System.Windows.LogicalTreeHelper> API，邏輯樹狀結構有時候包含的節點既不是 <xref:System.Windows.FrameworkElement>，也不是 <xref:System.Windows.FrameworkContentElement>。  例如，邏輯樹狀結構所報告的 <xref:System.Windows.Controls.TextBlock> 之 <xref:System.Windows.Controls.TextBlock.Text%2A> 值，就是個字串。  
  
<a name="override_logical_tree"></a>   
### 覆寫邏輯樹狀結構  
 資深控制項作者可以藉由覆寫數個用來定義一般物件或內容模型如何在邏輯樹狀結構內加入或移除物件的 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，覆寫邏輯樹狀結構。  如需如何覆寫邏輯樹狀結構的範例，請參閱 [覆寫邏輯樹狀結構](../../../../docs/framework/wpf/advanced/how-to-override-the-logical-tree.md)。  
  
<a name="pvi"></a>   
### 屬性值繼承  
 屬性值繼承作業會透過混合樹狀結構進行。  包含啟用屬性繼承之 <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> 屬性的實際中繼資料，就是 [WPF 架構層級](GTMT) <xref:System.Windows.FrameworkPropertyMetadata> 類別。  因此，存放原始值的父物件和繼承該值的子物件必須都是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>，而且必須都屬於某個邏輯樹狀結構的一部分。  不過，對於支援屬性繼承的現有 WPF 屬性而言，透過不在邏輯樹狀結構中的中間物件，屬性值的繼承便可以永遠存在。  主要是因為這與讓範本項目使用任何繼承屬性值有關，其中這些值是針對套用範本的執行個體而設定，或是在更高頁面層級的組合中設定的，繼而在樹狀結構中的更高層設定的。  為了使屬性值繼承能夠跨這類界限一致地運作，繼承的屬性必須註冊為附加屬性，而如果您想要以屬性繼承行為定義自訂的相依性屬性，則必須遵循這個模式。  Helper 類別公用程式方法完全無法預期屬性繼承所使用的樹狀結構，即使在執行階段也一樣。  如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
<a name="two_trees"></a>   
## 視覺化樹狀結構  
 除了邏輯樹狀結構的概念，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中還有[視覺化樹狀結構](GTMT)的概念。  視覺化樹狀結構會描述視覺化物件的結構，就如 <xref:System.Windows.Media.Visual> 基底類別所表示。  當您撰寫控制項的樣板時，就是在定義或重新定義適用於該控制項的視覺化樹狀結構。  視覺化樹狀結構也可讓開發人員對繪製作業採取低階控制，以改善效能和進行最佳化。  通常 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式在開發時，公開視覺化樹狀結構的一種方式，就是[路由事件](GTMT)的事件在路由時大多沿著視覺化樹狀結構前進，而非邏輯樹狀結構。  除非是控制項作者，否則並不容易立即察覺到此路由事件行為的細微差別。  透過視覺化樹狀結構進行路由事件，就可以讓在視覺化層級中實作組合的控制項處理事件或建立事件 setter。  
  
<a name="trees_content"></a>   
## 樹狀結構、內容項目和內容裝載  
 內容項目 \(衍生自 <xref:System.Windows.ContentElement> 的類別\) 不屬於視覺化樹狀結構的一部分，它們不是繼承自 <xref:System.Windows.Media.Visual>，也沒有視覺化表示。  為了能確實在 UI 中出現，<xref:System.Windows.ContentElement> 必須裝載於同時是 <xref:System.Windows.Media.Visual> 和邏輯樹狀結構項目的內容裝載 \(Content Host\)。  通常這類的物件是 <xref:System.Windows.FrameworkElement>。  您可以將內容裝載想像成內容的「瀏覽器」，並選擇該內容要如何顯示在裝載著控制項的螢幕區域內。  當裝載好內容時，該內容就可以成為某些樹狀結構處理序 \(通常與視覺化樹狀結構相關聯\) 中的參與者。  一般而言，<xref:System.Windows.FrameworkElement> 裝載類別包含實作程式碼，此實作程式碼會透過內容邏輯樹狀結構的子節點，將任何裝載的 <xref:System.Windows.ContentElement> 加入到事件路由，即使裝載的內容不屬於實際視覺化樹狀結構的一部分。  這是必要的，<xref:System.Windows.ContentElement> 才能獲得路由至本身以外任何項目的路由事件。  
  
<a name="tree_traversal"></a>   
## 樹狀結構周遊  
 <xref:System.Windows.LogicalTreeHelper> 類別提供 <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>、<xref:System.Windows.LogicalTreeHelper.GetParent%2A> 和 <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> 方法來周遊邏輯樹狀結構。  大部分情況下，您應該不需要周遊現有控制項的邏輯樹狀結構，因為這些控制項幾乎都會將其邏輯子項目公開為專用的集合屬性，以支援集合存取，例如 `Add`、索引子等等。  樹狀結構周遊功能主要適用於兩種控制項作者使用：選擇不從適用的控制項模式衍生 \(例如 <xref:System.Windows.Controls.ItemsControl> 或 <xref:System.Windows.Controls.Panel> 等已經定義集合屬性\) 的控制項作者，或者想要提供自己之集合屬性支援的控制項作者。  
  
 視覺化樹狀結構也支援進行視覺化樹狀結構周遊的 Helper 類別 <xref:System.Windows.Media.VisualTreeHelper>。  由於視覺化樹狀結構無法方便地透過控制項特定屬性公開，如在程式設計時有必要，建議使用 <xref:System.Windows.Media.VisualTreeHelper> 類別周遊視覺化樹狀結構。  如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。  
  
> [!NOTE]
>  有時候必須檢查所套用範本的視覺化樹狀結構。  當您使用這種技巧時應該要很小心。  即使您是在定義範本之控制項的視覺化樹狀結構中周遊，控制項的消費者一定可以藉由對執行個體設定 <xref:System.Windows.Controls.Control.Template%2A> 屬性而變更範本，甚至使用者也可以藉由變更系統佈景主題而影響到套用的範本。  
  
<a name="routes"></a>   
## 路由事件的樹狀結構路由  
 如前所述，任何指定路由事件的路由是在樹狀結構中沿著預先決定的單一路徑周遊，其中該樹狀結構是視覺化樹狀結構和邏輯樹狀結構表示的混合。  依據事件路由為通道 \(Tunneling\) 或反昇 \(Bubbling\) 路由事件而定，其會在樹狀結構內向上或向下行進。  事件路由概念沒有直接支援的 Helper 類別可供在事件路由上「前進」，而不管是否引發實際路由的事件。  有個類別可代表路徑：<xref:System.Windows.EventRoute>，但此類別的方法一般僅供內部使用。  
  
<a name="resourcesandtrees"></a>   
## 資源字典和樹狀結構  
 對於頁面中定義的所有 `Resources` 的資源字典查閱，基本上會周遊其邏輯樹狀結構。  不在邏輯樹狀結構的物件可以參考具有索引鍵的資源，但資源查閱序列是從物件連接到邏輯樹狀結構的點開始。  在 WPF 中，只有邏輯樹狀結構節點才可以有包含 <xref:System.Windows.ResourceDictionary> 的 `Resources` 屬性，因此周遊視覺化樹狀結構以尋找來自 <xref:System.Windows.ResourceDictionary> 的具索引鍵資源並無任何好處。  
  
 不過，資源查閱也可延伸至目前邏輯樹狀結構以外的地方。  對於應用程式標記，資源查閱可以接著繼續尋找應用程式層級的資源字典，然後是做為靜態屬性或索引鍵來參考的佈景主題支援和系統值。  如果資源參考是動態的，則佈景主題本身也可以參考佈景主題邏輯樹狀結構以外的系統值。  如需資源字典和查閱邏輯的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
## 請參閱  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [初始化物件樹狀結構以外的物件項目](../../../../docs/framework/wpf/advanced/initialization-for-object-elements-not-in-an-object-tree.md)   
 [WPF 架構](../../../../docs/framework/wpf/advanced/wpf-architecture.md)