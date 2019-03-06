---
title: HOW TO：變更時鐘的速度而不變更其時刻表的速度
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
ms.openlocfilehash: 19e6874b9b472cb4a5f716677f99af03f2b73b10
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358271"
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a>HOW TO：變更時鐘的速度而不變更其時刻表的速度
A<xref:System.Windows.Media.Animation.ClockController>物件的<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>屬性可讓您變更的速度<xref:System.Windows.Media.Animation.Clock>而不需要改變<xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>時鐘的<xref:System.Windows.Media.Animation.Timeline>。 在下列範例中，<xref:System.Windows.Media.Animation.ClockController>用來以互動方式修改<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>的時鐘。 <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated>事件和時鐘<xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A>屬性用來顯示時鐘的目前的整體速度每次在其互動式<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>變更。  
  
## <a name="example"></a>範例  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
