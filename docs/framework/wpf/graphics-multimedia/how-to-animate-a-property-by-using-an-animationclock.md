---
title: "操作說明：使用 AnimationClock 建立屬性的動畫"
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
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47df7aaad45000bc8c761a9bb9022d37e0f0828c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>操作說明：使用 AnimationClock 建立屬性的動畫
這個範例示範如何使用<xref:System.Windows.Media.Animation.Clock>以動畫方式顯示屬性的物件。  
  
 有三種方式可以動畫顯示相依性屬性︰  
  
-   建立<xref:System.Windows.Media.Animation.AnimationTimeline>和其關聯屬性使用<xref:System.Windows.Media.Animation.Storyboard>。  
  
-   使用物件的<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，以套用單一<xref:System.Windows.Media.Animation.AnimationTimeline>至目標屬性。  
  
-   建立<xref:System.Windows.Media.Animation.AnimationClock>從<xref:System.Windows.Media.Animation.AnimationTimeline>並將它套用至屬性。  
  
 <xref:System.Windows.Media.Animation.Storyboard>物件和<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法可讓您建立屬性動畫沒有直接建立與散發時鐘 (如需範例，請參閱[使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)和[屬性而不建立動畫使用分鏡腳本](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md));建立和自動為您散發的時鐘。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立<xref:System.Windows.Media.Animation.AnimationClock>並將它套用到兩個類似的屬性。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 如需範例示範如何以互動方式控制<xref:System.Windows.Media.Animation.Clock>啟動之後，請參閱[以互動方式控制時鐘](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
