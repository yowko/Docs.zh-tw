---
title: "路由事件概觀 | Microsoft Docs"
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
  - "附加事件"
  - "反昇"
  - "按鈕設定, 群組"
  - "事件, 附加"
  - "事件, 路由"
  - "群組的按鈕設定"
  - "路由事件"
  - "事件的路由策略"
  - "通道"
ms.assetid: 1a2189ae-13b4-45b0-b12c-8de2e49c29d2
caps.latest.revision: 29
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 28
---
# 路由事件概觀
本主題說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的路由事件概念。  本主題會定義路由事件的術語、說明路由事件是如何透過項目樹狀結構路由傳送的、摘要說明如何處理路由事件，以及簡介說明如何建立自己的自訂路由事件。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您具有 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 和物件導向程式設計的基本知識，以及 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目間的關係如何能夠以樹狀結構的方式概念化的觀念。  為了能夠理解本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，並知道如何撰寫基礎的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式或網頁。  如需詳細資訊，請參閱 [逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) 和 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
<a name="routing"></a>   
## 什麼是路由事件  
 您可以從功能面或是從實作面來想像路由事件。  這裡同時陳述這兩種定義，因為不同人對於哪種定義較為實用的看法各有不同。  
  
 功能定義：路由事件這種事件類型可以在項目樹狀結構的多個接聽項上叫用處理常式，而非僅能在引發事件的物件上叫用。  
  
 實作定義：[路由事件](GTMT)是一種 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件，受到 <xref:System.Windows.RoutedEvent> 類別的執行個體所支援，並且由 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 事件系統所處理。  
  
 一般的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式包含許多項目。  不論是在程式碼中建立的，或是在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中宣告的，這些項目在項目樹狀結構中都彼此關聯著。  依據事件的定義，事件路由可以向兩個方向中的一個前進，但一般而言，路由會從來源項目出發前進，然後透過項目樹狀結構反昇 \(Bubble\) 向上，直到抵達項目樹狀結構的根項目 \(通常是頁面或視窗\)。  如果您過去曾經使用 DHTML 物件模型，那麼對這個反昇概念應該不陌生。  
  
 請考慮下列簡單項目樹狀結構：  
  
 [!code-xml[EventOvwSupport#GroupButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 這個項目樹狀結構會產生類似下列的情形：  
  
 ![是、否和取消按鈕](../../../../docs/framework/wpf/advanced/media/routedevent-ovw-1.png "RoutedEvent\_ovw\_1")  
  
 在這個簡化的項目樹狀結構中，<xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的來源是其中一個 <xref:System.Windows.Controls.Button> 項目，不論按下哪個 <xref:System.Windows.Controls.Button>，該項目就有機會成為處理事件的第一個項目。  但如果 <xref:System.Windows.Controls.Button> 所附加的處理常式都不會對該事件有反應，則事件會反昇至項目樹狀結構中的 <xref:System.Windows.Controls.Button> 父項目，也就是 <xref:System.Windows.Controls.StackPanel>。  也有可能事件會反昇至 <xref:System.Windows.Controls.Border>，然後超出項目樹狀結構的頁面根項目 \(未顯示\) 範圍。  
  
 換句話說，這個 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的事件路由如下：  
  
 Button\-\-\>StackPanel\-\-\>Border\-\-\>...  
  
### 路由事件的最上層案例  
 以下內容將簡短摘要說明促成路由事件概念的案例，以及為何一般的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件無法滿足這些案例。  
  
 **控制項複合和封裝**：[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的各種控制項都具有豐富的內容模型。  舉例來說，將影像置放在 <xref:System.Windows.Controls.Button> 內，即可以有效擴充按鈕的視覺化樹狀結構。  然而，加入的影像不能破壞造成按鈕回應其內容的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 點擊測試 \(Hit Testing\) 行為，就算使用者按下的像素在技術上是影像的一部分。  
  
 **單一處理常式附加點**：[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中，對於可以從多個項目引發的事件，您必須多次附加相同的處理常式才能處理這些事件。  路由事件讓您可以只附加一次該處理常式，再視需要使用處理常式邏輯判斷事件的來源，如先前範例所示。  例如，這可以做為先前顯示的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的處理常式：  
  
 [!code-csharp[EventOvwSupport#GroupButtonCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
 [!code-vb[EventOvwSupport#GroupButtonCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]  
  
 **類別處理**：路由事件允許類別所定義的靜態處理常式。  這個類別處理常式有機會在任何附加的執行個體處理常式進行前，先處理事件。  
  
 **不需反映即可參考事件**：有些程式碼和標記技術需要有識別特定事件的方式。  路由事件會將 <xref:System.Windows.RoutedEvent> 欄位建立為識別項，提供強固的事件識別技術，而不需要靜態或執行階段的反映。  
  
### 路由事件是如何實作的  
 [路由事件](GTMT)是一種 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件，受到 <xref:System.Windows.RoutedEvent> 類別的執行個體所支援，並且由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件系統所註冊。  從註冊取得的 <xref:System.Windows.RoutedEvent> 執行個體，通常會保留成註冊該路由事件進而「擁有」該路由事件的類別的 `public` `static` `readonly` 欄位成員。  對同名 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件 \(有時稱為「包裝函式」事件\) 的連接，是藉由覆寫 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件的 `add` 和 `remove` 實作而達成的。  一般而言，`add` 和 `remove` 是保留為隱含預設值，會使用適當的特定語言事件語法來加入和移除該事件的處理常式。  路由事件的支援和連接機制，在概念上與這種情況類似：[相依性屬性](GTMT) \(Property\) 是一種 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性，受到 <xref:System.Windows.DependencyProperty> 類別所支援，並向 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統註冊。  
  
 下列範例顯示自訂 `Tap` 路由事件的宣告，包括 <xref:System.Windows.RoutedEvent> 識別項欄位的註冊和公開，以及 `Tap` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件的 `add` 和 `remove` 實作。  
  
 [!code-csharp[RoutedEventCustom#AddRemoveHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
 [!code-vb[RoutedEventCustom#AddRemoveHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]  
  
### 路由事件處理常式和 XAML  
 若要使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 加入事件的處理常式，您要在做為事件接聽項的項目上，將事件名稱宣告為屬性 \(Attribute\)。  屬性的值則為實作處理常式方法的名稱，且程式碼後置 \(Code\-Behind\) 檔案的部分類別中必須要有該方法。  
  
 [!code-xml[EventOvwSupport#SimplestSyntax](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 用於加入標準 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件處理常式的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法，與加入路由事件處理常式的語法相同，因為您實際上就是將處理常式加入到其下具有路由事件實作的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件包裝函式中。  如需在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中加入事件處理常式的詳細資訊，請參閱 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
<a name="routing_strategies"></a>   
## 路由策略  
 路由事件使用下列三種路由策略中的一種：  
  
-   **反昇**：會叫用事件來源上的事件處理常式。  路由事件接著會路由至相鄰的父項目，直到抵達項目樹狀結構的根項目。  大部分的路由事件會使用反昇路由策略。  反昇路由事件通常用於回報不同控制項或其他 UI 項目的輸入或狀態變更。  
  
-   **直接**：只有來源項目本身有機會叫用回應的處理常式。  這就好比 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 針對事件使用的「路由」。  但是，跟標準 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件不同的是，直接路由事件支援類別處理 \(在後續的章節將說明類別處理\)，並可以讓 <xref:System.Windows.EventSetter> 和 <xref:System.Windows.EventTrigger> 所使用。  
  
-   **通道**：最初會叫用在項目樹狀結構的根項目上的事件處理常式。  路由事件接著會在路由過程中前進到鄰近的子項目，朝向身為路由事件來源的節點項目 \(即引發路由事件的項目\)。  通道路由事件通常會視為複合控制項的一部分來使用或處理，這樣複合部分的控制項就可以特意隱藏起來，或是使用完整控制項的專屬事件來取代。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中提供的輸入事件的實作，通常會以通道\/反昇配對組的方式進行。  由於用於配對組的命名慣例，通道事件有時候也稱為「預覽」事件。  
  
<a name="why_use"></a>   
## 為何使用路由事件  
 身為應用程式開發人員，您不一定有必要知道或是在意您處理中的事件是否是以路由事件實作的。  路由事件具有特殊的行為，但當您處理的事件就在引發事件的項目上時，您不大會感受到這個行為。  
  
 當您使用下列任何一個建議案例時，路由事件就相當好用：在通用根項目定義通用處理常式、複合自己的控制項，或者是定義自己的自訂控制項類別。  
  
 路由事件接聽項和路由事件來源不需要共用階層架構中的通用事件。  任何 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement> 都可以是任何路由事件的事件接聽項。  因此，您可以使用整個 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 工作組中的可用完整路由事件組做為概念上的「介面」，讓應用程式中的不同項目可以交換事件資訊。  這個路由事件的「介面」概念，對於輸入事件而言特別適用。  
  
 路由事件也可以用於在項目樹狀結構間進行通訊，因為事件的事件資料對路由中的每個項目而言都是永久有效的。  當某個項目變更事件資料中的內容時，該項變更就可以供路由中的下一個項目使用。  
  
 除了路由的觀點外，還有另外兩個原因讓任何指定的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件應該以路由事件實作，而非以標準 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件實作。  當您在實作自己的事件時，也應該考量這些準則：  
  
-   某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 樣式和樣板化功能，例如 <xref:System.Windows.EventSetter> 和 <xref:System.Windows.EventTrigger> 要求參考事件必須是路由事件。  這是稍早提過的事件識別項案例。  
  
-   路由事件支援的類別處理機制，讓類別可以指定靜態方法，有機會在註冊的執行個體處理常式進行存取前，先處理路由事件。  這對於控制項設計非常有用，因為類別可以強制執行事件驅動 \(Event\-Driven\) 的類別行為，讓行為不會因處理執行個體上的事件而意外隱藏。  
  
 上述每個考量都將於本主題的小節中分別討論。  
  
<a name="event_handing"></a>   
## 加入和實作路由事件的事件處理常式  
 若要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中加入事件處理常式，您只需要將事件名稱加入為項目的屬性 \(Attribute\)，並將屬性值設為會實作適當委派的事件處理常式名稱，如以下範例所示。  
  
 [!code-xml[EventOvwSupport#SimplestSyntax](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 `b1SetColor` 是實作的處理常式名稱，所包含的程式碼會處理 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  `b1SetColor` 必須與 <xref:System.Windows.RoutedEventHandler> 委派具有相同的簽章，該委派是 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的事件處理常式委派。  所有路由事件處理常式委派的第一個參數，會指定要加入事件處理常式的項目，而第二個參數則指定事件的資料。  
  
 [!code-csharp[EventOvwSupport#SimpleHandlerA](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
 [!code-vb[EventOvwSupport#SimpleHandlerA](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]  
[!code-csharp[EventOvwSupport#SimpleHandlerB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlerb)]
[!code-vb[EventOvwSupport#SimpleHandlerB](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlerb)]  
  
 <xref:System.Windows.RoutedEventHandler> 是基本的事件處理常式委派。  對於針對某些控制項或案例而特製化的路由事件，用於路由事件處理常式的委派也應該成為特製化的，這樣才能傳輸特製化的事件資料。  例如，在一般的輸入案例中，您可能會處理 <xref:System.Windows.UIElement.DragEnter> 路由事件。  而您的處理常式應該要實作 <xref:System.Windows.DragEventHandler> 委派。  藉由使用這些最為專用的委派，您可以在處理常式中處理 <xref:System.Windows.DragEventArgs>，並讀取 <xref:System.Windows.DragEventArgs.Data%2A> 屬性 \(Property\)，該屬性包含拖曳作業的剪貼簿承載內容。  
  
 如需如何使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 將事件處理常式加入到項目的完整範例，請參閱 [處理路由事件](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)。  
  
 在使用程式碼建立的應用程式中加入路由事件的處理常式，是相當直接的。  路由事件處理常式都可以透過 Helper 方法 <xref:System.Windows.UIElement.AddHandler%2A> \(這是現有支援呼叫 `add` 的相同方法\) 加入。 然而，現有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 路由事件通常都有 `add` 和 `remove` 邏輯的支援實作，讓路由事件的處理常式可以藉由特定語言的事件語法來加入，這跟 Helper 方法比較是更為直覺化的語法。  下列是 Helper 方法的使用範例：  
  
 [!code-csharp[EventOvwSupport#AddHandlerCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
 [!code-vb[EventOvwSupport#AddHandlerCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]  
  
 下一個範例顯示 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 運算子語法 \([!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)] 因為會處理取值 \(Dereferencing\) 而使用不同的運算子語法\)：  
  
 [!code-csharp[EventOvwSupport#AddHandlerPlusEquals](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
 [!code-vb[EventOvwSupport#AddHandlerPlusEquals](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]  
  
 如需如何在程式碼中加入事件處理常式的範例，請參閱 [使用程式碼加入事件處理常式](../../../../docs/framework/wpf/advanced/how-to-add-an-event-handler-using-code.md)。  
  
 如果是使用 [!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)]，您也可以使用 `Handles` 關鍵字，將處理常式加入為處理常式宣告的一部分。  如需詳細資訊，請參閱 [Visual Basic 和 WPF 事件處理](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
<a name="concept_handled"></a>   
### 已處理的概念  
 所有的路由事件都共用通用的事件資料基底類別：<xref:System.Windows.RoutedEventArgs>。  <xref:System.Windows.RoutedEventArgs> 會定義採用布林值的 <xref:System.Windows.RoutedEventArgs.Handled%2A> 屬性 \(Property\)。  <xref:System.Windows.RoutedEventArgs.Handled%2A> 屬性的目的在於讓路由過程的每個事件處理常式，可以將路由事件標記為「*已處理*」\(Handled\)，方法是藉由將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 值設定為 `true`。  當路由過程中的一個項目上的處理常式處理過共用的事件資料後，會再度將資料回報給路由過程的每個接聽項。  
  
 <xref:System.Windows.RoutedEventArgs.Handled%2A> 的值會影響到路由事件在路由過程中前進時的回報或處理方式。  如果路由事件的事件資料中的 <xref:System.Windows.RoutedEventArgs.Handled%2A> 為 `true`，則在其他項目上接聽該路由事件的處理常式，通常都不會再針對該特定事件執行個體進行叫用。  這對於這兩種情況皆成立：[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中附加的處理常式，以及由特定語言事件處理常式附加語法 \(例如 `+=` 或 `Handles`\) 所加入的處理常式。  對於大部分的一般處理常式案例，藉由將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 設定為 `true` 來將事件標記為已處理，將會「停止」通道路由或反昇路由的路由傳送，同時包括由類別處理常式於路由點中處理的任何事件的路由傳送。  
  
 然而，還是有一個 "handledEventsToo" 機制，可以讓接聽項繼續執行處理常式，以回應事件資料中 <xref:System.Windows.RoutedEventArgs.Handled%2A> 為 `true` 的路由事件。  換句話說，路由事件不會因為將事件資料標記為已處理而真正停止下來。  您只可以在程式碼中或是在 <xref:System.Windows.EventSetter> 中使用 handledEventsToo 機制：  
  
-   在程式碼中請改為呼叫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 方法 <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> 來加入處理常式，而不使用適用於一般 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件的特定語言事件語法。  指定 `handledEventsToo` 的值為 `true`。  
  
-   在 <xref:System.Windows.EventSetter> 中，將 <xref:System.Windows.EventSetter.HandledEventsToo%2A> 屬性 \(Attribute\) 設定為 `true`。  
  
 除了在路由事件產生 <xref:System.Windows.RoutedEventArgs.Handled%2A> 狀態的行為外，<xref:System.Windows.RoutedEventArgs.Handled%2A> 的概念也隱含意味著您應該如何設計應用程式和撰寫事件處理常式程式碼。  您可以將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 的概念，想像為路由事件所公開的簡單通訊協定。  至於實際上要如何使用這個通訊協定取決於您自己，不過 <xref:System.Windows.RoutedEventArgs.Handled%2A> 值的設計概念是用於下列情形：  
  
-   如果路由事件標記為已處理，那麼路由過程的其他項目則不需要再度處理該事件。  
  
-   如果路由事件未標記為已處理，那麼路由過程中稍早遇到的其他接聽項，不是選擇不要註冊處理常式，不然就是註冊的處理常式選擇不要操作事件資料並將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 設定為 `true` \(或者，當然也有可能是目前的接聽項是路由中的第一點\)。 目前接聽項的處理常式現在會採取的動作有三個可能：  
  
    -   不進行任何動作：事件維持在未處理，而事件會路由到下一個接聽項。  
  
    -   執行程式碼回應事件，但進行的決定是採取的動作不足以保證讓事件標記為已處理。  事件會路由到下一個接聽項。  
  
    -   執行程式碼回應事件。  在傳遞給處理常式的事件資料中，將事件標記為已處理，因為採取的動作被認定足夠保證標記為已處理。  事件仍然會路由到下一個接聽項，但事件資料中 <xref:System.Windows.RoutedEventArgs.Handled%2A>\=`true`，所有只有 `handledEventsToo` 接聽項有機會叫用進一步的處理常式。  
  
 這個概念設計是藉由前述的路由行為來鞏固的：對於叫用的路由事件，它比較難 \(雖然還是有可能以程式碼或樣式的方式達成\) 附加處理常式，即使路由過程中稍早的處理常式已將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 設定為 `true`。  
  
 如需 <xref:System.Windows.RoutedEventArgs.Handled%2A>、路由事件的類別處理的詳細資訊，以及適合將路由事件標記為 <xref:System.Windows.RoutedEventArgs.Handled%2A> 的時機建議，請參閱[將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)。  
  
 在應用程式中，常常都只有對引發事件的物件處理反昇路由事件，而完全不考慮事件的路由特性。  然而，在事件資料中將路由事件標記為已處理仍然是很好的作法，可以防止未預期的副作用 \(Side Effect\)，以免在項目樹狀結構中前進時所遇到的其他項目，也具有為該相同路由事件附加的處理常式。  
  
<a name="class_handlers"></a>   
## 類別處理常式  
 如果定義的類別是以某種方式衍生自 <xref:System.Windows.DependencyObject>，針對類別的宣告或繼承事件成員的路由事件，您也可以定義和附加其類別處理常式。  類別處理常式的叫用時間，是在附加到該類別的執行個體的任何執行個體接聽項處理常式之前，只要是路由事件抵達路由的項目執行個體的時候。  
  
 某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項對於部分路由事件，本身就具有類別處理作用。  這可能會造成表面上從未引發路由事件，但實際上卻已經過類別處理，而當您使用某些技術時，您的執行個體處理常式還是可能會處理該路由事件。  此外，許多基底類別和控制項會公開可用於覆寫類別處理行為的虛擬方法。  如需如何解決不想要的類別處理以及在自訂類別中定義自己的類別處理的詳細資訊，請參閱[將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)。  
  
<a name="attached_events"></a>   
## 在 WPF 中的附加事件  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語言也會定義一種特別的事件類別，稱為「*附加事件*」\(Attached Event\)。  附加事件可以讓您將特定事件的處理常式加入到任意項目中。  處理事件的項目不需要定義或繼承附加事件，而且可能引發事件的物件或處理執行個體的目的端，也不需要定義或用其他方式「擁有」該事件做為成員。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 輸入系統使用附加事件的範圍很廣。  然而，幾乎所有的這些附加事件都是透過基底項目轉送的。  接著，輸入事件會以對等的非附加路由事件呈現，其中該路由事件為基底項目類別的成員。  例如，在任何指定的 <xref:System.Windows.UIElement> 上都可以更輕鬆處理基礎附加事件 <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=fullName>，方法是藉由在該 <xref:System.Windows.UIElement> 上使用 <xref:System.Windows.UIElement.MouseDown>，而不是在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 或程式碼中處理附加事件語法。  
  
 如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中附加事件的詳細資訊，請參閱[附加事件概觀](../../../../docs/framework/wpf/advanced/attached-events-overview.md)。  
  
<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>   
## XAML 中的完整事件名稱  
 有另一種語法使用方式類似於 *typename*.*eventname* 附加事件的語法，但沒有嚴格指出附加事件使用方式，這種語法使用方式的使用時機是為子項目所引發路由事件來附加處理常式的時候。  您會將處理常式附加到通用父項目，以利用事件路由的優勢，即使通用父項目可能並沒有相關的路由事件做為成員。  請再度考慮這個範例：  
  
 [!code-xml[EventOvwSupport#GroupButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 在這裡，加入處理常式的父項目接聽項是一個 <xref:System.Windows.Controls.StackPanel>。  然而，加入的處理常式是要給由 <xref:System.Windows.Controls.Button> 類別 \(實際上是 <xref:System.Windows.Controls.Primitives.ButtonBase>，但可以透過繼承供 <xref:System.Windows.Controls.Button> 使用\) 所宣告和來引發的路由事件使用。  <xref:System.Windows.Controls.Button>「擁有」該事件，但路由事件系統卻允許將任何路由事件的處理常式附加到任何 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement> 執行個體接聽項，而卻另外附加有 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 事件的接聽項。  這些完整事件屬性 \(Attribute\) 名稱的預設 xmlns 命名空間通常是預設 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] xmlns 命名空間，但您也可以為自訂的路由事件指定前置命名空間。  如需 xmlns 的詳細資訊，請參閱 [WPF XAML 的 XAML 命名空間和命名空間對應](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="how_event_processing_works"></a>   
## WPF 輸入事件  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 平台內，路由事件的一項常見用途是輸入事件。在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，通道路由事件名稱習慣上是以 "Preview" 這個字做為前置字元。  輸入事件通常都成對出現，其中一個是反昇事件，而另一個是通道事件。  舉例來說，<xref:System.Windows.ContentElement.KeyDown> 事件和 <xref:System.Windows.ContentElement.PreviewKeyDown> 事件具有相同的簽章，而前者是反昇輸入事件，後者則是通道輸入事件。  有時候，輸入事件只有反昇版本，也或許只有直接路由版本。  在說明文件中，路由事件主題間會交互參照相似的路由事件，當有這類路由事件存在時就提供替代路由策略，而 Managed 參考頁面中的章節會釐清每個路由事件的路由策略。  
  
 成對出現的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 輸入事件的實作方式，是當發生單一使用者輸入動作 \(例如壓下滑鼠按鈕\) 時，會依序引發這兩個成對路由事件。  首先會引發通道事件，並在其路由中前進。  接著會引發反昇事件，並在其路由中前進。  這兩個事件會逐一共用相同的事件資料執行個體，因為引發反昇事件的實作類別中的 <xref:System.Windows.UIElement.RaiseEvent%2A> 方法呼叫會接聽來自通道事件的事件資料，並在新的引發事件中重複使用該資料。  具有通道事件處理常式的接聽項，是第一個有機會將路由事件標記為已處理的 \(類別處理常式優先，再來是執行個體處理常式\)。  如果通道路由過程中的項目已將路由事件標記為已處理，這些已經過處理的事件資料會傳送給反昇事件，且不會叫用為對等反昇輸入事件而附加的一般處理常式。  表面上看起來，甚至就好像沒有引發過這個已處理的反昇事件一樣。  這個處理行為對於以下情況的控制項複合 \(Compositing\) 非常有用：當您希望最後的控制項能夠回報所有的點擊測試輸入事件或焦點輸入事件，而非其複合部分。  最後的控制項項目在複合中更接近根項目，因而有機會先以類別處理通道事件，或許可以將該路由事件「取代」為更適合控制項的事件，做為支援控制項類別的程式碼部分。  
  
 為了說明輸入事件處理是如何進行的，請考慮下列輸入事件範例。  在下列樹狀結構圖例中，`leaf element #2` 依序是 `PreviewMouseDown` 和 `MouseDown` 事件的來源。  
  
 ![事件路由圖表](../../../../docs/framework/wpf/advanced/media/wcsdkcoreinputevents.png "wcsdkCoreInputEvents")  
輸入事件反昇和通道  
  
 事件處理的順序如下：  
  
1.  根項目上的 `PreviewMouseDown` \(通道\)。  
  
2.  中繼項目 \#1 上的 `PreviewMouseDown` \(通道\)。  
  
3.  來源項目 \#2 上的 `PreviewMouseDown` \(通道\)。  
  
4.  來源項目 \#2 上的 `MouseDown` \(反昇\)。  
  
5.  中繼項目 \#1 上的 `MouseDown` \(反昇\)。  
  
6.  根項目上的 `MouseDown` \(反昇\)。  
  
 路由事件處理常式委派會提供兩個物件的參考：引發事件的物件以及叫用處理常式的物件。  叫用處理常式的物件即是 `sender` 參數所回報的物件。  首先引發事件的物件則是由事件資料中的 <xref:System.Windows.RoutedEventArgs.Source%2A> 屬性 \(Property\) 所回報。  路由事件還是可以由相同物件來引發和處理，這時 `sender` 和 <xref:System.Windows.RoutedEventArgs.Source%2A> 就會相同 \(這是事件處理範例清單中步驟 3 和 4 的情況\)。  
  
 由於通道和反昇的原因，父項目接收到的輸入事件中的 <xref:System.Windows.RoutedEventArgs.Source%2A>，是他們的一個子項目。  如果很需要知道來源項目為何者，您可以藉由存取 <xref:System.Windows.RoutedEventArgs.Source%2A> 屬性以識別來源項目。  
  
 通常，一旦將輸入事件標記為 <xref:System.Windows.RoutedEventArgs.Handled%2A>，就不會叫用進一步的處理常式。  一般而言，只要叫用的處理常式能夠解決針對輸入事件的應用程式特定邏輯處理，您就應該將輸入事件標記為已處理。  
  
 關於 <xref:System.Windows.RoutedEventArgs.Handled%2A> 狀態的這項一般陳述的例外情況是，特意註冊為要忽略事件資料 <xref:System.Windows.RoutedEventArgs.Handled%2A> 狀態的輸入事件處理常式，還是應該要在任一個路由過程中被叫用時。  如需詳細資訊，請參閱[預覽事件](../../../../docs/framework/wpf/advanced/preview-events.md)或[將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)。  
  
 通道和反昇事件間的共用事件資料模型，以及先通道再反昇事件的循序引發方式，並不是對所有路由事件皆成立的概念。  該行為的具體實作方式是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 輸入裝置如何選擇引發和連接輸入事件配對組。  實作您自己的輸入事件是進階的案例，但您也可以選擇將該模型用於自己的輸入事件。  
  
 有些類別選擇以類別處理某些輸入事件，通常是希望重新定義在該控制項內特殊使用者導向的輸入事件所代表的意義為何，以及希望引發新事件。  如需詳細資訊，請參閱[將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)。  
  
 如需輸入和一般應用案例中輸入和事件的互動方式的詳細資訊，請參閱[輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)。  
  
<a name="events_styles"></a>   
## EventSetters 和 EventTriggers  
 在樣式中，藉由使用 <xref:System.Windows.EventSetter>，您可以在標記中包含某些預先宣告的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 事件處理語法。  當套用樣式時，就會將參考的處理常式加入到樣式執行個體中。  您只能針對路由事件宣告 <xref:System.Windows.EventSetter>。  以下是範例。  請注意，這裡參考的 `b1SetColor` 方法是程式碼後置檔案。  
  
 [!code-xml[EventOvwSupport#XAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]  
  
 這裡的好處是，樣式有可能包含可以套用到應用程式中任何按鈕的大量其他資訊，而且讓 <xref:System.Windows.EventSetter> 成為該樣式的一部分，能夠促使程式碼於標記層級重複使用事件。  此外，<xref:System.Windows.EventSetter> 讓處理常式的方法名稱相對於一般應用程式和頁面標記而言更加抽象化。  
  
 另一個結合 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的路由事件和動畫功能的特製化語法是 <xref:System.Windows.EventTrigger>。  與 <xref:System.Windows.EventSetter> 一樣，只有路由事件可用於 <xref:System.Windows.EventTrigger>。一般而言，<xref:System.Windows.EventTrigger> 會宣告為樣式的一部分，但 <xref:System.Windows.EventTrigger> 也可以在頁面層級項目上宣告為 <xref:System.Windows.FrameworkElement.Triggers%2A> 集合的一部分，或宣告在 <xref:System.Windows.Controls.ControlTemplate> 中。<xref:System.Windows.EventTrigger> 可讓您指定每當路由事件到達其路徑中的某個項目，而且該項目宣告該事件的 <xref:System.Windows.EventTrigger> 時，就執行的 <xref:System.Windows.Media.Animation.Storyboard>。  單就處理事件和使它啟動現有的腳本而言，<xref:System.Windows.EventTrigger> 的優點在於 <xref:System.Windows.EventTrigger> 可以更確實控制腳本和其執行階段行為。如需詳細資訊，請參閱 [在腳本開始後使用事件觸發程式進行控制](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。  
  
<a name="more_about"></a>   
## 更多關於路由事件的資訊  
 本主題主要是從這些觀點來討論路由事件：描述基本概念，以及對於各種基底項目和控制項中已經有的路由事件的回應方式和時機。  然而，您可以藉著所有必要的支援 \(例如特製化的事件資料類別和委派\) 來在自訂類別中建立您自己的路由事件。  路由事件的擁有者可以是任何類別，但路由事件必須由 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement> 衍生類別所引發和處理，才會好用。  如需自訂事件的詳細資訊，請參閱 [建立自訂路由事件](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md)。  
  
## 請參閱  
 <xref:System.Windows.EventManager>   
 <xref:System.Windows.RoutedEvent>   
 <xref:System.Windows.RoutedEventArgs>   
 [將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)   
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)   
 [弱式事件模式](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)