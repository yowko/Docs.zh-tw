---
title: "如何：變更時鐘的速度而不變更其時刻表的速度 | Microsoft Docs"
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
  - "時鐘, 變更速度"
  - "時鐘的速度, 變更"
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：變更時鐘的速度而不變更其時刻表的速度
<xref:System.Windows.Media.Animation.ClockController> 物件的 <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> 屬性可以讓您變更 <xref:System.Windows.Media.Animation.Clock> 的速度，而不需要更改時鐘之 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>。  下列範例使用 <xref:System.Windows.Media.Animation.ClockController> 以互動方式修改時鐘的 <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>。  <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> 事件和時鐘的 <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> 屬性則是用來在每次變更時鐘的 <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> 時，顯示其目前的整體速度。  
  
## 範例  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]