---
title: "如何：在重複循環期間累加動畫值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96a91856cdfcf1ca7ae87e8e571306170feecb7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a>如何：在重複循環期間累加動畫值
這個範例示範如何使用<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>屬性重複循環累加動畫值。  
  
## <a name="example"></a>範例  
 使用<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>累積重複循環基底值的動畫的屬性。 比方說，如果您設定重複 9 次動畫 (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ="9 x")，並設定要繪製介於 10 到 15 之間的屬性 (從 = 10 到 = 15)，屬性以動畫方式顯示從 10 到 15 在第一個週期中，從 15 到 20 的第二個週期從 20 到 25 期間第三個週期，依此類推。 因此，每次的動畫循環使用先前的動畫循環結束動畫值做為其基底值。  
  
 您可以使用`IsCumulative`具有最基本的動畫和大部分的主要畫面格動畫屬性。 如需詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)和[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
 下列範例會顯示動畫四個矩形的寬度，以這種行為。 範例：  
  
-   以動畫方式顯示與第一個矩形<xref:System.Windows.Media.Animation.DoubleAnimation>並設定<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>屬性`true`。  
  
-   以動畫方式顯示與第二個矩形<xref:System.Windows.Media.Animation.DoubleAnimation>並設定<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>屬性的預設值為`false`。  
  
-   以動畫顯示具有的第三個矩形<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>並設定<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A>屬性`true`。  
  
-   以動畫顯示具有的最後一個矩形<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>並設定<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A>屬性`false`。  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a>請參閱  
 [將動畫輸出值加入至動畫啟動值](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [重複動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
