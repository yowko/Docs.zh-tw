---
title: "動畫秘訣和訣竅 | Microsoft Docs"
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
  - "建立物件的動畫 [WPF], 疑難排解"
  - "動畫秘訣和訣竅 [WPF]"
  - "動畫 [WPF], FillBehavior 屬性"
  - "動畫 [WPF], 使用系統資源"
  - "效能疑難排解 [WPF], 動畫"
  - "秘訣和訣竅 [WPF], 動畫"
  - "疑難排解 [WPF], 動畫"
  - "疑難排解動畫 [WPF]"
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 動畫秘訣和訣竅
在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中使用動畫時，有一些秘訣和訣竅可以讓動畫以較佳的方式執行，並去除您的挫折感。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="generalissuessection"></a>   
## 一般問題  
  
### 建立捲軸或滑桿位置的動畫會凍結捲軸或滑桿  
 如果使用具有 <xref:System.Windows.Media.Animation.FillBehavior> 之 <xref:System.Windows.Media.Animation.FillBehavior> \(預設值\) 的動畫來建立捲軸或滑桿位置的動畫，則使用者會無法再移動捲軸或滑桿。  這是因為即使動畫結束，動畫仍然會覆寫目標屬性的基底值。  若要停止動畫覆寫屬性的目前值，請移除動畫，或將 <xref:System.Windows.Media.Animation.FillBehavior> 的 <xref:System.Windows.Media.Animation.FillBehavior> 指定給動畫。  如需詳細資訊和範例，請參閱 [使用腳本建立屬性的動畫後進行設定](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md)。  
  
### 建立動畫輸出的動畫無效  
 如果物件是另一個動畫的輸出，則無法建立該物件的動畫。  例如，如果使用 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> 來建立 <xref:System.Windows.Shapes.Rectangle> 之 <xref:System.Windows.Shapes.Shape.Fill%2A> 的動畫 \(從 <xref:System.Windows.Media.RadialGradientBrush> 至 <xref:System.Windows.Media.SolidColorBrush>\)，則無法建立 <xref:System.Windows.Media.RadialGradientBrush> 或 <xref:System.Windows.Media.SolidColorBrush> 之任何屬性的動畫。  
  
### 建立屬性值的動畫之後無法變更屬性值  
 在某些情況下，即使動畫已結束，在建立屬性值的動畫之後，還是可能會無法變更該屬性值。  這是因為即使動畫結束，動畫仍然會覆寫屬性的基底值。  若要停止動畫覆寫屬性的目前值，請移除動畫，或將 <xref:System.Windows.Media.Animation.FillBehavior> 的 <xref:System.Windows.Media.Animation.FillBehavior> 指定給動畫。  如需詳細資訊和範例，請參閱 [使用腳本建立屬性的動畫後進行設定](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md)。  
  
### 變更時刻表無效  
 雖然大部分 <xref:System.Windows.Media.Animation.Timeline> 屬性都可以建立動畫，而且可以進行資料繫結，但是變更使用中 <xref:System.Windows.Media.Animation.Timeline> 的屬性值似乎沒有作用。  那是因為當開始 <xref:System.Windows.Media.Animation.Timeline> 時，計時系統會複製 <xref:System.Windows.Media.Animation.Timeline>，並使用該複本來建立 <xref:System.Windows.Media.Animation.Clock> 物件。  因此，對系統複本而言，修改原始項目並沒有任何作用。  
  
 如果 <xref:System.Windows.Media.Animation.Timeline> 要反映變更，則必須重新產生該項目的時鐘，用來取代先前建立的時鐘。  時鐘並不會自動產生。  下列是數種套用時刻表變更的方式：  
  
-   如果時刻表就是或屬於 <xref:System.Windows.Media.Animation.Storyboard>，則使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 或 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法重新套用時刻表的腳本，就可以讓時刻表反映變更。  這個舉動同樣會引發重新啟動動畫的副作用。  在程式碼中，您可以使用 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> 方法將腳本回復到它的前一個位置。  
  
-   如果您已使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法直接將動畫套用至屬性，請再次呼叫 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法，並將修改過的動畫傳遞給它。  
  
-   如果直接在時鐘層級進行處理，請建立及套用一組新的時鐘，並用它們來取代產生的前一組時鐘。  
  
 如需時刻表和時鐘的詳細資訊，請參閱[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)。  
  
### FillBehavior.Stop 未如預期運作  
 有時，將 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性設定為 <xref:System.Windows.Media.Animation.FillBehavior> 似乎沒有作用 \(如因為動畫的 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> 設定為 <xref:System.Windows.Media.Animation.HandoffBehavior> 而將動畫「傳遞」至另一個動畫時\)。  
  
 下列範例會建立 <xref:System.Windows.Controls.Canvas>、<xref:System.Windows.Shapes.Rectangle> 和 <xref:System.Windows.Media.TranslateTransform>。  會建立 <xref:System.Windows.Media.TranslateTransform> 的動畫，以在 <xref:System.Windows.Controls.Canvas> 上移動 <xref:System.Windows.Shapes.Rectangle>。  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 本節範例使用先前的物件來示範多種 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性未如預期運作的情況。  
  
#### FillBehavior\="Stop" 和具有多個動畫的 HandoffBehavior  
 有時，當動畫被第二個動畫取代時，動畫似乎忽略了它的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性。  在下列範例中，會建立兩個 <xref:System.Windows.Media.Animation.Storyboard> 物件，並使用它們來建立先前範例中顯示之相同 <xref:System.Windows.Media.TranslateTransform> 的動畫。  
  
 第一個 <xref:System.Windows.Media.Animation.Storyboard> \(`B1`\) 會將 <xref:System.Windows.Media.TranslateTransform> 之 <xref:System.Windows.Media.TranslateTransform.X%2A> 屬性的動畫從 0 建立到 350，這會將矩形往右移動 350 個像素。  當動畫到達其持續時間的結尾並停止播放時，<xref:System.Windows.Media.TranslateTransform.X%2A> 屬性會回復為它的原始值 0。  因此，矩形會往右移動 350 個像素，然後再跳回它的原始位置。  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 第二個 <xref:System.Windows.Media.Animation.Storyboard> \(`B2`\) 也會建立相同 <xref:System.Windows.Media.TranslateTransform> 之 <xref:System.Windows.Media.TranslateTransform.X%2A> 屬性的動畫。  因為在這個 <xref:System.Windows.Media.Animation.Storyboard> 中只設定動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性，所以動畫會使用用來建立動畫的目前屬性值做為開始值。  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 如果您在播放第一個 <xref:System.Windows.Media.Animation.Storyboard> 時按一下第二個按鈕，可能會希望發生下列行為：  
  
1.  因為動畫具有 <xref:System.Windows.Media.Animation.FillBehavior> 的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>，所以第一個腳本會結束，並將矩形傳送回其原始位置。  
  
2.  第二個腳本會作用，並將動畫從目前位置 0 建立到 500。  
  
 **但結果並不是那樣，** 而是矩形未跳回，而且持續移至右邊。  那是因為第二個動畫使用第一個動畫的目前值做為它的開始值，並將動畫從該值建立到 500。  當第二個動畫因使用 <xref:System.Windows.Media.Animation.HandoffBehavior> <xref:System.Windows.Media.Animation.HandoffBehavior> 而取代第一個動畫時，第一個動畫的 <xref:System.Windows.Media.Animation.FillBehavior> 會沒有作用。  
  
#### FillBehavior 和 Completed 事件  
 下面的範例示範另一個 <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 似乎沒有作用的案例。  同樣地，這些範例會使用「腳本」將 <xref:System.Windows.Media.TranslateTransform> 之 <xref:System.Windows.Media.TranslateTransform.X%2A> 屬性的動畫從 0 建立到 350。  然而，這次範例會註冊 <xref:System.Windows.Media.Animation.Timeline.Completed> 事件。  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> 事件處理常式會啟動另一個 <xref:System.Windows.Media.Animation.Storyboard>，將相同屬性的動畫從目前值建立到 500。  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 下列是將第二個 <xref:System.Windows.Media.Animation.Storyboard> 定義為資源的標記。  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 當您執行 <xref:System.Windows.Media.Animation.Storyboard> 時，可能會預期將 <xref:System.Windows.Media.TranslateTransform> 之 <xref:System.Windows.Media.TranslateTransform.X%2A> 屬性的動畫從 0 建立到 350，然後在完成時回復為 0 \(因為它的 <xref:System.Windows.Media.Animation.FillBehavior> 設定是 <xref:System.Windows.Media.Animation.FillBehavior>\)，然後再將動畫從 0 建立到 500。  但是，<xref:System.Windows.Media.TranslateTransform> 的動畫是從 0 建立到 350，再建立到 500。  
  
 那是由於 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 引發事件的順序，而且因為已快取屬性值，除非屬性失效，否則並不會進行重新計算屬性值。  因為 <xref:System.Windows.Media.Animation.Timeline.Completed> 事件是由根 \(Root\) 時刻表 \(第一個 <xref:System.Windows.Media.Animation.Storyboard>\) 所觸發 \(Trigger\)，所以會先處理該事件。  同時，<xref:System.Windows.Media.TranslateTransform.X%2A> 屬性因未失效，所以仍然會傳回它的動畫值。  第二個 <xref:System.Windows.Media.Animation.Storyboard> 會使用快取值做為它的開始值，並開始建立動畫。  
  
<a name="performancesection"></a>   
## 效能  
  
### 動畫在離開頁面之後繼續執行  
 當您離開包含執行中動畫的 <xref:System.Windows.Controls.Page> 時，除非對 <xref:System.Windows.Controls.Page> 進行記憶體回收，否則那些動畫仍然會繼續播放。  根據使用的巡覽系統，離開的頁面可能會停留在記憶體中一段未定的時間，而它的動畫會耗用資源。  當頁面包含不斷執行的 \(環境 \(Ambient\)\) 動畫時，這最為明顯。  
  
 因此，最好是使用 <xref:System.Windows.FrameworkElement.Unloaded> 事件，在您離開頁面時移除動畫。  
  
 有幾種不同的方式可以移除動畫。  下列技術可以用來移除屬於 <xref:System.Windows.Media.Animation.Storyboard> 的動畫。  
  
-   若要移除利用事件觸發程序所啟動的 <xref:System.Windows.Media.Animation.Storyboard>，請參閱 [How to: Remove a Storyboard](http://msdn.microsoft.com/zh-tw/7fe39531-de2f-46a0-a69f-b783d04235ee)。  
  
-   若要使用程式碼來移除 <xref:System.Windows.Media.Animation.Storyboard>，請參閱 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> 方法。  
  
 不論動畫的啟動方式為何，都可能會使用下一個技術。  
  
-   若要從特定屬性移除動畫，請使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> 方法。  將製作為動畫的屬性指定為第一個參數，以及 `null` 做為第二個參數。  這會將所有動畫時鐘從這個屬性中移除。  
  
 如需各種建立屬性動畫之方式的詳細資訊，請參閱[建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。  
  
### 使用 Compose HandoffBehavior 會耗用系統資源  
 當您使用 <xref:System.Windows.Media.Animation.HandoffBehavior> <xref:System.Windows.Media.Animation.HandoffBehavior> 將 <xref:System.Windows.Media.Animation.Storyboard>、<xref:System.Windows.Media.Animation.AnimationTimeline> 或 <xref:System.Windows.Media.Animation.AnimationClock> 套用至屬性時，先前與該屬性相關聯的任何 <xref:System.Windows.Media.Animation.Clock> 物件仍然會繼續耗用系統資源，計時系統並不會自動移除這些時鐘。  
  
 為避免在使用 <xref:System.Windows.Media.Animation.HandoffBehavior> 套用大量時鐘時發生效能問題，請在完成撰寫時鐘之後，將它們從動畫屬性中移除。  移除時鐘有好幾種方式。  
  
-   若要將所有時鐘從屬性移除，請使用動畫物件的 <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> 或 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> 方法。  將製作為動畫的屬性指定為第一個參數，以及 `null` 做為第二個參數。  這會將所有動畫時鐘從這個屬性中移除。  
  
-   若要將特定 <xref:System.Windows.Media.Animation.AnimationClock> 從時鐘清單移除，請使用 <xref:System.Windows.Media.Animation.AnimationClock> 的 <xref:System.Windows.Media.Animation.Clock.Controller%2A> 屬性擷取 <xref:System.Windows.Media.Animation.ClockController>，然後呼叫 <xref:System.Windows.Media.Animation.ClockController> 的 <xref:System.Windows.Media.Animation.ClockController.Remove%2A> 方法。  這通常是在時鐘的 <xref:System.Windows.Media.Animation.Clock.Completed> 事件處理常式中完成。  請注意，<xref:System.Windows.Media.Animation.ClockController> 只能控制根時鐘，而子時鐘的 <xref:System.Windows.Media.Animation.Clock.Controller%2A> 屬性會傳回 `null`。  同時請注意，如果時鐘的有效持續期間為永久，則不會呼叫 <xref:System.Windows.Media.Animation.Clock.Completed> 事件。  在本案例中，使用者需要決定何時呼叫 <xref:System.Windows.Media.Animation.ClockController.Remove%2A>。  
  
 這主要是將存留期長的物件顯示為動畫時發生的問題。  對物件進行記憶體回收時，也會中斷其時鐘，並一併進行記憶體回收。  
  
 如需時鐘物件的詳細資訊，請參閱[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)。  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)