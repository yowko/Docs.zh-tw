---
title: 作法：在分鏡腳本開始後加以控制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855859"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>作法：在分鏡腳本開始後加以控制

這個範例示範如何使用程式碼來控制啟動<xref:System.Windows.Media.Animation.Storyboard>後的。 若要[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]在中控制分鏡腳本，請使用<xref:System.Windows.Trigger>和<xref:System.Windows.TriggerAction>物件; 如需範例，請參閱[使用事件觸發程式在啟動後控制分](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)鏡腳本。

若要啟動分鏡腳本，您<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>可以使用其方法，將分鏡腳本的動畫散發至其動畫和啟動分鏡腳本的屬性。

若要將分鏡腳本設為可<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>控制，您可以使用方法，並將**true**指定為第二個參數。 接著，您可以使用分鏡腳本的互動方法來暫停、繼續、搜尋、停止、加速或減緩分鏡腳本，或將它移至其填滿期間。 以下是分鏡腳本的互動式方法清單：

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>：暫停分鏡腳本。

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>：繼續已暫停的分鏡腳本。

- <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>：設定分鏡腳本的互動速度。

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>：搜尋腳本指定的位置。

- <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>：搜尋分鏡腳本至指定的位置。 與方法<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>不同的是，這種作業會在下一個滴答之前處理。

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>：將分鏡腳本前進到其填滿期間（如果有的話）。

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>：停止分鏡腳本。

在下列範例中，會使用數個分鏡腳本方法來以互動方式控制分鏡腳本。

> [!NOTE]
> 若要查看使用觸發[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]程式來控制分鏡腳本的範例，請參閱在腳本[啟動後使用事件觸發程式來控制分](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)鏡腳本。

## <a name="example"></a>範例

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a>另請參閱

- [在分鏡腳本開始後使用事件觸發程式進行控制](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
