---
title: 動畫秘訣和訣竅
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting [WPF], animation
- animations [WPF], FillBehavior property
- troubleshooting animation [WPF]
- animating objects [WPF], troubleshooting
- animation tips and tricks [WPF]
- tips and tricks [WPF], animation
- performance troubleshooting [WPF], animation
- animations [WPF], use of system resources
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
ms.openlocfilehash: ef59631663e6cf1c98adfed77a2dbdb6ca124fa1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636025"
---
# <a name="animation-tips-and-tricks"></a>動畫秘訣和訣竅
在 WPF 中使用動畫時，有許多秘訣和訣竅可以讓您的動畫執行得更好，並節省您的挫折。  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>一般問題  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>以動畫顯示捲軸或滑桿位置會凍結  
 如果您使用具有 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> （預設值） <xref:System.Windows.Media.Animation.FillBehavior> 的動畫，以動畫顯示捲軸或滑杆的位置，使用者將無法再移動捲軸或滑杆。 這是因為即使動畫結束，仍然在覆寫目標屬性的基底值。 若要停止動畫覆寫屬性的目前值，請將它移除，或為它提供 <xref:System.Windows.Media.Animation.FillBehavior> 的 <xref:System.Windows.Media.Animation.FillBehavior.Stop>。 如需詳細資訊和範例，請參閱[使用分鏡腳本建立屬性的動畫後進行設定](how-to-set-a-property-after-animating-it-with-a-storyboard.md)。  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>以動畫顯示動畫的輸出沒有任何效果  
 您無法以動畫顯示已是另一個動畫輸出的物件。 例如，如果您使用 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>，以動畫顯示從 <xref:System.Windows.Media.RadialGradientBrush> 到 <xref:System.Windows.Media.SolidColorBrush>之 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>，您就無法以動畫顯示 <xref:System.Windows.Media.RadialGradientBrush> 或 <xref:System.Windows.Media.SolidColorBrush>的任何屬性。  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>無法在以動畫顯示屬性之後變更該屬性的值  
 在某些情況下，即使動畫已結束，您可能無法變更已經以動畫顯示的屬性值。 這是因為即使動畫結束，仍然在覆寫屬性的基底值。 若要停止動畫覆寫屬性的目前值，請將它移除，或為它提供 <xref:System.Windows.Media.Animation.FillBehavior> 的 <xref:System.Windows.Media.Animation.FillBehavior.Stop>。 如需詳細資訊和範例，請參閱[使用分鏡腳本建立屬性的動畫後進行設定](how-to-set-a-property-after-animating-it-with-a-storyboard.md)。  
  
### <a name="changing-a-timeline-has-no-effect"></a>變更時間軸沒有任何作用  
 雖然大部分 <xref:System.Windows.Media.Animation.Timeline> 的屬性都是 animatable 的，而且可以是資料系結的，但變更作用中 <xref:System.Windows.Media.Animation.Timeline> 的屬性值似乎沒有任何效果。 這是因為當 <xref:System.Windows.Media.Animation.Timeline> 開始時，計時系統會建立 <xref:System.Windows.Media.Animation.Timeline> 的複本，並使用它來建立 <xref:System.Windows.Media.Animation.Clock> 物件。 修改原始內容不會影響系統的複本。  
  
 若要讓 <xref:System.Windows.Media.Animation.Timeline> 反映變更，必須重新產生其時鐘並用來取代先前建立的時鐘。 時鐘不會自動產生。 以下是幾種可套用時間軸變更的方式︰  
  
- 如果時間軸是或屬於 <xref:System.Windows.Media.Animation.Storyboard>，您可以使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 或 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法來重新套用其分鏡腳本，使其反映變更。 這也會一併重新啟動動畫。 在程式碼中，您可以使用 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> 方法，將分鏡腳本推進回到先前的位置。  
  
- 如果您使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法將動畫直接套用至屬性，請再次呼叫 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法，並將已修改的動畫傳遞給它。  
  
- 如果您直接在時鐘層級運作，請建立並套用一組新的時鐘，並使用它們來取代前一組產生的時鐘。  
  
 如需時程表和時鐘的詳細資訊，請參閱[動畫和計時系統總覽](animation-and-timing-system-overview.md)。  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop 未如預期運作  
 有時候，將 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性設為 <xref:System.Windows.Media.Animation.FillBehavior.Stop> 似乎沒有任何作用，例如當一個動畫「退出」到另一個動畫時，其 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> 設定為 <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>。  
  
 下列範例會建立一個 <xref:System.Windows.Controls.Canvas>、一個 <xref:System.Windows.Shapes.Rectangle> 和一個 <xref:System.Windows.Media.TranslateTransform>。 <xref:System.Windows.Media.TranslateTransform> 將會以動畫的形式移動 <xref:System.Windows.Controls.Canvas>周圍的 <xref:System.Windows.Shapes.Rectangle>。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 本節中的範例會使用上述物件來示範數個案例，其中 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性的行為不如預期。  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" 且有多個動畫的 HandoffBehavior  
 有時候動畫會在以第二個動畫取代時，忽略它的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性。 請採用下列範例，這會建立兩個 <xref:System.Windows.Media.Animation.Storyboard> 物件，並使用它們以動畫顯示上述範例中的相同 <xref:System.Windows.Media.TranslateTransform>。  
  
 第一個 <xref:System.Windows.Media.Animation.Storyboard>`B1`，會將 <xref:System.Windows.Media.TranslateTransform> 的 <xref:System.Windows.Media.TranslateTransform.X%2A> 屬性從0繪製到350，這會將矩形350圖元向右移動。 當動畫到達其持續時間的結尾並停止播放時，<xref:System.Windows.Media.TranslateTransform.X%2A> 屬性會還原為其原始值0。 結果，矩形會向右移動 350 像素，然後再跳回其原始位置。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 第二個 <xref:System.Windows.Media.Animation.Storyboard>`B2`也會以動畫呈現相同 <xref:System.Windows.Media.TranslateTransform>的 <xref:System.Windows.Media.TranslateTransform.X%2A> 屬性。 因為只有此 <xref:System.Windows.Media.Animation.Storyboard> 中動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性已設定，所以動畫會使用其以動畫形式呈現其起始值之屬性的目前值。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 如果您在第一次 <xref:System.Windows.Media.Animation.Storyboard> 播放時按第二個按鈕，可能會預期下列行為：  
  
1. 第一個分鏡腳本會結束，並將矩形傳回其原始位置，因為動畫具有 <xref:System.Windows.Media.Animation.FillBehavior.Stop>的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>。  
  
2. 第二個分鏡腳本會生效，並從目前的位置 (現在是 0) 以動畫顯示到 500。  
  
 **但這不是發生的動作。** 相反地，矩形並未跳回，而是繼續向右移動。 這是因為第二個動畫使用第一個動畫的目前值做為其開始值，並從該值以動畫顯示到 500。 當第二個動畫因為使用 <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace><xref:System.Windows.Media.Animation.HandoffBehavior> 而取代第一個動畫時，第一個動畫的 <xref:System.Windows.Media.Animation.FillBehavior> 並不重要。  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior 和已完成的事件  
 下一個範例會示範 <xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 似乎沒有作用的另一個案例。 同樣地，此範例會使用分鏡腳本，以動畫顯示 <xref:System.Windows.Media.TranslateTransform> 的 <xref:System.Windows.Media.TranslateTransform.X%2A> 屬性（從0到350）。 不過，這次範例會註冊 <xref:System.Windows.Media.Animation.Timeline.Completed> 事件。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> 事件處理常式會啟動另一個 <xref:System.Windows.Media.Animation.Storyboard>，將相同的屬性從其目前的值繪製到500。  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 以下是將第二個 <xref:System.Windows.Media.Animation.Storyboard> 定義為資源的標記。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 當您執行 <xref:System.Windows.Media.Animation.Storyboard>時，可能會預期 <xref:System.Windows.Media.TranslateTransform> 的 <xref:System.Windows.Media.TranslateTransform.X%2A> 屬性會以動畫方式從0到350，然後在完成後還原為0（因為它具有 <xref:System.Windows.Media.Animation.FillBehavior.Stop>的 <xref:System.Windows.Media.Animation.FillBehavior> 設定），然後從0到500的動畫。 相反地，<xref:System.Windows.Media.TranslateTransform> 會從0到350的動畫，然後再繪製至500。  
  
 這是因為 WPF 引發事件的順序，而且因為屬性值已快取，而且除非屬性失效，否則不會重新計算。 <xref:System.Windows.Media.Animation.Timeline.Completed> 事件會先處理，因為它是由根時程表觸發（第一個 <xref:System.Windows.Media.Animation.Storyboard>）。 此時，<xref:System.Windows.Media.TranslateTransform.X%2A> 屬性仍會傳回其動畫值，因為它尚未失效。 第二個 <xref:System.Windows.Media.Animation.Storyboard> 使用快取的值作為其起始值，並開始製作動畫。  
  
<a name="performancesection"></a>   
## <a name="performance"></a>效能  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>動畫在離開頁面之後繼續執行  
 當您離開包含執行中動畫的 <xref:System.Windows.Controls.Page> 時，這些動畫將會繼續播放，直到 <xref:System.Windows.Controls.Page> 進行垃圾收集為止。 根據使用的導覽系統，您離開的頁面可能會留在記憶體中一段不等的時間，同時會因為動畫而耗用資源。 當頁面含有不斷執行的 (「環境」) 動畫時，這種情形會最明顯。  
  
 基於這個理由，當您離開頁面時，使用 <xref:System.Windows.FrameworkElement.Unloaded> 事件來移除動畫是個不錯的主意。  
  
 移除動畫有許多不同的方式。 下列技巧可以用來移除屬於 <xref:System.Windows.Media.Animation.Storyboard>的動畫。  
  
- 若要移除您從事件觸發程式開始的 <xref:System.Windows.Media.Animation.Storyboard>，請參閱[如何：移除分](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90))鏡腳本。  
  
- 若要使用程式碼移除 <xref:System.Windows.Media.Animation.Storyboard>，請參閱 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> 方法。  
  
 不論啟動動畫的方式為何，都可以使用下一個技術。  
  
- 若要從特定的屬性中移除動畫，請使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> 方法。 指定要製作動畫的屬性做為第一個參數，並 `null` 做為第二個參數。 這將會從屬性移除所有動畫時鐘。  
  
 如需有關如何以動畫顯示內容的不同方式的詳細資訊，請參閱[屬性動畫技術總覽](property-animation-techniques-overview.md)。  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>使用 Compose HandoffBehavior 會耗用系統資源  
 當您使用 <xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.HandoffBehavior>將 <xref:System.Windows.Media.Animation.Storyboard>、<xref:System.Windows.Media.Animation.AnimationTimeline>或 <xref:System.Windows.Media.Animation.AnimationClock> 套用至屬性時，先前與該屬性相關聯的任何 <xref:System.Windows.Media.Animation.Clock> 物件都會繼續使用系統資源;計時系統不會自動移除這些時鐘。  
  
 當您使用 <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>來套用大量時鐘時，若要避免效能問題，您應該在完成後，從動畫屬性中移除撰寫的時鐘。 有幾個方式可移除時鐘。  
  
- 若要從屬性中移除所有時鐘，請使用動畫物件的 <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> 或 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> 方法。 指定要製作動畫的屬性做為第一個參數，並 `null` 做為第二個參數。 這將會從屬性移除所有動畫時鐘。  
  
- 若要從時鐘清單中移除特定的 <xref:System.Windows.Media.Animation.AnimationClock>，請使用 <xref:System.Windows.Media.Animation.AnimationClock> 的 <xref:System.Windows.Media.Animation.Clock.Controller%2A> 屬性來抓取 <xref:System.Windows.Media.Animation.ClockController>，然後呼叫 <xref:System.Windows.Media.Animation.ClockController.Remove%2A> 的 <xref:System.Windows.Media.Animation.ClockController>方法。 這通常會在時鐘的 <xref:System.Windows.Media.Animation.Clock.Completed> 事件處理常式中完成。 請注意，只有根時鐘可由 <xref:System.Windows.Media.Animation.ClockController>控制;子時鐘的 <xref:System.Windows.Media.Animation.Clock.Controller%2A> 屬性會傳回 `null`。 另請注意，如果時鐘的有效持續時間永遠不會呼叫 <xref:System.Windows.Media.Animation.Clock.Completed> 事件。  在此情況下，使用者將需要判斷何時呼叫 <xref:System.Windows.Media.Animation.ClockController.Remove%2A>。  
  
 這主要是在存留期較長的物件才會發生的動畫問題。  記憶體回收物件時，也會中斷連接並記憶體回收其時鐘。  
  
 如需時鐘物件的詳細資訊，請參閱[動畫和計時系統總覽](animation-and-timing-system-overview.md)。  
  
## <a name="see-also"></a>請參閱

- [動畫概觀](animation-overview.md)
