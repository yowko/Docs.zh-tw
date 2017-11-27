---
title: "如何： 接收通知時時鐘 &#39; s 的狀態變更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f59fddb1add29d52ccba6fc8b8ce84938b53a1c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a>如何： 接收通知時時鐘 &#39; s 的狀態變更
時鐘的<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>就會發生事件時其<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>就變成無效，例如當時鐘啟動或停止。 您可以直接使用這個事件註冊<xref:System.Windows.Media.Animation.Clock>，也可以註冊使用<xref:System.Windows.Media.Animation.Timeline>。  
  
 在下列範例中，<xref:System.Windows.Media.Animation.Storyboard>和兩個<xref:System.Windows.Media.Animation.DoubleAnimation>物件用來繪製兩個矩形的寬度。 <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> 」 事件可用來接聽的時鐘狀態變更。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 下圖顯示不同的狀態動畫輸入做為父時間軸 (*分鏡腳本*) 進行。  
  
 ![具有兩個動畫分鏡腳本的時鐘狀態](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 下表顯示時間的*Animation1*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>事件引發：  
  
||||||||  
|-|-|-|-|-|-|-|  
|時間 （秒）|1|10|19|21|30|39|  
|狀態|作用中|作用中|已停止|作用中|作用中|已停止|  
  
 下表顯示時間的*Animation2*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>事件引發：  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|時間 （秒）|1|9|11|19|21|29|31|39|  
|狀態|作用中|填滿|作用中|已停止|作用中|填滿|作用中|已停止|  
  
 請注意， *Animation1*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>就會引發事件在 10 秒，即使其狀態會維持<xref:System.Windows.Media.Animation.ClockState.Active>。 這是因為其狀態變更在 10 秒，但其變更從<xref:System.Windows.Media.Animation.ClockState.Active>至<xref:System.Windows.Media.Animation.ClockState.Filling>然後再設回<xref:System.Windows.Media.Animation.ClockState.Active>中相同的刻度。
