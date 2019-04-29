---
title: HOW TO：設定動畫的持續時間
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: bdae1689ffeb8c54d756b9debbd26d57a052892d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651151"
---
# <a name="how-to-set-a-duration-for-an-animation"></a>HOW TO：設定動畫的持續時間
A<xref:System.Windows.Media.Animation.Timeline>代表一段時間和該區段的長度由時間軸的<xref:System.Windows.Duration>。 當<xref:System.Windows.Media.Animation.Timeline>結束其持續時間，它就會停止播放。 如果<xref:System.Windows.Media.Animation.Timeline>有子時間軸，它們也會停止播放。 如果動畫，<xref:System.Windows.Duration>指定花多少時間動畫轉換從其起始值到結束值。  
  
 您可以指定<xref:System.Windows.Duration>與特定、 有限的時間或特殊值<xref:System.Windows.Duration.Automatic%2A>或<xref:System.Windows.Duration.Forever%2A>。 動畫的持續時間必須一律是時間值，因為動畫必須永遠有已定義的有限的長度，否則動畫就不會知道如何在其目標值之間轉換。 容器時間軸 (<xref:System.Windows.Media.Animation.TimelineGroup>物件)，例如<xref:System.Windows.Media.Animation.Storyboard>並<xref:System.Windows.Media.Animation.ParallelTimeline>的預設持續時間<xref:System.Windows.Duration.Automatic%2A>，這表示它們會自動結束時其最後一個子項目停止播放。  
  
 在下列的範例、 寬度、 高度和填滿色彩的<xref:System.Windows.Shapes.Rectangle>以動畫顯示。 持續時間會設定導致包括控制動畫的認知的速度，並覆寫子時間軸與容器時間軸的持續時間的持續時間的動畫效果的動畫和容器時間軸上。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Duration>
- [動畫概觀](animation-overview.md)
