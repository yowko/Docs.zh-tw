---
title: "如何：在腳本開始後使用事件觸發程式進行控制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9e096969713cc4b9c42261b238691d51cb49d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>如何：在腳本開始後使用事件觸發程式進行控制
這個範例示範如何控制<xref:System.Windows.Media.Animation.Storyboard>之後啟動。 若要啟動<xref:System.Windows.Media.Animation.Storyboard>使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，使用<xref:System.Windows.Media.Animation.BeginStoryboard>，這會發佈這些物件和屬性，其以動畫顯示，然後啟動 分鏡腳本動畫。 如果您提供<xref:System.Windows.Media.Animation.BeginStoryboard>藉由指定的名稱及其<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>屬性，使其可控制的分鏡腳本。 您可以再以互動方式控制分鏡腳本之後啟動。  
  
 使用下列分鏡腳本動作搭配<xref:System.Windows.EventTrigger>物件來控制分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>： 暫停分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>： 繼續暫停的分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>： 變更分鏡腳本速度。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>： 如果有的話，往前移到其填滿期結束分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>： 停止分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>： 移除分鏡腳本，釋放資源。  
  
## <a name="example"></a>範例  
 下列範例會使用可控制的分鏡腳本的動作，以互動方式控制 分鏡腳本。  
  
 **注意：**若要查看使用程式碼控制分鏡腳本的範例，請參閱[控制分鏡腳本之後它啟動使用其互動方法](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)。  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 如需其他範例，請參閱[動畫範例圖庫](http://go.microsoft.com/fwlink/?LinkID=159969)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [在分鏡腳本開始後，使用其互動方法來進行控制](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
