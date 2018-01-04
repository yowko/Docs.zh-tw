---
title: "WPF 架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [WPF], attached
- attached properties [WPF]
- architecture [WPF]
- unmanaged components [WPF]
- affinity thread [WPF]
- Storyboards [WPF]
- milcore [WPF]
- components [WPF], unmanaged
- painter's algorithm
- interfaces [WPF], INotifyPropertyChange
- CommandBindings [WPF]
- data templates [WPF]
- thread [WPF], affinity
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d688bb460b01c0b3fe4d7571916b887cd485b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-architecture"></a>WPF 架構
本主題提供 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 類別階層的導覽。 它涵蓋大部分的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 主要子系統，並描述其互動方式。 它也會詳述 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 架構設計人員所進行的一些選擇。  
  
  
<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 主要 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 程式設計模型是透過 Managed 程式碼所公開。 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 設計階段早期，有關應該在系統的 Managed 元件與 Unmanaged 元件之間繪製線條的位置有許多爭論。 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 提供許多功能，讓開發更具生產力且更穩固 (包括記憶體管理、錯誤處理、一般類型系統等)，但都需要付出代價。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的主要元件如下圖所示。 圖表的紅色區段 (PresentationFramework、PresentationCore 和 milcore) 是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的主要程式碼部分。 其中只有一種是 Unmanaged 元件：milcore。 milcore 是使用 Unmanaged 程式碼所撰寫，以啟用與 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 的緊密整合。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的所有顯示都是透過 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 引擎所完成，以允許有效率的硬體和軟體轉譯。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 也需要記憶體和執行的良好控制。 milcore 中的組合引擎對於效能異常敏感，而且需要犧牲許多 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 優點才能獲得效能。  
  
 ![WPF 在 .NET Framework 中的位置。](../../../../docs/framework/wpf/advanced/media/wpf-architect1.PNG "wpf_architect1")  
  
 本主題稍後會討論 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的 Managed 與 Unmanaged 部分之間的通訊。 Managed 程式設計模型的其餘部分說明如下。  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 中的大部分物件[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]衍生自<xref:System.Windows.Threading.DispatcherObject>，可提供基本建構並行處理和執行緒處理。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 是根據發送器所實作的訊息系統。 此運作方式很像熟悉的 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 訊息提取；事實上，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 發送器使用 User32 訊息來執行跨執行緒呼叫。  
  
 討論 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的並行時，實際上需要了解兩個核心概念：發送器和執行緒相似性。  
  
 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的設計階段期間，目的是要移至單一執行的執行緒，而非執行緒「親和性」模型。 元件使用執行中執行緒的身分識別來儲存某些類型的狀態時，會發生執行緒親和性。 這最常見的形式是使用執行緒本機存放區 (TLS) 來儲存狀態。 執行緒親和性需要作業系統中只有一個實體執行緒擁有每個邏輯執行的執行緒，而這樣可能會耗用大量記憶體。 最後，透過執行緒親和性，WPF 的執行緒模型會與單一執行緒執行作業的現有 User32 執行緒模型同步。 這個的主要原因是交互操作性；[!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)] 這類系統、剪貼簿和 Internet Explorer 都需要單一執行緒親和性 (STA) 執行。  
  
 假設您的物件具有 STA 執行緒，則您需要執行緒之間的通訊方法，並驗證您位於正確的執行緒。 其中具有發送器的角色。 發送器是基本訊息發送系統，具有多個已設定優先權的佇列。 訊息範例包括未經處理的輸入通知 (滑鼠移動)、架構功能 (版面配置) 或使用者命令 (執行此方法)。 由衍生自<xref:System.Windows.Threading.DispatcherObject>，您建立[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]物件具有 STA 行為，並提供指標給發送器在建立時。  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 建置 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 時所使用的其中一個主要架構原理是方法或事件的屬性喜好設定。 屬性是宣告式，可讓您更輕鬆地指定意圖，而不是動作。 這也支援用於顯示使用者介面內容的模型驅動或資料驅動系統。 此原理的預期效果是建立多個可繫結的屬性，以進一步控制應用程式的行為。  
  
 若要讓屬性驅動多個系統，則需要比 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 所提供的屬性系統更豐富的屬性系統。 這項豐富性的簡單範例是變更通知。 若要啟用雙向繫結，您需要繫結兩端都支援變更通知。 若要讓行為繫結至屬性值，您需要在屬性值變更時收到通知。 [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] 的 **INotifyPropertyChange** 介面可讓物件發行變更通知，不過它是選擇性的。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]提供更豐富的屬性系統，衍生自<xref:System.Windows.DependencyObject>型別。 屬性系統實際上是「相依性」屬性系統，因此它會追蹤屬性運算式之間的相依性，並在相依性變更時自動重新驗證屬性值。 例如，如果您有繼承的屬性 (例如<xref:System.Windows.Controls.Control.FontSize%2A>)，如果在屬性上父項目繼承的值變更，系統就會自動更新。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 屬性系統的基礎是屬性運算式的概念。 在這個第一版 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，已關閉屬性運算式系統，而且運算式都會提供為架構的一部分。 運算式是屬性系統沒有資料繫結、樣式或繼承硬式編碼，而是由架構內的稍後層級所提供的原因。  
  
 屬性系統也會提供屬性值的疏鬆儲存體。 因為物件可以有數十個 (甚至數百個) 屬性，所以大部分的值都處於其預設狀態 (繼承、透過樣式設定等等)，而且並非物件的每個執行個體都需要有其上定義之每個屬性的完整加權。  
  
 屬性系統的最終新功能是附加屬性概念。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 項目的建置基礎是組合和元件重複使用的原則。 一般情況是，有些包含項目 (例如<xref:System.Windows.Controls.Grid>版面配置項目) 需要子項目，來控制其行為 （例如資料列/資料行資訊） 上的其他資料。 允許任何物件提供所有其他物件的屬性定義，而不是建立所有這些屬性與每個項目的關聯。 這與 JavaScript 的 "expando" 功能類似。  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 定義系統之後，下一個步驟是將像素繪製到螢幕。 <xref:System.Windows.Media.Visual>類別會提供每一個都會選擇性地包含繪圖指示和如何呈現這些指示 （剪輯、 轉換等等） 的相關中繼資料建立視覺化的物件樹狀結構。 <xref:System.Windows.Media.Visual>設計非常輕量且具有彈性，因此大部分的功能有沒有公用[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]曝光度和高度依賴受保護的回呼函式。  
  
 <xref:System.Windows.Media.Visual>其實是進入點[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]複合系統。 <xref:System.Windows.Media.Visual>這些兩個子系統，managed 之間的連線點[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]和 unmanaged 的 milcore。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 透過周遊 milcore 所管理的 Unmanaged 資料結構來顯示資料。 這些結構稱為組合節點，代表具有每個節點之轉譯指示的階層式顯示樹狀結構。 下圖右側所說明的這個樹狀結構只能透過訊息通訊協定進行存取。  
  
 程式設計時[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，您建立<xref:System.Windows.Media.Visual>項目和衍生的類型，此訊息的通訊協定透過複合樹狀結構內部通訊。 每個<xref:System.Windows.Media.Visual>中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]可能會建立一個、 none、 或組合的數個節點。  
  
 ![Windows Presentation Foundation 視覺化樹狀結構。](../../../../docs/framework/wpf/advanced/media/wpf-architecture2.PNG "wpf_architecture2")  
  
 這裡需要注意一個極為重要的架構詳細資料：會快取視覺效果的整個樹狀結構以及繪圖指示。 就圖形來說，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會使用保留轉譯系統。 這可讓系統以高重新整理速率重繪，而組合系統不會封鎖使用者程式碼的回呼。 這有助於防止出現沒有回應的應用程式。  
  
 圖表中實際上不大明顯的另一個重要詳細資料是系統如何實際執行組合。  
  
 在 User32 和 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 中，系統會在即時模式裁剪系統上運作。 需要轉譯元件時，系統會建立不允許元件接觸像素的外部裁剪界限，接著要求元件在該方塊中繪製像素。 此系統非常適合在記憶體受限系統中運作，因為內容變更時，您只需要接觸受影響元件；沒有兩個元件會形成單一像素的色彩。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用「繪製器的演算法」繪製模型。 這表示，會要求每個元件從後到前轉譯顯示，而不是裁剪每個元件。 這可在前一個元件的顯示上方繪製每個元件。 此模型的優點在於您可以有複雜且部分透明的圖形。 此模型運用現今的現代圖形硬體，因此相當快速 (建立 User32/[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 時則否)。  
  
 如前所述，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的核心原理是移至更具宣告性且「以屬性為主」的程式設計模型。 在視覺物件系統中，這出現在幾個有趣的地方。  
  
 首先，如果您考慮使用保留的模式圖形系統，則這真地會從命令式 DrawLine/DrawLine 類型模型移至資料導向模型：新的 Line()/新的 Line()。 這項移至資料驅動轉譯作業允許使用屬性來表示繪圖指示上的複雜作業。 衍生自類型<xref:System.Windows.Media.Drawing>是有效的轉譯物件模型。  
  
 其次，如果您評估動畫系統，則會看到它幾乎完全是宣告式。 您可以將動畫表示為動畫物件的一組屬性，而不需要開發人員計算下一個位置或下一個色彩。 這些動畫接著可以表示開發人員或設計人員的意圖 (在 5 秒內，將此按鈕從這裡移至目的地)，而且系統可以判斷完成該作業的最有效方式。  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>定義核心子系統包括版面配置、 輸入和事件。  
  
 版面配置是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的核心概念。 在許多系統中，會有固定一組版面配置模型 (HTML 支援三種版面配置模型：非固定、絕對和資料表) 或沒有版面配置模型 (User32 實際上只支援絕對定位)。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 一開始的假設是開發人員和設計人員想要具彈性且可擴充的版面配置模型，而此模型可透過屬性值驅動，而非命令式邏輯。 在<xref:System.Windows.UIElement>導入的層級，版面配置的基本合約是 – 兩階段使用的模型<xref:System.Windows.UIElement.Measure%2A>和<xref:System.Windows.UIElement.Arrange%2A>傳遞。  
  
 <xref:System.Windows.UIElement.Measure%2A>可讓元件，以確定它想要採取的大小。 這是從不同階段<xref:System.Windows.UIElement.Arrange%2A>因為有許多情況下，父項目將會詢問測量來判斷其最理想的位置和大小的數次的子系。 父項目要求子項目進行測量的事實示範 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的另一個重要原理：內容大小。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的所有控制項都支援調整成其內容原本大小的能力。 這會讓當地語系化更為簡單，並在調整事物時允許動態配置項目。 <xref:System.Windows.UIElement.Arrange%2A>階段允許的位置，並判斷每個子系的最終大小的父系。  
  
 說的輸出端通常花費許多時間[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]–<xref:System.Windows.Media.Visual>和相關物件。 不過，輸入端上也會進行極大的創新。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 輸入模型的最基本變更可能是一致模型，而使用此模型，即可透過系統來路由傳送輸入事件。  
  
 輸入來源是核心模式裝置驅動程式上的訊號，並且透過包含 Windows 核心和 User32 的複雜處理序路由傳送至正確的處理序和執行緒。 對應至輸入的 User32 訊息在路由傳送至 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 之後，會轉換為 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 未經處理的輸入訊息，並傳送至發送器。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 允許將未經處理的輸入事件轉換為多個實際事件，方法是在具有保證傳遞之系統的低層級實作 "MouseEnter" 這類功能。  
  
 每個輸入事件都會轉換成至少兩個事件：「預覽」事件和實際事件。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的所有事件都有透過項目樹狀結構進行路由傳送的概念。 如果事件是從樹狀結構中的目標往上周遊到根，則事件就是「事件反昇」，如果事件是從根開始並往下周遊到目標，則是「通道」。 輸入預覽事件通道，讓樹狀結構中的任何項目有機會進行篩選或對事件採取動作。 一般 (非預覽) 事件接著會從目標往上反昇到根。  
  
 通道與事件反昇階段之間的這項分割可讓鍵盤快速鍵這類功能的實作在複合情況下以一致的方式運作。 在 User32 中，您將實作鍵盤快速鍵，方法是具有包含所有您要支援之快速鍵的單一全域資料表 (Ctrl+N 對應至 "New")。 在應用程式的發送器中，您會呼叫可發覺 User32 中輸入訊息的 **TranslateAccelerator**，並判斷是否有任何快速鍵符合已註冊的快速鍵。 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，這不會運作，因為系統為完全「可組合」：任何項目都可以處理和使用任何鍵盤快速鍵。 具有這個兩階段輸入模型可讓元件實作其專屬 "TranslateAccelerator"。  
  
 若要進一步採取此步驟<xref:System.Windows.UIElement>也導入了 CommandBindings 的概念。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]命令系統允許的項目定義命令結束點 – 方面的功能的開發人員實作<xref:System.Windows.Input.ICommand>。 命令繫結可讓項目定義輸入手勢 (Ctrl+N) 與命令 (New) 之間的對應。 輸入手勢和命令定義都是可以擴充的，而且可以在使用階段連接在一起。 例如，這會讓允許使用者自訂其想要在應用程式內使用的重要繫結變得簡單。  
  
 在本主題中，到目前為止，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的「核心」功能是 PresentationCore 組件中所實作的功能，已經是焦點。 建置時[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、 清除基本項目之間的分隔 (喜歡的版面配置與合約**量值**和**排列**) 和架構片段 （例如特定的實作配置，例如<xref:System.Windows.Controls.Grid>) 是所要的結果。 目標是提供堆疊低層的擴充點，以讓外部開發人員視需要建立其專屬架構。  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>可以在查看兩個不同的方式。 它在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 低層級所引進的子系統上引進一組原則和自訂。 它同時引進一組新的子系統。  
  
 所導入的主要原則<xref:System.Windows.FrameworkElement>周圍的應用程式配置。 <xref:System.Windows.FrameworkElement>所導入的基本版面配置合約上建置<xref:System.Windows.UIElement>，並將 「 位置 」，它可以輕鬆擁有一致的導向配置語意的屬性集配置作者的版面配置的概念。 屬性，例如<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>， <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>， <xref:System.Windows.FrameworkElement.MinWidth%2A>，和<xref:System.Windows.FrameworkElement.Margin%2A>（若要提供幾個） 提供所有元件衍生自<xref:System.Windows.FrameworkElement>版面配置容器內的一致行為。  
  
 <xref:System.Windows.FrameworkElement>也提供更容易[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]核心層級中的中找到的許多功能公開[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。 例如，<xref:System.Windows.FrameworkElement>可直接存取透過動畫<xref:System.Windows.FrameworkElement.BeginStoryboard%2A>方法。 A<xref:System.Windows.Media.Animation.Storyboard>提供向指令碼針對一組屬性的多個動畫。  
  
 兩個最重要的事情，<xref:System.Windows.FrameworkElement>導入了資料繫結和樣式。  
  
 使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 或 [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] 來建立應用程式 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的使用者，應該相當熟悉[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的資料繫結子系統。 在所有這些系統中，有一種簡單的方式可表示您想要一或多個屬性從指定的項目繫結至資料的某個部分。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 完整支援屬性繫結、轉換和清單繫結。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中資料繫結的其中一個最有趣功能是引進資料範本。 資料範本可讓您以宣告方式指定應該如何視覺化資料。 您可以解決問題，並讓資料判斷將建立的顯示，而不是建立可繫結至資料的自訂使用者介面。  
  
 樣式實際上是簡單形式的資料繫結。 使用樣式，您可以將共用定義中的一組屬性繫結至項目的一或多個執行個體。 樣式套用至項目藉由明確參考 (藉由設定<xref:System.Windows.FrameworkElement.Style%2A>屬性) 或隱含地建立關聯的樣式[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]項目的型別。  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 控制項的最重要功能是設定範本。 如果您將 WPF 的組合系統視為保留模式轉譯系統，則設定範本可讓控制項透過參數化宣告方式描述其轉譯。 A<xref:System.Windows.Controls.ControlTemplate>其實只是指令碼來建立子系的一組項目，以繫結至控制項所提供的屬性。  
  
 <xref:System.Windows.Controls.Control>提供一組內建屬性， <xref:System.Windows.Controls.Control.Foreground%2A>， <xref:System.Windows.Controls.Control.Background%2A>， <xref:System.Windows.Controls.Control.Padding%2A>、 舉範本作者可以再使用來自訂控制項的顯示。 控制項的實作會提供資料模型和互動模型。 互動模型定義一組命令 (例如視窗的 Close) 以及輸入手勢的繫結 (例如按一下視窗右上角的紅色 X)。 資料模型提供一組屬性來自訂互動模型或是自訂顯示 (透過範本決定)。  
  
 資料模型 (屬性)、互動模型 (命令和事件) 與顯示模型 (範本) 之間的這項分割可啟用控制項外觀和行為的完整自訂。  
  
 控制項資料模型的一般層面是內容模型。 如果您看一下控制項喜歡<xref:System.Windows.Controls.Button>，您會看到它有一個名為 「 內容 」 類型的屬性<xref:System.Object>。 在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] 中，這個屬性一般會是字串；不過，這會限制您可放入按鈕的內容類型。 按鈕的內容可以是簡單字串、複雜資料物件或整個項目樹狀結構。 如果是資料物件，則使用資料範本來建構顯示。  
  
<a name="Summary"></a>   
## <a name="summary"></a>總結  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 設計成讓您建立動態資料驅動的呈現系統。 系統的每個組件都是設計成透過可驅動行為的屬性集來建立物件。 資料繫結是系統的基礎部分，並且在各層級進行整合。  
  
 傳統應用程式會建立顯示，然後繫結至一些資料。 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，會由某種類型的資料繫結產生控制項的所有相關項目，即顯示的每個層面。 在按鈕內建立組合的控制項，並將其顯示繫結至按鈕的內容屬性，即會顯示在按鈕內找到的文字。  
  
 當您開始開發 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式時，應該會覺得十分熟悉。 設定屬性、使用物件和資料繫結的方式，大致與使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 或 [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] 相同。 更深入調查 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的架構，即會發現您可以建立更多的應用程式，而這些應用程式基本上會將資料視為應用程式的核心驅動程式。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Threading.DispatcherObject>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Controls.Control>  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [版面配置](../../../../docs/framework/wpf/advanced/layout.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
