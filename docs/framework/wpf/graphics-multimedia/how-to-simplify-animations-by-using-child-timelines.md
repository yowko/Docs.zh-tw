---
title: 操作說明：使用子時間軸簡化動畫
ms.date: 03/30/2017
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
ms.openlocfilehash: 57ea558b167f647ec7597ba95382abb0e48f699f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>操作說明：使用子時間軸簡化動畫
這個範例示範如何使用子簡化動畫<xref:System.Windows.Media.Animation.ParallelTimeline>物件。 A<xref:System.Windows.Media.Animation.Storyboard>是一種<xref:System.Windows.Media.Animation.Timeline>提供它所包含的時間軸的目標資訊。 使用<xref:System.Windows.Media.Animation.Storyboard>提供目標的資訊，包括物件和屬性資訊的時間軸。  
  
 若要開始動畫，請使用一或多個<xref:System.Windows.Media.Animation.ParallelTimeline>物件做為巢狀的子項目的<xref:System.Windows.Media.Animation.Storyboard>。 這些<xref:System.Windows.Media.Animation.ParallelTimeline>物件可以包含其他動畫和因此，更可封裝複雜的動畫時間序列。 比方說，如果您建立動畫<xref:System.Windows.Controls.TextBlock>和數個圖形的相同<xref:System.Windows.Media.Animation.Storyboard>，您可以區隔的動畫<xref:System.Windows.Controls.TextBlock>與圖形，放到不同的每個<xref:System.Windows.Media.Animation.ParallelTimeline>。 因為每個<xref:System.Windows.Media.Animation.ParallelTimeline>都有它自己<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>和所有子項目<xref:System.Windows.Media.Animation.ParallelTimeline>開始相對於此<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>，時間會更好封裝。  
  
 下列範例以動畫方式顯示兩個文字片段 (<xref:System.Windows.Controls.TextBlock>物件) 從在相同<xref:System.Windows.Media.Animation.Storyboard>。 A<xref:System.Windows.Media.Animation.ParallelTimeline>封裝的其中一個動畫<xref:System.Windows.Controls.TextBlock>物件。  
  
 **效能提示：**雖然您可以巢狀<xref:System.Windows.Media.Animation.Storyboard>時間表內彼此<xref:System.Windows.Media.Animation.ParallelTimeline>是比較適合巢狀結構，因為它們需要較少負荷。 (<xref:System.Windows.Media.Animation.Storyboard>類別繼承自<xref:System.Windows.Media.Animation.ParallelTimeline>類別。)  
  
## <a name="example"></a>範例  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [指定分鏡腳本動畫之間的 HandoffBehavior](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
