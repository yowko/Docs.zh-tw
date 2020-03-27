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
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344684"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>操作說明：使用主要畫面格建立矩形幾何的動畫
此示例演示如何使用關鍵幀對<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>進行動畫處理。  
  
## <a name="example"></a>範例  
 下面的示例使用 類<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Media.RectangleGeometry>設置<xref:System.Windows.Media.RectangleGeometry.Rect%2A>動畫。 這個動畫會以下列方式使用三個主要畫面格：  
  
1. 在前兩秒鐘內<xref:System.Windows.Media.Animation.LinearRectKeyFrame>，使用類的實例對矩形的位置、寬度和高度進行動畫處理。 線性關鍵幀（<xref:System.Windows.Media.Animation.LinearRectKeyFrame>如在值之間創建平滑線性過渡）  
  
2. 在下半秒結束時，使用<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>類的實例突然降低矩形的高度。 離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>如在值之間創建突然變化）表示，高度的降低會迅速發生，並且不微妙。  
  
3. 在最後兩秒鐘內<xref:System.Windows.Media.Animation.SplineRectKeyFrame>，使用類的實例將矩形更改回其原始大小和位置。 樣條線鍵幀，<xref:System.Windows.Media.Animation.SplineRectKeyFrame>如根據<xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。 在此範例中，變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
