---
title: 計時行為概觀
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: a85f980a0cefaa282e9e92d533a2306a9009e3e7
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559946"
---
# <a name="timing-behaviors-overview"></a>計時行為概觀
本主題描述動畫和其他 <xref:System.Windows.Media.Animation.Timeline> 物件的計時行為。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件：  
 若要了解本主題，您應該要熟悉基本動畫功能。 如需詳細資訊，請參閱[動畫總覽](animation-overview.md)。  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>時間軸型別  
 <xref:System.Windows.Media.Animation.Timeline> 代表時間區段。 它提供的屬性可讓您指定時間片段長度、應開始的時間、重複次數、時間在該片段中的播放速度等等。  
  
 從時間軸類別繼承的類別提供額外功能，例如，動畫和媒體播放。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供下列 <xref:System.Windows.Media.Animation.Timeline> 類型。  
  
|時間軸型別|描述|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|產生動畫屬性之輸出值的 <xref:System.Windows.Media.Animation.Timeline> 物件的抽象基類。|  
|<xref:System.Windows.Media.MediaTimeline>|從媒體檔案產生輸出。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|一種 <xref:System.Windows.Media.Animation.TimelineGroup> 類型，可將子 <xref:System.Windows.Media.Animation.Timeline> 物件分組並加以控制。|  
|<xref:System.Windows.Media.Animation.Storyboard>|一種 <xref:System.Windows.Media.Animation.ParallelTimeline> 類型，提供其所包含之時程表物件的目標資訊。|  
|<xref:System.Windows.Media.Animation.Timeline>|定義計時行為的抽象基底類別。|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|可包含其他 <xref:System.Windows.Media.Animation.Timeline> 物件之 <xref:System.Windows.Media.Animation.Timeline> 物件的抽象類別。|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>控制時間軸長度的屬性  
 <xref:System.Windows.Media.Animation.Timeline> 代表時間區段，而且時間軸的長度可以透過不同的方式來描述。 下表定義數個描述時間軸長度的詞彙。  
  
|詞彙|描述|屬性||||  
|----------|-----------------|----------------|-|-|-|  
|簡單持續時間|時間軸正向輪播一次所需的時間長度。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|重複一次|時間軸播放一次所需的時間長度，如果 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性為 true，則立即播放一次。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>、 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|作用期間|時間軸完成其 <xref:System.Windows.Media.Animation.RepeatBehavior> 屬性所指定之所有重複動作所花費的時間長度。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>中， <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>中， <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Duration 屬性  
 如先前所述，時間軸代表一段時間。 該區段的長度取決於時間軸的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 當時間到達其持續時間結尾時就會停止播放。 如果該時間軸有子時間軸，它們也會停止播放。 在動畫的案例中，<xref:System.Windows.Media.Animation.Timeline.Duration%2A> 會指定動畫從其起始值轉換為結束值所需的時間長度。 時間軸的持續時間有時稱為其*簡單的持續時間*，以區別單一反復專案的持續時間，以及動畫播放的總時間長度，包括重複。 您可以使用有限的時間值或特殊值 <xref:System.Windows.Duration.Automatic%2A> 或 <xref:System.Windows.Duration.Forever%2A>來指定持續時間。 動畫的持續時間應該會解析為 <xref:System.Windows.Duration.TimeSpan%2A> 值，因此可以在值之間轉換。  
  
 下列範例顯示具有五秒 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 的 <xref:System.Windows.Media.Animation.DoubleAnimation>。  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 容器時間軸（例如 <xref:System.Windows.Media.Animation.Storyboard> 和 <xref:System.Windows.Media.Animation.ParallelTimeline>）具有預設的 <xref:System.Windows.Duration.Automatic%2A>持續時間，這表示它們會在最後一個子系停止播放時自動結束。 下列範例顯示的 <xref:System.Windows.Media.Animation.Storyboard>，其 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 會解析為五秒，也就是其所有子 <xref:System.Windows.Media.Animation.DoubleAnimation> 物件完成所需的時間長度。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 藉由將容器時間軸的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 設定為 <xref:System.Windows.Duration.TimeSpan%2A> 值，您可以強制播放較長或更短的時間，而不會播放其子 <xref:System.Windows.Media.Animation.Timeline> 物件。 如果您將 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 設定為小於容器時間軸之子 <xref:System.Windows.Media.Animation.Timeline> 物件長度的值，則當容器時間軸執行時，子 <xref:System.Windows.Media.Animation.Timeline> 物件就會停止播放。 下列範例會將上述範例中 <xref:System.Windows.Media.Animation.Storyboard> 的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 設定為三秒。 因此，第一個 <xref:System.Windows.Media.Animation.DoubleAnimation> 會在三秒後停止進行（當它將目標矩形的寬度以動畫顯示為60時）。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>RepeatBehavior 屬性  
 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性會控制它重複其簡單持續時間的次數。 您可以使用 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性，指定時間軸播放的次數（反復專案 <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>）或其播放的總時間（重複的 <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>）。 在任一情況下，動畫會從頭到尾播放數次，以填滿要求的計數或持續時間。 根據預設，時間軸具有 `1.0`的反復專案計數，這表示它們會播放一次，而且完全不重複。  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性，藉由指定反復專案計數，讓 <xref:System.Windows.Media.Animation.DoubleAnimation> 播放兩倍的簡單持續時間。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 下一個範例會使用 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性，讓 <xref:System.Windows.Media.Animation.DoubleAnimation> 播放一半的簡單持續時間。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 如果您將 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性設定為 <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，<xref:System.Windows.Media.Animation.Timeline> 會重複，直到以互動方式或計時系統停止為止。 下列範例會使用 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性，讓 <xref:System.Windows.Media.Animation.DoubleAnimation> 無限期播放。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 如需其他範例，請參閱[重複動畫](how-to-repeat-an-animation.md)。  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>AutoReverse 屬性  
 [<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>] 屬性會指定 <xref:System.Windows.Media.Animation.Timeline> 是否會在每個向前反覆運算結束時向後播放。 下列範例會將設定為 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性，以 `true`;因此，它會從零繪製到100，然後從100到零的動畫。 播放時間總共 10 秒。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 當您使用 <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> 值來指定 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>，以及該 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性 `true`時，單一重複會包含一個正向反復專案，後面接著一個回溯反復專案。  下列範例會將上述範例中 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 設定為兩個的 <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>。 如此一來，<xref:System.Windows.Media.Animation.DoubleAnimation> 將會播放20秒：向前復原五秒，再向前復原5秒，然後反向五秒。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 如果容器時間軸具有子 <xref:System.Windows.Media.Animation.Timeline> 物件，則會在容器時間軸執行時反轉。 如需其他範例，請參閱[指定時程表是否自動反轉](how-to-specify-whether-a-timeline-automatically-reverses.md)。  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>BeginTime 屬性  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 屬性可讓您指定時間軸何時啟動。  時間軸的開始時間和其父時間軸有關。 開始使間為零表示該時間軸的父代一開始它就開始；任何其他值都會在該時間軸的父時間軸與其開始播放時間之間建立位移。 例如，開始時間為 2 秒表示該時間軸會在其父代到達 2 秒時開始播放。 根據預設，所有時間軸的開始時間都為零。 您也可以將時間軸的開始時間設定為 `null`，這會使時間軸無法啟動。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中，您可以使用[X:Null 標記延伸](../../../desktop-wpf/xaml-services/xnull-markup-extension.md)來指定 null。  
  
 請注意，當時間軸因為其 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 設定而重複時，不會套用開始時間。 如果您要建立 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 為10秒的動畫，以及 <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>的 <xref:System.Windows.Media.Animation.RepeatBehavior>，則第一次播放動畫前會有10秒的延遲，但不會針對每個後續的重複進行。 不過，如果動畫的父時間軸重新開始或重複，則 10 秒的延遲會再次出現。  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 屬性適用于錯開的時間軸。 下列範例會建立具有兩個子 <xref:System.Windows.Media.Animation.DoubleAnimation> 物件的 <xref:System.Windows.Media.Animation.Storyboard>。 第一個動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 為5秒，而第二個動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 為3秒。 此範例會將第二個 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 設為5秒，以便在第一個 <xref:System.Windows.Media.Animation.DoubleAnimation> 結束後開始播放。  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>FillBehavior 屬性  
 當 <xref:System.Windows.Media.Animation.Timeline> 達到其作用中持續時間總計的結尾時，<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性會指定它是要停止還是保留其最後一個值。 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 為 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> 「保留」其輸出值的動畫：所要動畫的屬性會保留動畫的最後一個值。 <xref:System.Windows.Media.Animation.FillBehavior.Stop> 的值，會導致動畫在結束後停止影響其目標屬性。  
  
 下列範例會建立具有兩個子 <xref:System.Windows.Media.Animation.DoubleAnimation> 物件的 <xref:System.Windows.Media.Animation.Storyboard>。 這兩個 <xref:System.Windows.Media.Animation.DoubleAnimation> 物件都會以動畫顯示從0到 100 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A>。 <xref:System.Windows.Shapes.Rectangle> 的元素具有非動畫的 <xref:System.Windows.FrameworkElement.Width%2A> 值 500 [與裝置無關的圖元]。  
  
- 第一個 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性會設定為 [<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>] （預設值）。 因此，在 <xref:System.Windows.Media.Animation.DoubleAnimation> 結束之後，矩形的寬度會維持在100。  
  
- 第二個 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性會設定為 [<xref:System.Windows.Media.Animation.FillBehavior.Stop>]。 因此，第二個 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會在 <xref:System.Windows.Media.Animation.DoubleAnimation> 結束後還原為500。  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>控制時間軸速度的屬性  
 <xref:System.Windows.Media.Animation.Timeline> 類別提供三個屬性來指定其速度：  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> –指定相對於其父系的速率，這是針對 <xref:System.Windows.Media.Animation.Timeline>進行的時間。 大於1的值會增加 <xref:System.Windows.Media.Animation.Timeline> 及其子 <xref:System.Windows.Media.Animation.Timeline> 物件的速度;介於0和1之間的值會變慢。 值為1時，表示 <xref:System.Windows.Media.Animation.Timeline> 以與父系相同的速率進行。 容器時間軸的 <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> 設定也會影響其所有子 <xref:System.Windows.Media.Animation.Timeline> 物件。  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> –指定花費在加速的時間軸 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 百分比。 如需範例，請參閱[如何：加速或減速動畫](how-to-accelerate-or-decelerate-an-animation.md)。 
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>-指定花費在減速之時間軸 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 的百分比。 如需範例，請參閱[如何：加速或減速動畫](how-to-accelerate-or-decelerate-an-animation.md)。  
  
## <a name="see-also"></a>請參閱

- [動畫概觀](animation-overview.md)
- [動畫和計時系統概觀](animation-and-timing-system-overview.md)
- [計時事件概觀](timing-events-overview.md)
- [「如何」主題](animation-and-timing-how-to-topics.md)
- [動畫計時行為範例](https://go.microsoft.com/fwlink/?LinkID=159970)
