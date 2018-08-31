---
title: WPF 中的樹狀結構
ms.date: 03/30/2017
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
ms.openlocfilehash: e6173916ad64a60d3727b5d35bb2a2302b881b38
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332805"
---
# <a name="trees-in-wpf"></a>WPF 中的樹狀結構
在許多技術中，元素和元件都會組織成樹狀結構，開發人員可直接管理樹狀結構中的物件節點來影響應用程式的轉譯或行為。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 也會使用數個樹狀結構比喻來定義程式元素之間的關聯性。 在大部分情形下，WPF 開發人員在概念上思考物件樹狀結構比喻時，可以使用程式碼建立應用程式或使用 XAML 定義應用程式的部分，但將會呼叫特定的 API 或使用特定標記來進行這些作業，而不是使用某些一般的物件樹狀結構管理 API，就像您可能在 XML DOM 中使用的方式。 WPF 會公開兩個協助程式類別提供樹狀結構比喻檢視<xref:System.Windows.LogicalTreeHelper>和<xref:System.Windows.Media.VisualTreeHelper>。 WPF 文件中也會使用視覺化樹狀結構和邏輯樹狀結構等詞彙，因為這些相同的樹狀結構在了解某些主要的 WPF 功能時非常好用。 本主題定義代表什麼意義的視覺化樹狀結構和邏輯樹狀結構、 討論這類樹狀結構與整體的物件樹狀結構概念，並介紹<xref:System.Windows.LogicalTreeHelper>和<xref:System.Windows.Media.VisualTreeHelper>s。  
  

  
<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>WPF 中的樹狀結構  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中最完整的樹狀結構就是物件樹狀結構。 如果您以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 定義應用程式頁面，然後載入 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，則會依據標記中元素的巢狀關聯性來建立樹狀結構。 如果您利用程式碼定義應用程式或應用程式的一部分，則會依據下列方式來建立樹狀結構：您如何針對用於實作指定物件之內容模型的屬性指派屬性值。 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，將完整的物件樹狀結構概念化並可回報給其公用 API 的方式有兩種：當做邏輯樹狀結構，以及當做視覺化樹狀結構。 邏輯樹狀結構與視覺化樹狀結構之間的差異不一定很重要，但有時可能會導致某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 子系統發生問題，並影響您對於使用標記或程式碼的選擇。  
  
 即使您不一定會直接管理邏輯樹狀結構或視覺化樹狀結構，但了解這些樹狀結構的互動方式，將有助於對 WPF 這種技術的認識。 將 WPF 比喻為某種樹狀結構，對於了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中屬性繼承和事件路由的運作方式也很重要。  
  
> [!NOTE]
>  因為物件樹狀結構比較接近是個概念而非實際的 API，所以另一種想像這個概念的方式是當成物件圖形。 實際上，物件之間的關聯性在執行階段，可能會讓樹狀結構比喻失效。 不過，特別是對以 XAML 定義的 UI 而言，樹狀結構比喻仍算是恰當，因此大部分的 WPF 文件在提及這個一般概念時，將會使用物件樹狀結構一詞。  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>邏輯樹狀結構  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，您要將內容加入至 UI 元素，方法則是為支援這些元素的物件設定屬性。 例如，您將項目加入<xref:System.Windows.Controls.ListBox>藉由操作的控制項及其<xref:System.Windows.Controls.ItemsControl.Items%2A>屬性。 如此一來，您會將項目置於<xref:System.Windows.Controls.ItemCollection>也就是<xref:System.Windows.Controls.ItemsControl.Items%2A>屬性值。 同樣地，將物件加入<xref:System.Windows.Controls.DockPanel>，您操作其<xref:System.Windows.Controls.Panel.Children%2A>屬性值。 在這裡，您會將物件新增至<xref:System.Windows.Controls.UIElementCollection>。 如需程式碼範例，請參閱[以動態方式加入元素](https://msdn.microsoft.com/library/d00f258a-7973-4de7-bc54-a3fc1f638419)。  
  
 中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，當您將清單中的項目<xref:System.Windows.Controls.ListBox>控制項或其他 UI 元素置於<xref:System.Windows.Controls.DockPanel>，您也使用<xref:System.Windows.Controls.ItemsControl.Items%2A>和<xref:System.Windows.Controls.Panel.Children%2A>屬性，明確或隱含，如下列範例所示。  
  
 [!code-xaml[TreeOvwsSupport#AllCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 如果您原本要處理這個 XAML 做為文件物件模型下的 XML，而且已包含註解化為隱含的標記 (這應該已合法)，則產生的 XML DOM 樹狀結構應該已包含 `<ListBox.Items>` 的元素及其他隱含項目。 但是當您讀取標記並寫入至物件時，XAML 不會以該方式處理，因此，產生的物件圖形實際上不會包含 `ListBox.Items`。 不過沒有<xref:System.Windows.Controls.ListBox>名為屬性`Items`，其中包含<xref:System.Windows.Controls.ItemCollection>，且<xref:System.Windows.Controls.ItemCollection>已初始化但其為空白時<xref:System.Windows.Controls.ListBox>處理 XAML 時。 然後，每個子物件項目作為內容存在於<xref:System.Windows.Controls.ListBox>新增至<xref:System.Windows.Controls.ItemCollection>藉由剖析器呼叫`ItemCollection.Add`。 目前為止，這個將 XAML 處理到物件樹狀結構中的範例，看起來很像所建立物件樹狀結構基本上是邏輯樹狀結構的範例。  
  
 不過，即使去除 XAML 隱含語法項目的因素，邏輯樹狀結構並不是會在執行階段針對應用程式 UI 存在的完整物件圖形。針對這點的主要原因是視覺效果和範本。 例如，假設<xref:System.Windows.Controls.Button>。 邏輯樹狀結構的報表<xref:System.Windows.Controls.Button>物件以及其字串`Content`。 但在執行階段的物件樹狀結構中，還有更多關於此按鈕的資訊。 特別是，按鈕才會出現在畫面上的方式，是因為會在特定<xref:System.Windows.Controls.Button>套用控制項範本。 來自已套用範本的視覺效果 (例如範本定義<xref:System.Windows.Controls.Border>位於視覺化按鈕周圍深灰色框線) 不會報告在邏輯樹狀結構中，即使您在執行階段查看邏輯樹狀結構 (例如處理的輸入的事件顯示 UI，然後讀取邏輯樹狀結構）。 若要尋找範本視覺效果，您需要改為檢查視覺化樹狀結構。  
  
 如需 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法與所建立物件圖形的對應方式以及 XAML 中隱含語法的詳細資訊，請參閱 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)或 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>邏輯樹狀結構的用途  
 邏輯樹狀結構的存在，是要讓內容模型可立即逐一查看其可能的子物件，並使內容模型得以延伸。 此外，邏輯樹狀結構也可提供某些通知適用的架構，例如，載入邏輯樹狀結構中的所有物件時。 基本上，邏輯樹狀結構近似於架構層級的執行階段物件圖形，其會排除視覺效果，但足以對您自己的執行階段應用程式組合進行許多查詢作業。  
  
 此外，將這兩個靜態和動態資源參考解析透過向上查看邏輯樹狀結構<xref:System.Windows.FrameworkElement.Resources%2A>上初始要求的物件，然後繼續在邏輯樹狀結構並檢查每個集合<xref:System.Windows.FrameworkElement>（或<xref:System.Windows.FrameworkContentElement>)另外`Resources`值，其中包含<xref:System.Windows.ResourceDictionary>，可能包含該索引鍵。 當邏輯樹狀結構和視覺化樹狀結構同時存在時，資源查閱會使用邏輯樹狀結構。 如需資源字典和查閱的詳細資訊，請參閱 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>邏輯樹狀結構的組合  
 邏輯樹狀結構定義於 WPF 架構層級，這表示，邏輯樹狀結構作業最相關的 WPF 基底項目是<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。 不過，您可以看到是否您實際使用<xref:System.Windows.LogicalTreeHelper>API，邏輯樹狀結構有時包含的節點，不是單選題<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。 比方說，邏輯樹狀結構會報告<xref:System.Windows.Controls.TextBlock.Text%2A>的值<xref:System.Windows.Controls.TextBlock>，這是字串。  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>覆寫邏輯樹狀結構  
 資深的控制項作者可藉由覆寫數個用來定義一般物件或內容模型如何在邏輯樹狀結構內加入或移除物件的 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，來覆寫邏輯樹狀結構。 如需如何覆寫邏輯樹狀結構的範例，請參閱[覆寫邏輯樹狀結構](../../../../docs/framework/wpf/advanced/how-to-override-the-logical-tree.md)。  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>屬性值繼承  
 屬性值繼承會透過混合式樹狀結構來進行。 包含的實際中繼資料<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>啟用屬性繼承的屬性是 WPF 架構層級<xref:System.Windows.FrameworkPropertyMetadata>類別。 因此，同時保留原始值的父代和子物件繼承該值必須同時<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>，而且必須是某個邏輯樹狀結構的一部分。 不過，對於支援屬性繼承的現有 WPF 屬性而言，透過不在邏輯樹狀結構中的中間物件，屬性值繼承便能永遠存在。 主要是因為這與讓範本元素使用任何繼承屬性值有關，這些值是設定於套用範本的執行個體上，或設定於比頁面層級組合還要更高的層級中，因而在邏輯樹狀結構中會比較高。 為了使屬性值繼承能夠跨這類界限一致地運作，必須將繼承屬性註冊為附加屬性，而如果您想要利用屬性繼承行為來定義自訂的相依性屬性，則必須遵循這個模式。 Helper 類別公用程式方法完全無法預期屬性繼承所使用的實際樹狀結構，即使在執行階段也一樣。 如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>視覺化樹狀結構  
 除了邏輯樹狀結構的概念，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中還有視覺化樹狀結構的概念。 視覺化樹狀結構描述的視覺物件，結構，表示的<xref:System.Windows.Media.Visual>基底類別。 當您撰寫控制項的範本時，就是在定義或重新定義適用於該控制項的視覺化樹狀結構。 視覺化樹狀結構也可引起開發人員的關注，讓想要對繪製作業採取低階控制的開發人員，能夠改善效能並進行最佳化。 通常在進行 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式程式設計時，公開視覺化樹狀結構的方式之一，就是路由事件的事件在路由傳送時大多會沿著視覺化樹狀結構進行周遊，而非邏輯樹狀結構。 除非您是控制項作者，否則不容易立即察覺到此路由事件行為的細微差異。 透過視覺化樹狀結構路由傳送事件，就能讓在視覺化層級中實作組合的控制項處理事件或建立事件 setter。  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>樹狀結構、內容項目元素及內容主機  
 內容項目 (衍生自類別<xref:System.Windows.ContentElement>) 不是視覺化樹狀結構的一部分; 它們不是繼承自<xref:System.Windows.Media.Visual>並沒有視覺表示法。 為了能確實出現在 UI 中，<xref:System.Windows.ContentElement>必須是兩者的內容主機中裝載<xref:System.Windows.Media.Visual>和邏輯樹狀結構參與者。 這類物件通常是<xref:System.Windows.FrameworkElement>。 您可以將內容主機想像成某些像是內容「瀏覽器」的項目，並選擇如何在主機控制的螢幕區域內顯示該內容。 裝載內容之後，該內容就可成為某些樹狀結構處理序 (通常會與視覺化樹狀結構相關聯) 中的參與者。 一般而言，<xref:System.Windows.FrameworkElement>裝載類別包含實作程式碼，將任何裝載<xref:System.Windows.ContentElement>透過內容邏輯樹狀結構的子節點的事件路由，即使裝載的內容不是，則為 true 的視覺化樹狀結構的一部分。 這是必要的讓<xref:System.Windows.ContentElement>可路由傳送至本身以外的任何項目路由的事件資料來源。  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>樹狀周遊  
 <xref:System.Windows.LogicalTreeHelper>類別會提供<xref:System.Windows.LogicalTreeHelper.GetChildren%2A>， <xref:System.Windows.LogicalTreeHelper.GetParent%2A>，和<xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A>周遊邏輯樹狀結構的方法。 在大部分情況下，您應該不需要周遊現有控制項的邏輯樹狀結構，因為這些控制項幾乎都會將其邏輯子元素公開為專用的集合屬性，以支援集合存取，例如 `Add`、索引子等等。 樹狀周遊是主要的案例，以供選擇不要將這類衍生自適用的控制項模式的控制項作者<xref:System.Windows.Controls.ItemsControl>或<xref:System.Windows.Controls.Panel>其中已經定義集合屬性，以及想要提供自己的集合屬性的支援。  
  
 視覺化樹狀結構也支援視覺化樹狀結構周遊的 helper 類別<xref:System.Windows.Media.VisualTreeHelper>。 視覺化樹狀結構不會公開為方便地透過控制項特定屬性，因此<xref:System.Windows.Media.VisualTreeHelper>類別是周遊視覺化樹狀結構，如果是您的程式設計案例所需的建議的方式。 如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。  
  
> [!NOTE]
>  有時必須檢查所套用範本的視覺化樹狀結構。 您應該謹慎使用此技術。 即使您周遊的視覺化樹狀結構的控制項，您在其中定義範本，您的控制項的取用者永遠可以變更範本藉由設定<xref:System.Windows.Controls.Control.Template%2A>屬性執行個體，以及甚至使用者也可以藉由變更會影響套用的範本系統佈景主題。  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>路由事件的樹狀結構路由  
 如前所述，任何指定路由事件的路由是在樹狀結構中沿著預先決定的單一路徑來周遊，該樹狀結構是視覺化樹狀結構和邏輯樹狀結構表示法的混合。 依據事件路由為通道或事件反昇的路由事件而定，其會在樹狀結構內向上或向下進行周遊。 事件路由概念沒有直接支援的 Helper 類別可用來在事件路由上「前進」，而不管是否會引發實際路由傳送的事件。 為代表路由的類別<xref:System.Windows.EventRoute>，但該類別的方法通常僅供內部使用。  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>資源字典和樹狀目錄  
 對於頁面中定義的所有 `Resources` 的資源字典查閱，基本上會周遊邏輯樹狀結構。 不在邏輯樹狀結構中的物件可以參考具有索引鍵的資源，但資源查閱序列是從物件連接到邏輯樹狀結構的點開始。 在 WPF 中，只有邏輯樹狀結構節點可以有`Resources`屬性，其中包含<xref:System.Windows.ResourceDictionary>，因此沒有任何好處中周遊視覺化樹狀結構以尋找索引鍵的資源，從<xref:System.Windows.ResourceDictionary>。  
  
 不過，資源查閱也可以延伸至目前邏輯樹狀結構以外的地方。 對於應用程式標記，資源查閱可接著繼續前進到應用程式層級的資源字典，然後到做為靜態屬性或索引鍵加以參考的佈景主題支援和系統值。 如果資源參考是動態的，則佈景主題本身也可以參考佈景主題邏輯樹狀結構以外的系統值。 如需資源字典和查閱邏輯的詳細資訊，請參閱 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
## <a name="see-also"></a>另請參閱  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [初始化物件樹狀結構以外的物件項目](../../../../docs/framework/wpf/advanced/initialization-for-object-elements-not-in-an-object-tree.md)  
 [WPF 架構](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
