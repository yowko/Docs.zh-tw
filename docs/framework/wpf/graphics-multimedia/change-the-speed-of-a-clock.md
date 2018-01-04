---
title: "如何：變更時鐘的速度而不變更其時刻表的速度"
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
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5421ed8b45c21e229d6c2682703cd9c7ee486e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a>如何：變更時鐘的速度而不變更其時刻表的速度
A<xref:System.Windows.Media.Animation.ClockController>物件的<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>屬性可讓您變更的速度<xref:System.Windows.Media.Animation.Clock>而不用更改<xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>的時鐘的<xref:System.Windows.Media.Animation.Timeline>。 在下列範例中，<xref:System.Windows.Media.Animation.ClockController>用來以互動方式修改<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>的時鐘。 <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated>事件與時鐘的<xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A>屬性用來顯示時鐘的目前全域速度每次它互動式<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>變更。  
  
## <a name="example"></a>範例  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
