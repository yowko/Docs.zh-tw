---
title: "將路由事件標記為已處理以及類別處理 | Microsoft Docs"
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
  - "反昇事件"
  - "類別接聽項"
  - "複合控制項"
  - "控制項, 複合"
  - "事件, 反昇"
  - "事件, 隱藏"
  - "事件, 通道"
  - "執行個體接聽項"
  - "接聽項"
  - "預覽路由事件"
  - "路由事件, 標記為已處理"
  - "路由事件, 預覽"
  - "隱藏事件"
  - "通道事件"
ms.assetid: 5e745508-4861-4b48-b5f6-5fc7ce5289d2
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 將路由事件標記為已處理以及類別處理
路由事件的處理常式可以在事件資料內將事件標記為已處理。  處理事件將有效縮短路由。  類別處理是路由事件支援的一種程式設計概念。  類別處理常式有機會在叫用類別的任何執行個體處理常式之前，在類別層級處理特定的路由事件。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題詳述[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)中介紹的概念。  
  
<a name="When_to_Mark_Events_as_Handled"></a>   
## 將事件標記為已處理的時機  
 當您在路由事件的事件資料中將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 屬性的值設定為 `true` 時，這個動作稱為「將事件標記為已處理」。  不論您是應用程式作者，還是負責回應現有路由事件或實作新事件的控制項作者，將路由事件標記為已處理的時機都沒有絕對的規則可循。  在大部分的情況下，路由事件的事件資料中採用的「已處理」概念都應該當做一種受限的通訊協定，規範的對象則是您自己的應用程式對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 中公開的各種路由事件的回應。  另一個要考量「已處理」問題的點是，如果您的程式碼以重要且相當完整的方法回應路由事件，通常就應該將該路由事件標記為已處理。通常，對於發生的任何單一路由事件，不應有超過一個重要回應需要有個別實作的處理常式。  如果需要的回應較多，則應該透過單一處理常式內鏈結的應用程式邏輯實作必要的程式碼，而不是使用路由事件系統來轉送。  關於何謂「重要」的概念也是主觀的，而且是根據您的應用程式或程式碼而定。  一般來說，「重要回應」的部分範例包括：設定焦點、修改公用 \(Public\) 狀態、設定影響視覺呈現效果的屬性，以及引發其他新事件等。  不重要回應的範例則包括：修改私用 \(Private\) 狀態 \(無視覺上的影響或程式設計表示\)、記錄事件，或是查看事件的引數並選擇不回應。  
  
 路由事件系統的行為強化了這種使用路由事件已處理狀態的「重要回應」模式，因為在回應事件資料已經標記為已處理的路由事件時，並不會叫用 \(Invoke\) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中加入的處理常式或是 <xref:System.Windows.UIElement.AddHandler%2A> 的通用簽章 \(Signature\)。  您必須執行使用 `handledEventsToo` 參數版本 \(<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>\) 加入處理常式的額外工作，才能處理事件路由中已由先前參與者標記為已處理的路由事件。  
  
 在某些情況下，控制項會自行將特定路由事件標記為已處理。  已處理的路由事件代表 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項作者決定該控制項回應此路由事件的動作是控制項實作中非常重要或完整的一部分，而且此事件已經不需要再做任何處理。  通常這是透過加入事件的類別處理常式，或是覆寫存在於基底類別中的其中一個類別處理常式視覺效果來完成。  您還是可以在必要時解決這種事件處理狀況；請參閱本主題後面的[解決控制項隱藏的事件](#WorkingAroundEventSuppressionByControls)。  
  
<a name="Preview_Events_vs__Bubbling_Events_and_Handling"></a>   
## 預覽 \(通道\) 事件與反昇事件的比較以及事件處理  
 預覽路由事件是經由項目樹狀結構遵循[通道](GTMT)路由傳送的事件。  命名規範中使用「預覽」一詞來表示輸入事件的一般原則，也就是預覽 \(通道\) 路由事件是在對等的反昇路由事件之前引發。  此外，具有通道和反昇配對的輸入路由事件也有不同的處理邏輯。  如果事件接聽程式 \(Listener\) 已將通道\/預覽路由事件標記為已處理，則反昇路由事件甚至會在任何反昇路由事件接聽程式收到它之前便標記為已處理。  就技術層面而言，通道和反昇路由事件是不同的事件，但它們卻刻意共用相同的事件資料執行個體，以便啟用上述行為。  
  
 通道和反昇路由事件之間的關聯是藉由任何特定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別引發其本身之宣告路由事件的內部實作方式來建立，而配對的輸入路由事件也是如此。  不過，除非有這種類別層級的實作存在，否則共用命名配置的通道路由事件和反昇路由事件之間便無任何關聯：如果沒有這樣的實作，它們只是完全不同的路由事件，既不會連續引發，也不會共用事件資料。  
  
 如需如何在自訂類別中實作通道\/反昇輸入路由事件配對的詳細資訊，請參閱 [建立自訂路由事件](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md)。  
  
<a name="Class_Handlers_and_Instance_Handlers"></a>   
## 類別處理常式和執行個體處理常式  
 路由事件會考量兩種不同類型的事件接聽程式：類別接聽程式和執行個體接聽程式。  類別接聽程式存在的原因是型別已經在其靜態建構函式中呼叫特定的 <xref:System.Windows.EventManager> [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] \(<xref:System.Windows.EventManager.RegisterClassHandler%2A>\)，或是已經覆寫來自項目基底類別的類別處理常式虛擬方法。  執行個體接聽程式是特定的類別執行個體\/項目，而其中已經透過呼叫 <xref:System.Windows.UIElement.AddHandler%2A>，附加該路由事件的一個或多個處理常式。現有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 路由事件在其 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 事件包裝函式 add{} 和 remove{} 實作過程中，將會一併呼叫 <xref:System.Windows.UIElement.AddHandler%2A>，而這個方法也可以用來啟用透過屬性 \(Attribute\) 語法附加事件處理常式的簡單 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 機制。  因此，即使是簡單的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 用法最終也會等於 <xref:System.Windows.UIElement.AddHandler%2A> 呼叫。  
  
 視覺化樹狀結構內的項目將會就已註冊的處理常式實作進行檢查。  在整個路由中，系統可能都會叫用處理常式，叫用的順序則是該路由事件之路由策略的型別中固有的順序。  例如，反昇路由事件會先叫用附加至引發路由事件之同一項目的處理常式。  接著路由事件會「反昇」至下一個父項目，依此類推，直到達到應用程式根項目為止。  
  
 就反昇路由中根項目的觀點而言，如果類別處理或更接近路由事件來源的任何項目叫用了將事件引數標記為已處理的處理常式，則不會叫用根項目上的處理常式，而且在尚未到達該路項目之前，事件路由也可有效縮短。  不過，路由並未完全中止，因為加入處理常式時可能使用了特殊條件，因此即使類別處理常式或執行個體處理常式已經將路由事件標記為已處理，仍然可以叫用這些處理常式。  有關這部分的說明，請參閱本主題稍後的[加入即使事件標記為已處理仍會引發的執行個體處理常式](#AddingInstanceHandlersthatAreRaisedEvenWhenEventsareMarkedHandled)。  
  
 在比事件路由更深的層級中，可能也有多個在任何指定之類別執行個體上作用的類別處理常式。  這是因為路由事件的類別處理模型使得類別階層中所有可能的類別，都能針對每個路由事件，註冊其本身專屬的類別處理常式。  每個類別處理常式都會加入內部存放區中，而在建構應用程式的事件路由時，則會將類别處理常式全部加入事件路由中。  類別處理常式加入路由中的方式是要先叫用最高層的衍生類別處理常式，接著再叫用每個後續基底類別中的類別處理常式。  一般來說，類別處理常式並不會註冊成使其也會回應已經標記為已處理的路由事件。  因此，這種類別處理機制可啟用下列兩個選項其中一個：  
  
-   衍生類別 \(Derived Class\) 可以藉由加入不會將路由事件標記為已處理的處理常式，補充繼承自基底類別的類別處理，因為基底類別處理常式將會在衍生類別處理常式之後叫用。  
  
-   衍生類別可以藉由加入將路由事件標記為已處理的類別處理常式，取代來自基底類別的類別處理。  使用這種方法時應該特別小心，因為它可能會變更預期的某些基底控制項設計，例如視覺外觀、狀態邏輯和命令處理。  
  
<a name="Class_Handling_of_Routed_Events"></a>   
## 控制項基底類別的路由事件類別處理  
 在事件路由中每個指定的項目節點上，類別接聽程式都有機會可以在項目上的任何執行個體接聽程式之前回應路由事件。  因此，類別處理常式有時候會用來隱藏特定控制項類別實作不想再傳播的路由事件，或是用來提供該路由事件的特殊處理方式 \(此種處理方式是類別的一項功能\)。  例如，類別可能會引發自己的類別專屬事件，而引發的事件中則包含特定使用者條件在該特定類別內容中之意義的詳細資訊。  接著，類別實作可能會將較為一般性的路由事件標記為已處理。  在類別處理常式加入後，通常並不會針對共用事件資料已經標記為已處理的路由事件來叫用它們，但是非一般情況也有 <xref:System.Windows.EventManager.RegisterClassHandler%28System.Type%2CSystem.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> 簽章可以將類別處理常式註冊成即使路由事件標記為已處理，還是會叫用這些常式。  
  
### 類別處理常式虛擬  
 某些項目，尤其是諸如 <xref:System.Windows.UIElement> 之類的基底項目，會公開對應於其公用路由事件清單的 "On\*Event" 和 "OnPreview\*Event" 虛擬方法。  您可以覆寫這些虛擬方法，以實作該路由事件的類別處理常式。  基底項目類別會依照前面的說明，使用 <xref:System.Windows.EventManager.RegisterClassHandler%28System.Type%2CSystem.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> 將這些虛擬方法註冊成它們的類別處理常式，以處理這一類的各個路由事件。  On\*Event 虛擬方法使實作相關路由事件的類別處理更為簡單，而且不需要在每個型別的靜態建構函式進行特殊的初始設定。  例如，您可以透過覆寫 <xref:System.Windows.UIElement.OnDragEnter%2A> 虛擬方法，加入任何 <xref:System.Windows.UIElement> 衍生類別中 <xref:System.Windows.UIElement.DragEnter> 事件的類別處理。  在這項覆寫內，您可以處理路由事件、引發其他事件、啟始可能變更執行個體之項目屬性的類別專用邏輯，或是執行這些動作的任何組合。  您通常應該在這種覆寫中呼叫基底實作，即使將事件標記為已處理也一樣。  由於虛擬方法是在基底類別上，因此強烈建議您呼叫基底實作。  從每個虛擬呼叫基底實作的標準保護虛擬模式會取代及平行處理路由事件處理原生的類似機制，藉以在任何指定的執行個體上呼叫類別階層中所有類別的類別處理常式，呼叫的順序則是從最高層的衍生類別處理常式開始，一直到基底類別處理常式為止。  只有當您的類別具有變更基底類別處理邏輯的特殊需求時，您才能忽略基底實作呼叫。  呼叫基底實作的時機是在覆寫程式碼之前或之後，需根據實作的性質而定。  
  
#### 輸入事件類別處理  
 類別處理常式虛擬方法全部都會註冊成只有在尚未將任何共用事件資料標記為已處理時才會叫用。  此外，輸入事件還有幾個特點，包括通道版本和反昇版本通常都會連續引發，而且都會共用事件資料。  這代表在指定的輸入事件類別處理常式配對中，若其中一個是通道版本，而另一個是反昇版本時，您可能不希望立即將事件標記為已處理。  如果您實作通道類別處理虛擬方法來將事件標記為已處理，便可制止系統叫用反昇類別處理常式 \(也可避免叫用一般通道或反昇事件所註冊的任何執行個體處理常式\)。  
  
 一旦完成節點的類別處理作業，便會考慮執行個體接聽程式。  
  
<a name="AddingInstanceHandlersthatAreRaisedEvenWhenEventsareMarkedHandled"></a>   
## 加入即使事件標記為已處理仍會引發的執行個體處理常式  
 <xref:System.Windows.UIElement.AddHandler%2A> 方法提供一種特殊的多載，可讓您加入每次事件抵達路由中的處理項目時，事件系統都會叫用的處理常式 \(即使其他處理常式已經調整事件資料，將該事件標記為已處理也一樣\)。  一般情況下並不會執行這個動作。  一般來說，即使需要多項結果，處理常式還是可以撰寫成用來調整應用程式碼中可能受事件影響的所有區域，而且也不論該事件是否在項目樹狀結構中處理。  此外，實際上需要回應該事件的項目只有一個，而且也已經發生適當的應用程式邏輯。  不過，雖然 `handledEventsToo` 多載也適用於項目樹狀結構或控制項複合 \(Compositing\) 已經將事件標記為已處理的例外狀況，但是樹狀目錄結構中層級較高或較低 \(視路由而定\) 的其他項目仍然希望叫用它們自己的處理常式。  
  
#### 將已處理事件標記為未處理的時機  
 一般來說，標記為已處理的路由事件通常不應該標記為未處理 \(也就是將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 設回 `false`\)，即使是在 `handledEventsToo` 運作上的處理常式也不能這樣做。  不過，某些輸入事件擁有高層級和較低層級的事件表示，而當高層級事件和低層級事件分別出現在樹狀結構中的兩個不同位置時，這些事件表示就有可能會重疊。  例如，假設子項目負責接聽高層級的按鍵事件 \(例如 <xref:System.Windows.UIElement.TextInput>\)，而父項目則負責接聽低層級的事件 \(<xref:System.Windows.UIElement.KeyDown>\)，  如果父項目處理低層級事件，則甚至是在理論上應該最早有機會處理事件的子項目中，都會隱藏較高層級的事件。  
  
 在這些情況中，可能必須將處理常式加入至低層級事件的父項目和子項目中。  子項目處理常式實作可以將低層級事件標記為已處理，但是父項目處理常式實作則會再次將它設定成未處理，使得樹狀結構中更上層的其他項目 \(以及高層級的事件\) 都有回應的機會。  這種情況應該非常罕見。  
  
<a name="Deliberately_Suppressing_Input_Events_for_Control"></a>   
## 刻意隱藏控制項複合的輸入事件  
 使用路由事件類別處理的主要案例包括輸入事件和複合控制項。  按照定義，複合控制項是由多個實用的控制項或控制項基底類別所組成。  控制項的作者經常想要合併每個子元件可能引發的所有可能的輸入事件，以便將整個控制項回報成單一的事件來源。  在某些情況下，控制項作者可能希望完全隱藏元件所傳回的事件，或是替換成元件定義的事件，以提供更詳細的資訊或更具體的行為。  任何元件作者都可以馬上查看的標準範例包括 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> 如何處理最終將解析成所有按鈕擁有之直覺化事件 \(即 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件\) 的任何滑鼠事件。  
  
 <xref:System.Windows.Controls.Button> 基底類別 \(<xref:System.Windows.Controls.Primitives.ButtonBase>\) 衍生自 <xref:System.Windows.Controls.Control>，而後者又是從 <xref:System.Windows.FrameworkElement> 和 <xref:System.Windows.UIElement> 衍生而來，而且控制項輸入處理需要的許多事件處理基礎架構都是由 <xref:System.Windows.UIElement> 層級提供。  具體來說，<xref:System.Windows.UIElement> 會處理負責滑鼠游標在其界限內之點擊測試 \(Hit Testing\) 的一般 <xref:System.Windows.Input.Mouse> 事件，並針對最常用的按鈕動作提供不同的事件，例如 <xref:System.Windows.UIElement.MouseLeftButtonDown>。  <xref:System.Windows.UIElement> 也會提供空白的虛擬 <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> 做為 <xref:System.Windows.UIElement.MouseLeftButtonDown> 的預先註冊類別處理常式，而 <xref:System.Windows.Controls.Primitives.ButtonBase> 則會覆寫它。  同樣地，<xref:System.Windows.Controls.Primitives.ButtonBase> 也會使用 <xref:System.Windows.UIElement.MouseLeftButtonUp> 的類別處理常式。  在傳遞事件資料的覆寫中，這些實作會透過將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 設定為 `true`，以便將該 <xref:System.Windows.RoutedEventArgs> 執行個體標記為已處理，而且該筆相同的事件資料將繼續循著剩下的路由，傳送到其他類別處理常式，並一併傳送到執行個體處理常式或事件 setter。  接著，<xref:System.Windows.Controls.Primitives.ButtonBase.OnMouseLeftButtonUp%2A> 覆寫也會引發 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  多數接聽程式的結果都是 <xref:System.Windows.UIElement.MouseLeftButtonDown> 和 <xref:System.Windows.UIElement.MouseLeftButtonUp> 事件「消失」並改由 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 取代，後者是較有意義的事件，因為目前已知這個事件是源自真正的按鈕而不是按鈕的某一個複合部分，或是完全源自其他項目。  
  
<a name="WorkingAroundEventSuppressionByControls"></a>   
### 解決控制項隱藏的事件  
 某些情況下，個別控制項內的這種事件隱藏行為可能會妨礙應用程式之事件處理邏輯中某些較為一般性的目的。  例如，如果因為某些原因，使得您的應用程式擁有一個位於應用程式根項目的 <xref:System.Windows.UIElement.MouseLeftButtonDown> 處理常式，您會發現在按鈕上按一下滑鼠的任何動作，都不會叫用根層級的 <xref:System.Windows.UIElement.MouseLeftButtonDown> 或 <xref:System.Windows.UIElement.MouseLeftButtonUp> 處理常式。  事件本身確實已經反昇 \(同樣地，事件路由並未真正結束，但是路由事件系統會在標記為已處理之後，變更它們的處理常式引動行為\)。  當路由事件到達該按鈕時，<xref:System.Windows.Controls.Primitives.ButtonBase> 類別處理會將 <xref:System.Windows.UIElement.MouseLeftButtonDown> 標記為已處理，因為它想替換為更有意義的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  因此，它並不會叫用路由中更上層的任何標準 <xref:System.Windows.UIElement.MouseLeftButtonDown> 處理常式。  有兩種技巧可以用來確保系統這種情況下一定會叫用您的處理常式。  
  
 第一種技巧是使用 <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> 的 `handledEventsToo` 簽章，刻意加入處理常式。  這種方法的限制是附加事件處理常式的這項技巧只能從程式碼執行，不能從標記執行。  透過[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將事件處理常式名稱指定成事件屬性值的簡單語法並不會啟用這種行為。  
  
 第二種技巧只適用於輸入事件，也就是路由事件的通道版本和反昇版本配對的情況。  針對這些路由事件，您可以改成將處理常式加入至預覽\/[通道](GTMT)對等路由事件。  該路由事件將會從根 \(Root\) 開始通過路由，因此按鈕類別處理程式碼不會攔截它 \(假設您已將預覽處理常式附加在應用程式項目樹狀結構的某個祖系項目層級\)。  如果使用這種方法，在將任何預覽事件標記為已處理時請特別小心。  在於根項目處理 <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> 的範例中，如果您在處理常式實作中將事件標記為 <xref:System.Windows.RoutedEventArgs.Handled%2A>，實際上您會隱藏 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  通常這並不是適當的行為。  
  
## 請參閱  
 <xref:System.Windows.EventManager>   
 [預覽事件](../../../../docs/framework/wpf/advanced/preview-events.md)   
 [建立自訂路由事件](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)