---
title: HOW TO：使用子時間表簡化動畫
ms.date: 03/30/2017
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
ms.openlocfilehash: 21a297208be045eea79d6f5ca6c8eac016d26345
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096390"
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>HOW TO：使用子時間表簡化動畫
此範例示範如何使用子簡化動畫<xref:System.Windows.Media.Animation.ParallelTimeline>物件。 A<xref:System.Windows.Media.Animation.Storyboard>是一種<xref:System.Windows.Media.Animation.Timeline>，提供它所包含的時間軸目標資訊。 使用<xref:System.Windows.Media.Animation.Storyboard>提供時間軸目標資訊，包括物件和屬性的資訊。  
  
 若要開始動畫，使用一或多個<xref:System.Windows.Media.Animation.ParallelTimeline>物件做為巢的狀子元素<xref:System.Windows.Media.Animation.Storyboard>。 這些<xref:System.Windows.Media.Animation.ParallelTimeline>物件可以包含其他動畫，並因此，更可以封裝在複雜動畫的時間序列。 比方說，如果您以動畫顯示<xref:System.Windows.Controls.TextBlock>和在相同的數個圖案<xref:System.Windows.Media.Animation.Storyboard>，您可以區隔的動畫<xref:System.Windows.Controls.TextBlock>和圖形，它們放入個別<xref:System.Windows.Media.Animation.ParallelTimeline>。 因為每個<xref:System.Windows.Media.Animation.ParallelTimeline>都有它自己<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>和所有子項目<xref:System.Windows.Media.Animation.ParallelTimeline>開始相對於這個<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>，計時更適當地在封裝中。  
  
 下列範例以動畫顯示的兩段文字 (<xref:System.Windows.Controls.TextBlock>物件) 從位於相同<xref:System.Windows.Media.Animation.Storyboard>。 A<xref:System.Windows.Media.Animation.ParallelTimeline>封裝的其中一個動畫<xref:System.Windows.Controls.TextBlock>物件。  
  
 **效能提示：** 雖然您可以巢狀<xref:System.Windows.Media.Animation.Storyboard>時間軸內彼此<xref:System.Windows.Media.Animation.ParallelTimeline>s 會更適合進行巢狀，因為它們需要較少額外負荷。 (<xref:System.Windows.Media.Animation.Storyboard>類別繼承自<xref:System.Windows.Media.Animation.ParallelTimeline>類別。)  
  
## <a name="example"></a>範例  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [指定分鏡腳本動畫之間的 HandoffBehavior](how-to-specify-handoffbehavior-between-storyboard-animations.md)
