---
title: 架構
ms.date: 03/30/2017
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
ms.openlocfilehash: b16be8470a47f3e8e362feb0b13e10aa901baacb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187125"
---
# <a name="wpf-architecture"></a>WPF 架構
本主題提供 Windows 演示基礎 （WPF） 類層次結構的導覽。 它涵蓋了 WPF 的大多數主要子系統，並描述了它們如何交互。 它還詳細介紹了 WPF 架構師所做的一些選擇。  

<a name="System_Object"></a>
## <a name="systemobject"></a>System.Object  
 主 WPF 程式設計模型通過託管代碼公開。 在 WPF 設計階段的早期，就系統託管元件和非託管元件之間的劃分位置進行了多次辯論。 CLR 提供了許多功能，使開發更高效、更可靠（包括記憶體管理、錯誤處理、一般型別系統等），但它們是有代價的。  
  
 下圖說明瞭世界森林論壇的主要組成部分。 關係圖的紅色部分（演示框架、演示核心和 milcore）是 WPF 的主要代碼部分。 其中只有一種是 Unmanaged 元件：milcore。 Milcore 編寫于非託管代碼中，以便與 DirectX 緊密集成。 WPF 中的所有顯示都通過 DirectX 引擎完成，從而可實現高效的硬體和軟體呈現。 WPF 還需要對記憶體和執行進行精細控制。 milcore 中的組合引擎對性能非常敏感，需要放棄 CLR 的許多優勢才能獲得性能。  
  
 ![WPF 在 .NET Framework 中的位置。](./media/wpf-architect1.PNG "wpf_architect1")  
  
 本主題稍後將討論 WPF 的託管和非託管部分之間的通信。 Managed 程式設計模型的其餘部分說明如下。  
  
<a name="System_Threading_DispatcherObject"></a>
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 WPF 中的大多數物件派生<xref:System.Windows.Threading.DispatcherObject>自，它提供了處理併發和執行緒的基本構造。 WPF 基於調度程式實現的消息傳遞系統。 這的工作原理很像熟悉的Win32消息泵;事實上，WPF 調度程式使用 User32 消息執行交叉執行緒調用。  
  
 在 WPF 中討論併發性時，實際上需要瞭解兩個核心概念 - 調度器和執行緒相關性。  
  
 在 WPF 的設計階段，目標是移動到單個執行執行緒，但採用非執行緒"關聯化"模型。 元件使用執行中執行緒的身分識別來儲存某些類型的狀態時，會發生執行緒親和性。 這最常見的形式是使用執行緒本機存放區 (TLS) 來儲存狀態。 執行緒親和性需要作業系統中只有一個實體執行緒擁有每個邏輯執行的執行緒，而這樣可能會耗用大量記憶體。 最後，透過執行緒親和性，WPF 的執行緒模型會與單一執行緒執行作業的現有 User32 執行緒模型同步。 這樣做的主要原因是互通性 – OLE 2.0、剪貼簿和 Internet 資源管理器等系統都需要單線程關聯 （STA） 執行。  
  
 假設您的物件具有 STA 執行緒，則您需要執行緒之間的通訊方法，並驗證您位於正確的執行緒。 其中具有發送器的角色。 發送器是基本訊息發送系統，具有多個已設定優先權的佇列。 訊息範例包括未經處理的輸入通知 (滑鼠移動)、架構功能 (版面配置) 或使用者命令 (執行此方法)。 通過派生從<xref:System.Windows.Threading.DispatcherObject>，您將創建具有 STA 行為的 CLR 物件，並在創建時為調度程式提供指向調度程式的指標。  
  
<a name="System_Windows_DependencyObject"></a>
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 構建 WPF 時使用的主要體系結構哲學之一是首選屬性而不是方法或事件。 屬性是宣告式，可讓您更輕鬆地指定意圖，而不是動作。 這也支援用於顯示使用者介面內容的模型驅動或資料驅動系統。 此原理的預期效果是建立多個可繫結的屬性，以進一步控制應用程式的行為。  
  
 為了使更多的系統由屬性驅動，需要比 CLR 提供的更豐富的屬性系統。 這項豐富性的簡單範例是變更通知。 若要啟用雙向繫結，您需要繫結兩端都支援變更通知。 若要讓行為繫結至屬性值，您需要在屬性值變更時收到通知。 微軟 .NET 框架有一個介面 **，NotifyPropertyChange**，它允許物件發佈更改通知，但它是可選的。  
  
 WPF 提供了一個更豐富的屬性系統，派生<xref:System.Windows.DependencyObject>自類型。 屬性系統實際上是「相依性」屬性系統，因此它會追蹤屬性運算式之間的相依性，並在相依性變更時自動重新驗證屬性值。 例如，如果屬性繼承 （如<xref:System.Windows.Controls.Control.FontSize%2A>），則如果屬性在繼承該值的元素的父項上發生更改，則系統將自動更新。  
  
 WPF 屬性系統的基礎是屬性運算式的概念。 在 WPF 的第一個版本中，屬性運算式系統已關閉，並且運算式都作為框架的一部分提供。 運算式是屬性系統沒有資料繫結、樣式或繼承硬式編碼，而是由架構內的稍後層級所提供的原因。  
  
 屬性系統也會提供屬性值的疏鬆儲存體。 因為物件可以有數十個 (甚至數百個) 屬性，所以大部分的值都處於其預設狀態 (繼承、透過樣式設定等等)，而且並非物件的每個執行個體都需要有其上定義之每個屬性的完整加權。  
  
 屬性系統的最終新功能是附加屬性概念。 WPF 元素基於組合和元件重用原則構建。 通常的情況是，某些包含元素（如<xref:System.Windows.Controls.Grid>佈局元素）需要子項目上的其他資料來控制其行為（如行/列資訊）。 允許任何物件提供所有其他物件的屬性定義，而不是建立所有這些屬性與每個項目的關聯。 這與 JavaScript 的 "expando" 功能類似。  
  
<a name="System_Windows_Media_Visual"></a>
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 定義系統之後，下一個步驟是將像素繪製到螢幕。 該<xref:System.Windows.Media.Visual>類用於構建一個可視物件樹，每個物件都可選地包含有關如何呈現這些指令（剪切、轉換等）的繪圖說明和中繼資料。 <xref:System.Windows.Media.Visual>設計為極其輕巧和靈活，因此大多數功能沒有公共 API 公開，並且嚴重依賴受保護的回檔功能。  
  
 <xref:System.Windows.Media.Visual>實際上是 WPF 組合系統的切入點。 <xref:System.Windows.Media.Visual>是這兩個子系統（託管 API 和非託管 milcore）之間的連接點。  
  
 WPF 通過遍歷 milcore 管理的非託管資料結構來顯示資料。 這些結構稱為組合節點，代表具有每個節點之轉譯指示的階層式顯示樹狀結構。 下圖右側所說明的這個樹狀結構只能透過訊息通訊協定進行存取。  
  
 程式設計 WPF 時，您將<xref:System.Windows.Media.Visual>創建元素和派生類型，這些元素和派生類型通過此消息傳遞協定在內部與組合樹通信。 WPF<xref:System.Windows.Media.Visual>中的每個節點可以創建一個、無或多個合成節點。  
  
 ![Windows Presentation Foundation 視覺化樹狀結構。](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 這裡需要注意一個極為重要的架構詳細資料：會快取視覺效果的整個樹狀結構以及繪圖指示。 在圖形方面，WPF 使用保留的渲染系統。 這可讓系統以高重新整理速率重繪，而組合系統不會封鎖使用者程式碼的回呼。 這有助於防止出現沒有回應的應用程式。  
  
 圖表中實際上不大明顯的另一個重要詳細資料是系統如何實際執行組合。  
  
 在 User32 和 GDI 中，系統可立即使用模式剪切系統。 需要轉譯元件時，系統會建立不允許元件接觸像素的外部裁剪界限，接著要求元件在該方塊中繪製像素。 此系統非常適合在記憶體受限系統中運作，因為內容變更時，您只需要接觸受影響元件；沒有兩個元件會形成單一像素的色彩。  
  
 WPF使用"畫家演算法"繪畫模型。 這表示，會要求每個元件從後到前轉譯顯示，而不是裁剪每個元件。 這可在前一個元件的顯示上方繪製每個元件。 此模型的優點在於您可以有複雜且部分透明的圖形。 在當今的現代圖形硬體中，此型號相對較快（創建 User32/GDI 時情況並非如此）。  
  
 如前所述，WPF 的核心理念是轉向更具聲明性的"以屬性為中心的"程式設計模型。 在視覺物件系統中，這出現在幾個有趣的地方。  
  
 首先，如果您考慮使用保留的模式圖形系統，則這真地會從命令式 DrawLine/DrawLine 類型模型移至資料導向模型：新的 Line()/新的 Line()。 這項移至資料驅動轉譯作業允許使用屬性來表示繪圖指示上的複雜作業。 派生的類型<xref:System.Windows.Media.Drawing>實際上是用於渲染的物件模型。  
  
 其次，如果您評估動畫系統，則會看到它幾乎完全是宣告式。 您可以將動畫表示為動畫物件的一組屬性，而不需要開發人員計算下一個位置或下一個色彩。 這些動畫接著可以表示開發人員或設計人員的意圖 (在 5 秒內，將此按鈕從這裡移至目的地)，而且系統可以判斷完成該作業的最有效方式。  
  
<a name="System_Windows_UIElement"></a>
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>定義核心子系統，包括佈局、輸入和事件。  
  
 佈局是 WPF 的核心概念。 在許多系統中，會有固定一組版面配置模型 (HTML 支援三種版面配置模型：非固定、絕對和資料表) 或沒有版面配置模型 (User32 實際上只支援絕對定位)。 WPF 首先假定開發人員和設計人員需要一個靈活、可擴展的佈局模型，該模型可以由屬性值而不是命令邏輯驅動。 在級別<xref:System.Windows.UIElement>上，引入了佈局的基本協定 - 具有<xref:System.Windows.UIElement.Measure%2A>和<xref:System.Windows.UIElement.Arrange%2A>傳遞的兩相模型。  
  
 <xref:System.Windows.UIElement.Measure%2A>允許元件確定它要採用的大小。 這是一個單獨的階段，<xref:System.Windows.UIElement.Arrange%2A>因為在許多情況下，父元素將要求子項目多次測量以確定其最佳位置和大小。 父元素要求子項目進行度量這一事實演示了 WPF 的另一個關鍵理念 - 內容大小。 WPF 中的所有控制項都支援調整其內容的自然大小。 這會讓當地語系化更為簡單，並在調整事物時允許動態配置項目。 該<xref:System.Windows.UIElement.Arrange%2A>階段允許父級定位並確定每個子級的最終大小。  
  
 經常花費大量時間討論 WPF 的輸出端和相關<xref:System.Windows.Media.Visual>物件。 不過，輸入端上也會進行極大的創新。 WPF 輸入模型中最根本的更改可能是通過系統路由輸入事件的一致模型。  
  
 輸入來源是核心模式裝置驅動程式上的訊號，並且透過包含 Windows 核心和 User32 的複雜處理序路由傳送至正確的處理序和執行緒。 將與輸入對應的 User32 消息路由到 WPF 後，該消息將轉換為 WPF 原始輸入消息併發送到調度程式。 WPF 允許將原始輸入事件轉換為多個實際事件，使"MouseEnter"等功能能夠在系統的較低級別實現，並保證交付。  
  
 每個輸入事件都會轉換成至少兩個事件：「預覽」事件和實際事件。 WPF 中的所有事件都有通過元素樹路由的概念。 如果事件從目標向上穿過樹到根，則表示為"氣泡"，如果事件從根開始並向下遍歷到目標，則表示為"隧道"。 輸入預覽事件通道，讓樹狀結構中的任何項目有機會進行篩選或對事件採取動作。 一般 (非預覽) 事件接著會從目標往上反昇到根。  
  
 通道與事件反昇階段之間的這項分割可讓鍵盤快速鍵這類功能的實作在複合情況下以一致的方式運作。 在 User32 中，您將實作鍵盤快速鍵，方法是具有包含所有您要支援之快速鍵的單一全域資料表 (Ctrl+N 對應至 "New")。 在應用程式的發送器中，您會呼叫可發覺 User32 中輸入訊息的 **TranslateAccelerator**，並判斷是否有任何快速鍵符合已註冊的快速鍵。 在 WPF 中，這不起作用，因為系統是完全"可組合的" - 任何元素都可以處理和使用任何鍵盤快速鍵。 具有這個兩階段輸入模型可讓元件實作其專屬 "TranslateAccelerator"。  
  
 為了更進一步，<xref:System.Windows.UIElement>還介紹了命令綁定的概念。 WPF 命令系統允許開發人員根據命令終結點（實現<xref:System.Windows.Input.ICommand>的）定義功能。 命令繫結可讓項目定義輸入手勢 (Ctrl+N) 與命令 (New) 之間的對應。 輸入手勢和命令定義都是可以擴充的，而且可以在使用階段連接在一起。 例如，這會讓允許使用者自訂其想要在應用程式內使用的重要繫結變得簡單。  
  
 在這一主題中，WPF 的"核心"功能（在演示核心程式集中實現的功能）一直是焦點。 構建 WPF 時，基礎部分（如使用**度量**和**排列**的佈局合同）和框架部分（如特定佈局（如<xref:System.Windows.Controls.Grid>等佈局的實現）之間的乾淨分離是預期的結果。 目標是提供堆疊低層的擴充點，以讓外部開發人員視需要建立其專屬架構。  
  
<a name="System_Windows_FrameworkElement"></a>
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>可以從兩種不同的方式看待。 它引入了一群組原則和自訂，這些子系統位於 WPF 的下層中。 它同時引進一組新的子系統。  
  
 引入<xref:System.Windows.FrameworkElement>的主要策略是圍繞應用程式佈局。 <xref:System.Windows.FrameworkElement>基於由引入<xref:System.Windows.UIElement>的基本佈局協定構建，並添加了佈局"槽"的概念，使佈局作者更容易具有一組一致的屬性驅動的佈局語義。 屬性（<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>例如<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.FrameworkElement.MinWidth%2A>，<xref:System.Windows.FrameworkElement.Margin%2A>和 （僅舉幾例） 提供從<xref:System.Windows.FrameworkElement>佈局容器內的一致行為派生的所有元件。  
  
 <xref:System.Windows.FrameworkElement>還提供了更容易的 API 暴露到 WPF 核心層中的許多功能。 例如，<xref:System.Windows.FrameworkElement>通過 方法提供對動畫的直接<xref:System.Windows.FrameworkElement.BeginStoryboard%2A>訪問。 提供了<xref:System.Windows.Media.Animation.Storyboard>一種針對一組屬性編寫多個動畫的腳本的方法。  
  
 <xref:System.Windows.FrameworkElement>引入的兩個最關鍵的事情是資料繫結和樣式。  
  
 WPF 中的資料繫結子系統對於使用 Windows 表單或ASP.NET創建應用程式[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]的人應相對熟悉。 在所有這些系統中，有一種簡單的方式可表示您想要一或多個屬性從指定的項目繫結至資料的某個部分。 WPF 完全支援屬性綁定、轉換和清單綁定。  
  
 WPF 中資料繫結最有趣的功能之一是引入資料範本。 資料範本可讓您以宣告方式指定應該如何視覺化資料。 您可以解決問題，並讓資料判斷將建立的顯示，而不是建立可繫結至資料的自訂使用者介面。  
  
 樣式實際上是簡單形式的資料繫結。 使用樣式，您可以將共用定義中的一組屬性繫結至項目的一或多個執行個體。 樣式通過顯式引用（通過設置<xref:System.Windows.FrameworkElement.Style%2A>屬性）或通過將樣式與元素的 CLR 類型關聯而隱式應用於元素。  
  
<a name="System_Windows_Controls_Control"></a>
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 控制項的最重要功能是設定範本。 如果您將 WPF 的組合系統視為保留模式轉譯系統，則設定範本可讓控制項透過參數化宣告方式描述其轉譯。 實際上<xref:System.Windows.Controls.ControlTemplate>，A 只不過是一個腳本來創建一組子項目，該元素具有控制項提供的屬性的綁定。  
  
 <xref:System.Windows.Controls.Control>提供了一組股票屬性<xref:System.Windows.Controls.Control.Foreground%2A>，<xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Control.Padding%2A>僅舉幾例，範本作者隨後可以使用這些屬性自訂控制項的顯示。 控制項的實作會提供資料模型和互動模型。 互動模型定義一組命令 (例如視窗的 Close) 以及輸入手勢的繫結 (例如按一下視窗右上角的紅色 X)。 資料模型提供一組屬性來自訂互動模型或是自訂顯示 (透過範本決定)。  
  
 資料模型 (屬性)、互動模型 (命令和事件) 與顯示模型 (範本) 之間的這項分割可啟用控制項外觀和行為的完整自訂。  
  
 控制項資料模型的一般層面是內容模型。 如果查看控制項（如<xref:System.Windows.Controls.Button>），您將看到其具有名為"內容"的類型<xref:System.Object>屬性。 在 Windows 表單和ASP.NET中，此屬性通常是字串，但是這限制了可以放入按鈕的內容類型。 按鈕的內容可以是簡單字串、複雜資料物件或整個項目樹狀結構。 如果是資料物件，則使用資料範本來建構顯示。  
  
<a name="Summary"></a>
## <a name="summary"></a>摘要  
 WPF 旨在允許您創建動態資料驅動的演示系統。 系統的每個組件都是設計成透過可驅動行為的屬性集來建立物件。 資料繫結是系統的基礎部分，並且在各層級進行整合。  
  
 傳統應用程式會建立顯示，然後繫結至一些資料。 在 WPF 中，有關控制項的所有內容（顯示的各個方面）都由某種類型的資料繫結生成。 在按鈕內建立組合的控制項，並將其顯示繫結至按鈕的內容屬性，即會顯示在按鈕內找到的文字。  
  
 當您開始開發基於 WPF 的應用程式時，它應該感覺非常熟悉。 您可以設置屬性、使用物件和資料繫結的方式與使用 Windows 表單或ASP.NET大致相同。 通過對 WPF 體系結構的更深入調查，您會發現存在創建更豐富的應用程式的可能性，這些應用程式從根本上將資料視為應用程式的核心驅動因素。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [版面配置](layout.md)
- [動畫概觀](../graphics-multimedia/animation-overview.md)
