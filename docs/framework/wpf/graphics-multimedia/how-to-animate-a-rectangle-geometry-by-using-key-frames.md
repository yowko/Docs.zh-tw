---
title: 操作說明：使用主要畫面格建立矩形幾何的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: 581dc89d21091ad0ce856d7a7ced84fd7bcea9d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>操作說明：使用主要畫面格建立矩形幾何的動畫
此範例示範如何以動畫方式顯示<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>所使用的主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>。 這個動畫會以下列方式使用三個主要畫面格：  
  
1.  在第一個兩秒中，會使用的執行個體<xref:System.Windows.Media.Animation.LinearRectKeyFrame>以動畫方式顯示逐漸變更位置、 寬度和高度的矩形中的類別。 線性的主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearRectKeyFrame>建立值之間的平順地線性轉換。  
  
2.  在下個結束半秒，會使用的執行個體<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>類別突然減少矩形的高度。 獨立的主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>建立突變之間的值，也就是，請減少高度發生快速，而且不是難以察覺。  
  
3.  在最後的兩秒中，會使用的執行個體<xref:System.Windows.Media.Animation.SplineRectKeyFrame>類別，以變更回其原始大小和位置的矩形。 曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineRectKeyFrame>建立變數的值根據值之間轉換<xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A>屬性。 在此範例中，變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.RectangleGeometry>  
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>  
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
