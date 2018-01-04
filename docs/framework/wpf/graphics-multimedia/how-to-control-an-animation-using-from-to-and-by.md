---
title: "操作說明：使用 From、To 和 By 控制動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17f87c8bcf09022aa389df779e29f5e5affabc20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>操作說明：使用 From、To 和 By 控制動畫
「 從/至/者 」 或 「 基本動畫 」 會建立兩個目標值之間的轉換 (請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)的不同類型的動畫簡介)。 若要設定的基本動畫目標值，使用其<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>， <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。  下表摘要說明如何<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>， <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>可能使用屬性一起或分開來判斷動畫的目標值。  
  
|指定的屬性|產生的行為|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|動畫會從所指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性正在顯示動畫之屬性的基底值或前一個動畫的輸出值，根據前一個動畫的設定方式。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|動畫會從所指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性所指定的值為<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|動畫會從所指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性指定的總和值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|進展動畫的屬性的基底值的動畫，或前一個動畫的輸出所指定的值的值<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|動畫會從正在顯示動畫之屬性的基底值或前一個動畫的輸出值，該值與所指定的值的總和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。|  
  
> [!NOTE]
>  無法同時設定<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>上相同的動畫的屬性。  
  
 若要使用其他插補方法，或建立兩個以上的目標值之間的動畫，請使用主要畫面格動畫。 請參閱[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)如需詳細資訊。  
  
 將多個動畫套用至單一屬性的相關資訊，請參閱[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
 下列範例示範的設定不同的效果<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>， <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>動畫的屬性。  
  
## <a name="example"></a>範例  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [From、To 和 By 動畫目標值範例](http://go.microsoft.com/fwlink/?LinkID=159988)
