---
title: "如何：將動畫輸出值加入至動畫啟動值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a670a29e4bd982418ac92ef0e2ac65635763671
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>如何：將動畫輸出值加入至動畫啟動值
這個範例示範如何加入動畫的起始值的動畫輸出值。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>屬性會指定是否要將動畫加入動畫屬性的起始值 （基底值） 的輸出值。 您可以使用<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>具有最基本的動畫和大部分的主要畫面格動畫屬性。 如需詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)和[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
 下列範例顯示使用的效果<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType>屬性<xref:System.Windows.Media.Animation.DoubleAnimation>和使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType>屬性<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>請參閱  
 [在重複循環期間累加動畫值](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [動畫和計時](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
