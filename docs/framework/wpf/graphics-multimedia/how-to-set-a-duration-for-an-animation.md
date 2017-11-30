---
title: "如何：設定動畫的持續時間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9560e9d0a2809ae8f55a060eaec3b271539d5f94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-a-duration-for-an-animation"></a>如何：設定動畫的持續時間
A<xref:System.Windows.Media.Animation.Timeline>代表一段時間和區段長度由時間軸的<xref:System.Windows.Duration>。 當<xref:System.Windows.Media.Animation.Timeline>結束其持續時間，它就會停止播放。 如果<xref:System.Windows.Media.Animation.Timeline>具有子時刻表它們停止以及播放。 在動畫，<xref:System.Windows.Duration>指定動畫時間轉換從其起始值至它的結束值。  
  
 您可以指定<xref:System.Windows.Duration>與特定、 有限的時間或特殊值<xref:System.Windows.Duration.Automatic%2A>或<xref:System.Windows.Duration.Forever%2A>。 動畫的持續時間必須一律是時間值，因為動畫必須永遠有定義的有限的長度，否則動畫會不知道如何將其目標值之間轉換。 容器時間表 (<xref:System.Windows.Media.Animation.TimelineGroup>物件)，例如<xref:System.Windows.Media.Animation.Storyboard>和<xref:System.Windows.Media.Animation.ParallelTimeline>，有預設的持續時間<xref:System.Windows.Duration.Automatic%2A>，這表示它們會自動結束時其最後一個子系停止播放。  
  
 在下列範例、 寬度、 高度和填滿色彩的<xref:System.Windows.Shapes.Rectangle>的動畫。 持續時間會導致包括控制認知的動畫的速度，以及覆寫子時刻表的持續時間的持續時間的容器時間表的動畫效果的動畫和容器時間軸上設定。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Duration>  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
