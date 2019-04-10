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
ms.openlocfilehash: 3a22c83eb739a735d42fa0f670716a0e75bbd54c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295948"
---
# <a name="animation-tips-and-tricks"></a>動畫秘訣和訣竅
使用中的動畫時[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、 有一些秘訣和技巧，讓動畫有較佳，並減少您的挫折。  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>一般問題  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>以動畫顯示捲軸或滑桿位置會凍結  
 如果您以動畫顯示捲軸或使用的動畫會有滑桿的位置<xref:System.Windows.Media.Animation.FillBehavior>的<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>（預設值），使用者將再也無法移動捲軸或滑桿。 這是因為即使動畫結束，仍然在覆寫目標屬性的基底值。 若要停止從覆寫屬性的目前值的動畫，將它移除，或為它提供<xref:System.Windows.Media.Animation.FillBehavior>的<xref:System.Windows.Media.Animation.FillBehavior.Stop>。 如需詳細資訊和範例，請參閱 <<c0> [ 設定屬性之後以動畫顯示使用分鏡腳本](how-to-set-a-property-after-animating-it-with-a-storyboard.md)。  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>以動畫顯示動畫的輸出沒有任何效果  
 您無法以動畫顯示已是另一個動畫輸出的物件。 比方說，如果您使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>來建立動畫<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>從<xref:System.Windows.Media.RadialGradientBrush>來<xref:System.Windows.Media.SolidColorBrush>，您無法以動畫顯示的任何屬性<xref:System.Windows.Media.RadialGradientBrush>或<xref:System.Windows.Media.SolidColorBrush>。  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>無法在以動畫顯示屬性之後變更該屬性的值  
 在某些情況下，即使動畫已結束，您可能無法變更已經以動畫顯示的屬性值。 這是因為即使動畫結束，仍然在覆寫屬性的基底值。 若要停止從覆寫屬性的目前值的動畫，將它移除，或為它提供<xref:System.Windows.Media.Animation.FillBehavior>的<xref:System.Windows.Media.Animation.FillBehavior.Stop>。 如需詳細資訊和範例，請參閱 <<c0> [ 設定屬性之後以動畫顯示使用分鏡腳本](how-to-set-a-property-after-animating-it-with-a-storyboard.md)。  
  
### <a name="changing-a-timeline-has-no-effect"></a>變更時間軸沒有任何作用  
 雖然大部分<xref:System.Windows.Media.Animation.Timeline>屬性都可顯示動畫，並可進行資料繫結，變更使用中的屬性值<xref:System.Windows.Media.Animation.Timeline>似乎沒有任何作用。 這是因為，當<xref:System.Windows.Media.Animation.Timeline>是開始時，計時系統會建立一份<xref:System.Windows.Media.Animation.Timeline>並使用它來建立<xref:System.Windows.Media.Animation.Clock>物件。 修改原始內容不會影響系統的複本。  
  
 針對<xref:System.Windows.Media.Animation.Timeline>以反映變更，其時鐘必須重新產生並用以取代先前建立的時鐘。 時鐘不會自動產生。 以下是幾種可套用時間軸變更的方式︰  
  
-   如果時間軸是或屬於<xref:System.Windows.Media.Animation.Storyboard>，您可以將它重新套用其分鏡腳本的使用，以反映變更<xref:System.Windows.Media.Animation.BeginStoryboard>或<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法。 這也會一併重新啟動動畫。 在程式碼中，您可以使用<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>方法將分鏡腳本回它先前的位置。  
  
-   如果您直接將屬性套用動畫<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法中，呼叫<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法一次，並將它傳遞已修改的動畫。  
  
-   如果您直接在時鐘層級運作，請建立並套用一組新的時鐘，並使用它們來取代前一組產生的時鐘。  
  
 如需有關時間軸和時鐘的詳細資訊，請參閱[動畫和計時系統概觀](animation-and-timing-system-overview.md)。  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop 未如預期運作  
 有些時候設定時<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性，以<xref:System.Windows.Media.Animation.FillBehavior.Stop>似乎沒有任何作用，例如當一個動畫 「 遞交到 」 另一個因為它有<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>設定<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>。  
  
 下列範例會建立<xref:System.Windows.Controls.Canvas>，則<xref:System.Windows.Shapes.Rectangle>和<xref:System.Windows.Media.TranslateTransform>。 <xref:System.Windows.Media.TranslateTransform>會將動畫<xref:System.Windows.Shapes.Rectangle>周圍<xref:System.Windows.Controls.Canvas>。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 在本節中的範例來示範幾種情況下使用上述物件所在<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性行為不如您預期。  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" 且有多個動畫的 HandoffBehavior  
 有時候這看起來像是動畫會忽略其<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>時它會取代第二個動畫的屬性。 需要下列的範例中，會建立兩個<xref:System.Windows.Media.Animation.Storyboard>物件，並使用它們以動畫顯示相同<xref:System.Windows.Media.TranslateTransform>上述範例所示。  
  
 第一個<xref:System.Windows.Media.Animation.Storyboard>， `B1`，以動畫顯示<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>從 0 到 350，其中矩形 350 像素為單位向右移動。 當動畫到達其持續時間結尾，並停止播放，<xref:System.Windows.Media.TranslateTransform.X%2A>屬性還原成其原始值為 0。 結果，矩形會向右移動 350 像素，然後再跳回其原始位置。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 第二個<xref:System.Windows.Media.Animation.Storyboard>， `B2`，也以動畫顯示<xref:System.Windows.Media.TranslateTransform.X%2A>屬性的相同<xref:System.Windows.Media.TranslateTransform>。 因為只有<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>在此動畫的屬性<xref:System.Windows.Media.Animation.Storyboard>設定動畫建立動畫之屬性的目前值做為其起始值。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 如果您按一下第二個按鈕，在第一個<xref:System.Windows.Media.Animation.Storyboard>是正在播放，您可能預期下列行為：  
  
1. 第一個分鏡腳本結束，並將矩形傳送回其原始位置，因為動畫<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>的<xref:System.Windows.Media.Animation.FillBehavior.Stop>。  
  
2. 第二個分鏡腳本會生效，並從目前的位置 (現在是 0) 以動畫顯示到 500。  
  
 **但這不會發生什麼事。** 相反地，矩形並未跳回，而是繼續向右移動。 這是因為第二個動畫使用第一個動畫的目前值做為其開始值，並從該值以動畫顯示到 500。 當第二個動畫會取代第一個因為<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace><xref:System.Windows.Media.Animation.HandoffBehavior>使用時，<xref:System.Windows.Media.Animation.FillBehavior>的第一個動畫並不重要。  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior 和已完成的事件  
 下面的範例示範另一個案例，其中<xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>似乎沒有任何作用。 同樣地，此範例會使用分鏡腳本以動畫顯示<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>從 0 到 350。 不過，這次範例會註冊<xref:System.Windows.Media.Animation.Timeline.Completed>事件。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed>事件處理常式會啟動另一個<xref:System.Windows.Media.Animation.Storyboard>，以動畫顯示相同屬性從其目前的值設為 500。  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 以下是定義第二個標記<xref:System.Windows.Media.Animation.Storyboard>做為資源。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 當您執行<xref:System.Windows.Media.Animation.Storyboard>，您所料<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>動畫從 0 到 350，然後還原為 0 完成後 (因為它有<xref:System.Windows.Media.Animation.FillBehavior>設定<xref:System.Windows.Media.Animation.FillBehavior.Stop>)，並再建立動畫從 0 到 500。 相反地，<xref:System.Windows.Media.TranslateTransform>從以動畫顯示 0 到 350，然後到 500。  
  
 這是因為順序[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]引發事件，而且因為屬性值會快取，而且不重新計算除非屬性失效。 <xref:System.Windows.Media.Animation.Timeline.Completed>事件會先處理，因為它已觸發由根時間軸 (第一個<xref:System.Windows.Media.Animation.Storyboard>)。 此時，<xref:System.Windows.Media.TranslateTransform.X%2A>屬性仍會傳回其動畫的值，因為它尚未失效。 第二個<xref:System.Windows.Media.Animation.Storyboard>快取的值做為其起始值，並開始以動畫顯示。  
  
<a name="performancesection"></a>   
## <a name="performance"></a>效能  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>動畫在離開頁面之後繼續執行  
 當您瀏覽離開<xref:System.Windows.Controls.Page>，其中包含執行的動畫，這些動畫都會繼續播放，直到<xref:System.Windows.Controls.Page>回收。 根據使用的導覽系統，您離開的頁面可能會留在記憶體中一段不等的時間，同時會因為動畫而耗用資源。 當頁面含有不斷執行的 (「環境」) 動畫時，這種情形會最明顯。  
  
 基於這個理由，是個不錯的主意，若要使用<xref:System.Windows.FrameworkElement.Unloaded>事件移除動畫，當您離開頁面。  
  
 移除動畫有許多不同的方式。 下列技術可用來移除屬於動畫<xref:System.Windows.Media.Animation.Storyboard>。  
  
-   若要移除<xref:System.Windows.Media.Animation.Storyboard>您開始使用事件觸發程序，請參閱[How to:移除分鏡腳本](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90))。  
  
-   若要使用程式碼來移除<xref:System.Windows.Media.Animation.Storyboard>，請參閱<xref:System.Windows.Media.Animation.Storyboard.Remove%2A>方法。  
  
 不論啟動動畫的方式為何，都可以使用下一個技術。  
  
-   若要移除的特定屬性的動畫，請使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>方法。 指定的第一個參數，要繪製之屬性和`null`作為第二個。 這將會從屬性移除所有動畫時鐘。  
  
 如需以動畫顯示屬性的不同方式的詳細資訊，請參閱[屬性動畫技術概觀](property-animation-techniques-overview.md)。  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>使用 Compose HandoffBehavior 會耗用系統資源  
 當您套用<xref:System.Windows.Media.Animation.Storyboard>， <xref:System.Windows.Media.Animation.AnimationTimeline>，或<xref:System.Windows.Media.Animation.AnimationClock>屬性，使用<xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.HandoffBehavior>、 任何<xref:System.Windows.Media.Animation.Clock>先前該屬性相關聯的物件會繼續耗用系統資源，計時系統將不會移除這些時鐘自動的。  
  
 若要避免發生效能問題，當您套用大量時鐘使用<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>，完成之後，您應該從動畫屬性移除組成的時鐘。 有幾個方式可移除時鐘。  
  
-   若要從屬性移除所有時鐘，請使用<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29>或<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>動畫物件的方法。 指定的第一個參數，要繪製之屬性和`null`作為第二個。 這將會從屬性移除所有動畫時鐘。  
  
-   若要移除特定<xref:System.Windows.Media.Animation.AnimationClock>從時鐘清單，使用<xref:System.Windows.Media.Animation.Clock.Controller%2A>屬性<xref:System.Windows.Media.Animation.AnimationClock>擷取<xref:System.Windows.Media.Animation.ClockController>，然後呼叫<xref:System.Windows.Media.Animation.ClockController.Remove%2A>方法<xref:System.Windows.Media.Animation.ClockController>。 這通常是<xref:System.Windows.Media.Animation.Clock.Completed>時鐘的事件處理常式。 請注意，只有根時鐘可以控制<xref:System.Windows.Media.Animation.ClockController>;<xref:System.Windows.Media.Animation.Clock.Controller%2A>的子系時鐘的屬性會傳回`null`。 也請注意，<xref:System.Windows.Media.Animation.Clock.Completed>是否有效的持續時間的時鐘永遠不會呼叫事件。  在此情況下，使用者必須決定何時要呼叫<xref:System.Windows.Media.Animation.ClockController.Remove%2A>。  
  
 這主要是在存留期較長的物件才會發生的動畫問題。  記憶體回收物件時，也會中斷連接並記憶體回收其時鐘。  
  
 如需時鐘物件的詳細資訊，請參閱[動畫和計時系統概觀](animation-and-timing-system-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
