---
title: "如何：在腳本開始後使用事件觸發程式進行控制 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "事件觸發程序, 控制腳本"
  - "分鏡腳本, 在啟動後控制"
  - "觸發程序, 控制腳本"
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：在腳本開始後使用事件觸發程式進行控制
本範例說明如何在 <xref:System.Windows.Media.Animation.Storyboard> 啟動後加以控制。  若要使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來啟動 <xref:System.Windows.Media.Animation.Storyboard>，請使用 <xref:System.Windows.Media.Animation.BeginStoryboard>，它會將動畫散發至顯示為動畫的物件和屬性，並接著啟動腳本。  如果您藉由指定 <xref:System.Windows.Media.Animation.BeginStoryboard> 的 <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> 屬性來指派名稱，它就會成為可控制的腳本。  在腳本啟動後，您就可以用互動方式控制腳本。  
  
 您可以將下列腳本動作與 <xref:System.Windows.EventTrigger> 物件搭配使用，以控制腳本。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>：暫停腳本。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>：繼續暫停的腳本。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>：變更腳本速度。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>：讓腳本前進至填滿期間結尾 \(如果有的話\)。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>：停止腳本。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>：移除腳本，因而釋放資源。  
  
## 範例  
 下列範例使用可控制的腳本動作以互動方式控制腳本。  
  
 **注意：**如需藉由使用程式碼控制腳本的範例，請參閱 [在腳本開始後，使用腳本的互動方法來控制腳本](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)。  
  
 [!code-xml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 如需其他範例，請參閱[動畫範例圖庫](http://go.microsoft.com/fwlink/?LinkID=159969) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>   
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>   
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>   
 <xref:System.Windows.Media.Animation.PauseStoryboard>   
 <xref:System.Windows.Media.Animation.StopStoryboard>   
 <xref:System.Windows.Media.Animation.SeekStoryboard>   
 [在腳本開始後，使用腳本的互動方法來控制腳本](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)