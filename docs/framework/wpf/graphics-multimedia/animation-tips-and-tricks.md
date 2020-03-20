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
ms.openlocfilehash: 6b540448599c1e1083ed367a312ef60fceacd0d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187643"
---
# <a name="animation-tips-and-tricks"></a>動畫秘訣和訣竅
在 WPF 中處理動畫時，有許多提示和技巧可以使動畫更好地執行，並節省您的挫折感。  
  
<a name="generalissuessection"></a>
## <a name="general-issues"></a>一般問題  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>以動畫顯示捲軸或滑桿位置會凍結  
 如果使用具有 的<xref:System.Windows.Media.Animation.FillBehavior><xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>動畫（預設值）為捲軸或滑塊的位置設置動畫，則使用者將無法再移動捲軸或滑塊。 這是因為即使動畫結束，仍然在覆寫目標屬性的基底值。 要阻止動畫重寫屬性的當前值，請將其刪除，或將其<xref:System.Windows.Media.Animation.FillBehavior>為 。 <xref:System.Windows.Media.Animation.FillBehavior.Stop> 有關詳細資訊和示例，請參閱[使用分鏡腳本設置屬性後設置屬性](how-to-set-a-property-after-animating-it-with-a-storyboard.md)。  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>以動畫顯示動畫的輸出沒有任何效果  
 您無法以動畫顯示已是另一個動畫輸出的物件。 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>例如，如果使用 的 動畫從<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Media.RadialGradientBrush> <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.RadialGradientBrush> <xref:System.Windows.Media.SolidColorBrush>  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>無法在以動畫顯示屬性之後變更該屬性的值  
 在某些情況下，即使動畫已結束，您可能無法變更已經以動畫顯示的屬性值。 這是因為即使動畫結束，仍然在覆寫屬性的基底值。 要阻止動畫重寫屬性的當前值，請將其刪除，或將其<xref:System.Windows.Media.Animation.FillBehavior>為 。 <xref:System.Windows.Media.Animation.FillBehavior.Stop> 有關詳細資訊和示例，請參閱[使用分鏡腳本設置屬性後設置屬性](how-to-set-a-property-after-animating-it-with-a-storyboard.md)。  
  
### <a name="changing-a-timeline-has-no-effect"></a>變更時間軸沒有任何作用  
 儘管大多數<xref:System.Windows.Media.Animation.Timeline>屬性都是可動畫的，並且可以綁定資料，但更改活動的屬性<xref:System.Windows.Media.Animation.Timeline>值似乎不起作用。 這是因為，當 開始 時<xref:System.Windows.Media.Animation.Timeline>，計時系統會複製 並<xref:System.Windows.Media.Animation.Timeline>用它來創建<xref:System.Windows.Media.Animation.Clock>物件。 修改原始內容不會影響系統的複本。  
  
 <xref:System.Windows.Media.Animation.Timeline>要反映更改，必須重新生成其時鐘，並用於替換以前創建的時鐘。 時鐘不會自動產生。 以下是幾種可套用時間軸變更的方式︰  
  
- 如果時間表是 或 屬於<xref:System.Windows.Media.Animation.Storyboard>， 則可以通過使用<xref:System.Windows.Media.Animation.BeginStoryboard>或<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法重新應用其分鏡腳本來使其反映更改。 這也會一併重新啟動動畫。 在代碼中，可以使用 方法<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>將分鏡腳本推進回其以前的位置。  
  
- 如果使用 方法將動畫直接應用於屬性<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>，請再次調用 該方法<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>並傳遞已修改的動畫。  
  
- 如果您直接在時鐘層級運作，請建立並套用一組新的時鐘，並使用它們來取代前一組產生的時鐘。  
  
 有關時間表和時鐘的詳細資訊，請參閱[動畫和計時系統概述](animation-and-timing-system-overview.md)。  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop 未如預期運作  
 有時，<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>將屬性設置為<xref:System.Windows.Media.Animation.FillBehavior.Stop>似乎不起作用，例如，當一個動畫由於具有 的<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A><xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>設置而"手離"另一個動畫時，它具有 。  
  
 下面的示例創建 和<xref:System.Windows.Controls.Canvas> <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Media.TranslateTransform>。 <xref:System.Windows.Media.TranslateTransform>將進行動畫移動。 <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Shapes.Rectangle>  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 本節中的示例使用前面的物件來演示<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性未按預期表現的幾個情況。  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" 且有多個動畫的 HandoffBehavior  
 有時，當動畫被第二個動畫替換<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>時，它似乎會忽略其屬性。 以以下示例為例，該示例創建<xref:System.Windows.Media.Animation.Storyboard>兩個物件，並使用它們為上<xref:System.Windows.Media.TranslateTransform>一個示例所示的相同物件設置動畫。  
  
 第一<xref:System.Windows.Media.Animation.Storyboard>個`B1`，為<xref:System.Windows.Media.TranslateTransform.X%2A>從<xref:System.Windows.Media.TranslateTransform>0 到 350 的屬性設置動畫，該屬性將矩形向右移動 350 圖元。 當動畫達到其持續時間的末尾並停止播放時，<xref:System.Windows.Media.TranslateTransform.X%2A>屬性將恢復為其原始值 0。 結果，矩形會向右移動 350 像素，然後再跳回其原始位置。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 第二<xref:System.Windows.Media.Animation.Storyboard>個`B2`，還對相同的<xref:System.Windows.Media.TranslateTransform.X%2A><xref:System.Windows.Media.TranslateTransform>屬性進行動畫處理。 由於僅<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>設置動畫<xref:System.Windows.Media.Animation.Storyboard>的屬性，因此動畫使用其動畫屬性的當前值作為其起始值。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 如果在播放第一個按鈕時按一下第<xref:System.Windows.Media.Animation.Storyboard>二個按鈕，則可能預期會出現以下行為：  
  
1. 第一個分鏡腳本結束，並將矩形發送回其原始位置，因為動畫具有<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>的<xref:System.Windows.Media.Animation.FillBehavior.Stop>。  
  
2. 第二個分鏡腳本會生效，並從目前的位置 (現在是 0) 以動畫顯示到 500。  
  
 **但這不是發生的動作。** 相反地，矩形並未跳回，而是繼續向右移動。 這是因為第二個動畫使用第一個動畫的目前值做為其開始值，並從該值以動畫顯示到 500。 當第二個動畫替換第一個動畫<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace><xref:System.Windows.Media.Animation.HandoffBehavior>時，因為使用了<xref:System.Windows.Media.Animation.FillBehavior>，第一個動畫的則無關緊要。  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior 和已完成的事件  
 接下來的示例演示了另一個場景，<xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>其中似乎沒有效果。 同樣，該示例使用分鏡腳本為<xref:System.Windows.Media.TranslateTransform.X%2A><xref:System.Windows.Media.TranslateTransform>從 0 到 350 的屬性設置動畫。 但是，這一次，該示例註冊該<xref:System.Windows.Media.Animation.Timeline.Completed>事件。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 事件<xref:System.Windows.Media.Animation.Timeline.Completed>處理常式啟動另一<xref:System.Windows.Media.Animation.Storyboard>個將同一屬性從當前值動畫到 500 的動畫。  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 以下是將第二<xref:System.Windows.Media.Animation.Storyboard>個標記定義為資源。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 運行 時<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.TranslateTransform.X%2A>，您可能希望 的屬性<xref:System.Windows.Media.TranslateTransform>從 0 到 350 進行動畫處理，然後在它完成後還原為 0（因為它具有<xref:System.Windows.Media.Animation.FillBehavior><xref:System.Windows.Media.Animation.FillBehavior.Stop>的設置），然後從 0 到 500 進行動畫處理。 相反，<xref:System.Windows.Media.TranslateTransform>動畫從 0 到 350，然後到 500。  
  
 這是因為 WPF 引發事件的順序，以及屬性值被緩存，並且除非屬性無效，否則不會重新計算。 首先<xref:System.Windows.Media.Animation.Timeline.Completed>處理事件，因為它是由根時間表（第一個<xref:System.Windows.Media.Animation.Storyboard>）觸發的。 此時，<xref:System.Windows.Media.TranslateTransform.X%2A>該屬性仍返回其動畫值，因為它尚未失效。 第二<xref:System.Windows.Media.Animation.Storyboard>個使用緩存的值作為其起始值，並開始進行動畫處理。  
  
<a name="performancesection"></a>
## <a name="performance"></a>效能  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>動畫在離開頁面之後繼續執行  
 當您從包含正在運行的動畫的<xref:System.Windows.Controls.Page>導航時，這些動畫將繼續播放，<xref:System.Windows.Controls.Page>直到垃圾回收。 根據使用的導覽系統，您離開的頁面可能會留在記憶體中一段不等的時間，同時會因為動畫而耗用資源。 當頁面含有不斷執行的 (「環境」) 動畫時，這種情形會最明顯。  
  
 因此，最好在<xref:System.Windows.FrameworkElement.Unloaded>遠離頁面時使用事件刪除動畫。  
  
 移除動畫有許多不同的方式。 以下技術可用於刪除屬於 的<xref:System.Windows.Media.Animation.Storyboard>動畫。  
  
- 要刪除<xref:System.Windows.Media.Animation.Storyboard>從事件觸發器開始，請參閱[如何：刪除分鏡腳本](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90))。  
  
- 要使用代碼刪除 ，<xref:System.Windows.Media.Animation.Storyboard>請參閱<xref:System.Windows.Media.Animation.Storyboard.Remove%2A>方法。  
  
 不論啟動動畫的方式為何，都可以使用下一個技術。  
  
- 要從特定屬性中刪除動畫，請使用 方法<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>。 將正在動畫處理的屬性指定為第一個參數`null`，並將第二個參數指定為第二個參數。 這將會從屬性移除所有動畫時鐘。  
  
 有關設置屬性動畫的不同方法的詳細資訊，請參閱[屬性動畫技術概述](property-animation-techniques-overview.md)。  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>使用 Compose HandoffBehavior 會耗用系統資源  
 <xref:System.Windows.Media.Animation.Storyboard>當您使用<xref:System.Windows.Media.Animation.AnimationTimeline><xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.AnimationClock>對 屬性應用 ，時，以前與該<xref:System.Windows.Media.Animation.Clock>屬性關聯的任何物件將繼續使用系統資源;因此，使用<xref:System.Windows.Media.Animation.HandoffBehavior>計時系統不會自動刪除這些時鐘。  
  
 為了避免使用<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>應用大量時鐘時的性能問題，應在動畫屬性完成後從動畫屬性中刪除組合時鐘。 有幾個方式可移除時鐘。  
  
- 要從屬性中刪除所有時鐘，請使用動畫物件的<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29>或<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>方法。 將正在動畫處理的屬性指定為第一個參數`null`，並將第二個參數指定為第二個參數。 這將會從屬性移除所有動畫時鐘。  
  
- 若要從時鐘清單中<xref:System.Windows.Media.Animation.AnimationClock>刪除特定<xref:System.Windows.Media.Animation.Clock.Controller%2A>項，請使用 的屬性<xref:System.Windows.Media.Animation.AnimationClock>來檢索<xref:System.Windows.Media.Animation.ClockController>， 然後調用<xref:System.Windows.Media.Animation.ClockController.Remove%2A>的方法<xref:System.Windows.Media.Animation.ClockController>。 這通常在時鐘<xref:System.Windows.Media.Animation.Clock.Completed>的事件處理常式中完成。 請注意，只有根時鐘可以由<xref:System.Windows.Media.Animation.ClockController>。子<xref:System.Windows.Media.Animation.Clock.Controller%2A>時鐘的屬性將返回`null`。 另請注意，如果<xref:System.Windows.Media.Animation.Clock.Completed>時鐘的有效持續時間是永遠的，將不會調用該事件。  在這種情況下，使用者將需要確定何時調用<xref:System.Windows.Media.Animation.ClockController.Remove%2A>。  
  
 這主要是在存留期較長的物件才會發生的動畫問題。  記憶體回收物件時，也會中斷連接並記憶體回收其時鐘。  
  
 有關時鐘物件的詳細資訊，請參閱[動畫和計時系統概述](animation-and-timing-system-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
