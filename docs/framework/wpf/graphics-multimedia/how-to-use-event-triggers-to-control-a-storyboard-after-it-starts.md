---
title: 如何：在腳本開始後使用事件觸發程式進行控制
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186707"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>如何：在腳本開始後使用事件觸發程式進行控制

此示例演示如何在 啟動後控制<xref:System.Windows.Media.Animation.Storyboard>。 要使用<xref:System.Windows.Media.Animation.Storyboard>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]開始 ，<xref:System.Windows.Media.Animation.BeginStoryboard>使用 ， 將動畫分發到它們為物件和屬性設置動畫，然後啟動分鏡腳本。 如果通過指定<xref:System.Windows.Media.Animation.BeginStoryboard>名稱<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>的屬性來命名，則可以將其製作為可控制的分鏡腳本。 然後，您可以在分鏡腳本啟動後以對話模式控制它。

將以下分鏡腳本操作與<xref:System.Windows.EventTrigger>物件一起使用來控制分鏡腳本。

- <xref:System.Windows.Media.Animation.PauseStoryboard>：暫停分鏡腳本。

- <xref:System.Windows.Media.Animation.ResumeStoryboard>：恢復暫停的分鏡腳本。

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>：更改分鏡腳本速度。

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>：將分鏡腳本提前到填充期結束時（如果有）。

- <xref:System.Windows.Media.Animation.StopStoryboard>：停止分鏡腳本。

- <xref:System.Windows.Media.Animation.RemoveStoryboard>：刪除分鏡腳本，釋放資源。

## <a name="example"></a>範例

下面的示例使用可控的分鏡腳本操作來交互控制分鏡腳本。

> [!NOTE]
> 要查看使用代碼控制分鏡腳本的示例，請參閱[在分鏡腳本開始使用其交互方法後對其進行控制](how-to-control-a-storyboard-after-it-starts.md)。

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

有關其他示例，請參閱[動畫示例庫](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)。

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
