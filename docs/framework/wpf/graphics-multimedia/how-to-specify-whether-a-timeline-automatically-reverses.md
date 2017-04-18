---
title: "如何：指定時刻表是否會自動反轉 | Microsoft Docs"
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
  - "時刻表的 AutoReverse 屬性"
  - "時刻表, AutoReverse 屬性"
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：指定時刻表是否會自動反轉
時間表的 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性會決定它在完成向前反覆項目後是否以反向順序播放。  下列範例會顯示幾個持續時間和目標值完全相同、但 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 設定不同的動畫。  為示範 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性在 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 設定不同之下的行為，部分動畫會設定重複播放。  最後一個動畫顯示 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性在巢狀時間表上如何運作。  
  
## 範例  
 [!code-xml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]