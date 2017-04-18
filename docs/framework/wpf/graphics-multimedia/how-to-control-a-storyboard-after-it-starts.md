---
title: "如何：在腳本開始後進行控制 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分鏡腳本, 在啟動後控制"
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：在腳本開始後進行控制
本範例示範如何使用程式碼在 <xref:System.Windows.Media.Animation.Storyboard> 啟動後加以控制。  若要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中控制腳本，請使用 <xref:System.Windows.Trigger> 和 <xref:System.Windows.TriggerAction> 物件；如需範例，請參閱 [在腳本開始後使用事件觸發程式進行控制](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。  
  
 若要啟動腳本，請使用它的 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法，此方法會將腳本的動畫散發至顯示為動畫的屬性，並接著啟動腳本。  
  
 若要將腳本設成可控制，請使用 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法並將第二個參數指定為 **true**。  您接著就可以使用腳本的互動式方法暫停、繼續、搜尋、停止、加快或放慢腳本的速度，或前進至填滿期間。  以下是腳本互動式方法的清單：  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>：暫停腳本。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>：繼續暫停的腳本。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>：設定腳本的互動速度。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>：搜尋腳本中的指定位置。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>：搜尋腳本至指定的位置。  與 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> 方法不同的是，此作業會在下一個時間之前進行處理。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>：腳本前進至填滿期間 \(如果有的話\)。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>：停止腳本。  
  
 在下列範例中，會使用多個腳本方法以互動方式控制腳本。  
  
 **注意：**如需使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的觸發程序控制腳本的範例，請參閱 [在腳本開始後使用事件觸發程式進行控制](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。  
  
## 範例  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## 請參閱  
 [在腳本開始後使用事件觸發程式進行控制](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)