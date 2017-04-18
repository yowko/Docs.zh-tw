---
title: "WPF 架構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "執行緒相似性"
  - "架構"
  - "附加屬性"
  - "類別, System.Object"
  - "類別, System.Threading.DispatcherObject"
  - "類別, System.Windows.Controls.Control"
  - "類別, System.Windows.DependencyObject"
  - "類別, System.Windows.FrameworkElement"
  - "類別, System.Windows.Media.Visual"
  - "類別, System.Windows.UIElement"
  - "CommandBindings"
  - "元件, Unmanaged"
  - "Control 類別"
  - "資料範本"
  - "DependencyObject 類別"
  - "DispatcherObject 類別"
  - "FrameworkElement 類別"
  - "INotifyPropertyChange 介面"
  - "介面, INotifyPropertyChange"
  - "milcore"
  - "繪製器的演算法"
  - "屬性, 附加"
  - "分鏡腳本"
  - "System.Object 類別"
  - "System.Threading.DispatcherObject 類別"
  - "System.Windows.Controls.Control 類別"
  - "System.Windows.DependencyObject 類別"
  - "System.Windows.FrameworkElement 類別"
  - "System.Windows.Media.Visual 類別"
  - "System.Windows.UIElement 類別"
  - "thread, 相似性"
  - "UIElement 類別"
  - "Unmanaged 元件"
  - "Visual 類別"
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# WPF 架構
本主題提供 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 類別階層架構的導覽，  其中涵蓋大部分的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 主要子系統，並描述它們的互動方式。  同時也詳述 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 架構設計人員所做的一些選擇。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="System_Object"></a>   
## System.Object  
 主要 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 程式撰寫模型 \(Programming Model\) 是透過 Managed 程式碼公開。  在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的設計階段初期，曾針對系統中的 Managed 元件與 Unmanaged 元件應如何劃分界線而產生了數次辯論。  [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 提供的許多功能可讓開發程序更具生產力且更穩固 \(包括記憶體管理、錯誤處理、一般類型系統等\)，但是它們都需要成本。  
  
 下圖說明 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的主要元件。  圖表的紅色區段 \(PresentationFramework、PresentationCore 和 milcore\) 是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的主要程式碼部分。  其中，只有一個是 Unmanaged 元件 \- milcore。  為了能與 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 緊密整合，因此 milcore 以 Unmanaged 程式碼撰寫而成。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的所有顯示都是透過 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 引擎完成，以便進行有效的硬體和軟體轉譯。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 也需要精確控制記憶體和執行。  Milcore 中的複合引擎十分損耗效能，而且需要放棄 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 的許多優點才能獲得效能。  
  
 ![WPF 在 .NET Framework 中的位置。](../../../../docs/framework/wpf/advanced/media/wpf-architect1.png "wpf\_architect1")  
  
 本主題稍後會討論 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 之 Managed 與 Unmanaged 間的通訊部分。  以下將說明 Managed 程式撰寫模型的其餘部分。  
  
<a name="System_Threading_DispatcherObject"></a>   
## System.Threading.DispatcherObject  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的大部分物件都是衍生自 <xref:System.Windows.Threading.DispatcherObject>，它提供處理並行和執行緒的基本建構。  而 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 是以發送器實作的訊息系統為基礎。  其運作方式與常見的 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 訊息幫浦 \(Message Pump\) 十分類似。事實上，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 發送器正是使用 User32 訊息來執行跨緒行緒呼叫。  
  
 在討論 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的並行時，務必要了解兩個核心概念：發送器和執行緒相似性。  
  
 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的設計階段，目標是移至執行中的單一執行緒，但該執行緒必須是非執行緒 Affinitized 模型。  當元件使用執行中執行緒的識別來儲存某種類型的狀態時，就會發生執行緒相似性。  此種動作最常見的形式是使用執行緒本機存放區 \(TLS\) 來儲存狀態。  執行緒相似性需要作業系統中的每個實體執行緒只擁有一個邏輯執行緒，而這十分耗損記憶體。  最後，WPF 的執行緒模型會與具有執行緒相似性之單一執行緒執行的現有 User32 執行緒模型同步。  這麼做的主要原因是互通性 \(Interoperability\)，[!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)] 這類系統、剪貼簿和 Internet Explorer 全都需要單一執行緒相似性 \(Single Thread Affinity，STA\) 執行。  
  
 假設您擁有具有 STA 執行緒的物件，則需要能在執行緒之間通訊的方法，並驗證您是位在正確的執行緒上。  因此產生了發送器角色。  發送器是基本訊息發送系統，具有多個設定優先順序的佇列。  訊息範例包括原始輸入告知 \(滑鼠移動時\)、架構功能 \(配置\) 或使用者命令 \(執行這個方法\)。  您可以透過從 <xref:System.Windows.Threading.DispatcherObject> 衍生，建立具有 STA 行為的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件，而且會在建立階段提供發送器的指標。  
  
<a name="System_Windows_DependencyObject"></a>   
## System.Windows.DependencyObject  
 其中一個用於建置 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的主要架構原理是偏好使用屬性，而非使用方法或事件。  屬性是宣告式的，可讓您更輕鬆地指定目的，而不是動作。  這也支援模型驅動 \(或資料驅動\) 系統，用以顯示使用者介面內容。  這個原理的預期效果是建立更多可以繫結的屬性，以便更適當地控制應用程式的行為。  
  
 若想更充分利用由屬性驅動的系統，則您需要的屬性系統要比 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 所能提供者更加豐富。  這項豐富度的簡單範例是變更告知。  若要啟用雙向繫結，繫結的兩端都需要支援變更告知。  而為了讓行為繫結至屬性值，您需要在屬性值變更時收到告知。  [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] 具有的 **INotifyPropertyChange** 介面可允許物件發行變更告知，但這是選用的。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供較豐富的屬性系統，此系統衍生自 <xref:System.Windows.DependencyObject> 型別。  屬性系統實際上是「相依性」屬性系統，會追蹤屬性運算式之間的相依性，而且會在相依性變更時自動重新驗證屬性值。  例如，如果擁有繼承的屬性 \(如 <xref:System.Windows.Controls.Control.FontSize%2A>\)，則會在繼承該值之項目的父代 \(Parent\) 的屬性變更時，自動更新系統。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 屬性系統的基礎是屬性運算式的概念。  在第一版 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，關閉了屬性運算式系統，而運算式都是提供為架構的一部分。  屬性系統未將資料繫結、樣式設定或繼承 \(Inheritance\) 硬式編碼，而是透過架構內的後面層次加以提供的原因，正是因為運算式。  
  
 屬性系統也提供做為屬性值的疏鬆儲存。  因為物件會有很多的屬性，而且大部分的值都是處於它們的預設狀態 \(繼承、透過樣式設定等\)，所以並非物件的每個執行個體都需要每個已定義屬性的完整加權。  
  
 屬性系統的最後一項新功能是[附加屬性](GTMT)。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 項目是建構於複合和元件重複使用的原則之上。  通常是一些包含項目 \(如 <xref:System.Windows.Controls.Grid> 配置項目\) 需要子項目的額外資料，用以控制其行為 \(如資料列\/資料行資訊\)。  任何物件都能夠提供其他任何物件的屬性定義，因此不需要將所有這些屬性與每個項目建立關聯。  這與 JavaScript 的 "expando" 功能類似。  
  
<a name="System_Windows_Media_Visual"></a>   
## System.Windows.Media.Visual  
 在定義系統之後，下一個步驟是將像素繪製至螢幕。  <xref:System.Windows.Media.Visual> 類別可用來建置視覺物件的樹狀結構，而每個物件都會選擇性地含有繪製指示以及關於如何呈現這些指示的中繼資料，例如裁剪、轉換等。  <xref:System.Windows.Media.Visual> 的設計十分輕量和彈性，因此大部分功能都沒有公開公用的 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]，而且十分依賴受保護的回呼函式 \(Callback Function\)。  
  
 <xref:System.Windows.Media.Visual> 實際上是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 系統的進入點。  <xref:System.Windows.Media.Visual> 則是 Managed [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] 與 Unmanaged milcore 這兩個子系統之間的連線點。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 是透過周遊 milcore 管理的 Unmanaged 資料結構，來顯示資料。  這些結構稱為複合節點，代表一個階層顯示樹狀結構，且在每個節點都具有轉譯指令。  這種樹狀結構 \(如下圖右邊所示\) 只能透過訊息通訊協定進行存取。  
  
 以程式撰寫 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 時，請建立 <xref:System.Windows.Media.Visual> 項目以及衍生型別，以透過這個訊息通訊協定與複合樹狀結構進行內部通訊。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的每個 <xref:System.Windows.Media.Visual> 可以建立一個或數個複合節點，也可以完全不建立。  
  
 ![Windows Presentation Foundation 視覺化樹狀結構。](../../../../docs/framework/wpf/advanced/media/wpf-architecture2.png "wpf\_architecture2")  
  
 此處需注意一個十分重要的架構細節：會快取整個視覺化和繪製指示的樹狀結構。  就圖形而言，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用保留的呈現系統。  這會讓系統以高重新整理頻率進行重新繪製，而複合系統不會因使用者程式碼回呼而遭到封鎖。  這有助於防止顯示沒有回應的應用程式。  
  
 另一個在圖表中看不出來的重要細節，是系統如何實際執行複合。  
  
 在 User32 和 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 中，系統是以即時模式裁剪系統運作。  當需要呈現元件時，系統會建立超出就不允許元件接觸像素的裁剪界限，然後要求元件在該方塊中繪製像素。  因為當某個項目變更時，您只需要接觸受影響的元件 \(不會同時有兩個元件造成單一像素的色彩\)，所以這個系統十分適用於記憶體受限系統。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用「繪製器的演算法」繪製模型。  這表示不會裁剪每個元件，而是要求每個元件從顯示的後面往前呈現。  這樣可允許每個元件繪製在先前元件的顯示上。  這個模型的優點是會有複雜且局部透明的圖案。  搭配當今的現代圖形硬體，這個模型會變得相當快速 \(但不適用於建立 User32\/ [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 時\)。  
  
 如前所述，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的核心原理是要移往較具宣告式的「屬性中心」程式撰寫模型。  在視覺系統中，這會出現許多有趣的部分。  
  
 首先，如果是保留模式圖形系統，則這實際上會遠離必要的 DrawLine\/DrawLine 型別模型，傾向資料導向模型：new Line\(\)\/new Line\(\)。  此一傾向資料驅動呈現的現象，允許使用屬性來表示繪製指示上的複雜作業。  而衍生自 <xref:System.Windows.Media.Drawing> 的型別就是最後用於呈現的物件模型。  
  
 其次，如果評估動畫系統，則會發現它幾乎完全是宣告式的。  您可以用動畫物件的一組屬性來表示動畫，而不需要開發人員計算下一個位置或下一個色彩。  接著，這些動畫可以表示開發人員或設計人員的目的 \(在五秒內將這個按鈕從這裡移至那裡\)，而系統可以判斷完成該作業的最有效率方式。  
  
<a name="System_Windows_UIElement"></a>   
## System.Windows.UIElement  
 <xref:System.Windows.UIElement> 定義核心子系統，包括「配置」、「輸入」和「事件」。  
  
 「配置」是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的核心概念。  在許多系統中，有的具有一組固定的配置模型 \(HTML 支援三種配置模型：流程、絕對和表格\)，有的則沒有配置模型 \(User32 實際上僅支援絕對位置\)。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 是從假設開發人員和設計人員想要富彈性且可延伸的配置模型開始著手，而這套模型可以透過屬性值驅動，而不是命令式邏輯。  在 <xref:System.Windows.UIElement> 層級中，引入了配置的基本合約，這是具有 <xref:System.Windows.UIElement.Measure%2A> 和 <xref:System.Windows.UIElement.Arrange%2A> 傳遞的兩階段模型。  
  
 <xref:System.Windows.UIElement.Measure%2A> 允許元件判斷要取用的大小。  因為在許多情況下，父項目都會要求對子項進行多次測量，以決定它的最佳位置和大小，所以這是與 <xref:System.Windows.UIElement.Arrange%2A> 不同的階段。  父項目要求子項目進行測量的事實說明了 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的另一重要原理：調整大小以放入內容。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的所有控制項都支援將大小調整為其內容的原始大小。  這可以簡化當地語系化，而且允許在重新調整大小時動態配置項目。  <xref:System.Windows.UIElement.Arrange%2A> 階段允許父代進行定位和決定每個子項的最終大小。  
  
 提及 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的輸出端 <xref:System.Windows.Media.Visual> 和相關物件時，通常需要花費大量時間。  然而，輸入端上也有極大量的創新功能。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 輸入模型中最基本的變更可能是一致性模型，可用來透過系統傳送輸入事件。  
  
 輸入是從核心模式裝置驅動程式的信號開始，而且會透過內含 Windows 核心和 User32 的複雜處理序傳送至正確的處理序和執行緒。  將對應至輸入的 User32 訊息傳送至 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 之後，該訊息就會轉換成 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 原始輸入訊息，並且傳送至發送器。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 允許將原始輸入事件轉換成多個實際事件，讓 "MouseEnter" 這類功能在可保證傳遞的系統低層次實作。  
  
 每個輸入事件至少都會轉換為兩個事件：「預覽」事件和實際事件。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的所有事件都會透過項目樹狀結構進行傳送。  如果事件是從目標開始往上周遊到樹狀結構的根，則事件稱為「反昇」，如果是從根開始往下周遊到目標，則事件稱為「通道」。  輸入預覽事件通道，可讓樹狀結構中的任一項目進行篩選，或對事件採取動作。  一般 \(非預覽\) 事件則會從目標反昇至根。  
  
 將通道和反昇階段分割開來，可以讓鍵盤快速鍵這類功能的實作在複合全局中以一致的方式運作。  在 User32 中，讓單一全域資料表包含想要支援的所有快速鍵 \(Ctrl\+N 對應至 \[新增\]\)，即可實作鍵盤快速鍵。  在應用程式的發送器中，會呼叫 **TranslateAccelerator**，以探查 User32 中的輸入訊息，並判斷是否有任何項目符合已登錄的快速鍵。  在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，因為系統是完全「可組合」的 \(任何項目都可以處理和使用任何鍵盤快速鍵\)，所以不適用。  輸入具有這兩個階段模型，則可允許元件實作它們自己的 "TranslateAccelerator"。  
  
 更進一步地來說，<xref:System.Windows.UIElement> 也引入了 CommandBindings 的概念。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 命令系統允許開發人員以命令端點的觀點來定義功能，而命令端點是實作 <xref:System.Windows.Input.ICommand> 的項目。  命令繫結可讓項目定義輸入動作 \(Ctrl\+N\) 和命令 \(新增\) 之間的對應。  輸入動作和命令定義都是可以延伸的，而且可以在使用階段連接在一起。  例如，若要允許使用者自訂想要用於應用程式內的按鍵繫結，則這可予以簡化。  
  
 此時，主題的重點是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的「核心」功能 \(在 PresentationCore 組件中實作的功能\)。  建置 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 時，需要完整區隔基礎部分 \(如具有 **Measure** 和 **Arrange** 之配置的合約\) 與架構部分 \(如 <xref:System.Windows.Controls.Grid> 這類特定配置的實作\)。  目的是要提供堆疊低處的延伸點，允許外部開發人員在需要時建立他們自己的架構。  
  
<a name="System_Windows_FrameworkElement"></a>   
## System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> 可以從兩個角度來看。  它引入了子系統的一組原則和自訂項目，而這些子系統是在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的低層級中引入。  它也引入了一組新的子系統。  
  
 <xref:System.Windows.FrameworkElement> 引入的主要原則是有關應用程式配置。  <xref:System.Windows.FrameworkElement> 是根據 <xref:System.Windows.UIElement> 引入的基本配置合約進行建置，並加入配置「位置」的概念，讓配置作者可以輕鬆地擁有一致的屬性驅動配置語意 \(Semantics\) 集合。  <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、<xref:System.Windows.FrameworkElement.MinWidth%2A> 和 <xref:System.Windows.FrameworkElement.Margin%2A> 等這類的屬性，讓所有衍生自 <xref:System.Windows.FrameworkElement> 的元件在配置容器內具有一致的行為。  
  
 <xref:System.Windows.FrameworkElement> 也提供可在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 核心層級找到之許多功能的較簡易 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 公開。  例如，<xref:System.Windows.FrameworkElement> 透過 <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> 方法直接存取動畫。  而 <xref:System.Windows.Media.Animation.Storyboard> 提供方式，根據一組屬性來撰寫多個動畫的指令碼。  
  
 <xref:System.Windows.FrameworkElement> 引入的兩個最重要項目是資料繫結和樣式。  
  
 使用過 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 或 [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] 來建立應用程式[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的使用者，應該都相當熟悉 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的資料繫結子系統。  在上述的每個系統中，都有簡單的方式可表示您要將來自所指定項目的一個或多個屬性繫結至資料片段。  而 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 完全支援屬性繫結、轉換和清單繫結。  
  
 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，資料繫結的其中一個有趣功能是引入資料範本。  資料範本可讓您以宣告方式指定視覺化資料片段的方式。  如果不想要建立可以繫結至資料的自訂使用者介面，則可以轉回問題，讓資料判斷要建立的顯示。  
  
 樣式設定實際上是輕量的資料繫結格式。  您可以使用樣式，將來自共用定義的一組屬性繫結至項目的一個或多個執行個體。  可以透過明確參考 \(設定 <xref:System.Windows.FrameworkElement.Style%2A> 屬性\) 或將樣式關聯至項目之 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 型別的隱含方式，將樣式套用至項目。  
  
<a name="System_Windows_Controls_Control"></a>   
## System.Windows.Controls.Control  
 控制項的最重要功能是樣板化。  如果您將 WPF 的複合系統視為保留模式呈現系統，則樣板化允許控制項以參數化的宣告方式描述它的呈現。  <xref:System.Windows.Controls.ControlTemplate> 實際上就是建立一組子項目的指令碼，這些子項目會繫結至控制項所提供的屬性。  
  
 <xref:System.Windows.Controls.Control> 提供一組內建屬性 \(Stock Property\) \(<xref:System.Windows.Controls.Control.Foreground%2A>、<xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Padding%2A> 等\)，讓範本作者可以用來自訂控制項的顯示。  控制項的實作會提供資料模型和互動模型。  互動模型定義一組命令 \(如關閉視窗\) 以及與輸入動作的繫結 \(如按一下視窗上方的紅色 X\)。  資料模型提供一組屬性，用以自訂互動模型或自訂顯示 \(由範本決定\)。  
  
 將資料模型 \(屬性\)、互動模型 \(命令和事件\) 和顯示模型 \(範本\) 分割開來，可以讓您完整自訂控制項的外觀和行為。  
  
 控制項的通用資料模型部分是內容模型。  如果查看 <xref:System.Windows.Controls.Button> 這類控制項，則會看到它具有型別為 <xref:System.Object> 的 "Content" 屬性。  在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] 中，這個屬性一般會是字串，而這限制了可以放入按鈕中的內容類型。  按鈕的內容可以是簡單字串、複雜資料物件或整個項目樹狀結構。  如果是資料物件，則會使用資料範本來建構顯示。  
  
<a name="Summary"></a>   
## 摘要  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 是設計成允許您建立動態的資料驅動呈現系統。  系統的每個部分都設計成透過驅動行為的屬性值來建立物件。  資料繫結是系統的基礎部分，而且會在每個層級進行整合。  
  
 傳統應用程式會建立顯示，然後繫結至一些資料。  在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，與控制項相關的所有項目 \(顯示的每個部分\) 都是透過資料繫結的某個型別所產生。  而在按鈕內建立組成的控制項，並將它的顯示繫結至按鈕的內容屬性，就會顯示在按鈕內找到的文字。  
  
 當您開始開發 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 架構應用程式時，應該會覺得十分熟悉。  您設定屬性、使用物件及資料繫結的方式，與使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 或 [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] 的方式幾乎相同。  在您深入查看 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的架構之後，會發現可以建立較豐富的應用程式，這些應用程式基本上會將資料視為應用程式的核心驅動程式。  
  
## 請參閱  
 <xref:System.Windows.Media.Visual>   
 <xref:System.Windows.UIElement>   
 <xref:System.Windows.Input.ICommand>   
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.Threading.DispatcherObject>   
 <xref:System.Windows.Input.CommandBinding>   
 <xref:System.Windows.Controls.Control>   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [配置](../../../../docs/framework/wpf/advanced/layout.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)