---
title: "計時行為概觀 | Microsoft Docs"
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
  - "行為, 計時"
  - "計時行為"
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 計時行為概觀
本主題說明動畫和其他 <xref:System.Windows.Media.Animation.Timeline> 物件的計時行為。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要條件  
 若要了解本主題，您應該熟悉基本動畫功能。  如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
<a name="timelinetypes"></a>   
## Timeline 型別  
 <xref:System.Windows.Media.Animation.Timeline> 代表一個時間區段。  它提供的屬性可以讓您指定區段的長度、開始時間、要重複的次數、區段的時間進行速度等等。  
  
 繼承自時間表類別的類別還可以提供額外的功能，如動畫和媒體播放。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供下列 <xref:System.Windows.Media.Animation.Timeline> 型別。  
  
|Timeline 型別|描述|  
|-----------------|--------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|<xref:System.Windows.Media.Animation.Timeline> 物件的抽象基底類別，會產生動畫屬性的輸出值。|  
|<xref:System.Windows.Media.MediaTimeline>|產生媒體檔案的輸出。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|一種 <xref:System.Windows.Media.Animation.TimelineGroup>，可分組和控制子 <xref:System.Windows.Media.Animation.Timeline> 物件。|  
|<xref:System.Windows.Media.Animation.Storyboard>|一種 <xref:System.Windows.Media.Animation.ParallelTimeline>，可以提供所含 Timeline 物件的目標資訊。|  
|<xref:System.Windows.Media.Animation.Timeline>|定義計時行為的抽象基底類別。|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|<xref:System.Windows.Media.Animation.Timeline> 物件的抽象類別，可以包含其他 <xref:System.Windows.Media.Animation.Timeline> 物件。|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## 控制時間表長度的屬性  
 <xref:System.Windows.Media.Animation.Timeline> 代表一個時間區段，而時間表長度有不同描述方式。  下表定義數個描述時間表長度的詞彙。  
  
|詞彙|描述|屬性||||  
|--------|--------|--------|-|-|-|  
|簡單持續期間|時間表完成一次順向反覆項目所用的時間長度。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|重複一次|時間表順向播放一次，再反向播放一次 \(如果 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性為 true\) 所用的時間長度。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|作用期|時間表完成其 <xref:System.Windows.Media.Animation.RepeatBehavior> 屬性指定之所有重複項目所用的時間長度。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### Duration 屬性  
 之前已說明過，時刻表代表時間區段。  區段長度是由時間表的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 決定。  當時間表過了持續期間後，就會停止播放。  如果時間表有子系時間表，子系時間表也會停止播放。  動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 會指定動畫從開始值轉換到結束值要用多少時間。  時間表的持續期間有時又稱為「簡單持續期間」，用以區別單一反覆項目的持續期間和整個動畫 \(包括重複\) 播放的時間長度。  您可以將持續期間指定為有限時間值或是特殊值 \(<xref:System.Windows.Duration.Automatic%2A> 或 <xref:System.Windows.Duration.Forever%2A>\)。  動畫的持續期間應解析為 <xref:System.Windows.Duration.TimeSpan%2A> 值，以便在值之間轉換。  
  
 下列範例顯示的 <xref:System.Windows.Media.Animation.DoubleAnimation> 具有 5 秒的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>。  
  
  
  
 容器時間表 \(如 <xref:System.Windows.Media.Animation.Storyboard> 和 <xref:System.Windows.Media.Animation.ParallelTimeline>\) 的預設持續期間為 <xref:System.Windows.Duration.Automatic%2A>，這表示它們會在最後一個子系停止播放時自動結束。  下列範例顯示 <xref:System.Windows.Media.Animation.Storyboard>，它的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 會解析為 5 秒，這是它所有的子 <xref:System.Windows.Media.Animation.DoubleAnimation> 物件完成所用的時間長度。  
  
  
  
 將容器時間表的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 設為 <xref:System.Windows.Duration.TimeSpan%2A> 值，可以強制容器時間表播放比它的子 <xref:System.Windows.Media.Animation.Timeline> 物件的播放時間更長或更短的時間。  如果您將 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 設為小於容器時間表子 <xref:System.Windows.Media.Animation.Timeline> 物件長度的值，子 <xref:System.Windows.Media.Animation.Timeline> 物件也會在容器時間表停止時停止播放。  下列範例會將前述範例之 <xref:System.Windows.Media.Animation.Storyboard> 的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 設為 3 秒。  因此，第一個 <xref:System.Windows.Media.Animation.DoubleAnimation> 會在 3 秒後停止，屆時目標矩形的寛度會是 60。  
  
  
  
<a name="repeatinganimations"></a>   
### RepeatBehavior 屬性  
 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性會控制它要重複簡單持續期間幾次。  您可以用 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性指定時間表播放 \(反覆項目 <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>\) 的次數，或時間表應播放 \(重複 <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>\) 的時間總長度。  不論是哪種情況，動畫都會從頭到尾不斷重複執行，直到達到所要求的計數或持續期間。  根據預設，時間表的反覆項目計數為 `1.0`，表示播放一次且不再重複。  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性指定反覆項目計數，讓 <xref:System.Windows.Media.Animation.DoubleAnimation> 播放簡單持續期間兩次。  
  
  
  
 接下來的範例會使用 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性，使 <xref:System.Windows.Media.Animation.DoubleAnimation> 只播放簡單持續期間的一半。  
  
  
  
 如果您將 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性設為 <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，<xref:System.Windows.Media.Animation.Timeline> 就會一直重複，重到看動畫的人或計時系統將它停止。  下列範例會使用 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性讓 <xref:System.Windows.Media.Animation.DoubleAnimation> 無止盡地播放。  
  
  
  
 如需其他範例，請參閱 [重複動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)。  
  
<a name="autoreverseproperty"></a>   
### AutoReverse 屬性  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性指定 <xref:System.Windows.Media.Animation.Timeline> 是否要在每次順向反覆項目結束時反向播放。  下列範例會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性設為 `true`，結果是動畫會從零播到 100，再從 100 播到零。  總共播放 10 秒。  
  
  
  
 當您將 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 指定為 <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> 值，且這個 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性值為 `true`，一次重複就會包括一個順向反覆項目再接上一個反向反覆項目。  下列範例會將上一個範例中 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 的 <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> 設為 2。  結果是 <xref:System.Windows.Media.Animation.DoubleAnimation> 播放 20 秒：順向 5 秒反向 5 秒，然後再順向 5 秒反向 5 秒一遍。  
  
  
  
 如果容器時間表包含子 <xref:System.Windows.Media.Animation.Timeline> 物件，這些子物件會在時間表反轉時也跟著反轉。  如需其他範例，請參閱 [指定時刻表是否會自動反轉](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)。  
  
<a name="timelinebegin"></a>   
## BeginTime 屬性  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 屬性可以指定時間表何時開始。  時間表的開始時間與它的父時間表有關。  開始時間為零秒表示時間表和它的父時間表同時開始，其他值則表示父時間表開始播放及子系時間表開始播放之間有一段間隔時間。  例如，開始時間 2 秒表示時間表會在它的父時間表播放 2 秒鐘之後才開始播放。  所有時間表的預設開始時間都是零秒。  您也可以將時間表的開始時間設為 `null`，這樣時間表就不會播放。  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中要用 [x:Null 標記延伸](../../../../docs/framework/xaml-services/x-null-markup-extension.md)指定 null。  
  
 請注意，受到時間表的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 設定影響，每次時間表重複時都不會套用開始時間。  如果您建立 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 為 10 秒、<xref:System.Windows.Media.Animation.RepeatBehavior> 為 <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A> 的動畫，在動畫第一次播放前會有 10 秒的延遲，但之後的每一次重複都不會延遲。  但是，當動畫的父時間表從頭開始或重複播放時，10 秒延遲就會再度發生。  
  
 若要錯開時間表，<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 屬性會非常有用。  下列範例會建立 <xref:System.Windows.Media.Animation.Storyboard>，它有兩個子 <xref:System.Windows.Media.Animation.DoubleAnimation> 物件。  第一個動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 為 5 秒，第二個動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 為 3 秒。  這個範例會將第二個 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 設為 5 秒，因此它會在第一個 <xref:System.Windows.Media.Animation.DoubleAnimation> 結束後開始播放。  
  
  
  
<a name="fillbehaviorproperty"></a>   
## FillBehavior 屬性  
 當 <xref:System.Windows.Media.Animation.Timeline> 過了整個作用持續期間時，<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性會指定它該停止或是停留在最後一個值。  動畫的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 為 <xref:System.Windows.Media.Animation.FillBehavior> 時，它就會「停留在」它的最後一個值：動畫所針對的屬性仍保持動畫的最後一個值。  其值為 <xref:System.Windows.Media.Animation.FillBehavior> 時，動畫會在結束後停止影響它的目標屬性。  
  
 下列範例會建立 <xref:System.Windows.Media.Animation.Storyboard>，它有兩個子 <xref:System.Windows.Media.Animation.DoubleAnimation> 物件。  這兩個 <xref:System.Windows.Media.Animation.DoubleAnimation> 物件都會將 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 製作為 0 到 100 的動畫。  <xref:System.Windows.Shapes.Rectangle> 項目有 500 個[與裝置無關的像素](GTMT)的非動畫 <xref:System.Windows.FrameworkElement.Width%2A> 值。  
  
-   第一個 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性設為 <xref:System.Windows.Media.Animation.FillBehavior>，即預設值。  結果是在 <xref:System.Windows.Media.Animation.DoubleAnimation> 結束後，Rectangle 的 Width 仍停留在 100。  
  
-   第二個 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性設為 <xref:System.Windows.Media.Animation.FillBehavior>。  結果是在 <xref:System.Windows.Media.Animation.DoubleAnimation> 結束後，第二個 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 還原成 500。  
  
  
  
<a name="speedproperties"></a>   
## 控制時間表速度的屬性  
 <xref:System.Windows.Media.Animation.Timeline> 類別提供三個用於指定速度的屬性：  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> \- 指定 <xref:System.Windows.Media.Animation.Timeline> 相對於其父代的時間進行比率。  其值大於 1，<xref:System.Windows.Media.Animation.Timeline> 及其子 <xref:System.Windows.Media.Animation.Timeline> 物件的速度會加快；零到 1 的值則減慢。  其值為 1，則表示 <xref:System.Windows.Media.Animation.Timeline> 的進行速度和其父代相同。  容器時間表的 <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> 設定也會影響它所有的子 <xref:System.Windows.Media.Animation.Timeline> 物件。  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> \- 指定 Timeline 的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 進行加速的時間百分比。  如需範例，請參閱 [動畫加速或減速](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md)。  
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> \- 指定 Timeline 的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 進行減速的時間百分比。  如需範例，請參閱 [動畫加速或減速](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md)。  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [計時事件概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)   
 [動畫計時行為範例](http://go.microsoft.com/fwlink/?LinkID=159970)