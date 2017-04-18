---
title: "動畫和計時系統概觀 | Microsoft Docs"
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
  - "動畫 [WPF]"
  - "計時系統 [WPF]"
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 動畫和計時系統概觀
本主題說明計時系統如何使用動畫、<xref:System.Windows.Media.Animation.Timeline> 和 <xref:System.Windows.Media.Animation.Clock> 類別建立屬性的動畫。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要條件  
 若要了解這個主題，您應該要能夠使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫建立屬性的動畫，如[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)中所述。  這也有助於熟悉[相依性屬性](GTMT)；如需詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
<a name="timelinesandclocks"></a>   
## 時間表和時鐘  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)中會說明 <xref:System.Windows.Media.Animation.Timeline> 如何代表示時間區段，以及動畫為何是一種會產生輸出值的 <xref:System.Windows.Media.Animation.Timeline>。  <xref:System.Windows.Media.Animation.Timeline> 本身不會做其他的事，只是描述一個時間區段。  真正在執行工作的是時間表的 <xref:System.Windows.Media.Animation.Clock> 物件。  同樣的，動畫並不真的是在建立屬性的動畫：動畫類別只負責描述計算輸出值的方式，真正會計算動畫輸出並將該輸出套用至屬性的乃是 <xref:System.Windows.Media.Animation.Clock>。  
  
 <xref:System.Windows.Media.Animation.Clock> 是一種特殊的物件，它可以維護 <xref:System.Windows.Media.Animation.Timeline> 的時間相關執行階段狀態。  它以三個位元提供了動畫和計時系統最重要的資訊：<xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>、<xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A> 和 <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>。  <xref:System.Windows.Media.Animation.Clock> 會使用其 <xref:System.Windows.Media.Animation.Timeline> 所描述的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 等計時行為，來決定它目前的時間、進度和狀態。  
  
 在大部分情況下，您的時間表會自動建立 <xref:System.Windows.Media.Animation.Clock>。  當您使用 <xref:System.Windows.Media.Animation.Storyboard> 或 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法建立動畫時，您的時間表會自動建立時鐘，並將動畫套用至它們的目標屬性。  您也可以使用 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> 方法，明確建立 <xref:System.Windows.Media.Animation.Clock>。  <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=fullName>方法會針對呼叫它的 <xref:System.Windows.Media.Animation.Timeline> 建立適當類型的時鐘。  如果 <xref:System.Windows.Media.Animation.Timeline> 包含子時間表，也會為子時間表建立 <xref:System.Windows.Media.Animation.Clock> 物件。  產生的 <xref:System.Windows.Media.Animation.Clock> 物件會依照來源 <xref:System.Windows.Media.Animation.Timeline> 物件樹狀目錄的結構，排列在樹狀目錄中。  
  
 不同型別的時間表有不同型別的時鐘。  下表針對其中幾種不同的 <xref:System.Windows.Media.Animation.Timeline> 型別顯示相對應的 <xref:System.Windows.Media.Animation.Clock> 型別。  
  
|Timeline 型別|Clock 型別|時鐘用途|  
|-----------------|--------------|----------|  
|Animation \(繼承自 <xref:System.Windows.Media.Animation.AnimationTimeline>\)|<xref:System.Windows.Media.Animation.AnimationClock>|產生相依性屬性的輸出值|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|處理媒體檔案|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|分組並控制它的子 <xref:System.Windows.Media.Animation.Clock> 物件|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|分組並控制它的子 <xref:System.Windows.Media.Animation.Clock> 物件|  
  
 使用 <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> 方法，可以將您建立的任何 <xref:System.Windows.Media.Animation.AnimationClock> 物件套用至相容的相依性屬性。  
  
 在會耗損效能的情況中，如顯示大量類似物件的動畫，管理您自己的 <xref:System.Windows.Media.Animation.Clock> 之使用可以提升效能。  
  
<a name="timemanager"></a>   
## 時鐘和時間管理員  
 當您在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中將物件顯示為動畫，其實會替時間表建立時間管理員，以便管理 <xref:System.Windows.Media.MediaPlayer.Clock%2A> 物件。  時間管理員是 <xref:System.Windows.Media.MediaPlayer.Clock%2A> 物件的樹狀目錄的根，控制了這個樹狀目錄中的時間流程。  系統會為每個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式自動建立時間管理員，而應用程式開發人員看不見時間管理員。時間管理員每秒會「跳動」許多次，每秒實際發生的跳動次數因可用的系統資源而異。  時間管理員每跳動一次，就會計算計時樹狀目錄中所有 <xref:System.Windows.Media.Animation.ClockState> <xref:System.Windows.Media.Animation.Clock> 物件的狀態。  
  
 下圖顯示時間管理員、<xref:System.Windows.Media.Animation.AnimationClock> 和用來建立動畫的相依性屬性之間的關係。  
  
 ![計時系統元件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-1clock1prop.png "graphicsmm\_clocks\_1clock1prop")  
建立屬性的動畫  
  
 時間管理員每跳動一次，就會更新應用程式中每個 <xref:System.Windows.Media.Animation.ClockState> <xref:System.Windows.Media.Animation.Clock> 的時間。  如果 <xref:System.Windows.Media.Animation.Clock> 是 <xref:System.Windows.Media.Animation.AnimationClock>，則會使用建立它的 <xref:System.Windows.Media.Animation.AnimationTimeline> 的 <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> 方法，來計算目前的輸出值。  <xref:System.Windows.Media.Animation.AnimationClock> 會提供 <xref:System.Windows.Media.Animation.AnimationTimeline> 目前本機時間、輸入值 \(通常是屬性的基底實值\) 和預設目的值。  當您使用 <xref:System.Windows.DependencyObject.GetValue%2A> 方法或它的 CLR 存取子擷取動畫屬性值時，會得到它的 <xref:System.Windows.Media.Animation.AnimationClock> 的輸出。  
  
#### 時鐘群組  
 前一節中說明了不同時間表類型如何有不同類型的 <xref:System.Windows.Media.Animation.Clock> 物件。  下圖顯示時間管理員、<xref:System.Windows.Media.Animation.ClockGroup>、<xref:System.Windows.Media.Animation.AnimationClock> 和以動畫顯示之相依性屬性之間的關係。  如果時間表是由其他時間表組成的群組 \(例如由動畫和其他時間表組成的 <xref:System.Windows.Media.Animation.Storyboard> 類別\)，則會建立 <xref:System.Windows.Media.Animation.ClockGroup>。  
  
 ![計時系統元件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm\_clocks\_2clock1clockgroup2prop")  
ClockGroup  
  
#### 撰寫  
 您可以使數個時鐘和單一屬性產生關聯，在這種情況下每一個時鐘都使用前一個時鐘的輸出值做為它的基底實值。  下圖顯示套用到相同屬性的三個 <xref:System.Windows.Media.Animation.AnimationClock> 物件。  時鐘1 使用動畫屬性的基底實值做為輸入，並用它來產生輸出。  時鐘2 拿時鐘1 的輸出做為輸入，並用它來產生輸出。  時鐘3 拿時鐘2 的輸出做為輸入，並用它來產生輸出。  當有數個時鐘同時影響同一個屬性，即稱這些時鐘形成撰寫鏈結。  
  
 ![計時系統元件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1prop.png "graphicsmm\_clocks\_2clock1prop")  
撰寫鏈結  
  
 請注意，雖然 <xref:System.Windows.Media.Animation.AnimationClock> 物件的輸入和輸出之間建立了撰寫鏈結關係，但是它們的計時行為不會受影響；<xref:System.Windows.Media.Animation.Clock> 物件 \(包括 <xref:System.Windows.Media.Animation.AnimationClock> 物件\) 與它們的父 <xref:System.Windows.Media.Animation.Clock> 物件有階層上的相依性。  
  
 若要套用數個時鐘至同一個屬性，請在套用 <xref:System.Windows.Media.Animation.Storyboard>、動畫或 <xref:System.Windows.Media.Animation.AnimationClock> 時使用 <xref:System.Windows.Media.Animation.HandoffBehavior> <xref:System.Windows.Media.Animation.HandoffBehavior>。  
  
#### 跳動和事件的合併  
 除了計算輸出值，時間管理員也會在它每次跳動時執行其他工作：判斷每個時鐘的狀態，並在適當時引發事件。  
  
 雖然跳動發生次數很頻繁，但每次跳動之間仍可能發生許多事情。  例如，<xref:System.Windows.Media.Animation.Clock> 可能已停止、又啟動，然後又再度停止，在這個情況下它的 <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> 值已經變更三次。  理論上，一次跳動可以引發 <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> 事件許多次；但是時間引擎會合併事件，使得每一次跳動最多只會引發 <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> 事件一次。  所有的計時事件皆是如此：每種類型的事件最多只會發生於特定 <xref:System.Windows.Media.Animation.Clock> 物件一次。  
  
 當 <xref:System.Windows.Media.Animation.Clock> 在跳動之間切換狀態然後又回到它的原始狀態 \(例如從 <xref:System.Windows.Media.Animation.ClockState> 變為 <xref:System.Windows.Media.Animation.ClockState> 然後又變回 <xref:System.Windows.Media.Animation.ClockState>\)，相關聯的事件仍會發生。  
  
 如需計時事件的詳細資訊，請參閱[計時事件概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)。  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## 屬性的目前值和基底實值  
 可用來建立動畫的屬性會有兩個值：基底實值和目前值。  當您使用屬性的 CLR 存取子或 <xref:System.Windows.DependencyObject.SetValue%2A> 方法設定屬性值時，是在設定它的基底實值。  當屬性沒有用來建立動畫時，它的基底實值和目前值相同。  
  
 當您以屬性建立動畫時，<xref:System.Windows.Media.Animation.AnimationClock> 設定的是動畫的「目前」值。  當 <xref:System.Windows.Media.Animation.AnimationClock> 為 <xref:System.Windows.Media.Animation.ClockState> 或 <xref:System.Windows.Media.Animation.ClockState> 時，透過屬性的 CLR 存取子或 <xref:System.Windows.DependencyObject.GetValue%2A> 方法擷取屬性的值，將會傳回 <xref:System.Windows.Media.Animation.AnimationClock> 的輸出。  您可以使用 <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> 方法擷取屬性的基底實值。  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [計時事件概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)   
 [計時行為概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)