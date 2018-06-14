---
title: 如何：指定時刻表是否會自動反轉
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 498aefa16b8a76262c01965b8992ef9a94b7ce28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560061"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>如何：指定時刻表是否會自動反轉
時間軸的<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性會決定是否它在後反向播放完成向前反覆項目。 下列範例顯示相同的持續時間和目標值，但具有不同的數個動畫<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>設定。 若要示範如何<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性具有不同的行為<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>設定，某些動畫會設定為重複。 最後一個動畫顯示如何<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性巢狀的時間軸上的運作方式。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
