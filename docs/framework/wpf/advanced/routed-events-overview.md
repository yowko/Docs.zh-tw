---
title: 路由事件概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached events [WPF]
- grouped button set [WPF]
- routed events [WPF]
- events [WPF], routed
- tunneling [WPF]
- events [WPF], attached
- routing strategies for events [WPF]
- button set [WPF], grouped
- bubbling [WPF]
ms.assetid: 1a2189ae-13b4-45b0-b12c-8de2e49c29d2
ms.openlocfilehash: 24fa283ec0c1fef2023845df0a05c3f1ebf5df06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400747"
---
# <a name="routed-events-overview"></a>路由事件概觀

本主題說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中路由事件的概念。 本主題會定義路由事件的術語、說明如何透過元素的樹狀結構路由傳送路由事件、摘要說明如何處理路由事件，以及介紹如何建立您自己的自訂路由事件。

<a name="prerequisites"></a>

## <a name="prerequisites"></a>必要條件

本主題假設您具備 common language runtime (CLR) 和麵向物件程式設計的基本知識, 以及如何將元素之間[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的關聯性概念化為樹狀結構的概念。 若要遵循本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，並知道如何撰寫非常基本的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式或頁面。 如需詳細資訊，請參閱[逐步解說：我的第一個 WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)桌面應用程式和[XAML 總覽 (WPF)](xaml-overview-wpf.md)。

<a name="routing"></a>

## <a name="what-is-a-routed-event"></a>什麼是路由事件？

您可以從功能或實作觀點來考量路由事件。 此處說明這兩個定義，讓使用者能夠選擇較實用的定義。

功能定義:路由事件是一種事件種類, 可以在專案樹狀結構中的多個接聽程式上叫用處理程式, 而不只是在引發事件的物件上叫用。

執行定義:路由事件是由<xref:System.Windows.RoutedEvent>類別的實例所支援的 CLR 事件, 並[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]由事件系統處理。

一般的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式包含許多元素。 不論是在程式碼中建立或是在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中宣告，這些元素均存在於彼此間的元素樹狀結構關聯性中。 事件路由的周遊方向取決於事件定義，但通常路由會從來源元素開始周遊，然後透過元素樹狀結構向上執行「事件反昇」，直到它到達元素樹狀結構根元素 (通常是頁面或視窗) 為止。 如果您先前曾用過 DHTML 物件模型，可能很熟悉這個事件反昇概念。

請考慮下列簡單的元素樹狀結構：

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

這個元素樹狀結構會產生如下的畫面：

![[是]、[否] 和 [取消] 按鈕](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")

在這個簡化的元素樹狀結構中, <xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件的來源是其中一個<xref:System.Windows.Controls.Button>專案, 而<xref:System.Windows.Controls.Button>按下的是第一個有機會處理事件的元素。 但是, 如果未附加至事件<xref:System.Windows.Controls.Button>的處理常式, 則事件會向上反升<xref:System.Windows.Controls.Button>至專案<xref:System.Windows.Controls.StackPanel>樹狀結構中的父系, 也就是。 可能的話, 事件會冒泡<xref:System.Windows.Controls.Border>到, 然後再到專案樹狀結構的頁面根目錄 (未顯示)。

換句話說, 此<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件的事件路由為:

Button-->StackPanel-->Border-->...

### <a name="top-level-scenarios-for-routed-events"></a>路由事件的最上層案例

以下是引發路由事件概念之案例的簡短摘要, 以及為什麼一般 CLR 事件無法滿足這些案例的原因:

**控制項撰寫和封裝:** 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的各種控制項都有豐富的內容模型。 例如, 您可以將影像放在<xref:System.Windows.Controls.Button>中, 以有效地擴充按鈕的視覺化樹狀結構。 不過, 新增的映射不能中斷導致按鈕回應<xref:System.Windows.Controls.Primitives.ButtonBase.Click>其內容的點擊測試行為, 即使使用者按一下的是影像中技術上的圖元。

**單數處理常式附加點:** 在[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]中, 您必須多次附加相同的處理常式, 以處理可從多個元素引發的事件。 路由事件可讓您只需附加該處理常式一次 (如上一個範例中所示)，然後就能視需要使用處理常式邏輯判斷此事件來自何處。 例如，這可能是先前所示之 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的處理常式：

[!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
[!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]

**類別處理:** 路由事件允許由類別定義的靜態處理常式。 這個類別處理常式有機會在任何附加的執行個體處理常式之前處理事件。

**參考不含反映的事件:** 某些程式碼和標記技術需要一個可識別特定事件的方式。 路由事件會建立一個<xref:System.Windows.RoutedEvent>欄位做為識別碼, 以提供健全的事件識別技術, 不需要靜態或執行時間反映。

### <a name="how-routed-events-are-implemented"></a>路由事件的實作方式

路由事件是一個 CLR 事件, 它是由<xref:System.Windows.RoutedEvent>類別的實例所支援, 並已向[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]事件系統註冊。 從<xref:System.Windows.RoutedEvent>註冊取得的實例通常會保留`public` `static` `readonly`為類別的欄位成員, 註冊並因此「擁有」路由事件。 與相同名稱 clr 事件 (有時稱為「包裝函式」事件) 的連接是藉由覆寫 clr 事件`add`的`remove`和實作為來完成。 一般而言，`add` 和 `remove` 會保留為隱含的預設值，以使用適當的語言特定事件語法來加入和移除該事件的處理常式。 路由事件的支援和連接機制在概念上類似于相依性屬性是由<xref:System.Windows.DependencyProperty>類別支援並向[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性系統註冊的 CLR 屬性。

下列範例顯示`Tap`自訂路由事件的宣告, 包括註冊和公開<xref:System.Windows.RoutedEvent> [識別碼] 欄位, 以及`Tap` CLR 事件的`add`和`remove` [執行]。

[!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
[!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]

### <a name="routed-event-handlers-and-xaml"></a>路由事件處理常式和 XAML

若要使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 加入事件的處理常式，您可以宣告事件名稱做為屬於事件接聽程式之元素上的屬性。 屬性的值是您所實作之處理常式方法的名稱，此名稱必須存在於程式碼後置檔案的部分類別中。

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

加入標準 CLR 事件處理常式的語法和加入路由事件處理常式相同,因為您實際上是將處理常式加入至CLR事件包裝函式,其底下會有路由事件執行。[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 如需在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中加入事件處理常式的詳細資訊，請參閱 [XAML 概觀 (WPF)](xaml-overview-wpf.md)。

<a name="routing_strategies"></a>

## <a name="routing-strategies"></a>路由傳送策略

路由事件會使用下列其中一個路由傳送策略：

- **路由**系統會叫用事件來源上的事件處理常式。 路由事件接著會路由傳送到後續的父元素，直到其到達元素樹狀結構的根元素為止。 大部分的路由事件會使用事件反昇路由傳送策略。 事件反昇的路由事件通常是用來報告來自不同控制項或其他 UI 元素的輸入或狀態變更。

- **直銷**只有來源元素本身會有機會在回應中叫用處理程式。 這類似於 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 針對事件所使用的「路由傳送」。 不過, 與標準 CLR 事件不同的是, 直接路由事件支援類別處理 (下一節會說明類別處理), 而且可供<xref:System.Windows.EventSetter>和<xref:System.Windows.EventTrigger>使用。

- **建立**一開始, 會叫用元素樹狀結構根目錄的事件處理常式。 路由事件接著會在路由中朝向屬於路由事件來源的節點元素 (會引發路由事件的元素) 移動，以透過後續的子元素周遊該路由。 通道路由事件時常會做為複合控制項的一部分來使用或處理，這類來自複合組件的事件可利用專用於該完整控制項的事件來刻意隱藏或取代。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中提供的輸入事件通常會實作為成對的通道/事件反昇組合。 由於用於配對的命名慣例，通道事件有時也稱為預覽事件。

<a name="why_use"></a>

## <a name="why-use-routed-events"></a>為什麼要使用路由事件？

身為應用程式開發人員，您不一定需要知道或在意要將您正在處理的事件實作為路由事件。 路由事件都有特殊的行為，但是，如果您正在引發事件的元素上處理該事件，則大多不會看見該行為。

路由事件變成功能強大之處在於，您是否使用任何建議的案例︰在一般的根元素上定義一般的處理常式、組合自己的控制項，或定義自己的控制項類別。

路由事件接聽程式和路由事件來源不需要在其階層中共用一般事件。 Any <xref:System.Windows.UIElement> 或<xref:System.Windows.ContentElement>可以是任何路由事件的事件接聽程式。 因此, 您可以在整個工作 API 集內使用完整的路由事件集, 做為概念「介面」, 讓應用程式中的不同元素可以交換事件資訊。 路由事件的這個「介面」概念特別適用於輸入事件。

路由事件也可用來透過元素樹狀結構進行通訊，因為事件的事件資料會永久存在於路由的每個元素中。 一個元素可以變更事件資料中的某些內容，而該變更可供路由中的下一個元素使用。

除了路由的外觀以外, 還有其他兩個原因, 表示任何[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]指定的事件可能會實作為路由事件, 而不是標準 CLR 事件。 如果您要實作自己的事件，也可以考慮這些準則：

- 某些[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]樣式設定和範本化功能<xref:System.Windows.EventSetter> ( <xref:System.Windows.EventTrigger>例如和) 會要求參考的事件為路由事件。 這是先前所述的事件識別碼案例。

- 路由事件支援類別處理機制，此類別可藉以指定靜態方法，有機會在任何已註冊的執行個體處理常式可存取路由事件之前處理它們。 這在控制項設計中非常有用，因為您的類別可以強制執行事件驅動的類別行為，您無法藉由處理執行個體上的事件來附帶隱藏這類行為。

上述每個考量都會在本主題的不同小節中加以討論。

<a name="event_handing"></a>

## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>加入和實作路由事件的事件處理常式

若要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中加入事件處理常式，您只需將事件名稱加入至元素做為屬性，並將屬性值設為實作適當委派的事件處理常式名稱，如下列範例所示。

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

`b1SetColor`這是已執行的處理常式名稱, 其中包含處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件的程式碼。 `b1SetColor`必須具有與<xref:System.Windows.RoutedEventHandler>委派相同的簽章, 也就是<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件的事件處理常式委派。 所有路由事件處理常式委派的第一個參數會指定要加入事件處理常式的元素，而第二個參數會指定事件的資料。

[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]

<xref:System.Windows.RoutedEventHandler>是基本路由事件處理常式委派。 如果是針對特定控制項或案例特製化的路由事件，用於路由事件處理常式的委派也可能會變得更特製化，讓它們能夠傳輸特製化的事件資料。 例如, 在一般輸入案例中, 您可能會處理<xref:System.Windows.UIElement.DragEnter>路由事件。 您的<xref:System.Windows.DragEventHandler>處理常式應該會執行委派。 藉由使用最特定的委派, 您可以<xref:System.Windows.DragEventArgs>在處理常式中處理, 並<xref:System.Windows.DragEventArgs.Data%2A>讀取屬性, 其中包含拖曳作業的剪貼簿承載。

如需如何使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來將事件處理常式加入至元素的完整範例，請參閱[處理路由事件](how-to-handle-a-routed-event.md)。

在使用程式碼建立的應用程式中加入路由事件的處理常式很簡單。 路由事件處理常式一律可以透過 helper 方法<xref:System.Windows.UIElement.AddHandler%2A>加入 (這與現有的支援所`add`呼叫的方法相同)。不過，現有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 路由事件通常支援實作 `add` 和 `remove` 邏輯，以允許透過語言特有的事件語法來加入路由事件的處理常式，此語法是比 Helper 方法更直覺的語法。 以下是 Helper 方法的使用方式範例：

[!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
[!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]

下一個範例顯示C#運算子語法 (Visual Basic 因其對取值的處理而略有不同的運算子語法):

[!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
[!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]

如需如何在程式碼中加入事件處理常式的範例，請參閱[使用程式碼加入事件處理常式](how-to-add-an-event-handler-using-code.md)。

如果您使用 Visual Basic, 您也可以使用`Handles`關鍵字, 在處理常式宣告中加入處理常式。 如需詳細資訊，請參閱 [Visual Basic 和 WPF 事件處理](visual-basic-and-wpf-event-handling.md)。

<a name="concept_handled"></a>

### <a name="the-concept-of-handled"></a>已處理的概念

所有路由事件都會共用一個通用的事件資料基類<xref:System.Windows.RoutedEventArgs>。 <xref:System.Windows.RoutedEventArgs>定義接受<xref:System.Windows.RoutedEventArgs.Handled%2A>布林值的屬性。 <xref:System.Windows.RoutedEventArgs.Handled%2A>屬性的用途是將的值<xref:System.Windows.RoutedEventArgs.Handled%2A>設定為`true`, 以啟用沿著路由的任何事件處理常式, 以將路由事件標示為已*處理*。 透過處理常式在路由中的某一個元素上進行處理之後，就會再次向路由中的每一個接聽程式報告共用的事件資料。

的值<xref:System.Windows.RoutedEventArgs.Handled%2A>會影響路由事件在路由中進一步傳遞時的報告或處理方式。 如果<xref:System.Windows.RoutedEventArgs.Handled%2A> 是`true`在路由事件的事件資料中, 則通常不會再針對該特定事件實例叫用接聽其他元素上之路由事件的處理常式。 此情況適用於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中附加的處理常式，以及適用於利用語言特定之事件處理常式附加語法 (例如 `+=` 或 `Handles`) 所加入的處理常式。 在大部分常見的處理常式案例中, 將設定<xref:System.Windows.RoutedEventArgs.Handled%2A>為`true`所處理的事件標示為將會針對通道路由或反升路由進行「停止」路由, 也適用于在路由中由類別處理常式在某個點上處理的任何事件。

不過, 有一個「handledEventsToo」機制, 接聽程式仍然可以執行處理常式, 以回應事件資料<xref:System.Windows.RoutedEventArgs.Handled%2A> `true`中的路由事件。 換句話說，事件路由無法藉由將事件資料標示為已處理來真正停止。 您只能在程式<xref:System.Windows.EventSetter>代碼或中使用 handledEventsToo 機制:

- 在程式碼中, 不要使用適用于一般 CLR 事件的語言特定事件語法, 而是呼叫[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]方法<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>來新增您的處理常式。 將 `handledEventsToo` 的值指定為 `true`。

- 在中<xref:System.Windows.EventSetter.HandledEventsToo%2A> `true`, 將屬性設定為。 <xref:System.Windows.EventSetter>

除了<xref:System.Windows.RoutedEventArgs.Handled%2A>狀態在路由事件中產生的行為之外, 的<xref:System.Windows.RoutedEventArgs.Handled%2A>概念也會影響您應該如何設計應用程式並撰寫事件處理常式程式碼。 您可以將<xref:System.Windows.RoutedEventArgs.Handled%2A>概念理解為路由事件所公開的簡單通訊協定。 您可以自行決定如何使用此通訊協定, 但要如何使用其值<xref:System.Windows.RoutedEventArgs.Handled%2A>的概念設計如下所示:

- 如果將路由事件標示為已處理，則不需再次透過該路由中的其他元素來處理它。

- 如果路由事件未標示為已處理, 則先前在路由中的其他接聽程式已選擇不註冊處理常式, 或已註冊的處理常式選擇不要操作事件資料, 並將設定<xref:System.Windows.RoutedEventArgs.Handled%2A>為。 `true` (或者，當然有可能目前的接聽程式為路由中的第一個點)。目前接聽程式上的處理常式現在有三個可能的做法：

  - 不採取任何動作；事件會保持未處理狀態，而事件會路由傳送到下一個接聽程式。

  - 執行程式碼以回應事件，但判定採取的動作後續不足以保證會將事件標示為已處理。 事件會路由傳送到下一個接聽程式。

  - 執行程式碼以回應事件。 在傳遞至處理常式的事件資料中將事件標示為已處理，因為已將所採取的動作視為後續不足以保證會標示為已處理。 事件仍會路由至下一個接聽程式, 但<xref:System.Windows.RoutedEventArgs.Handled%2A>在其事件資料中, 因此`handledEventsToo`只有接聽項有機會叫用= `true`進一步的處理常式。

這個概念設計會由先前所述的路由行為加強: 更難以 (雖然程式碼或樣式中仍然可行) 附加路由事件的處理常式, 即使已經設定<xref:System.Windows.RoutedEventArgs.Handled%2A>了路由的先前處理常式也是一樣。至`true`。

如需有關<xref:System.Windows.RoutedEventArgs.Handled%2A>的詳細資訊、路由事件的類別處理, 以及有關將路由事件標示為<xref:System.Windows.RoutedEventArgs.Handled%2A>時的建議事項, 請參閱將[路由事件標示為已處理, 以及類別處理](marking-routed-events-as-handled-and-class-handling.md)。

在應用程式中，只在引發事件反昇路由事件的物件上處理該事件是相當常見的，而這並不完全與事件的路由特性有關。 不過，它仍是在事件資料中將路由事件標示為已處理的最佳做法，萬一元素樹狀結構中進一步向上的元素也具有已針對該相同路由事件附加的處理常式時，可避免發生未預期的副作用。

<a name="class_handlers"></a>

## <a name="class-handlers"></a>類別處理常式

如果您要定義從<xref:System.Windows.DependencyObject>某種方式衍生的類別, 您也可以針對屬於類別之已宣告或繼承事件成員的路由事件定義和附加類別處理常式。 每當路由事件到達其路由中的元素執行個體時，就可以在任何附加至該類別執行個體的執行個體接聽程式處理常式之前叫用類別處理常式。

某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項具有適用於特定路由事件的繼承類別處理。 這可能會造成表面上未曾引發過路由事件，但實際上卻已處理過類別的情況，而且，如果您使用某些技術，您的執行個體處理常式可能仍會處理該路由事件。 此外，許多基底類別和控制項會公開可用於覆寫類別處理行為的虛擬方法。 如需如何因應不想要的類別處理，並在自訂類別中定義您自己之類別處理的詳細資訊，請參閱[將路由事件標記為已處理以及類別處理](marking-routed-events-as-handled-and-class-handling.md)。

<a name="attached_events"></a>

## <a name="attached-events-in-wpf"></a>在 WPF 中附加事件

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語言也會定義稱為「附加事件」的特定事件類型。 附加事件可讓您將特殊事件的處理常式加入至任意元素。 處理事件的元素不需要定義或繼承附加事件，而物件不可能引發事件，且目的地處理執行個體也不需定義或「擁有」該事件做為類別成員。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 輸入系統會廣泛使用附加事件。 不過，幾乎這所有的附加事件都會轉送到基底元素。 輸入事件接著會顯示為對等的非附加路由事件，其為基底元素類別的成員。 例如, 基礎附加事件<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>可以在任何指定<xref:System.Windows.UIElement>的上使用<xref:System.Windows.UIElement.MouseDown>來處理, 而不是在<xref:System.Windows.UIElement>或程式碼中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理附加事件語法。

如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中附加事件的詳細資訊，請參閱[附加事件概觀](attached-events-overview.md)。

<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>

## <a name="qualified-event-names-in-xaml"></a>XAML 中的完整事件名稱

類似 *typename*.*eventname* 附加事件語法的另一種語法用法 (但嚴格來說，它不是附加事件的使用方式) 是，當您連接由子元素所引發之路由事件的處理常式時。 您可將處理常式附加到共同父項，以利用事件路由，即使共同父項可能沒有相關的路由事件做為成員。 再看一下這個範例：

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

在此, 會將處理常式加入其中的父項目接聽<xref:System.Windows.Controls.StackPanel>項為。 不過, 它會加入已宣告之路由事件的處理常式, 而且會由<xref:System.Windows.Controls.Button>類別引發 (<xref:System.Windows.Controls.Primitives.ButtonBase> <xref:System.Windows.Controls.Button>實際上是, 但可透過繼承)。 <xref:System.Windows.Controls.Button>「擁有」事件, 但路由事件系統允許將任何路由事件的處理常式附加至任何<xref:System.Windows.UIElement>可能附加 common language runtime (CLR) 事件之接聽程式的或<xref:System.Windows.ContentElement>實例接聽程式。 這些完整事件屬性名稱的預設 xmlns 命名空間通常是預設的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] xmlns 命名空間，但您也可以針對自訂路由事件指定有前置詞的命名空間。 如需 xmlns 的詳細資訊，請參閱 [WPF XAML 的 XAML 命名空間和命名空間對應](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。

<a name="how_event_processing_works"></a>

## <a name="wpf-input-events"></a>WPF 輸入事件

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 平台中有一個路由事件的常用應用程式適用於輸入事件。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，通道路由事件名稱前面依慣例會加上 "Preview" 這個字。 輸入事件通常會成對出現，其中一個是事件反昇事件，另一個則是通道事件。 例如, <xref:System.Windows.ContentElement.KeyDown>事件<xref:System.Windows.ContentElement.PreviewKeyDown>和事件具有相同的簽章, 而前者是反升輸入事件, 後者則是通道輸入事件。 有時，輸入事件只會有事件反昇版本，或可能只有直接路由版本。 在文件中，路由事件主題會交互參考具備替代路由傳送策略的類似路由事件 (如果這類路由事件存在)，而受管理參考頁面中的章節會釐清每個路由事件的路由傳送策略。

系統會實作成對出現的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 輸入事件，讓來自輸入的單一使用者動作 (例如按下滑鼠按鈕) 將依序引發配對中的這兩個路由事件。 首先，引發通道事件，並周遊其路由。 接著，引發事件反昇事件，並周遊其路由。 這兩個事件實際上會共用相同的事件資料實例, <xref:System.Windows.UIElement.RaiseEvent%2A>因為引發反升事件的實類別中的方法呼叫會接聽來自通道事件的事件資料, 並在新引發的事件中重複使用它。 具有通道事件處理常式的接聽程式有機會優先將路由事件標示為已處理 (第一個是類別處理常式，然後是執行個體處理常式)。 如果將通道路由中的元素標示為已處理，則已經處理的事件資料就會針對事件反昇事件進行傳送，而且將不會叫用基於對等事件反昇輸入事件附加的一般處理常式。 表面上來看，就如同未曾引發過已處理的事件反昇事件。 這個處理行為非常適用於控制項複合，您可能想要讓您的最終控制項 (而不是它的複合組件) 報告所有以點擊測試為基礎的輸入事件或以焦點為基礎的輸入事件。 最後一個控制項元素更接近複合中的根元素，因此有機會優先對通道事件進行類別處理，而且，或許可利用更專屬於控制項的事件，做為支援控制項類別的程式碼一部分來「取代」該路由事件。

如需輸入事件處理如何運作的圖表說明，請考量下列輸入事件範例。 在下列樹狀結構圖例中`leaf element #2` , 是`PreviewMouseDown`和`MouseDown`事件的來源:

![事件路由圖表](./media/routed-events-overview/input-event-routing.png)

事件處理的順序如下：

1. 根元素上的 `PreviewMouseDown` (通道)。

2. 中繼元素 #1 上的 `PreviewMouseDown` (通道)。

3. 來源元素 #2 上的 `PreviewMouseDown` (通道)。

4. 來源元素 #2 上的 `MouseDown` (事件反昇)。

5. 中繼元素 #1 上的 `MouseDown` (事件反昇)。

6. 根元素上的 `MouseDown` (事件反昇)。

路由事件處理常式委派提供對兩個物件的參考︰引發事件的物件，以及已叫用處理常式的物件。 已叫用處理常式的物件是 `sender` 參數所報告的物件。 第一次引發事件的物件是由事件資料中<xref:System.Windows.RoutedEventArgs.Source%2A>的屬性所報告。 路由事件仍然可以由相同的物件引發和處理, 在這種情況下`sender` , <xref:System.Windows.RoutedEventArgs.Source%2A>和都相同 (在事件處理範例清單中, 步驟3和4的情況如下)。

因為通道和反升, 父元素會收到輸入事件, <xref:System.Windows.RoutedEventArgs.Source%2A>其中是其子專案的其中一個。 當您瞭解來源元素為何時, 您可以藉由存取<xref:System.Windows.RoutedEventArgs.Source%2A>屬性來識別來源元素。

通常, 一旦標示<xref:System.Windows.RoutedEventArgs.Handled%2A>輸入事件之後, 就不會叫用進一步的處理常式。 一般而言，您應該在叫用處理常式來處理代表輸入事件意義之應用程式特定的邏輯處理之後，儘速將輸入事件標示為已處理。

此一般語句關於<xref:System.Windows.RoutedEventArgs.Handled%2A>狀態的例外狀況, 是為了刻意忽略<xref:System.Windows.RoutedEventArgs.Handled%2A>事件資料狀態的輸入事件處理常式, 仍然會沿著任一路由叫用。 如需詳細資訊，請參閱[預覽事件](preview-events.md)或[將路由事件標記為已處理以及類別處理](marking-routed-events-as-handled-and-class-handling.md)。

通道事件與事件反昇事件之間共用的事件資料模型，以及後續引發的第一個通道事件，然後是事件反昇事件，不是一般適用於所有路由事件的概念。 該行為特別是透過 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 輸入裝置如何選擇引發並連接輸入事件配對的方式來實作。 實作您自己的輸入事件是一個進階案例，但您也可以選擇針對自己的輸入事件遵循該模型。

某些類別會選擇對特定輸入事件進行類別處理，一般的用意是重新定義特定使用者驅動的輸入事件在該控制項內所代表的意義，然後引發新的事件。 如需詳細資訊，請參閱[將路由事件標記為已處理以及類別處理](marking-routed-events-as-handled-and-class-handling.md)。

如需輸入以及在一般應用程式案例中輸入如何與事件互動的詳細資訊，請參閱[輸入概觀](input-overview.md)。

<a name="events_styles"></a>

## <a name="eventsetters-and-eventtriggers"></a>EventSetters 和 EventTriggers

在樣式中, 您可以[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.EventSetter>使用, 在標記中包含一些預先宣告的事件處理語法。 套用樣式時，會將參考的處理常式加入至樣式執行個體。 <xref:System.Windows.EventSetter>您只能針對路由事件宣告。 下列為範例。 請注意，此處參考的 `b1SetColor` 方法位於程式碼後置檔案中。

[!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]

這裡所得到的優點是, 樣式可能包含許多其他資訊, 可套用至應用程式中的任何按鈕, 而讓<xref:System.Windows.EventSetter>成為該樣式的一部分, 即使在標記層級也能重複使用程式碼。 此外, <xref:System.Windows.EventSetter>處理常式的抽象方法名稱會從一般應用程式和頁面標記進一步執行。

另一個結合的路由事件和動畫功能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的特製化語法<xref:System.Windows.EventTrigger>是。 如同, 只有路由事件可以用於<xref:System.Windows.EventTrigger>。 <xref:System.Windows.EventSetter> 通常會將宣告為樣式的一部分, <xref:System.Windows.EventTrigger>但也可以在頁面層級專案上宣告為<xref:System.Windows.FrameworkElement.Triggers%2A>集合的一部分, 或在中<xref:System.Windows.Controls.ControlTemplate>宣告。 <xref:System.Windows.EventTrigger> 可讓您<xref:System.Windows.Media.Animation.Storyboard>指定在路由事件到達<xref:System.Windows.EventTrigger>其路由中宣告該事件之專案的時執行的。 <xref:System.Windows.EventTrigger> 除了處理事件並<xref:System.Windows.EventTrigger>使其啟動現有的分鏡腳本之外, 的優點是<xref:System.Windows.EventTrigger> , 可讓您更有效地控制腳本和其執行時間行為。 如需詳細資訊，請參閱[在分鏡腳本開始後使用事件觸發程式進行控制](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。

<a name="more_about"></a>

## <a name="more-about-routed-events"></a>深入了解路由事件

本主題主要是從描述基本概念並提供如何及何時回應路由事件的觀點來討論路由事件，而路由事件已經存在於各種基底元素和控制項中。 不過，您可以在自訂類別上建立自己的路由事件以及所有必要的支援，例如特製化的事件資料類別和委派。 路由事件擁有者可以是任何類別, 但路由事件必須由引發並由<xref:System.Windows.UIElement>或<xref:System.Windows.ContentElement>衍生類別處理, 才能發揮效用。 如需自訂事件的詳細資訊，請參閱[建立自訂路由事件](how-to-create-a-custom-routed-event.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.EventManager>
- <xref:System.Windows.RoutedEvent>
- <xref:System.Windows.RoutedEventArgs>
- [將路由事件標記為已處理以及類別處理](marking-routed-events-as-handled-and-class-handling.md)
- [輸入概觀](input-overview.md)
- [命令概觀](commanding-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [WPF 中的樹狀結構](trees-in-wpf.md)
- [弱式事件模式](weak-event-patterns.md)
