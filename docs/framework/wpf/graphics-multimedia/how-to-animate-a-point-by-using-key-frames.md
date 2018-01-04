---
title: "操作說明：使用主要畫面格建立點的動畫"
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
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c115d31c6ace26f8fd9dd6cff3fdeead89eea33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>操作說明：使用主要畫面格建立點的動畫
這個範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Point>。  
  
## <a name="example"></a>範例  
 下列範例會沿著三角路徑來移動橢圓形。 此範例會使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性<xref:System.Windows.Media.EllipseGeometry>。 這個動畫會以下列方式使用三個主要畫面格：  
  
1.  在第一個半秒，會使用的執行個體<xref:System.Windows.Media.Animation.LinearPointKeyFrame>沿著路徑橢圓形移交穩定的速率，從其起始位置的類別。 線性的主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearPointKeyFrame>建立平滑的線性插補值之間。  
  
2.  在下個結束半秒，會使用的執行個體<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>突然移動路徑上的橢圓形的下一個位置的類別。 獨立的主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>建立值之間的突然跳躍點。  
  
3.  在最後的兩秒中，會使用的執行個體<xref:System.Windows.Media.Animation.SplinePointKeyFrame>類別，以將橢圓形移回其開始位置。 曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplinePointKeyFrame>建立變數的值根據值之間轉換<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>屬性。 在此範例中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。  
  
 此範例的程式碼版本使用的其他動畫範例的一致性，<xref:System.Windows.Media.Animation.Storyboard>物件以套用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>。 不過，當套用程式碼中的單一動畫，它會更容易使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，而不要使用<xref:System.Windows.Media.Animation.Storyboard>。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
