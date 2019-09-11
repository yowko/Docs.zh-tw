---
title: HOW TO：在分鏡腳本開始後使用事件觸發程序進行控制
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855856"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>作法：在分鏡腳本開始後使用事件觸發程序進行控制

這個範例示範如何在啟動<xref:System.Windows.Media.Animation.Storyboard>之後控制。 若要使用<xref:System.Windows.Media.Animation.Storyboard> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]來啟動，請<xref:System.Windows.Media.Animation.BeginStoryboard>使用，它會將動畫散佈至物件和屬性的動畫，然後啟動分鏡腳本。 如果您藉<xref:System.Windows.Media.Animation.BeginStoryboard>由指定其<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>屬性來提供名稱，則會將它設為可控制的分鏡腳本。 接著，您可以在腳本開始之後，以互動方式進行控制。

將下列分鏡腳本動作與<xref:System.Windows.EventTrigger>物件一起使用，以控制分鏡腳本。

- <xref:System.Windows.Media.Animation.PauseStoryboard>：暫停分鏡腳本。

- <xref:System.Windows.Media.Animation.ResumeStoryboard>：繼續已暫停的分鏡腳本。

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>：變更分鏡腳本的速度。

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>：將分鏡腳本前進到其填滿期間的結尾（如果有的話）。

- <xref:System.Windows.Media.Animation.StopStoryboard>：停止分鏡腳本。

- <xref:System.Windows.Media.Animation.RemoveStoryboard>：移除分鏡腳本，釋放資源。

## <a name="example"></a>範例

下列範例會使用可控制的分鏡腳本動作，以互動方式控制分鏡腳本。

> [!NOTE]
> 若要查看使用程式碼控制分鏡腳本的範例，請參閱[在腳本開始之後使用其互動方法來控制分](how-to-control-a-storyboard-after-it-starts.md)鏡腳本。

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

如需其他範例，請參閱[動畫範例庫](https://go.microsoft.com/fwlink/?LinkID=159969)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [在分鏡腳本開始後，使用其互動方法來進行控制](how-to-control-a-storyboard-after-it-starts.md)
- [動畫概觀](animation-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
