---
title: HOW TO：時鐘的狀態變更時接收通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
ms.openlocfilehash: dc3fffb88ce59ceb908d6febd2f078820513b641
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363133"
---
# <a name="how-to-receive-notification-when-a-clocks-state-changes"></a>HOW TO：時鐘的狀態變更時接收通知
時鐘<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>就會發生事件時其<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>就會變成無效，例如當時鐘啟動或停止。 您可以直接使用這個事件註冊<xref:System.Windows.Media.Animation.Clock>，或您可以註冊使用<xref:System.Windows.Media.Animation.Timeline>。  
  
 在下列範例中，<xref:System.Windows.Media.Animation.Storyboard>並將兩個<xref:System.Windows.Media.Animation.DoubleAnimation>物件用來以動畫顯示兩個矩形的寬度。 <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>事件用來接聽的時鐘狀態變更。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 下圖顯示動畫的不同狀態輸入為父時間軸 (*分鏡腳本*) 進行。  
  
 ![具有兩個動畫的分鏡腳本的時鐘狀態](./media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 下表顯示時間處*Animation1*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>引發事件：  
  
||||||||  
|-|-|-|-|-|-|-|  
|時間 （秒）|1|10|19|21|30|39|  
|狀況|作用中|作用中|已停止|作用中|作用中|已停止|  
  
 下表顯示時間處*Animation2*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>引發事件：  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|時間 （秒）|1|9|11|19|21|29|31|39|  
|狀況|作用中|填滿|作用中|已停止|作用中|填滿|作用中|已停止|  
  
 請注意， *Animation1*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>就會引發事件在 10 秒，即使其狀態會維持<xref:System.Windows.Media.Animation.ClockState.Active>。 這是因為其狀態變更在 10 秒，但從變更<xref:System.Windows.Media.Animation.ClockState.Active>要<xref:System.Windows.Media.Animation.ClockState.Filling>，然後再回到<xref:System.Windows.Media.Animation.ClockState.Active>中相同的刻度。
