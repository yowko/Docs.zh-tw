---
title: 計時行為概觀
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 3bb42ddd991d3ae1221cc794afdd4aafc74a6046
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145393"
---
# <a name="timing-behaviors-overview"></a>計時行為概觀
本主題介紹動畫和其他<xref:System.Windows.Media.Animation.Timeline>物件的計時行為。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該要熟悉基本動畫功能。 有關詳細資訊，請參閱[動畫概述](animation-overview.md)。  
  
<a name="timelinetypes"></a>
## <a name="timeline-types"></a>時間軸型別  
 A<xref:System.Windows.Media.Animation.Timeline>表示時間段。 它提供的屬性可讓您指定時間片段長度、應開始的時間、重複次數、時間在該片段中的播放速度等等。  
  
 從時間軸類別繼承的類別提供額外功能，例如，動畫和媒體播放。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供了以下<xref:System.Windows.Media.Animation.Timeline>類型。  
  
|時間軸型別|描述|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|為屬性生成輸出<xref:System.Windows.Media.Animation.Timeline>值的物件的抽象基類。|  
|<xref:System.Windows.Media.MediaTimeline>|從媒體檔案產生輸出。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.TimelineGroup>該組和控制子<xref:System.Windows.Media.Animation.Timeline>物件的一種類型。|  
|<xref:System.Windows.Media.Animation.Storyboard>|提供<xref:System.Windows.Media.Animation.ParallelTimeline>其包含的時間表物件的定位資訊的類型。|  
|<xref:System.Windows.Media.Animation.Timeline>|定義計時行為的抽象基底類別。|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|可以包含其他<xref:System.Windows.Media.Animation.Timeline><xref:System.Windows.Media.Animation.Timeline>物件的物件的抽象類別。|  
  
<a name="propertiesthatcontroltimelinelength"></a>
## <a name="properties-that-control-the-length-of-a-timeline"></a>控制時間軸長度的屬性  
 表示<xref:System.Windows.Media.Animation.Timeline>時間段，可以以不同的方式描述時間表的長度。 下表定義數個描述時間軸長度的詞彙。  
  
|詞彙|描述|屬性||||  
|----------|-----------------|----------------|-|-|-|  
|簡單持續時間|時間軸正向輪播一次所需的時間長度。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|重複一次|時間表向前播放一次所需的時間長度，如果<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性為 true，則向後播放一次。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|作用期間|時間表完成其<xref:System.Windows.Media.Animation.RepeatBehavior>屬性指定的所有重複所需的時間長度。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>
### <a name="the-duration-property"></a>Duration 屬性  
 如先前所述，時間軸代表一段時間。 該段的長度由時間表的<xref:System.Windows.Media.Animation.Timeline.Duration%2A>確定。 當時間到達其持續時間結尾時就會停止播放。 如果該時間軸有子時間軸，它們也會停止播放。 在動畫的情況下， 指定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>動畫從起始值過渡到其結束值所需的時間。 時間表的持續時間有時稱為*其簡單持續時間*，以區分單個反覆運算的持續時間和動畫播放的總時間長度（包括重複）。 可以使用有限時間值或特殊值<xref:System.Windows.Duration.Automatic%2A>或<xref:System.Windows.Duration.Forever%2A>指定持續時間。 動畫的持續時間應解析為<xref:System.Windows.Duration.TimeSpan%2A>值，以便它可以在值之間轉換。  
  
 下面的示例顯示 a<xref:System.Windows.Media.Animation.DoubleAnimation><xref:System.Windows.Media.Animation.Timeline.Duration%2A>的五秒。  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 容器時間表（如<xref:System.Windows.Media.Animation.Storyboard>和<xref:System.Windows.Media.Animation.ParallelTimeline>）的預設持續時間為<xref:System.Windows.Duration.Automatic%2A>，這意味著它們在最後一個子級停止播放時會自動結束。 下面的示例顯示其<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.Animation.Timeline.Duration%2A>解析為五秒的 a，即完成其所有子<xref:System.Windows.Media.Animation.DoubleAnimation>物件所需的時間長度。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>通過將容器時間表設置為<xref:System.Windows.Duration.TimeSpan%2A>值，可以強制播放比其子<xref:System.Windows.Media.Animation.Timeline>物件播放的時間更長或短。 如果將 設置為<xref:System.Windows.Media.Animation.Timeline.Duration%2A>小於容器時間表子<xref:System.Windows.Media.Animation.Timeline>物件長度的值，則子<xref:System.Windows.Media.Animation.Timeline>物件在容器時間表時停止播放。 下面的示例將<xref:System.Windows.Media.Animation.Timeline.Duration%2A>上述示例中的<xref:System.Windows.Media.Animation.Storyboard>的 將 集 到三秒。 因此，第一個<xref:System.Windows.Media.Animation.DoubleAnimation>停止在三秒鐘後前進，當它已動畫的目標矩形的寬度到60。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>
### <a name="the-repeatbehavior-property"></a>RepeatBehavior 屬性  
 屬性<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A><xref:System.Windows.Media.Animation.Timeline>控制它重複其簡單持續時間的次數。 使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性，可以指定時間表播放的次數（反覆運算<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>）或時間表應播放的總時間長度（重複）。 <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A> 在任一情況下，動畫會從頭到尾播放數次，以填滿要求的計數或持續時間。 預設情況下，時間表的反覆運算計數為`1.0`，這意味著它們播放一次，並且根本不重複。  
  
 下面的示例使用 屬性<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>通過指定反覆運算計數<xref:System.Windows.Media.Animation.DoubleAnimation>使播放具有兩倍的簡單持續時間。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 下一個示例使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性使<xref:System.Windows.Media.Animation.DoubleAnimation>該遊戲的一半簡單持續時間。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 如果將<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>設置為<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，則<xref:System.Windows.Media.Animation.Timeline>重複，直到以對話模式或由計時系統停止。 下面的示例使用 屬性<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>無限期地進行<xref:System.Windows.Media.Animation.DoubleAnimation>播放。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 有關其他示例，請參閱[重複動畫](how-to-repeat-an-animation.md)。  
  
<a name="autoreverseproperty"></a>
### <a name="the-autoreverse-property"></a>AutoReverse 屬性  
 屬性<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>指定 將在<xref:System.Windows.Media.Animation.Timeline>每次向前反覆運算結束時向後播放 。 下面的示例將設置到<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>的 屬性<xref:System.Windows.Media.Animation.DoubleAnimation> `true`。因此，它將動畫從零到 100，然後從 100 到零。 播放時間總共 10 秒。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>當使用 值指定 的<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A><xref:System.Windows.Media.Animation.Timeline><xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>和 屬性時<xref:System.Windows.Media.Animation.Timeline>`true`，單個重複由一個向前反覆運算組成，後跟一個向後反覆運算。  下面的示例將<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A><xref:System.Windows.Media.Animation.DoubleAnimation>上一個示例的 將 的<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>將 集的 2 個集。 結果，<xref:System.Windows.Media.Animation.DoubleAnimation>播放 20 秒：向前 5 秒，向後 5 秒，再次向前前進 5 秒，然後向後向後 5 秒。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 如果容器時間表具有子<xref:System.Windows.Media.Animation.Timeline>物件，則當容器時間表執行時，它們會反轉。 有關其他示例，請參閱[指定時間表是否自動反轉](how-to-specify-whether-a-timeline-automatically-reverses.md)。  
  
<a name="timelinebegin"></a>
## <a name="the-begintime-property"></a>BeginTime 屬性  
 屬性<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>使您能夠指定時間表何時啟動。  時間軸的開始時間和其父時間軸有關。 開始使間為零表示該時間軸的父代一開始它就開始；任何其他值都會在該時間軸的父時間軸與其開始播放時間之間建立位移。 例如，開始時間為 2 秒表示該時間軸會在其父代到達 2 秒時開始播放。 根據預設，所有時間軸的開始時間都為零。 您還可以將時間表的開始時間設置為`null`，這可以防止時間表啟動。 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中，使用[x：空白標記副檔名](../../../desktop-wpf/xaml-services/xnull-markup-extension.md)指定 null。  
  
 請注意，每次時間表因其<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>設置而重複時，不會應用開始時間。 如果要創建具有<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>10 秒和 1<xref:System.Windows.Media.Animation.RepeatBehavior>的<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>動畫，則在首次播放動畫之前會有 10 秒的延遲，但每次連續重複時不會延遲。 不過，如果動畫的父時間軸重新開始或重複，則 10 秒的延遲會再次出現。  
  
 該<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>屬性可用於驚人的時間表。 下面的示例創建具有兩<xref:System.Windows.Media.Animation.Storyboard>個子<xref:System.Windows.Media.Animation.DoubleAnimation>物件的 。 第一<xref:System.Windows.Media.Animation.Timeline.Duration%2A>個動畫有 5 秒，第二個<xref:System.Windows.Media.Animation.Timeline.Duration%2A>動畫有 3 秒。 該示例將第<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>二<xref:System.Windows.Media.Animation.DoubleAnimation>秒設置為 5 秒，以便它在第一<xref:System.Windows.Media.Animation.DoubleAnimation>端後開始播放。  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>
## <a name="the-fillbehavior-property"></a>FillBehavior 屬性  
 當<xref:System.Windows.Media.Animation.Timeline>達到其總活動持續時間的末尾時，<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性指定它是停止還是保留其最後一個值。 具有"保留"<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>其<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>輸出值的動畫：正在動畫的屬性將保留動畫的最後一個值。 動畫結束後<xref:System.Windows.Media.Animation.FillBehavior.Stop>停止影響其目標屬性的值。  
  
 下面的示例創建具有兩<xref:System.Windows.Media.Animation.Storyboard>個子<xref:System.Windows.Media.Animation.DoubleAnimation>物件的 。 兩<xref:System.Windows.Media.Animation.DoubleAnimation>個物件為<xref:System.Windows.FrameworkElement.Width%2A>0<xref:System.Windows.Shapes.Rectangle>到 100 的 動畫。 元素<xref:System.Windows.Shapes.Rectangle>的非動畫<xref:System.Windows.FrameworkElement.Width%2A>值為 500 [設備無關圖元]。  
  
- 第<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>一<xref:System.Windows.Media.Animation.DoubleAnimation>個的屬性設置為<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>，預設值。 因此，矩形的寬度在<xref:System.Windows.Media.Animation.DoubleAnimation>結束後保持在 100。  
  
- 第<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>二<xref:System.Windows.Media.Animation.DoubleAnimation>個屬性設置為<xref:System.Windows.Media.Animation.FillBehavior.Stop>。 因此，第<xref:System.Windows.FrameworkElement.Width%2A>二<xref:System.Windows.Shapes.Rectangle>個在<xref:System.Windows.Media.Animation.DoubleAnimation>結束後將恢復為 500。  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>
## <a name="properties-that-control-the-speed-of-a-timeline"></a>控制時間軸速度的屬性  
 類<xref:System.Windows.Media.Animation.Timeline>提供了三個屬性來指定其速度：  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>• 指定相對於其父級的速率，此時將進行<xref:System.Windows.Media.Animation.Timeline>。 大於 1 的值會增加<xref:System.Windows.Media.Animation.Timeline>及其子<xref:System.Windows.Media.Animation.Timeline>物件的速度;零和 1 之間的值減慢速度。 值 1 表示<xref:System.Windows.Media.Animation.Timeline>以與其父值相同的速率前進。 容器<xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>時間表的設置也會影響其所有子<xref:System.Windows.Media.Animation.Timeline>物件。  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>• 指定加速花費的時間<xref:System.Windows.Media.Animation.Timeline.Duration%2A>軸的百分比。 例如，請參閱[如何：加速或減速動畫](how-to-accelerate-or-decelerate-an-animation.md)。
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>- 指定時間軸的<xref:System.Windows.Media.Animation.Timeline.Duration%2A>百分比，用於減速。 例如，請參閱[如何：加速或減速動畫](how-to-accelerate-or-decelerate-an-animation.md)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [動畫和計時系統概觀](animation-and-timing-system-overview.md)
- [計時事件概觀](timing-events-overview.md)
- [如何使用主題](animation-and-timing-how-to-topics.md)
- [動畫計時行為範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
