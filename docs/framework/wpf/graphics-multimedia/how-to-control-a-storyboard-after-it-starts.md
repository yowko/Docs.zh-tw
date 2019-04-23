---
title: HOW TO：分鏡腳本開始後進行控制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 107391386dfbb718f9436d9a039b08439fbc3279
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161482"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>HOW TO：分鏡腳本開始後進行控制
此範例示範如何使用程式碼，以控制<xref:System.Windows.Media.Animation.Storyboard>啟動之後。 若要控制在分鏡腳本[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，使用<xref:System.Windows.Trigger>並<xref:System.Windows.TriggerAction>物件; 如需範例，請參閱[使用事件觸發程序來控制分鏡腳本開始後](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。  
  
 若要啟動分鏡腳本，您使用其<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法，將它們建立動畫，並啟動分鏡腳本的屬性的分鏡腳本的動畫。  
  
 要控制分鏡腳本，請使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法並指定 **，則為 true**做為第二個參數。 您接著可以使用分鏡腳本的互動方法來暫停、 繼續、 搜尋、 停止、 加速，或分鏡腳本，變慢或前進到其填滿期間。 以下是一份分鏡腳本的互動方法：  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>：暫停分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>：繼續已暫停的分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>：設定分鏡腳本的互動速度。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>：搜尋分鏡腳本的指定位置。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>：搜尋分鏡腳本，以指定的位置。 不同於<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>方法，這項作業會處理下一個刻度之前。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>：如果有的話，請前進到其填滿期間，將分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>：停止分鏡腳本。  
  
 在下列範例中，數個分鏡腳本的方法來以互動方式控制分鏡腳本。  
  
 **注意：** 若要控制使用觸發程序及分鏡腳本的範例，請參閱[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，請參閱 <<c2> [ 來控制分鏡腳本開始後使用事件觸發程序](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a>另請參閱

- [在分鏡腳本開始後使用事件觸發程式進行控制](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
