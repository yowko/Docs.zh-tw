---
title: "如何：在腳本開始後進行控制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 051ac6fea73b207fb5ef4d6293c5e996552f1281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>如何：在腳本開始後進行控制
這個範例示範如何使用程式碼控制<xref:System.Windows.Media.Animation.Storyboard>啟動它之後。 若要控制中的腳本[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，使用<xref:System.Windows.Trigger>和<xref:System.Windows.TriggerAction>物件; 如需範例，請參閱[使用事件觸發程序來控制分鏡腳本之後啟動](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。  
  
 若要啟動分鏡腳本，您使用其<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法，將發佈分鏡腳本動畫的屬性，它們以動畫顯示，並啟動分鏡腳本。  
  
 要從此分鏡腳本，請使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法並指定**true**做為第二個參數。 您接著可以使用分鏡腳本的互動式方法來暫停、 繼續、 搜尋、 停止、 加速，或分鏡腳本，變慢或前進到其填滿期間。 一份分鏡腳本的互動的方法如下：  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>： 暫停分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>： 繼續暫停的分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>： 設定分鏡腳本的互動速度。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>： 搜尋分鏡腳本的指定位置。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>： 搜尋至指定的位置分鏡腳本。 不同於<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>方法，這項作業會處理之前的下一個刻度。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>： 如果有的話，往前移到其填滿期間，分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>： 停止分鏡腳本。  
  
 在下列範例中，數個分鏡腳本方法可用來以互動方式控制 分鏡腳本。  
  
 **注意：**控制使用觸發程序與分鏡腳本的範例，請參閱[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，請參閱[使用事件觸發程序來控制分鏡腳本之後啟動](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a>請參閱  
 [在分鏡腳本開始後使用事件觸發程式進行控制](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
