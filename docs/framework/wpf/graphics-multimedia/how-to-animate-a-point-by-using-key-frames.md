---
title: 操作說明：使用主要畫面格建立點的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344873"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>操作說明：使用主要畫面格建立點的動畫
此示例演示如何使用 類<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>為 。 <xref:System.Windows.Point>  
  
## <a name="example"></a>範例  
 下列範例會沿著三角路徑來移動橢圓形。 該示例使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>類對 屬性<xref:System.Windows.Media.EllipseGeometry.Center%2A><xref:System.Windows.Media.EllipseGeometry>進行動畫處理。 這個動畫會以下列方式使用三個主要畫面格：  
  
1. 在前半秒，使用<xref:System.Windows.Media.Animation.LinearPointKeyFrame>類的實例以穩定速率從起始位置沿路徑移動橢圓。 線性關鍵幀（<xref:System.Windows.Media.Animation.LinearPointKeyFrame>如在值之間創建平滑線性插值）。  
  
2. 在下半秒結束時，使用<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>類的實例突然沿路徑將橢圓移動到下一個位置。 離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>如在值之間創建突然跳轉）  
  
3. 在最後兩秒鐘內，使用<xref:System.Windows.Media.Animation.SplinePointKeyFrame>類的實例將橢圓移回其起始位置。 樣條線鍵幀，<xref:System.Windows.Media.Animation.SplinePointKeyFrame>如根據<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。 在此範例中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。  
  
 為了與其他動畫示例保持一致，此示例的代碼版本使用<xref:System.Windows.Media.Animation.Storyboard>物件來應用 。 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> 但是，在代碼中應用單個動畫時，使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法而不是 使用 更簡單。 <xref:System.Windows.Media.Animation.Storyboard> 例如，請參閱[在不使用分鏡腳本的情況下為屬性設置動畫](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
