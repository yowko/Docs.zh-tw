---
title: "計時行為概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9305b69927a1ed0ad4f154ab972316f3dee951e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="timing-behaviors-overview"></a>計時行為概觀
本主題描述的執行時間行為的動畫和其他<xref:System.Windows.Media.Animation.Timeline>物件。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該要熟悉基本動畫功能。 如需詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>時間軸型別  
 A<xref:System.Windows.Media.Animation.Timeline>代表一段時間。 它提供的屬性可讓您指定時間片段長度、應開始的時間、重複次數、時間在該片段中的播放速度等等。  
  
 從時間軸類別繼承的類別提供額外功能，例如，動畫和媒體播放。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供下列<xref:System.Windows.Media.Animation.Timeline>型別。  
  
|時間軸型別|描述|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|抽象基底類別<xref:System.Windows.Media.Animation.Timeline>產生輸出值建立屬性的物件。|  
|<xref:System.Windows.Media.MediaTimeline>|從媒體檔案產生輸出。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|一種<xref:System.Windows.Media.Animation.TimelineGroup>群組和控制項子系<xref:System.Windows.Media.Animation.Timeline>物件。|  
|<xref:System.Windows.Media.Animation.Storyboard>|一種<xref:System.Windows.Media.Animation.ParallelTimeline>提供它所包含的時間軸物件的目標資訊。|  
|<xref:System.Windows.Media.Animation.Timeline>|定義計時行為的抽象基底類別。|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|抽象類別，如<xref:System.Windows.Media.Animation.Timeline>可以包含其他物件<xref:System.Windows.Media.Animation.Timeline>物件。|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>控制時間軸長度的屬性  
 A<xref:System.Windows.Media.Animation.Timeline>代表一段時間，並以時間表的長度可以描述不同的方式。 下表定義數個描述時間軸長度的詞彙。  
  
|詞彙|描述|屬性||||  
|----------|-----------------|----------------|-|-|-|  
|簡單持續時間|時間軸正向輪播一次所需的時間長度。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|重複一次|時間長度所花費的時間軸向前播放和之後，<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性為 true，一次反向播放。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|作用期間|花費的時間軸來完成所有重複項目所指定的時間長度其<xref:System.Windows.Media.Animation.RepeatBehavior>屬性。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Duration 屬性  
 如先前所述，時間軸代表一段時間。 區段長度取決於時間軸的<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 當時間到達其持續時間結尾時就會停止播放。 如果該時間軸有子時間軸，它們也會停止播放。 在動畫，<xref:System.Windows.Media.Animation.Timeline.Duration%2A>指定動畫時間轉換從其起始值至它的結束值。 有時稱為 「 時間軸的持續時間其*簡單的持續期間*，以區別單一反覆運算的持續時間和動畫播放包括重複的時間的總長度。 您可以指定使用有限的時間值或特殊值持續時間<xref:System.Windows.Duration.Automatic%2A>或<xref:System.Windows.Duration.Forever%2A>。 動畫的持續時間應該解析為<xref:System.Windows.Duration.TimeSpan%2A>值，因此它可以轉換值之間。  
  
 下列範例所示<xref:System.Windows.Media.Animation.DoubleAnimation>與<xref:System.Windows.Media.Animation.Timeline.Duration%2A>五秒。  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 容器時間表，例如<xref:System.Windows.Media.Animation.Storyboard>和<xref:System.Windows.Media.Animation.ParallelTimeline>，有預設的持續時間<xref:System.Windows.Duration.Automatic%2A>，這表示它們會自動結束時其最後一個子系停止播放。 下列範例所示<xref:System.Windows.Media.Animation.Storyboard>其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>解析為五秒的所有子系所花費的時間長度<xref:System.Windows.Media.Animation.DoubleAnimation>物件完成。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 藉由設定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>容器時間軸的<xref:System.Windows.Duration.TimeSpan%2A>值，您可以強制播放超過或少於其子<xref:System.Windows.Media.Animation.Timeline>物件會播放。 如果您設定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>小於容器時間軸的子系的長度值<xref:System.Windows.Media.Animation.Timeline>物件、 子系<xref:System.Windows.Media.Animation.Timeline>物件停止播放容器時間表執行時。 下列範例會設定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>的<xref:System.Windows.Media.Animation.Storyboard>從先前的範例，以三秒。 如此一來，第一個<xref:System.Windows.Media.Animation.DoubleAnimation>就會停止進行三秒之後，當它具有動畫目標矩形的寬度為 60。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>RepeatBehavior 屬性  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>控制它重複其簡單的持續時間的次數。 使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性，您可以指定多少次在時間表播放 (反覆項目<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) 或它應該播放的時間的總長度 (重複<xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>)。 在任一情況下，動畫會從頭到尾播放數次，以填滿要求的計數或持續時間。 根據預設，時間軸具有的反覆項目計數`1.0`，這表示它們播放一次，且沒有重複。  
  
 下列範例會使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性使<xref:System.Windows.Media.Animation.DoubleAnimation>播放兩次其簡單的持續期間內，藉由指定反覆項目計數。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 下一個範例會使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性使<xref:System.Windows.Media.Animation.DoubleAnimation>播放的一半其簡單持續時間。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 如果您設定<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>至<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>、<xref:System.Windows.Media.Animation.Timeline>會重複，直到停止以互動方式或計時系統。 下列範例會使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性使<xref:System.Windows.Media.Animation.DoubleAnimation>無限期地播放。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 如需其他範例，請參閱[動畫重複](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)。  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>AutoReverse 屬性  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性會指定是否<xref:System.Windows.Media.Animation.Timeline>會在每個向前反覆項目結尾回溯播放。 下列範例會設定為<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性<xref:System.Windows.Media.Animation.DoubleAnimation>至`true`; 如此一來，它繪製從 0 到 100，然後從 100 到零。 播放時間總共 10 秒。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 當您使用<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>值，以指定<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>的<xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性，<xref:System.Windows.Media.Animation.Timeline>是`true`，其中包含單一重複向前反覆項目後面接著一個回溯反覆項目。  下列範例會設定<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>的<xref:System.Windows.Media.Animation.DoubleAnimation>從上述範例<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>兩個。 如此一來，<xref:System.Windows.Media.Animation.DoubleAnimation>播放 20 秒： 轉寄的五秒，向後的五秒轉寄 5 秒一次，然後再向後的五秒。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 如果容器時間表具有子項<xref:System.Windows.Media.Animation.Timeline>物件，這些反向容器時間表執行時。 如需其他範例，請參閱[指定是否時間軸會自動反轉](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)。  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>BeginTime 屬性  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>屬性可讓您指定的時間軸的起點。  時間軸的開始時間和其父時間軸有關。 開始使間為零表示該時間軸的父代一開始它就開始；任何其他值都會在該時間軸的父時間軸與其開始播放時間之間建立位移。 例如，開始時間為 2 秒表示該時間軸會在其父代到達 2 秒時開始播放。 根據預設，所有時間軸的開始時間都為零。 您也可以設定時間軸的開始時間`null`，它可防止在時間軸開始。 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，您可以指定 null 使用[X:null 標記延伸](../../../../docs/framework/xaml-services/x-null-markup-extension.md)。  
  
 請注意，開始時間不是套用時間軸會重複，因為每次它<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>設定。 如果您要建立動畫<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>10 秒，<xref:System.Windows.Media.Animation.RepeatBehavior>的<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，會有 10 秒延遲之前動畫播放第一次，但不是會針對每個後續的重複。 不過，如果動畫的父時間軸重新開始或重複，則 10 秒的延遲會再次出現。  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>屬性可用於交錯配置砸下大筆花費。 下列範例會建立<xref:System.Windows.Media.Animation.Storyboard>具有兩個子<xref:System.Windows.Media.Animation.DoubleAnimation>物件。 第一個動畫的<xref:System.Windows.Media.Animation.Timeline.Duration%2A>五秒的第二個和<xref:System.Windows.Media.Animation.Timeline.Duration%2A>的 3 秒。 範例會設定<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>第二個<xref:System.Windows.Media.Animation.DoubleAnimation>為 5 秒，因此它開始播放後第一個<xref:System.Windows.Media.Animation.DoubleAnimation>結束。  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>FillBehavior 屬性  
 當<xref:System.Windows.Media.Animation.Timeline>存取作用中的總持續時間，結尾<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性會指定是否會停止，或保存其最後一個值。 動畫<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>的<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>「 保留 」 其輸出值： 正在顯示動畫之屬性會保留最後一個值的動畫。 值為<xref:System.Windows.Media.Animation.FillBehavior.Stop>後會結束後，會影響其目標屬性的動畫停止。  
  
 下列範例會建立<xref:System.Windows.Media.Animation.Storyboard>具有兩個子<xref:System.Windows.Media.Animation.DoubleAnimation>物件。 同時<xref:System.Windows.Media.Animation.DoubleAnimation>製作物件動畫<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Shapes.Rectangle>從 0 到 100。 <xref:System.Windows.Shapes.Rectangle>元素具有非動畫<xref:System.Windows.FrameworkElement.Width%2A>500 [裝置無關的像素] 的值。  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性的第一個<xref:System.Windows.Media.Animation.DoubleAnimation>設<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>，預設值。 如此一來，矩形的寬度會保持在之後的 100<xref:System.Windows.Media.Animation.DoubleAnimation>結束。  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性的第二個<xref:System.Windows.Media.Animation.DoubleAnimation>設<xref:System.Windows.Media.Animation.FillBehavior.Stop>。 如此一來，<xref:System.Windows.FrameworkElement.Width%2A>第二個<xref:System.Windows.Shapes.Rectangle>會還原為 500 之後<xref:System.Windows.Media.Animation.DoubleAnimation>結束。  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>控制時間軸速度的屬性  
 <xref:System.Windows.Media.Animation.Timeline>類別提供三個屬性來指定它的速度：  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>– 指定該比率，相對於其父代，時間的進行<xref:System.Windows.Media.Animation.Timeline>。 大於 1 的值增加的速度<xref:System.Windows.Media.Animation.Timeline>及其子<xref:System.Windows.Media.Animation.Timeline>物件中，值介於 0 與速度變慢。 其中一個值，指出<xref:System.Windows.Media.Animation.Timeline>做為其父系的相同速度的進展。 <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>容器時間軸的設定會影響它的所有子<xref:System.Windows.Media.Animation.Timeline>物件。  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>– 指定的百分比<xref:System.Windows.Media.Animation.Timeline.Duration%2A>的時間軸在加速。 如需範例，請參閱[如何： 加速或減速動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md)。 
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>-指定的百分比<xref:System.Windows.Media.Animation.Timeline.Duration%2A>的時間軸在減速。 如需範例，請參閱[如何： 加速或減速動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md)。  
  
## <a name="see-also"></a>請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [計時事件概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [動畫計時行為範例](http://go.microsoft.com/fwlink/?LinkID=159970)
