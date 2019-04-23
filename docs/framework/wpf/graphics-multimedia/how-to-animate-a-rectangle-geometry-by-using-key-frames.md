---
title: HOW TO：使用主要畫面格建立矩形幾何的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: 03953b79127ffceeb49e4ece2070d09f382448a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311340"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>HOW TO：使用主要畫面格建立矩形幾何的動畫
此範例示範如何建立動畫<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>使用主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>。 這個動畫會以下列方式使用三個主要畫面格：  
  
1. 在前的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.LinearRectKeyFrame>類別以動畫顯示的位置、 寬度和高度的矩形逐漸變更。 線性主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearRectKeyFrame>建立平滑的線性轉換值之間。  
  
2. 下一步 結束期間半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>突然減少矩形的高度的類別。 特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>突然之間建立變更的值，也就是，高度降低很快就會完成，而不是微量。  
  
3. 在最後的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.SplineRectKeyFrame>類別，以變更回其原始大小和位置的矩形。 曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineRectKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A>屬性。 在此範例中，變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [主要畫面格操作說明主題](key-frame-animation-how-to-topics.md)
