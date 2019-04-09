---
title: HOW TO：使用主要畫面格建立點的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: 2e34ba035c8d7f9132915a9269d545f32033cbed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132583"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>HOW TO：使用主要畫面格建立點的動畫
此範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Point>。  
  
## <a name="example"></a>範例  
 下列範例會沿著三角路徑來移動橢圓形。 此範例會使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性<xref:System.Windows.Media.EllipseGeometry>。 這個動畫會以下列方式使用三個主要畫面格：  
  
1.  在前半秒，期間使用的執行個體<xref:System.Windows.Media.Animation.LinearPointKeyFrame>將橢圓形沿著路徑以穩定速率，從其起始位置的類別。 線性主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearPointKeyFrame>建立平滑的線性插補值之間。  
  
2.  下一步 結束期間半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>突然將橢圓形沿著路徑移動到下一個位置的類別。 特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>建立突然跳躍點之間的值。  
  
3.  在最後的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.SplinePointKeyFrame>類別來將橢圓形移回起始位置。 曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplinePointKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>屬性。 在此範例中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
 為了和其他動畫範例保持一致，使用此範例中的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>物件，要套用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>。 不過，套用單一動畫的程式碼中，時，使用的工作變得更容易<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，而不是使用<xref:System.Windows.Media.Animation.Storyboard>。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
